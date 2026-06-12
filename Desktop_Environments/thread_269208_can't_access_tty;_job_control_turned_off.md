---
title: "can't access tty; job control turned off"
date: 2006-10-01
forum: Desktop Environments
---

### Post by vurtualife on 2006-10-01
I’m getting a “/bin/sh: can't access tty; job control turned off” error when booting my Linux environment for the first time after installing Ubuntu. After reading some forums, it seems the issue is that I’m apparently running my shell on dev/console [ash] and need to instead run my shell on tty1 or ttys0.  Can someone possibly walk this Linux newbie through what commands I need to type at the shell prompt to switch from ash to tty1 [or if perhaps there's another work-around for this issue]?

 
Any feedback/suggestions would be great, thanks!

](*,)    :-k     :confused:**[B][B]**[/B][/B]

---

### Post by thingy on 2006-10-01
There are several posts on google and in launchpad which show situations where the user's computer is dropped into the BusyBox environment once the kernel is booted up.

1) Can you inform us what version of Ubuntu you installed!

2) Since you managed to install Ubuntu fine using the cds, I am assuming that the problem seems to be that the installer has setup your grub/lilo configuration incorrectly, such that either of these don't know where your root partition is.

3) In which case, can you please let us know how you had partitioned your installation of Ubuntu and what boot manager you are using, i.e. grub/lilo

4) Btw, can you confirm what type of installation you did...was it a server/standard/etc.


jc

---

### Post by vurtualife on 2006-10-01
I appreciate the feedback, thingy --

1) Installed version 6.06

3) Installed Ubuntu on a newly formatted drive, and allowed the installation to partition the drive using its default partition settings; Boot manager is GRUB


4)Standard Desktop install.


Hope this helps; let me know if you need further info.

:D

---

### Post by thingy on 2006-10-01
- What type of hard disks do you have installed in your system?

- Which disk is Ubuntu on and do you recall how it was partitioned? I think the default is a two partition scheme, one root and one swap.

- The reason I'm asking the above is that I'd like you to try specifying a boot time kernel parameter which tells the kernel where your root partition is. For example if your root partition is hda1, then enter the boot time parameter root=/dev/hda1   when the system startups and grub is loaded and it picks the kernel to boot.

- One last thing...can you get a hold of the 6.06.1 version of Ubuntu? It has a newer kernel + updates and hence it would be worthwhile to see if that resolves your issue.


- Also, is there anyway you get take a picture of your screen when you get this problem? There could be messages above that would indicate what the problem is. E.g. modules loaded in wrong order!

---

### Post by vurtualife on 2006-10-01
- MAXTOR DiamondMax 80GB [1 Hard Drive as Master]

- If I recall correctly, it is one root and one swap...


"For example if your root partition is hda1, then enter the boot time parameter root=/dev/hda1 when the system startups and grub is loaded and it picks the kernel to boot."

 - how exactly would I go about doing that? 

I double-checked the install and it seems I do have ver 6.06.1 installed...

Essenially what happens is when booting the machine, it gets to the screen with the "Ubuntu" logo on top, a progress bar towards the middle, and the on the bottom are the following comments:

Loading essential drivers...                  ok
Mounting root file system...
Waiting for root file system...

It hangs there for aboujt 5 minutes, then goes to a screen where I ultimately receive the error indicated above [title of thread].




Thanks again!

---

### Post by vurtualife on 2006-10-01
This is what is on the final screen:

kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
[Linux-bzImage, steup=0x1c00, size=0x15787d]
initrd /boot/initrd.img-2.6.15-26-386
[Linux-initrd @ 0x841000, 0x6ae351 bytes]
savedefault
boot
uncompressing Linux... ok, booting the kernel.
ALERT! /dev/hda1 does not exist. Dropping to a shell!!

BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built-in Shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty: job control turned off

#_

---

### Post by thingy on 2006-10-01
Hi

Don't have good news.

>  ALERT! /dev/hda1 does not exist. Dropping to a shell!!

This is the problem!

Here look at this thread:

[http://www.ubuntuforums.org/showthread.php?t=252578&highlight=ALERT%21+%2Fdev%2Fhda1](http://www.ubuntuforums.org/showthread.php?t=252578&highlight=ALERT%21+%2Fdev%2Fhda1)

Which is about the same issue as you. However, the fix being suggested is for you to download the alternate ubuntu install cd and use that to install ubuntu.


Looking at the forums, it seems ["A LOT" ]("http://www.ubuntuforums.org/search.php?query=ALERT%21+%2Fdev%2Fhda1+does+not+exist.&searchuser=&exactname=0&starteronly=0&childforums=0&titleonly=0&showposts=0&searchdate=&beforeafter=&sortby=&sortorder=&replyless=0&replylimit=0&searchthreadid=0&saveprefs=0&quicksearch=1&searchtype=0&exclude=&nocache=0&ajax=0&imagehash=&imagestamp=&")of people are having this issue and I still haven't come across a definitive answer as to what is going on.

Can you inform us whether you have any USB/Firewire hard drives plugged in to your system. Also, do you have anything like a USB Flash drive(pen device) or a SD/MMC/CF card plugged in? If any of the above is true, can you unplug/remove the item and try booting up.

I hope the alternate CD works out for you...else, to solve this is going to involve messing about with grub/the installed kernel/and the /etc/fstab file(at least). It will be difficult for anyone to talk you through the experimentation needed!

---

### Post by thingy on 2006-10-01
In my opinion, the desktop cd is a complete PITA and should be avoided! The partioning part of it is crap and I don't trust the installer either.

---

### Post by vurtualife on 2006-10-01
Thanks for all your feedback, Thingy...

I'll play with it some more, then try the alternate boot CD..

:)

---

