---
title: "Kde 3.4.2"
date: 2005-07-28
forum: Desktop Environments
---

### Post by SpEcIeS on 2005-07-28
Just a little thought. KDE 3.4.2 is out very soon. Check out [ftp://ftp.kde.org/pub/kde/stable/3.4.2/kubuntu/](ftp://ftp.kde.org/pub/kde/stable/3.4.2/kubuntu/) :) More Security.  :grin:

---

### Post by SGC on 2005-07-28
**To update to this release:**

** Add this to your sources.list**
deb [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main

**Then:**
sudo apt-get update
sudo apt-get upgrade

---

### Post by Mishura on 2005-07-28
There's already packages for it?  *Looks at KDE.org*  They haven't announced KDE 3.4.2 yet...

---

### Post by skyboy on 2005-07-28
Just did the update, worked like a charm 
Thanks for the info

---

### Post by hammett111 on 2005-07-28
No good for AMD64

---

### Post by SGC on 2005-07-28
[QUOTE=hammett111]No good for AMD64[/QUOTE]
 Only i386 packages are available, No amd64 or ppc packages so far.

---

### Post by ykpaiha on 2005-07-28
works fine for me.
Just i had to add a sudo  apt-get install -f once
I don't know why...so
I don't see much change here, just kcontrol desepear from menu I'll work this out next.
Thanks for you usefull post.

---

### Post by Freddy on 2005-07-28
Yep, noticed that kcontrol disapered to. First after trying to upgrade, Kde libs broke but it was easy to fix it.
All those who upgrade to kde 3.4.2, Control Center can be started from the commandline with kcontrol or be put under a submenu with menu editor.

/Freddan

---

### Post by skyboy on 2005-07-28
to add kcontrol to the panel bar
panel menu -> add panel - > special button - > Preferences

---

### Post by Freddy on 2005-07-28
Yeah but that's only if you want it in your panel, that's not where it's disapeared from but for quick access that could be an idea, not for me though

/Freddan

---

### Post by ykpaiha on 2005-07-28
I mention as weel a system setting deb is it in replacement of kcontrol?
Unfortunatly this one stays in english but is now in the menu ....
The real name is kde-systemsettings
The future in on...But it nead some eye candy...it looks too much  as a wellknown krosoft pouah!

---

### Post by skyboy on 2005-07-28
then Edit KDE Menu Editor -> add new Item
name it Kcontrol and put in the field "Command" : kcontrol
, choose a nice icon and save !
Done, Kcontrol is back in KDE menu

---

### Post by vedro on 2005-07-28
ellow....

I7§ about to upgrade to KDE 3.4.2 and am wondering if I can now delete from the sources.list --> deb [http://kubuntu.org/hoary-kde341](http://kubuntu.org/hoary-kde341) hoary-updates main This is the KDE 3.4.1 update source.
And replace with the source for KDE 3.4.2?

heva a nice day,
vedro

---

### Post by Freddy on 2005-07-28
Yeah, that's the way to go for now, as you may or may not have seen I already mentioned that way in my first post, but you explaind it in more detail for those who don't know how to get it back into the menu atleast, 

To bad that you have to put it in a submenu in Kubuntu's menu, why have they taken away the option to make new head items in the Kmenu ?

/Freddan

---

### Post by skyboy on 2005-07-28
Freddy>> i have no clue :) maybe a little mistake ??

Vedro>> yes, you can remove the KDE3.4.1 rep from your sources after upgrade but if you leave it, it doesn't make any problem either. so up to you really.

---

### Post by vedro on 2005-07-28
ok..tnx..

and of I go and upgrade :)

...,
vedro

---

### Post by Paulus on 2005-07-28
it's not even on kde.org, whats going on?!

---

### Post by SGC on 2005-07-28
[QUOTE=Paulus]it's not even on kde.org, whats going on?![/QUOTE]
 It will be annouced later today , but its on kde.org:

**KDE 3.4.2 Release Announcement**
[http://kde.org/announcements/announce-3.4.2.php](http://kde.org/announcements/announce-3.4.2.php)

**KDE 3.4.2 Changelog**
[http://kde.org/announcements/changelogs/changelog3_4_1to3_4_2.php](http://kde.org/announcements/changelogs/changelog3_4_1to3_4_2.php)

---

### Post by Feanor on 2005-07-28
I've updated my system... Kcontrol disappeared I don't know why... However I can use it by kooldock and the main panel  ;-) It's better now  :grin:

---

### Post by vedro on 2005-07-28
ellow...

I have updated to and everything is working like a charm :)
I recomend the upgrade to all..there is nothing to loose...

have a nice day, 
vedro

---

### Post by Paulus on 2005-07-28
[QUOTE=SGC]It will be annouced later today , but its on kde.org:

**KDE 3.4.2 Release Announcement**
[http://kde.org/announcements/announce-3.4.2.php]("http://kde.org/announcements/announce-3.4.2.php")

**KDE 3.4.2 Changelog**
[http://kde.org/announcements/changelogs/changelog3_4_1to3_4_2.php]("http://kde.org/announcements/changelogs/changelog3_4_1to3_4_2.php")[/QUOTE]

they must have just updated, nm :grin:

---

### Post by GeneralZod on 2005-07-28
Is there a deb-src entry for apt-get? There's a bug in kdelibs that really annoys me and I like to patch it every time I upgrade, and having a deb-src is the easiest way.

---

### Post by SGC on 2005-07-28
[QUOTE=GeneralZod]Is there a deb-src entry for apt-get? There's a bug in kdelibs that really annoys me and I like to patch it every time I upgrade, and having a deb-src is the easiest way.[/QUOTE]
 I'm not sure, but isn't the deb-src usually have the same url:
```
deb-src [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main
```

If you [browse the files](ftp://ftp.kde.org/pub/kde/stable/3.4.2/kubuntu/pool/) , you will find in addition to .deb files, there are .dsc and .gz files, are those the files that you are looking for?

---

### Post by GeneralZod on 2005-07-28
[QUOTE=SGC]I'm not sure, but isn't the deb-src usually have the same url:
```
deb-src [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main
```

If you [browse the files](ftp://ftp.kde.org/pub/kde/stable/3.4.2/kubuntu/pool/) , you will find in addition to .deb files, there are .dsc and .gz files, are those the files that you are looking for?[/QUOTE]

I'm kicking myself that it didn't occur to me to try this :) That seems to do the trick; many thanks! :D

---

### Post by abandoned_hussam on 2005-07-28
I have a problem with kde 3.4.2. spellcheck does not work anymore in kopete. this used to work in kde 3.4.1 
any ideas?

---

### Post by JuanC on 2005-07-28
Upgrade to KDE 3.4.2 without problems.

No KControl in Menu , but it doesn't matter  :) 

KDE seems to be faster and more stable now , it could be also because i add backport repository and some libraries were upgraded.

Good work Kubuntu and KDE !!!!

---

### Post by Jonathan2007 on 2005-07-28
Upgrading as I speak. Download is running at the max speed for my connection. I am kind of surprised kubuntu.org isn't getting hammered. Anywho does anyone know if it fixes any major bugs or is it just speed and behind the scenes improvements?

---

### Post by cdhinch on 2005-07-28
Here another Control Center fix.  Right click on the panel -> Configure Panel -> Layout -> Menus.  Then put a check mark in the box next to Preferences.  Click OK.  You will now have a new sub-menu on the K-Menu called Preferences.  The Control Center is at the very top of that sub-menu.  You will now also have access to all the individual componants of the Control Center without opening the Control center.

Charles

---

### Post by SpEcIeS on 2005-07-28
That was a nice little tip. :) Prior to this I just made a shortcut  to kcontrol via menu edit.

---

### Post by Mishura on 2005-07-29
KDE 3.4.2 works pretty good.  :)

KControl does dissapear from K Menu, but was easily replaced.  I didn't even notice it until I read this thread further.

Question:  Does anybody notice any more Konqueror crashes when accessing a Kpart, such as KPDF or Kaffeine? (I have the "fixed" kaffeine deb)  I haven't tested this yet, but previous KDE versions did this almost all the time.

---

### Post by Feanor on 2005-07-29
There's a problem with kaffeine when opening files... When you click on any video file kaffeine doesn't play this video but it seems to load an entire playlist and plays another video file... This don't happen with all the files only with someone do this work... It works well before the upgrade to kde 3.4.2 so I guess if there a way to return to the version of kaffeine that I had before ( I took it from deb [http://dinton.no-ip.org/](http://dinton.no-ip.org/) kubuntu main repository ), or if there is a way to solve this problem.  :???:

---

### Post by SGC on 2005-07-29
[QUOTE=Feanor]There's a problem with kaffeine when opening files... When you click on any video file kaffeine doesn't play this video but it seems to load an entire playlist and plays another video file... This don't happen with all the files only with someone do this work... It works well before the upgrade to kde 3.4.2 so I guess if there a way to return to the version of kaffeine that I had before ( I took it from deb [http://dinton.no-ip.org/](http://dinton.no-ip.org/) kubuntu main repository ), or if there is a way to solve this problem.  :???:[/QUOTE]
 Kaffeine is not part of kde, so it does not updated with kde 3.4.2 , your version still the same version which you had before the update.

---

### Post by Feanor on 2005-07-29
So what can be the possible cause and solution? Kaffeine works fine just before upgrade...  :?

---

### Post by godzero on 2005-07-29
ALL video broke here.
E.G. In Kaffeine: I get the blue overlay, and xorg pegs out my cpu.

---

### Post by web250 on 2005-07-29
Upgrade worked OK for me, not as easy as 3.4.1 upgrade.

The installation messed up when installing kdelibs. Then, on reboot, X was broken. I had to revert xorg.conf to vesa settings, reinstall nvidia drivers, and then edit xorg.conf again to get my X back to normal. Not a major problem, took 5 minutes to fix, but odd none-the-less.

Kcontrol was gone, and easily replaced.

No visible problems yet.

---

### Post by godzero on 2005-07-29
Ya, I had the lib problems, and some odd font problems. Fix was easy.

Update on the video thing: They're running again... not sure what I did to fix it (arg!)... tried a few things... then *another* reboot (Crtl-Alt-Backspace didn't seem to work) and wolla (sp?), back up and running....

---

### Post by improverrr on 2005-07-29
one very minor problem i have noticed since upgrade.  Using Firefox 1.04 and "my yahoo" page with 3 columns seems to be alittle wider than the window with settings at 1024x768.  Was fine immediateley before(3.4.1) upgrade(3.42) and immediately had this issue after the upgrade.  Wierd, this seems to be the only page affected.  I dont know what kde would have to do with websites...unless it is a font issue... but really didnt notice what it was doing before.

but for what i use pc for, it is working good thus far

---

### Post by Jonathan2007 on 2005-07-30
Well I got upgraded fine. I just went into Synaptic and told it to upgrade kdebase (and its dependencies) and it worked great. And get this Kcontrol did **not** disappear. And I can play xvid movie files fine using Kaffeine.

---

### Post by geearf on 2005-07-30
Interesting, thanks.

But why is'nt there a single repos for kde/kubuntu ?
I mean, we have one for .1 now one for .2 , i just don't get it.

Thanks,

---

### Post by manicka on 2005-07-30
[QUOTE=geearf]Interesting, thanks.

But why is'nt there a single repos for kde/kubuntu ?
I mean, we have one for .1 now one for .2 , i just don't get it.

Thanks,[/QUOTE]
 I'd imagine it's because 3.4.0 is the official release version and .1 and .2 are optional addons

---

### Post by geearf on 2005-07-31
Well there could be like one 'unofficial' repos and that's it ?

---

### Post by dc2447 on 2005-07-31
I upgraded and now I'm having real problems getting to some sites using firefox.

Example: cpfc.org

I can browse it via konq but when I use firefox it starts loading the page and then hangs 'transferring data from cpfc.org' - have tried reinstalling firefox but no avail.

---

### Post by coolclassic on 2005-07-31
[QUOTE=web250]

The installation messed up when installing kdelibs.[/QUOTE]

I have upgraded to kde 3.4.2 with no problems but I have noticed that kdelibs did not install is this an issue or can I safely ignore.

---

### Post by 8FootSativa on 2005-07-31
After the upgrade Konquerer is even more unstable.  :-|

---

### Post by dc2447 on 2005-07-31
I eventually got firefox working be uninstalling and deleting by .mozilla dir.

Nightmare

---

### Post by SpEcIeS on 2005-07-31
Everything on my end works very well. The only issue I seem to have is the those annoying "Tips" dialog boxes popup, even prior select to not show them. No biggy. :)

