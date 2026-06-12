---
title: "want to get windows partition to mount at bootup"
date: 2008-07-13
forum: Desktop Environments
---

### Post by jimlikessweets on 2008-07-13
i would like to have my windows partition mount at bootup. at the moment i don't even know how to access it from xubuntu. in the past when i was using ubuntu it worked out of the box, but with xubuntu it doesn't. how do i gain access to my windows partition from xubuntu and how do i customize it to start at boot up?

thanks in advanced for all help
-jim

---

### Post by gnuvistawouldbecool on 2008-07-13
Well, I usually ensure that when I am installing GNU/Linux that the windows partition has a mount point of /mnt/windows in the disk partitioning part of the installer.  It never fails to mount for me then, unless windows happens to be hibernated at the time, in which case it refuses to mount.

Not sure of any other ways though.  I know in Mandriva the disk management is called is diskdrake, but I don't know it for the ubuntu system.  In fact if someone were to tell me it would be helpful.

---

### Post by tech0007 on 2008-07-13
If you're using hardy, the windows partition will appear under Places menu on the top panel. Then you can do 'sudo apt-get install ntfs-config' to mount it on boot.

If not, post the output of 'sudo fdisk -l /dev/sdX' (X is usually 'a' if you have 1 hard drive. then edit your /etc/fstab accordingly.

---

### Post by jimlikessweets on 2008-07-15
> **tech0007 said:**
> If you're using hardy, the windows partition will appear under Places menu on the top panel. Then you can do 'sudo apt-get install ntfs-config' to mount it on boot.

If not, post the output of 'sudo fdisk -l /dev/sdX' (X is usually 'a' if you have 1 hard drive. then edit your /etc/fstab accordingly.

alright so i installed ntfs-config and it found my partition. now it appears in my media folder. thanks a lot for your help.

---

