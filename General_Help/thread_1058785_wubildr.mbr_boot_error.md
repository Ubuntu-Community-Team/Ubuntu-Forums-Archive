---
title: "wubildr.mbr boot error"
date: 2009-02-03
forum: General Help
---

### Post by rodnas on 2009-02-03
recently downloaded ubuntu using Wubi.
it is currently on a separate partition.
Currently the OS will not boot, instead, the following error occurs:
```

File \ubuntu\winboot\wubildr.mbr
Status 0xc000000f

```
What steps can I take in order to perform a successful boot?

current platform - vista sp1

(also posted in Wubi but no activity there)

---

### Post by rodnas on 2009-02-03
/bump

---

### Post by rodnas on 2009-02-04
Are you guys serious, does nobody here know what to do?

---

### Post by luis_tercero on 2009-05-07
I have the same problem, i installed ubuntu 8.1 in a new partition, after i restart, when i got to choose ubuntu, get the next message:

file: \ubuntu\winboot\wubildr.mbr
status:0xc000000f

what can i do?

---

### Post by hd.deman on 2009-07-07
same problem((

---

### Post by legendbb on 2009-08-11
I have managed to installed more than 3 systems by using WUBI.

Until recently I forgot to supervise the initial reboot after WUBI installation stage in windows. I am not sure if that's the cause, probably not. Since I have certain impression, I did forget once or two in previous installation.

anyway no uBuntu boot.

MSG:
File:\wubildr.mbr
Status: 0xc000000f
info: The selected entry could not be loaded because the application is missing or corrupt.

Try all the uninstall/install combination I can imagine.

Anyone help?:confused:

---

### Post by legendbb on 2009-08-11
Just after submiting my previous reply.

I got in uBuntu installation stage. For my problematic machine, I definitely has a nested boot loader menu. When I click 1st uBuntu (actually it's XuBuntu I selected), I got the same error, the way I did is to clock Windows XP, then there is a same menu shows up.

Window XP
                       --->Windows XP
--->XuBuntu      (this one worked)
XuBuntu  (error)

I'll see if the bootloader gets fixed after uBuntu installation stage.

After full installation of XuBuntu, the bootloader is the same, I have to take the XuBuntu in the 2nd layer to get in.

I login in windows and compared boot.ini with working machines. They are exactly the same.

C:\wubildr.mbr is there.

Maybe MBR is corrupted pointing to nonexisting partition.

Any fix other than restore MBR for windows and reinstall uBuntu?

Thanks,

---

