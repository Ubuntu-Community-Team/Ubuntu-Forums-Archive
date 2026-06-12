---
title: "Can't get usb-devices working in XFCE..."
date: 2005-09-11
forum: Desktop Environments
---

### Post by YourSurrogateGod on 2005-09-11
Worked fine in Gnome.

Pretty much I plug in a device (a memory stick or an external hard drive) and I can't get to it. I don't see any folders or anything popping up. And when I go to /media, all I see is usbdisk-1 and when I open that, I don't see any of my files. Is there some sort of feature that I ought to enable in universe?

---

### Post by Juergen on 2005-09-11
Open the 'xfce' menu, click 'run...' and type 'gnome-volume-manager'
Remember to mark 'save session' when you exit this session and it should start automatically the next time.

But AFAIK there is no config for it to start rox instead of nautilus, you'd have to recompile it for this.
You just have to live with that...

---

### Post by cwaldbieser on 2005-09-11
[QUOTE=Juergen]Open the 'xfce' menu, click 'run...' and type 'gnome-volume-manager'
Remember to mark 'save session' when you exit this session and it should start automatically the next time.

But AFAIK there is no config for it to start rox instead of nautilus, you'd have to recompile it for this.
You just have to live with that...[/QUOTE]
If you are a little familiar with shell scripting, you can write your own hotplug script to mount the drive for you.  Or if you are a command line junkie, you can just manually mount it yourself.

---

### Post by YourSurrogateGod on 2005-09-11
[QUOTE=Juergen]Open the 'xfce' menu, click 'run...' and type 'gnome-volume-manager'
Remember to mark 'save session' when you exit this session and it should start automatically the next time.

But AFAIK there is no config for it to start rox instead of nautilus, you'd have to recompile it for this.
You just have to live with that...[/QUOTE]
Cool, that worked.

---

