---
title: "X11VNC General"
date: 2010-03-10
forum: Desktop Environments
---

### Post by makaveli0129 on 2010-03-10
Hi all i was wondering is it possible where i have the x11VNC and i access my computer to freeze the screens on the host computer but be allowed to do what i am doing on my display? ie. i access my home computer from laptop freeze home computer screen for user there but still have normal functions to see what is really happening on my laptop?

---

### Post by yoi on 2010-03-10
I think it is not possible since x11vnc ties your VNC session to the physical screen.

If you want to do something like that, you should just start a normal VNC server (e.g. vncserver, but not x11vnc) on your home computer and connect to the computer from your laptop.

---

### Post by krunge on 2010-03-10
I think yoi is correct that is it not possible to do what you ask for perfectly.  And using a virtual X server like vncserver or Xvfb is a really good way to make sure no one can see your desktop (and you can even access it locally if desired, just run vncviewer locally.)

However, I believe there are some **approximate** ways to do what is asked for:
[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-blockdpy](http://www.karlrunge.com/x11vnc/faq.html#faq-blockdpy)[/INDENT]
these aren't bullet-proof, but could be of use to keep nosey people from seeing what is on the screen.

---

