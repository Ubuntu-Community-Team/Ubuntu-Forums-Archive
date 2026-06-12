---
title: "Nagging Update Manager"
date: 2009-06-04
forum: General Help
---

### Post by Peder_Erickson on 2009-06-04
Quite some time ago, I left windows due to bugs, viruses, and the Operating system ALWAYS NAGGING ABOUT SOMETHING....  now I got a new laptop that came with Vista 64 bit, and made it dual boot (Ok maybe I havn't completely left windows, I have a few games I like to play that don't run properly in WINE) but when I installed the 64 bit version of Ubuntu on that machine, and the update manager popped up that first time, and now it always pops up on it's own, becoming a general nusance.  I liked the fact that Ubuntu never nagged me before, but now I get a nag every couple of minutes from that program.  Is there any way to get it to stick in the upper corner of the screen in that icon anymore?  I've also been getting this in a 32 bit version of Ubuntu in VirtualBox, and on 2 other Laptop and a Desktop

Is there any way to change back to using an little icon in the notification area?

---

### Post by steeleyuk on 2009-06-04
To get the old method back, do the following:

Press ALT+F2 > type *gconf-editor* > /apps/update-notifier > uncheck auto_launch

And yes, the nagging is a pain. The old method was perfectly fine.

---

### Post by Peder_Erickson on 2009-06-04
Thanks for the quick reply!

I wonder why they decided to change that?

---

### Post by mcduck on 2009-06-04
> **Peder_Erickson said:**
> Thanks for the quick reply!

I wonder why they decided to change that?

Probably because some people didn't pay attention to small things like a icon in the notification area telling about available updates.

In my opinion simply setting security updates to install automatically by default might have been a better way, but as long as the old behavior can be enabled through gconf it's OK..

---

### Post by steeleyuk on 2009-06-04
> In my opinion simply setting security updates to install automatically by default might have been a better way, but as long as the old behavior can be enabled through gconf it's OK..

I thought that. They should have either left it the way it was or applied security updates automatically.

Another reason they apparently changed it was they wanted to reduce the number of icons on the notification area.

---

### Post by killernurd on 2009-06-10
> **steeleyuk said:**
> To get the old method back, do the following:

Press ALT+F2 > type *gconf-editor* > /apps/update-notifier > uncheck auto_launch

And yes, the nagging is a pain. The old method was perfectly fine.

Thanks, steeleyuk - fixed my issue right quick :)

---

