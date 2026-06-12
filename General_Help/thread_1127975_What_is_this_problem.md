---
title: "What is this problem?"
date: 2009-04-17
forum: General Help
---

### Post by Naz_Farooq on 2009-04-17
Hello guys,
I have been using ubuntu 8.10 intrepid for a long last 5 months. I have faced some challenges but with the help of ubuntu forum and my self interest, I have been defeating those challenges well. Now I have been facing a challenge again and need help from my seniors. I need to update my system with update manager, but whenever I press 'check'  button on update manager, it gives me some error of signature and some links error. It has been 46 days when I last updated my system. I am attaching a picture of the error too so that u can easily find a solution for me. I will appreciate any help from you in this regard.

Thanks in advance.

---

### Post by Arup on 2009-04-17
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com xxxxxx 

Replace the xxxx with the numbers being shown on the screen one by one, this way all the signatures would be imported and you won't find the error anymore.

---

### Post by kpkeerthi on 2009-04-17
Before you upgrade to Jaunty, you might want to remove the non-standard (3rd party repos like ppa) ubuntu repositories and the packages you have installed from those repositories as this may lead to a broken upgrade. Look in System -> Admin -> Software Source.

---

### Post by Naz_Farooq on 2009-04-17
> **Arup said:**
> sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com xxxxxx 

Replace the xxxx with the numbers being shown on the screen one by one, this way all the signatures would be imported and you won't find the error anymore.

Thanks a lot Arup, but can you please tell me something beneficial for other errors too.
The result of your suggestion is also attached. Please have a look at it and give me some solution.

---

### Post by Naz_Farooq on 2009-04-17
> **kpkeerthi said:**
> Before you upgrade to Jaunty, you might want to remove the non-standard (3rd party repos like ppa) ubuntu repositories and the packages you have installed from those repositories as this may lead to a broken upgrade. Look in System -> Admin -> Software Source.

Here is a picture of my 'third party software' list from software sources. Take a look and please tell me what to do.

---

### Post by kpkeerthi on 2009-04-17
> **Naz_Farooq said:**
> Here is a picture of my 'third party software' list from software sources. Take a look and please tell me what to do.

You should be good. You don't have to manually disable the 3rd party repositories. Ubuntu has already done that for you (Wow!). Did you notice the lines reading "Disabled on upgrade to Jaunty"?

---

### Post by Naz_Farooq on 2009-04-17
> **kpkeerthi said:**
> You should be good. You don't have to manually disable the 3rd party repositories. Ubuntu has already done that for you (Wow!). Did you notice the lines reading "Disabled for Jaunty upgrade"?

Yes, I noticed it and wondered on it same as you did. But there is a problem in upgrading, it is saying 'you don't have enough disk space for new upgrade'. I have 17 BG Z: drive for ubuntu 8.10 intrepid and have updated it till now. Is it possible in some way that I may upgrade it in same space. What should I do now. System restarted automatically after giving me low disk space message.

---

### Post by kpkeerthi on 2009-04-17
You seem to be using a Middle-east mirror. Can you switch to Main server.

System => Administration => Software Sources. Change to "Main Server" in the "Download from:" drop down and try again.

---

### Post by kpkeerthi on 2009-04-17
> **Naz_Farooq said:**
> Yes, I noticed it and wondered on it same as you did. But there is a problem in upgrading, it is saying 'you don't have enough disk space for new upgrade'. I have 17 BG Z: drive for ubuntu 8.10 intrepid and have updated it till now. Is it possible in some way that I may upgrade it in same space. What should I do now. System restarted automatically after giving me low disk space message.

Can you post the outputs of
```
df -h
``` and ```
mount
```?

---

### Post by Naz_Farooq on 2009-04-17
> **kpkeerthi said:**
> Can you post the outputs of
```
df -h
``` and ```
mount
```?

