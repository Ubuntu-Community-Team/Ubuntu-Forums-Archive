---
title: "[Feisty &amp; Emerald] Windowframes missing"
date: 2007-05-08
forum: Desktop Effects &amp; Customization
---

### Post by OberstKlinck on 2007-05-08
Hi everyone,

After I uninstalled the fglrx drivers and all the other stuff that prevents my ATI Radeon 9600 SE from working properly, I now want those fancy desktop effects.
I activated the built-in ones (in Feisty Fawn), which is "Compiz", I think.

But I was told that I need another window decorator to be able to use cool themes they offer on sites like [http://www.gnome-look.org](http://www.gnome-look.org) and so I installed "Emerald".

The Emerald Theme Manager works as expected and the theme can be loaded, but then my problems began. Since I am not able to find a starter or something uncomplicated I tried to type "emerald" into the shell and got this:

emerald: Could not acquire decoration manager selection on screen 0 display ":0.0"

Okay, then after "emerald --help" showed me that there was "emerald --replace", that was my next attept. That did work out, but not really how it was supposed to, because my windows had now window frames, but only corners. Looked like this:

[[img]http://img367.imageshack.us/img367/7340/emeraldproblemub2.th.png[/img]](http://img367.imageshack.us/my.php?image=emeraldproblemub2.png)

I would be incredibly happy if anyone was able to help me getting my desktop pimped.
Thanks a lot,
OberstKlinck

---

### Post by EXCiD3 on 2007-05-08
I had the same problems when I tried to use Compiz (that comes with Ubuntu Fiesty). My windows looked the exact same. I have since switched to Beryl. Emerald is a theme manager that Beryl uses. It would not display when my desktop color was set to 16 bit. I had to change it to 24 bit mode in XORG.CONF. I don't know how to fix your problem, but I would also like to know how to fix it.

---

### Post by Ateo on 2007-05-08
This thread will probably assist you as it did me:

[http://ubuntuforums.org/showthread.php?t=423743](http://ubuntuforums.org/showthread.php?t=423743)

---

