---
title: "UNR 9.10 - classic desktop mode"
date: 2009-11-03
forum: Desktop Environments
---

### Post by lett on 2009-11-03
Hello,
since I have installed UNR 9.10 version I can not find a way to switch into "classic mode" desktop. I am aware of the fact that desktop switcher application (which was responsible for this oprion in 9.04)  is not included into 9.10 because of some technical problems. So, my question is: what exactly should be done in order to get classic gnome desktop mode in UNR 9.10? Or, to be more specific: what packages should be removed/added and what changes in startup procedure should be performed?

Thanks in advance

---

### Post by dust79 on 2009-11-03
Hello,

I had a similar problem. For some reason i got netbook remix when upgrading from 9.04 to 9.10. Dont know how.. And i didnt succeed to switch to classic. Instead I did mess things up so I dont even have any menus anymore. Can someone advice how to get classic desktop mode through command line?

Thanks alot for your help.

---

### Post by NickJones on 2009-11-03
From the login screen.

---

### Post by lett on 2009-11-03
> **NickJones said:**
> From the login screen.

Obviously it does not work (I log in into GNOME session).

---

### Post by vinchenzosaldevar on 2009-11-03
i too can't stand this horrible mess of a desktop, in the old release I knew quite a few people who had the NBR but I never met anyone who didn't change it into the classic desktop mode.

personally I never had any problems with the classic desktop in jaunty and just presumed it would still be here in karmic.

someone help us please!

---

### Post by eholly on 2009-11-03
Try 

System > Start-up > Netbook Launcher > double click on then  (dissable by changing command to xxnetbook-launcher)
reboot and add to panels what you want. 

                      E Holly

---

### Post by wel on 2009-11-03
> **lett said:**
> Hello,
since I have installed UNR 9.10 version I can not find a way to switch into "classic mode" desktop. I am aware of the fact that desktop switcher application (which was responsible for this oprion in 9.04)  is not included into 9.10 because of some technical problems. So, my question is: what exactly should be done in order to get classic gnome desktop mode in UNR 9.10? Or, to be more specific: what packages should be removed/added and what changes in startup procedure should be performed?

Thanks in advance
Here the solution in spanish or translate.

[http://www.ubuntu-es.org/?q=node/116488#comment-340069](http://www.ubuntu-es.org/?q=node/116488#comment-340069)

---

### Post by manue on 2009-11-03
> **eholly said:**
> Try 

System > Start-up > Netbook Launcher > double click on then  (dissable by changing command to xxnetbook-launcher)
reboot and add to panels what you want. 

                      E Holly
I found out this just a couple of minutes ago, so that I got a most 'friendly' desktop (without such big icons covering the whole screen)
However what I can not yet fix is how to allow the right-button of the mouse to show a menu through which the possibility to create short-cuts to applications or to place archives in the desktop is available.
Thanks for any help on this
Manuel

---

### Post by lett on 2009-11-04
Hi, I have found and successfully tried out solution of this problem - below is the link:

[http://ubuntuforums.org/showthread.php?t=1308792](http://ubuntuforums.org/showthread.php?t=1308792)

It is not a perfect solution: now I do not have gnome desktop icons. It seems that default UNR configuration does not contain some GNOME packages. The question is: which ones?

---

### Post by Geopon on 2009-11-05
I have an Acer Aspire One.

I installed 9.10 directly from the updater

i have the standard desktop running.

I don't know how.

I was running the desktop mode in 9.04 so i assumed it just mimiced my settings like it did with everything else.

Everything works fine and out of the box.

I'll gladly give screenshots or do anything i can to help.

I only googled this topic as i noticed the switcher was no longer avalible and i wanted to see what the UNR thingy looked like

i activated by making it a startup application and just rebooted to see it.

I still have the grey bars on the top and bottom so i just disabled it again.

But yeah, everything works fine for me :)


P.S count this as my introduction too :) ):P


oh wait

my battery counter says my charger is still plugged in and my battery is 100%

thats the only problem

---

### Post by sseelbinder on 2009-11-05
I also upgraded from UNR 9.04 to 9.10 and lost the classic desktop functionality, and would certainly like to see it reinstated.  How could we obtain confirmation that it is being looked into?  Or, does anyone know how the Ubuntu Laptop version runs on the Netbooks?  Not sure if I should wait for a UNR classic desktop fix or try running the laptop version on my Netbook?

