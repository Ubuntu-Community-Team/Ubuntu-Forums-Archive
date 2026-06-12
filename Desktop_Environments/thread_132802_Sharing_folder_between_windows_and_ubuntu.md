---
title: "Sharing folder between windows and ubuntu"
date: 2006-02-19
forum: Desktop Environments
---

### Post by godrox on 2006-02-19
I have three systems: 1 windows xp, 2 ubuntus. Ubuntu computer #1 is setup as a file server using the simple samba directions found here: [http://find.pcworld.com/51118]("http://find.pcworld.com/51118"). However, instead of placing the shared folder in Unbuntu's home folder, I placed it on a second empty harddrive (slave) hd2. The connection to this folder from the windows xp system works perfectly, but I cannot get the other Ubuntu system to browse to this same folder. No matter what I try, all I can see is "files" and "homes," both of which turn up empty. I've tried various users/password, changing user's home directory, various connection methods, and still blah... Any help please? :-k 

P.S. I'm still very much new to the whole linux system. I plan to eventually have all three systems setup with Ubuntu, but am still in the learning process. I'd appreciate it if any generous replies are kept on a noobish level for me. :-#

---

### Post by msnthrp on 2006-02-19
Have you tried using the Systems Settings menu?  I was having trouble getting a USBDrive to be seen.  

Click on K-start, down and click on System Settings, down to System Administration and click on Disks & Filesystems.  Enter the Adminstrator box and log in.  The drives being seen by the machine will show up.  Now mount them and then be sure to enable them - I have forgotten exactly how that works but it is easy to figure out.

You may have to reboot the machine for the settings to take effect.

Good Luck.

---

### Post by godrox on 2006-02-19
I'm not having any trouble with the drive itself. The shared folder works perfectly from my windows XP system, but for some reason I can't get my other Ubuntu system to connect to the same folder. I'm not sure what a disk management solution provides for this.

---

### Post by Milamber_Cubed on 2006-02-19
I had a bit of an issue with one ubuntu box finding the other in the "network servers" bit of the Places menu. All I had to do was press control-L in an nautilus window and type smb://hostname and then enter the username/password pair that i created with the smbpasswd command. If you created a user especially for samba access (as the guide appears to tell you to) it might be worth making sure that the linux password for that user is the same as the smb password and that the unix user has at least read access to the shared directories.

---

