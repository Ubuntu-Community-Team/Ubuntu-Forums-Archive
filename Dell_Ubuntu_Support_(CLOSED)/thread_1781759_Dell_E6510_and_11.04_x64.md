---
title: "Dell E6510 and 11.04 x64"
date: 2011-06-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nair on 2011-06-14
I just ripped a 11.04 x64 CD and attempted to install Ubuntu on this Dell E6510.  I got a black screen, which I remember getting a year ago when I installed 10.04 x64 on this machine.  Is this the same issue with the graphics driver where you have to enable some proprietary graphics driver in order to see anything?  I think the code for it went something like:

modeset.nouveau=0

I can't remember exactly where that code goes because I haven't dealt with it in a year.

If I remember also, fiddling with this graphics driver disables the user from booting off of a live CD or thumb drive, or maybe it just makes it inconvenient, I don't know.  Regardless, before I ripped the CD, I checked these forums to see if anyone reported problems with 11.04 on a Dell E6510 already, since there were so many problems/failures with 10.04 on the Dell E6510.  I never found any problems on these forums, so maybe I am just doing it wrong.  Am I the only one experiencing this problem with 11.04 x64?  And by the way, was any other work around found for the problem with 10.04?

It's probably all the same problem as it was a year ago, and it probably requires the same workaround with the proprietary graphics drivers is my guess.

---

### Post by nair on 2011-06-14
I got 11.04 x64 installed and running on this e6510.  I followed the same steps I followed last year with 10.04 x64.  I found the thread here: [http://ubuntuforums.org/showthread.php?t=1509957&page=2](http://ubuntuforums.org/showthread.php?t=1509957&page=2)

The steps they outlined which helped me were:

> Pre-Install:

1.Boot from the CD and hit any key to get to the menu screen.
2.At the install screen press "F6", "Esc", and delete "quiet" and "splash" from the command line. 
3.Add "nomodeset" at the end of the line.
4.Press "Ctrl" and "X" to boot.
5.Install Ubuntu

Post-Install:

1.During boot hold down the shift key to get to the grub menu.
2.Press the 'e' key to edit the boot command
3.Use arrow keys to move to end of line, and delete "quiet" and "splash" from the command line.
4.Add "nouveau.modeset=0" at the end of the line.
5.Press "Ctrl" and "X" to boot.
6.Go to System - Hardware Drivers and install the Nvidia proprietary drivers.
[...]
8.RebootOne thing to note--I did not yet attempt to install the proprietary graphics drivers, because I have another problem I want to solve first.  I cannot figure out how to save my changes to the grub boot command.  I figured out how to edit grub 2 while booted into Ubuntu using the following code in the terminal:

```
sudo gedit /etc/default/grub
```Unfortunately, the file that comes up in gedit looks completely different from the more simple boot command screen I saw when I pressed "e" (which I pressed while looking at the grub 2 screen itself).  Does anyone know how to implement the changes described above in that quote...AND make them permanent?  My changes are resetting between each reboot.

PS: For some reason, I don't remember having to solve this problem last year with 10.04 and grub 1.98.  Did grub 1.99 change the way to save changes?

---

### Post by KaridaSerious on 2011-06-22
Edit /boot/grub/grub.cfg perhaps? I have the same kind of problem, cannot install nvidia drivers and the desktop is very laggy eg. scrolling a web page goes 1 fps which is extremely annoying.

---

