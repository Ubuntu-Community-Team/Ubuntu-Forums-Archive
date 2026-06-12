---
title: "Unwanted icon in Computer location"
date: 2006-03-10
forum: Desktop Environments
---

### Post by entryname on 2006-03-10
Hello :KS  this is my first post. I solved two other problems by searching and finding the answers, but I couldn't find this one.  I looked in several forums and read several "read first" posts, so apologies if this is in the wrong place or I shouldn't have posted it, but I did try to do the right thing. :-k 

*(I will add in parentheses here that having at one time or another run Knoppix, Mandrake 9.2, Mandrake 10.1, Mepis, and briefly DSL, Puppy and Beatrix, thus far I'm impressed with Ubuntu. It's rock steady unlike Mepis that over several months crashed repeatedly and failed to start on average perhaps one time in five.)*

One of the answers I found was this one
[Zip drive trouble]("http://ubuntuforums.org/archive/index.php/t-12074.html")
but that's where this problem came from. I had previously had a zip drive icon in Computer.... which didn't work. When I made the new icon, that became Zip Drive.... and the old icon became Zip Drive 1.  As "Zip Drive 1" doesn't work I'd like to get rid of it. I don't understand though where the icons in this folder come from, so I don't know how to. :confused: 

As I understand it, this point was put in the original thread and got a "yes that's right" sort of response? that is, sorry it's unavoidable, you can't get rid of the duff one??

media contains cdrom cdrom0 cdrom1 floppy floppy0 zip zip0

/etc/fstab:
[COLOR="Blue"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdd	/media/zip0	auto	rw,user,noauto,sync	0	0[/COLOR]

/etc/udev/links.conf:
[COLOR="Blue"]# This file does not exist. Please do not ask the debian maintainer about it.
# You may use it to do strange and wonderful things, at your risk.

L fd		/proc/self/fd
L stdin		/proc/self/fd/0
L stdout	/proc/self/fd/1
L stderr	/proc/self/fd/2
L core		/proc/kcore
L sndstat	/proc/asound/oss/sndstat
L MAKEDEV	/sbin/MAKEDEV

D pts
D shm

# Hic sunt leones.
M ppp		c 108 0
D loop
M loop/0	b 7 0
D net
M net/tun	c 10 200
M hdd4 		b 22 64
[/COLOR]

....sooooo.... is there any way of removing Zip Drive 1 (the one the system put there that doesn't work) pretty please??

---

### Post by jasay on 2006-03-12
You might try opening nautilus.  Is zip drive 1 shown in the places panel on the left?.  If it is right click and remove.  Seems to work for me anyway, but I'm on dapper right now so I don't know if it translates.:???:

Edit: Whoops, just realized that you are talking about Computer not Places.  Good thing I can read.

---

### Post by entryname on 2006-03-12
No, it's not in the places list, only in the Computer location as an icon. 

I don't understand exactly where these icons come from. I tried searching for a file, any file, containing "Zip Drive 1" but search files couldn't find one. I also tried looking in one or two config files to see if I could see zip drives being set up but I couldn't, apart from the manual one. 

Especially given that for example icons for a USB drive appear when it is plugged in, I suspect Computer is some sort of dynamic thing that doesn't exist as an actual file or directory, but if there is a hack to get rid of Zip Drive 1 I'd be interested. Ubuntu has done soooo well compared to Mepis, I'd just like it to be *right*, you know??

---

