---
title: "USB Help!!"
date: 2009-02-05
forum: General Help
---

### Post by AngusMcBurger on 2009-02-05
I went to system, administration, Create a USB Startup disk thinking it would be like the live cd (I wanted linux on a pc with a currently faulty dvd drive!). In the end I just deleted it but linux seems to want to install everything on it because when I tried to download a flash plugin for Firefox it came up with an error message saying:
Can not install 'flashplugin-nonfree' (E:Unable to correct problems, you have held broken packages.)
(My memory stick is name E: and because it is 4gb I thought I wouldn't mind having ubuntu on it.)
How do I stop it wanting to save on to my memory stick?!
Help fast!
Thanks!

---

### Post by lykwydchykyn on 2009-02-05
> **AngusMcBurger said:**
> I went to system, administration, Create a USB Startup disk thinking it would be like the live cd (I wanted linux on a pc with a currently faulty dvd drive!). In the end I just deleted it but linux seems to want to install everything on it because when I tried to download a flash plugin for Firefox it came up with an error message saying:
Can not install 'flashplugin-nonfree' (E:Unable to correct problems, you have held broken packages.)
(My memory stick is name E: and because it is 4gb I thought I wouldn't mind having ubuntu on it.)
How do I stop it wanting to save on to my memory stick?!
Help fast!
Thanks!

The "E:" has nothing to do with your USB drive.  Linux does not use drive letters.  E: here is just short for "error", that's the way APT outputs errors.

You may want to run this at the prompt to fix your broken packages:
```

sudo aptitude -f install

```

if it doesn't work, post the output here.

---

### Post by cariboo on 2009-02-05
Your problem has nothing to do with your USB device. You have broken packages that need to be repaired before you can install any thing. Go to SYstem-->Administration-->Synaptic PAckage Manager-->Edit-->Fix Broken Packages, and either reinstall the broken packages, or completely remove them.

Jim

---

### Post by AngusMcBurger on 2009-02-05
It still doesn't seem to want to save downloads properly?! :?

---

### Post by lykwydchykyn on 2009-02-05
Can you elaborate?

---