---

### Post by Feanor on 2005-07-31
[QUOTE=coolclassic]I have upgraded to kde 3.4.2 with no problems but I have noticed that kdelibs did not install is this an issue or can I safely ignore.[/QUOTE]

You can resolve this by upgrading another time your system

for example if you do

```
sudo aptitude upgrade
```

kdelibs should be installed correctly

---

### Post by coolclassic on 2005-08-01
Oops silly me kdelibs was allready installed. Whilst browsing the sections in kynaptic >KDE Desktop Enviroment, kdelibs is not installed but on browsing Libraries kdelibs4 is installed. I would of thought these would be in the same section.

---

### Post by SpEcIeS on 2005-08-01
Here is something. On my system, due to an qt3 upgrade from sid, kdesdk will not install. In order to install kdesdk I would need to downgrade a qt3 package, which in turn would downgrade a lot of other software from sid that runs much better than the kubuntu packages, such as the other qt 3.3.4 packages, digikam and kaffeine.  Also others.

What packages do I require to recompile in order to apply kdesdk? Kdesdk is one, but do I need to recompile the kdelibs package too, because kdelibs4-dev complains about qt?  :neutral:

_Update_
The natural order of the universe has been restored. It turns out, after doing some repo searching, that I was missing the complementary libidn11-dev.   :grin:

