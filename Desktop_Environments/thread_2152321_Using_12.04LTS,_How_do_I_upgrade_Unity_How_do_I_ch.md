---
title: "Using 12.04LTS, How do I upgrade Unity? How do I check current version?"
date: 2013-06-07
forum: Desktop Environments
---

### Post by TWj2X6Ln4F on 2013-06-07
Hey guys,

Topic title says it all. If I understand correctly, newer versions of ubuntu have a newer version of unity, am I correct? Is it at all possible to upgrade? How do I check the current version of unity I am running now?

---

### Post by vadimkolchev on 2013-06-07
It is highly likely that the "new" version of unity will bring with itself a whole lot of updated packages, libraries and so on, so you will need to enable repositories from newer release and it is not what you need if you plan to stay on lts. LTS is stable, but still you have to deal with older software, it is a price you have to pay.

---

### Post by ArminasAnarchy on 2013-06-07
The command to upgrade packages is:

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

There are three parts: the first checks your list of installed software against the latest in the repositories, the second upgrades those packages which are out of date (if applicable), and the third upgrades those packages which are core system packages - things like your kernel image, etc (sudo apt-get upgrade only upgrades non-essential installed software e.g. your browser). I'm not sure whether the desktop environment (in your case, Unity) would be in upgrade or dist-upgrade, so it's best to run both - the "&&" syntax means you can enter the whole let as one line, without having to issue three seperate commands (though if you'd rather do it that way, feel welcome!).

That said, it will only upgrade your Unity **if there is a newer version in your distro's repos.** If you're up to date with the latest version for your particular distro (say you're on 12.04, and the "newer" version you've heard about is in 13.04), then consider either upgrading to the newest version, or Google Unity. Because the software is open source, there will be a source code package on the website - you can then install that (assuming it doesn't clash with anything already installed). I wouldn't be surprised if there was a .deb file out there of the latest build too, there might even be a PPA (basically, a personal, private repository - it means you can get a particular package, but no testing will have gone on to ensure it works on your distro. I use a PPA for installing the alpha builds of Firefox/Thunderbird (Aurora/Earlybird)).

---

### Post by Frogs Hair on 2013-06-07
Try the following command and look under "Architecture."```
 dpkg -s unity
``` The rest of the output are libraries and dependencies which may change if you attempt to upgrade. Starting with 12.10 Unity has no 2D option and if an official distribution upgrade doesn't come via the update manager I would not attempt it. 13.04 is currently using unity 7 and my output may differ due to having aptitude installed.  
 
The link is a ppa for a patch to enhance features for Unity in 12.04. Use at your own risk.  [http://www.webupd8.org/2013/04/new-unity-revamped-ppa-for-ubuntu-1204.html](http://www.webupd8.org/2013/04/new-unity-revamped-ppa-for-ubuntu-1204.html)

---

### Post by vadimkolchev on 2013-06-07
He said he needs to use lts and install a newer version of unity. I wouldn't recommend it, because he will lose all benefits from lts in terms of stability and security.

---

### Post by ArminasAnarchy on 2013-06-07
> **vadimkolchev said:**
> It is highly likely that the "new" version of unity will bring with itself a whole lot of updated packages, libraries and so on, so you will need to enable repositories from newer release and it is not what you need if you plan to stay on lts. LTS is stable, but still you have to deal with older software, it is a price you have to pay.

+1 to this. As evidenced by my use of Aurora/Earlybird, I'd rather be using the latest and greatest rather than the necessarily most stable software, but that's an entirely personal choice, and one you have to decide for yourself. It more of less comes down to whether you think you're capable of ignoring and/or finding solutions to any issues you're likely to encounter. That said, I've done a lot of distro hopping, and even using the beta builds of the next Xubuntu release, the only issues I encountered where cosmetic ones, rather than fatal system flaws which made the computer unusable.

---

### Post by ArminasAnarchy on 2013-06-07
> 
 		 		 		 		 		 				 				 		 			 				[INDENT] 					He said he needs to use lts and install a newer version of unity. I  wouldn't recommend it, because he will lose all benefits from lts in  terms of stability and security. 
[/INDENT] 			
  			   		
 			 				 			 			 			 		
 	
Ehhh. On the security front certainly, I think since we're all on Linux,  it's something we can more or less forget about. There are no known  Linux viruses "in the wild" AFAIK, and all Ubuntu builds use outdated  kernel images anyway (3.9.4 according to the website, I'm not on my  13.04 build atm so can't check the kernel version, but IIRC it was  3.8.x, maybe 3.7.x). I think stability isn't much of an issue either. I  install 12.04 LTS for friends/family I've converted, but I do it simply  because they're not so "linux savvy", and it means they won't be  badgered to upgrade after 9 months. It's a major advantage for  buisnesses too, since it means staff don't have to be retrained. For the  average desktop user, as OP seems to typify, newer software is (more or  less) worth the very small new learning curve (i.e. of working out  where XX is in the settings, how to use new features etc), IMHO.

---

### Post by vadimkolchev on 2013-06-07
It is 3.8.0 here, surely not the latest and there are more bleeding-edge distros. But if he wants, let me say, a "way" to update unity to the latest version, he should just update repos to the 12.10 ones, then update system and 13.04, and update again. It will be better for the software compatibility and probably will cause less errors if any, than trying to install unity version manually and trying to mix software from different releases.

---

### Post by ArminasAnarchy on 2013-06-07
> **vadimkolchev said:**
> It is 3.8.0 here, surely not the latest and there are more bleeding-edge distros. But if he wants, let me say, a "way" to update unity to the latest version, he should just update repos to the 12.10 ones, then update system and 13.04, and update again. It will be better for the software compatibility and probably will cause less errors if any, than trying to install unity version manually and trying to mix software from different releases.

Agreed, or just install a new version cleanly - this is probably the way I'd do it. OP may have reasons for sticking with 12.04, though, and so searching for a .deb, and then solving problems as and when s/he encounters them, IF he encounters them, may be preferable (for him/her, not me).

---

### Post by vadimkolchev on 2013-06-07
Sure, but the only thing I say is that it will not be 12.04 anymore, since he will have to update manually many packages to their newer state, I think, but I may be mistaken. However, I do not think that Unity upgrading involves only one Unity deb. I think, as in gnome, there are a lot of dependancies that will have to be satisfied.

---

### Post by Frogs Hair on 2013-06-08
The out put of the command in   post 4 # lists the current Unity version and dependencies for the installed version which gives a general idea of what packages are involved in a newer version.
 
```
dpkg -s unity
Package: unity
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 4960
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 7.0.0daily13.04.18~13.04-0ubuntu1
Provides: indicator-renderer
Depends: compiz-core, libatk-bridge2.0-0 (>= 2.5.3), libatk1.0-0 (>= 2.2.0), libbamf3-1 (>= 0.4.0), libc6 (>= 2.17), libcairo2 (>= 1.2.4), libdbusmenu-glib4 (>= 0.4.2), libdee-1.0-4 (>= 0.5.2), libgcc1 (>= 1:4.1.1), libgdk-pixbuf2.0-0 (>= 2.22.0), libgl1-mesa-glx | libgl1, libglew1.8 (>= 1.8.0), libglib2.0-0 (>= 2.35.9), libgtk-3-0 (>= 3.1.6), libindicator3-7 (>= 0.4.90), libjson-glib-1.0-0 (>= 0.12.0), libnotify4 (>= 0.7.0), libnux-4.0-0, libpango1.0-0 (>= 1.22.0), libsigc++-2.0-0c2a (>= 2.0.2), libstartup-notification0 (>= 0.2), libstdc++6 (>= 4.6), libunity-core-6.0-5 (= 7.0.0daily13.04.18~13.04-0ubuntu1), libunity-misc4 (>= 4.0.2), libunity-protocol-private0 (>= 6.90.2daily13.04.05), libx11-6, libxext6, libxfixes3 (>= 1:5.0-4ubuntu1), libxrender1, libzeitgeist-1.0-1 (>= 0.3.14), session-migration, python, unity-common (= 7.0.0daily13.04.18~13.04-0ubuntu1), compiz, compiz-core-abiversion-20130125, libnux-abiversion-20130411.0, compiz-plugins-default, libglib2.0-bin, python-gconf, nux-tools, dconf-tools, unity-asset-pool (>= 0.8.18)
Recommends: gnome-control-center-unity, unity-lens-files, unity-lens-video, unity-lens-photos, unity-lens-friends, unity-lens-applications, unity-lens-shopping, unity-lens-music, indicator-appmenu, indicator-application, indicator-sound, indicator-bluetooth, indicator-datetime, indicator-messages, indicator-printers, indicator-power, indicator-session, indicator-sync, hud
Breaks: unity-lens-applications (<< 5.12.0-0ubuntu2), unity-lens-files (<< 5.10.0-0ubuntu2), unity-lens-music (<< 6.0.0), unity-lens-video (<< 0.3.6-0ubuntu2)
Description: Interface designed for efficiency of space and interaction.
 Unity is a desktop experience that sings. Designed by Canonical and the Ayatana
 community, Unity is all about the combination of familiarity and the future. We
 bring together visual design, analysis of user experience testing, modern
 graphics technologies and a deep understanding of the free software landscape
 to produce what we hope will be the lightest, most elegant and most delightful
 way to use your PC.
Homepage: https://launchpad.net/unity



```

---

