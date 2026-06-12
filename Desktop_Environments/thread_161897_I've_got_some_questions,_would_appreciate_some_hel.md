---
title: "I've got some questions, would appreciate some help."
date: 2006-04-18
forum: Desktop Environments
---

### Post by Just4 on 2006-04-18
This is my first time posting, so forgive me if I ask some questions that have already been asked a lot here. - Anyways, I'm pretty much a newbie when it comes to Linux (I've been working with Computers for most all of my life, though DOS and Windows mainly) and I have a fair knowledge of hardware, anyways, for one, I'd like to know what the minimum system requirements are for Kubuntu? I have a Pentium 3 1Ghz/192MB RAM/5.2GB HD (I know the RAM and HD are lacking, but its all I have at the moment, I can upgrade atleast the memory next month, and I can always install another drive for a swap partition, running on a PCChips M754LMR mainboard, (SiS900 based onboard Networking, Nvidia TNT2 Ali (I believe) onboard, and C-Media CMI-8738 onboard sound. Though I use a PCI Radeon 9000 64MB card for graphics on it, though if needed I can switch to the onboard (if the ATI card isn't supported) or another card (I have a few other PCI graphics cards laying around)) - Anyways, besides all the technical info about the system and whether or not what I have will run it, I want to know how easy is it? I'm looking for something relatively easy to install and use (as I've said, this is one of my first attempts at Linux, I've tried ArkLinux but it wasn't very stable.) - from my relatively little dwelling in the Linux world, I like the KDE user interface better than Gnome, and I am not running this system for anything demanding (E-mail, basic web browsing, basic text editing/office apps, little bit of music, maybe some very basic 2D games) just looking for something thats stable and not Windows, and ran across Ubuntu/Kubuntu while looking for easy distros. Anyways, sorry for the long post and thanks beforehand for any help/info.

---

### Post by John.Michael.Kane on 2006-04-18
You can run it on that it will be a little tight and might not be as fast. however you can always uninstall some stuff from kubuntu that you don't need. your ati card model should not have any problems. if you had an old nvidia card around that would give you a better chance at an errorless setup. however try it with what you have that is really the only way to find out. If you have any issues after you install it please post, and someone will try to help with any issues.

---

### Post by Sef on 2006-04-18
If you can wait till about 1 June, Xubuntu will come out as an iso.  It has a lightweight window manager, which should run faster on your machine.

If you can't wait, then do a server install from Breezy and type these commands:

sudo apt-get update

sudo apt-get install xubuntu

---

### Post by Just4 on 2006-04-18
Right now I'm waiting on the ISO to download, but yeah, I can wait for it to release with X, this is more or less just a project anyways (Just to get into Linux and if I find I really like it I may migrate to it completly), I'll try it with my current setup either way and if runs a bit too slow I'll just install X-window sys or wait for Xubuntu (Or try out some different distros while waiting)

---

### Post by aysiu on 2006-04-18
You're posting in Hoary right now. Are you downloading Kubuntu Hoary? Just curious.

The advice about Xubuntu is good. Right now (in Breezy), you have to enable extra repositories for that before you can install it. Full instructions are here:
[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

KDE will run on 192 MB of RAM... slowly, maybe, and there are tweaks to slim it down a bit, too (```
sudo apt-get update
sudo apt-get install kpersonalizer
kpersonalizer
``` may help)

For hardware detection, nothing beats a live CD. Yes, with 192 MB of RAM, the live CD will run extremely slowly, but it will run. The live CD isn't for testing speed--it's for testing how well your video, sound, internet, etc. will be detected by an install.

---

### Post by Just4 on 2006-04-18
[QUOTE=aysiu]You're posting in Hoary right now. Are you downloading Kubuntu Hoary? Just curious.

The advice about Xubuntu is good. Right now (in Breezy), you have to enable extra repositories for that before you can install it. Full instructions are here:
[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

KDE will run on 192 MB of RAM... slowly, maybe, and there are tweaks to slim it down a bit, too (```
sudo apt-get update
sudo apt-get install kpersonalizer
kpersonalizer
``` may help)

For hardware detection, nothing beats a live CD. Yes, with 192 MB of RAM, the live CD will run extremely slowly, but it will run. The live CD isn't for testing speed--it's for testing how well your video, sound, internet, etc. will be detected by an install.[/QUOTE]

I was actually linked from [http://www.kubuntu.org/faq.php#gettinghelp](http://www.kubuntu.org/faq.php#gettinghelp) - I figured it was the right forum, sorry if it isn't. Anyways, I'll download the LiveCD as well to test the hardware detection. Thanks for all the help so far, again sorry if this is the wrong forum.

---

### Post by Just4 on 2006-04-19
I've got it all installed with Xfce, everything works flawlessly, except the sound. Any ideas? (I can put in a soundcard if needed, I have a few laying around that ma yor may not work.) And another, in Xfce, how do I edit the menu (Add items, etc) I specifically want to add something under the Internet sub-menu, how I can do that?

---

