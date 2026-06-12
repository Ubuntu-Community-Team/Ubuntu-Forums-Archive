---
title: "Software Updater Update button Not Working"
date: 2023-05-16
forum: Desktop Environments
---

### Post by ShowMeGrrl on 2023-05-16
I have a System76 Wild Dog running Ubuntu 18.04. I would like to update the OS to Ubuntu 20.04. Consistent with most instructions I've read about how to do this upgrade, I open the Software Updater app, which tells me if any of my apps or system need updates. I've installed all of the available updates for my system. The Software Updater informs me that all my software is up to date BUT that I am running 18.04 and 20.04.6 is available. It offers 2 buttons: "Update" and "OK."  When I click on the "Update" button, nothing happens. 

Is there some reason this app won't let me update my OS? I thought maybe I didn't have enough space on my computer, but I supposedly have 167 GB available, which should be plenty.  I also have lots of memory on my computer (64GB).

---

### Post by ActionParsnip on 2023-05-17
Can you do it in the terminal OK? Be sure to disable all PPAs (If you have any enabled)

---

### Post by grahammechanical on 2023-05-17
Two things come into my mind. Have you set Software & Updates>Updates tab to notify of a new Ubuntu version that is a long term support version?

Like me you are using a machine that came pre-installed with Ubuntu. In your case the supplier is System76. The supplier may have installed specialized hardware drivers for the keyboard from the supplier's own repositories. Check Software & Updates>Other Software tab to see if a System76 repository is installed. If System76 does not provide a 20.04 repository then the upgrade will disable some special features of the hardware. So, make a note of the repository address. You will need to add that repository address after the upgrade in order to get those missing features back.

After the upgrade you can install Synaptic Package Manager and search for the suppliers name. Synaptic will find any packages available from the supplier and install them. Functionality will be restored.

I have a machine with Ubuntu 20.04 installed. I tested what would happen if I upgraded to 22.04 by putting in a new install of 22.04. I lost some keyboard functionality. By putting in the 20.04 supplier repository address and using Synaptic to find the supplier drivers I restored keyboard functionality.

Regards

---

### Post by ShowMeGrrl on 2023-05-18
Thank you, grahammechanical and ActionParsnip. I did move to the terminal and tried the "sudo do-release-upgrade" command but frustratingly got the "Please install all available updates for your release before upgrading" message, even though the statement repeatedly provided on the Software Updater GUI was that "The software on this computer is up to date."  




I then contacted System76, the maker of my 2016 Wild Dog desktop computer. After going through several steps, I was successful in updating to 20.04. System76 provided excellent support. And grahammechanical, you are on the right track with your guesses.


The System76 support person had me type in these commands:


> 
sudo apt clean
sudo apt update -m
sudo dpkg --configure -a
sudo apt install -f
sudo apt full-upgrade
sudo apt autoremove --purge
sudo do-release-upgrade



This continued to produce the "Please install all available updates...." message but did provide the hint that an nvidia driver might be the problem. It turned out the problem is that my nvidia GPU is so old that it needs an older driver than is now included in System76's nvidia package. 


Here are the commands (in order) that I used:


The following commands still produced the "Please install all available updates..." and did not show which updates to apply:


> 
sudo apt dist-upgrade
sudo do-release-upgrade


The following commands indicated that the problem is that my old system needs the 470 driver not the 525 driver that is included in System76's nvidia package:


> 
sudo apt purge ~nnvidia
sudo apt clean
sudo apt update
sudo apt install system76-driver-nvidia


The following commands were to install the 470 driver:


> 
sudo apt purge nvidia*
sudo apt clean
sudo apt update
sudo apt install nvidia-driver-470



The above commands successfully installed the 470 driver and that indeed was the missing driver. I was then able to update to Ubuntu 20.04 without any hickups. I used the Software Updater GUI to do it, since the System76 person had apparently left for the day and was no longer around to hold my hand. 


I realize this problem was rather particular to my own case and because I have such an old computer. But perhaps it will help somebody.

---

