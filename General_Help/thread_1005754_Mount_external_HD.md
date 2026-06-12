---
title: "Mount external HD"
date: 2008-12-08
forum: General Help
---

### Post by mayagrafix on 2008-12-08
I have a USB external HD. When I turn it on, it used to mount itself and show up in desktop. No more. Why?

Also used to be a mount program in Applications Menu but do not see it there anymore. WTF?

TIA

---

### Post by lovelyvik293 on 2008-12-08
You can mount the USB from the nautilus.

---

### Post by taurus on 2008-12-08
Is your external harddrive a ntfs filesystem?  The last time you used it, did you just unplug it from windows or did you remember to use the safely remove hardware icon to unmount it first before you unplugged it?

What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by mayagrafix on 2008-12-08
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3555    28555506   83  Linux
/dev/sda2            3556        3648      747022+   5  Extended
/dev/sda5            3556        3648      746991   82  Linux swap / Solaris
rafael@Inspiron:/$



Yes it is NTFS windows HD i use for B/U and Yes, i did remove safely first umount the unplug

---

### Post by mayagrafix on 2008-12-08
> **lovelyvik293 said:**
> You can mount the USB from the nautilus.

Me thinks that is how i did last time but now no show :confused:

---

### Post by mayagrafix on 2008-12-09
Ok, the ipod mounts itself beautifully when I plug it in the USB dock. Even my motorola phone S6 phone connects great when I use the USB cord. So does my digital camera using same USB cable. They all connect right away. Only the external HD does not communicate!

What is command for terminal to search and to show devices connected to computer? 

Thanks for help, you are good guys ):P

---

### Post by taurus on 2008-12-09
```
dmesg | tail
df -h
```

---

### Post by mayagrafix on 2008-12-09
rafael@Inspiron:~$ dmesg | tail
[86041.484448] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[86041.484715] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[86041.668473] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[86041.668671] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[86041.856385] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[86041.856632] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[86042.028377] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[86042.028719] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[86042.201350] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[86042.201571] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
rafael@Inspiron:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              27G  4.8G   21G  19% /
tmpfs                 125M     0  125M   0% /lib/init/rw
varrun                125M  220K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
udev                  125M  2.7M  122M   3% /dev
tmpfs                 125M  352K  125M   1% /dev/shm
lrm                   125M  2.0M  123M   2% /lib/modules/2.6.27-9-generic/volatile
/dev/sdc2              28G   24G  4.4G  85% /media/BIGDOG'S IP
rafael@Inspiron:~$

---

### Post by mayagrafix on 2008-12-10
Update:

I did a re-boot with the USB Drive plugged in and running. It now shows up in the computer tab of the file browser (nautilus). However it gives a message of "cannot mount" when I click on it. Maybe the OS is scanning through the files because I see the HD light blinking on the drive. Maybe tomorrow after it has gone through all 200 gigs it will open.

---

### Post by vanadium on 2008-12-10
Reread the post of taurus. You will need to check and repair your ntfs disk, something that is best done using MS Windows.

---

