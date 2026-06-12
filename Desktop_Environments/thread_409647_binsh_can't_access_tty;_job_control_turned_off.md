---
title: "/bin/sh: can't access tty; job control turned off"
date: 2007-04-14
forum: Desktop Environments
---

### Post by brandon_r87 on 2007-04-14
Hello,

I'm getting a pretty big error during startup, as I can't even boot into the recovery command line.  I searched the forums and found other cases, but the other cases involved messed up menu.lst files, and I have double, triple, quadruple checked it and it is right.  I considered doing another install, but considering the amount of time I spent installing Kubuntu on dmraid, then fixing dmraid after upgrading to Edgy, I'm hoping someone will have a solution for me.  I'm not sure what kind of info to post other than this snippet of my startup:

```
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
Done.
Target filesystem doesn't have /sbin/init

BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands

/bin/sh: can't access tty; job control turned off
(initramfs)

blah blah blah

**and freezes after this line:** [17179578.884000] usb 1-5: configuration #1 from 1 choice
```

Thanks
Brandon

---

### Post by RaZer0r on 2007-04-14
this is the cause of an error in the kernel update last few days...
if you boot an previous kernel, you should be able to bootup, and I suggest you do an apt-update and apt-get dist-upgrade right away, this might solve your problem, if you fill in an bug report, the problems with the current .14 kernel is still under developement

---

### Post by brandon_r87 on 2007-04-14
Thanks for the quick reply, but my only other kernel option doesn't boot either.  I think this is because I didn't run update-initramfs on that particular kernel.  So I boot off a live CD and chrooted into my install.  I ran apt-get update and dist-upgrade, but no kernel packages were changed,  only kde and qt stuff.  I also ran update-initramfs on my old kernel to see if that would solve booting it.

The /bin/sh can't access tty; job control turned off problem was not solved and I now get the same error on the old kernel as the new one, which leads me to think that the update-initramfs I ran on it must be doing something wrong.  Also, it reports /sbin/init is missing in the filesystem, is this my problem?

---

### Post by Winters on 2007-04-16
Hi!

I had the same error but later I found out that it was due to my optical drive. I had an old LG cd-rom and for some reason it showed me that error. I bought another drive and it finally worked! I

---

### Post by brandon_r87 on 2007-04-17
Winters:
>  Hi!
I had the same error but later I found out that it was due to my optical drive. I had an old LG cd-rom and for some reason it showed me that error. I bought another drive and it finally worked! I

To be clear, this is not an error I get booting off the Live CD.  I can do that fine.  This is an error booting an existing install.

---

### Post by Winters on 2007-04-28
Sorry! my mistake!

---

