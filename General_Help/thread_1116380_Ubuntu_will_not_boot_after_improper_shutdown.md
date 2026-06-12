---
title: "Ubuntu will not boot after improper shutdown"
date: 2009-04-04
forum: General Help
---

### Post by tklaus on 2009-04-04
I recently was using Ubuntu and left my laptop for a little while to find that the battery had run out. Ever since then I have been getting the Minimal bash-like line supported message on the grub screen and that is as far as I can go when I am trying to boot Ubuntu. I have a dual boot setup with vista and vista works fine but I think the problems came from when it was shut down improperly because there are no changes that **[B]**[/B]I have made to either system.


I already posted in the absolute beginners forum but it was suggested I post here. This is the thread link for more information.

[http://ubuntuforums.org/showthread.php?t=1115523](http://ubuntuforums.org/showthread.php?t=1115523)

I need to be able to access Ubuntu somewhat soon because I have a project that I am working on that requires an X11 terminal window. I really appreciate the help.

---

### Post by SteveNorman on 2009-04-05
Me again ,looks like this is stumping a few people. 

[https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu)

best I can find. I would read through the whole thing and try all the options ending with a removal. Looks like it mentions some files you can check for. If you end up removing your wubi I would download and burn a live cd of the most ubdated stable 8.10 and use a cd install. When you do the cd install make sure you give ubuntu plenty of hard disk space. Later you can set up a partition for home and if you have any problems like this again your home folder will be safe.

edit your title to include "wubi" and maybe you can atract Ago's attention.

He is the one you want on this. You might try pming him

[http://ubuntuforums.org/member.php?u=9190](http://ubuntuforums.org/member.php?u=9190)

 but read his wubi guide first.

[http://ubuntuforums.org/showthread.php?t=396526](http://ubuntuforums.org/showthread.php?t=396526)


good luck

---

### Post by Yashiro on 2009-04-05
You've done a full disk check and repair from within Vista, right?

If you have actual data you need to save just boot using a live CD and do:
sudo mkdir -p /media/Windows
sudo mount -t ntfs-3g /dev/sda1 /media/Windows
sudo mkdir -p /media/root.disk
sudo mount -o loop /media/Windows/ubuntu/disks/root.disk /media/root.disk
gksu nautilus /media/root.disk

Fixing some of the paths if need be.

---

