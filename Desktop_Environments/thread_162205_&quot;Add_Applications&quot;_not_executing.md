---
title: "&quot;Add Applications&quot; not executing"
date: 2006-04-18
forum: Desktop Environments
---

### Post by lostplot on 2006-04-18
Hi all,

I'm unable to launch the "Add Applications" program, which is annoying because I'm a noob and its the only way I know how to install and remove things on ubuntu.

Any help would be very much appreciated.

Cheers, 
lostplot

---

### Post by aysiu on 2006-04-18
A few things:

1. What happens when you try to launch it? Any errors, or does it just fizzle out?

2. If it just fizzles out, go to Applications > Accessories > Terminal, type ```
gksudo gnome-app-install
``` and see if there are any errors. If any appear, post them back here.

3. In the meantime, just as point-in-click is the "advanced" version of Add Applications. You can go to System > Administration > Synaptic Package Manager.

---

### Post by lostplot on 2006-04-18
Thanks for the speedy reply.

When launching from Applications > Add Applications it does fizzle out without any error messages. 

I gave it a go with the terminal, and here's the results:

```
  File "/usr/bin/gnome-app-install", line 41, in ?
    from AppInstall import AppInstall
  File "/usr/lib/gnome-app-install/AppInstall.py", line 30, in ?
    import gtkmozembed
ImportError: libgtkembedmoz.so: cannot open shared object file: No such file or directory
```

The Synaptic Package Manager did the job nicely, but it told me this:

> The following problems were found on your system:

W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org)
breezy/free Packages (/var/lib/apt/lists/
packages.freecontrib.org_ubuntu_plf_dlists_breezy_free_binary-
i386_Packages) - stat (2 No such file or directory)
 ...etc.


:-k

---

