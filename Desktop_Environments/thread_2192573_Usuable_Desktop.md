---
title: "Usuable Desktop"
date: 2013-12-08
forum: Desktop Environments
---

### Post by brian.farr on 2013-12-08
Just installed unbuntu on virtualbox on my Macbook Pro 9,1 looks great and appears to be working great. One major issue is the usable desktop space. I realise it is through virtualbox but I am losing about a 3rd of my usable desktop. Is there some way I can increase the usable area? I have a 13" screen on my Macbook so it was small enough in the original format.

Want to use unbuntu but at the moment is doesn't appear to be a good option, please advise.

---

### Post by deadflowr on 2013-12-08
What do you mean by usable space?
Is the vb ubuntu desktop size smaller than the vb programs window or something.

A screenshot can give us a better understanding of what you mean.

---

### Post by brian.farr on 2013-12-08
> **deadflowr said:**
> What do you mean by usable space?
Is the vb ubuntu desktop size smaller than the vb programs window or something.

A screenshot can give us a better understanding of what you mean.


 
When I usable space I mean the area in the desktop I can actually view and work in.
THe VB screen fills the Mac screen no problems but the unbuntu terminal window remains the same size in normal mode and full screen, full screen sees a black border around the unbuntu terminal.
I have attempted to get a decent screenshot and attach my best effort :(
Hope this helps.

---

### Post by deadflowr on 2013-12-08
Try changing the resolution.
Open the dash and search/type Displays.

---

### Post by steeldriver on 2013-12-08
If the **virtual machine desktop** is not filling the **VirtualBox application window on the host** when you resize / maximize it, then that is usually because you have not reserved enough video memory in the VM setup (under the VirtualBox Settings menu  --> Display --> Video)

---

### Post by brian.farr on 2013-12-09
> **deadflowr said:**
> Try changing the resolution.
Open the dash and search/type Displays.

Thanks, dumb question for you but I am new to this so please bear with me. Where do I find the "dash"? I assume you mean dashboard or is it another terminal window? Is this in VB or unbuntu?

Cheers
Brian

---

### Post by brian.farr on 2013-12-09
> **steeldriver said:**
> If the **virtual machine desktop** is not filling the **VirtualBox application window on the host** when you resize / maximize it, then that is usually because you have not reserved enough video memory in the VM setup (under the VirtualBox Settings menu  --> Display --> Video)

Done this and rebooted but still the same. Do I need to reinstall unbuntu after changing the setting?

Cheers
Brian

---

### Post by coffeecat on 2013-12-09
The dash is what opens when you click on the topmost icon in the launcher (dock!). Or you can tap the super key to open the dash. I think the super key on an Apple keyboard is the cmd key. Click on one of the desktop guides in my sig to get a complete guide to the Unity desktop.

By the way - have you installed guest additions in Ubuntu? It's been a long time since I've used virtualised Ubuntu in VBox but I think you only get a default resolution until you install guest additions. Plus, using a virtualised OS is very clunky until you do install guest additions.

---

### Post by brian.farr on 2013-12-09
Coffeecat,

I have attached a snapshot of the display, only 2 choices available here. If this is not the correct option please let me know.
Having not heard of "guest additions" is meaningless to me, please can you expand.

Cheers
Brian

---

### Post by deadflowr on 2013-12-09
I'm not sure, did you increase the resolution from something like 800x600 to what is in that screenie of 1024x768?
I can see that the window is now too big for the currently looking window, as it now has scrollbars on the bottom and right-hand side.

As far as guest additions go, I haven't the foggiest idea of how to install them on a mac.
You'll probably have to go to the virtualbox website for that.

I do notice, off hand, that you're running, what seems to be, without 3d acceleration enabled, as the launcher seems like it is the 2d launcher version for ubuntu. If that sentence makes sense.
You can try enabling that in the vb settings > displays. If you want.
Of course if the 3d is already enabled, disregard my comment and laugh it off.

---

### Post by coffeecat on 2013-12-09
> **brian.farr said:**
> 
Having not heard of "guest additions" is meaningless to me, please can you expand.


Which means you haven't installed guest additions. :) A VirtualBox guest OS is about the most irritating and user hostile thing to use unless you install guest additions. You install guest additions in the guest OS - that is, in Ubuntu.

The instructions for installing guest additions are in the user manual. The pdf for the manual will be somewhere in your Mac filesystem but it's been so long since I installed VB on a Mac, I can't remember where. If you double-click on the downloaded dmg installer, the pdf might be viewable from the Finder window that opens.  Failing that, you can download and/or view the manual here:

[https://www.virtualbox.org/wiki/Downloads#manual](https://www.virtualbox.org/wiki/Downloads#manual)

Under the heading User Manual, the left link is for the pdf.

---

### Post by steeldriver on 2013-12-09
On the Windows version of VirtualBox, there is an 'Install Guest Additions...' item in the 'Devices' menu of the main application window, I don't know if it's the same on the Mac. The actual additions seem to be bundled as an iso virtual CD within the guest (although they may be out of date)

The one annoyance I've faced with that is that most modern *buntu desktops automount the virtual CD so that when you try 'Install Guest Additions' it fails because the CD is already mounted. I can't honestly remember how I fixed it last time - it usually involves resorting to the command line and a lot of cursing. In my experience, clicking yes to the 'force unmount' dialog has never worked.

Once you've got ONE version of guest additions installed, it will likely tell you a newer version is available next time you restart VirtualBox - fortunately the update process seems to go much smoother than the install process.

---

