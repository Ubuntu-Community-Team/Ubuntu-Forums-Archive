---
title: "Framebuffer in console?"
date: 2006-01-13
forum: General Help
---

### Post by Pixel on 2006-01-13
I work alot with the console, I never use GDM, occasionally I'll use X...

I want to get some eye candy for my console... in the form of anice framebuffer (If you ever booted into a Gentoo CD, it's the font size and stuff)...

I'd like to try and get this working on my system, as well as getting mouse support in the console, but I'm not sure where to start.

---

### Post by podfish on 2007-01-27
mouse support is easy, install gpm, just like in gentoo.  Then you'll have pointy-clicky(and middle-clicky) console goodness.

I'm researching framebuffer right now.  i miss my 1280x1024 framebuffer console (with background) that I had in gentoo.

---

### Post by KingCharles on 2007-02-04
I have been able to get the console to 1680 x 1050 x 32, but the way I did it, was by recompiling the kernel and changing the framebuffer from **vga** to **nvidiafb** (I have an Apple Cinema Display 20" on an nvidia GeForce 4200 Ti).

The problem with this is:

[LIST=1]
[*] You have to re-compile the kernel, and of course this takes time
[*] If you want to use X you won't be able to use restricted drivers (at least not the nvidia ones) with the non-vga framebuffer
[*] Your system will most likely be set for only one resolution
[/LIST]

My knowledge of kernel tweaking is limited and I don't know whether is a way to simply change the framebuffer without having to re-compile the whole kernel.

---

### Post by maxadamo on 2008-03-19
come on, use this guide: 
[http://www.savvyadmin.com/2007/12/25/console-framebuffer-in-ubuntu/](http://www.savvyadmin.com/2007/12/25/console-framebuffer-in-ubuntu/)
:)
there is no need to recompile kernel.
Anyway I don't know how to setup a background image to the console (like gentoo)

---

