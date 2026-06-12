---
title: "Samba/CIFS trouble with Linux client"
date: 2009-01-20
forum: General Help
---

### Post by chuckj on 2009-01-20
I have a Ubuntu server with SAMBA installed (version 3.0.28a). I am sharing (among others) a folder named WebWork with the following smb.conf script:

[global]
   workgroup = MSHOME
   security = SHARE

<snip>

[WebWork]
   path = /raid0/WebWork
   read only = No
   create mask = 0666
   force create mode = 0666
   directory mask = 0777
   force directory mode = 0777
   guest ok = Yes

Using a Windows XP computer, I can connect to this folder and add or delete folders and files. When files are created with XP, they have the 0666 permissions (-rw-rw-rw-). This is well and good.

I have been trying to move to a Linux, using Ubuntu 8.10. When I right-click in the folder to "Create Document"->"Empty File", the new file is created with -rw-r--r--, 0644. I can't write to the file. I am not the owner, so I can't chmod the file unless I SSH to the server and 
use sudo chmod. I've given up on /etc/fstab until I solve this, I am trying different mount strings on the command line to see the verbose response. My latest attempt is:

sudo mount -t cifs --verbose -o user=chuck,password=######,rw //Tiffany/WebWork /home/chuck/WebWork

I have searched the internet and read documentation and still can't find out how to have my Linux workstation have the same privileges as my Windows workstation.

I can't believe that this isn't a common problem, or that it doesn't have an easy answer.  Can anyone help me?

Thanks
Chuck Jungmann

---

### Post by HermanAB on 2009-01-20
Try the file_mode and dir_mode options.  See man 'mount.cifs'.

My solution to Samba Hell is to avoid using it wherever possible.  It is so much easier to use NFS instead, even from Windows (Windows Services for Unix).

Cheers,

Herman

---

### Post by chuckj on 2009-01-20
I tried file_mode and dir_mode in previous failed attempts. I stopped using them because I read that the "force create mode" should override it anyhow.

This morning I was wondering if I could bypass samba and connect in a more linux-like way. I was considering changing the drive to NFS, but I have been avoiding that file system because I thought it's less fault-tolerant than ext2 or ext3.

Besides, it bugs me that a Windows computer gets better treatment from a Linux server than another Linux box. I want to understand why it's not working.

---

### Post by hangfire on 2009-01-20
Check the umask of all users involved on both ends of the mount, by logging in and running the ```
umask
``` command. Make sure there is no 022 in there anywhere, if so, set it in both .bash_profile and .bashrc to:

```
umask 000
```

Since Samba & Linux both have a strong concept of who owns what, what you are doing is a bit out of the ordinary.

-HF

---

### Post by chuckj on 2009-01-20
I went to /etc/profile and changed the umask 022 to 000 at the end of the file, restarted my computer, and now it's working as I wanted.

Thank you for your help.

---

