---
title: "Broadcom 43xx install help"
date: 2007-09-08
forum: Dell  Ubuntu Support
---

### Post by aguttorm on 2007-09-08
So here's my problem:

I've just loaded Edgy on my laptop (I dual-boot Ubuntu and XP), and I travel a lot with it, so I don't often have a hardwire connection to the internet.  I'm having the same problem as most everyone else with the Broadcom 43xx driver.

I've followed the directions in this guide:  How to: Broadcom Wireless cards without Ndiswrapper for Dapper and Edgy.  The problem for me is that I can't access the internet to get the repositories I need since I don't have a hardware connection.

I've copied over bcm43xx-fwcutter, ndiswrapper, and the wireless driver to my ubuntu desktop.  Is there anything I can do from here?  I REALLY REALLY REALLY want to use Ubuntu more, but without internet access, I'm relegated to XP.

Please help!

P.S.  I am a complete noob to Linux, Ubuntu, and coding in general.  I've dealt with DOS a bit, and that made sense to me.  Linux....not so much (yet.)

---

### Post by strabes on 2007-09-08
This is the howto that I used to get two of my friends bcm4318 cards working: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Just follow the howto all the way through. I had to compile ndiswrapper from source both times. It's really not hard if you just follow all of the directions exactly.

I suppose you could download the relevant files while inside windows, boot into linux, and run the other commands.

---

