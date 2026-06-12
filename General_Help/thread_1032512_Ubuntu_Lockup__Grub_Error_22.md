---
title: "Ubuntu Lockup / Grub Error 22"
date: 2009-01-06
forum: General Help
---

### Post by TransplantedCanuck on 2009-01-06
Hi,

In my ever continuing saga of Ubuntu Epic Fail vs The Boyfriend...

Today's wonderful Ubuntu activity:

All the open programs in Ubuntu turned gray and crashed one after the other over the course of a few seconds. My girlfriend attempted to reboot and an error message that said something about Ubuntu being unable to safely Quit/shutdown.

She rebooted manually and grub hangs at stage 1.5 with the Error 22....

how can I fix it or do I need to reinstall Ubuntu again? 



I apologise for the bitter tone, its been a long frustrating day and Ubuntu is constantly causing me problems (weekly). Usually somewhat more minor. Sadly for me, the girlfriend prefers Ubuntu, but she doesn't have to try and keep it running.

---

### Post by TransplantedCanuck on 2009-01-06
Ah, just thought of a few more points:

This is not a dual boot system, pure straight-up Ubuntu.
There are 2 harddrives in the system
There is no RAID

Feel free to be "technical" with me, I'm only a linux noob, not a computer world noob.

---

### Post by lgeek on 2009-01-06
well, your girfriend definetly has a good taste.u can use a live ubuntu disk to reinstall grub.boot from the live cd or dvd.open a terminal.type
sudo grub
u will enter in the grub command line
then type
root (hd a,b) 
"where 'a' is the physical hard disk numb most probably 0 if u have only one hard disk or u can press tab after hd and check.'b' is the partition number in which ubuntu is installed or again press tab to find the number.
then type
setup (hda)
quit

now reboot. that's all.

---

### Post by TransplantedCanuck on 2009-01-06
Thanks for the response, one more question before I go ahead with trying that...

How can I open up a display of which drive is which from the live CD... I don't remember which one is which within ubuntu anymore.



TBH, I know she has good taste, I just find Ubuntu/Linux terribly frustrating for me, as I don't have the time to learn it, I just have to fix it.

---

### Post by Herman on 2009-01-06
EDIT: You can look at your hard drive and see your partition numbers with Gnome Partition Editor, in the Live CD.

> All the open programs in Ubuntu turned gray and crashed one after the other over the course of a few seconds. My girlfriend attempted to reboot and an error message that said something about Ubuntu being unable to safely Quit/shutdown.
She rebooted manually and grub hangs at stage 1.5 with the Error 22....
how can I fix it or do I need to reinstall Ubuntu again?  There's a fair chance you're having some kind of hardware problems by the sounds of things.

I agree with lgeek, (above), re-installing GRUB sometimes does fix GRUB Error 22, but not in every case, only when GRUB Error 22 has been caused by having your partition numbers accidentally changed, usually by hard disk partitioning software.

Another cause of GRUB Error 22 means:> 22 : No such partition
This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk. I would suggest booting your Ubuntu Live CD and opening Gnome Partition Editor, (System--> Administration --> Partition Editor ), and take a look at your hard drive.
If it's healthy it will be a normal color and you can right-click on your Ubuntu partition and click 'check', 'apply', apply', and let GParted run a file system check on it for you. That might fix it. 
Be sure to take a look at the report of what happened by clicking the arrow buttons for the drop-down pages. It may give us some clues to help identify the problem.
If your partition/partitions have a black box around then, that's a bad sign, but you can probably still fix them.

Another thing I think you should do, is open a terminal in your Live CD, and run a badblocks check to make sure your hard drive is okay.
Do something like:
```
sudo badblocks -sv /dev/sda1
```Where: /dev/sda1 is the partition to be checked. Replace this number with your own partition number which you should know from reading the output from 'sudo fdisk -lu', or by looking with Gnome Partition Editor.

If your hard disk has bad blocks, you will be given lots of numbers. Your hard disk probably should be replaced very soon!!!
A 'bad block' is an area of your hard disk where the material is losing it's ability to retain a magnetic field and thus store data reliably. There are spare sectors in your hard disk when it is new, which the hard disc will swap out silently when badblocks develop due to imperfections and deterioration of the materials. It's only after those spare sectors have been all used up that bad blocks start to become apparent to the file system. When that starts to happen, your hard disk is getting close to the end of its useful life.

