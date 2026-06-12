---
title: "New HD and access paths"
date: 2006-06-09
forum: Desktop Environments
---

### Post by tbobo05 on 2006-06-09
I recently installed a new harddrive (hdb1) on my box to act as a slave for my /home directory.  My problem is that when I formatted, I changed the access path of the new drive to /home via the disk formatter GUI in Gnome.  Now, nothing on my desktop works.  Im guessing this is because my box points to the new home directory on the new harddrive which is empty.  Can someone tell me how to change the access path for my /home directory to point toward my old HD (hda1)?

---

### Post by Rui Pais on 2006-06-09
hi,
```
sudo gedit /etc/fstab
```

(or kedit if you use kubuntu)

---

### Post by jive_turkey on 2006-06-09
Its pretty simple, go System --> Administration --> Disks, then click on the disks you want to change. Change to the partitions tab, then find the partition you need to change, there should be an access path box that you can change to whatever you want. Good luck

\\:D/

---

### Post by tbobo05 on 2006-06-09
when i try to launch anything from gnome, i get

 "Error:  Could not launch application.  Details:  Failed to change to directory '/home/tony' (No such file or directory) "

guessing because it could not access my prefs for the applications i am trying to launch.  going to try to edit fstab manually via CL right quick, thanks for quick replies

---

### Post by Rui Pais on 2006-06-09
hi, sorry i forget your home is not available...

did sudo nano -w /etc/fstab in a console work?

---

### Post by tbobo05 on 2006-06-09
it didnt list hdb at all.  I thought it may be due to me not restarting after i installed and formatted the second harddrive......BIG MISTAKE! Can't even get to login screen now.  Its failing during INIT saying:


           "INIT:  ID "1" respawning too fast:  disabled for 5 minutes
            INIT:  ID "2" respawning too fast:  disabled for 5 minutes
            INIT:  no more processes left in this runlevel "

after 5 minute wait, same error message appeared.  boot from cd maybe to edit it?

[EDIT] im also assuming the <Mount Point> would be the same as access path?

---

### Post by tbobo05 on 2006-06-09
it didnt list hdb at all.  I thought it may be due to me not restarting after i installed and formatted the second harddrive......BIG MISTAKE! Can't even get to login screen now.  Its failing during INIT saying:


           "INIT:  ID "1" respawning too fast:  disabled for 5 minutes
            INIT:  ID "2" respawning too fast:  disabled for 5 minutes
            INIT:  no more processes left in this runlevel "

after 5 minute wait, same error message appeared.  boot from cd maybe to edit it?
[EDIT] after 2ed reboot, it seems that everything works fine now.  checked acess path of second hard drive and it has revereted back to the default of "none." i do not know why this happened, just happy that it did.  now, how do i go about changing /home and everything in it to the second harddrive without screwing everything up?

---

### Post by Rui Pais on 2006-06-09
hi,
if the 2nd hard disk is formated, mount it somewhere,
and do 
```
cp -a /home/* /mnt/mymeany2nddrive/
```
change /etc/fstab to point to new hd partition
close session go to a console and do a 
```
sudo mount -a 
```
check with df -h if everything is ok. 
login, check if everything is ok.

if it is ok you can delete your old /home/* (becarefull not the new one that is mounted!)

---

### Post by tbobo05 on 2006-06-09
ok, is the new hd supposed to showup on fstab? or do i have to add it myself?  also, for the mount point do i put /home? or /mnt/home (where i originally mounted the file to copy everything)



[EDIT]  i think i have it all figured out now, thank you very much for your help.

---

### Post by Rui Pais on 2006-06-10
hi,
no, you have to add it by hand to fstab. It appears (to kernel) only with df that lists partitions mounted. 
Your mount point is temporary. Add to fstab as /home, like:
> /dev/hdXX       /home           ext3    defaults,noatime          0       1 
where hdXX is your disk partition (like hdb1)

After you do mount -a with the new fstab it shoulfd point /home to the new place. Again you could check with df.

---

