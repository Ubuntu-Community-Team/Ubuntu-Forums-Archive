---
title: "Emulator or Dual Boot for Windows Games?"
date: 2006-07-29
forum: Desktop Environments
---

### Post by Technosexual on 2006-07-29
I have recently bought a new computer, and instead of using Windows XP like I had before, I installed Dapper Drake. I have found Ubuntu programs to replace all the Windows ones I am used to, such as OpenOffice, Gaim and GimpShop. The problem Im having is trying to decide if I should get a program such as Cedega to try and run my games (with the monthly fee), or make a windows partition just big enough for my games. I have quite a large collection of games, some of which do not run on Cedega, so Im leaning towards the idea of a dual OS system. There are also many other Windows emulators that I could try, but none are completely successfull. If anybody has any ideas of the fastest and easiest way to make Windows games easily playable (smoothly), whether it be an emulator suggestion, or a dual booting method, please reply.

---

### Post by Krank on 2006-07-29
I'd recommend dual-booting. Cedega never agreed with me or my games, so these days I just run Wine when I can. Mostly becuse the games I run are mostly old ones...

Anyways, Wine/Cedega has so many issues it's not even funny. I'm certain the Wine team are doing the best they can, but so far it's not really production quality when it comes to games.

So, depending on the heaviness of your machine and its specs, I'd recommend either dualbooting or something like VMware (which emulates the entire system, slower than normal).

---

### Post by nemin on 2006-07-29
I'd definatly advice a dual boot system for your situation. It isn't hard to set up, and this way you'll be able to play *all* games you want. Emulators will slow down your games and won't be able to run all of them. Moreover, I think most graphics cards just perform better under windows.
A dual boot situation will only use some more disc space.
Good luck!

---

### Post by Technosexual on 2006-07-29
Yes, I think dual booting would be the best solution, esspecially since Im going to be running mostly new games that use quite a few resources. My system is quite fast, and could probably run everything under an emulator, but I would hate to see the power go to waste. Anyways, I have never made a dual boot system, and have only installed operating systems on 4 separate ocassions, so I dont know where to start. Are there any techniques to set things up to increase the speed of OS switching? or is it just the standard routine of installing the different OSs in separate partitions and editing the master boot record?

---

### Post by Lord Illidan on 2006-07-29
> **Technosexual said:**
> Yes, I think dual booting would be the best solution, esspecially since Im going to be running mostly new games that use quite a few resources. My system is quite fast, and could probably run everything under an emulator, but I would hate to see the power go to waste. Anyways, I have never made a dual boot system, and have only installed operating systems on 4 separate ocassions, so I dont know where to start. Are there any techniques to set things up to increase the speed of OS switching? or is it just the standard routine of installing the different OSs in separate partitions and editing the master boot record?

It's quite easy. Just install the different OSs in seperate partitions, then edit the mbr. 

Usually we install windows first on say, half or third of the harddrive, and then use the other half for linux.
For example, if you have a 100 gig harddrive, leave a 30-50 gig for Windows, NTFS or FAT 32.

Then, make a 20 gig for Linux.. the / partition.
Then the rest make it the /home partition for Linux.

In your case you could try to resize your partitions using the live cd..but sometimes the windows cd gets picky because it wants to install in the first primary partition.

---

### Post by Technosexual on 2006-07-29
I was thinking of just getting a second hard drive for windows. I have a 100gb for ubunutu now, and a 60 should be more than enough for games.

---

### Post by Lord Illidan on 2006-07-29
Good idea. That way you won't need to fiddle with partitions. If you install windows, be prepared to re-install grub, a very short process.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Technosexual on 2006-07-29
Hmmm, would this create a simple selector? And then default to a certain OS after a certain timer period? Or would I need something like BootMagic?

---

