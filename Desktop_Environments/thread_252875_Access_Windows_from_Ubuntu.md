---
title: "Access Windows from Ubuntu"
date: 2006-09-07
forum: Desktop Environments
---

### Post by hellmet on 2006-09-07
Dear all,

I have two systems in my house..
My mother uses one..with XP on it..

I use one with ubuntu on it...
Sometimes I need to run certain
files and programs on Windows ,
and I find Wine to be not sufficient..

The systems are connected thru LAN.
I am looking for a solution thru which
I'll be able to access the Windows XP
computer just as if I were sitting at that computer.
That is able to run/install etc from my Ubuntu Machine..

I am sure there must be a way..but I am 
not able to find one..


Please help me...

---

### Post by Najand on 2006-09-07
You can share your files in Ubuntu 
and access windows XP shared files 
using Samba. You can find more details
at [http://ubuntuguide.org](http://ubuntuguide.org)

> **hellmet said:**
> Dear all,

I have two systems in my house..
My mother uses one..with XP on it..

I use one with ubuntu on it...
Sometimes I need to run certain
files and programs on Windows ,
and I find Wine to be not sufficient..

The systems are connected thru LAN.
I am looking for a solution thru which
I'll be able to access the Windows XP
computer just as if I were sitting at that computer.
That is able to run/install etc from my Ubuntu Machine..

I am sure there must be a way..but I am 
not able to find one..


Please help me...

---

### Post by Scunizi on 2006-09-07
If you want the graphic interface of XP on the other machine to show up in a window on your linux box.. install TightVNC or something similar on the windows machine.  You can then access it by using the Terminal Server Client located off the Applications/Internet menu of Ubuntu.  It won't allow file transfer but will give you complete control over the xp box.

---

### Post by etank on 2006-09-07
To do some of what you are looking for with haveing to install anything on either machine turn on Remote Desktop on the XP machine. Then you can use the Terminal Server Client tool from inside Ubuntu to access the machine. The only problem is that Remote Desktop on XP is single user only. That means that if someone else is on the box then it will lock the screen to them until you are done. If that isn't what you want then use TightVNC or UltraVNC like suggested before.

---

### Post by Toxicity999 on 2006-09-07
Another possibility is to make a VMware image of your current Xp machines HDD minus the fluf. And fire it up in VMware, or QEmu. That is assuming you only need whats there now and not literal direct access.

---

### Post by hellmet on 2006-09-08
Oh...THanks a TON ..a TON ppl...
the Tight VNC thing worked like a charm...
I needed it for my GRE s/w..
I din want to put Windows on my PC
for just that..neither did I want to waste space
with VMWARE...

thanks once again@all

---

