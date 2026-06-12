---
title: "Setting up Amanda with a tape changer"
date: 2009-04-10
forum: General Help
---

### Post by wililupy on 2009-04-10
Hello,

I am new to Amanda on Ubuntu. I have successfully installed it on 8.10, but I am extremely confused when it comes to setting it up with a tape changer.

The tape changer is a ATL Powerstor L200, which Ubuntu found and called /dev/sg7 on my server. I also installed mtx so that I can manage it. I can get it to successfully load a tape using sudo mtx -f /dev/sg7 load 1 and it loads the tape from slot 0 to the drive. However, I am confused when it comes to actually setting it up in Amanda. Everything I have read is make sure that mtx works. Doing that, it works, but I don't know how to set it up from here. I know I need to add a configuration and a data pool, but all the howto's explain how to set it up using vtapes. I want to write directly to tape since the server only has a 33GB Hard drive, and trying to backup almost 800GB just won't work. 

I know that people have done this before since they all say they have, but it must be a well kept secret, since no one wants to share exactly how they did it. 

Any information on this would be greatly appreciated. 

Thanks,
Luke

---

### Post by wililupy on 2009-04-17
Finally got it working. It took reading the entire manpage for every command and configuration file, but I finally got it working. The little trick was mtx. Once I installed that little gem, it was almost easy.

Basically, after I installed it, I had permission issues with the amandabackup user. I added the user the the tape group and everything was good for permissions. Also, setting up the /etc/amanda/config$/changer.conf was a little tricky, but the amanda wiki had the settings for the chg-zd-mtx and once I had that all setup, amanda could then talk to the tape drive.

There were a couple things that I had to do with trial and error, and that was finding the tape drive. Luckly, ls -l /dev/sg* helped narrow down what the tape drive was on as well as running cat /proc/scsi/scsi and seeing what was what. 

Setting up the cron job failed however. Looking at the /var/log/syslog, it says the cron failed to login for my cron job as amandabackup. I'm hoping it was becuase I failed to set a password for the user. I set one this morning after seeing that my backup failed, and manually ran amdump, which performed the incremental perfectly. 

If anyone wants, I'll write a howto of how I setup my server to do tape backups with the changer. I managed to get this to work with a Quantum DLT7000 (My ATL L200) and a Quantum DLT8000 (A Sun StorEdge L9 with Barcode Reader) with minimal headaches. 

One thing to note though, If you can avoid it, don't use aptitude to get Amanda. Just download the binary from amanda.zmanda.com or download the source code and build it yourself. One thing I learned was downloading amanda with aptitude sets the user and group up to backup, which isn't bad, but when it comes to setting up the server, manually writing the configuration files is a huge hassle, where amserverconfig works way easier. 

Thanks to everyone at the Amanda Wiki, since I guess not too many people use Ubuntu as the backend of a backup server.

---

