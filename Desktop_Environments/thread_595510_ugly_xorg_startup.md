---
title: "ugly xorg startup"
date: 2007-10-28
forum: Desktop Environments
---

### Post by 88axit7 on 2007-10-28
hello all, 
whenever i start my desktop (Xfce4), i get this really ugly screen that looks like my desktop but all messed up and static-like.  This shows up right before the ugly-grey-zig-zag-and-cursor xorg screen.  i changed the xorg screen to black but i still get this ugly screen right before it.  If anyone knows what is going on please help.

I'm not using a manager to start the desktop,  just startxfce4.

thanks ubuntu!

---

### Post by TeaSwigger on 2007-10-28
> **88axit7 said:**
> hello all, 
whenever i start my desktop (Xfce4), i get this really ugly screen that looks like my desktop but all messed up and static-like.  This shows up right before the ugly-grey-zig-zag-and-cursor xorg screen.  i changed the xorg screen to black but i still get this ugly screen right before it.  If anyone knows what is going on please help.

I'm not using a manager to start the desktop,  just startxfce4.

thanks ubuntu!

Video configuration / "driver" issue perhaps?

---

### Post by 88axit7 on 2007-11-02
UPDATE

I Installed Gutsy and selected 'use entire disc' in the partitioning part of the install.  Installed just the CLI interface, Then installed Xorg and Xfce.  

I type startxfce4 and get this: I see that same ugly scrambled screen from before.  INCLUDING MY OLD WALLPAPER!!

This seems really strange to me.  Can someone please explain?  I'm be reading about Xorg...

---

### Post by 88axit7 on 2007-11-15
i upgraded my ram and now the scrambled screen is alot more detailed scrambling.  I should have realized this when it was still there after a reinstall,  but evidentaly the image is saved in ram.  

Does anyone know how to change this?!  My startup is so ugly!

---

### Post by vavoem on 2007-11-16
This will be a dump of your graphicscard memory when you last rebooted your system.
I have the exact same issue.
I gues there's not much you can do about it except to flush your grapics card memory before you start xorg
Don't no how though, anyone ?

---

### Post by Jouke74 on 2007-11-16
I haven't got a clue what ugly-grey-zig-zag screen you mean, but you might want to try the "nosplash" option by changing that in your boot/grub/menu.lst file.

---

