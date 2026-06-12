---
title: "Windws and Ubuntu 2 harddrives."
date: 2005-12-29
forum: General Help
---

### Post by mztriz on 2005-12-29
I have two computers one is windows with 18gb harrdrive and the other is 160gb with ubuntu. What I would like to do is take the 160 out of it's current computer and put it in with the windows computer. What would I have to do to get it to boot correctly?

---

### Post by DaMasta on 2005-12-29
Set the jumper accordingly. I have mine with linux as the master and windows as the slave. You'll have to edit grub to boot to the windows drive.

---

### Post by mztriz on 2005-12-29
[QUOTE=DaMasta]Set the jumper accordingly. I have mine with linux as the master and windows as the slave. You'll have to edit grub to boot to the windows drive.[/QUOTE]
how do I edit the grub? and should i edit it before i put it in the other computer?

---

### Post by Juergen on 2005-12-29
DaMasta was a bit short I think :-)

You have to modify /etc/fstab and /boot/grub/menu.lst to your new device-id.
Probably change hda to hdb and hd(0,x) to hd(1,x).

Change jumpers and then put the drive in its new home.

Then you need to boot from a live-CD and install GRUB to its new home.
So:```
mount /dev/hdb1 /mnt
chroot /mnt
/sbin/grub-install
reboot
```
I don't know if this generates a 'Windows' entry in your menu, so you might have to add that - should be easy to find examples here (or in google)

---

### Post by mztriz on 2005-12-29
[QUOTE=Juergen]DaMasta was a bit short I think :-)

You have to modify /etc/fstab and /boot/grub/menu.lst to your new device-id.
Probably change hda to hdb and hd(0,x) to hd(1,x).

Change jumpers and then put the drive in its new home.

Then you need to boot from a live-CD and install GRUB to its new home.
So:```
mount /dev/hdb1 /mnt
chroot /mnt
/sbin/grub-install
reboot
```
I don't know if this generates a 'Windows' entry in your menu, so you might have to add that - should be easy to find examples here (or in google)[/QUOTE]
Ok, I will try that shortly.
Thank you!! :D

---

### Post by Juergen on 2005-12-29
Grmbl. Those Debian-Scripts....

Be sure to edit the **commented** parts of /boot/grub/menu.lst
And before running 'grub-install' run '/sbin/update-grub' - that might even create the 'Windows' entry

Check It!!

---

### Post by mztriz on 2005-12-29
[QUOTE=Juergen]Grmbl. Those Debian-Scripts....

Be sure to edit the **commented** parts of /boot/grub/menu.lst
And before running 'grub-install' run '/sbin/update-grub' - that might even create the 'Windows' entry

Check It!![/QUOTE]
Ok I will thanks again.

---

### Post by mztriz on 2005-12-29
I'm scared I'm going to mess this up so...
in fstab i should do this...```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```
that hda becomes hdb?

---

### Post by DaMasta on 2005-12-29
I always bump my cdrom drives to the second channel. Right now I have three hard drives and a cd writer. I have linux set to /dev/hda, windows set to /dev/hdb and my mp3 drive set to /dev/hdc while my cd writer is set to /dev/hdd. It all depends on how you set it up. However, if you change you linux drive to /dev/hda, make sure you switch that /dev/hdc1 to /dev/hda1 and /dev/hdc5 to /dev/hda5.

---

### Post by mztriz on 2005-12-29
[QUOTE=DaMasta]I always bump my cdrom drives to the second channel. Right now I have three hard drives and a cd writer. I have linux set to /dev/hda, windows set to /dev/hdb and my mp3 drive set to /dev/hdc while my cd writer is set to /dev/hdd. It all depends on how you set it up. However, if you change you linux drive to /dev/hda, make sure you switch that /dev/hdc1 to /dev/hda1 and /dev/hdc5 to /dev/hda5.[/QUOTE]
I'm so confused I have no idea what you're talking about. I should add another line for windows that is hdb what????
This computer isn't going to have anything on it anymore im moving my linux harddrive into the other computer because this one is pentium 2 and the other one is pentium 4

---

### Post by DaMasta on 2005-12-29
Okay, first tell me how you have your windows machine setup. The linux hard drive is going into the windows machine right?

---

### Post by mztriz on 2005-12-29
[QUOTE=DaMasta]Okay, first tell me how you have your windows machine setup. The linux hard drive is going into the windows machine right?[/QUOTE]
yes i'm just going to put my linux harddrive into my other computer all i wanted to do was make sure it booted correctly. Other than that it has the same things a floppy and cd-rom.
It just has a newer motherboard and processor.

---

