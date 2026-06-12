---
title: "Can I resize a VMware hard drive partition after installation of XP?"
date: 2007-05-26
forum: Desktop Environments
---

### Post by diablo75 on 2007-05-26
I have XP installed in VMware, and I'd like to increase the size of the virtual partition XP is installed on.  Is there a way to do this?

Thanks.

---

### Post by yabbadabbadont on 2007-05-26
Not that I've ever found or heard of.  However, you can easily create another blank "drive" and attatch it to your existing VM then format it inside of XP.  It is just like adding another hard drive to your XP machine.  (It will probably require you to activate XP again though...  which is why I no longer use XP.  ;))

---

### Post by diablo75 on 2007-05-30
Something didn't seem to go right...

I opened up the virtual machines settings, and clicked "Add" to add a new hard drive.  I told it that I wanted it to be 10 gigs in size (the system hard drive that I started with was 6 gigs).  After it completed creating the drive, it didn't show up in Windows for me to format in Administrative Preferences>Computer Management>Drive Manager.  Also, in the Virutal Machine settings itself, the drive fails to appear in the list of devices that are available to XP.

But if I use the utility in Linux under Accessories>Drive Usage Analyser, the .vmware folder is taking up just a hair over 16 gigs of space.  What gives??

---

### Post by yabbadabbadont on 2007-05-30
Please post the contents of the vmx file for your VM and the output of "ls -lR ~/.vmware" when run in a terminal.

---

### Post by diablo75 on 2007-05-30
How do I find the contents of this VMX file?

I entered the command you asked to have entered in terminal and the output looks like this:

:~$ls -IR ~/.vmware
favorites.vmls  preferences
:~$

---

### Post by g8m on 2007-05-31
I did change once the size of a virtual disk,from 4 to 8gigs.
     vmwware-vdiskmanager -x 8GB ***disk***.vmdk

In the virtual machine I could add another partition to that disk.

I dont know if it's possible to change the size of a partition.

---

### Post by cwmoser on 2007-07-10
I tried to change the hard drive size from 8GB to 16GB for a virtual machine in VMserver.

I ran the command:

$ vmware-vdiskmanager  -x16Gb  “Windows 2000 Professional.vmdk”

Then booted the virtual machine using the Live Gparted CD.  The hard drive was increased to 16GB and shows as 16GB when I right click on My Computer -> Manage -> Disk Management.  But, when I right click on the C: icon in My Computer, it shows as an 8GB hard drive.   Also, at the DOS prompt, when I do a DIR it shows as 8GB.  I tried rebooting, chkdsk, etc but still there is this discrepency.

Any ideas?

Thanks

Carl

---

### Post by diablo75 on 2007-07-10
Nevermind.  you tried that already.

---

### Post by cwmoser on 2007-07-10
Look at this at[FONT="Courier New"] /var/lib/vmware/Virtual Machines/Windows 2000 Professional:

-rw------- 1 carl carl 2147221504 2007-07-10 21:12 Windows 2000 Professional-f001.vmdk
-rw------- 1 carl carl 2147221504 2007-07-10 21:12 Windows 2000 Professional-f002.vmdk
-rw------- 1 carl carl 2147221504 2007-07-10 21:12 Windows 2000 Professional-f003.vmdk
-rw------- 1 carl carl 2147221504 2007-07-10 21:11 Windows 2000 Professional-f004.vmdk
-rw------- 1 carl carl    1048576 2007-06-12 07:13 Windows 2000 Professional-f005.vmdk
-rw------- 1 carl carl 2147221504 2007-07-10 16:02 Windows 2000 Professional-f006.vmdk
-rw------- 1 carl carl 2147221504 2007-07-10 16:03 Windows 2000 Professional-f007.vmdk
-rw------- 1 carl carl 2147221504 2007-07-10 16:04 Windows 2000 Professional-f008.vmdk
-rw------- 1 carl carl 2147221504 2007-07-10 18:35 Windows 2000 Professional-f009.vmdk
-rw------- 1 carl carl    1048576 2007-07-10 16:05 Windows 2000 Professional-f010.vmdk
-rw------- 1 carl carl        870 2007-07-10 21:06 Windows 2000 Professional.vmdk
-rw------- 1 carl carl          0 2007-06-12 07:09 Windows 2000 Professional.vmsd
-rwxr-xr-x 1 carl carl       1043 2007-07-10 21:06 Windows 2000 Professional.vmx
[/FONT]

The files now show that space went from 8GB to 16GB -- note the addition of *f006.vmdk through *f009.vmdk.


I think this is close but there must be another step to complete the process.

Carl

---

### Post by ojlnx on 2008-06-29
Did you manage to sort this out? yes, I got exactly same problem :-/ Thanks

---

