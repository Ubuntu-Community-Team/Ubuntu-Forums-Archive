---
title: "IMG backup of USB"
date: 2009-03-05
forum: General Help
---

### Post by Ofloo on 2009-03-05
I want to make a backup of an usb stick of mine, how do I make such a backup, I know you're supposed to use dd but I have no clue how to do this, anyone any suggestions?

EDIT: maybe I should include that this is a bootable usb stick.

---

### Post by kanikilu on 2009-03-05
I think you want to specify the usb drive as the in file (if=...) and the location you want to save it to as the out file (of=...). Something like:

```
dd if=/dev/sdb of=/home/username/usbimage.img bs=1024
```

Obviously replace /dev/sdb with whatever your usb drive is (you can use *sudo fdisk -l* to check that). The out file doesn't need an extension (.img), but I use it out of habit.

---

### Post by Ofloo on 2009-03-08
Thank you I'll give it a shot

---

