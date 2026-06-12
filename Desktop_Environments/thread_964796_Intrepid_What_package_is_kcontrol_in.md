---
title: "Intrepid: What package is kcontrol in?"
date: 2008-10-31
forum: Desktop Environments
---

### Post by djvishnu on 2008-10-31
I use gnome, and used to skin my kde3 apps with kcontrol. Does anyone know what application i can use to do the same in Intrepid?

---

### Post by Zyrshnikashnu on 2008-10-31
Yes, I'd also like to know where to find the KDE control panel these days.

---

### Post by mgol on 2008-11-01
Me too... I can't stand those huge fonts in Amarok, and I'd like Amarok and Krusader to use Ubuntu colors, this blue over orange looks really weird.

```

$ sudo apt-get install kcontrol
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kcontrol is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  kdelibs4c2a kdebase-workspace-bin
E: Package kcontrol has no installation candidate

```

I have kdelibs4c2a, but there is no kcontrol in there.

---

### Post by benerivo on 2008-11-01
Since kcontrol is not in intrepid, i think you may have to use qt3-qtconfig.

---

### Post by djvishnu on 2008-11-02
> **benerivo said:**
> Since kcontrol is not in intrepid, i think you may have to use qt3-qtconfig.

Ai! thank you!

qt3-qtconfig and qt4-qtconfig were just what i needed!

---

### Post by SunnyRabbiera on 2008-11-02
Kcontrol is no longet the main KDE configuration editor in KDE4, it is known as systemsettings, or systemsettings-kde4 in older builds

---

### Post by meho_r on 2008-11-03
But what about KDE 3 apps that many of us have installed (i.e. Kile)? How to change colors/style if there's no kcontrol? qt3-qtconfig doesn't change a thing...

---

### Post by zgornel on 2008-11-03
QT3 (e.g KDE3) apps should be rendered by the QT4 (KDE4) libs. Anyway, strictly KDE3 and KDE4 apps do not look upon the configuration of qt3-config and qt4-config. For further customization of KDE4 apps, install kde4-artwork and systemsettings packages. I have the problem with k3b and kile and double-shadows under the menus because of compiz and "kde3" settings.

---

### Post by mgol on 2008-11-03
> **zgornel said:**
> For further customization of KDE4 apps, install kde4-artwork and systemsettings packages.

```

$ sudo apt-get install kde4-artwork
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kde4-artwork

```

---

### Post by meho_r on 2008-11-03
> **mgol said:**
> ```

$ sudo apt-get install kde4-artwork
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kde4-artwork

```

Try kdeartwork

---

### Post by zgornel on 2008-11-03
Yes, I did not specify the exact name of the package (i never remember them) so I invented one :D

---

### Post by HalNineThousand on 2008-11-12
I'm really upset that kcontrol is not included in Intrepid.  I've used KDE for about 8 years and never dreamed of moving to GNome or any other desktop, but the new systemsettings program is weak compared to kcontrol and doesn't let you change settings on much of anything.  Right now I have no sound in KDE and I'm used to kcontrol to use in troubleshooting.   I could also use it to install my printers in CUPS easily, but without kcontrol, I don't know a quick way to do that other than the web interface for CUPS, which is a pain.

I have 2 16:9 monitors that have great resolution  and my panel at the bottom is thin.  With kcontrol I could make it larger, but not with systemsettings or with the current KDE 4.1 panel settings available.  I'm terribly disappointed in KDE 4.1 because it seems that as they go to 4.0, then 4.1, they're taking away more and more of our ability to customize the DE and going more with the proprietary software attitude that "we know what's best for you and the less you have to think, the better."

I see there's a package with kcontrol in it, but it conflicts with other stuff.  If I knew how to build packages, I'd grab the source and figure out how to build one without the conflicts, but I just don't have the time to do that.

If it weren't for a few needed items, such as VLC being able to read H.264 (HD) video and some other things I need, I'd go straight back to Gutsy.  That's the last time where I didn't have to fight Kubuntu for issues like dual head monitors and sound.

---

