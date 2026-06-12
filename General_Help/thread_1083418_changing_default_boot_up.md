---
title: "changing default boot up"
date: 2009-02-28
forum: General Help
---

### Post by simon dew on 2009-02-28
I just installed Xubuntu onto an Asus Eee 710 with wireless and web cam, I find that on the default boot up 'Ubuntu 7.10, kernel 2.6.22.16-generic' that the system can't see the wireless network card although if I boot up on the line 'Ubuntu 7.10, kernel 2.6.22.14-generic' everything works a treat. 
Q1, How can I either remove the .16 line or make the .14 the default and or
Q2. how can I fix the .16 line?

---

### Post by thtrgremlin on 2009-02-28
all of your boot entries are in /boot/grub/menu.lst

```
gksudo gedit /boot/grub/menu.lst
```

It is fairly straight forward, and gives a lot of directions. The actual entries are at the very end.

If you would like some help editing that file then just post the contents here and can help you.

Best luck.

---

### Post by -kg- on 2009-03-01
> **simon dew said:**
> I just installed Xubuntu onto an Asus Eee 710 with wireless and web cam, I find that on the default boot up 'Ubuntu 7.10, kernel 2.6.22.16-generic' that the system can't see the wireless network card although if I boot up on the line 'Ubuntu 7.10, kernel 2.6.22.14-generic' everything works a treat. 
Q1, How can I either remove the .16 line or make the .14 the default and or
Q2. how can I fix the .16 line?

I don't think that anything in GRUB would affect the ability of the new kernel to "see" the wireless card.  That would be in the drivers, which you may need to update or otherwise change or reinstall to function correctly.  That is beyond my scope.

If you want to automatically launch the .14 kernel until you can get the .16 working, all you have to do is edit your menu.lst as thtrgremlin has suggested.

Look a little way down the file, and you will find a line that says,

> default		0

If your menu.lst is set up like mine, you should change this to:

> default		2

That should put you on the previous kernel to be auto-launched.

Alternatively, you can install "Startup Manager" through Synaptics.  Launch Synaptics and do a search for "startup manager' then check it for installation.  Once it is installed, you can launch it from "System/Administration/Startup-Manager" and you will have the ability to change which kernel to boot from automatically from the starting page.

---

### Post by simon dew on 2009-03-01
Thanks for incredibly fast responses to my questions. I'll have a crack at downloading the startup manager as I can't seem to find a an editable forum for the command lines either in the applications/accessories/terminal  or on hitting esc after the bios has loaded and hitting 'e' for edit or 'c' for command line. I'm a bit of a greenhorn to open source software but I like what I see!

Many thanks
S.

---

### Post by thtrgremlin on 2009-03-01
> I can't seem to find a an editable forum for the command lines

Not sure what you mean, but happy to help further if you could elaborate on what you mean.

Good luck

---

