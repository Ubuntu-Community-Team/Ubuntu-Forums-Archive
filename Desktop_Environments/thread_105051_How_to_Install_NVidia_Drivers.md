---
title: "How to Install NVidia Drivers"
date: 2005-12-17
forum: Desktop Environments
---

### Post by jaywatkins on 2005-12-17
Hello,

I am playing around with edubuntu, and I am trying to get the drivers installed correctly.  The best resolution I can get is 600X480!  I followed a procedure from the Wiki, but it failed to give me the desired settings.  Although I do think the drivers are loaded, since an NVidia splash screen appears at boot.

The machine is a beige box, that I built, with an NVidia GeForce FX-5700 256MB.

I am sure someone had to do this at one time, any idea how?

Thanks

- Jason

---

### Post by serenity on 2005-12-17
did you follow the directions here:
[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)


that's specifically for ubuntu, not edubuntu, but they're both gnome so i'd assume it would work


then go to system -> preferences -> screen resolution to select what resolution you want

---

### Post by pmj on 2005-12-17
Since you get the splash screen, the driver should be working already. Your problem with resolution might be the same as the one I had, that Ubuntu fails to detect your monitor's horizontal and vertical frequencies. I had to find them with google by searching for the words samtron 96p (my monitor) and vertical and horizontal.

That gave me this page: [http://www.samtron.com/product/96p_spec.html]("http://www.samtron.com/product/96p_spec.html"), where I can see that for my monitor the horizontal frequency is 30-96KHz and the vertical frequency is  50-160Hz. These numbers has to be added to the file /etc/X11/xorg.conf, under Section "Monitor".

For me, this section looks like this:

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 96.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

---

### Post by jaywatkins on 2005-12-17
I did follow the how-to, but I still cannot change my resolution.  I am going through a KVM switch.  Should that matter?  I will try googling the monitor, but it is a generic Dell Trinitron P780.  Chock one up for Windows/Mac OS.

Thanks for the replies...:p

---

### Post by jaywatkins on 2005-12-17
That was it!

Setting the V-Sync/H-Sync refresh in xorg.conf worked.

Thanks again   :KS

---

