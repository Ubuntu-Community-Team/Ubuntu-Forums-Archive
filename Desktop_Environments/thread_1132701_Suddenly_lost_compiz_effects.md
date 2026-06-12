---
title: "Suddenly lost compiz effects"
date: 2009-04-22
forum: Desktop Environments
---

### Post by gruszczy on 2009-04-22
I am using 9.04. Yesterday I have run an update and noticed, that compiz was updated. Today, when I run again my Ubuntu, all those cool desktop effects were lost. I run compiz-check, but really have no idea where to go from here.

compiz-check:
```

gruszczy@gruszczy-laptop:~$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: PCI ID 8086:2a02 detected. 

Would you like to know more? (Y/n) y

 Your particular graphics chip may be blacklisted on certain distributions.
 However that does not necessarily mean you will not be able to run Compiz.

 You can skip this blacklist -- but keep in mind that you did so.
 Do not complain if you encounter any problems with Compiz afterwards. 

Do you want to skip blacklist checks by Compiz? (y/N) n


```

---

### Post by gruszczy on 2009-04-23
Bump! Anyone noticed similar issues and found a solution?

Can it be related to my intel drivers?

When I run compiz --replace I got:

Checking for Xgl: not present. 

I tried to google that, but found nothing that helped.

EDIT2: It seems my driver was 'blacklisted', what this means in this context. The workaround was to skip checking something. But why was it working in the first place?

---

### Post by MeanEYE on 2009-04-23
Same graphic card, same problem...

---

### Post by MeanEYE on 2009-04-23
[http://ubuntuforums.org/showthread.php?t=1133874&highlight=intel+compiz](http://ubuntuforums.org/showthread.php?t=1133874&highlight=intel+compiz)

Take a look at this :)

---