---

### Post by GreatBunzinni on 2005-08-01
What's the deal with the way these packages are made? The dependencies are all screwed up. KDE 3.4.2 installs without problems but when the first update is made, there are a bunch of packages that are listed as must-have dependencies. 

For example, I don't want kruler. It is useless. If I try to remove kruler through kynaptic, it tells that kdegraphics lists kruler as a must-have dependency. Therefore, if I wish to remove kruler, I have to remove kdegraphics as well. What's up with that??

Because of the way the packages are made, now I have my beautifull kubuntu filled with useless packages and I have no way to remove them without breaking KDE. Who was the genius behind this brilliant move?

Oh, and KDE control center is nowhere to be found, which sucks a lot.


P.S.: there are good things as well. One of my first impressions was that the PDFs are opened incredibly fast.

---

### Post by geearf on 2005-08-01
I can't use Kplayer right now :(

I don't know where this update broke something (or not ?), but still :(

---

### Post by SpEcIeS on 2005-08-01
[QUOTE=GreatBunzinni]What's the deal with the way these packages are made? The dependencies are all screwed up. KDE 3.4.2 installs without problems but when the first update is made, there are a bunch of packages that are listed as must-have dependencies. 

For example, I don't want kruler. It is useless. If I try to remove kruler through kynaptic, it tells that kdegraphics lists kruler as a must-have dependency. Therefore, if I wish to remove kruler, I have to remove kdegraphics as well. What's up with that??

