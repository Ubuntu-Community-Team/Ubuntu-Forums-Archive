---
title: "Simple Backup Incomplete Backups"
date: 2008-12-26
forum: General Help
---

### Post by CrusaderAD on 2008-12-26
Does anyone know why when running a Simple Backup it backs up little or no data? I'm backing up some mapped drives on the network and it's always worked before. It will run the process, but when I find the folder upon completion, it's only like 103kb and has no data in the files folder.

---

### Post by CrusaderAD on 2009-01-15
Bump!

---

### Post by daaussie on 2010-03-15
Hi, i recently am trying this system & found a similar thing. Sometimes it does complete backups with file ending with ".ful", but most days it does a semi backup and has a file ending with ".inc". 

I thought maybe it was because I am accessing some of the files when the backup is running.

But I can't seem to clearly define what time the backup starts. I don't access the backup files from 8pm-6am everyday, but can't find the setting for this time range. The closest I found under the backup tabs was "Time/Precisely at/5 hours", but I still get the same .inc file.

Can someone tell me what the "Precisely at" means? You can change the hours up to 13 and you can choose minutes too. Is this a clock???

Thanks

---

### Post by chaanakya_chiraag on 2010-03-15
I would just move to rsync or something, as most of those gui (graphical) backup managers are just way too hard to debug.  OP, check out my post (second one in sig)

---

### Post by daaussie on 2010-03-15
PS I notice that the version installed is 0.10.4, whereas on the site they provide 0.10.5. 
So in terminal, I tried "sude apt-get remove sbackup" followed by reboot, followed by "sude apt-get install sbackup"

But it installs 0.10.4 again?????

weird

---

### Post by daaussie on 2010-03-15
can you explain how to install & use rsync briefly pleasee???

---

### Post by chaanakya_chiraag on 2010-03-16
Please check my tutorial (2nd one in signature).  If you don't understand something, post back here or on the tutorial and I'll do my best to answer your question.

---

### Post by CrusaderAD on 2010-03-16
Just an FYI guys, I use Keep now:

```
sudo apt-get install keep
```

Very nice backup program.

---

### Post by chaanakya_chiraag on 2010-03-16
I started out using graphical backup programs, but they wouldn't let me backup to a network drive, so I hacked together my own script :D  That's the beauty of Linux :)
- Chiraag

---

### Post by daaussie on 2010-03-20
I have solved the problem and thought I would post it here for others.
It was actually very simple and I shouldnt have missed it before

Simple Backup program now works well.

Background:
9.10 Ubuntu
I set it to backup network drives which is does fine. these are loaded automatically during boot through fstab

Solution:
Go to properties/Time, and under "Do a full backup at least once every" put 1 day. It will then do a full backup daily. It has done this 3 days running now. 
Sometimes an incomplete (.inc) appears but this looks like is for those files that have changed. which is good. 

What I havent figured out:
Is what the "Hour" and "Minute" time actually refers to. The maximum is 13 hours? 
Mine is set to 8 hours. Does this mean it does an inc. backup every 8 hours AND a full backup every day?
It says custom cron time is: 0.4 * * * but not sure what this means.

---

### Post by CrusaderAD on 2010-03-22
> **chaanakya_chiraag said:**
> I started out using graphical backup programs, but they wouldn't let me backup to a network drive, so I hacked together my own script :D  That's the beauty of Linux :)
- Chiraag

I networked them through fstab, then you can backup the directory that loads the networked drive. Works great.

---

### Post by cong06 on 2010-03-22
> **raptormanad said:**
> I networked them through fstab, then you can backup the directory that loads the networked drive. Works great.

rsync also handles ssh, so you don't even have to mount. Though you'd still have to enter the password...

---

### Post by chaanakya_chiraag on 2010-03-22
I personally mount the network drive as part of the script and sync the two directories.  Then, at the end, I unmount it.  All I need is the sudo password which I pass through the command ```
yes
```  It works great :)

---

### Post by cong06 on 2010-03-23
> **chaanakya_chiraag said:**
> I personally mount the network drive as part of the script and sync the two directories.  Then, at the end, I unmount it.  All I need is the sudo password which I pass through the command ```
yes
```  It works great :)

