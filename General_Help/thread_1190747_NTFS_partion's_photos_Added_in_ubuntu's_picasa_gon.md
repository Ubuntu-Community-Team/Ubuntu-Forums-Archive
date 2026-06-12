---
title: "NTFS partion's photos Added in ubuntu's picasa gone while restarting the system"
date: 2009-06-18
forum: General Help
---

### Post by sivamec on 2009-06-18
Hi Experts,


In Ubuntu's picassa, I have added NTFS's folder(photos) to view. So that, I am able to see the photos.

But when i restarted the system, None of NTFS's added folder are not present in the picassa. only the photos in ext3 are present in the picassa.

Do i want to add any packages to view the NTFS's phots even after restarting the system.

Regards,
-Siva.

---

### Post by metiosarius on 2009-06-18
You need to add your NTFS partition to your **/etc/fstab** file.
An easier method would be to follow this tutorial which uses a GUI: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by ajgreeny on 2009-06-18
If the ntfs partition is unmounted the photos will not be available to picasa on ubuntu.  You will need to import, ie copy, them into your ubuntu partition for that to happen, I think.  If the ntfs partition is mounted then I do not know what is going on, and you will have to await other peoples input.  You can easily mount the ntfs partition at boot time by editing the /etc/fstab file, or just install ntfs-3g and ntfs-config and you can set up those partitions to mount at boot using a gui.

---

### Post by sivamec on 2009-06-18
Metiosarius and Ajgreeny, 

Thanks for your speedy reply, i will check it..

Regards,
-Siva.

---

