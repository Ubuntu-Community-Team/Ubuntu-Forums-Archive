---
title: "Dell Notebook, Gutsy and Suspend"
date: 2007-11-17
forum: Dell  Ubuntu Support
---

### Post by intargc on 2007-11-17
Has anyone gotten a resume from suspend-to-ram working on a Dell?  The problem I'm having is that it suspends just fine... however, when resuming, it is inconsistent.  Sometimes it works 100% perfectly, other times (about 75% of the time) it does not and I will get a blank screen.  Switching to a console and then back to X doesn't work and it's as if my keyboard is unresponsive, yet the hard drive has spun up.  The only thing that I can do is a hard reboot.

I'm using Gusty with the default kernel.  I'm on a Dell XPS M1330, but I'm sure that if anyone has gotten an Inspiron to work properly would be able to help me out as well as I don't believe the ACPI is any different.

I've scoured the internet, made numerous adjustments to /etc/default/acpi-support and nothing makes this consistently work! 

Thanks

---

### Post by LML on 2007-11-17
Suspend worked out of the box for me (Dell xps m1330). But perhaps this can help you:

l[http://blog.higherthings.org/borghardt/article/3077.html]("http://blog.higherthings.org/borghardt/article/3077.html")

---

