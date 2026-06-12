---
title: "Can't boot into Jaunty!"
date: 2009-04-29
forum: General Help
---

### Post by PrimaryMaster on 2009-04-29
Last night i updated to Jausty. Today it booted up fine but when i clicked on Firefox, it showed up on the task bar and then disappeared. I checked the system monitor and firefox wasn't in the running processes. So i decided to use the package manager and reinstall all firefox components. After i did that it still wasn't working. I restarted the pc hoping it to initialize whatever and work.

Unfortunately now it doesn't boot into Ubuntu at all. I tried the recovery mode and the older kernel version with no success. The recovery option gives me this:

Begin: Running /scripts/local-bottom ...
Done.
Done. 
Begin: Running /scripts/init-bottom ...
mount: mounting /dev on /root/dev failed: No such file or directory
Done.
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init=bootarg.

Busybox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
[   3.504794] usb 4-1: configuration #1 chosen from 1 choice
.. same usb stuff blah blah blah...

and then :

(initframs)

What do i do now? I have lots of files that i need from my Ubuntu partition. I am writing on the same pc now from Vista. 

Please help. Thank you.

Cheers,
PM

---

### Post by Tipped OuT on 2009-04-29
Try booting into an older kernel bye pressing the esc key when it says so.

---

### Post by PrimaryMaster on 2009-04-29
Thank you but like i said above i already tried that. No go.

---

### Post by Kareeser on 2009-04-29
Primary, can you run this command?

```
cat /usr/bin/firefox
```

If the command comes up empty, reinstall firefox.

```
sudo apt-get install --reinstall firefox-3.0
```

---

### Post by PrimaryMaster on 2009-04-29
Thank you. Will try that and let you know. Though i don't think that the reason for not booting up is Firefox. There must be something else going on. How can Firefox effect the boot up?

---

### Post by Kareeser on 2009-04-30
Ah, my bad. I skimmed your post too quickly and assumed that your install was still working, and you were asking about getting Firefox to work again.

Disregard my post.

---

### Post by PrimaryMaster on 2009-04-30
Can anyone explain what is happening here:

Begin: Running /scripts/init-bottom ...
mount: mounting /dev on /root/dev failed: No such file or directory
Done.
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init=bootarg.

---

### Post by life4himsq on 2009-05-01
A friend just brought me an old 800Mhz with ubuntu 9.04 installed that was doing that. I searched around a short time, after not really finding anything I figured it couldn't hurt to just reinstall grub. I reinstalled grub by these instructions, [http://www.sorgonet.com/linux/grubrestore/](http://www.sorgonet.com/linux/grubrestore/) and that did it. The computer is back up and running good. I did the grub on a Kubuntu liveCD. Hope you can get yours going as easy as I did. If you have any questions, just let me know.

---

### Post by lmmendonza on 2009-05-21
> **PrimaryMaster said:**
> Can anyone explain what is happening here:

Begin: Running /scripts/init-bottom ...
mount: mounting /dev on /root/dev failed: No such file or directory
Done.
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init=bootarg.

I have the same problem.I am a beginner of ubuntu and so somebody please help me.i have some very important documents that have to be recovered.

---

