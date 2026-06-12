---
title: "Ubuntu gutsy LiveCD: how to customize login and password?"
date: 2007-10-16
forum: Desktop Effects &amp; Customization
---

### Post by darkmaster on 2007-10-16
Hi all, I'm trying to use reconstrctor on Ubuntu Gutsy. Of course, since it is designed for feisty, it has problems. But the problems I', getting are really severe... I can't customize login and password.

Since I use entrance instead of GDM and entrance does not support autologin, I NEED to insert an username and password. Ubuntu Gutsy uses a unknown username and password.
How do I change them?

The question can be also read as: do you know which is the password and username for the Ubuntu Gutsy LIVECD?

Or do you now how to change the sudo password in Ubuntu Gutsy? When I use reconstrctor, I can access to a command line of the Live CD system that is going to be started. So, I created a new user with a new password for the login. This user DOES login correclty after I created it. But when I try and execute a sudo command, the password I created for the user is not the right one and sudo doesn't work. 

So, how can I set this password? Any idea???
Please help. It is impossibile that in the entire Ubuntu community nobody knows how to solve such an appaently simple task. The Ubuntu creators, for example, should lnow it for sure! Pleaaaase :(

---

### Post by shafin on 2007-12-04
try username linux or root or ubuntu with a blank password.

---

### Post by darkmaster on 2007-12-05
> **shafin said:**
> try username linux or root or ubuntu with a blank password.

tried all of these combination already :(

---

### Post by hallowname on 2007-12-12
the file 10user or 10adduser or something of that sort is in a casper/scripts/.... folder either inside the remaster folder (the open ISO) or the initrd (the file that /initrd.img on the live disc is linked to) chroot to the root fol (uncompressed squashfs) and run 'passwd user' to fixate 'user's password...

have phun hacking

---

### Post by darkmaster on 2007-12-12
> **hallowname said:**
> the file 10user or 10adduser or something of that sort is in a casper/scripts/.... folder either inside the remaster folder (the open ISO) or the initrd (the file that /initrd.img on the live disc is linked to) chroot to the root fol (uncompressed squashfs) and run 'passwd user' to fixate 'user's password...

have phun hacking

Already di all of this hacking man, no luck. Ubuntu did something strange to protect this release. With Feisty I had no problem hacking it :(
Even creating a new user and giving him administration privileges won't work once the iso is loaded. It is considered as a common user unable even to run sudo :(

---

### Post by Ptero-4 on 2007-12-15
Hi. I got a small question for you guys. I'm trying to mod my gutsy CD (actually LinuxMint 4 which is based on gutsy) and wanted to know something, I made my own filesystem.squashfs image supercharged with lots of custom repos, all the dev tools (anjuta and stuff) and dev libs, picasa, etc and now I want to put it in a geubuntu luna nuova (also gutsy based) LiveCD (my plan is to extract the contents of the geubuntu liveCD using the instructions at this guide:
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)
Drop my squashfs image in the casper folder, give the LiveCD a name, make it's md5 and rebuild it using the same guide. But I wonder: Will the LiveCD desktop (what you see when you boot off the CD) keep being the original one? or it will automatically change to the contents of the squashfs image? and if it's the latter, is there any way to have the liveCD desktop and the desktop inside the squashfs image be diferent?

---

### Post by darkmaster on 2007-12-16
> **Ptero-4 said:**
> Hi. I got a small question for you guys. I'm trying to mod my gutsy CD (actually LinuxMint 4 which is based on gutsy) and wanted to know something, I made my own filesystem.squashfs image supercharged with lots of custom repos, all the dev tools (anjuta and stuff) and dev libs, picasa, etc and now I want to put it in a geubuntu luna nuova (also gutsy based) LiveCD (my plan is to extract the contents of the geubuntu liveCD using the instructions at this guide:
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)
Drop my squashfs image in the casper folder, give the LiveCD a name, make it's md5 and rebuild it using the same guide. But I wonder: Will the LiveCD desktop (what you see when you boot off the CD) keep being the original one? or it will automatically change to the contents of the squashfs image? and if it's the latter, is there any way to have the liveCD desktop and the desktop inside the squashfs image be diferent?

I don't now about this man but now reconstructor for Gtsy is out so there's no problem anymore building a custom Ubuntu from gutsy. Can I ask you what are you planning with your custom Geubuntu Luna Nuova?

---

### Post by Ptero-4 on 2007-12-16
> **darkmaster said:**
> I don't now about this man but now reconstructor for Gtsy is out so there's no problem anymore building a custom Ubuntu from gutsy. Can I ask you what are you planning with your custom Geubuntu Luna Nuova?

What I was planning is something like this.
Make it so that when you boot into the LiveCD, you get to see Geubuntu (e17, geubuntu artwork), but if you use the install icon to install linux, what installs in your box (what you see after rebooting and booting off your newly installed system) is linuxmint with my customizations, the problem is that from past aptemts (with gutsy's reconstructor) I noticed that the contents of the squashfs image (this is the image that the liveCD installer lays on your HD) get copied to the LiveCD desktop (the desktop you work on while you're on the LiveCD) and I don't want that (see the attachment 1 for the LiveCD desktop and attachment 2 for the desktop in the installed system).

P.D: I would like to not have to install e17 in the squashfs image since I already built it and don't want to mess with it again.

---

### Post by darkmaster on 2007-12-18
> **Ptero-4 said:**
> What I was planning is something like this.
Make it so that when you boot into the LiveCD, you get to see Geubuntu (e17, geubuntu artwork), but if you use the install icon to install linux, what installs in your box (what you see after rebooting and booting off your newly installed system) is linuxmint with my customizations, the problem is that from past aptemts (with gutsy's reconstructor) I noticed that the contents of the squashfs image (this is the image that the liveCD installer lays on your HD) get copied to the LiveCD desktop (the desktop you work on while you're on the LiveCD) and I don't want that (see the attachment 1 for the LiveCD desktop and attachment 2 for the desktop in the installed system).

P.D: I would like to not have to install e17 in the squashfs image since I already built it and don't want to mess with it again.

Sorry, personally I wouldn't know how to help you on this. But may I ask you why are you trying to create something like that? Wouldn't it be something like a fake Geubuntu? I mean, you run the Live and see a Geubuntu dekstop, then install it and obtain a totally different thing... but why?

---

### Post by Ptero-4 on 2007-12-18
It's more like an experiment to see if it's possible (my idea is something like making a liveCD that uses a extremelly lite desktop on the LiveCD but installs a more standar (xfce perhaps) one, the reason is that some people might have enough RAM/CPU in their boxes to run XFCE (or gnome/KDE) from a regular HD install but not to run them off the LiveCD (due to the fact that the LiveCD takes away some RAM and you don't have swap while in it).
The idea is to slowly phase out the alternate CD and make it become a "update-CD" solelly for the purpose of dist-updating. In that way we might be able to eliminate the download options that might confuse people who are coming by first time, and instead give them a LiveCD that can gracefully go from full gnome/KDE/xfce desktop to fluxbox/icewm or even CLI/ncurses based on the hardware-detection done on startup (while conversing the install image that is supposed to be there).
To put it simply, when the user sticks the liveCD, ubuntu detects if the PC have enough RAM/CPU to confortably run whatever DE comes in it (Gnome/KDE or XFce), if it detects that the computer won't be able to run that DE from the LiveCD (remember that you need more RAM/CPU to run the LiveCD than you would need to run off the HD, and some computers can run xubuntu fine from the HD but can't bear the extra load of running it off the liveCD), it can downgrade to a lighter WM without forcing the user to install it, that way the user will only use a lighter WM to do the instalation and then he gets the real deal when he boots off his HD, where he gets to use all the RAM and have also a swap partition.

---

### Post by darkmaster on 2007-12-19
uhm, could be a nice idea but I till believe that the user would get confused by the sight of a desktop of a certain kind in Live and then finding himself with a different desktop once it's installed... ayway, sorry, I cannot help you here, too much a technical problem for me ;)

---

