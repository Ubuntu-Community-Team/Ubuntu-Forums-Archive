---
title: "General Questions"
date: 2005-04-09
forum: Desktop Environments
---

### Post by Misagh on 2005-04-09
Hi all, 
Well, I seem to have installed my first linux distro without any problems.
I'm very impressed by how easy Kubuntu is to use.
I just have a few questions for you very helpful people  :-D  :

1. Is there any way I can assign a root password to gain access to root or log in as root? I was never asked to do this during installation of Kubuntu!
2. I have side buttons on my mouse, and in windows I can use these to go backwards and forwards while browsing the internet or just exploring the contents of a hard drive. Is it possible to set these up in Kubuntu too? They just work in windows, never needed to install drivers or anything.
3. I am trying to play a film, its in .avi format, through kaffiene. I have managed to get the sound and video to work fine. However, the film has subtitles which are supplied in a .txt file, but the subtitles don't show. How can I fix this?
4. Do you know of any sites where I can get some hints and tips for beginners who want to learn to use linux? As easy as Kubuntu was to install and run, its obvious that actually using it is only the start, and its pretty daunting, as I don't really know what most of this stuff does. I'm going to pick up a copy of 'linux for dummies' next chance I get, as I hear its quite good!

Thanks all!

---

### Post by bored2k on 2005-04-09
1. Enable a root passwd with sudo su. [http://www.ubuntulinux.org/wiki/RootSudo/](http://www.ubuntulinux.org/wiki/RootSudo/)
3. Download VLC, and select the subs manually.
4. [http://ubuntuforums.org/forumdisplay.php?f=58](http://ubuntuforums.org/forumdisplay.php?f=58) ; [http://ubuntuguide.org/](http://ubuntuguide.org/) ; man command (in a terminal).

---

### Post by Misagh on 2005-04-09
Great, thats really helpful, thank you!
I followed the instructions for the whole root thing. I think it works.
I was wondering if there was any way I can actually log in as root in the gui, eg, when I start up Kubuntu and have to log into my user account. Is there any way to log into root rather than into my user account.
The reason i ask is that I managed to mount my spare fat32 hard drive, (i cant take credit, i just looked through the forums and found someone else who had posted how to do it :p). However, I can only view the files on the fat32 hdd, I don't have the permission to modify them.
I just thought that If i could log in as root, I would be able to change the permissions so that i could view+modify the files while logged in usually!

---

### Post by sjalex on 2005-04-09
Once your root password is set you should be able to login as root. However, that should not be necessary.

You can change your /etc/fstab to fix your access problem: (as root) edit the file so that the line containing the entry for your FAT32 partition has "users" in the options column (fourth column) and remount and you should be in business.

That should give whichever user mounts the partition default permissions.

---

### Post by dermotti on 2005-04-10
I belive its KDM thats preventing you from logging in as root. I would like to know how to change that as well...

---

