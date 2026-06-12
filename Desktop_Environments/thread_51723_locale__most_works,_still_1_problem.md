---
title: "locale : most works, still 1 problem"
date: 2005-07-25
forum: Desktop Environments
---

### Post by SL0MO on 2005-07-25
I have a dualboot Ubuntu 5.04 (ext2) / windows XP (NTFS) + shared fat32 partition.
I also have an external NTFS disk 200gb.

In fstab I have : 
```

#windows xp partition
/dev/hda1       /mnt/windowsxp  ntfs    ro,nls=utf8,umask=0222 0 0
#external hd
/dev/hdd5       /mnt/external     ntfs    ro,nls=utf8,umask=0222 0 0
# fat32 share
/dev/hda6       /mnt/fatshare   vfat    rw,uid=1000,gid=1000,iocharset=utf8,codepage=850,umask=0000 0 0

``` 

Ubuntu has en_US.UTF-8 as locale.

All special charaters like "ë à" display fine on the ubuntu/ntfs/fat32 disks. (nautilus)
By adding "codepage=850" it even works when I create a file on the fat drive in
linux and then read it in windows or visa versa.

On the external hd I have my cd collection ripped to ogg/mp3. 
It is organised like mymusicfolder/genre/artist/album.
I wrote a java app which analyses this directory structure, get id3 info from the files
and outputs html files with artist,album,genre,cdcover,...
These html files are written in the "mymusic" directory so that it contains relative
path in case i take the disk to a friend and the driveletter changes in windows orso.
It' all just plain HTML, no php or database involved.
Every html file has <meta http-equiv="Content-Type" content="text/html; charset=utf-8">.
If I put some music on my linux disk and I run the java app and then open the html files it created in Firefox
it displays special characters fine. On my fat disk they also display fine. If I run the java app in windows 
and create the html files on the ntfs disk and open them in firefox in linux, it fails to display the special characters. 
(I can't create them from linux because NTFS write restrictions)
If I look at the source of the html in gedit, the characters are fine.
I'm using firefox 1.0.6 and my default character encoding is set to UTF-8.
Is it firefox that fails to read from the ntfs mounted disk or something else?
Epiphany same result.
Please help.

[screenshot wrong](http://users.pandora.be/8ERT/pics/wrong.png) 
[screenshot how it should be](http://users.pandora.be/8ERT/pics/ok.png)

---

