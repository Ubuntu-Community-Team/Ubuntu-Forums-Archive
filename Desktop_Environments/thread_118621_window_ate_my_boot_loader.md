---
title: "window ate my boot loader"
date: 2006-01-17
forum: Desktop Environments
---

### Post by paxmanchris on 2006-01-17
i have been working on a dule boot system.
i have 2 seprate phycical hard drives. on one drive i have 2 partition one with windows operating system, and one with ubuntu.
on the other drive i have all my storage stuff, my data, and my home directory.

my windows was acting up to the point where i needed to reinstall it. so i did on its partiton. but now the boot loader dose not come up. it just gos strait into window.

no important data was lost, its all programs i can just redownload. but i dont want to have to go through all of that again.

is there anyway around this?

---

### Post by ge77inhigh on 2006-01-17
U might have seected the wrong partion or your window needed more space so it delted ur ubuntu data. i would reformat the hd and try that shit again

---

### Post by otake-tux on 2006-01-17
windows always does that. whenever reinstalling, windows will override grub.  It just that. why? I dunno.  grub is in there its the configuration file that got messed up.  get a live cd (DSL or kannopix or the gentoo install), mount and cd into the directory with the ubuntu partition get into /boot/grub and write a new grub configuration file.

theres no need to reformat.  you can write a new grub configuration file.  I'll try to help as much as I can.

---

### Post by krismatth3 on 2006-01-17
If you've been using grub, just boot with a live CD and then run

# /sbin/grub-install /dev/hda

(Or /dev/sda if you're using a SCSI based system.)

Installing windows xp wipes out the master boot record on the primary hard drive. grub-install should restore that.

---

### Post by ahave2005 on 2006-01-17
It's more or less the same as krism, but have a look at the ubuntu wiki:
[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

/ahave

---

### Post by handy on 2006-01-17
This will give you more info' if you're hungry for it:

[http://ubuntuforums.org/showthread.php?t=114332](http://ubuntuforums.org/showthread.php?t=114332)

---

