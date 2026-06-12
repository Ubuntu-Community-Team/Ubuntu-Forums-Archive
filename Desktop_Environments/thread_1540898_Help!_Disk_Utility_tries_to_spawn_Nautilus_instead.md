---
title: "Help! Disk Utility tries to spawn Nautilus instead of Thunar"
date: 2010-07-28
forum: Desktop Environments
---

### Post by EdwardR on 2010-07-28
Hi, I'm actually running Mint 9 XFCE RC, but it is based on Xubuntu a fix that would work in Xubuntu should work in Mint XFCE also.

I am having an issue with Disk Utility.   When I use it to mount a partition, it creates a clickable link to the  location, e.g. /media/yourdrive, but when I click on the link, it tries  to run Nautilus to open the location and fails with the error message  Error Spawning Nautilus.  I don't have Nautilus installed on the  machine.  It is possible that when I was playing around after first  installing Mint I might have installed and subsequently removed  Nautilus.  Is there a way to make Disk Utility call Thunar instead of  Nautilus?  I did not see any sort of Preferences tab where I could  change settings.  I have tried removing and reinstalling Disk Utility,  but no luck.

thanks

Ed

---

### Post by EdwardR on 2010-08-04
I've been told that the new version of Disk Utility has Nautilus hard coded in.

---

### Post by kerry_s on 2010-08-04
> **EdwardR said:**
> I've been told that the new version of Disk Utility has Nautilus hard coded in.

so make a link to thunar.

sudo ln -s /usr/bin/thunar /usr/bin/nautilus

---

### Post by EdwardR on 2010-08-12
Thanks, I'll try that.  I assume this a command I will have to set to run each time I boot up?

---

### Post by EdwardR on 2010-08-12
That worked great, thanks!

---

### Post by Wisp558 on 2010-08-12
> **EdwardR said:**
> Thanks, I'll try that.  I assume this a command I will have to set to run each time I boot up?

Symlinks are quite persistent, the fix is permanent. Just as a note, you can pretend a file is another file all the time, and even whole directories! Symlinks are useful; for example, if you dual boot, you can point your Documents folder to your windows' My Documents folder and have a unified location. There are many possibilities, and the syntax is simple.

Also, since you fixed the problem, mark the topic as solved.

---

