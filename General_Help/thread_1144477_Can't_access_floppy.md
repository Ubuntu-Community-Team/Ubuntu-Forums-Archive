---
title: "Can't access floppy"
date: 2009-04-30
forum: General Help
---

### Post by RHL on 2009-04-30
Hello, everyone. I'm new to Ubuntu. I've been given a Hewlett-Packard Pavilion 9600 desktop system with Ubuntu 8.10 installed (Kernel Linux 2.6.27-9-generic) and would like to be able to use the floppy drive. When I go to 'Computer' on the Places menu, the resulting window displays icons for both optical drives and the hard drive, but there's nothing representing the floppy. The system will boot from a Windows emergency boot floppy disk just fine, so I'm satisfied the drive is connected and functioning properly. Can anyone tell me what I need to do to get access to the floppy drive with Ubuntu? Any help would be appreciated. Thanks!
 
RHL

---

### Post by _Purple_ on 2009-04-30
Type this command in terminal and see if you can access your floppy drive
```
sudo modprobe floppy
``` 

or open the file /etc/modules
```
gksudo gedit /etc/modules
```

Then add floppy at the end of the file, save and reboot.

---

### Post by RHL on 2009-05-02
Thank you, _Purple_! This is definitely a step in the right direction. I can now "see" the floppy drive in GNOME & Nautilus, but I can't format media.
 
If I insert a readable disk and double-click the Floppy Drive icon in Places/Computer, the error "Unable to mount location - Can't mount file" is displayed, even though the disk volume mounts.
 
Double-clicking on /usr/bin/gfloppy results in the error "Cannot initialize device - You do not have the proper permissions to write to /dev/floppy/0 or /dev/fd0, formatting will not be possible."

---

### Post by Yellow Pasque on 2009-05-02
Add your user to the floppy group:
```
sudo useradd -G floppy *username*
```

---

### Post by RHL on 2009-05-02
Tried
 
sudo useradd -G floppy owner
 
("owner" is my user login), but still get the same response when trying to run gfloppy. But, the Users Administration Tool did the trick. Not sure I understand the difference between useradd and users-admin, but making a floppy group (no, I didn't already have one) and setting my user account to be a member thereof was very simple using the latter. Thanks, Temüjin, for giving me the right idea!

---

