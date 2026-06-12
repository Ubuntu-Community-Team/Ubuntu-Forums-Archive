---
title: "Kiba-Dock Not Working"
date: 2009-02-01
forum: General Help
---

### Post by StaticYum on 2009-02-01
I just installed kiba-dock and it work fine once install but after next boot when i double click the icon it does nothing..So i put it in the terminal and it gave me this :


"(kiba-dock:14530): GLib-GObject-WARNING **: cannot register existing type `GFileMonitor'

(kiba-dock:14530): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(kiba-dock:14530): GLib-GObject-CRITICAL **: g_type_register_static: assertion `parent_type > 0' failed

(kiba-dock:14530): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed"



can anyone tell me whats wrong please........cant resit the bouncing icon  and jazzy interface \\:D/

Thanks in Advance!!

---

### Post by adamgray1337 on 2010-10-09
I am having this same problem, it worked when i installed but when i rebooted my computer it started "scanning for disk errors" and now kiba wont launch. I tried sudo apt-get --purge remove kiba-dock, and i deleted the repositories from my sources list and tried re installing and putting the repositories back into the sources list. Still no help. When I open my terminal and type kiba-dock i get this error message:


Error (plugin.c @ line 207):
    '/usr/lib/kiba-dock/libdbus.so' is not loadable


(kiba-dock:2792): GLib-GObject-WARNING **: cannot register existing type `GFileMonitor'

(kiba-dock:2792): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(kiba-dock:2792): GLib-GObject-CRITICAL **: g_type_register_static: assertion `parent_type > 0' failed

(kiba-dock:2792): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed


I am running ubuntu 10.10 if that helps.

---

### Post by soad6 on 2010-11-10
I have the same issue as both of you. line 207 can't load. using ubuntu 10.10 -64 bit. I've tried from a deb file and it says that libglitz1 dependency needed. However libglitz1 no longer exists so I'm very unsure what to do now to fix this. ppa repo version doesn't work either if you try this. Not sure about compiling from source as instructed for 9.04 edition but I don't think it will make much difference, or if maybe there is another issue. I will look for another way to install this.

---

### Post by Tankerdog2002 on 2010-12-29
soad6

You can download libglitz1 here:

[http://packages.ubuntu.com/karmic/libglitz1](http://packages.ubuntu.com/karmic/libglitz1)

---

