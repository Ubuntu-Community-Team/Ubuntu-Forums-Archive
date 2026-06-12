---
title: "ElectricSheep problem"
date: 2006-07-22
forum: Desktop Environments
---

### Post by Blazeix on 2006-07-22
Hi. I downloaded the [Electric Sheep screensaver](http://www.electricsheep.org/) from an Ubuntu repository, and I can't get it to work. I have downloaded the screensaver cache, which it needs to run, but when I try to run it I get the following error:
```

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  65
  Current serial number in output stream:  65
Terminated

```

Does anybody know what this error is, and how to fix it? Thanks

---

### Post by YoshiHNS on 2007-12-10
Yeah, im having the same problem.

Question. did you try using any of the other methods of installing? I did have it working before just through the package manager, but uninstalled it cause i was not getting any sheep (turned out i had the ports closed, D'OH). Now i cannot get it running again. I tried installing it as desribed in the guides for dapper, through synaptic, through .tar.bz, and all lead to the same error. All my other screensavers are there and still work.

---

### Post by YoshiHNS on 2007-12-16
Ok, after a failed attempt, i left it installed. Couple days later, I downloaded an update for electric sheep from the update manager and it works now.

---

### Post by al2cane on 2008-01-11
I installed it via synaptic too, but I don't get an error, it just doesn't work. The preview screen is just blank, even when I dropped some files into ~./sheep it still doesn't work.

Have a Mac running Leopard here, and that's not updating either, but at least it's working when I manually put the files into ~/Library/Application Data/ElectricSheep

Oddly, the Windows XP machine is the only one that's working no problem, with no tweaks.

---

