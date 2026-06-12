---
title: "Device Manager?"
date: 2008-07-13
forum: Desktop Environments
---

### Post by Ooder on 2008-07-13
I just installed Hardy on a laptop last night.  However, I cannot access the device manager.  All documentation says it should be in System->Administration->Device Manager.  I only see Hardware Testing and Hardware Drivers.  Why can I not see the Device Manger?

---

### Post by Agroth on 2008-07-13
Not sure if this is the same thing but try System -> Preferences -> Hardware Information.

---

### Post by Ooder on 2008-07-13
I also don't see Hadware Information, only Hardware Testing and Hardware Drivers

---

### Post by Tim Sharitt on 2008-07-13
> **Agroth said:**
> Not sure if this is the same thing but try System -> **Preferences** -> Hardware Information.

The window title says Device Manager. Hope that helps.

---

### Post by orrcad on 2008-07-14
I have the same thing. No Hardware Information option showing. I've tried using hardinfo via terminal but it says the package is not installed. Why would I not see something as fundamental as Hardware Information.. 

Ubuntu Hardy latest was used for install.
This is not helping the USB Wifi adaptor that I can't get Ubuntu to recognize...Zydas 1211.(another long story)

this is the second time i've tried Ubuntu. Second time I've run into problems.sigh.

cheers Neil

---

### Post by Ooder on 2008-07-14
> **orrcad said:**
> I have the same thing. No Hardware Information option showing. I've tried using hardinfo via terminal but it says the package is not installed. Why would I not see something as fundamental as Hardware Information.. 

Ubuntu Hardy latest was used for install.
This is not helping the USB Wifi adaptor that I can't get Ubuntu to recognize...Zydas 1211.(another long story)

this is the second time i've tried Ubuntu. Second time I've run into problems.sigh.

cheers Neil

I am actually trying to get a wireless adapter to work also, which is why I need to to see Hardware Information.  I tired to install the gnome-device-manager package but it said it could not be found.

---

### Post by dancer58 on 2008-07-15
I went to [http://wiki.hardinfo.org/HomePage](http://wiki.hardinfo.org/HomePage) and got the latest version.
It has been updated in SVN

I would like to see it as part of Ubuntu package also

Harold

---

### Post by a Tim Holt on 2008-07-29
I've managed to use the synaptics package manager to install the gnome-device-manager in Hardy Heron, but the application completely lacks any 'advanced' option tabs. What gives? FYI, I'm following the instructions for WIFI card ndiswrapper-ing found in beginning Ubuntu Linux 2nd ed., chapter 8. None of the devices have any 'advanced' tab when selected, only a 'summary' tab. The program looks mostly the same as those figured in the book, and has the same title bar contents (i.e. "Device Manager").

---

### Post by linux_tech on 2008-07-29
Did you install the hal-device manager? This is to view hardware information.

---