### Post by DaMasta on 2005-12-29
[QUOTE=mztriz]yes i'm just going to put my linux harddrive into my other computer all i wanted to do was make sure it booted correctly. Other than that it has the same things a floppy and cd-rom.
It just has a newer motherboard and processor.[/QUOTE]
Right, but we need to know whether the cdrom is on the first ide channel or the second. For example, it could be /dev/hdb or /dev/hdc or even /dev/hdd. We need to edit grub for it's destination location.

---

### Post by mztriz on 2005-12-29
[QUOTE=DaMasta]Right, but we need to know whether the cdrom is on the first ide channel or the second. For example, it could be /dev/hdb or /dev/hdc or even /dev/hdd. We need to edit grub for it's destination location.[/QUOTE]
I don't know, how can I find out? :???: The live cd?

---

### Post by DaMasta on 2005-12-29
I tend to do things the hard way which would be popping the case open and looking. This is a dubious task if you don't really know what you're looking for. I know very little about the live cd. So we're kind of at an impasse. Lets wait until someone with some more knowledge comes along.

---

### Post by mztriz on 2005-12-29
[QUOTE=DaMasta]I tend to do things the hard way which would be popping the case open and looking. This is a dubious task if you don't really know what you're looking for. I know very little about the live cd. So we're kind of at an impasse. Lets wait until someone with some more knowledge comes along.[/QUOTE]
No, I can just look I guess lol  I don't even know why I was thinking that haha. 
Ok brb.

---

### Post by Bachstelze on 2005-12-29
Just plug in your hard drive wherever you want, boot from a Live CD, run sudo fstab -l and paste the results here.

---

### Post by DaMasta on 2005-12-29
[QUOTE=HymnToLife]Just plug in your hard drive wherever you want, boot from a Live CD, run sudo fstab -l and paste the results here.[/QUOTE]
That won't work. If he just plugged in the hd, the bios would see two drives trying to be master and some will flip out and show no drives connected.

---

### Post by mztriz on 2005-12-29
ok... I got confused and decided to take a picture instead. I *think* the cd-rom is on IDE1.  [IMG]http://tinypic.com/jfgje0.jpg[/IMG]
Which is weird because I just put together a new motherboard etc for my brother this morning. (although I did read the manual a little lol.) And for the record I'm not a guy as you said "he". That's the whole reason I put a picture of my self in the avatar; I guess that didn't work lol.

---

### Post by DaMasta on 2005-12-29
Ok, sorry about the gender error. I think the jumper settings on the actual drives is a better indication of what is where. Can you get into your bios? You can probably tell there too.

---

### Post by wounded on 2005-12-29
I assume this wont work (Because no one has mentioned it) but what seemed like the obvious thing that I would have tried would have been to hook up the second drive, put in the Ubuntu Install CD, manually edit the partition table so everything mounts where you want it (Though dont allow the install prog to format/delete anything). It will then error and bring you to that menu. Select Install GRUB and then once that is done Abort. 

Wouldnt that put grub on the MBR with the correct settings to boot into either (As well as have an fstab with all the partitions in it)?

---

### Post by DaMasta on 2005-12-29
Yeah, but I'm pretty sure not adjusting the drive jumpers to prevent conflicts will cause problems. I can tell you from experience that having two drives set as master causes problems.

---

### Post by mztriz on 2005-12-30
[QUOTE=DaMasta]Yeah, but I'm pretty sure not adjusting the drive jumpers to prevent conflicts will cause problems. I can tell you from experience that having two drives set as master causes problems.[/QUOTE]
I'm sorry I am talking so long I would understand if you're not online when I am ready. I am currently transfering a file to a differnt computer =/.
I will be back soon with the bios information.

---

### Post by mztriz on 2005-12-30
okay, now I'm getting somewhere.
Primary Drive 0 - Harddrive
Primary Drive 1- Off
Secondary Drive 0- Cd-rom
Secondary Drive 1- Off

I hope that helps :)

---

### Post by DaMasta on 2005-12-30
Ok. And just to confirm, this is the bios output from the windows machine right? If so:
Primary Drive 0 - Harddrive (windows)
Primary Drive 1- Off
Secondary Drive 0- Cd-rom
Secondary Drive 1- Off

