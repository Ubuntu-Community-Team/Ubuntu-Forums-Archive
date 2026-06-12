---
title: "Compiz-Switch - an easy way to switch Compiz off and on"
date: 2008-01-09
forum: Desktop Effects &amp; Customization
---

### Post by Forlong on 2008-01-09
[Compiz-Switch]("http://forlong.blogage.de/article/pages/Compiz-Switch") is a simple yet effective way to switch between Compiz and the window manager of your desktop environment on a single click.

[IMG]http://blogage.de/files/1366/image?compiz-switch-panel.png[/IMG]

[list][*]If Compiz is running, it will switch to the default window decorator of your desktop environment.
[*]If Compiz is not running, it will be launched immediately.[/list]

**[SIZE="3"]Installation[/SIZE]**

Just go [here]("http://forlong.blogage.de/article/pages/Compiz-Switch") and download the latest deb to your desktop.
Then double-click the file to install.


**[SIZE="3"]Usage[/SIZE]**

After you installed Compiz-Switch it should show up in the menu under:

[LIST][*]**GNOME**
Applications &#8594; Accessories &#8594; Compiz-Switch

[*]**KDE**
K-menu &#8594; Utilities &#8594; Compiz-Switch

[*]**Xfce**
Applications &#8594; Accessories &#8594; Compiz-Switch[/LIST]

If you want the icon to show up in the panel, all you have to do in GNOME and KDE is drag & drop the icon from the menu to the panel.

For Xfce this is unfortunately a little more complicated, because it doesn't support d&d for that. Here's a little workaround:

[LIST=1][*]Run *Applications &#8594; Accessories &#8594; Appfinder*
[*]Do a right-click on the panel and choose *Add New Item* in the context menu and double-click *Launcher*.
[*]Drag & drop *Compiz-Switch* from the Appfinder in the field with the New Item icon.
[*]Remove the New Item entry and choose *Close*.[/LIST]
Now you should have the icon in the panel.


**Switching to a specific window manager**

Compiz-Switch checks for available window managers in that order:

[LIST=1][*]Metacity (GNOME)
[*]Kwin (KDE)
[*]Xfwm (Xfce)[/LIST]
In case you have more than one of those installed, you may want to tell the program which one to use.
In order to do so, add either *metacity*, *kwin* or *xfwm4* to the command in your panel starter.


**[SIZE="3"]Compatibility[/SIZE]**

Compiz-Switch has been tested to work with:
[LIST][*]Ubuntu (Studio) Feisty
[LIST][*]Pre-installed Compiz / installed from the repository
[*][Backported Compiz packages from Gutsy]("http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty")[/LIST]
[*]Ubuntu Gutsy (pre-installed Compiz)
[*]Kubuntu Gutsy (Compiz installed from the main repository)
[*]Xubuntu Gutsy (Compiz installed from the main repository)[/LIST]

