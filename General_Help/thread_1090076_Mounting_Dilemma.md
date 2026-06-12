---
title: "Mounting Dilemma"
date: 2009-03-07
forum: General Help
---

### Post by humphreybc on 2009-03-07
Hi there,

So I installed ubuntu last week with the Wubi installer through Windows Vista, and I have been super happy with it since then. I worked out how to automatically mount my NTFS drives on startup using ntfs configuration tool and it's been good. Today I tried ripping an audio CD for the first time, and when I put in the disk, I realised that ubuntu didn't recognize my disk drive (there was nothing listed under places at all for it). It was there before hand, but not now... so I quit ubuntu and booted up Windows to rip the disk and to no surprise, windows media player crashed on me and I had to hard-restart the laptop.

I went back into ubuntu and during the boot process something came up saying it couldn't mount the boot disk because Windows had an unclean shutdown and the NTFS disks were still in use, so it suggested a command to force mount it, which I typed in and ubuntu booted. Then I tried mounting Local Disk and my other HDD, and it said "You are not privilaged to mount 'Local Disk' - even though I was admin. I tried to re-do it using NTFS config tool, but that just told me that Windows had had an unclean shutdown and something about refreshing the $LogFile. So I went back into Windows Vista and ran Ccleaner to wipe the system logs, and ran disk cleaner on C drive etc, then shutdown Vista (which took about 10 mins for some reason!)

I chose to boot ubuntu again and it wouldn't boot, gave me an error along the lines of "such and such has been mounted 24 times something-a-rather force mount" then it just sat there.

And that's where I am.... help please!

EDIT: Okay well I shutdown Vista after writing this and rebooted into Ubuntu to write down the correct error messages and, whaddya know, it fixed itself and booted fine and then it even mounted all my local disks perfectly like it was before... and now it's even going to rip my CD! Crazy... oh well i'm not complaining!

---

### Post by lindsay7 on 2009-03-07
Hi, I read your post and I happy you got this resolved. I have a question for you. I am relatively new to Ubuntu and as tring to learn as I go. I have a dual boot system with vista and ubuntu 8.1 on this machine which has two hard drives and two usbs connected to it. These all show up when I start ubuntu and I can access the forlders and files. The C: drive has vista, I sure it is ntsf, and Ubuntu on it with the file system that the install put on it. the F: drive is ntsf and both usbs are fat32.

So my question is why do you need to mount these doing something special? Am i missing something that I should be doing?

---

### Post by humphreybc on 2009-03-07
Hmm well if everything is working then there isn't really a concern for you! This is my file system:

160GB Local Disk (/C) with Windows Vista on it
160GB Media Disk (/D) with Ubuntu and a whole bunch of songs/photos and videos

Basically when I installed Ubuntu under the file system straight away Local Disk showed up with no problems, but I had to click it each time I started up to mount it. On the other hand, I couldn't find my music and photos on the same disk that Ubuntu was actually installed on, but then I found a way to do this by a command line that mounted it to /host
The ntfs configuration tool is just so that Ubuntu mounts my Local Disk on startup, therefore all the shortcuts I have to things like My Documents etc in my dock at the bottom of the screen have a place to go straight away on startup, without me having to manually mount the disk.

---

### Post by lindsay7 on 2009-03-07
As for most things in Ubuntu, there are a lot of subleties I just do not undrstand yet. It could be that since I have Ubnutu and vista on the same hard drive things act diffently and it could be that just these drives showing up under places/computer does not mean that they are indeed mounted until I use them. Anyway, thanks for the response.

---

### Post by humphreybc on 2009-03-07
That could be something to do with it! Yeah i'm in the same boat, I don't understand most of the stuff people tell me to do!

---

