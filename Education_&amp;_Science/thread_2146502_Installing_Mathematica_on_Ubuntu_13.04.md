---
title: "Installing Mathematica on Ubuntu 13.04"
date: 2013-05-18
forum: Education &amp; Science
---

### Post by jialinl on 2013-05-18
Error message: Extraction failed. No space left on .4849
.Removing temporary files.

I run the following commands:
owner@ubuntu:~/Downloads$ cd .
owner@ubuntu:~/Downloads$ cd ..
owner@ubuntu:~$ cd Documents/
owner@ubuntu:~/Documents$ cd Mathematica/
owner@ubuntu:~/Documents/Mathematica$ sudo sh ./Mathematica_9.0.1_LINUX.sh 
Mathematica Secured 9.0.1 for LINUX Installer Archive

Verifying archive integrity. 

I'm certain there is enough disk space. So I am confused about this error message. Can anyone help? Thanks.

---

### Post by monkeybrain2012 on 2013-05-18
If you install with sudo mathematica get installed in /usr/local/ Are you sure you have enough space there? (as oppose to your home directory) Try run the install script without sudo and see what happens (this will install Mathematica in your home)

---

### Post by jialinl on 2013-05-18
What command do I run without sudo? Just sh ./Mathematica_9.0.1_LINUX.sh?

---

### Post by monkeybrain2012 on 2013-05-18
Yes.

---

### Post by jialinl on 2013-05-18
Still says the same thing.
owner@ubuntu:~/Documents/Mathematica$ sh ./Mathematica_9.0.1_LINUX.sh 
Mathematica Secured 9.0.1 for LINUX Installer Archive

Verifying archive integrity. 
Extracting installer. .......................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................Extraction failed. No space left on .5039
.Removing temporary files.

---

### Post by jialinl on 2013-05-18
How can I check how much space I have left? This is really strange. I seriously doubt there is no space. Maybe I didn't allocate enough space to my home drive? How can I change that?
Sorry these are super elementary questions...

---

### Post by steeldriver on 2013-05-18
You can check free space with the df command e.g.

```
df -h
```

According to this page, it needs 5.5GB --> [http://www.wolfram.com/mathematica/features/system-requirements.html](http://www.wolfram.com/mathematica/features/system-requirements.html)

---

### Post by jialinl on 2013-05-18
I just checked and 
owner@ubuntu:~/Documents/Mathematica$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0       17G   16G  846M  96% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            2.9G  4.0K  2.9G   1% /dev
tmpfs           588M  900K  587M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.9G   84K  2.9G   1% /run/shm
none            100M   28K  100M   1% /run/user
/dev/sda2       581G  109G  473G  19% /host


How may I install Mathematica in the /host drive?
Sorry these are super elementary questions...

---

### Post by monkeybrain2012 on 2013-05-18
Well how did you install Ubuntu? Is this WUBI??

---

### Post by jialinl on 2013-05-19
Sorry, what is WUBI?

I used to have Windows 7, then I directed download Ubuntu on my C dirve and installed it.

---

### Post by monkeybrain2012 on 2013-05-19
So you are using WUBI. You downloaded a Windows installer which is an .exe file, and installed in your C drive, this means inside the WIndows file system (Linux doesn't use terminology like "C drive". :)). WUBI is a demo that installed inside Windows to give you a taste of Ubuntu, but it is not a real installation and not meant for serious use. It has many limitations and one being the size limit (as far as I know) 

   Unfortunately I can't help you there other than to tell you to make a separate partition and install Ubuntu for real.

---

### Post by jialinl on 2013-05-20
Okay. So how can I do a real installation? I thought this is as real as it could be. lol.

---

### Post by monkeybrain2012 on 2013-05-20
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

If you have UEFI there may be some extra work. Check out oldfred's links here
[http://ubuntuforums.org/showthread.php?t=2140521](http://ubuntuforums.org/showthread.php?t=2140521)

---

### Post by jialinl on 2013-05-20
Thanks a lot for the help. I will seriously consider reinstalling everything. It seems to be quite a bit of work.

---

### Post by ImmanuelElim on 2013-06-01
Hi jialinl,

Have you installed mathematica 9.0.1 linux version successfully? 
I have installed Ubuntu 12.04 within Win 7 and mathematica 9.0.1 linux can be 
installled on Ubuntu. If you need help, post it and see what I can do.

---

### Post by rewyllys on 2013-07-06
> **zeeshanaayan07 said:**
> Where is the download link..?
Here is a download link for *Mathematica*: [https://www.wolfram.com/mathematica/trial/](https://www.wolfram.com/mathematica/trial/)

---

### Post by RichardET on 2013-08-18
My advice is to stick with Win. 7 and buy the Windows version of Mathematica.

---

### Post by rewyllys on 2013-08-18
> **RichardET said:**
> My advice is to stick with Win. 7 and buy the Windows version of Mathematica.
Offering your preference is OK, but it doesn't do much to help people install* Mathematica* on Ubuntu, the topic of this thread.

---

### Post by RichardET on 2013-08-19
I was actually trying to be helpful;  I use SAS JMP and prior to version 9, they supported three systems, OS/X, Linux, and Windows.  This was back in 2009 and i wanted in the worst way to go with the Linux version, but I noticed that the feature set for the Linux version was always "behind" the Windows version, and I kept procrastinating buying JMP.  When version 9 came out, I did bite, but by the then the Linux version was gone;  Software like Mathematica and JMP are expensive and one should always consider which platorm best suits the software, so one gets the most out of it.  
For me, I try to go the path of least resistance with software, that way I am the most productive with it.  These are my ideas only, and I am not trying to convert anyone.

---

### Post by monkeybrain20122 on 2013-09-03
> **RichardET said:**
> I was actually trying to be helpful;  I use SAS JMP and prior to version 9, they supported three systems, OS/X, Linux, and Windows.  This was back in 2009 and i wanted in the worst way to go with the Linux version, but I noticed that the feature set for the Linux version was always "behind" the Windows version, and I kept procrastinating buying JMP.  When version 9 came out, I did bite, but by the then the Linux version was gone;  Software like Mathematica and JMP are expensive and one should always consider which platorm best suits the software, so one gets the most out of it.  
For me, I try to go the path of least resistance with software, that way I am the most productive with it.  These are my ideas only, and I am not trying to convert anyone.

The thread is about Mathematica, not SAS. Mathematica works fine in Linux, OP's problem is that he installed Ubuntu with Wubi and run into the size limit, it is not because of anything wrong with the Linux version. I went to a top research university in Canada we use software such as Mathematica and Matlab all on Linux or Unix. In fact Linux is the preferred platform for scientific work, so all our hard core science departments (Math, physics and chemistry and most of Computer science) use Linux (or Unix).

---

### Post by rewyllys on 2013-09-03
> **monkeybrain20122 said:**
> . . . In fact Linux is the preferred platform for scientific work, so all our hard core science departments (Math, physics and chemistry and most of Computer science) use Linux (or Unix).
Well said!

---

