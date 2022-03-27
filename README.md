# Aval-bot
Market making bot using [Dexalot](https://dexalot.com/)'s smart contracts and REST API endpoints 📈

You can either manually run commands to read order book, create orders or cancel them.
Or you can run the bot, which does this automatically, according to steps describeed in docs
(That is a reason why there are 2 cancels consecutively, that loop is pretty unusable)

Bot does only basic stuff, it also undercuts itself. But since he cancels all orders it does not make a difference.

There are no event listeners implemented, no time 😭😭😭

Project is based on some hello-world examples, so there is a lot of unecessary files.
Everzthing important is in file `bot.html`

*Disclaimer: Code is a mess of hack'n'slash coding, so do not look for best practices, error checking etc.*

# What is done
- ✅Start with depositing your tokens from the frontend (See bonus items)
- ✅Get Reference Data from the RESTAPI (contract addresses, pairs, trade increments, min, max trade amount)
- ✅Enter a BUY & a SELL order with a predefined spread around a given mid price or last price against the contracts. (Keep orders in an internal map)
- ✅Shut down your market maker manually
- ✅Restart your market maker &  Get your open orders from RESTAPI at startup
- ✅Wait ~10 seconds and Cancel Buy & Sell your previously opened orders. ~~If you can foresee & mitigate a potential issue in the previous step.~~
- ✅Wait ~20 seconds and enter a new set of buy & sell orders  with different prices based on the changing mid/last price  against the contracts.
- ✅Wait ~30 seconds and CancelAll all your open orders using CancelAll against the contracts.
- 🚫Listen to OrderUpdate Events. We will enter an order that will fill one of your orders and your code have to react by entering a new order in about ~10 seconds after the fill. 
- 🚫Listen to Executed Events and react to it as above.
- 🚫Read the order book from the contracts and console.log it
- 🚫Deposit tokens into Dexalot Portfolio programmatically
- 🚫Get gas cost of each order and log it before in order to make buy/sell decisions with t-cost in mind (and console.log it ).

# Run
```
http-server
```

# Quick setup 
No smart deployment here...
```
apt install nodejs
apt install npm
nvm install v16.14.0
npm install --save http-server
npm install --save ethers
```
(Some more steps might be required so act according to errors you encounter. Sorry)