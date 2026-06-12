---
title: "Problems with X..."
date: 2005-07-11
forum: Desktop Environments
---

### Post by robertobech on 2005-07-11
Every time I try to run mplayer or xine I get this error:

```
error while loading shared libraries: libXxf86vm.so.1: cannot open shared object file: No such file or directory
```

This wasn't happening until a few days ago... in fact, this libXxf86vm.so.1 doesn't even exist in my system...

When I try to install libxxf86vm1 through apt-get I get this error:

```
unable to stat `./usr/X11R6/lib/libXxf86vm.so.1.0' (which I was about to install): Permission denied
```

Does anybody know how to solve it

---

### Post by sanji on 2005-07-11
How about if you remove the application fist. Then you add-on the xine back and follow the instruction again. Actually, I'm fresh in uBuntu and i'm going to tell you my problem too.  :---) 

Hey, some can help me to solve video problem in my  xine!!! The audio - good. video - damn (its never appear) for .avi file. I'd already follow the guides to add-on xine in [http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by robertobech on 2005-07-12
It doesn't work...

Weird... now there is a libxxf68vm file on my Ubuntu system, but seems like it's damaged - it appears red when I do a ls. Worse: I tryed to copy the libxxf86vm file from my office's installation, but I just can't overwrite the one I have at home! It says some things about permissions that I don't have, but since I'm root, how can I not have permission to overwrite the file? I've tryed to re-install xorg, but it doesn't work, because it can't acess the libxxf66vm files. I'm really confused...

I'm pretty much stuck: I can't even install other packages, because it always says it can't lstat the damn file. Suggestions?

---

