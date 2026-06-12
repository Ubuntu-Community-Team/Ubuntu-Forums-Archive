---
title: "Xorg.conf"
date: 2008-08-02
forum: Desktop Environments
---

### Post by Psicolonia on 2008-08-02
Hi everyone,

I run the command  sudo displayconfig-gtk and chose my Intel i915.

now gnome is on low graphics I have no backup of xorg.conf and I can't run compiz!

Also (I don't know if it's related) I chaged my grub vga mode and can't see bootsplash now. I'm using vga=788 now but can't see anything (only letters) If I remove vga=xxx than I'll get the usplash and compiz but the effects will be very very slow compared to what they were before.

Can anyone help me out here???

thank you

---

### Post by overdrank on 2008-08-02
> **Psicolonia said:**
> Hi everyone,

I run the command  sudo displayconfig-gtk and chose my Intel i915.

now gnome is on low graphics I have no backup of xorg.conf and I can't run compiz!

Also (I don't know if it's related) I chaged my grub vga mode and can't see bootsplash now. I'm using vga=788 now but can't see anything (only letters) If I remove vga=xxx than I'll get the usplash and compiz but the effects will be very very slow compared to what they were before.

Can anyone help me out here???

thank you

Hi and what was the driver set at before you changed it? You may also try and use the xfix option in booting recovery mode.

---

### Post by Psicolonia on 2008-08-03
i can't remember what was the previous driver. could it be none?

---

### Post by Shmifty on 2008-08-03
> sudo dpkg-reconfigure xserver-xorgAnd follow the prompts

---

### Post by Psicolonia on 2008-08-03
i've done that several times. it only prompts for kernel framebuffer, keyboard layout and that's it! :(

anyone knows how i can restore the original xorg.conf (The one that was there at instalation time?) i have no backups in /etc/X11

---

### Post by Nergar on 2008-08-03
&#65279;I was playing with startupmanager when the system crashed, now X wont use Intel driver and it is using vesa. I tried with the displayconfig-gtk dialog but it doesn't work, xorg.conf has not changed. something changed and Xorg is not autoconfiguring X correctly. Maybe the vga=xxx has something to do. Remove it

---

### Post by Psicolonia on 2008-08-03
i've done that, everything is still the same

---

