---
title: "mounting ntfs"
date: 2009-02-26
forum: General Help
---

### Post by mosaic2s on 2009-02-26
When I boot into ubuntu 8.04, the autostart thunderbird - profile folder on ntfs partition - does not open - it says thunderbird is already running....

on closing this error message, if i open the thunderbird from menu - it works without a problem.

I feel the problem lies in ntfs mount command that does not start before thunderbird starts. How to resolve it?

---

### Post by taseedorf on 2009-02-26
Are you mounting the ntfs folder using fstab? or letting it mount by itself?

---

### Post by mosaic2s on 2009-02-26
i do not remember about fstab. most likely it is happening by itself.

---

### Post by taseedorf on 2009-02-27
try adding an  entry for your disk in fstab

sudo gedit /etc/fstab

than search google or forums for fstab windows example

---

### Post by vanadium on 2009-02-27
In this thread an example is given of how an ntfs partition can be mounted automatically during startup by including it in /etc/fstab.

[http://ubuntuforums.org/showthread.php?t=1081887](http://ubuntuforums.org/showthread.php?t=1081887)

If youu want specific help for your case, you should post the output of the command

```

sudo blkid

```

---

### Post by mosaic2s on 2009-02-27
Thanks.
Its done. The link worked. am learning some steps in linux.

---

