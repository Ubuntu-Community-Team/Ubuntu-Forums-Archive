---
title: "Want to reinstall, but need files off unbootable hdd first"
date: 2009-04-23
forum: General Help
---

### Post by knixo4 on 2009-04-23
Well, I've given up on trying to fix my grub error 17 problem, and have decided to just reinstall.  I'm in the live cd, and trying to copy a folder from my screwed partition onto an external drive, but now I'm getting the permission denied message.  What's the way around?

Thanks for your help.

---

### Post by SuperSonic4 on 2009-04-23
Preface the command to copy with sudo which should copy the files as root. You *may* have to chown them back to you after install

---

### Post by dabl on 2009-04-23
You have to mount the partition before you can access the data on it -- it's not clear from your post whether you understand that or not.

---

### Post by Moop on 2009-04-23
Use ```
gksudo nautilus 
``` to open a window with sudo privileges and then browse to the files you want to copy.

---

### Post by knixo4 on 2009-04-23
I have no idea what I'm doing.  I think the /sda1 drive is mounted, as I can see the folder.

---

### Post by SuperSonic4 on 2009-04-23
Moop's suggestion would be better in that case.

---

### Post by knixo4 on 2009-04-23
Took moop's suggestion, and got the following:

Initializing nautilus-share extension
seahorse nautilus module initialized
** (nautilus:7451): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:7451): GLib-GIO-WARNING **: Missing callback called fullpath = /root/.config/user-dirs.dirs


I was able, however to locate the desired folder in a popup window, but yet, permission denied.

---

### Post by knixo4 on 2009-04-23
Wait a sec.  It appears that I am now able to change the permissions and move forward...

---

### Post by knixo4 on 2009-04-23
Indeed, that is the case.  You guys are my HEROES!  Thanks.

---

### Post by SuperSonic4 on 2009-04-23
Heh, no problem. In the world of linux root can do *anything*, it's part of the reason why it's dangerous to enable the root account or run common applications as root

---

