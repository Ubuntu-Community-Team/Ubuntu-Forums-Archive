---
title: "TORAM parameter"
date: 2014-12-08
forum: Desktop Environments
---

### Post by buntuluxx on 2014-12-08
I am using Ubuntu 14.10 from a LiveCD and would like to know where I have to add the **"TORAM"** parameter, in order for everything to boot to RAM.
I need to press "e" to get into the boot code, but where and how exactly do I implement "TORAM"?
[Img]http://www.faclic.com/files/exploitation-pc/reparer-restaurer-reinstaller-grub2-live-cd-ubuntu-1.jpg[/img]

---

### Post by mörgæs on 2014-12-08
I don't understand... Using a live boot you automatically get everything loaded into RAM. 

The picture shows kernel 2.6.32 used in 10.04.

---

### Post by buntuluxx on 2014-12-08
Dont mind the version of the picture, its just meant to serve as an illustration.

The LiveCD is still required during a live session. 
I want everything to load into RAM.

I have read, that a simple way to do this concerns adding "TORAM" in the boot menu.
But where and how exactly?

In the console, when pressing "c" in the boot menu?
Or in the grub code when pressing "e" in the boot menu?

I have also seen "TORAM=yes"

---

### Post by mörgæs on 2014-12-08
> **buntuluxx said:**
> 
I have read...

Please post all relevant links you have found.

---

### Post by buntuluxx on 2014-12-08
It has generally been established, that adding this "toram" parameter somewhere in the grub boot menu, results in the system to boot to RAM. It is supposedly a new functionality within casper.

Here is a thread on the Forum indicating such.[http://ubuntuforums.org/showthread.php?t=1583206](http://ubuntuforums.org/showthread.php?t=1583206)

---

### Post by buntuluxx on 2014-12-08
Edit: Figured it out.
The "toram" must be added exactly before "--" in the top casper line. It worked.

Another question arises, though. The usable space is only 8.4 GB , although I have 16GB of RAM. What can I do to utilize all of my RAM?

---

### Post by mörgæs on 2014-12-08
Please post the output from **free -m** in CODE tags.

---

### Post by buntuluxx on 2014-12-08
Here is the output:
I shall translate, since I am using the German version:
Gesamt = Total
Belegt = Used
Frei = Free
Gemeinsam = Mutual
```
jackson@jackson:~$ free -m
             Gesamt Belegt Frei Gemeinsam Puffer Cached
Speicher:      15927       3268      12658       1611        323       2203
-/+ Puffer/Cache:        741      15185
Auslagerungsdatei:          0          0          0

```

Also a df:
```
jackson@jackson:~$ df -h
Dateisystem    Größe Benutzt Verf. Verw% Eingehängt auf
/cow            7,8G     47M  7,8G    1% /
udev            7,8G    4,0K  7,8G    1% /dev
tmpfs           1,6G    1,3M  1,6G    1% /run
/dev/loop0      1,5G    1,5G     0  100% /rofs
none            4,0K       0  4,0K    0% /sys/fs/cgroup
tmpfs           7,8G     20K  7,8G    1% /tmp
none            5,0M       0  5,0M    0% /run/lock
none            7,8G     88K  7,8G    1% /run/shm
none            100M     28K  100M    1% /run/user


```

Can I use extend commands here?
I am not sure how it works with RAM.

---

### Post by buntuluxx on 2014-12-08
I have conducted a little experiment.
As you can see, the free -m command indicates, that the whole 15927MB of RAM are available, despite root only being 8,4GB large.

So I tried to create a RAM Disk, in order to check if more space was available, which was indeed successful, proving that the additonal 8GB should be available.
I successfully created the 7.5GB large directory /ramdisk in tmp, while the 8GB in root where still free.
```
jackson@jackson:~$ sudo su
[sudo] password for jackson: 
root@jackson:/home/jackson# mkdir /tmp/ramdisk; chmod 777 /tmp/ramdisk
root@jackson:/home/jackson# mount -t tmpfs -o size=7.5G tmpfs /tmp/ramdisk

```

The only question that remains is, how I can utilize the entire space in root, as I need the 16GB whole.

(Kinda funny that I was able to create a RamDisk within a System that entirely runs out of RAM:KS)

---

### Post by mörgæs on 2014-12-09
Now I have been playing some more with the option and 

> **mörgæs said:**
> Using a live boot you automatically get everything loaded into RAM. 


is only partially true. Yes, in a live boot everything gets loaded into RAM on demand, but in order to load it all from the beginning TORAM is needed.

---

### Post by buntuluxx on 2014-12-10
I have recently created a custom Xubuntu 14.04 LiveCD with remastersys, that boots completely into RAM with the "toram" parameter. I am using 16GB 2133 RAM in total.
Unfortunately, the booted system only uses 8GB in root/filesystem, hence half.
I want to utilize the entire 16GB as a whole.

Here some free output:
I shall translate, since I am using the German version:
Gesamt = Total
Belegt = Used
Frei = Free
Gemeinsam = Mutual
```
jackson@jackson:~$ free -m
             Gesamt Belegt Frei Gemeinsam Puffer Cached
Speicher:      15927       3268      12658       1611        323       2203
-/+ Puffer/Cache:        741      15185
Auslagerungsdatei:          0          0          0

```

Also a df:
```
jackson@jackson:~$ df -h
Dateisystem    Größe Benutzt Verf. Verw% Eingehängt auf
/cow            7,8G     47M  7,8G    1% /
udev            7,8G    4,0K  7,8G    1% /dev
tmpfs           1,6G    1,3M  1,6G    1% /run
/dev/loop0      1,5G    1,5G     0  100% /rofs
none            4,0K       0  4,0K    0% /sys/fs/cgroup
tmpfs           7,8G     20K  7,8G    1% /tmp
none            5,0M       0  5,0M    0% /run/lock
none            7,8G     88K  7,8G    1% /run/shm
none            100M     28K  100M    1% /run/user


```

As you can see, the free -m command indicates, that the whole 15927MB of RAM are available, despite root only being 8,4GB large.

So I tried to create a RAM Disk, in order to check if more space was available, which was indeed successful, proving that the additonal 8GB should be available.
I successfully created the 7.5GB large directory /ramdisk in tmp, while the 8GB in root where still free.
```
jackson@jackson:~$ sudo su
[sudo] password for jackson: 
root@jackson:/home/jackson# mkdir /tmp/ramdisk; chmod 777 /tmp/ramdisk
root@jackson:/home/jackson# mount -t tmpfs -o size=7.5G tmpfs /tmp/ramdisk

```

The only question that remains is, how I can utilize the entire space in root, as I need the 16GB whole.

---

### Post by slickymaster on 2014-12-11
@buntuluxx

I've merged your other thread - _Xubuntu only usea half of the disk space_ - with this one. Please do not create duplicate threads, it dilutes community effort.

---

