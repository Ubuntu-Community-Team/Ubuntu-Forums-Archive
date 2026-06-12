---
title: "Small problem with mounting NTFS"
date: 2005-10-31
forum: Desktop Environments
---

### Post by WebLOCH on 2005-10-31
Hey guys...

  Just taken ubuntu mainstream on my harddrive, re-arranged all the partitions so windows takes up about 30gb including data files.  In doing so I took the advice of a friend and created three linux partitions;   "/"   "/boot"  "/home"

  Now after logging in I edited "fstab" to mount the partitions to "/home/windows/" but then attempted to remount but it always tells me there is no such mount point :P

  I know for a fact the folder exists, I am also referencing it correctly as it works fine if I specify "/mnt/whatever".

  I was wondering if any of you knew what the problem was?  Thanks in advance.

---

### Post by abou on 2005-10-31
Make sure that in fstab the file type is listed as NTFS and not as VFAT.  That is was what was causing me troubles.

---

### Post by WebLOCH on 2005-10-31
Thanks for the suggestion but I already checked, thanks all the same :(

By the way your avatar is insanely cool, i've loved megaman since I got my NES way back in the day, been hunting for megaman t-shirts, know where I can get any?

---

### Post by manicka on 2005-10-31
[QUOTE=WebLOCH]Hey guys...

  Just taken ubuntu mainstream on my harddrive, re-arranged all the partitions so windows takes up about 30gb including data files.  In doing so I took the advice of a friend and created three linux partitions;   "/"   "/boot"  "/home"

  Now after logging in I edited "fstab" to mount the partitions to "/home/windows/" but then attempted to remount but it always tells me there is no such mount point :P

  I know for a fact the folder exists, I am also referencing it correctly as it works fine if I specify "/mnt/whatever".

  I was wondering if any of you knew what the problem was?  Thanks in advance.[/QUOTE]

Why do you neeed it to mount as /home/windows. It works the same way as /mnt/whatever.

Is it the /home/windows folder you have created or /home/*username*/windows?

---

### Post by Nomad64 on 2005-10-31
First make sure that the directory that you are trying to mount your NTFS partition accually exists. As manicka said: "Is it the /home/windows folder you have created or /home/*username*/windows?" An easy way to check is to open up a console, and type: "cd /home/windows" and see if you can enter the folder (even if nothing is mounted there, if the folder is created, it will be there with nothing inside of it).

Also, double check that your fstab entry looks simular to this one (probably a different partition reference for you):
```
/dev/hda1       /home/windows/  ntfs    nls=utf8,umask=0222 0       0
```

---

### Post by WebLOCH on 2005-10-31
[QUOTE=manicka]Why do you neeed it to mount as /home/windows. It works the same way as /mnt/whatever.

Is it the /home/windows folder you have created or /home/*username*/windows?[/QUOTE]

I don't need to to be "/home/windows/" it is simply a matter of organisational preference, also I prefer not to have the two partitions showing as mount shortcuts on my desktop.

The folder is indeed "/home/windows/", I did double check because I keep making the same mistake myself.  Thanks for that suggestion too :(

---

### Post by manicka on 2005-11-01
This is my fstab entry for my ntfs partition. It may give you some ideas. It doesn't appear on my desktop. 

/dev/hda1       /tocos_c        ntfs     defaults,umask=002,nls=utf8 0 0

---

### Post by Nomad64 on 2005-11-01
Hum...although your fstab entry is different from the example I posted above, it would still work. Maybe a permission problem (doubtful)?

---

