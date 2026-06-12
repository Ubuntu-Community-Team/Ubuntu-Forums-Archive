---
title: "NetworkManager Applet Issue"
date: 2006-02-28
forum: Desktop Environments
---

### Post by danish_demon on 2006-02-28
hello all,

first of all, i have the (in)famous d-link dwl-XXX rt2570 usb wireless adapter.  my problem is that inconsistently, at boot-up, the d-link won't come up at the "configuring network interfaces" step (i.e. link light won't come on).  when this happens, when i log in the link light is on, but the NetworkManager applet ("nm-applet" in command terms)  will try to connect into a wired network via ethernet connection (which is disabled in system->admin->networking).  a lot of times it will say it gets connected to this "fictional" wired network.  then some times when i try to connect to my wireless network (which the NM applet sees) my system will hang and i have to hard reboot.

my question is, i guess, can i customize this applet (i believe i dled it as gtkwifi, but correct me if i'm wrong) to not even try to use the eth0 (wired ethernet) connection and go straight to wireless (if it sees any networks)?  is my inconsistent start-up connection just an issue with the system or is there something i can do to make this more reliable?

thank you all for your time.

---

