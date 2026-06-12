---
title: "Partition problem during installation"
date: 2008-12-14
forum: General Help
---

### Post by chjustc on 2008-12-14
I tried to install Kubuntu 8.10 for 64-bit machines on my desktop, which has windows Vista as the only operating system.

The installation disk was loaded OK. When the installation came to the part of partitioning hard disk, no windows partition can be found. The installation found /dev/sda and /dev/sdb. But, there was no partition table on either of them. All the space was free.

Then, I opened a shell prompt, and ran
```
ubuntu@ubuntu:~$ sudo fdisk -l
```
I got the results as follows,
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       76534   614759323+   7  HPFS/NTFS
/dev/sda2           76535       77826    10377990    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38fb89b5

Disk /dev/sdb doesn't contain a valid partition table
```
Then, I use testdisk to analyze /dev/sda, and got the following,
```
The harddisk (320 GB / 298 GiB) seems too small! (< 629 GB / 586 GiB)
Check the harddisk size: HD jummpers settings, BIOS detections

The following partitions can't be recovered:
Partition          Start         End        Size in sectors
HPFS-NTFS     0    1    1    76533  25463   1229518647
HPFS-NTFS   3917  133  57    75908  22848   1124411392
```
When I chose to deeper search /dev/sda, I got one more partion as follows,
```
Disk /dev/sda - 320 GB / 298 GiB - CHS 38914  255 63
   Partition         Start          End      Size in sectors
* FAT32 LBA   29574    0    134243  254  63  75023550 [FREEDOS]
```
When I listed the files in this partition, I saw file names in non-English characters, which I don't recognize at all.

I also analyzed and deeper analyzed /dev/sdb, and got the following,
```
Disk /dev/sdb - 320 GB / 298 GiB - CHS 38913 255 63
Current partition structure:
   Partition         Start          End      Size in sectors

Partition sector doesn't have the end mark OxAA55
```
What should I do to make the installation see the existing windows partition.

By the way, By the way, this machine is a new desktop that I bought from HP several months ago. It has windows Vista on it. I have not done anything about partitioning on it after I bought it.

I installed ubuntu several times on my own laptop and other desktops without any problem. I was always able to find the existing (windows) partition. I always left the windows partition alone or just cut the size of it from the end. But, this time, I don't know what is going on. I don't want to break anything on the windows partition.

Thanks.

---

### Post by bluefrog on 2008-12-14
this machine might be tattoed. you might not be able to install anything else (including windows xp) than what was installed initially (vista)

---

### Post by chjustc on 2008-12-14
> **bluefrog said:**
> this machine might be tattoed. you might not be able to install anything else (including windows xp) than what was installed initially (vista)
How do I check this?

If what you say is true, does it mean that there is no way to keep the windows partition if I want to install kubuntu?

---

### Post by bluefrog on 2008-12-14
if it is tattoed there is no way to have anything else than the original vista on your machine.
Ask your vendor or HP to find out if it is tattoed.

if it is and you have not been warned about it when you bought it then you should ask for replacement for a non tattoed. if they don't want, sue them.

---

### Post by chjustc on 2008-12-14
> **bluefrog said:**
> if it is tattoed there is no way to have anything else than the original vista on your machine.
Ask your vendor or HP to find out if it is tattoed.

if it is and you have not been warned about it when you bought it then you should ask for replacement for a non tattoed. if they don't want, sue them.
OK. I can try to do that.

By "there is no way to have anything else than the original vista on your machine", do you mean without formatting the disk?  In other words, can I erase the Vista partition and install ubuntu even when it is tattoed?

---

### Post by gsmbk on 2008-12-14
I guess your problem has something to do with the Vista new file system.
It's not the same NTFS that the Windows XP used to use.

Have you installed the supporting library to do so ?
check your installed packages for "libntfs-3g23"
```
The ntfs-3g driver is an open source, GPL licensed, third generation Linux
NTFS driver which was implemented by the Linux-NTFS project. It provides
full read-write access to NTFS, excluding access to encrypted files, writing
compressed files, changing file ownership, access right.
```[http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

and this one as well
[http://www.linux-ntfs.org/](http://www.linux-ntfs.org/)

BTW, why you're keeping Vista on your machine in the first place :P ?

---

### Post by chjustc on 2008-12-14
```
I guess your problem has something to do with the Vista new file system.
It's not the same NTFS that the Windows XP used to use.

