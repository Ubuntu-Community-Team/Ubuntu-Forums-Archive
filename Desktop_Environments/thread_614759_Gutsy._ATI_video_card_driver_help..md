---
title: "Gutsy. ATI video card driver help."
date: 2007-11-16
forum: Desktop Environments
---

### Post by brjoon1021 on 2007-11-16
I have an ATI 9700 Pro (ALL-IN-Wonder version) video card, it has the R300 chip, I think. I am not a gamer - yet anyway. But I will do photo editing and video editing. I watch DVDs and on line videos.

I am pretty confused about what is available to the "red-headed-stephchild" ATI card owners (in the Linux world we are the dregs). I tried to use envy to install the driver there and it screwed everything up so badly that I could not even start X. I had to reinstall. So, without it am I just running the generic Vesa driver? isn't there something better ? I have used the fglrx driver before on other distros, but for some reason it did not work this time at all for me.

I would appreciate your help. My card has TV capability, if that matters..

Thanks,

B

---

### Post by booglebox on 2007-11-16
Me too- running a 9250. Tried repeatedly doing all the steps on the ATI wiki but to no avail.

---

### Post by anthonie on 2007-11-20
Same trouble here with the latest Ubuntu. Have been running older versions for years, without any significant trouble ever. I have an onboard Intel 93454 graphics card which worked fine, even after upgrading Feisty to Gutsy. The only trouble I got was that E17 would not run properly. 

But then...
Just recently I got back an AGP card I had somewhere else and put it in this machine. Its an ATI 3D club 9250 Radeon with 256Mb memory. 

At once with about every reboot I would make I would have to reset the drivers. Did the whole gpkg reconfigure trick couple of times, no, over and over and after a while less problems seemed to appear.

This morning I made the mistake of upgrading some things and boom, no graphics card anymore. Now, with every single reboot I make it nags me about the card not being recognised etcetera.

Tried downloading the official ATI drivers, as others reported good results with that: nada. 

Just a couple of weeks ago I gave my Feisty CD to a fellow who had lots of trouble with his Windows machine. I gave it to him to play around with, he took it with him while traveling. So right now, I am downloading Feisty again and I will downgrade as soon as I can get that ISO burned. 

Feisty seems a lot more stable, even with these graphics cards from ATI. So I ll start from scratch and have learnt for once and for all that also with Ubuntu, the latest is not necesarily the greatest. Back to Feisty.

---

### Post by Arron17 on 2007-11-20
This guide [http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385) Helped me to get my ati radeon 9550 card working with Full 3D acceleration, hope it helps you too.

---

### Post by Miguel on 2007-11-21
Just for the record, ATi dropped support for R200 cards with fglrx 8.29.6. I fear most of the troubles you guys are seeing are caused by trying to install a quite recent driver of fglrx. If you are really interested in running fglrx for your cards, you should look for fglrx 8.28.8.

And this is to the original poster: you are ***not*** running vesa by default. The default configuration for r200 (radeon 8500 to 9250), r300 (radeon 9500 to 9800) r400 (X300 to X850) is xserver-xorg-video-ati. It has 2D (faster than fglrx) and 3D (25% slower than fglrx) accel. Since yesterdeay, X1000 cards will also have 2D acceleration with that driver. This driver also supports AIGLX with (in general) decent performance, and will run Quake 3 and similar games very well. Nexuiz is another story.

It's a shame we can't enable st3c texture compression (due to patents), and to this day we don't AFAIK have vertex shader progammability.

EDIT: With gutsy, your 9700 can probably do TV-out with the default driver, although I'm not 100% sure (I haven't tested my Mobility Radeon 9600)

---

### Post by anthonie on 2007-11-21
Gracias Miguel por (o para?) su info!

For the interested: Yesterday I downloaded Feisty Alternative. Everything went as smooth as it could possibly be,  At default my resolution is now 1280x1024. 

