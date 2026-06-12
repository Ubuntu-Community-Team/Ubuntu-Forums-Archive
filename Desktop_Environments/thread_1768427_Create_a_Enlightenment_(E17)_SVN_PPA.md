---
title: "Create a Enlightenment (E17) SVN PPA?"
date: 2011-05-26
forum: Desktop Environments
---

### Post by merlwiz79 on 2011-05-26
**Update: [COLOR="Red"]( 32bit and 64bit packages)[/COLOR]**> Can't seem to update without the Profiles wizard crashing.
Will try again later this week to update the packages.
[http://launchpad.net/~merlwiz79/+archive/e17-svn](http://launchpad.net/~merlwiz79/+archive/e17-svn)
**Repo: (Ubuntu 11.04)**
ppa:merlwiz79/e17-svn
Or
```
deb http://ppa.launchpad.net/merlwiz79/e17-svn/ubuntu natty main 
deb-src http://ppa.launchpad.net/merlwiz79/e17-svn/ubuntu natty main 
```
I am thinking about creating a PPA of the E17 svn.
I have already made some of the main packages.
I only seem to have a few problems with it.
I get an error that says that the evas xpm loader is missing.
I also can't find the elementary weather module.
Other that that It seems to run fine.

I want to package most of the svn as I can.
I would update the packages as much as I have time for.
This wouldn't be for creating a distro from as it would have bugs.
Also I'll be moving in a few months so there will be a month or more without updates.

Anyone interested in this?

Current screenshot of E17 on Xubuntu 11.04:
[[img]http://i.imgur.com/xBiP1l.jpg[/img]](http://i.imgur.com/xBiP1.png)

---

### Post by Bonster on 2011-05-27
Looks interesting, go ahead do it =)

---

### Post by Frogs Hair on 2011-05-27
I wanted to try E17 on 10.10 , but was afraid to break my installation . It would be great if they would finish it and have a stable release.

---

### Post by gtpitch on 2011-05-27
Isn't bodhi linux just ubuntu with enlightenment?

---

### Post by merlwiz79 on 2011-05-28
> **gtpitch said:**
> Isn't bodhi linux just ubuntu with enlightenment?

Yea it's on Lucid.
This is on Natty.

---

### Post by NormanFLinux on 2011-05-28
There is an e17 project on Sourceforge with Natty. But the DVD appears to be broken due to a mismatch in the hash. After you download 1 GB and burn it to a USB stick, you discover it won't boot.

Good luck on creating an up to date e17 distro with the latest e17 build.

---

### Post by Frogs Hair on 2011-05-28
> **gtpitch said:**
> Isn't bodhi linux just ubuntu with enlightenment?

Yes , but there is only 32 bit.

---

### Post by beastrace91 on 2011-05-28
> **gtpitch said:**
> Isn't bodhi linux just ubuntu with enlightenment?

Little bit more than that - we build a good deal more than just Enlightenment. Plus for being based on Lucid a good deal of our packages are current. For instance the latest version of Bodhi ships with the 2.6.39 kernel.

That being said - not sure on your evas error, but the weather module you are looking for is called "forecasts"

~Jeff

---

### Post by merlwiz79 on 2011-05-28
> **beastrace91 said:**
> Little bit more than that - we build a good deal more than just Enlightenment. Plus for being based on Lucid a good deal of our packages are current. For instance the latest version of Bodhi ships with the 2.6.39 kernel.

That being said - not sure on your evas error, but the weather module you are looking for is called "forecasts"

~Jeff
Not sure either evas xpm loader is enable and the package compiles without errors. 
Here is the error in ~/.xsessions-errors:```
sh: evas_image_loader.xpm: not found
```None of the icons that are xpm are shown.

I forgot to compile libeweather.
Once I made that package it worked.
I've compiled more than the standard debian packages.
Working on the extra emodules.

The Bodhi ephoto app doesn't work.
It has the same problem mine does.
Do you upload your source packages any where?
Some of your emodules aren't in the svn.

---

### Post by beastrace91 on 2011-05-28
Oh look at that - ephoto is broken at the moment. Will have to look into that issue >.<

Which modules? Pretty much all our stuff comes from the E svn.

~Jeff

---

### Post by merlwiz79 on 2011-05-28
> **beastrace91 said:**
> Oh look at that - ephoto is broken at the moment. Will have to look into that issue >.<

Which modules? Pretty much all our stuff comes from the E svn.

~Jeff

Here are some packages not in the svn.
bodhi-close
bodhi-profiles
bodhi-quickstart (interested how this works)
bodhi-shutdown

---

### Post by beastrace91 on 2011-05-31
bodhi-profiles and bodhi-quickstart are just data. The profiles you select from at login and our quick start guide to help uses find their way around E17.

I'll see if I can find the source code for those other two. My build system lost its storage drive to failure earlier this month >.<

~Jeff

---

### Post by seanbw on 2011-05-31
I have Bodhi and I do like it but my difficulty at the moment is this:
I have decided to stay with Ubuntu but my next upgrade will be a fresh installation of the natty AMD64 and after looking at Gnome, KDE and E17 (which I got from Macpup and PCLnux - I think), I decided my ideal distro will be Ubuntu AMD64 with the E17 desktop and the reason I like Ubuntu is the regular updates and the consistency of the community support.
I did look at Mint and liked but overall,Ubuntu wins because of the consistency of production and support.
So I will definitely be supportive of an E17 PPA so please go ahead if you can. I love the desktop and combined with Ubuntu - its the bees knees for me.

---

### Post by merlwiz79 on 2011-05-31
Started work on real packages for the PPA today.
It's taking a long time to make sure everything's correct and built in the correct order.
It's being built for i386 and amd64.
I'll post a link to the PPA when I have enough packages built for Enlightenment to run.

---

### Post by merlwiz79 on 2011-06-01
I kind of went crazy and was up until 3AM working on packages and patches.
I can't stop seeing the code I was looking at yesterday. :shock:
I'll start working on it again after dinner.

I still have a problem with the elementary xpm icons not showing.
I still get the error sh: evas_image_loader.xpm: not found
I guess just use an icon them that doesn't use xpms.

---

### Post by merlwiz79 on 2011-06-02
I just uploaded enlightenment and elementary to be built on my PPA.
They aren't even showing and they were uploaded successfully.
Once they get built I'll build the emodules-extras and post the link.
It's 2:42AM so I'm off to bed and will work on it later today.

Once these packages are built you'll be able to run the svn of e17.

[b]
Edit:[/b] Darn the e17 package was rejected.
```
Rejected:
dpkg-source failed for e17_0.16.999.59859-1.dsc [return: 9]
[dpkg-source output:   dpkg-source: info: extracting e17 in e17-0.16.999.59859
 dpkg-source: info: unpacking e17_0.16.999.59859.orig.tar.gz
 dpkg-source: info: unpacking e17_0.16.999.59859-1.debian.tar.gz
 dpkg-source: info: applying 01_menu_extra_path.patch
 dpkg-source: info: applying 02_upgrade_notice.diff]
```

---

### Post by merlwiz79 on 2011-06-02
Fixed the patch so it doesn't cause the package to be rejected.
It's currently compiling on my PPA.

---

### Post by merlwiz79 on 2011-06-02
Well It's missing the extra emodules but you should be able to run the base e17.
I still have a few packages to do before they can be compiled.
This will probably take several hours to do.
[http://launchpad.net/~merlwiz79/+archive/e17-svn](http://launchpad.net/~merlwiz79/+archive/e17-svn)
**Repo: (Ubuntu 11.04)**
ppa:merlwiz79/e17-svn
Or
```
deb http://ppa.launchpad.net/merlwiz79/e17-svn/ubuntu natty main 
deb-src http://ppa.launchpad.net/merlwiz79/e17-svn/ubuntu natty main 
```

---

### Post by Frogs Hair on 2011-06-02
> **merlwiz79 said:**
> Well It's missing the extra emodules but you should be able to run the base e17.
I still have a few packages to do before they can be compiled.
This will probably take several hours to do.
[http://launchpad.net/~merlwiz79/+archive/e17-svn](http://launchpad.net/~merlwiz79/+archive/e17-svn)
**Repo: (Ubuntu 11.04)**
ppa:merlwiz79/e17-svn
Or
```
deb http://ppa.launchpad.net/merlwiz79/e17-svn/ubuntu natty main 
deb-src http://ppa.launchpad.net/merlwiz79/e17-svn/ubuntu natty main 
```

Will this be available for 32 or 64 bit or both ?

---

### Post by merlwiz79 on 2011-06-02
> **Frogs Hair said:**
> Will this be available for 32 or 64 bit or both ?

It's for both but I've only used the i386(32bit) packages.

---

### Post by merlwiz79 on 2011-06-02
Ok the extra emodules have been built on my PPA.
If you want to use Network Manager don't install emodules-all.
I also took the OpenOffice.org Quick Start emodule and rewrote it for LibreOffice.
[[img]http://i.imgur.com/Rlwwtl.jpg[/img]](http://i.imgur.com/Rlwwt.png)
[http://launchpad.net/~merlwiz79/+archive/e17-svn](http://launchpad.net/~merlwiz79/+archive/e17-svn)
**Repo: **(Ubuntu 11.04 or Linux Mint 11)
```
deb http://ppa.launchpad.net/merlwiz79/e17-svn/ubuntu natty main 
deb-src http://ppa.launchpad.net/merlwiz79/e17-svn/ubuntu natty main 
```

---

### Post by Silent Warrior on 2011-06-03
Happy day! Hope you keep this going.

---

### Post by merlwiz79 on 2011-06-03
> **Silent Warrior said:**
> Happy day! Hope you keep this going.

I plan on making even more packages and will try to keep it updated.
I'm not going to update it too much as that'll cause major bandwidth usage.

I just installed it on my PC and found that only VirtualBox had this error.```
sh: evas_image_loader.xpm: not found
```

---

### Post by merlwiz79 on 2011-06-04
Fixed some packages in the PPA.

Here's how my desktop looks now.
[[IMG]http://i.imgur.com/zpa86l.jpg[/IMG]]("http://i.imgur.com/zpa86.jpg")

---

### Post by wlake on 2011-06-06
Merlwiz79, my desktop so far using your PPA on Mint 11. Thanks.

[ATTACH]194381[/ATTACH]

---

### Post by merlwiz79 on 2011-06-06
> **wlake said:**
> Merlwiz79, my desktop so far using your PPA on Mint 11. Thanks.

[ATTACH]194381[/ATTACH]
Nice themes.
Glad you got it working.
I like the Bodhi themes and thought of making them into packages.
Also was thinking of making some of the[ popular ones]("http://e17-stuff.org/index.php?xsortmode=high&page=0&xcontentmode=39x7000x7010x7020x7030x7040x7041x7050x7060x7070x7080x7090x7100x7110x7120x7130x7140x7150x7200x7210") into packages as well.

I'm thinking I need to make a meta package called e17-desktop or something.
This way it installs most of what you need without problems.
Also probably need to remove exalt from the extras-all package so people can still use gnome network manager.
Exalt just doesn't have enough options.

---

### Post by wlake on 2011-06-07
> **merlwiz79 said:**
> Nice themes.
Glad you got it working.
I like the Bodhi themes and thought of making them into packages.
Also was thinking of making some of the[ popular ones]("http://e17-stuff.org/index.php?xsortmode=high&page=0&xcontentmode=39x7000x7010x7020x7030x7040x7041x7050x7060x7070x7080x7090x7100x7110x7120x7130x7140x7150x7200x7210") into packages as well.

I'm thinking I need to make a meta package called e17-desktop or something.
This way it installs most of what you need without problems.
Also probably need to remove exalt from the extras-all package so people can still use gnome network manager.
Exalt just doesn't have enough options.

I'm using network manager. Didn't have too much trouble to get it working. It seemed to work OK after I added a systray to the shelf. Before I couldn't see nm-applet.

I'm still finding my way around E17. It is very fast. I hope you can keep this up. The easier it is for people to install themes, etc., the more likely they are to try it.
Regards,

---

### Post by merlwiz79 on 2011-06-09
Added emodule-trash to the PPA.
I patched it to get use exo-utils.
This allows you to actually use the file manager you want.
I've tested with PCManFM, Thunar and Nautilus.
Just open Preferred Applications and select the file manager you want.

---

### Post by stanks on 2011-07-11
so how often you will update?

---

### Post by moonliter on 2011-07-12
good replacment from unity
thanks for your work, please keep it up

---

### Post by Frogs Hair on 2011-08-04
I started with core packages from the software center and then  to added the ppa sources . After a partial upgrade due to a missing package I had many errors . I deleted everything and reinstalled the core packages. I will be sticking to those for the now .:popcorn:

---

### Post by stanca on 2011-08-08
You're doing a very good job Merlwiz79.:D I missed the ecomorph effects for some time and now I'm enjoying them again thanks to you.Keep it up!:P
 My E17 desktop:

---

### Post by Frogs Hair on 2011-08-09
Success ! 

I'm using my own settings at the moment , but I was able to install an apply themes finally .

---

### Post by alelondon on 2011-08-14
gracias! anyone tried it on debian?

---

### Post by Frogs Hair on 2011-08-15
> **alelondon said:**
> gracias! anyone tried it on debian?

I don't know if the PPA will work with debian , but you can check at the link.[http://debe17.com/](http://debe17.com/)

---

### Post by merlwiz79 on 2011-08-18
Sorry if it seems like there haven't  been any updates.
I've been trying to update for a few days but the config wizard keeps crashing.
It also shows no real errors and will run after it crashes.
After it crashes it selects the wrong settings(not the default settings).
I'll try again later tonight.

---

### Post by Pirate Zoro on 2011-08-19
looks awesome :D installing as we speak, going to try it out for a week and see how it goes

---

### Post by murataht on 2011-09-04
Have not tried yet, but seems promising. Thanks.

---

### Post by merlwiz79 on 2011-09-18
I'm slowly updating the PPA with the latest svn downloads from yesterday.
The wizard seems to be broken since they changed it and forced [ConnMan]("http://connman.net/") to be used by default no matter what.
Not sure if anyone would use ConnMan as it's probably missing features that Network Manager has.
ConnMan can't be installed with Network Manager or Wicd which is what a lot of people use.
Which you can enable in Startup apps.
It has always been disabled in the Debian packages so I built a patch to remove it from being compiled and loaded.
I then had the wizard skip it.
It also has a lot of configurations skipped by default and won't show when set to display them.(menu select, ibar, extra desktop files, default icon theme, battery, cpufreq, temperature, backlight, mixer, composition, favorites and desktop links)
I have setup a default config install for ibar if you use the wizard.
I tried to add default settings for the desktop links and fileman favorites but that one doesn't seem to want to copy the files.
I also forced the profiles to select the menu I created for Enlightenment since the wizard didn't select it like it was suppose to.

The Wizard is only run on 1st login or if you select it to in profiles.
All settings can be fixed through Enlightenment settings.

---

### Post by Blasphemist on 2011-09-18
I've done 2 things. First, bodhi 1.2 released this week and I love it. My screen shot here is a very slightly tweaked lappy profile and bodhi site downloaded theme. 

I also installed E17 to my oneiric sand box but it will take a lot of work to do what is easy with bodhi.

My recommendation, start with bodhi and get good with E17. Then work on doing it on oneiric or something else. Bodhi still gives you much to customize and you can make it easy or very personal and detailed.

I'm just a user that has found a ubuntu related spin that I like much.

---

### Post by Frogs Hair on 2011-09-19
> My recommendation, start with bodhi and get good with E17. Then work on doing it on oneiric or something else. Bodhi still gives you much to customize and you can make it easy or very personal and detailed.

I looked into Bodhi (10.04 Based) before installing the core packages from the software center . I have no interest in triple booting , so the core packages or PPA work the best for me . I do like using E17 from time to time , but who knows when it will be finished . That makes it hard for me to consider it as a contender for longterm use .

---

### Post by janosimas on 2011-10-03
******************
Update:
I reinstalled my system and this e17, everything is working fine. I have no idea of what happened before.

******************



Hi,
I installed this e17 and I'm having a really bad experience :-/

I was using the e17 package from the repository and upgraded to this version. When I first started enlightenment after this there was a lot of errors of modules that I assumed was because differences of the versions but...

small problem:
engage and "start everything aspell" give some error of date of configuration.

medium problem:
- I cant access my configuration dialogs that need root access like: "advanced settings" in "user and groups"
- Chrome doesn't know anymore with what programs it open files like downloaded pdf


BIG problem:
no sound, somehow after this upgrade I'm out of the groups pulse and pulse-access. I'm not sure what more may have happened and including my user in these groups does not solve the problem.


All of these problem also occur in ubuntu classic (gnome) except my configuration setting that work just fine.


anyway, everything else worked just fine, a lot better than the old package. I'm glad someone did this ppa. :-D

---

### Post by Meizirkki on 2011-10-21
Thank you so much for this repository merlwiz79!

packages.enlightenment.org is horribly outdated, bodhi has no 64-bit packages (and I can't find their sources..?), plus I've been getting odd build error with easy_e17 script ever since upgrading to 11.10

You saved me from lot of trouble, thanks :) :guitar:

---

### Post by rojaasensei on 2011-11-05
I'm confused.  I would like to try enlightenment.

Do I install the e17 package from the software centre first and then install the packages from the ppa?

I ask as there seems to be no "desktop" in the ppa.

---

### Post by Frogs Hair on 2011-11-05
> **rojaasensei said:**
> I'm confused.  I would like to try enlightenment.

Do I install the e17 package from the software centre first and then install the packages from the ppa?

I ask as there seems to be no "desktop" in the ppa.

Either one or the other , the PPA will give you a better E17 experience . The core packages in the software center will give you an idea of what E17 is like and are easy to remove .

I don't know if the PPA in this thread is still active so check it out first . There is an active PPA .```
sudo add-apt-repository ppa:hannes-janetzek/enlightenment-svn
sudo apt-get update
sudo apt-get install e17

``` 

If you have the resources and time try this out .[http://bodhilinux.com/](http://bodhilinux.com/)

---

### Post by rojaasensei on 2011-11-06
Thank you.
I did look into Bodhi, downloaded the ISO.

Found out with the live CD and the forum that my Broadband (Broadcom) isn't very compatible

---

### Post by plaid on 2012-02-01
Thanks for doing this Merlwiz.  I've been using Enlightenment since I discovered it on my very first Slackware distro a decade ago and it has been a pain to keep Enlightenment up to date.

---

### Post by plaid on 2012-02-02
hmm.. I installed your packages and tried starting enlightenment, but my system hangs with no output, so I have to log into a virtual terminal and kill enlightenment.  I'm going to compile my own enlightenment now and see if that works.
-- Plaid

---

### Post by Tux Aubrey on 2012-04-28
> I don't know if the PPA in this thread is still active so check it out first . There is an active PPA .
```
Code:
sudo add-apt-repository ppa:hannes-janetzek/enlightenment-svn
sudo apt-get update
sudo apt-get install e17
```

Is anyone else using the hannes-janetzek ppa?  I have it working fine on 11.10, apart from some of the module updates being a day or so behind the core API.

It has not worked for me at all on 12.04 yet.

Anyone with different experiences?  The hannes-janetzek ppa does not seem to be supported online anywhere and it might be worth opening a thread for it here if there is interest.

---

