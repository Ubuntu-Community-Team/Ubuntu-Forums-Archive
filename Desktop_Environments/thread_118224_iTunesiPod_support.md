---
title: "iTunes/iPod support"
date: 2006-01-16
forum: Desktop Environments
---

### Post by tode on 2006-01-16
hi everybody.
i have a simple question: i'm a mac user, and i want to install ubuntu on my girlfriend's pc (she had a lot of problems with windows and i thoght that linux could solve most of them), but i saw that iTunes is not supported on this os, so i don't know how to give her a way to upload mp3s on her ipod.
is there anybody who could help me? i've tried to search in past topics but i can't load the search page.
sorry if someone alreafy asked this question.
thanks a lot.

---

### Post by kaamos on 2006-01-16
There are apps like banshee (very Itunes-like) and gtkpod (more of just a file manager) to transfer mp3s to an ipod. So this shouldn't be a problem.

---

### Post by tode on 2006-01-16
[QUOTE=kaamos]There are apps like banshee (very Itunes-like) and gtkpod (more of just a file manager) to transfer mp3s to an ipod. So this shouldn't be a problem.[/QUOTE]

thanks, tomorrow i'll try to install both on them, then i'll let you know if i solve this situation.
thanks again.

---

### Post by Jason-X on 2006-01-16
I didn't have much luck with Banshee. It was very unstable. 

I use Gtkpod to transfer mp3's to my iPod and it works really well. It doesn't automatically sync the new tracks in your library like iTunes does. You wil have to add them manually, but if you want to use Linux, Gtkpod is the best option. Heres a link to the guide for getting it working with Ubuntu:

[https://wiki.ubuntu.com/IPodHowto](https://wiki.ubuntu.com/IPodHowto)

Hope this helps:)

---

### Post by John Jason Jordan on 2006-01-16
[QUOTE=Jason-X]I didn't have much luck with Banshee. It was very unstable. 

I use Gtkpod to transfer mp3's to my iPod and it works really well.[/QUOTE]
I never tried Banshee, but I can second your opinion that Gtkpod works really well.

However, there are some other issues that the OP needs to know and which no one has mentioned:

1) There are people who claim to have been able to take a brand new iPod and format it properly using just Linux. From what I have observed, this is more myth than truth. A new iPod comes formatted with HFS, the Mac filesystem. Linux can sort of read this filesystem, but writing to it is not recommended. Windows can't handle it at all. When a Windows user plugs in an iPod for the first time the user is supposed to have installed iTunes first, and iTunes will pop up and offer to format the iPod for Windows. What it really does is it wipes out the hard disk in the iPod, formats it FAT32 (Vfat in Linux-speak), and reinstalls the iPod files (database, etc.). Linux has no problem with FAT32, so this must be done before using the iPod on a Linux machine. In other words, to use a new iPod on Linux you need access to a Windows 2000 (SP4) or Windows XP machine with iTunes installed.

2) You cannot just unplug your iPod from a Linux machine. Doing so is very likely to trash the filesystem. If that happens, go back to (1) above and start over. All tunes on the iPod will be lost, of course. Unfortunately, users (translation: ME) happen to be forgetful sometimes. Therefore, I strongly recommend you use Gtkpod to export the songs from the iPod periodically to the computer's hard disk, and to backup media from there. 

3) In order to avoid problems as in (2) above you must learn at least a bit about mounting and unmounting drives in Linux. It's not hard; you just have to learn a couple commands you can give from a terminal. In my case the command is "umount /media/iPod." There are other things I had to learn how to do when it refuses to unmount. Also things I have to do when it refuses to mount after being plugged in. The exact commands vary depending on the computer's configuration.

4) One final small note: You must have the iPod plugged in and mounted before launching Gtkpod. Otherwise Gtkpod will insist the iPod does not exist and you will go crazy unmounting and mounting it again trying to get Gtkpod to see it. It took me hours to figure that out. Oh, and Gtkpod is very nice, but when you click on Help you get a popup that says "Help files not implemented." It seems Linux programmers do not realize that finishing the programming means the job is only half done.

---

### Post by sergiolib on 2006-01-17
Another good app to transfer music to IPod and vice-versa (non open source, though) is Yamipod (Yet Another Manager for the Ipod). I haven't had any problemas with it and the developer likes to work a lot on it, because he releases updates very often. ;)

---