out put for df -h is as follows
```
 nazfarooq@nazfarooq-laptop:~$ sudo df -h
[sudo] password for nazfarooq: 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              15G   12G  2.1G  86% /
tmpfs                 758M     0  758M   0% /lib/init/rw
varrun                758M  380K  758M   1% /var/run
varlock               758M     0  758M   0% /var/lock
udev                  758M  2.9M  756M   1% /dev
tmpfs                 758M  304K  758M   1% /dev/shm
lrm                   758M  2.0M  756M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda2              38G   32G  5.5G  86% /media/data
/dev/sdb1             942M  826M  117M  88% /media/disk
nazfarooq@nazfarooq-laptop:~$ 
```

and out put for mount is
```
 nazfarooq@nazfarooq-laptop:~$ mount
/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sda2 on /media/data type vfat (rw,utf8,umask=007,gid=46)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/nazfarooq/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nazfarooq)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
nazfarooq@nazfarooq-laptop:~$ 
```

any help would be appreciative.

---

### Post by kpkeerthi on 2009-04-17
> 
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              15G   12G  2.1G  86% /

```


Your root (and /home) is 86% full (2 GB free). I guess Ubuntu requires more than 2 GB for an upgrade (from what I understand from the error you got).

---

### Post by kpkeerthi on 2009-04-17
You can upgrading using the Alternate CD.

[http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD](http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD)

---

### Post by Naz_Farooq on 2009-04-17
> **kpkeerthi said:**
> Your root (and /home) is 86% full (2 GB free). I guess Ubuntu requires more than 2 GB for an upgrade (from what I understand from the error you got).

So what should I do now? How can I make more than 2GB space in my root /home directory?
Is there any solution for that?

---

### Post by Naz_Farooq on 2009-04-17
> **kpkeerthi said:**
> You can upgrading using the Alternate CD.

[http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD](http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD)

Dear it is taking much more time, it will download 1st in my system and then will be installed.
Can I not make space in my home folder in any way?
There must be some way.

---

### Post by kpkeerthi on 2009-04-17
You can. Use **gparted** (I believe it is also in System -> Admin -> Discs & Partitions) from **Ubuntu [COLOR="Red"]Live[/COLOR] CD** to 'expand' /dev/sda3 (your root /). To do that, you need to first shrink the partition next to /dev/sda3 and make some free space. Then, drag /dev/sda3 to fill in the free space you just created.

**Note: Backup your data before resizing your partitions.**

---

### Post by Naz_Farooq on 2009-04-17
> **kpkeerthi said:**
> You can. Use **gparted** (I believe it is also in System -> Admin -> Discs & Partitions) from **Ubuntu [COLOR="Red"]Live[/COLOR] CD** to 'expand' /dev/sda3 (your root /). To do that, you need to first shrink the partition next to /dev/sda3 and make some free space. Then, drag /dev/sda3 to fill in the free space you just created.

**Note: Backup your data before resizing your partitions.**

Will you please tell me some commands briefly. It says be careful it is an important partition, if you do some thing wrong it would damage your OS. If you tell me some commands, I would not be doing any wrong then.
Thanks for guiding me.

---

### Post by kpkeerthi on 2009-04-17
It a GUI tool. This page has got everything you need. [http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by Naz_Farooq on 2009-04-17
> **kpkeerthi said:**
> It a GUI tool. This page has got everything you need. [http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

I tried dparted but when I click on the partition and click the tab 'partion' to resize it or move it, I cannot edit it, means I can't do that. What is the solution for this. Is it login problem?

---

### Post by kpkeerthi on 2009-04-17
Are you in Live CD?

---

### Post by Naz_Farooq on 2009-04-17
> **kpkeerthi said:**
> Are you in Live CD?

nops, is it necessary?

---

### Post by codeseer on 2009-04-17
Yeah, use the live CD so that nothing is really active while you're resizing.

---

### Post by kpkeerthi on 2009-04-17
> **Naz_Farooq said:**
> nops, is it necessary?

Yes, You also need some patience. If you read my last post, I have explicity mentioned about using Live CD for the purpose.

---

### Post by Naz_Farooq on 2009-04-18
> **kpkeerthi said:**
> Yes, You also need some patience. If you read my last post, I have explicity mentioned about using Live CD for the purpose.

Thank You, I will be having patience now onwards.
Actually I did not have the that time.

---

