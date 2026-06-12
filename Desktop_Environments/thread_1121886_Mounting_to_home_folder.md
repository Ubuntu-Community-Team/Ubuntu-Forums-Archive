---
title: "Mounting to home folder"
date: 2009-04-10
forum: Desktop Environments
---

### Post by linlux on 2009-04-10
This is more of a contribution than a question...curious if anyone else has tried it.

I am running a dual boot Ubuntu Intrepid/Windows 7 install and it is running very smoothly with my semi new dual core Athlon. I set up a shared FAT32 partition for my data files so I could access from Win7 and Linux. Then I decided to mess around and copy all of my hidden home folder files and settings to the FAT32 and mount it as my home directory. I added this line to the fstab:

/dev/sda1       /home/gregory  vfat    rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0

Basically I copied the default settings by typing 'mount' after mounting the partition in File Browser.

All my files show up as the proper owner and everything seems to work except I am getting one error at login 'Could not update ICEAuthority'. Also I can't shut down normally, I have to use ctrl+alt+backspace to log out then shutdown.

---

