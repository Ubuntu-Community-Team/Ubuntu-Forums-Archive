---
title: "Xlib:  extension &quot;GLX&quot; missing on display &quot;:0.0&quot;."
date: 2006-03-03
forum: Desktop Environments
---

### Post by jnimble on 2006-03-03
I just finished installing wine, and when I tried running it heres what I got:

```
jnimble@ubuntu:~$ wine
wine: creating configuration directory '/home/jnimble/.wine'...
Xlib:  extension "GLX" missing on display ":0.0".
wine: '/home/jnimble/.wine' created successfully.
Wine 0.9.8
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
```
From experience with other distros I remember there should be a line in xorg.conf that is Load glx Load dri, but I dont see it in the auto-generated ubuntu xorg.conf. Should I add it or no? Is glx even necessary for Wine to operate?

Thanks again for the help everyone!

BTW, I have an ATI Radeon X700, already installed the 3D drivers ;)

EDIT: I thought I had my ati driver set up properly until I did fglrxinfo and got this:

```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!
```
I used the ubuntu provided drivers and followed [this guide](https://wiki.ubuntu.com/BinaryDriverHowto/ATI?highlight=%28driver%29%7C%28ati%29)

RE-EDIT: I definitely can't just add Load glx to xorg.conf because I tried that and X wouldn't start.

---

### Post by jpkotta on 2006-03-03
I would imagine that wine should work without GLX.  But let's try to get it working anyway.  Post the error log /var/log/Xorg.0.log and your /etc/X11/xorg.conf.  Also post the results of ```
lsmod | grep fglrx
```

---