Here's what you should see when it's finished if your hard disk has passed.
```
sudo badblocks -sv /dev/sda1
Checking blocks 0 to 12908226
Checking for bad blocks (read-only test):done
Pass completed, 0 bad blocks found.
```Good luck,
Regards, Herman :D

---

### Post by TransplantedCanuck on 2009-01-07
Thanks again for the replies, I'll take a look at that tonight. Sadly I'm leaning in Herman's direction... the harddrive may only be 6 months old, but I find it tricky to believe that GRUB would simply spontaneously combust on me.


If it is the HD, then I'll probably end up having to wipe it out and start over. 

Maybe i'll use this as a chance to build the girlfriend a new machine, theres got to be something strange somewhere with the hardware that causes her install of linux to be terribly unstable...


Anyway, I'll post later with results/feedback

---

### Post by Herman on 2009-01-07
Maybe you should take a look at the voltages from your power supply too, it might not be the hard drive's fault. You should be able to go into your computer's BIOS and find somewhere you can go and read your voltages, fan rpm, temperatures and so on. I have [lm-sensors]("http://ubuntuforums.org/showthread.php?t=2780") installed in my Ubuntu system, so I just need to type the command 'sensors' for a quick check on things like that. Of course, I have to have Ubuntu booted first though.
If your hard drive isn't getting the proper voltage it can't do it's job properly. Just try a few tests and experiments to try to determine and prove where the source of the problem is. 
I have 'fixed' computer hardware sometimes just by unplugging it and plugging things and plugging them back in again, (after cleaning usually). Sometimes, due to thermal expansion and contractions, parts can work loose or dirt can work its way in between contacts, hard drive cables are not really prone to that kind of probelm though, a few other parts can be, depending on the design of the hardware. It doesn't cost anything to unplug and re-plug something though, it's always worth a try, try a different power plug if you have another one spare that will reach.  Make sure the plug from the power supply is pushed all the way 'home' in the hard drive's socket. Maybe you think I'm being silly, but it's surprising how often even the professional computer makers and repairers make stupid, basic mistakes. No humans are perfect all the time. :D

> If it is the HD, then I'll probably end up having to wipe it out and start over. If it is the hard drive, rescue your data from it if you possibly can, and replace it. You can keep your faulty hard drive on a shelf or in a drawer, but make sure you mark it as 'faulty' and never use it ever again. Hard drives are cheap compared with the work you put into your data. Most people's data is worth more than any hardware. Some is irreplaceable. It's not worth messing around with a hard drive that even might be faulty, better to remove it.

---

### Post by TransplantedCanuck on 2009-01-07
> **Herman said:**
> Maybe you should take a look at the voltages from your power supply too, it might not be the hard drive's fault. You should be able to go into your computer's BIOS and find somewhere you can go and read your voltages, fan rpm, temperatures and so on. 

Not a bad idea, I could picture it being the power supply, even though its not THAT old...


> **Herman said:**
> 
 Maybe you think I'm being silly, but it's surprising how often even the professional computer makers and repairers make stupid, basic mistakes. No humans are perfect all the time. 

As a network engineer I always start at layer 1 (physical connectivity)... its the only way to stay say when you go on a consulting job at a completely crazy undocumented customer network.


> **Herman said:**
> 
If it is the hard drive, rescue your data from it if you possibly can, and replace it. You can keep your faulty hard drive on a shelf or in a drawer, but make sure you mark it as 'faulty' and never use it ever again. Hard drives are cheap compared with the work you put into your data. Most people's data is worth more than any hardware. Some is irreplaceable. It's not worth messing around with a hard drive that even might be faulty, better to remove it.

Truth. Just eating, will get started next.



edit: crap, forgot the CD drive is dead (its been dead for months... I'm lazy techsupport...) so no live-CD... debating right now if I just want to order a new DVD drive and hope I can fix it after that, or if I take a bit more time and put together a whole new box, hopefully one with less problems than the current one....

then maybe I might start to like ubuntu...

---

### Post by TransplantedCanuck on 2009-01-17
running a disk check fixed the problem. Cheers mate!

---

### Post by Herman on 2009-01-17
:) Okay! Cool! I'm happy for your that it turned out the easiest and cheapest fix was the one that worked. 
Regards, Herman :)

---

