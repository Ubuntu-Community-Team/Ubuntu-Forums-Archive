---
title: "A few compiz-fusion issues, please suggest solutions."
date: 2007-07-29
forum: Desktop Effects &amp; Customization
---

### Post by dannyboy79 on 2007-07-29
Hardware: ASRock 775dual-VSTA
Intel C2D 4300 (1.8ghz)
XFX GF 6200 128mb RAM AGP 8X- Dual Head-AGP & DVI (nvidia-glx-new driver-9755 from Fiesty Repositories) Nvidia-settings set to 2 Seperate Screens
17" Flat Panel Monitor via AGP (1280x1024) 17" HDTV via DVI-to-VGA adapter into VGA port on HDTV (1024x768)
2GB OCZ 667 DDRII
Optiarc DVD RW AD-7170A
2X Maxtor 6L300R0 (600gb total)
WDC WD200BB-53AUA1 (20gb)
WDC WD4000KD-00N (400gb)
WDC WD5000AAKS-0 (500gb)
ST350083 (500gb)

OS: Ubuntu Fiesty Fawn-2.6.20-16-generic

after uninstalling compiz-core and desktop-effects, then reinstalling everything again, things are working GREAT. Compiz stuff is even working on my SECOND SCREEN!!!!!!! I do have a few isssues that I would appreciate some feedback on to see if others are experiencing the same issues. I am using Trevino's repo's for feisty. they are:
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

I don't know where it was but I saw somewhere in my settings that I was using a flat file versus gconf. IS that the cause of all this? I use the compizconfig settings manager to set stuff, is that ok? The commands I use within a gocompiz bash script are:
compiz --replace ccp &
gtk-window-decorator --replace &
(NOTE: I didn't used to have the ccp in there but I added it recently as I read that it'll make compiz read the compiz config settings instead of gconf, is that correct?

1. When I open a new window it automagically is snapped to the top left corner so far that I can't even see the top border and the only way to move it is by holding alt+left mouse click on the window, then it moves. I made sure that window snapping is off. not sure what else to do.

2. The one and most important problem/gripe. When I click on any drop down menu (Application, Places etc etc), even when I right click to see a menu come up, it is VERY SLOW TO OPEN, it's actually a count of "one one thousand" for the drop down to open, which in MHO is way to slow!. This seems very wrong, any suggestions?

2. On my main screen (17" Flat Panel Monitor) the only way I can get the cube to rotate is if I hold ctrl-alt and hit the left mouse button over a window's top border, if I try it just on my normal desktop, it doesn't do anything but make a box for selecting multiple stuff on the desktop (like if you want to delete several things at once for instance)? What's more strange is that rotating the cube works fine on the desktop of the Second Screen (17" HTDV with VGA from XGX GF 6200 128mb AGP 8X), meaning, I can do it right on the desktop. Can anyone comment on this?

3. Viewport mouse switching is NOT checked but if I move the mouse to the left side of the display, the cube rotates to the next viewport? Why is this if that option isn't enabled.

4. Can't get pictures to show up on top or bottom of cube but can get a background picture to show when rotating cube? Yes, they are .png files.

5. I have my bottom panel on autohide and sometimes it won't appear when I move the mouse cursor towards the bottom of the screen? I can obviously do Super+Tab, and that will bring up a cool circle of all open windows and I can tab thru them and choose the one I want, but that's besides the point.

6. I used to be able to hold atl+mouse scroll up and down to control a windows transparency, now that doesn't work. How can I fix that?

7. if I have multiple windows open, I can't just click the window to have it raise, I have to hit the window border at the top, huh?? ANy suggestions.

---

### Post by aberflasm on 2007-07-30
Hello. I am a noob here but I will do my best to answer your questions. I'm using Feisty btw.

For the unnumbered question:
a. I cant locate it in any of the enabled features but i remember it as well. I dont think it is the problem though.
b.YES!!!
c. The ccp is news to me. I created a option in sessions to start compiz by calling compiz --replace -c emerald &

 and for the number questions ( you had 2 number 2s :) )
**_1_**. Had this problem too. Not sure what fixed it other a restart.
**_2_**.Not sure but it may be related to the animation effect you are using. Try to locate the the menu's animation settings and see if you can adjust the speed there.
**_2b_**.Not a clue why the difference between monitors.
**_3._**Under Rotate Cube, make sure to uncheck "Edge Flip Pointer".
**_4._**Not sure if you have cube caps enabled, and images specified, and png turned on.
**_5._**Sorry no help on this one either.
**_6._**Try the actions tab in general options. I think that is where you can specify what key combo to change window opacity with.
**_7_**This one annoyed me too. in general options, click on the Focus and Raise tab and uncheck auto-raise.

---

