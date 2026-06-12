---
title: "Dual Boot Ubuntu 11.10 and Windows 7: choose OS prompt at startup time = 0"
date: 2012-03-16
forum: Desktop Environments
---

### Post by gatech on 2012-03-16
Hey everyone,

Okay I'm pretty much a noob at Ubuntu right now. I setup a dual boot system with Windows 7 and Ubuntu 11.10. I need Windows 7 because it makes things easier as a student to use the Windows 7 OS. Somehow the boot prompt screen that allows you to choose which OS to run at bootup has been changed so that the display time is 0 and it doesn't show up. I have done a good deal of research and it all points to the BOOT.INI file in Windows C: but I have searched the entire computer and checked hidden files and cannot find it to edit it. Can someone please help me to get the OS boot screen prompt back? 
Thanks in advance

---

### Post by wojox on 2012-03-16
Try rebooting and holding the left <Shift> key down.

---

### Post by youngunix on 2012-03-16
> **gatech said:**
> Hey everyone,

Okay I'm pretty much a noob at Ubuntu right now. I setup a dual boot system with Windows 7 and Ubuntu 11.10. I need Windows 7 because it makes things easier as a student to use the Windows 7 OS. Somehow the boot prompt screen that allows you to choose which OS to run at bootup has been changed so that the display time is 0 and it doesn't show up. I have done a good deal of research and it all points to the BOOT.INI file in Windows C: but I have searched the entire computer and checked hidden files and cannot find it to edit it. Can someone please help me to get the OS boot screen prompt back? 
Thanks in advance


Here is how you change boot time from Windows 7:

Open **Control Panel** -> **System and Security** -> **System**, 
**to the left**, click on **Advanced System Settings** -> **Advanced tab**
Down to the 3rd box (**Startup and Recovery**), click on **Settings** -> the rest is pretty much clear.

Good Luck

---

### Post by gatech on 2012-03-16
Okay I wasn't sure where to post this because I can't get into my Windows 7 OS. It automatically boots me into Ubuntu. So I can't access control panel.

---

### Post by youngunix on 2012-03-16
> **gatech said:**
> Okay I wasn't sure where to post this because I can't get into my Windows 7 OS. It automatically boots me into Ubuntu. So I can't access control panel.

I see! Like "wojox" said at boot, quickly hold the "shift" button. OR

You can try: 
First, it is important that you back up any files you are going to alter:
```
sudo cp /etc/default/grub /etc/default/grub.bak
```

Now, you can change the settings in the "grub" file:
```
sudo gedit /etc/default/grub
```
and change ```
*GRUB_DEFAULT=0*
``` to ```
*GRUB_DEFAULT=saved*
```
then ```
GRUB_TIMEOUT="0"
``` to ```
GRUB_TIMEOUT="**"
```
Finally ```
sudo update-grub
```

** = any number of seconds you need the boot menu to wait.

---

### Post by gatech on 2012-03-16
Okay I tried this and it was unsuccessful. After coding the sudo update command it gave me an output of skipping windows 7 (loader) on wubi. I do believe that this may have an effect on my problem haha. But I am unsure how to fix it obviously. Anyway I did all that you recommended inside the grub file.

---

