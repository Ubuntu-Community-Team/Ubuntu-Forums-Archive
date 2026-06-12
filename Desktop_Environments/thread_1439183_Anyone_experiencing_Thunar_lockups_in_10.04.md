---
title: "Anyone experiencing Thunar lockups in 10.04?"
date: 2010-03-25
forum: Desktop Environments
---

### Post by Lord.Quackstar on 2010-03-25
I've recently upgraded to Xubuntu 10.04 beta only to find out that Thunar keeps locking up, sorta. By locking up I mean that the actual file and folder list does not respond to the mouse after using it for a minute or 2. However the top and side menu's work fine. The file list does update when changing folders but still dosen't respond to the mouse. However keyboard control's do work.

I've currenty been reduced to bringing up nautilus (this is technically Ubuntu with an XFCE addon) and using that instead.

Is anyone else experiencing this? If not then what can I do to remidy the problem?

Specs:
Type: Laptop
OS: Ubuntu 10.04 with XFCE

Howto reproduce the problem:
-Change directories by double clicking on folders in the file list, should eventually lock up

---

### Post by xerophyte on 2010-04-04
I have the same issue, does anyone know how to fix this i am running x86_64  10.04

---

### Post by Grïzlürk on 2010-04-17
Same issue here. I installed from Xubuntu 10.04 RC2 AMD64 Alternate ISO. I tried PCManFM from LXDE and exact same thing. For now I am using Dolphin but I became addicted to the Thunar speed. There is an open ticket on the LXDE bugtracking but no updates so far. As the 2 software seems to have the same behaviour and on 10.04 only (so far) it might be Distro related. On 9.10 it was working like a charm.

Maybe it is not related but since the 10.04 install it seems my group 1000 called users became a group called grizlurk (my username) maybe it affect. I also have some issue time to time with the panel who does not launch automatically since 10.04.

I've performed a clean install but kept my home folder from previous 9.10 install. So far this is the only annoyance with 10.04.

Xubuntu with KDE and Gnome, LXDE installed as well.

---

### Post by kerry_s on 2010-04-17
no problems here, i have thunar+xfdesktop4 on top of lubuntu.

---

### Post by straxus on 2010-05-03
I'm having this problem as well in Mythbuntu 10.4.  Left clicking to open a folder in the right pane causes the problem.  Right-clicking and going to 'open' works fine.  

I noticed that once the right pane has glitched, right-clicking and going to properties will always bring up the properties of the folder you just opened, rather than those of the file you right clicked on.

One of the work arounds I'm using for when this happens (when I forget to right-click-open) is to right click the current folder in the pathbar, and click 'open in new window'.  The new window will work fine - until you forget and left click open again.

Hopefully this gets patched soon.

---

### Post by rotten777 on 2010-05-03
Same here. I just upgraded and having weird issues. I've found a fix of changing the view in thunar (ctrl+1, ctrl+2, ctrl+3) to get it to respond. Not exactly my idea of a fix but I'll wait for the real fix and deal with it.

---

### Post by Bully_Jesus on 2010-05-04
I too have this problem. Other than this and Firefox audio the upgrade from 9.10 worked fine.

---

### Post by IgnorantGuru on 2010-05-04
The problem with double-clicking is a bug in GTK 2.20 which affects Thunar, PCManFM, XFBurn, and others, on many distros...
[https://bugzilla.gnome.org/show_bug.cgi?id=612802](https://bugzilla.gnome.org/show_bug.cgi?id=612802)

My mod of pcmanfm now has a fix for this in place...
[http://igurublog.wordpress.com/downloads/mod-pcmanfm/](http://igurublog.wordpress.com/downloads/mod-pcmanfm/)

---

### Post by straxus on 2010-05-04
Good to know.  Well, until the GTK bug is squashed, I found a livable workaround for Thunar over on the Debian User Forums.

edit > prefererences > behavior 
set navigation to single click

---

### Post by honeydew on 2010-05-14
I was told it was a specific problem with detailed list, and that if the view is set to Icon or List(simple) the problem does not exist.

---

### Post by Lord.Quackstar on 2010-05-19
BTW, installed Thunar on Lubuntu Beta 4 a week or 2 ago, and it locked up again. Since I didn't particularly like it anyway, I simply installed nautilus. And PCManFM doesn't freeze, so I'm fine.

Any updates?

---

### Post by mister_p_1998 on 2010-05-21
I had it on the 32 bit beta, but updates seem to have cured it...

---

### Post by realnick on 2010-05-24
> **honeydew said:**
> I was told it was a specific problem with detailed list, and that if the view is set to Icon or List(simple) the problem does not exist.

I got this problem when I changed to detailed list, but works fine with Icon view.

---

### Post by PcMojo on 2011-08-24
Are you sure it's Thunar? I have a similar problem with Kde->Dolphin. I'm on 11.04 but it's been like that since 10.10.

---

