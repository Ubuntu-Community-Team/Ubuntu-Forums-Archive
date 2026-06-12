---
title: "ntfs mount/permissions problem"
date: 2005-12-23
forum: General Help
---

### Post by eheron on 2005-12-23
i mounted my xp drive and it shows up but every time i open it it tells me:

You do not have the permissions necessary to view the contents of "windows".

What i need to know is if i did something wrong when i mounted it and if so what can i do so that i can have access to that drive.

keep in mind that i only just started using linux.

---

### Post by drogoh on 2005-12-23
[http://www.psychocats.net/linux/mountwindows.php](http://www.psychocats.net/linux/mountwindows.php)

(courtesy of aysiu's sig)

---

### Post by eheron on 2005-12-23
i tried that but i get an error that says:

"wrong fs type, bad option, bad superblock on /dev/sd1, missing codepage or other error"

i typed everything exactly the way it was in the tutorial (except for the drive names of course)

---

### Post by darth_vector on 2005-12-23
can you post the output of

```
fdisk -l
```

and the exact commands that you typed in

---

### Post by omair.majid on 2005-12-23
[QUOTE=eheron]i mounted my xp drive and it shows up but every time i open it it tells me:

You do not have the permissions necessary to view the contents of "windows".
[/QUOTE]

Try changing the permissions of the "windows" ( the mount point ) to be readable by all 

sudo chmod o+r windows

---

