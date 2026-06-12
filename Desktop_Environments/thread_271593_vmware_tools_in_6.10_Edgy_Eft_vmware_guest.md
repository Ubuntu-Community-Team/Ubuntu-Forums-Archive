---
title: "vmware tools in 6.10 Edgy Eft vmware guest"
date: 2006-10-04
forum: Desktop Environments
---

### Post by domino on 2006-10-04
Has anyone successfully installed vmware tools under Edgy? I didn't have a problem installing it. Just that I don't get mouse scroll and the guess OS doesn't release the mouse when I move to the host desktop.

I really don't know if this belong here or the development forum, so sorry if this thread doesn't belong here.

---

### Post by zaroff on 2006-10-08
I had the same problem with the mouse but I figured it out.  To get VMware Tools working in an Edgy virtual machine, here's what I did.  I followed this guide through step 5:  [http://asargent.com/blog/archives/35](http://asargent.com/blog/archives/35)

The vmware-config-tools.pl script dies prematurely with an error about the version of Xorg, so I had to manually install the mouse driver.  To get the mouse driver installed, I did:

sudo cp /usr/lib/vmware-tools/configurator/XOrg/6.8.x/vmmouse_drv.o /usr/lib/xorg/modules/input
sudo chmod 644 /usr/lib/xorg/modules/input/vmmouse_drv.o

Then I did step 6 from the above guide to change the mouse driver in xorg.conf.  Finally, vmware-config-tools.pl renamed /usr/bin/X to /usr/bin/X.BeforeVMwareToolsInstall so I had to rename it back:

sudo mv /usr/bin/X.BeforeVMwareToolsInstall /usr/bin/X

After this, I rebooted and everything was working.  Hope this helps.

---

### Post by domino on 2006-10-09
Hi zaroff,

For some reason the patch seems to fails on step 5. :( 'Guess i'll keep trying and hopefully get the mouse running correctly.

thanks!

```
admin@linux:/usr/bin$ sudo patch vmware-config-tools.pl /tmp/patch.txt
patching file vmware-config-tools.pl
Reversed (or previously applied) patch detected!  Assume -R? [n] y
Hunk #1 succeeded at 589 (offset 2 lines).
Hunk #2 FAILED at 3876.
Hunk #3 FAILED at 4031.
Hunk #4 FAILED at 4077.
Hunk #5 FAILED at 4936.
4 out of 5 hunks FAILED -- saving rejects to file vmware-config-tools.pl.rej
```

---

### Post by domino on 2006-10-09
Good news! it turns out after installing with vmware-tools-any-update2, all i had to do was install the mouse driver via your instructions:

```
sudo cp /usr/lib/vmware-tools/configurator/XOrg/6.8.x/vmmouse_drv.o /usr/lib/xorg/modules/input

sudo chmod 644 /usr/lib/xorg/modules/input/vmmouse_drv.o
```

PS. There is a minor correction to your how-to

> **zaroff said:**
> To get the mouse driver installed, I did:

sudo cp /usr/lib/vmware-tools/configurator/XOrg/6.8.x vmmouse_drv.o /usr/lib/xorg/modules/input


it should be: sudo cp /usr/lib/vmware-tools/configurator/XOrg/6.8.x**[COLOR="Red"]/[/COLOR]**vmmouse_drv.o /usr/lib/xorg/modules/input

Thanks for the heads up :KS

---

### Post by zaroff on 2006-10-09
> **domino said:**
> 

PS. There is a minor correction to your how-to



it should be: sudo cp /usr/lib/vmware-tools/configurator/XOrg/6.8.x**[COLOR="Red"]/[/COLOR]**vmmouse_drv.o /usr/lib/xorg/modules/input



Thanks, domino.  I've corrected it.  Glad to be of help.

---

### Post by saracen on 2006-11-06
I tried the howto and it's failing on Hunks 2-5 just like domino.  What's the solution?

---

### Post by domino on 2006-11-06
Try not patching anyting saracen. I failed to patch it also, but the steps I used on Post #4 solved my problem.

---

### Post by saracen on 2006-11-06
The mouse is working, scroll and everything.  But X is really jittery.  Moving windows and minimization is quite slow.  Is this normal behavior with Ubuntu as a guest OS under vmware?  It's my first time running Ubuntu in vmware (normally do normal install) so I have nothing to benchmark against.

---

### Post by domino on 2006-11-06
Assuming that vmware tools and drivers are installed correctly, it should be slightly jittery. it all depends on your processor speed and memory dedicated to your guest OS. The best way to benchmark is to install vmware workstation on a windows machine. vmware works optimal in windows. I personally don't feel any difference using edgy guest on a linux and windows host.

---

### Post by Techno.Scavenger on 2006-12-07
I think it is indeed quite slow. I am running Gentoo in VMWare server using Windows XP Sp2 as a host and it is usable. But Ubuntu 6.10 on the same machine is just too slow. I think I installed vmware-tools correctly. But I will keep on looking maybe there are few tweaks that may boost the speed of Ubuntu under VMWare. I'm kinda tired compiling everything in Gentoo specially the really big programs like OpenOffice. OpenOffice took me 2 days to compile. :(

---

### Post by Mr Wonka on 2006-12-19
I've got issues with speed as well. All the apps seem responsive enough (term, Firefox etc) it's just that the GUI operation seem to take an age. Dragging windows is appalling, they don't jitter, they pause for 2 seconds before jumping to where your mouse was 1 second ago. Kind of like viewing movement under a strobe light.

Scrolling windows is the same. In fact any GUI operation is just plain slow. I might go to gentoo just to get moving at a decent clip.

A solution would be very nice.,

Thanks
Adam

---

### Post by Techno.Scavenger on 2006-12-22
Though not relly a solution, I found that by using nxserver from Nomachine does help a lot. It's like a terminal server (Windows world) but I think it does really help for vmware  users.

---

### Post by butchd on 2007-02-28
> **zaroff said:**
> I had the same problem with the mouse but I figured it out.  To get VMware Tools working in an Edgy virtual machine, here's what I did.  I followed this guide through step 5:  [http://asargent.com/blog/archives/35](http://asargent.com/blog/archives/35)

The vmware-config-tools.pl script dies prematurely with an error about the version of Xorg, so I had to manually install the mouse driver.  To get the mouse driver installed, I did:

sudo cp /usr/lib/vmware-tools/configurator/XOrg/6.8.x/vmmouse_drv.o /usr/lib/xorg/modules/input
sudo chmod 644 /usr/lib/xorg/modules/input/vmmouse_drv.o

Then I did step 6 from the above guide to change the mouse driver in xorg.conf.  Finally, vmware-config-tools.pl renamed /usr/bin/X to /usr/bin/X.BeforeVMwareToolsInstall so I had to rename it back:

sudo mv /usr/bin/X.BeforeVMwareToolsInstall /usr/bin/X

After this, I rebooted and everything was working.  Hope this helps.

Hey, thanks a lot for this.  It took me hours before I found your suggestion and after running the vmware tools install, changing the mouse driver did the trick.  I can use my scroll button now!  Cheers to you, friend.

---

