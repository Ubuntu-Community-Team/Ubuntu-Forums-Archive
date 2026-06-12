---
title: "Second hard drive problem"
date: 2005-12-09
forum: Desktop Environments
---

### Post by dcast on 2005-12-09
Hey, I installed a 15 gig maxtor drive to add some extra space with my 20 gig. I went to system--> admin-->disks I made it accessible in /home and my system has some issues now eg nothing will open or run it just gives an error message. Does anyone know how to fix this

---

### Post by matthewv on 2005-12-09
Did you ensure that the disk was formatted first...
Try making sure that it is formatted, copying you /home folder, including all hidden folders over, and then making it accessible at /home

---

### Post by dcast on 2005-12-09
ya I did format it first, but I have to copy all my files over just to use it as a second drive for extra space?

---

### Post by dcast on 2005-12-09
Ok... So I tried again and this time it worked I made a folder where it is accessible from in the home directory but I have no priveleges the file owner and group is root how can I change this?

---

### Post by jerrykenny on 2005-12-09
I dont understand, do you intent to use the new disk for your home partition ?

if so then you need to specify that in your fstab, also then move your home folder,


Why dont you just use it as a spare partition called say, backup,?

sudo mkdir /media/backup

sudo gedit /etc/fstab

insert a line similar to this

/dev/hd??      /media/backup   reiserfs defaults          0       2

---

### Post by jerrykenny on 2005-12-09
sudo chmod 0777   /whatever/the/folder/is/called

---

### Post by dcast on 2005-12-09
solved it with chown thanks guys

---

