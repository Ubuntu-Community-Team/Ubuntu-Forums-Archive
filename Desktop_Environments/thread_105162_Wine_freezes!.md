---
title: "Wine freezes!"
date: 2005-12-17
forum: Desktop Environments
---

### Post by firecat53 on 2005-12-17
Each time I try to run winecfg (or wine), the computer says "wine: creating configuration directory '/home/user/.wine'..." and then completely locks up. No other messages, and it requires the computer be turned off to restart it. After trying a couple of times to install Wine via Automatix and Synaptic, I have no idea what the issue is!  Any ideas?? I'm not even sure where to look for the problem. I checked dmesg and /var/log/ and I don't see anything applicable to wine.

Thanks, Scott

---

### Post by firecat53 on 2006-01-19
Any thoughts on this? This is about the only issue that completely and reliably locks up the computer each and every time.  It creates the .wine directory, but then completely freezes and never finishes.  I'd really like to try out Picasa via Wine!

Thanks, Scott

---

### Post by jasay on 2006-01-19
I don't have a solution for you.  I would assume automatix uses the latest version of wine from the [winehq repos]("http://www.winehq.com/site/download-deb")??  If not, you should try putting ```
deb http://wine.sourceforge.net/apt/ binary/
```in your sources list and installing with apt/synaptic.  Probably won't help, but worth a shot.  

To give you some encouragement, I've had picasa running on two different installs flawlessly, so it shouldn't be too bad if you can find a workaround for your current problem.

---

### Post by dcstar on 2006-01-19
[QUOTE=firecat53]Any thoughts on this? This is about the only issue that completely and reliably locks up the computer each and every time.  It creates the .wine directory, but then completely freezes and never finishes.  I'd really like to try out Picasa via Wine!

Thanks, Scott[/QUOTE]
Delete the .wine directory and try again.

---

