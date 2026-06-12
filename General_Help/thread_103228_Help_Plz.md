---
title: "Help Plz"
date: 2005-12-13
forum: General Help
---

### Post by cdsboy on 2005-12-13
I have an IBM T40 and i want to plug a usb external drive. This used to work. But i reinstalled ubuntu and now it won't auto mount. help plz or atleast tell me how to mount it by myself

---

### Post by aclaunch on 2005-12-13
I have used external Zip drives and they mount as "/dev/sda4". You could try plugging in the drive and look at "dmesg" and see if anything shows up and if so, what it is being labeled. Then just "sudo mount /dev/xxx /mnt/ext_drive".

Good Luck,
Alan

---

