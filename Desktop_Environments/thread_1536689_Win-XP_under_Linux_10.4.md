---
title: "Win-XP under Linux 10.4"
date: 2010-07-22
forum: Desktop Environments
---

### Post by Desert Sailor on 2010-07-22
I am still a newb when it comes to Linux, but am running 10.4 and earlier versions for about 2 years.  I love Linux more and more.  However, there are some backward companies who refuse to provide Linux software, Intuit, (I have used WINE to run Quicken), but can't seem to get the Garmin map downloader to work in anything but windoes. For these cretin companies, I have had a dual boot machine with Windows XP on a separate partition. 

I have recently installed VirtualBox on my Linux and I see that I can install Win-XP as a virtual system.  

My question: I would like to eliminate the Windows partition totally, and just use Virtual Box for my windows applications. Is this a true Windows install, will it run ANY windows software?  Can I totally eliminate a separate Windows partition and not have problems? 

Thanks....

---

### Post by ajgreeny on 2010-07-22
> I would like to eliminate the Windows partition totally, and just use  Virtual Box for my windows applications.
Is this a true Windows install,  will it run ANY windows software?
The answer to that is just about a firm "Yes", though there are some games that play on windows and will not play properly in VB bacause windows will be using the graphics ability of ubuntu and not that of windows, so highly demanding games may not work totally.  For almost everything else it is fine.
> Can I totally eliminate a separate  Windows partition and not have problems? 
I think so, yes.

---

### Post by dabl on 2010-07-22
I use VMware, rather than VBox, but they both provide a full virtual environment, so "YES", it is really Windows running in the VM.

HOWEVER, note that when running in the VM, the Windows OS does not have direct access to the real hardware (since Linux has that).  You'll have a faux SVGA graphics, however much memory you allocate, and a virtual hard drive.  Stuff like Quicken and Garmin should be fine. Don't count on extreme graphics such as you would expect for advanced gaming, and it should be fine.

---

### Post by Desert Sailor on 2010-07-22
If I wanted to evaluate VMWare vs. VirtualBox, what is the name of the VMWare program from either the Ubuntu Software screen, or Apt get?

---

### Post by dabl on 2010-07-22
You need to go to the VMware site, to "products", and download the VMware Player VMware-3.1.0.xxx*.bundle file, 32-bit or 64-bit as applicable.  You'll have to register, but it is free (as in beer, not speech).

Once you have the *.bundle file, Ctrl-Alt-F1 out of X, shutdown the X server with ```
sudo service gdm stop
``` and change directory to /tmp.

Then ```
sudo cp /home/desert_sailor/Downloads/VMware(tab-to-complete) .
```

to copy it to /tmp.  Then

```
sudo sh VM(tab-to-complete)
``` and it will be installed.  Restart X with ```
sudo service gdm start
``` and you will find VMware Player in your System menu.  Follow the menu to make a hard disk drive of suitable size, up to 40G, and then use your Windows installation CD to install Windows on it.  When asked, you _do_ want the VMware Tools package.

---

