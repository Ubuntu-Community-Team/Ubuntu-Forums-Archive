---
title: "Caps lock and control not swapped with second monitor"
date: 2020-10-21
forum: Desktop Environments
---

### Post by mcarro on 2020-10-21
Hi. I am using Ubuntu 20.04 in a Lenovo Thinkpad Carbon X1 6th Gen. with an external monitor connected through USB C and an HDMI adapter. I swap Ctrl and Caps Lock using Gnome Tweaks. Everything is fine, except that about one week ago key swapping stopped working.  It happens consistently when doing as follows:

- Use the laptop disconnected, with Ctrl and Caps Lock swapped.
- Suspend laptop.
- Connect to docking station (monitor and keyboards are attached to docking station).
- Open laptop to resume.

Then, the Ctrl and Caps Lock are not swapped.  This does not happen when I resume without being connected.  

I am not sure whether the Gnome session has to redo the swapping every time the X Server resumes, and this is not happening when an external monitor is connected, or whether what happens is the opposite: Gnome is undoing the swapping when starting with an external monitor connected - or something entirely different.  Any hints as to where I could check what is going on?

Thanks in advance,

Manuel

---

