---
title: "problems with mount, please help!!!"
date: 2005-07-11
forum: Desktop Environments
---

### Post by yoshic on 2005-07-11
hi guys, how can i mount this filesystem  , 'fdisk -l' gives me this:

Device        Boot    Start    End     Blocks            Id         System
/dev/hdb1                    1    20325 10243768+   ef         EFI (FAT-12/16/32)


please help!!!!, ](*,)  ](*,) 

thanks guys, have a nice day.

---

### Post by adwait on 2005-07-11
Add the line

/dev/hdb1 <TAB>  /mnt<location  <TAB>   auto     rw,uid=1000,uid=1000  <TAB>  0 <TAB> 0 to your /etc/fstab.

FOR EDITIng that file,
sudo gedit /etc/fstab

---

### Post by yoshic on 2005-07-11
hi, thanks, but when i try to mount it, it says:

mount: you must specify the filesystem

any ideas???????
i'll be here all night  ](*,)  ](*,)  ](*,)  ](*,)

---

### Post by Wolki on 2005-07-12
try replacing auto in what adwait wrote with vfat.

oh, and don't forget that the directory you want to mount into has to exist, so "mkdir /mnt/<insert dir name here>"

---

### Post by yoshic on 2005-07-12
[QUOTE=Wolki]try replacing auto in what adwait wrote with vfat.

oh, and don't forget that the directory you want to mount into has to exist, so "mkdir /mnt/<insert dir name here>"[/QUOTE]

thanks, but it says  that is the wrong filesystem  ](*,)  ](*,)

---

### Post by adwait on 2005-07-13
Uhh sorry.......I fotgot thje <TAB> after the word auto :). Does that help?

---

### Post by alastair on 2005-07-13
Look at the filesystem possibilities in :

man mount

Then, make sure /mnt/tmp exists (as a test) and try :

mount -t vfat /dev/hdb1 /mnt/tmp
mount -t fat /dev/hdb1 /mnt/tmp
mount -t fat -o fat=12 /dev/hdb1 /mnt/tmp
mount -t fat -o fat=16 /dev/hdb1 /mnt/tmp

Something here might work ....

---

### Post by yoshic on 2005-07-13
thanks guys, il'll check it tonight, by the way, (i suppused that i needed put a tab after 'auto')

---

### Post by yoshic on 2005-07-15
snothing works!!! this is driven me crazy, any other suggest???? ](*,)  ](*,)  ](*,) 

please help!!! ](*,)  ](*,)

---

### Post by uniko on 2005-07-15
You could try:
mount -t msdos /dev/hdb1 /mnt/tmp

Worked for me once.

---

### Post by yoshic on 2005-07-16
thanks guys!!! for your help it's been helpful   :grin:  :grin:

---

