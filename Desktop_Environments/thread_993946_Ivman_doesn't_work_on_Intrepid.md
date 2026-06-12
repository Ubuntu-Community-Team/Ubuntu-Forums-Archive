---
title: "Ivman doesn't work on Intrepid"
date: 2008-11-26
forum: Desktop Environments
---

### Post by deadlinx on 2008-11-26
Hi,

I use Ubuntu (Intrepid Ibex),
with Fluxbox (*without Gnome*).

I'd like to automount my devices,
as I've done in the past,
for this reason I've always used, 
successfully, ivman.

On Intrepid Ibex, ivman simply 
doesn't work at all, also after 
trying to tune it, as Gentoo 
tutorial advised.

I hope someone has an idea 
on how to make it working,
'cause manual mounting is 
really boring.

---

### Post by deadlinx on 2008-11-26
Hi,

I've also to prepare a Linux-box,
with 256 MB RAM, for a non-skilled person,
so I can't use kde or gnome and 
I have to use a WM and a window manager 
without automount is not a good idea 
for a newbie.

---

### Post by deadlinx on 2008-11-26
Hi,

I forget to say he likes nor Xfce nor E17

---

### Post by deadlinx on 2008-11-27
Uuuh,

is there anybody??

I think it's not a ivman bug, but a pmount bug: 
in fact ivman uses pmount and it (pmount) 
does not recognises usb disks and pendrives as 
"block device"; anyway I'm sure pmount worked 
correctly in the past, because of ivman, in the past,
correctly mounted all usb memory devices.


deadlinx

---

### Post by deadlinx on 2008-11-27
Hi,

my opinion on pmount bug seems to be correctly,
ivman debug mode confirms my opinion.

deadlinx

---

### Post by deadlinx on 2008-11-27
Hi,

I've also read about launchpad bugs,
but it seems to there is nor solutions,
nor hacks or workaround to make it working
in Intrepid.

It's quite frustrating :-(

Thank you in advance 


deadlinx

---

### Post by deadlinx on 2008-11-28
JUuuuuuuuuuuh,

is there anybody reading?

Don't say me there's nobody using ivman,
with a Window Manager in Intrepid Ibex.

so, please, help


deadlinx

---

### Post by deadlinx on 2008-11-28
Don't say me everybody uses only GUI tools,
I can't belive it,

So please, give an idea and so on,


deadlinx

---

### Post by nxmehta on 2008-12-08
This is a bizarre little thread.  If you want people to respond to your thread you should give a little bit more info about your problem other than "it doesn't work".

Anways, I'm having the same problems with ivman/pmount.  I don't think there is a fix available.  The last I saw of the problem and a possible workaround was at [http://ubuntuforums.org/showthread.php?t=968590](http://ubuntuforums.org/showthread.php?t=968590)

---

### Post by nxmehta on 2008-12-09
The bug is officially listed here: [https://bugs.launchpad.net/ubuntu/+source/pmount/+bug/296164](https://bugs.launchpad.net/ubuntu/+source/pmount/+bug/296164)

Looks like the pmount maintainer says that it will not be fixed for a long time.  The problem is that pmount depends on sysfs which is deprecated.  Apparently this is hard to change.  So unless you add all possible devices that you want to pmount to /etc/pmount.allow, ivman is basically useless.

Fun!

---

### Post by deadlinx on 2008-12-10
Hi,

@ nxmehta: thank you for your answer.



I've read that link saturday,
anyway it's frustrating to 
discover that the solution 
is manual mounting...
...back to past...
....it's so 90's...

---

### Post by HornedBeast on 2009-02-23
Hello,

I have recently ran into this problem with Ivman and Pmount.

I ended up running Ivman as root so it could use normal "mount". Trouble then was, all the files it was creating from auto-ripping cd's and dvds were then root assigned.

Is there an alternative to Ivman that works at all?

I'm basically trying to make it so that I can put an audio cd into my headless Intrepid Server. It then detects if its audio, video or data and runs the appropriate app. 

So, for an audio CD, it would automatically rip using "abcde", then eject.

For DVD's it would automatically run "vobcopy".

Ivman seems to do exactly that, but with Pmount not working and having to use root for everything, it seems absolutely useless.

How does this pmount.allow stuff work? Do I have to list the exact device that each user is allowed to mount? How will it know if someone has plugged in a new USB storage that's never mounted before?

Regards,

HB

---

