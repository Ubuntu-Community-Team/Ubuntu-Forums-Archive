---
title: "Xubuntu won't load (I think)"
date: 2008-04-27
forum: Desktop Environments
---

### Post by wkdude18 on 2008-04-27
I have all three major ubuntu variants, (xubuntu,kubuntu, ubuntu). I just upgraded to 8.04 yeah! but xubuntu is not loading. It used to load on Gutsy, but now whenever I select a Xubuntu session it justs has a pale brown screen and even if it was loading it is taking forever. Any advice, or do I just need to be patient (or uninstall Xubuntu :()?

---

### Post by Person98 on 2008-04-27
i would give xubuntu a reinstall, use synaptics select xubuntu-desktop for reinstall see if that does it, good luck

---

### Post by grege on 2008-04-29
Mine is the same. I have Gnome, KDE4 and Xfce installed. Gnome and KDE4 work fine, Xfce just sits there with a blank page with a mouse pointer. I uninstalled everything xfce4 and Xubuntu the reinstalled Xubuntu Desktop. Still nothing.

Might be something in Gnome or KDE stopping it. I have looked through the logs and cannot see anything.

Mine is a system that was a beta and upgraded till it is hardy. Maybe some residual beta stuff causing issue.

:(

---

### Post by grege on 2008-04-29
Just installed Xubuntu desktop on my notebook. Same deal. Brown screen, mouse pointer, then nothing. This computer was also a beta that was updated. The difference is that this one did not previously have Xfce installed. The result is the same - not a working desktop. Gnome and, in this case, KDE 3 work just fine.

I am not going to reformat and install Xubuntu, I will just continue using Gnome.

Odd but.....

:(

---

### Post by grege on 2008-04-29
Curious.

Tried it on a third machine. This one also an upgraded beta. This time it worked fine.

The two having trouble have Intel CPUs, one an NVidia 8400GS the other integrated Intel graphics. 

The one that worked has an Nvidia chipset, an 8400GS and an AMD CPU.

Logic fails at this point, I cannot think it is a CPU issue.

:)

ps
I do want to try Xfce, I intend to put it on an EeePC when I get my hands on a new 9" model. I want to learn to use it, but I am stymied.

---

### Post by grege on 2008-04-29
Solution

log out and in a couple of times and the error evaporates.

use ctl-alt-bckspce to exit blank screen

:)

---

### Post by peterstastny on 2008-04-29
Hi Folks,
i was wondering if someone would come with similar issue.
Mine is probably the same:
I have yesterday installed brand new 7.10 (i had not 8.04 at disposal which is not problem of course ...). After restart, system came up with full of upgrades for 7.10 so I installed them too. After another restart I had finally fresh and fully upgraded 7.10.
I have run Update Manager and clicked on "Upgrade to 8.04", of course ;) (looking for it for couple of week) and succesfully finished installation, which prompted me to reboot.

I have done it and log in but after that only clear screen (no panels, simply nothing only mouse pointer).

Why is that so? Is there some kind of 'serious' solution?
Reinstall can be the one, but without burned CD of 8.04 I would have to go again through 7.10 to 8.04 ... it took me last evening around one hour. I am sorry I do not have so much time ;( 

Any help would be welcome :)

Peter

p.s. all you need is 'to post', so everyone can share the moment of pure enlightenment with you :)

---

### Post by a2brute on 2008-07-24
Another user reporting the same problem here.

I installed xubuntu 8.04 from CD, it booted to a blank screen.  So I jumped to a console (ctrl-alt-F1) logged in and ran "sudo dpkg-reconfigure xserver-xorg"   I found that if I switched to the using the frame buffer, it would then reboot into the desktop just fine.  

However, everything is terribly slow, video-wise.  So I ran the hardware driver application to install the restricted nvidia drivers.  I have a GeForce4 MX 440 PCI card.  After installing the restricted drivers for the nvidia card, I reboot and the login screen comes up just fine.  But after logging in, now I get a blank (black) desktop with a mouse pointer, but no panels or menus or icons at all.  

Any ideas?

Thanks.

---