Ofcourse the question now is, what was it from the updates that screwed my late Ubuntu install in the first place? I suppose I have to be carefull with graphics drivers, but are there other things to be suspicious about?

regards,

Anthonie

---

### Post by Miguel on 2007-11-21
> **anthonie said:**
> Gracias Miguel para su info!


You're very welcome

> 
Ofcourse the question now is, what was it from the updates that screwed my late Ubuntu install in the first place? I suppose I have to be carefull with graphics drivers, but are there other things to be suspicious about?


OK, the first thing I'd be suspicious is 3rd party drivers. Have you installed fglrx? Please note that, on your card, you shouldn't install the version from the Ubuntu repositories. In any case, let's keep the default ati driver by now. 

When you say that updates bork your system, are you just updating Feisty (via synaptic or update manager) or are you dist-upgrading to Gutsy? If it's the latter, I'd be suspicious about another repositories you have enabled (i.e. for compiz-fusion or some other). A good thing to do might be updating before installing anything else.

If the amount of packages to update is not huge, could you post the list?

---

### Post by Idiot_Box on 2007-11-21
Just a quick heads up to Ubuntu and Debian users for easy installation of Nvidia and ATI video cards.  

Alberto Milone wrote (ENVY), a python automation script which will:
 [LIST]
[*]detect the model of your graphic card
[*]download the right version of the proprietary driver for your ATI or Nvidia card from ATI or Nvidia's websites
[*]handle the dependencies required to build the module
[*]install/uninstall the driver
[*]set up your xorg.conf
[/LIST]


