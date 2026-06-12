---
title: "Black screen"
date: 2006-08-24
forum: Desktop Environments
---

### Post by Barbalbero on 2006-08-24
First a big "Hello!" to all, as this is my first post :) (and sorry for my english as i'm italian)

Now, i hope this is the right place to post, as i've a weird problem. I installed Ubuntu 6.06 about 2 weeks ago. No problems until now. I've just returned home from a small vacation, and on boot, i choose Ubuntu (from Grub, i've Windows XP on another parition), it shows the Ubuntu logo with all the loading lines (and "ok" at the right), but then it stalls, simply remaining black, after having fully loaded all things.

I've red some topic before posting, but the strange thing is that this is happened all of a sudden without touching nothing from the last time i've used it, and i've also tried a reinstall, but even the live session from the installation CD doesn't start anymore (never happened before with any live distro i've tried), showing me the same issue.

It's probably a video issue, i know that ATI cards (i've got a Radeon 9700 pro) have problems with Ubuntu, but i can't understand why it all happened so sudden, when some days ago all was fine...

Thanks in advance!

---

### Post by akniss on 2006-08-24
> **Barbalbero said:**
> First a big "Hello!" to all, as this is my first post :) (and sorry for my english as i'm italian)

Now, i hope this is the right place to post, as i've a weird problem. I installed Ubuntu 6.06 about 2 weeks ago. No problems until now. I've just returned home from a small vacation, and on boot, i choose Ubuntu (from Grub, i've Windows XP on another parition), it shows the Ubuntu logo with all the loading lines (and "ok" at the right), but then it stalls, simply remaining black, after having fully loaded all things.

I've red some topic before posting, but the strange thing is that this is happened all of a sudden without touching nothing from the last time i've used it, and i've also tried a reinstall, but even the live session from the installation CD doesn't start anymore (never happened before with any live distro i've tried), showing me the same issue.

It's probably a video issue, i know that ATI cards (i've got a Radeon 9700 pro) have problems with Ubuntu, but i can't understand why it all happened so sudden, when some days ago all was fine...

Thanks in advance!

Did it perhaps start shortly after an xserver update?  See this:
[http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)

---

### Post by Barbalbero on 2006-08-25
Thanks for the reply.

I tried sudo aptitude dist-upgrade, and my version of xorg is "1:1.0.2-0ubuntu10.4", but nothing changed.

But i saw that when all goes black, even the keyboard doesn't work (if i try to enamble caps lock nothing happens), so maybe it's more complex than a "simple" display issue...

The problem is that i can't even reinstall because the live session from the installation CD doesn't work....

---

### Post by FuriousLettuce on 2006-08-25
Does XP work?

---

### Post by Barbalbero on 2006-08-25
Yes, XP works flawlessly

---

### Post by FuriousLettuce on 2006-08-25
Does a live cd of another distro work? If so, can you use gparted to format the partition and reinstall from the disk? I know it's a drastic decision, but without seeing all your logs / config files it will probably be a fairly difficult fix.

---

### Post by Barbalbero on 2006-08-25
Yes, i thought that, i'll try. Thanks!

---

### Post by Barbalbero on 2006-08-25
Ok, now i'm typing from the Ubuntu installation CD, which only starts in safe graphics mode. But i wonder, starting the CD in normal mode behave like a "fresh" install? Because if it is so, i fear that even if i reinstall, the same thing will happen, given that the CD has nothing to do with anything i've installed on the HD, working on its own (i suppose).

---

