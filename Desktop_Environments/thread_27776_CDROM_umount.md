---
title: "CDROM umount"
date: 2005-04-17
forum: Desktop Environments
---

### Post by trash-can on 2005-04-17
Ok, this is kind of usabilyty problem. It is just weird that there is no easy way to umount CD-ROM media. It is really nice that there is such thing as autoumounting media, but hey, there is no option to umount CDROM when it is automounted, just Eject!!!  :confused:

Such a simple task as blanking CD-RW media and writing to it something else becomes not so trivial. I mean, ofcourse, i can always enter ```
sudo umount /dev/my_cdrom_device
``` but why should I?! There has to be Umount option!!! I am confused about what developers are thinking!

Oh, yeah, I wrote little Nautilus script to workaround this issue.

I wonder how and if someone else has noticed this problem and what is your solution?

---

### Post by TravisNewman on 2005-04-18
noticed the problem, but the solution I use is the one you specify-
sudo umount device

It's not clean cut by any means, but it works.

I wouldn't mind if there were a fix to this either ;)

---

### Post by tim1 on 2005-04-18
[QUOTE=trash-can]Such a simple task as blanking CD-RW media and writing to it something else becomes not so trivial.[/QUOTE]

It's the job of the burning tool to check if the disc is mounted and to unmount it. The nautilus-cd-burner does this, GnomeBaker aswell.

greets, tim

---

### Post by trash-can on 2005-04-18
[QUOTE=tim1]It's the job of the burning tool to check if the disc is mounted and to unmount it. The nautilus-cd-burner does this, GnomeBaker aswell.[/QUOTE]
Good point, tim! So far I used Graveman to burn CDs which was incapable of umounting CD(few times I got errors and writing failed, after umounting everything went smooth). Just checked out GnomeBaker. It is great!

Thanks for the tip!

---

