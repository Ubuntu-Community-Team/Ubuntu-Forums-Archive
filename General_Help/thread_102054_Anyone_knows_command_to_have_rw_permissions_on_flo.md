---
title: "Anyone knows command to have r/w permissions on floppy in ubuntu live cd"
date: 2005-12-11
forum: General Help
---

### Post by ank on 2005-12-11
hai guys , i use windows xp.
i just got ubuntu live cd. 
i cannot edit fstab, not allowed on live cd. 
i mounted my floppy drive using 

sudo mkdir /media/floppy0
sudo mount -t vfat /dev/fd0 /media/floppy0    [ after inserting the disk ]


the floppy indeed mount, but i can't copy any file to or from floppy. while copying from the floppy, it shows an IO error and gives option to retry or cancel. while trying to copy to the floppy, it tells me that i didn't have the write permission.

do u know any command that allows me to read/write the floppy, i.e., can u tell me any additional parameters , i could add to commands above , o rw or something like that.


guys , i will be greatful  if u answer.

---

### Post by nlindblad on 2005-12-11
Are you copying the files using sudo aswell?

If not, try a ```
sudo chmod a+rwx /media/floppy0
```

That will change the permissions and allow regular users to write/read/execute...

---

### Post by ank on 2005-12-12
[QUOTE=nlindblad]Are you copying the files using sudo aswell?

If not, try a ```
sudo chmod a+rwx /media/floppy0
```

That will change the permissions and allow regular users to write/read/execute...[/QUOTE]



Thank u nlindblad for replying. I just managed to work out a wonderful command.

sudo mkdir /media/f	
sudo mount -t vfat -o iocharset=utf8 -o umask=000 /dev/fd0 /media/f  
( only after inserting the disk )


wow, to my surprise it gave me r-w permissions on my windows formatted floppy.

---

### Post by nlindblad on 2005-12-12
[QUOTE=ank]Thank u nlindblad for replying. I just managed to work out a wonderful command.

sudo mkdir /media/f	
sudo mount -t vfat -o iocharset=utf8 -o umask=000 /dev/fd0 /media/f  
( only after inserting the disk )


wow, to my surprise it gave me r-w permissions on my windows formatted floppy.[/QUOTE]

Umasks are probably a better idea, yeah...

---

