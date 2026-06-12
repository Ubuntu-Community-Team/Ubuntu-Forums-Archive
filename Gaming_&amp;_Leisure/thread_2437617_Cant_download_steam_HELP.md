---
title: "Cant download steam HELP"
date: 2020-02-26
forum: Gaming &amp; Leisure
---

### Post by ckraemer95 on 2020-02-26
I'm about at the end of my rope with this here...ive been trying to download steam for about a week now. I've got ubuntu 19 through my stylo 4+ and long story short ive purged everything downloaded steam deb downloaded the 32 bit libraries via this; sudo apt-get install '^libc6*; (which seems to be the only one that works) then sudo apt install steam then changed it to where I can run it as root...so thats where I'm at...i click on applications games steam it pops up with steam needs to install these additional packages (the 32 bit libraries) then it cant find them and it doesnt have an installation candidate. Click on the steam desktop image which pops up with you are missing the 32 bit libraries and may not run and also message saying failed to run steam.desktop this feature requires a file manager service like thunar but I have xfe file manager that I've set as my default file manager even tried to gio mime it to steam..nothing seems to be working...its been at least a week..just wanna game...please I've searched through all the forums is there ANYBODY who can help or should I just give up.

---

### Post by deadflowr on 2020-02-26
Isn't the stylo 4+ an arm cpu?

---

### Post by DuckHook on 2020-02-26
> **deadflowr said:**
> Isn't the stylo 4+ an arm cpu?
Not only is it ARM (Snapdragon 450) but it's a phone.

@ckraemer95

Ubuntu desktop apps will not magically work on phones. In general, phone apps must be specifically designed for phones; likewise, desktop apps for desktops. The two architectures do not intersect.

---

### Post by oldrocker99 on 2020-02-26
Every OS, from Windows, OSX, Linux and Android have one thing in common: they are built to run only apps which are written for it, and it's entirely possible that your CPU (a fine one, BTW) just won't handle Steam.'

Or maybe it will, with some tweaks. Google is your friend.

---

### Post by mastablasta on 2020-02-27
well, just in case the OP is just using Stylo phone as modem, wi-fi hot spot or in general for internet access, then all they need to do is to install steam that is found in ubuntu software center. people are over complicating things.

to use steam you need good, stable internet connection.

---

### Post by DuckHook on 2020-02-27
> **mastablasta said:**
> well, just in case the OP is just using Stylo phone as modem, wi-fi hot spot or in general for internet access, then all they need to do is to install steam that is found in ubuntu software center. people are over complicating things.

to use steam you need good, stable internet connection.
This is a more logical interpretation of OP's post. Will wait for clarification from OP.

---

### Post by guiverc on 2020-02-27
I don't know what release you're using.  There is no Ubuntu 19, as Ubuntu server and desktop releases use the *yy.mm* format, and only special purpose releases *like Ubuntu Core 18 for IoT appliances* that use the *yy* format.

If your release is 19.04, then it's EOL ([http://ubuntu-news.org/2020/01/23/ubuntu-19-04-disco-dingo-end-of-life-reached-on-january-23-2020/](http://ubuntu-news.org/2020/01/23/ubuntu-19-04-disco-dingo-end-of-life-reached-on-january-23-2020/)) and this could be part of your problem, or you're not using Ubuntu at all, but something else calling it Ubuntu 19 (*as there is no Ubuntu 19*).

---

