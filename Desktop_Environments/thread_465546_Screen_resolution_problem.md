---
title: "Screen resolution problem"
date: 2007-06-05
forum: Desktop Environments
---

### Post by nicenick on 2007-06-05
Ok, completely frustrated now.

Ubuntu 6.06 LTS, PCChips A31G Ver 1.1 Motherboard, with built in SIS VGA. No External Video Card. Optiquest Q41 14" CRT VGA Montior.

System was perfect for 6 months, 1 week ago my screen resolution went haywire. The Ubuntu opening splash screen displays perfect ..loading this and that. Then when it comes time to display the Login screen, the monitor goes black and the monitor lamp goes fror green to yellow, the Ubuntu sound is played.  I press [ctrl] [alt] [+] one time and the monitor lamp goes from yellow back to green, but the screen is still black, then [ctrl] [alt] [+] again and an ubuntu log in screen appears but very distorted (1/2 screen wide and 2 screens tall) then [ctrl] [alt] [+] again. Now I get a clear log in screen but huge (2 screens tall and 2 screens wide)

Using [system] [preferences] [screen resolution] any choice other than 1280X1024 causes me to be thrown out of ubuntu, back to the login screen with a black screen and a yellow monitor lamp.

After trying many different things/advice from these forums. I finally gave up and reinstalled ubuntu from my live CD (which by the way has the same proboem now)

The new install does the same thing.

QUESTION: How is it the Ubuntu original splash screen knows how to display perfectly.
Question: When and where does Ubuntu decide to select a stupid screen resolution?
Question: Where can I find and edit that file to prevent it from doing so? 

I don't think it is a BIOS or driver or SIS problem because the SPLASH SCREEN IS PERFECT.
It seems to be something Ubuntu decides to change, and sometime last week after working for 6 months, it decided to do something different.

Someone HELP PLEASE

Nice Nick

---

### Post by nicenick on 2007-06-08
I installed a 3.5" floppy drive, go a WIN98 bootable diskette with Fdisk and format.
I deleted all partitions on my Ubuntu hard drive, I set up 1 continous FAT32 partition, I formatted the entire drive with Command.com for win 98.  I removed all other drives from the computer and rebooted.

Imagine my suprise when GRUB 1.5 tried to load, with error of course

Back to Win98 boot from floppy, executed this command, fdisk/mbr (master boot record).

Computer booted into WIN98 dos prompt.

Reconnected CD drive, installed ubuntu CD and did new install.  

Ubuntu now works fine and all my screen resolutions are back.

Don't know what the actual problem was, but I really had to get rid of everything to make it go away.

Nicenick

---

