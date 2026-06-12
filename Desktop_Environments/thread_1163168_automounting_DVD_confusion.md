---
title: "automounting DVD confusion"
date: 2009-05-18
forum: Desktop Environments
---

### Post by slumbergod on 2009-05-18
Hi all,

I am been search for a while and can't seem to find a solution (probably because I am not really sure what search parameters to use). If someone knows more perhaps you can help me out...

The problem...
When I burn a data DVD, I give it a title (like "archive-disc"). When I go to reinsert the disc it automounts as expected, but not entirely the way it should. In thunar or places, the disc is listed under the name I gave it. Under /media it is not mounted under its name, but instead cdrom0.

I notice when it is automounting I get a warning box popping up saying something like "Could not mount cdrom0
mount: block device /dev/scd0 is write-protected, mounting read-only".

This is frustrating me and I remember I had this problem under Hardy. Then along came Intrepid and it was fixed (along with lots of other small but annoying issues). It seems for me that with the release of Jaunty, many of the old annoying issues I had have suddenly come back.

I thought I would see if I could sort the issues out before I decided on rolling back to Intrepid. Does anyone know more about why media seem to be mounted under two names in Xubuntu?

(I have gnome-services disabled).

---

### Post by slumbergod on 2009-05-19
Actually, I discovered the reason why. For some reason Xubuntu ships with an entry in fstab as well as the automounting feature. I just commented out the cdrom entry in fstab.

---

