---
title: "Kubuntu multiple hard drives issue"
date: 2008-12-18
forum: General Help
---

### Post by ChrisR1982 on 2008-12-18
Hi I just wana say I am new to Linux, I only installed Kubuntu 3 days ago.. up until now I have had no problems and no reason to use Windows... but now.. I have a problem.

OK... Here is my setup..

Single hard drive with 2 partitions:

Windows XP C:/
Kubuntu D:/ ubuntu/
My Windows Documents D:/My Documents

So a dual boot system... straight forward so far..

BUT kubuntu cant see D drive!

When I browse using Dolphin I can't find my D drive anywhere!!

Here is what Dolphin shows

[IMG]http://e.imagehost.org/0901/LinuxProblem.png[/IMG]

In the bottom left you can see Places. It shows ONE hard drive.. and when I go in there it is my C drive where Windows is. Root takes me to my kubuntu folder on D... When I select MEDIA it shows my laptops internal dvd drive... my USB dvd drive.. a virtual image drive.. My USB memory stick.. and My C drive... NOT my D drive..

I moved to Kubuntu for many reasons.. oneof them was a repeated problem with my cd/dvd drives.. I kept getting "You dont have burn rights" a clean install of windows sorted that.. but I got sick of having to do that every 2 months or so! I am getting that error now and I have finally had enough. So that just pushed me to install kubuntu. I can now burn disks no problem!

However... my D drive is almost full. I need to get my documents off of it and on to dvds... HOWEVER as kubuntu cant see the D drive I cant access the documents.. it is getting VERY tedious booting to windows and moving 3.5GB of data from my D drive to my USB stick and then rebooting into kubuntu, copying the data to my documents folder there, rebooting to windows, copy more data to usb pen, reboot to kubuntu.. THEN burn 4.5GB worth to a dvd... then starting the whole process again.. its taking me ages! And all because I can't access my D drive. 

I even tried booting into windows, copying my documents into a kubuntu folder and rebooting to kubuntu.. but the documents dont show up... its really beginning to frustrate me now.

PLEASE can someone help!?!

---

### Post by lovelyvik293 on 2008-12-18
I think you installed the kubuntu on the D drive.
Please tell about how you installed the kubuntu?

---

### Post by ChrisR1982 on 2008-12-18
I installed Windows to C drive and made a 2nd partition using Drive Image.

I then started windows. I put my Kubuntu disk into my PC (when in windows xp) and it gave me the option of installing Kubuntu alongside Windows (the 2nd of 3 options). I chose to Install Kubuntu to my D drive. SO kubuntu can access Kubuntu folder on D drive.. just not any other part of my D drive.

---

### Post by lovelyvik293 on 2008-12-18
Ok then your D drive is not formated.
Just check in the "/".It must be there.
You can post the output of 
```

ls /

```

---

### Post by taurus on 2008-12-18
Open a terminal and post the outputs of these commands.

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by ChrisR1982 on 2008-12-18
D drive is not formatted? Umm.. if it wasnt formatted then how do I have lots of documents on it and have been using it for 5 months now in windows? U mean not formatted fro kubuntu to see it? surely if i format it then I will then lose my documents?

post the results of those commands? umm.. ok

**ls /**
```
bin  boot  cdrom  dev  etc  home  host  initrd.img  initrd.img.old  lib  lost+found  media  mnt  opt  proc  root  sbin  srv  sys  tmp  usr  var  vmlinuz  vmlinuz.old
```

**df -h**
```
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk                          
                      6.0G  2.8G  2.9G  50% /         
tmpfs                1012M     0 1012M   0% /lib/init/rw
varrun               1012M  216K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M  2.9M 1009M   1% /dev
tmpfs                1012M     0 1012M   0% /dev/shm
/dev/sda5             125G  113G   12G  91% /host
lrm                  1012M  2.0M 1010M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda1              25G  9.7G   16G  39% /media/disk
/dev/sdb1             3.8G  3.7G   27M 100% /media/CHRIS USB
```

**cat /etc/fstab**
```
# /etc/fstab: static file system information.                                     
#                                                                                 
# <file system> <mount point>   <type>  <options>       <dump>  <pass>            
proc            /proc           proc    defaults        0       0                 
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

```

**bash Sudu fdisk -1**
```
bash: sudu: command not found
```

---

### Post by ChrisR1982 on 2008-12-18
```
/dev/sda5             125G  113G   12G  91% /host
/dev/sda1              25G  9.7G   16G  39% /media/disk

```

Not that I understood half of what I posted above... I think SDA1 is my C drive.. and SDA5 is my D drive.. how do I access that one? Where do I go?

---

### Post by Skripka on 2008-12-18
> **ChrisR1982 said:**
> ```
/dev/sda5             125G  113G   12G  91% /host
/dev/sda1              25G  9.7G   16G  39% /media/disk

```

Not that I understood half of what I posted above... I think SDA1 is my C drive.. and SDA5 is my D drive.. how do I access that one? Where do I go?

Sda1 and sda5 are partitions on the same physical drive.  Sda1 is almost maxed completely maxed out space wise (it is 91% full).  I'd wager Sda1 is your docs--but I'd be curious if you could mount the partition--as it is so full.

---

### Post by taurus on 2008-12-18
You can access /dev/sda1 from /media/disk and /dev/sda5 is at /host.

---

### Post by ChrisR1982 on 2008-12-18
Yeh as my DVD writer has not been working on Windows my hard drive has gradually got fuller and fuller and I finally had enough, hence me installing kubuntu. Kubuntu burns disks no problem using the same drive.. thats micro$haft windblow$ for ya!

**taurus** you are a star!!!!!!!!!!! Thats EXACTLY what I was looking for!! So whenever I want to access my D drive I just go to HOST. Thanks a lot!!! :)

*Documents folder added to Places*

Cheers all :)

---

### Post by ChrisR1982 on 2008-12-22
This can be locked as sorted :)

---

