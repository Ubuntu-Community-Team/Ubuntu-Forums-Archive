---
title: "AWN - Have no themes, applets, nothing - how to get the default ones?"
date: 2008-02-21
forum: Desktop Effects &amp; Customization
---

### Post by PiggiePaul on 2008-02-21
I installed AWN following the guide at the very top of this screen:

[http://wiki.awn-project.org/DistributionGuides#Gutsy_Gibbon_.287.10.29](http://wiki.awn-project.org/DistributionGuides#Gutsy_Gibbon_.287.10.29)

Edited the "Software Sources" as they explained, and then issued the command they say at the terminal:

[COLOR="Blue"]sudo apt-get install avant-window-navigator awn-manager[/COLOR]

This successfully installed AWN, but it's just the raw program.
I don't have the default Applets or anything.

I have tried the following command at the terminal: 

[COLOR="Blue"]sudo apt-get install awn-core-applets-bzr[/COLOR]

And just got the following output:

[COLOR="Blue"]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package awn-core-applets-bzr[/COLOR]

Also tried this:

[COLOR="Blue"]sudo apt-get install awn-extras[/COLOR]

And got the same output.

So, as I followed their instructions to the letter, and just ended up with the empty program, how do I now get the default stuff that goes with it?

thanks.

---

### Post by chipants on 2008-02-21
did you try "awn-core-applets" without the bzr at the end?

if the applets package just isn't in there, it would be lame, but you could uninstall, remove the 'gutsy-backports' repository, and try the " Reacocard's PPA" method provided on the same page as i originally directed you to in the original thread. ([http://wiki.awn-project.org/DistributionGuides#Gutsy_Gibbon_.287.10.29](http://wiki.awn-project.org/DistributionGuides#Gutsy_Gibbon_.287.10.29))

that method uses the same launchpad repo that i'm currently using. it *definitely* has the applet package.

i just don't know why the applets wouldn't be in the repo you're using.

---

### Post by xcalibur32 on 2008-02-22
To follow up on that. AWN works fine. But everytime I get two copies of the icon. For eg. when I open firefox, I get two icons of firefox - one on each end. Any fixes for that?

Thanks in advance.

---

### Post by chipants on 2008-02-22
> **xcalibur32 said:**
> To follow up on that. AWN works fine. But everytime I get two copies of the icon. For eg. when I open firefox, I get two icons of firefox - one on each end. Any fixes for that?

Thanks in advance.

i don't have that problem. however, AWN will create a new icon for each actual task, not one per program. so, for instance, if you have multiple firefox windows open, there will be one icon for each window.

if you're always getting two icons, i'm not really sure. although, i am rather sleepy and could be missing something obvious.

one thing that bugged me at first was that all launchers had the little triangle/arrow under them... but not running tasks. that is counterintuitive to me. and, also the exact opposite of the os x dock that AWN looks so much like. to remedy that problem (and maybe yours?), open the AWN manager and click on the 'Task Appearance' tab. make sure that 'Tasks Have Arrows' is checked. errr... i guess that really isn't related to your problem most likely. bleh. maybe i should get some sleep.

---

### Post by PiggiePaul on 2008-02-22
> **chipants said:**
> did you try "awn-core-applets" without the bzr at the end?

if the applets package just isn't in there, it would be lame, but you could uninstall, remove the 'gutsy-backports' repository, and try the " Reacocard's PPA" method provided on the same page as i originally directed you to in the original thread. ([http://wiki.awn-project.org/DistributionGuides#Gutsy_Gibbon_.287.10.29](http://wiki.awn-project.org/DistributionGuides#Gutsy_Gibbon_.287.10.29))

that method uses the same launchpad repo that i'm currently using. it *definitely* has the applet package.

i just don't know why the applets wouldn't be in the repo you're using.

Just tried this:

[COLOR="Blue"]sudo apt-get install awn-core-applets[/COLOR]

and got:

[COLOR="Blue"]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package awn-core-applets[/COLOR]

Methinks, I'm not impressed with how this is going, seeing as how I followed THEIR instructions in the 1st place!

---

### Post by reacocard on 2008-02-22
> **PiggiePaul said:**
> Just tried this:

[COLOR="Blue"]sudo apt-get install awn-core-applets[/COLOR]

and got:

[COLOR="Blue"]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package awn-core-applets[/COLOR]

Methinks, I'm not impressed with how this is going, seeing as how I followed THEIR instructions in the 1st place!

gutsy-backports does not have the applets. However, my PPA does, just follow this guide: [http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

EDIT: I've updated the AWN wiki page to make it clear that -backports doesn't have the applets and suggests the appropriate method of fixing that so that this issue shouldn't happen again.

---

### Post by Mad_Gouki on 2008-02-22
If you have the programs showing up twice, you might have 2 launcher/taskmanager applets added to the bar.  That applet should be available, even when the others are not.
I think you either don't have the repositories added, or the connection to them is interrupted.  Follow the link that reacocard posted, it will get you set up with the repositories you want.

---

### Post by PiggiePaul on 2008-02-22
> **reacocard said:**
> gutsy-backports does not have the applets. However, my PPA does, just follow this guide: [http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

EDIT: I've updated the AWN wiki page to make it clear that -backports doesn't have the applets and suggests the appropriate method of fixing that so that this issue shouldn't happen again.

Thank you for the reply.

At work now :(

So shall follow your instructions later tonight when at my home PC again, and will report back here.

Cheers :)

---

### Post by PiggiePaul on 2008-02-22
> **reacocard said:**
> gutsy-backports does not have the applets. However, my PPA does, just follow this guide: [http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

EDIT: I've updated the AWN wiki page to make it clear that -backports doesn't have the applets and suggests the appropriate method of fixing that so that this issue shouldn't happen again.

Errrr, home now........

Just follow this guide (on a 110 posting topic!!)

The guide (1st page) seems to talk about installing it with the addons.

Shall I just ignore the fact I already have it installed and follow your commands, ending with installing the APP again, but (hopefully) this time with the addons:

[COLOR="Blue"]sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr[/COLOR]


This is all (approx) a year old, so will I be getting the latest version following this guide?

I (Worryingly) notice at the start it says:

[COLOR="Blue"]First, add my AWN repo:  [/COLOR]

Then after the terminal instructions it says:

[COLOR="Blue"]NOTE: There is no stable AWN currently available in my repository.[/COLOR]

Bit unsure about what this means?


============= EDIT ==============

Well assumed the files were kept up to date :)

So went for it anyway and now have the latest version running.

Just got to get my head around it!

Like why do I have 2 icons appear in the bar when I have anything on screen? One on the left and another on the right? Even open folders show up twice?
Seems odd.

---

### Post by PiggiePaul on 2008-02-22
Just done a screen grab.

This is gonna get VERY messy when I have a few things running at the same time:

[IMG]http://i26.photobucket.com/albums/c145/Paul-rs/awn-screenshot.jpg[/IMG]

---

### Post by reacocard on 2008-02-22
> **PiggiePaul said:**
> Errrr, home now........

Just follow this guide (on a 110 posting topic!!)

The guide (1st page) seems to talk about installing it with the addons.

Shall I just ignore the fact I already have it installed and follow your commands, ending with installing the APP again, but (hopefully) this time with the addons:

[COLOR="Blue"]sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr[/COLOR]


This is all (approx) a year old, so will I be getting the latest version following this guide?

I (Worryingly) notice at the start it says:

[COLOR="Blue"]First, add my AWN repo:  [/COLOR]

Then after the terminal instructions it says:

[COLOR="Blue"]NOTE: There is no stable AWN currently available in my repository.[/COLOR]

Bit unsure about what this means?


============= EDIT ==============

Well assumed the files were kept up to date :)

So went for it anyway and now have the latest version running.

Just got to get my head around it!

Like why do I have 2 icons appear in the bar when I have anything on screen? One on the left and another on the right? Even open folders show up twice?
Seems odd.

hm, that's very odd behavior. in awn-manager (system->preferences->awn manager), under 'applets', make sure you only have one instance of the taskmanger applet (it's icon is the awn icon).

---

### Post by PiggiePaul on 2008-02-22
Right then.

If this is not normal (which I can't believe it is) I think the problem MIGHT be that I'd already installed AWN last night using the method at the top of the screen here:

[http://wiki.awn-project.org/DistributionGuides#Gutsy_Gibbon_.287.10.29](http://wiki.awn-project.org/DistributionGuides#Gutsy_Gibbon_.287.10.29)

And then (not knowing how to uninstall it) I used th other method to get the newer version with the default plugins.

I'm thinking due to this, I'm getting two instances running somehow.

Anyway, I guessed the best idea is to uninstall the whole lot and start a-fresh.

So, to start with, I went to Synaptic Package Manager, found AWN highlighted, un-ticked them and told it to uninstall, so (as far as I can see) the new/latest vesion has gone.

BUT. I'm still left with some/most of the old one I installed from last night.

The preferences have gone, but I can still run it, albeit, it's giving some graphical glitches. So, first things first.

given that I used This instruction:

 [COLOR="Blue"]sudo apt-get install avant-window-navigator awn-manager[/COLOR]

From the top of this page:

[http://wiki.awn-project.org/DistributionGuides#Gutsy_Gibbon_.287.10.29](http://wiki.awn-project.org/DistributionGuides#Gutsy_Gibbon_.287.10.29)

How do  I uninstall AWN?

Thanks.

Also, is it normal for a icon to appear in the AWN bar for every program/folder that you open on screen?
So if I had 10 folders open on screen then I'd have 10 folder icons on the AWN bar?

=======Another Edit=========

Went back to Synaptic Package Manager and (oddly) some part was still highlighted so unticked it, and seems to have gone now, rebooted also.

Will re-install from your links again.

---

### Post by chipants on 2008-02-22
> **PiggiePaul said:**
> Just done a screen grab.

This is gonna get VERY messy when I have a few things running at the same time:



i like your AWN them, but may i ask why you have the taskbar panel running underneath AWN? heh. when i get home, maybe i'll post a screenshot of my desktop. i generally like to use AWN for my task switching. but, i keep a slim gnome panel along the top of my screen, and add the 'window list' applet to it. to each his own, i guess. :D

---

### Post by PiggiePaul on 2008-02-22
> **chipants said:**
> i like your AWN them, but may i ask why you have the taskbar panel running underneath AWN? heh. when i get home, maybe i'll post a screenshot of my desktop. i generally like to use AWN for my task switching. but, i keep a slim gnome panel along the top of my screen, and add the 'window list' applet to it. to each his own, i guess. :D

No, don't worry, the bar was only still at the bottom until I decided I was going to do with either AWN or Cairo, THEN I was going to remove it, as if I decided to go with neither then I'd just keep the bar there.

Had a few issues (head baning against a plank of wood!) about the old version, then the new version (possibly on top) then trying to remove them BOTH, then I tried Cairo.

Oh dear.........

Sorry, but Cairo really did not do it for me, which was odd, cos from some little video clips Cairo looks quite nice, but in reality, I just was not happy with the look and all the stretching, zooming, unzooming and the rather BOLD look of the thing.

So, removed Cairo pretty quick!

Then After being doubly sure AWN was off the system for a 2nd time, I reinstalled using the command line (from that site that was posted earlier) and after a reboot, I think (he says with crossed fingers) It's all sorted itself out.

Phew !!!!!

No more double icons.

The only thing I'm not sure about yet is, is it going to auto run on the next reboot, as it's not done that yet, despite the option being turned on in the preferences.

If not, I'll be back here asking :)

---

### Post by PiggiePaul on 2008-02-22
Nope, Although it LOOKS fine and appears to work fine, I have 2 issues to yet resolve with my new AWN

1: It won't autostart upon bootup, despite the tick box being ticked.

2: I've not yet managed to work out how to add launchers to it. I've tried thru the options where you are supposed to browse to an exe file, but I've had no joy yet.

Unless it's my fault and I'm not quite sure where the exe files are in ubuntu?

======= EDIT ========

Well, as far as I can gather, the Add Launchers part of AWN basically does not work. I've tried googling for help and have read other having similar findings (perhaps we are doing something wrong, or there is a fix, or it's just not yet working?)

The only way (it seems) is to drag application icons onto the AWN bar from /USR/SHARE/APPLICATIONS

Just going to do a reboot and see if they stay there!

---

### Post by chipants on 2008-02-22
> **PiggiePaul said:**
> Nope, Although it LOOKS fine and appears to work fine, I have 2 issues to yet resolve with my new AWN

1: It won't autostart upon bootup, despite the tick box being ticked.

2: I've not yet managed to work out how to add launchers to it. I've tried thru the options where you are supposed to browse to an exe file, but I've had no joy yet.

Unless it's my fault and I'm not quite sure where the exe files are in ubuntu?

======= EDIT ========

Well, as far as I can gather, the Add Launchers part of AWN basically does not work. I've tried googling for help and have read other having similar findings (perhaps we are doing something wrong, or there is a fix, or it's just not yet working?)

The only way (it seems) is to drag application icons onto the AWN bar from /USR/SHARE/APPLICATIONS

Just going to do a reboot and see if they stay there!

i don't remember the check-box to launch at startup in the AWN manager. i did it by adding as a program to launch on startup. geez, i wish i was at home to tell you, step-by-step what to do. but, my memory is not that great. in one of the system menus, there is an entry for managing sessions. i don't remember the title of the entry. it's got 'session' in it though. :) anyway, you just need to add the awn executable to the list of apps to run on gnome startup.

also there are no ".exe" files with linux. there are executable binaries, but they do not have an .exe extension at the end of them. they generally don't have an extension at all. however, you don't need to know anything about executables to add a launcher to AWN. you just have to drag apps from your applications menu right into the dock. it's as simple as that!

---

### Post by PiggiePaul on 2008-02-22
> **chipants said:**
> i don't remember the check-box to launch at startup in the AWN manager. i did it by adding as a program to launch on startup. geez, i wish i was at home to tell you, step-by-step what to do. but, my memory is not that great. in one of the system menus, there is an entry for managing sessions. i don't remember the title of the entry. it's got 'session' in it though. :) anyway, you just need to add the awn executable to the list of apps to run on gnome startup.

also there are no ".exe" files with linux. there are executable binaries, but they do not have an .exe extension at the end of them. they generally don't have an extension at all. however, you don't need to know anything about executables to add a launcher to AWN. you just have to drag apps from your applications menu right into the dock. it's as simple as that!

Thanks. why are you at work at this time on a Friday night anyway?

Yeah, I found that place where you can add startup progs, but "Again" I run up against the brick wall of not understanding where the .exe files (which are not actually .exe files) for any particular program are.

I think the person who designed the file structure for Linux must have been on speed or something as he sure likes creating different folders EVERYWHERE !!!!

At least with Windows you had:

C:/Program Files/Firefox/Firefox.exe  (or something like that)
but at least it was logical, that all programs were in their folders in program files.

I've found some/lots (in Linux) under /user/bin
Not sure if that's the only place, as I can't see Firefox in there :confused:

========= EDIT==========

Managed to find "Avant Window Navigator" in that /USER/BIN folder, and have added it to the startup progs. Rebooted and it works fine.
Rather odd that it appears to start at the left hand side of the screen and scroll towards the middle, but matters not I guess.

But (if the author of AWN happens to be reading) I think it's a superb app. Just what I wanted, yup, I guess a few bits are not working 100% but it works well enough to do it's job. for some odd reason that little line that separates the shortcuts from the actual running programs does not appear to work in this latest version either. I changed the color of the line to 100% opacity and white and it still does not show. But again, it's no big deal.

I'd LOVE an Ebay and a YouTube applett

---

### Post by chipants on 2008-02-22
> **PiggiePaul said:**
> Thanks. why are you at work at this time on a Friday night anyway?

Yeah, I found that place where you can add startup progs, but "Again" I run up against the brick wall of not understanding where the .exe files (which are not actually .exe files) for any particular program are.

I think the person who designed the file structure for Linux must have been on speed or something as he sure likes creating different folders EVERYWHERE !!!!

At least with Windows you had:

C:/Program Files/Firefox/Firefox.exe  (or something like that)
but at least it was logical, that all programs were in their folders in program files.

I've found some/lots (in Linux) under /user/bin
Not sure if that's the only place, as I can't see Firefox in there :confused:

========= EDIT==========

Managed to find "Avant Window Navigator" in that /USER/BIN folder, and have added it to the startup progs. Rebooted and it works fine.
Rather odd that it appears to start at the left hand side of the screen and scroll towards the middle, but matters not I guess.

But (if the author of AWN happens to be reading) I think it's a superb app. Just what I wanted, yup, I guess a few bits are not working 100% but it works well enough to do it's job. for some odd reason that little line that separates the shortcuts from the actual running programs does not appear to work in this latest version either. I changed the color of the line to 100% opacity and white and it still does not show. But again, it's no big deal.

I'd LOVE an Ebay and a YouTube applett

hahah. finally at home. glad you found the 'Sessions' app alright.

new linux users are often intimidated by the directory structure. it can be a little confusing at first, but everything has a place. once you understand the purpose of each 'folder', it all makes sense. as a matter of fact, it is easier to find things on a linux system because pretty much everybody follows convention and installs things to standard places. on a windows system, an installer can (and often do) put files pretty much anywhere. 

i, too, am using the newest version of AWN, but have no trouble with the separator. mine shows up just fine. strange problem. i have also wondered about the slow sliding from the left upon startup. it doesn't happen 100% of the time, but usually.

btw, there IS a youtube applet for AWN!

[http://wiki.awn-project.org/Youtube_Browser_Applet](http://wiki.awn-project.org/Youtube_Browser_Applet)

i haven't tried it yet, but looks pretty cool. haven't found an ebay one just yet.

---

### Post by pythonusr on 2008-03-03
Most applications are saved in /usr/bin, if I am not mistaken, and directoryies can be added to your $PATH in order to run them as a command from the terminal.

You won't really ever need to find where the binaries are for applications, but check /usr/bin first, then /usr/lib, which has other directories of applications (and their libraries).

You'll get used to it eventually. Applications don't have an extention on Linux, except under Wine, but that's a whole different story.

---

