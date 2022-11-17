Solana Project.
There are some function
To airdrop solana tokens to Phantom Address.
Create NFT Collection.
Mint NFT.
Display NFT if account is owner of some of them.
Create Candy Machine to Post NFT and information about them on solaneyes.com
See the NFT from Candy Machine by submitting CM Address.

We divided Project to 3 repositories:
first is https://github.com/nurnaoe/create-solana-nft-collection
Creating NFT Collection
second is https://github.com/nurnaoe/solana-candy-machine
Minting NFT Collection
third is https://github.com/nurnaoe/solana-nft-display
Displaying NFT Collection

Prerequirements: 
1.Any IDEA which has service to run typescript/javascript/solidity functions.  We used VS Code.
2.Solana crypto wallet. Better to use Phantom Wallet.
3.Node js.


🤨 NFT your face. Create and Update your NFT
git clone https://github.com/nurnaoe/create-solana-nft-collection
cd create-nft
npm install
npm start

If there will be some error with airdrop solana:
run these commands:

solana airdrop 1 EeZN1m2QYzrvFKX64vKTkzwmeg8BjQCBjNCLWbjiwBXS --url devnet

Make Sure that you used own public key.

change address in main function:

const mintAddress = new PublicKey("put your own public address")

🛠 Install the CLIs

Before we can get into this, we'll need to install:

The Solana CLI - the Sugar CLI needs this. You can install it here for your OS.
The Sugar CLI - you can install it here.

If they were installed right, you should see version numbers instead of errors when you run 
solana --version and sugar --version in your terminal.

This is also a good time to set up your local Solana wallet on the devnet if you don't have one. 
Run these commands in your terminal:

solana config set --url devnet
solana-keygen new --outfile ~/.config/solana/devnet.json

Save public Key to airdrop solana.
Save this seed phrase and your BIP39 passphrase to recover your new keypair.
Go to the Config File that was setted after 1st command and change Keypair Path to your path/devnet.json. Save file.
Go back to terminal and run these:

solana airdrop 2
If command result is error: run this command to airdrop by another way
solana airdrop 1 AKmdkAhRQ1PpdsZAW7NFrpjRRvdEKifG7YU4BSSAScd6 --url devnet
solana balance

Make sure that your folder name does not have spaces!

🍬 Set up your collection
This is going to be one of the hardest parts of the build: deciding what you want to make an NFT collection of. You'll need at least 5 images, one for each NFT in your collection. I'm going with some classic pepes because pepes just speak to me.

Make a new project folder in your Solana workspace and create an assets folder inside it. You need to pair each NFT asset with a metadata JSON file, numbering each pair from zero. So, your folder structure should look something like this:

...
|
|── assets
|   |── 0.png
|   |── 0.json
|   |...
|   |── 5.png
|   |── 5.json
|
|── node_modules
|── src
|── package.json
....

In practice, you'll write a script to generate these files, but for now, we'll just do it manually. 
You can start with these example assets and replace the images with your own. 
Make sure you update the JSON files too!

You can optionally also add a collection.json with a matching collection.png - these will be used by 
marketplaces as the collection name, description, and thumbnail.

Here's a template:

{
  "name": "Studious Crabs Collection",
  "symbol": "CRAB",
  "description": "Collection of 10 crabs seeking refuge from overfishing on the blockchain.",
  "image": "collection.png",
  "attributes": [],
  "properties": {
    "files": [
      {
        "uri": "collection.png",
        "type": "image/png"
      }
    ]
  }
}

🍭 Configure your Candy Machine

The next thing we need to do is create a Candy Machine configuration file. 
This is what's used to create the on-chain Candy Machine instance.

🚀 Launch your NFT collection

Smash in sugar launch in your terminal and hit y when it asks if you want to create a new configuration file. 
Answer the questions and you'll be left with a config.json file in your project folder.

If result is succesfull save candyy machine id and collection mint id.
You can check your candy machine at the link in your terminal.

Second Repo:
🌐 Create a front-end for your NFT collection

The Metaplex foundation has a slick React UI template you can use to create a front-end for your NFT collection. 
Let's set it up:

git clone https://github.com/metaplex-foundation/candy-machine-ui
cd candy-machine-ui
npm i

If you have some many vulnurabilities just use command to fix them:
npm audit fix/--force

There's a lot happening here that we don't need to worry about. Rename .env.example to .env and paste in your 
Candy Machine ID that you copied earlier.

REACT_APP_CANDY_MACHINE_ID= Your candy machine id
Add in last line: 
GENERATE_SOURCEMAP=false to solve future errors.
This is all you need to do! Now if you run npm start you'll see a shiny UI on localhost:3000 that you can use to mint your NFTs.

If you have some errors, just read about them and use npminstall to solve them.
To solve 3 warnings with red colored "fs " package error, write this string to ./node_modules/@project-serum/anchor/package.json file:
"browser": {
"fs":false,
"path": false,
"os":false
}

Third repo:

Displaying NFTs from a wallet

Run These commands:
git clone https://github.com/nurnaoe/solana-nft-display
cd solana-display-nfts-frontend 
npm install
npm run dev.
