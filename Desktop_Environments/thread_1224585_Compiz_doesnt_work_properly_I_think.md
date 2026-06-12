---
title: "Compiz doesnt work properly I think"
date: 2009-07-27
forum: Desktop Environments
---

### Post by sasadef on 2009-07-27
What happens to my computer cannot be describes by words, the Window borders are gone, cannopt manage Windows properly, I think I messed up... I will post pics

---

### Post by themusicalduck on 2009-07-27
Do you have emerald installed?

Try pressing alt+f2, type ```
 emerald --replace
``` into the box and then hit enter.

To make it work on startup automatically, you can enter the command into startup applications.

Go to System > Preferences > Startup Applications.

Click on Add and enter emerald --replace into the command box. Name it anything you like.

---

### Post by sasadef on 2009-07-27
I did... no effect... I also have it "checked" in the Compiz Config Icon... when I change from Metacity to Compiz it has the same effect

---

### Post by Aroll605 on 2009-07-27
```


$ killall emerald* && killall compiz* && compiz --replace


```

Otherwise, just relog (restart X)

---

### Post by sasadef on 2009-07-27
> **Aroll605 said:**
> ```


$ killall emerald* && killall compiz* && compiz --replace


```

Otherwise, just relog (restart X)

After that i got
```

$ killall emerald* && killall compiz* && compiz --replace
emerald*: no process killed

```

then i tried
```

$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

```

---

### Post by sasadef on 2009-07-28
bump... anyone?

---

### Post by hictio on 2009-07-28
Have you tested your box with [Compiz Check](http://forlong.blogage.de/entries/pages/Compiz-Check)?
I tell you because the "Checking for Xgl: not present." bit doesn't look any promising.

---

### Post by sasadef on 2009-07-28
it reads 
```

$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)
 Driver in use:         openchrome
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: openchrome driver in use 


```

---

### Post by hictio on 2009-07-28
But, did Compiz, or the Desktop Effects, work on that box at any given time?

---

### Post by andrea000 on 2009-07-28
I'm not sure but this looks like a problem i
had a while back and i found the problem to
be in compiz and i had to turn off full screen
support.I have not had it happen again.

hope this help's

---

### Post by sasadef on 2009-07-28
> **hictio said:**
> But, did Compiz, or the Desktop Effects, work on that box at any given time?
No it never did....

> **andrea000 said:**
> I'm not sure but this looks like a problem i
had a while back and i found the problem to
be in compiz and i had to turn off full screen
support.I have not had it happen again.

hope this help's

Tried it, and failed. thank for the reply anyways :)

---

### Post by mjstelly on 2009-07-28
> **sasadef said:**
> What happens to my computer cannot be describes by words, the Window borders are gone, cannopt manage Windows properly, I think I messed up... I will post pics

Compiz crashed my desktop. I think it's because I use Jaunty with an Intel mobo. There are known issues. So, I just got rid of it. I'll find some other resource vampire to replace it, I'm sure. :)

---

