---
title: "Loading kernel modules on startup"
date: 2005-10-14
forum: Desktop Environments
---

### Post by Jingo on 2005-10-14
How do I load the radeonfb module instead of vga16fb ?

To use the radeonfb in Hoary I just put it in /etc/mkinitrd/modules and a kernel reconfigure fixed it.

I have a Thinkpad T42 and vga16fb breaks hibernate function, but would still like a framebuffer console.


BTW. in which forum should I ask about kernel issues? I think there are to many forums now!!!

---

### Post by Dr. Nick on 2005-10-14
```
# /etc/modules: kernel modules to load at boot time.
```
Not sure if this is what you need or not as I am not real aware of the modueles mentioned, May just be able to type in the module name and have it work.

You can load the raedonfb here maybe and remove vga16fb all together if possible.

---

### Post by Jingo on 2005-10-14
[QUOTE=Dr. Nick]```
# /etc/modules: kernel modules to load at boot time.
```
Not sure if this is what you need or not as I am not real aware of the modueles mentioned, May just be able to type in the module name and have it work.

You can load the raedonfb here maybe and remove vga16fb all together if possible.[/QUOTE]

I would actually like the modules loaded just after the kernel is loaded, before the splash! In Hoary I had to make sure they went into kernels initrd-image.

/etc/modules is to far into the boot process.

---

### Post by Dr. Nick on 2005-10-14
Oh :( wasnt sure exactly when you needed them to load, I have never used any other way than /etc/modules so unfortanetly cant help, Hopefully someone else can

---

### Post by Psy-Q on 2005-10-16
Were you ever able to solve this? I have the same problem, and while I could figure out a few very crude hacks around it, it would be great to do this the "Ubuntu way".

Even just removing the bootsplash/progress bar and all the fb modules would work for me.

---

### Post by Jingo on 2005-10-17
No, I havn't found a solution yet.

I just want to use radeonfb instead of vga16fb and vesafb!

Somebody must know... it was very easy on Hoary.

---

### Post by Jingo on 2005-10-17
[QUOTE=Jingo]No, I havn't found a solution yet.

I just want to use radeonfb instead of vga16fb and vesafb!

Somebody must know... it was very easy on Hoary.[/QUOTE]

And... it is just as easy in Breezy... totally overlooked the /etc/mkinitramfs/modules

Add the modules to be loaded, and do dpkg-reconfigure linux-image-i686 and youre there.

---

