---
title: "Kinetic frezes for one minute after restart or sleep"
date: 2022-10-24
forum: Desktop Environments
---

### Post by robertinams2 on 2022-10-24
After restart or sleep ubuntu desktop freezes on a brand new kinetic installation, usually within one minute for 60 seconds. During this time nothing happens but mouse clicks are still recorded and executed when the system continues again. This seems to happen only once, but also when the laptop is idle for some time, if you work on it normally, the system behaves good (no freezes)

During this period the log fills up with the following messages :

Oct 24 21:35:53 msi gnome-shell[2707]: The offending signal was g-signal on GDBusProxy 0x559e48c700d0.
Oct 24 21:35:53 msi gnome-shell[2707]: Attempting to run a JS callback during garbage collection. This is most likely 
caused by destroying a Clutter actor or GTK widget with ::destroy signal connected, or using the destroy(), dispose(),
 or remove() vfuncs. Because it would crash the application, it has been blocked.
Oct 24 21:35:53 msi gnome-shell[2707]: The offending callback was DBusSignalCallback().
Oct 24 21:35:53 msi gnome-shell[2707]: Attempting to call back into JSAPI during the sweeping phase of GC. This is mos
t likely caused by not destroying a Clutter actor or Gtk+ widget with ::destroy signals connected, but can also be cau
sed by using the destroy(), dispose(), or remove() vfuncs. Because it would crash the application, it has been blocked
 and the JS callback not invoked.
Oct 24 21:35:53 msi gnome-shell[2707]: The offending signal was g-signal on GDBusProxy 0x559e48c700d0.
Oct 24 21:35:53 msi gnome-shell[2707]: Attempting to run a JS callback during garbage collection. This is most likely 
caused by destroying a Clutter actor or GTK widget with ::destroy signal connected, or using the destroy(), dispose(),
 or remove() vfuncs. Because it would crash the application, it has been blocked.
Oct 24 21:35:53 msi gnome-shell[2707]: The offending callback was DBusSignalCallback().
Oct 24 21:35:53 msi gnome-shell[2707]: Attempting to call back into JSAPI during the sweeping phase of GC. This is mos
t likely caused by not destroying a Clutter actor or Gtk+ widget with ::destroy signals connected, but can also be cau
sed by using the destroy(), dispose(), or remove() vfuncs. Because it would crash the application, it has been blocked
 and the JS callback not invoked.
Oct 24 21:35:53 msi gnome-shell[2707]: The offending signal was g-signal on GDBusProxy 0x559e48c700d0.
Oct 24 21:35:53 msi gnome-shell[2707]: Attempting to run a JS callback during garbage collection. This is most likely 
caused by destroying a Clutter actor or GTK widget with ::destroy signal connected, or using the destroy(), dispose(),
 or remove() vfuncs. Because it would crash the application, it has been blocked.
Oct 24 21:35:53 msi gnome-shell[2707]: The offending callback was DBusSignalCallback().

---

