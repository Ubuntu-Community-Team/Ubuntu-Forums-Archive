---
title: "No bluetooth in system&gt;preferences?  8.04"
date: 2009-01-28
forum: General Help
---

### Post by DXM31 on 2009-01-28
I am trying to connect my phone thru a bluetooth dongle and it keeps asking for a code.
I have tried "1234" because that is what is in /etc/bluetooth/hcid.conf
It doesn't work.
I also tried "0000" no go either.
So search some more and it found go to system>preferences>bluetooth
That doesn't exist.
In SPM it seems most of the bluetooth stuff is there but I am missing something.  What?
Thanks

---

### Post by gettinoriginal on 2009-01-28
Right click "Applications" edit menus, System, Preferences, and check bluetooth

---

### Post by DXM31 on 2009-01-28
> **gettinoriginal said:**
> Right click "Applications" edit menus, System, Preferences, and check bluetooth

Cool, thanks
I knew it would be something easy

---

### Post by finlost on 2009-03-14
I have a USB Motorola Bluetooth dongle that Ubuntu 8.04 finds, but it isn't giving me an icon in the upper right corner of my screen.  I do have the Bluetooth menu item turned on per the instructions two posts prior so I know Ubuntu is finding the dongle.

Am I correct stating that a Bluetooth icon should appear in the upper right of my screen?  Any troubleshooting advice to get the icon  to appear?

---

### Post by finlost on 2009-03-15
I found the answer to the missing icon in the upper right - alt+F2 and type bluetooth-applet.  From there, I checked the box on the General tab to "Only Display When Adapter Present".

---

