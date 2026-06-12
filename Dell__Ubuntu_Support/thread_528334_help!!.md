---
title: "help!!"
date: 2007-08-17
forum: Dell  Ubuntu Support
---

### Post by Janer on 2007-08-17
Hi,My pc is an INSPIRON 6400 and i have a problem. the instalation present this error "Failed to start x server (your graphical interface). It is likely that it is not set up correctly. Woul you like to view the x server output to diagnose the problem?

---

### Post by JcZndeR on 2007-08-17
try reconfiguring ur xorg config with:

```
sudo dpkg-reconfigure xserver-xorg
```

or if u have a nvidia card use the software at [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
works well for me.. =)

---

