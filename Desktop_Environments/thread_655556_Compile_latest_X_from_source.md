---
title: "Compile latest X from source"
date: 2008-01-01
forum: Desktop Environments
---

### Post by chocolatetoothpaste on 2008-01-01
Hey everyone,
  I've been searching around the net and these forums, but can't seem to find anything that would get me started.  I want to compile the latest version of X from source.  There is no real need to do this, other than for my education.  I'm trying to deepen my knowledge of linux, so I thought this might be a challenging task to undertake.  I'm moderately comfortable with compiling, I've done it many times.  But with X, I don't know which packages to download and compile.  Another question is, should I just 'install' it once compiled, or should I use 'checkinstall' to create .deb's and install from there?  Any advice one can offer would be appreciated.

---

### Post by tzulberti on 2008-01-03
To know the dependencies, you could use the command: apt-cache show xserver-xorg (no need for sudo). It will show you the dependencies, and much more info.

---

### Post by ~LoKe on 2008-01-03
While compiling it'll tell you if you're missing any dependencies, so just figure that out when you do it.

As for make install vs checkinstall...I recommend creating the debs and installing it that way, so it's easier to remove it later if you must.

---

### Post by chocolatetoothpaste on 2008-01-17
> **~LoKe said:**
> While compiling it'll tell you if you're missing any dependencies, so just figure that out when you do it.

As for make install vs checkinstall...I recommend creating the debs and installing it that way, so it's easier to remove it later if you must.
Will it matter which order I install components in?  I guess those are my main questions, which archives to download/compile and in what order.  I'll give it a try...

---

