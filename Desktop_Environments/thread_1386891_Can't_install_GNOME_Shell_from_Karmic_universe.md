---
title: "Can't install GNOME Shell from Karmic universe"
date: 2010-01-21
forum: Desktop Environments
---

### Post by wersdaluv on 2010-01-21
I'm trying to install the GNOME Shell package from the official repo (universe). 

I get this: ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnome-shell: Depends: gobject-introspection-glib-2.0 but it is not going to be installed
               Depends: gobject-introspection-freedesktop but it is not going to be installed
               Depends: gobject-introspection-repository but it is not going to be installed
E: Broken packages

```

I checked on Synaptic. I didn't see any broken package

Any idea why?

---

### Post by ssmithy on 2010-01-21
Check out this thread:

[http://ubuntuforums.org/showthread.php?t=1354787&highlight=gobject](http://ubuntuforums.org/showthread.php?t=1354787&highlight=gobject)

---

### Post by wersdaluv on 2010-01-21
That solved it! Thanks :)

---

