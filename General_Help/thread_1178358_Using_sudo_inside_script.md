---
title: "Using sudo inside script"
date: 2009-06-04
forum: General Help
---

### Post by iLoVe.cF- on 2009-06-04
Hi.

I've googled, searched around, with not much of a result at all.

here's a little example of an script.

!bin/bash
echo Backupscript to ftp is starting.
sudo cp -R /var/www/ /home/sd/backups/www/
sudo tar -cvvf /home/sd/backups/www.tar /home/sd/backups/www/
curlftpfs -v -o nonempty "ftpuser":"ftppassword@"ftpserveraddress"/backups/ ~/ftp/
sudo cp -v /home/sd/backups/www.tar /home/sd/ftp/
sudo rm /home/sd/backups/www.tar
sudo rm -R /home/sd/backups/www/
sudo umount /home/sd/ftp/
exit

This script is automaticly run after another script which backups sql is done.

But the real issue here is, curlftpfs command cannot run as sudo/root, while the others can be ran as root, which ive done tho.
But well, the issue really is that when the proccess is automated, it asks for a password, or will.
how can i make automaticly type it in, or not require it.

---

### Post by VMC on 2009-06-04
Why not leave sudo off and run the script as root.

---

### Post by Chronon on 2009-06-04
> **iLoVe.cF- said:**
> Hi.
But the real issue here is, curlftpfs command cannot run as sudo/root

> 
Fuse Options

-d
Enable FUSE debug output. Implies -f.
-f
Run curlftpfs in foreground mode.
-r
Mount read-only.
-s
Disable multi-threaded operation.
-o
Options are specified with a -o flag followed by a comma separated string of options.
allow_other
Allow access to other users. By default the mount point is only accessible to the user that mounted it and not even to root.
[B]allow_root
Allow access to root user. By default the mount point is only accessible to the user that mounted it and not even to [/B]root.

I think you can use this option.

---

### Post by Darkdelusions on 2009-06-04
I had a script that required sudo at one time instead of running 1 command under sudo I add sudo -v at the beginning of my script. 

The minus v flag just update the sudo's timestamp if you haven't sudoed in awhile it will prompt you for your password

---