That's interesting...
It's unfortunate that it doesn't work with ssh. Though that's probably a security feature.

---

### Post by chaanakya_chiraag on 2010-03-23
> **cong06 said:**
> That's interesting...
It's unfortunate that it doesn't work with ssh. Though that's probably a security feature.

I've never tried mounting the NAS with SSH...I'm not even sure if it supports SSH!!  I did know, however, that it supported Samba, so I used smbmount as indicated in my guide.  Do you know how the security of Samba compares with that of SSH??

---

### Post by daaussie on 2010-03-23
I am a bit confused by what you guys are talking about, but I used the command in terminal on workstation
sudo apt-get install smbfs
this program automatically loads a specified network drive
edit the fstab file: sudo gedit /etc/fstab (ask me how it needs to be altered if you do not know how)
need to install the following program to load SERVER drives on booting workstation: sudo apt-get install smbfs
then must make the SERVER folders on WORKSTATION home folder: sudo mkdir /home/WORKSTATION USERNAME/DIRECTORY_ON_SERVER (do this for all server folders)
REBOOT computer

PS YOU NEED TO ALSO INSTALL and CONFIGURE SMBFS on your SERVER.

It works like magic!!!! and backups easily too using simple backups.
I also load MYOB software for WIndows off the server drive using WINE on workstation and it works 100%.

---

### Post by cong06 on 2010-03-24
> **chaanakya_chiraag said:**
> I've never tried mounting the NAS with SSH...I'm not even sure if it supports SSH!!  I did know, however, that it supported Samba, so I used smbmount as indicated in my guide.  Do you know how the security of Samba compares with that of SSH??

Well, I don't know the security of samba, but ssh encrypts data being sent, and often yells at me because it thinks I'm being [MITM attacked](http://en.wikipedia.org/wiki/Man-in-the-middle_attack). 

Explaination: SSH uses keys to make sure that the computer that you're signing into is what it says it is. If you know gpg you know how it works. Basically you "trust" the computer the first time you sign in, and if a key changes (ie some guy is hacking your connection... or in my case the IP address changes) then ssh will warn you that someone is wiretapping.


SSH is pretty secure. If you're worried about security I'd definitely go with ssh.

---

### Post by daaussie on 2010-03-24
Is my setup insecure? I don't understand. I have modem/router firewall, then a server, and connected workstations on the network. To access the server, the workstations still need server username/password in the fstab aswell.

If this isn't as secure as SSH (which is knew to me), can you provide all commands and install terminology for both server and workstations, so I can give it a shot.

Look forward to your response.

---

### Post by daaussie on 2010-03-24
PS for those of you who need further explanation of Simple Backup, 

I also now discover that you set the timer, its a 23 hour clock, so 20 hour is 8pm. But also if you set it to do a complete backup everyday, it does this. 

Otherwise it just does the regular daily backup, but only of files that have changed (i.e. incremental). 

So its quite an amazing backup program and works very well!

---

### Post by Rasa1111 on 2010-03-24
hey OP, 

 i had the same problem when using simple backup. 

Since I have switched to using **Deja Dup**, my backups work perfectly now. 
And it is sooo easy.  [https://launchpad.net/deja-dup](https://launchpad.net/deja-dup)

---

### Post by cong06 on 2010-03-25
> **daaussie said:**
> Is my setup insecure? I don't understand. I have modem/router firewall, then a server, and connected workstations on the network. To access the server, the workstations still need server username/password in the fstab aswell.

If this isn't as secure as SSH (which is knew to me), can you provide all commands and install terminology for both server and workstations, so I can give it a shot.

Look forward to your response.

On a closed network (like yours sounds...) no one untrusted can "easedrop" on your connection so there's no problem. I just wouldn't (and I wonder if routers even allow) samba outside of closed networks.

For example, when I want to connect to my computer that's across the country (clearly not in my local network) I would not use samba. I would use SSH.

You're probably fine, and if you're not very familiar with command-line, then ssh might not be an option. It'd be a good (educational) idea to get familiar with it though: [https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

---

