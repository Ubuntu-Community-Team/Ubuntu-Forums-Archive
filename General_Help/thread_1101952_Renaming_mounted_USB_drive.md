---
title: "Renaming mounted USB drive"
date: 2009-03-20
forum: General Help
---

### Post by OBI_Ron on 2009-03-20
Hello Everyone,

I recently installed a Segate Free Agent external usb drive.  It mounted as
/media/FreeAgent Drive

Personally, I really hate spaces or any other special chars in file / path names.  Is there a way I can change the name it uses when mounting?

Also, I noticed that all of the files I copied to it are owned by root.  I was able to change permissions of the files using sudo 776 filename, but the files don't seem to respond to chown.

I tried sudo chown name filename, but the ownership stayed as root.

Any and all help is greatly appreciated.

---

### Post by kaibob on 2009-03-20
> **OBI_Ron said:**
> Hello Everyone,

I recently installed a Segate Free Agent external usb drive.  It mounted as
/media/FreeAgent Drive

Personally, I really hate spaces or any other special chars in file / path names.  Is there a way I can change the name it uses when mounting?
Have a look at the following howto:

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by OBI_Ron on 2009-03-20
kaibob,

Excellent!  Thanks for the help!  Iwas able to rename the mount.

Any ideas on the chown thing?

---

