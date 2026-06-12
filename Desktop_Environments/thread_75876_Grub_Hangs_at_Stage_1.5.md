---
title: "Grub Hangs at Stage 1.5"
date: 2005-10-14
forum: Desktop Environments
---

### Post by KrazyPenguin on 2005-10-14
I have 2 computers and Ubuntu installed on both.

NO WINDOWS!!!

My second computer Hangs at boot up.

It is an Asus P4P800.

"Loading.....

Stage 1.5"

Why does it hang for 30 seconds.
Everything else works great.
Thanks.

---

### Post by g14 on 2005-10-14
I get the exact same problem with breezy on my dual booting laptop except grub hangs forever. 

I have to boot from the breezy livecd, mount the local / partition, chroot into that partition, and run grub to reinstall the bootloader. I have to do this every time that I boot into windows.:(

---

### Post by KrazyPenguin on 2005-10-30
[B]Grub Hanging Problem Solved
[/B]

I don't know why this works, but this worked for me so maybe I can help somebody with the same problem. Maybe somebody that actually understands this Sh1T can translate this into english.

Anyway, here is what I did: (very EZ)

1) Boot Computer with Ubuntu CD.
2) Go through process until [!!] Disk Partition comes up.
3) Select Manual Partition
4) Breezy was on the 2nd partiton labelled Primary #2 and mounted as /media/hda2 with filesystem type ext3.
What I did was changed the Mount Point of Primary #1 from /media/hda2 to just "/".
5)Then I saved the settings.
6) Ignore the errors and continue the Ubuntu Installation.  It won't install so don't worry :???: 
7) Now click on "Install Grub"
8) My computer locked at 0% installation.
9) I turned off the computer.
10) It now boots perfectly.

11) HAPPY HAPPY HAPPY NICE NICE :D

---

### Post by NewbieNik on 2005-10-30
I had a similar problem with Hoary on certain disk controllers a while back. The easiest way round was to maually partition the disk and give a 500Mb-1Gb partition to /boot.
Other ways round were to specifiy the disk-controller options. Try looking in the menu list of boot options during the install, there are some tricky configurations in there that worked on various cards.

---

