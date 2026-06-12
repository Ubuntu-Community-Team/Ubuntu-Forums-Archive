---
title: "partition has insufficient space"
date: 2009-01-20
forum: Desktop Environments
---

### Post by markagraber on 2009-01-20
Hi, I am trying to install UpToDate medical software designed for the Mac but which runs under JAVA environment.  The only program I have not been able to get running on Ubuntu that I must have..... 

I am able to get the MAC package install to start using command line.

sudo ./media/cdrom0/ICE/disk1/setupLinux.bin 

JAVA etc. install fine but I get a "partition has insufficient space" message despite the hard drive being essentially empty.  This is the same regardless of where I choose to install the software.

Thoughts?
Thanks

---

### Post by oaqster on 2009-01-20
if its a java application you should be able to run it just using the JRE, not sure what the MAC package install is for?
in what form is this UpToDate software? do you have a .jar file with .class files in it or something else?
- oaqster

---

### Post by oaqster on 2009-01-20
also do you have your ubuntu install distributed over multiple partitions? it could be that you might be running out of space where this software is trying to install/run from, open up the system monitor and goto the file system tab (should be the last one) and have a look at the used space on your various mounts.  you can also check your mounts using

```
sudo fdisk -l *device_name*
```

replace device_name with your HDD name like 

```
sudo fdisk -l /dev/sda
sudo fdisk -l /dev/sdb
```

also for java what do you get when you do 

```
which java
java -version
```

Update: just noticed that your running this setup program from your cd drive, could it be that its trying to install directly to the CD?? if so try copying it over locally to HDD and try running it from there.

---

