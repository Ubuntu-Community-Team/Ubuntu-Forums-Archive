---
title: "Problems with X libs"
date: 2009-03-18
forum: General Help
---

### Post by MargaretG on 2009-03-18
Hello,
I am very new to Linux, and I am trying to learn X programming.I am trying to create an X window in C++, thore code compiles but doesn't link with errors "undefined reference" for functions like XOpenDisplay, XCreateWindow etc. I read that libraries should be under /usr/X11R6/lib, but my X11R6 directory contains only bin folder and no lib folder. Does anybody know how do I get the required libraries? And what are their names?
Thank you for your help,
Margaret

---

### Post by snova on 2009-03-18
> **MargaretG said:**
> I am very new to Linux, and I am trying to learn X programming.

X is pretty low-level, you would be well advised to learn Gtk+ (Gtkmm for C++) instead.

> I am trying to create an X window in C++, thore code compiles but doesn't link with errors "undefined reference" for functions like XOpenDisplay, XCreateWindow etc.

Add **-lX11** to your compile line. Including the headers is not enough, you must also link in the libraries or they are not accessible at runtime.

> I read that libraries should be under /usr/X11R6/lib, but my X11R6 directory contains only bin folder and no lib folder. Does anybody know how do I get the required libraries? And what are their names?
Thank you for your help,
Margaret

I don't think /usr/X11R6 is used on Ubuntu, at any rate, it contains virtually nothing on my system. They're in /usr/lib, along with all the rest of the libraries on your system.

---

### Post by MargaretG on 2009-03-19
Thank you so much for your prompt reply. It helped a lot, I finally was able to create my first X window today. I will look into Gtk+.
Thank you,
Margaret

---

