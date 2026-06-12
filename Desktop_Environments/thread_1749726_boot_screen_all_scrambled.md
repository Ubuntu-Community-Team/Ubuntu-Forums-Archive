---
title: "boot screen all scrambled"
date: 2011-05-04
forum: Desktop Environments
---

### Post by ffeingol on 2011-05-04
I have an nvidia based graphich card.  With the upgrade from 10.10 to 11.04 I switched from the nvidia closed source drivers to the open source experimental drivers.  Everything works fine except the boot screens.  Instead of seeing the Ubuntu screen with the dots moving across I just get a jumbled screen.

I'm guessing it's related to the graphic it's trying to load / the graphics driver, but I just not sure how to fix / reload it.

TIA

---

### Post by deconstrained on 2011-05-04
You can fix this manually by setting the grub gfx mode and adding the uvesafb module to your initrd. This solution has been offered/posted many times for boot splash problems in the forums, and it has generally worked for me.

---

### Post by ffeingol on 2011-05-05
Are you referring to something like this tutorial: [http://blog.samat.org/2010/11/09/High-resolution-text-console-with-uvesafb-and-Debian](http://blog.samat.org/2010/11/09/High-resolution-text-console-with-uvesafb-and-Debian)

---

### Post by deconstrained on 2011-05-05
Yeah, pretty much. There are more tutorial blog post around though, if you look. High-res Plymouth splash screens in Ubuntu is possible and not that difficult.

---

### Post by ffeingol on 2011-05-05
All I'd really like to do is get the default Ubuntu stuff back (not install new).

---

### Post by deconstrained on 2011-05-06
You don't have to install a new Plymouth theme in the process.

Here's what's happening (most of the time, in the case of this issue): the "noveau" open-source graphics driver is initially used on livedisks and most default Ubuntu installations. That driver is used at boot time for rendering the Plymouth screen, which is why booting to a livedisk always shows a nice high-res splash screen. However, when you install the proprietary graphics driver, that module is disabled, so you either get a low-res or glitchy Plymouth. Thus, you need to include the "uvesafb" module in your initrd in order to get better framebuffer rendering at boot time, and configure the kernel parameters accordingly.

---

