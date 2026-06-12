---
title: "Internet over PPP with Null Modem Cable"
date: 2005-12-11
forum: Desktop Environments
---

### Post by ChrisII on 2005-12-11
I am trying to set up a PPP connection to a WinXP System using PPP with a Null Modem Cable using Ubuntu 5.10.

I've played with pppconfig, tried pon, looked at wvdial.

My WinXP machine is set up to receive a PPP connection on com2 and I've set up ttys1 (com2) on the ubuntu machine as a PPP client. Both machines are connected via Null Modem cable on Com2.

I'm just not sure if i am doing things correctly.

I ran "sudo pon myconnection" no error occurred but no connection occurred either.

---

### Post by Sendervictorius on 2005-12-12
If I understand right, you are trying to set up your linux box as a ppp server? You should read one of the standard linux howtos to get an understanding about what you need to do. This one's a little old: [http://www.tldp.org/HOWTO/PPP-HOWTO/](http://www.tldp.org/HOWTO/PPP-HOWTO/)

Breezy uses ppp v 2.4.3.  Check out chapter 29. Using PPP across a null modem (direct serial) connection

-Andrew

---

### Post by ChrisII on 2005-12-12
Actually it's the other way around. I need the ubuntu system to be the PPP Client. I got WinXP as the PPP Server. See the problem is, the system i got running Ubuntu doesn't have a PS2 Port (missing) as well i haven't been able to find a working NIC either... LOL

I want internet and this is how i feel like doing it.

I will read this URL and by the sounds of it, that should be all i need, I will post again if i run into difficulty.

---

### Post by ChrisII on 2005-12-12
I believe I require a chatscript. But I just don't undetrstand how to make one, the documentation I found just isn't very helpful at explaining things...

Any Help?
Need a chatscript to connect to a PPP server on WinXP.

If I undertstood the commands on how to make one I'd do it myself.

EDIT:
I have succeeded in what i wanted to accomplish. I somehow managed to create a very simple chatscript. WinXP's like oh you are trying to connect, after getting the proper IP addresses configured. Everything is running excellently.

---Chatscript Contents---

'' "CLIENT \c"
'' ""

---END Chatscript--------

---

