---
title: "Can't delete Folder from USB key : Creating folders is not supported with protocol tr"
date: 2005-03-20
forum: Desktop Environments
---

### Post by loots on 2005-03-20
Hi,

(sorry form my english, but i speak french usually)

I'm using Kubuntu.

I mounted a USB key on my computer, see the content of my /etc/fstab :

/dev/sda        /media/cleusb   auto    rw,noauto,user,sync     0       0

In my Desktop environment (with a user account), i go on the "System" Icon at the bottom of screen and i choose "Storage Media" and "512MB removable Media" (my USB key).
When i create  folder or a file on the USB KEY, there is no problem. I can delete files which goes in the "trash folder", but when i want delete a folder, i get the error message :

Creating folders is not supported with protocol trash

When i open "konsole" with the user account, i can delete the folder.

Have an idea ?

Thanks.

---

### Post by nivok on 2005-07-17
I had the same error on one of my mounted ext3 volumes, I could rm -rf the directory in Konsole but not in Konqueror.  so I played with some buttons if you hold SHIFT + right click move to trash / delete key it seems to delete it fine, I think it has something to do with the folder being locked.

---

