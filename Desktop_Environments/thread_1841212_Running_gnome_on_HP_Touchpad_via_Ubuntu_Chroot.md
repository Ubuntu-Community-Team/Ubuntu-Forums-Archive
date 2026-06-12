---
title: "Running gnome on HP Touchpad via Ubuntu Chroot"
date: 2011-09-09
forum: Desktop Environments
---

### Post by masterosok on 2011-09-09
I have installed gnome, gdm and ubuntu-desktop but I can't seem to get them to launch. I might not even be using the right commands. 

How do I check that I have everything installed to run start the ubuntu desktop?

When I try gdm I get the following error:

** (gdm-binary:24645): WARNING **: Couldn't connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory


When I try startx I get the following error:

hostname: Temporary failure in name resolution
xauth: (stdin):1: bad display name "KennethsHPTouchpad:0" in "add: command


Fatal server error:
Server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock


XIO: fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
after 7 requests (7 known processed) with 0 events remaining.
xauth (argv):1: bad display name "KennethsHPTouchPad:0" in "remove" command

---

