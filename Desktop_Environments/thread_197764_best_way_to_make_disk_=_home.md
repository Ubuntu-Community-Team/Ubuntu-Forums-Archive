---
title: "best way to make disk = /home?"
date: 2006-06-16
forum: Desktop Environments
---

### Post by frup on 2006-06-16
i have an 80GB ext3 disk i would like to set as my /home directory.
i understand i should back up /home then i guess copy it to the drive then edit fstab to make the drives mount point /home..? is it that simple?

how would i delete the old home? would that be wise?

---

### Post by Gustav on 2006-06-16
Yup, it's that simple.

Just remove the old /home directory when you are very sure everything is copied to the new partition.

---

### Post by Anduu on 2006-06-16
See here for details...

[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

---

### Post by Ramses de Norre on 2006-06-16
Using cp, mv, nautilus or whatever wont work, all links will be broken. So be sure to use the command described in the guide mentioned above.

---

### Post by frup on 2006-06-16
Is this where i should start and finish?

cd /old/home
find . -depth -print0 | sudo cpio --null --sparse -pvd /new/
sudo mv /old/home /old/home_backup
sudo mkdir /old/home

Yes, one of those lines looks really complicated--please type it as is--or, if you're unsure of your typing skills, copy and paste it into the terminal. Believe me--the command is necessary.

Next, we're going to specify to use the new home partition as /home:
sudo cp /old/etc/fstab /old/etc/fstab_backup
sudo nano /old/etc/fstab

You'll then be taken to the nano text editor. Add in this line:
/dev/hda7 /home ext3 nodev,nosuid 0 2

Then save (Control-X), confirm (Y), and exit (Enter)

After you reboot, you should be now using your new /home partition.

If you find that you are running out of room on your old partition and you're pretty confident everything is working as it should be, then go ahead and delete the backup of home:
sudo rm -rf /home_backup

---

### Post by Ramses de Norre on 2006-06-16
Indeed =)

---

### Post by Gustav on 2006-06-16
Sorry for saying it was simple :) (I really thought it was)

---

### Post by Ramses de Norre on 2006-06-16
It is quite simple, you just need a link to that find command line ;)

---

### Post by frup on 2006-06-16
ok thankyou very much i will try it tomorrow.

---

