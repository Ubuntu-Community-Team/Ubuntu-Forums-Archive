---
title: "Shares and/or FTP to Ubuntu Box..."
date: 2005-11-17
forum: Desktop Environments
---

### Post by jrennard on 2005-11-17
Greetings,

I am trying to setup shares on my Ubuntu box that will allow me to drop various files in there so I can use them on Ubuntu.  

I'm coming primarily from a Windows XP system.  I went through the process of allowing Ubuntu to setup Samba for sharing, but I cannot get the shares to show up in Windows.

Also, do I need to join my Ubuntu box to the domain for something like this to work?  

I appreciate your help in getting these shares to show up.

---------

Is there a way to allow me to FTP files directly to my Apache websites on Ubuntu?  Thanks!

---

### Post by Sheco on 2005-11-17
edit /etc/samba/smb.conf

make sure it has these lines:
```

[global]
  smb passwd file = /etc/samba/smbpasswd
  security = user

[homes]
  comment=Home directories
  browsable=no
  writable=yes

```

and add the samba password
```

smbpasswd -a your_user

```

this user has to be a valid local user on this machine, samba password doesnt have to be the same as the local user's password.

restart samba.

easy way to connect: start menu->run... (replace samba_ip with the ip of the ubuntu box)
\\samba_ip\

---

### Post by jrennard on 2005-11-17
I don't have a smbpasswd file.  Do I need to create a file there?  If so, what do I name the extension?  Thanks.

---

### Post by jrennard on 2005-11-17
Fabulous!

Nevermind!  I figured it out...

I just had to run that smbpasswd command and it took care of it.  I appreciate the help.  The shares popped up perfectly.  =)

---

### Post by bursto22 on 2005-12-13
There *is also * a way you can send files to your apache website. Download the program Winscp, run it in windows, and you should be able to connect to your server from anywhere.

---

