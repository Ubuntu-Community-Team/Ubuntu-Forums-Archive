---
title: "Browsing Samba Shares Locks up System"
date: 2008-12-04
forum: General Help
---

### Post by basketcase on 2008-12-04
Dell Dimension 8400
Fresh install of 8.10
Edited /etc/fstab to mount shares.
Created .smbcredentials
Shares mount fine.

I'm able to open a terminal and navigate to /mnt/homedir and /mnt/systems but if I opened up the GUI file browser and navigate to the shares that way, the system locks up completely.  I can't ctl+alt+f2, I can't SSH into the box.  If I have an SSH connection to the box, it dies.  

I'm not sure how to troubleshoot it, to figure out what is causing the system to lockup like it is.  The only way to 'fix' it is to just power down the system.  

I replaced Nautilus with Thunar, though it is quicker, the system still locks up.  

Let me know what you might need to determine what is causing this to not work.  It's the last little bit I need working to switch over to Ubuntu completely.

Thanks!

---

### Post by basketcase on 2008-12-04
Little more info...shutting down the system tonight, there were some random numbers and an error related to CIFS and VFS.  I tried to write it down, but it wasn't there long enough.

If it is there in the morning, I'll report back what it was.

Though, probably a permission error, I am unable to write to these shares from Ubuntu.

Thanks!

---

### Post by basketcase on 2008-12-08
> **basketcase said:**
> Little more info...shutting down the system tonight, there were some random numbers and an error related to CIFS and VFS.  I tried to write it down, but it wasn't there long enough.

If it is there in the morning, I'll report back what it was.

Though, probably a permission error, I am unable to write to these shares from Ubuntu.

Thanks!

so the CIFS VFS problem was resolved and it is related to this [bug]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/153444")

The system still continues to lock up while browsing those files from the GUI.

---

### Post by CrusaderAD on 2008-12-08
Your fstab file might be messed up. 

sudo vi /etc/fstab

---

### Post by basketcase on 2008-12-08
> **raptormanad said:**
> Your fstab file might be messed up. 

sudo vi /etc/fstab

Here is my /etc/fstab:
Like I said, it mounts the drives fine...I can cd into the directory in the terminal, and do whatever I need to do, but I can not reliably browse the directories from the GUI.

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b811bb54-ed73-415b-b901-e6fe455f080c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=0a594b4e-8417-4957-abf7-549685345c52 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#home-directory
//server/share /home/user/homedirectory cifs credentials=/root/.smbcredentials 0 0
#systems-share
//server/share/share /home/user/systemsshare cifs credentials=/root/.smbcredentials 0 0

---

### Post by basketcase on 2008-12-11
TTT. Anyone?

---

### Post by Freaky_Llama on 2008-12-11
I have a locking issue on my laptop as well, with a cifs share setup the same way you have. If I have nautilus open to the share, I could be doing something else in terminal or Firefox, and I get a total lock (REISUB don't help). The Scroll and Caps lock LED's blink, which, if I'm not mistaken, is a Kernel panic. 

However, it doesn't happen every time I venture into the share.

Dell D630 laptop
Ubuntu 8.10

---

### Post by basketcase on 2008-12-11
> **Freaky_Llama said:**
> I have a locking issue on my laptop as well, with a cifs share setup the same way you have. If I have nautilus open to the share, I could be doing something else in terminal or Firefox, and I get a total lock (REISUB don't help). The Scroll and Caps lock LED's blink, which, if I'm not mistaken, is a Kernel panic. 

However, it doesn't happen every time I venture into the share.

Dell D630 laptop
Ubuntu 8.10


Mine seems to be lessing, but still continues to do it.  Not everytime now, but it locks up at the most inconvenient time.

---

### Post by basketcase on 2008-12-12
Back to the top...someone has to have some idea.

---

### Post by basketcase on 2009-02-03
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/307408](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/307408)

Updated to 2.6.28-5 in intrepid proposed and it fixed my issue.

---

