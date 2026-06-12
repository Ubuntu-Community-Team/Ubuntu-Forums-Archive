---
title: "VM Freeware that allows for USB access"
date: 2009-10-28
forum: Desktop Environments
---

### Post by RSASKA on 2009-10-28
Hello,

I use Virtual Box OSE as a virtual machine to access Win XP, however it does not enable access to USB drive. Based on the posts on this forum, VIrtual Box does in fact enable access to USB drive - but it is not freeware.

Please tell me where I can search for freeware VMs that run on Ubuntu 9.04 tand also enable access to USB.

---

### Post by andrea000 on 2009-10-28
> **RSASKA said:**
> Hello,

I use Virtual Box OSE as a virtual machine to access Win XP, however it does not enable access to USB drive. Based on the posts on this forum, VIrtual Box does in fact enable access to USB drive - but it is not freeware.

Please tell me where I can search for freeware VMs that run on Ubuntu 9.04 tand also enable access to USB.
Virtualbox does have usb support and it's free but it's
not open source you can download a deb from [here]("http://www.virtualbox.org/wiki/Linux_Downloads") or add
the ppa to your software source from the same page

---

### Post by RSASKA on 2009-11-26
> **andrea000 said:**
> Virtualbox does have usb support and it's free but it's
not open source you can download a deb from [here]("http://www.virtualbox.org/wiki/Linux_Downloads") or add
the ppa to your software source from the same page


I'm all thumbs when it comes to computers:

what do you mean by "download a deb" and
"add the ppa to your software source from the same page"

---

### Post by Ginsu543 on 2009-11-27
"Download a deb" means to download the *.deb package file. Once you download it to your hard drive, you can install the package by double-clicking it, which will bring up the Archive Manager. Just click on "Install Package" button and it will install the .deb package for you.

"Add the ppa..." means to add the ppa in Software Sources to add the package you want to install to the list of repositories Synaptic can access. Go to System --> Administration --> Software Sources, then click on "Other Software" tab. Click on the "Add..." button and copy the ppa line into the "APT line:" space. Click "Add source" then close. Once done, open Terminal and follow the directions on the VirtualBox website to add the public key for Sun (this basically lets Ubuntu know that this ppa is a "trusted" site). Then you can install the program by opening Synaptic and looking for "virtualbox-3.0." Mark the file for installation and hit "Apply."

Having said all that, just downloading the .deb file and double-clicking it is the easiest way to install IMO. Just make sure you download the right file (32-bit or 64-bit) for the type of system you have. I myself have just installed the closed-source VirtualBox on my rig just this evening and am happily running Windows XP in a VM right now as I type this (in fact, I'm on this site while I wait for all the updates to finish downloading). As Andrea mentioned above, the closed-source version does support usb.

---

### Post by RSASKA on 2009-11-28
Hi,

Thanks for the info!

I went to the website and download virtualbox-3.0_3.0.12-54655_Ubuntu_jaunty_i386.deb. However, I was prompted to uninstall Virtual Box OSE before installing virtualbox 3.0. 

Just a note to those in my similar situation:

Virtual Box OSE was installed under Applications -> Accesories

Virtual Box has been installed under Applications -> System Tools

---

### Post by impact on 2009-11-28
Don't forget to add yourself to the vboxusers group once the package is installed (in a terminal, type: "sudo usermod -G vboxusers -a username" replace username with your username on your system; when it's done, log out and log back in to your system for it to work... see [http://www.virtualbox.org/manual/UserManual.html](http://www.virtualbox.org/manual/UserManual.html) section Installing on Linux hosts).

---

### Post by RSASKA on 2009-11-28
I installed the Virtual Machine, but have been unable to get the USB port to work. Attached is the screenshot that shows the settings. Please advise

---

### Post by Ginsu543 on 2009-11-28
I believe the installation process takes you through how to add yourself to the vboxusers group (I didn't have to do anything extra in Terminal to get VirtualBox working).

---

### Post by RSASKA on 2009-11-28
I can access VirtualBox to use Windows XP just fine - however I am unable to access my USB drive using VirtualBox.


Also, I performed the following command in terminal:

 "sudo usermod -G vboxusers -a username" 

where "username" is my username

---

### Post by mikeac72 on 2009-11-28
Create a USB filter in settings?

---

### Post by RSASKA on 2009-11-28
I created three USB filters but still no luck, please see attachment of the screenshot I took and advise.

---

### Post by impact on 2009-12-25
Late reply, I know, but perhaps you just need to right-click the little USB icon at the bottom of the Virtualbox window (it looks like a USB connector and is right next to the network icon) and then tick the appropriate USB device. I know my installation won't see any devices until I select them like that.

---

### Post by chinna saaeb on 2011-02-01
Virtual box OSE does not support USB access.
You need to use personal use and evaluation version to get that.
It works well

---

### Post by garyjmellor on 2011-02-08
Please see my post here:
 
[http://ubuntuforums.org/showthread.php?p=10439282#post10439282](http://ubuntuforums.org/showthread.php?p=10439282#post10439282)
 
VirtualBox OSE (4.0.2 r69518 ) and USB working fine and dandy.

---

### Post by gradinaruvasile on 2011-02-08
I have VBox working since the 2 series. Absolutely no problems in using USB devices.
Since 4 series there is no OSE, the regular VBox replaced it (no ootb USB support), you have to download the addon and install it.

There is no need for pre defined filters to use USB devices casually .
Launch the VM (obviously you have to have USB support enabled - it is by default), right-click on the lower right side usb icon, select your device and click on it (avoid your mouse/keyboard from the list!).

---

