---
title: "From Xterm to a full Ubuntu Unity session"
date: 2015-10-18
forum: Desktop Environments
---

### Post by tonymobily on 2015-10-18
I am setting up a large-ish network where users have pre-cooked Xvnc sessions created for them in advance. They can also reset those session via a web interface. We plan on releasing this as free software.
One of the requirements is starting a proper Ubuntu/Unity session starting from a "naked" X server (basically, just "X" running).
My understanding is that this includes:

[LIST]
[*]Launching dbus
[*]Running Unity
[/LIST]
I am after the full desktop environment, with top menu changing depending on the application shown, DBUS fully working, shortcuts working (CTRL-ALT-T), etc.
While for other environments it's easy to figure out what to run (the panel, the file manager, you're good to go), with Ubuntu I just cannot find the right sequence... help?

---

### Post by TheFu on 2015-10-18
Unity requires 3D accel GPUs. VNC doesn't provide that. C-A-T inside Unity opens the trash, BTW.

Perhaps LXDE or XFCE or Mate or .... any DE that doesn't mandate 3d-accel graphics will work?

---

### Post by tonymobily on 2015-10-18
Please note that this is not a question about VNC, but about X.
I am running FULL Unity sessions over VNC without any trouble, using lightDm (which then runs the unity-greeter).

Again, please ignore the VNC part... the question is about "how to go from xterm to Unity in X",,,

---

### Post by TheFu on 2015-10-18
Very cool. Didn't think that was possible without 3D-accel GPUs.  Perhaps **spice** could be used, but you didn't mention running KVM virtualization. BTW, spice promises near-native graphics performance, but I wouldn't trust it except over a secure LAN connection. Redhat's virtualization monster-framework includes spice and they consider their setup with SSL secure over the internet. I never got that working even in my own lab.

I suppose you've tried these answers already?
* [https://askubuntu.com/questions/320042/why-does-startx-usr-bin-unity-not-load-my-desktop-settings](https://askubuntu.com/questions/320042/why-does-startx-usr-bin-unity-not-load-my-desktop-settings)
* [https://askubuntu.com/questions/41809/how-to-start-x-and-unity-without-gdm](https://askubuntu.com/questions/41809/how-to-start-x-and-unity-without-gdm)  --- implies that Unity with everything cannot be started without GDM first.

---

