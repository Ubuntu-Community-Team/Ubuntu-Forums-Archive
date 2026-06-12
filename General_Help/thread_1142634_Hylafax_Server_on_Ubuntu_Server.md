---
title: "Hylafax Server on Ubuntu Server"
date: 2009-04-29
forum: General Help
---

### Post by drunkgunner on 2009-04-29
Hi all.
 
I hope I'm posting under the right topic. I'm trying to get Hylafax server running on an Ubuntu Server 8.04.2. The server and modem installed fine, but when I run sudo faxstat, it says (with X representing the phone number):
 
```
Modem ttyACM0 (X.XXX.XXX.XXXX): Waiting for modem to come ready
```
 
 
I can cu -l into the modem and run commands, but when I try to see the status (either busy or ready) it says busy. 
 
The server is on an old Dell Optiplex GX260, and the modem is a US Robotics v.92 external USB, model number 5637. This is a class 1 modem, according to cu and the faxaddmodem command. This is a project for my job, and must be done as cheeply as possible (meaning absolutely no Windows). If it works, it will be replicated to 77 satellite [COLOR=#002e5e]offices. [/COLOR]I have been to the hylafax [COLOR=#002e5e]website[/COLOR] and poured over the documentation there, and searched google, but to no avail. That may not mean much though, because I'm new to Ubuntu (only been using it for about 3 years). Any suggestions?

---

### Post by Digram_seth on 2009-05-09
well a good idea is to get serial modem it worked for me

---

### Post by drunkgunner on 2009-05-15
Is there any way to get this modem to work though? My boss is on me to get this resolved. Anyone need more details?

---

### Post by richw on 2009-05-21
Did you get this working in the end?

If not I'd suggest trying Ubuntu 9.04 to test with - it might be the case that the driver has been updated and it will work now. Otherwise it might be easier to pick up a external serial modem (the cheap USR external cream cased ones seem to work really well under class 1 but are limited to 14.4 send).

---

### Post by capt scroggins on 2009-06-17
I am having the same exact problem as OP. I have a US Robotics Courier external modem. Although they say these are the best for this I cannot get the status to say "Running". I have tried the set up on this site to no avail.

[http://www.aboutdebian.com/modems.htm](http://www.aboutdebian.com/modems.htm)

---

### Post by markvwxyz on 2009-07-29
see post at [http://ubuntuforums.org/showthread.php?p=7702176#post7702176](http://ubuntuforums.org/showthread.php?p=7702176#post7702176)

---

### Post by t4thfavor on 2009-07-29
I only got 1 usb modem to work 2 or 3 times. I mostly have luck with the USR serial modems, and multitech. They are far more expensive, but your time costs much more money in the end.

---

