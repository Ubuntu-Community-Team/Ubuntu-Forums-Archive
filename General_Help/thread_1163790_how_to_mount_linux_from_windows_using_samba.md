---
title: "how to mount linux from windows using samba"
date: 2009-05-19
forum: General Help
---

### Post by suresh_vandiyur on 2009-05-19
i need files from windows. how i can mount that. what command will be used for samba mounting. plz help me..

---

### Post by KhurramM on 2009-05-19
The linux machine with samba running is recognized in the windows network as a windows machine.

Simply search the network by IP addy or host name (as supplied to and by samba), u can then browse the samba shares.

This might help u:
[http://www.swerdna.net.au/linhowtolanprimer.html](http://www.swerdna.net.au/linhowtolanprimer.html)

---

### Post by suresh_vandiyur on 2009-05-19
> **KhurramM said:**
> The linux machine with samba running is recognized in the windows network as a windows machine.

Simply search the network by IP addy or host name (as supplied to and by samba), u can then browse the samba shares.

This might help u:
[http://www.swerdna.net.au/linhowtolanprimer.html](http://www.swerdna.net.au/linhowtolanprimer.html)
i need my windows files.. how to mount the files in my linux system.. i need mounting commands..

---

### Post by KhurramM on 2009-05-19
U guys really dont wanna search thoroughly:

[http://www.swerdna.net.au/linhowtosambacifs.html](http://www.swerdna.net.au/linhowtosambacifs.html)

[http://www.swerdna.net.au/linux.html](http://www.swerdna.net.au/linux.html)

[http://en.wikipedia.org/wiki/Smbmount](http://en.wikipedia.org/wiki/Smbmount)

---

### Post by suresh_vandiyur on 2009-05-19
> **KhurramM said:**
> U guys really dont wanna search thoroughly:

[http://www.swerdna.net.au/linhowtosambacifs.html](http://www.swerdna.net.au/linhowtosambacifs.html)

[http://www.swerdna.net.au/linux.html](http://www.swerdna.net.au/linux.html)

[http://en.wikipedia.org/wiki/Smbmount](http://en.wikipedia.org/wiki/Smbmount)
ok... thank you so much.

---

### Post by lisati on 2009-05-19
I've successfully used this tutorial as the basis for setting up file sharing with three different versions of Ubuntu and three different versions of Windows: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by dmizer on 2009-05-19
To mount Windows files, see the second link in my sig.

---

### Post by geraldvillorente on 2009-05-19
If the harddisk is attached locally:

NTFS filesystem
```

sudo mkdir /media/windows 
sudo mount -t ntfs-3g /dev/<device node> /media/windows

```
 example
```
 
sudo mount -t ntfs-3g /dev/sdb1 /media/windows

```
 or, with "-o force" option
 example
```

sudo mount -t ntfs-3g /dev/sdb1 /media/windows -o force

```
FAT filesystem
```

sudo mkdir /media/windows 
sudo mount -t vfat /dev/<device node> /media/windows

```
 example
```

 sudo mount -t vfat /dev/sdb1 /media/windows

```
 or, with "-o force" option
 example
```

 sudo mount -t vfat /dev/sdb1 /media/windows -o force

```

If in the network:
1. Share the folder or the drive of the source.
2. Access the source by using smb command
   ```

     smb://ipaddress 
       or 
     smb://hostname
   
```
Hope I'm correct...

---

