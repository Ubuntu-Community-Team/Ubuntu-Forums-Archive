---
title: "App behaves differently if I load it from the commandline or a Launcher icon"
date: 2008-06-26
forum: Desktop Environments
---

### Post by fotherington on 2008-06-26
I'm using the program AuctionSieve ([www.auctionsieve.com](www.auctionsieve.com)) to search Ebay listings, but have been getting some weird behaviour when using it. When I run AuctionSieve from the commandline using the command ```
java -Xmx512m -jar -DBROWSER="firefox %s" /usr/local/jar/AuctionSieve/auctionsieve.jar
```, and then click 'view' inside the program to open the auction's webpage I get ```
browser = firefox %s
Trying firefox http://rover.ebay.com/rover/1/710-53481-19255-0/1?type=2&campid=5335846438&toolid=10001&customid=AuctionSieve1.9.1&ext=310059890415&item=310059890415
```
appearing in the terminal, and everything works fine.

I created a Launcher icon which runs the same command. If I click on it to run AuctionSieve, when I click 'view' I get
```
browser = firefox s
Trying firefox s "http://rover.ebay.com/rover/1/710-53481-19255-0/1?type=2&campid=5335846438&toolid=10001&customid=AuctionSieve1.9.1&ext=180255426326&item=180255426326"
```
appearing in the terminal, and Firefox tries to open two windows, one of them with the address "s" and one of them with the address "file:///home/tom/%22http://rover.ebay.com/rover/1/710-53481-19255-0/1?type=2&campid=5335846438&toolid=10001&customid=AuctionSieve1.9.1&ext=180255426326&item=180255426326%22".

Any ideas on why %s is changing into s in the second example? I'm running Ubuntu 8.04, and fiddling with the settings in Gnome's Preferred Applications menu setting doesn't seem to do help.

---

