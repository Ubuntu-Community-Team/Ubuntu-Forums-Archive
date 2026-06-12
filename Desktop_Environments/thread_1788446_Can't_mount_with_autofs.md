---
title: "Can't mount with autofs"
date: 2011-06-22
forum: Desktop Environments
---

### Post by NarsilAnduril on 2011-06-22
Hi,

I need help with a small problem with autofs mount. I did it a lot of times but I do believe I am missing something time time ...

The static mount works fine, here is my fstab (of course uncommented for the test, and /mnt/temp/NAS* directories created) :
```
# Partages NAS1
#172.26.155.6:/volume1/movies /mnt/temp/NAS1/movies nfs rsize=8192,wsize=8192,timeo=14,intr,nolock
#172.26.155.6:/volume1/music /mnt/temp/NAS1/music nfs rsize=8192,wsize=8192,timeo=14,intr,nolock
#172.26.155.6:/volume1/photos /mnt/temp/NAS1/photos nfs rsize=8192,wsize=8192,timeo=14,intr,nolock

# Partages NAS2
#172.26.155.7:/volume1/sauvegardes /mnt/temp/NAS2/sauvegardes nfs rsize=8192,wsize=8192,timeo=14,intr,nolock
#172.26.155.7:/volume1/partage /mnt/temp/NAS2/partages nfs rsize=8192,wsize=8192,timeo=14,intr,nolock
#172.26.155.7:/volume2/torrent /mnt/temp/NAS2/torrent nfs rsize=8192,wsize=8192,timeo=14,intr,nolock
```

Now, with this auto.master :
```
/mnt/NAS1 /etc/autoNAS1.nfs --ghost --timeout=60
/mnt/NAS2 /etc/autoNAS2.nfs --ghost --timeout=60
```

This autoNAS1.nfs :
```
movies 172.26.155.6:/volume1/movies
music 172.26.155.6:/volume1/music
photos 172.26.155.6:/volume1/photos
```

And this autoNAS2.nfs :
```
sauvegardes 172.26.155.7:/volume1/sauvegardes
partage 172.26.155.7:/volume1/partage
torrent 172.26.155.7:/volume2/torrent
```

It doesn't work.

All /etc/auto* files are executables
```
ls -la /etc/auto*
-rwxr-xr-x 1 root root  758 2011-06-22 20:37 /etc/auto.master
-rwxr-xr-x 1 root root  524 2011-04-10 08:26 /etc/auto.misc
-rwxr-xr-x 1 root root  106 2011-06-22 20:39 /etc/autoNAS1.nfs
-rwxr-xr-x 1 root root  122 2011-06-22 20:41 /etc/autoNAS2.nfs
-rwxr-xr-x 1 root root 1374 2011-04-10 08:26 /etc/auto.net
-rwxr-xr-x 1 root root  687 2011-04-10 08:26 /etc/auto.smb

```

/mnt/NAS1 and /mnt/NAS2 are empty
autofs is installed
nfs-common is installed

... what is missing ?

Thanks for your help !

---

### Post by NarsilAnduril on 2011-06-23
up ?

---

### Post by NarsilAnduril on 2011-06-23
Auto answer :

Put both autoNAS1.nfs and autoNAS2.nfs in same file auto.nfs
Modify auto.master to set 
```
/mnt/NAS /etc/auto.nfs --ghost --timeout=60
```
Set all /etc/auto* to unexecutable
```
sudo chmod -x /etc/auto*
```
restart autofs
Enjoy !

But I still don't understand why, that's bad.

---

