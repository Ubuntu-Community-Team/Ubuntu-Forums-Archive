---
title: "Drive becomes write protected"
date: 2009-05-19
forum: General Help
---

### Post by DustinD on 2009-05-19
Hello everyone,

I just installed Jaunty-i386 on a new hard drive on Sunday. I have Hardy on my other hard drive that is still installed. I am using the BIOS settings to pick which HD boots. After I installed Jaunty from a DVD that I burned, I copied all of the .* files from my home/user directory from my old HD to the new one. When I go to access the old HD after booting the PC it asks me for my password, and then lets me in. My plan is to use the old HD as another backup location, and as a storage location for a bunch of old, mostly unimportant files that I don't want to transfer over.

After I rebooted the PC for the first time it complained about the permissions of my home folder, and told me it was ignoring the .dmrc file because of it. I ignored the problem at first, but after a few hours of computing FireFox locked up while surfing. Actually it just refused to do most things, like load web pages when I opened a new tab. I checked my uTorrent program that was running under wine to see if my internet was up. It was up, but there was an error message next to a torrent that had been downloading that said "Error: Disk is write protected". I could not fix the problem, so I rebooted, took the error message on boot up seriously, and changed the permissions on my home/user folder to 644 like it asked me to. That boot-up error message never came back.

Later, after a few hours of happy computing many things did not seem to want to work or load, and all of the files in my Jaunty HD had a locked icon on them. The other HD was fine and unlocked. I rebooted, and then it happened again a few hours later. Each time after a few hours of running just fine, the Jaunty HD suddenly ends up write protected for seemingly no reason.

The only things I can think of for a reason why is the fact that both HDs have pretty much the same stuff, partitions, and users on them, maybe that is causing a conflict? They are both still boot-able.

While reading about problems involving write protection errors someone mentioned that having "view hidden files" turned on could cause drives to write lock, is there any merit to that idea? It makes no sense to me. I have however, had it turned on each time the problem happened.

Could it be a permissions issue with the /dev/sd* files? Who should own them, and what should the permissions be? Right now it is root:disk 660

I forgot to say that the new drive is ext4, the old one is ext3.

I hope that was enough information without getting too long winded, thank you all for any help you can give me.

---

### Post by geraldvillorente on 2009-05-19
change the permission to 755 or 777

or

chown the source drive to root

---

### Post by DustinD on 2009-05-20
I did like you suggested and changed all of the sd* files to 755, but it happened again. Everything in my /home section which is a ext4 partition and file-system had normal permissions, but it still went write protected about a half hour before I got home from work according to my torrent download logs. 

I tried to use the following command after it went write protected this time, and this is the message I got: 

dustin@dustin-9:/$ sudo chmod 777 home
chmod: changing permissions of `home': Read-only file system

I was still able to play with the /dev/sd* files without any trouble.

After I rebooted I changed /home from 755 to 777 and back again without any trouble using the same commands.

So does anyone know why my /home file system is turning read only on me? It takes roughly 24 hours +/-4 each time, and happens whether I am actively using the computer or not.

thank you again for your help.

---

