---
title: "How to mount USB from terminal?"
date: 2006-08-12
forum: Desktop Environments
---

### Post by ryan76 on 2006-08-12
I tried what was suggested in this thread [http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264) and now xserver is not loading. I get the message 'Failed to start the X server' surrounded by a whole lot of macrons.

I just want to copy my files to a USB drive and reinstall, but the live CD can't see them and I can't copy them to the USB drive from outside gdm because I don't know how to mount the USB.

Can someone help please? How can I make my files visible from the live CD I am using now, or mount the USB from terminal?

Thanks

---

### Post by davidsxls on 2006-08-12
try $ dmesg|tail
there must be something about your usb drive on /dev/sd?. if you don't have any scsi or sata device, it will be /dev/sda1 (first partition). 
to mount: $ sudo mkdir -p /media/usb_dripve && sudo mount -t auto /dev/sda1 /media/usb_drive
it will be mounted on /media/usb_drive

---

### Post by ryan76 on 2006-08-13
Thanks, I tried that and I got the message:
```

mount: you must specify the filesystem type
```

(I have to reboot out of the live CD then reboot it to use the internet every time I want to test something.. is there a way to not have to do that too??)

cheers

---

