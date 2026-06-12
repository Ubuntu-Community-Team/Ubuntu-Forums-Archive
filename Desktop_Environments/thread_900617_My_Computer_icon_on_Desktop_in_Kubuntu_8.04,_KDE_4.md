---
title: "My Computer icon on Desktop in Kubuntu 8.04, KDE 4.1"
date: 2008-08-25
forum: Desktop Environments
---

### Post by SammerHammer on 2008-08-25
The title really explains all that I wanted to say.
I can't find any way to go to My Computer in KDE. When I type My Computer in the Dolphin address bar, it doesn't work.
However, openSUSE uses KDE and I have seen screenshots of openSUSE with a My Computer icon on the desktop.
Please help me find a way to get to the My Computer interface, because it is really annoying to manage my USB devices, and partitions, and CD drives without it.

The same problem in Xubuntu (I tried the live Cd)

---

### Post by crazyone on 2008-08-25
try typing computer in dolphin. becuase that is the true name if im not mistaken

---

### Post by SammerHammer on 2008-08-25
Dolphin should have a My Computer button on the side panel, like it does for Trash and Home.

---

### Post by SammerHammer on 2008-08-26
EDIT: When I use Nautilus (the GNOME file manager) on KDE, I can visit My Computer, so this is a file manager problem, not a KDE problem, I think.

---

### Post by SuperSonic4 on 2008-08-26
Have you tried *system:/media*? It is in a computer icon at the bottom of kubuntu. Kicker might not be enabled though, so type kicker into a command (alt+f2) and go from there

---

### Post by SammerHammer on 2008-08-26
> **SuperSonic4 said:**
> Have you tried *system:/media*? It is in a computer icon at the bottom of kubuntu. Kicker might not be enabled though, so type kicker into a command (alt+f2) and go from there

I have KDE4, so I don't think I need kicker.
BTW, the system:/media command doesn't work in Dolphin.

---

### Post by pgatrick on 2008-08-27
Do you have the 'new device notifier' widget? Alternately you could just open up whatever file manager you like and go to '/media'.

EDIT: Also, for me at least, Dolphin lists the various mounted drives on the sidebar.

---

### Post by SammerHammer on 2008-08-28
> **pgatrick said:**
> Do you have the 'new device notifier' widget? Alternately you could just open up whatever file manager you like and go to '/media'.

EDIT: Also, for me at least, Dolphin lists the various mounted drives on the sidebar.

Yes, I have that widget in the Panel, but it doesn't have the same effect as the actual My Computer interface. /media just brings up some folders, not icons.

---

### Post by nitin.pant on 2010-05-14
I was trying to find the same thing. A trying few things but it doesnt happen to work. I think the computer:/ , media:/ or sysinfo:/ protocols are just not supported in KDE4. 
I even tried to install kiosysinfo package but even that wont let you open sysinfo:/

But SUSE has found a way to show my computer icon! So there is a way.. i will keep trying. I'll keep you guys informed as and when(and only if) iam able to do it..

---

### Post by rosco136 on 2011-06-22
> **nitin.pant said:**
> I was trying to find the same thing. A trying few things but it doesnt happen to work. I think the computer:/ , media:/ or sysinfo:/ protocols are just not supported in KDE4. 
I even tried to install kiosysinfo package but even that wont let you open sysinfo:/

But SUSE has found a way to show my computer icon! So there is a way.. i will keep trying. I'll keep you guys informed as and when(and only if) iam able to do it..

So did you ever find a way round the "My Computer Icon" in Kubuntu?

It's driving me nuts, where do I find how much free HDD space I have, other than using console commands?
I'm trying to remember why I switched to Kubuntu from SUSE. 
I wouldn't be surprised to hear that Novell have written some parts of KDE themselves, for their distro.

In addition, I can't find an equivalent to the Hardware Info list that is available in SUSE. I'm not saying there isn't one, I just I can't find it!

---

### Post by smsmith on 2011-06-25
Try KInfoCenter for your hardware list.

In Dolphin, choose View -> Panels, make sure that Places is turned on.  You can add shortcuts to wherever you want there.  Mounted drives also show up in the Places list.

In the status bar of Dolphin, right click, choose Show Space Information.

---