### Post by everettattebury on 2008-11-12
I'm running gnome in intrepid ibex.  I have changed the fonts to a serif font that I like, but Amarok still uses the default sans fonts.  (I'm talking about the application fonts, used in the menus and tooltips, not the Playlist Window, Player Window, and Context Sidebar that are controlled by the Amarok settings.)

I have installed qt3-qtconfig, and qt4-qtconfig, and neither of these seems to have any effect on Amarok.

Is there some configuration file somewhere that I can edit by hand to get the fonts I want?

---

### Post by zgornel on 2008-11-13
> **everettattebury said:**
> I'm running gnome in intrepid ibex.  I have changed the fonts to a serif font that I like, but Amarok still uses the default sans fonts.  (I'm talking about the application fonts, used in the menus and tooltips, not the Playlist Window, Player Window, and Context Sidebar that are controlled by the Amarok settings.)

I have installed qt3-qtconfig, and qt4-qtconfig, and neither of these seems to have any effect on Amarok.

Is there some configuration file somewhere that I can edit by hand to get the fonts I want?

Install the systemsettings and kdeartwork packages. You should find there the setings for KDE4 fonts.

---

### Post by lorebett on 2008-11-13
Do you mean that in KDE4 there's no kcontrol anymore?
I had the impression that systemsettings is the configuration panel provided by kubuntu and not from kde 4 (I've just installed kubuntu 8.10)...

systemsettings does not let you do anything basically... where can you change the driver for your graphic card?

And what about printer configuration?  The one in this version really sucks: it does not even scan for samba printers...

So you're saying that these are the tools provided by KDE 4? :confused:

probably it's time to switch to Gnome... :cry:

---

### Post by edantes on 2008-11-13
I installed  **systemsettings** and **kdeartwork**.  All I get from **systemsetting**  is an empty gray window.  Is this really IT?


Anyway, I used **kcontrol** before to set the spell checker to aspell with UTF8 encoding so I could use it with **kile**.

How do I do this now?

---

### Post by everettattebury on 2008-11-14
> **zgornel said:**
> Install the systemsettings and kdeartwork packages. You should find there the setings for KDE4 fonts.

Thanks, I didn't have kdeartwork, after installing it, many more tools showed up in System Settings.  I knew there had to be a way.

---

### Post by edantes on 2008-11-15
> **everettattebury said:**
> Thanks, I didn't have kdeartwork, after installing it, many more tools showed up in System Settings.  I knew there had to be a way.

I have both packages installed and and still no tools show in System Settings.  Do I still need the rest of kde installed?

---

### Post by everettattebury on 2008-11-17
> **edantes said:**
> I have both packages installed and and still no tools show in System Settings.  Do I still need the rest of kde installed?

Install kdebase-bin and see if that does it.

---

### Post by Keronn on 2008-11-22
> **everettattebury said:**
> Install kdebase-bin and see if that does it.

I installed systemsettings and kdeartwork (my fonts are ugly in the kde apps and qt3/4-config didn't help). I tried kdebase-bin, kdelibs, kdelibs-data but I still have an empty window when I open the system settings. 

I really didn't want to install all the kde desktop, there must be a simpler solution. Somebody has a clue ?

---

### Post by sdm_cacto on 2008-11-26
nop,  i just want to change the way Amarok looks. I cant do it properly without kcontrol and qtconfig doesnt seem to change anything.
maybe cause i upgraded from Hardy, where i used to have kcontrol. 
Maybe if someone makes a package?

---

### Post by Keronn on 2008-11-27
This thread is interesting : [http://ubuntuforums.org/showthread.php?p=6061570](http://ubuntuforums.org/showthread.php?p=6061570) Edit : I put the good link

When you run systemsettings in sudo mode, (gksudo systemsettings) all works fine. It changes the qt apps launched in superuser. But nothing happens in user mode, even if I copy /root/.kderc and all files in /root/.kde/share/config/ to the same location in my homedir (jeroenvrp's trick), giving them the correct autorisations and owner.

It seems that the applications launched in user mode don't reffer to these files.

---

### Post by rozbarwinek on 2008-11-28
The simplest way to have kcontrol in 8.10 is installation of those 4 packages (in that order):

```

kdebase-data_3.5.9-0ubuntu7_all
libkonq4_3.5.9-0ubuntu7_i386
kicker_3.5.9-0ubuntu7_i386
kcontrol_3.5.9-0ubuntu7_i386

```

from Hardy repository (can be found at [http://packages.ubuntu.com/](http://packages.ubuntu.com/))

That's all :)

---

### Post by Keronn on 2008-11-30
It works like a charm, thanks a lot !

---

### Post by retrovertigo on 2008-12-01
> **rozbarwinek said:**
> The simplest way to have kcontrol in 8.10 is installation of those 4 packages (in that order):

```

kdebase-data_3.5.9-0ubuntu7_all
libkonq4_3.5.9-0ubuntu7_i386
kicker_3.5.9-0ubuntu7_i386
kcontrol_3.5.9-0ubuntu7_i386

```

from Hardy repository (can be found at [http://packages.ubuntu.com/](http://packages.ubuntu.com/))

That's all :)

This worked (sort of).  I had to use the --force-all option for both the kdebase-data and kcontrol packages.  This then caused a conflict in apt, which didn't go away until I removed the packages.

Luckily my font preferences are now stored in /home/username/.kde/share/config/kdeglobals, so I can edit them there without the need of kcontrol.

---

### Post by Keronn on 2008-12-05
> **retrovertigo said:**
> This then caused a conflict in apt, which didn't go away until I removed the packages.No problem for me, with aptitude. There are different solutions submitted to solve the dependencies issues : with one of them kdebase-data is no more upgraded and I can keep kcontrol.

---

### Post by TheAL76 on 2008-12-07
Guys, this method worked for me without having to install anything extra:

1. Open /home/yourusername/.kde/share/config/kdeglobals in your favorite editor.
2. I wanted UnDotum size 10 to be my font, so I added this:

```

[General]
fixed=Monospace,5,-1,5,50,0,0,0,0,0
font=UnDotum,10,-1,5,50,0,0,0,0,0
menuFont=UnDotum,10,-1,5,50,0,0,0,0,0
taskbarFont=UnDotum,10,-1,5,50,0,0,0,0,0
toolBarFont=UnDotum,10,-1,5,50,0,0,0,0,0

```

3. Save and close this kdeglobals file; close out any open KDE apps and re-open them. Voila! For me, both of my KDE apps are looking much better (Amarok and k9Copy).

See if this works for you. I didn't want to clutter up my system with additional KDE nonsense, so being able to just edit this kdeglobals file directly seems like the best option.

Cheers,

TheAL76

---

### Post by seneika on 2008-12-11
> **lorebett said:**
> Do you mean that in KDE4 there's no kcontrol anymore?
I had the impression that systemsettings is the configuration panel provided by kubuntu and not from kde 4 (I've just installed kubuntu 8.10)...

systemsettings does not let you do anything basically... where can you change the driver for your graphic card?

And what about printer configuration?  The one in this version really sucks: it does not even scan for samba printers...

So you're saying that these are the tools provided by KDE 4? :confused:

probably it's time to switch to Gnome... :cry:


I totally agree... KDE4 mostly sucks. They're trying to change kde into windows. They started alright: kde is stopping working and becoming annoying.

What a shame!

---

### Post by lorebett on 2008-12-11
I only hope that they're working on porting the previous nice programs...

---

### Post by ZenYoga on 2009-01-05
> **TheAL76 said:**
> Guys, this method worked for me without having to install anything extra:

1. Open /home/yourusername/.kde/share/config/kdeglobals in your favorite editor.
2. I wanted UnDotum size 10 to be my font, so I added this:

```

[General]
fixed=Monospace,5,-1,5,50,0,0,0,0,0
font=UnDotum,10,-1,5,50,0,0,0,0,0
menuFont=UnDotum,10,-1,5,50,0,0,0,0,0
taskbarFont=UnDotum,10,-1,5,50,0,0,0,0,0
toolBarFont=UnDotum,10,-1,5,50,0,0,0,0,0

```

3. Save and close this kdeglobals file; close out any open KDE apps and re-open them. Voila! For me, both of my KDE apps are looking much better (Amarok and k9Copy).

See if this works for you. I didn't want to clutter up my system with additional KDE nonsense, so being able to just edit this kdeglobals file directly seems like the best option.

Cheers,

TheAL76

Thanks!
That did changed the fonts but I've also changed the antialias type in Gnome to LCD type (ClearType).
How do I set that setting in kdeglobals file?

---

### Post by RgnKjnVA on 2009-01-31
> **rozbarwinek said:**
> The simplest way to have kcontrol in 8.10 is installation of those 4 packages (in that order):

```

kdebase-data_3.5.9-0ubuntu7_all
libkonq4_3.5.9-0ubuntu7_i386
kicker_3.5.9-0ubuntu7_i386
kcontrol_3.5.9-0ubuntu7_i386

```

from Hardy repository (can be found at [http://packages.ubuntu.com/](http://packages.ubuntu.com/))

That's all :)

I must be missing something. That site seems to indicate that the packages are available in Universe which I have configured yet I get...

laptop:~$ sudo apt-get install kdebase-data_3.5.9-0ubuntu7_all
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kdebase-data_3.5.9-0ubuntu7_all

This is true for all of those packages. Any idea why that might be? Also, is it not possible to port Amarok or something? Alternatively, is it not possible to make modifying the glaringly bright interface much, much easier?

---

### Post by RgnKjnVA on 2009-02-01
Even after adding the Hardy repos below I get the same error (?!)

```
deb http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://archive.ubuntu.com/ubuntu/ hardy-security multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse universe
deb http://archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe
deb http://archive.canonical.com/ubuntu hardy partner
```

---

### Post by MonkeeSage on 2009-02-04
If you're getting the packages from apt you have to follow the apt package selection syntax (e.g., a deb named **kdebase-data_3.5.9-0ubuntu7_all.deb** would be selected in apt with **kdebase-data=3.5.9-0ubuntu7**--i.e., just the name of the package, an equals sign, and the version [leaving off the last underscore and architecture, in this case "_all"]).

---

### Post by RgnKjnVA on 2009-02-05
Ah thanks for the tip but seems the same result. (?)

laptop:~$ sudo apt-get install kdebase-data=3.5.9-0ubuntu7
[sudo] password for : 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Version '3.5.9-0ubuntu7' for 'kdebase-data' was not found

---

### Post by MonkeeSage on 2009-02-07
> **RgnKjnVA said:**
> Ah thanks for the tip but seems the same result. (?)

laptop:~$ sudo apt-get install kdebase-data=3.5.9-0ubuntu7
[sudo] password for : 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Version '3.5.9-0ubuntu7' for 'kdebase-data' was not found

Where did you add the repositories? In /etc/apt/sources.list? And did you run "sudo apt-get update" after adding them? I've not tried this myself, so I can't say that it works correctly, but according to [http://packages.ubuntu.com](http://packages.ubuntu.com), 3.5.9-0ubuntu7 is the correct version of kdebase-data in the hardy repos.

---

### Post by RgnKjnVA on 2009-02-08
I just ran through the whole process again to verify my steps and reproed the problem.

> **MonkeeSage said:**
> Where did you add the repositories? In /etc/apt/sources.list? 

Yes, in /etc/apt/sources.list

> And did you run "sudo apt-get update" after adding them? 

Yup, I did.

> I've not tried this myself, so I can't say that it works correctly, but according to [http://packages.ubuntu.com](http://packages.ubuntu.com), 3.5.9-0ubuntu7 is the correct version of kdebase-data in the hardy repos.

That's what I thought too

---

### Post by m4cph1sto on 2009-02-11
RgnKjnVA, try searching for those packages using synaptic package manager (after adding the hardy repos and doing apt-get update) and installing that way.  

Here's what I've found (I haven't actually installed any of them yet):

If I simply add the hardy repo to sources.list, a search in Synaptic lists the following package versions: kdebase-data 4.1.3, libkonq4 3.5.9, kicker 3.5.9, and kcontrol 3.5.9.  There is no kdebase-data 3.5.9.

However, if I comment out all of the lines in sources.list and then add only the hardy repo, a search in Synaptic lists all those packages with the proper versions, including kdebase-data 3.5.9.  

When I try to install kdebase-data 3.5.9, it says I must remove various packages (like kile and okular), so I'm not sure if this solution is going to work.  I also don't know if installing the newer version of kdebase-data along with kcontrol 3.5.9 will work.  I'll try it if I get brave enough.

For the record I'm using gnome, but I use kile for LaTeX and I really, really need inline spell checking, which is why I'm struggling to get kcontrol to work!

*Update:
kcontrol depends on kdebase-data 3.5.9, and will not install with 4.1.3.  If anyone's willing to use the method I described (comment out all lines in sources.list then add only the hardy repo), and then install kdebase-data 3.5.9 and the rest, and then configure something like spell check in kile... please post your success!

---

### Post by RgnKjnVA on 2009-02-12
Thank you much m4cph1sto, that did the trick. My Amarok ui is now a glorious shade of dark and all is right with the world...well, except for the Bluetooth issues in Intrepid but at least I'm down to only one annoyance now.

To answer your question, rolling back to kdebase-data 3.5.9 removes 4.1.3. You can go back to 4.1.3 with relative ease. After configuring the color scheme I wanted, I reinstalled KDE4 to get the code base back to standard Intrepid. All appears to be OK and my KDE color changes remain intact! Not sure what the impact would be for the kile/okular/LaTex stuff you're referring to though.

Thanks again. Ubuntu rocks...if you're into tweaking.

---

### Post by cyberscribe on 2009-06-06
What a bunch of insufferable crap -- for Ubuntu users that prefer Gnome over KDE, Amarok 2 is honestly just not worth all the trouble.

I loved Amarok 1 in Ubuntu -- but Amarok 2 is pure 100% junk.  What a sad devolution.  This strict adherence to dumb KDE conventions ensures that *only* KDE users will ever find this particular application usable.

I'm off to find another application similar to Amarok 1...goodbye Amarok 2!

---

### Post by lorebett on 2009-06-06
> **cyberscribe said:**
> 
I loved Amarok 1 in Ubuntu -- but Amarok 2 is pure 100% junk.  What a sad devolution.  This strict adherence to dumb KDE conventions ensures that *only* KDE users will ever find this particular application usable.


well, actually I'm not able to use it from KDE either, due to sound problems :cry:

---

### Post by RgnKjnVA on 2009-06-06
> **cyberscribe said:**
> What a bunch of insufferable crap -- for Ubuntu users that prefer Gnome over KDE, Amarok 2 is honestly just not worth all the trouble.

I loved Amarok 1 in Ubuntu -- but Amarok 2 is pure 100% junk.  What a sad devolution.  This strict adherence to dumb KDE conventions ensures that *only* KDE users will ever find this particular application usable.

I'm off to find another application similar to Amarok 1...goodbye Amarok 2!

Amarok is a KDE app so... *shrug* 

Take a look at Exaile but it's pretty early in the dev cycle and not nearly as fully featured as Amarok 1. I'm keeping an eye on Exaile and hope they make a lot of progress quickly. It seems to rely a lot on plug-ins that aren't part of the root package. I gave it a try though admittedly not for long but I'm kinda spoiled by Amarok's robustness and I managed to get Amarok skinned/themed in a reasonably acceptable way for me so I don't mind waiting.

[http://www.exaile.org/](http://www.exaile.org/)

actually, this post made me take another look at Exaile 0.2.14 and install some of the plug-ins that add the functionality I'm interested in. It's pretty darn close to being cool but seems to have a lot of little 'gotchas'. Going to install the 0.3 build later to see how it's coming along and report my issues fwiw to hopefully help move things forward.

---

### Post by everettattebury on 2009-06-06
> **cyberscribe said:**
> What a bunch of insufferable crap -- for Ubuntu users that prefer Gnome over KDE, Amarok 2 is honestly just not worth all the trouble.

I loved Amarok 1 in Ubuntu -- but Amarok 2 is pure 100% junk.  What a sad devolution.  This strict adherence to dumb KDE conventions ensures that *only* KDE users will ever find this particular application usable.

I'm off to find another application similar to Amarok 1...goodbye Amarok 2!

You can have Amarok 1.4 back:

[instructions here]("http://www.m0gky.co.uk/blog/466/")

---

