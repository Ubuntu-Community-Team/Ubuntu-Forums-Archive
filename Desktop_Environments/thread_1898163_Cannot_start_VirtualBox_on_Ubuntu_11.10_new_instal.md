---
title: "Cannot start VirtualBox on Ubuntu 11.10 new installation"
date: 2011-12-20
forum: Desktop Environments
---

### Post by MacDuff on 2011-12-20
With clean installation of Ubuntu 11.10 but previously used VirtualBox VDI,  I am not able to run the virtual windows VDI.

Have installed VB from the Ubuntu repositories and no joy
Have installed VB from the Oracle website and no joy
I also did an installation using apt-get and no joy

This is the error message I am now getting:
Failed to open a session for the virtual machine Win-XP
The device helper structure version has changed.
If you have upgraded VirtualBox recently make sure you have terminated all VMs and upgraded an extension packs.  If this error persists try re-installing VirtualBox
(VERR_PDM_DEVHLPR3_VERSION_MISMATCH).

I have deleted and re-installed several times with no success

Anyone know what else I can do?

---

### Post by wildmanne39 on 2011-12-20
Hi, did you import and export this vm or did you clone it or what?
Thanks

---

### Post by MacDuff on 2011-12-20
> **wildmanne39 said:**
> Hi, did you import and export this vm or did you clone it or what?
Thanks

I just copied the .virtualbox directory to a backup file then copied the VDI and Machines back to the new .virtualbox directory.

I have done this several times in the past and everything worked.

---

### Post by wildmanne39 on 2011-12-20
Hi, I am not sure if this will help but look at post 2.
[http://ubuntuforums.org/showthread.php?t=1892356](http://ubuntuforums.org/showthread.php?t=1892356)
Thanks

---

### Post by ubix on 2011-12-20
***MacDuff***, have you installed Extension pack?

I suggest you ask for help [VirtualBox](https://forums.virtualbox.org/index.php) dedicated forum. If you have not missed the Extension pack, the issues you have will be much better understood by the folks there than by us here!

---

### Post by MacDuff on 2011-12-20
> **ubix said:**
> ***MacDuff***, have you installed Extension pack? 

Yes. from Oracle and from the repositories.  Several times.

>  I suggest you ask for help [VirtualBox](https://forums.virtualbox.org/index.php) dedicated forum. If you have not missed the Extension pack, the issues you have will be much better understood by the folks there than by us here!

Thanks I will give that a try.

---

### Post by mozkill on 2011-12-23
I am getting this error after exporting a Windows7 appliance from a Ubuntu 11.10 system and tried to import it into a XBuntu 11.10 system.   Even after installing the extension pack and trying all kinds of things in the VM settings, I am unable to start the imported appliance. 

I'm going to have to re-install my Windows 7 VM.  I am disappointed.  Now I know I can't trust exported appliances.



> 
Failed to open a session for the virtual machine Windows7Pro.
The device helper structure version has changed.
If you have upgraded VirtualBox recently, please make sure you have terminated all VMs and upgraded any extension packs. If this error persists, try re-installing VirtualBox. (VERR_PDM_DEVHLPR3_VERSION_MISMATCH).

Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Console
Interface: 
IConsole {1968b7d3-e3bf-4ceb-99e0-cb7c913317bb}

---

### Post by ubix on 2011-12-23
> **mozkill said:**
> I am getting this error after exporting a Windows7 appliance from a Ubuntu 11.10 system and tried to import it into a XBuntu 11.10 system.   Even after installing the extension pack and trying all kinds of things in the VM settings, I am unable to start the imported appliance. 

I'm going to have to re-install my Windows 7 VM.  I am disappointed.  Now I know I can't trust exported appliances.

I do not know what exactly are you doing, though I have a vague idea, and I think that this should work fine, however I do not know enough to help you out. Before you say that you know something about this I suggest you ask for help people who do know about these things. This is not Ubuntu related issue. Check out [VirtualBox](https://forums.virtualbox.org/index.php) dedicated forum.

---

### Post by MacDuff on 2011-12-23
Mozkill:

I solved my problem when I was trying to migrate a Virtual WinXP System from Kubuntu 11.04 to 11.10.

I was starting out with a clean /home but I had copied the entire .virtualbox directory (that had been copied to a backup drive) onto the clean /home.  In retrospect, I should have installed VirtualBox first, then copied ONLY the .VDI sub-directory to the .VirtualBox directory.
Then using VirtualBox create a new virtual drive and when it asks if you want to create new or use an existing drive, point to the VDI file that you transferred.

That solved the loading error problem but I still could not get Windows (XP in my case) to run.  I got a brief blue screen then the MS Windows black and white apology screen.

I recalled getting that a few years ago and remembered that it was caused by the wrong chipset setting.  In my case it had to be PIIX3 but was defaulting to ICH9.  You can change that by selecting (with VirtualBox running), Settings > System > Motherboard.  Chipset will be in the middle of the window.  

Good Luck

---

### Post by nickymlg on 2012-05-13
Hi, I had same/similar problem creating a new VM after installing updated extension pack 4.1.14. When I tried to start it up, I got the error about device helper structure. Finally, I solved it unchecking the USB 2.0 EHCI controller box under VM configuration.
Hope this may help.

---

