---
title: "XGL+Beryl+fglrx splash background problem"
date: 2007-04-10
forum: Desktop Effects &amp; Customization
---

### Post by amohanty on 2007-04-10
Hi,

So I got beryl installation down to a script :). I can install from beryl-svn and uninstall with one command and a few mouse clicks. Finally no more mac-envy.

With just one teeny problem. When I log-in the background to my gnome splash is this grainy, gray and white, no signal tv kind of stuff. I have looked all over the place and cannot figure out how to solve it. A massive analysis of the logs don't tell me anything either. 

I am guessing this has more to do with Xgl rather then beryl because metacity on gnome comes up with the background I specified in the login manager settings.

Any help or pointers would be greatly appreciated.

Thanks.
AM

---

### Post by joeally on 2007-04-14
I'm having the same problem

---

### Post by rbrtoclto on 2007-04-20
You need to start Xgl with the -br option, e.g. in */usr/local/bin/startxgl.sh* you might have something like:

```
Xgl :1 -br -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
```

---

