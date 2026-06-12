---
title: "Re-Installing X"
date: 2010-01-01
forum: Desktop Environments
---

### Post by jimford on 2010-01-01
For some reason X seems to be corrupted and won't start.

I can hit the ESC button whilst booting and get to the GRUB menu - and from there I can get a root console.

How can I reinstall X from the console, please?

As I found Gnome glacially slow on the laptop I use, I want to use Xfce4. I've previously tried logging off to select Xfce4 as the desktop, but the laptop just shuts down. How can I manually configure the default desktop to be Xfce4 - I can't find any obvious config file that would do it?

Jim

---

### Post by SalahTr on 2010-01-01
In  **Grub** menu, you should choose **Ubuntu 9.10, ....(recovery mode)**.
After booting execute :
```
sudo aptitude update && sudo aptitude install xubuntu-desktop
```

---

### Post by jimford on 2010-01-01
Thanks for the reply.

I find I now can't even get a console!

The boot process proceeds, but I then get a warning that the display is not correctly configured and will run in low resolution. On proceeding it hangs with a blank screen.

I suspect that it's the Xserver that's blown!

Is there any way I can interrupt the boot process to go straight into a console?

Jim

---