Because of the way the packages are made, now I have my beautifull kubuntu filled with useless packages and I have no way to remove them without breaking KDE. Who was the genius behind this brilliant move?

Oh, and KDE control center is nowhere to be found, which sucks a lot.


P.S.: there are good things as well. One of my first impressions was that the PDFs are opened incredibly fast.[/QUOTE]
This is one of the problems with any packaging system, dependency hell. From what I understand, gentoo is a nice lean distro that asks you what you want then compiles and installs. This takes more time, but does offer a custom install. Try a stage one install. :) Perhaps this is more in your direction.  ;-) 

Thanks to insanely large harddrives these days, I am not particularly worried about additional small packages, but having better package installs would be nice. 

Patience is in order and I believe that the people that are doing the packaging have quite a job. Cheers to them all. :)

Aside from the odd glitch, KDE 3.4.2 seems to be working very well, and the PDF's really do seem to be a lot quicker. :)

---

### Post by Latem on 2005-08-02
The way I think packages are orginized is like this:
kdegraphics (empty)
kdegraphics-common (all stuff common to kdegraphics)
kdegraphcs-appname (for each application in kdegraphics)

In actuallity kdegraphics package does not install any files, it's there just as a placeholder or something.  I know I have the same issue as you described with wanting to uninstall one kdegraphics application needs to uninstall kdegraphics package; under Mandriva too.  And if packages are orginized in a similar way (likely), there actually isn't anything in kdegraphics package other than the description and changelog.  So I think it's safe to uninstall a kdegraphics app and kdegraphics package, you can just install kdegraphics package again if you'd like.  If there is a way to check the contents of a package in Kubuntu (ie thru Synaptic maybe) it should show that there is no files in kdegraphics.  This is how it works under Mandriva, and I think it's likely how it works under Kubuntu.  My kubuntu experience is limited, and I don't have it installed any more to check this, but thought I'd post it here because I think that's how it works with KDE packages in general.

Latem

---

### Post by hod139 on 2005-08-02
Is there any estimate on when we can expect to see any amd64 packages?

---

### Post by SGC on 2005-08-02
Removing kdegraphics will not remove others applications that comes with it.

Its a meta package when you install it, it will install kruler, kfax, kpdf, kooka, etc. And when you removing it, it will removes nothing.

The same thing goes for other kde packages like kdemultimedia, kdepim, kdenetwork, etc

---

