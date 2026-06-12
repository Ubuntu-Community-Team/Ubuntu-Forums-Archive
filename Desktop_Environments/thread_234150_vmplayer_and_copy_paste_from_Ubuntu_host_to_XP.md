---
title: "vmplayer and copy paste from Ubuntu host to XP"
date: 2006-08-11
forum: Desktop Environments
---

### Post by roger64 on 2006-08-11
First, I tell you what I did, and then ask you a question. :) 

It is now very easy to install vmplayer with Synaptic (vmplayer is now a supported Gnome application and can be installed thru a multiverse repository). The huge advantage is that, installing this way, vmplayer stays fitted even after your Ubuntu kernel updates, so first I did 
#sudo apt-get install vmware-player

After installing vmplayer with Synaptic, getting a vmx file suiting my needs was easy thru easyvmx. OK.
[http://www.easyvmx.com](http://www.easyvmx.com) 
Then I added, within XP, a CD with some tools.
[http://www.vmware.com/download/esx/esx2-16515update.html](http://www.vmware.com/download/esx/esx2-16515update.html) 

I now have a fully nicely working XP within Ubuntu, with CD-ROM, Ethernet and Internet, sound, USB1 -vmplayer does not yet support USB2-. The best of both worlds? 

MY QUESTION ;) 

One thing is missing and that's why I post today:according to vmware site, vmplayer is reported to allow copy and paste between the host OS -for me Ubuntu- to the guest OS -for me XP- and back. 

This does not work for me yet. I suspect, but I am not sure, I missed the installation of a vmware-toolbox in Ubuntu but, if true, I do not know where to get it and how to install it, the EASY way (look above...).

Thanks for any tip to get a step further, the EASY way. :D

---

### Post by yetanothersteve on 2006-08-15
If you installed the VMWare Tools you would be able to copy and paste from XP to Ubuntu and vice versa. You would also get improved hardware support, especially video or graphics.

The VMWare Tools are in the VMWare Workstation release in the folder lib/isoimages and the one you want is windows.iso.
There are other images for other guest operating systems, like linux or freebsd.

You just need to download VMWare Workstation to get the tools ISOs, you should not have to install it or even get a key.

The tools may be in another product from VMWare, but I cannot speak to that.

---

