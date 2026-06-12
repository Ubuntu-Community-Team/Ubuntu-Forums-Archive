---
title: "xfce4. external USB Hard Drive is read only despite my efforts..."
date: 2010-06-26
forum: Desktop Environments
---

### Post by brjoon1021 on 2010-06-26
:confused::confused:

I am using Thunar and XFCE4. I started with the minimal install CD, so this is not exactly Xubuntu as I do not have Xubuntu-desktop package installed.

I installed psydm to be able to easily edit and control mounting, fstab etc... Anyways, I can't figure out how to write to this disk. I have amended the Thunar icon to read "gksudo Thunar" as its command. It opens Thunar with whatever elevated rights that would come along with the command. I still can't write to the disk. If I change the permissions for the disk under the properties tab to be "read&write" for the user group, It asks me about something to be done retroactively  to files. No matter whether I choose yes or no here, it still does not change the disk to a writable disk.

No love and no ideas. Can you help me write to this disk ? I run as a user called "user" so maybe I should not have made Thunar open as "gksudo" ?

Any help would be good....

B.

---

### Post by brjoon1021 on 2010-06-27
Bump. Anybody can help ?

---

### Post by brjoon1021 on 2010-06-28
Here is my fstab.

The last line is the device in question

/dev/sdb2                                  /media/sdb2  vfat  defaults             0  0  
/dev/sdc2                                  /media/sdc2  vfat  defaults             0  0  
/dev/sdd1                                  /media/sdd1  vfat  users,user           0  0

I made some changes to the fstab and it is still only a read-only disk.

/dev/sdd1                                  /media/sdd1  vfat  defaults             0  0 

* Is it too much to expect an operating system to be ready to assume an external hard drive might have been added to the system to put something on it ?

---

### Post by bigwigbaz on 2010-07-02
Can you Alt+F2 'gksu thunar' and get write access that way? beware though, it will still be opened as root until you close the window wherever you navigate to, but I assume you are aware of that. 

Have you tried adding another USB device before/after? I had all sorts of problems after my secondary internal drive failed, I had to temporarily leave an old 128MB usb drive attached, as sdb1 was inaccessible until I manually modified the fstab. This then forced the next USB to be sdc1 so was ok for read and write access. 

Sorry I can't be more helpful.

---

