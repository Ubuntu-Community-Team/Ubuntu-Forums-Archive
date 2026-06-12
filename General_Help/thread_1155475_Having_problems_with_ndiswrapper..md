---
title: "Having problems with ndiswrapper."
date: 2009-05-10
forum: General Help
---

### Post by Bonzzai on 2009-05-10
I've only worked with Ubuntu a bit, but I just installed Ubuntu 8.10 on my other laptop. (Compaq Presario M2000 w/ about a gig 1/2 of RAM.) I'm trying to get the wireless driver to work, but I can't figure out how to install ndiswrapper. I've tried downloading it here, putting it on the other laptop, and installing it, but the wireless still doesn't work.

I downloaded 'ndiswrapper-1.54.tar.gz', tried following the installation instructions, and I'm STILL lost.

How can I install ndiswrapper to get my wireless working?

---

### Post by Yellow Pasque on 2009-05-10
The ndiswrapper packages are actually on the Ubuntu CD.

---

### Post by Bonzzai on 2009-05-10
> **Temüjin said:**
> The ndiswrapper packages are actually on the Ubuntu CD.

So I can just type "sudo app-get install ndiswrapper" or something along those lines to get the wireless card to work?

---

### Post by Yellow Pasque on 2009-05-10
Put the CD in. Open Nautilus, navigate to the CD, The ndiswrapper .debs are located in pool/main/n/
Copy+paste them to your desktop. Install the .debs by double-clicking on them (IIRC, you have to do the 'common' one before 'utils'). Then you'll need a Windows XP driver for your wireless chipset to 'wrap'.

---

### Post by rudy.b on 2009-05-11
Here are the steps I used to install the ndiswrapper GUI and wireless driver on my system:

[LIST]Insert the Ubuntu CD[/list]
[list]Allow packages to be installable from CD
  System > Administration > Software Sources > Third-Party Software
  Ensure the Cdrom option is checked and click "Close"[/list]
[list]Install the ndiswrapper GUI Application (ndisgtk)
  System > Administration > Synaptic Package Manager
  Search for the package "ndisgtk", mark for installation, and apply[/list]
[list]Install the driver
  System > Administration > Windows Wireless Drivers > Install New Driver
  For this step you'll need the Windows XP version of the driver for your card.  Browse to the .inf file and click "Install"[/LIST]
  
You should see the wireless networking icon in your notification area; click that to select your network and configure your settings.

---

