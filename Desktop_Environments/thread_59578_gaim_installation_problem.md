---
title: "gaim installation problem"
date: 2005-08-24
forum: Desktop Environments
---

### Post by cymoril on 2005-08-24
hi everyone,

i want to install gaim but i keep receiving this error:

The following packages have unmet dependencies:
  gaim: Depends: gaim-data (= 1:1.4.0-1ubuntu1~5.04ubp1) but 1:1.1.4-1ubuntu4.4 is to be installed
E: Broken packages


i have updated my packages and i have the latest gaim-data.
the error above says i have 1:1.4.0-1ubuntu1~5.04ubp1 though, instead of the 1:1.1.4-1ubuntu4.4 i need?

when remove gaim-data and apt-get install it again:

Preconfiguring packages ...
Selecting previously deselected package gaim-data.
(Reading database ... 63689 files and directories currently installed.)
Unpacking gaim-data (from .../gaim-data_1%3a1.1.4-1ubuntu4.4_all.deb) ...
Setting up gaim-data (1.1.4-1ubuntu4.4) ...


am i doing something wrong?

thank you.

---

### Post by c0rderr0y on 2005-08-24
do you get the same error trying to install gimp?

---

### Post by KeplerNiko on 2005-08-24
I don't intend to threadjack, but I'd be wary of upgrading the version of Gaim that came with Ubuntu to 1.5.0, at least for the time being.

Yesterday I installed the latest version of Gaim, and since then I've not been able to get sound working right (it functioned fine before).  For some reason, the only two sound options I have are "consolebeep" and "command."  I'm still working on getting things straight to try to get "esdplay %s" to work with the command option, but previously I could select ALSA, ESD, or any of hte other sound protocols I wanted.  With the upgrade to 1.5.0 those options disappeared from Gaim's menu.

I'm not sure of any good reason to upgrade from 1.1.4, and I wish I hadn't done so.

---

### Post by Baltor on 2005-08-24
I'm also having this problem and am curious as to how to fix it.
Thanks.

---

### Post by Mishura on 2005-08-25
I'll get flamed for suggesting this, but why not install the AutoPackage from Gaim's website?  I'm using it right now (1.5.0) and its pretty stable.  Easy as hell to install too.  Just remember to uninstall Gaim from Synaptic before you install the autopackage.

---

### Post by Doctoxic on 2005-08-27
i am having this exactly this same trouble with several programs - see this thread:

