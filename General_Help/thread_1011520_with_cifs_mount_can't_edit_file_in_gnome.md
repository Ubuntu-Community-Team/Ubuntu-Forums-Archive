---
title: "with cifs mount can't edit file in gnome"
date: 2008-12-14
forum: General Help
---

### Post by guillemsola on 2008-12-14
Hi all,

I have a cheap external NAS device (conceptronic CHD3LAN) that with new kernels (since hardy) I have to use with cifs instead of smbfs because smbfs now it's deprecated.

I can mount it apparently without problems with cifs, I do it in fstab
> 
//192.168.1.3/PUBLIC /mnt/NAS cifs guest,iocharset=utf8,nounix  0    0


If I try to edit something with nano or a java application all goes ok. But If can't edit a file with gedit, gimp, openoffice... I can create new files, rename, erase them but never save an existing file again.

I don't know why gnome has this behaviour. My other cifs shares all goes good, it's only something with this weird NAS device. Does anybody knows a way to fix that????

In the past with smbfs I was able to do everything as expected. I tried to compile samba source but I can't see any option to recompile again smbmount & smbumount as I read in dmizer post about cifs. Is it possible to have again smbfs with newer kernels????? Maybe that could be a fix for my issue.

thanks,

---

### Post by geirha on 2008-12-14
Creating, renaming and deleting files requires write access on the directory, while editing a file requires write access on the file. It sounds like the files you create does not become writeable to you automatically. Could you create a test file, test.txt for example, and show the permissions on them? These commands should do just that:
```
echo Hello > /mnt/NAS/test.txt
ls -ld /mnt/NAS /mnt/NAS/test.txt
```

Also, create a file with gedit, and run that ls command on that file as well.


It might be you just need to add some extra options to your fstab line; possibly uid, gid and/or file_mode with the proper values. The options are explained in mount.cifs(8)
```
man mount.cifs
```

---

### Post by guillemsola on 2008-12-15
Well, I've already tried setting uid, gid, file_mode, and many other options without success. I also have read the mount man many times (there is also another called "linux-cifs-client-guide" on the samba web) but I can't find how to fix that.

when I mount my disk I have those permissions:
> 
-rwxrwSrwx 1 root root   66 12 des 07:58 x.txt


If I try with uid=my_username and file_mode=0777
> 
-rwxrwxrwx 1 guillem root   66 12 des 07:58 x.txt


With both options I get the same, I can't edit with OO or gedit.

As I told, what I can do is edit a file with an application like nano or a java one. My feeling is that it's something more related with gnome not with the mount itself, maybe because of the poor cifs implementation on my NAS device.

thanks,

---

### Post by geirha on 2008-12-15
I can't quite see the logic in why it would work with nano, but not gedit. The permissions shown by ls should allow everyone to edit files on that mount, so there must be something odd with cifs indeed. A little google showed up this mailing list message: 

[https://lists.ubuntu.com/archives/ubuntu-uk/2007-August/006465.html](https://lists.ubuntu.com/archives/ubuntu-uk/2007-August/006465.html)

It suggests adding the noperm option to the mount. I don't know enough about NASes and cifs to provide any more help, but that looks like a possible work around at least.

---

### Post by guillemsola on 2008-12-15
thanks for your help, I tried many things, including noperm, but is always the same.

Maybe my last chance is to recompile samba source to get the smbmount again, but since it's deprecated I'm not sure if it's possible to do that.

I downloaded the samba source and smbfs code is still there. Does anybody knows how to recompile samba source with the option with-smbfs? :confused:

I tried to do that as I read in [http://ubuntuforums.org/showthread.php?t=707370](http://ubuntuforums.org/showthread.php?t=707370) without success.

regards,

---

