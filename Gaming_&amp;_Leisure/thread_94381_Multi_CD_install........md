---
title: "Multi CD install......."
date: 2005-11-23
forum: Gaming &amp; Leisure
---

### Post by OldGaf on 2005-11-23
OK, I have read many threads by people trying to install programs from more then one CD and no one seems to have a fix.

I am trying to install COD with wine. When I need to put the 2nd CD in I am unable to eject the 1st one. The only process that is using the CD is the install program. I am not in the CD dir when I call the setup exe so it is not the shell that is using it. I am unable to force the eject from the shell.

So...... is it NOT possible to install an application in Kubuntu that has more then   one CD? if so, then I would have to say that this OS is pretty useless!

---

### Post by xENObRAIN on 2005-11-23
This has been posted as a solution in cedega threads, I'm sure it's relevant here:

```

killall -USR2 wineserver

```

also try adding
```

--monitor-cdrom-eject

```
when you run the installer from the commandline.

---

### Post by OldGaf on 2005-11-24
Thanks for the reply.... I will give it a try when I get home from work today.

---

### Post by OldGaf on 2005-11-24
> 
Code:

killall -USR2 wineserver


also try adding
Code:

--monitor-cdrom-eject



Nope.... that didn't work. It just takes out the install program...... sigh..... I was SO close to going with linux too. Maybe I should try another Distro.....

---

### Post by tflovik on 2005-11-26
When you start installing you have to be in another directory than your cdrom. eg. wine /media/dvd/COD .
If you start installing when in the cdrom directory you will be unable to unmount or eject if the installer asks for another cd.

---