[http://ubuntuforums.org/showthread.php?t=60266](http://ubuntuforums.org/showthread.php?t=60266)

Its not just GIMP - also
gaim
mozilla-firefox
mozilla-firefox-gnome-support
smbclient

But assuming its a similar problem for all i'll just descibe whats happening with GIMP.

If i try and 'upgrade GIMP' (or even install it now as i unistalled it to see if a complete reinstall would fix it) i get a message :
gimp:
Depends: gimp-data (=2.2.8-1ubuntu1~5.04ubp1) but 2.2.2-1ubuntu5 is to be installed
It says they have unresolvable dependencies.

If i look at the GIMP_DATA file the installed and latest versions are 2.2.2-ubuntu5 - so i assume i am missing a repository - but they are all ticked in my repository list.

My repository file looks like this:
------------------------------------------------------------------------------------------------------------------------------
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

## deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

## deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
## deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse universe main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
--------------------------------------------------------------------------------------------------------------------------------

I am at a loss as to what to do - any suggestions gratefully received.

Many thanks

Doc

---

### Post by KeplerNiko on 2005-08-29
[QUOTE=Mishura]I'll get flamed for suggesting this, but why not install the AutoPackage from Gaim's website?  I'm using it right now (1.5.0) and its pretty stable.  Easy as hell to install too.  Just remember to uninstall Gaim from Synaptic before you install the autopackage.[/QUOTE]
 If I follow what you're suggesting, the reason I haven't done that (well, besides not knowing about it) is because when I try to uninstall Gaim, Synaptic also tags the "ubuntudesktop" to be removed as well.  That's not good.

However, I think I did get things resolved--initially I simply reinstalled Gaim using Synaptic PM.  That only worked temporarily, though--I was able to select the different sound outputs, but after a day or two the other options mysteriously disappeared and it went back to command or console beep.

I finally deleted the /usr/lib/gaim for 1.5.0 (or whatever it is--do a "whereis" for Gaim, and it's the one that's in /usr or ~/share something).  Restarting Gaim brought up 1.1.4, and it once again had all of the sound options available.  It seems to be stable.

I figure that newer version of programs, particularly those that can/are bundled with Ubuntu, don't play well with the old versions.  Because those programs can't be uninstalled (or maybe even modified; I'm talking about the ones that spawn the "remove ubuntudesktop" in SPM), the newer versions create their own install directories, and they don't play well with the old versions.

The solution for me was to uninstall the new version.  Fortunately Gaim hasn't added any huge new features since 1.1.4, so I'm not losing out.

---

### Post by mhearn on 2005-08-31
[QUOTE=KeplerNiko]If I follow what you're suggesting, the reason I haven't done that (well, besides not knowing about it) is because when I try to uninstall Gaim, Synaptic also tags the "ubuntudesktop" to be removed as well.  That's not good.

However, I think I did get things resolved--initially I simply reinstalled Gaim using Synaptic PM.  That only worked temporarily, though--I was able to select the different sound outputs, but after a day or two the other options mysteriously disappeared and it went back to command or console beep.

I finally deleted the /usr/lib/gaim for 1.5.0 (or whatever it is--do a "whereis" for Gaim, and it's the one that's in /usr or ~/share something).  Restarting Gaim brought up 1.1.4, and it once again had all of the sound options available.  It seems to be stable.

I figure that newer version of programs, particularly those that can/are bundled with Ubuntu, don't play well with the old versions.  Because those programs can't be uninstalled (or maybe even modified; I'm talking about the ones that spawn the "remove ubuntudesktop" in SPM), the newer versions create their own install directories, and they don't play well with the old versions.

The solution for me was to uninstall the new version.  Fortunately Gaim hasn't added any huge new features since 1.1.4, so I'm not losing out.[/QUOTE]
 It's OK to uninstall ubuntu-desktop. Just remember to put it back before upgrading to Breezy.

---

### Post by TheOrangeRider on 2005-09-25
[QUOTE=cymoril]

i want to install gaim but i keep receiving this error:

The following packages have unmet dependencies:
  gaim: Depends: gaim-data (= 1:1.4.0-1ubuntu1~5.04ubp1) but 1:1.1.4-1ubuntu4.4 is to be installed
E: Broken packages


i have updated my packages and i have the latest gaim-data.
the error above says i have 1:1.4.0-1ubuntu1~5.04ubp1 though, instead of the 1:1.1.4-1ubuntu4.4 i need?

when remove gaim-data and apt-get install it again:

Preconfiguring packages ...
Selecting previously deselected package gaim-data.
(Reading database ... 63689 files and directories currently installed.)
Unpacking gaim-data (from .../gaim-data_1%3a1.1.4-1ubuntu4.4_all.deb) ...
Setting up gaim-data (1.1.4-1ubuntu4.4) ...
[/QUOTE]

I just installed Kubuntu and have come across the same problem. Has anyone figured out how to fix this yet? Or should I just try manually installing Gaim 1.5?

---

### Post by treris on 2005-09-25
I also just used the autopackage thats available from the gaim website and then used an rpm package and alien to get the guifications installed, i did this last week somewhere and have had no problems yet, I was using kmess for a while because of the file transfer problems between gaim en msn, but kmess kept on crashing so I switched back to gaim.

---

### Post by TheOrangeRider on 2005-09-29
You know what the problem was (for me anyway)? I had backport repositories in my sources.list that seemed to be causing the problem. Once I removed them I could install gaim (and adobe) fine. I don't understand how or why having these repos would affect it, but removing them seemed to make the problem go away.

---

