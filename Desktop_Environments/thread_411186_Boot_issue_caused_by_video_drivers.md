---
title: "Boot issue caused by video drivers?"
date: 2007-04-16
forum: Desktop Environments
---

### Post by Makaze on 2007-04-16
I had an issue where my Ubuntu stopped booting. The error that was causing this was:
```
Failed to start the X server (your graphical interface). It is likely that it is not set up correctly.


(==) Log file: "/var/log/Xorg.0.log", Time: Fri Apr 13 13:50:07 2007
(==) Using config file: "/etc/X11/xorg.conf"
Parse error on line 76 of section InputDevice in file
/etc/X11/xorg.conf
"" is not a valid keyword in this section.
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found
```

I was able to fix this issue by running ```
dpkg-reconfigure xserver-xorg
``` and following through the prompts.

Now my only concern is that A) I have an ATI Mobility Radeon X1300 video card that I need to make sure the drivers are installed for and B) Grub is showing two entries for Ubuntu and I only have one installed. One entry actually boots, the other doesn't. This started happening directly after I installed my ATI drivers last time. So if any of you have any pointers there it'd be greatly appreciated. Proper video drivers are important to me as I'm a gamer ....



And just incase it's needed I have a Acer Travel-Mate 6460-6752 laptop

---

### Post by lotacus on 2007-04-16
I am not exactly sure what your problem is. I didn't see any direct question.

For your boot entries, you can edit /boot/grub/menu.lst and remove the non-working entry. You may want to make a backup first. Be sure to edit under sudo.

sudo cp /boot/grub/menu.lst /boot/grub/menu.bak
sudo gedit /boot/grub/menu.lst

There are many guides detailing how to install ATI drivers. I personally use this wiki [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Install_the_8.35.5_Driver_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Install_the_8.35.5_Driver_Manually")

---

### Post by leogibson on 2007-04-17
i'm having this same problem with the latest RC release.  i had this problem when edgy first came out...i think possibly dapper too.  after a week of waiting for the new releases to be more stable, this went away, but this is still very annoying.

---

### Post by Makaze on 2007-04-17
> **lotacus said:**
> I am not exactly sure what your problem is. I didn't see any direct question.

For your boot entries, you can edit /boot/grub/menu.lst and remove the non-working entry. You may want to make a backup first. Be sure to edit under sudo.

sudo cp /boot/grub/menu.lst /boot/grub/menu.bak
sudo gedit /boot/grub/menu.lst

There are many guides detailing how to install ATI drivers. I personally use this wiki [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Install_the_8.35.5_Driver_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Install_the_8.35.5_Driver_Manually")

I am actually unable to follow the manual ati driver install directions as I cannot make a .deb from the .run file downloaded in the link for some reason. 
```
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/edgy
./packages/Ubuntu/ati-packager.sh: 178: dpkg-architecture: not found
Error: unsupported architecture: 
Removing temporary directory: fglrx-install.fY5816
```

And thank you for the instructions on the grub issue. I followed your advice and was able to successful remove the extra entry.

Any idea on how to get my 5-button Labtec mouse to work? Trying to install the mouse is actually what started the whole not booting issue in the first place.

---

### Post by lotacus on 2007-04-18
I am not sure if the wiki is updated with the new drivers. I believe the person had linked it to an old set. If you go to ATI's website you can download the newer drivers which support fiesty and AMD64. When you are following the instructions on the wiki, don't forget to replace any reference to the old drivers with the newer one you downloaded.

As for the mouse button's, I have no idea.

---

