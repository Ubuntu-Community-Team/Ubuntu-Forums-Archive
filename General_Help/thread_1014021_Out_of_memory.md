---
title: "Out of memory?"
date: 2008-12-17
forum: General Help
---

### Post by ElectricMoose on 2008-12-17
I dual booted Kubuntu Via Wubi on my Windows Vista 64x bit machine. I was installing some extra things on Kubuntu with the package installer. It was about 100mb I think. When I go to install flash, it tells me that I am out of memory. I know that when I installed Kubuntu I selected 15gb, is this why? Is there anyway to change it?

---

### Post by doobiest on 2008-12-17
Can you verify that its out of diskspace?

I dont know how to do this graphically on kubuntu, I do know how to through gnome. 

Here's the command line way.  Open up a terminal and type in df -h.  -h means human readable, rather than showing the exact byte count.

Paste it back so we can see.

If you want you can resize the partition, it's pretty easy. Just load up the ubuntu live cd again, and from a terminal type in gparted. From there you can resize partition.

---

### Post by ElectricMoose on 2008-12-17
> **doobiest said:**
> Can you verify that its out of diskspace?

I dont know how to do this graphically on kubuntu, I do know how to through gnome. 

Here's the command line way.  Open up a terminal and type in df -h.  -h means human readable, rather than showing the exact byte count.

Paste it back so we can see.

If you want you can resize the partition, it's pretty easy. Just load up the ubuntu live cd again, and from a terminal type in gparted. From there you can resize partition.

But I have not installed it Via the live CD, I have Dual booted with a program called Wubi. I do have numerous live CD's but I feel they will be ineffective in this scenario.

---

### Post by doobiest on 2008-12-17
A live cd will work. the point I was trying to get across is that you have to run a disk partitioner while you are NOT running the OS on the harddrive.  an ubuntu livecd has gparted on it so you can run the partition editor from there.

---

### Post by ElectricMoose on 2008-12-17
> **doobiest said:**
> A live cd will work. the point I was trying to get across is that you have to run a disk partitioner while you are NOT running the OS on the harddrive.  an ubuntu livecd has gparted on it so you can run the partition editor from there.

Well I don't want to get all complicated here, I just got Kubuntu to try it out, so in the future when my laptop gets outdated, I well entirely convert it. I only want a couple more GB of free space. I will go on linux a bit later today and try to see how much space I have left.

---

### Post by doobiest on 2008-12-17
Either free up space. I recommend installing xdiskusage to get an overview of where your diskspace is being eaten up, sudo apt-get install xdiskusage

Or resize the partition.

Or you could mount /home to a different harddrive if you find that your home directory is the source of the disk usage

Also did you confirm you are in fact out of space?  df -h

---

### Post by ElectricMoose on 2008-12-17
> **doobiest said:**
> Either free up space. I recommend installing xdiskusage to get an overview of where your diskspace is being eaten up, sudo apt-get install xdiskusage

Or resize the partition.

Or you could mount /home to a different harddrive if you find that your home directory is the source of the disk usage

Also did you confirm you are in fact out of space?  df -h

I will reconfirm I am out of space in just a moment, but I doubt I will be able to install xdiskusage considering how I am out of space, I tried to install flash and it did not work. I will repost in an hour or 2 with my disk status

---

### Post by ElectricMoose on 2008-12-17
> **ElectricMoose said:**
> I will reconfirm I am out of space in just a moment, but I doubt I will be able to install xdiskusage considering how I am out of space, I tried to install flash and it did not work. I will repost in an hour or 2 with my disk status

Something came up, I will have to do it tommorow

---

### Post by brandon88tube on 2008-12-17
You might have a memory problem, but I doubt it. This seems like a disk space problem instead.

---

### Post by |{urse on 2008-12-17
or a damaged hard disk problem.

---

### Post by ago on 2008-12-19
15gb is sufficient unless you installed on a fat partition

---

### Post by ElectricMoose on 2008-12-20
> **doobiest said:**
> Either free up space. I recommend installing xdiskusage to get an overview of where your diskspace is being eaten up, sudo apt-get install xdiskusage

Or resize the partition.

Or you could mount /home to a different harddrive if you find that your home directory is the source of the disk usage

Also did you confirm you are in fact out of space?  df -h

Er, it's gotten to a point where I can't even open terminal, I'll just go reinstall it and try ubuntu this time...

---

### Post by durrantj on 2008-12-21
> **doobiest said:**
> 
Or you could mount /home to a different harddrive if you find that your home directory is the source of the disk usage

Also did you confirm you are in fact out of space?  df -h

I would like to jump in on this discussion.  I have a Ubuntu wubi running on a machine with 2 320 GB hard drives.  I want to leave one for Windows (ouch) and use the 2nd one for Ubuntu.  The results of df -h gives me 

/host/ubuntu/disks/root.disk
                       13G   12G  1.2G  91% /
varrun                1.7G  232K  1.7G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G   68K  1.7G   1% /dev
devshm                1.7G  184K  1.7G   1% /dev/shm
lrm                   1.7G   39M  1.7G   3% /lib/modules/2.6.24-22-generic/volatile
gvfs-fuse-daemon       13G   12G  1.2G  91% /home/john/.gvfs
/dev/sdb1             296G   18G  263G   7% /media/disk

How do I mount my /home drive on sdb1?
Thanks in advance.

---

### Post by brandon88tube on 2008-12-22
> **durrantj said:**
> I would like to jump in on this discussion.  I have a Ubuntu wubi running on a machine with 2 320 GB hard drives.  I want to leave one for Windows (ouch) and use the 2nd one for Ubuntu.  The results of df -h gives me 

/host/ubuntu/disks/root.disk
                       13G   12G  1.2G  91% /
varrun                1.7G  232K  1.7G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G   68K  1.7G   1% /dev
devshm                1.7G  184K  1.7G   1% /dev/shm
lrm                   1.7G   39M  1.7G   3% /lib/modules/2.6.24-22-generic/volatile
gvfs-fuse-daemon       13G   12G  1.2G  91% /home/john/.gvfs
/dev/sdb1             296G   18G  263G   7% /media/disk

How do I mount my /home drive on sdb1?
Thanks in advance.

You would probably want to go the LVPM route and install it to the second hard drive that doesn't contain the Windows operating system.

---

### Post by durrantj on 2008-12-22
And I would go the LVPM route how?  I have things set up now like I like them and don't want to loose what I have.

---

### Post by brandon88tube on 2008-12-22
Here is a link [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

---

