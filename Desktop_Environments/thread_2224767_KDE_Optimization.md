---
title: "KDE Optimization"
date: 2014-05-18
forum: Desktop Environments
---

### Post by wd5gnr2 on 2014-05-18
This seems to work pretty well. Comments welcome (and yes, I know you have to rebuild the cache on first login after a restart but I so infrequently restart...)

Step 1: Create a mount point for a tmpfs
sudo mkdir /tmp-ram

Step 2: Mount tmpfs on new mount point
sudo <your favorite editor> /etc/fstab

Add this line to the bottom of the /etc/fstab
tmpfs         /tmp-ram     tmpfs      noatime,nosuid,nodev,size={XXX}    0    0

{XXX} is the maximum amount of RAM you want to dedicate to the temporary file system.
For example, I have size=900M   (900 megabytes)


Step 3: Create mount
You can reboot or just issue:
sudo mount -a

Step 4: 
Create file in ~/.kde/env named relo.sh

export KDETMP=/tmp-ram 
export KDEVARTMP=/tmp-ram 
ln -s /tmp-ram/kde-{USERID} ~/.kde/tmp-{HOSTNAME}

Replace {HOSTNAME} with whatever the hostname command tells you your computer name is. For example, mine is:
~/.kde/tmp-enterprise

Replace {USERID} with your user ID

I did a chmod +x relo.sh but that is probably not necessary

Step 5. Log out of KDE

Step 6. Open a console (Control+Alt+F1) and log in.

Step 7. Remove tmp-{HOSTNAME}
rm ~/.kde/tmp-{HOSTNAME}
(replace {HOSTNAME} with your hostname
You can then exit the console or if you are lazy you can reboot by issuing the command:
sudo reboot

Step 8. Return to X and log in.
If you didn't reboot use Control+Alt+F7 (not sure it is always on F7). Then log in

Step 9. Verify
Open a konsole prompt and issue:
ls -l ~/.kde

You should see cache-XXX, socket-XXX, and tmp-XXX as links to /tmp-ram (XXX is your hostname).


It is pretty easy to reverse all of this. Simply remove relo.sh and delete the tmp file with KDE not running. Then log back in. You can also unmount the tmpfs, remove the fstab line, and delete the tmp-ram mount point.

This seems to work well for me. Then again, I have a write through SSD cache to a RAID array so writes are expensive even if cached. Your mileage may vary.

---

### Post by oldos2er on 2014-05-18
Would you consider creating a [proper tutorial]("http://ubuntuforums.org/showthread.php?t=2143602") and posting it to the [Tutorials subforum]("http://ubuntuforums.org/forumdisplay.php?f=100")? How-to threads posted in support areas tend to be quickly buried and forgotten.

---

### Post by wd5gnr2 on 2014-05-18
I will. However, I was curious if anyone first had any reason this was not a good thing. I had written several tutorials under my pre-sso login (wd5gnr) and considered it here, but thought I'd see if there was any reason to not encourage people to do this.

---

