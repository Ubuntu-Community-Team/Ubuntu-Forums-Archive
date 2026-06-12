---
title: "Connecting the dots"
date: 2009-06-18
forum: General Help
---

### Post by Javijavi on 2009-06-18
Ok, so being my first foray into linux with the goal of creating a file server for my LAN and associated windows boxes, I have been having to learn to drive all over again as does anybody diving into a totally foreign system. So here's what I have done so far; can you tell me if I am headed down the right path?

1) Install ubuntu
2) Download Disk Management software for recognizing addition of new hard drives
3) Install 3 large format harddrives
4) Harddrives are recognized but not formatted
5) Download GParted and format harddrives
6) Harddrives are now recognized and formatted with ext3/4 file system, but I cant write to drives
7) Take ownership of said harddrives? This is where I am stuck. I cant find a way to actually use the harddrives yet. I dont have write permission to the drives. I cant find a tool to examine drive properties and access permissions.

And my next steps will be

9) use logical volume manager to combine extra harddrives into one logical spanned unit. 
10) download and configure samba for access by windows workstations

Then I think I will be finished eh?

---

### Post by geirha on 2009-06-18
Only root can change ownership of files and folders, so:

Hit Alt+F2 to get the run-dialog, then run "gksu nautilus". Browse to /media -> right click a mount point -> select properties -> permissions tab -> make your regular user the owner.

Another way is to install [nautilus-gksu]("apt://nautilus-gksu"), which will give you a new option, "Open as administrator" in the right-click menu of nautilus.


Can't help you on 9 as I have little experience with raid setups. For samba, see [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by rushikesh988 on 2009-06-18
> **geirha said:**
> Only root can change ownership of files and folders, so:

Hit Alt+F2 to get the run-dialog, then run "gksu nautilus". Browse to /media -> right click a mount point -> select properties -> permissions tab -> make your regular user the owner.

Another way is to install [nautilus-gksu]("apt://nautilus-gksu"), which will give you a new option, "Open as administrator" in the right-click menu of nautilus.


Can't help you on 9 as I have little experience with raid setups. For samba, see [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
I got the simple way brother no need to install anything ..

just go to terminal and type  
sudo nautilus  


thats it!

---

### Post by poundjd on 2009-06-18
You may try searching on "file ownership Linux" at google, and then reading the man pages of the commands that pop up.  I did and this was first or second [http://www.tuxfiles.org/linuxhelp/fileowner.html](http://www.tuxfiles.org/linuxhelp/fileowner.html). 

  I'm new and this is what I do when I am stuck.  Fast as some of these questions get answered here in the forum,  You will learn more and retain more of it if you do all of the research.

Now how do I find out how to have an application save a file using a list of usernames from a LDAP directory, on a Ubuntu server instead of the process owners username.

-jeff
> **Javijavi said:**
> Ok, so being my first foray into linux with the goal of creating a file server for my LAN and associated windows boxes, I have been having to learn to drive all over again as does anybody diving into a totally foreign system. So here's what I have done so far; can you tell me if I am headed down the right path?

1) Install ubuntu
2) Download Disk Management software for recognizing addition of new hard drives
3) Install 3 large format harddrives
4) Harddrives are recognized but not formatted
5) Download GParted and format harddrives
6) Harddrives are now recognized and formatted with ext3/4 file system, but I cant write to drives
7) Take ownership of said harddrives? This is where I am stuck. I cant find a way to actually use the harddrives yet. I dont have write permission to the drives. I cant find a tool to examine drive properties and access permissions.

And my next steps will be

9) use logical volume manager to combine extra harddrives into one logical spanned unit. 
10) download and configure samba for access by windows workstations

Then I think I will be finished eh?

---

### Post by Chronon on 2009-06-18
> **rushikesh988 said:**
> I got the simple way brother no need to install anything ..

just go to terminal and type  
sudo nautilus  


thats it!

That's a less preferable way than rushikesh988 mentioned.  I believe that gksudo is preferable to sudo when running a GUI application.

---

### Post by Javijavi on 2009-06-22
Success! File server appears to be up and running! 1.2 TB of backup storage space. I tested both rushkins's and gheira's method for drive permission's. Rushkin's was a little faster and worked as advertised, gheira's was predictably more user friendly and "sticks in my memory" stronger than the console command. I am pleased with the server now that it appears to be fully functional. Still had some quirks where no guide could help out, such as user accounts in an active directory domain with samba and more read/write permission access woes. I eventually had to just tell samba to grant any guest root level access. But this is ok since it resides behind NAT and who's job role is nothing more than to act as a glorified NAS device. Probably a better way to handle this but I'm still wiping my forehead with relief now that backups are writing. 

For anyone who stumbles across this in the future, reverse steps 5 and 9. Use LVM first to span the drives, then use GParted to format them, not the other way around.

Now lets just hope linux lives up to its name and I can come back a year later without ever having rebooted the server to see it still humming along :)

---

