---
title: "Console after xgl - compiz install"
date: 2006-07-25
forum: Desktop Environments
---

### Post by exif on 2006-07-25
I have just recently installed xlg and compiz and they are working without a hitch so far. But now when I press ctrl-alt-F1 - F6 for the console, my screen just goes black as though the resolution cannot be displyed.

Before the xgl - compiz install it worked fine. The only other changes I have done is change xorg.conf to use the proprietary nvidia drivers (changed nv to nvidia) and I also changed the default depth to 24 rather than 16.

What would cause console to not be able to display?

---

### Post by pablo13 on 2006-07-26
Hi, I have exactly the same problem but I didn't related to compiz instalation ... but after reading your post I've just realized that it's true; after installing xgl & compiz the virtual consoles stopped working.

Anybody have an answer?

Thanks,
Pablo

---

### Post by Promixa on 2007-10-05
Hi, I seem to have the same problem with compiz fusion. If I switch to the linux console (Ctrl+Alt+F1), I just get a black screen.
When I remove the kernel option vga=794, which I had used before, the console is accessable again. So far I did not find a way to keep this kernel option and switch to the console :(.
So my advice is to remove the kernel option.

I found out how to fix this problem in a german forum: [HTML]http://forum.ubuntuusers.de/topic/102973/[/HTML]

[LIST=1]add entry **fbcon** to **/etc/initramfs-tools/modules**
[*]rebuild initial ramdisk with the command **sudo update-initramfs -u -k all**
[/LIST]

I guess you have to do that every time you install a new kernel!

---

### Post by macbuff on 2007-10-10
> **Promixa said:**
> Hi, I seem to have the same problem with compiz fusion. If I switch to the linux console (Ctrl+Alt+F1), I just get a black screen.
When I remove the kernel option vga=794, which I had used before, the console is accessable again. So far I did not find a way to keep this kernel option and switch to the console :(.
So my advice is to remove the kernel option.

I found out how to fix this problem in a german forum: [HTML]http://forum.ubuntuusers.de/topic/102973/[/HTML]

[LIST=1]add entry **fbcon** to **/etc/initramfs-tools/modules**
[*]rebuild initial ramdisk with the command **sudo update-initramfs -u -k all**
[/LIST]

I guess you have to do that every time you install a new kernel!

I tried adding fbcon to /etc/modules and that did work up untill the most recent kernel on gutsy.  I just tried the method shown above and that didn't have any effect on my system.  (DELL D610 laptop) I'm using 2.6.22-24-generic.  On my DELL desktop system at work (GX270) the VC's are missing also.

John

---

### Post by macbuff on 2007-10-10
> **macbuff said:**
> I tried adding fbcon to /etc/modules and that did work up untill the most recent kernel on gutsy.  I just tried the method shown above and that didn't have any effect on my system.  (DELL D610 laptop) I'm using 2.6.22-24-generic.  On my DELL desktop system at work (GX270) the VC's are missing also.


I got the framebuffer console to appear by commenting out the entry in /etc/modprobe.d/blacklist-framebuffer for intelfb and adding fbcon to /etc/initramfs-tools/modules then rebuilding the initrd as in the post above.

If the system boots as normal, the consoles are still blank.

But removing 'splash' from the kernel entry in grub lets the framebuffer console appear.

Its a bit clunky, but it works.

John

---