[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

I have used this from Dapper to Gutsy to install video drivers...works great!!  Hope this helps.
I have used this to install both a new Nvidia and an older ATI Radeon 9800 Pro.

---

### Post by anthonie on 2007-11-21
> **Miguel said:**
> Have you installed fglrx? 
Not seperately. To my knowledge, that is.

> Please note that, on your card, you shouldn't install the version from the Ubuntu repositories. In any case, let's keep the default ati driver by now. 

Thanks, I'll keep an eye on that. 

> When you say that updates bork your system, are you just updating Feisty (via synaptic or update manager) or are you dist-upgrading to Gutsy?

Synaptec. I did not have a close look, the last time I was updating. I will ofcourse in the future! :D

> If the amount of packages to update is not huge, could you post the list?
193. it's a bit much.

Thanks

regards,

Anthonie

---

### Post by Miguel on 2007-11-21
> **anthonie said:**
> 
193. it's a bit much.


Don't worry. Open a terminal and type there
```

sudo aptitude dist-upgrade

```

Because you have upgradeable packages, it will ask for confirmation. You can copy-paste the whole list here and then hit "n" to refuse those changes.

---

### Post by anthonie on 2007-11-21
Miguel,

The list is below

The following NEW packages will be automatically installed:
  linux-headers-2.6.20-16 linux-headers-2.6.20-16-generic 
  linux-image-2.6.20-16-generic linux-restricted-modules-2.6.20-16-generic 

The following NEW packages will be installed:
  linux-headers-2.6.20-16 linux-headers-2.6.20-16-generic 
  linux-image-2.6.20-16-generic linux-restricted-modules-2.6.20-16-generic 

The following packages will be upgraded:
  app-install-data app-install-data-commercial apport apport-gtk bind9-host 
  bsdutils capplets-data cdrecord cupsys cupsys-bsd cupsys-client 
  cupsys-common dbus dbus-1-utils dnsutils evolution-data-server 
  evolution-data-server-common file firefox firefox-gnome-support 
  genisoimage gimp gimp-data gimp-python gnome-app-install 
  gnome-control-center gnome-panel gnome-panel-data hpijs hplip hplip-data 
  hwdb-client-common hwdb-client-gnome iptables language-pack-en libbind9-0 
  libcamel1.2-10 libcupsimage2 libcupsys2 libcurl3 libdbus-1-3 libdns22 
  libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 
  libedataserver1.2-9 libedataserverui1.2-8 libegroupwise1.2-13 
  libexchange-storage1.2-3 libexif12 libflac7 libfreetype6 libgimp2.0 
  libgl1-mesa-dri libgl1-mesa-glx libglu1-mesa libgnome-window-settings1 
  libisc11 libisccc0 libisccfg1 libjasper-1.701-1 libkrb53 liblwres9 
  libmagic1 libmagick9 libmetacity0 libnspr4 libnss3 libpanel-applet2-0 
  libpng12-0 libpoppler1 libpoppler1-glib libslab0 libsmbclient libsndfile1 
  libssl0.9.8 libvorbis0a libvorbisenc2 libvorbisfile3 libwrap0 
  linux-generic linux-headers-generic linux-image-generic 
  linux-restricted-modules-common linux-restricted-modules-generic 
  mesa-utils metacity metacity-common mkisofs mount openoffice.org 
  openoffice.org-base openoffice.org-calc openoffice.org-common 
  openoffice.org-core openoffice.org-draw openoffice.org-evolution 
  openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk 
  openoffice.org-impress openoffice.org-java-common openoffice.org-math 
  openoffice.org-style-human openoffice.org-writer openssl poppler-utils 
  python python-apport python-gdbm python-launchpad-bugs python-minimal 
  python-problem-report python-uno python2.5 python2.5-minimal rdesktop 
  rsync samba-common smbclient tar tcpdump ttf-opensymbol tzdata 
  unattended-upgrades update-manager update-manager-core util-linux 
  util-linux-locales vim-common vim-tiny wodim xscreensaver-data 
  xscreensaver-gl

---

### Post by Miguel on 2007-11-21
Of all these packages, only two "blocks" should affect your 2D and/or 3D rendering abilities*. They are the new linux kernel and the mesa upgrade (probably a security one). Upgrading mesa is not dangerous in principle. The only thing you can lose with mesa is 3D so, unless you are running compiz, gnome should look okay even if you removed mesa. That leaves the kernel. However, as it is a new kernel, a new entry will be created in grub, allowing you to choose between both kernels during boot.

What I would do is "safe-upgrading" the packages so that you have at least most security updates and then have a look at the remaining packages (muuch less, probably only the kernel). A safe upgrade only installs those packages without a version bump, so that only security fixes have been applied. To do this, type in a terminal
```

sudo aptitude upgrade

```
Yes, without "dist-". It can also be performed in synaptic, but to do that, you must tell synaptic to do a especial kind of update (it defautls to dist-upgrade). On the latest aptitude, "sudo aptitude safe-upgrade" also works.

You are probably wondering if this is safe or not. If you are not sure, but you have a way to get to the internet (from windows or from another computer) I can help you to hold or downgrade especific packages to get back to X. And this without performing a clean install.

So, what I am asking you to do is:[list][*] Decide whether you want to safe-upgrade or not
[*] If you want to, do it and then restart X (Ctrl+Alt+Backspace will do it) after all packages are downloaded and installed.
[*] You should be back to gdm. Great. What packages are left to dist-upgrade?
[/list]

PS: I'm going out now, so I won't be able to check your answers till tomorrow at 9:00 CET.

NOTE: I don't know if a screwed up dbus upgrade can bork X.

---

### Post by anthonie on 2007-11-21
> You are probably wondering if this is safe or not.

Nope, because

> A safe upgrade only installs those packages without a version bump, so that only security fixes have been applied. To do this, type in a terminal

sounds way too logical for me to worry. Assuming ofcourse that without a version bump no major changes will be made to software affecting the graphics. But that's probably more the way of Redmond :)

I will do a safe upgrade tonight. And yes, I run a triple-boot Ubuntu/XP/Vista. Getting on the net will be no problem. I'll post the results from my upgrade as soon as I have them.

muchas gracias

PS: Una otra pregunta

Are there any known problems with E17 and Feisty/Gutsy that might affect the cards settings? I plan on reinstalling E.

---

### Post by anthonie on 2007-11-21
Hi Miguel,

Upgrade went flawless. However, the system did not like the idea of just restarting X, so it became a reboot. Rebooting goes so fast, it doesn't really matter. So far, everything works fine. 

Below the list of available upgrades.

anthonie@ubuntu:~$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  linux-headers-2.6.20-16 linux-headers-2.6.20-16-generic 
  linux-image-2.6.20-16-generic linux-restricted-modules-2.6.20-16-generic 
The following NEW packages will be installed:
  linux-headers-2.6.20-16 linux-headers-2.6.20-16-generic 
  linux-image-2.6.20-16-generic linux-restricted-modules-2.6.20-16-generic 
The following packages will be upgraded:
  linux-headers-generic linux-image-generic 
  linux-restricted-modules-generic 
3 packages upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 48.9MB of archives. After unpacking 179MB will be used.
Do you want to continue? [Y/n/?] 


I'll go and play some more with this fresh ubuntu install.

---

### Post by Miguel on 2007-11-22
> 
Hi Miguel,

Upgrade went flawless. However, the system did not like the idea of just restarting X, so it became a reboot. Rebooting goes so fast, it doesn't really matter. So far, everything works fine.

Below the list of available upgrades.

I'm glad it worked, although it sucks that you had to reboot. IMHO, one should only be forced to reboot after a kernel upgrade, but I'm probably a bit over the top for those things.

The only remaining packages to upgrade are (as aptitude says) linux-whatever-generic metapackages. These are created so that, when there is an ABI bump (this means that modules won't work again unless recompiled), you can upgrade your system without many fears. That's why aptitude is telling you new packages will be installed. 

These being kernel updates, as I told you, will generate a new entry in grub. So you can fully dist-upgrade your system **as long as you don't remove any other package**. After installing those packages you will need to reboot. Now grub should have two more entries related to kernel 2.6.20-16-generic. Choose that one and see if all is going alright.

If not, we'll have to tell both aptitude and apt to hold a couple of packages, more concretely
```

linux-headers-generic linux-image-generic linux-restricted-modules-generic

```

Remember, as long as you keep both kernels you aren't running any especial risk.

EDIT: I must admit I've never used E17, so I have no idea how well it works. I've used fvwm-crystal, as well as IceWM, Xfce, and the two big DE's, but no *box (for more than an hour) or Enlightment. Sorry. All I can say us that they shouldn't affect anything of your xorg config. Else, it's a bug.

---

### Post by anthonie on 2007-11-22
Hola Miguel,

corren tiempos de allegria!

> No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

In other words: Everything seems to work really nice, smooth and above all; fast!
I'll be off to Palma for a couple of days and after that I'll be looking into some eye candy. Had a try with E17 CVS yesterday-night, so far without any luck.  It may sound silly, but I really like the ability of Linux to customize the look of your PC. 

thanks again!

---

### Post by brjoon1021 on 2007-11-25
As for Envy choosing the correct driver for the video card that it detects... it was Envy that killed X twice and I had to reinstall.

All in all, Nvidia cards are better for Linux, right ? I think that I will dump this Radeon and get a 6600 GT.

---

### Post by anthonie on 2007-12-03
I was slightly succesfull installing E17 again, with help of this thread
[http://ubuntuforums.org/showthread.php?t=546746](http://ubuntuforums.org/showthread.php?t=546746)

However, the graphicssystem seems slightly buggy now. For instance, when I try to switch from Gnome to E17, it may happen that the graphics are all screwed up and I have to reboot first.

---

### Post by sasakitomiya on 2008-02-26
Sorry I now the last post was like 2 months ago.  I have an Asus M6Ne with an ATI Mobility Radeon 9700.  It works fine with Gutsy I installed and it supported Compfiz and everything.  I changed to the fglrx drive and Compfiz doesn't support it but it works fine.  With a little tuning in screen resolution.  All I needed to do was open the restricted drives and activate it.

---

