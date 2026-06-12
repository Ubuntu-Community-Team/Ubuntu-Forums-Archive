---
title: "[SOLVED] Desktop cube 7.10"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by RuB3N on 2007-10-19
Where on ubuntu 7.10 is the desktop effects like desktop cube and wobbly windows?

---

### Post by sekazi on 2007-10-19
run this in a terminal
sudo apt-get install compizconfig-settings-manager

Advanced Desktop Effects Settings should appear in System > Preferences

---

### Post by RuB3N on 2007-10-19
but how do i enable it.... where u have 4 desktops...... i just got the program to run it

---

### Post by lazyart on 2007-10-19
System>Preferences>Appearance>Desktop Effects

---

### Post by tynen on 2007-10-19
Thanks for that tip, I got the settings installed, I'm trying to get the common cube that you see on youtube and stuff to work. Any Sugestions?

---

### Post by sharp65 on 2007-10-19
I need help with that too, specific options would be great. I've messed around but can't get it working.

---

### Post by Lavos on 2007-10-19
Here are a few things that might fix it:

Assuming you have already installed CompizFusion Settings Manager as described earlier, go to
System>Preferences>Advanced Desktop Effects Settings
and make sure that Desktop Cube and Rotate Cube are both enabled. The default keybinding for rotating the cube is "<Ctrl><Alt>Mousebutton1". Just hold down the mousebutton and drag, and the cube should move.

