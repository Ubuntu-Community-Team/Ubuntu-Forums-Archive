---
title: "GUI smb: Where is the mount point?"
date: 2005-04-28
forum: Desktop Environments
---

### Post by thorN on 2005-04-28
If I connect to a Windows Share with the gnome/nautilus tool, using "Places > Connect to Server", does it create a mount point on the file system? Where is it?

I've noticed that some programs can't save properly onto the Windows Share because it uses smb:// in the filename paths (, I think).

edit: This thread, [Why does mounting a network drive act different than browsing?](http://ubuntuforums.org/showthread.php?t=29529), covers the same thing.

It looks as if Nautilus isn't a front-end for mount, but works differently.

Thanks for any repsonses.

---

### Post by nad on 2005-04-28
No. There is no mount point. Nautilus is a file manager. It is using the smb protocol to transparently handle file requests. If your app doesn't understand the smb protocol... However, drag and drop through nautilus will work.

If you wish to mount the share, please see the man pages for mount, samba and smbmount.

---

### Post by duff on 2005-04-28
[QUOTE=thorN]It looks as if Nautilus isn't a front-end for mount, but works differently.[/QUOTE]
That's true.  You can either mount it yourself, or ask the developer of the program you're using to add gnome-vfs support.

---

### Post by thorN on 2005-04-28
I've made a script to mount the path I want:

```

sudo mkdir /media/joe/ -v

sudo apt-get install smbfs

echo Enter Windows network password...
sudo mount //HOST/SHARE /media/SHARE/ -o username=joe,dmask=777,fmask=777

```

It installs SMBFS because I use this with the LiveCD

---

