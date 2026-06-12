---
title: "0 Byte free Space"
date: 2008-12-04
forum: General Help
---

### Post by sim-value on 2008-12-04
HI !

my Computer is turning against me because im getting a new one ! :help:

Anyway ... since some days im constantly shown that i have 0 byte free space <-- not very much 

I already deleted about 400 MB but it still remains like that ...

This really sucks cause i dont know what to do cause i didnt do anything ... ( i think) i cant even edit text files or use auto-login cause firefox doesnt have space for cookies ...

Greetings /me

---

### Post by ajcham on 2008-12-04
Did you actually delete the files or are they still in your Trash?  Right-click the wastebasket icon in the bottom right hand corner and select 'Empty the Deleted Items folder'.

---

### Post by taurus on 2008-12-04
Can you post the output of this command from a terminal?

```
df -h
```
Also, make sure you empty your trash bin since files that you thought you have deleted are still resided in the trash bin.

---

### Post by sim-value on 2008-12-04
I actually never move files to Trash but use Shift + Del ...

Anyway i let Disk Usage Analyzer run und then deleted something while "Watch for changes in Home Folder" was on and now i atleast can use the space i got from deleting this files ...

Thanks for your help ...

Oh and by the way what does the DF output mean ?

> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             9.8G  8.6G  693M  93% /
varrun                189M  128K  189M   1% /var/run
varlock               189M     0  189M   0% /var/lock
udev                  189M   60K  189M   1% /dev
devshm                189M   12K  189M   1% /dev/shm
lrm                   189M   37M  152M  20% /lib/modules/2.6.24-21-generic/volatile
overflow              1.0M   40K  984K   4% /tmp
gvfs-fuse-daemon      9.8G  8.6G  693M  93% /home/sim/.gvfs


---