### Post by Phlod on 2005-08-09
Perhaps this is not exactly the right place to ask this, but it's related to Konqeror 3.4.2, so here goes.
I've noticed a peculiar behavior when using Konq as a file browser, when I open a folder with brackets in it [] Konq is unable to read the directory, and just takes me back the the dir I was in.  Remove the brackets, everything's fine.
Also, somewhat to do with what someone said earlier about Kaffeine loading everything in the directory when you double-click on a single movie file, mine does this now too, but again, only with movies whose filenames contain brackets.
Now, I know that brackets often denote things like ranges of numbers and the like in BASH, but Konq has never done this to me in previous versions.  However, due to my Kubuntu newbhood, I just installed when I found out KDE 3.4.2 was available.  Before I used Mandriva, and it had no such quirk, but it wasn't KDE 3.4.  However, I found no bug report on bugzilla about this, so I'm assuming it's a Kubuntu peculiarity for the time being.
Any help would be wonderful.  This is rather annoying.

--Phlod

---

### Post by drizek on 2005-08-09
[QUOTE=Phlod]Perhaps this is not exactly the right place to ask this, but it's related to Konqeror 3.4.2, so here goes.
I've noticed a peculiar behavior when using Konq as a file browser, when I open a folder with brackets in it [] Konq is unable to read the directory, and just takes me back the the dir I was in.  Remove the brackets, everything's fine.
Also, somewhat to do with what someone said earlier about Kaffeine loading everything in the directory when you double-click on a single movie file, mine does this now too, but again, only with movies whose filenames contain brackets.
Now, I know that brackets often denote things like ranges of numbers and the like in BASH, but Konq has never done this to me in previous versions.  However, due to my Kubuntu newbhood, I just installed when I found out KDE 3.4.2 was available.  Before I used Mandriva, and it had no such quirk, but it wasn't KDE 3.4.  However, I found no bug report on bugzilla about this, so I'm assuming it's a Kubuntu peculiarity for the time being.
Any help would be wonderful.  This is rather annoying.

--Phlod[/QUOTE]
 this was asked before in another thread.

you have to add a / at the end of the address to get it to work

ex: /home/phlod/crap[]

wont work, you need to type in

/home/phlod/crap[]/

---

### Post by Phlod on 2005-08-09
Sorry about re-asking a question, but I couldn't find anything when I searched the forum archives.
However, how do I type in the '/' when I'm using it in Filebrowser mode, and just pointing and clicking?  I can cd between bracketed directories in Konsole just fine.

--Phlod

---

### Post by drizek on 2005-08-09
[QUOTE=Phlod]Sorry about re-asking a question, but I couldn't find anything when I searched the forum archives.
However, how do I type in the '/' when I'm using it in Filebrowser mode, and just pointing and clicking?  I can cd between bracketed directories in Konsole just fine.

--Phlod[/QUOTE]
 click the folder, get an error, add the / it in, hit enter

---

### Post by sc0rpi0n on 2005-08-13
[QUOTE=SGC]**To update to this release:**

** Add this to your sources.list**
deb [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main

**Then:**
sudo apt-get update
sudo apt-get upgrade[/QUOTE]


hi all. i'm a newcomer. I've performed these commands but i'm not able to upgrade kde. when i do "apt-upgrade" it says that there are 0 updates. How can i resolve? Tnx

---

### Post by manicka on 2005-08-13
[QUOTE=sc0rpi0n]hi all. i'm a newcomer. I've performed these commands but i'm not able to upgrade kde. when i do "apt-upgrade" it says that there are 0 updates. How can i resolve? Tnx[/QUOTE]
 If you start synaptic or the Ubuntu Update Manager, are there any updates available?

Could you post your sources.list?

---

### Post by sc0rpi0n on 2005-08-13
[QUOTE=manicka]If you start synaptic or the Ubuntu Update Manager, are there any updates available?

Could you post your sources.list?[/QUOTE]


Kynaptic says that my system is up to date. This is my sources.list:


# [EDIT_ME] : If you're using an i386 machine, then replace line below with
# your original "deb cdrom:" line.
#deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release amd64 (20050407)]/ hoary main restricted

# ======================= Official repositories ========================
# [EDIT_ME] : Replace the "tr"s with your original country code.
deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) hoary-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe multiverse

