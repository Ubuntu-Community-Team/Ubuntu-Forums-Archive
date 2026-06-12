---
title: "*Danger* Mounted Vfat as Home by accident"
date: 2005-10-15
forum: Desktop Environments
---

### Post by Omnios on 2005-10-15
Was in a hurry to get my backupfiles from my vfat drive and accidentily mounted it as /home/MyName with the disk utility. Now im locked out of gnome with a hole bunch of errors saying files dont match etc and kicking me out after a few seconds. Anyways I looked into fstab and there was nothing there so im wondering what file do I have to modify to get my gnome back. Basicly think I have to unmount it to get it working again. 

 Anyone have any experience with this?

---

### Post by audax321 on 2005-10-15
Well, there has to be something in /etc/fstab since that is what defines all your mount points. Can you please post it?

Or if you know what the parition is, just hit CNTRL+ALT+F6 to get to a log-in. Then after logging in, type:

sudo umount /dev/hda1

and change /dev/hda1 to whatever you mounted as /home/(username)

Although I'd recommend against the second method since you might actually be using the /home mount while you are trying to unmount it. Also don't accidently unmount the root partition... if it even lets you... but that would probably not be good :)

By the way, to see the fstab file at the prompt either type:

sudo nano /etc/fstab (to edit it)

or

cat /etc/fstab (to print its contents)

---

### Post by Omnios on 2005-10-15
K figured it out I had a mount problem so I exited and tryed to log back in. I rebooted and the problem fixed itself. Killing X will probably achieve the same reults. The admin disk thing reset with the beboot.

---

