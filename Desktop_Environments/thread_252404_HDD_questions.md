---
title: "HDD questions"
date: 2006-09-06
forum: Desktop Environments
---

### Post by bastupungen on 2006-09-06
Hello! 
I installed ubuntu a couple of week ago on 1 hdd. I then later added 2 HDD and had problems with boot up (my root folder renamed it self from sda1 too sdc1, small problem now fixed.

The problem, or should i say, confusion i have now is that my hdd config seems rather, should i say, fu***d up! When i go too system -> administration -> Disks i can see my disks, fine. The problem is that my sda1 (new drive partitioned and formated) is mounted at / i double checked by going to the terminal and typing mount. This is what i get:
/dev/sda1 on / (....)

So according to the mount command my original install drive, now called sdc1 is not mounted. How this would work in ANY way is beyond me, which i why i think this is some kind of error.

Anyways, i have tried to change the mount point of /dev/sda1 to something else than / and failed miserably. When i change mountpoint in the Disks software it just changes back when i close.

Is this correct that my CLEAN partition could be mounted at /. What does this mean. And how do i change this to what should be the correct setting (/dev/sdc1 at / and /dev/sda1 at /mnt/whatever)?

---

### Post by kidders on 2006-09-06
That kind of renaming will only occur if you plug your disks in in the wrong order. Your first serial disk is always /dev/sda, however if you subsequently add another one in front of it, *it* becomes /dev/sda.

Try swapping your disks around, for a quick solution :-P

Alternatively, you can edit your /etc/fstab to reflect the way your system is configured.

The fact that you were obviously able to reboot your system seems terribly odd! Can you post your /etc/fstab and the output of the **mount** command?

---

### Post by bastupungen on 2006-09-06
Sure, FSTAB:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

And Mount:
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)

What happend was the ubuntu stoped loading when i added the HDD's. So, i changed in the grub loading menu that it should load the root folder from /dev/sdc1 (instead of /dev/sda1). Then everything loaded fine and i have not had many strange problems occuring because of it, except not being able to mount the drives properly.

