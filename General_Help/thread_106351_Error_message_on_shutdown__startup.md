---
title: "Error message on shutdown / startup"
date: 2005-12-20
forum: General Help
---

### Post by landcross on 2005-12-20
Can anyone tell me how to fix this error message on closedown and startup

"no final new line on etc stab"

Thanks

---

### Post by BathroomNinja on 2005-12-20
according to this thread: [http://www.linuxquestions.org/questions/showthread.php?threadid=338737](http://www.linuxquestions.org/questions/showthread.php?threadid=338737)

It looks like you were editing your fstab and somehow messed up the very last line.

Go to a terminal and type:
```

cat /etc/fstab

```

Copy that info, and paste it here.  be sure to use the 'code' tage by clicking on that option that looks like # next to the <>

---

### Post by landcross on 2005-12-20
This is what it shows

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1 /media/windows vfat umask=000 0 0bill@billntl:~$

---

### Post by BathroomNinja on 2005-12-20
OK.  Looks like you added the windows partition.  Just as a *temporary*test, try this.

Use ```
sudo gedit /etc/fstab
```
to edit your fstab

Put a # at the begining of the last line so that it looks like this:
```
#/dev/hdb1 /media/windows vfat umask=000 0 0
```

Then, add a new line with the following:
```

/dev/hdb1 /media/windows vfat iocharset=utf8,rw,user,umask=000 0 0


```

Just for kicks, make sure you hit ENTER after you type in that line.  So there should be an extra, blank, line at the end.  Save the file. Close gedit.

Now, in the terminal, type in:
```
sudo mount -a
```

Now reboot.  Let me know what happens.

---

### Post by landcross on 2005-12-21
Thanks for your help this has solved the problem. no error message shown

---

