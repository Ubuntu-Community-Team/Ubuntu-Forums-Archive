---
title: "How to change ntfs-3g automount options?"
date: 2009-01-08
forum: General Help
---

### Post by ffi on 2009-01-08
I would like to know how to change the default mount options given to ntfs-3g removable media

---

### Post by ffi on 2009-01-09
no one has any ideas?

---

### Post by mssever on 2009-01-09
I think you have to muck about with udev configuration. I tried that several years ago and found it very difficult. Ultimately, I was unsuccessful. The situation might have changed for the better since then.

---

### Post by ffi on 2009-02-04
I cannot find any rule in there to change ntfs-3g mount options

---

### Post by Gizenshya on 2009-02-04
just wondering... why the automount?

if its just the one drive, edit your fstab.

or, just manually mount the drive(s).  save a txt file with the command you want.

---

### Post by ffi on 2009-02-04
because they are removable media

> just manually mount the drive(s). save a txt file with the command you want.

not an option, it's not for me but for someone who can't be expected to get this.

---

### Post by lakersforce on 2009-02-04
> **ffi said:**
> I would like to know how to change the default mount options given to ntfs-3g removable media

...fstab...?

---

### Post by ffi on 2009-02-04
no, i want to change them for **removable** media

---

### Post by Gizenshya on 2009-02-04
hmmm...

you seem to be using "removable" with the meaning of "hot-swappable."

but I don't know how to set automount options.

a text file is just copy and paste, though.  If its in the same USB port, thats all that would need to be done anyway.  it would be the same sdxx unless another drive is added.  and the sdxx would be the only thing that would need to be changed anyway.

If its just absolutely not an option, then so be it.  But unless someone posts otherwise, it seems like it might just be the *only* option.

---

### Post by ffi on 2009-02-05
somewhere hal/udev must be told what to do with an ntfs-3g partition...

---

### Post by geirha on 2009-02-05
As far as I know, hal doesn't care about what partitions are on the drive. It just detects that a removable drive has become present and alerts gnome-volume-manager about it. gnome-volume-manager does the actual mounting. Don't know how to configure the mount options other than with fstab though.

---

### Post by 4MD D4D on 2009-02-05
their is a code to pull up automount options but its a force done through the terminal I will do some digging and see if i can find it

sorry I can't be more help at the moment

---

