---
title: "NTFS access / Windows XP"
date: 2006-01-10
forum: General Help
---

### Post by Buzbe on 2006-01-10
Hi,

I've just installed breezy badger (for about the 5th time, I love it) and I cant seem to access my NTFS paritions mounted on the desktop as apparently i dont have the correct permissions.  I'm not 100% sure but I reckon i could access them before.  I have windows XP home installed on them, has anyone else had this problem with windows xp and ubuntu?

Jon

---

### Post by TLE on 2006-01-10
If it is a permission problem you probably need to look in your /etc/fstab file. This is the file that contains information about how, and with what kind of permissions, the different filesystems are mounted. I belive there are examples of "NTFS fstab entries" in the built-in help function, (click somewhere on the desktop and press F1). Unfortenately I can't tell you what the exact names of the sections are since a have a danish version og Ubuntu, but I belive it is something like

Ubuntu 5.10 starter guide - (Left column) Windows partitions

It should contain some fstab examples so you can see if that is the problem and correct your fstab accordingly, (remember to back it up before you start messing with it)

Regards TLE

---

### Post by ember on 2006-01-10
I didn't have any problem - can you post your /etc/fstab?

---

### Post by Ocxic on 2006-01-10
add this line to your /etc/fstab
```

/dev/hdb1       /media/NTFS_Kev ntfs    defaults,umask=0222        0       0

```

where "hdb1" is your NTFS hard drive and making the mount point in /media will  put an icone on your desktop autmatically, just make sure you create a directory in /media

---

### Post by aysiu on 2006-01-10
[QUOTE=Buzbe]Hi,

I've just installed breezy badger (for about the 5th time, I love it) and I cant seem to access my NTFS paritions mounted on the desktop as apparently i dont have the correct permissions.  I'm not 100% sure but I reckon i could access them before.  I have windows XP home installed on them, has anyone else had this problem with windows xp and ubuntu?

Jon[/QUOTE] See the fourth link of my sig--very detailed directions.

---

### Post by Buzbe on 2006-01-13
ok, will post ftab when at home.  I'm just worried as i'm sure its supposed to work 'right out of the box' if you get what i mean?

---

### Post by hillbilly on 2006-01-13
Hmm...it didnt work out of the box for me. That is I had to manually edit the fstab file. And also the first time I edited it, I could only access the partitions as root, because I had not set the proper options in the /etc/fstab
My entry looks something like this
> /dev/hdb1       /media/Win/C ntfs    auto,user,umask=0222        0       0

Hmm...atleast i thnk its like that, will check it up once i go back home !!

---

### Post by aysiu on 2006-01-13
[QUOTE=Buzbe]ok, will post ftab when at home.  I'm just worried as i'm sure its supposed to work 'right out of the box' if you get what i mean?[/QUOTE] It's not supposed to. For some reason, Breezy adds your Windows partitions so that only root can read them. You have to modify your /etc/fstab to get them mounted correctly... see the fourth link of my sig for more details.

---

### Post by Robor on 2006-01-13
[QUOTE=Ocxic]add this line to your /etc/fstab
```

/dev/hdb1       /media/NTFS_Kev ntfs    defaults,umask=0222        0       0

```

where "hdb1" is your NTFS hard drive and making the mount point in /media will  put an icone on your desktop autmatically, just make sure you create a directory in /media[/QUOTE]
Thanks!  I had my WinXP and FAT32 partitions mounted but had to browse to them to access them.  Your mention of creating and using a mount point in '/media' got icons on my desktop for them.  :smile:

---

