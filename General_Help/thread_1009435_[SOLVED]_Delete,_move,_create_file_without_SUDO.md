---
title: "[SOLVED] Delete, move, create file without SUDO"
date: 2008-12-12
forum: General Help
---

### Post by jac0117 on 2008-12-12
I have a solid state drive that only holds 32GB so most of my media is on a regular spinning hard drive.

However I cannot modify my files in my media hard drive.  Every time I try to create a file, move, or delete a file or folder I get an error that says, "permission denied".  I have to do SUDO every time I want to do anything with files in my media hard drive.  Is there a way that I can fix this? It really annoys me.

---

### Post by ibuclaw on 2008-12-12
Which desktop environment are you running on? Gnome, KDE or Other?

Regards
Iain

---

### Post by bodhi.zazen on 2008-12-12
And what filesystem ?

---

### Post by ezsit on 2008-12-12
Is your solid state drive a usb flash drive? What is the mount point - the folder your drive gets mounted to?

If you have a usb flash drive plugged in and its mounted at /media/disk then changing the ownership of the mount point may let you do what you want to do. However, changing the ownership of the mount point will only last for the duration you have the drive plugged in, remove the drive and mount point will get recreated the next time you plug in the drive. You can change the ownership of the mount point by:

chown username:username -R /media/disk

This should allow you to access your files without the use of sudo. I believe this will only work if your drive is formatted in a Linux native filesystem (ext3, xfs, jfs). If your drive is formatted FAT or NTFS I'm not sure why you need sudo since all my flash drives that are FAT just work normally under Ubuntu.

---

### Post by jac0117 on 2008-12-12
Q: *Which desktop environment are you running on? Gnome, KDE or Other?*
A: I'm running Gnome
 
Q: *And what filesystem ?*
A: Ext3  (this is the solid state drive)

Q: *Is your solid state drive a usb flash drive? What is the mount point - the folder your drive gets mounted to?*
A: No it's not USB, the interface is SATA II.  

The mount point for the media drive is /media/sdb5.  I formatted this disk as FAT32  ( this is the spinning disk IDE interface).

---

### Post by jac0117 on 2008-12-12
I did the following:

sudo chown jcampos:jcampos -R /media/sdb5


and I get a bunch of "operation denied" errors

---

### Post by ibuclaw on 2008-12-12
Seems that the device has been mounted with static permissions.

What you could do is create an fstab line for the drive.

Run:
```
sudo vol_id /dev/sdb5
```
Take note of the line: **ID_FS_UUID=** as the text after that is what we'll be using to identify the disk.

Now open up your fstab file in a text editor
```
sudo gedit /etc/fstab
```

And at the bottom, put this:
```
# External 32GB SSD Drive
UUID=**THE_UUID_IDENTIFIER**    /media/sdb5    ext3    defaults    0    2
```
"THE_UUID_IDENTIFIER", is ofcourse the UUID for the drive (so replace that text with the actual UUID).

Once finished, Save and quit, then re-insert your external drive again.

If you still don't have write access, the chown command should work now.

Regards
Iain

---

### Post by geirha on 2008-12-12
FAT32 doesn't support the permissions and ownership Ubuntu uses, so instead all files and folders on that filesystem will get the same ownership and permissions when it gets mounted, and that can not be changed with chown or chmod. Tinivole has the right idea, but it seems he missed the part about FAT32. His instructions apply, but the fstab line should look something like
```
UUID=*ABCD-1234* /media/sdb5 vfat defaults,uid=jcampos,gid=jcampos,fmask=113,dmask=002 0 0
```
This will make you the owner of all files and folders in /media/sdb5, you'll have read and write access and any other user will only have read access.

---

### Post by jac0117 on 2008-12-17
Thanks guys for your help... but this solution doesn't seem to solve the problem.  Should I just format the drive to ext3?  I initially formated it as FAT32 because I want to SSH or connect via FTP to my computer from other computers so I figured that Windows systems would not be able to access any data as ext3.

---

### Post by wolterh on 2008-12-17
Why don't you install an apache server and host the files there? Any windows machine will be able to access the files there. Its just like downloading files from [http://ftp.gnome.org](http://ftp.gnome.org)

If you like this option, then go ahead and format your drive as an ext3, and then install the apache thing. You might want to look it up as 'how to install lamp server' or something like that.

I currently have it in my drive so that people at home can download files more easily.

---

### Post by anjilslaire on 2008-12-17
The ext3 won't affect Windows in that sense. It's the protocol (ssh/ftp) that provides the access, not the file system (in a simplified sense)

---

### Post by jac0117 on 2008-12-17
Thank you to all you guys that helped.  So I formatted the drive as ext3.  Then it would still not allow me to create, copy or delete.  So I did EZSIT said:

sudo chown username:username -R /media/Media/

Now I have write permissions. 

I'll also look into apache and lamp server...

Thanks to all again.

---

### Post by The Cog on 2008-12-17
If you only intend to use the drive for Ubuntu, I would suggest reformatting ot with ext3. This supports larger files, and also has journalling which should help in case of crashes, power cuts etc. In this case, you need to change the permissions of the mount point so your normal user can access it. e.g. 
sudo chmod 777 /media/harddrive

If you wnat to keep it as fat32, you have to tell the OS to mount the drive with suitable simulated permissions (FAT doesn't do unix permissions). Add the option "umask=0" to the options field in /etc/fstab, for instance changing the word "defaults" to "defaults,umask=0", no spaces. This should make the drive writable by everyone.

Your choice of what file system you use will not affect Linux's ability to share files using samba, sftp or whatever you choose to share the files with. Except of course that with FAT, Linux can't store file ownership info.

---

