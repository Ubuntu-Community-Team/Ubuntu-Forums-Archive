---
title: "Windows and GRUB"
date: 2007-09-18
forum: Desktop Environments
---

### Post by snipazer on 2007-09-18
Hey everyone, kinda new to ubuntu. This is my second ubuntu install. I have a problem though. I had Vista on a partition when I installed Fiesty. Fiesty doesn't recognize Vista as a bootable partition. It won't let me boot back into windows. Is there a way for me to get back into that without installing a third party boot manager? Thanks

---

### Post by matthew.lns1 on 2007-09-18
I don't think so. GRUB works great for me.

---

### Post by arkara on 2007-09-18
thats weird...
try to pop in vista cd. and boot from it.
go to the recovery console and type fixmbr
this will make vista bootable and linux not bootable

now popin the ubuntu live cd and boot up
when it loads go to the terminal and type

sudo grub

it will ask you for a pass..((i think)type in the root pass if you have one)

then in the grub>  

type find /boot/grub/stage1

it should see sth like (hd?,?)

?=numbers

then type 

root (hd?,?)

and then
setup (hd?)

and then exit
and then reboot
this should fix it(i think)

---

### Post by snipazer on 2007-09-18
> **arkara said:**
> thats weird...
try to pop in vista cd. and boot from it.
go to the recovery console and type fixmbr
this will make vista bootable and linux not bootable

now popin the ubuntu live cd and boot up
when it loads go to the terminal and type

sudo grub

it will ask you for a pass..((i think)type in the root pass if you have one)

then in the grub>  

type find /boot/grub/stage1

it should see sth like (hd?,?)

?=numbers

then type 

root (hd?,?)

and then
setup (hd?)

and then exit
and then reboot
this should fix it(i think)

Do you have a link to a tut or something? Thanks

---

### Post by Rupertronco on 2007-09-18
Using the Windows disc to restore it's bootloader to the MBR (which is what was suggested in the above post) will permit you to boot only into Windows. It is possible to use the Windows bootloader to boot Linux, however I do not recommend this approach. I would use GRUB, it will boot both operating systems just fine. 

The commands posted above will restore GRUB to your MBR. My recommendation is to use this procedure as it will allow you to boot both operating systems without any trouble. A link supporting this process can be found [here](apcmag.com/dualboot). 

Also if you are unfamiliar with GRUB I would suggest you look at some documentation on it. It's very easy to use and the steps posted above will work just fine. 

The question marks in the post above referr to the hard drive number and partition number your linux install is on. hd(0,0) would be HDD 1, Partition 1. Keep this in mind, many people forget GRUB starts counting at 0. If your linux partition is partition 3 then it will be root(0,2) for example.

---

### Post by snipazer on 2007-09-18
Thanks, that clears up a lot of confusion.

---

### Post by tsumiro on 2007-09-19
i once had a problem like this, but it would bring up the boot selection screen and i couldnt change which one i wanted to boot. u cant use a usb keyboard, but by the sounds of it, thats not your problem... sorry, i didnt fully understand this question, but if your havin the same problem i was havin, then changin the keyboard to use a scsi is how to fix....


yeeeahhhhhhh....

---

