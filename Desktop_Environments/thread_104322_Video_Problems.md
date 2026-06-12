---
title: "Video Problems"
date: 2005-12-15
forum: Desktop Environments
---

### Post by Progressive on 2005-12-15
I just downloaded Kubuntu 5.10 for my Sony VAIO FS Laptop. I dual booted it with Windows XP Home.

I am getting some video problems. Everything turns like static (as in television static) among other similar weird problems until I refresh the desktop, but then starts turning to static again.

Is that a driver problem? I am thinking it might be a booting/partitioning problem because I noticed somewhere in the static that the words "Windows  Saving System Settings" were clearly visible.

A side problem is that I havent been able to figure out how to set Windows back as the default in the boot loader or change the amount of time before it bypasses the selection process. I didnt have these problems with the Mandriva boot loader, plus it looked prettier. Maybe I should revert to the old boot loader?

A third problem is that when I set it to shutdown or restart, it gets almost all the way to shutting off or restarting, but does not actually do it.

Another thing you should be aware of is that I previously had Mandriva 2005 installed on the partition. It is possible that I did not format the partition correctly. Would all these be symptoms of if I wrote Kubuntu on top of the Mandriva partion without formatting first?

---

### Post by Sutekh on 2005-12-22
[QUOTE=Progressive]I just downloaded Kubuntu 5.10 for my Sony VAIO FS Laptop. I dual booted it with Windows XP Home.

I am getting some video problems. Everything turns like static (as in television static) among other similar weird problems until I refresh the desktop, but then starts turning to static again.

Is that a driver problem? I am thinking it might be a booting/partitioning problem because I noticed somewhere in the static that the words "Windows  Saving System Settings" were clearly visible.[/QUOTE]

Does it look like the picture in this thread (post #1) [http://ubuntuforums.org/showthread.php?t=104247]("http://ubuntuforums.org/showthread.php?t=104247")
If so, you'll need to install video drivers for you card, which is a ...?

[QUOTE=Progressive]A side problem is that I havent been able to figure out how to set Windows back as the default in the boot loader or change the amount of time before it bypasses the selection process. I didnt have these problems with the Mandriva boot loader, plus it looked prettier. Maybe I should revert to the old boot loader?[/QUOTE]

No, GRUB is fine.  It's easy to change these things.
First, backup the GRUB menu, then edit it
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
```
Then look for the line that has default 0.  This means that GRUB defaults to the first entry (GRUB starts counting at 0), just replace this value with that of your Windows entry.  For me it is 4 (Ubuntu - 0, Ubuntu Recovery Mode - 1, Memtest - 2, Other operating systems - 3, Windows XP -4) 

To change the timeout look for the line with timeout 10 and change it to the value you want in seconds.

[QUOTE=Progressive]A third problem is that when I set it to shutdown or restart, it gets almost all the way to shutting off or restarting, but does not actually do it.

Another thing you should be aware of is that I previously had Mandriva 2005 installed on the partition. It is possible that I did not format the partition correctly. Would all these be symptoms of if I wrote Kubuntu on top of the Mandriva partion without formatting first?[/QUOTE]

I'm not sure what's happening with the shutdown, restart thing.  When you installed Kubuntu, what options did you choose at the partioning step? Did you do it yourself or automatically?

---