---

### Post by lett on 2009-11-06
As far as I know the only difference between regular Ubuntu version and Netbook Remix is that user interface change. No special drivers for netbooks hardware, no optimization - nothing. I have resigned from UNR and right now I install regular version.

---

### Post by sseelbinder on 2009-11-07
I followed Lett's lead and removed UNR and installed the desktop version.  Timely method to get to the classic desktop, but sucessful.

---

### Post by traffas on 2009-11-09
Has anyone solved this problem in an elegant way without reinstallation? I like the fisher-price interface most of the time, but when I'm developing I need windows that aren't maximized. I don't care if I have to reboot, but I need classic Gnome some of the time.

UNR seems to be smaller than a full install. Is this the case or am I imagining things?

How can we get classic Gnome on UNR?

---

### Post by T3CHKOMMIE on 2009-11-10
> **traffas said:**
>  but when I'm developing I need windows that aren't maximized. 


im pretty sure there is not YET a button to switch between the two desktops like there was in 9.04 BUT to help you with the full size windows stuff i too cant stand full size screens all the time, to get rid  of that functionality, go to your startup applications in your systems > Prefrences >start up apps.

find "maximus" and uncheck it. reboot and you should never have those annoying AUTO fullsized windows again.

hope this helps.

---

### Post by phoenix55 on 2009-11-14
Here's what I did.

Step 1: Uncheck Maximus

   - Go to: System > Preferences
   - Uncheck 'Maximus Windows Management'
   - Restart the system
   New applications will not open maximized to the netbook's full screen

Step 2: Enable show_desktop

   - Open a terminal window (Accessories > Terminal)
   - Enter: gconf-editor. That opens the configuration editor GUI
   - Go to the node: / apps > nautilus > preferences (click preferences)
   - On the right window (showing the parameters associated with
        preferences) scroll down to 'show_desktop' and enable (click) it.
   This will get rid of the default desktop. No need to restart.

Step 3: Add the 'Main Menu' Applet to the panel

   - Right-click on the panel (mine is at the top edge)
   - Select the 'Main Menu' applet
   This will put the same menu structure as the original desktop but in a
   drop-down menu as the good old classical desktop.

  I still need to fine tune things a bit further (eg make minimized apps go to a panel at the bottom of the screen rather than the top panel) but in the meantime I've got what I want the most.

Enjoy the classical desktop look.

---

### Post by penguat on 2009-11-15
As a first step please could someone make/post a bash script to do that?

---

### Post by Luffield on 2009-11-22
Thanks for the guide, phoenix55. I used it to get the exact setup I wanted - one panel on the top, normal desktop with icons, and Maximus on. I love it. Took me 5 minutes. Thanks!

---

### Post by macachis on 2009-12-04
Here also: thank you very much, phoenix55.

But I have a small problem: when I switch on the computer, sometimes the UNR desktop appears again. In that case, I can make two things: restart the computer (sometimes works, sometimes not) or repeat the steps to enable show_desktop. Has anyone an idea about how to solve it?

