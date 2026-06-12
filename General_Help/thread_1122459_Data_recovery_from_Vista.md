---
title: "Data recovery from Vista"
date: 2009-04-11
forum: General Help
---

### Post by amitpartani on 2009-04-11
Hi,

Few days ago my thinkpad x61 laptop with Vista home basic refused to boot. It had some corrupt boot sector file. My laptop doesn't have a CD/DVD drive. To back up my data I installed Ubuntu 7.04 on an external hard drive and booted my laptop from external hard drive. 

My first goal is to recover my Vista data. When I mount my windows partition and go to Users directory, I get the following error

amitpartani@PARTANIS-Linux:/media/windows$ ls
A                       Garmin        ProgramData    System Volume Information
autoexec.bat            hiberfil.sys  Program Files  tvtpktfilter.dat
Boot                    Icons         $Recycle.Bin   Users
bootmgr                 Intel         RRbackups      WAUUPGRD
BOOTSECT.BAK            MSOCache      _SMA           Windows
config.sys              pagefile.sys  SWSHARE        YServer.txt
Documents and Settings  pdf995        SWTOOLS
DRIVERS                 PerfLogs      syslevel.lgl
amitpartani@PARTANIS-Linux:/media/windows$ cd Users/
amitpartani@PARTANIS-Linux:/media/windows/Users$ ls
ls: reading directory .: Input/output error
amitpartani@PARTANIS-Linux:/media/windows/Users$ 
amitpartani@PARTANIS-Linux:/media/windows/Users$ 


Is there a way by which I can access the data in Users directory.

My second goal is to fix the vista bootmanager. I know ms-sys is no longer supported by Ubuntu..Is there any other way I can fix Vista bootmgr withing Ubuntu..


Any help will be greatly appreciate. I really need to get my data out, matter of life and death..

Thanks,


Amit

---

### Post by amitpartani on 2009-04-13
35 views and no replies yet..I am getting desperate, please help

---

### Post by defaultusername on 2009-04-13
amitpartani,

I/O errors usually indicate hardware problems. Just because it's mountable doesn't always mean r/w is going to work. Given the sudden, unexplained corrupted boot sector, the disk being fubar makes sense. What filesystem does it use?

I'm not a data recovery expert, but you should always mirror on a *separate drive* in case of hardware failures. Recovery isn't always an option.

---

### Post by amitpartani on 2009-04-13
> **defaultusername said:**
> amitpartani,

I/O errors usually indicate hardware problems. Just because it's mountable doesn't always mean r/w is going to work. Given the sudden, unexplained corrupted boot sector, the disk being fubar makes sense. What filesystem does it use?

I'm not a data recovery expert, but you should always mirror on a *separate drive* in case of hardware failures. Recovery isn't always an option.

Thanks much for reply. Its NTFS file system. How do I mirror the drive?

---

### Post by amitpartani on 2009-04-16
Finally got it to work. I ordered an USB to SATA cable, took my hard drive out, treated it like an external hard drive and ran chkdsk from XP. It fixed the errors and bad sectors and recovered the data I wanted(possibly happened because drive was almost full before it crashed).

The Vista boot sector is still bad, but Ubuntu can easily view all the files on there, without any trouble.

---

