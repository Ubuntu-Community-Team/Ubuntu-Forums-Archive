---
title: "sync/copy hard drive"
date: 2009-05-03
forum: General Help
---

### Post by jchysk on 2009-05-03
Hi. I'm going out to Vegas for the summer and will be staying with a friend who has an almost identical computer (hardware) to me. Instead of bringing out my entire desktop I was just going to bring an external hard drive with all my stuff on it.
I have a brand new external hdd (still in the box) and was going to clone the hdd that is currently running my OS.
I'm pretty much just planning to take these steps and wanted to know if it should work. I don't see any flaws, but I'm not a pro at Linux.

Format the external to EXT3
Use rsync to clone the drive, to retain permissions and not deal with partitioning size issues.
Install grub on it.
Upgrade to 9.04.
Use the drive in Vegas.
Come back and format the original drive to EXT4.
rsync the external to the original

I'm currently running Ubuntu 8.10 64-bit. Another reason I wanted to copy everything before upgrading to 9.04 is to make sure everything I use works properly before completely switching over to it. Please let me know if there's something that won't work or if there's a better way to go about this. Thanks.

---

### Post by maheshasolkar on 2009-05-04
There's no way the part after coming back is going to work... what happens in Vegas, stays in Vegas!

Jokes apart, can you not try to use the external hard drive just with your computer, just like you would use with the friend's computer? You can try that before and after the upgrade.

If the transfer works one way, there are good chances that it would work the other way too.

---

