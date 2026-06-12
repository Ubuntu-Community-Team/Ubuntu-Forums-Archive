---
title: "UT2004 Installation Shared Between Windows and Ubuntu?"
date: 2005-08-21
forum: Gaming &amp; Leisure
---

### Post by talkingwires on 2005-08-21
Does anyone have a guide for running Unreal Tournament 2004 in Linux and Windows using a shared installation? The game takes up several gigabytes of space, and I'd rather not double that amount just to be able to play it in Ubuntu. I've got a shared FAT32 partition, but I'm not really sure where to go from there...

---

### Post by flying_icarus on 2005-08-21
Hi!

I tried something similar, installing linux version of ut2004 on a fat32 partition, and it didn't work. I didn't take too much time to look into it, but it seemed that the fat32 filesystem doesn't have "what it takes" to host and run linux binaries. 

So I'm fairly sure you won't have much luck, but if you get it working, let us all know! :)

---

### Post by Hairy_Palms on 2005-08-21
u sure fat32 is the problem? ive run enemy territory from an external fat32 hd before, are you emulating on the windows side with cedega? or on the linux side with cygwin?

---

### Post by talkingwires on 2005-08-21
[QUOTE=Hairy_Palms]u sure fat32 is the problem? ive run enemy territory from an external fat32 hd before, are you emulating on the windows side with cedega? or on the linux side with cygwin?[/QUOTE]Well, Epic provides native binaries for Linux and Windows, so there's no need for emulation. Linux support was one of the reasons I picked up the game in the first place...

---

### Post by evilghost on 2005-08-21
I'm an avid UT2004 gamer, why the requirement for playing UT2004 in Win32?  Why even bother with a shared installation or more specifically, why are you doing this to begin with?

---

### Post by talkingwires on 2005-08-22
[QUOTE=evilghost]I'm an avid UT2004 gamer, why the requirement for playing UT2004 in Win32?  Why even bother with a shared installation or more specifically, why are you doing this to begin with?[/QUOTE]
So, you're basically asking, "Why even bother booting into Windows at all?"

I prefer Ubuntu, but there's just some things that I need Windows for: Photoshop, Internet Explorer (Before anybody says anything, I do freelance web design work!), managing my iPod (still waiting for GTKpod to support Smart Playlists), and burning CDs (I got tired of making coasters with Gnome Baker). Often times, I just want to play a quick game and then get back to work. I don't want to have to reboot, pausing anything that may be downloading and closing all my applications, especially when the game runs fine under bother operating systems. But I'm not about to dedicate 11Gb of space for two seperate installs. That's ridiculous, and that's why I'm bothering with this.

---

### Post by fragmental on 2005-08-23
if fat32 isn't up to the task, there are ext2 drivers for windows.

---

### Post by talkingwires on 2005-08-23
Alrighty, I found a [solution](http://www.ataricommunity.com/forums/showthread.php?threadid=473668).

---

### Post by Maier on 2005-09-01
Good way to do it..

But i don't understand, why have the game in 2 OS's, when UT loads, you play it. You dont do graphics work at the same time.. so why not just keep it in 1 OS ?

just wandering :)

---

