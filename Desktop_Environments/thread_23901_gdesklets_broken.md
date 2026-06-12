---
title: "gdesklets broken"
date: 2005-04-04
forum: Desktop Environments
---

### Post by danip on 2005-04-04
gdesklets broke on me after a system update not sure what the problem is.  I want to compile it from source now since i miss having it on my desktop.

```
checking for pygtk-2.0 >= 2.4.0 pyorbit-2 >= 2.0.1 gnome-python-2.0 >= 2.6.0... Package ORBit-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `ORBit-2.0.pc'
to the PKG_CONFIG_PATH environment variable
Package 'ORBit-2.0', required by 'PyORBit', not found

configure: error: Library requirements (pygtk-2.0 >= 2.4.0 pyorbit-2 >= 2.0.1 gnome-python-2.0 >= 2.6.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.


```

I get that error during the compile.  I went through synaptic to see if I could find those packages.  I found all sorts of ORBit's and pyorbit packages, I installed them and yet I still get the error.

---

### Post by Xian on 2005-04-04
[QUOTE=danip]I get that error during the compile.  I went through synaptic to see if I could find those packages.  I found all sorts of ORBit's and pyorbit packages, I installed them and yet I still get the error.[/QUOTE]
Gdesklets is looking for the corresponding development libraries. Open Synaptic and look for your pyorbit-devel, python-devel, or orbit-devel packages. You don't need to install all of them as this is just redundant, but for example just find what type of pyorbit or python application you are running that is similarly named to what Gdesklets is complaining about, and then install the matching devel package.

---

