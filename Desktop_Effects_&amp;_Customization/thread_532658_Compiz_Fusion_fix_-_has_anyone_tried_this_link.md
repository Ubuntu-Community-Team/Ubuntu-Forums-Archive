---
title: "Compiz Fusion fix - has anyone tried this link?"
date: 2007-08-23
forum: Desktop Effects &amp; Customization
---

### Post by bmdavis on 2007-08-23
Like many of you, I'm stuck on getting CompizFusion to work on a computer with an ATI card  (Inspiron 6400, ATI X1400 to be exact), keep getting the "impossible to start compiz" line in the terminal.   And like many of you, I've Googled and searched countless times, gone through tons of tutorials, installed and uninstalled, etc. to no avail.

Too bad that's what has attracted so many newbies to linux, huh?  ;-)


Anyways, stumbled upon this link today, and was wondering if anyone has used it to try a fix?  

[URL="http://isilanes.blogspot.com/"]
http://isilanes.blogspot.com/[/URL]

Searched the forum and didn't find the link, so might be worth a try!  I'm hoping someone else has tried it so I don't go through all the steps though... ha.

Good luck everyone!

---

### Post by praet on 2007-08-23
Were you able to get direct rendering to work?

```
glxinfo |grep -i direct

```

---

### Post by shorty28898 on 2007-08-23
if i cant get direct rendering to work, what can i do?

---

### Post by praet on 2007-08-27
shorty28898,

direct rendering is a capability that is enabled by the prober installation of drivers for your video card.

Make sure you have installed the card's driver. Usually using Restricted Drivers manager is enough.

If you are still having problems, try searching online with your video card 
```
lspci |grep VGA
```
and also check your xorg logfile for errors: 
```
cat /var/log/Xorg.0.log |grep EE
```

Good luck.

---

