---
title: "gnome takes ages to load the Desktop"
date: 2015-09-29
forum: Desktop Environments
---

### Post by dgoosens on 2015-09-29
hi all,

Using Ubuntu Gnome 14.04 and it takes like forever to load the Desktop on boot.
I do not encounter this issue when doing a logoff followed by a login.

Have been looking all over the web but only found a few suggestions that barely made a difference

Really got the feeling that this is related to Nautilus (got version 3.10.1)...
I did try the 
killall nautilus
command on boot and that does make a difference...

I could obviously add that command to the startup scripts...
But I'd rather figure out what takes so long and really solve the problem.

Point is, I have no clue where to start looking...
Checked various logs that don't show any weird stuff, at least to me.

So...
Anyone knows a solution ?
Or could anyone at least tell me where I should start looking?
Let me know if there is some log or other info that might be pertinent...

Thanks a lot in advance!
dgoosens

---

### Post by VMC on 2015-09-29
Could be *fstab* points to wrong swap partition. When grub comes up, go to '*linux*' line and remove '*quiet'* from the end of the line, then F10. See if you can spot where the holdup occurs.

Most likely we will need more information.

---

### Post by dgoosens on 2015-09-30
thanks for getting back at me

I may have been unclear...
I mean, once I log in, it takes ages

Have been testing the killall nautilus command and that clearly makes a difference...

Finally, I am encountering this issue both on my laptop and on my PC...
Both are running 14.04 Gnome Edition
Both are more or less configured the same way.

Anybody ?

---

