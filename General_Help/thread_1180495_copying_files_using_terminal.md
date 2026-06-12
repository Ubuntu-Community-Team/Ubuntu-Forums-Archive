---
title: "copying files using terminal"
date: 2009-06-06
forum: General Help
---

### Post by gogreenpower on 2009-06-06
im copying my home folder onto an external usb drive using

sudo cp -r /home/kane /media/disk

and i got a blinking curser on the next line with no text, is this normal? it is a fairly big home folder, or should i get some type of message?

---

### Post by 3rdalbum on 2009-06-06
That's correct, cp does not print out status messages. It is copying.

When you get your command prompt back, then "cp" has finished and the copying has been successful.

---

### Post by colau on 2009-06-06
> **gogreenpower said:**
> im copying my home folder onto an external usb drive using

sudo cp -r /home/kane /media/disk

and i got a blinking curser on the next line with no text, is this normal? it is a fairly big home folder, or should i get some type of message?
The command is correct to copy directory.
```

man cp

```
;)

---

### Post by gogreenpower on 2009-06-06
is it generally quicker or slower to copy through the terminal?

---

### Post by colau on 2009-06-06
> **gogreenpower said:**
> is it generally quicker or slower to copy through the terminal?
Test it yourself.
Copy from terminal and copy from a file browser like nautilus.
See the difference.:D

---

### Post by qualudeburrito on 2009-06-06
> **gogreenpower said:**
> im copying my home folder onto an external usb drive using

sudo cp -r /home/kane /media/disk

and i got a blinking curser on the next line with no text, is this normal? it is a fairly big home folder, or should i get some type of message?
If you use, 

cp -rv

progress will be shown.  The "v" stands for verbose.

---

### Post by gogreenpower on 2009-06-07
ok its finished without any errors but its not in the external harddrive????
its coming from an ext3 hd to a ext4, would that make a difference?

changed it to ext3 and still no difference.

there not hidden.

do you need to mount the usb hard drive in the shell? as this is all i have access to?

---

### Post by colau on 2009-06-07
> **gogreenpower said:**
> ok its finished without any errors but its not in the external harddrive????
its coming from an ext3 hd to a ext4, would that make a difference?

changed it to ext3 and still no difference.

there not hidden.

do you need to mount the usb hard drive in the shell? as this is all i have access to?
Can you post
```

fdisk -l

```

---

### Post by gogreenpower on 2009-06-07
got it sorted, just had to mount the external usb hard drive with

*sudo mount -t ext3 /dev/sdb1 /media/disk*

then copy the files with

*sudo cp -rv /home/user /media/disk*

then unmount the drive with
[I]
sudo umount /media/disk[/I]



thanks for everyone that helped

---

