---
title: "Broken filesystem after update"
date: 2006-09-14
forum: Desktop Environments
---

### Post by jmlude_93 on 2006-09-14
Earlier this evening I updated my Dapper 6.06 to the new kernel that was available (2.6.15-26-K).  Along with the kernel update, my Nvidia driver was also updated.  Everything seemed to go fine, and after it was finished installing, the update manager said that I needed to reboot.

After the reboot, I got this:

```

Uncompressing LInux... Ok, booting the kernel.

mount: Mounting dev/sda1 on /root failed: No such device
mount: Mounting /root/dev on /dev.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys/failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or direcotry
Target filesystem doesn't have /sbin/init

BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built in shell (ash)

/bin/sh: can't access tty; job control turned off

```

I have no idea what to do except to re-install.  I wanted to get the opinion of other people before I decided to do that.

---

### Post by linuxusr50 on 2006-09-14
Are you still able to boot back to your previous kernel by hitting ESC whe grub starts the boot?  If so, does everything work normally then?

---

### Post by jmlude_93 on 2006-09-14
No.

The Grub menu only displays the 2.6.15-26-K kernel.  No other kernel is displayed for Ubuntu.

I have two other OS's, and they both work fine.

---

### Post by linuxusr50 on 2006-09-14
Are you able to boot in to failsafe and get a terminal prompt?

---

### Post by jmlude_93 on 2006-09-14
No.

That was one of the first things I tried.

---

### Post by linuxusr50 on 2006-09-14
You might have a look at this thread.  Seems there are others that had the same issue.  Looks like this may be dapper bug related or a problem with your /etc/X11/xorg.conf file.

I am sure there is an answer, however I am at a loss for other suggestions at this point.

[http://ubuntuforums.org/showthread.php?t=185396&page=3]("http://ubuntuforums.org/showthread.php?t=185396&page=3")

---

