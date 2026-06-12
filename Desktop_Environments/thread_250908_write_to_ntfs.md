---
title: "write to ntfs ? ? ?"
date: 2006-09-04
forum: Desktop Environments
---

### Post by guest5 on 2006-09-04
is it possible to write to ntfs file system and if not does everyone format their external drives for use or ???

---

### Post by taurus on 2006-09-04
If you intent to write to your NTFS, then you are just asking for trouble!!!  If you really want to share files between Windows and Linux, then format it as fat32 (vfat).  That's how people do it around here...

---

### Post by Najand on 2006-09-04
> **guest5 said:**
> is it possible to write to ntfs file system and if not does everyone format their external drives for use or ???

It is possible. There must be a few different ways. I use another filesystem module called "captive-ntfs". For a  fast installation, just download the tar.gz file (captive-static-1.1.7.tar.gz (12.8MB)) from [http://www.jankratochvil.net/project/captive/#download]("http://www.jankratochvil.net/project/captive/#download") then use "tar" command to  extract it.
```
tar xvfz captive-static-1.1.7.tar.gz
```
cd to captive-statics-1.1.7 and run
```
./INSTALL
```
After installation use
```
mount -t captive-ntfs TARGET-DEVICE MOUNTPOINT
```
to mount your ntfs drive or add a similar line to your /etc/fstab file.

---

### Post by Jussi Kukkonen on 2006-09-04
There are drivers for that but at least I consider them experimental...

I suggest using FAT for removable drives if you need to work with windows too.

---

### Post by guest5 on 2006-09-05
thank you so much.  if i decide to format the ntfs to fat, will ubuntu be able to preform this or do i need a 3rd party drive?  i don't believe that the windows 'manage' can format a ntsf drive to fat32.

meanwhile, i believe i will try the solution proffered above.

thanks.

---

### Post by whizbaby on 2006-09-05
Use (at own gusto):
gparted         (graphical)
fdisk or cfdisk (terminal)
you'll have your fat32 in no time (of course destroying all the data on that partition, but you know that...)

---

### Post by guest5 on 2006-09-05
thanks, and yes, but the fact is, this is my first week with linux, so before i can reformat, i need to borrow one of my buddies .5 tbyte drives.  i must say again, i am amazingly impressed with this OS, and all of you are so helpful, all this and without crass wordplay.  this may be the best forum on the web, imo.

thanks again.

---

### Post by guest5 on 2006-09-05
when i ./INSTALL from w/in the directory, i received the error

hadmadder@ubuntu:~/dnls/captive-static-1.1.7$ ./INSTALL
bash: ./INSTALL: No such file or directory
hadmadder@ubuntu:~/dnls/captive-static-1.1.7$


there is a file called install in this directory.

what did i do wrong?  do i need to iinstall some compiler tools or something maybe?

---

### Post by taurus on 2006-09-05
> **guest5 said:**
> when i ./INSTALL from w/in the directory, i received the error

hadmadder@ubuntu:~/dnls/captive-static-1.1.7$ ./INSTALL
bash: ./INSTALL: No such file or directory
hadmadder@ubuntu:~/dnls/captive-static-1.1.7$


there is a file called install in this directory.

what did i do wrong?  do i need to iinstall some compiler tools or something maybe?
What is the output of this command then?

```
ls -la ~/dnl/captive-static-1.1.7
```
However, INSTALL is NOT the install that you are thinking about.  It contains the instructions on how to install captive on your machine.  Therefore, you need to read it with either more or less...

```
more INSTALL
```

---

### Post by guest5 on 2006-09-05
taurus  -  i know that means something, but me, on only day 4 of using linux, your output question is beyond me, as this will be my first install in this particular format, i will have to go through it like a child so that i can understand it for next time without assistance.  thanks for all patience.

---

### Post by taurus on 2006-09-05
The "ls -la ~/dnl/captive-static-1.1.7" means to list all the files with permissions in /home/hadmadder/dnl/captive-static-1.1.7.

The "more INSTALL" is to view the file INSTALL.

So, run the first command, the "ls -la" thing, and paste the output here but chances are this is what you need to do to install it on your machine...

```

sudo aptitude update 
sudo aptitude install build-essential <-- you need to install gcc and other files before you can build anything from source...
./configure
make
sudo make checkinstall

```

---

### Post by guest5 on 2006-09-05
o, silly me, here is the output:

hadmadder@ubuntu:~$ ls -la ~/dnls/captive-static-1.1.7
total 13152
drwxr-xr-x 2 hadmadder hadmadder     4096 2006-01-26 16:46 .
drwxr-xr-x 6 hadmadder hadmadder     4096 2006-09-05 09:19 ..
-rwxr-xr-x 1 hadmadder hadmadder     1999 2006-01-25 18:40 install
-rw-r--r-- 1 hadmadder hadmadder 13428882 2006-01-26 16:46 root.tar.gz
-rwxr-xr-x 1 hadmadder hadmadder      191 2003-11-26 22:54 uninstall
hadmadder@ubuntu:~$

---

### Post by guest5 on 2006-09-05
the first part seemed to go well, then this:

./configure: No such file or directory

---

### Post by taurus on 2006-09-05
If you look at the output from "ls -la", you would have known that there is no such thing as configure so the ./configure is not going to work.  Therefore, you need to run the install to install it!!!

```

sudo ./install

```
And if you want to unistall it, then just run the uninstall command.

```

sudo ./unistall

```

---

### Post by guest5 on 2006-09-05
ok, it installed.  sorry bout my clock being slow today, which must preimpt this following question;  the mount command:

mount -t captive-ntfs TARGET-DEVICE MOUNTPOINT

i don't understand this command, i see this part 
'mount -t captive-ntfs'

but what am i to do with the rest of it ?

---

### Post by taurus on 2006-09-05
TARGET-DEVICE is the partition where your NTFS is resided while MOUNTPOINT is where you want to mount it!!!

---

### Post by guest5 on 2006-09-05
ok, i admit it, i am a total idiot.  where do i want to mount it, it is a usb drive right there on my desktop

---

### Post by taurus on 2006-09-05
You can mount it anywhere you want and before you do it, you need to create it first.

```
sudo mkdir /media/windows
```

---

### Post by LKRaider on 2006-09-05
Please, don't use the Captive driver, as it is slow, outdated and prone to errors.

Check this thread for a more up-to-date and completely opensource solution:
[HOWTO: NTFS with read/write support using the NEW ntfs-3g (easy & safe method)](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by Najand on 2006-09-05
> **guest5 said:**
> ok, it installed.  sorry bout my clock being slow today, which must preimpt this following question;  the mount command:

mount -t captive-ntfs TARGET-DEVICE MOUNTPOINT

i don't understand this command, i see this part 
'mount -t captive-ntfs'

but what am i to do with the rest of it ?

you must change TARGET=DEVICE with the name of your hardware, which is like /dev/hda2 (in case of USB drives /dev/sda1 or similar). To find out which device is that use the command:
```
fdisk -l
```
to see your active hard devices. 
MOUNTPOINT is the name of directory you are intending to mount the device on it. You should make a directory like MYDRIVE with:
```
sudo mkdir /media/MYDRIVE
```
and then use the same directory at the mount command.
For example if your target device is /dev/sda1 and your mountpoint is /mnt/MYDRIVE the mount command would be:
```
sudo mount -t captive-ntfs /dev/sda1 /mnt/MYDRIVE
```

---

### Post by guest5 on 2006-09-05
right on, i'll get there, inxin milexmile, lol at myself.

thanks for hanging in there with me, some things just aren't in the manual that i am reading.

---

### Post by guest5 on 2006-09-05
thank you too lkraider, i will look into that as well, and rather needed this little excersize no matter if i format or use one of these.

thanx again

---

