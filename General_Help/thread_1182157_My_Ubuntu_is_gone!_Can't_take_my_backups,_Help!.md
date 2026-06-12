---
title: "My Ubuntu is gone! Can't take my backups, Help!"
date: 2009-06-08
forum: General Help
---

### Post by Seregwethrin on 2009-06-08
[[IMG]http://img197.imageshack.us/img197/9762/08062009203.th.jpg[/IMG]]("http://img197.imageshack.us/my.php?image=08062009203.jpg")

I had ati driver which I've downloaded from ati.amd.com installed my ubuntu at the beginning by manually. Later I've uninstalled it to install graphic driver from software manager due to some video slowing down problems.

But the error at the picture happened. I cannot open my ubuntu. I can access it by ssh but I can't take my backups. When I opened a ubuntu from live cd, it does not see my user folder. Even I've tried to mv it and chmod it to 0777 with all subfolders and subfiles.

I'm trying to access my usb disk from ssh but I can't. I don't know enough to access flash disk from ssh. Just tried /mound /dev/sda1 /mnt for sda sda1 sda2 and sda5 and they all exists at dev folder but nothing more sda.

I need help to get my backups. Do you have any idea? Any ways to follow?

---

### Post by weblordpepe on 2009-06-08
Hi buddy.

You may want to try resetting the Xorg package to defaults (the X server's package).

When you SSH into your machine,run the following: ```
sudo dpkg-reconfigure xserver-xorg 
```
Then press CTRL-ALT-Backspace or reboot. That should solve the display issue.

As for the file / folder access problem you mentioned - I have no clue. It may be that you need to boot into your regular Ubuntu to see the folders. The output of the 'mount' command would be helpful. Try to get your system back up, and type 'mount'.

---

