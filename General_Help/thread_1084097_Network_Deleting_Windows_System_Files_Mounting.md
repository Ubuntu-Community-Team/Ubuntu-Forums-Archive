---
title: "Network/ Deleting Windows System Files/ Mounting"
date: 2009-03-01
forum: General Help
---

### Post by Badmonkey005 on 2009-03-01
To avoid clutter in the forum I thought I'd put my three support questions into one. I want to thank you guys in advance for your help, I have come here before and always receive a welcome and helpful response.

However illiterate I am to Linux and Ubuntu, I am computer savvy and know about the terminal and the common sense stuff (keeping you from needing to explain more than necessary) 

_**WPA Protected Wireless Network:**_

I have a netgear PCI antenna on my computer with no problems connecting to a WPA protected wireless router in my home with windows.

**WPA Pre-Shared key. TKIP encryption. SSID NOT broadcasted.**

I have tried connecting with ubuntu (running live) on the wireless network with no luck. I enter the SSID name and select the "WPA/WPA2 Personal" security option and enter the WPA password. It does NOT allow me to specify that it is a TKIP encryption and kicks pack asking for a new WPA password after it trys connecting (thus telling me that it DOES communicate with the router on some level) I don't understand what needs to happen. Does Ubuntu only really support a WEP key? If so that would suck because I would have to change the settings on my skype phone, ps3, computer, printer and T.V.
_________________________________________________________________

**_Deleting Windows System Files_**
I have a hard drive ripped off another computer where it used to serve as the main boot drive for windows vista. I am now using it as a backup drive for system restores but when I try to delete certain folders from Ubuntu it gives me am "operation not supported" error. Sudo delete from the terminal? Haven't tried that yet, I've been using the GUI interface but am not sure what needs to be done to whipe the protected folders.
_________________________________________________________________
**_Mounting an encrypted HD_**

I forked over the extra bucks for Vista Ultimate for the BitLocker encryption (don't hate me for being a windows fan or call me stupid for spending that kind of money, I still greatly appreciate the freedom ubuntu gives me). I want to mount the drive just to test the encryption and see what it looks like if someone were to try and access the drive. I made a directory and tried a sudo mount drive one to that directory (I forget what the first drive was labeled with the sudo fdisk -l command) but it gave me an error saying that the drive was not a true NTFS format. Is this because of the encryption or is something messed up?

Thank you again.

---

### Post by BbUiDgZ on 2009-03-01
> **Badmonkey005 said:**
> 

**_Deleting Windows System Files_**
I have a hard drive ripped off another computer where it used to serve as the main boot drive for windows vista. I am now using it as a backup drive for system restores but when I try to delete certain folders from Ubuntu it gives me am "operation not supported" error. Sudo delete from the terminal? Haven't tried that yet, I've been using the GUI interface but am not sure what needs to be done to whipe the protected folders.


assuming you have the drive mounted. open teminal and browse to the root of your mounted drive.
```
cd /media/your-drive-name
```

to delete all files and folders from that drive type
```
sudo rm -rf *
```
-rf means "recursive force" delete and the * is the wildcard meaning all files and folders. WARNING!! IF YOU DO THIS IN THE ROOT OF YOUR SYSTEM YOU WILL DELETE EVERYTHING.

---

### Post by Badmonkey005 on 2009-03-01
Thank you for your quick reply. It IS the root directory but its on a dummy drive. I do have one folder I want to keep but there aren't many other ones that need to be deleted so I can do those one by one via the terminal.

---

### Post by BbUiDgZ on 2009-03-01
> **Badmonkey005 said:**
> Thank you for your quick reply. It IS the root directory but its on a dummy drive. I do have one folder I want to keep but there aren't many other ones that need to be deleted so I can do those one by one via the terminal.

replace * with folder name

```
sudo rm -rf /path/to/folder/you/want/to/delete 
```

---

### Post by Badmonkey005 on 2009-03-01
one of the common sense things :P

Thank you though :guitar:

---