The major question i have is if i can remove the mount of / (/dev/sdc1) or will that **** up my system telling me that i have no system anymore? (even though the system wasn't there in the first place)

Oh, and also. I don't wan't too have to swap disks physically. The server is located 20 kmeters away from me. I have VNC access of course. If you wan't i can give you access too it to have a look

---

### Post by bastupungen on 2006-09-06
heh.. i just looked at the fstab and realised that i probobly dont have an swap-file. I don't have an /dev/sda5 (of course i have an /dev/sdc5)

---

### Post by kidders on 2006-09-07
Hmm... that all explains your problems, I think. The information in your /etc/fstab is inconsistent with the kernel boot directives from /boot/grub/menu.lst.

I *could* log in and fix it for you, but you'd only wind up having to give me root privileges, which **should** be unacceptable to you!

Here's what to do, to straighten things out:

[LIST=1]
[*]Assuming you're really sure /dev/sdc1 is the root partition, update your /etc/fstab so it agrees with you. Judging by the way your disks are actually mounted, your root partition isn't at /dev/sdc1 at all!
[*]Add a line in /etc/fstab to have any new partitions mount where you want them.
[/LIST]

Something still doesn't feel quite right to me about all this, but you need to sort out the inconsistencies in your config files sooner or later.

Incidentally, if you're so far away from the server, tinkering with the way it boots is kinda dangerous ... what if it breaks?

---

### Post by bastupungen on 2006-09-07
Yeah i guess giving you root access would be stupid, especially because its an, to be, web and file server! =D
e that this should
What do you mean when you say "Judging by the way your disks are actually mounted, your root partition isn't at /dev/sdc1 at all!"? 
I am quite sur be the disc that i installed to. Because when i look in discs in the system menu i can see 3 discs. /dev/sda is partitioned and clean. Partitions that i added after i installed, which should have killed my system if it was my system-drive. And i have /dev/sdb that is compleatly clean, not even an partition on it. and i have /dev/sdc that has one large partition and an swap-file and it says that its partly used drive.

If you want too take a look at the system i could give you access to vnc, but not sudo or root. But i dont think its neccessary from my part.

heh, yeah.. what if it breaks! =D then i guess i have to take a car ride! But thats ok, then i get to see my grandma!

---

### Post by bastupungen on 2006-09-07
Ok.. hmm.. I tried to umount the /dev/sda1 from / which seems to not be possible. it says its busy. And i am also unable to mount /dev/sdc1 at /. I thought that if i mounted something else there i could unmound the other drive, but no.

if i edit fstab and do that restart command, that i now cannot recall how to do, do you think that /dev/sda1 will be able to umount itself?

---

### Post by kidders on 2006-09-07
Yeah, you'll never succeed in dismounting your root filesystem that way ... you can't "eject" something that's in use ... which it always will be, since it's the root. Also, trying to mount something on top of your root on the fly would be a terribly idea!

Any time you change anything that fundamental to the way your system works, you *have* to reboot.

The thing that's not adding up for me is that you seem certain your root filesystem is at /dev/sdc1, which doesn't tally with the fact that your system swears it's at /dev/sda1. So, one of two things is the truth:

[LIST=1]
[*]Your root is really at /dev/sda1, in which case, tweaking /etc/fstab to mount /dev/sdc1 there instead will bork your system. You will then need a bootable CD to put your /etc/fstab back the way it was.
[*]Something very odd is happening (that is either causing Linux to mistake one hard disk device for another, or causing device names to change during boot), and your root is, in fact, at /dev/sdc1. In this case, tweaking your /etc/fstab will fix all your problems.
[/LIST]

Number two is very unlikely, but I've been inclined to take your word for it up to now, when you say that you are certain about where your root filesystem is at.

So, why not start at the beginning? Pretend you have no idea where anything is, and use **mount** and **cfdisk** to figure out the new hard disk arrangement from scratch. Then, write a new /etc/fstab (making sure /boot/grub/menu.lst is consistent with it), and hit CTRL+ALT+DEL.

Does that seem sensible?

---

### Post by kidders on 2006-09-07
With regard to your other post ...

> What do you mean when you say "Judging by the way your disks are actually mounted, your root partition isn't at /dev/sdc1 at all!"?

When you type "mount" your system tells you what's mounted right now. If it says /dev/sda1 is at / then I can't think of a reason not to believe it.

This is all getting very confusing! Maybe I *should* take a look. If you'd like that, set me up an unprivileged account and give me sudo access to /sbin/cfdisk only. I'd also appreciate access to your system logs. I'll see what I can figure out for you :-P

---

### Post by bastupungen on 2006-09-07
dammit.. Im not sure how too make it possible for another user to be able to log in through vnc. I can login to my user, I added that option in remote desktop control in gnome system. I guess I have to add that option to your user too, and of course a password. The problem is that i dont know if i can log out of my current user and still be able to login remotely

OK.... Now i crashed something! wierd! hmm.. i use tightvnc and tried too switch too another console and start another x from there using the command alt + f1. The problem is just that i thought i needed ctrl + alt + f1 and now the computer seems to be frozen. I can login too it through vnc but i cannot do anything. I see the screen but everything is frozen. Is there any command like ctrl+alt+delete in windows to be able to see why this is. And also alt+f1 does not work. And also noone is at my cottage to restart the server. crap

Edit: I tried ctrl clt backspace which killed everything, i cant even login to vnc right now. Its probobly in a shell, curses!

---

### Post by bastupungen on 2006-09-08
Ok, The HDD problem is now fixed. I changed the hdd's physically. I had to get out here anyhow, because i lost my admins right. I messed up bad. Good that theres an easy way to fix it, at least. (Though i am question the way ubuntu handles groups. Ubuntu seriously should have asked me if i REALLY wanted to remove all users from the admin group, and explain the consequences. In a sence human are stupid and does stupid things.)

But now too the real question. Why did this happen? Why was i able too boot and run the everything fine when my / folder wasn't even correctly mounted? Is it possible too add an automatic search during boot too find the / if there is a similar problem like i had. The problem this gives me now is that i cannot use the raid card i was hoping too use. Because the raid card goes ahead of the motherboards built-in sata controller and is assigned hdd names first. Is it possible to fix a hdd at a specified name? All too many questions that are important to linux usability and compability but cannot be answerd by me. If any linux developer wan't to check my problem out they can contact me at
[email]bastupungen@mail.nu[/email]

---

### Post by kidders on 2006-09-08
Oh crap. CTRL+ALT+BACKSPACE restarts your X server, so if something is the matter with it and the restart fails, you're sunk :-( At any rate, I wasn't expecting anything as elaborate as a VNC session ... a plain text-based interface is all I would use/want.

> Ubuntu seriously should have asked me if i REALLY wanted to remove all users from the admin group

It does ... Linux users should take it for granted that anything you need to be root (or have similar administrative privileges) to do has the potential to screw up your system. On any operating system, you shouldn't really do something that requires elevated privileges without a good understanding of what the effects might be ... that's why you need elevated privileges to do it!

> Why was i able too boot and run the everything fine when my / folder wasn't even correctly mounted?

Your root was correctly mounted, because of a directive in /boot/grub/menu.lst. (See the output you posted of the **mount** command). This was despite contradictory instructions about where it was ... pretty impressive, no?

> Is it possible too add an automatic search during boot too find the /

You probably could do this if you really wanted to, but Linux prefers not to touch hard disk partitions without an explicit instruction to do so. In more general terms though, what if you had more than one / partition?

> i cannot use the raid card i was hoping too use. Because the raid card goes ahead of the motherboards built-in sata controller

How does this affect your ability to use it? Generally, the names assigned to devices (and the order they are assigned in) are irrelevant.

> Is it possible to fix a hdd at a specified name?

Yep ... udev can do that for you.

On a related note, it's pretty vital not to fiddle around with settings that are vital to the basic function of a Linux system without a good understanding of their impact. Unfortunately, if you give any operating system conflicting or inconsistent instructions about something like *where* it is, you will break it.

---

