---
title: "shared partition"
date: 2006-06-09
forum: Desktop Environments
---

### Post by jturnbul on 2006-06-09
I have a large partition on my computer that is used to store music, pictures,  video, and other such things.  My goal is to have this partition shared by every user on the comoputer, so they can add, delete, rename files.  It is an Ext3 partion.

I have messed around with a few configurations, and can get all users to view, and play files, but i need to 'sudo' in order to make new directories, rename/ move files.  

Any suggetions on how the partition should be mounted.
This is how it is currently mounted

/dev/sdb9       /media/sdb9     ext3    defaults,rw,users,exec                   0       2

BTW, I have made it so I own every file and folder under my account user id, and group id, but it still does not let me edit them

---

### Post by Rui Pais on 2006-06-09
Hi,
i have a partition of kind, mounted at folder /mnt/pub owned by root but change they permissions to 0777 (sudo chmod a+r,a+w,a+x /mnt/pub) with no special set at fstab and work well. 

Since the folder belongs to root noone can delete, but inside everybody can read write and execute. Of course a user can make a folder of its one and make it not readble by others... but its his/her folder :)

---

### Post by jturnbul on 2006-06-10
thanks, that worked.  So simple.  I thought I tried that before, but its working now

---

