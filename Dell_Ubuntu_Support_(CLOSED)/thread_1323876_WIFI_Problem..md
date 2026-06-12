---
title: "WIFI Problem."
date: 2009-11-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Skrip on 2009-11-12
Hello, I have Installed  Ubuntu 9.10 on my laptop DELL XPS 1530 and  have problem with my wireless... any know about this problem??

---

### Post by JBAlaska on 2009-11-12
Are you trying to connect to 2.4GHz(B/G) or 5GHz(N)? There seems to be a issue with 9.10 and the Intel 4965 @ 5GHz. Try connecting to 2.4GHz and see if that helps.

---

### Post by Skrip on 2009-11-12
The problem is that the WIFI seems not working at all, because it does not find mine and other connection...

---

### Post by Skrip on 2009-11-13
any solution to this problem?

---

### Post by bobcollard on 2009-11-14
> **Skrip said:**
> The problem is that the WIFI seems not working at all, because it does not find mine and other connection...

Check your driver by going to menu/applications/system/hardware drivers and see if the drivers there are installed.  You may find a choice of two, I don't know the brand of card in your computer, mine is a Broadcom in my Dell 1545.  I had to reinstall the driver because the different system wiped out the old one.

---

### Post by Skrip on 2009-11-15
Well i have tried to go to Hardware Drivers but there it dont find anything dont know why.... even drivers for nvidia as it used to do at previous versions of ubuntu..

---

### Post by bobcollard on 2009-11-15
> **Skrip said:**
> Well i have tried to go to Hardware Drivers but there it dont find anything dont know why.... even drivers for nvidia as it used to do at previous versions of ubuntu..
You might try wicd.  It is another Linux network manager.  Get it through the synaptic Package Manager.  Some people have had good luck with that.  I'm out of suggestions.

---

### Post by jeb800e on 2009-11-15
Get the NDISwrapper packages from Synaptic. Make sure you check "ndiswrapper-common" and "ndisgtk" or something like that. Selecting these will most likely automatically select a few other packages. Thats okay, it needs those extra packages to run.

Once installed, go to System < Administration < Windows Wireless Drivers. Follow the on-screen instructions

---

### Post by life2short1971 on 2009-11-20
try physically removing the card and reinstalling it

---

### Post by Skrip on 2009-11-22
Ok Thanks Guys i could not resolve the problem so i uninstalled it...

---

### Post by ublintu on 2009-11-22
Do you have broadcom wireless? If yes, maybe you can try this (the first post): [http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)
I had the same problem with broadcom and this solved it.

---

