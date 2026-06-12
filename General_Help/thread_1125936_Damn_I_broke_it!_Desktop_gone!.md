---
title: "Damn I broke it! Desktop gone!"
date: 2009-04-14
forum: General Help
---

### Post by sailthesea on 2009-04-14
Hi guys 
 I was just trying to fix a sound problem using the sticky in Multimedia but have run into a problem 
 When I rebooted I can only get to the kernel logon screen and I don't know how to get to my desktop I haven't learned enough about the CLI to to do it It seems I've removed some element of Gnome but no idea what Can I sudo back to my desktop and fix it? 
I only really want to rescue the mods I've done so far !
 I am using 8.10 installed with Wubi in Win 2000! Its done great so farI want to dual boot but I need to get my CD burnt first
 Thanks !

---

### Post by JC Cheloven on 2009-04-14
At the command line you have, try:

```
startx
```

---

### Post by sailthesea on 2009-04-14
Cool Will try that 
Gonna wait a few and see if anything else comes up though
Ta

---

### Post by balaknair on 2009-04-15
If you've been trying to reinstall some of the stuff like the alsa packages in Ubuntu, you might have removed the package ubuntu-desktop.

Try the command ***sudo apt-get install ubuntu-desktop***

---

