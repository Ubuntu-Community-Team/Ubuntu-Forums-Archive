---
title: "Tried adding LXDE to UNR, now USB broken again"
date: 2010-02-19
forum: Desktop Environments
---

### Post by Ubunthree on 2010-02-19
MSI Wind U100, Karmic, Netbook Remix.

I installed LXDE from the repos (and then the whole lubuntu-desktop package shortly thereafter, when I found out that it was available), and am able to log in to either environment. Using LXDE, I found that pcmanfm had a bug which prevented it from assigning default "open with" applications to file types. Some forum surfing gave me a fix for this, which was to enable a lucid repo, upgrade to the latest pcmanfm, and then turn the repo off again. This fixed the "open with" issue, but I was unable to find a way to mount USB flash drives under LXDE, and I needed to use one. So I logged back in under UNR and discovered that UNR now will not detect USB devices any more either. A mouse will work if it is plugged in before startup, but not if it is unplugged and put back in again. Flash drives are invisible even if I start up with them.

I had this problem when I first started with UNR, but fixed that by installing or reinstalling gvfs, gnome-mount, gnome-device-manager, gnome-volume-manager, hal and thunar (as recommended in another thread on these forums). This solution, however, is not working this time around; nothing I do will wake up my USB ports. And I seem to remember flash drives being mounted at startup even before I fixed the automounting problem, which is not the case this time. If anyone can tell me what I need to do here, I would be grateful.

Ideally I would like to fix LXDE too and keep it along with UNR, as I kind of like it, but if I need to somehow wipe LXDE in order to fix this, then I can live without it.

Thanks!

---

### Post by Ubunthree on 2010-02-20
It gets worse. I don't know how to undo whatever it was that killed USB for me, so I decided to just totally reinstall UNR and update it back to where I was yesterday. As I am of course unable to lifeboat anything onto a flash drive as I normally would, I opened the U100, pulled the hard drive out, hooked it through a transfer cable into my desktop machine and saved my Home folder there. That at least went well enough, and the U100 is put back together just fine. I have the UNR iso on a flash drive, and can *boot* into that. "Install Ubuntu-Netbook-Remix 9.10" appears in the Favorites menu as it should. But, when I click on it, I get the "Opening... Install Ubuntu-Netbook-Remix 9.10" notification, and then.... nothing happens. The LED on the flash drive comes on for a couple of seconds, and then nothing. The flash drive doesn't appear in the "Volumes" section of the Files & Folders menu, though lsusb seems to show it, and gparted appears to show it as /dev/sdb with the mount point at /cdrom. So I am not only unable to mount USB devices, but also unable to reinstall the system. I need to fix all of this, as the netbook is more or less useless to me if I can't get files in and out of it.

I have WinXP on the same machine, and flash drives mount as they should there.

Thanks in advance for any help anyone can give me.

(This started as a Desktop Environment question, but probably should be moved into the Laptops or General Help forum,,,)

---

### Post by Ubunthree on 2010-02-21
Okay, never mind... All I could think of was that the flash drive's UNR had been corrupted somehow, so I ran it through the USB Startup Disk Creator again to remake it, and was apparently that worked, because I was finally able to reinstall with that.

I will mark this "solved" if I ever find out why this happened in the first place, and how it could have been fixed without reinstalling the whole OS.

Why does the koala hate USB devices so?

---

