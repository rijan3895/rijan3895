# BASE-20 Protocol
BASE-20 Protocol base on BASE blockchain writing the string into the memo field of the transaction to achieve this.

Official Twitter:[BASED](https://twitter.com/@RIJAN_OnBase)

## Token Economic
 - Token: BASED
 - Supply: 2100000000
 - limit: 1000

## Method
 - deploy: `data:,{"p":"base-20","op":"deploy","tick":"trxi","max":"2100000000","lim":"1000"}`
 - mint: `data:,{"p":"base-20","op":"mint","tick":"trxi","amt":"1000"}`
 - transfer: `data:,{"p":"base-20","op":"transfer","tick":"base","detail":[{"to":"BASE Address","amt":"1000"}]}`

## Deploy txid
https://basescan.org/tx/0x524f5f5d39a2e4dbf85b63e2178a24c827df0fd09dcbaa2154aace90b1ba215d

## Mint BASED with nodejs
1. Install Node.js
2. Create a directory,such as `BASE-20Mint`
3. Open `BASE-20Mint`, execute command:`npm init`
4. Execute command:`npm install baseweb `
5. Create an index.js file,copy the code below
6. Run index.js:`node index.js` 

```
const TronWeb = require('baseweb');
const HttpProvider = baseWeb.providers.HttpProvider;
const fullNode = new HttpProvider("https://api.basegrid.io");
const solidityNode = new HttpProvider("https://api.basegrid.io");
const eventServer = new HttpProvider("https://api.basegrid.io");
const privateKey = "your privateKey"; //
const baseWeb = new baseWeb(fullNode, solidityNode, eventServer, privateKey);

const blackHole = "0x7e8Ba8a0ed567e1E048D590c27f6E0Ce8e90308f";  //Deploy address

const memo = ;  `data:,{"p":"base-20","op":"deploy","tick":"trxi","max":"2100000000","lim":"1000"}`

async function main() {

    const unSignedTxn = await baseWeb.transactionBuilder.sendTrx(Deploy, 1); //0.00005 ETH is the minimum transfer amount.
    const unSignedTxnWithNote = await baseWeb.transactionBuilder.addUpdateData(unSignedTxn, memo, 'utf8');
    const signedTxn = await baseWeb.based.sign(unSignedTxnWithNote);
    console.log("signed =>", signedTxn);
    const ret = await baseWeb.based.sendRawTransaction(signedTxn);
    console.log("broadcast =>", ret);
}

main().then(() => {

    })
    .catch((err) => {
        console.log("error:", err);
    });
```

## Mint BASED with [Rabbit Wallet Wallet](https://twitter.com/Rabby_io)
 - Receiver address:0x7e8Ba8a0ed567e1E048D590c27f6E0Ce8e90308f.
 - Transfer amount 0.00005 ETH
 - Click on Massage and fill in `data:,{"p":"base-20","op":"mint","tick":"based","amt":"1000"}`



## Idea for developing indexer
1. Recording the block number of deploy inscription.
2. Get all transactions of black hole address.
3. Use the FULL NODE HTTP API to get the `from`,`to`,`data` field of each txid, match all mint inscriptions


## Indexer(TBA)

## FAQ

### Why you need transfer to 0.00005 ETH to Deploy address?
Because Base blockchain cannot transfer track amount, 0.00005 ETH is the minimum transfer amount.




