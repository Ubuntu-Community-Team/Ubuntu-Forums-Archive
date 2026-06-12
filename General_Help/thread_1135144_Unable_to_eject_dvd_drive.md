---
title: "Unable to eject dvd drive"
date: 2009-04-24
forum: General Help
---

### Post by sandy8925 on 2009-04-24
I'm using Ubuntu 8.10.

The problem I'm having is that whenever I try to open my DVD drive by pressing the normal eject button on the front, it doesn't open and a an error message comes on the screen saying:

"You don't have permission to unmount /dev/scd0. Only root can do that."

It's not really much of a problem since I can always open up a terminal and type:

sudo umount /dev/scd0

and then I'm able to open the DVD drive. But I'd still like to fix this. Can someone please help ?

---

### Post by gettinoriginal on 2009-04-24
Two things that will possibly help you.  System > Admin > Users and Groups > Root, unlock, password, then check both boxes (you and root).  This adds you to roots group.  You also may right click on the DVD applet on your desktop and choose "eject"  Hope one of these helps you.  :P

---

### Post by Kain000 on 2009-04-24
> **gettinoriginal said:**
> Two things that will possibly help you.  System > Admin > Users and Groups > Root, unlock, password, then check both boxes (you and root).  This adds you to roots group.  You also may right click on the DVD applet on your desktop and choose "eject"  Hope one of these helps you.  :P
I dont think you should add yourself to the root group for securety reasons, but in the same menu you can give yourself permission to mount and unmount drives, thus allowing you eo eject things but w/o allowing you to install anything w/o a password.

---

### Post by gettinoriginal on 2009-04-24
I have myself added to my root group, but it still asks for password.  I think it is default for any root process to require it.  But then I could be wrong.

---

### Post by sandy8925 on 2009-05-07
I would prefer not to add myself to the root group. I did check the Users and Groups program. In my User's properties , under the User Privileges tab the option "Use CD-ROM drives" was already checked. By the way I am using Jaunty now but the problem still seems to persist. I did an upgrade using the alternate iso.

---

### Post by Dngrsone on 2009-05-07
Since he is using the button on the device to try to eject, it would be him as the user requesting to unmount, but rather the device, which should be user system or something, no?

I had a problem with my Dell where it would just ignore my pushing the button.  I always opened up a terminal and typed ```
eject
``` to open my drive bay.

---

