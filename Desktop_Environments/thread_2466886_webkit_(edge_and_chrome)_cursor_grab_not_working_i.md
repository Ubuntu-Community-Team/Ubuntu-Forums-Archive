---
title: "webkit (edge and chrome) cursor: grab not working in Gnome (working in KDE) on 20.04"
date: 2021-09-09
forum: Desktop Environments
---

### Post by melser.anton on 2021-09-09
I am not sure where exactly this should go, or whether it is simply a Gnome bug that has been fixed in more recent versions of Gnome that Ubuntu doesn't want to backport. In any case, on webkit in Gnome on Ubuntu 20.04 the `cursor: grab` cursor style doesn't change from the default cursor. I saw the behaviour on two different Gnome installs (Chrome 93 and Chromium Edge 95), and `cursor: grab` works fine on the other webkits I tested in KDE (same ubuntu but logging into KDE as opposed to Gnome) and Windows and it also works fine on Firefox in the same Gnome where webkit doesn't work.

I looked but couldn't find anything - is this a known bug? Can anyone else repro?

EDIT: actually after installing KDE on one of the ubuntus and rebooting, the grab hand now IS appearing as normal. However, on the other (VM) install it is NOT, even after a reboot. This is a weird bug...

---

