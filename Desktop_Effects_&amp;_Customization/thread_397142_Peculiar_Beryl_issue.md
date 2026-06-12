---
title: "Peculiar Beryl issue"
date: 2007-03-30
forum: Desktop Effects &amp; Customization
---

### Post by Cloudy on 2007-03-30
Take a look at this:

[http://img.photobucket.com/albums/v82/CloudStrife888/wtf.png](http://img.photobucket.com/albums/v82/CloudStrife888/wtf.png)

Whenever I run "Beryl Manager" from the System Tools menu that's what happens. What's causing this? Why? I'm using the "ati" driver in my xorg.conf and according to glxinfo direct rendering is enabled:

```

travis@travis-laptop:~$ glxinfo
name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x4b
display: :0  screen: 0
direct rendering: Yes

```

What's the libGL warning mean btw..?

---

### Post by Cloudy on 2007-03-30
Anyone? :-k

---

### Post by ryankhart on 2007-04-10
You are in luck! This tutorial with help you very well. [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

---

