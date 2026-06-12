---
title: "mounting slave drive"
date: 2006-08-11
forum: Desktop Environments
---

### Post by firebird45331 on 2006-08-11
I can manually mount my slave drive by typing:

sudo mount -t ntfs -o umask=0222 /dev/hdb1 /mnt/windows

Then when I restart I have to remount it again.  How do I make it mount automatically

---

### Post by Ramses de Norre on 2006-08-11
```
echo "/dev/hdb1 /mnt/windows ntfs defaults,nls=utf8,umask=0222 0"|sudo tee -a /etc/fstab
```

---

### Post by firebird45331 on 2006-08-11
thank you, that worked.   Don't know for sure what that all meant but it got the job done, thanks.

---

### Post by Ramses de Norre on 2006-08-11
echo is used to get the line outputted, I then piped that output through tee which is a command to add text to a file, the -a option means append, it's the same as ">>" but with tee you can use sudo and with ">>" not.

The line is "device_node mountpoint filesystem options dump".

---

### Post by ajgreeny on 2006-08-11
Just to clarify things, what the command did was to add the line:-

/dev/hdb1 /mnt/windows ntfs defaults,nls=utf8,umask=0222 0

to your /etc/fstab file without opening it and editing it.
Just out of interest, I think there should really be an extra 0 (zero) after a tab space at the end.  Perhaps Ramses de Norre can let us both know if it matters or not.  I think the zero has an effect on the way the mounted partition is checked by fsck on bootup, btu I'm not sure how an ntfs partition is dealt with by fsck.
Any answers Ramses?

---

