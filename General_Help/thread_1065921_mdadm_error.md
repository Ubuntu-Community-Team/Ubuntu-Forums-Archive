---
title: "mdadm error"
date: 2009-02-10
forum: General Help
---

### Post by Kissell on 2009-02-10
So, I was growing an array, adding another disk to it...  and the computer rebooted during that process...

When it came back up, i couldn't mount the array, mdadm kept saying "Segmentation Fault" and I was really worried.

I removed the entries from mdadm.conf and got it to reassemble, and everything is working now, except now when I do "mdadm --examine --scan" it shows that there are two arrays both at /dev/md0.  Except one array is using he old UUID and shows the old number of disks in the aray...  and the other array at md0 is using the correct number of devices and has the new UUID of the new assembled array.  

Everything is operating okay...  but I don't like that mdadm seems to think there are two arrays at /dev/md0.  Anyone know how to make this display correctly?

---

### Post by fjgaude on 2009-02-13
I suppose I'd do the conventional: re-name the **mdadm.conf** file, remove **mdadm** using **apt-get**, reboot. Then re-install mdadm and run this:

```
sudo mdadm --assemble --scan
```

A new mdadm.conf file will be auto created. Compare with the old. Let us know what you get.

---