I found other solution to change to classic desktop, but as I am a newe, I don't know very well how it works. It says to use Synaptic to install "Ubuntu desktop" package and uninstall "Ubuntu Netbook remix" and " Ubutu Netbook remix default" packages. It sounds like if you install the normal Ubuntu 9.10 version, isn't it? In that case, can this be a problem in a netbook? (I mean, does UNR have any special drivers o whatever for netbooks? I've read the 2 things, yes and no).

You can see that here (in spanish. If you can't understand, I can try to help you): 
[http://www.elbulto.com/post/linux-gnu/3860/de-ubuntu-netbook-remix-a-el-clasico-u.html](http://www.elbulto.com/post/linux-gnu/3860/de-ubuntu-netbook-remix-a-el-clasico-u.html)

Just in case, I have an Acer AO za3 

Thanks!

---

### Post by Rei Malebario on 2009-12-19
Phoenix55: That was brilliant! I've been trying to do this since I installed UNR about two weeks ago.
I've kept Maximus running (I rather like it and it does save some screen real estate) but I've now got the kind of desktop environment I wanted and it was pretty easy to do too.
Thanks a lot!

---

### Post by DZ* on 2009-12-22
> **lett said:**
> As far as I know the only difference between regular Ubuntu version and Netbook Remix is that user interface change. No special drivers for netbooks hardware, no optimization - nothing. I have resigned from UNR and right now I install regular version.

Is this not true? :

"What have you done with Intel to optimize the new platform for Atom?

-- Canonical has been working closely with Intel for more than a year on support for the Intel Atom processors. The optimizations mostly center around taking advantage of the power-saving extensions afforded by the Intel Atom processors, as well at some boot optimizations."

from:
[http://blog.laptopmag.com/ubuntu-netbook-remix-qa-with-canonical](http://blog.laptopmag.com/ubuntu-netbook-remix-qa-with-canonical)

---

### Post by DZ* on 2009-12-23
> **macachis said:**
> when I switch on the computer, sometimes the UNR desktop appears again. In that case, I can make two things: restart the computer (sometimes works, sometimes not) or repeat the steps to enable show_desktop. Has anyone an idea about how to solve it?

I had exactly the same problem (bought Dell mini 10v on Monday and decided to give UNR a try, but didn't like its desktop).

After some frustration, I determined that the beast is called netbook-launcher "A Clutter-based desktop launcher". Unchecking it's box in System -> Preferences -> Startup Applications solves the problem.

P.S. I think the applet to add for the classic menu look is "menu bar", not "main menu"

---

### Post by GlennJ on 2010-01-27
> **phoenix55 said:**
> Here's what I did.

Step 1: Uncheck Maximus

   - Go to: System > Preferences
   - Uncheck 'Maximus Windows Management'
   - Restart the system
   New applications will not open maximized to the netbook's full screen

Step 2: Enable show_desktop

   - Open a terminal window (Accessories > Terminal)
   - Enter: gconf-editor. That opens the configuration editor GUI
   - Go to the node: / apps > nautilus > preferences (click preferences)
   - On the right window (showing the parameters associated with
        preferences) scroll down to 'show_desktop' and enable (click) it.
   This will get rid of the default desktop. No need to restart.

Step 3: Add the 'Main Menu' Applet to the panel

   - Right-click on the panel (mine is at the top edge)
   - Select the 'Main Menu' applet
   This will put the same menu structure as the original desktop but in a
   drop-down menu as the good old classical desktop.

  I still need to fine tune things a bit further (eg make minimized apps go to a panel at the bottom of the screen rather than the top panel) but in the meantime I've got what I want the most.

Enjoy the classical desktop look.

I can do all that, but right click on the menu only allows me to remove menu items from the top panel, not add them.  Do you know how to turn them on?  

                  GlennJ

---

### Post by eltonw on 2010-01-28
> **lett said:**
> As far as I know the only difference between regular Ubuntu version and Netbook Remix is that user interface change. No special drivers for netbooks hardware, no optimization - nothing. I have resigned from UNR and right now I install regular version.

"All of the initial Ubuntu Netbook remixes combine optimisations from the Moblin project for Intel® Atom&#8482; processors and it is specially designed for netbooks." Quoted from:[http://www.canonical.com/projects/ubuntu/unr](http://www.canonical.com/projects/ubuntu/unr) ;) ... so one can gather that NBR is not just 'cosmetics'!

cheers,

---

### Post by eltonw on 2010-01-28
> **GlennJ said:**
> I can do all that, but right click on the menu only allows me to remove menu items from the top panel, not add them.  Do you know how to turn them on?  

                  GlennJ

Go to System ==> Main Menu, this should bring up the menu editor and you then select **[COLOR="Olive"]+[/COLOR]** Ne_w_ Item.

HTH,
;)

---

### Post by tom4jean on 2010-03-03
Really no reason to mess with changing the maximus settings.
If you double click the top bar of the window you are working with it will un-maximize it and you can move it around any way you like.
Or you can right click it and choose from the drop-down menu to unmaximize or minimize.

At first I was not sure if I liked the netbook interface either but in playing around with it more I am finding it just as easy, if not more so, to use then the classic one. It is just "new" and takes a little getting used too.

Overall I think it does make the small netbook screen easier to use.

---

### Post by ohiomoto on 2010-03-03
I agree that you don't need to change the maximus settings.  I was perfectly happy using Remix, but the menus became slow/unresponsive so I was using keyboard shortcuts anyway.  But if my wife wanted to use it, she couldn't get things to work properly so I added a menu to the top panel and went to a normal desktop.  I'm happy because my top panel now works just like it did with remix, but I have a Main Menu app in place of the Go Home app placed in the upper left corner.
[ATTACH]148858[/ATTACH]

---

### Post by tom4jean on 2010-03-04
> **ohiomoto said:**
> ...so I added a menu to the top panel and went to a normal desktop.  I'm happy because my top panel now works just like it did with remix, but I have a Main Menu app in place of the Go Home app placed in the upper left corner.
[ATTACH]148858[/ATTACH]

Looks great!,
 I have to admit since I started out using Ubuntu Linux as my first Linux ( I have tired a number of distros since and always come back). I do in some ways miss that original gnome "look" with the remix now on my netbook and I am thinking about switching to the full look again too. Although I agree with the others the kernel in the remix is custom built for netbooks and it is not only the user interface that makes remix different, so I would go with the modifications to remix suggested in this forum to get the regular desktop,
Incidentally they just announced the new look for Ubuntu that I think will be released in the beta 10.04 and I am liking it and will probably go the regular desk top at that time.
Here are a couple links to the new artwork;

[https://wiki.ubuntu.com/Brand](https://wiki.ubuntu.com/Brand)

[http://fridge.ubuntu.com/node/1991](http://fridge.ubuntu.com/node/1991)

---

### Post by eltonw on 2010-03-04
I must confess that I have not been following this thread _as closely as I would have liked_. Is there any indication that in the upcoming version, we (the users) will get back the option to enable the classic desktop either during installation or from the system menu? 

My preference is for the classic desktop on my 10" inch netbook since I do not have the problem with settings or options dialogs as with the netbook interface: viz: not being able to access the "OK" button at the bottom of some program dialogs.:( (Hitting TAB, TAB... does not always work, so to enable some preferences in various apps. sometimes winds up as a gamble...

If this question had already been posed, and / or answered, kindly pardon my ignorance.#-o

Given that the next iteration of ubuntu NBR is shortly to arrive, I guess I will live with the netbook interface till then.

---

### Post by tom4jean on 2010-03-07
Well after discovering another "glitch" in the UNR desktop; 
That if you install more then 30 games the icons in the middle of the game menu get huge and push off the bottom icons so you no longer have access to them. (this is a known problem with no known fix that I have found on another forum after it happened to me and I searched).

I have gone back through this thread and gleaning tips from everyone and went to the "classic desktop".

My steps;

1. Open "startup applications" in preferences.
Un-checked "Maximus windows management" and "Netbook launcher". Log out and back in. 

2. Removed "go home" applet from upper left corner by right clicking it and selecting "remove from panel". 
(as noted by others if you click on the "go Home" applet the UNR desktop comes back on.)

3. Remove the "window picker" applet from the top panel the same way.
(You cant "see it" without an open window but it is in the middle of the top panel just right click anywhere and the menu is there to remove it)

4. Right click the middle of the top panel and add the "Menu Bar" applet and move it to the left top corner and lock it to the panel. 
(Don't confuse this with the "Main Menu" applet. The "Menu Bar" is the familiar Ubuntu drop down menu that includes the; "Applications", "Places" and "System" drop down menus. "Main Menu" is the generic Gnome menu that wont give you access to Places and System.)

5. Right click the middle of the top panel again and click "new panel" it should put it at the bottom of the desktop. 

6. Right click the middle of the new bottom panel and add the "show desktop" applet and move it to the bottom left corner and lock it to the panel.

7. Right click the bottom panel again and add the "window list" applet and move it to the left lower corner next to the "show desktop" icon and lock it to the panel.
(The "windows list" applet is the familiar way that open windows are shown on the panel. This is not the same as the "window picker" removed from the top panel. The "Window picker" Applet is the one some people think is part of the way maximus displays windows and they don't like it)

8. Right click the middle of bottom panel again and add the "trash applet" and move it to the bottom right corner and lock it to the panel.

9. Right click the middle of the bottom panel one last time and add the "screen switcher" applet, and once it is activated right click it go to preferences and change it to show 2 columns, then move it to the bottom right next to the "trash applet" and lock it to the panel. 

I don't think I missed anything this should be the "classic desktop" arrangement.

Edit;
I just figured out a trick to get the UNR desktop to display and then turn off again if you want to switch it on or off.
After setting up the classic desktop add the "Go Home" and the "force quit" applets to one of your panels where ever you like. If you click the "Go Home" applet the UNR desktop starts. Then if you click the "Force quit" applet and click on an empty place on the UNR desktop and then confirm you want to "force quit" this application the UNR desktop goes off and you are back to the Classic desktop.
Between the two applets you have a switch to turn on or off the UNR desktop.

---

### Post by tom4jean on 2010-03-08
Screen shots of my Classic desktop, note in the bottom right corner the icons I added for the "Go Home" and "Force Quit" applets to turn the UNR desktop on and off.

Followed by a shot of my same classic desktop with the UNR turned on.

Click the images to enlarge.

---

### Post by polymath257 on 2010-03-20
> **tom4jean said:**
> Well after discovering another "glitch" in the UNR desktop; 
That if you install more then 30 games the icons in the middle of the game menu get huge and push off the bottom icons so you no longer have access to them. (this is a known problem with no known fix that I have found on another forum after it happened to me and I searched).

I have gone back through this thread and gleaning tips from everyone and went to the "classic desktop".

My steps;

1. Open "startup applications" in preferences.
Un-checked "Maximus windows management" and "Netbook launcher". Log out and back in. 

2. Removed "go home" applet from upper left corner by right clicking it and selecting "remove from panel". 
(as noted by others if you click on the "go Home" applet the UNR desktop comes back on.)

3. Remove the "window picker" applet from the top panel the same way.
(You cant "see it" without an open window but it is in the middle of the top panel just right click anywhere and the menu is there to remove it)

4. Right click the middle of the top panel and add the "Menu Bar" applet and move it to the left top corner and lock it to the panel. 
(Don't confuse this with the "Main Menu" applet. The "Menu Bar" is the familiar Ubuntu drop down menu that includes the; "Applications", "Places" and "System" drop down menus. "Main Menu" is the generic Gnome menu that wont give you access to Places and System.)

5. Right click the middle of the top panel again and click "new panel" it should put it at the bottom of the desktop. 

6. Right click the middle of the new bottom panel and add the "show desktop" applet and move it to the bottom left corner and lock it to the panel.

7. Right click the bottom panel again and add the "window list" applet and move it to the left lower corner next to the "show desktop" icon and lock it to the panel.
(The "windows list" applet is the familiar way that open windows are shown on the panel. This is not the same as the "window picker" removed from the top panel. The "Window picker" Applet is the one some people think is part of the way maximus displays windows and they don't like it)

8. Right click the middle of bottom panel again and add the "trash applet" and move it to the bottom right corner and lock it to the panel.

9. Right click the middle of the bottom panel one last time and add the "screen switcher" applet, and once it is activated right click it go to preferences and change it to show 2 columns, then move it to the bottom right next to the "trash applet" and lock it to the panel. 

I don't think I missed anything this should be the "classic desktop" arrangement.

Edit;
I just figured out a trick to get the UNR desktop to display and then turn off again if you want to switch it on or off.
After setting up the classic desktop add the "Go Home" and the "force quit" applets to one of your panels where ever you like. If you click the "Go Home" applet the UNR desktop starts. Then if you click the "Force quit" applet and click on an empty place on the UNR desktop and then confirm you want to "force quit" this application the UNR desktop goes off and you are back to the Classic desktop.
Between the two applets you have a switch to turn on or off the UNR desktop.


This worked very well for me. Thank you so much!

---

### Post by sickid on 2010-03-22
Does anyone know how to get my ~/Desktop files displayed on my Desktop?

---

### Post by ohiomoto on 2010-03-22
Follow the instructions in step #2.
> **phoenix55 said:**
> Here's what I did.

Step 1: Uncheck Maximus

   - Go to: System > Preferences
   - Uncheck 'Maximus Windows Management'
   - Restart the system
   New applications will not open maximized to the netbook's full screen

Step 2: Enable show_desktop

   - Open a terminal window (Accessories > Terminal)
   - Enter: gconf-editor. That opens the configuration editor GUI
   - Go to the node: / apps > nautilus > preferences (click preferences)
   - On the right window (showing the parameters associated with
        preferences) scroll down to 'show_desktop' and enable (click) it.
   This will get rid of the default desktop. No need to restart.

Step 3: Add the 'Main Menu' Applet to the panel

   - Right-click on the panel (mine is at the top edge)
   - Select the 'Main Menu' applet
   This will put the same menu structure as the original desktop but in a
   drop-down menu as the good old classical desktop.

  I still need to fine tune things a bit further (eg make minimized apps go to a panel at the bottom of the screen rather than the top panel) but in the meantime I've got what I want the most.

Enjoy the classical desktop look.

---

### Post by varanasi on 2010-05-11
Are those of you that are using gconf-editor to enable show desktop upgrading or new installs?  I ask because I cannot adjust that key.  Gconf-editor says it is unwritable.  Also, I cannot adjust - in any way - the top bar.  All the options to unlock the applets are greyed.

It occurs to me that these problems are because I have a clean, new install, and perhaps, I don't have the standard gnome desktop installed?

(I feel as if I have returned to the gentoo world!)

---

### Post by eltonw on 2010-05-11
> **varanasi said:**
> Are those of you that are using gconf-editor to enable show desktop upgrading or new installs?  I ask because I cannot adjust that key.  Gconf-editor says it is unwritable.  Also, I cannot adjust - in any way - the top bar.  All the options to unlock the applets are greyed.

It occurs to me that these problems are because I have a clean, new install, and perhaps, I don't have the standard gnome desktop installed?

(I feel as if I have returned to the gentoo world!)

_If by "*new installs*" you mean LUCID LYNX (10.4),_ then the procedure is much easier:
[http://ubuntuforums.org/showthread.php?p=9283097#post9283097]("http://ubuntuforums.org/showthread.php?p=9283097#post9283097") 

With Karmic, I never tried changing from the tabbed interface, because it felt too much like like "jumping through hoops"

cheers,

---

### Post by pete_m on 2010-05-13
thanks for all the guidance in this thread. . 

i've llaterly found ( linked elsewhere iin these forums) these useful hints

[http://maketecheasier.com/13-ways-to-customize-ubuntu-netbook-remix-for-better-usability/2010/02/07](http://maketecheasier.com/13-ways-to-customize-ubuntu-netbook-remix-for-better-usability/2010/02/07)


i've followed the process in 9.10 and now have a very flexible desktop- tho' panels are rather crowded on my netbook

i've made some screenshots of my work in progress - 
[http://www.youtube.com/watch?v=YoI4wRVVjBs](http://www.youtube.com/watch?v=YoI4wRVVjBs)


i have created a couple of perl scripts attacheed to launchers to **toggle** elements in my setup [B] - 

enable/ disable nautilus desktop[/B] 
you can use gconf-editor manually and  /apps/nautilus   keys to show/hide desktop should give you the right-clickable desktop

[B]show/hide simple nbr desktop
[/B] pkill netbook-launcher gets rid of it and the go-home applet will wake it again
i'm looking forward to developments in** Uunity** inteface and **DockbarX**  looks interesting

**show/hide  cairo-dock**

 **show/hide  cairo-clock**

happy to post the code if any are interested.  .

i'm writing this in **eb4** netbook remix   booted from a usb created on 9.10 - its default **Orbital theme** features nice icons, fine use of screen real-estate but seemingly lacks a show desktop button. several fave ubuntu apps are also not included . .

for reasons unknown to me the developers seem to have abandoned ubuntu in exclusive favour of Debian Sid.

i'm hoping to upgrade from karmic to lucid ( and perhaps maverick as it appears ) so as to continue benefit from the inestimable benefits of the Ubuntu  community.and to include sid as extra repositories 


P.S.

for those like me who like to tinker i've made a handful of custom launchers . .

NAUTILUS  - user home
nautilus --no-desktop --browser %U


AYOR - use root with caution - you can do damage from here

NAUTILUS  - ROOT home
gksu nautilus --no-desktop --browser %U

NAUTILUS  - filesystem as ROOT
gksu  nautilus --no-desktop --browser /

ROOT terminal :
gksu /usr/bin/x-terminal-emulator

ROOT GNOME CONFIGURATION  :
gksu gconf-editor


[COLOR=White]<pad>[/COLOR]

---

