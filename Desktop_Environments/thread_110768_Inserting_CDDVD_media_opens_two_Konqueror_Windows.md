---
title: "Inserting CD/DVD media opens two Konqueror Windows"
date: 2005-12-31
forum: Desktop Environments
---

### Post by sinbad782 on 2005-12-31
I have a problem with Kubuntu (with KDE 3.5) in that if I insert any media (cds or dvds) into the optical drive, I get two Konqueror windows popping up to browse the files and not one. 

The machine I have Ubuntu installed on was upgraded from Hoary to Breezy and includes the newest KDE packages. Does anyone have any tips on how to make this autorun type behaviour go back to normal (i.e. KDE should open only one window for file browsing)?

Thanks, PJS

---

### Post by sinbad782 on 2005-12-31
Looks like this HOWTO should answer it:

[http://www.ubuntuforums.org/showthread.php?t=90457](http://www.ubuntuforums.org/showthread.php?t=90457)

---

### Post by GeneralZod on 2006-01-01
If that doesn't help, do

```

ps -A | grep ivman

```

from the command-line.  If more than one instance of ivman is reported, kill the extra ones until only one remains.

---

