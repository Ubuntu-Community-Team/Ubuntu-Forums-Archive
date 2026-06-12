---
title: "mounting second harddrive on boot"
date: 2009-04-28
forum: General Help
---

### Post by yon2501 on 2009-04-28
im having a little trouble finding out how to mount on boot a second harddrive or in my case a partition. i just swapped out my hd with a 250gig partitioned it so just enough space if there for ubuntu and windows to install and run the left about 200 gigs open for shared space, windows mounts fine but i cant get the shared space to mount on boot in ubuntu. how?

---

### Post by reality1011 on 2009-04-28
look into adding the information to your /etc/fstab file.  I posted something recently where I displayed the contents of my fstab file

---

### Post by bumanie on 2009-04-28
You will need to add the drive to /etc/fstab Is the second drive formatted to ntfs or ext3/4? If it is ntfs you could use the ntfs configuration tool which will automatically add the drive to /etc/fstab for you, if it is ext3/4 you will have to do so manually.
To use ntfs configuration tool > sudo apt-get install ntfs-configThen go to Applications --> System Tools --> Ntfs Configuration tool. Fill out the window that appears and the drive will be added to /etc/fstab and mount at each boot. If it is ext3/4, [look here]("http://www.tuxfiles.org/linuxhelp/fstab.html")You can use the drive letter as in the tutorial or use the UUID if you wish. To find the UUID > blkidHope this helps.

---

