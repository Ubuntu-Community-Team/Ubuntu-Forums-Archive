---
title: "Usb mounting problem"
date: 2009-05-04
forum: General Help
---

### Post by Brainy142 on 2009-05-04
Guy's I just did a fresh install of ubuntu and I have a problem....

I CANT mount anything via USB:confused:

---

### Post by taurus on 2009-05-04
What kind of USB is it?  Insert it into a USB slot and post the outputs of these commands from a terminal.

Applications -> Accessories -> Terminal
```
dmesg | tail 
sudo fdisk -l
```
p.s.  Remember to use the _safely remove hardware_ option (lower right corner) in windows to unmount it first before you unplug it from your machine.

---

### Post by Brainy142 on 2009-05-04
Nah it was just stupid permissions (who the hell decided to by DEFULT not to allow mounting of removable drives.)

---

