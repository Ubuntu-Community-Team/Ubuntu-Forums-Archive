---
title: "random openbox chatter"
date: 2006-06-06
forum: Desktop Environments
---

### Post by fuscia on 2006-06-06
so as not to bog down the desktop pics thread, i've started this openbox thread. (watch no one show up now.) i'll be right back...

---

### Post by curuxz on 2006-06-06
*stands around* erm what are we suposed to do now we HAVE shown up?

Im confused and mostly I want to go home

---

### Post by raublekick on 2006-06-06
thank you, fuscia! 

ok so here goes: i added Gaim to my menu, right below Web browser. Great! Now, is there a way I can make a sub menu isntead? i'm sure there is, i've just never used xml before. 

next, i need some sort of panel with a clock and other stuff on it. in installed pypanel but have no idea how to use it. obconf has the dock section, but i see no dock. 

third and final question for now: can you use GTK+2 themes at all, or am i stuck with gtk+?

---

### Post by fuscia on 2006-06-06
first of all, there is already a pretty slick howto, by stormy eyes - [http://ubuntuforums.org/showthread.php?t=75471&highlight=openbox](http://ubuntuforums.org/showthread.php?t=75471&highlight=openbox)

raublekick asked about menu editing. there's a nice little app called 'obmenu' which is drunken child easy to use - [http://obmenu.sourceforge.net/index.html](http://obmenu.sourceforge.net/index.html)
installing it can be a pain in the butt trying to figure out what pyglade is called in synaptic. 
here's a screenshot of my openbox right-click menu...

[[IMG]http://img415.imageshack.us/img415/1038/obmenuscr5dy.th.jpg[/IMG]](http://img415.imageshack.us/my.php?image=obmenuscr5dy.jpg)

another thing that baffles people when they first try openbox is the absolutely instant appearance of a black screen upon logging in. it *is* blank. right-click  and you'll find the default menu. you'll have to use another program to set the background wallpaper. i use feh, but others can be used.

what did i leave out? 

oh! it's faster than asterisks!

---

### Post by fuscia on 2006-06-06
[QUOTE=raublekick]thank you, fuscia![/quote]

my pleasure. 

> ok so here goes: i added Gaim to my menu, right below Web browser. Great! Now, is there a way I can make a sub menu isntead? i'm sure there is, i've just never used xml before. 

obmenu will cure all your ills, my friend.

> next, i need some sort of panel with a clock and other stuff on it. in installed pypanel but have no idea how to use it. obconf has the dock section, but i see no dock.

you can enter pypanel in the terminal, put it on your menu (i have 'on' and 'off' in sub-menues for both pypanel and conky), or put *pypanel & exec openbox* in your .xinitrc file and it will start upon logging in.

i never have, don't currently, nor ever will get this 'dock' thing. meh. 

> third and final question for now: can you use GTK+2 themes at all, or am i stuck with gtk+?

i've made a few of my own openbox themes. they're easy to make. i wouldn't know a gtk theme unless i knew it were a gtk theme.

> *stands around* erm what are we suposed to do now we HAVE shown up?

Im confused and mostly I want to go home

now, now. patience...

---

### Post by RAV TUX on 2006-06-06
[quote=fuscia]first of all, there is already a pretty slick howto, by stormy eyes - [http://ubuntuforums.org/showthread.php?t=75471&highlight=openbox]("http://ubuntuforums.org/showthread.php?t=75471&highlight=openbox")



[/quote] 
Openbox reminds me of Morphing-Morphix.

[http://www.morphix.org/index.php?option=com_content&task=view&id=64&Itemid=59](http://www.morphix.org/index.php?option=com_content&task=view&id=64&Itemid=59)

---

### Post by PapaWiskas on 2006-06-06
OK fuscia, because I am an idiot I need some clarification if you dont mind.

I go to my synaptic to double check if I have all my dependencies for this obmenu thingy....since the last time I tried openbox, which I really, really, really want to get working, and all I had was a blank screen with nothing and it freaked me out, and for some reason, the right click did not bring up any menus at all.  So I got scared and dumped it, fearing that I had called upon some evil demons and my Ubuntu was going to be hosed forever.

Where was I?  Oh yeah....these dependencies....I doubled checked and I do have python installed...in the installed version column in synaptic is says version number is 2.4.2-0ubuntu3, I assume this is good enough because it says it needs at least python 2.3 or better.  Am I right, I am good to go there?
However...pygtk and pyglade I could not find those exclusively by those names.  But I am wondering is pyglade the same thing as python-glade2 2.8.6-0ubuntu1 (which I already have installed) or do I need the python-glade1.2 which is not installed, or am I just stupid and neither of those is what I need.  I also have python-gtk2 2.8.6-0ubuntu1 installed but not python-gtk-1.2, so are either of those the same thing as pygtk?

I think I have it all covered but just am not 100% sure I am correct in my assumptions.

Thanks for taking the time to respond.

Best Regards,
Papa

---

### Post by fuscia on 2006-06-06
papa, python#.#-glade and python#.#-gtk are right. i'm not sure which version worked, though. i'm one of those people who just keeps installing junk until it works. you may need the dev packages, as well, but i don't remember. sorry to be so vaguely helpful.

edit: if anything, this thread proves the old saying "in the kingdom of the blind, it is the one-eyed guy who gets to pick the movie."

---

### Post by PapaWiskas on 2006-06-06
[QUOTE=fuscia]
you can enter pypanel in the terminal, put it on your menu (i have 'on' and 'off' in sub-menues for both pypanel and conky), or put *pypanel & exec openbox* in your .xinitrc file and it will start upon logging in.
[/QUOTE]


How did you do that...what is the command to turn a particular program off and on.  I have pypanel entry that will turn it on, but not one to turn it off.

Also I used feh to set a background, but when I logged back in the background was blank again....how do I get my desktop image to stay?

---

### Post by fuscia on 2006-06-06
[QUOTE=PapaWiskas]How did you do that...what is the command to turn a particular program off and on.  I have pypanel entry that will turn it on, but not one to turn it off.[/quote]

select 'new menu' and make it pypanel, then create a 'new item' for 'on' and one for 'off. for 'on' the command is simply *pypanel*. for 'off'. the command is *killall pypanel*.

> Also I used feh to set a background, but when I logged back in the background was blank again....how do I get my desktop image to stay?

no idea. i change my wallpaper so often, i 'don't care if it's not there when i log in.

---

### Post by PapaWiskas on 2006-06-06
[QUOTE=fuscia]select 'new menu' and make it pypanel, then create a 'new item' for 'on' and one for 'off. for 'on' the command is simply *pypanel*. for 'off'. the command is *killall pypanel*.[/QUOTE]

.
Thank you for the help on that..

[QUOTE=fuscia]
no idea. i change my wallpaper so often, i 'don't care if it's not there when i log in.[/QUOTE]

That made me laugh so hard I almost wet myself....

---

### Post by raublekick on 2006-06-06
thank you fuscia!

obmenu is awesome, but i will suggest menu maker as well. menumaker will create a menu for you, which is nice, but now i need to trim the fat (right now my menu is about 600lbs, i need to to be about 120lbs :) )

i'm still trying to figure out the gtk2 theme thing, i just haven't seen any info on it at all.

---

### Post by fuscia on 2006-06-07
my pleasure, guys.

---

### Post by raublekick on 2006-06-07
ah, i figured out my gtk2 theme quandry: 

sudo apt-get install gtk-theme-switch
this installs switch and switch2 (for switching gtk1 and gtk2 themes respectively). just run switch2 and pick a theme! however only ones installed in your .themes directory seem to work.

---

### Post by graabein on 2006-06-07
If you have GNOME installed you might try adding *gnome-settings-deamon* to your .xinitrc-file. 8)


EDIT: There's also some good openbox info on the [Gentoo wiki]("http://gentoo-wiki.com/HOWTO_Openbox").

---

### Post by raublekick on 2006-06-07
yeah that gentoo wiki is awesome. i think i might write a how-to today on how to set up openbox. i'll link to stormyeyes' one but expand upon it with all the options to set up the menu, themes, and so forth. 

of course, i'll thank stormy and fuscia.

---

### Post by GarethMB on 2006-06-07
[QUOTE=raublekick]yeah that gentoo wiki is awesome. i think i might write a how-to today on how to set up openbox. i'll link to stormyeyes' one but expand upon it with all the options to set up the menu, themes, and so forth. 

of course, i'll thank stormy and fuscia.[/QUOTE]
i look forward to reading it

---

### Post by Zodiac on 2006-06-07
[QUOTE=fuscia]first of all, there is already a pretty slick howto, by stormy eyes - [http://ubuntuforums.org/showthread.php?t=75471&highlight=openbox](http://ubuntuforums.org/showthread.php?t=75471&highlight=openbox)

raublekick asked about menu editing. there's a nice little app called 'obmenu' which is drunken child easy to use - [http://obmenu.sourceforge.net/index.html](http://obmenu.sourceforge.net/index.html)
installing it can be a pain in the butt trying to figure out what pyglade is called in synaptic. 
here's a screenshot of my openbox right-click menu...

[[IMG]http://img415.imageshack.us/img415/1038/obmenuscr5dy.th.jpg[/IMG]](http://img415.imageshack.us/my.php?image=obmenuscr5dy.jpg)

another thing that baffles people when they first try openbox is the absolutely instant appearance of a black screen upon logging in. it *is* blank. right-click  and you'll find the default menu. you'll have to use another program to set the background wallpaper. i use feh, but others can be used.

what did i leave out? 

oh! it's faster than asterisks![/QUOTE]


EWWWW... Go Canes! ???? Tell me you are not a Canes "fan"...

Read this please: [http://www.nicholasbattaglia.com/article/20/a-heartbreaking-work-of-staggering-genius](http://www.nicholasbattaglia.com/article/20/a-heartbreaking-work-of-staggering-genius)

---

### Post by fuscia on 2006-06-07
[QUOTE=Zodiac]EWWWW... Go Canes! ???? Tell me you are not a Canes "fan"...

Read this please: [http://www.nicholasbattaglia.com/article/20/a-heartbreaking-work-of-staggering-genius](http://www.nicholasbattaglia.com/article/20/a-heartbreaking-work-of-staggering-genius)[/QUOTE]

flaunting your bitterness, eh? canes rock!!!

---

### Post by Zodiac on 2006-06-07
haha... Redneck hockey fans? Please.

One guy had a sign that said, "America's hockey team"... Yea right... 

And cheerleaders??? Cheerleaders??? In hockey??!!!?

Now I don't want to get your little thread moved to the backyard, but, the Canes suck. Good team, wrong town. Stop messing up a perfectly good Northern/Canadian sport.

Thanks!

---

### Post by raublekick on 2006-06-07
i'm kinda happy for the canes. i just with philly would step it up and actually practice what they are weak at.


anyways, i found a hige problem for me. when i logout of openbox, i am greeted by a blue screen. well, there is a faint text box for my login/password, but that's all i can see, and it's hard to see. so from here, i am stuck because i can't see to change session or shutdown/reboot. anyone else experience this?

also, i'm having a tough time getting stuff to run at start, i put stuff in .xinitrc like many people and places have said, but nothing happened on reboot.


<edit> got all that stuff solved and i am now working on a guide.

---

### Post by benplaut on 2006-06-07
[SIZE="7"]DO NOT USE THIS!!![/SIZE]
[SIZE="4"]I wrote this tutorial exactly 1 year and 1 day ago.  Please stop using it... there's a much better method now available at 
[http://icculus.org/openbox/index.php/Help:Autostart](http://icculus.org/openbox/index.php/Help:Autostart)[/SIZE]
8-[
___________________________
ok, here's the easy way to get autostart that won't mess with your xinitrc, and can be used form gdm.

First, make the file ~/.config/openbox/autostart.sh.  In it modify the following to fit your needs.

```
gedit ~/.config/openbox/autostart.sh
```

Panels usually cooperate better if you let them load after the WM, so this is a bit different from others.

```
#!/bin/sh
# Auto-mounting drives
gnome-volume-manager &
# GTK themes... this is just one method
gnome-settings-daemon &
# Full paths never fail...
fbsetbg /home/dapper/Backgrounds/whatever.png & 
idesk &
conky &
wmwifi &
wmpower &
# Put yakuake near the end (if you want it), as it takes a while to load
yakuake &
pypanel &
# This prevents the panel from failing if it loads too fast
if pgrep pypanel
then exec openbox
else pypanel && exec openbox
fi
```

Panels are finicky... the little thing at the end should help.

OK, here's for gdm:

First,
```
chmod +x ~/.config/openbox/autostart.sh
```

Now, edit the session file:

```
sudo gedit /usr/share/xsessions/openbox-autostart.desktop
```

and insert the following into the file:

```
[Desktop Entry]
Encoding=UTF-8
Name=Openbox Autostart
Comment=Openbox with autostart goodness
Exec=/home/dapper/.config/openbox/autostart.sh
Icon=
Type=Application
```
**Note**: Edit the Exec line to match your user account

finally,
```
sudo chmod +x /usr/share/xsessions/openbox-autostart.desktop
```
(i'm not sure if that's required, but it can't hurt)
>>>>>>><<<<<<<

i'll write up a little bit on customizing idesk (all those icons) and pypanel later.  Conky is well documented... play around with it.

openbox ftw!!!11!!1!

<edit>
typos

<edit2>

you can find all of my config here:
[http://www.ubuntuforums.org/showpost.php?p=1109087&postcount=168](http://www.ubuntuforums.org/showpost.php?p=1109087&postcount=168)

<edit3>
STOP USING THIS! IT'S OLD!

---

### Post by raublekick on 2006-06-07
awesome dude, you mind if i throw that into my guide (credited to you, of course)? i just started writing this part and your way is much more generic.

---

### Post by benplaut on 2006-06-07
[QUOTE=raublekick]awesome dude, you mind if i throw that into my guide (credited to you, of course)? i just started writing this part and your way is much more generic.[/QUOTE]

you have my blessing :)

---

### Post by raublekick on 2006-06-08
sweet man. my "guide" is pretty much done, just gotta post it on here. it's pretty much just a future resource for me, but it consolidates lots of info found from various sources.

---

### Post by benplaut on 2006-06-08
okey dokey... looking forward to it.

Make sure to include one important part: the #openbox IRC channel on irc.oftc.net

the guys in there are helpful as anything...

---

### Post by raublekick on 2006-06-08
radd, will do.

---

### Post by egon spengler on 2006-06-08
[QUOTE=PapaWiskas]Also I used feh to set a background, but when I logged back in the background was blank again....how do I get my desktop image to stay?[/QUOTE]

Feh creates a file called ~/.fehbg with the path to the last set background. If you add the line [code]eval `cat .fehbg`/[code] to your .xinitrc it should set the background on start. I assume you can add something similar to an openbox autostart file but of course you'd need the full path.

A better, imo of course, wallpaper setter is [nitrogen](http://minuslab.net/code/nitrogen/). I got no idea if it's in Dapper repos but it wasn't in Breezy and so you may need to compile though

edit:
Forgot to say, [planet openbox](http://planetob.openmonkey.com/) is worth a look

---

### Post by Hanj on 2006-06-08
A big thanks for all the tips in this thread. Got me to try OpenBox, and so far I really like it. Some things I'm missing though, maybe someone can help:
1. Is there any way I can get a sound volume control and a battery level indicator in pypanel?
2. When I select "suspend" from the gnome logout menu, which command is being run? It would be nice to be able to do this from the terminal.
3. Is there any way I can map the OpenBox menu to a keyboard shortcut? When I have some program in fullscreen I have to switch to a new workspace and right-click on the desktop just to launch a program, which is quite annying.

---

### Post by raublekick on 2006-06-08
[QUOTE=Hanj]A big thanks for all the tips in this thread. Got me to try OpenBox, and so far I really like it. Some things I'm missing though, maybe someone can help:
1. Is there any way I can get a sound volume control and a battery level indicator in pypanel?
2. When I select "suspend" from the gnome logout menu, which command is being run? It would be nice to be able to do this from the terminal.
3. Is there any way I can map the OpenBox menu to a keyboard shortcut? When I have some program in fullscreen I have to switch to a new workspace and right-click on the desktop just to launch a program, which is quite annying.[/QUOTE]


1. All I can think of off the top of my head is to run gnome-panel. It just places the gnome panel right at the top, so basically you will be running a super light gnome. There has got to be a better way though. 

2. I think running
```
sudo shutdown -z
``` should do it.  Check [this site out for more info. ]("http://enterprise.linux.com/article.pl?sid=05/05/04/1219226&tid=89")

3. It doesn't have one by defauly, but add this to your rc.xml file under the keybindings:
```
<keybind key="A-F1">
    <action name="ShowMenu"><menu>root-menu</menu></action>
  </keybind>
```

---

### Post by Hanj on 2006-06-08
> There has got to be a better way though. Yeah, that's what I thought too. I really like pypanel, so it would be great to be able to use it.

> I think running shutdown -z should do itStrange. I get this:
```
$: ~ > sudo shutdown -z
Password:
shutdown: invalid option -- z
Usage:    shutdown [-akrhHPfnc] [-t secs] time [warning message]
                  -a:      use /etc/shutdown.allow
                  -k:      don't really shutdown, only warn.
                  -r:      reboot after shutdown.
                  -h:      halt after shutdown.
                  -P:      halt action is to turn off power.
                  -H:      halt action is to just halt.
                  -f:      do a 'fast' reboot (skip fsck).
                  -F:      Force fsck on reboot.
                  -n:      do not go through "init" but go down real fast.
                  -c:      cancel a running shutdown.
                  -t secs: delay between warning and kill signal.
                  ** the "time" argument is mandatory! (try "now") **

```

Adding those lines to rc.xml worked fine though. Thanks alot!

---

### Post by raublekick on 2006-06-08
Hmm... that site I linked to listed it, so I assumed it would work. Perhaps there is a suspend command?

---

### Post by Hanj on 2006-06-08
Well there is a command called suspend, but it doesn't do anything on my system (and there's no man page and no --help switch).

[Edit]I found out that I could run gnome-power-preferences and make it show a system tray icon, so this solves the problem of showing a battery indicator in the panel. However, when I right click the battery and select Suspend, it just activates the screensaver. I find all this quite strange since it works from within Gnome. I have gnome-power-manager running in the background btw (don't know if that matters)[/Edit]

---

### Post by raublekick on 2006-06-08
very odd. i don't run linux on my laptop so i can't really be of service beyond this point :\



my how-to is up:
[http://ubuntuforums.org/showthread.php?t=192106](http://ubuntuforums.org/showthread.php?t=192106)

please leave suggestions orcheck the bottom for the stuff i still want to do.

---

### Post by fortherose on 2006-06-08
I am new to this forum and not too sure how to use it, but here goes.  I don't know if I'm speaking to a group or an individual, but here is my question.  How and where do I input the following data, in order to improve the performance of my ATI Radeon x700 on my laptop.  I don't know much about programming, but I can follow directions well.  Thank you very much...James

Section "Device"
   Identifier  "card0"
   Driver      "fglrx"
   Option       "no_accel" "no"
   Option       "no_dri" "no"
   Option       "DynamicClocks" "on"
   Option       "mtrr" "on"
   Option       "DesktopSetup" "Single"
   Option       "ScreenOverlap" "0"
   Option       "Capabilities" "0x00000000"
   Option       "CapabilitiesEx" "0x00000000"
   Option       "VideoOverlay" "on"
   Option       "OpenGLOverlay" "off"
   Option       "CenterMode" "off"
   Option       "PseudoColorVisuals" "off"
   Option       "Stereo" "off"
   Option       "StereoSyncEnable" "1"
   Option       "FSAAEnable" "no"
   Option       "FSAAScale" "1"
   Option       "FSAADisableGamma" "no"
   Option       "FSAACustomizeMSPos" "no"
   Option       "FSAAMSPosX0" "0.000000"
   Option       "FSAAMSPosY0" "0.000000"
   Option       "FSAAMSPosX1" "0.000000"
   Option       "FSAAMSPosY1" "0.000000"
   Option       "FSAAMSPosX2" "0.000000"
   Option       "FSAAMSPosY2" "0.000000"
   Option       "FSAAMSPosX3" "0.000000"
   Option       "FSAAMSPosY3" "0.000000"
   Option       "FSAAMSPosX4" "0.000000"
   Option       "FSAAMSPosY4" "0.000000"
   Option       "FSAAMSPosX5" "0.000000"
   Option       "FSAAMSPosY5" "0.000000"
   Option       "UseFastTLS" "0"
   Option       "BlockSignalsOnLock" "on"
   Option       "UseInternalAGPGART" "no"
   Option       "ForceGenericCPU" "no"
   Option       "KernelModuleParm" "agplock=0"
   Option       "PowerState" "1"
   BusID       "PCI:1:0:0"
EndSection

---

### Post by fortherose on 2006-06-08
I am new to this forum and not too sure how to use it, but here goes. I don't know if I'm speaking to a group or an individual, but here is my question. How and where do I input the following data, in order to improve the performance of my ATI Radeon x700 on my laptop. I don't know much about programming, but I can follow directions well. Thank you very much...James

Section "Device"
Identifier "card0"
Driver "fglrx"
Option "no_accel" "no"
Option "no_dri" "no"
Option "DynamicClocks" "on"
Option "mtrr" "on"
Option "DesktopSetup" "Single"
Option "ScreenOverlap" "0"
Option "Capabilities" "0x00000000"
Option "CapabilitiesEx" "0x00000000"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
Option "CenterMode" "off"
Option "PseudoColorVisuals" "off"
Option "Stereo" "off"
Option "StereoSyncEnable" "1"
Option "FSAAEnable" "no"
Option "FSAAScale" "1"
Option "FSAADisableGamma" "no"
Option "FSAACustomizeMSPos" "no"
Option "FSAAMSPosX0" "0.000000"
Option "FSAAMSPosY0" "0.000000"
Option "FSAAMSPosX1" "0.000000"
Option "FSAAMSPosY1" "0.000000"
Option "FSAAMSPosX2" "0.000000"
Option "FSAAMSPosY2" "0.000000"
Option "FSAAMSPosX3" "0.000000"
Option "FSAAMSPosY3" "0.000000"
Option "FSAAMSPosX4" "0.000000"
Option "FSAAMSPosY4" "0.000000"
Option "FSAAMSPosX5" "0.000000"
Option "FSAAMSPosY5" "0.000000"
Option "UseFastTLS" "0"
Option "BlockSignalsOnLock" "on"
Option "UseInternalAGPGART" "no"
Option "ForceGenericCPU" "no"
Option "KernelModuleParm" "agplock=0"
Option "PowerState" "1"
BusID "PCI:1:0:0"
EndSection

---

### Post by graabein on 2006-06-08
I have a question. I saw on planet openbox that someone was working on a pager. What does that do? Is it something that can be incorporated in pypanel or is it something else? Sort of like holding down Alt+Tab? Or is it more like a notification area for tomboy and gaim etc?

---

### Post by Hanj on 2006-06-08
Um, fortherose, that doesn't seem to be an ObenBox question? Maybe you should post it as a separate thread?

Anyway, seems like the solution to my suspend problem was to simply do an MS-style reboot :)

---

### Post by benplaut on 2006-06-08
to answer two questions, pypanel can't b changed very much.  You can't add any indicators, but i really like the pager.  I've set mine to right click on it to go right, left click to go left.  Put it in the corner of the screen and it's very fast.

For all the monitors and pager stuff that you need, look into the Dockapps.  Grab a few from [http://dockapps.org/](http://dockapps.org/) , make, make install, and just run the program to put it in the dock.

Put them in your autostart file to make them run automagikely, and make sure the dock is where you want it, this can be set from your rc.xml, or from obconf.

Here's what i've found works best (in rc.xml) in terms of not messing with other windows:

```
<dock>
  <position>Floating</position>
  <stacking>Bottom</stacking>
  <direction>Vertical</direction>
  <floatingX>0</floatingX>
  <floatingY>0</floatingY>
  <autoHide>yes</autoHide>
  <hideDelay>300</hideDelay>
  <moveButton>A-Left</moveButton>
</dock>
```

---

### Post by benplaut on 2006-06-08
[QUOTE=Hanj]Um, fortherose, that doesn't seem to be an ObenBox question? Maybe you should post it as a separate thread?

Anyway, seems like the solution to my suspend problem was to simply do an MS-style reboot :)[/QUOTE]

try looking into the acpi and apm commands... they deal with suspend and hibernate.  Newer computers usually have acpi, but only apm has a command
```
apm --suspend
```  Anyway, it has to do with those.

Later i'll make a little dialog for yall with turn off, reboot, etc stuff... like the old gnome one was (the new one can be cloned in python, i only know bash)

---

### Post by Hanj on 2006-06-09
I've looked at acpi commands already, but no luck. apm just gives me an error saying I have no apm support in my kernel. Anyway, as I said, after a reboot suspend works ok using the gnome-power-preferences systray icon, so I'm happy.

---

### Post by benplaut on 2006-06-09
ok, good :)

---

### Post by zikki on 2006-06-13
Guys, thank you very much. I really prefer OpenBox with PyPanel to Gnome or KDE, but there is one question - is there any way to replicate "menu button" in pypanel? Maybe putting a link in a launcher to some kind of program that just displays gnome menu? Do you know anything about that?

Thanks in advance.

UPDATE:
Looks like apwal could be a good candidate for a small launcher application (sudo apt-get install apwal)

---

### Post by kuad on 2006-06-14
@zikki, I use gmrun as an application launcher. Otherwise just customise the openbox menu to your liking.

Does anyone know if its possible to make the openbox menu show up at a specific location? eg the centre of the screen. I'm using hotkeys to open the menu, but it always opens wherever the mouse cursor is - which is a bit irritating because I'm minimising the use of the mouse and keep losing track of wherever the cursor is.

---

### Post by zikki on 2006-06-14
Thanks for gmrun, Kuad. But actually what I want is something that can replicate gnome start button in ubuntu. I'm missing it a lot in pypanel.

---

### Post by kuad on 2006-06-14
[QUOTE=zikki]Thanks for gmrun, Kuad. But actually what I want is something that can replicate gnome start button in ubuntu. I'm missing it a lot in pypanel.[/QUOTE]
I don't think pypanel can do menus. You can customise your Openbox menu to get something similar but it will take a little work ie changing menu.xml either by hand or using obmenu [http://obmenu.sourceforge.net/](http://obmenu.sourceforge.net/) which should be easier.

Have a look at [http://www.icculus.org/openbox/docs.php](http://www.icculus.org/openbox/docs.php) for more info about customising

---

### Post by zikki on 2006-06-14
Kuad, I don't think pypanel is able to provide something like gnome menu either, but it can call an application through its launch panel, which in its turn can do anything. Right now I have apwal with ubuntu icon in launch panel and when I press it it launches apwal, which is pretty good, but needs setup. I want to find some application which can simply display ubuntu/debian menu.

---

### Post by GarethMB on 2006-06-14
I installed gnome theme switch to make openbox's themes look nicer. But now i have to use that and gnome theme manager to change the controls aspect of my theme in gnome. How can i remove gtk switch and restore gnome theme manager to its original functionality?

---

### Post by fuscia on 2006-06-14
[QUOTE=GarethMB]I installed gnome theme switch to make openbox's themes look nicer. But now i have to use that and gnome theme manager to change the controls aspect of my theme in gnome. How can i remove gtk switch and restore gnome theme manager to its original functionality?[/QUOTE]

if you don't normally use gnome (in other words, don't have gnome setup in any particular way), you could try the drastic measure of removing all the gnome configuration files.

---

### Post by GarethMB on 2006-06-14
[QUOTE=fuscia]if you don't normally use gnome (in other words, don't have gnome setup in any particular way), you could try the drastic measure of removing all the gnome configuration files.[/QUOTE]
No. I use gnome 90% of the time. I want gnome theme manager to behave normally.

---

### Post by fuscia on 2006-06-14
[QUOTE=GarethMB]No. I use gnome 90% of the time. I want gnome theme manager to behave normally.[/QUOTE]

what i would do (not recommended by the supposed 'sane' faction) is uninstall gnome theme manager, get rid of the config files associated with it and then reinstall it. i think you'd also have to hunt down all the theme switch files as well.

---

### Post by GarethMB on 2006-06-14
Any ideas how to go about that. I tried doing it through synaptic but it's still the same.

---

### Post by fuscia on 2006-06-14
[QUOTE=GarethMB]Any ideas how to go about that. I tried doing it through synaptic but it's still the same.[/QUOTE]

when you uninstalled gnome theme switch, did you get rid of its files, or just uninstall it? if you left the files, they'll probably still have an effect on gnome theme manager. if you get rid of switch's files, gnome theme manager will probably revert to its normal behavior. i've never used switch, so i don't know what the file(s) would be called. you could open nautilus, select 'show hidden files' and look through the list to see if there is a file. if not, it may be a sub file.

---

### Post by GarethMB on 2006-06-14
[QUOTE=fuscia]when you uninstalled gnome theme switch, did you get rid of its files, or just uninstall it? if you left the files, they'll probably still have an effect on gnome theme manager. if you get rid of switch's files, gnome theme manager will probably revert to its normal behavior. i've never used switch, so i don't know what the file(s) would be called. you could open nautilus, select 'show hidden files' and look through the list to see if there is a file. if not, it may be a sub file.[/QUOTE]
I used remove configuration files option. Perhaps i'll go on a file hunt, this is such a pain. I just reinstalled Dapper. On a side not fuscia now you have a decent computer do you prefer openbox to KDE still?

---

### Post by fuscia on 2006-06-14
[QUOTE=GarethMB]I used remove configuration files option. Perhaps i'll go on a file hunt, this is such a pain. I just reinstalled Dapper.[/quote]

yup, the type of problem you've been having is no fun at all.

> On a side note fuscia now you have a decent computer do you prefer openbox to KDE still?

it depends on my mood. everything is pretty zippy now, so speed is no longer an issue. i've spent more time in both kde and gnome since i got my new machine. they are more fun to play with, but i still think that for actually using my computer to do something other than play with the themes and icons, i still prefer openbox. the right click menu, using obmenu, makes it so easy to set it up exactly how i want it (something i appreciate even more after playing with xfce's bugged up menu editor this morning).

btw, i'm enjoying thunar. it's the first file manager i've ever been enthusiastic for.

EDIT: just discovered 'custom menu' in kde and it's even easier than obmenu. i think that may have just pushed me over to the dark side.

---

### Post by GarethMB on 2006-06-14
[QUOTE=fuscia]yup, the type of problem you've been having is no fun at all.



it depends on my mood. everything is pretty zippy now, so speed is no longer an issue. i've spent more time in both kde and gnome since i got my new machine. they are more fun to play with, but i still think that for actually using my computer to do something other than play with the themes and icons, i still prefer openbox. the right click menu, using obmenu, makes it so easy to set it up exactly how i want it (something i appreciate even more after playing with xfce's bugged up menu editor this morning).

btw, i'm enjoying thunar. it's the first file manager i've ever been enthusiastic for.[/QUOTE]
Check your PMs

---

### Post by fuscia on 2006-06-14
[QUOTE=GarethMB]Check your PMs[/QUOTE]

just did and sent you a response. you may be planning on purging more than you need to, but if it's all switch stuff, i can't see the harm. there's something beautifully silent and final about file genocide.

EDIT: btw, you *do* realize i have no idea what i'm talking about, don't you?

---

### Post by zikki on 2006-06-15
Guys, anyone has problems during pypanel startup?
I noticed that if I power-up my computer, sometimes, pypanel fails to load completely, or loads after all other applications have loaded, therefore, I have no tray icons. I had to switch back to fbpanel instead :( 

Is there anyone who experience the same problem? :sad:

---

### Post by raublekick on 2006-06-15
[QUOTE=zikki]Guys, anyone has problems during pypanel startup?
I noticed that if I power-up my computer, sometimes, pypanel fails to load completely, or loads after all other applications have loaded, therefore, I have no tray icons. I had to switch back to fbpanel instead :( 

Is there anyone who experience the same problem? :sad:[/QUOTE]


actually i think i do. the launcher part of pypanel has not worked for me, and when i login it seems to flicker, but your explaination makes more sense.

---

### Post by graabein on 2006-06-16
I have installed pypanel from universe but it won't start. I posted a thread on the  [general desktop forum]("http://www.ubuntuforums.org/showthread.php?t=197362").

---

### Post by fuscia on 2006-06-16
[QUOTE=graabein]I have installed pypanel from universe but it won't start. I posted a thread on the  [general desktop forum]("http://www.ubuntuforums.org/showthread.php?t=197362").[/QUOTE]

i installed it from universe, in both breezy and dapper, and have no problem at all. the error message you have in that other thread seems more like a python problem than a pypanel problem, though.

---

### Post by Adrenal on 2006-06-16
For some reason, whenever i try to run 'pypanel', i get 
> Traceback (most recent call last):
  File "/usr/bin/pypanel", line 957, in ?
    PyPanel(display.Display())
  File "/usr/lib/python2.4/site-packages/Xlib/display.py", line 80, in __init__
    self.display = _BaseDisplay(display)
  File "/usr/lib/python2.4/site-packages/Xlib/display.py", line 67, in __init__
    apply(protocol.display.Display.__init__, (self, ) + args, keys)
  File "/usr/lib/python2.4/site-packages/Xlib/protocol/display.py", line 123, in __init__
    self.default_screen = min(self.default_screen, len(self.info.roots) - 1)
  File "/usr/lib/python2.4/site-packages/Xlib/protocol/rq.py", line 1371, in __getattr__
    raise AttributeError(attr)
AttributeError: roots

Any thoughts

---

### Post by zikki on 2006-06-16
Adrenal, please, follow this link: 
[http://www.linuxforums.org/forum/linux-desktop-x-windows/50612-pypanel.html](http://www.linuxforums.org/forum/linux-desktop-x-windows/50612-pypanel.html)

---

### Post by zikki on 2006-06-16
Guys, I think I somehow managed to create a startup script, that prevents pypnanel from stalling on power-up. Here's the script I'm using right now.

```
#!/bin/sh


# Loading Openbox
openbox & wmpid=$!

# Trying to start pypanel
pypanel &

# Cheking if pypanel appeared on the screen
# xprop -name PyPanel - case sensitive!
until sleep 6; xprop -name PyPanel; do killall pypanel; sleep 0; pypanel& done



# Loading untrayed services...
export OOO_FORCE_DESKTOP=gnome # Telling OpenOffice to use GNOME themes
gnome-volume-manager & # Drives' automount
GSDPID=`pidof gnome-settings-daemon` # Loading GNOME settings, if not loaded.
if [  "x$GSDPID" == "x" ]; then gnome-settings-daemon & fi
nautilus &
gkrellm &

# Loading trayed services...
update-notifier & # Loading Update Manager
glipper & # Gnome Clipboard
gaim & 
mail-notification &
amule &



# Waiting for openbox to finish
wait $wmpid

# End

```

---

### Post by K.Mandla on 2006-06-16
Good stuff in this thread. My openbox stories usually begin with ...

openbox | obconf | openbox-themes ... to get stuff going
xfce4-terminal ... I just like this terminal best
feh ... i need some kind of background
thunar ... i'm used to it, i like it
pypanel ... good enough, and light
mousepad ... gotta have something to edit with ... no way will I use vi
swiftfox ... :D

After that, it depends on what mood I'm in. :D

---

### Post by MichaelOnTheSound on 2006-06-17
i'm always available for open chatter...it's my specialty!!

---

### Post by graabein on 2006-06-17
There's a new chat in town...

---

### Post by ijanos on 2006-08-19
Hi!

yesterday (after an upgrade i think) my openbox (with all gui apps) started to use some kind of text-antialias. I just want to turn it off, and i'm interested in the CLI way. can anyone help me? I have simply no idea which config file should be responsible for this.

---

### Post by fuscia on 2006-08-19
> **ijanos said:**
> Hi!

yesterday (after an upgrade i think) my openbox (with all gui apps) started to use some kind of text-antialias. I just want to turn it off, and i'm interested in the CLI way. can anyone help me? I have simply no idea which config file should be responsible for this.

if it's system wide, wouldn't that be an .xorg thing? sorry, i don't know.

---

### Post by ijanos on 2006-08-19
np 

It's fun to trail such things, at least for me :) 
Now i'm a bit closer, the thing maybe connected with the files in /etc/fonts 
And yes it is system wide, GDM changed too. 
 
ps: Don't you experienced such things with the last updates. If I am right then things changed after this update:

```
[UPGRADE] gtk2-engines-clearlooks 1:2.7.4.is.2.6.9-0ubuntu1 -> 1:2.7.4.is.2.6.10-0ubuntu1
[UPGRADE] gtk2-engines-industrial 1:2.7.4.is.2.6.9-0ubuntu1 -> 1:2.7.4.is.2.6.10-0ubuntu1
[UPGRADE] libcairo2 1.2.0-0ubuntu1quinn2 -> 1.2.2-0ubuntu2
[UPGRADE] libdrm2 2.0+cvs20060625 -> 2.0.2+cvs20060815
[UPGRADE] libfreetype6 2.1.10-1ubuntu2.2 -> 2.2.1-0ubuntu1
[UPGRADE] libvte-common 1:0.12.2-0ubuntu1 -> 1:0.13.5-0ubuntu2
[UPGRADE] libvte4 1:0.12.2-0ubuntu1 -> 1:0.13.5-0ubuntu2
[UPGRADE] mesa-utils 6.5.1-0ubuntu16 -> 6.5.1+cvs20060815

```

---

### Post by graabein on 2006-08-23
You look scary ijanos! You could be in a Tim Burton movie! Just kidding :grin:

---

### Post by PapaWiskas on 2006-08-31
Ok...where the heck is the .xintric file located....I want to be able to edit it to set feh to use a certain background image....

---

### Post by Kindred on 2006-09-01
> **PapaWiskas said:**
> Ok...where the heck is the .xintric file located....I want to be able to edit it to set feh to use a certain background image....

.xinitrc goes in your home dir. 

Mine looks like this: 

```
#!/bin/sh

#
# ~/.xinitrc
#
# Executed by startx (run your window manager from here)
#

# exec wmaker
# exec startkde
# exec icewm
# exec blackbox
# exec fluxbox
# exec startxfce4
# exec gnome-session
# exec ion3
# exec ratpoison

mplayer $HOME/.sounds/startup.wav &
conky -c $HOME/.dotfiles/conky/conkyrc &
conky -c $HOME/.dotfiles/conky/conkyrc1 &
conky -c $HOME/.dotfiles/conky/conkyrc2 &
conky -c $HOME/.dotfiles/conky/conkyrc3 &
eval `cat $HOME/.fehbg` &
exec dbus-launch --exit-with-session openbox
exec openbox
```

---

### Post by ijanos on 2006-09-01
I just faced another font problem. I think i'd leave them alone
There is only one dot in my ö character :-s Funny isnt it? :D
Anybody ever heard about reset font settings or something like that? :D

> **graabein said:**
> You look scary ijanos! You could be in a Tim Burton movie! Just kidding :grin:
:twisted: This is my just-wake-up-at-a-summer-festival-after-3-hours-of-sleep looking :)

---

### Post by ijanos on 2006-09-16
I found another pypanel workaround (the one mentioned in the thread doesnt work for me)
simply put time.sleep(1) in the ~/.pypanelrc so pypanel will wait a second before start.

---

### Post by bonzodog on 2006-09-17
I have just started using OpenBox, in Zenwalk, admittedly.
Used mmaker to set up the menu, and got obconf and openbox packages from linuxpackages.net (the slackware packages site).

I have installed imlib2 and pypanel works from the command line.

As I also have xfce installed, and my wife wants that, I managed to get gdm to start openbox, but I now need to find a way of getting openbox to start pypanel and the xfce-mcs-manager (to get gtk themes and xfrun) on startup.

I was thinking that the easiest way of doing it would be to create an xinitrc file in /etc/X11/xinit/ that starts these things then point /etc/X11/gdm/XSession to it.

Would I be correct?

---

### Post by ijanos on 2006-09-17
> **bonzodog said:**
> I have just started using OpenBox, in Zenwalk, admittedly.
Used mmaker to set up the menu, and got obconf and openbox packages from linuxpackages.net (the slackware packages site).

I have installed imlib2 and pypanel works from the command line.

As I also have xfce installed, and my wife wants that, I managed to get gdm to start openbox, but I now need to find a way of getting openbox to start pypanel and the xfce-mcs-manager (to get gtk themes and xfrun) on startup.

I was thinking that the easiest way of doing it would be to create an xinitrc file in /etc/X11/xinit/ that starts these things then point /etc/X11/gdm/XSession to it.

Would I be correct?

Create script which start the things you want, eg:
```
#!/bin/sh
xfce-mcs-manager &
pypanel &
exec openbox
```

And modify your /usr/share/xsessions/openbox.desktop file:
```
[Desktop Entry]
Encoding=UTF-8
Name=Openbox
Comment=Use this session to run Openbox as your desktop environment
Exec=/path-to-your/script
Icon=
Type=Application

```

And about the xfce-mcs-mananger, you can set GTK2 theme and font using gtk-theme-switch so you dont have to run xfce-mcs.

---

### Post by DJiNN on 2006-10-01
I have just started trying OB3 out (On Ubuntu). Really like it, "Almost" as much as FluxBox. :) 

But just wanted to say for anyone reading this thread, that there is a program out there called "[obmenu]("http://obmenu.sourceforge.net/")" if you would like to easily change the menu in OB. Works really well and is certainly a lot easier than doing it by hand. :)

---

### Post by kerry_s on 2006-10-01
I usally just do my menus by hand, i just dont like installing extra apps for something i can do myself. It also gives me a chance to learn how it all works, gui's aren't always dependable. Right now i'm running openbox in edgy which is still constantly updating packages, in fact just to get obconf working you've got to fix the link's. I'm trying something different with this install, i'm using konqueror as my all in one, it's like a mini mini kde. I've got konqueror doing the desktop,filemanager,web browser,pic viewer, and what ever else i can make it do. It's still a little bit slow starting up(just like kde,lol). But once it's loaded it works just fine, it's way faster than a kde install. I run duelmonitors and kde has great dual screen support.

---

### Post by Kindred on 2006-10-01
Openbox and Konqueror, that's a new one to me. :)

Currently i'm using openbox + thunar + xfce4-panel.

Agreed about the menus, I prefer to do that myself after trying I think menumaker(?) and it made quite a mess, besides nothing would ever do it how I prefer and it's not that hard.

---

### Post by kerry_s on 2006-10-01
That's almost like the setup before this one. I had openbox + rox + xfce4-panel on dapper. I like to try something different with each install, and since konqueror has all that bloatware with it i thought i would take advantage of it.LOL. I was looking around after i installed konqueror and realized alot of the kde apps was there like for the desktop and kicker. But since i'm not running kde it was just sitting there so i put it to use. It saved on not having to install other app's to do the same thing. I just launch it at start up in my .xsession->

```
#!/bin/sh

xset s off off &
xset +dpms &
xset dpms 0 0 300 &
sudo athcool on &
sudo conky &
kicker &
kdesktop &
kdeinit &
wmix &


exec openbox 

```

---

### Post by raublekick on 2006-11-09
hey guys, please check this:

[http://ubuntuforums.org/showthread.php?t=296239](http://ubuntuforums.org/showthread.php?t=296239)

---

### Post by raublekick on 2006-11-10
some weird openbox issues in edgy:

installed pypanel
~$: pypanel
bash: pypanel: command not found
~$: locate pypanel
~$: 
~$: whereis pypanel
pypanel: /usr/share/pypanel /usr/share/man/man1/pypanel.1.gz

so i guess the pypanel package just installs the pypanel .png and some documentation? 


also, i cannot find an rc.xml on my system anywhere! there was no menu either, but luckily menumaker makes one from nothing. 

did someone completely bork the packaging for these or is it just a weird quirk on my machine?


third thing, how the heck do i change the font? it's really really small compared to what Gnome uses.

---

### Post by Kindred on 2006-11-10
I would usually expect openbox to install a copy of rc.xml and menu.xml in /etc/xdg/openbox

The fonts for the openbox menu and titlebars are set in the theme it uses so I would copy one from /usr/share/themes and put it in ~/.themes and edit it, or just download some more or something...

---

### Post by commodore on 2006-12-26
Edgy sucks so bad. Pypanel and obconf don't work at all. Also, I made that xsession and autostart stuff but I get this error when logging in:
"Xession: unable to launch "/home/ville/.config/openbox/autostart.sh" Xsession --- "/home/ville/.config/openbox/autostart.sh" not found; falling back to default session"

---

### Post by fuscia on 2006-12-26
> **commodore said:**
> Edgy sucks so bad. Pypanel and obconf don't work at all. Also, I made that xsession and autostart stuff but I get this error when logging in:
"Xession: unable to launch "/home/ville/.config/openbox/autostart.sh" Xsession --- "/home/ville/.config/openbox/autostart.sh" not found; falling back to default session"

i've pretty much had my fill of trying to get pypanel to work, but i've had no trouble with obconf, though it did require setting it up differently than in dapper (i don't recall what it was i had to do, unfortunately).

---

### Post by bonzodog on 2006-12-26
pypanel can be awkward - I for one do not use an autostart.sh script, I just adapt the xinitrc.openbox file in /etc/X11/xinit/. But you do need to add the 'wait 1' line to the file along with all progs to start.

To add openbox to gdm, all I did was create an openbox.desktop file, and add the openbox option to /etc/X11/gdm/Xsession. In that file you tell it to go look at /etc/X11/xinit/xinitrc.openbox. Then I adapted the xinitrc file to start what I needed. Pypanel 2.4 still doesn't start all the time though.

---

### Post by K.Mandla on 2006-12-26
> **commodore said:**
> Edgy sucks so bad. Pypanel and obconf don't work at all. Also, I made that xsession and autostart stuff but I get this error when logging in:
"Xession: unable to launch "/home/ville/.config/openbox/autostart.sh" Xsession --- "/home/ville/.config/openbox/autostart.sh" not found; falling back to default session"
Maybe someone has mentioned this already, but the obconf issue can be fixed by making links from the missing libraries to the ones available.

```
cd /usr/lib/
sudo ln libobparser.so.0.4.0 libobparser.so.1
sudo ln libobrender.so.0.4.0 libobrender.so.1
```
As far as the PyPanel issue, the last I heard there was a workaround, but I haven't used it so I can't vouch for it. (I don't use it. I actually like OB better without a panel.)

[http://www.ubuntuforums.org/showthread.php?t=280236](http://www.ubuntuforums.org/showthread.php?t=280236)

---

### Post by commodore on 2006-12-28
Without a panel? How do you change windows? Alt+TAB? Just clicking?

Anyways I was editing my menu.xml and then clicked on reconfigure and now it uses the default menu. I can't get my custom menu back. I tried changing the menu.xml file (thought I made a syntax error) but it still doesn't work.

EDIT: I did actually f up the menu.xml. I used failsafe terminal session and started openbox there so I saw the problem. Sorry for BUMPing the thread :blush:

---

### Post by K.Mandla on 2006-12-28
You can switch workspaces via the mouse wheel over the desktop, or with the left CTRL+ALT+Right and CTRL+ALT+Left keys. Is that what you meant?

As far as switching windows, I just use the right click > Desktop menu or the press of the mouse wheel.

---

### Post by bonzodog on 2006-12-28
I actually only have the panel for the system tray and clock, as I use Quod Libet and Gaim.

---

### Post by K.Mandla on 2006-12-28
By the way, someone posted this on my blog as a solution to the broken PyPanel thing. It sounds like just a rebuild of python-xlib, but there might be more than that involved.

[quote=dr.zombo]Hey,

I got the same problem with pypanel for the last 2 hours, but then I did the following trick:

do an apt-get remove python-xlib

clear all dependencies for python-xlib:

apt-get install debhelper python-dev python-xlib libx11-dev libxft-dev libxpm-dev libimlib2-dev dpatch sed python-central

grab it from here:
[http://sourceforge.net/projects/python-xlib/](http://sourceforge.net/projects/python-xlib/)
unpack, and install it with python setup.py install

and finaly cd to pypanel and python setup.py install
taddaaa it works!!

cheers, dr.zombo[/quote]
It is, as yet, completely untested by me so I make no endorsement whatsoever. Try, test and use at your own risk. :shock: :oops: 8-[

---

### Post by fuscia on 2006-12-28
> **K.Mandla said:**
> By the way, someone posted this on my blog as a solution to the broken PyPanel thing. It sounds like just a rebuild of python-xlib, but there might be more than that involved.


It is, as yet, completely untested by me so I make no endorsement whatsoever. Try, test and use at your own risk. :shock: :oops: 8-[

finally!!! thanks.8)

---

### Post by K.Mandla on 2006-12-28
> **fuscia said:**
> finally!!! thanks.8)

Did it work? It would be cool if it did.

---

### Post by fuscia on 2006-12-28
> **K.Mandla said:**
> Did it work? It would be cool if it did.

sure did.

---

### Post by K.Mandla on 2006-12-28
Excellent! Someone should write it up as a howto. :D

---

### Post by fuscia on 2006-12-29
> **K.Mandla said:**
> Excellent! Someone should write it up as a howto. :D

more like a howididit - [http://ubuntuforums.org/showthread.php?p=1943620#post1943620](http://ubuntuforums.org/showthread.php?p=1943620#post1943620)

i used your name so they would burn down *your* barn if it doesn't work.

---

### Post by K.Mandla on 2006-12-29
Yeah, gee, thanks. #-o Just kidding. 

I'll try it in a few minutes and make sure it's working on my end too. It probably belongs in the wiki too, along with the obconf fix as Edgy-specific Openbox fixes. Sounds like a good project for me today. 

Thanks for being the guinea pig. :mrgreen:

---

### Post by K.Mandla on 2006-12-29
Well, it kind of worked for me, but I had to download the PyPanel source as well, and install it from there too.

So I'm guessing that the process is to get the python environment in place, download the python-xlib and PyPanel source, and install both through python?

(Funny that I'm spending this much time tinkering with something I don't even use. :roll: )

---

### Post by commodore on 2006-12-29
Why don't people use fbpanel? Is something wrong with that? I installed fbpanel and the only problem is that the "show desktop" button doesn't always work with the first try.

---

### Post by fuscia on 2006-12-29
> **K.Mandla said:**
> Well, it kind of worked for me, but I had to download the PyPanel source as well, and install it from there too.

So I'm guessing that the process is to get the python environment in place, download the python-xlib and PyPanel source, and install both through python?


i guess that's pretty much it.

---

### Post by K.Mandla on 2006-12-29
> **commodore said:**
> Why don't people use fbpanel? Is something wrong with that? I installed fbpanel and the only problem is that the "show desktop" button doesn't always work with the first try.
Beats me. I know most Openbox howtos mention PyPanel in the same breath, so perhaps there's a tendency to use it first. 

That being said, I think I'll give fbpanel a whirl. It can't be more cantankerous to set up than PyPanel under Edgy. :roll:

---

### Post by ice60 on 2006-12-29
i use fluxbox.

anyway, i used this tutorial to make my printscreen button take screenshots. also, pressing alt-print screen lets you take a screenshot of any part of the desktop -
[http://gentoo-wiki.com/TIP_Make_a_Screenshot_with_PrintScreen_Key](http://gentoo-wiki.com/TIP_Make_a_Screenshot_with_PrintScreen_Key)

i've got a show desktop key combo too, but i don't think it works with openbox :-k

it's probably different for openbox, but this is how i use the keybinding to show the desktop. in a file called ~.fluxbox/keys
x x :ShowDesktop #where x is the key you want to use :|

---

### Post by fuscia on 2007-01-06
just found this quote at [http://ports.openbsd.nu/x11/openbox](http://ports.openbsd.nu/x11/openbox)

[i]"Openbox works with your applications, and makes your desktop easier to
manage. This is because the approach to its development was the opposite
of what seems to be the general case for window managers. Openbox was
written first to comply with standards and to work properly. Only when
that was in place did the team turn to the visual interface."[/i]

i wonder if it's true.:-k

---

### Post by ijanos on 2007-01-07
> **fuscia said:**
> just found this quote at [http://ports.openbsd.nu/x11/openbox](http://ports.openbsd.nu/x11/openbox)

[i]"Openbox works with your applications, and makes your desktop easier to
manage. This is because the approach to its development was the opposite
of what seems to be the general case for window managers. Openbox was
written first to comply with standards and to work properly. Only when
that was in place did the team turn to the visual interface."[/i]

i wonder if it's true.:-k

Why do you think its not?

---

### Post by fuscia on 2007-01-07
> **ijanos said:**
> Why do you think its not?

i don't think it's not. i just don't know.

---

### Post by commodore on 2007-01-14
Is there a shortcut key to open the right-click menu?

---

### Post by bonzodog on 2007-01-15
hrm...I have stopped using the xfce-mcs-manager for gtk theming etc, and it took away my thunar icons !. So, I now use gtk-chtheme on my Zenwalk Linux box. Is there anyway of getting the icon theme mentioned in the ~/.gtkrc2.0 file?

---

### Post by fuscia on 2007-01-15
> **bonzodog said:**
> hrm...I have stopped using the xfce-mcs-manager for gtk theming etc, and it took away my thunar icons !. So, I now use gtk-chtheme on my Zenwalk Linux box. Is there anyway of getting the icon theme mentioned in the ~/.gtkrc2.0 file?

just write it in as *gtk-icon-theme-name= "stupidiconthemename"*.

---

### Post by K.Mandla on 2007-01-15
> **commodore said:**
> Is there a shortcut key to open the right-click menu?
Check the key bindings in ~/.config/openbox/rc.xml. I'm sure there's something in there you could use.

---

### Post by bonzodog on 2007-01-15
> **fuscia said:**
> just write it in as *gtk-icon-theme-name= "stupidiconthemename"*.

Cool!! thanks :D

---

### Post by fuscia on 2007-01-26
i was going to make a new thread about this, but i feel solidarity is important in this issue: openbox not only bakes cookies better that your grandmother, it makes them faster, too! let's face it, your grandmother has enough trouble keeping up with lwm. she's done. let the woman rest and switch to openbox. it's time for someone else to bake the cookies!

---

### Post by K.Mandla on 2007-01-27
Yes! I think. :-k

But definitely +1 for grandmothers, +1 for cookies and +1 for Openbox.

---

### Post by bonzodog on 2007-01-28
Heres a recent screenie of my openbox set-up on Zenwalk Linux:

[[img]http://xs211.xs.to/xs211/07035/openzen.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs211&d=07035&f=openzen.png)

I now use gtk-chtheme for gtk theming, and that is the wmtime dockapp with peksystray in the dock. Looks, and feels very clean. Have added in a font called 'Final Frontier' that I found on gnome-look.org in a pack of 30 fonts.

The Robot background is off deviant art, and is called 'clank'.

---

### Post by fuscia on 2007-01-28
looks good, bonzo. that gtk-chtheme is teh bomba!

---

### Post by K.Mandla on 2007-02-06
Sorry for the bump, but I gotta brag:

[center][[img]http://xs312.xs.to/xs312/07062/empty-desktop.jpg.xs.jpg[/img]](http://xs.to/xs.php?h=xs312&d=07062&f=empty-desktop.jpg) [[img]http://xs312.xs.to/xs312/07062/configs-desktop.jpg.xs.jpg[/img]](http://xs.to/xs.php?h=xs312&d=07062&f=configs-desktop.jpg) [[img]http://xs312.xs.to/xs312/07062/cluttered-desktop.jpg.xs.jpg[/img]](http://xs.to/xs.php?h=xs312&d=07062&f=cluttered-desktop.jpg)[/center]

Openbox on Arch, actually. Cut to look like Feisty Gnome. Pentium II Mobile stock, running at 300Mhz and 256Mb PC133, and it boots in under 40 seconds. :biggrin:

And I gotta give a +1 to dropping PyPanel for fbpanel or lxpanel. They are both more impressive to me: fbpanel is a definite step up, and lxpanel improves upon fbpanel even further.

---

### Post by bonzodog on 2007-02-27
Is it possible to change the mouse cursor theme in Openbox?

I guess it would be something like "gtk-cursor-theme-name", but it's not responding to that at the moment.
I found that if I put the icon theme name setting in .gtkrc.mine, it was always there regardless of how often I changed theme, btw.

---

### Post by bonzodog on 2007-03-04
ok, gonna bump this. I really could do with finding out how to change the mouse/pointer theme in openbox.

---

### Post by fuscia on 2007-03-04
in which directory are your mouse themes, bonzo? and, can you post the contents of your .gtkrc file?

---

### Post by bonzodog on 2007-03-04
My mouse themes live in ~/.icons, which is the standard.
My ~/.gtkrc2.0 file:
```

# -- THEME AUTO-WRITTEN DO NOT EDIT
include "/home/bonzodog/.themes/Rezlooks-expressive/gtk-2.0/gtkrc"

style "user-font" {
	font_name = "DejaVu Sans 9"
}

widget_class "*" style "user-font"

gtk-font-name="DejaVu Sans 9"

include "/home/bonzodog/.gtkrc.mine"

# -- THEME AUTO-WRITTEN DO NOT EDIT

```

I have the Icon definition in ~/.gtkrc.mine

---

### Post by fuscia on 2007-03-04
> **bonzodog said:**
> My mouse themes live in ~/.icons, which is the standard.

I have the Icon definition in ~/.gtkrc.mine

here's what i'm thinking: if the mouse theme is in the icon folder, wouldn't one have to indicate it with *gtk-icon-theme-name= "stupid_cursor_theme-name"*? (that's what messed up thunar, without changing the icon theme, for me.)

---

### Post by bonzodog on 2007-03-04
No, my current icon theme name points to the main Icon folder in /usr/share/icons, and uses a genuine Icon theme. 
However, there is a way of changing the mouse cursor theme as well. What I need is the keywords for it. 

There are Icon themes AND mouse themes in the root icon folder as well as my home ~/.icons folder. If I wanted to use a mouse theme from my home folder, I simply provide the full path.

---

### Post by K.Mandla on 2007-03-04
Mouse cursor themes are in ~/.Xdefaults, with the theme decompressed to ~/.icons. Add this to .Xdefaults ... 

```
Xcursor.theme:Vanilla-DMZ
```
or whatever theme you like, so long as the name matches the folder it live in, inside ~/.icons.

---

### Post by fuscia on 2007-03-04
> **K.Mandla said:**
> Mouse cursor themes are in ~/.Xdefaults, with the theme decompressed to ~/.icons. Add this to .Xdefaults ... 

```
Xcursor.theme:Vanilla-DMZ
```
or whatever theme you like, so long as the name matches the folder it live in, inside ~/.icons.

that's it! i had *Xcursor*theme: [stupidthemename]* in there and it wouldn't work. (i got that mess from an arch howto.)

---

### Post by Graduate on 2007-03-05
1) Sorry if this is not relevant to this thread but I'm looking for a certain theme. [http://www.boxwhore.org/modules/myalbum/photo.php?lid=161](http://www.boxwhore.org/modules/myalbum/photo.php?lid=161) The description says that the theme is called cutthroat, but I can't find a theme with such a name.


2) Also, is there a way to edit pypanel's appearance?

---

### Post by fuscia on 2007-03-06
> **Graduate said:**
> 1) Sorry if this is not relevant to this thread but I'm looking for a certain theme. [http://www.boxwhore.org/modules/myalbum/photo.php?lid=161](http://www.boxwhore.org/modules/myalbum/photo.php?lid=161) The description says that the theme is called cutthroat, but I can't find a theme with such a name.

i think it's really called 'cuttooth' - [http://www.gnome-look.org/content/show.php?content=48087](http://www.gnome-look.org/content/show.php?content=48087)


> 2) Also, is there a way to edit pypanel's appearance?

what are you trying to do? have you had a look at .pypanelrc, yet?

relevant to 'random'? pretty much can't go wrong there.

---

### Post by Graduate on 2007-03-06
lol, didn't think about the random part

But thanks for the theme. As for pypanel, I want to change the clock to 12h format, maybe change the invisible background and change the text from bright blue to black. I will definitely play around with pypanelrc. Thanks for the quick reply.

---

### Post by urukrama on 2007-03-30
Ok, fuscia, your continuous praise of OpenBox has finally touched my heart!

I got an old computer with little RAM that ran Ubuntu, but veerrryy slowly. I decided to give the light wm-s another try: installed fluxbox (which I liked before), icewm (which I didn't like, but didn't spend much time with) and openbox (which I tried before but gave up on almost immediately).

Now, after trying all of them out, and customising as much as I can to suit my needs and tastes, I've come to really love OpenBox (thanks to raublekick's excellent howto). Icewm is not bad either, and way easier to configure and customise than I thought, and fluxbox still has its charms, but Openbox caught me. I like its ease, speed, and spartan simplicity. 

So much so, that I also got it set up on my main machine. It revolutionises the way I work with my computer: by having less, it helps me to focus more on what I actually need to do with my machine.

I might have a few more questions as I explore Openbox more, but so far, this man is happy. :)

---

### Post by fuscia on 2007-03-30
that's great, uru. i use it on my not even year old laptop. i don't need an 'experience' to open an app. i just need it opened *now*.

---

### Post by K.Mandla on 2007-03-30
> **fuscia said:**
> i don't need an 'experience' to open an app. i just need it opened *now*.
Well said.

I spent the last week on the Feisty beta with Gnome and while it's a fantastic step forward for Ubuntu, I couldn't bear all the bulk. I want something done and I want it done fast. Even if my computer was made in 2000. ;)

---

### Post by urukrama on 2007-03-31
It's been quite fun customising OpenBox, actually. I just went through all the configuration files and played around a bit. You can really change a lot by just changing a few little things. There are, however, still a few things I haven't been able to do yet.

I still have to figure out what I'll use to draw my desktop. I use feh to provide the background image, but don't have anything for icons on the desktop. I haven't really looked around yet to see what programs I could use, though I did use PCMan FM's functionality to draw the desktop, but don't want to use that.

I don't use the desktop very often, but find it useful as a place to temporarily store files before I move them to a proper location. Any suggestions?

[I]K.Mandla, what is fbpanel like, actually? I'm using pypanel at the moment, but from your screenshots it seems that fbpanel has more options. Is it as easy to set up as pypanel (on Dapper) and does it use a lot of system resources? Would you recommend it?
[/I]

EDIT: I just noticed it is in the repos. I'll give it a try.

EDIT2: just tried fbpanel. Not bad, but I think I'll stick with pypanel. Its simplicity matches that of openbox better. I'll experiment a bit more, though, just for the fun of it.

---

### Post by bonzodog on 2007-03-31
> **urukrama said:**
> I still have to figure out what I'll use to draw my desktop. I use feh to provide the background image, but don't have anything for icons on the desktop. I haven't really looked around yet to see what programs I could use, though I did use PCMan FM's functionality to draw the desktop, but don't want to use that.

Try a little known program, quite new, that uses a GUI front end for wallpaper selection.
It's called Nitrogen. It can be found here:[http://minuslab.net/code/nitrogen/](http://minuslab.net/code/nitrogen/)

> 
*EDIT2: just tried fbpanel. Not bad, but I think I'll stick with pypanel. Its simplicity matches that of openbox better. I'll experiment a bit more, though, just for the fun of it.*

Do you really need a panel?

If you want a clock and system tray, have you thought about using openbox's dock that takes windowmaker dockapps?

I use a WM dockapp called wmtime (found at dockapps.org, or possibly in repos),
and a system tray called peksystray -found here-
[http://sourceforge.net/projects/peksystray](http://sourceforge.net/projects/peksystray)

A screenie of my desktop:
[[img]http://xs412.xs.to/xs412/07091/openzen5.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs412&d=07091&f=openzen5.png)

---

### Post by K.Mandla on 2007-03-31
> **urukrama said:**
> K.Mandla, what is fbpanel like, actually? I'm using pypanel at the moment, but from your screenshots it seems that fbpanel has more options. Is it as easy to set up as pypanel (on Dapper) and does it use a lot of system resources? Would you recommend it?
I liked fbpanel much more than PyPanel, although the latter has its following. I think a lot of people get started with PyPanel when they start with Openbox, and it just kind of sticks. I always found it a little fragile.

fbpanel is very nice, and [lxpanel]("http://sourceforge.net/projects/lxpanel/") is even better -- much easier to customize and set up. fbpanel has a bonus in that you can run two at once (like a top and bottom bar from a Gnome setup), whereas I couldn't ever find the two-panel option for lxpanel.

Usually I run lxpanel if I put together a straight Beryl box, so I have something to trigger menus and whatnot.

[CENTER][[img]http://xs412.xs.to/xs412/07084/screenshot.jpg.xs.jpg[/img]](http://xs.to/xs.php?h=xs412&d=07084&f=screenshot.jpg)[/CENTER]

---

### Post by urukrama on 2007-03-31
> **K.Mandla said:**
> fbpanel is very nice, and [lxpanel]("http://sourceforge.net/projects/lxpanel/") is even better -- much easier to customize and set up. fbpanel has a bonus in that you can run two at once (like a top and bottom bar from a Gnome setup), whereas I couldn't ever find the two-panel option for lxpanel.

I can't get lxpanel installed. If I try to compile from source, I seem to miss packages I can't find in the repos (and am a bit too lazy to look elsewhere). I found a .deb for ubuntu, but when I run that some dependencies clash. Is there a .deb package available for Dapper anywhere?

I also tried perlpanel but didn't like it. It used a lot of resources, and I couldn't really cusomise it the way I wanted it. So I'm back to pypanel for the moment.

Oh, and how do you configure idesk? I have it installed, and looked into the .ideskrc file, but have no clue what to do with it. If I run iDesk, nothing seems to happen...

---

### Post by Somenoob on 2007-03-31
Does anyone know of a more feature rich/elegant panel than pypanel?

---

### Post by K.Mandla on 2007-03-31
> **urukrama said:**
> I can't get lxpanel installed. If I try to compile from source, I seem to miss packages I can't find in the repos (and am a bit too lazy to look elsewhere). I found a .deb for ubuntu, but when I run that some dependencies clash. Is there a .deb package available for Dapper anywhere?
I'll look around. I'm very sure I installed it from a deb, and I think the same person who makes PCManFM makes lxpanel (or they're working together), and I know there are usually up-to-date debs somewhere. [Here we go.]("https://sourceforge.net/project/showfiles.php?group_id=180858&package_id=210079&release_id=467145") Or is that the one that doesn't work for you?
> **urukrama said:**
> I also tried perlpanel but didn't like it. It used a lot of resources, and I couldn't really cusomise it the way I wanted it.
I had the same experience with perlpanel. fbpanel was easier to work with, for me.
> **urukrama said:**
> Oh, and how do you configure idesk? I have it installed, and looked into the .ideskrc file, but have no clue what to do with it. If I run iDesk, nothing seems to happen...
There's an [iDesk wiki]("http://idesk.sourceforge.net/wiki/index.php/Main_Page"); I haven't used that in a very long time but I know it's almost completely text-file configured. Some charitable soul has created an [iDesktool]("http://www.jmurray.id.au/ideskconf.html") to help out, but I've never used it.
> **Somenoob said:**
> Does anyone know of a more feature rich/elegant panel than pypanel?
[fbpanel]("http://packages.ubuntu.com/feisty/x11/fbpanel") and [lxpanel]("https://sourceforge.net/project/showfiles.php?group_id=180858&package_id=210079&release_id=467145") are my favorites.

---

### Post by fuscia on 2007-03-31
i've used a bunch of different panels (mostly pypanel), even the xfce panel and kicker. this last time i reinstalled, i didn't feel like messing with pypanel, so for a clock i just use my personalized google page.

---

### Post by urukrama on 2007-04-01
> **K.Mandla said:**
> [Here we go.]("https://sourceforge.net/project/showfiles.php?group_id=180858&package_id=210079&release_id=467145") Or is that the one that doesn't work for you?

Yes, that doesn't work for me. I get "Error: Dependency is not satisfiable:libatk1.0-0"

---

### Post by urukrama on 2007-04-02
Is it actually possible to get rounded corners in Openbox? I've seen some themes for Fluxbox that have rounded corners, but nothing for blackbox. Just wondering...

---

### Post by fuscia on 2007-04-02
> **urukrama said:**
> Is it actually possible to get rounded corners in Openbox? I've seen some themes for Fluxbox that have rounded corners, but nothing for blackbox. Just wondering...

i think there might have been some discussion on the openbox mailing list about rounded corners a while back. i don't remember what was said, though (i'm a squared corner fascist). 

(it's fun to watch the young fawn stumble into the clearing of brazen anticipation.)

---

### Post by ynnhoj on 2007-04-02
> **fuscia said:**
> i've used a bunch of different panels (mostly pypanel), even the xfce panel and kicker. this last time i reinstalled, i didn't feel like messing with pypanel, so for a clock i just use my personalized google page.when using openbox i've always liked pypanel the best out of the panels i've tried, but lately i've just been using a combination of visibility ([http://projects.l3ib.org/visibility](http://projects.l3ib.org/visibility)) and conky to create a panel-like thing.

here's a screenie from a couple days ago that'll show you what i mean: [http://xs414.xs.to/xs414/07142/screen.png](http://xs414.xs.to/xs414/07142/screen.png).

---

### Post by urukrama on 2007-04-03
> **fuscia said:**
> (it's fun to watch the young fawn stumble into the clearing of brazen anticipation.)

It is quite fun! :) 

I think I'm almost there. Idesk is set up, but still neads some tweaking. I managed to integrate the orage calender into the pypanel clock (all by myself -- hurray! :p). I have a practical and good looking Openbox menu, and I feel at home in openbox.

Some things I haven't managed to do yet:

1. Docker. I have no idea how to configure that. I probably won't use it, but just wanted to see what it would look like, just in case... I couldn't find any documentation about it either.

2. I still have to play around a bit with pypanel. I like the basics I have now, but want to see what and how much I could integrate in the launcher part of it.

3. fuscia, I saw on one of your screenshots you have a menu for desktop backgrounds in your openbox menu. I really liked that, and integrated one into mine. Do you know if it would be possible to include something into that command to change the theme as well? If so, what would that be? I tried some things, but needless to say, it didn't work. 

4. Is it possible to use the "windows key" for keyboard shortcuts in openbox? If so, would it function like Ctrl and Alt (as a modifier) or as a simple key? And also, If it can be used, how is it called?

5. Anything else that is neat that I haven't come across yet. Any suggestions?

I've been playing a little with fluxbox also. It is pretty neat in some ways, but other aspects I don't quite get (the panel for example -- I never liked it). What I do like, however, is that each submenu has its own header. Is this possible in openbox?

---

### Post by ynnhoj on 2007-04-03
you ought to be able to switch your theme with the switch2 command; it's in this package: [http://packages.ubuntu.com/edgy/x11/gtk-theme-switch](http://packages.ubuntu.com/edgy/x11/gtk-theme-switch).  "switch2 --help" should tell you what you need to know..

i'm not sure about the windows key with the keybindings, as i've never tried.. but a quick look at [the openbox documentation](http://icculus.org/openbox/docs.php?page=details.html#keybindings) tells me that you can--use "W" in place of "A", "S", etc..

---

### Post by urukrama on 2007-04-03
Is it normal that Fluxbox (4-5 MB) runs lighter on my computer than Openbox (5-6 MB)? I expected the opposite, as fluxbox has more features.

If I then count pypanel as well (6-7 MB), my Openbox configuration runs much heavier than fluxbox!

---

### Post by raublekick on 2007-04-03
> **ynnhoj said:**
> when using openbox i've always liked pypanel the best out of the panels i've tried, but lately i've just been using a combination of visibility ([http://projects.l3ib.org/visibility](http://projects.l3ib.org/visibility)) and conky to create a panel-like thing.

here's a screenie from a couple days ago that'll show you what i mean: [http://xs414.xs.to/xs414/07142/screen.png](http://xs414.xs.to/xs414/07142/screen.png).

that's a pretty clever set up there, johnny! you guys are making me want to go back to openbox again...

i've fallen too much in love with some gnome stuff though. 

urukrama, glad my guide was a help :)

---

### Post by fuscia on 2007-04-03
> **ynnhoj said:**
> when using openbox i've always liked pypanel the best out of the panels i've tried, but lately i've just been using a combination of visibility ([http://projects.l3ib.org/visibility](http://projects.l3ib.org/visibility)) and conky to create a panel-like thing.

here's a screenie from a couple days ago that'll show you what i mean: [http://xs414.xs.to/xs414/07142/screen.png](http://xs414.xs.to/xs414/07142/screen.png).

that's some pretty crafty lookin' stuff, dude.

[quote=uru]
3. fuscia, I saw on one of your screenshots you have a menu for desktop backgrounds in your openbox menu. I really liked that, and integrated one into mine. Do you know if it would be possible to include something into that command to change the theme as well? If so, what would that be? I tried some things, but needless to say, it didn't work.[/quote]

if you mean for changing openbox themes, obconf is the way to go for that (even though it would be cool to do it in the menu. i suppose if you can figure out what commands obconf initiates when you switch themes, you could write that into the menu). for switching gtk themes, i was using gtk-chtheme, but it wipes out my icon themes, so now, i just edit the .gtkrc-2.0 file in nano.

funny you should say about feeling at home in openbox. at times, it feels so functional to me, i get bored with it and have to use something awkward just for a change of pace.

---

### Post by urukrama on 2007-04-04
It's me again :p

Yes, fuscia, I was trying to change the theme through the menu, so that when I change my wallpaper, my theme would change as well. It would be neat, but I guess I'll just let it go.

How do I get OpenOffice to follow the gtk apps in themes? Right now it is ugly bluish metalic. All is fine if I use the gnome-settings-daemon, but I don't want to do that as it messes up my gnome settings, so I'm using that gtkrc-2.0 file to change my settings. (I tried switch2 but that didn't work properly; I can't use about half of the themes I have.)

Thank you all for your help!


EDIT: Fuscia, have you seen these pipemenus at [http://david.chalkskeletons.com/scripts.html](http://david.chalkskeletons.com/scripts.html)? There are two there that might allow for changing the themes through the menu. I haven't tried them out yet, but will so shortly.

---

### Post by fuscia on 2007-04-04
uru, when i installed openbox, i just used the one in apt. when i want gradients in a menu, i just edit the .themerc for an individual theme. so, instead of... 

*menu.title/items.bg.color: #whatevercolor*

i'd do...

[i]menu.title/items.bg: flat solid/splitlevel gradient vertical/horizontal
menu.title/items.bg.color: #whatevercolor
menu.title/items.bg.colorTo: #whateverothercolor[/i]


i don't use openoffice, so i'm not sure what to tell you. changing the theme in .gtkrc-2.0 should have done it. of course, if you use an app as root, it will follow the root theme (i just did *sudo gtk-chtheme* to change the root theme).

i don't even know what pipe-menus are. i've pretty much just made up my own little fixes for the menu, like for turning conky on and off, for example: i made a submenu called 'conky' and put an item called 'on' (with the command being *conky -d*) and an item called 'off' (with the command being *killall conky*) in that submenu. it may be goofy, but it works.

---

### Post by urukrama on 2007-04-04
Are you using Edgy?

In dapper (what I run), the openbox version in the repos is 3.2. I don't think it supports gradients, as I have themes that have gradients as in your previous post, but they don't affect the way the theme is displayed.

At the moment, I'm trying to get Openbox 3.3.1 running. Quite an ordeal... If it works, I'll install in also on my laptop, and we're fully happy. Or so I hope...

*EDIT: It worked. I now have Openbox 3.3.1 running, and gradients are visible.*

---

### Post by fuscia on 2007-04-04
> **urukrama said:**
> *EDIT: It worked. I now have Openbox 3.3.1 running, and gradients are visible.*

rock&roll!!1

yes, edgy.

---

### Post by urukrama on 2007-04-04
> **fuscia said:**
> rock&roll!!1


Hmm. Not so rocky and rolly, on second thoughts. Openbox 3.3.1 froze twice in the thirty minutes I used it, freezing my entire system (first time in Ubuntu for me). It is still on that old pc, but I guess I won't be putting it on my laptop... It sure looked good, though.

---

### Post by urukrama on 2007-04-05
I finally got the OpenOffice problem solved. It now follows the gtk/gnome theme. I just had to add "OOO_FORCE_DESKTOP=gnome" to my openbox startup menu. 

Hurrary!

I'm happy now with how things look and work. I made it functional for my needs (I integrated gnome's volume control into it, etc.). Idesk still needs a little work, butis functional; better looks will come when I decide on the wallpaper. I've edited my menu a hundred times, but it does now exactly what I want it to do (obmenu is great!). 

It is wonderfully simple and elegant. Amazing the speed (and productivity) I get out of my 7 year old laptop! 

Thank you all for your help. It has been invaluable.

Oh, and I'll see if I can get a screenshot of my system up.

---

### Post by fuscia on 2007-04-05
i posted this a while ago, uru, but i think this is something that will dawn on you, more and more, the more you use openbox...

[i]"Openbox works with your applications, and makes your desktop easier to
manage. This is because the approach to its development was the opposite
of what seems to be the general case for window managers. Openbox was
written first to comply with standards and to work properly. Only when
that was in place did the team turn to the visual interface."[/i]


> **commodore said:**
> Why don't people use fbpanel? Is something wrong with that? I installed fbpanel and the only problem is that the "show desktop" button doesn't always work with the first try.

just tried it again. i've got a relatively new installation and i just hadn't felt like doing pypanel. my current wallpaper demands a panel (it just does), so i decided to give fbpanel another shot. well, it's perfect! LOL!!1

---

### Post by ynnhoj on 2007-04-05
fbpanel is alright.  i think version 2.4 of pypanel was the last, so i suspect it will become more and more problematic over time (as python and other dependencies are updated).. might as well find something new eventually, unless you want to spend time patching pypanel and fixing problems fairly frequently.

---

### Post by fuscia on 2007-04-06
i don't really need a panel, except for the clock, and now that i have a clock on my homepage, i don't even need that. some wallpapers need frames and that's what i use the panel for. pypanel was always great because one could use it as a frame and still have minimum interference as it was transparent. i've seen pics of a transparent fbpanel but haven't needed to find out how to do that yet. fbpanel strikes me as being very similar to icewm's panel, but a bit less oafish.

---

### Post by ynnhoj on 2007-04-06
i still haven't decided on what i like best yet.  all i know is that i want to be able to see the date and time.  i can display that with conky or gkrellm, but i'm not too crazy about either of those apps..  and most dock apps are kinda ugly :o  so i guess it's conky or a panel, until i think of something i like better.

[i'm fussy and lazy.  not exactly the best combination..]

---

### Post by fuscia on 2007-04-06
> **ynnhoj said:**
> i still haven't decided on what i like best yet.  all i know is that i want to be able to see the date and time.  i can display that with conky or gkrellm, but i'm not too crazy about either of those apps..  and most dock apps are kinda ugly :o  so i guess it's conky or a panel, until i think of something i like better.

i suppose you could just do *date* in a terminal and you wouldn't need any of that stuff. or xclock...

> [i'm fussy and lazy.  not exactly the best combination..]

try 'lazy' and 'impatient' sometime. you'll be amazed at how quickly you can get past the things you *should* have done.

---

### Post by graabein on 2007-04-06
I did Openbox on Ubuntu a while but now I've settled in on Xubuntu (Xfce). It works very nicely for my needs and hardware. Got it set up with a panel at the top just like in GNOME.

On topic: How does cairo-clock do on Openbox? Too dependant on new hardware and/or libs?

---

### Post by ynnhoj on 2007-04-07
> **fuscia said:**
> i suppose you could just do *date* in a terminal and you wouldn't need any of that stuff. or xclock...xclock is another idea i had.. and then forgot about--it's good that you mentioned it.  i think the reason i never tried was because i didn't feel like learning the command options to make it display the way i'd like it to :o

edit: as it turns out, xclock isn't such a bad option.. it looks okay with the window decorations turned off

---

### Post by urukrama on 2007-04-07
> **ynnhoj said:**
> edit: as it turns out, xclock isn't such a bad option.. it looks okay with the window decorations turned off

Is there actually a way you can disable the window decorations for a particular app by default? Or would you have to do that manually every time you start xclock?

---

### Post by ynnhoj on 2007-04-07
you can do it in the <applications> element of your rc.xml file.  i have:
```
<applications>
  <application name="xclock">
    <decor>no</decor>
    <shade>no</shade>
    <skip_pager>yes</skip_pager>
    <skip_taskbar>yes</skip_taskbar>
    <fullscreen>no</fullscreen>
    <maximized>no</maximized>
  </application>
<!--
other stuff...
-->
</applications>
```you can also set some other things (like position) which i've skipped over.  i probably don't need the shade, fullscreen, or maximized lines either.. but i typed them in anyways, i guess.

---

### Post by fuscia on 2007-04-07
hm! i didn't know xclock was so configurable. i've always just minimized it.

---

### Post by urukrama on 2007-04-08
> **ynnhoj said:**
> you can do it in the <applications> element of your rc.xml file.

Thanks. Very neat.

---

### Post by ynnhoj on 2007-04-08
[dali clock](http://www.jwz.org/xdaliclock/) is pretty nifty too, but i think xclock is easier to look at.

---

### Post by urukrama on 2007-04-08
Oh, one more thing: Is it possible to change the way the menu works? When I right click the desktop now close to the right side of the screen, the menu opens and then moves further left when I open a submenu, and even further left when I open another one, etc. Is it possible to configure it in such a way that when the menu opens in such an area, the submenu opens to the left of the main menu, not to the right (as Fluxbox does; I saw this also in a Blackbox screenshot)?

I looked in the rc.xml file, but didn't see anything straight away. I'll give it another look, but help is always appreciated.

---

### Post by ynnhoj on 2007-04-08
huh..  i've never noticed that before, but off-hand i can't think of a way to fix it in the config files.  my solution would be: to not open the menu too close to the right-hand edge of your screen :-P

---

### Post by urukrama on 2007-04-09
Well, when you open the menu at the bottom of the desktop, and enter a submenu, the menu moves up to allow the full display of the submenu. I guess this is related. Openbox could also just move the submenu up, and leave the root menu at whatever level it was when opened. Instead it prefers keep the top entry of the submenu always at the same height as the submenu entry. 

I assume this behaviour must be controlled somewhere, but I can't find anything. Blackbox and Fluxbox operate differently, which gives me some hope that this is actually changeable...

---

### Post by urukrama on 2007-04-11
> **fuscia said:**
> i posted this a while ago, uru, but i think this is something that will dawn on you, more and more, the more you use openbox...

[i]"Openbox works with your applications, and makes your desktop easier to
manage. This is because the approach to its development was the opposite
of what seems to be the general case for window managers. Openbox was
written first to comply with standards and to work properly. Only when
that was in place did the team turn to the visual interface."[/i]

I've surprised myself. Once I had openbox completely set up and the fun of configuring everything was over, I sort of expected I would go back to Xfce, which has been my default environment for a while now.

Not so. I think I'll stick to Openbox. You're right, fuscia. This is a great WM.

---

### Post by bonzodog on 2007-04-11
I have now slimmed my desktop even more. I now use conky to display the time and date:

[[img]http://xs514.xs.to/xs514/07140/openzen7.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs514&d=07140&f=openzen7.png)

---

### Post by PARO on 2007-04-14
I have a question for you guys, I've set up the xfce4-terminal to appear over the desktop on startup, but it's awfully large by default. I'd like it to open as ~300x350, but I can't find any info on how to specify default application dimentions in rc.xml.  I tried imitating the position lines in rc and adding "w" and "h" lines, but that didn't work.  Anyone know how it can be done? Btw, using Openbox v.3.3-2 from the repos.

---

### Post by fuscia on 2007-04-15
> **PARO said:**
> I have a question for you guys, I've set up the xfce4-terminal to appear over the desktop on startup, but it's awfully large by default. I'd like it to open as ~300x350, but I can't find any info on how to specify default application dimentions in rc.xml.  I tried imitating the position lines in rc and adding "w" and "h" lines, but that didn't work.  Anyone know how it can be done? Btw, using Openbox v.3.3-2 from the repos.

if i'm not mistaken, you would alter the properties of xfce4-terminal, not openbox, in that case. look at .config/Terminal/terminalrc and you'll see a line *MiscDefaultGeometry*. you can change that to get the dimensions you wish, but remember the size would change if you changed to a different size font, or to a font that is inherently larger at the same number size.

---

### Post by ynnhoj on 2007-04-15
have you checked to see if xfce4-terminal has a command-line option to set its size when you start it?  i don't have it installed so i can't look (and i can't seem to find a man page anywhere online..), but i assume that "xfce4-terminal --help" would give you some information.

---

### Post by bonzodog on 2007-04-15
I've found that the font size seems to affect the terminal default size as well. Try setting up a terminal font like smoothansi and getting the terminal to use that as default.

---

### Post by PARO on 2007-04-15
Ah, yes. It has an option called "geometry," that seemed to work fine. Thanks.  Now I'm content with my desktop :D

---

### Post by fuscia on 2007-04-21
looks like obmenu bit the muffin during the upgrade to feisty. i haven't even begun to look at why.

---

### Post by raublekick on 2007-04-21
> **fuscia said:**
> looks like obmenu bit the muffin during the upgrade to feisty. i haven't even begun to look at why.

i remember obmenu not working by default in edgy, or was that something else (besides pypanel...)?

---

### Post by fuscia on 2007-04-21
> **raublekick said:**
> i remember obmenu not working by default in edgy, or was that something else (besides pypanel...)?

both ob*conf* and pypanel were expecting puppies in edgy. some parsing thing in the former and just plain ole broke in the case of the latter.

---

### Post by raublekick on 2007-04-21
ok yeah, maybe it was obconf. in that case i remembe just having to rename, or link to, some files. 

sad to hear that openbox is getting more and more shafted as time goes on :-/

---

### Post by fuscia on 2007-04-21
> **raublekick said:**
> ok yeah, maybe it was obconf. in that case i remembe just having to rename, or link to, some files. 

sad to hear that openbox is getting more and more shafted as time goes on :-/

i don't know about that. obconf works in feisty and the upgrade to feisty updated to the latest version of ob. don't worry, little brother.

---

### Post by urukrama on 2007-04-22
I've been trying to use Openbox without a panel for a while now. I'm using docker for a systemtray/notification area, and use conky as clock (the only thing it displays). I'm liking it, but there is one thing I haven't been able to solve satisfactorily. 

One of the reasons I like panels is for the window list it can display. It allows me to easily see what (minimised) applications I have running. Now that I don't use a panel, I'm looking for an alternative. Alt-tab would be perfect, but Openbox's alt-tab is not quite there yet; pressing alt-tab only shows you the next application/window, and doesn't give you a quick overview. 

I've tried to look for an alt-tab replacement but haven't been succesful. [Superswitch]("http://www.gnomefiles.org/app.php?soft_id=1231") looks promising (and perhaps a bit overkill for my needs) but doesn't work on Dapper. Alternatively, I'd like some (small) dockapp (preferably not horribly ugly...heh); I've looked for some sort of iconbox/window list for the dock, but it seems there is no such thing.

I know I can use Openbox's Desktop menu, but that is a bit clumsy, as you don't have a quick overview of all applications on one or all desktops.

Any suggestions, anyone?

I hope the developers develop it's alt-tab feature a bit, perhaps integrating the desktop menu into it. Apart from that Openbox really rocks.

---

### Post by urukrama on 2007-04-22
[Visibility]("http://projects.l3ib.org/visibility") might work for me actually, if only I knew how to install it. I can't find the source package anywhere, and the project's website makes no sense to me. Ynnhoj, was it you that had it installed? I remember seeing it somewhere. If so, how did you do it?

In my search for a solution, I've come across some interesting projects that have mysteriously disappeared, like this enlightenment-like [iconbox]("http://66.102.9.104/linux?q=cache:GqYKVUz-ebYJ:freshmeat.net/projects/riconbox/+iconbox&hl=en&ct=clnk&cd=4").

---

### Post by fuscia on 2007-04-22
middle-clicking on the desktop would cut out a step, but i wish it were setup like xfce's middle click.

---

### Post by ynnhoj on 2007-04-22
> **urukrama said:**
> [Visibility]("http://projects.l3ib.org/visibility") might work for me actually, if only I knew how to install it. I can't find the source package anywhere, and the project's website makes no sense to me. Ynnhoj, was it you that had it installed? I remember seeing it somewhere. If so, how did you do it?i had installed visibility in arch, using a pkgbuild from the aur.  on the visibility project page, if you click "browse source" and go to the trunk directory it all seems to be there--but i can't seem to find a link to download it all in one tarball.  odd..

here's another option for you though: don't minimize things.  change the minimize button in yer title bar to shade/roll-up.  that way you can hide things but you can still see the titlebar there, so you know what's running.

---

### Post by urukrama on 2007-04-23
Yeah, it is strange the source is not downloadable. In general, though, are you happy with visibility? Is it stable and relatively or tolerably bug-free?

Your suggestion to shade instead of minimise would only partially work. What I want is something that allows me to easily see what applications I have running (like a normal alt-tab or a panel with a window list. Even if I shade the applications, I still have to go through all of them (or close/shade the top ones) to see what I am running.

fuscia, that is exactly what I am looking for. The window list/task switcher in xfce is great. I remember reading somewhere that Openbox's client list menu has changed to that format (showing all desktops in one window), but can't find it anywhere now (mailing list?).

Anyway, I'll keep looking, and keep trying to get visibility going.

---

### Post by fuscia on 2007-04-23
> **urukrama said:**
> fuscia, that is exactly what I am looking for. The window list/task switcher in xfce is great. I remember reading somewhere that Openbox's client list menu has changed to that format (showing all desktops in one window), but can't find it anywhere now (mailing list?).

here's the mailing list address - 
[email]openbox-subscribe@icculus.org[/email]

i don't think the menu format has changed. the version in feisty looks to be the latest version and the menu, i think, was the same (i don't have openbox installed now. i'm going through a kde phase).

---

### Post by bonzodog on 2007-04-23
Obconf is fine on Zenwalk, and on most other distro's - it just seems that Ubuntu's build is a little screwed up. It might be best for someone to build a third party package of it, or build it from source on Ubuntu.

---

### Post by urukrama on 2007-04-23
btw, does anyone know if you can change the colour of the slit/dock? It now follows the colour of the menu headers/window decorations, but I'd much rather have it follow the colour of the menu background. I know Fluxbox allows you to change that in the theme file you use. I tried copying and modifying the fluxbox syntax to match openbox's, but no luck so far...

---

### Post by dbbolton on 2007-04-28
> **fuscia said:**
> so as not to bog down the desktop pics thread, i've started this openbox thread. (watch no one show up now.) i'll be right back...
which file browser to you use with Openbox ? what about a panel ?

---

### Post by graabein on 2007-04-28
I tried [PCManFM]("http://pcmanfm.sourceforge.net/") on Xfce and was very pleased with it.

---

### Post by urukrama on 2007-04-28
> **dbbolton said:**
> which file browser to you use with Openbox ? what about a panel ?

I use Thunar with Openbox. Rox, Xfe, and PCMan File Manager seem popular as well.

If I use a panel, I use pypanel. Currently I'm not using any panel, and loving it. Other panels are fbpanel, perlpanel (which I find a bit too heavy and clunky), lxpanel. You can even use gnome-panel, xfce-panel, or kicker if you really want, though they will use more system resources.

If you just want a system tray/notification area and a clock, you can use some dockapps.

---

### Post by dbbolton on 2007-04-28
> **urukrama said:**
> I use Thunar with Openbox. Rox, Xfe, and PCMan File Manager seem popular as well.

If I use a panel, I use pypanel. Currently I'm not using any panel, and loving it. Other panels are fbpanel, perlpanel (which I find a bit too heavy and clunky), lxpanel. You can even use gnome-panel, xfce-panel, or kicker if you really want, though they will use more system resources.

If you just want a system tray/notification area and a clock, you can use some dockapps.
i've been using fspanel and thunar. i wanted to try pypanel but couldn't get it to work.

---

### Post by fuscia on 2007-04-28
> **dbbolton said:**
> which file browser to you use with Openbox ? what about a panel ?

i use thunar when i use openbox. i used to use pypanel, but i got sick of it, so i started using perlpanel which picks up the gtk theme.

---

### Post by dbbolton on 2007-04-28
> **fuscia said:**
> i use thunar when i use openbox. i used to use pypanel, but i got sick of it, so i started using perlpanel which picks up the gtk theme.
hmm, i'll give perlpnael a try. fspanel is very light/fast, but a bit of an eye sore.

---

### Post by dbbolton on 2007-04-28
i like perlpanel, but i get this error when i try to add a notification area to the tray:

```
Can't locate Gtk2/TrayManager.pm in @INC (@INC contains: /usr/share/perlpanel/ /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl . /home/daniel/.perlpanel/applets /usr/share/perlpanel//PerlPanel/Applet) at /usr/share/perlpanel//PerlPanel/Applet/NotificationArea.pm line 21.
BEGIN failed--compilation aborted at /usr/share/perlpanel//PerlPanel/Applet/NotificationArea.pm line 21.
Compilation failed in require at (eval 10) line 1.
```

anyone have this problem?

---

### Post by fuscia on 2007-04-29
> **dbbolton said:**
> i like perlpanel, but i get this error when i try to add a notification area to the tray:

```
Can't locate Gtk2/TrayManager.pm in @INC (@INC contains: /usr/share/perlpanel/ /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl . /home/daniel/.perlpanel/applets /usr/share/perlpanel//PerlPanel/Applet) at /usr/share/perlpanel//PerlPanel/Applet/NotificationArea.pm line 21.
BEGIN failed--compilation aborted at /usr/share/perlpanel//PerlPanel/Applet/NotificationArea.pm line 21.
Compilation failed in require at (eval 10) line 1.
```

anyone have this problem?

news to me. i had no trouble.

---

### Post by ynnhoj on 2007-04-29
**urukrama**: still interested in getting visibility set up?  it occurred to me that you can use subversion to get the source, which you could then compile.  this all worked for me (i'm using arch, not ubuntu.. but if you have all the dependencies installed then everything should be good)

first off: some packages you'll need that you might not have installed.. (i hope i get all the package names right -- i've looked some of them up on [http://packages.ubuntu.com](http://packages.ubuntu.com))
[LIST]
[*]subversion, so you can get the source.
[*]build-essential, so you have a compiler and make.
[*]autoconf, so you can use the autoreconf command
[*]and a few things visibility depends upon: libpng, libxft, and libsigc++2.0 (i think you'll have all three of these already)
[/LIST]
```
sudo aptitude install subversion build-essential autoconf libpng libxft libsigc++2.0
```
(i'm not 100% on the package name for "libsigc++2.0".  that's what it's called on arch, but it might just be "libsigc++".  i might be off on the package names for libpng and libxft too, but i'm sure you'll figure it out.)


okay, so get the source:
```
svn export -r 128 http://svn.l3ib.org/visibility/trunk/ visibility
```
128 seems to be the latest revision number (according to the trac source browser).  so now you ought to have a directory called visibility with all the source, readme, and other files.  "cd" into it.

generate a configure script from the configure.ac file
```
autoreconf
```
(note: this step might require "sudo" -- so "sudo autoreconf".  i was root when i installed it on my machine, so sudo wasn't necessary)

the next three steps to build and install are pretty typical
```
./configure
make
sudo make install
```

now you should have visibility installed.  if you do a "whereis visibility", you'll find the path to the executeable: /usr/local/bin/visibility.  /usr/local/bin isn't in my path, so i had to add it to my path so i could type "visibility" at the command-line instead of typing "/usr/local/bin/visibility" every time.

one last thing: when you downloaded the source with subversion, you also got a sample configuration file for visibility "config.sample".  copy to where it needs to be
```
cp config.sample ~/.config/visibility/config
```
and customize it to your liking.  of course, you'll have to create the directory ~/.config/visibility first :)


..wow, lots of typing.  hope it works for you.

---

### Post by MrGreen on 2007-04-29
Hi,

I am a new ubuntu user, used to using Openbox & Pypanel although they are loaded pypanel refuses to start 

mrgreen@ubuntu:~$ pypanel
Traceback (most recent call last):
  File "/usr/bin/pypanel", line 957, in <module>
    PyPanel(display.Display())
  File "/var/lib/python-support/python2.5/Xlib/display.py", line 80, in __init__
    self.display = _BaseDisplay(display)
  File "/var/lib/python-support/python2.5/Xlib/display.py", line 67, in __init__
    apply(protocol.display.Display.__init__, (self, ) + args, keys)
  File "/var/lib/python-support/python2.5/Xlib/protocol/display.py", line 124, in __init__
    self.default_screen = min(self.default_screen, len(self.info.roots) - 1)
  File "/var/lib/python-support/python2.5/Xlib/protocol/rq.py", line 1371, in __getattr__
    raise AttributeError(attr)
AttributeError: roots
mrgreen@ubuntu:~$ 

Read the perlpanel is a better option but I have never used it how simple is it to set up?

One other question I assume openbox starts from .xinitrc ? [using gdm!] 

TIA 

MrGreen

---

### Post by urukrama on 2007-04-30
> **ynnhoj said:**
> **urukrama**: still interested in getting visibility set up?

Yes I am still interested! I'm really used to not having a panel now, but the quick overview of running applications is still wanted. Thank you very much for all the effort! I'll try it out once I'm back home.

---

### Post by urukrama on 2007-04-30
> **MrGreen said:**
> Hi,

I am a new ubuntu user, used to using Openbox & Pypanel although they are loaded pypanel refuses to start 

Read the perlpanel is a better option but I have never used it how simple is it to set up?

One other question I assume openbox starts from .xinitrc ? [using gdm!] 


If you are using Ubuntu Edgy, have a look at [this]("http://ubuntuforums.org/showthread.php?t=327514&highlight=openbox+howto") thread to fix pypanel (if you are not using Edgy, perhaps you are encountering a similar issue?)

Perlpanel is easy to install. I forget it if it is in the repos, but if it isn't there should be a deb package available somewhere. I can look if you want me to. I've never really liked perlpanel, though. It uses a lot more resources than lbpanel or pypanel, and I couldn't really configure it the way I wanted (but then again, I didn't try very hard). I've used xfce4-panel in the past as well. A bit heavier, but you get more fun.

If you want to create an autostart for Openbox, have a look at raublekick's [howto]("http://ubuntuforums.org/showthread.php?t=192106&highlight=openbox+howto").

---

### Post by fuscia on 2007-04-30
perlpanel is in the repos and it's drunken child simple to use.

> **urukrama said:**
> If you are using Ubuntu Edgy, have a look at [this]("http://ubuntuforums.org/showthread.php?t=327514&highlight=openbox+howto") thread to fix pypanel 

i'm an idiot! in my mind, i read 'feisty' instead of 'edgy' and clicked on that link, thinking "ooh, i should check that out." imagine my surprise (stupid, stupid, stupid...)

---

### Post by MrGreen on 2007-04-30
Thanks guys ... for the heads up ... got to stop using gnome hehe

---

### Post by MrGreen on 2007-04-30
I got pypanel running its the display.py changed 2048 to 4096 I'm surprised this is not fixed ??

Anyway I will keep on getting it set up ....

---

### Post by ynnhoj on 2007-04-30
i remember having read about that fix before.. something about a buffer size not being large enough in some cases, thus the change in size.  but that's in xlib not the pypanel source.

in either case afaik pypanel is no longer being developed, so you might find more problems as other updates come and go and pypanel stays the same.  i assume updates to python and/or python-xlib would be the main culprits.

---

### Post by MrGreen on 2007-05-01
Maybe will have to use a different panel in the future ;-(

visibility looks good

---

### Post by skwid on 2007-05-01
I am trying to get visibility up and running but when I do a ./configure I get an error saying No Packag 'xft' found?

Any Ideas?

---

### Post by MrGreen on 2007-05-01
you may have a dep missing .... check deps for package [look in install notes!] 

should be good to go

---

### Post by ynnhoj on 2007-05-01
> **skwid said:**
> I am trying to get visibility up and running but when I do a ./configure I get an error saying No Packag 'xft' found?

Any Ideas?try "sudo aptitude install libxft2" -- is that already installed?  and if it is installed but still doesn't work, maybe try "sudo aptitude install libxft-dev".

---

### Post by skwid on 2007-05-01
> **ynnhoj said:**
> try "sudo aptitude install libxft2" -- is that already installed?  and if it is installed but still doesn't work, maybe try "sudo aptitude install libxft-dev".

Worked like a charm.  Thanks bro.

Now is there any documentation on configuring this damn thing  :) !

---

### Post by ynnhoj on 2007-05-01
documentation -- nope, not so much :/ (none that i'm aware, at least).  but you do have a sample config file to edit (config.sample in the source you downloaded with svn).  it's fairly simple and has useful comments beside each line, so you'll probably figure it all out on your own.

---

### Post by urukrama on 2007-05-02
> okay, so get the source:
```
svn export -r 128 http://svn.l3ib.org/visibility/trunk/ visibility
```


I get the following error when I try to get the code:

```
urukrama@svar:~$ svn export -r 128 [http://svn.l3ib.org/visibility/trunk/](http://svn.l3ib.org/visibility/trunk/) visibility
svn: REPORT request failed on '/visibility/!svn/vcc/default'
svn: REPORT of '/visibility/!svn/vcc/default': 200 OK ([http://svn.l3ib.org](http://svn.l3ib.org))

```

I have everything installed you mentioned earlier, and have no experience with svn so I don't know how to interpret this. What now?

---

### Post by skwid on 2007-05-02
Is there any way to get drop shadows etc... maybe beryl with openbox?

Thanks!

---

### Post by MrGreen on 2007-05-02
errr xcompmgr ? compiz I forget .... lol

---

### Post by K.Mandla on 2007-05-02
Yup. If you install [xcompmgr]("http://packages.ubuntu.com/feisty/x11/xcompmgr") and [transset]("http://packages.ubuntu.com/feisty/x11/transset") (and maybe compile [transset-df]("http://forchheimer.se/transset-df/") because it's fun), you can get transparencies and drop shadows with Openbox. 

[[img]http://xs412.xs.to/xs412/07073/xcompmgr-1.jpg.xs.jpg[/img]](http://xs.to/xs.php?h=xs412&d=07073&f=xcompmgr-1.jpg) [[img]http://xs412.xs.to/xs412/07073/xcompmgr-2.jpg.xs.jpg[/img]](http://xs.to/xs.php?h=xs412&d=07073&f=xcompmgr-2.jpg)

You can't really run Beryl and Openbox together, since they're both window managers. You can run Beryl without anything else though, and get the effects without the entire DE.

More ideas, if you want 'em. ...

[http://kmandla.wordpress.com/2007/02/14/binding-transparency-to-the-mouse-wheel-in-openbox/](http://kmandla.wordpress.com/2007/02/14/binding-transparency-to-the-mouse-wheel-in-openbox/)
[http://kmandla.wordpress.com/2007/02/14/transparencies-in-openbox-with-xcompmgr/](http://kmandla.wordpress.com/2007/02/14/transparencies-in-openbox-with-xcompmgr/)
[http://kmandla.wordpress.com/2007/02/20/yes-virginia-you-can-run-beryl-alone/](http://kmandla.wordpress.com/2007/02/20/yes-virginia-you-can-run-beryl-alone/)

---

### Post by MrGreen on 2007-05-02
Would be nice to able to run Openbox from gdm :( 

no idea why it does not work...:confused:

---

### Post by fuscia on 2007-05-02
> **MrGreen said:**
> Would be nice to able to run Openbox from gdm :( 

no idea why it does not work...:confused:

it should, unless you installed it from source. then, you have to add it yourself.

---

### Post by MrGreen on 2007-05-02
no its the autostart thing.... thats not working but I guess I could just add a script that I could run after openbox starts not an ideal way of doing it

wondering if I should try a bash script instead ?

doh!!!!!!!!! I got it 

in openbox-autostart there was an extra ' ' after autostart.sh 

works a treat now .... where has pypanel gone hehe

thanks guys for all your help

MrG

---

### Post by ynnhoj on 2007-05-02
> **urukrama said:**
> I get the following error when I try to get the code:
```
urukrama@svar:~$ svn export -r 128 [http://svn.l3ib.org/visibility/trunk/](http://svn.l3ib.org/visibility/trunk/) visibility
svn: REPORT request failed on '/visibility/!svn/vcc/default'
svn: REPORT of '/visibility/!svn/vcc/default': 200 OK ([http://svn.l3ib.org](http://svn.l3ib.org))

```
I have everything installed you mentioned earlier, and have no experience with svn so I don't know how to interpret this. What now?y'know, i haven't encountered that before.  seems odd, because if "200 OK" was returned then.. shouldn't everything be just fine?  are you behind any sort of firewall or something else?

i guess for now i can get the source with svn, make a tarball, and attach it.  "tar -xzvf visibility.tar.gz" will extract it into ./visibility/

---

### Post by ynnhoj on 2007-05-02
hmm, another interesting thing i've stumbled upon: [tint task manager](http://code.google.com/p/ttm/).  it's a panel-ish thing.  well, i guess not a full-blown panel -- just a task list.  a simple install; use the svn command on the source page, make, and make install..

the author posted about it in the screenshots thread at the arch forums so i thought i'd shared.

---

### Post by urukrama on 2007-05-04
Yes, I do have a firewall. Thanks for the source.

It still doesn't work, though. When I have to do this:

> **ynnhoj said:**
> generate a configure script from the configure.ac file
```
autoreconf
```
(note: this step might require "sudo" -- so "sudo autoreconf".  i was root when i installed it on my machine, so sudo wasn't necessary)

I get this error:

```
configure.ac: 35: `automake requires `AM_CONFIG_HEADER', not `AC_CONFIG_HEADER'
automake: configure.ac: required file `./mkinstalldirs' not found
automake: configure.ac: required file `./config.guess' not found
automake: configure.ac: required file `./config.sub' not found
autoreconf: automake failed with exit status: 1

```

Is there a way to get around this autoreconf business?

I have automake1.4 and automake 1.9 installed (I also tried with 1.7 and 1.8, both in the repos). Autoconf is 2.59. 

**EDIT: I uninstalled automake1.4 and all worked fine! Many many thanks ynnhoj. This looks really neat. Now starts editing the configuration file.**

EDIT2: A pity you can't autohide this, or have it display only on the desktop, like conky. Otherwise this is nice. Don't know if I'll stick to it, though.

---

### Post by skwid on 2007-05-04
Glad you got it to work.   Visibility is a sweet program.  I may try out the Tint thing ynnhoj posted about.   It looks fairly neat.  

[HERE]("http://www.skwiz0d.com/screenshots/2007-05-03.png") is a SS of my currenty Openbox Setup.

---

### Post by MrGreen on 2007-05-04
emmm your ss is very rezza like ;-) ... man we could do with openbox-svn headless menus

---

### Post by skwid on 2007-05-04
Thanks.  I have to thank russellc for alot of the help converting to openbox.  It wasn't easy by far but It's growing on me very fast.  I love the minimal look and I need to do some MAJOR menu customization but I'll post up some new shots when I get some more work done to it this weekend.


J

---

### Post by dbbolton on 2007-05-05
fuscia, could you upload the TrayManager.pm file from perlpanel? it seems that this file is necessary to run the systray applet, but for whatever reason, i don't have it. i just downloaded the latest version from [http://perlpanel.org/files/dist/0.9.1/PerlPanel-0.9.1.tar.gz](http://perlpanel.org/files/dist/0.9.1/PerlPanel-0.9.1.tar.gz) and that file wasn't there either.

there was a folder called ~/PerlPanel-0.9.1/lib/PerlPanel/Applet/ that had a bunch of .pm files, but no traymanager.

---

### Post by fuscia on 2007-05-06
> **dbbolton said:**
> fuscia, could you upload the TrayManager.pm file from perlpanel? it seems that this file is necessary to run the systray applet, but for whatever reason, i don't have it. i just downloaded the latest version from [http://perlpanel.org/files/dist/0.9.1/PerlPanel-0.9.1.tar.gz](http://perlpanel.org/files/dist/0.9.1/PerlPanel-0.9.1.tar.gz) and that file wasn't there either.

there was a folder called ~/PerlPanel-0.9.1/lib/PerlPanel/Applet/ that had a bunch of .pm files, but no traymanager.

all i have is a .perlpanelrc file. there is no perlpanel directory.

---

### Post by urukrama on 2007-05-06
Ok, Superswitcher was updated (to 0.5) and I was able to install it. It uses Super(windows key)-tab to switch between tasks. Looks impressive, but a bit difficult or clumsy if used alongside alt-tab. Uses about 8 MB RAM on my laptop.

I also discovered that Openbox will change its default client list menu! :hurray: I've attached a picture. More info at [http://d.minuslab.net/?p=32](http://d.minuslab.net/?p=32) and [planet openbox]("http://planetob.openmonkey.com/"). I believe this should already be available through svn.

---

### Post by dbbolton on 2007-05-06
> **fuscia said:**
> all i have is a .perlpanelrc file. there is no perlpanel directory.
there's one called "NotificationArea.pm", but for some reason, when i try to add a notification area applet to the panel says that it can't find "TrayManager.pm"

i think i might have a talk with the devs about this one.

---

### Post by urukrama on 2007-05-06
Have you tried lxpanel, dbbolton? I don't remember what plugins perlpanel had, but I find lxpanel has all I would want from a panel, and is much lighter on system resources.

---

### Post by dbbolton on 2007-05-06
i *tried* to install it.

```
checking for PACKAGE... configure: error: Package requirements (gtk+-2.0 >= 2.6.0              gthread-2.0              libstartup-notification-1.0) were not met:

No package 'gtk+-2.0' found
No package 'gthread-2.0' found
No package 'libstartup-notification-1.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

---

### Post by urukrama on 2007-05-06
> **dbbolton said:**
> 
No package 'gtk+-2.0' found
No package 'gthread-2.0' found
No package 'libstartup-notification-1.0' found


You'll have to install the packages it says it can't find (look for them in Synaptic). If you do have those installed, make sure you have the -dev (eg, gthread-dev, etc) version also installed, as they are needed for the compiling.

It also took me a while before I got this. Once you know this, all those packages that simple wouldn't install suddenly work like a charm :-)

---

### Post by urukrama on 2007-05-07
Just found out skippy, a full-screen task-switcher (and copy of Mac's Expose). I'd seen it earlier, but always thought it was a KDE app, which it isn't.

It is pretty nifty, and allows me to see immediately what applications I have open. Runs at about 13-15 MB RAM, though. It is in the repos.

---

### Post by dbbolton on 2007-05-07
> **urukrama said:**
> Just found out skippy, a full-screen task-switcher (and copy of Mac's Expose). I'd seen it earlier, but always thought it was a KDE app, which it isn't.

It is pretty nifty, and allows me to see immediately what applications I have open. Runs at about 13-15 MB RAM, though. It is in the repos.
it's pretty cool. i wish it had a mouse hotspot though.

---

### Post by urukrama on 2007-05-11
I'm trying bbtime out, to get a small clock in the dock. I have it installed, and manage to configure it, but for some reason I can never change the font. The font format on the default config file looks like this 

```
! font which determines the height (compatible with blackbox)
bbtime.heightBy.font: -*-helvetica-medium-r-*-*-*-120-*-*-*-*-*-*
!** label font **
bbtime.labelFont:     -*-helvetica-medium-r-*-*-*-120-*-*-*-*-*-*

```

I've tried to edit this, but don't get anywhere. No matter how much I change this, the font doesn't change in the clock. I don't have helvetica installed, so I tried to substitute other fonts, but it always complains it can't find the fonts. Even if I just change the size in the above, nothing happens (but no complaints in the terminal).

How would I have to edit this, if I want to use "URW Gothic L" as a font, size 10? I've come across this font config format before, and never managed to work with it. Help appreciated :-)

---

### Post by juxtaposed on 2007-05-15
Cool - I just got the GTK programs to look decent in openbox.

It seemed to not work for awhile in ubuntu, then it started to work (I didn't do anything to get it to work that I remember either).

Now, in debian, I installed that and everything looks great :)

---

### Post by dbbolton on 2007-05-20
know any good sites for OB themes ?

---

### Post by bonzodog on 2007-05-20
There is a few sites linked off OB's home site for themes, not least of which is [http://www.minuslab.net/themes/](http://www.minuslab.net/themes/)

Check out:[http://david.chalkskeletons.com/..files/openbox-themes.tar.gz](http://david.chalkskeletons.com/..files/openbox-themes.tar.gz)
Thats a tarball of about 30 OB themes.

[http://themes.freshmeat.net/browse/1087/](http://themes.freshmeat.net/browse/1087/) - the openbox freshmeat themes.

Unfortunately, we have just lost boxwhore, which had 58 themes on it.

---

### Post by dbbolton on 2007-05-20
> **ynnhoj said:**
> hmm, another interesting thing i've stumbled upon: [tint task manager]("http://code.google.com/p/ttm/").  it's a panel-ish thing.  well, i guess not a full-blown panel -- just a task list.  a simple install; use the svn command on the source page, make, and make install..

the author posted about it in the screenshots thread at the arch forums so i thought i'd shared.
i decided to try out TTM. here's what happened when it did make:

```
daniel@lennox:~$ cd ttm/src
daniel@lennox:~/ttm/src$ make
cc -Wall -g -lX11 `pkg-config --cflags cairo pangocairo x11` -Wall -g `pkg-config --libs cairo pangocairo x11` -o tint tint.c server.c window.c task.c visual.c event.c config.c
Package cairo was not found in the pkg-config search path.
Perhaps you should add the directory containing `cairo.pc'
to the PKG_CONFIG_PATH environment variable
No package 'cairo' found
Package pangocairo was not found in the pkg-config search path.
Perhaps you should add the directory containing `pangocairo.pc'
to the PKG_CONFIG_PATH environment variable
No package 'pangocairo' found
Package cairo was not found in the pkg-config search path.
Perhaps you should add the directory containing `cairo.pc'
to the PKG_CONFIG_PATH environment variable
No package 'cairo' found
Package pangocairo was not found in the pkg-config search path.
Perhaps you should add the directory containing `pangocairo.pc'
to the PKG_CONFIG_PATH environment variable

```edit: you have to install the -dev packages for cairo and pango

[[IMG]http://i103.photobucket.com/albums/m128/envyouraudience/th_oblack.png[/IMG]](http://i103.photobucket.com/albums/m128/envyouraudience/oblack.png)

---

### Post by urukrama on 2007-05-21
Looks very nice, dbbolton. Whenever I see a nice dark theme, I'm tempted to try one out myself, but I can never get used to it.

How do you get the Desktop menu in your root menu? I can't remember whether this is standard in Openbox, and I deleted it. What does that section of your menu.xml look like?

---

### Post by urukrama on 2007-05-21
> **bonzodog said:**
> Check out:[http://david.chalkskeletons.com/..files/openbox-themes.tar.gz](http://david.chalkskeletons.com/..files/openbox-themes.tar.gz)
Thats a tarball of about 30 OB themes.

That should be [http://david.chalkskeletons.com/files/openbox-themes.tar.gz](http://david.chalkskeletons.com/files/openbox-themes.tar.gz)
The link on the original website is wrong.

---

### Post by dbbolton on 2007-05-21
> **urukrama said:**
> Looks very nice, dbbolton. Whenever I see a nice dark theme, I'm tempted to try one out myself, but I can never get used to it.

How do you get the Desktop menu in your root menu? I can't remember whether this is standard in Openbox, and I deleted it. What does that section of your menu.xml look like?
```
        <menu id="client-list-menu"/>
```

---

### Post by dbbolton on 2007-05-21
ok, so i installed the artwiz fonts. but how do i use them ?


edit: you have to enable bitmap fonts ;)

these fonts go really well with ob

---

### Post by urukrama on 2007-05-21
> **dbbolton said:**
> ```
        <menu id="client-list-menu"/>
```

Oh. I should have known...:rolleyes: Thanks.

---

### Post by dbbolton on 2007-05-21
does anyone know of a standalone clock app for openbox ? (kind of like a widget)

---

### Post by urukrama on 2007-05-21
There are several things you could use;

* dockapps: plenty of clocks: wmtime, wmcalclock, pywmtime, etc.
* bbtime: a blackbox application that works fine with openbox (its in the repos). There is also a bbdate. You can load it in the dock, but need not do so. 
* xclock: light analog clock.
* gdesklets/adesklets: both have clocks. They work fine with openbox
* conky: conky can show the time.

I suppose you could also use a KDE clock, though I don't know what is available there.

---

### Post by dbbolton on 2007-05-22
> **urukrama said:**
> There are several things you could use;

* dockapps: plenty of clocks: wmtime, wmcalclock, pywmtime, etc.
* bbtime: a blackbox application that works fine with openbox (its in the repos). There is also a bbdate. You can load it in the dock, but need not do so. 
* xclock: light analog clock.
* gdesklets/adesklets: both have clocks. They work fine with openbox
* conky: conky can show the time.

I suppose you could also use a KDE clock, though I don't know what is available there.
cool stuff. i'm digging xclock right now.


does anyone know how to make gnome-terminal transparent in openbox ?

---

### Post by urukrama on 2007-05-22
> **dbbolton said:**
> cool stuff. i'm digging xclock right now.

I like bbtime at the moment. You can change the colours to match your theme, though I'm still having a hard time to change the font (or at least the size -- having it just a tad smaller would look much nicer). 

But I had a second look at xclock. I didn't know you could do so much with it (check man xclock). I might give it another try.

> **dbbolton said:**
> does anyone know how to make gnome-terminal transparent in openbox ?

Just like you would in Gnome. Open the terminal, go to Edit > Current Profile [or Profiles & edit the profile you want, if you want to have more than one profile] > Effects and then select 'Transparent Background' and set the slider to the amount of transparency you want. You can set a background picture in the same location. Changing fonts, font colours, etc. can also be done through these profiles.

If you want a lighter terminal, try xfce4-terminal. You can make it transparent too (Edit > Preferences > Appearance).

---

### Post by dbbolton on 2007-05-22
i know how to do it. but the transparency isn't working with my wallpaper.

---

### Post by urukrama on 2007-05-22
Strange. All works fine here.

---

### Post by urukrama on 2007-05-23
Openbox 3.4 is on its way! Lots of nice additions (apart from plenty of bug fixes). See the revamped [Openbox site]("http://icculus.org/openbox/index.php/Help:Upgrading_to_3.4") for details.

---

### Post by graabein on 2007-05-23
I used to have Openbox but found the machines was responsive enough with Xfce. 

One thing I wonder though is if Openbox can run XGL and Compiz and that stuff? Are [screenlets]("http://hendrik.kaju.pri.ee/screenlets/?q=node/14") an alternative to desktop clock?

---

### Post by bonzodog on 2007-05-23
Announcement!

After talking to the *-look themes site hoster, there is now a box-look.org site, he is currently in the process of setting it up. It will host Blackbox, Fluxbox, Openbox, IceWM, and WindowMaker themes.

[http://www.box-look.org](http://www.box-look.org)

**Give it a few days.** The site is clearly under construction.

I have suggested that he cross over icons, fonts, gtk themes, and Cliparts, and possibly GDM themes from the sister sites, then add Openbox, Blackbox, and Fluxbox, Screenshots, and Wallpapers as additional categories.

---

### Post by fuscia on 2007-05-23
that's great news, bonzo.

---

### Post by DanaJansens on 2007-05-23
> **benplaut said:**
> ok, here's the easy way to get autostart that won't mess with your xinitrc, and can be used form gdm.


People are obviously being confused about autostart.

[http://icculus.org/openbox/index.php/Help:Autostart#Making_your_own_autostart](http://icculus.org/openbox/index.php/Help:Autostart#Making_your_own_autostart)

If you choose the Openbox option in GDM, it will already automatically run your autostart script.  This script is run just before the Openbox WM is launched.  You don't have to edit any GDM stuff, and you don't have to run Openbox in the autostart. It is already being run.

If you need something to start after Openbox has launched, use "sleep" to slow it down, like this:

(sleep 2 && pypanel) &

You're making autostart a lot more complicated then it needs to be. :p

---

### Post by urukrama on 2007-05-24
> **DanaJansens said:**
> People are obviously being confused about autostart.

[http://icculus.org/openbox/index.php/Help:Autostart#Making_your_own_autostart](http://icculus.org/openbox/index.php/Help:Autostart#Making_your_own_autostart)

Isn't this only true for Openbox 3.4, which is still to appear in a final version?

---

### Post by urukrama on 2007-05-24
> **dbbolton said:**
> it's pretty cool. i wish it [=skippy] had a mouse hotspot though.

Have you tried using it with [brighside]("http://wiki.catmur.co.uk/Brightside/")? It probably uses quite some system resources, and it may or may not work with Openbox, but if you're really keen on having something like this, you could give it a try.

---

### Post by dbbolton on 2007-05-24
> **urukrama said:**
> Have you tried using it with [brighside]("http://wiki.catmur.co.uk/Brightside/")? It probably uses quite some system resources, and it may or may not work with Openbox, but if you're really keen on having something like this, you could give it a try.
thanks, but i don't really need an expose now that i'm using tint.


quick question, after you install pypanel, how do you launch it? 'pypanel' prints command not found.

---

### Post by ynnhoj on 2007-05-24
are you sure pypanel installed correctly?  i guess it could have installed to a directory that's not in your path.. what's the output of the command:
```
whereis pypanel
```
?

---

### Post by dbbolton on 2007-05-24
> **ynnhoj said:**
> are you sure pypanel installed correctly?  i guess it could have installed to a directory that's not in your path.. what's the output of the command:
```
whereis pypanel
```
?
i think my whole computer had been messed up. i just did a clean install of feisty, and everything is working smoothly, including pypanel :)

---

### Post by dbbolton on 2007-05-25
here's a screenie

[[IMG]http://i103.photobucket.com/albums/m128/envyouraudience/th_ob_brown.jpg[/IMG]](http://i103.photobucket.com/albums/m128/envyouraudience/ob_brown.jpg)

---

### Post by fuscia on 2007-05-26
openbox has freed us from the nazi-like oppression of desktop environments.

sorry, i just read about godwin's law (you can thank matthew for that) and i felt compelled to post such a remark.
[http://socialdiscussion.com/general-discussion/539-what-godwins-law-why-cant-i-mention-nazis-get-away.html](http://socialdiscussion.com/general-discussion/539-what-godwins-law-why-cant-i-mention-nazis-get-away.html)

---

### Post by dbbolton on 2007-05-26
> **fuscia said:**
> openbox has freed us from the nazi-like oppression of desktop environments.

sorry, i just read about godwin's law (you can thank matthew for that) and i felt compelled to post such a remark.
[http://socialdiscussion.com/general-discussion/539-what-godwins-law-why-cant-i-mention-nazis-get-away.html](http://socialdiscussion.com/general-discussion/539-what-godwins-law-why-cant-i-mention-nazis-get-away.html)
[IMG]http://imgs.xkcd.com/comics/regarding_mussolini.png[/IMG]

[http://xkcd.com/c261.html](http://xkcd.com/c261.html)

---

### Post by ynnhoj on 2007-05-26
> **dbbolton said:**
> here's a screenie

[[IMG]http://i103.photobucket.com/albums/m128/envyouraudience/th_ob_brown.jpg[/IMG]](http://i103.photobucket.com/albums/m128/envyouraudience/ob_brown.jpg)
lookin' good.  but why not take the window decoration off the xclock?

---

### Post by dbbolton on 2007-05-26
> **ynnhoj said:**
> lookin' good.  but why not take the window decoration off the xclock?
how ?

---

### Post by urukrama on 2007-05-26
> **dbbolton said:**
> how ?

At the end of your rc.xml file (in ~/.config/openbox/), under the applications section add:

```
<application name="xclock">
    <decor>no</decor>
    <shade>no</shade>
    <skip_pager>yes</skip_pager>
    <skip_taskbar>no</skip_taskbar>
    <fullscreen>no</fullscreen>
    <maximized>no</maximized>
  </application>
```

Change the other settings as you wish (skip pager/taskbar, etc). Whenever you load xclock you'll have it without the window decoration.

---

### Post by fuscia on 2007-05-27
back from the luftwaf...uh, i mean kde...

---

### Post by dbbolton on 2007-05-27
> **fuscia said:**
> back from the luftwaf...uh, i mean kde...
what is das Font in your title bar ?

---

### Post by fuscia on 2007-05-27
> **dbbolton said:**
> what is das Font in your title bar ?

Das ist der HeldustryFTBlack Font, Herr Bolton!

---

### Post by dbbolton on 2007-05-27
> **fuscia said:**
> Das ist der HeldustryFTBlack Font, Herr Bolton!
Jawohl!

---

### Post by urukrama on 2007-05-27
I'm more interested in the wallpaper. Can you reveal the source, herr fuscia?

---

### Post by dbbolton on 2007-05-27
it is pretty sweet.

---

### Post by fuscia on 2007-05-27
> **urukrama said:**
> I'm more interested in the wallpaper. Can you reveal the source, herr fuscia?

es kommt aus der Siten Interfaceliftung!  [das wunderbar vallpapiersiten](http://interfacelift.com/)

---

### Post by urukrama on 2007-05-27
danke!

---

### Post by fuscia on 2007-05-27
ach! es ist genug mit dieses zillypoopenspiel!!1

---

### Post by urukrama on 2007-05-28
I'm currently playing around with [apwal]("http://apwal.free.fr/"), a simple icon-box application launcher. It is quite neat and fast and gives you quick (graphical) access to whatever commands you configure. It seems to be fairly unknown, but is in the repos.

---

### Post by yabbadabbadont on 2007-05-28
> **urukrama said:**
> I'm currently playing around with [apwal]("http://apwal.free.fr/"), a simple icon-box application launcher. It is quite neat and fast and gives you quick (graphical) access to whatever commands you configure. It seems to be fairly unknown, but is in the repos.

That looks interesting.  I've used (and liked) wmDrawer with Fluxbox in the past.

[http://people.easter-eggs.org/~valos/wmdrawer/](http://people.easter-eggs.org/~valos/wmdrawer/)

---

### Post by urukrama on 2007-05-28
I never liked the looks of wmdrawer (and of most dockapps, actually). Apwal is nice in that if you run the program, icons just appear around your cursor (wherever it happens to be, and in whatever pattern/shape/order you want). I like it that you don't have to keep it running constantly. I've assigned a keyboard shortcut to it, so it doesn't take up any space on my desktop and remains easily accessible.

The fun thing, moreover, with apwal is that you don't necessarily need to have a straight line of icons. I have them in a star at the moment, which looks a bit cooler. :-)

---

### Post by fuscia on 2007-05-28
> **yabbadabbadont said:**
> That looks interesting.  I've used (and liked) wmDrawer with Fluxbox in the past.

[http://people.easter-eggs.org/~valos/wmdrawer/](http://people.easter-eggs.org/~valos/wmdrawer/)

i just thought "gosh, that looks a lot like window maker." DOH!1

---

### Post by yabbadabbadont on 2007-05-28
> **urukrama said:**
> I never liked the looks of wmdrawer (and of most dockapps, actually).

I agree that the default look of the app isn't very pretty.  If you assign custom icons, including to the drawer, and then enable transparency, it can look nice.  Now days I just use keyboard shortcuts instead.

Although partially obscured, these may not be safe for work.  (for you.  they would be fine everywhere that I have worked.)

Edit: I removed the direct image links and have instead provided an indirect link.  (My post on the Gentoo forums where I originally posted the screenshots)

[http://forums.gentoo.org/viewtopic-p-3135575.html#3135575](http://forums.gentoo.org/viewtopic-p-3135575.html#3135575)

---

### Post by urukrama on 2007-05-28
Hmm. Wmdrawer seems to be one of the better dockapps. I prefer apwal though, as I'm trying to have a desktop that is as free as possible (no docks, no panels, no icons, etc.) -- it helps me to focus more on my work.

---

### Post by dbbolton on 2007-06-01
has anyone tried the openbox theme called "ubuntu-e17"? i've taken a liking to it.

---

### Post by urukrama on 2007-06-01
Where can I find it?

---

### Post by dbbolton on 2007-06-01
i'm pretty sure it came from [http://david.chalkskeletons.com/files/openbox-themes.tar.gz](http://david.chalkskeletons.com/files/openbox-themes.tar.gz)

here's a screenshot of it:

[[IMG]http://i103.photobucket.com/albums/m128/envyouraudience/th_ue17thm.jpg[/IMG]](http://i103.photobucket.com/albums/m128/envyouraudience/ue17thm.jpg)

---

### Post by ynnhoj on 2007-06-02
openbox v3.3.995 has made it's way into the arch linux repository, so i upgraded and played around with it earlier.  i like the clearlooks theme a bit better as a default compared to what it was before ("thebear" i think?).  and that new desktop/window list (middle-click) menu is very nice.

---

### Post by Techn101 on 2007-06-03
openbox-3.3.995-1 certainly has some improvements. The ALT-Tab is much better than before. But it has caused me also al lot of problems. Had to make my customized menu.xml en rc.xml again. And ttm(tint task manager) just won't start at startup. I have this as startup-script

```

#!/bin/bash
eval `cat ~/.fehbg` &
tint &
gconf & 
gnome-settings-daemon &
pidgin &
conky -d -x 1140 -y 15 &
xcompmgr &

```

Does anybody know the solution?

---

### Post by ynnhoj on 2007-06-03
if you open an xterm and do "tint &" does it work normally, or do you get an error message?

---

### Post by Techn101 on 2007-06-03
Yes, than it starts. When I'm  starting Openbox,  I see black from the taskbar and than it goes away. 
I've tried the autostart.sh script from the New Openbox release too, and that also didn't work.

BTW: I use Arch Linux

---

### Post by ynnhoj on 2007-06-03
that's strange.  i guess it could be conflicting with one of the other processes you're starting from that script?  what if you were to move the call to tint to the end of the file, so it's the last program that's started?  you could even put a sleep ahead of it if necessary.

---

### Post by urukrama on 2007-06-04
It probably interferes with one of the other apps you have in your startup. I've had the same problem with skippy.

---

### Post by Techn101 on 2007-06-04
Placed tint and feh (for my background image) at the beginning om my ~/.config/openbox/autostart.sh file , and it looks that it's solved now.  Probably it was interfering with dbus or the gnome-settings-daemon .
Thanks for the help !

Edit: Mostly it starts at bootup; but when I start an app like swiftfox it goes away. 
And if I have other app's than feh or ttm in my autostart.sh script, it won't start at startup.

---

### Post by dbbolton on 2007-06-04
does it bother anyone else that box-look.org is getting junked up with all the EXACT SAME gtk themes that are already on gnome-look.org ?

---

### Post by bonzodog on 2007-06-05
> **dbbolton said:**
> does it bother anyone else that box-look.org is getting junked up with all the EXACT SAME gtk themes that are already on gnome-look.org ?

Um, that was my idea.

I was more or less behind getting box-look.org set-up.

Xfce-look.org, and gnome-look.org both share the gtk themes, and I thought that since Openbox and Fluxbox can both use gtk themes, it would be a good idea to allow the gtk themes into box-look.org, thus giving the *box users somewhere to resource everything they would need for a desktop - WM theme, gtk Theme, and Wallpaper.

The Gtk themes are useful outside of the gnome dekstop, which is why they keep the gtk name - they just theme the widgets and tool bars. Xfce also uses Gtk theming as part of it's desktop set-up, and now Openbox and Fluxbox can as well.

---

### Post by fuscia on 2007-06-05
> **dbbolton said:**
> does it bother anyone else that box-look.org is getting junked up with all the EXACT SAME gtk themes that are already on gnome-look.org ?

no.

---

### Post by dbbolton on 2007-06-05
> **bonzodog said:**
> Um, that was my idea.

I was more or less behind getting box-look.org set-up.

Xfce-look.org, and gnome-look.org both share the gtk themes, and I thought that since Openbox and Fluxbox can both use gtk themes, it would be a good idea to allow the gtk themes into box-look.org, thus giving the *box users somewhere to resource everything they would need for a desktop - WM theme, gtk Theme, and Wallpaper.

The Gtk themes are useful outside of the gnome dekstop, which is why they keep the gtk name - they just theme the widgets and tool bars. Xfce also uses Gtk theming as part of it's desktop set-up, and now Openbox and Fluxbox can as well.

i didn't mean that it was a poor idea. i meant that it is redundant to have the same content on two different sites.

---

### Post by yabbadabbadont on 2007-06-05
> **dbbolton said:**
> i didn't mean that it was a poor idea. i meant that it is redundant to have the same content on two different sites.

It is called an "offsite backup".  ;)

Look at all the themes that were lost when boxwhore went away....

---

### Post by dbbolton on 2007-06-05
> **yabbadabbadont said:**
> It is called an "offsite backup".  ;)

Look at all the themes that were lost when boxwhore went away....
good point. it's better than no themes at all.

---

### Post by NerdyShinobi on 2007-06-06
Ahoy!  I just wanted to pop my head in and say hello, and to thank you all for the great help in this thread.  I was drawn into the world of Openbox by K.Mandla's blog and stumbled in here looking for more configuration help.  I found the help, resources, fixes (the pypanel fix for Egdy works brilliantly in Feisty!), and even an impromptu German lesson.  Openbox just plain rawks.  Thanks fellow entities. :KS

---

### Post by ynnhoj on 2007-06-10
i was just looking at the downloads page on the openbox site, and version 3.4.2 is available -- so i guess 3.4 is officially released now.  also, obconf 2.0.1 is there for download.  hopefully they'll hit the arch repositories soon; i don't feeling like messing around with pkgbuilds...

---

### Post by urukrama on 2007-06-10
Wow, they're going fast! I still have a 3.4 preview installed. It is a serious upgrade -- such good new features. Makes me love Openbox even more.

---

### Post by Rasi on 2007-06-15
hi.. as i love openbox and thunar i naturally use those two.

but now i wanted to tweak my setup a little...

so i downloaded some icon set (nuoveXT) and extracted it to ~/.icons
i edited my ~/.gtk-2.0 file as seen in the shot... but the icons do not appear.


any help on this? i tried installing xfce4 and changed the icons in the xfce-setup... but when i start openbox, the icons still don't show up...


so here is the screen.. everything needed, is seen there:

[http://carnager.dyndns.org/icons.png](http://carnager.dyndns.org/icons.png)

---

### Post by bonzodog on 2007-06-15
hrm..not sure why it's doing it, but, a quick hint, create .gtkrc.mine, and move the icon theme setting to there, otherwise, the gtk theme manager will overwrite that file everytime the theme is changed.

One possibility is to install the icon theme to /usr/share/icons, It will probably work then.

---

### Post by urukrama on 2007-06-15
I don't know if you did, but you'll have to restart Thunar (or any other Gtk app) for the changes to take effect.

---

### Post by Rasi on 2007-06-15
i rebooted the computer :)

well, i dont know why,  but i removed all kde packages, that were left on my harddisk and suddenly it works...

well.. but now the next question.. i tried to create a keyboard shortcut for gmrun.. which does not work:

 <keybind key="A-F2">
    <action name="Execute">
      <startupnotify>
        <enabled>true</enabled>
        <name>Gmrun</name>
      </startupnotify>
      <execute>gmrun</execute>
    </action>
  </keybind>


any clue? when i press alt and F2, nothing happens

---

### Post by bonzodog on 2007-06-15
just looking at the documentation.

It looks like a simple syntax error. Try using <enabled>yes</enabled>
[http://icculus.org/openbox/index.php/Help:Actions#Execute](http://icculus.org/openbox/index.php/Help:Actions#Execute)

---

### Post by yabbadabbadont on 2007-06-15
I apologize if this has already been asked (and answered) in this thread (I didn't feel like reading through 30 pages), but can anyone recommend a good menu editor for openbox?  (version 3.3 if it matters)

---

### Post by dbbolton on 2007-06-15
> **yabbadabbadont said:**
> I apologize if this has already been asked (and answered) in this thread (I didn't feel like reading through 30 pages), but can anyone recommend a good menu editor for openbox?  (version 3.3 if it matters)
obmenu?

[http://obmenu.sourceforge.net/](http://obmenu.sourceforge.net/)

---

### Post by Rasi on 2007-06-15
hmm.. can be done with obmenu 

[http://obmenu.sourceforge.net/](http://obmenu.sourceforge.net/)



edit: damn.. too slow :P

---

### Post by yabbadabbadont on 2007-06-15
My thanks to both of you.

---

### Post by urukrama on 2007-06-15
yabba, why don't you try Openbox 3.4? You'll have to compile it yourself, but It improved immensely over 3.3.

---

### Post by yabbadabbadont on 2007-06-15
> **urukrama said:**
> yabba, why don't you try Openbox 3.4? You'll have to compile it yourself, but It improved immensely over 3.3.

I was actually thinking about building Fluxbox from SVN again and using it.  It's just a matter of what I'm used to when it comes to configuration files and such.  I may pull down the new openbox too.  It's always good to have plenty of shiny new toys with which to play.  :D

---

### Post by fuscia on 2007-06-17
wooooooooooooooow! 3.4 rox! this is nice.

---

### Post by ynnhoj on 2007-06-17
anybody use [wbar](http://freshmeat.net/projects/wbar/)?  it's a nifty little quick launch bar.  it's actually not that type of thing i'd normally use, but i've been playing with it anyways...

---

### Post by fuscia on 2007-06-18
> **fuscia said:**
> wooooooooooooooow! 3.4 rox! this is nice.

the new obconf is great, especially with the font options. and, the middle click desktop menu is much, much better. good stuff!

---

### Post by urukrama on 2007-06-18
Apart from the handy alt-tab, I especially like the extended [theme configuration options]("http://icculus.org/openbox/index.php/Help:Upgrading_to_3.4#Themes"). So much more to play with!

---

### Post by JMO707 on 2007-06-20
I just want a system tray. Docker... I just dont know how to use it.

Any advice?

---

### Post by dbbolton on 2007-06-21
> **JMO707 said:**
> I just want a system tray. Docker... I just dont know how to use it.

Any advice?
check out pypanel. for some reason, the system tray on perlpanel never worked for me.

---

### Post by urukrama on 2007-06-21
> **JMO707 said:**
> I just want a system tray. Docker... I just dont know how to use it.

Any advice?

Just type "docker" in gmrun or a terminal, or add "docker &" to your autostart menu. You won't see docker, until you start a program that uses the system tray. An icon will then appear in your dock (to change the position and settings of the dock, use obconf). There are several options you can use with docker (arrange icons vertically or horizontally, etc.). Type "man docker" into a terminal, and you'll get all the options.

Another systray is peksystray. I've never managed to get it installed, but some Openbox users like it.

---

### Post by JMO707 on 2007-06-21
Thanks. Im lookin for peksystray (I didnt know of it)
With docker the thing is that It dont "dock" anything. I tried Sonata, Pidgin and Azureus, but none of the appear on it. I readed the man page, but dont give too much details on this.

---

### Post by JMO707 on 2007-06-21
Well, it happens. I just was seeing how to autostart things, and looked that docker doesnt work when I launch it through a terminal. At the start of the sessin, it just do it =)

---

### Post by urukrama on 2007-06-22
Was there a problem with ObMenu in Feisty or Edgy? I can't quite remember, but if so, you could try out [Denu]("http://denu.sourceforge.net/"). From the website:

> Denu is aimed at easing menu organization over a set of varying window managers. Denu was specifically created for Gentoo Linux but as of 2.3.1 denu may be run according to the run-down from any distribution. Version 2.3.x supports gnome 2.10, KDE, fluxbox, openbox, IceWM, Xfce4 and waimea.

---

### Post by diatribe on 2007-06-24
was wondering is there any way to set up different background for the seperate desktops?  I know I have to use fbstebg for a wallpaper, so I assume it would ahve to be an outside program

---

### Post by dbbolton on 2007-06-28
when i try to launch obconf, i get this:
```
obconf: error while loading shared libraries: libobrender.so.0: cannot open shared object file: No such file or directory
```any ideas?

=============
edit: i was able to get obconf to run by doing this:
```

sudo ln -s libobrender.so libobrender.so.0
sudo ln -s libobparser.so libobparser.so.0
```

but now it just crashes as soon as the window appears.

---

### Post by fuscia on 2007-06-29
db, do yourself a favor and install 3.4. install obconf from source and you'll be mighty happy.

---

### Post by dbbolton on 2007-06-29
> **fuscia said:**
> db, do yourself a favor and install 3.4. install obconf from source and you'll be mighty happy.
i installed ob 3.4 from the deb they have on the site, but i installed obconf from the repos. that's probably the problem. i'll purge in and compile it from source and see if that helps

---

### Post by yabbadabbadont on 2007-06-29
> **urukrama said:**
> Was there a problem with ObMenu in Feisty or Edgy? I can't quite remember, but if so, you could try out [Denu]("http://denu.sourceforge.net/"). From the website:

Denu hasn't been maintained for a couple of years almost.  It looks like the newest file in the SVN is 22 months old.  I've tried menumaker and then hand edited the result, but it still leaves something to be desired.  I was starting to work on a modification of the fluxbox-generate_menu script that comes with Fluxbox so that it would produce a menu for fbpanel, but the newest version of fbpanel automatically finds all the freedesktop.org desktop files and builds a proper menu.  So now I'm going to see how difficult it is to modify the script to produce an Openbox menu.

---

### Post by dbbolton on 2007-06-29
> **dbbolton said:**
> i installed ob 3.4 from the deb they have on the site, but i installed obconf from the repos. that's probably the problem. i'll purge in and compile it from source and see if that helps
so, i downloaded the source for obconf 2.0.1 and after installing 30MB of dev packages and still not getting the go-ahead from ./configure, i decided to just install the feisty deb. it seems to be working all right so far.

---

### Post by fuscia on 2007-06-30
> **dbbolton said:**
> so, i downloaded the source for obconf 2.0.1 and after installing 30MB of dev packages and still not getting the go-ahead from ./configure, i decided to just install the feisty deb. it seems to be working all right so far.

cool. isn't the new version slick?

---

### Post by dbbolton on 2007-06-30
> **fuscia said:**
> cool. isn't the new version slick?
it's pretty much boss.

---

### Post by Freddy on 2007-06-30
Hi all, I'm playing around with OpenBox and I think I dig it but (and its a major but :)) I have some problems.

1) I upgraded with the deb packages to 3.4.2 and after that PyPanel wont show up at all, thats a major bummer :(. I reinstalled it, the repoway, cause when trying to install it from source I got some very weird errors.

2) When using [http://icculus.org/openbox/index.php/Help:Autostart](http://icculus.org/openbox/index.php/Help:Autostart) to make Pypanel (which did show up in 3.3) start when entering Openbox i get this.
```
Xsession unable to launch "home/freddan/.config/openbox/
autsotart.sh "X session---"/home/freddan/.config/openbox/
autostart.sh" not found; falling back to default session.
``` Another major bummer :(. I can log in to Openbox, but only when choosing a plain Openbox session, not the Openbox Autostart session.

3) I only have Enlightenment17 and Openbox installed (wanted the menus of Openbox, won't bother to edit xml files in E17 to get it the way I want) and when using Thunar, the icons it uses isn't what I choose in E17, they are just paperlooking icons that look really awful. How can I make Thunar use the icons that I choose in E17 icon manager. (Thunar doesn't use them inside E17 either.)

If someone of you can help me with these questions I would be eternally thankful, cause I want my Openbox to fully work and my icons to show :).

/Freddan

---

### Post by Freddy on 2007-06-30
I solved my number 3 problem, with a little help from Fuscia without her even knowing she helped me :). Thanks for your thread about exactly the same problem ;). Now it's just my number 1 and 2 issue to go and I'm a fully Openbox user.

/Freddan

---

### Post by Freddy on 2007-06-30
Damn I will soon give up and throw my computers out the window :(.

I finally found out why PyPanel won't execute, it seems that python2.5 has a problem with not finding the proper locale. 

This happens when trying to run pypanel:
```
Traceback (most recent call last):
  File "/usr/bin/pypanel" line 948, in <module>
    locale.setlocale(locale.LC_ALL,")
  File "/usr/libpython2.5/locale.py" line 476, in setlocale
    return_setlocale(catagory, locale)
locale.Error: unsupported locale setting
```I installed localeconf and run,
```
dpkg-reconfigure localeconf
```but I wasn't suprised when the same error showed up again :(.

I guess these minimal WMs just just isn't for me, but I will prevail, I just need some help prevailing :).

/Freddan

---

### Post by urukrama on 2007-06-30
Why don't you try another panel? There's plenty of them: perlpanel, lxpanel, etc. You can even use gnome-panel or xfce-panel. There was a fix for pypanel in Edgy around; perhaps that is of some use?

I've responded to your autostart problem in the [thread]("http://ubuntuforums.org/showthread.php?t=488761&highlight=openbox") you started on this.

---

### Post by yabbadabbadont on 2007-07-01
fbpanel is pretty nice.  At least the latest version (4.9) is.  You'll have to build if from source though.  I just "sudo apt-get build-dep fbpanel" and it pulled in all the dev libs needed.

---

### Post by Freddy on 2007-07-01
Thanks both of you, I guess I'll have to try fbpanel on for size.

---

### Post by moore.bryan on 2007-07-01
> **Freddy said:**
> Damn I will soon give up and throw my computers out the window :(.

I finally found out why PyPanel won't execute, it seems that python2.5 has a problem with not finding the proper locale. 

This happens when trying to run pypanel:
```
Traceback (most recent call last):
  File "/usr/bin/pypanel" line 948, in <module>
    locale.setlocale(locale.LC_ALL,")
  File "/usr/libpython2.5/locale.py" line 476, in setlocale
    return_setlocale(catagory, locale)
locale.Error: unsupported locale setting
```I installed localeconf and run,
```
dpkg-reconfigure localeconf
```but I wasn't suprised when the same error showed up again :(.

I guess these minimal WMs just just isn't for me, but I will prevail, I just need some help prevailing :).

/Freddan

*sorry i'm late coming into this, but did you install pypanel from the repos or compile it by hand?  i had to compile to get it working...*

---

### Post by Freddy on 2007-07-01
Thanks, for all the help. fbpanel seemed kind of nice and pypanel worked like a charm when it was compiled and not installed through Ubuntus repository.

I tried a another guide found here on our Howto section for making a working autostart file, it didn't work though. [http://doc.gwos.org/index.php/Openbo...ght#Use_obmenu](http://doc.gwos.org/index.php/Openbo...ght#Use_obmenu) 

When reaching the part where I'm suppose to make a desktop entry something goes terrible wrong. 
I fire up the file with nano.
```
sudo nano /usr/share/xsessions/openbox-autostart.desktop
```
but when trying to save the entry, I get
> Error saving, no such file or
I look up the place with Thunar and I can see and open the file there with the right entry but I cant save it? and of course I cant do a chmod on it either.

Thanks for any help.   /Freddan

---

### Post by Freddy on 2007-07-01
Haha I got it working, I just forgot that part about making a desktop entry and erased that file, logged back into Openbox and voila PyPanel autostarted :).

Everything is working now and I thank you all from the bottom of my heart.

/Freddan

---

### Post by fuscia on 2007-07-04
i just noticed this about perlpanel. in the lower right corner, in that pager thing (it's called a 'pager', right?), it not only shows what's open on a desktop, it shows what its position on the desktop is, as well. check out the screenshot.

edit: is this the only one that does that, or is this just the first time i noticed it? aside from being 'kinda neat', what's the point?

---

### Post by RedSquirrel on 2007-07-04
> **fuscia said:**
> i just noticed this about perlpanel. in the lower right corner, in that pager thing (it's called a 'pager', right?), it not only shows what's open on a desktop, it shows what its position on the desktop is, as well. check out the screenshot.

edit: is this the only one that does that, or is this just the first time i noticed it? aside from being 'kinda neat', what's the point?
It's just a miniature version of your workspace to give you a nice  visual representation of what you have open. You can probably even click and drag those little windows to another workspace in the pager. You can do that in every other pager I've used (fbpager has that for sure).

I would like to use a pager that has thumbnail previews of the desktop (like enlightenment has) but I haven't found anything that can do that. Instead of blank squares in the pager, it draws a thumbnail of your current desktop every half a second or so. I've always thought that was cool and I'm disappointed that that feature has been dropped in pretty much all pagers. :(

---

### Post by fuscia on 2007-07-04
> **RedSquirrel said:**
> It's just a miniature version of your workspace to give you a nice  visual representation of what you have open. You can probably even click and drag those little windows to another workspace in the pager. You can do that in every other pager I've used (fbpager has that for sure).

I would like to use a pager that has thumbnail previews of the desktop (like enlightenment has) but I haven't found anything that can do that. Instead of blank squares in the pager, it draws a thumbnail of your current desktop every half a second or so. I've always thought that was cool and I'm disappointed that that feature has been dropped in pretty much all pagers. :(

wow! you're right! i imagine this is how daredevil sees the world.

---

### Post by dbbolton on 2007-07-04
fuscia, does the system tray/notification area on perlpanel work for you?

---

### Post by fuscia on 2007-07-04
> **dbbolton said:**
> fuscia, does the system tray/notification area on perlpanel work for you?

i don't use it, but i just tried to add it to answer your question and i got this error message:

[i]Can't locate Gtk2/TrayManager.pm in @INC (@INC contains: /usr/share/perlpanel/ /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl . /home/fuscia/.perlpanel/applets /usr/share/perlpanel//PerlPanel/Applet /home/fuscia/.perlpanel/applets /usr/share/perlpanel//PerlPanel/Applet) at /usr/share/perlpanel//PerlPanel/Applet/NotificationArea.pm line 21.
BEGIN failed--compilation aborted at /usr/share/perlpanel//PerlPanel/Applet/NotificationArea.pm line 21.
Compilation failed in require at (eval 34) line 1.[/i]

---

### Post by dbbolton on 2007-07-04
> **fuscia said:**
> i don't use it, but i just tried to add it to answer your question and i got this error message:

[i]Can't locate Gtk2/TrayManager.pm in @INC (@INC contains: /usr/share/perlpanel/ /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl . /home/fuscia/.perlpanel/applets /usr/share/perlpanel//PerlPanel/Applet /home/fuscia/.perlpanel/applets /usr/share/perlpanel//PerlPanel/Applet) at /usr/share/perlpanel//PerlPanel/Applet/NotificationArea.pm line 21.
BEGIN failed--compilation aborted at /usr/share/perlpanel//PerlPanel/Applet/NotificationArea.pm line 21.
Compilation failed in require at (eval 34) line 1.[/i]
gah. i think that project is dead. i remember filing a bug report about the notification area a long time ago, and never heard anything about it afterward. i've been using pypanel since. it's a shame though, because i really like the customisationability of perlpanel.

---

### Post by fuscia on 2007-07-04
i saw reference to an ***obpanel*** somewhere today. now, i'm guessing this is some kind of typo as i can't find anything about it, but this could still be like what my father likes to call "the pursuit for the *real* italian spaghetti" (think 'holy grail").

---

### Post by diatribe on 2007-07-04
> **fuscia said:**
> i saw reference to an ***obpanel*** somewhere today. now, i'm guessing this is some kind of typo as i can't find anything about it, but this could still be like what my father likes to call "the pursuit for the *real* italian spaghetti" (think 'holy grail").

I think obpanel is another name for rspanel, check this site:

[http://code.google.com/p/rspanel/](http://code.google.com/p/rspanel/)

it is available for svn checkout

also trayer is good for a system tray, it is what I use in lieu of any panels.  between the window list and main menu a panel is kind of unnecessary IMO

---

### Post by dbbolton on 2007-07-04
> **diatribe said:**
> 
also trayer is good for a system tray, it is what I use in lieu of any panels.  between the window list and main menu a panel is kind of unnecessary IMO

link ?

---

### Post by ynnhoj on 2007-07-05
looks like you can find a .deb and a source tarball here: [http://developer.berlios.de/project/showfiles.php?group_id=1595](http://developer.berlios.de/project/showfiles.php?group_id=1595).  it looks like an old file, though..

---

### Post by bonzodog on 2007-07-05
As I have no real need for a Taskbar, but need a tray and clock, I decided to use conky for the clock (enlarged text as per k.mandlas layout), and a Program called [Peksystray]("http://peksystray.sourceforge.net") for the systray. Peksystray attaches itself to the openbox dock. Some Windowmaker dockapps work quite well in openbox as well.

---

### Post by diatribe on 2007-07-05
> **dbbolton said:**
> link ?

trayer is available in the repos; I use conky for the clock/other monitoring

---

### Post by urukrama on 2007-07-05
I've never managed to instally Peksystray on Dapper, so I just stick with docker, which does the job fine. Isn't trayer in the repos?

For a clock, I use conky and bbtime, which I'm quite fond of, except that I can't seem to change the font in bbtime, even though it should be possible.

---

### Post by dbbolton on 2007-07-06
is it possible to customise pypanel?

---

### Post by urukrama on 2007-07-07
Yes. Edit the .pypanelrc file that should be in your home directory. You have a lot of options there to play with.

---

### Post by Freddy on 2007-07-07
> **urukrama said:**
> Yes. Edit the .pypanelrc file that should be in your home directory. You have a lot of options there to play with.
And everything is well commentated, it was a breeze customizing PyPanel :).

---

### Post by fuscia on 2007-07-07
any of you tried 3.4 with gnome? (i mean selecting 'gnome-openbox' in gdm, not just *openbox --replace*.) the openbox middle-click menu works in it (the right-click menu doesn't). also, i noticed that gtk themes can be changed when just using openbox, by using the gnome-theme-manager.

---

### Post by w4tch0 on 2007-07-07
> **fuscia said:**
> any of you tried 3.4 with gnome? (i mean selecting 'gnome-openbox' in gdm, not just *openbox --replace*.) the openbox middle-click menu works in it (the right-click menu doesn't). also, i noticed that gtk themes can be changed when just using openbox, by using the gnome-theme-manager.

I am using it this way since 3.4 came out (currently running at 3.4.2).
And yes, right-click on desktop brings up the gnome menu instead of the openbox one, but i kinda understood it that this is the desired behavior  for the gnome-openbox sesion :)
And the integration of obconf into gnome setings menu is also cool :)

---

### Post by urukrama on 2007-07-07
> **fuscia said:**
> also, i noticed that gtk themes can be changed when just using openbox, by using the gnome-theme-manager.

Yeah, but that means you have another application running (gnome-settings-daemon). I prefer to keep things lighter, and specify the gtk and icon theme, as well as fonts, in the .gtkrc-2.0 or .gtkrc-2.0.mine files. It is a bit clumsy if you want to change themes regularly, but if you stick to one theme for a while, it is worth it.

---

### Post by w4tch0 on 2007-07-07
> **urukrama said:**
> Yeah, but that means you have another application running (gnome-settings-daemon). I prefer to keep things lighter, and specify the gtk and icon theme, as well as fonts, in the .gtkrc-2.0 or .gtkrc-2.0.mine files. It is a bit clumsy if you want to change themes regularly, but if you stick to one theme for a while, it is worth it.

Well, some of us don't run openbox because they want to save resources,  but rather because they think metacity is clumsy :P

If you login from gdm with "gnome-openbox" session selected, you obviously get a full gnome desktop as if you where running normal gnome session, only instead of metacity you get openbox and instead of the app which was changing decorations of metacity you get obconf :) .... this is by no means light weight :D

So if you are looking a for a lightweight approach, you might be better off with selecting the raw openbox session and customizing the things you want to run in it using some rc file (can't tell exactly which one, it's been years since i last time run such ultra light desktop :P ).

Also to add to the right-click menu: if you think of it, when running the gnome-openbox session, if you do the right-click on desktop you basicly don't do a right click on the openbox "root-window" but rather on the gnome app which is above it and handles all the icons and stuff .... thus you get gnome right-click menu.

---

### Post by fuscia on 2007-07-07
> **urukrama said:**
> Yeah, but that means you have another application running (gnome-settings-daemon). I prefer to keep things lighter, and specify the gtk and icon theme, as well as fonts, in the .gtkrc-2.0 or .gtkrc-2.0.mine files. It is a bit clumsy if you want to change themes regularly, but if you stick to one theme for a while, it is worth it.

1.4% of 175mb/1gb memory. as often as i change themes and wallpapers, it's worth it to me.

---

### Post by urukrama on 2007-07-07
When you use an old computer with less than a fourth of that memory, you become a little picky on what you run...

---

### Post by fuscia on 2007-07-07
> **urukrama said:**
> When you use an old computer with less than a fourth of that memory, you become a little picky on what you run...

i agree. my old desktop is pretty stripped down.

---

### Post by Freddy on 2007-07-07
Hi again. I posted this under the "General Help" section, but it's kind of hard to get answers there now a days, threads vanishes to fast.

I use Firefox under the the window manager OpenBox but when I watched couple of videos on youtube it suddenly crashed on me, I killed it of and restarted it, but the windecoration is gone and when I try to close it through File->Quit it kills of OpenBox. I have tried to purge it and to remove the configuration files inside /etc and /home, but with no luck at all.

In Enlightenment17 everything works like it should, so it must be a problem with OpenBox and their themes but I have tried to change those to but you guessed it, no luck with that either .

Anyone have any bright ideas, cause I'm totally out of them. / Freddan

---

### Post by fuscia on 2007-07-07
i've had problem with youtube crashing both epiphany and swiftfox. if i keep youtube relegated to only one tab, it doesn't happen (or, it hasn't happened, so far).

---

### Post by Freddy on 2007-07-07
> **fuscia said:**
> i've had problem with youtube crashing both epiphany and swiftfox. if i keep youtube relegated to only one tab, it doesn't happen (or, it hasn't happened, so far).
Great, good to know that. I had youtube in 2 tabs, that must have been why it crashed. Any ideas  how to get my Firefox to work again within OpenBox? I deleted every config file I could find and reinstalled it, with no luck.

/Freddan

---

### Post by urukrama on 2007-07-07
Firefox with Youtube crashes due to some flash problems unique to Ubuntu. I saw some fixes somewhere, though I haven't tried them (one of them involved something with Xorg and colours). It is the same with any youtube-like site (video.google.com, dailymotion, etc.). 

FF freezes regularly on my laptop (even with just one tab), but it never pulls Openbox down, and when I restart it (after killall-ing it) all is fine again. It seems like your problems are a bit more serious. Do you get anything error messages when you run it from the terminal?

EDIT: See [here]("http://ubuntuforums.org/showthread.php?p=1672572") or [here]("http://grumpymole.blogspot.com/2006/10/ubuntu-firefox-flash-crash-this-fix.html").

---

### Post by Freddy on 2007-07-07
> **urukrama said:**
> Firefox with Youtube crashes due to some flash problems unique to Ubuntu. I saw some fixes somewhere, though I haven't tried them (one of them involved something with Xorg and colours). It is the same with any youtube-like site (video.google.com, dailymotion, etc.). 

FF freezes regularly on my laptop (even with just one tab), but it never pulls Openbox down, and when I restart it (after killall-ing it) all is fine again. It seems like your problems are a bit more serious. Do you get anything error messages when you run it from the terminal?

EDIT: See [here]("http://ubuntuforums.org/showthread.php?p=1672572") or [here]("http://grumpymole.blogspot.com/2006/10/ubuntu-firefox-flash-crash-this-fix.html").
Hmm, I hate when somethings breaks and then suddenly fixes itself without me knowing how. I logged in and out and opened E17 and tried it from there and then back to Firefox through OpenBox  again, nothing worked. Then I worked in E17 for a while and came back to OB to try it from a terminal like you suggested and suddenly it all worked again and I have no clue why.

Well at least I know that I really need that fix you talked about :).

/Freddan

---

### Post by dbbolton on 2007-07-09
does anyone else use xcompmgr? it adds some nice shadows under things, at the expense of 1MB of memory.

[IMG]http://i103.photobucket.com/albums/m128/envyouraudience/ombre.png[/IMG]

i'm not really sure what else can be done with it

---

### Post by urukrama on 2007-07-09
I use it occasionally, especially when I use very light openbox themes with no or very small borders.

> **dbbolton said:**
> i'm not really sure what else can be done with it

You can make things transparent (though you need transset too), or make menus and windows fade in and out. See man xcompmgr for all the options. There is also a very detailed thread about xcompmgr [here]("http://ubuntuforums.org/showthread.php?t=75527").

---

### Post by moore.bryan on 2007-07-09
> **Freddy said:**
> Hmm, I hate when somethings breaks and then suddenly fixes itself without me knowing how. I logged in and out and opened E17 and tried it from there and then back to Firefox through OpenBox  again, nothing worked. Then I worked in E17 for a while and came back to OB to try it from a terminal like you suggested and suddenly it all worked again and I have no clue why.

Well at least I know that I really need that fix you talked about :).

/Freddan
*i'm currently using [swiftweasel]("http://swiftweasel.sourceforge.net/") with [gnash]("http://www.gnu.org/software/gnash/") as my primary flash player and i was able to have three tabs playing youtube content concurrently... maybe it's how ff works with flash...*

---

### Post by Freddy on 2007-07-09
> **moore.bryan said:**
> *i'm currently using [swiftweasel]("http://swiftweasel.sourceforge.net/") with [gnash]("http://www.gnu.org/software/gnash/") as my primary flash player and i was able to have three tabs playing youtube content concurrently... maybe it's how ff works with flash...*
Actually to my understanding, it's a problem between flash and alsa, when I changed to OSS for flash all my problems is gone. This is a well documented bug that Canonical has chosen to ignore, it's been here since hoary according to bugzilla.

/Freddan

---

### Post by moore.bryan on 2007-07-09
> **yabbadabbadont said:**
> I was starting to work on a modification of the fluxbox-generate_menu script that comes with Fluxbox so that it would produce a menu for fbpanel,... So now I'm going to see how difficult it is to modify the script to produce an Openbox menu.
*aren't you just looking for [menumaker]("http://menumaker.sourceforge.net/")?*

---

### Post by moore.bryan on 2007-07-09
> **Freddy said:**
> Actually to my understanding, it's a problem between flash and alsa, when I changed to OSS for flash all my problems is gone.
*that would make sense... i'm using oss.*

---

### Post by urukrama on 2007-07-10
In Openbox 3.4, if you are using the root menu or client list menu and an application starts, the menu will always disappear when the application appears. This wasn't the case in ob 3.3. Does anyone of you know how to disable that? It is irritating at times.

---

### Post by yabbadabbadont on 2007-07-10
> **moore.bryan said:**
> *aren't you just looking for [menumaker]("http://menumaker.sourceforge.net/")?*

No, but thanks for the suggestion.  I've tried menumaker and didn't care much for the output.  Plus, it misses some applications.  I have already modified my fluxbox-generate_menu script to my liking and to include some more applications.  However, since I've started using the latest version of fbpanel, it isn't as high a priority as it was before to make it output an Openbox menu.  The new fbpanel's menu plugin automatically scans all the desktop files in the /usr/share/applications directory and generates a proper menu.

---

### Post by moore.bryan on 2007-07-10
[I]@yabbadabbadont
no problem... i've always found it useful, but i don't have many programs.
[/I]

---

### Post by urukrama on 2007-07-17
My install got really messed up two days ago, so I went for a complete reinstall. Since I just use Openbox, I decided to go for a server install and add whatever else I need or want. It took me a while, but it was worth it. Openbox is unbelievably fast! Incredible on this old machine...

I do have some problems, however. For some reason, I can't get my gtk and icon theme and fonts right. My gtk theme is specified in the .gtkrc-2.0 file in my home directory (as "include "/home/urukrama/.themes/THEMENAME/gtk-2.0/gtkrc", and when I use Openbox that gets displayed correctly. Any other settings (fonts, icons, only icons in toolbar) just don't show. 

It doesn't make any difference whether I put it in my .gtkrc2.0 file or my .gtkrc2.0.mine file (which is what I prefer). I know the codes are correctly written, since the file is a copy from my previous install, and everything worked fine there. (When I run gnome-settings-manager, I can easily change fonts, icons and themes, but I prefer not to use it as I'm running short on resources.)

Do I need some special libraries installed for this to display properly? Any suggestions?

EDIT: I should perhaps add that I did not install gtk-theme-switch or an alternative, as I always change themes through these two text files.

---

### Post by fuscia on 2007-07-17
> **urukrama said:**
> EDIT: I should perhaps add that I did not install gtk-theme-switch or an alternative, as I always change themes through these two text files.

what i would do would be install gtk-theme-switch, see if that straightens things out, then dump it and hope things still were fixed.

---

### Post by urukrama on 2007-07-17
I just did that, fuscia, but it doesn't help. Gtk-theme-switch doesn't even work with most of the themes I have in my ~/.themes folder. I'll keep looking.

---

### Post by fuscia on 2007-07-17
> **urukrama said:**
> I just did that, fuscia, but it doesn't help. Gtk-theme-switch doesn't even work with most of the themes I have in my ~/.themes folder. I'll keep looking.

and you've got the gtk-engines you need?

---

### Post by bonzodog on 2007-07-17
Openbox does use a couple of libraries to load the gtk themes in itself. Make sure you have the all the engines installed that you need for a start -- one of them might pull down the missing gtk2.0 libraries.

It would be interesting seeing a log of openboxes start up -- it might tell you that you have forgotten something, as there is a chance that the gtk theming is not classed as an absolute dependency by apt.

---

### Post by RedSquirrel on 2007-07-17
@urukrama:

Check your ~/.xsession-errors file as well. There might be some information in there.

Which icon themes and fonts are you trying to use? Does it work with the gtk and icon themes out of the repositories? e.g., packages gtk2-engines, tango-icon-theme

---

### Post by urukrama on 2007-07-17
Hmm. This is strange. I couldn't stand the ugly default fonts and icons much longer, so I went back to using xfce, where everything had always looked fine. I just logged out of xfce, and back into openbox to have a look at the .xsessions-errors file as RedSquirrel suggested, and now everything looks fine again.

Very strange, since I did look at the xsessions-errors file earlier and it had something about bad font settings (can't remember the details).But that is all gone now, and icons, fonts and all the rest looks mighty fine now. Defies my comprehension.

But thank you all for your help. Much appreciated!

---

### Post by Somenoob on 2007-07-17
> **urukrama said:**
> Hmm. This is strange. I couldn't stand the ugly default fonts and icons much longer, so I went back to using xfce, where everything had always looked fine. I just logged out of xfce, and back into openbox to have a look at the .xsessions-errors file as RedSquirrel suggested, and now everything looks fine again.

Very strange, since I did look at the xsessions-errors file earlier and it had something about bad font settings (can't remember the details).But that is all gone now, and icons, fonts and all the rest looks mighty fine now. Defies my comprehension.

But thank you all for your help. Much appreciated!

Did you put gnome-daemon-settings in your openbox launch list?

---

### Post by urukrama on 2007-07-17
No.

---

### Post by RedSquirrel on 2007-07-17
> **urukrama said:**
> Hmm. This is strange. I couldn't stand the ugly default fonts and icons much longer, so I went back to using xfce, where everything had always looked fine. I just logged out of xfce, and back into openbox to have a look at the .xsessions-errors file as RedSquirrel suggested, and now everything looks fine again.

Very strange, since I did look at the xsessions-errors file earlier and it had something about bad font settings (can't remember the details).But that is all gone now, and icons, fonts and all the rest looks mighty fine now. Defies my comprehension.

The xfce4 metapackage pulls in a lot of stuff so very likely the appropriate packages (gtk etc.) were installed with that.  Whatever the reason, I'm glad everything is working for you again. :)

---

### Post by urukrama on 2007-07-17
It is probably something like that, though I did keep an eye on what came with xfce4 when I installed it, and it all seemed specific xfce4 stuff, nothing exclusively gtk related (I had those already installed). 

But whatever happened, I'm a happy man :)

---

### Post by urukrama on 2007-07-18
One more odd thing happens: to log out of Openbox I always have to click exit in the menu *twice*. THe first time my dock goes to the top left corner (as it normally does when you log out), but then nothing else happens. Only if I click exit a second time go I get back to gdm. 

I have no idea why this happens.

---

### Post by urukrama on 2007-07-22
I want to add a shutdown/reboot option to my Openbox menu, but would like something that doesn't require sudo, and with some sort of confirmation before shutting down/rebooting. Is there something around that I could use?

Gnome, Xfce, Kde etc all have shutdown/restart options that don't require sudo, btu I can't figure out what commands they use. Even if I could figure that out, without any confirmation dialog box, that would already be great!

---

### Post by moore.bryan on 2007-07-22
> **urukrama said:**
> I want to add a shutdown/reboot option to my Openbox menu, but would like something that doesn't require sudo, and with some sort of confirmation before shutting down/rebooting. Is there something around that I could use?
[I]i think most will suggest you add a line to the visudo file to allow the shutdown script to be called without a password:
```
sudo visudo
``` and add at the bottom ```
ALL     ALL=NOPASSWD:/usr/bin/shutdown
``` then, when you call ```
sudo shutdown -r now
``` and ```
sudo shutdown -h now
``` it won't require a password.
as far as the dialog, i think you might want to look at gshutdown, kshutdown, or wmshutdown to see if one of them fits your needs; they're all in the repos.[/I]

---

### Post by urukrama on 2007-07-22
Thanks for the reply, bryan.

I tried wmshutdown, but that just doesn't work. I installed it from the repos, but can't find it anywhere on my system and using the 'wmshutdown' command tells me that there is no such command.

kshutdown is nice, but very slow on this computer (I guess because it first needs to load all those kde things).

I can't find a gshutdown in the repos, but if that is the general gnome dialog, that'd be perfect!

---

### Post by moore.bryan on 2007-07-22
[I][here]("http://packages.ubuntu.com/feisty/gnome/gshutdown")'s the page for gshutdown; it's in the universe repos.  wmshutdown is an icon/button which you could put in a dock or panel to click for the shutdown dialog, but as far as i know, can't just be called from the cli.
--------
EDIT:
--------
ah... i think i know why you couldn't find it: you're running dapper.  it seems it doesn't show-up until feisty!  you could still try to install it by upgrading all it's dependencies and/or installing the [source]("http://gshutdown.tuxfamily.org/release/gshutdown-0.2.tar.gz").  that might take a while, but the only other option would seem to be dist-upgrading.  sorry... :-(
[/I]

---

### Post by urukrama on 2007-07-22
Openbox 3.4.3 is out! And Obconf has been updated too.

Read the news [here]("http://icculus.org/openbox/index.php/Openbox:News#Openbox_3.4.3_and_ObConf_2.0.2_released")

See the changelog [here]("http://icculus.org/openbox/index.php/Openbox:Changelog#3.4.3") (another long list)

---

### Post by dbbolton on 2007-07-22
is there a way to get nitrogen to set the background to a specific image at startup?

---

### Post by fuscia on 2007-07-22
i can't even figure out how to get nitrogen installed. it seems that every time i try, i end up with dependency problems, or something like that.

---

### Post by fuscia on 2007-07-22
btw, 3.4.3 is out, as is obconf 2.0.2. i'm still reeling from 3.4.2.

---

### Post by dbbolton on 2007-07-22
> **fuscia said:**
> i can't even figure out how to get nitrogen installed. it seems that every time i try, i end up with dependency problems, or something like that.
i tried the deb that was linked from their site, but it told me that the dependency 'libc6' was not satisfiable. (i think the person who compiled the deb made an error.) but, i compiled it from the svn and it works fine.

---

### Post by urukrama on 2007-07-23
I installed gshutdown, but it only works with KDE and Gnome. Oh well.

---

### Post by moore.bryan on 2007-07-23
> **urukrama said:**
> I installed gshutdown, but it only works with KDE and Gnome. Oh well.
*that is a shame... does it just not load?*

---

### Post by urukrama on 2007-07-23
It loads fine, but then gives an error message that it only works with Gnome and KDE. It looks nice though: you can shut down/reboot/suspend etc your computer in x amount of minutes (or days).

---

### Post by moore.bryan on 2007-07-23
> **urukrama said:**
> It loads fine, but then gives an error message that it only works with Gnome and KDE. It looks nice though: you can shut down/reboot/suspend etc your computer in x amount of minutes (or days).
*you can do that with the shutdown command, though... "now" can be so many different things.  ;-)*

---

### Post by urukrama on 2007-07-23
Interesting. Thanks for the help.

---

### Post by moore.bryan on 2007-07-24
*no problem... sorry it wasn't able to get working for you...*

---

### Post by BOBSONATOR on 2007-07-24
fuscia, dbbolton, this is for you.


```
wget http://l3ib.org/nitrogen/files/nitrogen-1.0.tar.gz
```

```
 tar -xzvf nitrogen-1.0.tar.gz
```

```
cd nitrogen-1.0
```

```
./configure
```

It might ask for a missing dependency. just find it through synaptic, and install its -dev package along with it.

```
make
```

```
sudo make install
```

and for usage,

direct it to your wallpaper directory.
```
nitrogen /home/USERNAME/pictures
```

---

### Post by dbbolton on 2007-07-24
> **BOBSONATOR said:**
> fuscia, dbbolton, this is for you.


```
wget http://l3ib.org/nitrogen/files/nitrogen-1.0.tar.gz
```

```
 tar -xzvf nitrogen-1.0.tar.gz
```

```
cd nitrogen-1.0
```

```
./configure
```

It might ask for a missing dependency. just find it through synaptic, and install its -dev package along with it.

```
make
```

```
sudo make install
```

and for usage,

direct it to your wallpaper directory.
```
nitrogen /home/USERNAME/pictures
```
do you know if there is a command that you can add to your startup script in order to make nitrogen set the background automatically at startup?

i've been using feh to do that, but if i can kill two birds with one stone, all the better.

---

### Post by fuscia on 2007-07-24
> **BOBSONATOR said:**
> fuscia, dbbolton, this is for you.

wow! it works! thanks, bob. your kindness outweighs you. 

i feel a little sad moving on from feh. feh was always so dependable. but, i guess our little openbox is all grown up now. 'sniff'.

---

### Post by el mariachi on 2007-07-24
hey guys!
thanks for pointing me to this topic dbbolton!
I'm taking my first steps in OpenBox and became really sad when I found that it doesn't come with all the neat menus and panels... 

I'll try ttm (although I'm not very fluent in SVN stuff). How can I have a menu like yours? And to the guys that don't have a visible system tray where are your tray icons?

---

### Post by dbbolton on 2007-07-24
> **el mariachi said:**
> hey guys!
thanks for pointing me to this topic dbbolton!
I'm taking my first steps in OpenBox and became really sad when I found that it doesn't come with all the neat menus and panels... 

I'll try ttm (although I'm not very fluent in SVN stuff). How can I have a menu like yours? And to the guys that don't have a visible system tray where are your tray icons?
i think the fact that it doesn't come with anything makes it more fun, because you get to make it exactly how you want!

to get started with your menus, try using obmenu:
[http://obmenu.sourceforge.net/](http://obmenu.sourceforge.net/)

about the system tray- the only panel that i have used with a working system tray is pypanel. you can get it from the repos: ```
sudo apt-get install pypanel
```

perlpanel allegedly comes with a system tray but i've never gotten it to work.

ttm is just a window list with text labels (no icons of any sort), and it doesn't have a system tray.

---

### Post by el mariachi on 2007-07-24
I need a window list, I don't know how to live without my windows listed.
Although this doesn't look:
```
mariachi@central-dogma:~/ttm/src$ tint

(process:11098): Pango-CRITICAL **: pango_font_description_from_string: assertion `str != NULL' failed
Segmentation fault (core dumped)

```
I'm a noob at compiling, even though the instructions seem fool proof lol

---

### Post by dbbolton on 2007-07-24
> **el mariachi said:**
> I need a window list, I don't know how to live without my windows listed.
Although this doesn't look:
```
mariachi@central-dogma:~/ttm/src$ tint

(process:11098): Pango-CRITICAL **: pango_font_description_from_string: assertion `str != NULL' failed
Segmentation fault (core dumped)

```
I'm a noob at compiling, even though the instructions seem fool proof lol
you need to install these packages before you compile tint:

libcairo2-dev
libpango1.0-dev

---

### Post by urukrama on 2007-07-24
> **el mariachi said:**
> And to the guys that don't have a visible system tray where are your tray icons?

I use docker (in the repos). It is a very light system tray and loads in the 'dock', which you can configure in obconf (position, autohide, etc.) It is useful if you don't want a panel. If you do like panels, you can use pypanel, perlpanel or even gnome-panel, kicker, or xfce-panel (they all have system trays).

Openbox is very minimalistic, as you've noticed, but that is its strength. You just add whatever you want, and there are plenty of lightweight apps that work very well with Openbox.

Hope you have fun with openbox! Just try things out and play around.

---

### Post by urukrama on 2007-07-24
> **el mariachi said:**
> I need a window list, I don't know how to live without my windows listed.

That is what I thought for a while, but I've really learned to work without it. I use pypanel still occasionally, but generally have no panel (or window list) at all. Alt-tab and openbox' client-list-menu are all I need to keep an eye on my open applications. Or I use skippy, though it doesn't show the minimised apps, unfortunately.

---

### Post by urukrama on 2007-07-24
> **fuscia said:**
> i saw reference to an ***obpanel*** somewhere today. now, i'm guessing this is some kind of typo as i can't find anything about it, but this could still be like what my father likes to call "the pursuit for the *real* italian spaghetti" (think 'holy grail").

Is this your *real* italian spaghetti: [http://cia.vc/stats/project/obpanel](http://cia.vc/stats/project/obpanel)?

---

### Post by ynnhoj on 2007-07-24
> **el mariachi said:**
> I need a window list, I don't know how to live without my windows listed.
Although this doesn't look:
```
mariachi@central-dogma:~/ttm/src$ tint

(process:11098): Pango-CRITICAL **: pango_font_description_from_string: assertion `str != NULL' failed
Segmentation fault (core dumped)

```
I'm a noob at compiling, even though the instructions seem fool proof lol
if you'd like to do it the easy way (so to speak), you might as well use xfce4-panel.  or maybe even gnome-panel -- but i like xfce4-panel much better!  it's easy to configure, and will have everything you're going to need.  just use aptitude to install the xfce4-panel package (if you are using thunar as your file manager, you'll probably have most of the xfce dependencies installed anyways..)

---

### Post by fuscia on 2007-07-24
> **urukrama said:**
> Is this your *real* italian spaghetti: [http://cia.vc/stats/project/obpanel](http://cia.vc/stats/project/obpanel)?

that's a some spicey meataball! i totally forgot about that. too bad i don't understand subversion yet (as if i'll ever get around to it). 

el mariachi, you're in for a true delight. i don't know anything about anything and i'm very much at home in openbox. i use it on my old desktop with lightweight apps and on my fancy laptop with top dollar apps. it's great on both. i once asked the openbox mailing list which distro did openbox the best. they all said it didn't matter, that openbox worked equally well on all of them. that was cool.

---

### Post by dbbolton on 2007-07-24
has anyone been able to get the gmail pipemenu to work?
[http://david.chalkskeletons.com/scripts/gmail-openbox-0.0.3.1.py](http://david.chalkskeletons.com/scripts/gmail-openbox-0.0.3.1.py)

if so, could you help a brother out?

---

i saved the script as '/home/daniel/.config/openbox/scripts/gmail.py'. i opened it with gedit and entered my username and password in the proper fields. then i added this line to my menu.xml
```
    <menu id="gmail" label="Gmail" execute="/home/daniel/.config/openbox/scripts/gmail.py" />
```

i'm not sure if it was necessary, but i also installed the package 'python-libgmail'.

it's just giving me a blank menu. and a headache.

---

### Post by ynnhoj on 2007-07-24
> **fuscia said:**
> that's a some spicey meataball! i totally forgot about that. too bad i don't understand subversion yet (as if i'll ever get around to it).
there's not much to it; in this case you'd do a
```
svn checkout http://rspanel.googlecode.com/svn/trunk/ rspanel
```
to get the latest revision of the projects source, and then it's just a matter of checking out the readme and following the instructions to build and install (which tends to be the standard.. ./configure; make; make install).

---

### Post by urukrama on 2007-07-24
> **fuscia said:**
> that's a some spicey meataball! i totally forgot about that. too bad i don't understand subversion yet (as if i'll ever get around to it).

There is not that much to it, if you just want to install a subversion app. Install subversion (in the repos), and then just do 

```
svn checkout http://rspanel.googlecode.com/svn/trunk/ rspanel
```

and you'll have the source code in your home directory. Then just do the usual ./configure, make and checkisntall/make install

I haven't installed it, as I miss libobrender-dev, which is needed for compiling, and couldn't be bothered to search for it.

EDIT: seems like ynnhoj beat me to it :)

---

### Post by ynnhoj on 2007-07-24
> **dbbolton said:**
> has anyone been able to get the gmail pipemenu to work?
[http://david.chalkskeletons.com/scripts/gmail-openbox-0.0.3.1.py](http://david.chalkskeletons.com/scripts/gmail-openbox-0.0.3.1.py)

if so, could you help a brother out?

---

i saved the script as '/home/daniel/.config/openbox/scripts/gmail.py'. i opened it with gedit and entered my username and password in the proper fields. then i added this line to my menu.xml
```
    <menu id="gmail" label="Gmail" execute="/home/daniel/.config/openbox/scripts/gmail.py" />
```

i'm not sure if it was necessary, but i also installed the package 'python-libgmail'.

it's just giving me a blank menu. and a headache.
you definitely need the python-libgmail package -- i tried it before i installed it, and the script threw an error about that module being absent.

what's the output when you run it yourself from the command line?  ie:
```
python /home/daniel/.config/openbox/scripts/gmail.py
```
i get a menu with one item (the label says "700 new messages" :o)

maybe it's not working because you've forgotten to make the script executable?  (chmod u+x ~/.config/openbox/scripts/gmail.py)
also: have you included the closing tag for the pipe menu? ("<menu id="gmail" />")  i have a feeling your menu wouldn't work at all if you did forget, but it's another possible problem i guess.

---

### Post by dbbolton on 2007-07-24
> **ynnhoj said:**
> you definitely need the python-libgmail package -- i tried it before i installed it, and the script threw an error about that module being absent.

what's the output when you run it yourself from the command line?  ie:
```
python /home/daniel/.config/openbox/scripts/gmail.py
```
i get a menu with one item (the label says "700 new messages" :o)

maybe it's not working because you've forgotten to make the script executable?  (chmod u+x ~/.config/openbox/scripts/gmail.py)
also: have you included the closing tag for the pipe menu? ("<menu id="gmail" />")  i have a feeling your menu wouldn't work at all if you did forget, but it's another possible problem i guess.
ok, i made it executable. when i run it from the command line, it basically tells me that i have 2 new messages. however, my menu still looks like this (after restarting OB)

[IMG]http://i103.photobucket.com/albums/m128/envyouraudience/gpmu.png[/IMG]

---

### Post by ynnhoj on 2007-07-24
odd.  it's doing the same thing for me :/

i wonder how old this script is?  the comment beside it in the list of pipe menu scripts on the openbox wiki is "probably needs work."

**edit:** i changed the shebang line in the script from
```
#!/usr/bin/python2.3
```
to
```
#!/usr/bin/python
```
and it seems to work fine.  maybe the author wasn't sure if it would work with python2.5.. but not everybody necessarily has older versions of python installed (2.3 was a while ago).


yet another edit:  i guess i spoke too soon!  the menu displays okay, but the link it generates to be opened in yer browser doesn't seem to work.  i get a page with the "google accounts" header and an "invalid request" error message.

---

### Post by dbbolton on 2007-07-24
> **ynnhoj said:**
> odd.  it's doing the same thing for me :/

i wonder how old this script is?  the comment beside it in the list of pipe menu scripts on the openbox wiki is "probably needs work."
guess they were right :)

---

### Post by DonnieP on 2007-07-24
> **urukrama said:**
> I haven't installed it, as I miss libobrender-dev, which is needed for compiling, and couldn't be bothered to search for it.

The dependencies for rspanel (if you didn't compile OB in the first place in which case you'd already have these) are:
libpango1.0-dev
libxml2-dev

Question:  Now that I've got rspanel working, is there any way to configure it?  If there is, I can't find it (like changing it's position).

---

### Post by fuscia on 2007-07-25
thanks, you guys. i got rspanel installed. it's sort of a tastefu...even more tasteful version of the fluxbox panel. no clock, though...

---

### Post by el mariachi on 2007-07-25
@dbbolton I already had those libs installed at the time of compilation.

The strong point of OpenBox, besides being minimalistic, is it's (light)weight, right? So, to make things even more light and fast, what apps did you replace from the original gnome? Stuff like file managers, image viewers, etc-

---

### Post by urukrama on 2007-07-25
As file manager I use Thunar. As media player I use mpd + gmpc. Mousepad/Leafpad for a simple text editor. Feh as image viewer (and to set the desktop image). 

I need some heavier apps for work as well (mainly OpenOffice), but by keeping other things light, OpenOffice does not slow my system down as it does in Gnome (on a 6 year old computer). I could also use a lighter browser, but I'm used to Opera, both for browsing and email.

You'll have to figure out yourself where you want to strike the balance. If you like some non-lightweight apps and have a very recent and fast computer, you might not want to go for all the lightweight options. Just go for whatever is practical for you.

---

### Post by urukrama on 2007-07-25
> **DonnieP said:**
> The dependencies for rspanel (if you didn't compile OB in the first place in which case you'd already have these) are:
libpango1.0-dev
libxml2-dev

I did compile Openbox and have those packages installed, but when I try to compile, I get this error message:

```
checking for libX11... yes
checking for ObRender... no
Cannot find libObRender, aborting.

```

Not that it really matters though. I'm not that interested in it, and probably won't use it.

---

### Post by fuscia on 2007-07-25
> **el mariachi said:**
> @dbbolton I already had those libs installed at the time of compilation.

The strong point of OpenBox, besides being minimalistic, is it's (light)weight, right? So, to make things even more light and fast, what apps did you replace from the original gnome? Stuff like file managers, image viewers, etc-

feh is a good image viewer and background setter. gqview is pretty light and is also a good image viewer. i use thunar for a file manager, but there are a bunch of others, like pcman, emilfm, etc. i use epiphany for a browser, but i've also used dillo and links2 (in graphical mode). if you want an email client, sylpheed-claws-gtk2 is great and will pick up your gtk theme (i just use gmail). audacious for music.

---

### Post by el mariachi on 2007-07-25
I also want to use Thunar, but I don't know how to replace Nautilus with it.
This is how i wanted my desktop to look like, with panels and dock, yet minimal.
[http://thunar.xfce.org/images/user-screenshots/dougwhiteley-20060326.png](http://thunar.xfce.org/images/user-screenshots/dougwhiteley-20060326.png)

I already use epiphany -blazing fast.

I tried to install OB in a friend's computer witch uses Xubuntu (I converted him to the Linux side:lolflag:) but it doesn't seem to work out-of-the-box. Is it a big pain to make it work, or it's doable?

---

### Post by dbbolton on 2007-07-25
> **el mariachi said:**
> @dbbolton I already had those libs installed at the time of compilation.

The strong point of OpenBox, besides being minimalistic, is it's (light)weight, right? So, to make things even more light and fast, what apps did you replace from the original gnome? Stuff like file managers, image viewers, etc-
hmm, then i don't know.

as for apps, you can replace gaim with ayttm. dillo is probably the lightest graphical web browser. i agree with urukrama on leafpad, thunar, and feh.

if you want to go ultralight, you could try terminal-based apps like midnight commander (mc), emacs, etc.

---

### Post by dbbolton on 2007-07-25
> **el mariachi said:**
> I also want to use Thunar, but I don't know how to replace Nautilus with it.
This is how i wanted my desktop to look like, with panels and dock, yet minimal.
[http://thunar.xfce.org/images/user-screenshots/dougwhiteley-20060326.png](http://thunar.xfce.org/images/user-screenshots/dougwhiteley-20060326.png)

I already use epiphany -blazing fast.

I tried to install OB in a friend's computer witch uses Xubuntu (I converted him to the Linux side:lolflag:) but it doesn't seem to work out-of-the-box. Is it a big pain to make it work, or it's doable?
this might help for replacing nautilus:

[http://www.psychocats.net/ubuntu/nonautilusplease](http://www.psychocats.net/ubuntu/nonautilusplease)

---

### Post by el mariachi on 2007-07-25
> **dbbolton said:**
> this might help for replacing nautilus:

[http://www.psychocats.net/ubuntu/nonautilusplease](http://www.psychocats.net/ubuntu/nonautilusplease)

hummm the script didn't work..:confused:

---

### Post by urukrama on 2007-07-25
> **el mariachi said:**
> I also want to use Thunar, but I don't know how to replace Nautilus with it.

You won't have to replace Nautilus with Thunar in Openbox if you don't load Nautilus (and I don't see why you should). Nautilus is linked to Gnome, but Openbox isn't so you won't use it. Unless, you want to use the Places Menu in Gnome-panel, of course. If so, you can use [this script]("http://psychocats.net/ubuntu/nonautilusplease") to change the default file manager to Thunar (note this will also affect your Gnome session!)

Nautilus also draws the desktop in Gnome. Openbox doesn't manage the desktop, but if you want launchers etc. you can use idesk (in the repos). Note that if you let Nautilus draw the desktop in Openbox, all folders on  the desktop will open with Nautilus by default. Aysiu's script does not affect that (as the desktop is Nautilus).

> This is how i wanted my desktop to look like, with panels and dock, yet minimal.
[http://thunar.xfce.org/images/user-screenshots/dougwhiteley-20060326.png](http://thunar.xfce.org/images/user-screenshots/dougwhiteley-20060326.png)

This should be doable in Openbox. Just use the panels of your choice (xfce-panel works fine), choose an [Openbox theme]("http://box-look.org/index.php?xcontentmode=7402") you look, and edit your menu (using [obmenu]("http://obmenu.sourceforge.net/")) to look like the one in the picture. 

> I tried to install OB in a friend's computer witch uses Xubuntu but it doesn't seem to work out-of-the-box. Is it a big pain to make it work, or it's doable?

It is doable, but it requires a little work. When you say it doesn't work out-of-the-box, what do you mean? Does it not load properly, or does it have very few things you can do? Note that when you launch Openbox for the first time you just get a blank screen (the desktop). Right click and you have your menu. 

If you haven't done so already, follow the instructions in this [howto]("http://ubuntuforums.org/showthread.php?t=192106&highlight=openbox+howto"). If you use Openbox 3.4 (which I highly recommend), some of the info in there is no longer relevant (like the autostart section -- just skipp that as Ob 3.4 comes with an autostart system like the one described there; the commands given in the sample autostart file in that howto *will* work, though), but setting up the menus etc is still the same.

If you want to use Openbox 3.4, download a Feisty deb [here]("http://icculus.org/openbox/releases/openbox_3.4.3-0ubuntu1_i386.deb"). A Feisty deb for Obconf2 can be found [here]("http://icculus.org/openbox/obconf/obconf_2.0.2-0ubuntu1_i386.deb"). (Obconf makes it a lot easier to switch themes, change fonts, and configure Openbox)

---

### Post by el mariachi on 2007-07-25
OB is running fine in my computer now. and it's unbelievably FAST:KS

I'll try harder the next time I'm at my friend's house.
I actually found out how to switch OB on by accident (kill nautilus session:lolflag:)
Now I discover that I'm too "addicted" to the Gnome Main Menu (Apps, Places, System). the places menu is irrelevant, because a simple thunar launcher does the trick. but how do I access all those other functions now? Stuff like themes and system monitor.

ObMenu isn't configuring my menu right... sometimes it does change it sometimes it doesn't...

I'm liking OB so far, I'll need to re-learn how to get to some places again though

EDIT: Like, for instance, HOW DO I TAKE A SCREENSHOT NOW? lol Print Screen Doesn't work anymore

---

### Post by dbbolton on 2007-07-25
> **el mariachi said:**
> OB is running fine in my computer now. and it's unbelievably FAST:KS

I'll try harder the next time I'm at my friend's house.
I actually found out how to switch OB on by accident (kill nautilus session:lolflag:)
Now I discover that I'm too "addicted" to the Gnome Main Menu (Apps, Places, System). the places menu is irrelevant, because a simple thunar launcher does the trick. but how do I access all those other functions now? Stuff like themes and system monitor.

ObMenu isn't configuring my menu right... sometimes it does change it sometimes it doesn't...

I'm liking OB so far, I'll need to re-learn how to get to some places again though

EDIT: Like, for instance, HOW DO I TAKE A SCREENSHOT NOW? lol Print Screen Doesn't work anymore
the command to change your theme (assuming that you have gnome installed, not kde) is 'gnome-theme-manager' and the command for the system monitor is 'gnome-system-monitor'.  i use 'gnome-screenshot --delay=5' to take screenshots, where 5 is the number of seconds of delay.

one way to figure out the command for the entries is to just guess at it (which is what i normally do) or open a gnome session, launch the app from the menu, then open the system monitor and look at the process name, which is usually the same as the command to launch it. 

if you can't figure it out, browse to /usr/bin/ and look at the executables whose names start with gnome- . you'll probably find what you're looking for.

also, the deskbar in gnome is helpful to figure out the command for certain gnome apps.

---

### Post by urukrama on 2007-07-25
> **el mariachi said:**
>  but how do I access all those other functions now? Stuff like themes and system monitor.

Just make an entry in your openbox menu for it. "gnome-theme-manager" will allow you to change themes and icons (also add gnome-settings-daemon to your autostart file, and your gtk apps will use the gtk themes configured in gnome). Or you can edit the .gtk2.0.rc and .gtk2.0.mine files (more info on this in this thread and the howto I linked to earlier). The basic admin tasks in gnome can also be included in your menu. If you use menumaker (see howto), you'll have all these already in your menu, but you will very likely want to delete a lot of other entries that it generates.

For the system monitor, just add gnome-system-monitor to your menu. I've also edited the rc.xml file so that whenever I press ctrl + alt + delete, the gnome system monitor starts.

> EDIT: Like, for instance, HOW DO I TAKE A SCREENSHOT NOW? lol Print Screen Doesn't work anymore

There are different ways of doing this. You can add a keyboard shortcut to your rc.xml file (in /home/USERNAME/.config/openbox/) to lauch gnome-screenshot or scrot (see man scrot for the exact command you want). Just bind it to the print screen key, reconfigure Openbox (desktop menu > Openbox > reconfigure) and you'll be able to use it. Alternatively, you can use the Gimp to take a screenshot (Acquire > Screenshot)

I'm a bit confused about some things you said, though. Are you trying Openbox on its own, or are you using Openbox within Gnome? The "kill nautilus session" should not be necessary for the former. Just log out, and then when you are at the GDM click Options (or F10) > Sessions > Openbox and click change session. You will then log into Openbox, and Nautilus won't load, unless you added it to your autostart file. (You can also select Openbox/Gnome in Gdm if you have installed Ob 3.4).

Even if you load just pure Openbox, you can still use a lot of gnome stuff (panels, admin tasks, etc.) Just add them to your autostart file or add entries for them in your desktop menu.

---

### Post by urukrama on 2007-07-25
> **dbbolton said:**
> if you can't figure it out, browse to /usr/bin/ and look at the executables whose names start with gnome- . you'll probably find what you're looking for.

also, the deskbar in gnome is helpful to figure out the command for certain gnome apps.

If you have Xfce installed, xfce4- appfinder is a great tool. I've used it a lot to set up my menus.

---

### Post by el mariachi on 2007-07-25
I'm using OpenBox within Gnome. I just mistakenly killed nautilus but now everything is configured right.

Thanks for the help so far;)

---

### Post by urukrama on 2007-07-25
You can use Openbox as a window manager in Gnome without killing Nautilus, but if you want to have the right click desktop menu, you will have to disable Nautilus from drawing the desktop. You can still use Nautilus, though, but use the following command:

> nautilus --no-desktop  --browser

Also, if you use the Gnome/Openbox session in Gdm, Openbox will load automatically withing gnome, and you'll have an entry in your preferences menu for obconf. Pretty neat.

---

### Post by DonnieP on 2007-07-25
> **urukrama said:**
> I did compile Openbox and have those packages installed, but when I try to compile, I get this error message:

```
checking for libX11... yes
checking for ObRender... no
Cannot find libObRender, aborting.

```

Not that it really matters though. I'm not that interested in it, and probably won't use it.

urukrama:  I got the exact same message at first.  After some detours I found that running this identifies what's actually missing (one at a time - fix one then run it again and it tells you another one).

```
pkg-config --print-errors --exists obrender-3.0

```

---

### Post by urukrama on 2007-07-25
Thank you DonnieP. I'll try it out.

---

### Post by dbbolton on 2007-07-25
i got the "recent documents" pipemenus to work. but for some reason, it only shows the image files that i've opened recently, like pngs and jpgs. no text files, documents, videos, etc. i tried both the sh and ruby versions, but they both do the same thing.

is this how they were intended, or an error?

---

### Post by bonzodog on 2007-07-25
Just so people know, there are prebuilt Feisty packages of openbox 3.4.3 on the Openbox Website along with obconf 2.0.2.

[http://icculus.org/openbox/index.php/Openbox:Download](http://icculus.org/openbox/index.php/Openbox:Download)

I am going to build Nitrogen 1.0 for my Zen box, as I am still running the old one.

---

### Post by fuscia on 2007-07-25
> **el mariachi]ObMenu isn't configuring my menu right... sometimes it does change it sometimes it doesn't...[/QUOTE]

do you have *menu.xml* in your /home/username/.config/openbox/ folder?

[QUOTE=el mariachi said:**
> 
Now I discover that I'm too "addicted" to the Gnome Main Menu (Apps, Places, System). the places menu is irrelevant, because a simple thunar launcher does the trick. but how do I access all those other functions now? Stuff like themes and system monitor.

*gnome-control-center* brings up the attached (see picture) and you can even put it in your right-click menu...

---

### Post by BOBSONATOR on 2007-07-25
When you use gnome-theme-manager or the gnome-font-manager, or even when you use totem, you make the enviornment turn into gnome, so you have to use ways to get around it.

Here are some of my ways.

Instead of gnome-theme-manager & font manager, use [gtk-chtheme]("http://plasmasturm.org/code/gtk-chtheme/")

and to change the icons, add this line to your ~/.gtkrc-2.0 and add this line

gtk-icon-theme-name="Tango" or any other theme you have

---

### Post by bonzodog on 2007-07-25
> **BOBSONATOR said:**
> When you use gnome-theme-manager or the gnome-font-manager, or even when you use totem, you make the enviornment turn into gnome, so you have to use ways to get around it.

Here are some of my ways.

Instead of gnome-theme-manager & font manager, use [gtk-chtheme]("http://plasmasturm.org/code/gtk-chtheme/")

and to change the icons, add this line to your ~/.gtkrc-2.0 and add this line

gtk-icon-theme-name="Tango" or any other theme you have

A minor thing to that;

Put the icon theme name in a file called ~/.gtkrc.mine.

You see, when you change the gtk theme, it rewrites the .gtkrc-2.0 file, but it always leaves in the line 'include .gtkrc.mine'. So, if you create that file with the icon theme name in it, it will always be referred to.

---

### Post by dbbolton on 2007-07-25
> **bonzodog said:**
> A minor thing to that;

Put the icon theme name in a file called ~/.gtkrc.mine.

You see, when you change the gtk theme, it rewrites the .gtkrc-2.0 file, but it always leaves in the line 'include .gtkrc.mine'. So, if you create that file with the icon theme name in it, it will always be referred to.
how can you specify your system font?

---

### Post by ynnhoj on 2007-07-25
> **dbbolton said:**
> how can you specify your system font?
this would go in yer .gtkrc.mine -
```
style "user-font"
{
font_name = "[font-name] [size]"
}
widget_class "*" style "user-font"
gtk-font-name = "[font-name] [size]"
```
just fill in the font name and size in the quotes.

---

### Post by moore.bryan on 2007-07-25
> **el mariachi said:**
> The strong point of OpenBox, besides being minimalistic, is it's (light)weight, right? So, to make things even more light and fast, what apps did you replace from the original gnome? Stuff like file managers, image viewers, etc-
> **urukrama said:**
> Mousepad/Leafpad for a simple text editor. Feh as image viewer (and to set the desktop image).
*both of these are awesome!* 
> **fuscia said:**
> feh is a good image viewer and background setter. gqview is pretty light and is also a good image viewer. i use thunar for a file manager, but there are a bunch of others, like pcman, emilfm, etc.
*one of those "others" is xfe... dual-pane, fast as lightning...*
> **fuscia said:**
> i use epiphany for a browser, but i've also used dillo and links2 (in graphical mode). if you want an email client, sylpheed-claws-gtk2 is great and will pick up your gtk theme (i just use gmail). audacious for music.
*epiphany lacks snap for me... i chose swiftweasel and it was nice.  ;-)  go with both sylpheed (claws-mail) and audacious (the successor to xmms).*
> **el mariachi said:**
> OB is running fine in my computer now. and it's stuff like themes and system monitor.
*you might want to look at conky...  oh, and i throw-in pypanel.  :-)*

---

### Post by SithVsJedi on 2007-07-25
what patch do i need to install oblivion?

---

### Post by fuscia on 2007-07-25
> **moore.bryan said:**
> *one of those "others" is xfe... dual-pane, fast as lightning...*]

xfe, that's the one i was trying to think of. when i want ugly, that's the one i use. you know, for things like flwm, or qvwm.

---

### Post by moore.bryan on 2007-07-25
> **fuscia said:**
> xfe, that's the one i was trying to think of. when i want ugly, that's the one i use. you know, for things like flwm, or qvwm.
[I]who you callin' ugly?
;-)
[/I]

---

### Post by fuscia on 2007-07-25
> **moore.bryan said:**
> [I]who you callin' ugly?
;-)
[/I]

i meant good ugly, not bad ugly.

---

### Post by Freddy on 2007-07-26
> **bonzodog said:**
> A minor thing to that;

Put the icon theme name in a file called ~/.gtkrc.mine.

You see, when you change the gtk theme, it rewrites the .gtkrc-2.0 file, but it always leaves in the line 'include .gtkrc.mine'. So, if you create that file with the icon theme name in it, it will always be referred to.
You have to write that inside ~/.gtkrc-2.0.mine not ~/.gtkrc.mine.

---

### Post by ynnhoj on 2007-07-26
> **Freddy said:**
> You have to write that inside ~/.gtkrc-2.0.mine not ~/.gtkrc.mine.
i suppose that depends one how your ~/.gtkrc-2.0 file has been generated.  on my (arch) system, it's .gtkrc.mine.  all you need to do is look at the contents of .gtkrc-2.0 to be sure..

---

### Post by kerry_s on 2007-07-26
.gtkrc.mine/.gtkrc is for gtk1.2 applications, totally different thing from .gtkrc-2.0.mine/.gtkrc-2.0 which covers gtk2 applications

---

### Post by bonzodog on 2007-07-26
> **kerry_s said:**
> .gtkrc.mine/.gtkrc is for gtk1.2 applications, totally different thing from .gtkrc-2.0.mine/.gtkrc-2.0 which covers gtk2 applications

Yes, but the gtk-chtheme application parses the gtkrc-2.0 file to include '.gtkrc.mine', not gtkrc2.0.mine. The *.mine file is *only* read by the gtkrc2.0 file.

Also, to answer an earlier query from dbbolton, the font is set by gtk-chtheme, and then parsed to .gtkrc-2.0. Thats the UI font, anyway. 
To set the Openbox font, you **now** use obconf, as the font settings in the theme files have become invalid, and no longer need to written in to new theme files.

---

### Post by shinynew on 2007-07-26
I am going to post a screen shot and all my conky config files, because I just got it how i want it.
[http://www.imagemirror.com/showpic.php?pic=screenshot.png]("screenshot")
 (this image host is great)
I am useing xfce4terminal with transparcy, Always on bottom, no borders, on all desktops, and zsh
Conky set up
```
background yes
use_xft yes
xftfont HandelGotD:size=8
xftalpha 0.1
update_interval 0.75
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 5
maximum_width 300 100
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

cpu_avg_samples 2
net_avg_samples 2

out_to_console no

use_xft yes

xftfont Bitstream Vera Sans Mono:size=9

xftalpha 0.8

mail_spool $MAIL

update_interval 1.0

stippled_borders 0

border_margin 4

border_width 1

default_color white
default_shade_color white
default_outline_color white


alignment top_left
gap_x 10
gap_y 10


use_spacer no

no_buffers no

uppercase no

TEXT
$sysname $kernel    ${time %A,%d %B}
$stippled_hr
${color lightgrey}Time:$color ${time %k:%M:%S}
${color lightgrey}Uptime:$color $uptime ${color lightgrey}- Load:$color $loadavg
${color lightgrey}CPU1 Usage:${color} ${cpu cpu1}% ${cpubar cpu1}
${color #4F6B93}${cpugraph 25 8098ff ffc7ea}
${color lightgrey}RAM Usage:$color $mem/$memmax - $memperc%
${color lightgrey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar}
${color lightgrey}Processes:$color $processes  ${color grey}Running:$color $running_processes
$color$stippled_hr
${color lightgrey}Networking:
${offset 10}Down:${color #a9c7ea} ${downspeed eth0} k/s${color lightgrey} ${alignr}Up:${color #a9c7ea} ${upspeed eth0} k/s
${offset 10}${color #4F6B93}${downspeedgraph eth0 25,100 8098ff ffc7ea} ${alignr}${color #4F6B93}${upspeedgraph eth0 25,100 8098ff ffc7ea}
${offset 10}${color lightgrey}Total: ${color #a9c7ea}${totaldown eth0} ${alignr}${color lightgrey}Total: ${color #a9c7ea}${totalup eth0}
$color$stippled_hr
${color lightgrey}File systems:$alignr
/      $color${fs_used_perc /}%/${fs_size /}
$color$stippled_hr
  ${color}Name            PID     CPU%   MEM%
${color #ddaa00} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
  ${color}Mem usage
${color #ddaa00} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color lightgrey} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color lightgrey} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
${color lightgrey} ${top_mem name 4} ${top_mem pid 4} ${top_mem cpu 4} ${top_mem mem 4}
$color$stippled_hr
${color lightgrey}Port(s)${offset 48}Connections:
${color lightgrey} ALL: ${alignc}${tcp_portmon 1 65535 count}
$color$stippled_hr
${color lightgray}Email: ${color D7D3C5}${execi 600 python ~/.gmail/gmail.py}
$color$stippled_hr
${execi 300 ~/.config/tweakorss.sh}
```
Conky is also being used as my screensaver (sorry no screenshot)
```
background no
#use_xft yes
#xftfont HandelGotD:size=8
#xftalpha 0.1
update_interval 0.5
total_run_times 0
#own_window yes
#own_window_type normal
#own_window_transparent yes
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 1000 700
maximum_width 1200
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes

cpu_avg_samples 2
net_avg_samples 2

out_to_console no

#use_xft yes

#xftfont Bitstream Vera Sans Mono:size=12

#xftalpha 0.8

#mail_spool $MAIL

update_interval 1.0

stippled_borders 0

border_margin 4

border_width 1

default_color white
default_shade_color white
default_outline_color white


alignment top_left
gap_x 10
gap_y 10


use_spacer no

no_buffers no

uppercase no

TEXT
$sysname $kernel    ${time %A,%d %B}
$stippled_hr
${color lightgrey}Time:$color ${time %k:%M:%S}
${color lightgrey}Uptime:$color $uptime ${color lightgrey}- Load:$color $loadavg
${color lightgrey}CPU1 Usage:${color} ${cpu cpu1}% ${cpubar cpu1}
${color #4F6B93}${cpugraph 25 8098ff ffc7ea}
${color lightgrey}RAM Usage:$color $mem/$memmax - $memperc%
${color lightgrey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar}
${color lightgrey}Processes:$color $processes  ${color grey}Running:$color $running_processes
$color$stippled_hr
${color lightgrey}Networking:
${offset 10}Down:${color #a9c7ea} ${downspeed eth0} k/s${color lightgrey} ${alignr}Up:${color #a9c7ea} ${upspeed eth0} k/s
${offset 10}${color #4F6B93}${downspeedgraph eth0 25,420 8098ff ffc7ea} ${alignr}${color #4F6B93}${upspeedgraph eth0 25,420 8098ff ffc7ea}
${offset 10}${color lightgrey}Total: ${color #a9c7ea}${totaldown eth0} ${alignr}${color lightgrey}Total: ${color #a9c7ea}${totalup eth0}
$color$stippled_hr
${color lightgrey}File systems:$alignr
/      $color${fs_used_perc /}%/${fs_size /}                            ${alignr}${color}Mem usage
$color$stippled_hr
  ${color}Name            PID     CPU%   MEM%                           ${alignr}${color}  Name             PID     CPU%   MEM% .
${color #ddaa00} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}   ${alignr}${color #ddaa00} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2} ${alignr}${color lightgrey} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3} ${alignr}${color lightgrey} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4} ${alignr}${color lightgrey} ${top_mem name 4} ${top_mem pid 4} ${top_mem cpu 4} ${top_mem mem 4}
${color lightgrey} ${top name 5} ${top pid 5} ${top cpu 5} ${top mem 5} ${alignr}${color lightgrey} ${top_mem name 5} ${top_mem pid 5} ${top_mem cpu 5} ${top_mem mem 5}
  $color$stippled_hr
${color lightgrey}Port(s)${offset 48}Connections:
${color lightgrey} Torrentflux:              ${tcp_portmon 49160 49300 count}
${color lightgrey} ALL:                      ${tcp_portmon 1 65535 count}
${color #ddaa00}Outbound Connection ${alignr} Remote Service/Port$color              
 ${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}  
 ${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}  
 ${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}  
 ${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice 3}  
 ${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 rservice 4}  
 ${tcp_portmon 32768 61000 rhost 5} ${alignr} ${tcp_portmon 32768 61000 rservice 5}  
${color #ddaa00}Inbound Connection ${alignr} Local Service/Port$color
 ${tcp_portmon 1 32767 rhost 0} ${alignr} ${tcp_portmon 1 32767 lservice 0}
 ${tcp_portmon 1 32767 rhost 1} ${alignr} ${tcp_portmon 1 32767 lservice 1}
 ${tcp_portmon 1 32767 rhost 2} ${alignr} ${tcp_portmon 1 32767 lservice 2}
 ${tcp_portmon 1 32767 rhost 3} ${alignr} ${tcp_portmon 1 32767 lservice 3}
 ${tcp_portmon 1 32767 rhost 4} ${alignr} ${tcp_portmon 1 32767 lservice 4}
 ${tcp_portmon 1 32767 rhost 5} ${alignr} ${tcp_portmon 1 32767 lservice 5}
$color$stippled_hr
${color lightgray}Email: ${color D7D3C5}${execi 600 python ~/.gmail/gmail.py}
$color$stippled_hr
${execi 600 curl -s http://digg.com/rss/index.xml | grep title | sed 's/<\/title>/ /' | sed 's/<title>/ /' | sed 10q}

```
I highly recommend useing this one liner for RSS in conky```

${execi 600 curl -s http://digg.com/rss/index.xml | grep title | sed 's/<\/title>/ /' | sed 's/<title>/ /' | sed 10q}
```

the URL should be pretty self explanintory, and the very last line sed 10q is how many lines to show (you can use 9q, 11q however many you want.)



I am also useing Docker, tilda, synergy, and torrentflux.

EDIT: sorry this kind of turned out to be pretty conky centric, but There should really be more people posting their desktops and what apps they run.

---

### Post by RedSquirrel on 2007-07-26
There are lots of threads with people posting what they run. Just do a search. ;)

Here are two:

[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)
[http://ubuntuforums.org/showthread.php?t=489082](http://ubuntuforums.org/showthread.php?t=489082)

---

### Post by dbbolton on 2007-07-26
i'm having a bit of trouble with my fonts in openbox (on two different computers). this is without a start-up script. when i start an openbox-session, the menu looks like this:

[IMG]http://i103.photobucket.com/albums/m128/envyouraudience/beforeob.png[/IMG]

when i restart it from the menu, it looks like this:

[IMG]http://i103.photobucket.com/albums/m128/envyouraudience/afterob.png[/IMG]

which is how it should look. why are the fonts smaller than they should be at startup?

---

### Post by Rutabega on 2007-07-26
dbbolton- I've had the same problem. I don't know the cause as I'm a Openbox newb. So I lazily just increased the font size in obconf-appearances. That solved the problem of the font size problem.

---

### Post by darkfox on 2007-07-27
Bryan,
I believe that (in Feisty at least) 'shutdown' is located in /sbin and not in /usr/bin.  So the line in sudoers should read in order to work:

```
ALL     ALL=NOPASSWD:/sbin/shutdown
```

---

### Post by ceelo on 2007-07-27
> **dbbolton said:**
> i'm having a bit of trouble with my fonts in openbox (on two different computers). this is without a start-up script. when i start an openbox-session, the menu looks like this:


when i restart it from the menu, it looks like this:


which is how it should look. why are the fonts smaller than they should be at startup?

The gnome-settings-daemon process has been known to sneak it's way into my Openbox sessions and it tends to change font sizes for me if I've set them differently in GNOME. Check your processes to see if it's running in each instance.

---

### Post by moore.bryan on 2007-07-27
> **darkfox said:**
> Bryan,
I believe that (in Feisty at least) 'shutdown' is located in /sbin and not in /usr/bin.  So the line in sudoers should read in order to work:

```
ALL     ALL=NOPASSWD:/sbin/shutdown
```
*very true... turns out i had made a symlink in /usr/bin and forgot about it.  ;-)*

---

### Post by dbbolton on 2007-07-27
> **ceelo said:**
> The gnome-settings-daemon process has been known to sneak it's way into my Openbox sessions and it tends to change font sizes for me if I've set them differently in GNOME. Check your processes to see if it's running in each instance.
apparently, when i log into a plain openbox session (no startup script whatsoever), gnome-settings-daemon is still running. what invokes it?

---

### Post by bonzodog on 2007-07-27
It's gnome and gdm. If you have logged into gnome beforehand, then gnome-settings-daemon will not exit with logout.

You need to kill gnome-settings-daemon on the CLI.

I have just rebuilt this box using Zenwalk-core, which is a base install of 200MB, with no X or anything.

I then added things a package at a time, and now have a box that logs in using SLiM, and then only has openbox on it.

---

### Post by dbbolton on 2007-07-28
> **bonzodog said:**
> It's gnome and gdm. If you have logged into gnome beforehand, then gnome-settings-daemon will not exit with logout.

You need to kill gnome-settings-daemon on the CLI.

I have just rebuilt this box using Zenwalk-core, which is a base install of 200MB, with no X or anything.

I then added things a package at a time, and now have a box that logs in using SLiM, and then only has openbox on it.
could it also be caused by other users who remain logged in? on my desktop, which i share with my brother, he always leaves himself logged in (regular gnome session). i'm beginning to wonder about this because he uses ktorrent, and whenever i log into a plain OB session, several kde-related processes crop up (like kded, kdeinit, klauncher). the system monitor indicates my username with these processes as well, even though i didn't open ktorrent.

---

### Post by bonzodog on 2007-07-28
So, if I understand you, your brother initially logs in from gdm, then you use 'switch user' to log in yourself?

if so, this is what's causing the gnome-settings-daemon and the kde stuff to run in the background.

---

### Post by Sammm_ on 2007-07-28
I havent read through this thread fully so the answer might be in here but...

Is it possible to make tint flash when something happens, IE when I get a message on pidgin? It's a feature I would really like to have.

---

### Post by dbbolton on 2007-07-28
> **Sammm_ said:**
> I havent read through this thread fully so the answer might be in here but...

Is it possible to make tint flash when something happens, IE when I get a message on pidgin? It's a feature I would really like to have.
tint doesn't have that feature afaik, but visibility does.

---

### Post by Sammm_ on 2007-07-28
> **dbbolton said:**
> tint doesn't have that feature afaik, but visibility does.

Ah ok, I'll give visibility a go then.

---

### Post by Ralgunagar on 2007-07-28
hey guys! whats up?

---

### Post by Sammm_ on 2007-07-28
A few questions...

How can I make openbox use my XFCE Programs menu? I installed Obmenu to see what help it offered but when I try to run it I get this error..

```
sam@foxhound:~$ obmenu
Traceback (most recent call last):
  File "/usr/bin/obmenu", line 582, in <module>
    app.init()
  File "/usr/bin/obmenu", line 489, in init
    self.menu.loadMenu(self.menu_path)
  File "/usr/lib/python2.5/site-packages/obxml.py", line 153, in loadMenu
    self.dom = xml.dom.minidom.parseString(fil.read())
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/minidom.py", line 1925, in parseString
    return expatbuilder.parseString(string)
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/expatbuilder.py", line 942, in parseString
    return builder.parseString(string)
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/expatbuilder.py", line 223, in parseString
    parser.Parse(string, True)
xml.parsers.expat.ExpatError: no element found: line 1, column 0

```

No doubt a problem with me compiling it, any ideas how to fix it?

[I]Secondly as per the instructions at [http://icculus.org/openbox/index.php/Help:Autostart](http://icculus.org/openbox/index.php/Help:Autostart) i created an autostart.sh in .config/openbox/. It contains this information...

```
# Run the system-wide support stuff
. $GLOBALAUTOSTART

# Programs to launch at startup
hsetroot ~/Images/mandolux-aleaf-1024.jpg &

# Programs that will run after Openbox has started
(sleep 2 && tint && conky -d) &
```

This dosent seem to run on startup - no evidence of tint or conky.[/I]
**Edit:** Solved this by installing the .deb from the openbox site. However I've broken obconf...
```
obconf: error while loading shared libraries: libobrender.so.0: cannot open shared object file: No such file or directory
```


And finally... how do I set a GTK theme in openbox?

---

### Post by dbbolton on 2007-07-28
> **Sammm_ said:**
> A few questions...

How can I make openbox use my XFCE Programs menu? I installed Obmenu to see what help it offered but when I try to run it I get this error..

```
sam@foxhound:~$ obmenu
Traceback (most recent call last):
  File "/usr/bin/obmenu", line 582, in <module>
    app.init()
  File "/usr/bin/obmenu", line 489, in init
    self.menu.loadMenu(self.menu_path)
  File "/usr/lib/python2.5/site-packages/obxml.py", line 153, in loadMenu
    self.dom = xml.dom.minidom.parseString(fil.read())
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/minidom.py", line 1925, in parseString
    return expatbuilder.parseString(string)
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/expatbuilder.py", line 942, in parseString
    return builder.parseString(string)
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/expatbuilder.py", line 223, in parseString
    parser.Parse(string, True)
xml.parsers.expat.ExpatError: no element found: line 1, column 0

```

No doubt a problem with me compiling it, any ideas how to fix it?

[I]Secondly as per the instructions at [http://icculus.org/openbox/index.php/Help:Autostart](http://icculus.org/openbox/index.php/Help:Autostart) i created an autostart.sh in .config/openbox/. It contains this information...

```
# Run the system-wide support stuff
. $GLOBALAUTOSTART

# Programs to launch at startup
hsetroot ~/Images/mandolux-aleaf-1024.jpg &

# Programs that will run after Openbox has started
(sleep 2 && tint && conky -d) &
```

This dosent seem to run on startup - no evidence of tint or conky.[/I]
**Edit:** Solved this by installing the .deb from the openbox site. However I've broken obconf...
```
obconf: error while loading shared libraries: libobrender.so.0: cannot open shared object file: No such file or directory
```


And finally... how do I set a GTK theme in openbox?
i had a very similar problem:

> when i try to launch obconf, i get this:
```
obconf: error while loading shared libraries: libobrender.so.0: cannot open shared object file: No such file or directory
```any ideas?

=============
edit: i was able to get obconf to run by doing this:
```

sudo ln -s libobrender.so libobrender.so.0
sudo ln -s libobparser.so libobparser.so.0
```but now it just crashes as soon as the window appears.

i fixed it by purging obconf and openbox, then installing the latest debs.

---

### Post by Sammm_ on 2007-07-28
Well, I got Obconf to work by installing the newest deb & i managed to set my Gtk themes using switch 2, however, I still have the small matter of Obmenu to work out...

---

### Post by ynnhoj on 2007-07-28
do you have a ~/.config/openbox/menu.xml file?  if not, it could be failing because it's trying to read a file that doesn't exist.  the sample is found in /etc/xdg/openbox/menu.xml -- you'd just have to copy it to ~/.config/openbox.  but something tells me that this might not be the problem..

---

### Post by bonzodog on 2007-07-29
sammm:

first off, is it setting the wallpaper on launch?

If so, then it IS reading the autostart.sh file.

Those commands for tint and conky are not supposed to be in brackets.

Personally, I use Nitrogen to set wallpaper; check the Ubuntu repos for this, but if you cannot see it in there, go to: [http://l3ib.org/nitrogen/](http://l3ib.org/nitrogen/)
It's a graphical app that will let you choose wallpaper on the fly.

Also, make sure you are using the 3.4.3 .deb for openbox off the openbox site, along with the 2.0.2 obconf from there. The feisty repo version is outdated, and broken.

As for obmenu: it looks like a missing python lib, or you are possibly missing expat.

Check you have the xml.python libraries installed.

---

### Post by Sammm_ on 2007-07-29
> **bonzodog said:**
> sammm:

first off, is it setting the wallpaper on launch?

If so, then it IS reading the autostart.sh file.

Those commands for tint and conky are not supposed to be in brackets.

Personally, I use Nitrogen to set wallpaper; check the Ubuntu repos for this, but if you cannot see it in there, go to: [http://l3ib.org/nitrogen/](http://l3ib.org/nitrogen/)
It's a graphical app that will let you choose wallpaper on the fly.

Also, make sure you are using the 3.4.3 .deb for openbox off the openbox site, along with the 2.0.2 obconf from there. The feisty repo version is outdated, and broken.

As for obmenu: it looks like a missing python lib, or you are possibly missing expat.

Check you have the xml.python libraries installed.

It wasn't setting the wallpaper on launch however... I installed feh and edited the autostart.sh file so it looks like this...
```
# Run the system-wide support stuff
. $GLOBALAUTOSTART

# Programs to launch at startup
feh --bg-scale ~/Images/mandolux-aleaf-1024.jpg &
tint &
```

That launches fine now.

Installed the pythonlibs and Obmenu works fine, however after creating a menu with this code in it...

```
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 0.8//EN'
  'http://www.freedesktop.org/standards/menu-spec/menu-0.8.dtd'>
<!-- Automatically generated do not edit -->
<Menu>
	<menu id="None-65465" label="Accessories">
		<item label="Terminal">
			<action name="Execute">
				<execute>
					xfce4-terminal
				</execute>
			</action>
		</item>
		<item label="Thunar">
			<action name="Execute">
				<execute>
					thunar
				</execute>
			</action>
		</item>
		<item label="Mousepad">
			<action name="Execute">
				<execute>
					mousepad
				</execute>
			</action>
		</item>
	</menu>
	<menu id="None-24941" label="Multimedia">
		<item label="Gxine">
			<action name="Execute">
				<execute>
					gxine
				</execute>
			</action>
		</item>
		<item label="Exaile">
			<action name="Execute">
				<execute>
					exaile
				</execute>
			</action>
		</item>
	</menu>
	<menu id="None-535054" label="Network">
		<item label="Firefox">
			<action name="Execute">
				<execute>
					firefox
				</execute>
			</action>
		</item>
		<item label="Pidgin">
			<action name="Execute">
				<execute>
					pidgin
				</execute>
			</action>
		</item>
		<item label="Mutt">
			<action name="Execute">
				<execute>
					mutt
				</execute>
			</action>
		</item>
		<item label="Deluge">
			<action name="Execute">
				<execute>
					deluge
				</execute>
			</action>
		</item>
	</menu>
	<menu id="None-124848" label="Graphics">
		<item label="GQview">
			<action name="Execute">
				<execute>
					gqview
				</execute>
			</action>
		</item>
		<item label="Gimp">
			<action name="Execute">
				<execute>
					gimp
				</execute>
			</action>
		</item>
   </menu>
</Menu>	

```

It does not load as the openbox menu when I right click.

---

### Post by bonzodog on 2007-07-29
is it in ~/.config/openbox/menu.xml?

---

### Post by Sammm_ on 2007-07-29
> **bonzodog said:**
> is it in ~/.config/openbox/menu.xml?

It is indeed.

**Edit:** Another quick question, how would I go about changing my icon theme in openbox?
**Edit 2:** When I return from my holiday I'm going to re-install Xubuntu and my first task will be setting up openbox properly, hopefully menus and the like will work from a fresh install.

---

### Post by dbbolton on 2007-07-29
> **Sammm_ said:**
> It is indeed.

**Edit:** Another quick question, how would I go about changing my icon theme in openbox?
**Edit 2:** When I return from my holiday I'm going to re-install Xubuntu and my first task will be setting up openbox properly, hopefully menus and the like will work from a fresh install.
it seems that the most popular way to change your icon theme is to make a file called .gtkrc.mine in your home folder which contains a line such as:
```
 gtk-icon-theme-name="Tango"
```

if you want to run gnome-settings-daemon in the background, you can use gnome-theme-manager to change your icon theme.

---

### Post by urukrama on 2007-07-31
> **Sammm_ said:**
> It does not load as the openbox menu when I right click.

Make sure you reconfigure Openbox first (there is normally an entry in the right click desktop menu for this, otherwise you can add one with Obmenu).

---

### Post by el mariachi on 2007-07-31
I reckon some people have enabled real transparency in openbox. How can I try this? (it's not a misunderstanding, is it?)

---

### Post by dbbolton on 2007-07-31
> **el mariachi said:**
> I reckon some people have enabled real transparency in openbox. How can I try this? (it's not a misunderstanding, is it?)
check this out: [http://icculus.org/openbox/index.php/Help:FAQ#How_do_I_get_true_32-bit_transparent_windows.3F](http://icculus.org/openbox/index.php/Help:FAQ#How_do_I_get_true_32-bit_transparent_windows.3F)

---

### Post by urukrama on 2007-07-31
You can use xcompmgr and transset to do so. See [here]("http://ubuntuforums.org/showthread.php?t=75527").

---

### Post by fuscia on 2007-07-31
once again, i've grown tired of the novelty of whichever other wm i've been using (or, was it a DE...?). back to the dull routine of my computer actually doing what i tell it to do...oh hum...

---

### Post by dbbolton on 2007-08-01
what would be the proper order for a startup script with these items:

feh --bg-center 
tint
conky
docker
gnome-settings-daemon
exec openbox-session

?

---

### Post by el mariachi on 2007-08-01
how do you make the commands in the Obmenu run as sudo? I wrote (for eg) sudo thunar and it doesn't do anything (sudo synaptic too)

edit: gksu did the trick ;)

---

### Post by urukrama on 2007-08-01
I don't know, but this is what my autostart.sh file looks like:
> 
# OpenOffice gtk theme
export OOO_FORCE_DESKTOP=gnome
# Auto-mounting drives 
gnome-volume-manager & 
# feh stores the last background in .fehbg 
eval `cat $HOME/.fehbg` &
docker &
bbtime &
openbox
fi

If I use conky, I place it after docker and bbtime. What is 'openbox-session'? I've never used it.

---

### Post by urukrama on 2007-08-01
> **el mariachi said:**
> how do you make the commands in the Obmenu run as sudo? I wrote (for eg) sudo thunar and it doesn't do anything (sudo synaptic too)

Try gksudo instead of sudo.

---

### Post by dbbolton on 2007-08-01
> **urukrama said:**
> I don't know, but this is what my autostart.sh file looks like:


If I use conky, I place it after docker and bbtime. What is 'openbox-session'? I've never used it.
'/usr/bin/openbox-session' what what was mentioned in the file '/usr/share/xsessions/openbox.desktop' by default, so i just used that. here's what it looks like

```
#!/bin/sh

if test -n "$1"; then
    echo "Syntax: openbox-session"
    echo
    echo "See the openbox-session(1) manpage for help."
  exit
fi

AUTOSTART="$HOME/.config/openbox/autostart.sh"
GLOBALAUTOSTART="/etc/xdg/openbox/autostart.sh"

if test -e $AUTOSTART; then
    . $AUTOSTART
else
    if test -e $GLOBALAUTOSTART; then
        . $GLOBALAUTOSTART
    fi
fi

exec /usr/bin/openbox "$@"

```


what does 'fi' do at the end of your autostart file?

---

### Post by urukrama on 2007-08-01
Is the startup script to be used when you login through GDM (or similar), selecting 'openbox' in the sessions menu? Or is it to autologin when you start your computer?

If the former, you don't need 'openbox-session', do you? You select that in GDM, and when Openbox starts it automatically uses the autostart.sh file in ~/.config/openbox

---

### Post by el mariachi on 2007-08-01
thanks!

I have asked this in a lot of places but no one could give me a good answer and google hasn't been my friend too (or maybe I don't know how to be his friend). anyways, I want my terminal to be more colorful and change the first line to just [mariachi]$ instead of mariachi@central-dogma:~$

like this one
[http://offload2.icculus.org/openbox/mw/images/5/5d/Borosaiob_2007-06-06.png](http://offload2.icculus.org/openbox/mw/images/5/5d/Borosaiob_2007-06-06.png)

---

### Post by ynnhoj on 2007-08-01
terminal colours, among all sorts of other things, can be defined in your ~/.Xdefaults file (make sure that's a capital X).  google "Xdefaults" you'll find several examples.

and to change your prompt, you need to edit your PS1 variable.  look in your ~/.bashrc file -- there's probably already a line in there that says "PS1 = .......", so you'd just want to change that line.  i think that this:
```
PS1 = '[\u]$ '
```
woud do the trick.

---

### Post by el mariachi on 2007-08-04
Some questions came up:
-Do you guys use the openbox session or openbox-gnome?
I'm using just openbox and it seems even faster -is there a drawback?
-I'm trying out xcompmgr and it gives conky a border. How do I make it borderless?

++Thanks:)

---

### Post by urukrama on 2007-08-04
> **el mariachi said:**
> -Do you guys use the openbox session or openbox-gnome?
I'm using just openbox and it seems even faster -is there a drawback?

I'm using the openbox session. The 'drawback' is that it doesn't load all the gnome stuff, which is actually a plus for me. You can always add the gnome things you like to your autostart file (I just added gnome-volume-manage, but you could also add gnome-settings-daemon (for themes, icons, and fonts), gnome-panel, etc.)

It all depends on the way you like to use your computer.

> -I'm trying out xcompmgr and it gives conky a border. How do I make it borderless?

I'm not sure how to go around that. I don't use xcompmgr that often, and if I do, I generally just turn conky off. But you could try and play with the 'background' and 'double_buffer' settings in your .conkyrc. Perhaps these could help. Otherwise, I wouldn't know. I have always been too lazy to try and find out. :)

Or you could use gkrellm instead of conky.

---

### Post by el mariachi on 2007-08-04
I haven't missed a single feature while using the 'openbox' session.. other than the ye' old slowness :D

gkrellm is U G L Y xD I just dumped xcompmgr I can live without drop shadows, although transparency is classic eye-candy

---

### Post by shearn89 on 2007-08-05
> **el mariachi said:**
> -I'm trying out xcompmgr and it gives conky a border. 

You can fix this by changing "own_window" to "no" - its probably still on "yes" if you've been using nautilus.

---

### Post by fuscia on 2007-08-07
any of you all figure out how to change the order of wallpapers in nitrogen?

---

### Post by dbbolton on 2007-08-07
this was in the readme

```
Usage:  nitrogen [OPTIONS] DIRECTORY

Options:
        --no-recurse
                Do not recurse into subdirectories
        --restore
                Restore saved backgrounds
        --sort=[arg]
                How to sort the backgrounds. Valid options are:
                        * alpha, for alphanumeric sort
                        * ralpha, for reverse alphanumeric sort
                        * time, for last modified time sort (oldest first)
                        * rtime, for reverse last modified time sort (newest first)
```

alpha is the only order i ever use.

---

### Post by fuscia on 2007-08-07
awesome! thanks, db. i'm loving nitrogen.

---

### Post by shearn89 on 2007-08-09
Whenever i try and compile nitrogen, i get an error saying i need to install "glib2", but i can't seem to find it anywhere... help?

---

### Post by fuscia on 2007-08-09
> **shearn89 said:**
> Whenever i try and compile nitrogen, i get an error saying i need to install "glib2", but i can't seem to find it anywhere... help?

i think it's "libglib2" on ubuntu.

---

### Post by shearn89 on 2007-08-09
Just tried that - apparently I already have the latest version installed. I'll post the exact error here, give me a mo..

EDIT: here we are:
```

...
checking pkg-config is at least version 0.9.0... yes
checking for GLIB2... configure: error: Package requirements (glib-2.0 >= 2.6.0) were not met:

No package 'glib-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLIB2_CFLAGS
and GLIB2_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

Then, "sudo apt-get install libglib2.0-0":
```
alex@alex-laptop:~$ sudo apt-get install libglib2.0-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libglib2.0-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by BoyOfDestiny on 2007-08-09
> **shearn89 said:**
> Just tried that - apparently I already have the latest version installed. I'll post the exact error here, give me a mo..

EDIT: here we are:
```

...
checking pkg-config is at least version 0.9.0... yes
checking for GLIB2... configure: error: Package requirements (glib-2.0 >= 2.6.0) were not met:

No package 'glib-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLIB2_CFLAGS
and GLIB2_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

Then, "sudo apt-get install libglib2.0-0":
```
alex@alex-laptop:~$ sudo apt-get install libglib2.0-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libglib2.0-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

sudo apt-get install libglib2.0-dev

Note: Never tried building this, but I'm betting that's what's missing. :)

---

### Post by ynnhoj on 2007-08-09
> **BoyOfDestiny said:**
> sudo apt-get install libglib2.0-dev

Note: Never tried building this, but I'm betting that's what's missing. :)
odds are pretty good that that's what is needed.
[http://packages.ubuntu.com/feisty/libdevel/libglib2.0-dev](http://packages.ubuntu.com/feisty/libdevel/libglib2.0-dev)

---

### Post by urukrama on 2007-08-10
I'm switching between gnome/openbox and xfce/openbox at the moment. I want to be able to smoothly hibernate, logout, shutdown and reboot using Openbox, with a confirmation dialog. I tried using the power buttons in gnome-panel and xfce-panel in pure Openbox, but they don't work outside of gnome and xfce ('quit' just quits the panel).

So far all is quite nice. A little slower, but still fast enough.

---

### Post by el mariachi on 2007-08-10
> **urukrama said:**
> I'm switching between gnome/openbox and xfce/openbox at the moment. I want to be able to smoothly hibernate, logout, shutdown and reboot using Openbox, with a confirmation dialog. I tried using the power buttons in gnome-panel and xfce-panel in pure Openbox, but they don't work outside of gnome and xfce ('quit' just quits the panel).

So far all is quite nice. A little slower, but still fast enough.

have you tried using commands in obmenu?

Restart (sudo reboot) works for me, shutdown doesn't.

I've seen an app that replaces the gnome manager for this stuff, don't remember the name now though.

---

### Post by urukrama on 2007-08-10
I know about that mariachi, but I want a confirmation box before logging out/shutdown/etc. and that you don't get with commands in the menu. Kshutdown works, but is too slow on this computer.

The app you are referring to might be gshutdown. We discussed it in this thread earlier.

---

### Post by el mariachi on 2007-08-10
I see... I tried to google it, because I also want an alternative to commands in the menu, but I don't even know what to search for...

---

### Post by fuscia on 2007-08-10
el mariachi, *gksudo shutdown now* works in obmenu. you'll even get the confirmation box.

---

### Post by urukrama on 2007-08-10
But why is it not possible to do this without sudo-ing? It is possible in gnome, kde, and xfce.

BTW we've passed the 500 posts mark in this thread.

---

### Post by moore.bryan on 2007-08-10
> **urukrama said:**
> But why is it not possible to do this without sudo-ing? It is possible in gnome, kde, and xfce.
*i know the usual work-around is to put a line in visudo specifying shutdown not needing a password...*
> BTW we've passed the 500 posts mark in this thread.
*GREAT thread in a GREAT forum!  :-)*

---

### Post by shearn89 on 2007-08-10
> **urukrama said:**
> BTW we've passed the 500 posts mark in this thread.

High-five! (my wife is dead...) \\:D/

---

### Post by urukrama on 2007-08-10
> **moore.bryan said:**
> i know the usual work-around is to put a line in visudo specifying shutdown not needing a password...

I know that workaround, but am too stubborn to use it :-) Anyway, I'm not really complaining, just wondering. And I'm having fun using XFCE and Gnome with Openbox.

---

### Post by moore.bryan on 2007-08-10
*gotcha... it does seem silly to sudo the shutdown command... has anyone tried changing the ownership and positions on it?  there's another [thread]("http://ubuntuforums.org/showthread.php?t=79508") which seems to say one can just change privileges and get it to work sans sudo...*

---

### Post by el mariachi on 2007-08-10
Not sure if this is OB related...
I opened OOWriter and stumbled upon a un-gtked app with an horrifying resemblance to Windows 98. It isn't using the system fonts too...
I'm on PURE openbox. This didn't happen in gnome. What's missing?

---

### Post by moore.bryan on 2007-08-10
> **el mariachi said:**
> Not sure if this is OB related...
I opened OOWriter and stumbled upon a un-gtked app with an horrifying resemblance to Windows 98. It isn't using the system fonts too...
I'm on PURE openbox. This didn't happen in gnome. What's missing?
*screenshot?  ;-)  i'm running pure openbox and i don't have this issue...*

---

### Post by urukrama on 2007-08-10
> **el mariachi said:**
> I opened OOWriter and stumbled upon a un-gtked app with an horrifying resemblance to Windows 98. It isn't using the system fonts too...
I'm on PURE openbox. This didn't happen in gnome. What's missing?

Add this to the beginning of your autostart.sh file: 

```
export OOO_FORCE_DESKTOP=gnome
```

and OpenOffice will look like other gtk themes.

---

### Post by dbbolton on 2007-08-10
when you add an "openbox menu" to perlpanel, where does it get the menu.xml file? it definitely isn't loading my ~/.config/openbox/menu.xml - it's totally different on perlpanel.

---

### Post by fuscia on 2007-08-10
> **dbbolton said:**
> when you add an "openbox menu" to perlpanel, where does it get the menu.xml file? it definitely isn't loading my ~/.config/openbox/menu.xml - it's totally different on perlpanel.

look here */usr/share/perlpanel/PerlPanel/Applet/OpenBoxMenu.pm* where it seems to be pointing at */etc/xdg/openbox/menu.xml*

---

### Post by dbbolton on 2007-08-10
> **fuscia said:**
> look here */usr/share/perlpanel/PerlPanel/Applet/OpenBoxMenu.pm* where it seems to be pointing at */etc/xdg/openbox/menu.xml*
ok, i got it working. thanks!

---

### Post by fuscia on 2007-08-10
cool.

---

### Post by el mariachi on 2007-08-11
How do i change the arrows in the OB menu?

---

### Post by fuscia on 2007-08-11
> **el mariachi said:**
> How do i change the arrows in the OB menu?

what arrows?

---

### Post by urukrama on 2007-08-11
Change the bullet.xpm in the folder of the theme you are using. Create one yourself, or use one you like from another theme.

---

### Post by el mariachi on 2007-08-11
oh. I thought they were something else. Thanks! :D

---

### Post by picpak on 2007-08-11
Does anyone here who uses trayer know how to get it to load on all workspaces? This has been killing me lately.

---

### Post by urukrama on 2007-08-11
Openbox 3.4.4 is out, btw. Here is the changelog:

> Updated Traditional Chinese translation 
Updated Norwegian translation 
Fix for MoveToEdge skipping edges sometimes 
Let you specify the vertical and horizontal padding independently in themes 
Fix so that if you select an omnipresent window on another desktop in the client list menus, it will go to that desktop 
Make the GrowToEdge action shrink once there is no more room to grow, similar to in 3.4.2, but shrinking to edges as well 
Move the Send To and Layers submenus to the top of the client menu 
Fix race causing omnipresent windows to lose focus when switching desktops very quickly 
Don't focus new windows on other desktops if they aren't related to the currently focused window 
Add corner resizing areas in the inner client border (Fixes themes such as Onyx) 
New focus stealing prevention that is smart and not intrusive and not annoying 
Revert a small change in 3.4.3 that caused windows to be placed funny in Smart placement when there was a dock or something on the side of the screen 
Show a notification when switching desktops 
Fix for delayed focus-follows-mouse interrupting move/resize or menus 
Make screen edge warp keep warping without having the move the mouse 1 pixel 
Fix for resizing terminals in the top/left sides getting a little confused 
Fix to keep oldschool (Non-EWMH) fullscreen windows from being moved and resized inside of the struts (Fixes Acroread) 
Accept the <command> option for the Restart command, similar to the Execute action 
Don't make clicking on dock apps sometimes act like clicking on the root window (Don't propogate button events up) 
Fix a bug introduced in 3.4.3 which caused the Windows key as a modifier for bindings to not work properly 
Let windows skip across monitors in a Xinerama setup when using MoveToEdge or Shift-arrow in an interactive move 
Make move and resize take the dock into account for resistance 
Raise new windows when it makes sense, when they aren't being focused 
Change default config to use click events for mouse wheel bindings instead of presses

Download [here]("http://icculus.org/openbox/index.php/Openbox:Download").

---

### Post by K.Mandla on 2007-08-11
3.4.4 is excellent. Faster and snappier, from my perspective. You'll want the ObConf deb too, since that has been updated as well.

---

### Post by urukrama on 2007-08-12
> **K.Mandla said:**
> 3.4.4 is excellent. Faster and snappier, from my perspective.

I've updated Openbox, mainly for the 'new focus stealing prevention that is smart and not intrusive and not annoying'. I also have the feeling it is faster than 3.4.2 (never used 3.4.3).

One odd thing, though: where do I find the default configuration files for Openbox? Given that some things changed (the option to have or not have a notification when switching desktops, etc), I assume that there are some additional sections in the 3.4.4 rc.xml file, but I can't find any. Not in /usr/share/ not in /usr/local/share/, not in /etc/ .

*EDIT: Found them! They are in /etc/xdg/openbox/*

You can download the new obconf [here]("http://icculus.org/openbox/index.php/Openbox:Download#ObConf_-_Openbox_configuration_tool").

---

### Post by el mariachi on 2007-08-12
are you sure Obconf has been updated? I already use version 2.0.2 since I switched to OpenBox, which was about a month ago.

---

### Post by urukrama on 2007-08-12
> **el mariachi said:**
> are you sure Obconf has been updated? I already use version 2.0.2 since I switched to OpenBox, which was about a month ago.

It was released with Openbox 3.4.3, on [July 22nd]("http://icculus.org/openbox/index.php/Openbox:News#Openbox_3.4.3_and_ObConf_2.0.2_released"). If you installed Openbox 3.4.3, you probably have Obconf 2.0.2 as well. Sorry for the confusion.

---

### Post by fuscia on 2007-08-12
i had always installed openbox via synaptic, until 3.4.2. if i decide to upgrade to 3.4.4, what do i need to do? (gnub alert!)

---

### Post by el mariachi on 2007-08-12
> **fuscia said:**
> i had always installed openbox via synaptic, until 3.4.2. if i decide to upgrade to 3.4.4, what do i need to do? (gnub alert!)
I just downloaded the deb from it's site and everything works great:)

---

### Post by urukrama on 2007-08-12
> **fuscia said:**
> i had always installed openbox via synaptic, until 3.4.2. if i decide to upgrade to 3.4.4, what do i need to do? (gnub alert!)

If you use Feisty, download the .[deb]("http://icculus.org/openbox/releases/openbox_3.4.4-0ubuntu1_i386.deb"); otherwise download the [source]("http://icculus.org/openbox/releases/openbox-3.4.4.tar.gz") and follow[ the installation instructions]("http://icculus.org/openbox/index.php/Help:Installing#Building_and_installing_the_program").

---

### Post by fuscia on 2007-08-12
sorry, i meant don't i need to get rid of the existing openbox, first? if so, how do i do that? just dump everything i can find that says 'openbox' on it?

---

### Post by el mariachi on 2007-08-12
If you installed it from the repos just go for the deb and the package will be updated. You don't need to remove anything.

---

### Post by urukrama on 2007-08-12
If you installed through Synaptic, you can uninstall it through there (or apt/aptitude). If you installed it with a deb package, you can do the same. If you installed from source and used 'sudo checkinstall' as the last step (instead of 'sudo make install'), you should also be able to remove it through Synaptic (or apt-get). If you just used 'make install', try configuring (./configure) and making (make) the package again and then do 'sudo make unisntall'.

Or you can try and delete everything manually.

---

### Post by fuscia on 2007-08-12
> **urukrama said:**
> If you installed through Synaptic, you can uninstall it through there (or apt/aptitude). If you installed it with a deb package, you can do the same. If you installed from source and used 'sudo checkinstall' as the last step (instead of 'sudo make install'), you should also be able to remove it through Synaptic (or apt-get). If you just used 'make install', try configuring (./configure) and making (make) the package again and then do 'sudo make unisntall'.

Or you can try and delete everything manually.

well, that was simple. took me less than thirty seconds. thanks, dude.

---

### Post by el mariachi on 2007-08-12
urukrama: I'm still searching for that shutdown/restart/log-off manager alternative, with no luck. If you find anything please share ;)

---

### Post by ynnhoj on 2007-08-12
have you tried using xfce4's shutdown/etc dialog?  maybe it won't work outside of the xfce desktop environment, but it could be worth a try.  add an entry for the command
```
/usr/lib/xfce4/xfsm-shutdown-helper
```
to your openbox menu and see what happens.

i'd test it myself, but i don't have xfce installed :o

---

### Post by el mariachi on 2007-08-12
well I'm on pure openbox but, for the exception of Thunar, I use gnome's stuff like theme management and system monitor. I'll see if it works anyway.

---

### Post by fuscia on 2007-08-12
> **el mariachi said:**
> urukrama: I'm still searching for that shutdown/restart/log-off manager alternative, with no luck. If you find anything please share ;)

why not just do an 'exits' sub-menu, with seperate item entries for log out, restart and shutdown?

---

### Post by el mariachi on 2007-08-12
because I like to have a special window for that and those submenus don't work well for me. I must have the wrong commands

---

### Post by fuscia on 2007-08-13
> **el mariachi said:**
> because I like to have a special window for that and those submenus don't work well for me. I must have the wrong commands

i can't remember, are you opposed to using the xfce panel, as well? if not, you could use its logout window.

---

### Post by K.Mandla on 2007-08-13
> **el mariachi said:**
> because I like to have a special window for that and those submenus don't work well for me. I must have the wrong commands
Are those sudo commands? Like "sudo shutdown -h now"? Or something else?

I was just thinking that you could edit your /etc/sudoers file and allow anyone to run a shutdown command, and then they (should) work without sudo.

Sorry if I've misunderstood.

---

### Post by urukrama on 2007-08-13
> **fuscia said:**
> i can't remember, are you opposed to using the xfce panel, as well? if not, you could use its logout window.

Does that work for you? Whenever I use it, it only kills the panel, but doesn't affect my openbox session in any way. Same with the gnome-panel.

---

### Post by fuscia on 2007-08-13
> **urukrama said:**
> Does that work for you? Whenever I use it, it only kills the panel, but doesn't affect my openbox session in any way. Same with the gnome-panel.

darn! you're right. i just use a menu entry, so it never occurred to me that might not  work. nevermind...

---

### Post by picpak on 2007-08-13
> **el mariachi said:**
> because I like to have a special window for that and those submenus don't work well for me. I must have the wrong commands

Would using

```
xfce4-session-logout
```

work? I haven't tried it yet.

---

### Post by fuscia on 2007-08-13
> **picpak said:**
> Would using

```
xfce4-session-logout
```

work? I haven't tried it yet.

xfce4-session has to be installed. might as well just click on 'exit'.

---

### Post by el mariachi on 2007-08-13
I've using 'sudo shutdown -h now' and it doesn't work... 
'sudo reboot' WAS working but not anymore... I just press the power button now and it begins the shutdown procedure

---

### Post by diatribe on 2007-08-13
> **el mariachi said:**
> I've using 'sudo shutdown -h now' and it doesn't work... 
'sudo reboot' WAS working but not anymore... I just press the power button now and it begins the shutdown procedure

you may want to try gksudo, so it prompts for your pass, then it may work

---

### Post by moore.bryan on 2007-08-13
*hey all... is anyone else getting "segmentation fault" when trying to run the newest obconf?*

---

### Post by urukrama on 2007-08-13
not I

---

### Post by K.Mandla on 2007-08-14
> **moore.bryan said:**
> *hey all... is anyone else getting "segmentation fault" when trying to run the newest obconf?*
Not here, but I'm on Arch right now.

---

### Post by moore.bryan on 2007-08-14
*i sometimes think i'm the only on in the world... ;-)*

---

### Post by el mariachi on 2007-08-14
that never happened to me. you got it from the deb right?

---

### Post by moore.bryan on 2007-08-14
*yup... right off the openbox site.*

---

### Post by fuscia on 2007-08-14
none here, bryan, and i consider segmentation faults somewhat of a specialty for me.

---

### Post by urukrama on 2007-08-14
Last time I had a segmentation fault (with Thunar) almost all my applications started having segmentation faults. Reinstalling didn't help, and I couldn't find an easy solution, so I ended up doing a clean install.

---

### Post by el mariachi on 2007-08-14
I might have to do one, clean install that is. Suddenly everything seems to have gone slowish -I upgraded the kernel to Gutsy's version and it seemed to be faster at first but now even epiphany drags.
This way everything will be installed just right. I'll also install PCLinuxOS or Fedora (haven't decided yet) just to feel another distro -with openbox of course!

---

### Post by moore.bryan on 2007-08-14
> **urukrama said:**
> Last time I had a segmentation fault (with Thunar) almost all my applications started having segmentation faults. Reinstalling didn't help, and I couldn't find an easy solution, so I ended up doing a clean install.
*i don't have segmentation faults with any other programs... just obconf.  and this is on a "brand new" install, so i'd hate to have to go through all that hassle just after i get everything where i want it... ;-)*

---

### Post by K.Mandla on 2007-08-14
It's a dirty word, but have you tried compiling it for yourself?

---

### Post by moore.bryan on 2007-08-14
*i didn't even think of that... just did it, with success.  thank you k.mandla for the sound of reason...*

---

### Post by K.Mandla on 2007-08-14
> **moore.bryan said:**
> *i didn't even think of that... just did it, with success.  thank you k.mandla for the sound of reason...*
You're more than welcome. Glad it worked. :mrgreen:

---

### Post by el mariachi on 2007-08-15
darn it. I can't compile nitrogen under fedora 7.
I already have gcc, GTKMM-dev, GTK, autoconf, automake 
what are all the dependencies?
this maybe a little offtopic but I can't live in OpenBox without this:
There's a small app that runs single commands ('Run program/application') I have it on Ubuntu but I completely forgot it's name.. any idea?
Thanks guys!

---

### Post by urukrama on 2007-08-15
[gmrun]("http://directory.fsf.org/all/gmrun.html")?

---

### Post by el mariachi on 2007-08-15
> **urukrama said:**
> [gmrun]("http://directory.fsf.org/all/gmrun.html")?
May you have a happy and prosperous life!:KS

---

### Post by moore.bryan on 2007-08-15
[I]hey guys/gals...

i know ob folk are always looking for a decent minimalist fm... i'm an xfe fan because i hate thunar, but i know many think it's ugly.  ran across [flybird]("http://www.fly-bird.org/") and it looks pretty nice.[/I]

---

### Post by dbbolton on 2007-08-15
> **el mariachi said:**
> darn it. I can't compile nitrogen under fedora 7.
I already have gcc, GTKMM-dev, GTK, autoconf, automake 
what are all the dependencies?
this maybe a little offtopic but I can't live in OpenBox without this:
There's a small app that runs single commands ('Run program/application') I have it on Ubuntu but I completely forgot it's name.. any idea?
Thanks guys!
this might help (i mean the dependencies list)

[http://ubuntuforums.org/showthread.php?t=508848](http://ubuntuforums.org/showthread.php?t=508848)

---

### Post by dbbolton on 2007-08-15
> **moore.bryan said:**
> [I]hey guys/gals...

i know ob folk are always looking for a decent minimalist fm... i'm an xfe fan because i hate thunar, but i know many think it's ugly.  ran across [flybird]("http://www.fly-bird.org/") and it looks pretty nice.[/I]
wow, it looks like a pretty version of gentoo fm!!

---

### Post by el mariachi on 2007-08-15
> **dbbolton said:**
> wow, it looks like a pretty version of gentoo fm!!
and of kommander -commander style fm.
is it faster than Thunar? (I like Thunar)

I compiled nitrogen, dunno how -I just installed a lot of dev stuff and it worked:lolflag:

My fedora is coming along good. But I was thinking, Is there a way to change the GTK theme of KDE apps like Amarok, kaffeine, k3b etc?

---

### Post by urukrama on 2007-08-15
> **el mariachi said:**
> My fedora is coming along good. But I was thinking, Is there a way to change the GTK theme of KDE apps like Amarok, kaffeine, k3b etc?

KDE apps don't use gtk themes. You'll have to hunt for themes on kde-look.org. You can use kcontrol to change theme, icon, colour, etc. settings, but it is all a bit more complicated than gnome-theme-manager (some find it great, others don't).

Thanks for info on FlyBird, bryan. It looks nice. I'll try it out in a little while, though I doubt it will replace my heavy-duty krusader.

---

### Post by el mariachi on 2007-08-15
> **urukrama said:**
> KDE apps don't use gtk themes. You'll have to hunt for themes on kde-look.org. You can use kcontrol to change theme, icon, colour, etc. settings, but it is all a bit more complicated than gnome-theme-manager **(some find it great, others don't)**.

Thanks for info on FlyBird, bryan. It looks nice. I'll try it out in a little while, though I doubt it will replace my heavy-duty krusader.

yep.. some people don't like to have gazillions of options to configure and none of them is a simple gtk theme chooser:lolflag:

---

### Post by K.Mandla on 2007-08-15
> **moore.bryan said:**
> [I]hey guys/gals...

i know ob folk are always looking for a decent minimalist fm... i'm an xfe fan because i hate thunar, but i know many think it's ugly.  ran across [flybird]("http://www.fly-bird.org/") and it looks pretty nice.[/I]
I started to compile that with yaourt (I'm still in Arch right now) and I got a fistful of Gnome dependencies. I think I'll hold off, even though it does look pretty nice.

---

### Post by picpak on 2007-08-15
> **el mariachi said:**
> I compiled nitrogen, dunno how -I just installed a lot of dev stuff and it worked:lolflag:

Dang! If you had waited a couple hours you could have used my [precompiled .deb](http://ubuntuforums.org/attachment.php?attachmentid=40750&d=1187215835)! :lolflag:

---

### Post by moore.bryan on 2007-08-15
> **el mariachi said:**
> is it faster than Thunar? (I like Thunar)
*xfe is a lot faster for me, flybird is almost as fast as xfe...*
> **urukrama said:**
> Thanks for info on FlyBird, bryan. It looks nice. I'll try it out in a little while, though I doubt it will replace my heavy-duty krusader.
*ew... krusader?  ;-)  no prob...*
> **K.Mandla said:**
> I started to compile that with yaourt (I'm still in Arch right now) and I got a fistful of Gnome dependencies. I think I'll hold off, even though it does look pretty nice.
*really?  i don't recall it asking for many at all on my system... perhaps i already had them.*

---

### Post by el mariachi on 2007-08-15
> **picpak said:**
> Dang! If you had waited a couple hours you could have used my [precompiled .deb]("http://ubuntuforums.org/attachment.php?attachmentid=40750&d=1187215835")! :lolflag:
no use for me anyway _>Fedora doesn't like deb:p
I'll use it on Ubuntu so thanks anyway!:KS

---

### Post by picpak on 2007-08-15
No problem, glad I could help.

---

### Post by urukrama on 2007-08-16
> **moore.bryan said:**
> ew... krusader?  ;-)  no prob...

It is the only KDE app I use, though not very regularly. A bit heavy, no doubt, but it has more features I use and like than Gnome-commander, Tux-commander or xfe have.

EDIT: I am not having much luck with FlyBird. My ubuntu laptop is not online, at the moment, and have only a Windows laptop that I can use to connect to the internet. I'm having a hard time getting all the dependecies. :( (libvte-dev is giving some serious problem)

---

### Post by K.Mandla on 2007-08-16
> **moore.bryan said:**
> *really?  i don't recall it asking for many at all on my system... perhaps i already had them.*
It's possible. I avoid them like the plague, so when I do see them, they stick out like a sore thumb. 

I've run out of similes, so I'll stop now. :p

---

### Post by urukrama on 2007-08-17
KMandla, the Wiki on the Flybird site gives these dependencies:
> SCons 
gtk+-2.0 >= 2.6 
gnome-vfs-2.0 
vte 
libgnomeui-2.0 
gnome-desktop 
eel-2.0

---

### Post by el mariachi on 2007-08-17
doesn't gnome-desktop install other stuff as well?

---

### Post by ynnhoj on 2007-08-17
> **el mariachi said:**
> doesn't gnome-desktop install other stuff as well?
gnome-desktop only has a few dependencies; were you thinking of ubuntu-desktop? it's the metapackage that installs everything.

---

### Post by fuscia on 2007-08-17
i couldn't find eel in the suppositories, so i gave up on flybird (plus, i love thunar). nice logo, though.

---

### Post by dbbolton on 2007-08-17
> **fuscia said:**
> i couldn't find eel in the suppositories, so i gave up on flybird (plus, i love thunar). nice logo, though.
i think the ubuntu package for eel is called libeel2-2

---

### Post by bonzodog on 2007-08-17
i am now using PCManFM for a file manager. It's very light, and resembles Thunar in more than a few ways.

---

### Post by moore.bryan on 2007-08-17
*looks nice, but it doesn't seem to be dual-pane.  :-(*

---

### Post by fuscia on 2007-08-17
just tried flybird. yuk.

---

### Post by moore.bryan on 2007-08-17
> **fuscia said:**
> just tried flybird. yuk.
[i]
is that a technical term?
;-)
[/i]

---

### Post by fuscia on 2007-08-17
> **moore.bryan said:**
> [i]
is that a technical term?
;-)
[/i]

it's a new kde media player.

---

### Post by moore.bryan on 2007-08-17
> **fuscia said:**
> it's a new kde media player.
[i]
shouldn't that by kyuk then?
[/i]

---

### Post by picpak on 2007-08-17
He probably means [JuK](http://developer.kde.org/~wheeler/juk.html). I've used it before; it's a nice player.

---

### Post by picpak on 2007-08-17
Anyone know how to bind the Windows key to the Openbox menu? I tried this:

```
    <keybind key="W">
        <action name="ShowMenu">
          <menu>root-menu</menu>
        </action>
    </keybind>
```

but it didn't work.

---

### Post by moore.bryan on 2007-08-17
*the key is usually "Super_L" or "Super_R", depending on which side of the keyboard the windows key is...*

---

### Post by picpak on 2007-08-17
I had them both, so I binded them both. It works perfectly, thanks! It's a much nicer solution than having a 1px margin to right-click in.

---

### Post by moore.bryan on 2007-08-17
> **picpak said:**
> I had them both, so I binded them both. It works perfectly, thanks! It's a much nicer solution than having a 1px margin to right-click in.
[i]
i completely agree... i went nuts with keybindings when i first installed openbox, now i need a cheatsheet to remember all my keyboard shortcuts.  hmm... doesn't that defeat the purpose?
;-)
[/i]

---

### Post by picpak on 2007-08-17
LOL, the only shortcuts I have now are this, Ctrl+T for the terminal, and my multimedia keys.

---

### Post by Bense on 2007-08-17
> **picpak said:**
> Anyone know how to bind the Windows key to the Openbox menu? I tried this:

```
    <keybind key="W">
        <action name="ShowMenu">
          <menu>root-menu</menu>
        </action>
    </keybind>
```

but it didn't work.

I know that you resolved this this instance, but should you ever run into this again you can fire open "xev" and press the key with the cursor over that window that pops up and it will tell you the name of the key pressed.  It's great for getting those "multimedia" keys to work.

---

### Post by picpak on 2007-08-17
> **Bense said:**
> I know that you resolved this this instance, but should you ever run into this again you can fire open "xev" and press the key with the cursor over that window that pops up and it will tell you the name of the key pressed.  It's great for getting those "multimedia" keys to work.

I use xev all the time...it's just I knew that W was used as the Windows key, but not that it had to be used with another key. Thanks though.

---

### Post by moore.bryan on 2007-08-17
> **urukrama said:**
> KMandla, the Wiki on the Flybird site gives these dependencies:
[i]
uh, i didn't install gnome-desktop and i'm running it...
[/i]

---

### Post by urukrama on 2007-08-17
> **moore.bryan said:**
> [i]
uh, i didn't install gnome-desktop and i'm running it...
[/i]

One of the dependencies of libeel-dev is libgnome-desktop-dev. 

I'm trying to get Flybird installed as I write (have an internet connection again). I hope I like it :-)

EDIT: Ok, this didn't quite work. According to the Flybird [Wiki]("http://fly-bird.org/wiki/pmwiki.php/Main/Installation") I have to use the following command:
```
su -c 'scons install'
```
I've never used su before, but guessed now that, unlike sudo, you need to know your root password for su (correct?). Since I don't know it, I tried sudo, but had to change to command to
```
sudo scons insall
```
Some output appears in the terminal, and when I try to run Flybird, I get the following error message:
```
I/O error : Permission denied
I/O warning : failed to load external entity "/usr/local/share/flybird/daafilemanager.glade"

(flybird:7548): libglade-WARNING **: document not well formed
Could not load main window xml descritpion

```
And I have no idea what to do now. (Why can't they just use the regular ./configure, make, checkinstall way...)

EDIT2: This is silly. I can run Flybird when I sudo the command, but not as a regular user. Hmm.

---

### Post by K.Mandla on 2007-08-17
> **urukrama said:**
> KMandla, the Wiki on the Flybird site gives these dependencies:
Yep, it's gnome-vfs and libgnomeui that I'd just as soon avoid. Too much Gnome makes my computer run like molasses.

---

### Post by moore.bryan on 2007-08-17
> **urukrama said:**
> ```
su -c 'scons install'
```
[i]
i never used this either, but i put it in just as it is and it worked for me...[/i]

---

### Post by urukrama on 2007-08-18
> **moore.bryan said:**
> i never used this either, but i put it in just as it is and it worked for me...

How then did you install it?

Anyway, I'll probably not keep Flybird. I prefer Thunar, and Krusader if I have to move a lot of files around.

How do I uninstall Flybird? Do I just delete all Flybird files manually, or is there a smoother way?

---

### Post by ynnhoj on 2007-08-18
> **urukrama said:**
> How then did you install it?

Anyway, I'll probably not keep Flybird. I prefer Thunar, and Krusader if I have to move a lot of files around.

How do I uninstall Flybird? Do I just delete all Flybird files manually, or is there a smoother way?
is there an "uninstall" target for scons?  i would assume that if you build and install using scons, there ought to be a way to remove the application with scons as well.  but that's just a guess..

---

### Post by picpak on 2007-08-18
I'm working on a script called ObBindings, a keybindings GUI for Openbox. Right now it's fairly limited, since it can only add keybindings, and even then it can only be ones that are executable. If you're interested though, you can download it and test it at the bottom of the post.

**BACKUP YOUR .CONFIG/OPENBOX/RC.XML BEFORE MAKING ANY CHANGES!**

```
cp .config/openbox/rc.xml .config/openbox/rc.xml.old
```

The script comes with a backup and restore function, but I haven't tested it yet.

---

### Post by moore.bryan on 2007-08-18
> **urukrama said:**
> How then did you install it?

Anyway, I'll probably not keep Flybird. I prefer Thunar, and Krusader if I have to move a lot of files around.

How do I uninstall Flybird? Do I just delete all Flybird files manually, or is there a smoother way?

> **ynnhoj said:**
> is there an "uninstall" target for scons?  i would assume that if you build and install using scons, there ought to be a way to remove the application with scons as well.  but that's just a guess..
*```
sudo -c scons uninstall
``` from in the flybird dir worked for me...*

---

### Post by urukrama on 2007-08-19
Nice, picpac. I haven't tried it yet, but I like the idea :-) It would be even nicer if it were integrated with obmenu (which needs some updating as well). *hint hint* ;-)

EDIT: I get the following error message when I try to run it:

> /home/urukrama/Desktop/obbindings: line 9: zenity: command not found

Are there some other dependencies I need to have installed?

---

### Post by dbbolton on 2007-08-19
> **urukrama said:**
> Nice, picpac. I haven't tried it yet, but I like the idea :-) It would be even nicer if it were integrated with obmenu (which needs some updating as well). *hint hint* ;-)

EDIT: I get the following error message when I try to run it:



Are there some other dependencies I need to have installed?
zenity is a program that provides limited user interaction with scripts. for example:

```
zenity --question --title "Title" --text "Question text?"
	if [ "$?" = "0" ]; then
		$(function)
```

i think it comes with ubuntu by default. are you using a custom install?

---

### Post by el mariachi on 2007-08-19
it worked for me! not a single error message

---

### Post by urukrama on 2007-08-19
Yes. A server install.

---

### Post by picpak on 2007-08-19
> **urukrama said:**
> Nice, picpac. I haven't tried it yet, but I like the idea :-) It would be even nicer if it were integrated with obmenu (which needs some updating as well). *hint hint* ;-)

I wish I knew more than Zenity and Bash, because then I would integrate it into obconf. Here's a mockup:

---

### Post by moore.bryan on 2007-08-19
> **picpak said:**
> I wish I knew more than Zenity and Bash, because then I would integrate it into obconf. Here's a mockup:

*frickin' sweet...:guitar:*

---

### Post by urukrama on 2007-08-20
I did an Openbox Ubuntu server install on an old machine that wasn't used. All worked fine, and all was nice. But then at some point I logged in and suddenly couldn't use the desktop space anymore: right click, middle click or scrolling don't do anything. Right clicking on the window decorations also doesn't bring up the client menu. 

Alt-F1 (custom keybind) still brings up the root menu, though, as alt-space also brings up the client menu. There seems to be nothing wrong with the menus themselves, in other words. 

There is also nothing wrong with the mouse -- all the buttons work in other applications. Everything else works in Openbox works fine as well (dock, keyboard bindings, etc.)

I looked into xsessions-errors, and this is what I get after a fresh login:
> /etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "urukrama"
/etc/gdm/Xsession: Beginning session setup...
/home/urukrama/.config/openbox/rc.xml:295: parser error : Opening and ending tag mismatch: keybind line 286 and keyboard
  </keyboard>
             ^
/home/urukrama/.config/openbox/rc.xml:707: parser error : Opening and ending tag mismatch: keyboard line 150 and openbox_config
</openbox_config>
                 ^
/home/urukrama/.config/openbox/rc.xml:708: parser error : Premature end of data in tag openbox_config line 4

^
/home/urukrama/.config/openbox/menu.xml:294: parser error : Opening and ending tag mismatch: menu line 3 and openbox_menu
</openbox_menu>
               ^
/home/urukrama/.config/openbox/menu.xml:295: parser error : Premature end of data in tag openbox_menu line 2

^
(The ^s are a bit mixed up. They point to the end of the entry (just after the last character)

The 'parser error' seems to be a blank line at the end of both the rc.xml and menu.xml file. I've tried to delete it (and save the file), but when I log in the next time, it is back again. And even when I delete the blank line, reconfigure (or restart) openbox, nothing changes, and the desktop still does not respond to any mouse activity.

What now?

---

### Post by ynnhoj on 2007-08-20
can you post the whole contents of those xml files?

---

### Post by urukrama on 2007-08-20
> **ynnhoj said:**
> can you post the whole contents of those xml files?

Sure. I've attached them to this post.

---

### Post by ynnhoj on 2007-08-20
there are a couple problems problem in your rc.xml: (this is starting at line 282)
```
    <keybind key="W-F6">
      <action name="Execute">
        <execute>opera</execute>
      </action></keybind>
	<keybind key="W-F7">
      <action name="Execute">
        <execute>oowriter</execute>
      </action>
    <keybind key="C-A-Delete">
```
- line 285: you have "</action></keybind>" all on one line -- i think they should be separated by a newline.
- line 290: you haven't closed the <keybind key="W-F7"> tag with a </keybind> before starting the next keybinding (<keybind key="C-A-Delete">).

edit: i think the menu file is okay, but it might be worth going over it more closely as well to check for similar errors.

---

### Post by urukrama on 2007-08-20
> **ynnhoj said:**
> - line 290: you haven't closed the <keybind key="W-F7"> tag with a </keybind> before starting the next keybinding (<keybind key="C-A-Delete">).

Thank you. That was a silly thing; I missed that mistake (despite repeatedly looking for one). I fixed it and all is back to normal. The other mistake did not affect anything.

---

### Post by ynnhoj on 2007-08-20
> **urukrama said:**
> Thank you. That was a silly thing; I missed that mistake (despite repeatedly looking for one). I fixed it and all is back to normal. The other mistake did not affect anything.
yer welcome.  i couldn't recall for sure from my xml & web services course back in college whether or not a parser would consider two closing tags on one line an error, so i mentioned it anyways..  guess it's okay though.  learn something new everyday!

---

### Post by el mariachi on 2007-08-21
Urukrama: What's the benefit of installing Ubuntu server edition? Is it lighter?

---

### Post by urukrama on 2007-08-21
I find it lighter, it works well for older computers and it doesn't come with a lot of applications I don't need.

I've done two server installs so far, and next time I need to install ubuntu I'll probably do it again. If you plan to do it, be prepared to spend some time on it -- it'll take longer than the 30 minutes a full ubuntu install needs, especially the first time you do it!

The disadvantage is that some things you are used to in ubuntu might not work because you did not install the needed packages, and unless you know what to add, you won't get it to work. The positive result is that I learned a *little* more about ubuntu :-)

If you have a decent computer you might not notice a big difference. If you work with older hardware and low specs, and have the time and inclination,  it is well worth it.

---

### Post by bonzodog on 2007-08-21
> **el mariachi said:**
> Urukrama: What's the benefit of installing Ubuntu server edition? Is it lighter?

I actually built my my box by installing Zenwalk Core, then adding X, and only the X apps I needed from there. It makes Ubuntu server look bloated, as Zenwalk Core literally only has enough installed to get an operational console based system, with just one or two extra apps like netpkg, Zenwalks package manager.

---

### Post by el mariachi on 2007-08-21
I'm gonna try it with in my old Pentium 3, supposing it will be faster than with the current Xubuntu installation.
Now that you've spoken of zenwalk... I've been looking at the system for quite some time now. I know it's based on Slack but I don't know what package system it uses (care to help?:))
And btw, do you find it to be faster than Ubuntu (server install)? I'm looking to build the faster system possible, with graphical apps -it's for my little brother. 
I know OSes like Puppy and DSL are lightning fast (I used them in the past) but I found them ugly. Can they use OpenBox as a WM? That would be faster than ZenWalk or Ubuntu server right? Lotta questions I know:lolflag:

---

### Post by bonzodog on 2007-08-21
> **el mariachi said:**
> Now that you've spoken of zenwalk... I've been looking at the system for quite some time now. I know it's based on Slack but I don't know what package system it uses (care to help?:))

Zenwalk uses the Slackware .tgz binary packge format. Do not confuse this with .tgz source file format. They can normally be told apart by looking at how the package is named.

I have always found Zenwalk to be lightning fast compared to any install of ubuntu. It uses Xfce as it's default desk, but openbox is in it's repos, even better though is that the openbox slackware packages on the openbox site work fine in Zenwalk. I am using the site packages because the Zen repo version is out of date.

BUT - a word of warning -- Zenwalk  tries to configure as much as it can and we do have GUI configs for a lot of things via a central control panel, but there is always something that might require you to jump feet first into the CLI, and it pays to be confident on the command line.

---

### Post by el mariachi on 2007-08-21
I'm writing from a freshly installed Ubuntu server ^^·
Now I need some help guys.:lolflag:

OpenBox is up and running, but I miss some stuff and I don't know where to get it.
How do you get a GUI for dpkg? is boring to use the cli everytime I need to install a deb
And rezlooks engine doesn't work :s Clearlooks and all the standard ones work. I installed rezlooks engine 0.6 from the deb from gnome-look

---

### Post by dbbolton on 2007-08-21
> **el mariachi said:**
> I'm writing from a freshly installed Ubuntu server ^^·
Now I need some help guys.:lolflag:

OpenBox is up and running, but I miss some stuff and I don't know where to get it.
How do you get a GUI for dpkg? is boring to use the cli everytime I need to install a deb
And rezlooks engine doesn't work :s Clearlooks and all the standard ones work. I installed rezlooks engine 0.6 from the deb from gnome-look
for the packages, you can use gdebi package installer

---

### Post by urukrama on 2007-08-21
> **el mariachi said:**
> I'm writing from a freshly installed Ubuntu server ^^· 

That was fast! :-)

A GUI for dpkg? If you mean synaptic, just install gksudo and synaptic, if you mean to install deb files, install gdebi.

I don't use rezlooks, so I'm not sure what is wrong there, though I have problems on this server install to get murrine working (though it works fine on my laptop). There is probably something in your /home/username/.xsessions-error file. I hope it says more than 'rezlooks engine not found' (that is what I get for murrine).

---

### Post by el mariachi on 2007-08-21
```
(epiphany:12786): libgnomevfs-WARNING **: Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libhttp.so' (/usr/lib/gnome-vfs-2.0/modules/libhttp.so: cannot open shared object file: No such file or directory)
```It's filled with that (xsession-errors)
It says that it can't find the rezlooks module :confused:

Yeah it was pretty fast, although a bit scary lol It was me and a command line for a couple of minutes. -I hate dependencies...
It's 'as fast as lightning' now:guitar:

another thing. I can't copy paste anything when I close the original app. I need a clipboard right?

---

### Post by ynnhoj on 2007-08-21
> **el mariachi said:**
> Yeah it was pretty fast, although a bit scary lol It was me and a command line for a couple of minutes. -I hate dependencies...
It's 'as fast as lightning' now:guitar:
good show!  i much prefer to build a system from the bottom up, insteading of having to trim a bunch of fat (a generic ubuntu install is obese :))

i'm not sure what to say about the gnome-vfs errors though.

---

### Post by moore.bryan on 2007-08-21
> **urukrama said:**
> [krusader] is the only KDE app I use, though not very regularly. A bit heavy, no doubt, but it has more features I use and like than Gnome-commander, Tux-commander or xfe have.
*i just want to go back and give props to krusader... i've recently installed ubuntu on my work lappie (totally breaking the company rules) and needed to access shares on a windows 2003 server.  konqueror was **way** too large, xsmbrowser **way** too sparse, and krusader **just** right.  i would have never known about it if it hadn't been for this past post, urukrama... many, many thanks.*

---

### Post by urukrama on 2007-08-22
> **moore.bryan said:**
> *i just want to go back and give props to krusader... i've recently installed ubuntu on my work lappie (totally breaking the company rules) and needed to access shares on a windows 2003 server.  konqueror was **way** too large, xsmbrowser **way** too sparse, and krusader **just** right.  i would have never known about it if it hadn't been for this past post, urukrama... many, many thanks.*

I'm glad I could help :-) 

Despite its weight, Krusader is one of those apps I love more each time I use it. I found the Krusader [website]("http://krusader.sourceforge.net/") very handy in discovering all the features I've come to love. I especially like the graphical disk usage analyser (see attached screenshot).

If only it were gtk!

---

### Post by moore.bryan on 2007-08-22
[I]that is pretty neat!  i think krusader may be my new favorite linux program...

another thing for the community, though.  i've tried and tried, but can't get opera to recognize flash is installed.  i've copied every possible plugin to the correct folder and nothing.  it works great in ff, but no dice in opera.  i've also noticed a considerable slow-down in opera since i upgraded to gutsy and a considerable speed-up in ff; strange?
[/I]

---

### Post by K.Mandla on 2007-08-22
> **urukrama said:**
> I especially like the graphical disk usage analyser (see attached screenshot).

If only it were gtk!
Filelight? Baobab? I've seen those do the same things. ... Is either one GTK? I don't think so, but I can't remember. I think Filelight is KDE-based, and Baobab is the same thing with Gnome guts.

---

### Post by bonzodog on 2007-08-22
> **el mariachi said:**
> ```
(epiphany:12786): libgnomevfs-WARNING **: Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libhttp.so' (/usr/lib/gnome-vfs-2.0/modules/libhttp.so: cannot open shared object file: No such file or directory)
```It's filled with that (xsession-errors)
It says that it can't find the rezlooks module :confused:

Yeah it was pretty fast, although a bit scary lol It was me and a command line for a couple of minutes. -I hate dependencies...
It's 'as fast as lightning' now:guitar:

another thing. I can't copy paste anything when I close the original app. I need a clipboard right?

You need to add gnome-vfs to your box. Use aptitude to install stuff.
A system with only openbox is going to be very light, but you *have* to get used to the CLI more, and learn to love it.

Otherwise, install synaptic. At least then you will have a way of finding stuff in the repos.

---

### Post by el mariachi on 2007-08-22
I already have synaptic. And damn do I hate dependencies... those little buggers already made my Package count grow from 500 to 730... everyhting seems to install some lib.

Rezlooks engine is working now, except in synaptic... damn...
But damn this is fast! I wanted to try the new Kernel with it but the available script only works for the generic one.

---

### Post by dbbolton on 2007-08-22
> **el mariachi said:**
> I already have synaptic. And damn do I hate dependencies... those little buggers already made my Package count grow from 500 to 730... everyhting seems to install some lib.

Rezlooks engine is working now, except in synaptic... damn...
But damn this is fast! I wanted to try the new Kernel with it but the available script only works for the generic one.
the engine doesnt work in synaptic, because synaptic is run as gksudo and has a different profile. typically, "root"'s theme is raleigh.

---

### Post by el mariachi on 2007-08-22
and isn't there a way to change it manually? Like editing root's gtkrc file or something

---

### Post by Seisen on 2007-08-22
I am going to ask a stupid question but how do I save my background in openbox. I have tried every solution that I can find and nothing works. I am using feh by the way.

---

### Post by fuscia on 2007-08-22
> **Seisen said:**
> I am going to ask a stupid question but how do I save my background in openbox. I have tried every solution that I can find and nothing works. I am using feh by the way.

i think you can do it in .xinitrc, but i'm not sure what the command would be. maybe something like *exec openbox & feh --bg-scale whatkindofstupidwallpaperisthat.jpg*

---

### Post by picpak on 2007-08-22
> **Seisen said:**
> I am going to ask a stupid question but how do I save my background in openbox. I have tried every solution that I can find and nothing works. I am using feh by the way.

If you use [Nitrogen](http://ubuntuforums.org/showthread.php?t=407623&highlight=nitrogen), you can put the following in .config/openbox/autostart.sh:

```
nitrogen --restore &
```

---

### Post by Seisen on 2007-08-22
I figured it out I did a little searching and found the xinitrc file in /etc/X11 and added ```
 eval `cat $HOME/.fehbg` &
``` and now it works.

---

### Post by urukrama on 2007-08-22
> **K.Mandla said:**
> Filelight? Baobab? I've seen those do the same things. ... Is either one GTK? I don't think so, but I can't remember. I think Filelight is KDE-based, and Baobab is the same thing with Gnome guts.

I know, and I've used baobab in the past. But I like the speed of Krusader's analyser and the integration into the file manager.

Since my general install is light, I don't mind having a few heavier apps thrown in (mainly openoffice, opera and krusader, when I use it). Otherwise what is the point of having resources you never use? Even with all those apps running at the same time, my openbox install is still fast and responsive enough for my tastes. 

> another thing for the community, though. i've tried and tried, but can't get opera to recognize flash is installed. i've copied every possible plugin to the correct folder and nothing. it works great in ff, but no dice in opera.

At some point I had flash working in Opera. When I reinstalled, I lost all of that, and have no idea how to get it back. The pages at [www.opera.com](www.opera.com) (which I used earlier to set up flash in Opera) no longer help. I've given up, and use another browser for the few times I need flash. I'd like to get it working, though, so if you find the solution, please let me know.

---

### Post by moore.bryan on 2007-08-22
[I]ready for some silly questions?  ;-)
1. i have rezlooks-engine and some themes, but gtk-chtheme and gtk-theme-switch can't find them... what's the deal?
2. my "smooth" themes give me the ```
Gtk-WARNING **: Unable to locate loadable module in module_path: "libsmooth.so",
``` warning and i haven't found any solutions.

ideas?
[/I]

---

### Post by el mariachi on 2007-08-22
It also didn't work for me, until I did this nifty command
```
./configure --prefix=/usr
```
and it worked. have you tried it? *rezlooks*

---

### Post by moore.bryan on 2007-08-22
*no dice.*

---

### Post by urukrama on 2007-08-22
And you have the smooth gtk engine installed? Also make sure the permissions of the folders are correct. It gave me some issues once.

---

### Post by moore.bryan on 2007-08-22
*yup... permissions are all set to allow execution...*

---

### Post by Freddy on 2007-08-22
> **moore.bryan said:**
> [I]ready for some silly questions?  ;-)
1. i have rezlooks-engine and some themes, but gtk-chtheme and gtk-theme-switch can't find them... what's the deal?[/I]
You might need to move the engine file, I don't have rezlook engine installed right now but back when I used it (both Ubuntu deb and from source) it got installed in (if I recall correctly) in /usr/lib/gtk-2.0/2.8.0 or something similar and I had to move it manually to /usr/lib/gtk-2.0/2.10.0.

---

### Post by K.Mandla on 2007-08-22
The engine itself doesn't change anything; you have to find a theme that uses the engine and then apply it. 

Unless you're using Arch, in which case the AUR package includes five or six sample rezlooks themes.

You could also test it by editing a theme and changing the engine to rezlooks. But it might be quicker and easier just to download one. ;)

---

### Post by ynnhoj on 2007-08-23
> **el mariachi said:**
> and isn't there a way to change it manually? Like editing root's gtkrc file or something
you could create gtkrc files for root, or you could make a sym link to your own gtkrc file(s); that way, the themes for root will always match yours
```
sudo ln -s ~/.gtkrc-2.0 /root/.gtkrc-2.0
sudo ln -s ~/.gtkrc-2.0.mine /root/.gtkrc-2.0.mine
```

---

### Post by el mariachi on 2007-08-23
thanks! that did it.
This type of installation really teaches you a lot about how the system works.~8D
Moving on to the next issue... how do I change my system font (the one used by the apps) manually? which file do I have to edit? I don't want to install gnome tools for this

---

### Post by urukrama on 2007-08-23
Change your .gtkrc2.0.mine file. Mine looks like this: 
> style "Sans"
{
font_name = "Sans 10"
}
widget_class "*" style "Sans"
gtk-font-name = "Sans 10"

gtk-icon-theme-name = "etiquette"

gtk-toolbar-style = GTK_TOOLBAR_ICONS

The last line gives me only icons in the toolbars (without text).

Make sure you have the following line in your gtkrc-2.0 file:

> include "/home/USERNAME/.gtkrc-2.0.mine"

You could place everything in the gtkrc-2.0 file, but that gets overwritten when you use gtk theme switcher, or a similar program, to change your themes.

---

### Post by moore.bryan on 2007-08-23
[I]is it possible to put the theme choice in the .gtkrc-2.0.mine file?

oh, and just to let everyone know because you were all losing sleep over it, i got smooth engine working by compiling it myself.  rezlooks **is** sweet.
[/I]

---

### Post by ynnhoj on 2007-08-23
> **moore.bryan said:**
> *is it possible to put the theme choice in the .gtkrc-2.0.mine file?*
i suppose.  though i think you'd probably still need a ~/.gtkrc-2.0 file containing the line
```
include "/home/yourusername/.gtkrc-2.0.mine"
```
so i don't know what you'd gain, as you would still have two files.

---

### Post by moore.bryan on 2007-08-24
> **ynnhoj said:**
> so i don't know what you'd gain, as you would still have two files.
*when i was having the theme-chooser issue, this would have been a work-around... thanks for the input.*

---

### Post by shearn89 on 2007-08-24
Does anyone have a cool font they can reccommend for TTM? I'm using gelly, but kinda want something different... Anyone know of any plans to enable TrueType fonts (ie, not XFT) for it?

---

### Post by el mariachi on 2007-08-24
> **shearn89 said:**
> Does anyone have a cool font they can reccommend for TTM? I'm using gelly, but kinda want something different... Anyone know of any plans to enable TrueType fonts (ie, not XFT) for it?
Only recently (a couple of days ago actually) did the tint's devs added UTF support so, maybe, that's a little far in future plans for them.

---

### Post by el mariachi on 2007-08-25
Do you guys know how to run OpenBox without a login manager (like GDM)?
I'm doing a server install on my old pc and I realised GDM wants too install too much crap. I found this goo alternative :
[SLiM]("http://slim.berlios.de/index.php") but I can't compile it -there must be something missing but I dunno what. Soo: OpenBox, no login manager, how? 8D

edit; openbox's wiki has [this]("http://icculus.org/openbox/index.php/Help:Getting_started#Starting_Openbox_without_the_graphical_log_in") to say, which I don't really understand...
edit2: another site explained it better.-> just startx and then openbox-session ^^

---

### Post by K.Mandla on 2007-08-25
I never use a login manager with Openbox; one I did use for a short while was [Qingy]("http://qingy.sourceforge.net/"). I think there's a deb floating around somewhere that makes it easy to install.

P.S.: If you've already bumped up to Gutsy, there's [a package in the repos]("http://packages.ubuntu.com/gutsy/admin/qingy") for it.

---

### Post by el mariachi on 2007-08-25
I'll check it.
How do you do that? I mean I run startx and then openbox-session BUT if I close the terminal window: bye-bye GUI. The OpenBox wiki talks about some xinitrc file is that it?

btw: any good lightweight non-gnome-dependant web browser?  Epiphany is great but---gnome dependencies

---

### Post by K.Mandla on 2007-08-25
Oops, I completely ignored your question, didn't I? :oops:

Boot your computer to the login prompt, and log in from there. Then issue startx from the command line. Inside the .xinitrc file for that user, make sure you have this line somewhere.

```
exec openbox
```
If you want to get fancy you can compile an autologin script and set your .bash_profile to start X as soon as you log in. Of course, neither of those is desirable if you're sharing the machine with someone who needs their own account.

---

### Post by el mariachi on 2007-08-25
> **K.Mandla said:**
> Oops, I completely ignored your question, didn't I? :oops:

Boot your computer to the login prompt, and log in from there. Then issue startx from the command line. Inside the .xinitrc file for that user, make sure you have this line somewhere.

```
exec openbox
```If you want to get fancy you can compile an autologin script and set your .bash_profile to start X as soon as you log in. Of course, neither of those is desirable if you're sharing the machine with someone who needs their own account.
Thanks! I'll just have to settle with editing .xinitrc, I don't know anything about scripting-

---

### Post by ynnhoj on 2007-08-25
make sure that any other programs you call in your .xinitrc file are run in the background (with the ampersand), and that the last line is
```
exec [window-manager]
```
here's a simple example..
```
#!/bin/bash

numlockx on &
eval `cat $HOME/.fehbg` &
conky &
visibility &
exec openbox
```

also: another option for a display manager would be [xdm](http://packages.ubuntu.com/feisty/x11/xdm).  it's a bit ugly, but if you want to you can [customize it](http://gentoo-wiki.com/TIP_XDM_Login_Screen_Customization).  i believe that when you log in from xdm, it executes the ~/.xsession file to start up your window manager and any other programs that you desire.  so you could just do a sym link in your home directory..
```
ln -s .xinitrc .xsession
```
then you only have to edit .xinitrc, and whether you start xorg using startx or xdm won't make a difference..

---

### Post by el mariachi on 2007-08-25
Thanks!

Back to my regular desktop something weird is going on...
First conky was crashing without reason -after a restart it seems fixed :s
Secondly, docker's auto-hide hides it but doesn't shows it again. It was working until now... has this happened to any of you before?

---

### Post by moore.bryan on 2007-08-25
[I]el mariachi... there's a string of threads about autologin without *dm, but the method that worked flawlessly for me is:
[/I][LIST=1]
[*]*in a term, create what will be the autologin script with *```
nano autologin.c
```
[*]*type/paste *```
int main() {
     execlp( "login", "login", "-f", "your_user_here", 0);
 }
```* and make sure to change "your_user_here" to your user name.*
[*]*then compile (so you need to make sure you need gcc installed) *```
sudo gcc -o autologin autologin.c
```
[*]*copy the new autologin file to your /usr/local/sbin folder*
[*]*edit /etc/event.d/tty1 to use your new autologin file by adding this line to it:*```
 exec /sbin/getty -n -l /usr/local/sbin/autologin 38400 tty1
``` *and commenting-out this line: *```
 exec /sbin/getty 38400 tty1
```
[*]*now, edit your .bash_profile file to actually use openbox *```
 if [ -z "$DISPLAY" ] && [ $(tty) == /dev/tty1 ]; then
    startx
fi
```
[*]*remove your *dm and reboot.*[/LIST][I]unfortunately, i don't remember which thread(s) i compiled all that above from, so if anyone can give/claim props, please do so.

now, for the browser, i like swiftweasel... seems faster than all the other swifts, weasels, and foxes.
;-)
[/I]

---

### Post by moore.bryan on 2007-08-26
*hey folk... can anyone suggest a dock-bar like awn, but without all the gnome dependencies?*

---

### Post by picpak on 2007-08-26
> **moore.bryan said:**
> *hey folk... can anyone suggest a dock-bar like awn, but without all the gnome dependencies?*

[Cairo-dock](http://ubuntuforums.org/showthread.php?p=3248766#post3248766).

Of course, if you don't want to use xcompmgr, there's [SimDock](http://www.getdeb.net/app.php?name=SimDock).

---

### Post by moore.bryan on 2007-08-26
[I]thanks picpak... i've spent the better part of today playing around with all the docks i could find.  long story short, they all suck.  that's not to say they won't suck in the near future, but as of right now--pardon my french--they blow.  the major detractor is the lack of a system tray in them.  i'm investigating panel replacements, but haven't truly found anything i like.  cairo-dock seems to be the most promising, but it's not very user-friendly, imho.  simdock looks to be in the same vein as kiba-dock.  awn wouldn't even compile for me because it needs libwnck18, but gutsy's too advanced for its own good.  :-)

if only someone would create an efficient, effective, minimalist dock... maybe that'll be the impetus for me to sit down and learn to code.
[/I]

---

### Post by ynnhoj on 2007-08-26
[wbar](http://freshmeat.net/projects/wbar/?branch_id=66660&release_id=259132) is pretty decent, but it's just a launch bar -- no system tray.

---

### Post by felicity on 2007-08-27
I just started using Openbox recently, but I'm loving it so far. It's really easy to edit the xml files, and fun to reposition windows wherever one wants them, almost like the tiling window managers. The positioning of windows on specific desktops works much cleaner than using devilspie. The only feature I miss is being able to control windows by the title name but it's not a huge problem. It's definitely my WM of choice now and I can only thank the developers for their hard work in making such a fun and efficient WM.=D>

[[IMG]http://img263.imageshack.us/img263/1788/screenshotoh6.png[/IMG]]("http://img297.imageshack.us/img297/4482/screenshot2ad8.png")

---

### Post by moore.bryan on 2007-08-28
[I]okay folks, strange python-related issue.  at startup, i have pypanel run, with no errors, but when i try to launch the tray icon for wicd or obmenu, i get this:
```
moore@ubuntu:/opt/wicd$ ./tray.py
Traceback (most recent call last):
  File "./tray.py", line 5, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
ImportError: /var/lib/python-support/python2.5/gtk-2.0/gtk/_gtk.so: undefined symbol: gtk_recent_action_get_type
```and this, respectfully:
```
moore@ubuntu:/opt/wicd$ obmenu
Traceback (most recent call last):
  File "/usr/bin/obmenu", line 21, in <module>
    import obxml, gtk, gtk.glade, gobject, random, time, os, sys
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
ImportError: /var/lib/python-support/python2.5/gtk-2.0/gtk/_gtk.so: undefined symbol: gtk_recent_action_get_type
```any ideas for where i can start to trouble-shoot this?

i've already tried reinstalling all the python and gtk stuff i have, but to no avail...
[/I]

---

### Post by el mariachi on 2007-08-28
I was noticed it was a little buggy, that's why I started using docker.

---

### Post by el mariachi on 2007-08-29
I'm starting to hate the word 'compile' :mad:
It's the third machine in which I do a n ubuntu server install and I can't compile nitrogen! It always says cpp fails in a sanity check. Last time I was able to compile it because I installed so many packages that one of them had to be the one missing/jammed.

Guys, please, once and for all: tell me which packages do you need to compile nitrogen, so I can write them in a post-it and stick them on my screen! 

In similar news, my docker is completely messed up:
The auto-hide doesn't work -it hides but never comes back again (though it doesn't kill itself). What can cause this? I recompiled but it didn't work.

---

### Post by K.Mandla on 2007-08-29
> **felicity said:**
> I just started using Openbox recently, but I'm loving it so far. It's really easy to edit the xml files, and fun to reposition windows wherever one wants them, almost like the tiling window managers. The positioning of windows on specific desktops works much cleaner than using devilspie. The only feature I miss is being able to control windows by the title name but it's not a huge problem. It's definitely my WM of choice now and I can only thank the developers for their hard work in making such a fun and efficient WM.=D>

[[IMG]http://img263.imageshack.us/img263/1788/screenshotoh6.png[/IMG]]("http://img297.imageshack.us/img297/4482/screenshot2ad8.png")
A most excellent screenshot, by the way.

Oops, I just revealed my secret identity: Keanu Reeves. :shock:

---

### Post by fuscia on 2007-08-29
dumped a whole bunch of gnome stuff today and am using gtk-theme-switch2 instead of the gnome-theme-manager. nitrogen stopped working with some of my icon sets, so i've gone back to my trusty old feh (i think feh's feelings are still hurt, though). things seem zippier, but that could be just the drugs. i think i might, at least, go the server install the next time around. i might even try something like gentoo (yeah, right). i should write an epic poem about openbox.

---

### Post by el mariachi on 2007-08-30
:lolflag:

you can't be 100% gnome-free though. Those guys are small and crafty and sneak into your system in every oppurtunity. 

Thunar installs a bunch of them (why is gnome-keyring a dependency:confused:), epiphany another bunch. I can't find an independent lightweight browser..

---

### Post by shearn89 on 2007-08-30
Have you tried ROX-Filer? I'm not sure what the dependencies are, but ROX is itself a whole desktop package, so i guess the file manager shouldn't depend on GNOME...

---

### Post by ynnhoj on 2007-08-30
> **el mariachi said:**
> Thunar installs a bunch of them (why is gnome-keyring a dependency:confused:), epiphany another bunch. I can't find an independent lightweight browser..
have you tried pcmanfm as a file manager?  and for the browser, you might want to consider [kazehakase](http://kazehakase.sourceforge.jp/).

---

### Post by fuscia on 2007-08-30
i'm not completely gnome free. i love thunar and, if that means having some gnome stuff, i'm cool with that ('cool with that'? when did i learn to talk like that?). i'm just trying to dump stuff i don't need: nautilus, totem, open office, etc. (if i don't need it, what do i need it for?)

---

### Post by moore.bryan on 2007-08-30
> **el mariachi said:**
> 

you can't be 100% gnome-free though. Those guys are small and crafty and sneak into your system in every oppurtunity. 

Thunar installs a bunch of them (why is gnome-keyring a dependency:confused:), epiphany another bunch. I can't find an independent lightweight browser..
[i]i've tried and tried to rid myself of gnome and finally gave-up.  for work, i need to have access to an exchange server, so evolution is my only choice.  even my wonderful claws-mail has gnome depends... i don't really get that one.

if you're willing to trade one master for another, i suggest krusader.  it was suggested earlier in this wonderfully beautiful thread and i'm never going back to xfe!

a nice alternative to firefox, which seems "faster" on my system, is [swiftweasel]("http://swiftweasel.sourceforge.net/").[/i]

---

### Post by fuscia on 2007-08-30
> **moore.bryan said:**
> a nice alternative to firefox, which seems "faster" on my system, is [swiftweasel]("http://swiftweasel.sourceforge.net/").

isn't swiftweasel just a tweaked firefox?

---

### Post by moore.bryan on 2007-08-30
*in essence, yes.*

---

### Post by fuscia on 2007-08-30
is it possible to get a clock in tint? (did i already ask this?)

---

### Post by el mariachi on 2007-08-30
I don't think so fuscia.
Is kazehakase even in english? lol you gotta download it from the japanese sourceforge (I wish I knew kanji)
I'll try it anyways!

---

### Post by ynnhoj on 2007-08-30
i've also heard accounts that seamonkey was faster than firefox.  i can't confirm that, and i highly doubt that it would perform better than epiphany, but it might be worth consideration.  it's not exactly lightweight, though.

@ fuscia: to the best of my knowledge, no you can't put a clock on tint.  you could always display the date/time with conky (or gkrellm if you use that), or put an xclock on yer desktop.

---

### Post by fuscia on 2007-08-30
fornication! i was afraid of that. i've gone the xclock route, for now. i like tint a lot, so i guess i'll stay with xclock (or hey, why don't i get a tres tasteful wall clock?).

---

### Post by dbbolton on 2007-08-30
> **fuscia said:**
> fornication! i was afraid of that. i've gone the xclock route, for now. i like tint a lot, so i guess i'll stay with xclock (or hey, why don't i get a tres tasteful wall clock?).
i always just rely on conky to be my clock when i run tint/visibility

---

### Post by ynnhoj on 2007-08-30
another thing that i think is pretty sharp is the [dali clock](http://www.jwz.org/xdaliclock/).  download the source and compile it if yer interested.  (if you have, i think, java installed you can watch a preview on the site..)

---

### Post by fuscia on 2007-08-30
i tried the dali clock for about 19 seconds yesterday. not a big fan of conky, either. tried cairo clock for a while too. looks like it's xclock, or buy a wall clock.

---

### Post by K.Mandla on 2007-08-31
There used to be a post somewhere around here that showed how to hotwire the Openbox menu to show the current time, rather than the word "Openbox" at the top. Hmm. :-k Would that interest you, fuscia?

---

### Post by el mariachi on 2007-08-31
> **K.Mandla said:**
> There used to be a post somewhere around here that showed how to hotwire the Openbox menu to show the current time, rather than the word "Openbox" at the top. Hmm. :-k Would that interest you, fuscia?
If it doesn't interest fuscia it's still worth mentioning, as it surely interests me!:)

I'm thinking of removing my pypanel for a while but then I  would lose my clock. I'm also trying a pipe menu to show gmails. I know someone here has done it, care to tell me? Or do the scripts on openbox's site work fine?

Thanks for the tip K.Mandla!

---

### Post by urukrama on 2007-08-31
KMandla, do you mean [this]("http://ubuntuforums.org/showthread.php?t=274922")? It doesn't display in the header, though, as far as I can tell.

You could also use bbtime, which can be configured to appear in the dock. It's nothing fancy, but then I don't need anything fancy from a clock. I like it because it has exactly the right size for my tastes and needs (unlike most dock apps), and it runs very lightly.

---

### Post by bonzodog on 2007-08-31
I have got conky showing my clock, and use something called peksystray for the systray, it's a dockapp, that can be custom sized down to a single icon size (26x26).
[[img]http://xs218.xs.to/xs218/07330/openzen17.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs218&d=07330&f=openzen17.png)

---

### Post by el mariachi on 2007-08-31
I'm sorry that this is not related to the current discussion  (although I'm also searching for an answer to it).

Do you know what's the calendar/agenda from this screenshot?
[http://offload1.icculus.org/openbox/mw/images/1/17/OgMaciel_20070607.png](http://offload1.icculus.org/openbox/mw/images/1/17/OgMaciel_20070607.png)
And: Do you guys know how to change the default X mouse theme?

---

### Post by yabbadabbadont on 2007-08-31
> **el mariachi said:**
> And: Do you guys know how to change the default X mouse theme?

On Ubuntu, the only reliable way that I have found is to install xcursor-themes and then use update-alternatives to install a new theme.  You have to do a little work before hand though.  First, you will need to copy your cursor theme to its own directory in /usr/share/icons.  Next, you need to create its own ".theme" file in /etc/X11/cursors.  I just copy the "core.theme" file to a new name for the new theme.  As an example, let's assume that the new cursor theme is called "MyCursorTheme" and is located in /usr/share/icons/MyCursorTheme.  In /etc/X11/cursors, copy core.theme to MyCursorTheme.theme.  Next, edit MyCursorTheme.theme and change ```
Inherits=core
``` to ```
Inherits=MyCursorTheme
```  Now you have to add your theme to the list of available xcursor themes in /etc/alternatives.  You do this by running ```
sudo update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /etc/X11/cursors/MyCursorTheme.theme 20
```  Now to set your new theme as the default, run ```
sudo update-alternatives --config x-cursor-theme
```  You will probably have to restart X before the change will take affect.

---

### Post by el mariachi on 2007-08-31
it didn't work..:confused:
the default themes don't work too.

---

### Post by yabbadabbadont on 2007-08-31
> **el mariachi said:**
> it didn't work..:confused:
the default themes don't work too.

If the default themes don't work either, then there is something else going on.  Perhaps Openbox has its own setting somewhere for specifying the cursor theme to be used?  I know that Gnome uses its own setting.  The instructions I provided should have at least changed the cursor theme used at the login screen.  (assuming that you are using GDM)

---

### Post by el mariachi on 2007-08-31
I ain't using GDM. I simply do 'startx'

---

### Post by yabbadabbadont on 2007-08-31
> **el mariachi said:**
> I ain't using GDM. I simply do 'startx'

Good, that makes my next trouble-shooting suggestion easier.  :D

Backup your current ~/.xinitrc and then change it so that it simply launches an xterm.  startx and see if your cursor is using the theme you set as default with update-alternatives.  (Just type exit in the xterm to leave X)  If it does use your custom theme, then Openbox must be overriding the cursor.  If it doesn't, then either you did something wrong when following my instructions or I screwed them up somewhere.  ;)  I'll setup a new cursor theme on my system to make sure that my instructions were correct.

EDIT: I just tested my instructions (I used cut and paste, then changed the theme name) and they worked fine.

---

### Post by bonzodog on 2007-08-31
To change my mouse cursor theme, I simply altered the default theme in ~/.icons. If you look in the ~/.icons dir, you will see a folder called 'default'.

In the default folder is a file called index.theme.

Alter the line that says 'name' to the name of your mouse theme, which MUST be in /usr/share/icons and simply log out then back in.

For example, my index.theme file in the default folder reads:

```

[Icon Theme]
Name=neutral
Example=left_ptr_watch

```

---

### Post by el mariachi on 2007-08-31
I guess Ubuntu server edition doesn't have all this. That default theme must be something from Gnome (my guess).

Maybe some package is missing, because even the X default one don't show up (it stays the ye'old black non-animated ones)

---

### Post by yabbadabbadont on 2007-08-31
> **el mariachi said:**
> I guess Ubuntu server edition doesn't have all this. That default theme must be something from Gnome (my guess).

Maybe some package is missing, because even the X default one don't show up (it stays the ye'old black non-animated ones)

Do you have the xcursor-themes package installed?

---

### Post by el mariachi on 2007-08-31
> **yabbadabbadont said:**
> Do you have the xcursor-themes package installed?
yes and I can choose the theme from the update-package 'dialog' (it asks me to choose the theme's number, that is displayed) I'm trying to use Simple and Soft but neither red glass or any other theme  work. Maybe something needs to be run at startup..?

---

### Post by ynnhoj on 2007-08-31
can't you set the xcursor theme in your ~/.Xdefaults file..?

---

### Post by moore.bryan on 2007-08-31
> **el mariachi said:**
> I'm sorry that this is not related to the current discussion  (although I'm also searching for an answer to it).

Do you know what's the calendar/agenda from this screenshot?
[http://offload1.icculus.org/openbox/mw/images/1/17/OgMaciel_20070607.png](http://offload1.icculus.org/openbox/mw/images/1/17/OgMaciel_20070607.png)
And: Do you guys know how to change the default X mouse theme?
*it looks like the gnome-panel calendar...*

---

### Post by fuscia on 2007-09-01
> **K.Mandla said:**
> There used to be a post somewhere around here that showed how to hotwire the Openbox menu to show the current time, rather than the word "Openbox" at the top. Hmm. :-k Would that interest you, fuscia?

that does sounds intriguing. (i already know i'm using openbox. what harm could it do?)

---

### Post by dbbolton on 2007-09-01
> **fuscia said:**
> that does sounds intriguing. (i already know i'm using openbox. what harm could it do?)
i thought there was a pipemenu for that very purpose; i could be wrong though.

---

### Post by fuscia on 2007-09-01
here it is - [http://ubuntuforums.org/showthread.php?t=274922](http://ubuntuforums.org/showthread.php?t=274922)

very classy solution. thanks, k. and db.

---

### Post by el mariachi on 2007-09-01
> **ynnhoj said:**
> can't you set the xcursor theme in your ~/.Xdefaults file..?
I have no such file:confused:

---

### Post by moore.bryan on 2007-09-01
> **el mariachi said:**
> I have no such file:confused:
*you have to create it... here's mine:*

---

### Post by el mariachi on 2007-09-01
Hurray! That did it! Thanks moore.bryan!!

---

### Post by moore.bryan on 2007-09-01
*no problem... you may want to "cull" some of the useless stuff in it which doesn't apply to your system, though.*

---

### Post by cawill on 2007-09-01
I have just installed openbox, but the gtk mac menu bar appears at the top of the screen and I want to disable it for my user that is running openbox, but keep it when using gnome on another user, usually you can do this by creating a .gnomerc file in your home directory but this doesn't work, does anyone have an idea how to get rid of this without recompiling libgtk?

---

### Post by el mariachi on 2007-09-01
yeah I done that.
now I just need to force friggin' docker to work like I want it to! It's driving me nuts

---

### Post by moore.bryan on 2007-09-02
> **el mariachi said:**
> yeah I done that.
now I just need to force friggin' docker to work like I want it to! It's driving me nuts
*what's the problem?*

---

### Post by el mariachi on 2007-09-02
it doesn't auto-hide right and the only way to make it display icons vertically is using 'docker -vertical', changing the corresponding option in ObConf doesn't work.

If auto-hide is on it simply disappears, not leaving that thin 1 or 2px line that, once hovered, makes the dock appear. This means that docker gets hidden but I can't make it come back (except by disabling auto-hide).

This started *before* the last fresh install (server) that was made a week ago.

---

### Post by jviscosi on 2007-09-02
> **fuscia said:**
> (i already know i'm using openbox. what harm could it do?)

Hey Fuscia, I wanted to thank you for recommending Openbox in that [Fluxbox]("http://ubuntuforums.org/showthread.php?t=517527") thread.  I've been using Openbox nonstop for the last several days and it seems to include everything I love about Fluxbox while resolving everything about Fluxbox that bugged me.  I think I have a new permanent window manager!

Boring [screenshot]("http://farm2.static.flickr.com/1284/1303321369_81b3375cfe_b.jpg"), if anyone is interested ...

---

### Post by fuscia on 2007-09-02
> **jviscosi said:**
> Hey Fuscia, I wanted to thank you for recommending Openbox in that [Fluxbox]("http://ubuntuforums.org/showthread.php?t=517527") thread.  I've been using Openbox nonstop for the last several days and it seems to include everything I love about Fluxbox while resolving everything about Fluxbox that bugged me.  I think I have a new permanent window manager!

oh! i'm glad you're liking it. the recent changes, in my view, have kicked openbox up a few notches.  (no offense intended to fluxbox.)

when i first tried openbox, all i got was a blank screen. i thought it didn't work until i realized that's all there was to it.

---

### Post by urukrama on 2007-09-02
> **jviscosi said:**
> Boring [screenshot]("http://farm2.static.flickr.com/1284/1303321369_81b3375cfe_b.jpg"), if anyone is interested ...

Wow! You use a lot of dockapps.

Btw, is it possible to have a lightweight Openbox setup with KDE material, instead of Gnome? I don't mean using KDE with Openbox (instead of kwin), but having a pure openbox session and using KDE/qt apps and tools instead of gtk/gnome stuff.

It seems everyone goes automatically for the gnome/gtk apps, rather than KDE/qt.

---

### Post by ynnhoj on 2007-09-02
i used to use konqueror and amarok with openbox, without any major impacts on performance.  if you load the kde libraries when x starts, it's all good.  and even if you don't, it should just be the first time that you start a kde app that you notice a slow load..

---

### Post by moore.bryan on 2007-09-02
> **ynnhoj said:**
> it should just be the first time that you start a kde app that you notice a slow load..
*like a thousand years!  ;-)  no, seriously, i like a bunch of kde apps on openbox... i don't know if i could live without k3b; it beats the crap outta gnomebaker.  i could go cli, by why?  :-)*

---

### Post by ynnhoj on 2007-09-02
i guess it would depend on how often you use your burner -- i'm happy with mkisofs and cdrecord on the command-line.. but it's not often that i need to burn a cd. :)

---

### Post by K.Mandla on 2007-09-02
> **urukrama said:**
> KMandla, do you mean [this]("http://ubuntuforums.org/showthread.php?t=274922")? It doesn't display in the header, though, as far as I can tell.
Oops. That's the one. I mis-remembered it though. I thought it showed in the titlebar. Sort of the same idea though. :oops:

---

### Post by jviscosi on 2007-09-02
> **urukrama said:**
> Wow! You use a lot of dockapps.

LOL ... yes, I know.  I would have even more in there if they would fit.  You should see my [Window Maker setup]("http://www.flickr.com/photo_zoom.gne?id=542376910&size=o"), where the dockapps go around corners.

> **urukrama said:**
> 
Btw, is it possible to have a lightweight Openbox setup with KDE material, instead of Gnome?

Sure,  I use Amarok, K3B, and KPhotoAlbum all the time.  I have my login script run kdeinit at startup; otherwise the first KDE app you launch has to invoke it, which slows the app's initial startup time.  So as not to make the GTK apps feel left out, I also use Grip, Gaim, GnuCash, and Thunar.  ;-)  

Oh, one thing I've found when mixing and matching Gnome and KDE apps is that the respective sound servers (esd and artsd) seem to step on each other.  To get around that I start them both at login with a switch that causes them to release the sound device after two seconds of inactivity.  (I set that up a long time ago so I don't know if it's even necessary anymore ... maybe they play nicely now.)  Isn't KDE 4 going to use a new sound server?

---

### Post by urukrama on 2007-09-03
I'm thinking of an exclusive KDE/qt setup in Openbox, without any gtk apps, jviscosi, so I won't have to worry about the sound issues. But this is all for later. I'm still looking for a KDE theme I *really* like before I venture into that land.

What are lightweight KDE apps, actually? KDE apps are never included in 'lightweight apps' lists. I know Dolphin, but that is about it.

---

### Post by jviscosi on 2007-09-03
> **urukrama said:**
> What are lightweight KDE apps, actually? KDE apps are never included in 'lightweight apps' lists. I know Dolphin, but that is about it.

Hmm, I'm not sure ... well, I'm pretty confident that KWrite is lighter than OpenOffice Writer, and kate is a nice text editor that doesn't consume a lot of resources.  [This guy]("http://ktown.kde.org/%7Eseli/memory/desktop_benchmark.html") has done some actual measurement of memory usage for office apps and browsers between KDE, Gnome, XFCE, and Window Maker.  He is involved in the KDE project but doesn't appear to be particularly based.

Anything I talk about below is only apocryphal ...

KOffice is probably lighter than OpenOffice.

I'd suspect that ShowImg and digiKam are lighter than KPhotoAlbum.  They just seemed faster when I used them.  That said, I prefer KPhotoAlbum's functionality.

Konqueror is a heavier file manager than Thunar but seems to be a lighter browser than Firefox, and I'm pretty sure KMail is lighter than Thunderbird.  (I use Seamonkey for both browsing and e-mail.)  I'm not familiar with the new one, Dolphin.

Kopete is a perfectly serviceable IM client.  I don't know how light it is compared to Gaim, but it seems lighter than Trillian (for Windows).

K3B is irreplaceable.  ;-)

Amarok is by no stretch of the imagination lightweight, but it's also far and away the most functional Linux jukebox I've used.  If you want something lighter, give Juk a try.  I used it before Amarok was around.  I don't think Juk does iPods, but there is a project called kpod  that brings together libqtpod and ipodslave to give iPod functionality to Konqueror.  If you have a Creative Zen-based MP3 player, KZenExplorer will talk to it, and you can drag MP3 from Amarok, Konqueror, or Juk to it.

KXDocker is an interesting Kicker replacement, but I never used it much.

---

### Post by fuscia on 2007-09-03
kde-core is a lighter way to use kde. with kpersonalizer, you can shut off a lot of the glitz. i found dolphin to be lighter than thunar and i don't think konqueror uses very much more memory than thunar (it uses a lot less than nautilus, for sure). kmplayer is a nifty little media player that can use both xine and mplayer. i'm using kde now and it's pretty zippy.

---

### Post by urukrama on 2007-09-03
Thanks all for the input. Much appreciated.

---

### Post by K.Mandla on 2007-09-04
I brushed past KDEmod for Arch Linux a few days ago; I admit I was very impressed. I don't usually think well of full desktop suites, but KDEmod was snappy and full-featured at the same time. 

I downloaded Kubuntu for fun, but I haven't tried it yet.

---

### Post by felicity on 2007-09-04
Does anyone know how one would go about changing the program icons that show up in the Alt-Tab display? :)

---

### Post by el mariachi on 2007-09-04
> **felicity said:**
> Does anyone know how one would go about changing the program icons that show up in the Alt-Tab display? :)
If you use Gnome/KDE those should be the icons you selected in the theme manager.

On the other hand, if you're using pure openbox add this line to ~/.gtkrc 
```
gtk-icon-theme-name="Somatic-0.2"
```
where "Somatic-0.2" is the theme's name (change it accordingly).

---

### Post by felicity on 2007-09-04
el mariachi: Thanks for your help, but I already have the icon theme set in .gtkrc2.0. What I meant more specifically was changing the individual program icons. For instance MPlayer just has a generic icon (the same that urxvt uses for instance) and I'd like to be able to use a new icon for those individual programs that have generic ones. Is it possible to do this?

---

### Post by dbbolton on 2007-09-04
> **felicity said:**
> el mariachi: Thanks for your help, but I already have the icon theme set in .gtkrc2.0. What I meant more specifically was changing the individual program icons. For instance MPlayer just has a generic icon (the same that urxvt uses for instance) and I'd like to be able to use a new icon for those individual programs that have generic ones. Is it possible to do this?
i'm not sure, but i think those particular icons are loaded from /usr/share/pixmaps or possibly a folder unique to the program (for instance, the Exaile window icons come from /usr/share/exaile)

---

### Post by el mariachi on 2007-09-04
If the icons don't show up then, most probably, your icon theme doesn't have the icon for that specific app (which one is it btw?).
If this is the case, you'll have to get those icons from other icon themes and then copy them to the icon theme you're using. This is done by browsing into the folder of the theme with the app icons and copying all the icons for that app (they are organized by size and then by type -you want the application type)

or dbbolton is right :p

---

### Post by felicity on 2007-09-04
Cool, thanks a lot! :):):)

---

### Post by el mariachi on 2007-09-04
My turn:)
How do I add/modify the title of the menu? I used menumaker and it erased the title -I want it back >:( lol

---

### Post by felicity on 2007-09-04
You just put <separator label="Openbox" /> wherever you want. 
(under <menu id="root-menu" label="Openbox 3"> if you want it at the top of the menu)

---

### Post by el mariachi on 2007-09-04
This is weird... If I add either one of those lines to the top of menu.xml It reverts to the default menu :S

---

### Post by felicity on 2007-09-04
You don't add it to the top of menu.xml, you add

<separator label="Openbox" /> 

under 

<menu id="root-menu" label="Openbox 3">

---

### Post by el mariachi on 2007-09-05
> **felicity said:**
> You don't add it to the top of menu.xml, you add

<separator label="Openbox" /> 

under 

<menu id="root-menu" label="Openbox 3">
right! it works, thanks!:KS

---

### Post by fuscia on 2007-09-06
i can't remember how i did this. i had my menu setup so that one click would open a terminal and then start mplayer playing a stream from somafm. it was something like

*favorite_terminal %somestupidletter mplayer [http://somafm.com/whydoyoulistentothatcrap.pls](http://somafm.com/whydoyoulistentothatcrap.pls)*

any notions?

---

### Post by yabbadabbadont on 2007-09-06
Try this:
```
favorite_terminal %somestupidletter -e mplayer http://somafm.com/whydoyoulistentothatcrap.pls
```

---

### Post by fuscia on 2007-09-06
thanks, yabba. that worked great for xterm (*xterm % -e mplayer stupidcrap.pls*). can't get it to work for xfce4-terminal, though. any further thoughts?

edit: aha! it's *x-terminal-emulator % -e mplayer dopeycrap.pls*

---

### Post by yabbadabbadont on 2007-09-06
Glad it worked.  Always remember, the man pages are your friends.  ;)

---

### Post by fuscia on 2007-09-06
> **yabbadabbadont said:**
> Glad it worked.  Always remember, the man pages are your friends.  ;)

oh yeah. i just didn't know which one to read. thanks again.

---

### Post by fuscia on 2007-09-07
zoom, konqueror, zooooooooooooooooooooom!!17


edit: :lolflag:

---

### Post by urukrama on 2007-09-07
:confused:

---

### Post by el mariachi on 2007-09-07
there there fuscia, it's ok :3 lol

---

### Post by shearn89 on 2007-09-07
Long day in the office, fuschia?

---

### Post by fuscia on 2007-09-07
> **shearn89 said:**
> Long day in the office, fuschia?

more like long neck on the bottle.

---

### Post by el mariachi on 2007-09-07
Nice new avatar!

---

### Post by ynnhoj on 2007-09-07
> **fuscia said:**
> more like long neck on the bottle.
okay, so what was in the bottle?  i'm working on a very tasty pint of boddingtons right now :)

---

### Post by fuscia on 2007-09-08
> **el mariachi said:**
> Nice new avatar!

thanks. i've thrown off the shallow veneer of pageantry and joined the resistance. 

[quote=ynnhoj]
okay, so what was in the bottle? i'm working on a very tasty pint of boddingtons right now[/quote]

lite beer from miller. fewer calories, less taste.

---

### Post by el mariachi on 2007-09-10
can you tell me where you got it? :p the avatar, not the beer *hate those no cal*

---

### Post by fuscia on 2007-09-10
> **el mariachi said:**
> can you tell me where you got it? :p the avatar, not the beer *hate those no cal*

it's a still from this movie - [http://www.imdb.com/title/tt0162866/](http://www.imdb.com/title/tt0162866/)

---

### Post by urukrama on 2007-09-11
I just made a new openbox theme, [Groove]("http://box-look.org/content/show.php/show.php?content=66092"). I created icons for toggled hovered and toggled pressed buttons (shade_toggled_hover.xbm, shade_toggled_press.xbm, etc.) and added the [appropriate]("http://icculus.org/openbox/index.php/Help:Themes#window.inactive.button.toggled.unpressed.image.color") options to my themerc file. For some reason, however, it doesn't work. When I hover over and press a toggled icon (maximize or shade) its colour changes according to the values set in the themerc file. But the icon itself doesn't change, however. Is this a bug in Openbox itself, in my install of Openbox (built from source), or did I do something wrong in my theme (if I did, I really wouldn't know what)?

I use Openbox 3.4.4, which should support these theme parameters that were introduced in 3.4.1.

---

### Post by dbbolton on 2007-09-11
> **urukrama said:**
> I just made a new openbox theme, [Groove]("http://box-look.org/content/show.php/show.php?content=66092&vote=good&tan=41547325"). I created icons for toggled hovered and toggled pressed buttons (shade_toggled_hover.xbm, shade_toggled_press.xbm, etc.) and added the [appropriate]("http://icculus.org/openbox/index.php/Help:Themes#window.inactive.button.toggled.unpressed.image.color") options to my themerc file. For some reason, however, it doesn't work. When I hover over and press a toggled icon (maximize or shade) its colour changes according to the values set in the themerc file. But the icon itself doesn't change, however. Is this a bug in Openbox itself, in my install of Openbox (built from source), or did I do something wrong in my theme (if I did, I really wouldn't know what)?

I use Openbox 3.4.4, which should support these theme parameters that were introduced in 3.4.1.
you might want to remove 

&vote=good&tan=41547325

from the link.

---

### Post by urukrama on 2007-09-11
Done. Thank you for that. It is still in your post, though.

But do the icons display properly on your computer?

---

### Post by el mariachi on 2007-09-11
> **urukrama said:**
> Done. Thank you for that. It is still in your post, though.

But do the icons display properly on your computer?
There are themes that do that and even OB's Default theme does it. So my guess is that something isn't configured correctly. I hope it's that way, because a bug is much more serious.

---

### Post by quixotic-cynic on 2007-09-11
Hi. I've been lurking on this thread for a bit, and learnt lots of stuff so I didn't have to go posting yet more questions, yet I am finally stuck enough that I have a question... if I have no panel working how can I keep a margin at the top of the screen to enable access to the menu without having to minimise the windows? (I have to use C-d atm)

A setting in the config file or a tiny program that just sets a strut would be great - if someone knows one of those two I would be grateful knowing about it.

---

### Post by urukrama on 2007-09-11
You can use the latest version of Obconf for that, downloadable from the Openbox website. There is a tab called 'Margins'; go there and select where you want to have a margin and how big. Or you can do it manually in the rc.xml file in /home/username/.config/openbox/

**mariachi**: what about that Groove theme? Do the icons work there?

---

### Post by el mariachi on 2007-09-11
it does urukrama! I guess that leaves you with 'compiling error' ?

quixotic: I set up a 1px margin on top that way I can access the menu. Just do as urukrama instructed.

btw **urukrama: **Could you upload your GTK theme (it's a rezlooks isn't it?) to Box-Look?

---

### Post by quixotic-cynic on 2007-09-11
> **urukrama said:**
> You can use the latest version of Obconf for that, downloadable from the Openbox website. There is a tab called 'Margins'; go there and select where you want to have a margin and how big. Or you can do it manually in the rc.xml file in /home/username/.config/openbox/

Thanks, that is just what I needed to know. At present I prefer sticking to the package system (though I managed to compile my alsa drivers, most compiles blow up on me). Since the OB version is a bit behind I guess i'm going to have to wait for now... x_X

EDIT: There is a gutsy 3.4.4 package [here]("http://packages.ubuntu.com/gutsy/x11/openbox").

EDIt 2: Used dpkg -i with --simulate but there are loads of dependencies that feisy can't meet. I know I could put the gutsy repos in my sources.list but that will cause knock on problems afaik. Guess I will have to wait for a bit.

---

### Post by el mariachi on 2007-09-11
what the hell are you talking about?:confused:

Are you using Feisty? If so just go to OpenBox's site and download the .deb package. it's the same as using the package manager (Synaptic).

No need to use Gusty's build.

---

### Post by quixotic-cynic on 2007-09-11
> **el mariachi said:**
> what the hell are you talking about?:confused:

Are you using Feisty? If so just go to OpenBox's site and download the .deb package.

Ok. I made one too many assumptions - I did not realise that the openbox team would make an ubuntu .deb - that is very nice of them. Thank you for pointing that out. :) 

Unfortunatley the dependency problems still remained. I'm using dpkg because I don't have gdebi etc installed. I usually use aptitude.

EDIT: Installed the new packages and... yep, it broke (not suprising, I guess I should have known better >.< ) and I had to fix it from the command line. Aptitude worked great - pointed out the dependency problems nicely & I could get back to 3.3.

---

### Post by el mariachi on 2007-09-11
that is... weird. Are you using a normal Feisty install? I even did a server install and everything went great! Are all the repos available?

As a last resort you can install the packages manually from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) just search for the ones you need and download the deb. Easy as 1-2-3:KS

---

### Post by ynnhoj on 2007-09-11
nifty theme urukrama!  if i ever get back to using openbox i'll try it out.

---

### Post by urukrama on 2007-09-11
> **el mariachi said:**
> it does urukrama! I guess that leaves you with 'compiling error' ?
btw **urukrama: **Could you upload your GTK theme (it's a rezlooks isn't it?) to Box-Look?

Thanks for the feedback. Very strange... and annoying.

Yes the gtk theme uses the rezlooks engine. It is far from perfect, but I've uploaded it to gnome-look.org, [here]("http://gnome-look.org/content/show.php?content=66120").

> **ynnhoj said:**
> nifty theme urukrama!  if i ever get back to using openbox i'll try it out.

Thanks, ynnhoj. You're still hanging out with the tiling window managers?

---

### Post by quixotic-cynic on 2007-09-11
> **el mariachi said:**
> that is... weird. Are you using a normal Feisty install? I even did a server install and everything went great! Are all the repos available?

My install started as a command-line one too. All the repos are enabled apart from multiverse and backports (even added medibuntu).

Should backports be enabled xor will it cause problems?

It's frustrating knowing that other people did not have any problems. Otoh it is good to know it is at least feasible.

I know that I can d/l the packages manually. Unfortunately, last time I changed a few packages it had a cascade effect giving me a whole load of conflicts that I had to resolve - and thus I am somewhat aprehensive about taking that option in the future.

Thanks for the reply, I will try some more tinkering tomorrow.

EDIT: Couldnt resist trying now. I enabled backports and it now works (not sure about any side effects yet though) so the issue is resolved more or less.

Now the OB font's gone tiny - got something else to tweak...(not a problem)  ;)   Thanks again for helping me get that fixed.

---

### Post by ynnhoj on 2007-09-11
> **urukrama said:**
> 
Thanks, ynnhoj. You're still hanging out with the tiling window managers?
yep.  i'm not sure it gets any better than this (tiling wms)!  but i do still have a soft spot for good ol' openbox.

---

### Post by el mariachi on 2007-09-12
guys I can't make .obt files with ObConf, it keeps saying that 'xxx isn't a valid theme directory.'

---

### Post by urukrama on 2007-09-12
> **el mariachi said:**
> guys I can't make .obt files with ObConf, it keeps saying that 'xxx isn't a valid theme directory.'

When the file/folder dialog comes up, you have  to select the folder with the name of the theme, not the "openbox-3" folder. It should work fine then.

---

### Post by el mariachi on 2007-09-12
yep, that did it. :)

---

### Post by urukrama on 2007-09-12
> **el mariachi said:**
> yep, that did it. :)

Of course it did :p Does this mean we can expect a new theme from you?

---

### Post by bonzodog on 2007-09-12
I have just downloaded and tried el mariachi's new theme. It's cool.

[http://www.box-look.org/content/show.php/gZen?content=66141](http://www.box-look.org/content/show.php/gZen?content=66141)

That, i believe (from info in the screenshots) , is el mariachi.

Quick question to him: How did you get the drop shadows?

edit: also, I have just had to repair the theme for the osd.elements, and some key theme elements were grammatically wrong.

It breaks the hidden dock in openbox in it's current form.

To fix it, i added to the osd area:

```

osd.border.color:#eeeeee
osd.border.width:1

```

Also, remove the fonts area from it -- they are no longer used, as they are specified from obconf.

There is an element error in the window.frame.color  -- the full stop is missing, and the C is lowercase.

Change the top comment to reflect your mod of the theme, adding your name and email address to the top as a new comment, and add the name of the theme.
BUT, leave in the previous attribution.

---

### Post by el mariachi on 2007-09-12
> **bonzodog said:**
> **It breaks the hidden dock in openbox in it's current form.**
Dude! That has been bugging me for a LONG time! Thanks a LOT!

I'm still a newbie in the theme-creation world so this type of comments are always appreciated. Again, thanks!:KS

I'll fix it and updated it. (btw: yes, iStrikeAgain is an alias, it seems el mariachi was already taken)

About the drop-shadows: It's xcompmgr (it's in the repos)
I run it with these settings (added this line to autostart.sh):
```
xcompmgr -cC -t-3 -l-5 -r5 -I0.028 -O0.03 -D5 -f &
```There are some useful tweaks for xorg.conf that go well with xcompmgr, if you don't know them and want them just ask ;)

**edit:**>  There is an element error in the window.frame.color  -- the full stop is missing, and the C is lowercase. I don't know what you mean by full stop, where should it be? *Fixed the uppercase 'C'
**edit2:**I think I got it. you mean it should be like this: window.frame.color: #eeeeee right?
**announcement: **I've fixed the bugs and updated the theme, you can get it @ box-look.org. The world is such a better place if you're in a community  :D

---

### Post by shearn89 on 2007-09-14
@el mariachi - NICE theme!

Anyone wishing to try Openbox - my tutorial just got the OK, so any criticism or feedback would be good. Any OB users who could spare the time to check it over and leave a comment are greatly appreciated! (Its my first Howto, so it may need some tweaking...)
It follows a post in the screenshot thread, and should give you a working, fairly decent OB setup quite easily.

---

### Post by el mariachi on 2007-09-14
Thanks! The gtk theme has been getting fairly decent downloads, I'm happy lol

I've taken a look at your tutorial. I think you should link to the documentation regarding autostart.sh (OpenBox's site is very good), so that people know what it is and know how to modify it.
Also you could say what feh, thunar and it's plugin are -I know what they are but will a newbie that just saw a screenshot and thinks 'wow OpenBox is cool I'll install that !!11!!!!1111'? The guide needs to be idiot-proof lol. Those are my recommendations, the rest is good imo. Congrats for the initiative!

---

### Post by shearn89 on 2007-09-14
cheers - just changed a few things (some formatting, added some links).

---

### Post by fuscia on 2007-09-14
> **shearn89 said:**
> anyone wishing to try Openbox - my tutorial just got the OK, so any criticism or feedback would be good. Any OB users who could spare the time to check it over and leave a comment are greatly appreciated! (Its my first Howto, so it may need some tweaking...)
It follows a post in the screenshot thread, and should give you a working, fairly decent OB setup quite easily.

pretty good. i hadn't heard about the pipe menu for managing wallpapers before (i just use feh for mine). i'll have to try it. your tutorial is a bit narrow in that it reflects the options you might choose, yourself. you might want to make it a bit more general. for example: instead of posting the code to install thunar, you might post a more generic code, like *sudo apt-get install favoritefilemanagerandallthetrimmings* and then list the possibilities (which would include anything from konqueror to thunar to mc). one of the intentions of openbox is to get out of people's way so that they can run whatever apps they wish, so it's important, i think, to make people aware of how wide their choices are, if that makes any sense.

---

### Post by shearn89 on 2007-09-14
> **fuscia said:**
> pretty good. i hadn't heard about the pipe menu for managing wallpapers before (i just use feh for mine). i'll have to try it. your tutorial is a bit narrow in that it reflects the options you might choose, yourself. you might want to make it a bit more general. for example: instead of posting the code to install thunar, you might post a more generic code, like *sudo apt-get install favoritefilemanagerandallthetrimmings* and then list the possibilities (which would include anything from konqueror to thunar to mc). one of the intentions of openbox is to get out of people's way so that they can run whatever apps they wish, so it's important, i think, to make people aware of how wide their choices are, if that makes any sense.

Thanks - it's mainly just an example of how to get it all up and running. I'll add in a comment about using a different file manager.

EDIT: added it in (as well as quoting your last sentence - very apt i feel). If people could let me know if they still think it is clear and easy to follow, I would be grateful.

---

### Post by el mariachi on 2007-09-14
apart from these details, that you already fixed, the guide is imo clear and easy to follow :)

---

### Post by shearn89 on 2007-09-15
Does anyone know any good hosting sites? As pointed out by K.Mandla, "wget"ting and attachment from the forums just saves an html file... A small problem, but it would be cool if the whole of my tutorial could be done Command-Line stylee...

---

### Post by quixotic-cynic on 2007-09-15
> **shearn89 said:**
> As pointed out by K.Mandla, "wget"ting and attachment from the forums just saves an html file... A small problem, but it would be cool if the whole of my tutorial could be done Command-Line stylee...

Would the kind of people that need a tutorial for openbox be able to appreciate the difference?

EDIT (reply for below): I guess that answers that question - some people do I suppose. ;)

---

### Post by shearn89 on 2007-09-15
I don't know - someone posted a comment requesting instructions to do it all via a terminal. I guess if you're trying to learn the syntax for all the useful commands its a good place to start...

---

### Post by K.Mandla on 2007-09-15
Not to diverge, but Ubuntulite has resurfaced as an Openbox/XDM-based deb package for Feisty. Right now the project needs some people to beta test, and since you're all well-versed in OB, you'd probably enjoy trying it out.

[http://groups.google.com/group/ubuntulite](http://groups.google.com/group/ubuntulite)

It's still very rough around the edges, but what it could use, at first glance, is a proper OB theme and some GTK1/2 accompaniment. If anyone is interested in trying their hand at it, remember that Feisty still uses 3.3.1, Gutsy will be 3.4.4, and I'm not sure if the themes are interchangable. 

Step up and get involved, and you could be famous! :roll:

---

### Post by yabbadabbadont on 2007-09-15
Isn't cross-posting to different threads/forums considered a no no?  If so, you'll have to give yourself a warning...   :D

---

### Post by K.Mandla on 2007-09-15
> **yabbadabbadont said:**
> Isn't cross-posting to different threads/forums considered a no no?  If so, you'll have to give yourself a warning...   :D
I shall report myself to the nearest authority. 

Except this one is asking for beta testers. The other is asking for themes and artwork.

Or that's what I'll tell the judge, anyway. ... :D

---

### Post by el mariachi on 2007-09-16
Seems like a good project! I'll beta test it too and maybe help out with the themes.

---

### Post by bonzodog on 2007-09-16
The accepted login manager for small and simple desktop distro's, is, IMO, SLiM. This is also in the repo's,  but it's only the very latest release that handles session management, and has a code re-work to strip it back a bit. 

Zenwalk Linux now uses SLiM as it was felt that gdm was a little too bloated for an xfce based distro. Personally, I love SLiM, and have it on my Zenwalk Core custom build desktop machine that has X and Openbox installed as the only environments available.

---

### Post by el mariachi on 2007-09-16
I just type 'startx' :pbut I used slim in the past and It's really good.
btw, Ubuntulite will use Kazehakase. Does any of you have experience with it? How does it compares to Epiphany.

---

### Post by K.Mandla on 2007-09-16
I love Kazehakase, and I really don't miss Firefox at all (I can't speak to Epiphany, I don't think I've used it in almost two years). Quick and speedy and does some nifty things that you can't do in Firefox without a bunch of additional extensions.

Unfortunately, 0.4.2 out of the Feisty repos has a nasty bug that prevents form submissions on secured sites. There might be a recompiled, newer version in UL.

---

### Post by ynnhoj on 2007-09-16
kazehakase seems nice, but every time i've built it it's been pretty buggy.  i'll wait a while and try it again another time..

---

### Post by el mariachi on 2007-09-16
I haven't used FireFox since I switched to Linux. I always use Epiphany, but I want to change because it depends on a bunch of gnome libs that I don't want. (I became very perfectionist lol).

I found some GTK browsers but they are all too dull. I'll try to compile Kazehakase myself, if I can download it from the japanese sourceforge lol

---

### Post by quixotic-cynic on 2007-09-16
Kazehakase fails for me for 1 major reson - no cookie whitelist! (afaik)

I mean, do they *seriously* expect me to allow cookies by default?!?!

Is there a no-script too? That would be another problem.

EDIT: I spent hours recently going throuhg all of the browsers in the repos. I came to the conclusion that *firefox* and *links2 -g* where the best (from my perspective). I tried Epiphany but, again, no cookie whitelist etc. links2 -g suprised me - i'm not sure many people know that it can do graphics.

---

### Post by el mariachi on 2007-09-16
I don't feel like compiling... Isn't there a kazehakase .deb somewhere?! 

Links2 just doesn't cut it for me... I need bling lol

btw Ob fans and gurus: I want to launch a script from the menu that needs to run in a terminal, what command do I add to the ObMenu entry? I use xfce-terminal and the script is the radio script made by Hund in the Screenshot Thread and is located in ~/scripts/radio

---

### Post by quixotic-cynic on 2007-09-16
> **el mariachi said:**
> I don't feel like compiling... Isn't there a kazehakase .deb somewhere?!

Edit: Repo version outdated so suggestion not helpful.

> **el mariachi said:**
> Links2 just doesn't cut it for me... I need bling lol

I'm not too bling-centric, but Links2 does push it even for me. How the hell people use w3m, links, etc as their main browser I shall never understand. :)

> **el mariachi said:**
> btw Ob fans and gurus: I want to launch a script from the menu that needs to run in a terminal, what command do I add to the ObMenu entry? I use xfce-terminal and the script is the radio script made by Hund in the Screenshot Thread and is located in ~/scripts/radio

I'm still a newbie (using Linux properly about 1 month) and have yet to graduate to Ob-gurudom ^_^  but derived from this thing I made to run my moblock updates (I started using urxvt because i'm a masochist):

    <item label='MB Update'>
      <action name='Execute'><execute>urxvt -e sudo sh /etc/cron.daily/moblock-nfq</execute></action>
    </item>

try this:

    <item label='Radio'>
      <action name='Execute'><execute>Terminal -x sudo sh ~/scripts/radio</execute></action>
    </item>

Does it work or did I miss something in what you are trying to do?

---

### Post by el mariachi on 2007-09-16
kazehakase's out-of-date in the repos :p that's why I asked :3

---

### Post by quixotic-cynic on 2007-09-16
doh  >.<

did the other idea work at all?

---

### Post by el mariachi on 2007-09-16
it did lol the cute ubuntu people keep the repo's stuff working but I want to try the new version.

---

### Post by quixotic-cynic on 2007-09-16
I tried to find a binary - and didn't manage it, so sorry. I did find a thread (partially) solving the compiling problem if you can muster the effort: [http://ubuntuforums.org/showthread.php?t=375802](http://ubuntuforums.org/showthread.php?t=375802).

Have you solved the script entry in your openbox menu? Did <action name='Execute'><execute>Terminal -x sudo sh ~/scripts/radio</execute></action> work?


EDIT: *Possible* solution:

1) Get the rpm of 0.4.7 here: [http://rpmseek.com/rpm-pl/kazehakase.html?hl=com&cx=2016:K:0](http://rpmseek.com/rpm-pl/kazehakase.html?hl=com&cx=2016:K:0)
2) Convert to deb using alien ([http://strabes.wordpress.com/2006/11/17/installing-rpm-packages-in-ubuntu/](http://strabes.wordpress.com/2006/11/17/installing-rpm-packages-in-ubuntu/))
3) Install deb

Any use?

EDIT: I know it's not the very latest but I thought it might be new enough.

---

### Post by el mariachi on 2007-09-16
The latest release is 0.4.8. I'll try to compile it, tomorrow :D
Yes, the menu entry did work, thank you!

---

### Post by wounded on 2007-09-17
I'm having trouble in my rc.xml file. I am trying to bind Alt+F9 to switch between play/pause in MPC but it doesn't work. If I switch the "mpc toggle" to "thunar" Thunar loads up when I press Alt+F9 O_O but "mpc toggle" doesn't work (It works if I do it from a terminal though).

This is what I have in my <keyboard> section.

```
    <keybind key="A-F9">
      <action name="Execute"><execute>mpc toggle</execute></action>
    </keybind>

```

Any ideas x.x?

(Also, an "mpc toggle" menu entry does nothing... Why does openbox hate MPD? :( )

---

### Post by yabbadabbadont on 2007-09-17
> **wounded said:**
> ```
    <keybind key="A-F9">
      <action name="Execute"><execute>mpc toggle</execute></action>
    </keybind>

```

Any ideas x.x?


```
    <keybind key="A-F9">
      <action name="Execute"><execute>xterm -iconic -e mpc toggle</execute></action>
    </keybind>

```
The only downside is that, if you use some sort of taskbar, you will see an xterm entry briefly flash in it and then disappear.

---

### Post by K.Mandla on 2007-09-18
> **el mariachi said:**
> The latest release is 0.4.8. I'll try to compile it, tomorrow :D
Any luck with 0.4.8? There's a recompiled 0.4.3 in the Ubuntulite repositories built of Debian testing, which should get it past the form submission bug. But if I could recompile 0.4.8, I'd do that for my own use.

Part of the reason I stick to Arch on my big machine is because 0.4.8 is in community, and Gutsy hasn't been stable enough for me to go jump to 0.4.3.

---

### Post by quixotic-cynic on 2007-09-18
I'm interested in whether or not someone has a sucessful compile of a later version too - I really want something better (read: faster / lighter) than firefox that still has what I need.

EDIT: *has decided kazehakase is satanic to compile*

EDIT2: The Kazehakase wiki req. no registration so gets spammed to hell. Anyone know a wiki where it would be possible to put proper documentation without it getting spammed?

---

### Post by K.Mandla on 2007-09-18
> **quixotic-cynic said:**
> I'm interested in whether or not someone has a sucessful compile of a later version too - I really want something better (read: faster / lighter) than firefox that still has what I need.

EDIT: *has decided kazehakase is satanic to compile*

EDIT2: The Kazehakase wiki req. no registration so gets spammed to hell. Anyone know a wiki where it would be possible to put proper documentation without it getting spammed?
Write it up as a tutorial and put it in the Tutorials and Tips forum. That's what I did for [VICE]("http://ubuntuforums.org/showthread.php?t=278022").

---

### Post by el mariachi on 2007-09-18
Yeah, this is really hard to compile :S I had no success at all.

---

### Post by quixotic-cynic on 2007-09-18
Couldn't get it to compile in the end. :(  I mentioned the documentation because there is *none* atm and that'd pretty stupid. I could contribute some after a sucessful compile... but there has to be somewhere to put it...

...

Okay, I got 0.4.7 installed via the method I posted [earlier]("http://ubuntuforums.org/showpost.php?p=3376387&postcount=799").

EDIT: FOUND 0.4.8! OH YEAH!  ... EDIT2: Nooo! AMD64 version. ... EDIT3: Found right version.

It is even easier than I thought it would be:
mkdir kazehakase
cd kazehakase
wget [http://download.fedora.redhat.com/pub/fedora/linux/updates/7/i386/kazehakase-0.4.8-1.fc7.i386.rpm](http://download.fedora.redhat.com/pub/fedora/linux/updates/7/i386/kazehakase-0.4.8-1.fc7.i386.rpm)
sudo aptitude install alien
sudo alien -i ./kazehakase-0.4.7-1.fc6.1.i386.rpm

Best I can do for now...

---

### Post by K.Mandla on 2007-09-18
Ah, royal sweetness. Thanks for that. I'm going to put it through a few tests on my end. Cheers and thanks again. ;)

Edit: Uh-oh. 

[quote=My little old laptop]dpkg-gencontrol: current build architecture i386 does not appear in package's list (amd64)[/quote]
Any ideas? It looks like that version was created for 64-bit. I'll keep looking.

---

### Post by quixotic-cynic on 2007-09-18
No! no! I fixed it just after you read it! ;)   (see previous post for edit comments)

I am really sorry about the mess-up - I should have been more thorough, but I was excited at finding the latest version. :(

---

### Post by K.Mandla on 2007-09-18
Ah, good. Thanks.

---

### Post by K.Mandla on 2007-09-18
Hm. It converts nicely and starts, but segfaults when a page is opened. Strange. ...

For now I can use 0.4.3 and get into my e-mail, etc. 

Now back to trying to unravel Siag. ... :)

---

### Post by wounded on 2007-09-19
> **yabbadabbadont said:**
> ```
    <keybind key="A-F9">
      <action name="Execute"><execute>xterm -iconic -e mpc toggle</execute></action>
    </keybind>

```
The only downside is that, if you use some sort of taskbar, you will see an xterm entry briefly flash in it and then disappear.

That is somewhat of a solution, I suppose, but I've had it work before. I passed "mpc toggle" to gmrun and it didn't work either so I guess it's a more generic thing than openbox messing up. I am using a non standard mpd port, but, I think my MPD_PORT variable is set up correctly because I don't have to pass any extra arguments to mpc or ncmpc via a terminal...

---

### Post by quixotic-cynic on 2007-09-19
See [http://ubuntuforums.org/showthread.php?t=554232](http://ubuntuforums.org/showthread.php?t=554232) for a full HOWTO to get Kazehakase 0.4.8 working.

---

### Post by quixotic-cynic on 2007-09-19
Before I loose it - lines for ~/.Xdefaults that make the rxvt terminal much more useful for people who don't like ultra-high-contrast tiny text. This is based on something I found a while ago, i'm afraid I cannot remember the initial source. Nb: more savelines = more memory used.

```
Rxvt*background:       DimGrey
!DarkSlateGrey 
Rxvt*foreground:       LightGray
Rxvt*scrollBar:	true
Rxvt*scrollBar_right:	true
Rxvt*saveLines:        2500
Rxvt*termName:         xterm
Rxvt*font:		xft:Monospace:size=12:medium:roman:antialias=true
Rxvt*boldFont:		xft:Monospace:size=12:bold:roman:antialias=true
Rxvt*italicFont:	xft:Monospace:size=12:medium:italic:autohint=true:antialias=true
Rxvt*boldItalicFont:	xft:Monospace:size=12:bold:italic:autohint=true:antialias=true
!Rxvt*fading:		60
!Rxvt*tintColor:	white
!Rxvt*shading:		20
!Rxvt*inheritPixmap:	true
!Rxvt*colorBD:		green
!Rxvt*colorIT:		grey
```

---

### Post by fuscia on 2007-09-20
for rxvt colors, i prefer giving the color shades number values, like 'gray10' for dark gray (for example), or 'gray90' for light gray.

---

### Post by quixotic-cynic on 2007-09-20
> **fuscia said:**
> 'gray10' for dark gray (for example), or 'gray90' for light gray.

Thanks. It's useful to know I can do that.

---

### Post by fuscia on 2007-09-20
> **quixotic-cynic said:**
> Thanks. It's useful to know I can do that.

it beats the crap out of trying to figure out what to call dark gray. i tried dark, dimmer, light black, etc.

---

### Post by ynnhoj on 2007-09-20
all those colours are defined in the rgb.txt file.  on my (arch) system it's found at: /usr/share/X11/rgb.txt.

if it's not there, a line in the "Files" section of your xorg.conf should tell you the location:
```
RgbPath	"/usr/share/X11/rgb"
```

---

### Post by quixotic-cynic on 2007-09-21
> **fuscia said:**
> it beats the crap out of trying to figure out what to call dark gray. i tried dark, dimmer, light black, etc.

^_^

> **ynnhoj said:**
> all those colours are defined in the rgb.txt file.  on my (arch) system it's found at: /usr/share/X11/rgb.txt.

... so I can make a color called FunkyNeonPink? :mrgreen:

---

### Post by fuscia on 2007-09-21
> **ynnhoj said:**
> all those colours are defined in the rgb.txt file.  on my (arch) system it's found at: /usr/share/X11/rgb.txt.

without samples, though, that file could pass for a horoscope. (wtf is 'cadet blue', for example?)

---

### Post by ynnhoj on 2007-09-21
paste the hex code into the gimp's colour selector and find out what it looks like :)  (duh!)

---

### Post by quixotic-cynic on 2007-09-22
<n/a>

---

### Post by fuscia on 2007-09-22
> **ynnhoj said:**
> paste the hex code into the gimp's colour selector and find out what it looks like :)  (duh!)

using number values is a far better way to control color than memorizing the appearance of colors associated with a bunch of flowery names that don't accurately describe those  colors. additionally, i would think gcolor2 would be sufficient for the task you suggest. using gimp would be a bit like getting a drink of water out of a fire hose.

---

### Post by ynnhoj on 2007-09-22
> **fuscia said:**
> using number values is a far better way to control color than memorizing the appearance of colors associated with a bunch of flowery names that don't accurately describe those  colors.
i totally agree -- i just thought i'd point out rgb.txt in case some folks didn't know where all those silly colour (you keep forgetting the "u" in colour, by the way) names were coming from.

---

### Post by ynnhoj on 2007-09-22
> **quixotic-cynic said:**
> Can anyone suggest a lightweight jabber client that is up to date? I tried centericq but had some problems with it. I have no problem with terminal-based apps but I do like the key options to be shown in them (e.g. aptitude).

Thanks for any suggestions. --QC
does pidgin do jabber..?  you could install pidgin and use the text-based version, which is called finch.  ("man finch" to get all the key bindings..)

---

### Post by fuscia on 2007-09-22
> **ynnhoj said:**
> (you keep forgetting the "u" in colour, by the way)

look at the way i spelled 'fuchsia'.

---

### Post by ynnhoj on 2007-09-22
well that's another story!

---

### Post by el mariachi on 2007-09-22
whenever I delete something from a pen drive or external hd, the stuff is just moved to .Trash-1000, a directory which I can't delete (If deleted it is moved to another .Trash-1000 directory atop the original one). How do I send the files to the bin or just delete them?

---

### Post by wounded on 2007-09-22
> **el mariachi said:**
> whenever I delete something from a pen drive or external hd, the stuff is just moved to .Trash-1000, a directory which I can't delete (If deleted it is moved to another .Trash-1000 directory atop the original one). How do I send the files to the bin or just delete them?

This happens to me and I use thunar. If you empty the trash bin they .trash stuff in the removable drive will get emptied also (Or you can just rm the stuff to bypass the trash system all together).

---

### Post by el mariachi on 2007-09-22
a stupid system --' I've made a menu entry to run rm -r on the directory

---

### Post by urukrama on 2007-09-22
> **el mariachi said:**
> a stupid system --' I've made a menu entry to run rm -r on the directory

What about shift+delete?

---

### Post by picpak on 2007-09-22
Going back to the topic we had almost a week ago: how do you compile slim 1.3.0 on Ubuntu?

---

### Post by el mariachi on 2007-09-22
sorry picpak to just change the topic :p it's a fast question.
Scribus (1.3.3.8 dev branch) isn't sporting my GTK theme.. it is a GTK app isn't it?

---

### Post by dbbolton on 2007-09-22
i'm getting this error when i launch obmenu:

```
Traceback (most recent call last):
  File "/usr/bin/obmenu", line 582, in <module>
    app.init()
  File "/usr/bin/obmenu", line 489, in init
    self.menu.loadMenu(self.menu_path)
  File "/usr/lib/python2.5/site-packages/obxml.py", line 153, in loadMenu
    self.dom = xml.dom.minidom.parseString(fil.read())
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/minidom.py", line 1925, in parseString
    return expatbuilder.parseString(string)
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/expatbuilder.py", line 942, in parseString
    return builder.parseString(string)
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/expatbuilder.py", line 223, in parseString
    parser.Parse(string, True)
xml.parsers.expat.ExpatError: mismatched tag: line 30, column 2

```anyone know what's up?

edit: i suppose this was caused by my menu.xml file, which is odd because i had copied the default one to my .config/openbox folder. i re-wrote the entire menu from scratch and now obmenu runs fine.

---

### Post by Carbon Tiger on 2007-09-22
Random question is it possible to set up a menu execute so the program runs in the terminal ie say I'm trying to run cplay ? 

Thanks.

---

### Post by yabbadabbadont on 2007-09-22
> **Carbon Tiger said:**
> Random question is it possible to set up a menu execute so the program runs in the terminal ie say I'm trying to run cplay ? 

Thanks.

Just call xterm with the "-e" parameter.  e.g. "xterm -e cplay"

---

### Post by Carbon Tiger on 2007-09-22
> **yabbadabbadont said:**
> Just call xterm with the "-e" parameter.  e.g. "xterm -e cplay"

And that does it thanks :)

---

### Post by JMO707 on 2007-09-23
Once again I'm here looking for a system tray =p

I've AWN running, but his applet is ugly ºoº

Tried to use wmsystray on the dock, but it doesn't compiles (error on make)

What are you using (if you do) for tray?

---

### Post by dbbolton on 2007-09-23
> **JMO707 said:**
> Once again I'm here looking for a system tray =p

I've AWN running, but his applet is ugly ºoº

Tried to use wmsystray on the dock, but it doesn't compiles (error on make)

What are you using (if you do) for tray?
if you want *just* a system tray, you could try docker. 

if you want a panel that includes a system tray, try pypanel.

---

### Post by quixotic-cynic on 2007-09-23
fbpanel can be used just as a system tray (and, for me, was far less painful to set up and change than pypanel)

---

### Post by yabbadabbadont on 2007-09-23
> **quixotic-cynic said:**
> fbpanel can be used just as a system tray (and, for me, was far less painful to set up and change than pypanel)

++

Also, if you build a newer version from source (it's easy), then the fbpanel system menu will automatically build a proper menu for you from the files found in /usr/share/applications.  (It looks like the Gnome menu basically)

---

### Post by quixotic-cynic on 2007-09-23
I don't use the menu thing - but I was very impressed in what it produced - a very nice menu.

---

### Post by JMO707 on 2007-09-23
Ahh, I finally am using the solution that you give me the firsth time I asked for a tray in this thread: peksystray =)

I endend up with a really minimal desk, wich I love.

[ [IMG]http://www.imagehosting.com/out.php/t1172832_01.png[/IMG]](http://www.imagehosting.com/out.php/i1172832_01.png)

---

### Post by PurposeOfReason on 2007-09-23
Hey, I was messing around with xcompmgr today and it's all been going good except that it puts a shadow around conky. I know how to get rid of it, by changing the own_window property but if I do that, then all the shadows go away. Is there a way to get it to just ignore conky?

---

### Post by dbbolton on 2007-09-24
> **PurposeOfReason said:**
> Hey, I was messing around with xcompmgr today and it's all been going good except that it puts a shadow around conky. I know how to get rid of it, by changing the own_window property but if I do that, then all the shadows go away. Is there a way to get it to just ignore conky?
the -C option might do it. (it's supposed to eliminate shadows on panels)

---

### Post by Carbon Tiger on 2007-09-24
Still putzing around on this......

Posted a screen shot last night with Xfce4 panel didn't care for it, doesn't match my desktop. But with some rewriting of my conky file to make it only show date/time, and adding in docker I think I have something I really like now. 

Thanks to the highly customizable menus in ob and middle click on my mouse to bring up the desktops (along with open files) makes it so easy to use. I think this might be the most fun I've had using a computer in years. :)

[http://i172.photobucket.com/albums/w3/qlebeau/Screenshot-1.png](http://i172.photobucket.com/albums/w3/qlebeau/Screenshot-1.png)

---

### Post by quixotic-cynic on 2007-09-24
> **Carbon Tiger said:**
> ...and middle click on my mouse to bring up the desktops (along with open files)

Thanks for reminding me about that - since I got rid of a panel I had been using alt-tab (which is a bit slower).

---

### Post by shearn89 on 2007-09-25
Hey all - weird problem. In openbox, even though i've changed the cursor theme, my standard mouse pointer is a black (rather old looking) pointer. When somethings loading, or i can select text, it changes to the appropriate theme's icons, but otherwise its an old (i guess x11) standard black pointer. If I start GNOME, it works fine.

Any ideas?

EDIT: Attached picture.
Plus, also just managed to actually (finally) get wireless to work at home! yay! took me long enough....

---

### Post by yabbadabbadont on 2007-09-25
> **shearn89 said:**
> Any ideas?

That is the default X cursor theme.  gnome-settings-de(a?)mon is overriding it for you.  You can either always start gnome-settings-demon, or change the system-wide default X cursor theme.  If you wish to change the default, let me know and I will post the long(ish) instructions.  (I don't feel like typing all of that up if I don't need to.  :D)

---

### Post by el mariachi on 2007-09-25
@yabbadabbadont: You mean you don't want to (re)write this?
[Change X cursor theme](http://ubuntuforums.org/showpost.php?p=3286591&postcount=693)

---

### Post by yabbadabbadont on 2007-09-25
> **el mariachi said:**
> @yabbadabbadont: You mean you don't want to (re)write this?
[Change X cursor theme](http://ubuntuforums.org/showpost.php?p=3286591&postcount=693)
With over 5000 posts, (just in this forum  EDIT: ubuntuforums.org that is), it's a wonder that I can remember what I posted yesterday, let alone 3 weeks ago...  :lol:

(and yes, that is what I didn't want to (re)type)

---

### Post by t0p on 2007-09-25
> **fuscia said:**
> i've made a few of my own openbox themes. they're easy to make. i wouldn't know a gtk theme unless i knew it were a gtk
theme.

Ho ho ho!

---

### Post by PurposeOfReason on 2007-09-25
> **dbbolton said:**
> the -C option might do it. (it's supposed to eliminate shadows on panels)
You would think so, but sadly not. Drop shadows weren't that cool anyways, lol.

But would it be possible to change what the volume popup looks like? I'm using the gnome-volume-manager though I'd be willing to use a different, less intrusive one if such one exists.

---

### Post by jviscosi on 2007-09-26
> **PurposeOfReason said:**
> Hey, I was messing around with xcompmgr today and it's all been going good except that it puts a shadow around conky. I know how to get rid of it, by changing the own_window property but if I do that, then all the shadows go away. Is there a way to get it to just ignore conky?

You might give [Devil's Pie]("http://burtonini.com/blog/computers/devilspie") a try.  I used to use it to remove shadows from gdesklet widgets by setting the window types to docks (if I remember correctly).  It can do all kinds of other stuff too.

If you're interested, I can post my Devil's Pie gdesklets config file when I get home.

---

### Post by shearn89 on 2007-09-26
> **yabbadabbadont said:**
> That is the default X cursor theme.  gnome-settings-de(a?)mon is overriding it for you.  You can either always start gnome-settings-demon, or change the system-wide default X cursor theme.  If you wish to change the default, let me know and I will post the long(ish) instructions.  (I don't feel like typing all of that up if I don't need to.  :D)

cheers - sorted it out.

---

### Post by commodore on 2007-09-30
I made a little GUI script for changing the background with feh. I haven't tested it that much but it worked for me. I wouldn't had made it if I would've known of the alternatives to feh. 
You need python, pygtk and of course feh.

---

### Post by PurposeOfReason on 2007-09-30
While I doubt it's possible, could you make the menu transparent? I know you can in fluxbox but I don't have the time to configure that today.

---

### Post by ynnhoj on 2007-09-30
i think you'd need to use xcompmgr and transset for that, PurposeOfReason..

---

### Post by PurposeOfReason on 2007-09-30
I thought about that, but from my understanding you have to click the object you want to make transparent. That wouldn't work for obvious reasons.

---

### Post by ynnhoj on 2007-09-30
i've never used it before -- that was just my best guess.  one of the other people who post frequently in this thread could probably tell you more about it..

---

### Post by el mariachi on 2007-09-30
I doubt you can do that in OpenBox... even with transset it is, as you said, obvious why it can't be done. If the menu was seen as a window you could set it's type and then make it transparent but I don't know how to do either of those

---

### Post by ynnhoj on 2007-09-30
> **commodore said:**
> I made a little GUI script for changing the background with feh. I haven't tested it that much but it worked for me. I wouldn't had made it if I would've known of the alternatives to feh. 
You need python, pygtk and of course feh.
noticed one problem..
[list]
[*]click the browse button
[*]cancel instead of choosing a file
[*]click the browse button again, and the filechooser dialog fails to open...
[i]Traceback (most recent call last):
  File "fehbg.py", line 135, in choose
    self.chooser.set_current_folder(self.file)
TypeError: GtkFileChooser.set_current_folder() argument 1 must be string, not None[/i]
[/list]
probably not a huge deal, as you can just restart the program, but it wouldn't hurt to resolve anyways :)

---

### Post by commodore on 2007-10-01
Weird but I can't seem to recreate that error. I tried to do something though, hope it fixes it.

---

### Post by shearn89 on 2007-10-03
here's a tricky one for you - on my openbuntu install (server edition + ob), i don't want to have to run gnome-settings-daemon, as it wipes my background everytime it starts. However, its the only way i can find to change the icon theme... Is there a tool out there (like gtk-theme-switch) to change icons?

---

### Post by ynnhoj on 2007-10-03
you might as well just do it manually; you can add..
```
gtk-icon-theme-name: "theme-name"
```
to your ~/.gtkrc-2.0.mine file (create it if it doesn't exist).

---

### Post by shearn89 on 2007-10-03
Cheers - works like a charm... i <3 ubuntu forums!

---

### Post by urukrama on 2007-10-04
Or you can use the xfce-mcs-manager and the xfce-setting-show dialog to change gtk themes, icons, and gtk fonts. If you don't load xfdesktop, it doesn't mess with the desktop image/settings.

---

### Post by ynnhoj on 2007-10-04
it's too bad [gtk-chtheme](http://plasmasturm.org/code//gtk-chtheme/) doesn't have an option to change the icon theme.  it would probably be pretty easy to add, though.. maybe i'll take a peak at the code later.

---

### Post by quixotic-cynic on 2007-10-05
Okay, I am being driven nuts by Firefox. I have started considering using Konqueror (since it seems faster but still has control-freak precision over cookies, js and images). I have tried a memory comparison, websites, etc, but memory use is not clear due to the KDE libraries. 

So, if a few of the people who frequent this thread could cease my mental anguish (hey, it's 1.32am and it's still bothering me ;)) - *on openbox* with Thunar as a file manager, is it nuts to use Konqueror? What about without Thunar?

Thanks to anyone who can help out with this question...

(I did read the brief comments on page 8/9).

---

### Post by fuscia on 2007-10-05
> **quixotic-cynic said:**
> Okay, I am being driven nuts by Firefox. I have started considering using Konqueror (since it seems faster but still has control-freak precision over cookies, js and images). I have tried a memory comparison, websites, etc, but memory use is not clear due to the KDE libraries. 

So, if a few of the people who frequent this thread could cease my mental anguish (hey, it's 1.32am and it's still bothering me ;)) - *on openbox* with Thunar as a file manager, is it nuts to use Konqueror? What about without Thunar?

Thanks to anyone who can help out with this question...

(I did read the brief comments on page 8/9).

there are a couple of different performance settings in konqueror, regarding memory usage, you might want to play with (settings>configure konqueror>performance). 

kde4 will come with both dolphin and konqueror. dolphin is similar to thunar, so it's not an outrageious thought to use both. have you tried monitoring how much memory you're using when combining the two?

---

### Post by urukrama on 2007-10-06
You can easily use KDE apps with Openbox, and if you use enough of them (media player, file manager, browser, etc.), it is worth it since they all use the same kde-libs.  I've played with that before, but never stick with it as I always realise after a short while that I am not that fond of kde apps. :-)

---

### Post by quixotic-cynic on 2007-10-06
Thanks for the replies. I used *free* to work out how much memory each used - boot + rxvt + browser, with a reboot in between.

Konqueror uses +8 megs of ram, (with an extra 5 cached?). However, I also just realised that that was with noscript and adblock disabled whereas  Konqueror has that functionality built in. Considering that the memory use of Firefox tends to be a bit dodgy, overall I think Konqueror is probably a serious competitor.

fuscia, I have dolphin installed but I was just thinking about using Konqueror as both browser and file manager... I did just try it though and dolphin seems to use less than 10 more megs (6?).

urukrama, I'm unlikely to ever use a lot of KDE apps - I know what you mean about not being fond of them. The default theme seems to be be very plasticy and too-rounded (and I kant stand the krazy obesssion with the knames). ;)

Thanks for the insights, i'm still not quite sure but more so than before.

---

### Post by urukrama on 2007-10-06
> **quixotic-cynic said:**
> urukrama, I'm unlikely to ever use a lot of KDE apps - I know what you mean about not being fond of them. The default theme seems to be be very plasticy and too-rounded 

I'm also still looking for a nice, sober kde/qt theme. Once I have that, I might spend more time with all the K-s. 

Have you considered other browsers? Opera offers plenty of control, but there if you have want less you can go also for epiphany, kazehakase, swiftfox/iceweasel, or even dillo, links2, elinks, etc. :-)

---

### Post by quixotic-cynic on 2007-10-06
Hmm, Konqueror can't disable referrer - minor but I always have it disabled in firefox (along with all the dom options etc).

There are a lot of browsers but my must-haves are control over:
* cookies, blocked by default with whitelist
* javascript, blocked by default with whitelist
* images, allowed by default with blacklist
& regular security updates.

Firefox does all that which is why I put up with it's annoyances but I really would like to switch. I liked Epiphany but it was too dumbed down. Opera, I'm not sure about...

Iceweasel seemed faster than FFx when I used it - it was really weird.

Edit: I think Konqueror was not one of my better ideas - the memory use of some of the 'other kde stuff' that runs has been creeping up a bit. Opera seems good, though I don't like the fact it is closed source (Kerckhoffs' principle etc).

Edit2: Opera = zoooooooommmmmmmmm!!! *but* takes about 8 seconds to start up on by pc?!?!? Edit3: Was my yoyo adblock list - it can't cope w/ lots of entries to block.

---

### Post by darkfox on 2007-10-06
Quixotic-cynic: I see that your edits have beaten me to it.  I was going to chip in that I needed a full featured graphical web browser that was fast and light, and while of course such a thing doesn't exist Opera came closest for me.  But yes, not appropriate if you need open-source.

But still, Opera. Fast, full, and not a resource-hog.  And eLinks for when you don't need the fancy stuff.

---

### Post by quixotic-cynic on 2007-10-06
Thanks, darkfox. I use 'links2 -g' sometimes too,

---

### Post by Rasi on 2007-10-08
don't know if it has been mentioned already, but you guys might want to check out this nice systray utility:

[http://stalonetray.sourceforge.net/](http://stalonetray.sourceforge.net/)

i have it running together with tint. can be run as a dock and just works.

---

### Post by aimran on 2007-10-09
My [mire V2 theme]("http://www.box-look.org/content/show.php/Mire+v2?content=60195&PHPSESSID=e8cf6e484a45c74438e1b058a3e2b545") is not looking as it is supposed to.

Window controls are not themed. I think its still using my metacity glossy bars/controls.

Any ideas?

---

### Post by ynnhoj on 2007-10-09
are you also using the mirev2 gtk theme?  you'll want to download that too..

---

### Post by aimran on 2007-10-09
Oh right, thanks! I thought that was just the gnome version.

---

### Post by arbulus on 2007-10-09
> **urukrama said:**
> Does that work for you? Whenever I use it, it only kills the panel, but doesn't affect my openbox session in any way. Same with the gnome-panel.

I recently heard of an app called Closure.  It provides a logout/shutdown option and confirmation screen.  I think it's actually geard toward folk running WMs instead of full-blown DEs.  It may be what you're looking for. 

Here's the project page:  [http://code.google.com/p/closure/](http://code.google.com/p/closure/)

---

### Post by -grubby on 2007-10-09
I use openbox w/ KDE when I use KDE

---

### Post by urukrama on 2007-10-09
> **arbulus said:**
> I recently heard of an app called Closure.  It provides a logout/shutdown option and confirmation screen.  I think it's actually geard toward folk running WMs instead of full-blown DEs.  It may be what you're looking for. 

Here's the project page:  [http://code.google.com/p/closure/](http://code.google.com/p/closure/)

Thank you. It looks interesting, but on closer inspection is not quite useful for my purposes. It is build to be used with AWN or Compiz/Beryl. According to the site, you still need sudo for some actions (presumably shutdown and reboot), and one of the dependencies is gnome-desktop.

---

### Post by John.Michael.Kane on 2007-10-09
> **urukrama said:**
> Thank you. It looks interesting, but on closer inspection is not quite useful for my purposes. It is build to be used with AWN or Compiz/Beryl. According to the site, you still need sudo for some actions (presumably shutdown and reboot), and one of the dependencies is gnome-desktop.

Here is a guide that might be of use, It requires the use of xmessage.
[using GUI dialog box]("http://linux.byexamples.com/archives/87/using-gui-dialog-box/")

---

### Post by arbulus on 2007-10-09
> **urukrama said:**
> Thank you. It looks interesting, but on closer inspection is not quite useful for my purposes. It is build to be used with AWN or Compiz/Beryl. According to the site, you still need sudo for some actions (presumably shutdown and reboot), and one of the dependencies is gnome-desktop.

I guess I missed some of that.  Wow, it has some really heavy dependencies.  

It's amazing how many things depend on GNOME and GTK in general.  It seems like it's really difficult to build a GUI and not have to use some sort of GTK dependency. And apps that require compositors can sometimes be frustrating.  While AWN is really nice (I use it and Compiz Fusion in GNOME) and that Closure app seems nifty, it seems like apps that require compositors alienate a big user base.  It's as though you can only use something that's nice and functional if you can afford the right hardware to run it.  It seems anathema to the Linux philosophy.

---

### Post by herbster on 2007-10-10
1. I am unable to use a lot of fonts for my Openbox menu when I select them in Obconf. I am only able to use certain fonts, as when I click on ones I got from dafont.com for example and hit ok, the menu font doesn't change at all :( :confused: Anyone?!

2. When altering the rc.xml, I can only notice the changes go into effect when I log out and back in, is there another way to "restart" the rc.xml or something without having to log out and in??

---

### Post by fuscia on 2007-10-10
> **herbster said:**
> 2. When altering the rc.xml, I can only notice the changes go into effect when I log out and back in, is there another way to "restart" the rc.xml or something without having to log out and in??

did you try 'reconfigure' in your right-click menu?

---

### Post by herbster on 2007-10-10
> **fuscia said:**
> did you try 'reconfigure' in your right-click menu?

Thank you! I had thought Reconfigure only applied to the menu, woops :)

---

### Post by urukrama on 2007-10-10
If I change fonts with Obconf, the changes take effect immediately. I don't have to 'Reconfigure' anything.

---

### Post by herbster on 2007-10-10
Yep, it's all fixed now, nevermind :)

---

### Post by urukrama on 2007-10-12
I'm having difficulties with OpenOffice in Xfce/Openbox -- it looks really terrible. It works fine Xfce without Openbox, or in pure Openbox if I add > export OOO_FORCE_DESKTOP=gnome to my autostart file. I don't know where to put this for xfce/openbox, though, since the Openbox autostart file isn't used when Openbox is a window manager of a desktop environment.

I have mentioned this already in an [existing thread]("http://ubuntuforums.org/showthread.php?p=3513657#post3513657"), but nobody seems to respond there. If you have a solution, you could post it there (otherwise I'll add the solution there myself).

---

### Post by yabbadabbadont on 2007-10-12
> **urukrama said:**
> I'm having difficulties with OpenOffice in Xfce/Openbox -- it looks really terrible. It works fine Xfce without Openbox, or in pure Openbox if I add  to my autostart file. I don't know where to put this for xfce/openbox, though, since the Openbox autostart file isn't used when Openbox is a window manager of a desktop environment.

I have mentioned this already in an [existing thread]("http://ubuntuforums.org/showthread.php?p=3513657#post3513657"), but nobody seems to respond there. If you have a solution, you could post it there (otherwise I'll add the solution there myself).

Just add it as the last line of your ~/.bashrc file.  If that doesn't work, then add it to ~/.bash_profile.  And if that doesn't work, add it to ~/.profile.  One of them should do the trick.  (or just add it to all three since it won't hurt anything ;))

---

### Post by el mariachi on 2007-10-13
I'm thinking about trying out the 64-bit version of Ubuntu (I've bought a 64 bit processor so using just half the bits is like burning money right? lol)

I couldn't find a 64-bit .deb but will it work regardless?

---

### Post by herbster on 2007-10-14
Some of my windows, primarily my aMSN chat windows, open with the titlebar beneath pypanel, so I can't grab the window by the titlebar and move it. I always have to hit alt+drag it away. How can I specify window not to open near the top as specific as the size of pypanel?? I already have the Obconf > Margins > Top margin set to 26px, the exact size of my pypanel but they still open up there and top gets cut off by the panel everytime :(

---

### Post by el mariachi on 2007-10-14
the margins only work for maximized windows. 
that happened to me too but I can't remember the solution now. Maybe someone will before me.

---

### Post by herbster on 2007-10-14
That would be great el mariachi. Asides from that I've got Openbox running so great, really love it :)

---

### Post by ynnhoj on 2007-10-14
in the applications section of your rc.xml file you should be able to force windows of a certain name or class (ie, an amsn chat dialog :)) to spawn at a certain coordinate.  if you look at the examples it should all be pretty straight-forward.

---

### Post by fuscia on 2007-10-14
wow! margins rock! (yes, i just realized this.)

---

### Post by herbster on 2007-10-14
ynnhoj,

Are you talking about the very end of the file at the <applications> section? I copied the example there and changed it to run Xine maximized on desktop 5, to test, and everytime I run Xine it doesn't work, just opens as it always does.

---

### Post by JMO707 on 2007-10-14
I was wondering: is it possible to set up the wallpaper without anything else than gconf?

gconftool-2 --type string --set /desktop/gnome/background/picture_filename *name*

seems to work, but only when I execut it from prompt. Putting it on autostart.sh is useless, as it appears to me. 

Can it be done?

---

### Post by Rasi on 2007-10-15
> **JMO707 said:**
> I was wondering: is it possible to set up the wallpaper without anything else than gconf?

gconftool-2 --type string --set /desktop/gnome/background/picture_filename *name*

seems to work, but only when I execut it from prompt. Putting it on autostart.sh is useless, as it appears to me. 

Can it be done?

has been mentioned several times, but you can either use feh (a command line tool), or you can use nitrogen, which has a little GUI to chose your wallpaper from. both should be available in the repos.

---

### Post by fuscia on 2007-10-15
> **Rasi said:**
> has been mentioned several times, but you can either use feh (a command line tool), or you can use nitrogen, which has a little GUI to chose your wallpaper from. both should be available in the repos.

feh is, nitrogen is not.

---

### Post by JMO707 on 2007-10-15
Yes yes, I know, but I was wondering if any external program, apart from the tools that come with Gnome, is necessary.

---

### Post by quixotic-cynic on 2007-10-20
Is there any way I can change the backgrounds of windows to light grey?

I looked at [http://icculus.org/openbox/index.php/Help:Themes](http://icculus.org/openbox/index.php/Help:Themes) but haven't found anything yet...

---

### Post by fuscia on 2007-10-20
> **quixotic-cynic said:**
> Is there any way I can change the backgrounds of windows to light grey?

I looked at [http://icculus.org/openbox/index.php/Help:Themes](http://icculus.org/openbox/index.php/Help:Themes) but haven't found anything yet...

if you're asking what i think you are, you can change the gtk theme to one that uses light gray with gtk-theme-switch2, or qt apps with qt3-config.

---

### Post by quixotic-cynic on 2007-10-20
Great. I suspect that is just what I am after. 

Thank you.

---

### Post by fuscia on 2007-10-20
> **quixotic-cynic said:**
> Great. I suspect that is just what I am after. 

Thank you.

my pleasure. 

if using gtk-theme-switch2 is one of the solutions, you can edit your .gtkrc-2.0 file to include .gtkrc-2.0.mine (i had to create it). in the latter file, you could choose an icon theme (everytime you use gtk-theme-switch2, it changes the icon theme to the default(yuk!) and there's no way to change it with gtk-theme-switch2). you can also include the font theme (which gtk-theme-switch2 can change), if you don't want to select it everytime you change a theme. unfortunately, qt3-config only affects non-kde apps, like opera, and doesn't seem to have an effect on kde apps, so you might as well just use kcontrol, if you use kde apps (kcontrol will change opera).

---

### Post by FoolishGhoul on 2007-10-23
not sure if this has been covered or not, but i've been searching the net for a while and haven't come up with anything satisfactory...

anyway, what i would like to do is fix the root-menu in the top left hand corner or the center of the screen (i'm starting the menu using a keyboard shortcut)

its really annoying having the menu appear under the mouse, when i hardly ever use the mouse for navigation...

any hints and tips would be appreciated...in simpleish language too! i know my way around a keyboard and emacs, but i'm not great at programming yet!

---

### Post by quixotic-cynic on 2007-10-26
> **fuscia said:**
> if using gtk-theme-switch2 is one of the solutions, you can edit your .gtkrc-2.0 file to include .gtkrc-2.0.mine (i had to create it). in the latter file, you could choose an icon theme (everytime you use gtk-theme-switch2, it changes the icon theme to the default(yuk!) and there's no way to change it with gtk-theme-switch2). 

That was a very good warning - I hate stuff that messes with my settings, grrrr ^_^

> **fuscia said:**
> if you're asking what i think you are, you can change the gtk theme to one that uses light gray with gtk-theme-switch2, or qt apps with qt3-config.

It was the right idea suggesting a theme change - that is how you would go about it. Unfortunately there are *no*  lower-contrast text/background themes for gtk (as far as I can see). I found one with a black text background and tried to isolate the line that made the it black so I could make it grey, but decided that so much effort for something so simple was stupid.

I tried  qt3-config and kcontrol and... Yay!  I got what I was looking for in about 20 seconds, thanks.

<gnome rant>
I've been getting annoyed with gnome hiding all its options, thus requiring users to hack text files to get anything done, for quite a while. I purged all Gnome packages and installed some KDE apps. I don't really like either but, for me, KDE is the least toxic. I still have a few gtk+ apps (Deluge...) but I am much happier with kcontrol than Gnomes miserable excuse for a config system.
</gnome rant>

---

### Post by quixotic-cynic on 2007-10-26
> **FoolishGhoul said:**
> anyway, what i would like to do is fix the root-menu in the top left hand corner or the center of the screen (i'm starting the menu using a keyboard shortcut)

I think you need to use something like <position>TopLeft</position> in the part of you ~/config/openbox/rc.xml file where you make the key binding.

```
<keybind key="A-F1">
    <action name="ShowMenu">
        <menu>root-menu</menu>
        <position>TopLeft</position>
    </action>
</keybind>
```

I haven't tried it (I don't really want to tamper with my setup) by I hope that gives you enough of an idea to work it out.

---

### Post by fuscia on 2007-10-26
> **quixotic-cynic said:**
> <gnome rant>
I've been getting annoyed with gnome hiding all its options, thus requiring users to hack text files to get anything done, for quite a while. I purged all Gnome packages and installed some KDE apps. I don't really like either but, for me, KDE is the least toxic. I still have a few gtk+ apps (Deluge...) but I am much happier with kcontrol than Gnomes miserable excuse for a config system.
</gnome rant>

i think gtk stuff looks great and i wonder if it is the structure that either allows for the possibility of great looking themes, or if its annoying 'hidden away' nature just keeps the average talent away from making gtk themes. kde color scheming is great, but the management of window decorations is a nightmare with no sense to it.

---

### Post by quixotic-cynic on 2007-10-26
> **fuscia said:**
> i think gtk stuff looks great and i wonder if it is the structure that either allows for the possibility of great looking themes, or if its annoying 'hidden away' nature just keeps the average talent away from making gtk themes.

I don't think theme makers would be put off by using text files (look at all the *box theme sites etc). However, after delving through the gtk theme files, I would say that the files are hell to understand (an exaggeration, but partly true). If the files where as readable as the openbox ones I'm sure there would be more themes. 

Also, stopping the user from tweaking a few settings in a GUI is just cruel - even windows *shudder* lets you do that.

> **fuscia said:**
> kde color scheming is great, but the management of window decorations is a nightmare with no sense to it.

:D   I'm with you on that one.

---

### Post by herbster on 2007-10-26
Okay I've been messing with the rc.xml file and I still can't figure out how the hell to get applications to open in certain workspaces and at specific locations, maximized/minimized, etc... basically functions similar to devilspie. For example I'd like Xine to always open on workspace 5, and be maximized. aMSN chat windows to open on workspace 1 at a specific location, etc.

This is really racking my brains. Anyone ?!?! :confused:

---

### Post by urukrama on 2007-10-27
Quite some time ago, I started working on a detailed howto for Openbox, that would help new users setup Openbox (and help me to remember some things). It was meant as a 'howto of howtos' (such arrogance! :p), that would detail how to install Openbox, configure it and use it, giving always plenty of options and links to other howtos on non-Openbox aspects (panels, apps, etc.).

After much neglect, I recently picked it up again and have most of it written now.  It is based on other existing howtos, lots of information from this thread and the openbox site, as well as my own experience.

I have one big gap remaining, though, and that is Openbox on Gutsy. How does it work? Are there some problems in getting it installed or running it? Does the Feisty deb work or do you have to compile from source? What about Obconf and obmenu? Do they work fine? Some feedback on this would be most helpful.

Now that shearn has posted a new howto for Openbox on these forums, I'm not quite sure what to do with mine. :confused: I don't want to have five Openbox howtos floating around on these forums, but mine is very different from his (as it isn't a guide for an 'easy' setup, but aims to be as complete as possible and practical), and the others are a bit outdated. Perhaps I'll post it on a blog or so, and link to it from here.

Anything you'd want to see included? Keep in mind, though, that the guide is meant for relative newcomers to Linux or Ubuntu users with very little technical knowledge, as the experienced users won't need a guide to get them going ;-)

---

### Post by urukrama on 2007-10-27
> **herbster said:**
>  For example I'd like Xine to always open on workspace 5, and be maximized. aMSN chat windows to open on workspace 1 at a specific location, etc.


This shouldn't be that hard.

For xine:
```
<application class="xine">
    <desktop>5</desktop>
    <layer>above</layer>
    <maximized>yes</maximized>
  </application>
```

for aMSN
```
<application class="amsn">
    <desktop>1</desktop>
  </application>
```

I don't think you can specify it to open in a particular area (top-left, bottom-right, etc.), though the app might remember what position it had on its last run.

Also make sure you have the app name right. I don't use xine or amsn, so can't tell, but are you sure that is the command used to launch them?

Finally, make sure you haven't left out the </applications> line at the end of the section, and that all xml code is wholesome. Perhaps you can post here your applications section of your rc.xml file?

---

### Post by herbster on 2007-10-27
> **urukrama said:**
> This shouldn't be that hard.

For xine:
```
<application class="xine">
    <desktop>5</desktop>
    <layer>above</layer>
    <maximized>yes</maximized>
  </application>
```

for aMSN
```
<application class="amsn">
    <desktop>1</desktop>
  </application>
```

I don't think you can specify it to open in a particular area (top-left, bottom-right, etc.), though the app might remember what position it had on its last run.

Also make sure you have the app name right. I don't use xine or amsn, so can't tell, but are you sure that is the command used to launch them?

Finally, make sure you haven't left out the </applications> line at the end of the section, and that all xml code is wholesome. Perhaps you can post here your applications section of your rc.xml file?

First with the bootyful Dandelion theme and now you done fixed this for me too! You doggone genius, go google image search yourself a beer picture, on me :D

Here's what I had in my rc.xml:

```
    <application name="xine"><decor>yes</decor><shade>no</shade><position><x>center</x><y>center</y></position><focus>yes</focus><desktop>5</desktop><head>0</head>
    # specifies xinerama head
    <layer>normal</layer>
    # 'above', 'normal', or 'below'
    <iconic>no</iconic>
    <skip_pager>no</skip_pager>
    <skip_taskbar>no</skip_taskbar>
    <fullscreen>no</fullscreen>
    <maximized>true</maximized>
    # 'Horizontal', 'Vertical' or boolean (yes/no/on/off/true/false)
  </application>
```

That of course did nothing but what you put for xine worked perfectly! Now I'm trying to add an entry for gnome-terminal that will start each one undecorated. I've tried both <decor> and <decorate> with no for each, neither works :(

---

### Post by herbster on 2007-10-27
> **urukrama said:**
> Quite some time ago, I started working on a detailed howto for Openbox, that would help new users setup Openbox (and help me to remember some things). It was meant as a 'howto of howtos' (such arrogance! :p), that would detail how to install Openbox, configure it and use it, giving always plenty of options and links to other howtos on non-Openbox aspects (panels, apps, etc.).

After much neglect, I recently picked it up again and have most of it written now.  It is based on other existing howtos, lots of information from this thread and the openbox site, as well as my own experience.

I have one big gap remaining, though, and that is Openbox on Gutsy. How does it work? Are there some problems in getting it installed or running it? Does the Feisty deb work or do you have to compile from source? What about Obconf and obmenu? Do they work fine? Some feedback on this would be most helpful.

Now that shearn has posted a new howto for Openbox on these forums, I'm not quite sure what to do with mine. :confused: I don't want to have five Openbox howtos floating around on these forums, but mine is very different from his (as it isn't a guide for an 'easy' setup, but aims to be as complete as possible and practical), and the others are a bit outdated. Perhaps I'll post it on a blog or so, and link to it from here.

Anything you'd want to see included? Keep in mind, though, that the guide is meant for relative newcomers to Linux or Ubuntu users with very little technical knowledge, as the experienced users won't need a guide to get them going ;-)

I'm using Gutsy and openbox is as easy as apt-get install openbox, zero issues whatsoever. Works as normally as on Feisty.

And I'd love to see your Openbox "howto," as newcomers to this awesome WM (like myself of not too long) can certainly use reminders and new info alike :)

---

### Post by urukrama on 2007-10-27
I'm glad it worked. :-)

> **herbster said:**
> Now I'm trying to add an entry for gnome-terminal that will start each one undecorated. I've tried both <decor> and <decorate> with no for each, neither works :(

This should work, no?

> <application class="gnome-terminal">
    <decor>no</decor>
  </application>

Thanks for the feedback on Gutsy Openbox.

---

### Post by herbster on 2007-10-28
> **urukrama said:**
> I'm glad it worked. :-)



This should work, no?



Thanks for the feedback on Gutsy Openbox.

```
    <application name="gnome-terminal">
      <decor>no</decor>
    </application>
```

It seems some apps use "class" while others use "name," I've been using trial & error, and that worked for gnome-terminal just fine.

---

### Post by urukrama on 2007-10-28
Good. Thank you for letting me know.

---

### Post by urukrama on 2007-10-28
Hmm. I wanted to install Nitrogen, but just realised it requires gtk 2.10.0 or higher, and dapper only comes with 2.8. Oh well...

---

### Post by herbster on 2007-10-28
Yeah Nitrogen brings about a fun install process... ./configure, apt-get install missing dependency after missing dependency and finally she works ;)

---

### Post by dbbolton on 2007-10-28
> **herbster said:**
> Yeah Nitrogen brings about a fun install process... ./configure, apt-get install missing dependency after missing dependency and finally she works ;)
i wrote them all down for just such an occasion

[http://ubuntuforums.org/showthread.php?t=508848](http://ubuntuforums.org/showthread.php?t=508848)

---

### Post by herbster on 2007-10-28
dbbolton,

Thanks! I bookmarked it for future reinstalls :)

---

### Post by urukrama on 2007-10-28
That is fairly common, herbster, but nitrogen cannot be compiled on Dapper (or so it seems) as it requires packages that are not in the Dapper repos and conflict with packages in the Dapper repos.

Btw, does Obmenu work alright in Gutsy?

Edit: thanks, ddbolton, for that howto. I'll link to it in my Openbox guide (which is getting quite long:-k)

---

### Post by herbster on 2007-10-28
urukrama,

Yup, obmenu works a-ok. Perhaps it's time for an upgrade? :D

BTW, I am looking for the option to set how long the OSD displays for (when switching desktops, alt+tab menu, etc.). It's not in Obconf or in the rc.xml that I can find.

---

### Post by urukrama on 2007-10-28
> **herbster said:**
> Yup, obmenu works a-ok. Perhaps it's time for an upgrade? :D

Some would say, but dapper is still dapper enough for me. I am tempted though, now that I found out the latest Openbox is in Gutsy (I thought it wasn't), but don't feel like reinstalling a system that works very fine. 

> **herbster said:**
> BTW, I am looking for the option to set how long the OSD displays for (when switching desktops, alt+tab menu, etc.). It's not in Obconf or in the rc.xml that I can find.

Look for this section in the rc.xml file:

>  <popupTime>875</popupTime>
<!-- The number of milliseconds to show the popup for when switching
       desktops.  Set this to 0 to disable the popup. -->

Change the number to whatever you want. Hope this helps.

---

### Post by shearn89 on 2007-10-29
> **urukrama said:**
> Quite some time ago, I started working on a detailed howto for Openbox, that would help new users setup Openbox (and help me to remember some things). It was meant as a 'howto of howtos' (such arrogance! :p), that would detail how to install Openbox, configure it and use it, giving always plenty of options and links to other howtos on non-Openbox aspects (panels, apps, etc.).

After much neglect, I recently picked it up again and have most of it written now.  It is based on other existing howtos, lots of information from this thread and the openbox site, as well as my own experience.

I have one big gap remaining, though, and that is Openbox on Gutsy. How does it work? Are there some problems in getting it installed or running it? Does the Feisty deb work or do you have to compile from source? What about Obconf and obmenu? Do they work fine? Some feedback on this would be most helpful.

Now that shearn has posted a new howto for Openbox on these forums, I'm not quite sure what to do with mine. :confused: I don't want to have five Openbox howtos floating around on these forums, but mine is very different from his (as it isn't a guide for an 'easy' setup, but aims to be as complete as possible and practical), and the others are a bit outdated. Perhaps I'll post it on a blog or so, and link to it from here.

Anything you'd want to see included? Keep in mind, though, that the guide is meant for relative newcomers to Linux or Ubuntu users with very little technical knowledge, as the experienced users won't need a guide to get them going ;-)

I think a real Openbox guide is a great idea - as you said, my howto is aimed mostly at Gnome users who want to give it a try, and as such, covers everything from the point of view of someone who's installed normal ubuntu first. A guide that gave some tips on maybe installing from a Server disc is a good idea (if thats where you're heading). If you haven't got anything on the server install, I recently re-did my OB setup with the Server disc, and may be able to help you out. Also, kmandla has some good tips on minimal setups (his blog on wordpress is great).

As to Gutsy, it seems to work fine - i use the .debs from the OB website, as they have some cool features (Obconf now has tabs for font selection etc).
The only thing I've found to be complicated is getting autostart to work properly - sometimes having installed from the repos it doesn't find the .config/openbox/autostar.sh file, and you have to create a session file to launch it. The 3.4.4 deb DOES seem to find that file, which is soooo useful.

---

### Post by urukrama on 2007-10-29
> **shearn89 said:**
> I think a real Openbox guide is a great idea - as you said, my howto is aimed mostly at Gnome users who want to give it a try, and as such, covers everything from the point of view of someone who's installed normal ubuntu first. A guide that gave some tips on maybe installing from a Server disc is a good idea (if thats where you're heading). If you haven't got anything on the server install, I recently re-did my OB setup with the Server disc, and may be able to help you out. Also, kmandla has some good tips on minimal setups (his blog on wordpress is great).

The idea was actually not to include details on how to set up a server install. The guide assumes you have ubuntu running, whether it is a command line install, a full ubuntu installation, or anything in between. What my guide covers is how to setup, configure and use Openbox. It is meant to help new users discover the possibilities in Openbox, and covers all the questions people who are new to Openbox keep asking, as well as plenty of configuration options, additional programs to be used with openbox (just listing them, giving a brief description, and linking to other guides for those apps), etc.

There is plenty of info around how to setup a server/command line install with a graphical environment (Kmandla, aysiu, some howtos on these forums). I have something written myself based on several of these that I use as a guide when I do a server install. Perhaps I should flesh that out a bit and put it up somewhere, linked to the Openbox guide. Hmm..

I don't want to include it in the Openbox guide, as that is getting fairly long, but it might be worth it to link them to each other.

> **shearn89 said:**
> As to Gutsy, it seems to work fine - i use the .debs from the OB website, as they have some cool features (Obconf now has tabs for font selection etc).

I just checked packages.ubuntu.com and it seems Gutsy has the latest versions of both Obconf and Openbox in its repos. You shouldn't see a difference between those and the openbox site ones.

---

### Post by shearn89 on 2007-10-29
> **urukrama said:**
> The idea was actually not to include details on how to set up a server install. The guide assumes you have ubuntu running, whether it is a command line install, a full ubuntu installation, or anything in between. What my guide covers is how to setup, configure and use Openbox. It is meant to help new users discover the possibilities in Openbox, and covers all the questions people who are new to Openbox keep asking, as well as plenty of configuration options, additional programs to be used with openbox (just listing them, giving a brief description, and linking to other guides for those apps), etc.

Cool. When you actually look at everything the rc.xml file can do (application control, keybindings, etc.) there's quite a bit there, and because its all written in xml, any new user would probs struggle with it.

> 
There is plenty of info around how to setup a server/command line install with a graphical environment (Kmandla, aysiu, some howtos on these forums). I have something written myself based on several of these that I use as a guide when I do a server install. Perhaps I should flesh that out a bit and put it up somewhere, linked to the Openbox guide. Hmm..

I don't want to include it in the Openbox guide, as that is getting fairly long, but it might be worth it to link them to each other.


Good idea - its probably not a good idea to put it in the guide, as it would complicate it somewhat. Thinking about it, it wouldn't fit in very easily, as it would be hard to navigate in the forum's thread-style format.

> 
I just checked packages.ubuntu.com and it seems Gutsy has the latest versions of both Obconf and Openbox in its repos. You shouldn't see a difference between those and the openbox site ones.

yeah, i just tried to find the version number using apt, but failed miserably.

---

### Post by herbster on 2007-10-29
> **urukrama said:**
> Some would say, but dapper is still dapper enough for me. I am tempted though, now that I found out the latest Openbox is in Gutsy (I thought it wasn't), but don't feel like reinstalling a system that works very fine. 



Look for this section in the rc.xml file:



Change the number to whatever you want. Hope this helps.

I didn't have that in my rc.xml. I've added it but it's not having any effect, which section is it in? Can you paste the block of code it's with? TIA

---

### Post by yabbadabbadont on 2007-10-30
> **herbster said:**
> I didn't have that in my rc.xml. I've added it but it's not having any effect, which section is it in? Can you paste the block of code it's with? TIA

Which version of Openbox are you using?  It may be that it is only available in newer versions.  It is in 3.4.4, which is the newest.

---

### Post by herbster on 2007-10-30
> **yabbadabbadont said:**
> Which version of Openbox are you using?  It may be that it is only available in newer versions.  It is in 3.4.4, which is the newest.

That's the one I have.

---

### Post by yabbadabbadont on 2007-10-30
Here is the full section from my rc.xml file:
```
  <desktops>
    <!-- this stuff is only used at startup, pagers allow you to change them
       during a session

       these are default values to use when other ones are not already set
       by other applications, or saved in your session

       use obconf if you want to change these without having to log out
       and back in -->
    <number>4</number>
    <firstdesk>1</firstdesk>
    <names>
      <!-- set names up here if you want to, like this:
    <name>desktop 1</name>
    <name>desktop 2</name>
    -->
    </names>
    <popupTime>0</popupTime>
    <!-- The number of milliseconds to show the popup for when switching
       desktops.  Set this to 0 to disable the popup. -->
  </desktops>

```

---

### Post by herbster on 2007-10-30
yabbadabbadont,

Thanks, that did it! I set it to 1500 and it's all good. :)

---

### Post by fuscia on 2007-10-31
well. it's been a while since i last used openbox (in fact, today is my first day since i installed gutsy). things just work, don't they? funny about that. thought i'd celebrate with a screen shot...

---

### Post by herbster on 2007-10-31
Any way to get a volume control in the tray of pypanel ??

---

### Post by fuscia on 2007-10-31
> **herbster said:**
> Any way to get a volume control in the tray of pypanel ??

i've never even thought about it, but i suppose if you could get something in the tray, you could do it that way. i've use knetworkmanager from the tray in pypanel before, so i'm guessing it's possible.

---

### Post by urukrama on 2007-10-31
> **herbster said:**
> Any way to get a volume control in the tray of pypanel ??

You can create a launcher that launches the volume manager of your choice (I like gnome-alsamixer). I don't think you can configure pypanel to raise or lower the volume when you scroll up or down on some part of it, though I'd be glad to know I'm wrong.

You could also create a keyboard shortcut to raise or lower the volume. Here is what I have in my rc.xml at the end of the keyboard section:

> <keybind key="C-Down">
      <action name="Execute">
        <execute>amixer -q set PCM 2- unmute</execute>
      </action>
    </keybind>
    <keybind key="C-Up">
      <action name="Execute">
        <execute>amixer -q set PCM 2+ unmute</execute>
      </action>
    </keybind>

---

### Post by herbster on 2007-10-31
> **urukrama said:**
> You can create a launcher that launches the volume manager of your choice (I like gnome-alsamixer). I don't think you can configure pypanel to raise or lower the volume when you scroll up or down on some part of it, though I'd be glad to know I'm wrong.

You could also create a keyboard shortcut to raise or lower the volume. Here is what I have in my rc.xml at the end of the keyboard section:

Hot damn, gnome alsa mixer rules! I had it on Edgy and forgot about it since it was before I got all my sound working and didn't need it much then. GREAT sound control there.

That's a really neat keybind, I've added it into my rc.xml. Thanks!!

---

### Post by el mariachi on 2007-11-01
Hello fellas! Finally my connection is back!

In my 'away' time I installed Gutsy 64Bit and everything is running smoothly.
Except for the fonts! They look awful. How can I enable hinting? (Pure Openbox as always)

Thanks ;)

---

### Post by yabbadabbadont on 2007-11-01
> **el mariachi said:**
> Hello fellas! Finally my connection is back!

In my 'away' time I installed Gutsy 64Bit and everything is running smoothly.
Except for the fonts! They look awful. How can I enable hinting? (Pure Openbox as always)

Thanks ;)

You didn't specify which fonts, but there is a thread with some tips that have been reported to work here:

[http://ubuntuforums.org/showthread.php?t=588438](http://ubuntuforums.org/showthread.php?t=588438)

---

### Post by yabbadabbadont on 2007-11-02
Does anyone have some mad "sed-fu" skillz that I could borrow?  I've ported the fluxbox-generate-menu script to my own, generate-openbox-menu.  It works fine and has all of the non-icon related configuration options of the original, but I've had to put some nasty kludges (extra for loops and code duplication) into it in order to prevent the inclusion of empty sub-menus.  I've already worked out a way to solve it that isn't kludgey, but it will require rewriting pretty much the whole thing.  (Isn't that way it usually is with code? :lol:)  In the mean time, if there is a simple way to strip empty menus from the menu file, I'd like to hear it.

They would appear in the file like so:
```
<menu id="Some-ID" label="Some-Label">
</menu>
```

---

### Post by shearn89 on 2007-11-02
Could you use something like "if line has "menu" in it, check to see if next line also has "menu"? I'm not that great at coding i'm afraid...

---

### Post by yabbadabbadont on 2007-11-02
> **shearn89 said:**
> Could you use something like "if line has "menu" in it, check to see if next line also has "menu"? I'm not that great at coding i'm afraid...

If I were writing a program, sure, but I'm doing this in a shell script.  ;)

---

### Post by diatribe on 2007-11-08
was wondering if any of you know if this is possible.  in fedora 8 they have an xml file which sets the gnome background as a slideshow, changing the background between 4 image files for sunrise, sunset, day, night.  I was wondering if there was anyway I could duplicate this action in openbox; like I said it is simply an xml file which links to 4 images, it should be able to be done but I am not sure how it would be

---

### Post by urukrama on 2007-11-09
> **diatribe said:**
> was wondering if any of you know if this is possible.  in fedora 8 they have an xml file which sets the gnome background as a slideshow, changing the background between 4 image files for sunrise, sunset, day, night.  I was wondering if there was anyway I could duplicate this action in openbox; like I said it is simply an xml file which links to 4 images, it should be able to be done but I am not sure how it would be

Openbox doesn't manage the desktop or its wallpaper, so you'll need a separate app for that. Feh doesn't do it, neither does nitrogen (please correct me if I'm wrong).

Perhaps [this]("http://www.linuxjournal.com/article/7343") is of some use.

EDIT: seems like you could use feh, if you want to. The Gentoo people have something in their wiki: [Make your background rotate with feh]("http://gentoo-wiki.com/Make_your_background_rotate_with_feh")

---

### Post by urukrama on 2007-11-11
I did a major cleanup on my laptop, and using debfoster, I removed about 400 MB of packages I never used. I must have removed something that obmenu relies on, however, for whenever I try to run it now, I get the following error message:

> Traceback (most recent call last):
  File "/usr/bin/obmenu", line 582, in ?
    app.init()
  File "/usr/bin/obmenu", line 489, in init
    self.menu.loadMenu(self.menu_path)
  File "/usr/lib/python2.4/site-packages/obxml.py", line 153, in loadMenu
    self.dom = xml.dom.minidom.parseString(fil.read())
  File "/usr/lib/python2.4/xml/dom/minidom.py", line 1925, in parseString
    return expatbuilder.parseString(string)
  File "/usr/lib/python2.4/xml/dom/expatbuilder.py", line 940, in parseString
    return builder.parseString(string)
  File "/usr/lib/python2.4/xml/dom/expatbuilder.py", line 223, in parseString
    parser.Parse(string, True)
xml.parsers.expat.ExpatError: not well-formed (invalid token): line 778, column 3


I tried reinstalling obmenu, but the same error remains. I still have python2.4, python-glade and python-gtk (the dependencies listed on the website) installed. Any suggestions?

---

### Post by ynnhoj on 2007-11-11
are you sure the xml in your menu.xml file is all well-formed?  it seems like obmenu is having a problem parsing something..

---

### Post by urukrama on 2007-11-11
ynnhoj, you're a genius! Or I am just stupid! Or both.

Yes, I had a bad section in the xml file (which still displayed my menu correctly, though). Fixed it, and Obmenu works fine again. Thank you.

---

### Post by ynnhoj on 2007-11-11
yep, genius :D

---

### Post by urukrama on 2007-11-12
Hmm. The dockapps have all mysteriously disappeared from [dockapps.org]("http://dockapps.org/")...

---

### Post by el mariachi on 2007-11-14
maintenance? it doesn't make sense dockapps.org without dockapps

---

### Post by shearn89 on 2007-11-15
+1 for maintenance.

---

### Post by cdiem on 2007-11-17
I'm quite new to openbox; I was wondering what you, the experienced users of openbox use as an icon-drawing program. As I could see from howtos, there are two possibilities - rox-filer and idesk. Or am I wrong (maybe there are some more)? Which one is better for everyday use?

---

### Post by fuscia on 2007-11-17
> **cdiem said:**
> I'm quite new to openbox; I was wondering what you, the experienced users of openbox use as an icon-drawing program. As I could see from howtos, there are two possibilities - rox-filer and idesk. Or am I wrong (maybe there are some more)? Which one is better for everyday use?

i haven't tried either one, but i'm someone who doesn't like desktop icons. i much prefer a right-click menu. have you used the right-click menu much in openbox?

---

### Post by cdiem on 2007-11-17
Not yet, actually (I'm new to openbox); but I'm used to saving things on the desktop (from my windows days); I find it convenient, when browsing, for instance. Maybe I'll have to give up this habit :). 
Also, the majority of screenshots I have seen with *box either do not have icons on the desktop, or use one of the abovementioned programs; I was wondering whether these two programs are a necessity for having icons on the desktop, or if there's some alternative.

---

### Post by el mariachi on 2007-11-17
> **cdiem said:**
> Not yet, actually (I'm new to openbox); but I'm used to saving things on the desktop (from my windows days); I find it convenient, when browsing, for instance. Maybe I'll have to give up this habit :). 
Also, the majority of screenshots I have seen with *box either do not have icons on the desktop, or use one of the abovementioned programs; I was wondering whether these two programs are a necessity for having icons on the desktop, or if there's some alternative.
I got used to dump all my stuff in my /home folder and then just pop the right-click menu and choose 'Thunar' ta-daah! there it is: my precious good-for-nothing stuff:KS

I've used Rox-filer in the past but just came back to good old pure OpenBox+Thunar. I've grown used to a clean desktop, and I like it!

---

### Post by fuscia on 2007-11-17
> **cdiem said:**
> Not yet, actually (I'm new to openbox); but I'm used to saving things on the desktop (from my windows days); I find it convenient, when browsing, for instance. Maybe I'll have to give up this habit :). 
Also, the majority of screenshots I have seen with *box either do not have icons on the desktop, or use one of the abovementioned programs; I was wondering whether these two programs are a necessity for having icons on the desktop, or if there's some alternative.

you'd have to use something as openbox won't do it by itself. if you eventually find out you just need to keep doing it that way, xfce and kde both do desktop icons *and* right-click menues. (you can do a pretty light version of kde with kde-core. and, it has been said, earlier in this thread, that xfce is just a 'box' for lazy people.) alternatively, you could have a filemanager in your right-click menu and just set it up to open to the place you keep all the stuff you'd normally find on your desktop.

---

### Post by urukrama on 2007-11-17
Idesk allows you to have launchers on the desktop, but will not show the files and directories you have in your /home/USERNAME/Desktop directory. Rox-filer does that. I don't use either, as the right click menu is much more convenient for me to launch  programs, and I don't like Rox-filer as a file manager. I have become used to not having my files on my desktop (it looks so much cleaner!). I rarely used the desktop icons to open my files that were on the Desktop anyway, so I don't miss much and have gained some aesthetic pleasure. 

Btw, PCMan-FM can also draw the desktop (and display your files and directories), as can Nautilus.

You could also use a pipemenu to show the contents of your Desktop directory in your desktop menu, if you like. [This]("http://david.chalkskeletons.com/scripts/dirlist") is what you'll need (and perhaps [this]("http://icculus.org/openbox/index.php/Help:Menus#Pipe_menus") for help).

EDIT: lol, all three of us at once!

---

### Post by el mariachi on 2007-11-17
> **urukrama said:**
> EDIT: lol, all three of us at once!
Cool!

PCman-Fm looks solid. Still prefer thunar though

---

### Post by fuscia on 2007-11-17
i used pcmanfm, once. it has this weird thing with deleting that is very troubling. if i recall, when i tried to delete one wallpaper from my wallpaper directory, it deleted all of them (fortunately, i had a backup). thunar is my favorite, anyway.

---

### Post by ynnhoj on 2007-11-17
fbdesk can also draw icons on yer desktop, but it might only be able to do launchers (like idesk).  i'm not sure.

---

### Post by urukrama on 2007-11-17
Thunar here too. Simple, beautiful and the custom actions are great (set image as wallpaper with feh, open file as root, open folder as root, open folder with feh, backup files or folders, etc.)

[Fbdesk]("http://fluxbox-wiki.org/index.php/Howto_fbdesk") seems to be similar to idesk, and only supports launchers.

---

### Post by ynnhoj on 2007-11-17
i've found lately that i don't really have much use for file managers.  i sometimes use thunar or mc, but mostly i just use the basic commands (cp, mv, rm, ls, cd, etc...) to browse and manage files from a terminal.  to me it's simpler, and i don't think it's any slower either..

---

### Post by bonzodog on 2007-11-17
I use pcmanfm as a file manager in openbox. Thunar, unfortunately, requires me to install xfce on this system, and I am trying to keep it one WM only.

I couldn't find any other gtk based FM that performs or behaves in the way thunar and pcmanfm(the classic explorer layout - file tree on one side, and dir contents in the other pane) do.

---

### Post by fuscia on 2007-11-17
> **ynnhoj said:**
> i've found lately that i don't really have much use for file managers.  i sometimes use thunar or mc, but mostly i just use the basic commands (cp, mv, rm, ls, cd, etc...) to browse and manage files from a terminal.  to me it's simpler, and i don't think it's any slower either..

what's the command for 'select all, except..."?

---

### Post by el mariachi on 2007-11-17
> **fuscia said:**
> what's the command for 'select all, except..."?
weird, I was going to google for that

---

### Post by ynnhoj on 2007-11-17
the wildcard characters ("*" and "?") usually get the job done, but it depends on the situation i guess.  when it's easier to use thunar, i do; that just doesn't seem to come up too often :)

---

### Post by el mariachi on 2007-11-17
> **ynnhoj said:**
> the wildcard characters ("*" and "?") usually get the job done, but it depends on the situation i guess.  when it's easier to use thunar, i do; that just doesn't seem to come up too often :)
I just like to see the icons :lolflag: I'm a very visual person

---

### Post by yabbadabbadont on 2007-11-17
> **fuscia said:**
> what's the command for 'select all, except..."?

While I don't know it off the top of my head, it is just a matter of learning how to use regular expressions properly.  (A somewhat daunting task, I admit.  :D)

---

### Post by dbbolton on 2007-11-17
is it possible to get a visual system beep in openbox?

---

### Post by herbster on 2007-11-17
^^^ That'd be really good. Titlebar flashes in aMSN window but no visual beep :/

---

### Post by shearn89 on 2007-11-17
Maybe a bubble-showing app? I'm sure i've heard of one somewhere. Or maybe that was an extension for Pidgin. Hmm.

On the icon issue - i tried them for a bit (mostly launchers for frequent apps), but found them to be not that great. I then moved to launchers in a panel (i think at one time i was running 3 different panel apps), and from there to keyboard shortcuts. I've found that since moving to openbox i use the terminal/keyboard a lot more - all my unzipping is cli, i use rtorrent and mpc, raggle for rss feeds. I think the only graphical stuff i use is Firefox (Gran Paradiso actually), and thunar for mounting/unmounting, and for when i want to view thumbnails. Or just get a visual rep of something.

Plus, no icons = more of pretty wallpaper! Something fuscia can tell you lots about...

---

### Post by urukrama on 2007-11-18
> **shearn89 said:**
> since moving to openbox i use the terminal/keyboard a lot more

You can't really equate the two. I am a keyboard user, as I work with texts and my hands are therefore always on the keyboard, but minimize my use of the cli. I know my way around it a little bit, but I just prefer graphical things. Just a side note ;-)

For launchers, I also use shortcuts (with the Windows key + F1, F2, etc), the Openbox menu, or sometimes even apwal (gives you the comfort of launcher buttons, without having to look at them when you don't need them).

Regarding the visual 'beep', I don't think Openbox itself can do this (nothing in the rc.xml file as far as I can tell). All I could find was [this]("http://www.faqs.org/docs/Linux-mini/Visual-Bell.html"). Not sure how helpful that is, though.

---

### Post by shearn89 on 2007-11-19
I guess. But without adding in all the menu shortcuts for yourself, or using something like menumaker, its harder to find all the gui's that are in GNOME. Plus i've switched to a server install, so i've been trying to get rid of as many gnome apps as possible...

---

### Post by johnraff on 2007-11-23
> **urukrama said:**
> Quite some time ago, I started working on a detailed howto for Openbox, that would help new users setup Openbox (and help me to remember some things). It was meant as a 'howto of howtos' (such arrogance! :p), that would detail how to install Openbox, configure it and use it, giving always plenty of options and links to other howtos on non-Openbox aspects (panels, apps, etc.).

After much neglect, I recently picked it up again and have most of it written now.  It is based on other existing howtos, lots of information from this thread and the openbox site, as well as my own experience.

I have one big gap remaining, though, and that is Openbox on Gutsy. How does it work? Are there some problems in getting it installed or running it? Does the Feisty deb work or do you have to compile from source? What about Obconf and obmenu? Do they work fine? Some feedback on this would be most helpful.

Now that shearn has posted a new howto for Openbox on these forums, I'm not quite sure what to do with mine. :confused: I don't want to have five Openbox howtos floating around on these forums, but mine is very different from his (as it isn't a guide for an 'easy' setup, but aims to be as complete as possible and practical), and the others are a bit outdated. Perhaps I'll post it on a blog or so, and link to it from here.

Anything you'd want to see included? Keep in mind, though, that the guide is meant for relative newcomers to Linux or Ubuntu users with very little technical knowledge, as the experienced users won't need a guide to get them going ;-)Urukrama, how's your howto coming on?
It sounds like *exactly* what I'm looking for. :)

---

### Post by herbster on 2007-11-25
Is there a way to align windows? Like in Gnome you hold SHIFT (IIRC) while dragging windows and they snap to edges and one another, something like this function?

---

### Post by urukrama on 2007-11-25
> **johnraff said:**
> Urukrama, how's your howto coming on?
It sounds like *exactly* what I'm looking for. :)

I'm nearly done (after weeks of inactivity!). I'll upload it soon, perhaps even tonight.

---

### Post by Rutabega on 2007-11-25
> **urukrama said:**
> I'm nearly done (after weeks of inactivity!). I'll upload it soon, perhaps even tonight.

Awesome! :KS

---

### Post by urukrama on 2007-11-25
> **Rutabega said:**
> Awesome! :KS

Well, it's done, or at least a first draft is. You can read the thing [here]("http://urukrama.wordpress.com/2007/11/26/an-openbox-guide/") or follow the link in my signature.  I hope it is useful to new users of Openbox.

I've attached the html version also to this message (in a .tar.gz archive; start the guide with index.html). I'll try and upload it to box.net or something similar soon.

Please give me some feedback if you have some.

---

### Post by johnraff on 2007-11-26
Many thanks Urukrama- looks just the job!
Clear instructions and plenty of links to more info. 
 :)

---

### Post by urukrama on 2007-11-26
> **johnraff said:**
> Many thanks Urukrama- looks just the job!
Clear instructions and plenty of links to more info. 
 :)

Thank you.

If you (or anyone else) want to see something aditional discussed, please let me know and I'll consider adding it to the guide. I still have some things that I want to add in the near future. I hope to keep the guide updated and something of a work in progress.

---

### Post by Rutabega on 2007-11-26
> **urukrama said:**
> Thank you.

If you (or anyone else) want to see something aditional discussed, please let me know and I'll consider adding it to the guide. I still have some things that I want to add in the near future. I hope to keep the guide updated and something of a work in progress.

A great and concise guide urukrama! So far the only difficulties that I am experiencing is the following: Shut down, Reboot and Hibernate with administrative privileges, I think this would benefit with an example or needs a bit of clearification, maybe this is just me, but I myself find it hard to get any use from the structure of this step.

I am currently going slowly through the guide, slowly but surely :)

---

### Post by urukrama on 2007-11-26
> **Rutabega said:**
> A great and concise guide urukrama! So far the only difficulties that I am experiencing is the following: Shut down, Reboot and Hibernate with administrative privileges, I think this would benefit with an example or needs a bit of clearification, maybe this is just me, but I myself find it hard to get any use from the structure of this step.

Just add the code given there to your menu.xml file, either manually, through copy and paste (wherever you want it to appear in your menu, but make sure you keep the xml structure intact!), or through obmenu (where 'action name' is Label in obmenu, action in obmenu is 'execute' and what comes after 'execute' goes in the 'execute' box in obmenu.

The structure of the menu code may appear confusing, but is fairly straightforward: <item [...]> and </item> signal the beginning and end of an item. <item label="abc"> shows how it appears in the menu. What comes between <action [...]> and </action> is what type of action this menu item performs, specified in <action name=" ">. Most entries in your menu will be "execute" as they execute certain commands; other options are "reconfigure", "restart" and "exit", used to reconfigure, restart or exit openbox. What appears between <execute> and </execute> is the command that is executed, in this case the commands for shutdown and reboot.

(If you copy it manually make sure to change the {s and }s into <s and >s)

If you add this to your menu as mentioned above, and reconfigure Openbox (in the root-menu), you will have entries in your menu for shut down, reboot, etc. Click on them, and you will be asked your password, after which your system will shut down, reboot, or whatever else you selected.

I hope this helps.

---

### Post by ynnhoj on 2007-11-26
nifty guide, uru.  one thing that would be good is to do away with those curly brackets in your xml examples.  just use [html entities](http://www.w3schools.com/html/html_entities.asp) to show angle brackets on your page.
< would be..```
&lt;
```
..and > would be..```
&gt;
```

---

### Post by johnraff on 2007-11-26
Oh yeh, one more little thing on accessibility: if command lines are longer than the width of the  containing box their ends are hidden. They can still be picked up with a copy+paste though so it's not too serious.
One way to fix it might be to set ```
overflow:visible;
``` in the css for *div.content*.

---

### Post by herbster on 2007-11-27
urukrama,

Great guide! I am having a problem with the shutdown and reboot commands, they don't work. I've copied your guide to the letter and when I click Shutdown or Reboot on the menu, nothing's happening :( Any ideas? :confused:

---

### Post by PurposeOfReason on 2007-11-27
I'm thinking about trying to run openbox on it's own with no gnome as I'm just not going to install it on my new machine. The only things that really matter or that I use from gnome are the settings, volume, and gtk. For volume I'll probably use aumix, though if there is something with an OSD, I'd prefer that. Icons should be able to be changed by finding the default folder and changing it, right? GTK, I should still be able to use gtk-theme-switch?

---

### Post by herbster on 2007-11-27
Yep I use gtk-theme-switch (apt-get install gtk-chtheme). To change icons I use the gnome-appearance-settings thingy.

---

### Post by PurposeOfReason on 2007-11-27
> **herbster said:**
> Yep I use gtk-theme-switch (apt-get install gtk-chtheme). To change icons I use the gnome-appearance-settings thingy.
Is there any other way for the icons as I'm sure if I install the gnome-appearance-settings, it'll install gnome too and I'd like to avoid that. I'm trying to just have openbox so it is light and the battery will last longer.

---

### Post by el mariachi on 2007-11-28
of course there is! in the pure-hardcore-openbox world we do stuff by hand :D
just create a .gtkrc.mine file (put this line in your .gtkrc)
```
include "/home/[username]/.gtkrc.mine"
```

and then, in your new .gtkrc.mine file add this line:
```
gtk-icon-theme-name="[iconfolder'sname]"
```

here's mine, for example:
```
style "MgOpen Mondata"
{
font_name = "MgOpen Cosmetica 7"
}
widget_class "*" style "MgOpen Mondata"
gtk-font-name = "MgOpen Cosmetica 7"

gtk-icon-theme-name="Tango-Style"
gtk-toolbar-style = GTK_TOOLBAR_ICONS
```

---

### Post by urukrama on 2007-11-28
> **PurposeOfReason said:**
> Is there any other way for the icons as I'm sure if I install the gnome-appearance-settings, it'll install gnome too and I'd like to avoid that. I'm trying to just have openbox so it is light and the battery will last longer.

Have a look at the guide linked to in my signature. I'm sure you'll find it useful and many of your questions will be answered there.

To change the volume, you can add the following to your rc.xml file in the keyboard section:

> <keybind key="C-Down">
      <action name="Execute">
        <execute>amixer -q set PCM 2- unmute</execute>
      </action>
    </keybind>
    <keybind key="C-Up">
      <action name="Execute">
        <execute>amixer -q set PCM 2+ unmute</execute>
      </action>
    </keybind>

This allows you to turn up/down the volume with Ctrl+Up/Down arrows. To have a graphical volume manager, try gnome-alsamixer. It has some gnome dependencies though.

---

### Post by PurposeOfReason on 2007-11-28
> **el mariachi said:**
> of course there is! in the pure-hardcore-openbox world we do stuff by hand :D
just create a .gtkrc.mine file (put this line in your .gtkrc)
```
include "/home/[username]/.gtkrc.mine"
```

and then, in your new .gtkrc.mine file add this line:
```
gtk-icon-theme-name="[iconfolder'sname]"
```

here's mine, for example:
```
style "MgOpen Mondata"
{
font_name = "MgOpen Cosmetica 7"
}
widget_class "*" style "MgOpen Mondata"
gtk-font-name = "MgOpen Cosmetica 7"

gtk-icon-theme-name="Tango-Style"
gtk-toolbar-style = GTK_TOOLBAR_ICONS
```
That is exactly what I was looking for, thanks.

---

### Post by herbster on 2007-11-28
> **el mariachi said:**
> of course there is! in the pure-hardcore-openbox world we do stuff by hand :D
just create a .gtkrc.mine file (put this line in your .gtkrc)
```
include "/home/[username]/.gtkrc.mine"
```

and then, in your new .gtkrc.mine file add this line:
```
gtk-icon-theme-name="[iconfolder'sname]"
```

here's mine, for example:
```
style "MgOpen Mondata"
{
font_name = "MgOpen Cosmetica 7"
}
widget_class "*" style "MgOpen Mondata"
gtk-font-name = "MgOpen Cosmetica 7"

gtk-icon-theme-name="Tango-Style"
gtk-toolbar-style = GTK_TOOLBAR_ICONS
```

I put the "include" line at the very bottom of my theme's .gtkrc. For the .gtkrc.mine I have:

```
gtk-icon-theme-name="black-white"
```

and also tried:

```
gtk-icon-theme-name="/home/bobby/.icons/black-white"
```

Doesn't seem to be working, no matter the icon theme name I put in (Human, etc.) :(

---

### Post by diatribe on 2007-11-28
the include line goes in ~/.gtkrc-2.0 not the theme rc

---

### Post by herbster on 2007-11-28
> **diatribe said:**
> the include line goes in ~/.gtkrc-2.0 not the theme rc

Okay, did that, still not changing :(

---

### Post by diatribe on 2007-11-28
and you have both .gtkrc-2.0 and .gtkrc.mine in your home folder?  if so you may need to try restarting x

---

### Post by herbster on 2007-11-28
Yes, and I just logged out and back in, didn't change.

---

### Post by alphane on 2007-11-29
> **urukrama said:**
> Have a look at the guide linked to in my signature. I'm sure you'll find it useful and many of your questions will be answered there.

To change the volume, you can add the following to your rc.xml file in the keyboard section:

This allows you to turn up/down the volume with Ctrl+Up/Down arrows. To have a graphical volume manager, try gnome-alsamixer. It has some gnome dependencies though.

Hey, i've used your vol up/down commands, and they work a treat (previously had MPD volume controls mapped to those keys, this is just a little more universal)

I was wondering though, if you or anyone else knew whether there was a way to link a graphical representation of the volume on the screen at all?

I've had something similar in the past in gnome, and I've seen that Macs have something similar also when they volume up/down?

---

### Post by urukrama on 2007-11-29
> **herbster said:**
> gtk-icon-theme-name="black-white"

Doesn't seem to be working, no matter the icon theme name I put in (Human, etc.) :(

Did you try it with extra spaces? Like this:

> gtk-icon-theme-name = &#8220;nameoficontheme&#8221;

*EDIT: We just reached a 1000 posts on 100 pages!*

---

### Post by PurposeOfReason on 2007-11-29
Okay, almost there with what I was wanting, all but the osd for the volume. I've been trying to get xsod to work but that isn't going as easily as I hoped. I can get it to display things, I just don't know how to make it display the current volume level. Does anyone have any experience with this or have a better way?

---

### Post by samwyse on 2007-11-29
Is it possible to make the window borders larger to make it easier to adjust size, especially from the sides? Just a couple of pixels would be nice.

---

### Post by urukrama on 2007-11-29
> **samwyse said:**
> Is it possible to make the window borders larger to make it easier to adjust size, especially from the sides? Just a couple of pixels would be nice.

Yes. Just edit the themerc file of the theme you are using. You will find it in /home/USERNAME/.themes/THEMENAME/openbox-3/themerc for themes you installed yourself, or /usr/share/themes/THEMENAME/openbox-3/themerc for themes that were installed systemwide (like the themes that come with Openbox).

In that file, there should be a line that reads:

> border.width: 

Change the number behind this line to whatever you want. 'Reconfigure' Openbox (in the root-menu) and the changes should be visible.

You might also be interested in some other parameters in that file. "window.handle.width:" governs the size of the handle, the decoration at the bottom of a window. "window.client.padding.width:" and "window.client.padding.height:" govern a decoration inside the window decoration and borders.

For more info, have a look at Openbox's [theme guide]("http://icculus.org/openbox/index.php/Help:Themes").

---

### Post by herbster on 2007-11-30
> **urukrama said:**
> Did you try it with extra spaces? Like this:

I must be doing something wrong. I have it exactly like that, and what I'm doing is using gtk-chtheme to click on the theme and then hit Apply again. Am I to be doing something else? It's not changing.

---

### Post by fuscia on 2007-11-30
gtk-icon-theme-name= "themename"

there are no spaces other than the one between the equals sign and the first quotation mark.

---

### Post by diatribe on 2007-11-30
herbster check your .gtkrc-2.0 and make sure it is referencing .gtkrc.mine and not .gtkrc-mine, I had that problem before

---

### Post by herbster on 2007-11-30
my .gtkrc.mine:

```
gtk-icon-theme-name= "Aero"
```

.gtkrc-2.0

```
# -- THEME AUTO-WRITTEN DO NOT EDIT
include "/home/bobby/.themes/aura/gtk-2.0/gtkrc"

include "/home/bobby/.gtkrc.mine"

# -- THEME AUTO-WRITTEN DO NOT EDIT
```

I changed the .gtkrc.mine from "Human" to "Aero" and a few other icon themes I have, I run gtk-chtheme and click on aura theme, Apply, icons do not change :confused:

---

### Post by fuscia on 2007-11-30
> **herbster said:**
> my .gtkrc.mine:

```
gtk-icon-theme-name= "Aero"
```

.gtkrc-2.0

```
# -- THEME AUTO-WRITTEN DO NOT EDIT
include "/home/bobby/.themes/aura/gtk-2.0/gtkrc"

include "/home/bobby/.gtkrc.mine"

# -- THEME AUTO-WRITTEN DO NOT EDIT
```

I changed the .gtkrc.mine from "Human" to "Aero" and a few other icon themes I have, I run gtk-chtheme and click on aura theme, Apply, icons do not change :confused:

i had problems with icon themes that only had .svg files (one folder in the icon directory labeled 'scalable').

have you tried gtk-theme-switch2?

---

### Post by herbster on 2007-11-30
Yup, I tried gtk-theme-switch and switch2. This is really baffling me brains.

---

### Post by fuscia on 2007-11-30
> **herbster said:**
> Yup, I tried gtk-theme-switch and switch2. This is really baffling me brains.

try checking the spelling and case of the icon theme name. if i recall, i had a theme called "areo", not "Aero". (they could be two different themes, though.)

---

### Post by urukrama on 2007-11-30
I see what you did wrong. The file should not be .gtkrc.mine, but .gtkrc-2.0.mine.

Change the path in the gtkrc-2.0.mine file and create a .gtkrc-2.0.mine file with the details as you had them. That should work.

---

### Post by herbster on 2007-11-30
Okay, I've made the changes but am noticing that my .gtkrc-2.0 isn't behaving-- it keeps changing the include line back to .gtkrc.mine when I open it a minute after having changed it. How can I stop it from doing that?

---

### Post by el mariachi on 2007-11-30
> **urukrama said:**
> I see what you did wrong. The file should not be .gtkrc.mine, but .gtkrc-2.0.mine.

Change the path in the gtkrc-2.0.mine file and create a .gtkrc-2.0.mine file with the details as you had them. That should work.

I use .gtkrc.mine and everything works like charm

---

### Post by urukrama on 2007-11-30
Hmm. Interesting.

EDIT: Are you sure that the name you give matches the name of the folder your icons are in? Or that the icon's folder has the right permissions for you to access it?

---

### Post by urukrama on 2007-12-02
> **PurposeOfReason said:**
> Okay, almost there with what I was wanting, all but the osd for the volume. I've been trying to get xsod to work but that isn't going as easily as I hoped. I can get it to display things, I just don't know how to make it display the current volume level. Does anyone have any experience with this or have a better way?

Have you tried osdsh? I've just found [this]("http://ubuntuforums.org/showthread.php?t=617812") Fluxbox howto that mentions it (about half way down). Perhaps you can get it to work fine in Openbox as well. 

I haven't tried it yet, but will experiment with it later. I might add it to my guide as well.

---

### Post by cknight on 2007-12-02
> **urukrama said:**
> Have you tried osdsh? I've just found [this]("http://ubuntuforums.org/showthread.php?t=617812") Fluxbox howto that mentions it (about half way down). Perhaps you can get it to work fine in Openbox as well. 

I haven't tried it yet, but will experiment with it later. I might add it to my guide as well.

I can't think of any reason osdsh wouldn't work with openbox.  It's a great little program.  If anyone does try this, please let me know if you run into any problems using it on Gutsy.  The various daemons  (volume, battery, etc) works great on my edgy desktop but seems to send my cpu to 100% if I use it on my Gutsy laptop.  The string output works without issue which still has its advantages, but I'm curious if this is just me or an issue with Gutsy.

If you do run into problems with the volume daemon hitting 100% you could parse the output from the amixer to (87% in this example):
```
osdctl -b volume,87
```
for a dynamically generated volume OSD.  Parsing isn't my forte, however, so you're on your own to get the volume level number.

---

### Post by urukrama on 2007-12-02
Thank you very much, cknight. This is a great tool. I don't run Gutsy (still on Dapper), so I can't help you with that. Great guide as well -- good info and very well written and structured. I have plenty of new ideas to play with now. :D

---

### Post by alphane on 2007-12-03
I've installed and been playing with the osdsh tool, and I can confirm that a) it works rather well, but b) I do experience the 100% CPU issue on gutsy after 5mins or so.

Anyone have any clues as to another command where I can read the amixer volume from?  Having looked through the output of amixer --help, I am completely baffled.

---

### Post by alphane on 2007-12-03
Have just stubled upon a post by pointone in this thread [http://ubuntuforums.org/showthread.php?t=165073&highlight=amixer+volume+level]("http://ubuntuforums.org/showthread.php?t=165073&highlight=amixer+volume+level")

Where he offers up these commands: 
```

sudo /etc/acpi/volupbtn.sh
sudo /etc/acpi/voldownbtn.shl

```

Now, THIS is more what I'm looking for.

Going to try and marry up a keymapping to do both up the volume, and activate these controls...

EDIT: Okay, given up after another hour.  Not sure how to invoke these commands without sudo, any clues anyone?  I've realised that using these also actually controls the volume, not quite sure how I didn't realise this.  So if someone can help me figure out how to bind these commands to keys, I'll be forever greatful!

---

### Post by cknight on 2007-12-04
> **alphane said:**
> Have just stubled upon a post by pointone in this thread [http://ubuntuforums.org/showthread.php?t=165073&highlight=amixer+volume+level]("http://ubuntuforums.org/showthread.php?t=165073&highlight=amixer+volume+level")

Where he offers up these commands: 
```

sudo /etc/acpi/volupbtn.sh
sudo /etc/acpi/voldownbtn.shl

```

OK, so I couldn't leave this alone and applied my master man-page skills to hack this together.  It bypasses the osdsh volume daemon and just uses plain old string output.  Here's the volume up command:
```
osdctl -b "Master Volume",$(amixer sset Master,0 5%+|grep "Front Left:"|cut -d "[" -f2|cut -d "%" -f1)
```

And corresponding volume down command:
```
osdctl -b "Master Volume",$(amixer sset Master,0 5%-|grep "Front Left:"|cut -d "[" -f2|cut -d "%" -f1)
```

Of course, don't forget that you need the 'osdsh' daemon running in the background.

Alternatively, to use the above acpi scripts as root without needing a password, you could edit your sudo users file to set an exception for those scripts such that those scripts are not prompted for a password when run against sudo.  See [http://ubuntuforums.org/showpost.php?p=3329897&postcount=40]("http://ubuntuforums.org/showpost.php?p=3329897&postcount=40") for more details.

---

### Post by diatribe on 2007-12-05
> **alphane said:**
> Have just stubled upon a post by pointone in this thread [http://ubuntuforums.org/showthread.php?t=165073&highlight=amixer+volume+level]("http://ubuntuforums.org/showthread.php?t=165073&highlight=amixer+volume+level")

Where he offers up these commands: 
```

sudo /etc/acpi/volupbtn.sh
sudo /etc/acpi/voldownbtn.shl

```

Now, THIS is more what I'm looking for.

Going to try and marry up a keymapping to do both up the volume, and activate these controls...

EDIT: Okay, given up after another hour.  Not sure how to invoke these commands without sudo, any clues anyone?  I've realised that using these also actually controls the volume, not quite sure how I didn't realise this.  So if someone can help me figure out how to bind these commands to keys, I'll be forever greatful!

use xbindkeys

---

### Post by shearn89 on 2007-12-06
Hey - back online after an arch install... took a while, but loving the lightweighted-ness.

For the icon issue, i wrote a script to do exactly this, change the theme via the command line. I have the icon theme set in .gtkrc.mine, and it all works perfectly. I think. It basically lists the folders in ~/.icons, and then you choose one to set as the theme. Feel free to hack/whatever.

```

#!/bin/bash

#NB - icon themes must be folders in ~/.icons
CHOSEN= cat ~/.gtkrc.mine
echo $CHOSEN
ls $HOME/.icons
echo -n "choose your theme:"
read -e CHOSEN
rm ~/.gtkrc.mine
echo "gtk-icon-theme-name = "\"$CHOSEN\""" > $HOME/.gtkrc.mine
echo "New theme file:"
cat ~/.gtkrc.mine

```

---

### Post by el mariachi on 2007-12-07
Thanks the script works, but I stupidly forgot that my fonts were set in .gtkrc.mine too... what lines do I have to add to change my fonts?

---

### Post by yabbadabbadont on 2007-12-07
> **el mariachi said:**
> Thanks the script works, but I stupidly forgot that my fonts were set in .gtkrc.mine too... what lines do I have to add to change my fonts?

```
style "user-font" {
        font_name = "Verdana 10"
}

widget_class "*" style "user-font"

gtk-font-name="Verdana 10"

```

I only set that nasty font, just so that I could provide the correct code for you.  I hope that you appreciate it.  :D

---

### Post by el mariachi on 2007-12-07
thank you buddy :D

---

### Post by shearn89 on 2007-12-08
oh yeah - i forgot that it "rm"s the file... I should find a way to change that. Maybe if i just mved it.... <goes off to tinker with code>

EDIT: until i find a way to merge it nicely, heres v1.1:
```

#!/bin/bash

#NB - icon themes must be folders in ~/.icons
CHOSEN= cat ~/.gtkrc.mine
echo $CHOSEN
ls $HOME/.icons
echo -n "choose your theme:"
read -e CHOSEN
mv ~/.gtkrc.mine ~/.gtkrc.old
echo "gtk-icon-theme-name = "\"$CHOSEN\""" > $HOME/.gtkrc.mine
echo "New theme file:"
cat ~/.gtkrc.mine
echo "Any other settings from the original file will be in .gtkrc.old, and will need manually merging."

```

---

### Post by yabbadabbadont on 2007-12-08
@shearn89:
```
/home/daffy $ cat .gtkrc.mine 
#Test line 1
#Test line 2
gtk-icon-theme-name = "black-white"
#Test line 3
#Test line 4
/home/daffy $ grep -vi "gtk-icon-theme-name" .gtkrc.mine 
#Test line 1
#Test line 2
#Test line 3
#Test line 4
```
The rest is left as an exercise for the student.  ;)

---

### Post by shearn89 on 2007-12-09
> **yabbadabbadont said:**
> @shearn89:
```
/home/daffy $ cat .gtkrc.mine 
#Test line 1
#Test line 2
gtk-icon-theme-name = "black-white"
#Test line 3
#Test line 4
/home/daffy $ grep -vi "gtk-icon-theme-name" .gtkrc.mine 
#Test line 1
#Test line 2
#Test line 3
#Test line 4
```
The rest is left as an exercise for the student.  ;)

hmmm.. i take it this is a challenge for me to figure out the other lines?

---

### Post by yabbadabbadont on 2007-12-09
> **shearn89 said:**
> hmmm.. i take it this is a challenge for me to figure out the other lines?
I was bored, so here you go:
```
#!/bin/bash

#NB - icon themes must be folders in ~/.icons
CHOSEN=$(grep -i gtk-icon-theme-name ~/.gtkrc.mine | cut -d "=" -f 2 | sed 's/^ *//')
echo $CHOSEN
ls $HOME/.icons
echo -n "choose your theme:"
read -e CHOSEN
mv ~/.gtkrc.mine ~/.gtkrc.old
grep -vi gtk-icon-theme-name ~/.gtkrc.old > ~/.gtkrc.mine
echo "gtk-icon-theme-name = "\"$CHOSEN\""" >> ~/.gtkrc.mine
echo "New theme file:"
cat ~/.gtkrc.mine

```

---

### Post by shearn89 on 2007-12-10
sweet. I think i would have had to trawl many man pages/google results to get all the "grep | cut " stuff...

---

### Post by urukrama on 2007-12-22
Does anyone know where I could get the source code for netwmpager? It is a small pager app that I saw on the Arch forums (on [this]("http://bbs.archlinux.org/viewtopic.php?id=40487&p=13") page). Its [website]("http://onion.dynserv.net/~timo/") is down, so I can't grab the source code, though it is in the Arch and Gentoo repos (but not Debian, it seems).

---

### Post by BattlePanic on 2007-12-23
Does Openbox have a setting to disable 'show window contents while dragging'

I remember WinXP having this display feature and it was quite helpful for older systems that have a hard time displaying a window while it was being moved around the screen.

I searched the forums but the answers I found are for Metacity/GNOME.

---

### Post by shearn89 on 2007-12-24
> **urukrama said:**
> Does anyone know where I could get the source code for netwmpager? It is a small pager app that I saw on the Arch forums (on [this]("http://bbs.archlinux.org/viewtopic.php?id=40487&p=13") page). Its [website]("http://onion.dynserv.net/~timo/") is down, so I can't grab the source code, though it is in the Arch and Gentoo repos (but not Debian, it seems).
i'll see if i can grab the source from the arch repos for you. hold on a mo.

EDIT: Can't get the source, as that involoves downloading from they're website. I got the archpkg for you, which seems to be the binary that is needed. If you untar it (it doesn't have its own folder), the only files are a config example and the executable. See if it works...

---

### Post by jviscosi on 2007-12-24
> **urukrama said:**
> Does anyone know where I could get the source code for netwmpager? It is a small pager app that I saw on the Arch forums (on [this]("http://bbs.archlinux.org/viewtopic.php?id=40487&p=13") page). Its [website]("http://onion.dynserv.net/%7Etimo/") is down, so I can't grab the source code, though it is in the Arch and Gentoo repos (but not Debian, it seems).

Is [this]("http://ftp.osuosl.org/pub/gentoo/distfiles/netwmpager-1.11.tar.bz2") it?

---

### Post by K.Mandla on 2007-12-25
In hopes of better organizing all the window manager and desktop environment threads, this has been shifted to Desktop Environments.

---

### Post by urukrama on 2007-12-25
> **jviscosi said:**
> Is [this]("http://ftp.osuosl.org/pub/gentoo/distfiles/netwmpager-1.11.tar.bz2") it?

Yes. Thank you very much.

---

### Post by urukrama on 2007-12-25
> **BattlePanic said:**
> Does Openbox have a setting to disable 'show window contents while dragging'

I remember WinXP having this display feature and it was quite helpful for older systems that have a hard time displaying a window while it was being moved around the screen.

I searched the forums but the answers I found are for Metacity/GNOME.

As far as I know, it doesnt. It does have the option to not show the window contents while resizing the window. Look for this in your rc.xml (it comes after the desktops section):

```
 <resize>
    <drawContents>yes</drawContents>
    <popupShow>Never</popupShow>
    <popupPosition>Center</popupPosition>
  </resize>
```

Change the 'yes' to 'no' and your window contents will remain the same while you resize.

---

### Post by vasiliymeshko on 2008-01-04
Is there a way to add apps that open in terminal to the menu?

---

### Post by jseiser on 2008-01-04
yes,

say rtorrent. urxvt -e rtorrent

so its  'terminal' '-e' 'program'

---

### Post by vasiliymeshko on 2008-01-04
> **jseiser said:**
> yes,

say rtorrent. urxvt -e rtorrent

so its  'terminal' '-e' 'program'

Thanks, that's what I was looking for.

---

### Post by urukrama on 2008-01-06
Openbox 3.4.5 is released. See [here]("http://icculus.org/openbox/index.php/Openbox:News#Openbox_3.4.5_released") for the announcement.

Nothing big; mainly bug fixes. Here is the changelog:
> Added Hungarian translation 
Updated Finnish, Russian, German and French translations 
Fixed some very minor memory leaks 
Hide the desktop popup when showing the focus popup 
Fix a crash when trying to access the More... menu of client-list-combined-menu 
Fix the coordinate popup only showing up on the first monitor in xinerama 
Add --exit to exit the currently running openbox instance

Download [here]("http://icculus.org/openbox/index.php/Openbox:Download") (no deb yet, so you'll have to compile from source on Ubuntu).

---

### Post by ynnhoj on 2008-01-06
nice to see that the openbox devs are staying on top of things.  i'm not sure that i've used it since.. maybe 3.4.1-ish.  once the update hits arch's repositories, maybe i'll install it again.

---

### Post by Patogen on 2008-01-18
Is it possible to use openbox amiga style? Instead of using a taskbar etc that you can let the open applications be icons on the desktop? I really like that feature from amiga and I don't want to run amiwm just for that ;)

---

### Post by urukrama on 2008-01-18
Openbox itself cannot do so, but you could use other applications to do so in Openbox, such as Rox-filer, or (the ugly) dfm. I'm not sure what other applications are available that have such a feature.

---

### Post by PurposeOfReason on 2008-01-21
I'm using openbox again, but I'm having trouble with window positions. In my rc.xml I have the following:
```
<applications>
    <application class="Minefield">
      <position>
        <x>10</x>
        <y>10</y>
      </position>
    </application>
    <application class="OpenOffice.org 2.3">
      <position>
        <x>10</x>
        <y>10</y>
      </position>
    </application>
    <application class="Gmrun">
      <position>
        <x>center</x>
        <y>center</y>
      </position>
    </application>
  </applications>
```

But only gmrun follows the format.

---

### Post by urukrama on 2008-01-22
Are you sure you have the right application class for Minefield and OpenOffice? You can find out when you type "xpropr WM_CLASS" in a terminal and then click on the application. You will get something of the type 
> WM_CLASS(STRING) = "mousepad", "Mousepad"

The first is the application name, the second the application class.

I generally use the application name (with <application name=" "> in the rc.xml file).

Other than that, I'm not sure what could be wrong. I don't have minefield or OO 2.3 installed, so I can't check whether the class is correct. But the syntax is fine.

---

### Post by PurposeOfReason on 2008-01-22
That's the class for both, I used that command. I'll try name I guess.

---

### Post by Gigamo on 2008-01-22
Just hopping in here, but is it possible to remove the menu header in the openbox right click menu? The title that says "Openbox", if you know what I mean.

Thanks

---

### Post by urukrama on 2008-01-22
Yes. If you have a header, you should have a <separator label="Openbox 3"/> line at the top of your menu.xml file. Remove that, and you'll have no header. If you like headers for submenus, you can add a line like that at the top of each submenu.

---

### Post by Gigamo on 2008-01-22
> **urukrama said:**
> Yes. If you have a header, you should have a <separator label="Openbox 3"/> line at the top of your menu.xml file. Remove that, and you'll have no header. If you like headers for submenus, you can add a line like that at the top of each submenu.

Thanks!

---

### Post by PurposeOfReason on 2008-01-22
Going out on a limb here.

Is there a program that is a mix of pypanel and visibility. What I'm looking for is basically this (poor) drawing.

--------   ---

The fist line is pypanel which would list workspace name, windowlist, clock. Then a break. The second line being like that notification area of pypanel. I realize I could do that all in one, but it's more just for looks. If I could run a second pypanel, that works.

---

### Post by urukrama on 2008-01-22
Have you tried trayer or stalonetray for a system tray (and using pypanel or another panel for everything else)?

---

### Post by Gigamo on 2008-01-22
Trayer could work really well for that.

---

### Post by PurposeOfReason on 2008-01-22
Trayer seems to be the best choice. I can't find any config files for it though (on my machine, man page, or on the internet) will I have to run it like so each time?
trayer --expand true --widthtype request --transparent true --alpha 255 --edge top --align right &

---

### Post by Gigamo on 2008-01-22
> **PurposeOfReason said:**
> Trayer seems to be the best choice. I can't find any config files for it though (on my machine, man page, or on the internet) will I have to run it like so each time?
trayer --expand true --widthtype request --transparent true --alpha 255 --edge top --align right &

Yep, that's what I do.

---

### Post by PurposeOfReason on 2008-01-22
Thanks. I got that to work though neither can match the look of my pypanel so it looks bad? Is there a possibly way to run two pypanels?

---

### Post by Gigamo on 2008-01-22
I have no idea about that. You could try using Tint task manager + pypanel though... I dunno.

---

### Post by ynnhoj on 2008-01-23
maybe you could use xfce4-panel?  you ought to be able to setup multiple panels (i think?);  add whatever plugins you want to each, and you're ready to go.  i'm not sure how customizable the fonts and colours will be though.

or.. have you tried fbpanel?  or maybe.. rspanel?  i think rspanel has a page on googlecode, but i'm not sure if it's still an active project.

---

### Post by PurposeOfReason on 2008-01-23
Going for a new approach. Just have pypanel in the top right as a clock a tray. But is there a way to make it so the clock is aligned right instead of getting pushed around by how many things are in the notification area?

---

### Post by urukrama on 2008-02-03
Openbox 3.4.6 is out (these guys work hard!). Here is the changelog:

> Added Basque translation 
Updated French, Vietnamese German, Simplified Chinese, Russian, Portuguese, Brasilian Portuguese, Norwegian, and Finnish translations 
New Clearlooks theme, updated by David Barr 
Updated the previous Clearlooks theme, and renamed it to Clearlooks-3.4 
Allow dialog type windows to go fullscreen (Fixes Kpdf) 
Remove the extraneous top border for undecorated windows while maximized 
Fixes for keyboard modifiers (Alt-tab dialog getting stuck on screen for some users) 
Automatically catch changes to the keyboard map and reconfigure the key bindings on the fly 
Fix focus moving incorrectly sometimes with focus under mouse enabled 
Make default configuration focus the desktop when you right click 
Add the <bar> and <raise> options for all window cycling actions, allowing you to have your target window temporarily raised above all others, and to turn the focus target indicator bar off 
Improve the LastDesktop action to not remember desktops you skipped across 
Ignore mouse clicks that are made on override-redirect (unmanaged) windows 
When opening a menu with a key binding, don't use the key binding to run something in the menu 
Add a <monitor> option for window placement, which gives you the option to place new windows on the active monitor, or the monitor where the mouse is, instead of on any monitor (for xinerama multihead setups) 
Add options for placing the window move/resize coordinate popu window in a fixed position on screen, rather than relative to the window being moved or resized 
Prevent the dock from auto-hiding completely offscreen if the theme has no borders for it 
New icon 
Fix race condition when running things that want to grab the keyboard (e.g. gnome-panel-control --main-menu) 
When dialog windows ask to not appear in the taskbar, still give them focus in normal ways (fixes new GNOME session logout dialogs) 
Fix bug with resizing corners on certain parts of the window frame 
Ping applications to tell when they are running or have become frozen. Show a [Not Responding] message in the title bar of windows which are frozen. 
When closing a window which is [Not Responding], kill the window's process if it is running on the same machine as Openbox. Otherwise, just disconnect the window from the X display. A second attempt to close a [Not Responding] window will kill it forcefully (kill -9). 
Fixes for internal timers 
Add a <wmclass> option for the execute action's startup-notification. This lets you tell Openbox that the application will map a window with the specified class - for applications that do not support startup-notification natively. 
Fix for empty dock taking up space onscreen after a reconfigure 
Reduce Openbox's additional memory footprint per-window and per-menu 
Faster horizontal gradient rendering 
Don't deiconify windows that aren't allowed to be directly iconified on restart (eg toolbars), as they can be iconified by other means 
Improve support for fullscreen windows in xinerama (TwinView) and multiple-screen setups 
Add a --config-file command line option, to specify an alternate configuration file path

Obconf has also been upgraded to 2.0.3. Here is the changelog:

> Added Norwegian translation 
Added Turkish translation 
Updated Traditional Czech, Chinese, Italian, and Swedish translations 
Add support for the desktop warping option 
Add support for showing the popup notification when changing desktops 
Better build support for Max OSX platform (no --export-dynamic) 
Major layout changes 
Add support for putting the move/resize popup in a fixed position on screen 
Add support for the <monitor> window placement option 
New icon by Myles Green 
Show an error when the configuration file is not valid, so it doesn't get destroyed by ObConf 
Add a --config-file option to specify an alternate configuration file. 
Auto-load the same configuration as Openbox is using, if Openbox was run with --config-file

You can download both [here]("http://icculus.org/openbox/index.php/Openbox:Download"). There is a Debian/Ubuntu deb available.

---

### Post by urukrama on 2008-02-06
And Openbox 3.4.6.1 is out...

It is a small bug fix release, but has some added features. My favourite (and the only reason why I upgraded) is that you can remove the "Manage Desktops" from the combined-client-list-menu (add <manageDesktops>no</manageDesktops> to the <menu> section of your rc.xml file). Here is the changelog:

> Updated Clearlooks theme 
Add the force="yes/no" option for the per-app settings' <position> tag 
Raise and focus modal children and their direct parents together, improved usability with direct modal transient windows 
Fix crash when using <raise> for NextWindow and there are no windows to move focus to 
Add the <manageDesktops> option in the rc.xml <menu> section, which toggles the "Manage Desktops" section appearing in the combined-client-list-menu 
Fix for menu headers showing the wrong text 
Fix for the <focusLast> behavior 
Treat modal direct children as one window with their parent consistently

You can download it [here]("http://icculus.org/openbox/index.php/Openbox:Download#Openbox"). There is deb for Ubuntu available.

---

### Post by ejket on 2008-02-07
I've been having fun with openbox since I've been home sick for a few days and have nothing better to do than get into trouble.  It's nice to get back to the metal again with something light and fast, and I think I'll stick with it for a while now that it's all set up.

Anyway, everything works pretty well, but is there really nothing better than feh to set backgrounds with?  My gripe is that it doesn't actually "scale" (which implies that the aspect ratio is maintained).  It ... "munges" the image when its aspect ratio differs from my monitor.  Almost all of my favorite images were not intended to be wallpaper, so that's a problem.  If I use "feh -bg-center" I'm usually either stuck with a nice image floating in a sea of black or one that's cut off on one edge or the other.

Any ideas?  Gnome can do it nicely -- there must be something else that can.

---

### Post by yabbadabbadont on 2008-02-07
> **ejket said:**
> I've been having fun with openbox since I've been home sick for a few days and have nothing better to do than get into trouble.  It's nice to get back to the metal again with something light and fast, and I think I'll stick with it for a while now that it's all set up.

Anyway, everything works pretty well, but is there really nothing better than feh to set backgrounds with?  My gripe is that it doesn't actually "scale" (which implies that the aspect ratio is maintained).  It ... "munges" the image when its aspect ratio differs from my monitor.  Almost all of my favorite images were not intended to be wallpaper, so that's a problem.  If I use "feh -bg-center" I'm usually either stuck with a nice image floating in a sea of black or one that's cut off on one edge or the other.

Any ideas?  Gnome can do it nicely -- there must be something else that can.
Install eterm.  (It may be listed as Eterm in the repositories)  Then use Esetroot to set your background.  ```
Esetroot -bgcolor black -fit YourWallpaperHere
```  In my example, if the wallpaper doesn't cover the entire screen when scaled (preserving aspect ratio), it will fill in the extra space with black.  ```
/home/daffy $ Esetroot
Esetroot [-display <display_name>] [-bgcolor <color>] [-scale] [-center] [-fit] [-mirror] pixmap
         Short options are also recognized (-d, -b, -s, -c, -f, and -m)

```

---

### Post by ejket on 2008-02-07
> **yabbadabbadont said:**
> Install eterm.  (It may be listed as Eterm in the repositories)  Then use Esetroot to set your background.

Yes, I used that back in my e16 days, and I did think of it.  I was hoping there was something sexier and more feature-rich around now.  There are some nice things you can do with feh, it's just that the lack of proper scaling is a pain ... and then there's the black background.

For some reason I thought that "display" could do what I wanted (it's part of imagemagick), but all my fiddling with that so far has been more darkly amusing than anything.

I also tried turning images into proper wallpapers with the gimp, and of course that works but it's a headache for someone who changes wallpaper very often.

Anyway, I agree that esetroot is worth a shot.  I guess I'll have to reset the bg in an .xinitrc file unless I can pipe the output to a file, though.

Thanks for the suggestion :)

---

### Post by Mark76 on 2008-02-07
I tried to add shutdown functionality to my openbox menu but nothing seems to have changed

---

### Post by urukrama on 2008-02-07
> **ejket said:**
> I was hoping there was something sexier and more feature-rich around now.  There are some nice things you can do with feh, it's just that the lack of proper scaling is a pain ... and then there's the black background.

Try hsetroot or habak. Both allow you to set mutliple images, with different coloured backgrounds, and much more. See [here]("http://urukrama.wordpress.com/2007/12/05/desktop-backgrounds-in-window-managers/") for more details (and other options).

---

### Post by urukrama on 2008-02-07
> **Mark76 said:**
> I tried to add shutdown functionality to my openbox menu but nothing seems to have changed

Sorry I haven't replied to your pm yet. Here is what you do (in Obmenu):

For a shut down entry, use the following command in Obmenu in the 'Execute' box: 
```
gksudo shutdown -h now
```

For a reboot entry, use this command:
```
gksudo shutdown -r now
```

Note this will ask you for your sudo password before shutting down.

---

### Post by ejket on 2008-02-07
> **urukrama said:**
> Try hsetroot or habak. Both allow you to set mutliple images, with different coloured backgrounds, and much more. See [here]("http://urukrama.wordpress.com/2007/12/05/desktop-backgrounds-in-window-managers/") for more details (and other options).

I downloaded hsetroot, and it was nice that it came as source, since now -- even though my C is rusty -- I can play with the code :)

It does proper scaling, though I haven't been able to make the colors work yet.  For some reason when I use a hex color, ie #303030, which is the format it expects, I keep getting a 'Missing color' error.

The immediate scaling problem is solved, though.  Too bad feh couldn't add that bit of code, since it also uses Imlib2 ... if I were more ambitious, I'd add it in myself.

Anyway, thanks, and thanks for all the other good stuff on your blog :)

Openbox is like a breath of fresh air.  I loved BB long ago, and there's a sort of nostalgia to it all.  Not to mention it's nice and fast.

---

### Post by ejket on 2008-02-07
> **urukrama said:**
> Sorry I haven't replied to your pm yet. Here is what you do (in Obmenu):

For a shut down entry, use the following command in Obmenu in the 'Execute' box: 
```
gksudo shutdown -h now
```

For a reboot entry, use this command:
```
gksudo shutdown -r now
```

Note this will ask you for your sudo password before shutting down.

You really should quote commands like that when they're going to be exec'd:

```
gksudo 'shutdown -h now'
```
```
gksudo 'shutdown -r now'
```

There's no other reliable way to parse which prog the args belong to.

---

### Post by urukrama on 2008-02-07
> **ejket said:**
> It does proper scaling, though I haven't been able to make the colors work yet. For some reason when I use a hex color, ie #303030, which is the format it expects, I keep getting a 'Missing color' error.

Try to put the colour code in parenthesis, e.g. '#303030'.

> **ejket said:**
> There's no other reliable way to parse which prog the args belong to.

I've never had any problem with it.

---

### Post by ejket on 2008-02-07
> **urukrama said:**
> Try to put the colour code in parenthesis, e.g. '#303030'.

D'oh!  Hoisted by my own petard, lol.  It shouldn't be necessary to quote this, but it works when you do.  I was going to try that next, honest :)

> **urukrama said:**
> > There's no other reliable way to parse which prog the args belong to.I've never had any problem with it.

Like I say, the parsing isn't reliable without the quoting.  It may work for you, but it didn't for me, and likely that's the problem Mark76 is having.

It's the same when you exec from within a C prog -- if it's a string, and you don't quote it, the results are undetermined, which is never a good thing.

**edit:**

For example, this is what I get when I skip the quotes:

```
tale@eyolf:~$ gksudo /sbin/shutdown -r reboot
gksudo: invalid option -- r
```

---

### Post by Mark76 on 2008-02-07
Just added the shutdown function to my OB menu, tried it and the computer shut down without even asking for my password.

Does that mean that "ALL   ALL=NOPASSWD:/sbin/shutdown" overrides gksudo?

Oh, and while we're about it, how about the log out and change user commands? :)

---

### Post by ejket on 2008-02-07
> **Mark76 said:**
> Just added the shutdown function to my OB menu, tried it and the computer shut down without even asking for my password.

Does that mean that "ALL   ALL=NOPASSWD:/sbin/shutdown" overrides gksudo?

Yes, but only when you run /sbin/shutdown.

---

### Post by urukrama on 2008-02-07
> **Mark76 said:**
> Just added the shutdown function to my OB menu, tried it and the computer shut down without even asking for my password.

Does that mean that "ALL   ALL=NOPASSWD:/sbin/shutdown" overrides gksudo?

Oh, and while we're about it, how about the log out and change user commands? :)

That does indeed override gksudo (as well as sudo) for the command 'shutdown'.

To log out, you would use the 'Exit' command in Openbox. In Obmenu, select 'Exit' in the Action menu for your menu entry (by default it shows 'Execute'). If you use Openbox 3.4.5 or higher, you can exit openbox also with the following command:

```
openbox --exit
```

You can not really switch users like you can in Gnome. You will need to log out and log in as a different user.

---

### Post by Mark76 on 2008-02-07
I hosed my system yesterday (something to do with $HOME, don't ask) and I've had to reinstall the whole bloody lot.

I'm using gsetroot as a desktop background manager, but I'm having problems getting it to load automatically.  I'll look over the weblog again but if I don't find anything expect more questions ;)

BTW: Gene Hunt For The Win.

---

### Post by urukrama on 2008-02-07
> **Mark76 said:**
> I'm using gsetroot as a desktop background manager, but I'm having problems getting it to load automatically.  I'll look over the weblog again but if I don't find anything expect more questions ;)

Since gsetroot is a front-end for Esetroot, you can add the following line to your autostart file:

```
Esetroot -s */path/to/your/image* &
```

There is no way to automatically reset the last used wallpaper, as with Feh.

---

### Post by Mark76 on 2008-02-07
Can I replace image with something more random?  I don't want to keep having to rewrite that line everytime I use a different wallpaper.

Also... do I delete the "eval `cat $HOME/.feh` &" line or keep it?

---

### Post by ejket on 2008-02-07
> **Mark76 said:**
> Can I replace image with something more random?  I don't want to keep having to rewrite that line everytime I use a different wallpaper.

Also... do I delete the "eval `cat $HOME/.feh` &" line or keep it?

If you leave that line in your autostart.sh you can replace the line in .feh with any command you want, including the command to set your background with Esetroot.  All you need is an elegant way to set your background and write that command to .feh at the same time ... like a shell script.  This will allow you to use feh itself if you want to, or any other CLI background setter, and will in the least avoid making you edit your autostart.sh every time you change your wallpaper.

**edit:**

Here's a dirty little script:
```
#! /bin/bash
#
Esetroot $1 $2 $3 $4 $5 $6
echo Esetroot $1 $2 $3 $4 $5 $6  > .feh
```

In my version of feh, the magic file is ".fehbg," but if ".feh" works for you, then the above should do it.

---

### Post by Mark76 on 2008-02-07
This is going to sound lame, but I don't have a directory or a file called .feh (and yes I do have "show hidden files" enabled).

I do, however have one called .fehbg.

No idea what the shell script should be though.

---

### Post by ejket on 2008-02-07
> **Mark76 said:**
> This is going to sound lame, but I don't have a directory or a file called .feh (and yes I do have "show hidden files" enabled).

I do, however have one called .fehbg.

No idea what the shell script should be though.

Hehe, I just finished an edit on that post.  I thought your file was ".feh" because of the "eval `cat $HOME/.feh` &" you mentioned ...

No problem, try this, then:

```
#! /bin/bash
#
Esetroot $1 $2 $3 $4 $5 $6
echo Esetroot $1 $2 $3 $4 $5 $6  > .fehbg
```

---

### Post by yabbadabbadont on 2008-02-07
> **urukrama said:**
> Try hsetroot or habak. Both allow you to set mutliple images, with different coloured backgrounds, and much more. See [here]("http://urukrama.wordpress.com/2007/12/05/desktop-backgrounds-in-window-managers/") for more details (and other options).

Thank you for the habak suggestion.  Arch includes it in their "Extra" repository and it has the one feature that I was thinking about hacking into Esetroot myself.  You can overlay text on the image.  (and it's purrrty too.  ;))  Now I just have to figure out how to create a darkened, semi-transparent background for the text.  I probably need to have it overlay a small blank image.  Time to experiment.  :D

---

### Post by Mark76 on 2008-02-07
> **ejket said:**
> Hehe, I just finished an edit on that post.  I thought your file was ".feh" because of the "eval `cat $HOME/.feh` &" you mentioned ...

No problem, try this, then:

```
#! /bin/bash
#
Esetroot $1 $2 $3 $4 $5 $6
echo Esetroot $1 $2 $3 $4 $5 $6  > .fehbg
```

At the risk of invoking the spirit of Carry-On, where do I stick it?

---

### Post by ejket on 2008-02-07
> **Mark76 said:**
> At the risk of invoking the spirit of Carry-On, where do I stick it?

Make it executable and put it in /usr/local/bin :)

I named mine "setbg" but of course you can call it whatever you like.  (Though before you decide this, check to make sure that you have no other executable with the same name.)

**edit:**

Here's a nice trick you can do with GQView ... in the preferences, add the above script as an editor.  Browse for the image you want, then "edit" it with the script.  Presto, new wallpaper that will remain permanent until you change it.

When you set the command line for the editor in the preferences, add your favorite switches, of course.  For me, this is the "-f" switch in Esetroot for proper scaling.  You can add a default background color as well.

---

### Post by ejket on 2008-02-07
> **yabbadabbadont said:**
> Thank you for the habak suggestion.  Arch includes it in their "Extra" repository ...

Actually, now that I've looked, it's in the Gutsy repo as well.

---

### Post by yabbadabbadont on 2008-02-07
Once I figured out that "Export bitmap" creates a png in inkscape, I was all set.  (It was the first time I had ever used inkscape)  It is pretty neat that you can apply different tint/alpha channel settings to each image/text object you display with habak.

---

### Post by ejket on 2008-02-07
> **yabbadabbadont said:**
> Once I figured out that "Export bitmap" creates a png in inkscape, I was all set.  (It was the first time I had ever used inkscape)  It is pretty neat that you can apply different tint/alpha channel settings to each image/text object you display with habak.

Now you've got me curious ... don't forget to post a screenie so we can see what the heck you're up to :)

I've read the readme, but haven't tried any havoc with habaks yet ...

---

### Post by RedSquirrel on 2008-02-07
> **ejket said:**
> Now you've got me curious ... don't forget to post a screenie so we can see what the heck you're up to :)

I was about to say that.

Is there a screenshot in our future? :)

---

### Post by yabbadabbadont on 2008-02-07
Since the wallpapers are selected randomly, I had to change it a dozen times or so before one that is "safe for work" came up.  :D

[http://omploader.org/iY2Vi](http://omploader.org/iY2Vi)

Click the thumb for the full image.

---

### Post by RedSquirrel on 2008-02-07
That's nice........... oh and I like the text at the bottom too. ;)

---

### Post by ejket on 2008-02-07
> **RedSquirrel said:**
> That's nice........... oh and I like the text at the bottom too. ;)

There's text at the bottom?  Oh, yeah, so there is :)

I'm liking the Esetroot + script glue + GQView background solution that I came up with, and I have yabbadabbadont to thank for the Esetroot part.

Openbox is starting to look better and better to me now.  Here's an example of what I can generate with my default args in GQView:

---

### Post by yabbadabbadont on 2008-02-07
Attached image appears to be corrupted.

---

### Post by ejket on 2008-02-07
> **yabbadabbadont said:**
> Attached image appears to be corrupted.

Mine?  It works on my end (with firefox).  Dunno what could be wrong with it.

---

### Post by yabbadabbadont on 2008-02-07
Edit: Never mind.

What I mistook for corruption, upon closer inspection, appears to be part of the wallpaper.  (It looks very similar to raster image corruption in the last few scanlines)

---

### Post by ejket on 2008-02-07
> **yabbadabbadont said:**
> Edit: Never mind.

What I mistook for corruption, upon closer inspection, appears to be part of the wallpaper.  (It looks very similar to raster image corruption in the last few scanlines)

I see what you mean.  Yes, it's just a bit funky at the bottom :)

---

### Post by Mark76 on 2008-02-08
I still seem to be having problems with getting the desktop image to load on start up.  I'm wondering if my fehbg file is at fault.  Or maybe I need to amend the fehrc file?

---

### Post by urukrama on 2008-02-08
> **Mark76 said:**
> I still seem to be having problems with getting the desktop image to load on start up.  I'm wondering if my fehbg file is at fault.  Or maybe I need to amend the fehrc file?

Try without the &#8221;s. That should do the trick. Also, you don't need to set the fehbg file manually. If you set a wallpaper with Feh, it will automatically be saved in that file. Add the following to your autostart file to reload the last set wallpaper:

```
eval `cat $HOME/.fehbg` &
```

---

### Post by Mark76 on 2008-02-08
Not sure what you mean by: "Try doing without the "s..."

---

### Post by urukrama on 2008-02-08
Use this line in your fehbg file:

> feh --bg-scale /usr/share/xfce4/backdrops/xubuntu-jmak-feisty.png

---

### Post by Mark76 on 2008-02-08
I'm having to do a complete reinstall :(

---

### Post by Mark76 on 2008-02-08
Yay!  I think I've found the answer to the wallpaper problem. Rox :guitar:

Yeah, lame joke. I know. So sue me.

Anyway, I added rox --pinboard=PIN & to my OB autostart list, dragged an image file into the pop up box that popped up when I selected Backdrop from the right click menu and then rebooted and it was still there.

Huzzah

---

### Post by ejket on 2008-02-08
> **Mark76 said:**
> Anyway, I added rox --pinboard=PIN & to my OB autostart list, dragged an image file into the pop up box that popped up when I selected Backdrop from the right click menu and then rebooted and it was still there.

Huzzah

That's good :)  I always wondered how rox handled the desktop, but since I dislike icons and such, I was never very motivated to look into it.

What panel is that, and how configurable is the appearance?

---

### Post by Mark76 on 2008-02-08
It's fbpanel, it's configurable if you can figure out the bloody config file.

---

### Post by Mark76 on 2008-02-08
Rox handles desktop icons better than xfce (I like xfce, but I could really live without the huge borders it draws around icons).

BTW, I need a screen grab app. Any suggestions?

Preferably something that doesn't require me to have GIMP open

---

### Post by RedSquirrel on 2008-02-08
> **Mark76 said:**
> It's fbpanel, it's configurable if you can figure out the bloody config file.

Yeah, that was my experience too. It's a nice panel, but you have to kind of play around with it to figure out what it can do.

---

### Post by RedSquirrel on 2008-02-08
> **Mark76 said:**
> BTW, I need a screen grab app. Any suggestions?

I use imagemagick, but scrot is also quite popular.

---

### Post by Mark76 on 2008-02-08
How do you use imagemagick? I've never been able to work that out :confused:

---

### Post by ejket on 2008-02-08
> **Mark76 said:**
> How do you use imagemagick? I've never been able to work that out :confused:

That's what makes it "magickal" :)

Actually imagemagick is just a set of utilites like "convert," "display," etc.  (Do a "man imagemagick" if you have it installed.)  The one to grab the screen is called "import."  I think it's worth having it around because it can do a lot of different things, and it's not very big.

---

### Post by Mark76 on 2008-02-08
I went with scrot in the end.

---

### Post by yabbadabbadont on 2008-02-08
I use the following simple scripts to grab screenshots.  (using import from ImageMagick)  I have them bound to PrintScreen and Alt-PrintScreen.  (Print and Alt-Sys_Req technically)

grab-screen:
```
#!/bin/bash
import -window root /mnt/images/Screenshots/$(date +%Y%m%d%H%M%S)-full.png
```

grab-selection:
```
#!/bin/bash
import /mnt/images/Screenshots/$(date +%Y%m%d%H%M%S)-selection.png
```

---

### Post by Nythain on 2008-02-08
imagemagick for the win... i actually use the same setup as yabba... in fact, i think it got the script from yabba or redsquirrel a while back when i got into flux

---

### Post by Mark76 on 2008-02-08
Is there a way to add a shut down button to fbpanel?  The open box menu doesn't work when rox is up and running.

---

### Post by ejket on 2008-02-08
> **yabbadabbadont said:**
> I use the following simple scripts to grab screenshots.  (using import from ImageMagick)  I have them bound to PrintScreen and Alt-PrintScreen.  (Print and Alt-Sys_Req technically)

grab-screen:
```
#!/bin/bash
import -window root /mnt/images/Screenshots/$(date +%Y%m%d%H%M%S)-full.png
```

grab-selection:
```
#!/bin/bash
import /mnt/images/Screenshots/$(date +%Y%m%d%H%M%S)-selection.png
```

I like it, and it saved me reading more man pages :)

---

### Post by RedSquirrel on 2008-02-08
> **Mark76 said:**
> Is there a way to add a shut down button to fbpanel?  

I shutdown from the console so I don't use this sort of thing, but couldn't you add a button to the launchbar in fbpanel with an action to shutdown?



> **Mark76 said:**
> The open box menu doesn't work when rox is up and running.

My rox knowledge is rusty, but I thought there was a "compatibility" option in the rox configuration options so that you can use the right-click menu.

A keyboard shortcut to open the menu might work as well.

---

### Post by johnraff on 2008-02-08
... a keyboard shortcut to shutdown too...

---

### Post by Mark76 on 2008-02-09
> My rox knowledge is rusty, but I thought there was a "compatibility" option in the rox configuration options so that you can use the right-click menu.

Yep, that did the trick. Ta:KS

I seem to be spending a lot more time in my cobbled together DE than I am in XFCE lately.  I think I prefer the way the various applications handle the tasks I've set them.

---

### Post by ejket on 2008-02-09
> **Mark76 said:**
> Yep, that did the trick. Ta:KS

I seem to be spending a lot more time in my cobbled together DE than I am in XFCE lately.  I think I prefer the way the various applications handle the tasks I've set them.

Well, there's a lot of satisfaction in rolling your own system.

You could take it further and try a minimal debian or arch install and work your way up from the bare metal, unless that's what you've already done.

I've been looking at arch again lately -- I got lured away from it a while back by the vastness of the debian repos -- .but arch is really a tight, sweet little distro.  If only they had texlive and a few other oddball things I need, I'd go back.

Of course, I'd probably have to symlink "apt-get" to "pacman" :)

---

### Post by Mark76 on 2008-02-09
I'm building it on a Xubuntu base.  So far the only thing I haven't been able to find a replacement for is the user interface.  But that's mostly because I have no idea where to look.

I quite fancy windows transparency too. Should I give xcompmgr another go?

---

### Post by RedSquirrel on 2008-02-09
> **Mark76 said:**
> Yep, that did the trick. Ta:KS

Glad it worked. :)



> **Mark76 said:**
> I'm building it on a Xubuntu base.  So far the only thing I haven't been able to find a replacement for is the user interface.  But that's mostly because I have no idea where to look.

I quite fancy windows transparency too. Should I give xcompmgr another go?

What are you missing in the interface?

[http://xwinman.org/](http://xwinman.org/) might give you some ideas about different window managers, for example.

As for xcompmgr, when I've tried it I found it to be slow but it's up to you. I read somewhere that it was developed for testing and the intention was that it would not be used regularly (but some people do use it all the time, which is fine, of course).

Xfce's xfwm4 compositing seemed OK.

---

### Post by RedSquirrel on 2008-02-09
> **ejket said:**
> I've been looking at arch again lately -- I got lured away from it a while back by the vastness of the debian repos -- .but arch is really a tight, sweet little distro.  If only they had texlive and a few other oddball things I need, I'd go back.

A quick check with pacman reveals there is a bunch of texlive stuff in the [community] repository. (Or, look here [http://aur.archlinux.org/packages.php](http://aur.archlinux.org/packages.php))


> **ejket said:**
>  Of course, I'd probably have to symlink "apt-get" to "pacman" :)

Nah. It's not really that hard to drop the apt-get. The new habit is formed quite easily. :)

---

### Post by Mark76 on 2008-02-09
Under Settings in Xubuntu there's an option called User Interface Settings.  It appears to control the look of the window pane (not the border).

---

### Post by RedSquirrel on 2008-02-09
> **Mark76 said:**
> Under Settings in Xubuntu there's an option called User Interface Settings.  It appears to control the look of the window pane (not the border).
It's been a while since I last used Xfce. If I recall correctly, that sets the GTK+ theme.

In that case, you can try gtk-chtheme (run it as 'gtk-chtheme') or gtk-theme-switch (run as 'switch2') to achieve the same thing when you use Openbox (or any other window manager).

---

### Post by Mark76 on 2008-02-09
Yep, got that. :)

Is it possible to use XFWM4 windows themes in OB?  There are a few in there I was quite fond of.

---

### Post by RedSquirrel on 2008-02-09
No, but you can see if someone has created a theme for Openbox that matches the xfwm4 theme or you can make your own. 

[http://box-look.org](http://box-look.org)

---

### Post by Mark76 on 2008-02-09
Okay

I know this isn't strictly an open box question, but what do I need to edit in the gkrellm config file to get it to display on the desktop without being in the taskbar?

---

### Post by ejket on 2008-02-09
> **RedSquirrel said:**
> [QUOTE=ejket;4299040]I've been looking at arch again lately -- I got lured away from it a while back by the vastness of the debian repos -- .but arch is really a tight, sweet little distro.  If only they had texlive and a few other oddball things I need, I'd go back.

A quick check with pacman reveals there is a bunch of texlive stuff in the [community] repository. (Or, look here [http://aur.archlinux.org/packages.php](http://aur.archlinux.org/packages.php))[/QUOTE]

Funny thing, just after I posted that I went and started on an arch install.  That wiki page for installing arch from another distro is rather handy -- or maybe I should wait until I actually boot into arch before I give my judgment on that :)

Thanks for the texlive info -- tetex doesn't have all the stuff I like.

> **RedSquirrel said:**
> [QUOTE=ejket;4299040]Of course, I'd probably have to symlink "apt-get" to "pacman" :)

Nah. It's not really that hard to drop the apt-get. The new habit is formed quite easily. :)[/QUOTE]

Yes, actually I fell easily back into the habit of pacman with this install.  It's been I guess 3 years since I used arch, though.  I'll probably eventually show up on the arch forums as "eerok," since that's what I registered as back then.  So be sure to help me promptly if you see me having trouble with anything :-D

---

### Post by ejket on 2008-02-09
> **Mark76 said:**
> Okay

I know this isn't strictly an open box question, but what do I need to edit in the gkrellm config file to get it to display on the desktop without being in the taskbar?

It's been a while since I used gkrellm, but I'm sure there's a box you can tick in the regular gui config that takes care of that.

---

### Post by Mark76 on 2008-02-09
I got it to display without being in the taskbar, but is it meant to stay above all windows?

---

### Post by ejket on 2008-02-09
There should be a box to tick for that, too ...

---

### Post by yabbadabbadont on 2008-02-09
There is.

---

### Post by Mark76 on 2008-02-09
Okay.  I ticked the boxes now it looks like this

---

### Post by yabbadabbadont on 2008-02-09
> **Mark76 said:**
> Okay.  I ticked the boxes now it looks like this

Is that good, or bad?  I can't tell from your post.  ;)

---

### Post by Mark76 on 2008-02-09
GAH!  I rebooted my computer and now it's gone back to closing when I close the taskbar entry.

Only seems to happen when I open it from Rox though.

---

### Post by Mark76 on 2008-02-09
Sorry, but could you show me which boxes to tick to get it to display without being on the taskbar? :(

---

### Post by yabbadabbadont on 2008-02-09
[http://ubuntuforums.org/showpost.php?p=4300503&postcount=1130](http://ubuntuforums.org/showpost.php?p=4300503&postcount=1130)

(last post on the previous page... :lol:)

---

### Post by Mark76 on 2008-02-09
It's not working :(

As soon as I close it on the task bar it closes

---

### Post by yabbadabbadont on 2008-02-09
If there is an entry in the taskbar, and you take the option to close it, then the associated program will close.  That is what is supposed to happen.  :)

Since this is the openbox thread, I assume that you are using openbox.  What panel are you using?  How do you start the panel?  How are you starting gkrellm?  Post the relevant configuration files, please.

---

### Post by Mark76 on 2008-02-09
I'm using fbpanel, which is in my openbox autostart menu, as is gkrellm.

Which are the relevant configuration files?

I swear I had gkrellm showing on the desktop without being in the taskbar.

---

### Post by yabbadabbadont on 2008-02-09
The simplest solution is to probably put gkrellm into the openbox dock.  Add the "-w" parameter to the command where you launch gkrellm.  Also, be sure to start gkrellm *before* you start fbpanel.  fbpanel has issues respecting the show/noshow taskbar hints and I found that it worked better to start gkrellm first.

---

### Post by Mark76 on 2008-02-09
It appears that in order for gkrellm to not be included on the task bar it has to be a dock/panel app.  And if that option is chosen it automatically takes up space and pushes any full sized windows to one side.

The -w command seems to make it stick to the top left corner for some reason

---

### Post by yabbadabbadont on 2008-02-09
The top left corner is probably the default location of the openbox dock.  It also defaults to having the "strut" property set (always reserves screen space).  You can change both using obconf.  You need to set it to "allow dock to be both above and below" or something like that.  You probably should also spend some time on the openbox website reading the excellent documentation that they provide.  :)

---

### Post by Mark76 on 2008-02-09
I forgot about the handy open box configuration gui. :oops:

I've rewrote the command in both the openbox menu and the autostart file to read gkrellm -w.

---

### Post by yabbadabbadont on 2008-02-09
> **Mark76 said:**
> I forgot about the handy open box configuration gui. :oops:

I've rewrote the command in both the openbox menu and the autostart file to read gkrellm -w.

It sounds like you got it working now.  I'm glad it helped.  Don't worry about forgetting things now and then.  It happens more frequently as one gets older I've found.  I spent 10 minutes the other day trouble-shooting my sound setup, only to realize that I hadn't turned on the speakers...  :lol:

---

### Post by Mark76 on 2008-02-09
Yeah, that happens.

I never even realised Open Box had a dock.

What else can I put in it?

---

### Post by Mark76 on 2008-02-09
Now that I have Rox Pinboard handling wallpaper and desktop icon duties (and pretty nicely too) can I edit out the entries for feh and esetroot from my autostart file?

---

### Post by yabbadabbadont on 2008-02-09
Probably.  Make a backup and try it and see what happens.

---

### Post by Mark76 on 2008-02-09
I edited the autostart file to remove the two entries, rebooted and...

No background.

Good job I backed the file up before trying it :lol:

Still, one of them must be redundant.

I'll have another go tomorrow.

---

### Post by Mark76 on 2008-02-10
Has anyone got an Openbox/Ubuntu splash screen I can have? :D

And why does start up manager need Firefox? :?

---

### Post by Mark76 on 2008-02-10
Another "not an openbox question" question.  But does anyone know how to get gdeskcal to stick to the Rox pinboard desktop (i.e. not disappear when I use show desktop)?

---

### Post by Mark76 on 2008-02-14
Is there a guide to setting up Skippy anywhere?

---

### Post by Mark76 on 2008-02-14
Uh, never mind, I found the answer in an old thread. :)

---

### Post by johnraff on 2008-02-15
Hi folks,
I thought Openbox didn't set any wallpaper by itself, and when I put it on a server gutsy install on another box that was indeed the case, but I've just installed it in this Xubuntu feisty setup and when I logged in I got this pastel orangy wallpaper without any effort on my part... (attachment)

Any idea where that might be coming from?

---

### Post by yabbadabbadont on 2008-02-15
The graphical login manager is capable of setting the root window pixmap if it has been configured to do so.

---

### Post by johnraff on 2008-02-15
Ah - gdm in this case. I've had a poke round /etc/gdm/ and it looked quite possible, but I couldn't put my finger on it There's an awful lot of stuff in there.
Ah well, I don't suppose it matters that much. Quite a nice background to be going on with really... :)

---

### Post by moore.bryan on 2008-02-15
i know this may have been covered *ad nauseum* somewhere, but is anyone using wbar instead of awn and, if so, figured-out a way to "trick it" into autohiding?

---

### Post by DJiNN on 2008-02-15
> **moore.bryan said:**
> i know this may have been covered *ad nauseum* somewhere, but is anyone using wbar instead of awn and, if so, figured-out a way to "trick it" into autohiding?

I've only just started playing around with wbar myself, so i haven't got an answer for you, but i'd be interested in ANY info about wbar. There doesn't seem to be a lot of info available for some reason, and it's such a great little app.

Current;y trying it with both OpenBox & FluxBox.

---

### Post by urukrama on 2008-02-15
In Pekwm you can use the screen edges for this. I don't use wbar, but just tried it out: I can make wbar appear when the mouse enters the bottom screen edge and disappear (killall wbar) when I click on a window or the desktop. Wbar is light enough for it to work. It appears almost instantly.

I don't know any solution in Openbox, apart from binding wbar and 'killall wbar' to a keybinding in the rc.xml.

EDIT: btw, DJiNN, have you see [this]("http://ubuntuforums.org/showthread.php?t=412867") thread? Somewhere on the first page all the wbar options are listed.

---

### Post by DJiNN on 2008-02-15
> **urukrama said:**
> 
EDIT: btw, DJiNN, have you see [this]("http://ubuntuforums.org/showthread.php?t=412867") thread? Somewhere on the first page all the wbar options are listed.

Thanks for that urukrama - That's just what i was after. :)

---

### Post by moore.bryan on 2008-02-15
> **DJiNN said:**
> I've only just started playing around with wbar myself, so i haven't got an answer for you, but i'd be interested in ANY info about wbar. There doesn't seem to be a lot of info available for some reason, and it's such a great little app.

Current;y trying it with both OpenBox & FluxBox.
right now, i'm in contact with the developer to see if he can give me any tidbits, but it doesn't look promising. he is, however, currently working on an autohide patch... so buggy he hasn't released it yet.
> **urukrama said:**
> In Pekwm you can use the screen edges for this. I don't use wbar, but just tried it out: I can make wbar appear when the mouse enters the bottom screen edge and disappear (killall wbar) when I click on a window or the desktop. Wbar is light enough for it to work. It appears almost instantly.

I don't know any solution in Openbox, apart from binding wbar and 'killall wbar' to a keybinding in the rc.xml.

EDIT: btw, DJiNN, have you see [this]("http://ubuntuforums.org/showthread.php?t=412867") thread? Somewhere on the first page all the wbar options are listed.
that's a brilliant idea, urukrama, but defeats the purpose of the mouse autohide. ;-)

---

### Post by urukrama on 2008-02-15
> **moore.bryan said:**
> that's a brilliant idea, urukrama, but defeats the purpose of the mouse autohide. ;-)

I know ;-) but if there is no mouse autohide, it is a decent enough alternative.

---

### Post by DJiNN on 2008-02-16
> **moore.bryan said:**
> right now, i'm in contact with the developer to see if he can give me any tidbits, but it doesn't look promising. he is, however, currently working on an autohide patch... so buggy he hasn't released it yet. 

Thanks for the info. Hopefully the outcome will be good, but it does seem to be a program that's in rather slow development. Shame, because it's such a great little app. I wonder if perhaps the creator has got somewhat bored or disheartened with the project, because there doesn't seem to be a lot happening with it lately?

Look forward to hearing any news that you can share. :)

---

### Post by moore.bryan on 2008-02-16
> **urukrama said:**
> I know ;-) but if there is no mouse autohide, it is a decent enough alternative.
very true...

> **DJiNN said:**
> Thanks for the info. Hopefully the outcome will be good, but it does seem to be a program that's in rather slow development. Shame, because it's such a great little app. I wonder if perhaps the creator has got somewhat bored or disheartened with the project, because there doesn't seem to be a lot happening with it lately?

Look forward to hearing any news that you can share. :)
as do i... another question to pose to my friends:
no matter what i do, i can't get my mouse/cursor theme to change... i've edited my .Xdefaults and .gtkrc-2.0 files, run ```
xrdb -merge $HOME/.Xdefaults
``` but to no avail; i'm pulling my hair out. help?

EDIT:

alright, so i've figured-out a work-around, but i never had to do anything like this before. i edited my .xinitrc file to include the line ```
xrdb -load /home/moore/.Xdefaults &
```

any ideas why?

---

### Post by ejket on 2008-02-16
> **moore.bryan said:**
> another question to pose to my friends:
no matter what i do, i can't get my mouse/cursor theme to change... i've edited my .Xdefaults and .gtkrc-2.0 files, run ```
xrdb -merge $HOME/.Xdefaults
``` but to no avail; i'm pulling my hair out. help?

EDIT:

alright, so i've figured-out a work-around, but i never had to do anything like this before. i edited my .xinitrc file to include the line ```
xrdb -load /home/moore/.Xdefaults &
```

any ideas why?

I haven't seen .Xdefaults used in a long time.  Usually it's .Xresources -- I'm not on Ubuntu right now so I can't check, but think I've always used .Xresources on Debian.

---

### Post by moore.bryan on 2008-02-17
that's funny... i don't have an .Xresources file and never heard of using one. is it more of a debian thing?

---

### Post by ejket on 2008-02-17
Well, it can be called anything, but it has to be called something, if you get what I'm saying :)  It depends on what X is configured to look for.  I'm just saying that if .Xdefaults isn't sourced by default, then maybe X is looking for another filename, and that would likely be .Xresources, which is very common.

I can't check because I've moved to Arch ...

---

### Post by moore.bryan on 2008-02-17
> **ejket said:**
> Well, it can be called anything, but it has to be called something, if you get what I'm saying :)  
absolutely! i just find it funny i never needed to use and .Xresources file before OR tell .xinitrc to load the .Xdefaults file... 
> **ejket said:**
> It depends on what X is configured to look for.  I'm just saying that if .Xdefaults isn't sourced by default, then maybe X is looking for another filename, and that would likely be .Xresources, which is very common.
I can't check because I've moved to Arch ...
makes me wonder how i would check what X is looking for...
thanks for you input, anyway; it has put me down a new path and that can't be a bad thing.

---

### Post by dbbolton on 2008-02-25
Has anyone else had problems with the latest version of obconf? It seems like it takes forever to start for me.

---

### Post by el mariachi on 2008-02-25
works fine for me (arch linux)

---

### Post by johnraff on 2008-02-26
Starts up pretty smartly for me too on ubuntu gutsy.

(thought I'd better reset the title too - wallpaper was a while ago...:) )

---

### Post by dbbolton on 2008-02-26
Oh well. It's not a serious issue; I can live with it.

By the way, I just now realised that if you hold Alt and right-click on conky or screenlets, you can treat them like a regular window :lol:

---

### Post by moore.bryan on 2008-03-13
two weeks since the last post in this thread!  please no; tell me this thread is still alive! or, is it that openbox on ubuntu runs so amazingly well, there's almost no problems!!!
;-)

---

### Post by eriqjaffe on 2008-03-13
I just put Openbox on my old laptop last night, and have been very happy so far, although I wish the default menu didn't assume that I was using xterm and Firefox.  Wasn't a big deal to change it, though.

So far, I'm liking it quite a bit.  I've put together a nice leightweight DE using it, PCManFM and fbpanel.

---

### Post by PurposeOfReason on 2008-03-18
Could someone help me with a keybinding? With compiz I would simple press Alt+F8 and it would let me resize the window in any direction without clicking and then set the window when I clicked the mouse. Is that possible in openbox? I mean, after I mapped the mousewheel to transparency I'm trying to get fancy. ;)

---

### Post by Mark76 on 2008-03-19
I can't get obconf working :(

---

### Post by PurposeOfReason on 2008-03-19
Does anyone here have a pipemenu to check gmail? There is one on the site but that uses python2.3 and doesn't work. I changed the bang from python2.3 to just python and that didn't work either.

---

### Post by el mariachi on 2008-03-20
I remember using one... I sent an email to the guy that wrote that outdated script and he updated it for me :D
I don't have it anymore though

---

### Post by PurposeOfReason on 2008-03-20
> **el mariachi said:**
> I remember using one... I sent an email to the guy that wrote that outdated script and he updated it for me :D
I don't have it anymore though
I got it to work if I disable the cache, but that isn't that nice. Do you know where you got the email address?

---

### Post by DJiNN on 2008-03-21
Can anyone tell me if OpenBox will work on a 64bit buntu system? I've got Xubuntu (64 bit) installed & would love to have a go with either OpenBox or Fluxbox, but don't want to risk installing if there's a chance that it may bork something. :)

Many thanks in advance for any help......

---

### Post by PurposeOfReason on 2008-03-21
Give me a reason it wouldn't work? AKA, it works fine. :)

---

### Post by Mark76 on 2008-03-21
Yep, I have 64 bit Xubuntu and it works for me.

Now... if *only* there was a way to disable raise on click I'd be a happy bunny :)

---

### Post by el mariachi on 2008-03-21
> **Mark76 said:**
> Yep, I have 64 bit Xubuntu and it works for me.

Now... if *only* there was a way to disable raise on click I'd be a happy bunny :)
+1

@PurposeOfReason: I'm looking for the guy's email ;)

---

### Post by DJiNN on 2008-03-21
Thanks for that PurposeOf Reason & Mark76.... i'm just downloading it now, so hopefully i'll be up & running soon. :)

PurposeOf Reason - Just seen one of the screens on your Deviant page.... nice looking Box. What's the Minefield thing though? Looks kind of like a Browser.... interesting.

---

### Post by el mariachi on 2008-03-21
Minefield is the codename for Firefox3 :D it's still in beta stage (beta4)

---

### Post by DJiNN on 2008-03-21
Thanks for that el mariachi. I'm running FF Beta 4 here right now but it doesn't look "Anything" like the one on [Purpose's Deviant page]("http://purposeofreason.deviantart.com/art/02-24-2008-78371230"). :) Hope you don't mind the link there Purpose? I'll gladly remove if you're not happy with it.....

---

### Post by el mariachi on 2008-03-21
he must be using some skin :D

---

### Post by PurposeOfReason on 2008-03-21
> **DJiNN said:**
> Thanks for that el mariachi. I'm running FF Beta 4 here right now but it doesn't look "Anything" like the one on [Purpose's Deviant page]("http://purposeofreason.deviantart.com/art/02-24-2008-78371230"). :) Hope you don't mind the link there Purpose? I'll gladly remove if you're not happy with it.....
Free advertising, why would I mind? :) That one, it's actually using eyeos which is like a remote server desktop. All open source. I don't use it anymore as I really don't have a user for it. Then firefox is customized with the compact menu extension and the elegant brit gtk theme.

[http://eyeos.org/](http://eyeos.org/)

---

### Post by urukrama on 2008-03-24
> **Mark76 said:**
> I can't get obconf working :(

Sorry for the delay. What happens when you type obconf in a terminal? What error messages do you get?

---

### Post by Mark76 on 2008-03-24
Erm. I got it working.

Then I decided to give the native ROX DE window manager a go :o

Maybe I should start a random ROX chatter thread :lol:

---

### Post by el mariachi on 2008-03-24
maybe... I don't know many people using that configuration though..
make some cool desktop and post it at the desktop thread.
with luck you'll start a fad hehe

---

### Post by Mark76 on 2008-03-24
Font-0.9.1 for Rox desktop is a pretty capable little app

---

### Post by DJiNN on 2008-03-27
> **Mark76 said:**
> Erm. I got it working.

Then I decided to give the native ROX DE window manager a go :o

Maybe I should start a random ROX chatter thread :lol:

I'd be interested in finding out more about ROX. I use the ROX Term when i'm running Tiny Me, and i love the file manager.... but could never get my head round the whole "Pinboard" thing, and the loss of the right click menu i also found somewhat annoying. :)

I know there's more to ROX than just those few apps though, so i'm up for another thread and getting stuck in & giving ROX a try. :)

---

### Post by Mark76 on 2008-03-27
Consider it done!

[http://ubuntuforums.org/showthread.php?p=4599038#post4599038](http://ubuntuforums.org/showthread.php?p=4599038#post4599038)

---

### Post by jediborger on 2008-03-28
I'm having an issue with gtk fonts. Basically I installed a very minimal ubuntu install as a server and have recently decided to put a minimal gui on it for some programs. So I set up Xvfb and vnc since this computer has no real hardware attached to it. I don't know if this affects gtk but mentioning it anyways. Then I decided i would use openbox as my minimal window manager. So far it's all great but all gtk applications have a black box around the font, thus I can't read the font unless I highlight the stuff which is not possible in all cases. I'd rather not have to install a settings daemon like "gnome-settings-daemon" but if there's one without DE dependencies i would go for it. Although I'm pretty sure the font issue can be solved through the .gtkrc-2.0 file. Has anyone else experienced this problem and/or knows how to fix my fonts?

---

### Post by el mariachi on 2008-03-28
i don't think i've ever experienced something like your issue.
the fonts can be set in the gtkrc file, but i don't remember what you've got to type in.
 
try installing gtk-chtheme and use it to set your system's font. I think it's in the repos.

---

### Post by jediborger on 2008-03-28
I tried changing the font with gtk-chtheme and it did, but there's still black boxes around everything. Maybe a screenshot will help. I might try restarting the machine to see if that helps, but is some gtk daemon that I can manually restart, maybe with pango or cairo?

---

### Post by urukrama on 2008-03-28
Is there anything relevant in your ~/.xsession-errors file?

---

### Post by eriqjaffe on 2008-03-30
Have you looked at that system with a monitor hooked up directly to it (if possible)?  The VNC color depth looks **really** low (notice the gradients, or lack thereof, on the window titles).  I wonder if that has something to do with it.

---

### Post by jediborger on 2008-03-30
I have no .xsession errors file but I've looked at the output of Xvfb and it has numerous lines saying:
```
matthew@home-server:~$ Xvfb :1
error opening security policy file /etc/X11/xserver/SecurityPolicy
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/share/fonts/X11/100dpi/:unscaled, removing from list!
Could not init font path element /usr/share/fonts/X11/75dpi/:unscaled, removing from list!
Could not init font path element /usr/share/fonts/X11/Type1, removing from list!
Could not init font path element /usr/share/fonts/X11/100dpi, removing from list!
Could not init font path element /usr/share/fonts/X11/75dpi, removing from list!
Could not init font path element /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType, removing from list!

```
As for bit depth, according to the Xvfb docs the default setting is 12 bits. Although when i try to change the default using the switches, I get an error saying the screen couldn't be added. :(

---

### Post by FakeOutdoorsman on 2008-04-01
I want to take a panel dump.  For those enlightened panel-less Openbox users, enrich me with your knowledge of navigation.  What are you doing/using to replace some of the functionality of a panel?

---

### Post by urukrama on 2008-04-02
> **FakeOutdoorsman said:**
> For those enlightened panel-less Openbox users, enrich me with your knowledge of navigation.  What are you doing/using to replace some of the functionality of a panel?

I use Openbox mainly without a panel. To navigate between windows I use the alt-tad switch; openbox has a handy on-screen-display to show you what windows you have running. Occasionally I use Openbox' client-menu (middle click on the desktop and bound to a key binding). If I have a lot of windows open, I sometimes also use [skippy]("http://thegraveyard.org/skippy.php"), a full-screen task switcher.

But most of it happens through the alt-tab dialog.

For a system tray, I use docker in the dock. I also load a clock in the dock. I don't use launchers, and I use Openbox' root-menu (right-click on desktop or Alt-F1 in my settings), gmrun or dmenu to launch applications. I've played with [apwal]("http://apwal.free.fr/") in the past, but haven't used it in while.

---

### Post by dbbolton on 2008-04-04
I noticed today that if you click on the pypanel clock, it launches xclock :D

---

### Post by el mariachi on 2008-04-04
nothing happens here :x

---

### Post by urukrama on 2008-04-04
> **dbbolton said:**
> I noticed today that if you click on the pypanel clock, it launches xclock :D

You can also make it launch something else. I use it to launch orage, so I have quick access to a calendar. Look for this section in the pypanelrc and change 'orage' with whatever app you like:

```
#--------------------------------
def clockButtonEvent(pp, button):
#--------------------------------
    """ Button event handler for the panel's clock object """
    
    if button == 1:
        os.system("orage &")
    elif button == 2:
        pass
    elif button == 3:
        pp.toggleHidden()  
    elif button == 4:
        pp.showDesktop()
    elif button == 5:
        pp.showDesktop()
```

---

### Post by El_Belgicano on 2008-04-05
Hi OB'ers,
Can anyone point me out a GUI to change the GDM Login screen ... lost it in my switch to openbox ...
I'll already feel happy with a simple command ;-)
Little question to all: what panel are you using?
Happy OB'ing to you all...

PS: useful tip Urukrama...

---

### Post by dbbolton on 2008-04-05
> **El_Belgicano said:**
> Hi OB'ers,
Can anyone point me out a GUI to change the GDM Login screen ... lost it in my switch to openbox ...
I'll already feel happy with a simple command ;-)
Little question to all: what panel are you using?
Happy OB'ing to you all...

PS: useful tip Urukrama...
You can change the GDM settings by running (as root):

```
gdmsetup
```

---

### Post by El_Belgicano on 2008-04-05
Haha, feeling like an idiot ... gdmsetup ... :)
thanks dbbolton ...

---

### Post by cardinals_fan on 2008-04-05
> **urukrama said:**
> You can also make it launch something else. I use it to launch orage, so I have quick access to a calendar. Look for this section in the pypanelrc and change 'orage' with whatever app you like:

```
#--------------------------------
def clockButtonEvent(pp, button):
#--------------------------------
    """ Button event handler for the panel's clock object """
    
    if button == 1:
        os.system("orage &")
    elif button == 2:
        pass
    elif button == 3:
        pp.toggleHidden()  
    elif button == 4:
        pp.showDesktop()
    elif button == 5:
        pp.showDesktop()
```
THANK YOU!  I have always wanted a way to execute a command from the panel's objects.

---

### Post by dbbolton on 2008-04-07
Can someone tell me how to use the .fehbg file in settting the wallpaper at startup? I think it involves cat or eval or something.

---

### Post by urukrama on 2008-04-07
Add the following to your autostart file:

> eval `cat $HOME/.fehbg` &

---

### Post by dbbolton on 2008-04-07
> **urukrama said:**
> Add the following to your autostart file:
It just seems to print:

```

daniel@mephista:~$ eval `cat $HOME/.fehbg` &
[1] 6169
daniel@mephista:~$ eval `cat $HOME/.fehbg` &
[2] 6178
[1]   Done                    eval `cat $HOME/.fehbg`
daniel@mephista:~$ eval `cat $HOME/.fehbg` &
[3] 6185
[2]   Done                    eval `cat $HOME/.fehbg`
daniel@mephista:~$ 

```

---

### Post by eriqjaffe on 2008-04-07
I just run
```
feh --bg-center /home/eriq/.config/openbox/openbox-wallpaper.png &
```
in my autostart.sh.  Works just fine.  I hadn't even noticed that .fehbg file until just now, in fact.  Looking at that file, it looks like it just contains the line I run in my autostart.sh anyways.

---

### Post by dbbolton on 2008-04-07
> **eriqjaffe said:**
> I just run
```
feh --bg-center /home/eriq/.config/openbox/openbox-wallpaper.png &
```
in my autostart.sh.  Works just fine.  I hadn't even noticed that .fehbg file until just now, in fact.  Looking at that file, it looks like it just contains the line I run in my autostart.sh anyways.
It's dynamic. The content changes to the last command used with feh to set the background. Since I change my wallpaper often, it is kind of a pain to change the autostart line. 

I'm using a "custom action" in Thunar so that I can right click on an image and set it as the background with feh. Maybe I could change the custom action to something like:

```

feh --bg-center %f 
ln -s %f ~/Images/fehbg

```

And then put 

```

feh --bg-center ~/Images/fehbg

```

in the austostart file. But how can I put two commands on one line for the custom action?

---

### Post by urukrama on 2008-04-08
> **dbbolton said:**
> It just seems to print:

```

daniel@mephista:~$ eval `cat $HOME/.fehbg` &
[1] 6169
daniel@mephista:~$ eval `cat $HOME/.fehbg` &
[2] 6178
[1]   Done                    eval `cat $HOME/.fehbg`
daniel@mephista:~$ eval `cat $HOME/.fehbg` &
[3] 6185
[2]   Done                    eval `cat $HOME/.fehbg`
daniel@mephista:~$ 

```

If I enter the command in a terminal I get something similar, but the wallpaper does change to whatever I used last with Feh (I was using hsetroot before I tried this, so I could see the wallpaper change).

If you want to use that Thunar custom actions command, try this line:
```
feh --bg-center %f && ln -s -f %f ~/Images/fehbg
```
I just tried this and it seems to work fine. You need the -f to override the existing link. Note that fehbg should be a file and not a folder, otherwise you will just get a list of files in the fehbg folder, which wouldn't help you in reloading the last set wallpaper at startup.

---

### Post by Mark76 on 2008-04-09
As an alternative to all these feh shenanigans I've found the Rox Desktop wallpaper app works remarkably well.

And it's incredibly simple to set up as well.

---

### Post by unsoiledchris on 2008-04-12
can anyone tell me how to make a menu item that goes to a folder when I click it?

example being.. item called Music, and when clicked it loads my Music folder?

tried to do it in obmenu but when I click it nothing happens :(

---

### Post by urukrama on 2008-04-12
> **unsoiledchris said:**
> can anyone tell me how to make a menu item that goes to a folder when I click it?

example being.. item called Music, and when clicked it loads my Music folder?

tried to do it in obmenu but when I click it nothing happens :(

It should be of the type:
```
*filemanager* "/path/to/folder"
```

So if you use Thunar and store your music in ~/Music, use the following:

```
thunar "/home/USERNAME/Music"
```

The same goes for text files: *texteditor* "/path/to/file" I find this very handy to add configuration files or logs (Openbox' rc.xml, conkyrc, pypanelrc, bashrc, xsession-errors, etc.) to my Openbox menu. Just a single click and you have access to the configuration file or log of your choice.

---

### Post by moore.bryan on 2008-04-12
urukrama... never new about orage; awesome little app. thanks a ton!

---

### Post by scottro on 2008-04-12
Re pypanel, a friend just made a patch for me so that one can specify width in percent and placement by LEFT, RIGHT and CENTER rather than having to specify in pixels.  It will still throw out a few errors if called from command line, but works quite well. 

[http://roddierod.homeunix.net/code_and_technology/index.html](http://roddierod.homeunix.net/code_and_technology/index.html)

---

### Post by unsoiledchris on 2008-04-12
> **urukrama said:**
> It should be of the type:
```
*filemanager* "/path/to/folder"
```

So if you use Thunar and store your music in ~/Music, use the following:

```
thunar "/home/USERNAME/Music"
```

The same goes for text files: *texteditor* "/path/to/file" I find this very handy to add configuration files or logs (Openbox' rc.xml, conkyrc, pypanelrc, bashrc, xsession-errors, etc.) to my Openbox menu. Just a single click and you have access to the configuration file or log of your choice.

awesome, thank you!

I have another question, could anyone tell me what app that is in the bottom left on this screenshot? [http://www.skwiz0d.com/screenshots/2007-05-03.png](http://www.skwiz0d.com/screenshots/2007-05-03.png)

---

### Post by Tenken on 2008-04-12
That looks like [Visibility]("http://projects.l3ib.org/trac/visibility")

---

### Post by urukrama on 2008-04-17
Openbox 3.4.7 is out. Though it hasn't been officially anounced yet, you can download it [here]("http://icculus.org/openbox/releases/openbox-3.4.7.1.tar.gz").

There isn't a package for Ubuntu or Debian (yet), so you'll have to compile from source.

Here is the changelog:

> Fully updated Czech, Simplified Chinese, Traditional Chinese, German, French, Hungarian, Norwegian, Vietnamese, Dutch, Swedish, Finnish, Brazilian Portuguese, Japanese and Portuguese translations 
Partially updated Spanish translation 
Add an example of the "force" option for the per-app placement options to the default rc.xml file 
Add a new xdg-autostart script. This will eventually end up in the PyXDG distribution hopefully, but it is included in Openbox for now. This script runs things based on the freedesktop.org autostart specification. You can have it run GNOME, KDE, ROX, or XFCE specific things if you want. The new default system-wide autostart.sh script runs it automatically 
Update the default menu.xml to include a lot of common apps 
Fix white font shadows (negative shadowtint) 
Update the autostart.sh to find gnome-settings-daemon correctly, as the GNOME people have moved it to libexec 
Fix focus possibly getting stolen when using the Focus action 
Drastically speed up rendering of Vertical and SplitVertical gradients 
Speed improvements also for Horizonal and Pyramid gradients 
Add new theme options, menu.overlap.x and menu.overlap.y options, that let you independently control the horizontal and vertical position of submenus 
Change _NET_ACTIVE_WINDOW messages to not change the current desktop, but to bring the window to the current desktop instead. This is the industry standard policy 
Use the pretty new openbox.png icon as the default window icon 
Allow matching per-application rules to windows by their window type (normal, dialog, splash, etc). The default rc.xml has more details 
Add new Openbox-themed prompt windows. Use these prompt windows to ask before killing off windows that aren't responding. This also means we don't need to ping every window constantly forever 
Add a new <prompt> option to the Execute action. If this is set to a string, a dialog will be shown with that string in it and "yes"/"no" buttons. The command to be executed will only be run if the user selects "yes" in the dialog 
Add a new <prompt> option to the Exit action, which is a boolean (not a string). When true, Openbox will show a dialog confirming if you want to exit. The default is to show the prompt 
Reduce Openbox's memory footprint and speed up rendering through the use of a new icon cache, so that Openbox only needs to keep 1 copy of an icon when 100 different windows share it 
Make Openbox menus have the "menu type" hint for compositors to see and use 
Fix the MoveResizeTo action for negative coords (opposite edges) 
Fix key bindings getting lost if multiple bindings at the same level could not be translated (Fixes VMWare causing Openbox keybindings to stop working) 
Fix the resize popup box for terminal windows with a base size of 0 (show the right size values for urxvt terminals) 
Fix some off-by-one bugs with the edge growing/shrinking code 
Add new theme options for menu line separators: menu.separator.color, menu.separator.width, menu.separator.padding.width, menu.separator.padding.height 
Add xfce-mcs-manager to the default autostart.sh, and run it automatically when gnome-settings-daemon is not present to have GTK apps inherit settings from the XFCE configuration tools 
Make the send-to-desktop menu in the client-menu indicate which is the current desktop for omnipresent windows, and don't close it if just toggling omni-presence when ctrl-clicking 
Add a new SessionLogout action that logs out through the session manager, when running Openbox within a session manager such as within an GNOME/Openbox or KDE/Openbox session. The action includes a <prompt> option which is similar to the Exit action's 
Add a new gdm-control command that lets you control gdm from within an X session. The gdm-control lets you change GDM's behaviour for when you end the current session. For instance, you can tell GDM to reboot, and then immediately log out of the current session, and the computer will be rebooted 
Show an information dialog when an error occurs for Openbox, such as when the Execute action fails or when XML syntax errors are present in the configuration files 
When making a window very narrow, don't draw buttons to the right of the title on top of the ones on its left.

---

### Post by Jose Catre-Vandis on 2008-04-19
Time for me to join in with some of my experiences in getting Openbox up and running, along with a few tips and a few queries!

Machine:```
aging Dell laptop CPt Latitude with 700mhz processor and 192mb ram
(Apart from age and speed, only foible is that it doesn't like to reboot)
```

Requirements: ```
Switch on and boot to desktop, no login needed. 
Simple method to shut down.
For non-tech users to browse internet and create simple files.
Ability for me to shh into laptop for admin purposes.
```

Base setup: ```
Ubuntu 7.10 Gutsy server
```

Packages - ```
openbox obconf openbox-themes xfe xfce4-terminal
tango-icon-theme-extras xorg mingetty flashplugin-nonfree alsa-oss liblame0
libxine1-ffmpeg sun-java6-fonts sun-java6-jre sun-java6-plugin unrar w32codecs mplayer
mozilla-mplayer acroread-plugins mozilla-acroread feh audacious pypanel abiword
gnumeric openssh-server portmap nfs-common gmessage mousepad

Courtesy ubuntuforums/psychocats/interweb blogs
``` [COLOR="Red"]obmenu[/COLOR] - not from repos. Also latest versions of openbox and obconf from openbox site, more on that later.


**Boot to Desktop**

It now appears I followed an "old school" route to get this done. But it works, with one issue outstanding, so for now I will stick to it. This required the installation of mingetty and the creation of a .bash_profile file in my home directory, along with editing of the etc/event.d/tty1 file:

**~/.bash_profile** contents:```
if [ `tty` = "/dev/tty1" ]; then
startx
fi


#if [ -z "$DISPLAY" ] && [ $(tty) = /dev/tty1 ]; then
#while true
#do
#startx --
#sleep 5
#done
#fi
```

**/etc/event.d/tty1** contents:```
# tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

start on runlevel 2
start on runlevel 3
start on runlevel 4
start on runlevel 5

stop on runlevel 0
stop on runlevel 1
stop on runlevel 6

respawn

exec /sbin/mingetty tty1 --autologin user
```

This works well, and takes the user straight to the desktop. The only problem I have is this, on selecting "Exit" from the right click menu, I am taken to a command prompt (By design!) When I then type logout, the X session is restarted and I am back to the desktop. So my only route to a command line login is with CTRL+ALT+F2 etc, but still logged in as me. This won't bother the eventual users, but it bothers me. ***Can this be fixed, or should I take the autostart.sh and autologin.c route?***

**Desktop Background**

This one is easy, using feh. I got me an image, called dots.jpg. Then simply ran ```
feh --bg-scale dots.jpg
``` Then made an entry in the ~/.xinitrc file of```
#starts feh to give background
sh ./.fehbg &
```

**Exit Strategy...**

Having read the whole of the random openbox chatter thread, i now know it would have been just as easy to make a couple of menu entries, but this solution was quite cool, and offers simplicity and options. Using gmessage (see it was installed above) with a bash script linked to a menu entry, I have created a dialog that offers Quit Openbox, Reboot and Shutdown, along with a cancel button. This is what you do.

Open up your favourite text editor and enter the following:```
#!/bin/bash
        gmessage "Are you sure you want to shut down your computer?" -center -title "Take action" -default "Cancel" -buttons "Cancel":1,"Close OpenBox":2,"Reboot":3,"Shutdown":4


       case $? in

               1)
                        echo "Exit";;

               2)
                        killall openbox;;

               3)
                        sudo shutdown -r now;;

               4)
                        sudo shutdown -h now;;

        esac
``` and save the file somewhere you can get at it. I saved mine as ~/.exitscript so that in normal use it is hidden, but in my home directory. Take care with line wrapping, the gmessage main line in the script all needs to be on one line to work properly. Now open up obmenu or by hand in menu.xml, and edit the "Exit" entry to point to the script like so:```
<item label="Exit">
                        <action name="Execute">
                                <execute>
                                        ~/.exitscript
                                </execute>
                        </action>
                </item>
```

I also made an entry in rc.xml to set up the look and feel of gmessage```
:<application name="gxmessage">
      <decor>no</decor>
      <shade>no</shade>
      <skip_pager>yes</skip_pager>
      <skip_taskbar>yes</skip_taskbar>
      <fullscreen>no</fullscreen>
      <maximized>no</maximized>
    </application>
```

Credits to **[COLOR="Sienna"]urukrama[/COLOR]** for this.

**Xinitrc**

This file is needed to start up programs on boot. I thought i would get firefox and terminal running, along with pypanel (and feh!). My ~/.xinitrc file looks like this:```
#!/usr/bin/env bash

#starts feh to give background
sh ./.fehbg &
pypanel &
xfce4-terminal &
firefox &

exec openbox
```


This again all works OK, but I don't get the behaviour I was expecting. When terminal starts up, i have it set in rc.xml to be on desktop 2, we go there, as in we move to desktop 2 and see terminal. I have Firefox setup in rc.xml to be on desktop 1, we don't go there, as in we stay on desktop 2, even though firefox is loaded on desktop 1. It doesn't matter which way round I have these two in xinitrc, or to which desktops i point them at, the focus always stays with terminal. ***Can anyone help with this?*** Below are my entries in rc.xml in the applications section:```
<application name="xfce4-terminal">
      <decor>no</decor>
      <desktop>1</desktop>
      <maximized>yes</maximized>
      <layer>below</layer>
    </application>

    <application class="Firefox-bin">
      <decor>no</decor>
      <desktop>2</desktop>
      <maximized>yes</maximized>
      <layer>normal</layer>
      <focus>yes</focus>
    </application>
```

**Openbox Update**

Downloaded the latest debs from the openbox site for openbox (*openbox_3.4.6.1-0_i386.deb*) and obconf (*obconf_2.0.3-0_i386.deb*). Installed obconf first, which went fine, but on trying to install openbox I get an error as follows:```
sudo dpkg -i openbox_3.4.6.1-0_i386.deb
[sudo] password for user:
(Reading database ... 44589 files and directories currently installed.)
Preparing to replace openbox 3.4.4-1 (using openbox_3.4.6.1-0_i386.deb) ...
Unpacking replacement openbox ...
dpkg: error processing openbox_3.4.6.1-0_i386.deb (--install):
 trying to overwrite `/usr/lib/libobrender.so.16', which is also in package libobrender16
Errors were encountered while processing:
 openbox_3.4.6.1-0_i386.deb

``` ***Any suggestions on what I need to do to fix this?***

That's as far as I have got, next steps is to get to work on some key bindings. Openbox is so easy to work with. I am also running it on top of Gnome on my main machine it's that good :)

---

### Post by johnraff on 2008-04-22
I had that libobrender16 (and libobparser16) error too. Maybe the new openbox package contains those libraries, which the earlier one had called in as outside dependencies.
I got Openbox to install by doing this first: ```
sudo aptitude remove libobrender16 libobparser16
```Aptitude will ask you if it's OK to uninstall the existing openbox too. Go along with that and you should then be able to install the new Openbox.

---

### Post by Jose Catre-Vandis on 2008-04-22
> **johnraff said:**
> I had that libobrender16 (and libobparser16) error too. Maybe the new openbox package contains those libraries, which the earlier one had called in as outside dependencies.
I got Openbox to install by doing this first: ```
sudo aptitude remove libobrender16 libobparser16
```Aptitude will ask you if it's OK to uninstall the existing openbox too. Go along with that and you should then be able to install the new Openbox.

Thanks johnraff

---

### Post by FakeOutdoorsman on 2008-04-25
I'm trying to apply a mousebind to skippy in Openbox 3.4.6.1:

rc.xml
```
<context name="Desktop">
<mousebind button="Super_L-Left" action="Click">
<action name="Execute">
<execute>skippy --?</execute>
</action>
</mousebind>
</context>
```

.skippyrc
```
[general]
keysym = Scroll_Lock
```

How can I translate the mouse combo on the desktop to a skippy Scroll_Lock hotkey?

---

### Post by urukrama on 2008-04-26
You could use xte or [xdotool]("http://www.semicomplete.com/projects/xdotool/") to simulate a keypress. If you use xte, the execute part of your mousbind would then be:

```
<execute>xte 'key Scroll_Lock'</execute>
```

Xte is part of sudo xautomation, which is in the ubuntu repositories. To install do:

```
sudo aptitude install xautomation
```

Xte will simulate a keypress (Scroll_Lock in this example), which will then trigger skippy. Note that you need to have skippy running before this.

For more info, see [this post]("http://urukrama.wordpress.com/2008/01/29/using-pekwms-screen-edges/") on my blog (it is about Pekwm, but the principle is the same).

---

### Post by FakeOutdoorsman on 2008-04-27
Thanks, that worked perfectly.  I previously saw your post when I was trying to figure this out, but somehow missed the xte information.  My hardware isn't ancient (P4 3 GHz, 2 GB RAM), but skippy takes almost a second to raise each window defore displaying them.  Is there a way to speed it up?

Also, what is the clock you use in your [screenshot]("http://img177.imageshack.us/my.php?image=preludebrownxh8.jpg")?  I haven't been using a panel, but xclock and/or conky both have borders (even with <decor>no</decor>) due to the Openbox theme "border.Width: 1".  I would like only these to be borderless, but I don't think that can be done.

---

### Post by urukrama on 2008-04-28
> **FakeOutdoorsman said:**
> My hardware isn't ancient (P4 3 GHz, 2 GB RAM), but skippy takes almost a second to raise each window defore displaying them.  Is there a way to speed it up?

Not that I know, but skippy should raise each window only once. It remembers the window contents for later, unless you ask it to take snapshots of all the windows again (with Ctrl+Scroll_Lock).

> **FakeOutdoorsman said:**
> Also, what is the clock you use in your [screenshot]("http://img177.imageshack.us/my.php?image=preludebrownxh8.jpg")?  I haven't been using a panel, but xclock and/or conky both have borders (even with <decor>no</decor>) due to the Openbox theme "border.Width: 1".  I would like only these to be borderless, but I don't think that can be done.

The clock in that screenshot is conky. I use the following settings in my conkyrc (I post only the relevant info):

```
own_window no
own_window_type normal
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager
```

Conky never gets a border or window decoration with these settings for me. For xclock, you can set the <decor>no</decor> in the applications section of the rc.xml file. If you want it to have no border either, untick the box for "Windows retain a border when undecorated" in the "Appearance" of Obconf, or change <keepBorder>yes</keepBorder> to <keepBorder>no</keepBorder> in the rc.xml file (somewhere in the beginning of the file, just under the title layout options. This should remove the border from undecorated windows. 

I don't think you can specifty to have only xclock to have no border when undecorated but all other undecorated windows to retain a border, but perhaps you don't want that.

---

### Post by chucky chuckaluck on 2008-05-03
openbox on arch is wicked fast. (how's that for random?)

---

### Post by InfinityCircuit on 2008-05-11
Here is my newest pipe menu, which I worked long and hard on because I suck at scripting.  It lists the open windows on all workspaces and lets you click on one to open it.  It is a clone of client-list-menu except that it doesn't discriminate by workspace.

```
#!/bin/bash

RAISE="wmctrl -i -a"
IFS="0"

echo "<openbox_pipe_menu>"

for win in $(wmctrl -l | cut -d ' ' -f 5- | tr '\n' '0')
do
        echo "<item label=\""$win"\">"
        echo "<action name=\"Execute\"><execute>$RAISE $(wmctrl -l | grep "$win" | awk '{print $1}')</execute></action>"
        echo "</item>"
done

echo "</openbox_pipe_menu>"

```

---

### Post by MedellinManDem on 2008-05-13
Does anyone know if there's anyway to add more workspaces to an Openbox/GNOME session? At present I only have four, I wnt more, but the workspace switcher doesn't seem to let me add anymore.

---

### Post by Sockerdrickan on 2008-05-13
rightclick on one of them>settings>number of workspaces<--change

---

### Post by MedellinManDem on 2008-05-13
> **Tux0r said:**
> rightclick on one of them>settings>number of workspaces<--change

Thanks, but I figured it out hence why my post was deleted.

I hadn't installed "obconf".

Thanks again.

---

### Post by watchitman on 2008-05-15
I'm using gmrun and it's in my autostart script. It pops up immediately on first login, even before the gnome settings load so I get to see it all ugly before the gtk theme kicks in. This is annoying. Is there a way to suppress the popup on first login, similar to the way you can use --quite on gnome-do?

---

### Post by urukrama on 2008-05-15
> **watchitman said:**
> I'm using gmrun and it's in my autostart script. It pops up immediately on first login, even before the gnome settings load so I get to see it all ugly before the gtk theme kicks in. This is annoying. Is there a way to suppress the popup on first login, similar to the way you can use --quite on gnome-do?

You don't need to have gmrun constantly running to use it. You can bind it to a keybinding (say Alt+F2), which would bring it up whenever you press those keys. Doing so means you don't have to load gmrun when you start openbox.

But to answer your question, you can use the following command to load gmrun only after gnome-settings-daemon loads:

```
(sleep 3 && gmrun) &
```

The autostart file also loads the applications in the order they appear in that file. So if you mention gmrun before gnome-settings-daemon, it will load gmrun first and then only gnome-settings-daemon.

---

### Post by watchitman on 2008-05-15
Thanks but even with (sleep 3 && gmrun) &, it still pops up on login. I'll have to try the keybinding. :)

---

### Post by urukrama on 2008-05-15
> **watchitman said:**
> Thanks but even with (sleep 3 && gmrun) &, it still pops up on login. I'll have to try the keybinding. :)

If you add gmrun to your autostart file it will always pop up on login (as you ask it to do so). The 'sleep 3' command only makes it load with a delay of 3 seconds.

---

### Post by dbbolton on 2008-05-17
Anyone know why this thread was put in the archive?

---

### Post by urukrama on 2008-05-17
I believe all existing threads of the "Absolute Beginner Talk" and "Main Support Categories" forums were put into the archive. I don't really see why, though.

---

### Post by chris4585 on 2008-05-17
One thing in openbox I cannot figure out, is there any way I can get the openbox menu to show up on a command? using a bin file even, anyone?

---

### Post by chris4585 on 2008-05-17
> <keybind key="C-Down">
<action name="Execute">
<execute>amixer -q set PCM 2- unmute</execute>
</action>
</keybind>
<keybind key="C-Up">
<action name="Execute">
<execute>amixer -q set PCM 2+ unmute</execute>
</action>
</keybind>

Thank you urukrama! I needed something like this, I made 2 launchers on my fbpanel for volume up/down and increased 2 to 10, works great

---

### Post by urukrama on 2008-05-17
> **chris4585 said:**
> Thank you urukrama! I needed something like this, I made 2 launchers on my fbpanel for volume up/down and increased 2 to 10, works great

If you want something on your panel to control the volume, you could also use something like [gvtray]("http://code.google.com/p/gtk-tray-utils/"), or its [modification]("http://david.chalkskeletons.com/blog/?p=20"). It rests in the system tray of your panel.

As for bringing up the Openbox menu with a command, you can use xdotool or xte to simulate a keypress (the keybinding of your root menu in Openbox). I wrote about this (but in a different context) [here]("http://urukrama.wordpress.com/2008/01/29/using-pekwms-screen-edges/").

---

### Post by chris4585 on 2008-05-17
> **urukrama said:**
> If you want something on your panel to control the volume, you could also use something like [gvtray]("http://code.google.com/p/gtk-tray-utils/"), or its [modification]("http://david.chalkskeletons.com/blog/?p=20"). It rests in the system tray of your panel.

As for bringing up the Openbox menu with a command, you can use xdotool or xte to simulate a keypress (the keybinding of your root menu in Openbox). I wrote about this (but in a different context) [here]("http://urukrama.wordpress.com/2008/01/29/using-pekwms-screen-edges/").

Thanks for letting me know about those system trays, but I like how I have my volume luanchers setup, they work perfect, and as for xte, THANK YOU! the 'only' problem with it is with the way I have my launcher setup on my fbpanel, if something is covering a very small area when I hit the luancher it will right click on that area, and that area is meant to be my desktop for my openbox menu, so if something is in that very small area it might not click and pop up my openbox menu.  It took me forever to figure out the command for xte

```
xte 'mousemove 160 1045' 'mouseclick 3'
```

I kept trying to do --option until I googled and figured out you had to use 'option'.

Its not 100% perfect, as if I set a key combo with it, I'll try that another day, I'm too lazy atm :lolflag:

---

### Post by eriqjaffe on 2008-05-17
> **urukrama said:**
> If you want something on your panel to control the volume, you could also use something like [gvtray]("http://code.google.com/p/gtk-tray-utils/"), or its [modification]("http://david.chalkskeletons.com/blog/?p=20"). It rests in the system tray of your panel.There's also [VolWheel]("http://oliwer.net/weblog/pivot/entry.php?id=2"), which I use on my desktop and laptop.

---

### Post by chris4585 on 2008-05-19
Yay, it took me nearly 5 days but I read the whole random openbox chatter, I've learned quit a bit.  I plan on making a guide/tutorial sometime, might be a while, I want to validate everything first.  I'm going to give credit to most everyone in this thread, I might have to reread it again to make sure of some things.  Thanks everyone who joined in this thread, I've been using openbox the past 3 weeks, and I absolutely love it.

:guitar:

---

### Post by urukrama on 2008-05-19
> **chris4585 said:**
> Yay, it took me nearly 5 days but I read the whole random openbox chatter, I've learned quit a bit.  I plan on making a guide/tutorial sometime, might be a while, I want to validate everything first.  I'm going to give credit to most everyone in this thread, I might have to reread it again to make sure of some things.

Have you seen my guide (link in signature). Before I wrote it, I went through this thread and added nearly everything that was mentioned here.

---

### Post by chris4585 on 2008-05-19
> **urukrama said:**
> Have you seen my guide (link in signature). Before I wrote it, I went through this thread and added nearly everything that was mentioned here.

Yes, I have, its a very impressive guide might I say :)

One idea that came to me a moment ago is listing possible setups with apps that use the least memory to the most memory as suggestions

Edit:

P.S. have you seen my fbpanel setup's as seen in my signature?

---

### Post by urukrama on 2008-05-25
For those who are interested: I have updated and thoroughly revised my [Openbox guide]("http://urukrama.wordpress.com/openbox-guide/"). I wrote about what exactly changed in [this post]("http://urukrama.wordpress.com/2008/05/26/update/").

The guide is a lot more comprehensive now. If you have any suggestions for improvements, please let me know.

Sorry for the shameless self-promotion :p

---

### Post by scottro on 2008-05-25
Shucks, that's one of the best openbox guides around.  Nothing to apologize for--it's not self-promotion, it's letting people know about an excellent resource.

---

### Post by dbbolton on 2008-05-27
Right now I have window decorations turned off for all windows, and I enabled the option to retain a border around undecorated windows.

Is it possible to make it so that only the focused window has a border?

---

### Post by el mariachi on 2008-05-27
that would be interesting

---

### Post by urukrama on 2008-05-27
> **dbbolton said:**
> Right now I have window decorations turned off for all windows, and I enabled the option to retain a border around undecorated windows.

Is it possible to make it so that only the focused window has a border?

Not in the rc.xml as far as I know. But you could edit your theme so that the inactive border has the same colour as your gtk/qt theme and is thus practically invisible.

Look for these two lines:

```
window.active.border.color: 
window.inactive.border.color:
```

EDIT: I got excited and tried it out. Behold the borders [here]("http://ubuntuforums.org/showpost.php?p=5057737&postcount=894").

---

### Post by dbbolton on 2008-05-27
> **urukrama said:**
> Not in the rc.xml as far as I know. But you could edit your theme so that the inactive border has the same colour as your gtk/qt theme and is thus practically invisible.

Look for these two lines:

```
window.active.border.color: 
window.inactive.border.color:
```

EDIT: I got excited and tried it out. Behold the borders [here]("http://ubuntuforums.org/showpost.php?p=5057737&postcount=894").
I actually tried something like this earlier. The problem is that my terminal is almost always darker than the other windows, so the border will stand out on it. I suppose I could go back tilda.

Oddly, I had to enable decoration for pypanel, otherwise it got a border. Maybe if I do the same for tilda it will end up borderless.

---

### Post by dbbolton on 2008-05-29
Any idea what this means?

[IMG]http://i103.photobucket.com/albums/m128/envyouraudience/Screenshot-OpenboxSyntaxError.png[/IMG]

Here is line 234 of my menu file:

```

      </openbox_menu>

```

and it is the last line.

---

### Post by RedSquirrel on 2008-05-29
> **dbbolton said:**
> Any idea what this means?

...

Here is line 234 of my menu file:

```

      </openbox_menu>

```and it is the last line.

You have an error in your menu.xml file. Have a look in your ~/.xsession-errors to see if there is more detailed information about the error. You can also post your menu.xml file.

---

### Post by dbbolton on 2008-06-01
I just decided to revert to the default menu. It seems to have eliminated the error.

On my other computer, I used some special characters as icons in my menu :D

[IMG]http://i103.photobucket.com/albums/m128/envyouraudience/newobmenu.png[/IMG]

---

### Post by chris4585 on 2008-06-01
Now that's neat dbbolton.

I"m quite happy with my new discovery, I finally found a way to get the openbox menu to appear from a launcher.

Info here: [http://crunchbang.org/archives/2008/03/14/invoke-openboxs-menu-with-xdotool/]("http://crunchbang.org/archives/2008/03/14/invoke-openboxs-menu-with-xdotool/")

---

### Post by el mariachi on 2008-06-01
dbbolton did you get that from the special symbols database (is that it's name?) or is it a "special" font (seems artwiz to me)

---

### Post by dbbolton on 2008-06-01
> **chris4585 said:**
> Now that's neat dbbolton.

I"m quite happy with my new discovery, I finally found a way to get the openbox menu to appear from a launcher.

Info here: [http://crunchbang.org/archives/2008/03/14/invoke-openboxs-menu-with-xdotool/](http://crunchbang.org/archives/2008/03/14/invoke-openboxs-menu-with-xdotool/)

Interesting. I'm going to try this with the pypanel launcher.

> **el mariachi said:**
> dbbolton did you get that from the special symbols database (is that it's name?) or is it a "special" font (seems artwiz to me)
The normal text is artwiz, but I'm pretty sure that the special characters are DejaVu Sans Mono, because artwiz doesn't support special characters and reverts to the system default font when they appear.

I found them in OpenOffice Writer, by clicking Insert > Special Character, choosing DejaVu Sans Mono as the font, and then scrolling to the bottom.

---

### Post by RedSquirrel on 2008-06-01
> **dbbolton said:**
> I just decided to revert to the default menu. It seems to have eliminated the error.

It might have been a mismatched tag or something.


> **dbbolton said:**
>  On my other computer, I used some special characters as icons in my menu :D

I don't think I've ever seen anything like that in a menu. Great job. :)

---

### Post by Protoss on 2008-06-02
Okay so I finally got tired of Gnome getting sluggish randomly, so I tried out OpenBox and am really loving it. 
I've got pypanel running, and I like its minimalism and transparency but wish it had plugins and whatnot. Is there a panel that has the awesome transparency (where the entire panel is transparent, even the systray and taskbar icons) of pypanel, but has a bit more functionality?

---

### Post by chris4585 on 2008-06-02
> **Protoss said:**
> Okay so I finally got tired of Gnome getting sluggish randomly, so I tried out OpenBox and am really loving it. 
I've got pypanel running, and I like its minimalism and transparency but wish it had plugins and whatnot. Is there a panel that has the awesome transparency (where the entire panel is transparent, even the systray and taskbar icons) of pypanel, but has a bit more functionality?

closes thing you'll find is fbpanel, the only thing that it can't do is make all of the systray transparent. Check my sig for more.

Perlpanel has tons of plugins I hear, but I'm not sure if its Transparent.

---

### Post by dbbolton on 2008-06-06
I made a theme info script for Openbox. I've tried it on both my computers with success, but I would really appreciate some other input:

[http://danielsudo.blogspot.com/2008/06/openbox-theme-info-script.html](http://danielsudo.blogspot.com/2008/06/openbox-theme-info-script.html)

---

### Post by FakeOutdoorsman on 2008-06-06
> **dbbolton said:**
> I made a theme info script for Openbox. I've tried it on both my computers with success, but I would really appreciate some other input:

[http://danielsudo.blogspot.com/2008/06/openbox-theme-info-script.html](http://danielsudo.blogspot.com/2008/06/openbox-theme-info-script.html)
Fails for me because I don't have feh, although your blog mentions that it needs feh, or at least that's the impression I get.  I suggest that if it doesn't detect .fehbg that it skips wallpaper detection:
```
python obinfo.py 
Traceback (most recent call last):
  File "obinfo.py", line 24, in <module>
    for line in open(os.path.expanduser("~/.fehbg")):
IOError: [Errno 2] No such file or directory: '/home/frinkahedron/.fehbg'
```

---

### Post by dbbolton on 2008-06-06
> **FakeOutdoorsman said:**
> Fails for me because I don't have feh, although your blog mentions that it needs feh, or at least that's the impression I get.  I suggest that if it doesn't detect .fehbg that it skips wallpaper detection:
```
python obinfo.py 
Traceback (most recent call last):
  File "obinfo.py", line 24, in <module>
    for line in open(os.path.expanduser("~/.fehbg")):
IOError: [Errno 2] No such file or directory: '/home/frinkahedron/.fehbg'
```
Thanks. Give the attachment a go :D

I'm going to apply the same idea to the other files shortly.

---

### Post by FakeOutdoorsman on 2008-06-06
> **dbbolton said:**
> Thanks. Give the attachment a go :D

I'm going to apply the same idea to the other files shortly.
That got rid of the feh error.  As for showing the distro, perhaps you can refer to "/etc/issue".

---

### Post by dbbolton on 2008-06-06
> **FakeOutdoorsman said:**
> That got rid of the feh error.  As for showing the distro, perhaps you can refer to "/etc/issue".
Thanks. I basically rewrote the whole thing. It should work with GNOME and openbox now. There are a few options after line 20.

[http://envyouraudience.googlepages.com/themeinfo.py](http://envyouraudience.googlepages.com/themeinfo.py)

---

### Post by rolypolycat on 2008-06-19
Hello!
I installed Openbox on a gutsy minimal install. I installed xfce4-mcs-manager to handle settings for icons, etc, and following urukrama's guide and the autostart on the openbox page, I came up with this for an autostart file:

# This shell script is run before Openbox launches.
# Environment variables set here are passed to the Openbox session.
#!/bin/sh
ivman &
xfce4-mcs-manager &
eval `cat $HOME/ .fehbg` &
xscreensaver -no-splash &
(sleep 3 && fbpanel) &

Even though I have xfce-mcs-manager installed, and it is in the file, it obviously doesn't autostart. When I run pcmanfm, it gives me an error message about my icon theme not being right because this file isn't running.
So, I tried making my own .gtkrc.mine file, and this is what it looks like

#--THEME AUTO-WRITTEN DO NOT EDIT
include "/home/shell/.icons"
gtk-icon-theme-name = "oxy-gnome"

I ran the command xfce4-mcs-manager in a terminal; tells me the command doesn't exist. When I add the item to obmenu, it saves okay, but when I come back, the entry is just generic-it won't run anything. 
Can anyone tell me what I'm doing wrong?:confused: I have the latest openbox, everything else from Synaptic: pcmanfm, gdm, and accessories: obmenu, obconf, xfce4-mcs-manager, gtk-engines installed. Why can't pcmanfm find my icons, and why doesn't xfce4-mcs-manager load like it's supposed to?
Thanks in advance for any help!

---

### Post by urukrama on 2008-06-19
Try the command xfce-mcs-manager (not xfce**4**-mcs-manager). Does that work?

---

### Post by rolypolycat on 2008-06-19
Trying xfce-mcs-manager in the startup file didn't work, either. Something else that's strange: when I run the command in a terminal, a lot of info whizzes by, essentially with variations on the same thing.
"Warning:  No symbols defined for <169> keycode 233; <16A>, keycode 234, etc.; all the way to <17F>, keycode 255. After that, the icons show up like they're supposed to for that session only.
Xfce-mcs-manager doesn't need thunar to work, does it? I'm not runing thunar; I'm running pcmanfm. I figure with all the stuff thunar and xfce drag in, I might as well be running xfce. I wanted something even lighter; that's why I went with openbox.If thunar was a dependancy, it should have been installed with xfce-manager, I would think? Either that, or my computer is illiterate and can't read my autostart file ;)
I removed fbpanel and installed xfce-panel, with which I'm more familiar. It loads nicely, but xfce-mcs-manager still doesn't load and says the same thing in a terminal. Just what is this "gtk-2.0 file software wants? It's not listed by that name in synaptic. I've tried installing gtk-engines, libgtk; it seems to no avail.Does it actually have another name?
By the way, several times I've re-done my computer with openbox, I have trouble with the menu. I'll edit it fine in obmenu, save it, but later, when I come back to add more entries, it says there are unsaved changes, even though I've saved them. (and saved them, and saved them again)If I just ignore the message, and quit, the new entries don't show up. Why is that?; does obmenu only allow so many entries before it must be edited by hand?

---

### Post by rolypolycat on 2008-06-20
Well, I made a .gtkrc-2.0 file, added the lines gtk-icon-theme-name = "oxy-gnome", and restarted. It worked! I don't know why it couldn't find the icons file in gtkrc-mine,though; I thought the latter file overrode the settings in gtkrc-2.0. Since I now have my nice icon set,(instead of that ugly one) I'm not fussing.
So far I managed to add my programs to my menu all in one shot, and they are there. I still don't know how or why obmenu decides out of the blue not to save any more of my changes, but I'll take advantage of it for now. Thank you!

---

### Post by dbbolton on 2008-06-21
I just did a minimal install with Ubuntu server. It took a little longer than I thought, but it is wicked fast. I have a couple of concerns though.

First of all is my choice of ReiserFS. It seems that it runs some check at boot to determine whether the filesystem is "clean", and it takes like 8 seconds. I don't remember ext3 doing anything like this. However, it seems that filebrowsing is a lot faster with Reiser. I've also heard that XFS is pretty fast, so I might reformat and try it.

Second of all, I am using SLiM rather than GDM. It seems all right, but after I've logged in, it still uses 2-4 MB of memory. From what I remember, GDM only uses like 400 KB.

Thoughts?

---

### Post by beebelo on 2008-06-26
I'm setting up Openbox for the first time, using Urukrama's excellent howto.  I am unable to make the Debian menu show in the Openbox menu, though I've followed directions.  I have 'menu' and 'menu-xdg' installed and the Debian menu works fine in Gnome.  

Following the  [Openbox Documentation:Help:Menus]("http://icculus.org/openbox/index.php/Help:Menus"), I added this to the root menu section of ~/.config/openbox/menu.xml:  
```
<menu id="Debian" />
```

It also says to add the following to the <menu> section of rc.xml.:  
```
<file>/var/lib/openbox/debian-menu.xml</file>
<file>debian-menu.xml</file>
```
That's the most likely problem, since my system doesn't have any file named "debian-menu.xml".  I did find a file "debian-menu.menu" in directory /var/lib/menus-xdg, and substituting that didn't work.  

Anyone using the Debian menu on your Openbox menu?  Any suggestions?  I am running Ubuntu Studio 8.04.

Thanks.

---

### Post by dbbolton on 2008-06-26
> **beebelo said:**
> I'm setting up Openbox for the first time, using Urukrama's excellent howto.  I am unable to make the Debian menu show in the Openbox menu, though I've followed directions.  I have 'menu' and 'menu-xdg' installed and the Debian menu works fine in Gnome.  

Following the  [Openbox Documentation:Help:Menus]("http://icculus.org/openbox/index.php/Help:Menus"), I added this to the root menu section of ~/.config/openbox/menu.xml:  
```
<menu id="Debian" />
```

It also says to add the following to the <menu> section of rc.xml.:  
```
<file>/var/lib/openbox/debian-menu.xml</file>
<file>debian-menu.xml</file>
```
That's the most likely problem, since my system doesn't have any file named "debian-menu.xml".  I did find a file "debian-menu.menu" in directory /var/lib/menus-xdg, and substituting that didn't work.  

Anyone using the Debian menu on your Openbox menu?  Any suggestions?  I am running Ubuntu Studio 8.04.

Thanks.
Do you have the packages "menu" and "menu-xdg" installed?

---

### Post by beebelo on 2008-06-26
> Originally posted by **dbbolton**
Do you have the packages "menu" and "menu-xdg" installed? 

Yes. ;)

> Originally Posted by **beebelo**  
I'm setting up Openbox for the first time, using Urukrama's excellent howto. I am unable to make the Debian menu show in the Openbox menu, though I've followed directions. *I have 'menu' and 'menu-xdg' installed and the Debian menu works fine in *Gnome. 

---

### Post by RedSquirrel on 2008-06-26
Try running:

```
sudo update-menus
```

That should generate the /var/lib/openbox/debian-menu.xml file.

---

### Post by beebelo on 2008-06-27
> **RedSquirrel said:**
> Try running:

```
sudo update-menus
```

That should generate the /var/lib/openbox/debian-menu.xml file.

Oh, shoot, I've already done that, as root and also as non-root!  

I'm familiar with using the debian menu.  It works; I've checked it after installing apps and running ```
sudo update-menus -v
```.  

But I never paid attention to where update-menus is putting stuff.  What is  /var/lib/menus-xdg/debian-menu.menu ?  I swear, I've searched the entire file system, and there is no "debian-menu.xml".  Guess I need to read the docs for "menus" and "menus-xdg".  

I think Ubuntu Studio is based on Ubuntu Server.  Could that have something to do with this?   

Also, maybe something is wrong with the Openbox config.  If I don't figure this out I'll post the appropriate parts of my Openbox config files...

Any other suggestions?

---

### Post by RedSquirrel on 2008-06-27
> **beebelo said:**
> ... I think Ubuntu Studio is based on Ubuntu Server.  Could that have something to do with this?   

Also, maybe something is wrong with the Openbox config.  If I don't figure this out I'll post the appropriate parts of my Openbox config files...

Any other suggestions?

You should have the script /etc/menu-methods/openbox. It should create the debian-menu.xml file under /var/lib/openbox (OR ~/.config/openbox if you ran 'update-menus' as your regular user). Do you have that script? What's in it? It needs to be executable as well:

```
sudo chmod +x /etc/menu-methods/openbox
```

In the past, I have run Openbox on Debian and the Debian menu works fine there. Maybe there's a bug with the openbox package on Ubuntu. You might have to look around (or switch to Debian :D).

[https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)

---

### Post by beebelo on 2008-06-29
> **RedSquirrel said:**
> You should have the script /etc/menu-methods/openbox. It should create the debian-menu.xml file under /var/lib/openbox (OR ~/.config/openbox if you ran 'update-menus' as your regular user). Do you have that script? What's in it? It needs to be executable as well:

Awesome!  I don't think I saw this script mentioned anywere.  I did find the script, just as you say.  Here is the content:

```
#!/usr/bin/install-menu

!include menu.h

compat="menu-1"

outputencoding="UTF-8"
genmenu="debian-menu.xml"
rootprefix="/var/lib/openbox/"
userprefix=".config/openbox/"
treewalk="(M)"

function xml_escape($s) = replace(replace(replace(replace(replace($s, \
                                "&",  "&amp;"), \
                                ">",  "&gt;"), \
                                "<",  "&lt;"), \
                                "'",  "&apos;"), \
                                "\"", "&quot;")
```
I will execute and get back with the result.

Thank you, RedSquirrel!

---

### Post by beebelo on 2008-06-29
Ok here's what's happening:

After making sure it's executable, I ran the script from a terminal in the window manager (both gnome and openbox), and I got: 
```
Openbox-Message: A window manager is already running on screen 0
```
Then I ran it from a console outside of the window manager and got:  
```
/etc/menu-methods$sh openbox
openbox: 3: !include: not found
openbox: 13: syntax error: "(" unexpected
```
The file "menu.h" *does exist* in this directory: 
```
/etc/menu-methods$ ls
gnome-panel-data    menu.h    translate_menus
gnome-vfolder-user  menu-xdg  xdg-desktop-entry-spec-apps
lang.h              openbox   xdg-desktop-entry-spec-dirs
menu.config         README    xdg-desktop-entry-spec-sessions

```
Why would it say the !include is not found, when it's right there?  Is it looking in the wrong place?  As for the unexpected "(", I wouldn't have a clue what do do there.

Thanks for any further direction with this.

---

### Post by jjgomera on 2008-06-29
Hello

Here is another openbox user with a problem

I like use smplayer to play video, but in openbox it draw out of screen, see attachment, i can maximize to double click but id like to see menus

xprop say that over it:

> ...
XdndAware(ATOM) = BITMAP
_MOTIF_DRAG_RECEIVER_INFO(_MOTIF_DRAG_RECEIVER_INFO) = 0x6c, 0x0, 0x5, 0xb7, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x58, 0xb7, 0x10, 0x0, 0x0, 0x0
_NET_WM_NAME(UTF8_STRING) = 0x53, 0x4d, 0x50, 0x6c, 0x61, 0x79, 0x65, 0x72
WM_CLIENT_LEADER(WINDOW): window id # 0x2e00003
_NET_WM_PID(CARDINAL) = 10060
_NET_WM_WINDOW_TYPE(ATOM) = _NET_WM_WINDOW_TYPE_NORMAL
_MOTIF_WM_HINTS(_MOTIF_WM_HINTS) = 0x2, 0x1, 0x7e, 0x0, 0x0
WM_PROTOCOLS(ATOM): protocols  WM_DELETE_WINDOW, WM_TAKE_FOCUS, _NET_WM_PING
WM_NAME(STRING) = "SMPlayer"
WM_LOCALE_NAME(STRING) = "es_ES.UTF-8"
WM_CLASS(STRING) = "smplayer", "Smplayer"
WM_HINTS(WM_HINTS):
		Client accepts input or input focus: True
		Initial state is Normal State.
		bitmap id # to use for icon: 0x2e001c9
		bitmap id # of mask for icon: 0x2e001cc
		window id # of group leader: 0x2e00003
WM_NORMAL_HINTS(WM_SIZE_HINTS):
		[B]user specified location: -32, -304
		program specified location: -32, -304[/B]
		user specified size: 704 by 493
		program specified size: 704 by 493
		program specified minimum size: 169 by 125
		window gravity: NorthWest
WM_CLIENT_MACHINE(STRING) = "ordenata"

in bold i think is the problem, but how can i change it

i've added this to rc.xml but dont work:

> <applications>
  <application class="smplayer">
    <decor>yes</decor>
    <position>
	<x>200</x>
	<y>200</y>
    </position>
  </application>
</applications>

Thanks in advance

---

### Post by chochem on 2008-06-29
I just check the comments in the rc.xml file, in particular:
```
  <application name="first element of window's WM_CLASS property (see xprop)"
              class="second element of window's WM_CLASS property (see xprop)"
```

I don't know if case is important in this context but if it is, then according to your xprop printout you should probably uppercase the S in smplayer. Or switch to name="smplayer". 

Hope it helps.

---

### Post by rolypolycat on 2008-06-30
Hello!

I realize this may be a stupid question, but I am a bit puzzled by these terms.
First of all, thanks to urukrama's great guide and the help I got on this thread. For the first time since starting linux 3 years ago, I have successfully built a desktop from bits and pieces, and everything is working.:KS Now that I've played around a bit, I'd like to try other stuff; ie, other bits and pieces. That's where my question comes in.
Exactly what is the difference between a panel, task list, system tray, launchers, docks, and pagers?:confused: I thought they all were part of the panel, as one unit,(I use the xfce4-panel), but from what I've read here, these can be used separately? Does a panel come with all this stuff: a clock, virtual desktops, space to quicklaunch programs, or is this all handled separately by other programs, and just lumped under the panel? Would using a bunch of little programs to get the same effect actually help memory use on my older machine, or just one do-it-all-panel-thingy?
System trays and panels sound like the same thing to me; likewise, docks and pagers. Are these different, or just different words for the same programs?
These are the basic functions I'm shooting for: some way to have at least 3 virtual desktops, a place to iconify or minimize a program, and a few things like a clock, terminal, maybe a few shortcuts for much used programs,(but not on the desktop) and in some way that uses even less memory.
Also what is the difference between a server install, alternate install and a cli install, apart from the size of the disk's download?:confused: Do all these methods basically install, or come pre-installed, with the same initial setup; then you add everything else.
Sorry for so many questions, but I want to learn more before I start tampering with the working setup I have now. Right now, I'm using pcmanfm, openbox,and xfce4-panel. I like the first 2, but I'm open to suggestions on the rest.
Thanks in advance!

---

### Post by urukrama on 2008-06-30
> **rolypolycat said:**
> Exactly what is the difference between a panel, task list, system tray, launchers, docks, and pagers?:confused: I thought they all were part of the panel, as one unit,(I use the xfce4-panel), but from what I've read here, these can be used separately? Does a panel come with all this stuff: a clock, virtual desktops, space to quicklaunch programs, or is this all handled separately by other programs, and just lumped under the panel? Would using a bunch of little programs to get the same effect actually help memory use on my older machine, or just one do-it-all-panel-thingy?

Most panels come with system trays/notification areas (where some applications, like many media players, place an icon), task lists (which shows which applications are running), pagers (workspace switchers), a clock (which shows the time) and launchers (icons to launch applications). These are generally not separate applications, but part of the panel (as with pypanel). Some panels also allow for additional plugins or applets (like xfce4-panel, perl-panel and gnome-panel).

There are, however, some applications available that don't provide all this, and focus only on a single function. Thus docker, trayer or peksystray only provide a system tray; netwmpager and ipager only provide a pager or workspace switcher, and tint task manager only provides a task list; or idesk, and bbbutton which only provide launchers.

Note that the number of virtual desktops is specified by Openbox, but a pager will make it easier to switch workspaces.


A dock is generally a combination of a launcher and a task list (and sometimes with a few added functions). Examples are AWN, Cairodock, bbdock, etc.

> **rolypolycat said:**
> These are the basic functions I'm shooting for: some way to have at least 3 virtual desktops, a place to iconify or minimize a program, and a few things like a clock, terminal, maybe a few shortcuts for much used programs,(but not on the desktop) and in some way that uses even less memory.

It all depends on your aesthetics and needs/wants. If you'd like to have them all in one place, use a panel that has all those functions, like xfce4-panel which you are using now. Otherwise you can use separate applications for each of those functions (see my guide for available options, I gave quite a list there). I am not sure what other panels have a terminal/command line plugin, though you could use gmrun for that.

I'd suggest you install a few of those applications and play around with them. Find out what you like best. Each app has its own character, as well as advantages and disadvantages.

I generally use bbpager as a pager, docker as a sytem tray, and lal as a clock. All three are loaded into Openbox' dock. I don't use a task list. See [this post]("http://ubuntuforums.org/showpost.php?p=5284539&postcount=873") to get an idea of what it looks like.

> **rolypolycat said:**
> Also what is the difference between a server install, alternate install and a cli install, apart from the size of the disk's download?:confused: Do all these methods basically install, or come pre-installed, with the same initial setup; then you add everything else.

The Alternate Install CD allows you to install Ubuntu without having to load the LiveCD. This is very useful for computers that don't have enough RAM to load the Live dekstop and the installer. With the Alternate Install CD you can also do a command-line install, which will install only the Ubuntu base, without a graphical environment (X), a desktop environment (Gnome, KDE, XFCE) and with hardly any applications (no OpenOffice, no Firefox, etc.). Whatever applications you want to use you'll have install yourself. [Aysiu has a guide for this]("http://psychocats.net/ubuntu/minimal"), if you need help installing Ubuntu this way.

A server install is also a command-line install, but comes with additional server applications and a different kernel optimised for server use (as far as I remember).

---

### Post by El_Belgicano on 2008-06-30
Hello all,
I'm using pypanel and xdotool to make my root-menu display on a click in de desktops area of pypanel, is there a way to make it appear at a predefined position?
Because I want to get rid of the fact it's covering pypanel, and make it appear some pixels above that zone.
Thanks

---

### Post by RedSquirrel on 2008-06-30
> **beebelo said:**
> Awesome!  I don't think I saw this script mentioned anywere.  I did find the script, just as you say.  Here is the content:

```
#!/usr/bin/install-menu

!include menu.h

compat="menu-1"

outputencoding="UTF-8"
genmenu="debian-menu.xml"
rootprefix="/var/lib/openbox/"
userprefix=".config/openbox/"
treewalk="(M)"

function xml_escape($s) = replace(replace(replace(replace(replace($s, \
                                "&",  "&amp;"), \
                                ">",  "&gt;"), \
                                "<",  "&lt;"), \
                                "'",  "&apos;"), \
                                "\"", "&quot;")
```


Is that all there is in that file? If so, you're missing several lines. I'm running Gentoo, but just for interest I downloaded the openbox deb from [http://packages.ubuntu.com/hardy/openbox](http://packages.ubuntu.com/hardy/openbox) and unpacked it. Here is the /etc/menu-methods/openbox file from that archive:

```
#!/usr/bin/install-menu

!include menu.h

compat="menu-1"

outputencoding="UTF-8"
genmenu="debian-menu.xml"
rootprefix="/var/lib/openbox/"
userprefix=".config/openbox/"
treewalk="(M)"

function xml_escape($s) = replace(replace(replace(replace(replace($s, \
                "&",  "&amp;"), \
                ">",  "&gt;"), \
                "<",  "&lt;"), \
                "'",  "&apos;"), \
                "\"", "&quot;")

supported
    x11=     nstring(level(), "  ") "<item label='" xml_escape(title()) "'>\n" \
             nstring(level(), "  ") "  <action name='Execute'><execute>" xml_escape($command) "</execute></action>\n" \
         nstring(level(), "  ") "</item>\n"
    text=    nstring(level(), "  ") "<item label='" xml_escape(title()) "'>\n" \
             nstring(level(), "  ") "  <action name='Execute'><execute>" xml_escape(term()) "</execute></action>\n" \
         nstring(level(), "  ") "</item>\n"
    wm=      nstring(level(), "  ") "<item label='" xml_escape(title()) "'>\n" \
             nstring(level(), "  ") "  <action name='Restart'><execute>" xml_escape($command) "</execute></action>\n" \
         nstring(level(), "  ") "</item>\n"
endsupported

startmenu=   nstring(level(), "  ")  "<menu id='" xml_escape(title()) "' label='" xml_escape(title()) "'>\n"
endmenu=     nstring(level(), "  ")  "</menu>\n"

preoutput=   "<?xml version=\"1.0\" encoding=\"UTF-8\"?>\n\n<!-- Automatically generated file. Do not edit (see /usr/share/doc/menu/html) -->\n\n<openbox_menu xmlns=\"http://openbox.org/\"\n        xmlns:xsi=\"http://www.w3.org/2001/XMLSchema-instance\"\n        xsi:schemaLocation=\"http://openbox.org/\n                file:///usr/share/openbox/menu.xsd\">\n\n"
postoutput=  "\n</openbox_menu>\n"

```> **beebelo said:**
> After making sure it's executable, I ran the script from a terminal ...

You cannot do that. It is a "/usr/bin/install-menu" script. The file is part of the menu system and must be run using the menu commands (e.g., update-menus, install-menu). There should be some documentation under /usr/share/doc/menu that you can read. ;)


Edit: I haven't tried Openbox on the latest Ubuntu (nor the "Studio" version) so I cannot provide an evaluation of the Debian menu on that system. If you can't get it to work, you may have to settle for one of the alternative methods of setting up a menu in Openbox.

---

### Post by chochem on 2008-06-30
Now that the issue of pagers, and panels, and docks (oh my) has come up...

I'm using the 'visibility' pager and quite happy with it, except that it's sometimes 'sticky' (i.e. appears on all desktops) and sometimes not, that is only on the desktop on which it was called (killing it and restarting it a couple of times will usually get it sticky). Normally this isn't an openbox problem as you can set these things in the 'applications' section of the rc.xml. However, "xprop | grep WM" on it yields the following:
```
WM_STATE(WM_STATE):
_NET_WM_DESKTOP(CARDINAL) = 4294967295
_NET_WM_ALLOWED_ACTIONS(ATOM) = _NET_WM_ACTION_CHANGE_DESKTOP, _NET_WM_ACTION_CLOSE, _NET_WM_ACTION_MOVE, _NET_WM_ACTION_MINIMIZE, _NET_WM_ACTION_FULLSCREEN, _NET_WM_ACTION_ABOVE, _NET_WM_ACTION_BELOW
_NET_WM_ICON(CARDINAL) = 48, 48, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, [etc.]
_NET_WM_VISIBLE_ICON_NAME(UTF8_STRING) = 0x55, 0x6e, 0x6e, 0x61, 0x6d, 0x65, 0x64, 0x20, 0x57, 0x69, 0x6e, 0x64, 0x6f, 0x77
_NET_WM_VISIBLE_NAME(UTF8_STRING) = 0x55, 0x6e, 0x6e, 0x61, 0x6d, 0x65, 0x64, 0x20, 0x57, 0x69, 0x6e, 0x64, 0x6f, 0x77
WM_HINTS(WM_HINTS):
WM_NORMAL_HINTS(WM_SIZE_HINTS):
_NET_WM_STATE(ATOM) = _NET_WM_STATE_SKIP_TASKBAR, _NET_WM_STATE_SKIP_PAGER
_MOTIF_WM_HINTS(_MOTIF_WM_HINTS) = 0x2, 0x0, 0x0, 0x0, 0x0

```
That is: no WM_CLASS, and no WM_WINDOW_ROLE so as to 'catch' it with rc.xml. The visibility config file allows you to specify whether it should behave in a 'dock' style whihc appears to govern whether or not it appears 'above' other apps but not if it's sticky.

Does anybody have any ideas as to how this can be fixed (i.e. always having it sticky)? The pager is no longer being developed so asking the developer is probably out of the question.

EDIT: In the unlikely event that anybody else comes across this needing a solution, I've posted one [here]("http://ubuntuforums.org/showpost.php?p=5356053&postcount=19")

---

### Post by Seisen on 2008-07-01
Just wondering if anybody has successfully build openbox 3.4.7.2 with obconf 2.0.3 both of these pulled from the git repositories. I got openbox to install just fine without any errors but when I try to build obconf it spouts out this error: ```
checking for OPENBOX... configure: error: Package requirements (obrender-3.0 >= 3.4.2 obparser-3.0 >= 3.4.2) were not met:

No package 'obrender-3.0' found
No package 'obparser-3.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables OPENBOX_CFLAGS
and OPENBOX_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I did notice that if you go to /usr/lib/pkgconfig, obrender-4.0.pc is listed which I assume is causing the problem.

---

### Post by jjgomera on 2008-07-01
> **chochem said:**
> I just check the comments in the rc.xml file, in particular:
```
  <application name="first element of window's WM_CLASS property (see xprop)"
              class="second element of window's WM_CLASS property (see xprop)"
```

I don't know if case is important in this context but if it is, then according to your xprop printout you should probably uppercase the S in smplayer. Or switch to name="smplayer". 

Hope it helps.
thanks, I've tried with smplayer, Smplayer, or SMPlayer but neither works

---

### Post by chochem on 2008-07-01
> **jjgomera said:**
> thanks, I've tried with smplayer, Smplayer, or SMPlayer but neither works

Ok, these are not exactly deep insights but a few things you might want to try/check:
- If the XML of your rc.xml is broken, everything that comes before the error will work which can make it semi-indetectable. As the applications bit tends to be at the end, this could be your problem. Try googling for an xml validation service.
- I can't tell from your response: Have you tried 'catching' it with name instead of class? Have you tried applying the same adjustments to another app to see if that works (in which case it probably is Smplayer that's the problem) Or maybe tried applying some other properties to smplayer to see if that might take effect (e.g. skip taskbar/pager, sticky, below/above...)
- Considered switching to VLC....? ;) (I know, that's probably not what you're looking for of suggestions)

---

### Post by moore.bryan on 2008-07-02
okay, here's one for everyone. my obconf now seg faults with the error message 
```
ObRender-Message: Unable to parse color '#0000000'
```
**note the incorrect color; i.e., **seven** zeros instead of six**

now, i've looked in all obconf files, as well as all libobrender* files and there is no text in **any** of those files telling anything to parse that color. **any** ideas?

---

### Post by moore.bryan on 2008-07-02
> **Seisen said:**
> Just wondering if anybody has successfully build openbox 3.4.7.2 with obconf 2.0.3 both of these pulled from the git repositories. I got openbox to install just fine without any errors but when I try to build obconf it spouts out this error: ```
checking for OPENBOX... configure: error: Package requirements (obrender-3.0 >= 3.4.2 obparser-3.0 >= 3.4.2) were not met:

No package 'obrender-3.0' found
No package 'obparser-3.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables OPENBOX_CFLAGS
and OPENBOX_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I did notice that if you go to /usr/lib/pkgconfig, obrender-4.0.pc is listed which I assume is causing the problem.
which obrender do you have installed?

---

### Post by urukrama on 2008-07-02
> **moore.bryan said:**
> okay, here's one for everyone. my obconf now seg faults with the error message 
```
ObRender-Message: Unable to parse color '#0000000'
```
**note the incorrect color; i.e., **seven** zeros instead of six**

now, i've looked in all obconf files, as well as all libobrender* files and there is no text in **any** of those files telling anything to parse that color. **any** ideas?

It is possible it is in one of your Openbox theme files. I've encountered similar issues before (with a different wrong colour), which was caused by a wrong themerc file. Generally, though, it doesn't prevent obconf from loading, but it only prints such errors in xsession-errors.

---

### Post by moore.bryan on 2008-07-02
@urukrama:
brilliant... i thought i had grep-ed all my files, but i hadn't; found the culprit in two theme files.
downside, it still seg faults.

---

### Post by moore.bryan on 2008-07-02
although i'm not able to understand much of it, i've attached the ltrace and strace outputs for my obconf... perhaps someone can help explain it?

---

### Post by dbbolton on 2008-07-02
@moore.brian:

I installed Openbox 3.4.6.1 and obconf 2.0.3 from the Ubuntu repositories, then built and installed 3.4.7.2 from the .tar.gz on the Openbox downloads page (not the git repository). I get a bunch of gdk errors from obconf, but no seg faults. Maybe you could try using obconf from the Ubuntu repos.

---

### Post by moore.bryan on 2008-07-02
okay, so i reinstalled obconf from the repos, cp'd /usr/local/bin/obconf to obconf.old and symln'd /usr/bin/obconf to /usr/local/bin and everything works; *shouldn't* have been **that** complicated.

@dbbolton:
thanks for the thoughts...

---

### Post by dbbolton on 2008-07-02
Does anyone know which aspects of the themerc apply to these buttons:

[IMG]http://i103.photobucket.com/albums/m128/envyouraudience/2008-07-02-191805_1280x960_scrot.png[/IMG]

---

### Post by el mariachi on 2008-07-03
How do I disable shadows for tint and trayer? (i'm using xcompmgr)

---

### Post by urukrama on 2008-07-03
> **dbbolton said:**
> Does anyone know which aspects of the themerc apply to these buttons:

[IMG]http://i103.photobucket.com/albums/m128/envyouraudience/2008-07-02-191805_1280x960_scrot.png[/IMG]

I'm not sure, but it seems to follow the colours and texture of your active window buttons (unpressed, hover, pressed), which is a bit impractical. The default button will have the hover settings, the other the unpressed settings.

---

### Post by urukrama on 2008-07-03
> **el mariachi said:**
> How do I disable shadows for tint and trayer? (i'm using xcompmgr)

Can you disable shadows for specific applications with xcompmgr? I've never seen such an option, but haven't used xcompmgr in a while either.

---

### Post by el mariachi on 2008-07-03
not that I know of. I was thinking about rc.xml

---

### Post by moore.bryan on 2008-07-03
okay, new wrinkle... the maximize button doesn't work. at all. it depresses, but nothing happens. minimize works fine and right-clicking the titlebar and selecting "maximize" works, but... uh, not the button.

---

### Post by dbbolton on 2008-07-03
> **el mariachi said:**
> How do I disable shadows for tint and trayer? (i'm using xcompmgr)
Did you use the -C option? -c makes shadows, and -C avoids putting shadows around windows of the panel class.

---

### Post by jjgomera on 2008-07-03
> **chochem said:**
> Ok, these are not exactly deep insights but a few things you might want to try/check:
- If the XML of your rc.xml is broken, everything that comes before the error will work which can make it semi-indetectable. As the applications bit tends to be at the end, this could be your problem. Try googling for an xml validation service.
- I can't tell from your response: Have you tried 'catching' it with name instead of class? Have you tried applying the same adjustments to another app to see if that works (in which case it probably is Smplayer that's the problem) Or maybe tried applying some other properties to smplayer to see if that might take effect (e.g. skip taskbar/pager, sticky, below/above...)
- Considered switching to VLC....? ;) (I know, that's probably not what you're looking for of suggestions)

thanks, finally solved, i dont know how i dont see it before, right click over the window bottom line, only one line to do :) and move. When start smplayer again, show in right position :oops:
I wonder how reach the window thats positions

---

### Post by el mariachi on 2008-07-03
> **dbbolton said:**
> Did you use the -C option? -c makes shadows, and -C avoids putting shadows around windows of the panel class.
-C doesn't get me shadows (I use xcompmgr from git btw)

---

### Post by dbbolton on 2008-07-03
> **el mariachi said:**
> -C doesn't get me shadows (I use xcompmgr from git btw)
You have to put both, such as 'xcompmgr -cC'

---

### Post by el mariachi on 2008-07-03
that did it, thanks dbbolton

---

### Post by chochem on 2008-07-03
> **jjgomera said:**
> thanks, finally solved, i dont know how i dont see it before, right click over the window bottom line, only one line to do :) and move. When start smplayer again, show in right position :oops:
I wonder how reach the window thats positions

Ha yeah, somehow the simple solutions always elude me....

---

### Post by dbbolton on 2008-07-08
I created a file to allow Openbox themerc highlighting in gedit. It's not perfect, but you all are more than welcome to give it a go.

Save this as /usr/share/gtksourceview-2.0/language-specs/openbox.lang

[html]
<?xml version="1.0" encoding="UTF-8"?>
<!--

 Author: Daniel Bolton (envyouraudience at gmail)

 This library is free software; you can redistribute it and/or modify
 it under the terms of the GNU General Public License as published by
 the Free Software Foundation; either version 2 of the License, or
 (at your option) any later version.

 This program is distributed in the hope that it will be useful,
 but WITHOUT ANY WARRANTY; without even the implied warranty of
 MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 GNU General Public License for more details.

 You should have received a copy of the GNU General Public License
 along with this program; if not, write to the Free Software
 Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307  USA

-->
<language id="openbox" _name="Openbox theme" version="2.0" _section="Others">
  <metadata>
    <property name="mimetypes">text/plain</property>
    <property name="globs">themerc</property>
    <property name="line-comment-start">#</property>
  </metadata>

  <styles>
    <style id="comment" _name="Comment" map-to="def:comment"/>
    <style id="string" _name="String" map-to="def:string"/>
    <style id="keyword" _name="Keyword" map-to="def:keyword"/>
    <style id="decimal" _name="Decimal" map-to="def:decimal"/>
    <style id="variable" _name="Data Type" map-to="def:type"/>
    <style id="state" _name="Widget State" map-to="def:special-constant"/>
    <style id="include-directive" _name="Include directive" map-to="def:preprocessor"/>
    <style id="boolean-value" _name="Boolean value" map-to="def:boolean"/>
  </styles>

  <definitions>
    <context id="double-quoted-string" style-ref="string" end-at-line-end="true">
      <start>"</start>
      <end>"</end>
      <include>
        <context ref="def:escape"/>
        <context ref="def:line-continue"/>
      </include>
    </context>
    <context id="single-quoted-string" style-ref="string" end-at-line-end="true">
      <start>'</start>
      <end>'</end>
      <include>
        <context ref="def:escape"/>
        <context ref="def:line-continue"/>
      </include>
    </context>
    <context id="line-comment" style-ref="comment" end-at-line-end="true">
      <start>#</start>
      <include>
        <context ref="def:escape"/>
        <context ref="def:line-continue"/>
      </include>
    </context>
    <!-- <context id="line-comment" style-ref="comment" end-at-line-end="true">
      <start>!</start>
      <include>
        <context ref="def:escape"/>
        <context ref="def:line-continue"/>
      </include>
    </context> -->
    <context id="keysymbol" style-ref="keyword">
      <match>=.:</match>
    </context>
    <context id="number" style-ref="decimal">
      <match>\b[0-9][0-9\.]*\b</match>
    </context>
    <context id="keyword" style-ref="keyword">
      <keyword>bg</keyword>
      <keyword>border</keyword>
      <keyword>button</keyword>
      <keyword>client</keyword>
      <keyword>color</keyword>
      <keyword>colorto</keyword>
      <keyword>colorTo</keyword>
      <keyword>font</keyword>
      <keyword>grip</keyword> 
      <keyword>handle</keyword>
      <keyword>highlight</keyword>
      <keyword>height</keyword>
      <keyword>hilight</keyword>
      <keyword>hover</keyword>
      <keyword>image</keyword> 
      <keyword>items</keyword>
      <keyword>justify</keyword>
      <keyword>label</keyword>
      <keyword>menu</keyword>
      <keyword>osd</keyword>
      <keyword>overlap</keyword>
      <keyword>padding</keyword>
      <keyword>pressed</keyword>
      <keyword>separator</keyword>
      <keyword>shadow</keyword>
      <keyword>splitto</keyword>
      <keyword>splitTo</keyword>
      <keyword>text</keyword>
      <keyword>title</keyword>
      <keyword>toggled</keyword>
      <keyword>unhighlight</keyword>
      <keyword>unhilight</keyword>
      <keyword>unpressed</keyword>
      <keyword>width</keyword>
      <keyword>window</keyword>
    </context>
    <context id="variable" style-ref="variable">
      <keyword>Border</keyword>
      <keyword>center</keyword>
      <keyword>Center</keyword>
      <keyword>flat</keyword>
      <keyword>Flat</keyword>
      <keyword>gradient</keyword>
      <keyword>Gradient</keyword>
      <keyword>horizontal</keyword>
      <keyword>Horizontal</keyword>
      <keyword>left</keyword>
      <keyword>Left</keyword>
      <keyword>parentrelative</keyword>
      <keyword>Parentrelative</keyword>
      <keyword>ParentRelative</keyword>
      <keyword>raised</keyword>
      <keyword>Raised</keyword>
      <keyword>right</keyword>
      <keyword>Right</keyword>
      <keyword>solid</keyword>
      <keyword>Solid</keyword>
      <keyword>splitvertical</keyword>
      <keyword>Splitvertical</keyword>
      <keyword>SplitVertical</keyword>
      <keyword>vertical</keyword>
      <keyword>Vertical</keyword>
    </context>
    <context id="state" style-ref="state">
      <keyword>active</keyword>
      <keyword>disabled</keyword> 
      <keyword>inactive</keyword>
    </context>
    <context id="include-directive" style-ref="include-directive">
      <keyword>include</keyword>
    </context>
    <context id="boolean-value" style-ref="boolean-value">
      <keyword>y</keyword>
      <keyword>n</keyword>
    </context>
    <context id="openbox">
      <include>
        <context ref="double-quoted-string"/>
        <context ref="single-quoted-string"/>
        <context ref="line-comment"/>
        <context ref="keysymbol"/>
        <context ref="number"/>
        <context ref="keyword"/>
        <context ref="variable"/>
        <context ref="state"/>
        <context ref="include-directive"/>
        <context ref="boolean-value"/>
      </include>
    </context>
  </definitions>
</language>
[/html]

Then select in gedit by going to View > Highlight Mode > Others > Openbox theme.

---