### Post by psyopper on 2007-07-30
> **dannyboy79 said:**
> 
I don't know where it was but I saw somewhere in my settings that I was using a flat file versus gconf. IS that the cause of all this? I use the compizconfig settings manager to set stuff, is that ok? The commands I use within a gocompiz bash script are:
compiz --replace ccp &
gtk-window-decorator --replace &
(NOTE: I didn't used to have the ccp in there but I added it recently as I read that it'll make compiz read the compiz config settings instead of gconf, is that correct?


Well, first I would like to commend you for taking the time to actually post your hardware, compiz version and installation repository. Most don't do this and it takes that much longer to get to the crux of the problem.

To answer this question, there are two methods that Compiz can use to store its configuration settings - in the GConf (G Configuration System, similar to the Windows Registry but only used for Gnome) and in a settings file. Using the GConf backend could cause a few weird keybinding and window display issues that may or may not effect your user experience.

I strongly recommend, for the time being, that people use the flatfile back end and not the GConf backend. To set the backend open the CompizConfig Settings Manager (CCSM) - System | Preferences | CompizConfig Settings Manager. In the bottom left corner is a button labeled "Backend". Click it and select Flatfile. You may need to readjust some of your settings after making this change, be prepared for that.

> **dannyboy79 said:**
> 
1. When I open a new window it automagically is snapped to the top left corner so far that I can't even see the top border and the only way to move it is by holding alt+left mouse click on the window, then it moves. I made sure that window snapping is off. not sure what else to do.


In the CCSM enable the "Place Windows" plugin and select "Smart" for your placement

> **dannyboy79 said:**
> 
2. The one and most important problem/gripe. When I click on any drop down menu (Application, Places etc etc), even when I right click to see a menu come up, it is VERY SLOW TO OPEN, it's actually a count of "one one thousand" for the drop down to open, which in MHO is way to slow!. This seems very wrong, any suggestions?


This might be related to the Fading Windows plugin. Try adjusting the timing in Fading Windows to see if it helps. There are methods to exclude particular menus. If you are interested let me know and I can help work them out.

> **dannyboy79 said:**
> 
2. On my main screen (17" Flat Panel Monitor) the only way I can get the cube to rotate is if I hold ctrl-alt and hit the left mouse button over a window's top border, if I try it just on my normal desktop, it doesn't do anything but make a box for selecting multiple stuff on the desktop (like if you want to delete several things at once for instance)? What's more strange is that rotating the cube works fine on the desktop of the Second Screen (17" HTDV with VGA from XGX GF 6200 128mb AGP 8X), meaning, I can do it right on the desktop. Can anyone comment on this?


Open the Rotate Cube plugin. Go to the Actions tab and take a look at your various methods of initiating the rotation. Adjust as necessary. It seems to me by what you are describing that you are rotating the cube by dragging a window "around the corner" to the next desktop, etiher left or right. 

You description is a little confusing for me to understand so I may be missing the point entirely. Maybe if you explained it to me in my own mentality - as if you were training your technophobe father how to do it I might understand a little better.

> **dannyboy79 said:**
> 
3. Viewport mouse switching is NOT checked but if I move the mouse to the left side of the display, the cube rotates to the next viewport? Why is this if that option isn't enabled.


That's not the Viewport Mouse Rotate plugin! It's in the Rotate Cube plugin, the check-box named "Edge Flip Pointer." Checking this lets you rotate the cube by moving your mouse "around the corner," unchecking it makes the edge "hard."

> **dannyboy79 said:**
> 
4. Can't get pictures to show up on top or bottom of cube but can get a background picture to show when rotating cube? Yes, they are .png files.


There are ongoing issues with cube caps (the top and bottom pictures). Compiz Fusion does not currently support a cubecap on the bottom, only on the top. This can be configured in the "Desktop Cube" plugin in the section labeled Cube Caps. There are some outstanding issues to be resolved in cube caps as well, like have you noticed that if you do put a square image on the cube cap is still squishes it even though it's a cube?

> **dannyboy79 said:**
> 
5. I have my bottom panel on autohide and sometimes it won't appear when I move the mouse cursor towards the bottom of the screen? I can obviously do Super+Tab, and that will bring up a cool circle of all open windows and I can tab thru them and choose the one I want, but that's besides the point.


I assume you are using the standard Ubuntu panels, actually called gnome-panel and not something like Avant Window Navigator (AWN) for that panel. Either way it's not a Compiz issue and I'm not really sure where to send you other than to ask first - does this happen alsow when you are NOT using compiz?

> **dannyboy79 said:**
> 
6. I used to be able to hold atl+mouse scroll up and down to control a windows transparency, now that doesn't work. How can I fix that?


I had this same problem, it's when I learned all about the GConf and flatflie backends. Using the GConf backend killed my ability to go one way, but the other way with the transparency worked just fine. Try switching to the FLatfile backend and see what happens here.

Transparency is controlled in the General Options plugin, Actions Tab, Opacity Settings section.

> **dannyboy79 said:**
> 
7. if I have multiple windows open, I can't just click the window to have it raise, I have to hit the window border at the top, huh?? ANy suggestions.

Not sure on this one. 

Remember, Compiz-Fusion is beta software. In fact I can't remember when it WASNT beta software either under the Compiz name, the Beryl name or the Compiz Fusion name. THere are new releases daily in the Trevino Repo which means that the people working on Compiz Fusion are working hard trying to fix things every day. THis means that each update there is a chance for something to work better, and subsequently for something else to break.

Be patient and enjoy what you have so far, it's still a heck of a lot better than Aero...

---

### Post by Andre_44 on 2007-08-01
I have the same issue with very slow menus. but its affecting only my primary display, not my TV-Out. the menu' on the TV are nice and tfast, but on the LCD they take 1.5 seconds to appear.  i had this problem the last time I tried compiz-fiusion almost 2 months ago.

---

### Post by dzark on 2007-08-04
Have the same issue with slow menus etc too.. Seems to be related to which X screen is primary/secondary. 

I've swap screen numbers in my xorg.conf (1 to 0 and 0 to 1) it results in my main (twinview dual-head) screens running at full speed and my auxillary screen (onboard card - mostly just for movies) being slow and laggy, which i can live with - Annoying though.. Anyone gotten further?


Cheers,
wulf solter

---

### Post by dannyboy79 on 2007-08-09
not me, I am not sure what you mean about switching screens though. in my situation I have a 17" flat panel HDTV on an upper shelf and to the right, my main screen is a 17" flat panel monitor. I can't really do that but I'll see if my aux screen is faster. if it maybe I need to switch them.

---

### Post by tehkain on 2007-08-10
I have issue number 5. It is not an issue without compiz.. I think it has something to do with corner hotspots in compiz. This issue has been bugging me for months.

---

### Post by babazoid on 2007-08-21
I also have issue number 2.  Context menus, popup windows take a loooooong time to show up.  It makes the system unusable.

- It's not related to the fade plugin, I've disabled it.
- I've tried various command line options (__GL_YIELD=NOTHING, etc)
- Only screen 0 is slow, not screen 1 as reported by other users.

This clearly seems like a bug of some sort and not a hardware problem. Can anyone help? 

Thanks

---

### Post by naseem on 2007-08-21
hy I downloaded updates and the had settings reset, now I'm tring to have the cube to rotate and chaked almost evrything in compiz settings manager about rotate cube, but it just doesn't work, I also wont to get back the rotation via the mouse weel hoew to get all this back?
(is it a setting trouble or something with latest compiz-fusion update?)

---

### Post by dannyboy79 on 2007-08-22
if you're using the compiz settings manager than ensure that you're using the flat file config. it's in the compiz settings manager. also, if you're using dual display with 2 seperate screens, I can't rotate my cube either UNLESS I move the mouse cursor over a window edge (the top panel of a window) then hold ctrl and move mouse left or right. good luck

---

### Post by babazoid on 2007-08-28
Still having the same problem with annoying delays on head 0.  Anyone have a solution?  This is preventing me from using Compiz-fusion at all...

---

### Post by dannyboy79 on 2007-08-28
same here as previously stated! this is just bullsh__ in my opinion. What's the point of having dual heads but not being able to use compiz. DAMN. Hope there's a solution sooner or later.

---

### Post by davidomundo on 2007-08-28
Regarding issue #2, I can confirm that only GTK applications are slow at opening. I run kubuntu and most of the programs that I run are KDE-based. All QT applications appear immediately.

I ran into this issue when I used openoffice, firefox, and the compizconfig settings manager (the only three GTK applications that I use).

This seems strange, and might be a problem with GTK applications failing to communicate with the window manager.

I'm using XGL with an ATI graphics card using the fglrx driver.

I have dual monitors, but I can't seem to access display 0.1 with my mouse or my keyboard. The only way I can gain temporary focus on that display is to start an application with DISPLAY=0.1. After I lose the keyboard focus, I can never regain it. Right now, I'm just using display 0.1 to start a:

DISPLAY=0.1 konsole -e tail -f /var/log/syslog

I thought I'd mention this because many people were talking about how the slow window/popup/menu appearances only occurred in display 0.0.

---

### Post by babazoid on 2007-08-31
I installed Xgl tonight -- in all the read-me files and whatnot there was never really a detailed explanation of what Xgl was or if I needed it.

[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

Once I installed it my twinview head :0.1 no longer worked properly... but the problems with menus appearing really slowly went away.  Also I was having an issue with resizing windows, and it also totally disappeared. 

Now... If only I could get both heads (my LCD and HDTV) working properly with twinview and XGL it would be perfect.

---

### Post by dannyboy79 on 2007-08-31
> **babazoid said:**
> I installed Xgl tonight -- in all the read-me files and whatnot there was never really a detailed explanation of what Xgl was or if I needed it.

[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

Once I installed it my twinview head :0.1 no longer worked properly... but the problems with menus appearing really slowly went away.  Also I was having an issue with resizing windows, and it also totally disappeared. 

Now... If only I could get both heads (my LCD and HDTV) working properly with twinview and XGL it would be perfect.
from the wiki: Xgl is an X server architecture designed to take advantage of modern graphics cards via their OpenGL drivers, layered on top of OpenGL via glitz
and here's a good fairly deep explaination of xgl: [http://principe.homelinux.net/](http://principe.homelinux.net/)

do you use nvidia-settings to setup twinview or seperate screen? if so, that's the easiest. it's a gui driven configuration for your gfx card

this would lead me to believe that the problem is with xorg then, because xgl is an xserver (based on the wiki?), so if the lag goes away when using compiz-fusion and xgl then it must be xorg right? ANyway, I may give this a shot. otherwise I am just going to pass on compiz since I need 2 seperate screens versus "needing" wobbly windows and such. I am not a workspace switching guy so all that functionality I don't use. if I was a coder or did super multi-tasking than I suppose I'd adapt and use all 4 workspaces but currently I don't.

---

### Post by babazoid on 2007-08-31
I realize that Xgl is described in the wiki, but I still don't understand what the difference between running compiz on plain X vs. Xgl is. 

None of the how-tos on installing Compizfusion really mention that... not the ones I've seen anyway.

I've got X configured with twinview and working 100% -- but when I launch Xgl screen 1 doesn't work properly. I've googled and it I can't seem to find the proper config switch ... if there is one to launch it dual-headed.

---

### Post by chronographer on 2007-09-27
> **babazoid said:**
> I also have issue number 2.  Context menus, popup windows take a loooooong time to show up.  It makes the system unusable.

- It's not related to the fade plugin, I've disabled it.
- I've tried various command line options (__GL_YIELD=NOTHING, etc)
- Only screen 0 is slow, not screen 1 as reported by other users.

This clearly seems like a bug of some sort and not a hardware problem. Can anyone help? 

Thanks

I too have this problem. i will try the above fix of changing  screen 0 and 1 around ( i.e. the numbers for each) and report back tonight. THIS is the one thing now stopping me from using compiz all the time!

agl

---

### Post by chewearn on 2007-10-03
> **babazoid said:**
> I also have issue number 2.  Context menus, popup windows take a loooooong time to show up.  It makes the system unusable.

- It's not related to the fade plugin, I've disabled it.
- I've tried various command line options (__GL_YIELD=NOTHING, etc)
- Only screen 0 is slow, not screen 1 as reported by other users.

This clearly seems like a bug of some sort and not a hardware problem. Can anyone help? 

Thanks

I saw another thread somewhere in the forum (can't find it now) about this issue, and someone suggested a partial solution.  Basically, you enable compiz on the main screen only, by this start-up script: 

```
#!/bin/bash
sleep 5
compiz --replace --only-current-screen &
sleep 5
gtk-window-decorator --replace &

```

After further trials, here is the script I used for emerald (instead of gtk-window-decorator):

```
#!/bin/bash
gnome-terminal &
sleep 5
compiz --replace --only-current-screen &
sleep 5
emerald --replace &

```

For some reason, the gnome-terminal is needed, else your second screen will be missing the gnome panels.

I have tried this on one setup, will try on another one later.  Not the perfect solution, compared to full blown compiz on two screens, but better than nothing.

---

### Post by dannyboy79 on 2007-10-03
very true, I like at least being able to have compiz on my main screen and not have the slow downs of drop down menus and right click menu's BUT also still have my second display. Hopefully this will work me, I'll try it out soon.

---

### Post by notquitemichael on 2007-10-04
hey,

i've found the reason this happened in beryl was when using the --no-context-share option at run. which suggests this is what compiz is doing. if it is possible to specify the screen then you just need to run the equivilent of this:

an 'almost' solution to your problem with the slow windows, if using the beryl workaround as follows:

open beryl on your first head:

beryl --screen 0.0

then emerald

emerald --screen 0

then beryl on your second head

beryl --screen 1.0

then emerald

emerald --screen 1

but i don't know compiz well enough to find the screen specifier, i'll look around.

---

### Post by bluenova on 2007-10-09
The slow issue has been stopping me from using Compiz. Now that I start it with --only-current-screen it works like a charm!

---

