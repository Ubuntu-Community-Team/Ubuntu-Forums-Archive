---
title: "Screen Unreadable on Toshiba M30"
date: 2005-02-08
forum: Desktop Environments
---

### Post by Keymaster2K on 2005-02-08
Hi there, I just recently installed Ubuntu Linux on my Toshiba Satellite M30-710 notebook (using a dual-boot system, as I am new to Linux... other OS is Windows XP Pro SP2).  In booting the GUI for Ubuntu, the resolution of my screen is okay at 1280 x 800; however, my screen is incredibly unreadable... everything is 'blurry'.  I am trying to find the vertical refresh and horizontal synch rates to set manually, as I am sure this will work.  Toshiba has no idea - can anyone help me?

---

### Post by nab on 2005-03-09
Hi May1950,

I had the same problem on my m30x.

I solved the problem by changing the BIOS setting. I disabled the option, where the resolution is always scaled to fit the whole screen. 

Sorry, I forgot the exact title of the item.  ;) 

I hope this helps you :-)

Niko

---

### Post by gkoenig on 2005-07-22
I have the same problem with the nearly unreadable screen.
Changing the BIOS setting did nit work for me..
I installed the proprietary nvidia display drivers and everything works perfetely.
You only have to apt-get install nvidia-kernel-common and change the driver in xorg.conf from nv to nvidia

Regards,
Gregor

---

