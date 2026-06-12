---
title: "Mounting Drives at Boot"
date: 2009-03-25
forum: General Help
---

### Post by davideotape on 2009-03-25
Just wondering if there was a way of making another partition separate from the Ubuntu partition automatically mount every time you boot.

All help appreciated :D

David

---

### Post by DeMus on 2009-03-25
> **davideotape said:**
> Just wondering if there was a way of making another partition separate from the Ubuntu partition automatically mount every time you boot.

All help appreciated :D

David

Yes, there is. :)  But, I'm sure you want to know how and not just if it is possible or not. I used this method:

Auto mount Windows disks
Fire up a terminal, to do this click Applications > Accessories > Terminal
Then type (or copy/paste) the following - 1 line at a time

```
sudo aptitude update
sudo aptitude install ntfs-config
```
Ok so when that returns you to user@pcname, then it should be installed          

Next, make sure you have NO drives mounted (they'll usually appear on your desktop). And then run the program from Applications > System Tools

Enter your password when prompted - and then choose the drives that you want to be automounted. Click Apply.

Now simply make sure that "Enable Write Support for Internal Drives" and click OK.

Success.

---

### Post by davideotape on 2009-03-25
```
The following NEW packages will be installed:
  ntfs-config 
The following packages will be REMOVED:
  libatk1.0-dbg{u} libfontconfig1-dbg{u} libgail-gnome-dbg{u} 
  libgail-gnome-module{u} libgda3-3-dbg{u} libgda3-sqlite{u} 
  libgnomevfs2-0-dbg{u} libgsf-1-114-dbg{u} libgsf-gnome-1-114-dbg{u} 
  libgstreamer0.10-0-dbg{u} libloudmouth1-0{u} libloudmouth1-0-dbg{u} 
  libmono-corlib1.0-cil{u} libmono-i18n1.0-cil{u} libnspr4-0d-dbg{u} 
  libnss3-1d-dbg{u} liboobs-1-4-dbg{u} libpango1.0-0-dbg{u} libruby1.8{u} 
  python-alsaaudio{u} python-fstab{u} python-numpy{u} python-sqlalchemy{u} 
  rhythmbox-dbg{u} ruby1.8{u} w3c-dtd-xhtml{u} 

```

I presume that this is bad, and that I need some of these packages?

---

### Post by DeMus on 2009-03-25
> **davideotape said:**
> ```
The following NEW packages will be installed:
  ntfs-config 
The following packages will be REMOVED:
  libatk1.0-dbg{u} libfontconfig1-dbg{u} libgail-gnome-dbg{u} 
  libgail-gnome-module{u} libgda3-3-dbg{u} libgda3-sqlite{u} 
  libgnomevfs2-0-dbg{u} libgsf-1-114-dbg{u} libgsf-gnome-1-114-dbg{u} 
  libgstreamer0.10-0-dbg{u} libloudmouth1-0{u} libloudmouth1-0-dbg{u} 
  libmono-corlib1.0-cil{u} libmono-i18n1.0-cil{u} libnspr4-0d-dbg{u} 
  libnss3-1d-dbg{u} liboobs-1-4-dbg{u} libpango1.0-0-dbg{u} libruby1.8{u} 
  python-alsaaudio{u} python-fstab{u} python-numpy{u} python-sqlalchemy{u} 
  rhythmbox-dbg{u} ruby1.8{u} w3c-dtd-xhtml{u} 

```

I presume that this is bad, and that I need some of these packages?

I would say when the system says they can be removed it is okay to let the system remove them. When I get a message like that I have always says Yes to it.
Did you un-install something lately, which could be related to these files?

---

### Post by vanadium on 2009-03-25
I am a bit surprised that DeMus advised you to use a tool designed to mount ntfs formatted disks, while you did not provide information on the file system of your disk. The advise of DeMus will work only if the other partition is formatted using the ntfs file system of MS Windows.

The general approach is to create a mount point (=empty directory) and add a line for the partition in question in the configuration file /etc/fstab. If you post the output here of "sudo blkid", and tell which one of the partitions listed in this command you want to automount, then I can tell you how this line is going to look.

---

### Post by DeMus on 2009-03-25
> **vanadium said:**
> I am a bit surprised that DeMus advised you to use a tool designed to mount ntfs formatted disks, while you did not provide information on the file system of your disk. The advise of DeMus will work only if the other partition is formatted using the ntfs file system of MS Windows.

The general approach is to create a mount point (=empty directory) and add a line for the partition in question in the configuration file /etc/fstab. If you post the output here of "sudo blkid", and tell which one of the partitions listed in this command you want to automount, then I can tell you how this line is going to look.

I admit I jumped to conclusions here. On the other hand if somebody asked a question like that it is probably somebody new in the Linux world, still having a Windows installation as dual boot. So, thinking about what I did, it does not sound so bad to me. But, I can be totally wrong here. I like to hear this form the O.P.

---

