---
title: "raid 1"
date: 2008-12-15
forum: General Help
---

### Post by lander2k2 on 2008-12-15
I have just installed Ubuntu 8.10.

I'm running a raid 1 array which is run by the bios (fakeraid).

Ubuntu is NOT on the array.  The OS is installed on a different physical drive.

Currently, the each partition on each drive appears separately - instead of appearing as a single partition like it should.

This mirrored array has worked for a couple of years in Windows and also worked in a previous installation of Kubuntu (with some configuration).

Can anyone tell me what to edit in order to have the raid 1 partitions be recognised by the OS?

---

### Post by b0b138 on 2008-12-15
Install dmraid. This will then create /dev/mapper/somethinghere (mine looked something like /dev/mapper/pdc_heigkir3) You will then need to mount that somewhere (like /media/raid), and can also be added to your fstab, which will look something like  /dev/mapper/pdc_heigkir3 /media/raid ext3 defaults 0 1  Replace ext3 with the correct label for the filesystem.

Check this thread  [http://ubuntuforums.org/showthread.php?t=630644](http://ubuntuforums.org/showthread.php?t=630644)  though it does have a lot of info on installing to a raid array.

---

### Post by fjgaude on 2008-12-16
Here's likely the best link to fakeraid. Give it a try. Just takes dmraid to be installed, which is in the repository. Have fun!

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by lander2k2 on 2008-12-16
Thanks guys.  The links were very helpful.

I mounted the raid partitions and can use them now.

I haven't figured out how to make them mount automatically when I boot up but I can live with that for now.

---

### Post by b0b138 on 2008-12-17
You should be able to add it to your /etc/fstab file like you would any other disk. The entry should look something like

# /dev/mapper/raid-id-numbers
UUID=the_uuid_of_the_partition /media/mountpoint ext3 defaults 0 1

though I'm not exactly sure of the "defaults 0 1" part, the syntax might be different.

Here is a recent thread about adding a new drive [http://ubuntuforums.org/showthread.php?t=1012541](http://ubuntuforums.org/showthread.php?t=1012541)

---

### Post by fjgaude on 2008-12-17
If you show us how you are manually mounting the array we can show you the exact line to add to your **fstab** file to have it mounted at boot time.

---

### Post by lander2k2 on 2008-12-18
I seem to have got it...

I mounted the partitions by:
sudo mount nvidia_gcceabdf1 /targetfolder
(I did this for each of the four mirrored partitions)

I got the UUID for each partition with:
blkid

I added the following to /etc/fstab (for each partition):

# /dev/mapper/nvidia_gcceabdf1
UUID=(partition UUID) /targetfolder ntfs defaults 0 1


It seems to be working okay.  The partitions did mount on boot.  I'm not sure if I got the "options, dump and pass" (defaults 0 1) right.

Will I mess anything up with the "defaults 0 1" or will it work fine as is - these partitions are just for data storage and need to be accessed from Windows as well as Ubuntu.

Thanks again.

---

### Post by fjgaude on 2008-12-18
I think for your situation it would be better to use 0 2 in the fstab line. The array will be checked every 30 or so boots for errors. I believe that a 0 1 makes it get checked each boot as the boot partition does.

Glad you got it working...

---

