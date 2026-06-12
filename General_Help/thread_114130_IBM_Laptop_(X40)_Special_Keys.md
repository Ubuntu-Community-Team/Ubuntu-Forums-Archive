---
title: "IBM Laptop (X40) Special Keys"
date: 2006-01-07
forum: General Help
---

### Post by mgchan on 2006-01-07
Is it possible to have the back/forward keys and trackpoint button (allows pushing down the trackpoint to act as a click) to work?  I can get wireless to turn off with Fn+F5, Fn+F3 turns the screen off, and contrast works.

Also, is there a way to link the volume buttons to volume control, so that pressing mute will show that it did something?

---

### Post by crash0 on 2006-04-13
i'm also very inetersted in that... i've got an ibm thinkpad r40e and none of the special buttons work :(

---

### Post by chacon on 2006-06-05
I am using 6.60 LTS and most of the button work... already.. the volume  and mute keys provide feedback some ubuntu packages.  I got the trackpoint to work by adding this to my xorg.conf:

       Option          "EmulateWheel"          "on"
        Option          "EmulateWheelButton"    "2"

I got the backward and forward nav keys to work but broke when i upgrade firefox..... :-(

---

