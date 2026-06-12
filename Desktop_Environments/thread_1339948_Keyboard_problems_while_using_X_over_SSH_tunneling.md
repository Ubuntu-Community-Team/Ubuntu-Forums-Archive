---
title: "Keyboard problems while using X over SSH tunneling"
date: 2009-11-28
forum: Desktop Environments
---

### Post by sm_news on 2009-11-28
Hello world:

I'm currently using Ubuntu 9.10 64-bit through Sun Virtual Box 3.0.12 r54655 on Mac OS X Snow Leopard (10.6.2)

My problem started when I upgraded from Ubuntu 9.04 32-bit to Ubuntu 9.10 64-bit. I can SSH into the Ubuntu VM using OpenSSH 5.3 which runs on my mac. I can type and use all of the command line programs perfectly, but when I run any X11 program where I can type into it (such as leafpad, xterm and other gnome apps), the keyboard output gets completely jumbled.

This is an example of what I type in and what it appears as in X:

q = -
w = =
e = reverse tab
r = forward tab
t = w
y = q
caps lock = space
space bar = n
back space = ,

Like I said, this affects all of X, not just gnome. Anyone have any ideas?

Thank you.

---

### Post by sm_news on 2009-11-29
Bump. No idea, anyone?

I've been looking around for solutions. I've encountered one problem and one "potential" solution:

First, the problem also happens while running Debian GNU/Linux, so I'm starting to think this may be a problem with Virtual Box. Which leads me to my second point: A while ago, some people posted a similar bug on the Virtual Box page here ([http://www.virtualbox.org/ticket/307](http://www.virtualbox.org/ticket/307)), indicating that the problem can be solved by "setting the DISPLAY variable to something that does not start with ":" (e.g. localhost:0.0)."

In Debian, the DISPLAY variable is set to localhost:10.0.

---

