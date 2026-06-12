---
title: "i can't access to my hard drive with ntfs format"
date: 2005-12-04
forum: Desktop Environments
---

### Post by César en Linux on 2005-12-04
hi

i can`t acces to my hard drive with ntfs format

i have 3 in total

what i can do???

---

### Post by Qrk on 2005-12-04
Assuming that your ntfs partition/drive is hda1

```
sudo mkdir /windows
```

```
sudo gedit /etc/fstab
```

add this line to it.
```

/dev/hda1       /windows 	ntfs    umask=0222        0       0
```

Edit: I noticed you were new, so heres a little advice. What I told you will automatically mount your windows hard drive to /windows on boot up. Once you've added the entry, 

```
sudo mount -a
```

will mount your windows directory, so you can access it.

Linux cannot write to ntfs, but it can read it just fine.

---

### Post by César en Linux on 2005-12-06
waht do the "Activo"(active) Boton ??

it can be use to access my windows file??

---

### Post by César en Linux on 2005-12-10
I do what you say, but I have a question

what it is mean "umask=0222        0       0"

---