becomes (this is how I'd do it)

Primary Drive 0 - Harddrive (linux)
Primary Drive 1- Harddrive (windows)
Secondary Drive 0- Cd-rom
Secondary Drive 1- Off

Now, if this is a pre-built computer (Dell, HP, Gateway, etc), alot of the times, they've set the drives to cable select. I do not like cable select. You can do it how you want. 
Now you should be able to boot fine if your fstab looks like this:
[i]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
[/i]

As you can see, there is no entry for hdb (which is windows). You can either add that manually, or maybe those commands will enter it, not sure. But while the grub commands are supposed to properly recognize xp, and it usually does, it never boots correctly for me. I always add the following:
[i]title Windows XP
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1[/i]

Have I mentioned you should backup your important stuff? Also, keep track of what jumpers and cables you have changed. Good luck. I'm here for the next 4 hours or so.

---

### Post by mztriz on 2005-12-30
[QUOTE=DaMasta]Ok. And just to confirm, this is the bios output from the windows machine right? If so:
Primary Drive 0 - Harddrive (windows)
Primary Drive 1- Off
Secondary Drive 0- Cd-rom
Secondary Drive 1- Off

becomes (this is how I'd do it)

Primary Drive 0 - Harddrive (linux)
Primary Drive 1- Harddrive (windows)
Secondary Drive 0- Cd-rom
Secondary Drive 1- Off

Now, if this is a pre-built computer (Dell, HP, Gateway, etc), alot of the times, they've set the drives to cable select. I do not like cable select. You can do it how you want. 
Now you should be able to boot fine if your fstab looks like this:
[i]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
[/i]

As you can see, there is no entry for hdb (which is windows). You can either add that manually, or maybe those commands will enter it, not sure. But while the grub commands are supposed to properly recognize xp, and it usually does, it never boots correctly for me. I always add the following:
[i]title Windows XP
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1[/i]

Have I mentioned you should backup your important stuff? Also, keep track of what jumpers and cables you have changed. Good luck. I'm here for the next 4 hours or so.[/QUOTE]
Ok, I just edited the fstab, what am I suppose to do with the menu.lst file?

---

### Post by mztriz on 2005-12-30
Or am I just suppose to plug it in, change the order in bios and boot now?

---

### Post by ThePerg on 2005-12-30
[QUOTE=DaMasta]That won't work. If he just plugged in the hd, the bios would see two drives trying to be master and some will flip out and show no drives connected.[/QUOTE]


Thats not the only thing that won't work.. if these are 2 completely different systems then you'll be lucky if it boots at all. hardware will be different and probably the IRQ / DMA and so forth.. so all your settings you currently have on linux on the current PC probably wont work on the second PC. 

Best bet is to save the data he wants, move the drive over and do a fresh install, then he can have it already setup for dual boot.

---

### Post by mztriz on 2005-12-30
[QUOTE=ThePerg]Thats not the only thing that won't work.. if these are 2 completely different systems then you'll be lucky if it boots at all. hardware will be different and probably the IRQ / DMA and so forth.. so all your settings you currently have on linux on the current PC probably wont work on the second PC. 

Best bet is to save the data he wants, move the drive over and do a fresh install, then he can have it already setup for dual boot.[/QUOTE]
Ahhh, for the millonth time on this message board I am not a guy. :p 
That being said; I should plug in the linux harddrive set it as master, unplug windows reinstall ubuntu plug back in windows as slave and then edit grub?

---

### Post by ThePerg on 2005-12-30
[QUOTE=mztriz]Ahhh, for the millonth time on this message board I am not a guy. :p 
That being said; I should plug in the linux harddrive set it as master, unplug windows reinstall ubuntu plug back in windows as slave and then edit grub?[/QUOTE]


Ooops sorry.. errr. ok

And yes.. that should work.

---

### Post by mztriz on 2005-12-30
[QUOTE=ThePerg]Ooops sorry.. errr. ok

And yes.. that should work.[/QUOTE]
Ok, I hope so I'm going to try it thanks :D

---

### Post by sesstreets on 2005-12-30
oMG GIRL HAX!

---

### Post by Juergen on 2005-12-30
Ahem, I really don't want to confuse you more than you probably are ;-)

But at least installing Windows on the 2nd HD won't work.
I think an already installed Windows might ignore the 1st HD completely if there are only Linux-partitions on it, but I'm not sure...

So *I* would leave the Windows-HD as master, and make the Linux one slave.

Then you'd have to switch all hda<->hdb and hd(0,x)<->hd(1,x) in the previous postings.

---

### Post by mztriz on 2005-12-31
[QUOTE=Juergen]Ahem, I really don't want to confuse you more than you probably are ;-)

But at least installing Windows on the 2nd HD won't work.
I think an already installed Windows might ignore the 1st HD completely if there are only Linux-partitions on it, but I'm not sure...

So *I* would leave the Windows-HD as master, and make the Linux one slave.

Then you'd have to switch all hda<->hdb and hd(0,x)<->hd(1,x) in the previous postings.[/QUOTE]
Yeah, I just took out the windows harrdrive and installed ubuntu instead. lol. 
I'm just going to use my little brothers computer for itunes.

---