My cube was flat to begin with. If you have a "flat cube", the following commands should fix that. Just type them in a terminal window.
```

gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4
gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1
``` (Taken from the thread [http://ubuntuforums.org/showthread.php?t=359367](http://ubuntuforums.org/showthread.php?t=359367) )

---

### Post by Biggus on 2007-10-19
> **Lavos said:**
> Here are a few things that might fix it:

Assuming you have already installed CompizFusion Settings Manager as described earlier, go to
System>Preferences>Advanced Desktop Effects Settings
and make sure that Desktop Cube and Rotate Cube are both enabled. The default keybinding for rotating the cube is "<Ctrl><Alt>Mousebutton1". Just hold down the mousebutton and drag, and the cube should move.

My cube was flat to begin with. If you have a "flat cube", the following commands should fix that. Just type them in a terminal window.
```

gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4
gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1
``` (Taken from the thread [http://ubuntuforums.org/showthread.php?t=359367](http://ubuntuforums.org/showthread.php?t=359367) )

DUDE!

You are teh awesomeness!

Worked like a charm, I'm actually sitting here laughing at how totally, unbelievably, ridiculously awesome this is.

One gazillion thank yooz!

---

### Post by bluedragon436 on 2007-10-19
Ok, so I have gotten compiz and installed it and activated the rotating cube and everything, and for some reason or another when I go to change the desktops it pops up as a small 2D box that says desktop 2 or 1 depending on which one I go to.  I went to the Advanced Desktop Effects Settings, and it is clicked on Enabled for all of this stuff, but yet if I go to System>Prefernces>Apperance>Desktop Effects, and click on one of them to enable I get an error of The composite extension is not available....  Does anyone know what is up with this???  I have tried everything I can think of, and still no cube, just a plain old box...  I am coming close to just completely reloading 7.10 and go from there, but am trying not to have to do that if possible.

---

### Post by cwatson81 on 2007-10-19
When trying to install the compiz-config-settings-manager.  I get an error that reads:

E: Couldn't find package compiz-config-settings-manager

I'm new to linux.  What am I doing wrong?

---

### Post by sdowney717 on 2007-10-19
where are all the key bindings listed in the manager?

---

### Post by Lavos on 2007-10-19
> **bluedragon436 said:**
> Ok, so I have gotten compiz and installed it and activated the rotating cube and everything, and for some reason or another when I go to change the desktops it pops up as a small 2D box that says desktop 2 or 1 depending on which one I go to.  I went to the Advanced Desktop Effects Settings, and it is clicked on Enabled for all of this stuff, but yet if I go to System>Prefernces>Apperance>Desktop Effects, and click on one of them to enable I get an error of The composite extension is not available....  Does anyone know what is up with this???  I have tried everything I can think of, and still no cube, just a plain old box...  I am coming close to just completely reloading 7.10 and go from there, but am trying not to have to do that if possible.

The error message "The composite extension is not available" might be related to the graphics driver. If you are not using a restricted driver, I don't think the advanced desktop effects will work. Do you have anything enabled under System>Administration>Restricted drivers manager?

> **cwatson81 said:**
> When trying to install the compiz-config-settings-manager.  I get an error that reads:

E: Couldn't find package compiz-config-settings-manager

I'm new to linux.  What am I doing wrong?

Looks like you just got an extra hyphen between compiz and config - make sure you spell it compizconfig-settings-manager.

Or you can use the Synaptic Package Manager and install it from there.
System>Administration>Synaptic Package Manager , search for compiz and you should find the package there.

> **sdowney717 said:**
> where are all the key bindings listed in the manager?

When you click on a plugin with keybindings available in the manager, you can find (and change) the keybindings under the Actions tab.

---

### Post by sdowney717 on 2007-10-19
for example the water effect, there is no action tab and in the old compiz - fusion there was some key to make it show rain drops.
Also I did not see any thing about rotating thge cube even though I know it is cntrl+alt plus mouse1 button.

---

### Post by sdowney717 on 2007-10-19
[http://gentoo-wiki.com/Compiz](http://gentoo-wiki.com/Compiz)
i found this it is cntrl plus super key. But nowhere in my CCSM is this key binding shown. So is it now hidden from the user?

---

### Post by sdowney717 on 2007-10-19
wiki list, but not anywhere in my CCSM that I can find

 Using Plugins

So you've suffered long enough trying to get XGL installed, now how do you use it? Here are the various key combinations for various plugins:

Switch windows = Alt + Tab

Arrange and View All Windows = F12 turns on or off; clicking a window will zoom it to the front

Arrange and View All Windows (gnome-window-decorator, not cgwd) = Ctrl + Shift + Up turns on; clicking a window will zoom it to the front, or select window using arrows and release Ctrl + Shift

Arrange and View Windows of the Same Application = F11 turns on or off; clicking a window will zoom it to the front

Slow Motion = Shift + F10

Switch desktops on cube = Ctrl + Alt + Left/Right Arrow

Switch desktops on cube - with active window following = Ctrl + Shift + Alt + Left/Right Arrow

Flatten Cube - Ctrl + Alt + Page Down, then Left/Right Arrows to switch desktops

Flatten Cube (gnome-window-decorator, not cgwd) - Ctrl + Alt + Down, then Left/Right Arrows to switch desktops

Rotate desktop cube = Ctrl + Alt + Left-click on wallpaper and drag

Display svg picture on top of cube = modify gconf db,add svg files to /apps/compiz/plugins/cube/screen0/options/svgs (restart needed)

Make window translucent/opaque (built-in) = Alt + mouse wheel up/down

Make window translucent/opaque (with the opacity plugin) = Ctrl + Shift + Scroll, or right-click the window's title bar and select Opacity (seems to be absent in current compiz cvs.)

Zoom-in once = Super-key right-click

Zoom-in manually = Super-key + wheel mouse up

Zoom-out manually = Super-key + wheel mouse down

Move window = Alt + left-click

Snap Move window (will stick to borders) = Shift during move (either by Alt + left-click or by title bar)

Resize window = Alt + right-click

Resize window (gnome-window-decorator, not cgwd) = Alt + middle-click

Water Effect = Ctrl + Super-key (I have to press the Ctrl key first) - (depends on water plugin)

Rain = Shift + F9 (Requires the water plugin)

---

### Post by blackened on 2007-10-19
> **Lavos said:**
> Here are a few things that might fix it:

Assuming you have already installed CompizFusion Settings Manager as described earlier, go to
System>Preferences>Advanced Desktop Effects Settings
and make sure that Desktop Cube and Rotate Cube are both enabled. The default keybinding for rotating the cube is "<Ctrl><Alt>Mousebutton1". Just hold down the mousebutton and drag, and the cube should move.

My cube was flat to begin with. If you have a "flat cube", the following commands should fix that. Just type them in a terminal window.
```

gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4
gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1
``` (Taken from the thread [http://ubuntuforums.org/showthread.php?t=359367](http://ubuntuforums.org/showthread.php?t=359367) )

The options you quoted as terminal input can be found and changed graphically using the sliders in CompizConfig under "General"->"General Options"->"Desktop Size" tab.

---

### Post by frenchcr on 2007-10-19
sdowney717...thanks bud!:KS

---

### Post by Lavos on 2007-10-19
> **sdowney717 said:**
> [http://gentoo-wiki.com/Compiz](http://gentoo-wiki.com/Compiz)
i found this it is cntrl plus super key. But nowhere in my CCSM is this key binding shown. So is it now hidden from the user?

Strange, that screenshot has less options than I have in my CCSM (See attached image). Are you sure your CCSM is up to date?

---

### Post by sdowney717 on 2007-10-19
[http://ubuntuforums.org/showthread.php?t=534614](http://ubuntuforums.org/showthread.php?t=534614)
shift switcher is shift+ super+ s
then use arrows to flip

the negative plugin is super +n and super +m

I also found this guide blog that tells a lot about ccsm on gutsy
[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

I would like to see a complete key binding list from somewhere.

---

### Post by sdowney717 on 2007-10-19
If mine is not upto date that would explain a lot. Are you running gutsy? I am.

If you are using Gutsy, can you go into synaptic and tell me the version of your ccsm?

---

### Post by sdowney717 on 2007-10-19
here is my list.

---

### Post by sdowney717 on 2007-10-19
I am running version 0.5.2

---

### Post by Argus on 2007-10-19
Thanks,

I got all that working but when I have the effects activated I can move my windows around ie I can open a terminal window but is is stuck in the upper left corner with no buttons to close it.

Sean

---

### Post by the lush on 2007-10-19
I tried the advice from this thread, but it doesn't seem to work for me. The error returned by the terminal is:

dpkg: error processing linux-restricted-modules-2.6.20-15-generic (--remove):
 cannot remove file `/usr/share/doc/linux-restricted-modules-2.6.20-15-generic/changelog.Debian.gz': Not a directory
Errors were encountered while processing:
 linux-restricted-modules-2.6.20-15-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

I have no idea what it means, but coupled with other issues I am beginning to really regret this, hell, even Vista has sound and a working input editor (SCIM worked under Feisty, but along with my sound has disappeared in Gutsy).

Dapper was good, Edgy was OK, Feisty + Beryl was great, but Gutsy seems to have too many issues. Is it possible to roll back?

---

### Post by tomerl on 2007-10-19
I've tried your solutions here, and still the desktop is flat, ie, more like a paper not like a cube.

---

### Post by imaxami on 2007-10-19
Thanks!!!  I got all the way through this and fixed the 2 sided issue with this command.  Much appreciated.

---

### Post by srturner47 on 2007-10-20
Here's what I did to get the cube:

Install the compiz settings manager.
Switch to custom settings:  System-Preferences-Appearence-Visual Effects-Custom
Click on Preferences next to Custom or run System-Preferences-Advanced Desktop Effects
Click on General Options under General
Click on Desktop Size
Change Horizontal Virtual Size to 4, Veritcal Virtual Size to 1, and Number of Desktops to 1
Click Back
Under Desktop, click Desktop Cube and Rotate Cube

That's it!  It should work.  To play with the cube hold Control-Alt and Left click the mouse.  Drag around and drool!  :)

---

### Post by sdowney717 on 2007-10-20
'I got all that working but when I have the effects activated I can move my windows around ie I can open a terminal window but is is stuck in the upper left corner with no buttons to close it.'

you need to activate the windows decoration plugin. This puts the 'frame' on around the window, with the close buttons. this is under effects catagory.

You can install emerald and emerald themes. When you have the emerald theme selected, clicked on, then run emerald --replace and it will load the theme.

---

### Post by Argus on 2007-10-20
> **sdowney717 said:**
> 'I got all that working but when I have the effects activated I can move my windows around ie I can open a terminal window but is is stuck in the upper left corner with no buttons to close it.'

you need to activate the windows decoration plugin. This puts the 'frame' on around the window, with the close buttons. this is under effects catagory.

You can install emerald and emerald themes. When you have the emerald theme selected, clicked on, then run emerald --replace and it will load the theme.

Nope, I installed emerald now I can change the them but some windows still do not have the buttons on there frame and I still can't move the window anywhere.

---

### Post by perce on 2007-10-20
Hi,

I'm supposed to use he super key to use many of the effects in Compiz. In Beryl on Feisty super was the win key, but in Compiz on Gutsy it it opens the Gnome menu but doesn't trigger any effects, either alone ore in combination with other keys.

---

### Post by Argus on 2007-10-22
> **perce said:**
> Hi,

I'm supposed to use he super key to use many of the effects in Compiz. In Beryl on Feisty super was the win key, but in Compiz on Gutsy it it opens the Gnome menu but doesn't trigger any effects, either alone ore in combination with other keys.

It's bound to ctrl -alt left click, you can change binding in the compiz menu under cube rotate.

---

### Post by xph on 2007-10-22
does that works on Intel cards?

---

### Post by alion on 2007-10-22
The right package name is compizconfig-settings-manager

---

### Post by gregbzh on 2007-10-22
I can get the cube and rotate it OK, but when it is enabled I lose the use of the sidebars in Opera and Firefox (all-in-on sidebar add-on).  I can still open them but have a *dead zone*at the side of the screen where it is impossible to easily click on the sidebar toggles. 

The sidebars, which I use a lot, work no problem when the cube is disabled. 

Any ideas on how I can have both?

Cheers.

---

### Post by gganitis on 2007-10-22
I have the same problem with compiz on gutsy! It doesn't rotate like a cube. I tried the commands you suggested in this threat but, nothing happened!
It looks like flat, and the Ctrl Alt + Click in the mouse doesn't rotate the desktops. When I change desktop appears a box in the center of the monitor informs that I have changed desktop. No effects everywhere.

May these problems be appeared because I forgot to uninstall compiz fusion before upgrading from Feisty to Gutsy? How can I uninstall it now and install it again?

Thanks a lot.

---

### Post by Baby Boy on 2007-10-22
My cube isn't a cube but a rectangle (like only one side of the cube)! It can rotate and everything, but how do I make it a cube? :confused:

---

### Post by gregbzh on 2007-10-22
You just need to set up 4 desktops.  You probably currently have two, which is the default.  Right click on the desktop switcher on your taskbar and from there you can choose 4 desktops.  Voila.

---

### Post by Baby Boy on 2007-10-22
Yep, simple as that. Thanks.

---

### Post by BDNiner on 2007-10-22
These tips worked excellently for me. and i didn't uninstall the old compiz. so i am very gratefull. I just have one question. The mouse wheel rotates my cube. but only when the pointer of over an empty part of the desktop. is there anyway to change this? i have only found the key bindings for the keyboard and not the mouse.

---

### Post by rockin_goliath on 2007-10-22
> **cwatson81 said:**
> When trying to install the compiz-config-settings-manager.  I get an error that reads:

E: Couldn't find package compiz-config-settings-manager

I'm new to linux.  What am I doing wrong?

it should be "compizconfig-settings-manager."

---

### Post by Persianelfster on 2007-10-22
Anyone find the link between GL Desktop and Compiz casue they effect eachother, i mean my cube is working and all just wondering...

---

### Post by vdb007 on 2007-11-27
Hi Ubuntu Members,

My cube works but all the four screens are not connected like one big cube. Any help is appreciated. Thanks !

---

### Post by shameless on 2007-12-03
hey, i had this working earlier this weekend, on a temp install, but now that i've gone to a permanent install, i can't get it to work. I'm spelling the command right, yet i get this:

philip@ubuntu-thx1138:~$ sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager

I can't get through to the custom settings on the desktop, and i've read through and tried everything else pertinent, but still i can't get it to work, and i really liked having it set up as a pentagon, gave me plenty of space to work with

any help would be greatly appreciated

#edit -- i realized i needed to enable my universe and multiverse ^^

---

### Post by tenjin1 on 2007-12-05
These are the directions I used to get Compiz-Fusion installed and working great -> [http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/]("http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/")

As for the cube problems:

```
Getting the cube

Firstly, enable the following plugins (by checking the box next to them):

    * Desktop Cube - to actually use it, we might have to disable some other plugins (just follow the popup)

    * Rotate Cube - that is necessary to spin the cube

    * Viewport Switcher (optional) - if you want to change desktops with the mousewheel

    * Cube Caps (optional) - lets you use an images on top and bottom of the cube


Secondly, we have to increase the number of the virtual desktops to 4
at General Options &#8594; Desktop Size &#8594; Horizontal Virtual Size
(the other two options have to be left at 1 - it should look like this then)

Now we can switch desktops via [Ctrl]+[Alt]+[Left]/[Right] and spin the cube via [Ctrl]+[Alt]+[Left Mousebutton] (or via middle-click on the desktop).

Configuring the Cube

    * Set the cube (semi-)transparent
      Set Desktop Cube &#8594; Transparent Cube &#8594; Opacity During Rotation to 85.0000 (or what suits you best)

          o Additionally you might want to disable Lighing in General Options &#8594; Display Settings

    * Cange the cube's color
      Cube Caps &#8594; Appearance &#8594; Cube Top/Bottom Color - choose a color for each option, that fits best to your wallpaper

    * Cube on a glossy plane
      Enable the Cube Reflection plugin

    * Show the cube's engine
      Enable the Cube Gears plugin
```

---

### Post by AlienTechKilla on 2007-12-05
So I have Compiz running on another machine (fiesty) with no issues but on my new machine I get an error when trying to sudo get the compizconfig-settings-manager. I have the same error as the guy above but I also don't see the option for this manager under synaptic. There's the command line:

paul@AlienTechKilla:~$ sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager

In synaptic I do see gnome-compiz-manager & compiz-extra as well as others. This is a fresh install of Ubuntu 7.04 ->upgraded to gusty via the update manager. Nothing has been installed but the upgrade. Any suggestions would greatly be appreciated

---

### Post by AlienTechKilla on 2007-12-05
I'm bumping again to see if anyone has experienced this before. My next step will be to download gusty and try again... but I'd really like to not have to do that. Again any help is anyways appreciated.

---

### Post by shameless on 2007-12-06
Ok, now i'm really confused. I had it working fine, but when i went through to work on getting an all mac skin, things stopped working. I haven't been able to even open the advanced config window, though i can see the processor trying to open it due to the jump in the load level. I'm using kiba-dock for the bottom docking bar, and i've got beryl and emerald on here too. I have something called compiz setting manager that's adjacent to compizconfig settings manager, it seems like i haven't been able to do anything since that popped up, but i'm not sure what program it's part of, and i can't find anything on it either. Some help please?

---

### Post by honkey on 2008-06-24
i cant type in my password if i want to install the compiz...
whatr is wrong in here?:confused:

---

