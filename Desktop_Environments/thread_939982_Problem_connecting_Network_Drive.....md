---
title: "Problem connecting Network Drive...."
date: 2008-10-06
forum: Desktop Environments
---

### Post by mikey5555 on 2008-10-06
Hello all,
I have a need to connect a "Network Storage" appliance (Linksys Network Storage System) which is connected to my network via Ethernet. This device has a "permanent" IP.  It was originally setup under Win XP, so it is formatted as NTFS.  
How can I map this drive to my UBUNTU system, make it a permanent connection, and have full Read and Write access?  It's local IP is 192.168.1.254.  I can see the drive when I go to **Places>Network>Windows Network>Workgroup>NET_STORAGE**.
However, when this method of opening the drive and accessing the files is used and I double-click a file (a .doc file), it appears it is about to open in Open Office Work Processor but nothing ever appears in Open Office. 
Here is a partial directory of the drive, copied from the "File Browser" window in Ubuntu - I had to add the owner/permissions info by hand, and the date and size are not included in the list below - this is because the only way I can view the drive is with the GUI file browser, and only the path/filename info is included when the drive contents are "highlighted" and copied/pasted into this text document:
> 
smb://net_storage/PUBLIC%20DISK/ADBS3					bill	Bill Teaff	-rw-r--r--
smb://net_storage/PUBLIC%20DISK/Aircraft%20Maintenance			bill	Bill Teaff	-rw-r--r--
smb://net_storage/PUBLIC%20DISK/Avantext				bill	Bill Teaff	-rw-r--r--
smb://net_storage/PUBLIC%20DISK/EC%20Matters				bill	Bill Teaff	-rw-r--r--
smb://net_storage/PUBLIC%20DISK/Excel%202008%20-%20Images		bill	Bill Teaff	-rw-r--r--
smb://net_storage/PUBLIC%20DISK/INET					bill	Bill Teaff	-rw-r--r--
smb://net_storage/PUBLIC%20DISK/Insurance				bill	Bill Teaff	-rw-r--r--
smb://net_storage/PUBLIC%20DISK/Mike-Hold				bill	Bill Teaff	-rw-r--r--
smb://net_storage/PUBLIC%20DISK/Old%20Backup%20files			bill	Bill Teaff	-rw-r--r--
smb://net_storage/PUBLIC%20DISK/old%20Excel%202007%20-%20Images		bill	Bill Teaff	-rw-r--r--
smb://net_storage/PUBLIC%20DISK/Outlook-exports				bill	Bill Teaff	-rw-r--r--
smb://net_storage/PUBLIC%20DISK/QBs					bill	Bill Teaff	-rw-r--r--
smb://net_storage/PUBLIC%20DISK/Stuff					bill	Bill Teaff	-rw-r--r--
smb://net_storage/PUBLIC%20DISK/VMWARE-Backup				bill	Bill Teaff	-rw-r--r--
smb://net_storage/PUBLIC%20DISK/QBInstanceFinder.log			bill	Bill Teaff	-rw-r--r--
smb://net_storage/PUBLIC%20DISK/QBWIN.LOG				bill	Bill Teaff	-rw-r--r--
smb://net_storage/PUBLIC%20DISK/QBTAXPRT.ini				bill	Bill Teaff	-rw-r--r--
smb://net_storage/PUBLIC%20DISK/qbw.ini					bill	Bill Teaff	-rw-r--r--
smb://net_storage/PUBLIC%20DISK/CompassBank.QBW				bill	Bill Teaff	-rw-r--r--
smb://net_storage/PUBLIC%20DISK/Excel%202008.QBW			bill	Bill Teaff	-rw-r--r--
smb://net_storage/PUBLIC%20DISK/Excel%20Aug%2030%202008.QBB		bill	Bill Teaff	-rw-r--r--
smb://net_storage/PUBLIC%20DISK/QBUpdateUtility.bat			bill	Bill Teaff	-rw-r--r--

As can be seen, the drive was formatted with NTFS and has some File/Directory names that include spaces.

I need the drive to be available at all times to this machine, and to be "connected" when Ubuntu boots.
AS it stands at this moment, the drive "mounted" by opening the **PLACES>NETWORK>WINDOWS NETWORK>WORKGROUP>NET_STORAGE>** "PATH" in a GUI file browser, then selecting **PUBLIC_DISK** and right-clicking on it and selecting "Connect to this Server".  This places an Icon on the desktop called **PUBLIC DISK** from which I can open the drive, the directories, and finally select the file I need or want.  The file will not "open" from this drive/directory combo, and must be "dragged-and-dropped" onto the desktop or some folder of the Ubuntu machine before I can actually open the file.  Most inconvenient....
Anyone have any advice or pointers on how to get this working...??

Regards...

mikey5555

---

### Post by maybeway36 on 2008-10-06
Try this line for your /etc/fstab: (edit with "gksu gedit /etc/fstab")
```
//192.168.1.254/PUBLIC\040DISK /media/shared cifs defaults,uid=1000,gid=1000,users 0 0
```
Then make sure to add the mountpoint folder:
```
sudo mkdir /media/shared
```
Run "sudo mount /media/shared" or reboot and it should work.

---

### Post by mikey5555 on 2008-10-06
> **maybeway36 said:**
> Try this line for your /etc/fstab: (edit with "gksu gedit /etc/fstab")
```
//192.168.1.254/PUBLIC\040DISK /media/shared cifs defaults,uid=1000,gid=1000,users 0 0
```
Then make sure to add the mountpoint folder:
```
sudo mkdir /media/shared
```
Run "sudo mount /media/shared" or reboot and it should work.

Thanks, that mostly worked
> 
Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.

mount: wrong fs type, bad option, bad superblock on //192.168.1.254/public disk,

       missing codepage or helper program, or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so

.



A check of the "syslog" found these error message lines:
> 
Oct  6 14:37:22 bill-uue kernel: [  162.117222]  CIFS VFS: No username specified
Oct  6 14:37:22 bill-uue kernel: [  162.117230]  CIFS VFS: cifs_mount failed w/return code = -22


How does one get past this problem...??

Regards...
mikey5555

---