If you want to use Compiz-Switch with Compiz compiled from (git) source, you can use **compiz-switch-x.x.x~source** (also available on the [project's site]("http://forlong.blogage.de/article/pages/Compiz-Switch")).

---

### Post by jryprt on 2008-01-09
Thanks works great.

---

### Post by Mr Fredrick on 2008-01-09
Works well, thanks.

Suggestion: It would be good if the icon changed slightly depending on whether Compiz was currently on or off. Users could then tell at a glance.

---

### Post by Forlong on 2008-01-10
> **Mr Fredrick said:**
> Suggestion: It would be good if the icon changed slightly depending on whether Compiz was currently on or off. Users could then tell at a glance.
Yeah, I thought about it myself.
Although it's a neat idea, it also has some downsides and it's certainly not for everyone.
I'll have a look into it how to achieve that but make it optional.

---

### Post by phxtravis on 2008-01-12
Noob here having problems installing Compiz-swtich, this is the end of the installation:
[HTML]The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

*** No known documentation files were found. The new package 
*** won't include a documentation directory.

Please write a description for the package.
End your description with an empty line or EOF.
>> Compiz-Switch 
>> 

*****************************************
**** Debian package creation selected ***
*****************************************
/usr/bin/checkinstall: line 1166: dpkg-architecture: command not found

*** Warning: The package version "switch_0.2.0~ubuntu_i386" is not a
*** Warning: debian policy compliant one. Please specify an alternate one


This package will be built according to these values: 

0 -  Maintainer: [ root@travis-laptop ]
1 -  Summary: [ Compiz-Switch ]
2 -  Name:    [ compiz ]
3 -  Version: [  ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ compiz-switch_0.2.0~ubuntu_i386 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.
[/HTML]

---

### Post by Forlong on 2008-01-13
How are you trying to install it?
Deb packages can be installed by simply double-clicking them.

---

### Post by Promaster91 on 2008-01-13
Wow thats nice. Thanks.

---

### Post by phxtravis on 2008-01-13
Using terminal commands...I just tried double clicking the .deb and I get "ERROR: Wrong architecture i386"
Checkinstall

First you need to install checkinstall itself:

[HTML]sudo apt-get install checkinstall[/HTML]

Then use this command to install:

[HTML]sudo checkinstall[/HTML]


From your blog, the first installation method you gave wouldn't even start.

[HTML]travis@travis-laptop:~/Documents/compiz-switch_0.2.0~ubuntu_i386$ sudo make install
make: *** No rule to make target `install'.  Stop.
travis@travis-laptop:~/Documents/compiz-switch_0.2.0~ubuntu_i386$ 
[/HTML]

---

### Post by Forlong on 2008-01-13
> **phxtravis said:**
> Using terminal commands...I just tried double clicking the .deb and I get "ERROR: Wrong architecture i386"
I see. Sorry, I obviously haven't thought about 64bit users.
For checkinstall, you need to use the source from the tar archive. It was linked at the bottom of the page but I have moved it back up again.

Please come back if you have any further questions.

---

### Post by phxtravis on 2008-01-13
Cool...got it installed using:
[HTML]sudo make install[/HTML]

thanks for the help!

---

### Post by Forlong on 2008-01-13
> **Mr Fredrick said:**
> Suggestion: It would be good if the icon changed slightly depending on whether Compiz was currently on or off. Users could then tell at a glance.
OK, I finally got this to work (although a little hackish but I'll improve it when I have more time).

For the sake of clarity, I chose to test this with totally different icons:
Active: [IMG]http://img114.imageshack.us/img114/5624/compizswitchaj2.png[/IMG] - inactive: [IMG]http://img512.imageshack.us/img512/1543/metacitybp8.png[/IMG]

But I think this is a little too much for most people, so I did some inactive versions of the original icon. Which one do you guys think would be best?

---

### Post by amadeus266 on 2008-01-15
I like the look of it. keep us posted.

---

### Post by amadeus266 on 2008-01-15
How about adding autostarting/autostopping of other eyecandy like kiba-dock or AWN. (If installed) Maybe add a preferences menu for such.

Just contributing my own ideas for improvement.

---

### Post by Mr Fredrick on 2008-01-15
Hi Forlong,

Just noticed this post. Have checked your inactive icons, I think the second one, from the left, is best. Great work, they look good.

---

### Post by Forlong on 2008-01-15
> **amadeus266 said:**
> How about adding autostarting/autostopping of other eyecandy like kiba-dock or AWN. (If installed) Maybe add a preferences menu for such.
That's a good idea, I will implement it as soon as I figure out how to properly use extensions.
You know, it would be great to run something like
```
compiz-switch -x -s -a
```
So it runs Xfwm by default (-x) and kills Screenlets (-s) and AWN (-a) with it.

But I'm pretty new to bash. I began learing how to script just some weeks ago and Compiz-Switch is a byproduct of that so to speak.
I wanted to learn how to distribute a program as well, that's why I made it in the first place (and I know people where looking for something like this).
> **amadeus266 said:**
> Just contributing my own ideas for improvement.
And I really appreciate it. Thanks.
> **Mr Fredrick said:**
> I think the second one, from the left, is best. Great work, they look good.
Thanks, I'm leaning towards the last one, though.

And I'm not quite sure if I should publish that version already anyway.
It's a little awkward to use, because you *have* to specify a window manager, when you want to use the changing icon...
The command for the panel-icon would then be like this:
```
compiz-switch metacity change-icon
```

---

### Post by ZDemon on 2008-01-17
Hi Forlong.

I just have a quick question : Are you sure using a compiz-wrapper is a good idea?

Ive been looking at your script, and i feel it can be done in a different way. I dont know how (im still a newbie), but surely there can be a better solution than using a wrapper?

For example, I have a blacklisted GFX card (Intel 965) but it works great with compiz, other than the fact movies dont play well. But since you are using a wrapper, it wont reactivate Compiz, because the blacklist 'list' is in /jusr/bin/compiz AND /usr/local/bin/compiz-wrapper.

Actually, it is the blacklisted users that really have the need to use your script, because Compiz somehow gives problem to them. Movie playback for example.

Anyway, great work. It works on my NVidia PC. Use it before playing Warcraft.

Cheers.

---

### Post by FokkerCharlie on 2008-01-21
Handy little utility - nice one!

I personally would choose the 3rd icon, but they're all good.

Cheerio!
Charlie

---

### Post by FokkerCharlie on 2008-01-30
Hi again

I've been noticing some funny effects when switching compiz back on again.  Essentially, my theme doesn't load up properly, eg the font in the title bar is larger than it should be, and the buttons (minimise, restore, close) don't appear on the windows.

Is this just me?  Is there a way around this?

Cheers
Charlie

---

### Post by Sukarn on 2008-06-18
Hey, I've been using Compiz-Switch for a long time now (since the end of January, I think)

I just installed it once and never thought of upgrading it since it worked so well. I used it all the way through Gutsy, then hardy during it alpha cycle, and I'm still using it.

I just remembered about this thread and came back to it. I saw that I had been using version 0.2.0 and version 0.4.3 was out on the website. I upgraded it just because it was available, but I wanted to let you know that the program (although very short and simple) had been working great and without any hiccups all the time.

Thanks for Compiz-Switch.

---

### Post by KaliVoid on 2008-06-18
Very nice :cool:

thanks.



The Golden Stare disappear form this thread ?!

---

### Post by conorsulli on 2008-06-19
THANKS!!!! should be a default in all distros e.g in the "add to panel.." feature in Gnome that supply compiz-fusion!

---

### Post by Forlong on 2008-06-21
Hi folks,

sorry for the late reply. I lay sick in bed for the past week and additionally lost track of Compiz-Switch a little, since Compiz-Check has most of my attention for now.

I'm using a modified version of Compiz-Switch atm that kills and restores Kiba-Dock (I'm using a very old version of that) with it.
I may release it soon.

> **ZDemon said:**
> Hi Forlong.

I just have a quick question : Are you sure using a compiz-wrapper is a good idea?

Ive been looking at your script, and i feel it can be done in a different way. I dont know how (im still a newbie), but surely there can be a better solution than using a wrapper?

For example, I have a blacklisted GFX card (Intel 965) but it works great with compiz, other than the fact movies dont play well. But since you are using a wrapper, it wont reactivate Compiz, because the blacklist 'list' is in /jusr/bin/compiz AND /usr/local/bin/compiz-wrapper.

Actually, it is the blacklisted users that really have the need to use your script, because Compiz somehow gives problem to them. Movie playback for example.
Making it dependent on the wrapper that comes with Ubuntu is simply the most sane way to go.
There are easy workarounds for blacklisted users available, so if you still need help with this, don't hesitate to contact me.


> **FokkerCharlie said:**
> I've been noticing some funny effects when switching compiz back on again.  Essentially, my theme doesn't load up properly, eg the font in the title bar is larger than it should be, and the buttons (minimise, restore, close) don't appear on the windows.

Is this just me?  Is there a way around this?
Since Compiz-Switch uses the same way to start Compiz as Ubuntu itself, this problem shouldn't be specific to Compiz-Switch then.
Try switching Compiz off and on via *System &#8594; Preferences &#8594; Appearance &#8594; Visual Effects* -- does it show the same symptoms?


> **Sukarn said:**
> Hey, I've been using Compiz-Switch for a long time now (since the end of January, I think)

I just installed it once and never thought of upgrading it since it worked so well. I used it all the way through Gutsy, then hardy during it alpha cycle, and I'm still using it.

I just remembered about this thread and came back to it. I saw that I had been using version 0.2.0 and version 0.4.3 was out on the website. I upgraded it just because it was available, but I wanted to let you know that the program (although very short and simple) had been working great and without any hiccups all the time.

Thanks for Compiz-Switch.
Thank you very much for your feedback. That's exactly what hobby-programmers like me need.
Frankly, I don't know if there are more than just a handful of users out there that are currently using my program so thanks again for your positive feedback.


> **conorsulli said:**
> THANKS!!!! should be a default in all distros e.g in the "add to panel.." feature in Gnome that supply compiz-fusion!
Thank you.
The idea of a panel applet already came to my mind too but I'd like to keep my programs independent of the desktop environment in use.

That doesn't mean there won't be one in the future, though. Don't know how complex to write those are.

---

### Post by Sukarn on 2008-06-21
> **Forlong said:**
> 
The idea of a panel applet already came to my mind too but I'd like to keep my programs independent of the desktop environment in use.

That doesn't mean there won't be one in the future, though. Don't know how complex to write those are.

I think it would be too much effort too create panel applets of Compiz-Switch.

The way it is right now, someone just has to drag it from the menu to the panel to add it to the panel in GNOME and KDE. The process is a little different for XFCE, but I can't comment on that because I'm not using it. I don't know about the other desktop environments (like E17, JWM, Fluxbox) as well.

---

### Post by Revvion on 2008-06-23
Got a question, i just installed it and can switch to compiz but it wont switch back to gnomes default (metacity i believe) anyone able to help me solve this? I tried using things like "compiz-switch -m".

---

### Post by Forlong on 2008-06-23
Is there any error message when running plain ```
compiz-switch
``` (twice) in a terminal?

---

### Post by Revvion on 2008-06-23
no errors at all, Aldo it does act weird because it never closes so running it twice in terminal is impossible unless i abort it by force.

---

### Post by Forlong on 2008-06-23
You know what, I'll upload the current version I'm using myself right now.
Maybe that'll fix this.

---

### Post by Forlong on 2008-06-23
Alright, here it is: [http://blogage.de/files/4374/download?compiz-switch_0-5-beta](http://blogage.de/files/4374/download?compiz-switch_0-5-beta)

Please note that's only the plain script.

Download this to your home directory.

Then run it like this:
```
~/compiz-switch_0-5-beta
```
Does it work?


edit: and you should be able to run it multiple times. Just hit the [&#8593;] key of your keyboard.

---

### Post by Revvion on 2008-06-23
Thanks ~/compiz-switch_0-5-beta seems to work fine

---

### Post by Forlong on 2008-06-23
OK, then right-click the panel icon of Compiz-Switch (I'm assuming you have one), choose Properties and click on the button next to the compiz-switch command -- there you choose the file you just downloaded.

---

