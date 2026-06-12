---
title: "unity suddenly vanished"
date: 2013-04-13
forum: Desktop Environments
---

### Post by slgtheindividual on 2013-04-13
i did an update as usual and unity vanished, using ccsm i got it back but it's very slow and clearly not working properly, also my wifi stopped working, I have no idea what happened, I'm running am Aspire E1-571 with intel hd graphics 4000. I did a reinstall but it didnt help, unity and wifi worked fine on live cd. Any help would be greatly appreciated.

---

### Post by slgtheindividual on 2013-04-14
also running 

/usr/lib/nux/unity_support_test -p

gives me 

OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x301)
OpenGL version string:  2.1 Mesa 9.0.3

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no

but previously unity 3d worked perfectly

---

### Post by slgtheindividual on 2013-04-14
fixed this problem, apparently somehow my drivers had stopped working/been removed, i pressed ctrl+alt+t to open a terminal and ran

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```

then sudo apt-get update and sudo reboot

this fixed the problem

---

### Post by slgtheindividual on 2013-04-14
now on a completely unrelated note the mark this thread as solved isnt appearing under thread tools as usual, any ideas?

---

### Post by howefield on 2013-04-14
> **slgtheindividual said:**
> now on a completely unrelated note the mark this thread as solved isnt appearing under thread tools as usual, any ideas?

Currently, a work in progress, see here.

[http://ubuntuforums.org/showthread.php?t=2121377](http://ubuntuforums.org/showthread.php?t=2121377)

---