Have you installed the supporting library to do so ?
check your installed packages for "libntfs-3g23"
```
The computer only has Vista on it. I'm using the installation CD of Kubuntu 8.10 to install kubuntu.  Do you mean that I should install "libntfs-3g23" during the installation?

```
BTW, why you're keeping Vista on your machine in the first place :P ?
```
My parents are also using this machine.  They like Vista better.

---

### Post by gsmbk on 2008-12-14
```
Do you mean that I should install "libntfs-3g23" during the installation?
```No, you can do it during the installation, or after it.

Go to your Synaptic Package Manager, and search for "libntfs-3g23".
Install it with all the required dependencies.

Try to mount the partitions again,after that. Or maybe you need to reboot once.

```
My parents are also using this machine.  They like Vista better. 
```Same here !! Fair enough :)

---

### Post by albinootje on 2008-12-14
> **chjustc said:**
> I tried to install Kubuntu 8.10 for 64-bit machines on my desktop, which has windows Vista as the only operating system.

The installation disk was loaded OK. When the installation came to the part of partitioning hard disk, no windows partition can be found. The installation found /dev/sda and /dev/sdb. But, there was no partition table on either of them. All the space was free.


I assume you used the desktop installation cdrom ?

Can you install gparted or qparted if it's not already there ?
(You can install new software during the Ubuntu-installation)

And see whether g- or qparted sees the windows-partitions correctly ?

---

### Post by chjustc on 2008-12-14
> I assume you used the desktop installation cdrom ?
Yes, I used kubuntu-8.10-desktop-amd64 installation cd.

> Can you install gparted or qparted if it's not already there ?
(You can install new software during the Ubuntu-installation)
Yes, I installed gparted by using
```
sudo apt-get install gparted
```
during the installation, but the problem persists.

> And see whether g- or qparted sees the windows-partitions correctly ?
I also used the gparted-0.3.9-13 live CD. The same problem persists.  And, the output from testdisk is also obtained by using the gparted live CD.

---

### Post by albinootje on 2008-12-14
Hmm :(
I would contact the hardware supplier then, as was suggested in another posting.

---

### Post by chjustc on 2008-12-14
> **albinootje said:**
> Hmm :(
I would contact the hardware supplier then, as was suggested in another posting.
OK. I will do that. 

But, let me ask this (although I asked in an earlier post but did not get answer):
Do you think I will be able to rebuild the partitions by using gparted live CD, and then install kubuntu?  I understand this might damage the Vista partition.

---

### Post by gsmbk on 2008-12-14
```
Do you think I will be able to rebuild the partitions by using gparted live CD, and then install kubuntu? I understand this might damage the Vista partition.
```

Definitely !!

Just back up your Vista files, and then use the gparted live cd.
Delete all the partitions, and have a fresh start :)

---

### Post by albinootje on 2008-12-14
I never heard about "Vista being tattoed" to the hard disk.

After a search-engine search i found this :
[http://www.computing.net/answers/windows-vista/vista-cloning-error/826.html](http://www.computing.net/answers/windows-vista/vista-cloning-error/826.html)

+++++++++++++++++++++
Yes it's HP time bomb that will go off whenever you try to tweak with its proprietary hardware and software that HP preinstalled - including Windows.

Put simply, Code Purple is a code that says you have violated HP tattoo. What the heck is that? It resembles Windows product activation mechanism.

The only way to get it fixed is by taking your baby to a HP authorized repair center where they have a special software called DMI utility. HP prohibit anyone - other than those designated as authorized - to get a copy of it. What does it do? It simply re-brands the software & hardware as HP.

At one time I tried coaxing a guy I know in giving me a copy - he won't because it usually call home and they will know where it's coming from

Use this post to braodcast to the world why no one should buy OEM brand machines with OEM preinstalled & tattooed Windows Vista apart from M$'s own Windows Vista.
+++++++++++++++++++++++++++++++++++++

Since you mentioned it is a HP machine you're working on, this might be the case.

---

### Post by chjustc on 2008-12-14
> **gsmbk said:**
> ```
Do you think I will be able to rebuild the partitions by using gparted live CD, and then install kubuntu? I understand this might damage the Vista partition.
```

Definitely !!

Just back up your Vista files, and then use the gparted live cd.
Delete all the partitions, and have a fresh start :)
OK. This will be my last option.

---

### Post by chjustc on 2008-12-14
> **albinootje said:**
> I never heard about "Vista being tattoed" to the hard disk.

After a search-engine search i found this :
[http://www.computing.net/answers/windows-vista/vista-cloning-error/826.html](http://www.computing.net/answers/windows-vista/vista-cloning-error/826.html)

+++++++++++++++++++++
Yes it's HP time bomb that will go off whenever you try to tweak with its proprietary hardware and software that HP preinstalled - including Windows.

Put simply, Code Purple is a code that says you have violated HP tattoo. What the heck is that? It resembles Windows product activation mechanism.

The only way to get it fixed is by taking your baby to a HP authorized repair center where they have a special software called DMI utility. HP prohibit anyone - other than those designated as authorized - to get a copy of it. What does it do? It simply re-brands the software & hardware as HP.

At one time I tried coaxing a guy I know in giving me a copy - he won't because it usually call home and they will know where it's coming from

Use this post to braodcast to the world why no one should buy OEM brand machines with OEM preinstalled & tattooed Windows Vista apart from M$'s own Windows Vista.
+++++++++++++++++++++++++++++++++++++

Since you mentioned it is a HP machine you're working on, this might be the case.
OK.  I will call HP and see what happens. Or, I will get rid of Vista by removing existing partitions and setting up new ones.

---

### Post by gsmbk on 2008-12-14
> 
Originally Posted by albinootje                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=6368509#post6368509")                 
                 I never heard about "Vista being tattoed" to the hard disk.

After a search-engine search i found this :
[http://www.computing.net/answers/win...error/826.html]("http://www.computing.net/answers/windows-vista/vista-cloning-error/826.html")

+++++++++++++++++++++
Yes it's HP time bomb that will go off whenever you try to tweak with its proprietary hardware and software that HP preinstalled - including Windows.

Put simply, Code Purple is a code that says you have violated HP tattoo. What the heck is that? It resembles Windows product activation mechanism.This is really weired !! And totally unacceptable !!

See this post...

[http://www.electronista.com/articles/08/12/11/hp.desktop.with.linux/](http://www.electronista.com/articles/08/12/11/hp.desktop.with.linux/)

Is this the same HP company ?? Jezz !! How controversial could this be !!
--------------------------------------------
@chjustc

Try this before going to your final solution... 
```
sudo apt-get install libntfs-3g23 
```Restart your machine, and try to mount the partitions again.
if it works, you're done.

Otherswise, as it seems, you should call HP, before going to the gparted solution, because it might cause a hard disk malfunction, and you might lose your hard disk.

Keep us posted.

---

### Post by caljohnsmith on 2008-12-14
It is clear from your first post that you have sda and sdb in a RAID configuration, and that is why the Kubuntu installer chokes. If you want to install Ubuntu under RAID, you could look at:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Or if you can figure out how to break your two drives out of the RAID setup without breaking Vista, then installing Kubuntu should be easy.

---

### Post by chjustc on 2008-12-14
> This is really weired !! And totally unacceptable !!

See this post...

[http://www.electronista.com/articles/08/12/11/hp.desktop.with.linux/](http://www.electronista.com/articles/08/12/11/hp.desktop.with.linux/)

Is this the same HP company ?? Jezz !! How controversial could this be !!
Well, I'm pretty sure it is the HP company you are talking about. I found a deal issued by HP online, called them up, and bought the machine.


> Try this before going to your final solution... 
```
sudo apt-get install libntfs-3g23 
```Restart your machine, and try to mount the partitions again.
if it works, you're done.
I understand that I can install libntfs-3g23.  But, I am not sure what you mean by restarting the computer. I'm using the CD to install.  If I restart, I need to sudo apt-get install libntfs-3g23 again, right?  I will try this without restarting and see what happens.

> Otherswise, as it seems, you should call HP, before going to the gparted solution, because it might cause a hard disk malfunction, and you might lose your hard disk.
OK, Thanks.


> Keep us posted.
Unfortunately, I am going to another country in a few days. If I don't fix it now, I can try again a few weeks later.

---

### Post by chjustc on 2008-12-14
> It is clear from your first post that you have sda and sdb in a RAID configuration, and that is why the Kubuntu installer chokes. If you want to install Ubuntu under RAID, you could look at:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
OK. I can try this. Thanks.

> Or if you can figure out how to break your two drives out of the RAID setup without breaking Vista, then installing Kubuntu should be easy.
Thanks[/QUOTE]
Any hint about how to do this?

---

### Post by albinootje on 2008-12-14
> **chjustc said:**
> 
Any hint about how to do this?

Probably by turning of any RAID options in your BIOS, and choose "plain" IDE, but i have no idea what that means for your current MS-Vista installation (whether it will break or not).

---

### Post by caljohnsmith on 2008-12-14
> **chjustc said:**
> 
Any hint about how to do this?
I sincerely wish I knew so I could help, but unfortunately I only have a little experience with RAID; if you do figure out how to disable your RAID configuration, please let me know how you did it so I'll know for future reference. :)

---

### Post by chjustc on 2008-12-14
> **caljohnsmith said:**
> I sincerely wish I knew so I could help, but unfortunately I only have a little experience with RAID; if you do figure out how to disable your RAID configuration, please let me know how you did it so I'll know for future reference. :)

OK, I think that I can get rid of Vista.  That means I don't mind if the installation of ubuntu erase the Vista partition.

Do I still need to worry about RAID during installation?

---

### Post by caljohnsmith on 2008-12-14
> **chjustc said:**
> OK, I think that I can get rid of Vista.  That means I don't mind if the installation of ubuntu erase the Vista partition.

Do I still need to worry about RAID during installation?
That's right, you don't need to worry about RAID during the installation since you don't mind erasing Vista. You might possibly have booting problems though after the installation if the RAID is set up in your BIOS. I would check your BIOS first and make sure RAID is disabled there, and if so, proceed with installing Kubuntu. Let me know how it goes.

---

### Post by chjustc on 2008-12-14
> **caljohnsmith said:**
> That's right, you don't need to worry about RAID during the installation since you don't mind erasing Vista. You might possibly have booting problems though after the installation if the RAID is set up in your BIOS. I would check your BIOS first and make sure RAID is disabled there, and if so, proceed with installing Kubuntu. Let me know how it goes.
OK, I deleted the existing RAID and installed kubuntu.  It successfully boots up. No Vista on my machine, only kubuntu. :)

---

### Post by caljohnsmith on 2008-12-15
Just for my future reference, did you have to disable any RAID settings in your BIOS? Anyway, cheers and have fun with your new Kubuntu install. :)

---

### Post by chjustc on 2008-12-15
> **caljohnsmith said:**
> Just for my future reference, did you have to disable any RAID settings in your BIOS? Anyway, cheers and have fun with your new Kubuntu install. :)
I don't know whether I had to, but I did do something that seems to be disabling RAID to me.

What I did is as follows:
When booting up, I first press F10 to enter the so called SetUP and tried to find anything related to RAID and did not find any.  Then, I quit the SetUP and followed instruction on the screen to enter NVIDIA RAID setting by pressing Ctrl+N.  In this RAID setting stuff, I chose to delete existing RAID.  I was immediately asked to set up new RAID, but I chose to quit.

And you know what's after that.  I insert the kubuntu CD ...

---

### Post by gsmbk on 2008-12-15
> OK, I deleted the existing RAID and installed kubuntu.  It successfully boots up. No Vista on my machine, only kubuntu.

Congrats :)

---

