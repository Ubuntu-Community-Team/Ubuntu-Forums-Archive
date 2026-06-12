---
title: "Xubuntu7.04 / PyNeighborhood Networking with Windows"
date: 2007-07-14
forum: Desktop Environments
---

### Post by ugm6hr on 2007-07-14
This is my How-To for getting Samba sharing to work between Xubuntu7.04 and Windows XP.  It is almost 100% GUI - so basically point-and-click in the main.  I hope it helps some people.

Just install pyNeighborhood v0.4 from Synaptic Package Manager (search and mark for installation *pyneighborhood* - everything else is installed when you create File-sharing with Samba (for Shared Folders).

I created a pyNeighborhood launcher as root in the panel with the command: ***gksudo pyNeighborhood***
**This step is important**, or it won't work - pyNeighborhood must be launched as *sudo*, **not from the menu entry automatically created**.  To do this - right-click the top panel and select *Add New Item* - then select *Launcher* and click *Add* - put sensible name and description in the appropriate boxes and pick an icon - then put **gksudo pyNeighborhood** in the command box and tick the *Use startup notification* box.  The launcher will then appear in the top panel, generally to the right of the blank space, but can be moved anywhere in the panel by right-clicking it and selecting *Move*.
In Ubuntu - it is possible to edit the Menu launcher to use *gksudo pyNeighborhood* to launch as an alternative.

Launch pyNeighyborhood by clicking on this **new gksudo launcher** - and then edit the pyNeighborhood Preferences as follows:

General tab:
Tick *Remove mount points after unmount*
Mount folder: */media/network* (of course - this can remain the default /mnt/lan, or could be /home/*user*/network or anything else)

File Managers tab:
delete default
create new: ***thunar*** (for Xubuntu) or ***nautilus*** (for Ubuntu)

I then added a shared folder on my laptop:
Applications->System->Shared folders
Shared folders tab:
Added a folder (I used my /home/user)
General tab:
Tick the *This computer is a WINS server* box

I then edited /etc/samba/smb.conf (as root) (in Terminal: *gksudo thunar* (Xubuntu) or *gksudo nautilus* (Ubuntu) and browse and double-click file), and added just [COLOR="Red"]one line[/COLOR] immediately below the [global] entry, so this part looked like:
```
#======================= Global Settings =======================

[global]
[COLOR="Red"]**security=share**[/COLOR]
## Browsing/Identification ###
```


This should now work just fine.  

My Windows computer can browse my shared folder without a password.  I can access my Windows shared folders from pyNeighborhood (started from panel launcher) on Xubuntu laptop - just by a series of double-clicks on the GROUPS / computer / shared folders entries.

**Not working?** - try the advice below in Post 2

PS: This is an alternative for Xubuntu, but I can't get it to work (with DHCP): [http://ubuntuforums.org/showthread.php?t=304131](http://ubuntuforums.org/showthread.php?t=304131)

---

### Post by ugm6hr on 2007-07-21
Just thought I'd start a trouble-shooting section for this how-to, since I'm now pointing people in its direction:

**1. pyNeighborhhod fails to mount a network drive**
Make sure you are running pyNeighborhood as root (from Terminal)
```
gksudo pyNeighborhood
```
This is why I created a separate panel launcher for root use of pyNeighborhhod.  Of course - you could create a menu entry, or edit the automatically created menu entry (if you know how).

**2. I cannot write to a shared network folder (on a different computer on the network)**
The problem may either be with the network drive computer, or your computer - go through the following steps...
Is the shared folder on a Ubuntu or XP box? 
If XP - there is a tick-box to allow network users to write to the drive. 
If Ubuntu - "Shared Folders" - untick the read-only box in Properties
If the share is already read/write enabled (and you can write to it from other networked computers), then it may be the write permissions for the path that you have mounted it to (on your computer).
Where have you specified the mount point for the network drives in pyNeighborhood? If it's in /home/user, then this will not be the problem. If not - you have 3 options:
1. Just change the mount-point to /home/user/network (or something similar)
2. You can always have to run nautilus as root to write to the network drive (this may be a sensible option if you don't want to risk accidentally deleting / modifying the contents of the network drive) - *gksudo thunar* (or *gksudo nautilus*) from Terminal (or have a panel launcher / menu entry to reflect this command)
3. Change the permissions on the mount-point: *sudo chown -R **user:user** /media/network* in Terminal where ***user*** is your login and *media/network* is your chosen mount-point.

**3. Scan failed**
This probably reflects a firewall restriction - possibly on Ubuntu:  I would suggest installing Firestarter (from Synaptic Package Manager).
You need to create a new rule for incoming traffic. Go to the policy tab, select 'inbound traffic policy' and click the 'add rule' button. select 'samba' as the service name and the relevant ports will be filled in automatically. the easiest way is to leave the option 'anyone' to make sure all computers can access the shared files.
Another possibility from Spam Banjo: if you don't use an open network share:
The scan also fails because the program doesn't save the default network password entered.  This method was designed with *security=share*, so this doesn't strictly apply, but: To fix it I went to EDIT>PREFERENCES>GENERAL and selected 'Always use default username and password' and entered my password for the server. Problem solved.

**Further improvements - need help**
Only problem I have is that it requires root use of pyNeighborhood, which means I have to put a password in every time I want to look at a network drive.  This is not too much of a problem, since I rarely need to do this.  The other problem is that it launches Thunar as root whenever I mount a network drive, which is not ideal.

Let me explain the problems I had trying to resolve the root use of pyNeighborhood:
Whatever I tried, it would not allow me to mount any shares.  I used my home/user directory as the mount point (to ensure I had write access).  I tried the following commands:
```
sudo chmod +s /usr/bin/smbmnt
sudo chmod +s /usr/bin/smbmount
sudo chmod +s /usr/bin/smbumount
```
The fact that it all works just fine as root tells me there is something that I don't have access to as my usual user, but I don't know what it is.

Just wondering if anyone has a better solution (or a fix for pyNeighborhood root use) to mounting network drives in Xubuntu using a GUI.  I like pyNeighborhood because it can delete any mounted drives automatically, which is useful for me because I roam on multiple (home) networks.

---

### Post by Spam Banjo on 2007-07-24
The scan failed regularly for me because the program was not saving the default network password I had entered.

---

### Post by lanruisen on 2007-11-20
Works fantastically on my Xubuntu 7.10 laptop. Thanks.

---

### Post by ugm6hr on 2007-11-21
> **lanruisen said:**
> Works fantastically on my Xubuntu 7.10 laptop. Thanks.

Glad to hear it's still useful.  I moved to Ubuntu7.10 myself.

---

### Post by heavyt on 2008-01-25
Very nice samba/network tool. The how to for mounting needs to be part of the install, thanks!

---

### Post by newbjeff on 2008-04-10
I'll just add that I had the same problem (on gOS 2)  that I could see, but not mount drives unless I started pyNeighborhood with root access.  I thought that giving my user name read/write access to the /mnt/lan folders might do it, but it didn't.  I finally got it working by adding mnt/lan folders under my user directory and setting the mount folder preferences in pyNeighborhood to point to that location.

---

### Post by excogitation on 2008-04-18
Is there a way to use pyNeighborhood to automatically mount shares as they become available? (startup, connection to different lan, ...)

---

