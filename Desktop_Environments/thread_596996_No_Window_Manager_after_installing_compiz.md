---
title: "No Window Manager after installing compiz"
date: 2007-10-30
forum: Desktop Environments
---

### Post by tynen on 2007-10-30
I have no window manager. The Window Tittle bar is completely missing. All of this occurred after reinstalling compiz. 

Cannot start the preferences application for your window manager

Window manager "compiz" has not registered a configuration tool

and whenever I try and install emerald I get this error.

emerald:
 Depends: libemeraldengine0 but it is not going to be installed
 Depends: libwnck18 but it is not going to be installed

---

### Post by tynen on 2007-10-30
Every thing I try and install that is a window manager complains about 

heliodor:
 Depends: **libwnck18** but it is not going to be installed

I try and install it and it says 

libwnck18:
  Depends: libwnck-common (<2.19) but 2.20.0-0ubuntu1 is to be installed

But libwnck-common is already installed!!

---

### Post by enz1m3 on 2007-11-02
Have you solved the problem? I'm having that same problem...

---

### Post by Jack78 on 2007-12-14
The solution seems to be to download the necessary packages (choose package files only in synaptic), and then navigate to /var/cache/apt/archives in nautilus and manually install the libemeraldengine0 package, then the emerald_0 package.

---

### Post by enz1m3 on 2007-12-14
Well, I couldn't really solve the problem that way.

I simply didn't install emerald, and I used a combination of other online tutorials, specifically related to ATI 200M Graphics Cards.

This happened to me because Compiz says it doesn't support my Graphic Board (they say it has no 3D accelaration).

Well, I've got Compiz Fusion working there (ok, so it takes like 1-2 minutes to load the login screen, but I can live with that!)

---

