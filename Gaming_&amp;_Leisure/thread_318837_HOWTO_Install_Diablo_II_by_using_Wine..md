---
title: "HOWTO: Install Diablo II by using Wine."
date: 2006-12-14
forum: Gaming &amp; Leisure
---

### Post by JasonValdron on 2006-12-14
How to install Diablo II under Ubuntu/Kubuntu. This how to is for Edgy, but it might work in other versions. We need to compile Wine by our selfs, or else, it will lag. Well, for me. Eheh

1. Download Wine source.
Come here: [http://sourceforge.net/project/showfiles.php?group_id=6241](http://sourceforge.net/project/showfiles.php?group_id=6241) and download the source package.

2. Extract Wine source, configure, make depend, make, make install.
```
cd /path/to/wine/souce
tar xf wine-VERSION.tar.bz2
./configure
make depend && make
make install
```
If it complains for missing packages, you can install them by using "apt-get install PACKAGE".

3. Put in your Diablo II install CD, mount it, run install.exe with Wine.

4. Install by switching CDs when it asks you, by unmounting and mounting the CDs, once done, you can install Lord of Destruction if you want to.

5. Download the lastest patch. Be sure to download the LOD one if you have LOD installed! You can found it here: [http://www.blizzard.com/support/?id=mdt0387p](http://www.blizzard.com/support/?id=mdt0387p)

6. Install the patch with Wine, it's supposed to go thought without problems.

7. Go download a NoCD patch from here: [http://www.gameburnworld.com/gp/gamefixes/diablo2.shtml](http://www.gameburnworld.com/gp/gamefixes/diablo2.shtml) Download the "DIABLO 2 v1.11b [ENGLISH] NO-CD/FIXED EXE (1.05MB)" one.

8. Important: Rename your current Game.exe to Game.exe.orig! If you don't it will not work! Afterwards, extract that NoCD patch into your Diablo II directory, and rename it to Game.exe.crk

9. Download this script D2 Loader for Linux script: [www.poksi.org/~hifi/lnxd2load/D2Loader-current.sh](www.poksi.org/~hifi/lnxd2load/D2Loader-current.sh)

10. Open it with your favorite text editor. And then change the options, be sure to change your path to the correct one. and you can set options if you want, I use -w for windowed.

11. Run D2Loader-current.sh and the game sould work! :)

Please leave some comments :) This is my first how to.

---

### Post by dsb on 2006-12-18
I tried your method but I got this error when trying to install 

dave@hercules:~$ wine /media/cdrom0/install.exe
wine: creating configuration directory '/home/dave/.wine'...
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!

---

### Post by Sammi on 2006-12-18
Do you have an ATI or Nvidia grafics card, and have you tried installing new grafics drivers?

---

### Post by JasonValdron on 2006-12-18
Do you have your video card drivers installed? If not well, install some that is 3D accelerated, which means you need NVIDIA or ATI.

---

### Post by lotusleaf on 2006-12-19
I'd suggest anyone interested in building WINE for themselves read this page:

[Recommended Packages (Building Wine on 32bit)](http://wiki.winehq.org/Recommended_Packages)

Building wine without some (or all?) of the above mentioned recommended packages (versions may differ from those printed for a few dev packages at above link) is not something I recommend. You may find some bumps in the road to using your newly built wine if you don't have certain packages installed prior to your build. It may say everything is dandy when you ./configure without them, but that doesn't mean a particular program you try to run with wine later won't burp, sputter, and fail because you didn't install one or more of the recommended packages it needed before you built wine from source.

You can import Alexandre Julliard's key like so:

```
gpg --keyserver wwwkeys.pgp.net --recv-keys B9461DD7
```

Then when you [download wine source packages](http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449) (downloading the bz2 and the sign file) you can verify it before using:

```
gpg --verify wine-0.9.27.tar.bz2.sign wine-0.9.27.tar.bz2
```

Substitute the wine version you downloaded for the above example in verifying the sig. Some may say that you don't need to follow this step, but it's very important to verify the gpg sigs of software you download before using. :)

And remember, there's the WINE IRC channel to get live answers to your questions:

[irc://irc.freenode.net/winehq](irc://irc.freenode.net/winehq)

There are lots of helpful people there! Good luck on your howto. =)

---

### Post by dsb on 2006-12-20
I have an older ati radeon R100 QD (7200) which I do not think the proprietary ATI drivers work as it says it is for 8500 and above. I have had wine/diabloII working with redhat and gentoo with this vid card running 3d accel, but I'm new to the Ubuntu, so I may not have all the packages installed as lotusleaf suggested.  I will look into that suggestion.

Thanks

---

### Post by argie on 2006-12-20
I had to run the D2VidTst.exe and choose one of the settings there to play. Else it would quit with an error. Perhaps you should try that too.

---

### Post by addefinnr on 2006-12-27
One small note... If the installer seems to freeze (ie: the progress bars don't seem to do anything) the installer is probably asking for another CD _behind_ the progress window. I couldn't move that window, but by moving the Setup window enough (where you can pick installation sizes etc.) BEFORE you proceed to install makes the progress window drop somewhere else so you can see the "insert disc" dialog.

---

### Post by lego72 on 2007-02-03
> **addefinnr said:**
> One small note... If the installer seems to freeze (ie: the progress bars don't seem to do anything) the installer is probably asking for another CD _behind_ the progress window. I couldn't move that window, but by moving the Setup window enough (where you can pick installation sizes etc.) BEFORE you proceed to install makes the progress window drop somewhere else so you can see the "insert disc" dialog.

This solved my problem when installing Diablo. Thanks for posting this, I was just about to give up (for the night anyway).

Hopefully this helps others.

---

### Post by verlooy on 2007-02-05
i never used wine before, where do i install the d2 files?

---

