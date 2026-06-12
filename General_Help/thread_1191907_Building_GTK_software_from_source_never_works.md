---
title: "Building GTK software from source never works"
date: 2009-06-19
forum: General Help
---

### Post by ThinkBuntu on 2009-06-19
I'm running Ubuntu 8.04 LTS, and it seems that building GTK apps never works properly. I tried to set up the latest version of gnome-do as well as the guake terminal, and the same thing happened with each:

```

./configure
# OK, need to install intltool. Did that...
./configure
# the usual output follows, until:
checking for DEPENDENCIES... configure: error: Package requirements (
    gtk+-2.0 >= 2.10.0
    pygtk-2.0
    x11
) were not met:

No package 'gtk+-2.0' found
No package 'pygtk-2.0' found
No package 'x11' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DEPENDENCIES_CFLAGS
and DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I looked around my system, and all of these libraries exist, predictably. What do I need to do for ./configure to recognize them?

---

### Post by loell on 2009-06-19
my guess is gtk **2.10.0** didn't landed on 8.04 at the time it was released.

---

### Post by geirha on 2009-06-19
You need the corresponding -dev packages when you want to build/develop something that is to be linked to a library. You'll probably get most of the needed dependancies by installing the build dependancies for the gnome-do package in the repositories. You can install those with the command:
```
sudo apt-get build-dep gnome-do
```

If you need more libs, search for packages on the form lib*name*-dev. E.g., for the x11 that configure is missing, do
```
aptitude search 'libx11.*-dev'
```

---

### Post by ThinkBuntu on 2009-06-19
Well, that's a bummer. It's been a while...how do I check if this has been backported?

---

### Post by ThinkBuntu on 2009-06-19
> **geirha said:**
> You need the corresponding -dev packages when you want to build/develop something that is to be linked to a library. You'll probably get most of the needed dependancies by installing the build dependancies for the gnome-do package in the repositories. You can install those with the command:
```
sudo apt-get build-dep gnome-do
```

If you need more libs, search for packages on the form lib*name*-dev. E.g., for the x11 that configure is missing, do
```
aptitude search 'libx11.*-dev'
```
Thanks, that worked!

---

### Post by loell on 2009-06-19
probably enable the bacports repo, and basically query it with  apt-cache search.

but i've got a feeling this couldn't be backported.

---

### Post by ThinkBuntu on 2009-06-19
OK, I've built and installed the program, but Python's having trouble importing the pygtk module for some odd reason. In the REPL, I am able to import pygtk...

```

% guake
Traceback (most recent call last):
  File "/usr/local/lib/guake/guake.py", line 21, in <module>
    import pygtk
ImportError: No module named pygtk

```

Manually invoking the file with python from the terminal works, however...almost as though the file is using another python bin or is changing the search path (I am certain it is not doing the latter).

---

### Post by HermanAB on 2009-06-19
Howdy,

There is a simple trick to it.  If you want to compile applications, then first compile your kernel.  That ensures that the whole development system is configured properly.  After a kernel compile, you should not have any trouble anymore.

---

### Post by uRock on 2012-02-25
Necromancy

Thread Closed

---

