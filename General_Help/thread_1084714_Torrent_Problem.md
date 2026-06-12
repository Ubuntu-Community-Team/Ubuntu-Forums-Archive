---
title: "Torrent Problem?"
date: 2009-03-02
forum: General Help
---

### Post by tmun52 on 2009-03-02
I'm trying to download files from Deluge torrent onto my external HDD. Everytime I start to download the file I get an error message

 *torrent paused: disk write error, seek failed: 'Invalid argument' fd: 148 offset: 5516946608 seekdir: 0*

I'm a new linux user, and I have no idea what this means or what to do :(.
Help would be appreciated. Thanks.

---

### Post by taurus on 2009-03-02
What filesystem is your external harddrive?  Looks like you don't have permission to write to it.

```
sudo fdisk -l
df -h
```

---

### Post by tmun52 on 2009-03-02
the file system is FAT32.

So does that mean it's not compatible with linux? Because I can play movies off of it just well.

---

### Post by taurus on 2009-03-02
How did you mount it?  Post the outputs of those two commands from my previous reply.

By the way, you can read from it but writing to it is the problem right now unless you remount it with the right "argument."

---

### Post by tmun52 on 2009-03-02
```
sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x283d9841

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ffc810

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38912   312560608+   c  W95 FAT32 (LBA)

Disk /dev/sdc: 2032 MB, 2032664576 bytes
64 heads, 63 sectors/track, 984 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         984     1983619+   6  FAT16
taher@taher-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              36G  3.8G   30G  12% /
tmpfs                 378M     0  378M   0% /lib/init/rw
varrun                378M   96K  378M   1% /var/run
varlock               378M     0  378M   0% /var/lock
udev                  378M  2.8M  375M   1% /dev
tmpfs                 378M  132K  378M   1% /dev/shm
lrm                   378M  2.0M  376M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sdb1             299G   35G  265G  12% /media/My Passport
/dev/scd0             699M  699M     0 100% /media/cdrom0
/dev/sdc1             1.9G   20M  1.9G   2% /media/disk
taher@taher-desktop:~$ 
```

---

### Post by taurus on 2009-03-02
Which one do you want to write to, /dev/sdb1 or /dev/sdc1?

For now, I assuming it's /dev/sdb1 since it's a larger harddrive.  Unmount it first and remove it.

```
sudo umount /dev/sdb1
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
df -h
```
If you want to write to /dev/sdb1 (320GB) now, you need to point deluge to /media/sdb1.

---

### Post by tmun52 on 2009-03-02
Thanks for the help, but I still get that same message, even when I redirected it to /media/sdb1

---

### Post by taurus on 2009-03-02
What's the output of this command from a terminal?

```
ls -la /media
```
Is that a new download or did you download it from windows (not finish) and now want to continue in Ubuntu?

---

### Post by tmun52 on 2009-03-02
```

total 82
drwxr-xr-x  6 root  root  4096 2009-03-02 12:35 .
drwxr-xr-x 20 root  root  4096 2009-03-01 21:40 ..
lrwxrwxrwx  1 root  root     6 2009-03-01 14:34 cdrom -> cdrom0
dr-xr-xr-x 10 root  root  2048 2008-10-29 19:24 cdrom0
drwx------  3 taher root 16384 1969-12-31 19:00 disk
-rw-r--r--  1 root  root   227 2009-03-02 12:35 .hal-mtab
-rw-------  1 root  root     0 2009-03-01 22:54 .hal-mtab-lock
drwx------ 20 taher root 32768 1969-12-31 19:00 My Passport
drwxr-xr-x  2 root  root  4096 2009-03-02 12:10 sdb1


```

I started a new torrent, not from an existing windows one.

---

### Post by taurus on 2009-03-02
Go back a little.  What command did you use to remount your /dev/sdb1?

---

### Post by tmun52 on 2009-03-02
Well, I think I unmounted it using umount /media/sdb1
then i unplugged the cord and put it back

---

### Post by taurus on 2009-03-02
```

sudo umount /dev/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
ls -la /media
```

---

### Post by tmun52 on 2009-03-02
> 
total 78
drwxr-xr-x  5 root  root  4096 2009-03-02 13:24 .
drwxr-xr-x 20 root  root  4096 2009-03-01 21:40 ..
lrwxrwxrwx  1 root  root     6 2009-03-01 14:34 cdrom -> cdrom0
dr-xr-xr-x 10 root  root  2048 2008-10-29 19:24 cdrom0
drwx------  3 taher root 16384 1969-12-31 19:00 disk
-rw-r--r--  1 root  root   110 2009-03-02 13:24 .hal-mtab
-rw-------  1 root  root     0 2009-03-02 13:17 .hal-mtab-lock
drwxrwxrwx 20 root  root 32768 1969-12-31 19:00 sdb1

here it is after i tried it again

---

### Post by taurus on 2009-03-02
Do you get any error message when you run this command?

```
touch /media/sdb1/testing
```

---

### Post by tmun52 on 2009-03-02
I didn't get anything at all 
> taher@taher-desktop:~$ touch /media/sdb1/testing
taher@taher-desktop:~$ 


---

### Post by taurus on 2009-03-02
It means that you are now able to write to /media/sdb1 as a regular user.  In fact, if you look in there, you should see a new file called testing that you have just created.

```
ls -la /media/sdb1
```
And if you want to remove it, run

```
rm /media/sdb1/testing
```
Now, see if deluge can write to it (probably best to restart deluge).

---

### Post by tmun52 on 2009-03-02
Thank you so much!
It's working great!

---