deb [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main

# Official source repos. Dead weight for non-developers.
# deb-src [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
# deb-src [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) hoary-updates main restricted universe multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe multiverse
# ======================================================================

# Unofficial repositories below, till end of file.

# For both amd64 and i386
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main

# For amd64 Only
# [EDIT_ME] : For an i386 machine, comment out the two lines below.
#deb [ftp://ftp.berlios.de/pub/kudos/hoary](ftp://ftp.berlios.de/pub/kudos/hoary) /
#deb [http://cyberspace.ucla.edu/marillat](http://cyberspace.ucla.edu/marillat) unstable main

# For i386 Only
# [EDIT_ME] : For an i386 machine, uncomment the line below.
deb [ftp://ftp.berlios.de/pub/gift-fasttrack](ftp://ftp.berlios.de/pub/gift-fasttrack) unstable main


# ================== Ubuntu Backports Project Mirrors ==================
# [EDIT_ME] : Uncomment only one of the "deb" lines below (geographically
# closest one to you). Uncomment none, if you don't want packages from UBP.
# (Get current mirrors list from [http://backports.ubuntuforums.org/url.php](http://backports.ubuntuforums.org/url.php))
#
# AU Australia:
# deb [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) hoary-extras main universe multiverse restricted
# ES Spain:
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted
# US United States, Minnesota:
# deb [http://acm.cs.umn.edu/ubp/](http://acm.cs.umn.edu/ubp/) hoary-extras main universe multiverse restricted
# US United States, Texas:
# deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
#======================================================================

# ======================= Blackdown Java Mirrors =======================
# [EDIT_ME] : Uncomment only one of the "deb" lines below (the one
# geographically closest to you). Uncomment none, if you don't need Java.
# Get current mirrors from [http://www.blackdown.org/java-linux/java-linux-d2.html](http://www.blackdown.org/java-linux/java-linux-d2.html)
#
# AT Austria:
# deb [ftp://gd.tuwien.ac.at/opsys/linux/java/debian](ftp://gd.tuwien.ac.at/opsys/linux/java/debian) sarge non-free
# AU Australia:
# deb [ftp://mirror.aarnet.edu.au/pub/java-linux/debian](ftp://mirror.aarnet.edu.au/pub/java-linux/debian) sarge non-free
# BE Belgium:
# deb [http://ftp2.skynet.be/pub/ftp.blackdown.org/debian](http://ftp2.skynet.be/pub/ftp.blackdown.org/debian) sarge non-free
# CH Switzerland:
# deb [ftp://mirror.switch.ch/mirror/java-linux/debian](ftp://mirror.switch.ch/mirror/java-linux/debian) sarge non-free
# DE Germany, Berlin:
# deb [ftp://ftp.informatik.hu-berlin.de/pub/Java/Linux/debian](ftp://ftp.informatik.hu-berlin.de/pub/Java/Linux/debian) sarge non-free
# DE Germany, Goettingen:
# deb [ftp://ftp.gwdg.de/pub/languages/java/linux/debian](ftp://ftp.gwdg.de/pub/languages/java/linux/debian) sarge non-free
# DK Denmark:
# deb [ftp://sunsite.dk/mirrors/java-linux/debian](ftp://sunsite.dk/mirrors/java-linux/debian) sarge non-free
# ES Spain:
# deb [ftp://ftp.cica.es/pub/java-linux/debian](ftp://ftp.cica.es/pub/java-linux/debian) sarge non-free
# FR France:
# deb [ftp://ftp.oleane.net/pub/java-linux/debian](ftp://ftp.oleane.net/pub/java-linux/debian) sarge non-free
# HU Hungary:
# deb [ftp://xenia.sote.hu/pub/mirrors/java.blackdown.org/debian](ftp://xenia.sote.hu/pub/mirrors/java.blackdown.org/debian) sarge non-free
# IT Italy:
#deb [http://mirrors.publicshout.org/java-linux/debian](http://mirrors.publicshout.org/java-linux/debian) sarge non-free
# UK United Kingdom:
deb [ftp://ftp.mirrorservice.org/sites/ftp.blackdown.org/java-linux/debian](ftp://ftp.mirrorservice.org/sites/ftp.blackdown.org/java-linux/debian) sarge non-free
# US United States, New Jersey:
# deb [ftp://ftp.tux.org/pub/java/debian](ftp://ftp.tux.org/pub/java/debian) sarge non-free
# US United States, North Carolina:
# deb [ftp://metalab.unc.edu/pub/linux/devel/lang/java/blackdown.org/debian](ftp://metalab.unc.edu/pub/linux/devel/lang/java/blackdown.org/debian) sarge non-free
#======================================================================
# FYI: Other Blackdown mirrors; known to be broken; don't use them...
# BE (no amd64)		[ftp://ftp.easynet.be/blackdown/](ftp://ftp.easynet.be/blackdown/)
# FI (site empty)	[ftp://ftp.funet.fi/pub/Linux/java/jdk/](ftp://ftp.funet.fi/pub/Linux/java/jdk/)
# NL (can't enter)	[ftp://ftp.nluug.nl/pub/os/Linux/java/jdk/](ftp://ftp.nluug.nl/pub/os/Linux/java/jdk/)
# RO (site missing)	[ftp://archive.logicnet.ro/mirrors/ftp.tux.org/](ftp://archive.logicnet.ro/mirrors/ftp.tux.org/)
# UK (no amd64)		[ftp://ftp.uk.linux.org/pub/linux/java/](ftp://ftp.uk.linux.org/pub/linux/java/)

---

### Post by manicka on 2005-08-13
Everything looks okay.

I'm stumped, :-k  anyone else?

As a side note I'd also suggest using synaptic instead of kynaptic. Synaptic has more features and functionality

---

### Post by johe07 on 2005-08-13
[QUOTE=sc0rpi0n]hi all. i'm a newcomer. I've performed these commands but i'm not able to upgrade kde. when i do "apt-upgrade" it says that there are 0 updates. How can i resolve? Tnx[/QUOTE]

I also not success!! what link should I put in the source list?? I'm now just finished install my ubuntu, using GNome...

---

### Post by AndyAWS on 2005-08-13
```
deb [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main
deb [http://kubuntu.org/hoary-kde341](http://kubuntu.org/hoary-kde341) hoary-updates main
```

That's from my sources.list, however the 341 repo is probably no longer required.
When I added the 342 repo everything updated.

Anyone having trouble make sure that you do "sudo apt-get update" after editing your sources.list, before "apt-get upgrade" ... or just use 'reload' in synaptic.

---

### Post by johe07 on 2005-08-13
[QUOTE=AndyAWS]```
deb [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main
deb [http://kubuntu.org/hoary-kde341](http://kubuntu.org/hoary-kde341) hoary-updates main
```

That's from my sources.list, however the 341 repo is probably no longer required.
When I added the 342 repo everything updated.

Anyone having trouble make sure that you do "sudo apt-get update" after editing your sources.list, before "apt-get upgrade" ... or just use 'reload' in synaptic.[/QUOTE]
 yes, i had put the exactly same as your source list, but it stil failed..
I did update and upgrade the hoary....

---

### Post by yongyi on 2005-08-14
I use breezy's source,but KDE package is not all 3.4.2:
>  kdebase: Depends: ksysguard (>= 4:3.4.1-0ubuntu4)  

Is there any KDE3.4.2 source for breezy ? Thanks!

---

### Post by SpEcIeS on 2005-08-14
[QUOTE=johe07]yes, i had put the exactly same as your source list, but it stil failed..
I did update and upgrade the hoary....[/QUOTE]
For binaries and source, use the following:
```

deb ftp://ftp.kde.org/pub/kde/stable/3.4.2/kubuntu hoary-updates main
deb-src ftp://ftp.kde.org/pub/kde/stable/3.4.2/kubuntu hoary-updates main
```
This has always worked for me. :)

---

### Post by Michael_Valentine on 2005-08-15
Any idea if this will work with other Debian based Distros such as Libranet?  :)

---

### Post by hod139 on 2005-08-22
Still wondering when we can expect to see kde 3.4.2 for AMD64.  The cervisia package is broken in 3.4.1, and the solution I got was "Please use the KDE 3.4.2 packages".

---

### Post by Jeezis on 2005-09-04
added those to my sources.list and i'm updating now, i <3 kubuntu!

---

### Post by mlomker on 2005-09-05
[QUOTE=hod139]Still wondering when we can expect to see kde 3.4.2 for AMD64.  The cervisia package is broken in 3.4.1, and the solution I got was "Please use the KDE 3.4.2 packages".[/QUOTE]

If you're a little daring you could always download a daily build of Breezy.  Betas are betas, though...you might fix one thing and break another.  I'm downloading a copy right now, myself, for AMD64.

[Kubuntu Breezy Dailies](http://cdimage.ubuntu.com/cdimage/kubuntu/daily/current/)

---

### Post by Brandon Hoult on 2005-09-10
Just updated to 3.4.2 and for some reason konqueror cannot connect to anything anymore.  HTTP FTP SFTP, nothing seems to work, but can browse my local filesystem fine.  I am not sure if it is related but the kde components-->service manager also does not work.  It just locks up the same as konqueror.  

Any ideas?

---

### Post by Brandon Hoult on 2005-09-10
[QUOTE=Brandon Hoult]Just updated to 3.4.2 and for some reason konqueror cannot connect to anything anymore.  HTTP FTP SFTP, nothing seems to work, but can browse my local filesystem fine.  I am not sure if it is related but the kde components-->service manager also does not work.  It just locks up the same as konqueror.  

Any ideas?[/QUOTE]
 Well, I seem to have fixed my problem, I uninstalled all of kde, removed the 3.4.2 repositories from my apt/sources.list and tried to install kde again.  This did not work, it wanted to install the 3.4.2 stuff again and had a bunch of broken dependencies.  Does anyone know why this did not work?
  So I put the 3.4.2 stuff back, and installed again.  It downloaded konq-plugins (which was not in my apt cache for some reason) and then installed kde again.  Now it seems to work..

---

### Post by snowjunkie on 2005-09-12
Guys I just installed the kde desktop using apt-get install kubuntu-desktop.  Then I used synaptic (yes, gnome synaptic) to remove all gnome packages.  This seemed to work great.

Now I'm trying to do the upgrade to 3.4.2. as suggested here.  Obviously gedit won't work for me, but kate doesn't work either.  I get the following error message.

alastair@ubuntu:~$ sudo kate /etc/apt/sources.list
Error: "/var/tmp/kdecache-alastair" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
kate: ERROR: Communication problem with kate, it probably crashed.

Hope someone can help!

---

### Post by Freddy on 2005-09-12
Kate has some problem when being used with root, there are some alternatives like Kedit and Kwrite. Kwrite I think you already have in your setup and Kedit is in your repos. /// Freddan

---

### Post by snowjunkie on 2005-09-13
I updated to kde 3.4.2 and rebooted and kate now works fine.

---

### Post by skoal on 2005-09-13
One thing I noticed strange about this upgrade procedure to KDE 3.4.2:

After enabling the repo's, 

If you do 'apt-get upgrade', you pull in some ~120MB of files and it omits like 5 KDE related packages.  If you do 'apt-get kde' instead, it only pulls in ~90MB but grabs all the KDE packages.  I really don't have a clue why that is.  So, I just did the upgrade first, then the 'apt-get kde' and all seems to work flawlessly.  None of those missing menu options like some mentioned...

\\//_

---

### Post by snowjunkie on 2005-09-14
I haven't used the apt-get kde but everything seems to be fine.  I wouldn't know if anything was missing anyway as I've only started to use KDE.  I do think the control panel is missing of the menu like some people have said.  This can be started from the terminal though (kcontrol).  I might try what you suggest to see if it fixes this.

Thanks!

---

### Post by snowjunkie on 2005-09-14
[QUOTE=skoal]If you do 'apt-get upgrade', you pull in some ~120MB of files and it omits like 5 KDE related packages.  If you do 'apt-get kde' instead, it only pulls in ~90MB but grabs all the KDE packages.[/QUOTE]

I think you meant apt-get install kde.  I've just tried it and it wanted to download 120MB/123MB... I'm kind of hoping this doesn't break anything now.

---

### Post by snowjunkie on 2005-09-15
Just to let you know.  It worked ok.  It installed a LOAD of kde applications that I didn't have already.  Excellent!

---

### Post by fanoodlehey on 2005-09-15
I installed KDE 3.4.2 and everything seemed to go ok until I rebooted. 

Now I just get a command prompt and have no desktop. I tried sudo /etc/init.d/kdm start but it was already running. I even stopped and started it and it looked like it started up but still no desktop. 

Any ideas?

---

### Post by snowjunkie on 2005-09-15
Could be your graphics setup... I seen another post on the forums somewhere that suggested removing the 3d nvidia settings from your x windows config file and then trying... 

have a search through the group or wait til someone else responds before following my suggestions... I'm only new to ubuntu.

---

### Post by fanoodlehey on 2005-09-15
The nvidia screen flashes up on the monitor before I get the command prompt if this is any help.

---

### Post by fanoodlehey on 2005-09-15
I think this is the thread you are talking about.
[http://ubuntuforums.org/showthread.php?t=65259](http://ubuntuforums.org/showthread.php?t=65259)
I'll try editing the xorg.conf file. Can't hurt too much.
Then maybe try to reinstall kde-desktop if that doesn't work.

---

### Post by snowjunkie on 2005-09-15
See this one as well...
[http://ubuntuforums.org/showthread.php?t=57888&highlight=KDE+nvidia](http://ubuntuforums.org/showthread.php?t=57888&highlight=KDE+nvidia)

---

### Post by fanoodlehey on 2005-09-15
Spot on. I only use kubuntu on my home pc so I'll have to wait to give it a shot this evening.

---

### Post by geearf on 2005-09-15
maybe startx will give you an error message ?

---

### Post by fanoodlehey on 2005-09-15
Yes, turns out it was the nvidia driver. I set "nvidia" to "vesa" in /etc/X11/xorg.conf and did startx. That gave me access to kde and I downloaded NVIDIA-Linux-x86-1.0-7676-pkg1.run. I installed that as per the nvidia driver instructions in the howto forum. Then I set "vesa" back to "nvidia" and rebooted. Looks to have worked.

Is there anywhere I should write a bug report on this? KDE? Nvidia? Kubuntu?

---

