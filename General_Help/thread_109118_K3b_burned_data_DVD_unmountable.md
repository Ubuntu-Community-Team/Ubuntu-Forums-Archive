---
title: "K3b burned data DVD unmountable"
date: 2005-12-27
forum: General Help
---

### Post by Billquinn1 on 2005-12-27
I hope no one else is having trouble with this but I am having all kinds of trouble so here goes. 
When I burn a data DVD with K3b, it burns fine and seems to have finished without error. When I close the drawer right back it does not "see" the disk. CDs burn fine and I installed Nerolinux and burned it with that and it loads fine.
I tried to manually mount the disc and got this output:


> bill@ubuntu:~$ mount /dev/hdc
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

bill@ubuntu:~$ dmesg | tail
[4314478.051000] Buffer I/O error on device hdc, logical block 0
[4314670.138000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on is                                         a0060/serio0).
[4314670.138000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4314670.266000] atkbd.c: Unknown key released (translated set 2, code 0xaa on i                                         sa0060/serio0).
[4314670.266000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4314679.969000] hdc: media error (bad sector): status=0x51 { DriveReady SeekCom                                         plete Error }
[4314679.969000] hdc: media error (bad sector): error=0x34 { AbortedCommand Last                                         FailedSense=0x03 }
[4314679.969000] ide: failed opcode was: unknown
[4314679.969000] end_request: I/O error, dev hdc, sector 64
[4314679.970000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=1                                         6


The DVDs are not usable on windows either but I was able to use a program called isobuster to see what was there and the data is there and usable if I could get at it. I don't want to use nerolinux but thats all I can get to work for now.

---

### Post by ossi on 2005-12-27
Have you tried to do it with these dvds with the command line script manually?

---

### Post by Billquinn1 on 2005-12-27
No. I will have to figure that out. I have never tried to manually burn a disc. I'll work that out and give it a try.

---

### Post by Billquinn1 on 2005-12-27
OK. I burned the same data using 

> growisofs -Z /dev/hdc -R -J directory/

It burned the DVD without  any problem. Does K3b use this program to burn the disk or something else?
I upgraded to version 0.12.7 of K3b but this did not help.

---

### Post by runlevel0 on 2005-12-28
[quote=Billquinn1]OK. I burned the same data using 
  Does K3b use this program to burn the disk or something else?
I upgraded to version 0.12.7 of K3b but this did not help.[/quote]

It uses CDRDAO. AFAIK there is a plugin for proper DVD handling in K3B. Launch Synaptic and search for DVD. I can't remember how the package was called.

---

