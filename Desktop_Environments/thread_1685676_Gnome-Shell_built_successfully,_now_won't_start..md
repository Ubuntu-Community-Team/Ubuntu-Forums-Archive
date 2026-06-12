---
title: "Gnome-Shell built successfully, now won't start."
date: 2011-02-11
forum: Desktop Environments
---

### Post by Arpy on 2011-02-11
So I went through the process of building gnome-shell following this guide [here]("http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html"). (Took forever). Anyways, I followed the little fixes, and it does start, but I run into the following problem.


```
paul@Pauls-Computer:~$ ~/gnome-shell/source/gnome-shell/src/gnome-shell --replace
Gtk-Message: Failed to load module "canberra-gtk-module"
Window manager warning: Log level 16: Accessibility: org.a11y.atspi schema not found. Are you sure that at-spi or at-spi2 is installed on your system?
Window manager warning: Log level 16: Accessibility: invalid module path (NULL)
Window manager warning: Log level 16: Accessibility: error loading the atk-bridge. Although the accessibility on the system is enabled and clutter accessibility is also enabled, accessibility support on GNOME Shell will not work

(mutter:2425): Bluetooth-WARNING **: Could not open RFKILL control device, please verify your installation
      JS LOG: GNOME Shell started at Fri Feb 11 2011 02:23:26 GMT-0600 (CST)
gnome-power-manager: error while loading shared libraries: libcanberra-gtk3.so.0: cannot open shared object file: No such file or directory
      JS LOG: Failed to acquire org.freedesktop.Notifications; trying again

(mutter:2425): GdmUser-WARNING **: Unable to load CK history: no seat-id found

** (ck-history:2448): WARNING **: Unknown option --since=2010-12-13T08:23:27.687540Z

(exe:2626): Gdk-WARNING **: XID collision, trouble ahead

(exe:2626): Gdk-WARNING **: XID collision, trouble ahead
  
(exe:2626): Gdk-WARNING **: XID collision, trouble ahead
^CHandling SIGINT.
Check failed: g_shutdown_pipe_write_fd != -1
Handling SIGINT.
Successfully wrote to shutdown pipe, resetting signal handler.
Shell killed with signal 2
```


I'm not very good with linux yet, and I'm not really sure what all this means. Pretty sure I'm missing a dependency or something perhaps?

---

### Post by nilarimogard on 2011-02-11
Did you remove the libcanberra-gtk-module.so file? Like so:

rm ~/gnome-shell/install/lib/gtk-3.0/modules/libcanberra-gtk-module.so


If you did and it still won't start, it might be that your graphics card / drivers are not supported. Gnome Shell works just fine on my desktop but it doesn't start on my netbook for some reason (most probably due to the graphics card).

---

### Post by Arpy on 2011-02-11
Yea I did.

I can actually use gnome-shell for like 5 minutes. But then it closes back out to normal gnome. Its kinda weird.

---

### Post by Arpy on 2011-02-12
Any ideas


-Don't mean to double post.. But I need this bumped-

---

### Post by nilarimogard on 2011-02-12
> **Arpy said:**
> Yea I did.

I can actually use gnome-shell for like 5 minutes. But then it closes back out to normal gnome. Its kinda weird.

Gnome Shell doesn't play very nice with some graphics cards... I've read it can use a lot of CPU on some computer so when it reaches a certain point, it crashes.

---

### Post by Buying_Some_Time on 2011-02-12
I have the exact same problem as the OP but, my shell doesn't crash it just gives me those errors, anyone know why?

---

### Post by __Ryan__ on 2011-03-14
Try running "jhbuild build" again. You are using the bleeding edge version of GNOME Shell so these repositories are constantly changing by the minute. Rebuilding will pull down and build the latest GNOME Shell and dependencies, hopefully a fix will be included.

Your second option is making sure your graphics card has the latest driver. If you are using NVIDIA card make sure you are using the recommended version. 

Good Luck!

---

