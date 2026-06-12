---
title: "Cant EJECT my CD not manualy and not from the player"
date: 2005-12-09
forum: General Help
---

### Post by leeb on 2005-12-09
OK I try to reinstall the pack of ioctl , that try t access the cd and now its work.


------------------------------------
I cant EJECT my cd.
the files browser can read files.

when I try eject the CD/DVD device  from the cd player I get this error

(eject) : ioctl failed: input/output error.

also I cant eject the device from the button on the device its self.

(I install Gstreamer-mad , and t swf-player - dont know if this realted but this is the last thing I install before i notice this problem)

thanks :)

---

### Post by conor on 2005-12-09
```
sudo umount /dev/hdc
sudo eject /dev/hdc
```

---

### Post by leeb on 2005-12-09
[QUOTE=conor]```
sudo umount /dev/hdc
sudo eject /dev/hdc
```[/QUOTE]

Thank you , next time I will try it.

:smile:

---

### Post by neighborlee on 2005-12-10
[QUOTE=leeb]OK I try to reinstall the pack of ioctl , that try t access the cd and now its work.


------------------------------------
I cant EJECT my cd.
the files browser can read files.

when I try eject the CD/DVD device  from the cd player I get this error

(eject) : ioctl failed: input/output error.

also I cant eject the device from the button on the device its self.

(I install Gstreamer-mad , and t swf-player - dont know if this realted but this is the last thing I install before i notice this problem)

thanks :)[/QUOTE]

you should use this instead:

[http://bugzilla.ubuntu.com/show_bug.cgi?id=11480](http://bugzilla.ubuntu.com/show_bug.cgi?id=11480)

umount is fine for maybe LFS but not any modern linux distro, especially considering ubuntu aims for 'ease of use'...people please start offering this URL if someone askes again ;-))

cheers
neighborlee

---

