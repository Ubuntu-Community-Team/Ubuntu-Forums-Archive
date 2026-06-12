---
title: "Performous help please"
date: 2011-01-17
forum: Gaming &amp; Leisure
---

### Post by Harold41 on 2011-01-17
Hi, i'm new here and I've had some problems with terminal
i downloaded a game called performous and the tools that go with it
and i'm having some problems mounting a disc
if anyone can help, please do so,
if this is in the wrong place then please let me know or move it
Thanks in Advance

---

### Post by lykeion on 2011-01-17
Applications > Ubuntu Software center > Enter "performous" in search field > Click Install for Peformous - A karaoke game.
Below it you'll see the performous-tools if you want to install that as well.

In Ubuntu (unlike Windows) you install programs through a package manager, like Ubuntu Software Center. It's only in very special cases you'd need to download and install manually.

About your problems with mounting a disc you'll have to give more details. Is it a disc image (iso) or is it a physical disc (CD/DVD)? 
In the latter case it should mount automatically. To mount an iso file read this: [https://help.ubuntu.com/community](https://help.ubuntu.com/community)

---

### Post by Harold41 on 2011-01-17
Thanks for replying Lykeion, i had already downloaded the packages from the software center but when i use ss_extract on terminal i get this,

[I][SIZE=1]nat@Nat-PC:~$ ss_extract

Options:
  -h [ --help ]         you are viewing it
  --dvd arg             path to Singstar DVD root
  -l [ --list ]         list tracks only
  --song arg            only extract the given track (ID or partial name)
  --video arg (=mkv)    specify video format (none, mkv, mpeg2)
  --audio arg (=ogg)    specify audio format (none, ogg, wav)

ERROR: No Singstar DVD path specified. Enter a path to a folder with pack_ee.pak in it.
nat@Nat-PC:~$ ss_extract --dvd '/media/SINGSTARQUEEN' 
Singstar DVDs have UDF and ISO-9660 filesystems on them. Your disc is mounted
as UDF and this causes some garbled data files, making ripping it impossible.

Please remount the disc as ISO-9660 and try again. E.g. on Linux:
# mount -t iso9660 /dev/cdrom /media/SINGSTARQUEEN
nat@Nat-PC:~$[/SIZE][/I] mount -t iso9660 /dev/cdrom /media/SINGSTARQUEEN
mount: only root can do that
nat@Nat-PC:~$ sudo mount -t iso9660 /dev/cdrom /media/SINGSTARQUEEN
[sudo] password for nat: 
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: /dev/sr0 already mounted or /media/SINGSTARQUEEN busy
mount: according to mtab, /dev/sr0 is already mounted on /media/SINGSTARQUEEN
nat@Nat-PC:~$ 

if anyone can help, please do

---

### Post by Harold41 on 2011-01-17
anyone?

---

### Post by lykeion on 2011-01-18
According to the error output there could be two problems for the ss_extract command:
1. You didn't specify the path to the DVD
2. The DVD was mounted in format UDF not in ISO-9660

First try to add the path to the ss_extract command:
```
ss_extract --dvd /media/SINGSTARQUEEN
```
If that doesn't work, try to remount as ISO-9660:
```
sudo umount /media/SINGSTARQUEEN
sudo mount -t iso9660 /dev/cdrom /media/SINGSTARQUEEN
```
Then try the first command again:
```
ss_extract --dvd /media/SINGSTARQUEEN
```

---

### Post by Harold41 on 2011-01-18
i got this, 

```
 nat@Nat-PC:~$ sudo umount /media/SINGSTARQUEEN
[sudo] password for nat: 
nat@Nat-PC:~$ sudo mount -t iso9660 /dev/cdrom /media/SINGSTARQUEEN
mount: mount point /media/SINGSTARQUEEN does not exist 
```

---

### Post by lykeion on 2011-01-19
Did you try this after you inserted the DVD?
If so and it didn't work what was the error output?
```
ss_extract --dvd /media/SINGSTARQUEEN
```

---

### Post by Harold41 on 2011-01-20
[FONT=monospace]```
 nat@Nat-PC:~$ ss_extract --dvd /media/SINGSTARQUEEN
Singstar DVDs have UDF and ISO-9660 filesystems on them. Your disc is mounted
as UDF and this causes some garbled data files, making ripping it impossible.

Please remount the disc as ISO-9660 and try again. E.g. on Linux:
# mount -t iso9660 /dev/cdrom /media/SINGSTARQUEEN 
```
i am having absolutely no luck with this


[/FONT]

---

### Post by Harold41 on 2011-01-20
[FONT=monospace]sorry double posted, running off a Usb modem


[/FONT]

---

### Post by lykeion on 2011-01-20
Indeed no luck at all.

Try this:
1. Make a mount directory to manually mount the DVD
```
sudo mkdir /media/mount_dir
```
2. Pop in the DVD and wait until it have automounted
3. Unmount the DVD
```
sudo umount /media/SINGSTARQUEEN
```
4. Manually mount it as ISO-9660 in your mount directory
```
sudo mount -t iso9660 /dev/cdrom /media/mount_dir
```
If above command fail you might want to mount using loopback device like this: 
sudo mount -t iso9660 /dev/cdrom /media/mount_dir -o loop
5. Run your ss_extract command
```
ss_extract --dvd /media/mount_dir
```

When you are done you can unmount, eject DVD, and remove the mount_dir

---

