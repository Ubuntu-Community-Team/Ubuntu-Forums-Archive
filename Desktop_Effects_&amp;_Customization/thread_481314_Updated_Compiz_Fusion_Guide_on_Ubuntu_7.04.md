---
title: "*Updated* Compiz Fusion Guide on Ubuntu 7.04"
date: 2007-06-23
forum: Desktop Effects &amp; Customization
---

### Post by isaacj87 on 2007-06-23
Hello, My problem isn't the installation...I've got it fully installed...but how do I get Compiz Fusion to start when I boot up? I tried adding 'compiz --replace' to the sessions but when I do it gives me a black screen. :(

---

### Post by jtraub on 2007-06-23
I have ATi X1900 XT and proprietary drivers installed on my machine (default from Feisty repositories)
```

mikv@hawk:~$ glxinfo | grep rendering
direct rendering: Yes
mikv@hawk:~$ glxinfo | grep texture_from_pixmap
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 

```
But last step of this guide ends with following errors
```

mikv@hawk:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

```

Any ideas?

---

### Post by moevmie on 2007-06-23
Hello, I'm getting this message when i try to install it, does anybody have any idea why????

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz: Depends: compiz-decorator but it is not installable
E: Broken packages
```

thanks in advance
m

EDIT: I'VE HAD THIS PROBLEM, BUT I MANAGED TO GET IT INSTALLED NOW, I THINK THE REPOSITORIES CHANGED...

---

### Post by crimesaucer on 2007-06-23
Thank you for the nice easy guide.

---

### Post by mostwanted on 2007-06-23
Not getting any window decorations... :(

---

### Post by BungaMan on 2007-06-23
me neither, it gives a warning about the version:

/usr/bin/compiz.real (decoration) - Warn: Property ignored because version is 20061011 and decoration plugin version is 20070319

---

### Post by pmj on 2007-06-23
I didn't get any window decorations either. But then again, I've never gotten window decorations with Compiz, only with Beryl.

---

### Post by Vorian on 2007-06-23
run alt+F2
and enter:
```
emerald --replace &
```

That will give you your default emerald theme

---

### Post by BungaMan on 2007-06-23
or you can run it as 
```
compiz --replace -c emerald &
```
got it from here [http://forums.opencompositing.org/viewtopic.php?f=14&t=131&p=6191&hilit=Property+ignored+because+version#p6191](http://forums.opencompositing.org/viewtopic.php?f=14&t=131&p=6191&hilit=Property+ignored+because+version#p6191)
However it did not give me borders just yet because emerald was not installed
so first install it with the following command and then run the command above...
```
sudo apt-get install emerald
```

---

### Post by pmj on 2007-06-23
Neither emerald --replace nor compiz --replace -c emerald & gives me decorations. In fact, the latter one gives me the following message:
```
/usr/bin/compiz: line 681: 30436 Segmentation fault      (core dumped) $@ 2>> $ERROUTPUT
```

It continues to load though, and animations and all are working. I just have no decorations. And yes, I did install emerald.

Edit: Updates mere minutes after installation? Yup, and they fixed my problems. Emerald works now.

---

### Post by Asraniel on 2007-06-23
how can i switch back to the kwin? compiz is nice, but xorg uses 500mb now.. thats a little bit too much for my taste (and from a usability point of view kwin is much better anyway)

---

### Post by fuoco on 2007-06-23
i have it all up and running, but many configurations won't work for me. for example no matter what i can't get a 4-sided cube. i get only 2 sides, 3 sides or 5 and more. also animations don't work (for example for minimizing, opening, closing etc..).
wobbly works rather badly even though it was very good with the 0.3.6 version i had before that.

any ideas?

---

### Post by Reb on 2007-06-23
My problem is that I can't get images on top (cube caps?), behind (skydome image?), and I don't even know what background image is.  Even when I set all of these with a 2560x1600 image, nothing shows up anywhere.   Is it a problem if the image is much larger than my screen resolution?

---

### Post by c.dric on 2007-06-23
thanks for the howto.

i do have a few problems with fusion tho ... 

1) i only have 500mb of ram and a nvidia card with 64mb of ram ... when i have more than 3 or 4 windows open the following windows i try to open are filled black. 

if i remember correctly, beryl used to have some kind of rendering options that would fix this problem on my comp ... anyone know if there is something similar with this setup ?

this one is [COLOR="Red"][solved][/COLOR]. starting compiz with --indirect-rendering fixes it.
found it here : [http://forums.opencompositing.org/viewtopic.php?f=40&t=522&st=0&sk=t&sd=a&hilit=black+window](http://forums.opencompositing.org/viewtopic.php?f=40&t=522&st=0&sk=t&sd=a&hilit=black+window)

2) when i log out and back in of a gnome session with fusion ... gnome gets stuck ... all i get is a cursor and a black screen ... rebooting the comp seems to fix the problem ... gnome starts properly ... so does fusion...

any ideas ?

thanks :D

---

### Post by crimesaucer on 2007-06-23
> **Reb said:**
> My problem is that I can't get images on top (cube caps?), behind (skydome image?), and I don't even know what background image is.  Even when I set all of these with a 2560x1600 image, nothing shows up anywhere.   Is it a problem if the image is much larger than my screen resolution?

Hey Reb, I had Beryl installed before this and when I installed and ran compiz --replace

...this also happened to me with the cube cap and other plug-ins not working, and what I had to do was open up my Beryl Settings Manager and click it back to XFWM (my original window manager), then I ran the compiz --replace command again and everything worked perfectly...reflection, cube caps, my super key...

I also set my old Beryl Manager to XFWM, then took Beryl off of the start up apps, and added the "compiz --replace" command and the "emerald --replace" commands to my start up apps and everything works perfectly from the start now.

...and I also think Wobbly is worse now, but everything else is very nice so it doesn't matter, it will be better in a few weeks.

---

### Post by precinto on 2007-06-23
Is anyone having problems with video playing? 

I can't use the xv video option in mplayer, it won't output the image, just the sound. The only one working is gl, but but I get a shivering image. VLC goes black when toggling fullscreen.

I'm using AIGLX with the ati open driver.

---

### Post by crimesaucer on 2007-06-23
I just checked, and YES, my sound works but my video does not.

---

### Post by P_Badger on 2007-06-23
> **crimesaucer said:**
> I just checked, and YES, my sound works but my video does not.

I'm also having the exact same issue.

On top of that, I don't get anything but a temporary desktop freeze when I try to right-click my mouse. No menu appears. Anybody know how to get around that?

---

### Post by precinto on 2007-06-23
BTW, launching from a terminal doesn't show any error in neither application. And with mplayer the video window plays a dark blue screen, with a little transparency you can correct with Alt+wheel. Video image is sometimes visible when changing between normal and fullscreen.

---

### Post by fuoco on 2007-06-23
> **precinto said:**
> Is anyone having problems with video playing? 

I can't use the xv video option in mplayer, it won't output the image, just the sound. The only one working is gl, but but I get a shivering image. VLC goes black when toggling fullscreen.

I'm using AIGLX with the ati open driver.

possibly this is a problem that is fixed in the ati driver version 6.6.192

---

### Post by Treviño on 2007-06-23
**Many thanks to Vorian** for posting *_this guide_* I had no time for making it here too (after the wiki, I mean), so thanks!

I'd suggest all users to read also the opencompositing thread since there are many helps there, that allow users to improve their experience... :)

Bye!

PS: The first link to the compiz wiki is wrong (double http :))

---

### Post by walkerk on 2007-06-23
Nice write up. I'm now running Compiz Fusion on a Dell 6400 w/ intergrated 945GM video. :D

---

### Post by gloomy on 2007-06-23
> **moevmie said:**
> Hello, I'm getting this message when i try to install it, does anybody have any idea why????

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz: Depends: compiz-decorator but it is not installable
E: Broken packages
```

thanks in advance
m

Having the same problem. 

Did step by step what was explained above.

Anybody any idea please ?

---

### Post by precinto on 2007-06-23
> **fuoco said:**
> possibly this is a problem that is fixed in the ati driver version 6.6.192

How do I know which version of the driver I am using? And is it possible to upgrade it?

---

### Post by crimesaucer on 2007-06-23
I fixed my Xine movie palyer like this: The Settings-->--Set Up-->--Video-->--I changed the driver from "auto" to "xshm"  and it worked for playback.

I also fixed the transparent video like this: ccsm-->--General-->--Opacity Settings-->--Window Opacities-->-- then edit the string and take "Unkown" off of the list.

---

### Post by c.dric on 2007-06-23
> **c.dric said:**
> 
1) i only have 500mb of ram and a nvidia card with 64mb of ram ... when i have more than 3 or 4 windows open the following windows i try to open are filled black. 

if i remember correctly, beryl used to have some kind of rendering options that would fix this problem on my comp ... anyone know if there is something similar with this setup ?

apparently it's a common problem with nvidia cards : 
[http://forums.opencompositing.org/viewtopic.php?f=51&t=438](http://forums.opencompositing.org/viewtopic.php?f=51&t=438)

anyone knows how to apply those fixes with fusion ?

this one is [COLOR="Red"][solved][/COLOR]. starting compiz with --indirect-rendering fixes it.
found it here : [http://forums.opencompositing.org/viewtopic.php?f=40&t=522&st=0&sk=t&sd=a&hilit=black+window](http://forums.opencompositing.org/viewtopic.php?f=40&t=522&st=0&sk=t&sd=a&hilit=black+window)

---

### Post by wvengen on 2007-06-23
Too bad 64 bit isn't fully present as of yet ...
[http://download.tuxfamily.org/3v1deb/dists/feisty/eyecandy/binary-amd64/Packages]("http://download.tuxfamily.org/3v1deb/dists/feisty/eyecandy/binary-amd64/Packages")

---

### Post by stani on 2007-06-23
Works like a charm, even on my old Thinkpad X30 (1.2GHz Pentium III-M & 768MB, with a somewhat unglamorous but perfectly adequate Intel 830 graphics controller).

---

### Post by giuseppe- on 2007-06-23
Hi guys, I installed all without problem but when I try compiz --replace nothing happen, Ubuntu still use metacity. Here's compiz --replace output, I hope you can help me.
```
giuseppe@ubuntu:~$ compiz --replace
Adding core settings (General Options)
Adding plugin neg (neg)
Adding plugin move (move)
Adding plugin scaleaddon (scaleaddon)
Adding plugin animation (animation)
Adding plugin expo (expo)
Adding plugin bench (bench)
Adding plugin reflex (reflex)
Adding plugin annotate (annotate)
Adding plugin vpswitch (vpswitch)
Adding plugin video (video)
Adding plugin put (put)
Adding plugin clone (clone)
Adding plugin inotify (inotify)
Adding plugin ring (ring)
Adding plugin crashhandler (crashhandler)
Adding plugin text (text)
Adding plugin dbus (dbus)
Adding plugin mblur (mblur)
Adding plugin firepaint (firepaint)
Adding plugin tile (tile)
Adding plugin fadedesktop (fadedesktop)
Adding plugin snap (snap)
Adding plugin showdesktop (showdesktop)
Adding plugin svg (svg)
Adding plugin wall (wall)
Adding plugin thumbnail (thumbnail)
Adding plugin imgjpeg (imgjpeg)
Adding plugin rotate (rotate)
Adding plugin resizeinfo (resizeinfo)
Adding plugin opacify (opacify)
Adding plugin decoration (decoration)
Adding plugin glib (glib)
Adding plugin snow (snow)
Adding plugin extrawm (extrawm)
Adding plugin switcher (switcher)
Adding plugin splash (splash)
Adding plugin trailfocus (trailfocus)
Adding plugin scale (scale)
Adding plugin png (png)
Adding plugin regex (regex)
Adding plugin addhelper (addhelper)
Adding plugin cube (cube)
Adding plugin blur (blur)
Adding plugin fs (fs)
Adding plugin zoom (zoom)
Adding plugin resize (resize)
Adding plugin fade (fade)
Adding plugin winrules (winrules)
Adding plugin fakeargb (fakeargb)
Adding plugin plane (plane)
Adding plugin cubereflex (cubereflex)
Adding plugin minimize (minimize)
Adding plugin place (place)
Adding plugin wobbly (wobbly)
Adding plugin group (group)
Adding plugin screenshot (screenshot)
Adding plugin water (water)
Backend     : ini
Integration : true
Profile     : default
Initializing core options...done
Initializing move options...done
Initializing decoration options...done
Initializing zoom options...done
Initializing resize options...done
Initializing minimize options...done
Initializing place options...done
Initializing wobbly options...done
Initializing fade options...done
Initializing cube options...done
Initializing rotate options...done
Initializing switcher options...done
Initializing scale options...done
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined s
```
Thanks for the guide :D

---

### Post by johntelthorst on 2007-06-23
> **jtraub said:**
> I have ATi X1900 XT and proprietary drivers installed on my machine (default from Feisty repositories)
```

mikv@hawk:~$ glxinfo | grep rendering
direct rendering: Yes
mikv@hawk:~$ glxinfo | grep texture_from_pixmap
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 

```
But last step of this guide ends with following errors
```

mikv@hawk:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

```

Any ideas?

I'm getting the same errors,  I have an ATI Radeon Xpress 200M

---

### Post by walkerk on 2007-06-23
nice write up :) i've got compiz fusion running great on a dell 6400 w/ 945gm integrated video..

seems to be working even better than beryl :)

---

### Post by precinto on 2007-06-23
> **johntelthorst said:**
> I'm getting the same errors,  I have an ATI Radeon Xpress 200M

I also got that error at first. I don't remember exactly what it was related to. Are you running a XGL session?

---

### Post by fuoco on 2007-06-23
> **precinto said:**
> How do I know which version of the driver I am using? And is it possible to upgrade it?

try:
dpkg-query -s xserver-xorg-video-ati|grep Version

well, 6.6.192 is not in ubuntu, it is in debian unstable or something like that. i used 'prevu' to create myself a working dev. Also a recent mesa is important usually. Gutsy has 6.5.3 which I also got using 'prevu'. just yesterday mesa 7.0 was released, and that might give even more advantage, but it's not yet on repos, so we should wait...

---

### Post by jtraub on 2007-06-23
> **johntelthorst said:**
> I'm getting the same errors,  I have an ATI Radeon Xpress 200M

Have you installed XGL? Install it and than log in.

---

### Post by johntelthorst on 2007-06-23
> **jtraub said:**
> Have you installed XGL? Install it and than log in.

No, I haven't, how do I go about that?  Thanks for the reply.

---

### Post by moevmie on 2007-06-23
The 64 bit version isn't really working yet i heard, I hope it's coming soon. Does anybody know anything about this????

thanks.
m

---

### Post by ramos289 on 2007-06-23
> **giuseppe- said:**
> Hi guys, I installed all without problem but when I try compiz --replace nothing happen, Ubuntu still use metacity. Here's compiz --replace output, I hope you can help me.
```
giuseppe@ubuntu:~$ compiz --replace
Adding core settings (General Options)
Adding plugin neg (neg)
Adding plugin move (move)
Adding plugin scaleaddon (scaleaddon)
Adding plugin animation (animation)
Adding plugin expo (expo)
Adding plugin bench (bench)
Adding plugin reflex (reflex)
Adding plugin annotate (annotate)
Adding plugin vpswitch (vpswitch)
Adding plugin video (video)
Adding plugin put (put)
Adding plugin clone (clone)
Adding plugin inotify (inotify)
Adding plugin ring (ring)
Adding plugin crashhandler (crashhandler)
Adding plugin text (text)
Adding plugin dbus (dbus)
Adding plugin mblur (mblur)
Adding plugin firepaint (firepaint)
Adding plugin tile (tile)
Adding plugin fadedesktop (fadedesktop)
Adding plugin snap (snap)
Adding plugin showdesktop (showdesktop)
Adding plugin svg (svg)
Adding plugin wall (wall)
Adding plugin thumbnail (thumbnail)
Adding plugin imgjpeg (imgjpeg)
Adding plugin rotate (rotate)
Adding plugin resizeinfo (resizeinfo)
Adding plugin opacify (opacify)
Adding plugin decoration (decoration)
Adding plugin glib (glib)
Adding plugin snow (snow)
Adding plugin extrawm (extrawm)
Adding plugin switcher (switcher)
Adding plugin splash (splash)
Adding plugin trailfocus (trailfocus)
Adding plugin scale (scale)
Adding plugin png (png)
Adding plugin regex (regex)
Adding plugin addhelper (addhelper)
Adding plugin cube (cube)
Adding plugin blur (blur)
Adding plugin fs (fs)
Adding plugin zoom (zoom)
Adding plugin resize (resize)
Adding plugin fade (fade)
Adding plugin winrules (winrules)
Adding plugin fakeargb (fakeargb)
Adding plugin plane (plane)
Adding plugin cubereflex (cubereflex)
Adding plugin minimize (minimize)
Adding plugin place (place)
Adding plugin wobbly (wobbly)
Adding plugin group (group)
Adding plugin screenshot (screenshot)
Adding plugin water (water)
Backend     : ini
Integration : true
Profile     : default
Initializing core options...done
Initializing move options...done
Initializing decoration options...done
Initializing zoom options...done
Initializing resize options...done
Initializing minimize options...done
Initializing place options...done
Initializing wobbly options...done
Initializing fade options...done
Initializing cube options...done
Initializing rotate options...done
Initializing switcher options...done
Initializing scale options...done
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined s
```
Thanks for the guide :D

I had the same problem.  The libdecoration0 package needs to be upgraded too.   Just do a search in Synaptic for libdecoration and upgrade it.

---

### Post by blanky on 2007-06-23
This is what I get when I run 'compiz --replace' from the terminal (Cause from ALT+F2 it wouldn't work, wanted to see what was up):

> 
jorge@blank:~$ compiz --replace
Adding plugin cube (cube)
Adding plugin resizeinfo (resizeinfo)
Adding plugin thumbnail (thumbnail)
Adding plugin screenshot (screenshot)
Adding plugin expo (expo)
Adding plugin video (video)
Adding plugin fade (fade)
Adding plugin clone (clone)
Adding plugin scale (scale)
Adding plugin fakeargb (fakeargb)
Adding plugin mblur (mblur)
Adding plugin scaleaddon (scaleaddon)
Adding plugin put (put)
Adding plugin firepaint (firepaint)
Adding plugin minimize (minimize)
Adding plugin switcher (switcher)
Adding plugin group (group)
Adding plugin snap (snap)
Adding plugin rotate (rotate)
Adding plugin trailfocus (trailfocus)
Adding plugin bench (bench)
Adding plugin showdesktop (showdesktop)
Adding plugin splash (splash)
Adding plugin water (water)
Adding plugin winrules (winrules)
Adding plugin reflex (reflex)
Adding plugin tile (tile)
Adding plugin zoom (zoom)
Adding plugin place (place)
Adding plugin inotify (inotify)
Adding plugin animation (animation)
Adding plugin move (move)
Adding plugin plane (plane)
Adding plugin wobbly (wobbly)
Adding plugin opacify (opacify)
Adding plugin cubereflex (cubereflex)
Adding plugin glib (glib)
Adding plugin fadedesktop (fadedesktop)
Adding plugin resize (resize)
Adding plugin addhelper (addhelper)
Adding plugin dbus (dbus)
Adding plugin imgjpeg (imgjpeg)
Adding plugin text (text)
Adding plugin snow (snow)
Adding plugin neg (neg)
Adding plugin decoration (decoration)
Adding plugin fs (fs)
Adding core settings (General Options)
Adding plugin blur (blur)
Adding plugin png (png)
Adding plugin wall (wall)
Adding plugin regex (regex)
Adding plugin svg (svg)
Adding plugin ring (ring)
Adding plugin vpswitch (vpswitch)
Adding plugin annotate (annotate)
Adding plugin extrawm (extrawm)
Adding plugin crashhandler (crashhandler)
Backend     : ini
Integration : true
Profile     : default
Initializing core options...done
Initializing minimize options...done
Initializing zoom options...done
Initializing place options...done
Initializing move options...done
Initializing resize options...done
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity


By the way, this is what 'glxinfo | grep rendering' says:

> 
jorge@blank:~$ glxinfo | grep rendering
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No


I've had that problem before, just forget how to solve it. Here's 'fglrxinfo':

> 
jorge@blank:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro
OpenGL version string: 2.0.6334 (8.34.8)


This is in my XGL session. In my other sessions, everything is perfectly fine, my drivers work, I play Enemy Territory at full hardware acceleration.

Can anyone help? Thanks!

---

### Post by Vorian on 2007-06-23
> **Treviño said:**
> 
PS: The first link to the compiz wiki is wrong (double http :))
Fixed, sorry about that :)

Thanks again for the package Treviño :)

---

### Post by P_Badger on 2007-06-23
Is ANYBODY else having issues with their right-click menu? For the life of me, I can't get it working. When I right-click, the whole desktop freezes until I zoom into it, which seems to get things going, again.

---

### Post by detyabozhye on 2007-06-23
Works tight! Using CompComm and Emerald because I like to have the titlebar scroll to shade/unshade thing. Does anyone know why the default Compiz decorator doesn't have an option for that (or did I miss it somehow)?

---

### Post by SveinT on 2007-06-23
Got things installed correctly, but for some reason it's horribly horribly slow on all other viewports/desktops than the main one. If I go right or left on the cube things start to get really slow, but as soon as I change back it's smooth again. Doesn't matter what method I use to switch desktop/viewport. Any ideas?

-edit-

Got it fixed by adjusting the horizontal size to 1 and then back to 5. There seems to be a bug in the config as 5 gives me 4, but it works perfectly now at least.

---

### Post by tprzepiorka on 2007-06-23
I'm not advanced with Ubuntu at all and was having some troubles. I followed the guide without problems but when I ran Compiz my desktop started having problems. The top bar on windows disappeared and I couldn't switch windows and none of the open windows were showing up on the window selector. I get none of the effects though and I am forced to restart Ubuntu.

 I am running Comaq nc6000, with ATI Mobility Radeon 9600 M10. Any help will be appreciated. (And yes I know it isn't a stable release and everything, but I still want to try to get it working ;))

---

### Post by Dashdot on 2007-06-23
> ian@desktop:~$ libdecoration
bash: libdecoration: command not found
ian@desktop:~$ compiz --replace
Adding plugin place (place)
Adding plugin ring (ring)
Adding plugin fade (fade)
Adding plugin wobbly (wobbly)
Adding plugin fadedesktop (fadedesktop)
Adding plugin opacify (opacify)
Adding plugin snow (snow)
Adding plugin winrules (winrules)
Adding plugin screenshot (screenshot)
Adding plugin fakeargb (fakeargb)
Adding plugin tile (tile)
Adding plugin dbus (dbus)
Adding plugin snap (snap)
Adding plugin firepaint (firepaint)
Adding plugin expo (expo)
Adding plugin thumbnail (thumbnail)
Adding plugin imgjpeg (imgjpeg)
Adding plugin switcher (switcher)
Adding plugin regex (regex)
Adding plugin zoom (zoom)
Adding plugin group (group)
Adding plugin blur (blur)
Adding plugin scale (scale)
Adding plugin svg (svg)
Adding plugin animation (animation)
Adding plugin fs (fs)
Adding plugin bench (bench)
Adding plugin crashhandler (crashhandler)
Adding plugin scaleaddon (scaleaddon)
Adding plugin mblur (mblur)
Adding plugin splash (splash)
Adding plugin move (move)
Adding plugin wall (wall)
Adding core settings (General Options)
Adding plugin glib (glib)
Adding plugin water (water)
Adding plugin vpswitch (vpswitch)
Adding plugin resizeinfo (resizeinfo)
Adding plugin clone (clone)
Adding plugin resize (resize)
Adding plugin addhelper (addhelper)
Adding plugin video (video)
Adding plugin reflex (reflex)
Adding plugin cube (cube)
Adding plugin showdesktop (showdesktop)
Adding plugin put (put)
Adding plugin trailfocus (trailfocus)
Adding plugin inotify (inotify)
Adding plugin neg (neg)
Adding plugin decoration (decoration)
Adding plugin annotate (annotate)
Adding plugin cubereflex (cubereflex)
Adding plugin rotate (rotate)
Adding plugin extrawm (extrawm)
Adding plugin png (png)
Adding plugin text (text)
Adding plugin plane (plane)
Adding plugin minimize (minimize)
Backend     : ini
Integration : true
Profile     : default
Initializing core options...done
Initializing place options...done
X connection to :0.0 broken (explicit kill or server shutdown).
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
Can't run metacity 
ian@desktop:~$ 



Whats going on?

---

### Post by Kayne on 2007-06-23
This guide worked for me, thank you very much! :)

Just two issues:
- When a new window opens, the window appears at the top left, but the titlebar is off-screen! So I have to hold <Alt> and drag the window down every time. Pretty annoying! Any solution for that?? I'm using emerald btw.
- The scale plug-in in Beryl did also show minimized windows, which was very useful! So I wonder, why this option was removed in Compiz Fusion :(

---

### Post by Vorian on 2007-06-23
> **Dashdot said:**
> Whats going on?
Use ALT+F2 and enter
```
compiz --replace -c emerald &
```
Try not to use the command in a terminal.

---

### Post by Dashdot on 2007-06-23
I did everything. There didn't seem to be any major problems BUT none of the extra functions in the "CompizConfig Setting Manger". I feel stupid. Lol.

---

### Post by Kayne on 2007-06-23
> **Kayne said:**
> This guide worked for me, thank you very much! :)

Just two issues:
- When a new window opens, the window appears at the top left, but the titlebar is off-screen! So I have to hold <Alt> and drag the window down every time. Pretty annoying! Any solution for that?? I'm using emerald btw.
- The scale plug-in in Beryl did also show minimized windows, which was very useful! So I wonder, why this option was removed in Compiz Fusion :(
Just found a solution for the first one. Activating the Places Plug-in solves that problem :)

---

### Post by Vorian on 2007-06-23
do this again in a terminal...
> sudo apt-get install compizconfig-backend-*

---

### Post by Treviño on 2007-06-23
> **Vorian said:**
> do this again in a terminal...
Names changed, now they are
```
libcompizconfig-backend-gconf
libcompizconfig-backend-kconfig
```

---

### Post by Vorian on 2007-06-23
> **Treviño said:**
> Names changed, now they are
```
libcompizconfig-backend-gconf
libcompizconfig-backend-kconfig
```

Thanks for the update :)

---

### Post by jefrazie on 2007-06-23
hey, thx for guide. worked perfectly for me. I have gotten everything to run fine. my comp specs are: core duo, 1gb ram, ati x1400 radeon

---

### Post by vh1 on 2007-06-23
when I just tried running this, it ran ridiculously slow
I'm talking like 2fps. it's on a macbook, but beryl runs flawlessly on this machine

---

### Post by Happy_Man on 2007-06-23
> **ramos289 said:**
> I had the same problem.  The libdecoration0 package needs to be upgraded too.   Just do a search in Synaptic for libdecoration and upgrade it.
Hehe, yeah, that took me about two hours to figure out when I was installing. Works great now though! 

(can't say anything about this thread, as I didn't use it. I compiled. The HARDCORE way!)

---

### Post by slippietheslip on 2007-06-23
Installs, but when i do the "compiz --replace" the screen flickers and nothing else happens.  I typed the command in the terminal and this is what I get.

Adding plugin neg (neg)
Adding plugin extrawm (extrawm)
Adding plugin scaleaddon (scaleaddon)
Adding plugin decoration (decoration)
Adding plugin regex (regex)
Adding plugin opacify (opacify)
Adding plugin imgjpeg (imgjpeg)
Adding plugin crashhandler (crashhandler)
Adding plugin vpswitch (vpswitch)
Adding plugin winrules (winrules)
Adding plugin glib (glib)
Adding plugin snap (snap)
Adding plugin splash (splash)
Adding plugin resizeinfo (resizeinfo)
Adding plugin group (group)
Adding plugin wobbly (wobbly)
Adding plugin cube (cube)
Adding plugin trailfocus (trailfocus)
Adding plugin text (text)
Adding plugin clone (clone)
Adding plugin video (video)
Adding plugin dbus (dbus)
Adding plugin showdesktop (showdesktop)
Adding plugin fade (fade)
Adding plugin annotate (annotate)
Adding plugin tile (tile)
Adding plugin animation (animation)
Adding plugin svg (svg)
Adding plugin switcher (switcher)
Adding plugin thumbnail (thumbnail)
Adding plugin water (water)
Adding plugin inotify (inotify)
Adding plugin addhelper (addhelper)
Adding plugin plane (plane)
Adding plugin move (move)
Adding plugin fakeargb (fakeargb)
Adding plugin cubereflex (cubereflex)
Adding plugin snow (snow)
Adding core settings (General Options)
Adding plugin rotate (rotate)
Adding plugin blur (blur)
Adding plugin resize (resize)
Adding plugin expo (expo)
Adding plugin mblur (mblur)
Adding plugin reflex (reflex)
Adding plugin bench (bench)
Adding plugin fs (fs)
Adding plugin png (png)
Adding plugin wall (wall)
Adding plugin put (put)
Adding plugin zoom (zoom)
Adding plugin ring (ring)
Adding plugin fadedesktop (fadedesktop)
Adding plugin place (place)
Adding plugin minimize (minimize)
Adding plugin firepaint (firepaint)
Adding plugin screenshot (screenshot)
Adding plugin scale (scale)
Backend     : ini
Integration : true
Profile     : default
Initializing core options...done
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

---

### Post by pjones0404 on 2007-06-23
just a quick question for everyone.

i am currently running edgy and i also have beryl installed and working. Will this same guide work for edgy or do i have to upgrade to feisty to get fusion working? 

thanks for any advice.

---

### Post by DarkMageZ on 2007-06-23
to those users of FGLRX... compiz/beryl/compiz-fusion will not work without using XGL.
XGL will break other functions of the system.

best advice. go downgrade to the opensource ati drivers if your card is supported by them or go complain to ATi about crappy drivers... tho you're probably better off buying a real graphics card.

---

### Post by mevets on 2007-06-23
For those that **can't** get emerald to draw window decorations try:
```

compiz  --indirect-rendering --replace

```
When I ran this it ran Compiz with kwin drawing the decorations. Its not emerald, but kwin is still nice.

---

### Post by jtraub on 2007-06-23
> **slippietheslip said:**
> Installs, but when i do the "compiz --replace" the screen flickers and nothing else happens.  I typed the command in the terminal and this is what I get.

Adding plugin neg (neg)
Adding plugin extrawm (extrawm)
Adding plugin scaleaddon (scaleaddon)
Adding plugin decoration (decoration)
Adding plugin regex (regex)
Adding plugin opacify (opacify)
Adding plugin imgjpeg (imgjpeg)
Adding plugin crashhandler (crashhandler)
Adding plugin vpswitch (vpswitch)
Adding plugin winrules (winrules)
Adding plugin glib (glib)
Adding plugin snap (snap)
Adding plugin splash (splash)
Adding plugin resizeinfo (resizeinfo)
Adding plugin group (group)
Adding plugin wobbly (wobbly)
Adding plugin cube (cube)
Adding plugin trailfocus (trailfocus)
Adding plugin text (text)
Adding plugin clone (clone)
Adding plugin video (video)
Adding plugin dbus (dbus)
Adding plugin showdesktop (showdesktop)
Adding plugin fade (fade)
Adding plugin annotate (annotate)
Adding plugin tile (tile)
Adding plugin animation (animation)
Adding plugin svg (svg)
Adding plugin switcher (switcher)
Adding plugin thumbnail (thumbnail)
Adding plugin water (water)
Adding plugin inotify (inotify)
Adding plugin addhelper (addhelper)
Adding plugin plane (plane)
Adding plugin move (move)
Adding plugin fakeargb (fakeargb)
Adding plugin cubereflex (cubereflex)
Adding plugin snow (snow)
Adding core settings (General Options)
Adding plugin rotate (rotate)
Adding plugin blur (blur)
Adding plugin resize (resize)
Adding plugin expo (expo)
Adding plugin mblur (mblur)
Adding plugin reflex (reflex)
Adding plugin bench (bench)
Adding plugin fs (fs)
Adding plugin png (png)
Adding plugin wall (wall)
Adding plugin put (put)
Adding plugin zoom (zoom)
Adding plugin ring (ring)
Adding plugin fadedesktop (fadedesktop)
Adding plugin place (place)
Adding plugin minimize (minimize)
Adding plugin firepaint (firepaint)
Adding plugin screenshot (screenshot)
Adding plugin scale (scale)
Backend     : ini
Integration : true
Profile     : default
Initializing core options...done
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Upgrade from Synaptic your libdecoration to version 0.5. After that effects should work.

---

### Post by standardissue on 2007-06-24
> **jtraub said:**
> Upgrade from Synaptic your libdecoration to version 0.5. After that effects should work.

I had the same problem, and that fixed it! Everything works now but the desktop cube. It doesn't activate at all. >_<

---

### Post by jtraub on 2007-06-24
> **standardissue said:**
> I had the same problem, and that fixed it! Everything works now but the desktop cube. It doesn't activate at all. >_<

Other effects are visible?

---

### Post by c3007223 on 2007-06-24
Hi,

I just installed compiz-fusion, and everything seems to work ok. I have 2 slight problems though. The blur effects don't seem to work. I've checked the enable boxes, mucked around with the settings, but nothing changes. There seems to be no effect at all. Is this the case for other people? - I've searched these forums and opencompositing.org and found nothing.

The second problem is that when I have the wobble plugin enabled, there is a faint chirping noise that comes from my laptop. has anyone else noticed this? This is the only occasion that I have observed this noise before. It even happens when my speakers are turned off. 

I'm relatively new to this forum stuff, so if I've posted this in the wrong spot just let me know.

---

### Post by standardissue on 2007-06-24
> **jtraub said:**
> Other effects are visible?

Indeed, everything else I've tested works beautifully. I'll continue to fiddle with it and repost if I figure out the issue.

---

### Post by Salazar420 on 2007-06-24
I thank you, as many others have already, for a nice, easy to execute tutorial. I've completed it effortlessly with copy&paste, and a little knowledge of how to edit the repositories. Again, congrats on the newbie-friendly tutorial.

---

### Post by CyberAngel on 2007-06-24
> **jtraub said:**
> ```

mikv@hawk:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

```

Any ideas?

Same problem using an Ati X1300 on a friend`s of mine pc. I have enabled the ATI restricted drivers from the restricted drivers manager on gnome.

Am I need to edit something on the xorg.conf file?

---

### Post by jtraub on 2007-06-24
> **CyberAngel said:**
> Am I need to edit something on the xorg.conf file?
You should install XGL first.

[http://ubuntuforums.org/showthread.php?t=482773](http://ubuntuforums.org/showthread.php?t=482773)

---

### Post by jtraub on 2007-06-24
This happens because you try to start Fusion in session X.Org, not XGL

---

### Post by Sokraates on 2007-06-24
Nice guide, but two questions remain:

1) How do I stop Compiz, once it's running? Beryl had that nifty taskbar-applet.

2) How do I bind certain actions to a corner?

Also has anyone noticed problems with Firefox, when Compiz Fusion is running? I surfed this thread and clicking on the link to the next page would only update the navigation bar, but not the page itself. A refresh helped.

Without Compiz, I had no such problems.

---

### Post by Koji-Murasame on 2007-06-24
> **Sokraates said:**
> Nice guide, but two questions remain:

1) How do I stop Compiz, once it's running? Beryl had that nifty taskbar-applet.

2) How do I bind certain actions to a corner?

Also has anyone noticed problems with Firefox, when Compiz Fusion is running? I surfed this thread and clicking on the link to the next page would only update the navigation bar, but not the page itself. A refresh helped.

Without Compiz, I had no such problems.

I was also wondering about switching back to another window manager. While Firefox does occasionally freeze up on me I thought that was a Firefox issue and not a Compiz problem. I don't think there has been any implementation for changing the scale or expo activation corners or the amount of time it takes to activate them. I have problems getting video to play correctly while I'm running Compiz Fusion. Also I was wondering how the window grouping/tab thing worked. I fiddled with the commands and can't figure it out.

---

### Post by CyberAngel on 2007-06-24
> **jtraub said:**
> You should install XGL first.

[http://ubuntuforums.org/showthread.php?t=482773](http://ubuntuforums.org/showthread.php?t=482773)

That was the problem :)
Thank you.

---

### Post by gkiller on 2007-06-24
> **crimesaucer said:**
> I also fixed the transparent video like this: ccsm-->--General-->--Opacity Settings-->--Window Opacities-->-- then edit the string and take "Unkown" off of the list.
If you want to fix the transparency in videos and general fullscreen windows (eg. image viewer), but keep them in other "unknown" entities (for me its Opera menus for example), you could add this to the opacity string. I tested it with all video players I know (vlc, mplayer, totem-gstreamer, gxine, xine):
> ((type=Unknown | Menu | PopupMenu | DropdownMenu | Tooltip | Notification | Combo | Dnd | name=sun-awt-X11-XWindowPeer) | (type=Normal & override_redirect=1)) & !(name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer **| state=fullscreen | name=^x11$ | name=^xv$ | name=^xine Video Window$**)


> **Sokraates said:**
> 1) How do I stop Compiz, once it's running? Beryl had that nifty taskbar-applet.Hit Alt-F2 (or open a terminal) and type: ```
metacity --replace
```

> 2) How do I bind certain actions to a corner?Apparently, there is no place to do that generally. Some plugins have that option in their own key-binding options. But since this was possible in Beryl I think that we will see this functionality soon in Fusion also.

---

### Post by crimesaucer on 2007-06-24
> **gkiller said:**
> If you want to fix the transparency in videos and general fullscreen windows (eg. image viewer), but keep them in other "unknown" entities (for me its Opera menus for example), you could add this to the opacity string. I tested it with all video players I know (vlc, mplayer, totem-gstreamer, gxine, xine):
.

Thanks, I'll keep that in mind...all though "unknown" seemed to only affect my Xine-ui and no other apps of mine.

---

### Post by 71CH on 2007-06-24
Hi
Do I need to uninstall beryl first or does it not matter?

---

### Post by smartboyathome on 2007-06-24
Beryl doesn't matter, but you DO need to uninstall compiz first. Oh, and switch back to compiz before starting fusion, as you can get nasty bugs when trying to start straight from Beryl.

---

### Post by martynp on 2007-06-24
Hi All,

Hate to say it but I am new to Ubuntu so still learning.......

When I installed Beryl I activated the NVIDIA drivers and was getting the dreaded 'Black Windows' when more than one window or menu was open. I searched this forum and found a fix which told me to set 'rendering path' to 'texture from pixmap' and 'rendering platform' to 'Force AIGLX'. This I did and Beryl works just fine on me Sony Vaio.

I installed Compiz Fusion yesterday and have the same problem...... black windows (i.e. a window frame but information blacked out inside it) if I slightly resize the window it returns to normal, but any new window or menu opened then will be black. In other words..... only 1 window can be open and has to be slightly adjusted to see the contents. This is the same problem I had when first installing Beryl..... all other aspects of Fusion are working for me.

Anyone know how to fix the BLACK WINDOWS OF HELL :evil: from Fusion?

Many, many thanks in advance

---

### Post by 71CH on 2007-06-24
> **smartboyathome said:**
> Beryl doesn't matter, but you DO need to uninstall compiz first. Oh, and switch back to compiz before starting fusion, as you can get nasty bugs when trying to start straight from Beryl.

What do you mean by switching back to compiz before starting fusion?  I thought I was supposed to uninstall compiz?

---

### Post by gkiller on 2007-06-24
martynp (black Nvidia bug):

You can try the tips in this thread, maybe some of them help:
[Opencompositing.org Forums]("http://forums.opencompositing.org/viewtopic.php?f=40&t=522&st=0&sk=t&sd=a&hilit=black+window")

---

### Post by gkiller on 2007-06-24
> **71CH said:**
> What do you mean by switching back to compiz before starting fusion?  I thought I was supposed to uninstall compiz?
I think what he meant is to select "Metacity" in the Beryl Manager Icon under Window Managers, then quit Beryl Manager, then uninstall compiz etc.

---

### Post by sanford42 on 2007-06-24
OK, someone hinted at this a bit earlier, but I didn't see a reply, and I'm having a similar problem. 

I followed the tutorial to the letter, and everything installed perfectly.  I have the wobbly windows, I have my theme, the transparency works great, zoom works great... everything so far is awesome. 

But (there's always a "but" in these threads, eh?)... Cube no worky.  It's enabled in the CompizConfig Settings Manager, but I still just have my standard four desktops -- can't rotate the cube with the Ctrl-Alt-Mouse or using Ctrl-Alt-<Arrow Key> commands. 

Any suggestions?

---

### Post by llamakc on 2007-06-24
> **sanford42 said:**
> OK, someone hinted at this a bit earlier, but I didn't see a reply, and I'm having a similar problem. 

I followed the tutorial to the letter, and everything installed perfectly.  I have the wobbly windows, I have my theme, the transparency works great, zoom works great... everything so far is awesome. 

But (there's always a "but" in these threads, eh?)... Cube no worky.  It's enabled in the CompizConfig Settings Manager, but I still just have my standard four desktops -- can't rotate the cube with the Ctrl-Alt-Mouse or using Ctrl-Alt-<Arrow Key> commands. 

Any suggestions?

Run ccsm and enable Viewport Mouse Switch plugin. Mine didn't work at first either. I ended up logging out of Gnome due to frustration, and logged back in to find the cube working.

---

### Post by sanford42 on 2007-06-24
well, gave that a try... no dice. 
saved it, logged out and back into GNOME... still no dice. 

i know it's probably just some minute detail that I'm overlooking, and that's what frustrates me.

---

### Post by sanford42 on 2007-06-24
And I answered my own question!

need to start gconf-editor, 
select /apps/compiz/general/screen0/options/ and change the value of hsize from 1 to 4.

works like a charm :D

---

### Post by gkiller on 2007-06-24
> **sanford42 said:**
> And I answered my own question!

need to start gconf-editor, 
select /apps/compiz/general/screen0/options/ and change the value of hsize from 1 to 4.

works like a charm :D
For the future: I think you can change that also from ccsm. Go to General > Desktop Settings. You can change the horizontal and vertical size the. Desktop Size should remain at 1 for single monitor mode.

---

### Post by sanford42 on 2007-06-24
tried that too, it didn't work. 

just when i was about to give up and go back to the default Ubuntu "Desktop Effects", i stumbled across that tidbit of info. 

thought i'd share

---

### Post by ivesjd on 2007-06-24
> **gkiller said:**
> For the future: I think you can change that also from ccsm. Go to General > Desktop Settings. You can change the horizontal and vertical size the. Desktop Size should remain at 1 for single monitor mode.

Actually, what I did, is set it to two desktops, and then a Horizontal size of four. So I have two desktops with a cube on each :)

---

### Post by ivesjd on 2007-06-24
> **isaacj87 said:**
> Hello, My problem isn't the installation...I've got it fully installed...but how do I get Compiz Fusion to start when I boot up? I tried adding 'compiz --replace' to the sessions but when I do it gives me a black screen. :(

And has anyone figured this out? This is my problems as well. I also tried ```
 compiz --replace -c emerald &
```
and also just added ```
 emerald --replace
``` (with the first one)

---

### Post by walkerk on 2007-06-24
> **ivesjd said:**
> And has anyone figured this out? This is my problems as well. I also tried ```
 compiz --replace -c emerald &
```
and also just added ```
 emerald --replace
``` (with the first one)

i was having problems running compiz fusion at boot when i first installed it (just froze for minutes once i loggeed in)... what helped me was to uninstall everything having to do with compiz and beryl.. then made sure i had a recent version of emerald.. 0.3.0-svn. rebooted.. installed compiz fusion. now i added compiz fusion to my System > Preferences > Sessions as '  compiz --replace -c emerald  '

---

### Post by ivesjd on 2007-06-24
How did you get the latest version of emerald?

---

### Post by Kegir on 2007-06-24
Where's the 64bit lov'n?

---

### Post by walkerk on 2007-06-24
you should be able to get a new version of emeralld (0.3.0+) in the feisty rep...

try un-installing emerald.. reboot, then re-install.. (ensure its a new version.) i haven't done this recently so i do not remember.. let me know it it doesn't work and i'll dig up an emerald svn..

---

### Post by ivesjd on 2007-06-24
I removed it and could only install version 2.1, I was told that version 3 would fix my problems, but I cant figure out where to get it from. Its not in synaptic.


***edit 
I got it from Treino's blog. (Same source that this how-to points to.) 


I feel kinda dumb now....
***/edit

---

### Post by cwood06 on 2007-06-24
For anyone just getting one desktop and cant make the cube...

go to system > prefrences > compizconfig then click on the backend config on the left hand side of the menu and use the gconf one.

This worked for my nvida system, this guide worked like a charm for my ati/xgl system

Thanks ! :KS

---

### Post by feest on 2007-06-24
when i try to get compiz --replace i get this and it crashes to metacity? how do i solve this:


```
sven@sven-desktop:~$ compiz --replace
Adding plugin vpswitch (vpswitch)
Adding plugin ring (ring)
Adding plugin resizeinfo (resizeinfo)
Adding plugin fakeargb (fakeargb)
Adding plugin video (video)
Adding plugin fs (fs)
Adding plugin wall (wall)
Adding plugin trailfocus (trailfocus)
Adding plugin scale (scale)
Adding plugin mblur (mblur)
Adding plugin scaleaddon (scaleaddon)
Adding plugin annotate (annotate)
Adding plugin snow (snow)
Adding plugin tile (tile)
Adding plugin cube (cube)
Adding plugin addhelper (addhelper)
Adding plugin move (move)
Adding plugin regex (regex)
Adding plugin water (water)
Adding plugin firepaint (firepaint)
Adding plugin expo (expo)
Adding plugin extrawm (extrawm)
Adding plugin glib (glib)
Adding plugin splash (splash)
Adding plugin dbus (dbus)
Adding plugin neg (neg)
Adding plugin svg (svg)
Adding plugin png (png)
Adding plugin animation (animation)
Adding plugin fade (fade)
Adding plugin crashhandler (crashhandler)
Adding core settings (General Options)
Adding plugin zoom (zoom)
Adding plugin inotify (inotify)
Adding plugin plane (plane)
Adding plugin resize (resize)
Adding plugin cubereflex (cubereflex)
Adding plugin place (place)
Adding plugin clone (clone)
Adding plugin opacify (opacify)
Adding plugin rotate (rotate)
Adding plugin minimize (minimize)
Adding plugin text (text)
Adding plugin thumbnail (thumbnail)
Adding plugin imgjpeg (imgjpeg)
Adding plugin wobbly (wobbly)
Adding plugin blur (blur)
Adding plugin decoration (decoration)
Adding plugin group (group)
Adding plugin showdesktop (showdesktop)
Adding plugin winrules (winrules)
Adding plugin screenshot (screenshot)
Adding plugin reflex (reflex)
Adding plugin snap (snap)
Adding plugin fadedesktop (fadedesktop)
Adding plugin bench (bench)
Adding plugin switcher (switcher)
Adding plugin put (put)
Backend     : ini
Integration : true
Profile     : default
Initializing core options...done
Windowmanager waarschuwing: "" in de configuratiedatabase is geen geldige waarde voor toetsbinding "toggle_shaded"
Windowmanager waarschuwing: Scherm 0 op display ":0.0" heeft al een windowmanager; probeer de optie: --replace te gebruiken om de huidige windowmanager te vervangen.
Can't run metacity 
sven@sven-desktop:~$ 

```

---

### Post by Vorian on 2007-06-24
> **feest said:**
> when i try to get compiz --replace i get this and it crashes to metacity? how do i solve this:

First thing, use alt+F2 to launch your application.  If you have beryl installed, then run
>  compiz --replace -c emerald &

---

### Post by Zero Prime on 2007-06-24
I thought I would point out something interesting.  I installed CF a couple days ago and could not get it to run.  Eventually I gave up.  This morning I saw that I had some updates.  I checked them and saw one for Beryl.  I thought this was odd since Beryl wasn't being supported anymore.  I installed all the updates.  After a reboot I found that Beryl had bit the dust on me.  Just for giggles I tried to run Compiz again and low and behold it worked.  Rather nice to, but I can't get the window transparencies to cut off.

---

### Post by XAsmodeanX on 2007-06-24
Any plans for a 64 bit version?  I'm getting broken dependencies when installing.

xasmodeanx@archdemon:~$ sudo apt-get install compiz compiz-kde
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz: Depends: compiz-decorator but it is not installable
E: Broken packages
xasmodeanx@archdemon:~$

---

### Post by precinto on 2007-06-24
> **crimesaucer said:**
> I just checked, and YES, my sound works but my video does not.

It seems the update solved it. Now I can use xv with mplayer and fullscreen without problems. 

The transparency issue was fixed by deleting the "Unknown" entry in CCSM-General Options-Opacity Settings.

---

### Post by jimmygoon on 2007-06-24
This is still confusing. Is Compiz to be fazed into Compiz Fusion? If so that needs to be more clear. As of now I'm left wondering why Beryl was discontinued and why Compiz is still "Active" if its going to be superseded by this new project/product. Also, a notice on compiz.org like the one on beryl-project.org would be nice.

---

### Post by Vorian on 2007-06-24
The Compiz site is down, but the news is on the front page of beryl [http://www.beryl-project.org/](http://www.beryl-project.org/)

as for the name...
[http://forum.compiz.org/viewtopic.php?t=1313](http://forum.compiz.org/viewtopic.php?t=1313)

---

### Post by anandanbu on 2007-06-24
Thank you very much for a clean and a neat guide for installing.

---

### Post by standardissue on 2007-06-24
> **llamakc said:**
> Run ccsm and enable Viewport Mouse Switch plugin. Mine didn't work at first either. I ended up logging out of Gnome due to frustration, and logged back in to find the cube working.

That did it for me. Cheers. :0)

---

### Post by jimmygoon on 2007-06-24
Grr. The fusion combined the best and the worst of beryl and compiz.

Three things that NEED to happen:

1. Integration with the gtk-window-decorator and some type of compiz-fusion-decorator

2. COMPIZ-MANAGER! Seriously, beryl wins consistently here. I need an EASY way to switch compiz on and off. I installed something from the repositories, but there were no executables in the file... I want to be able to switch windows decorators and compiz/beryl/metacity, etc... This is something beryl had out-of-box. Compiz needs this.

3. GTK+! Seriously, a composited GTK would be OUT of this WORLD. It would be amazing to see the window-titlebar and the menus/icons/buttons blended together like in Vista and in some neat ole Metacity+GTK themes that are already available.

Good work on getting these two combined, but these three (okay, maybe just the first two) really need to fall in place before wide acceptance and easy of use will come together.

Thanks for the efforts of both teams!

edit: So, I figured out how to launch the tray icon for compiz-manager, but sadly it didn't load the compiz settings properly, had its own configuration(s)/backend and it was over all not connected with the actual compiz preferences area. seriously, clone the beryl-manager. QUICKLY! Thanks again.

---

### Post by iceportal on 2007-06-25
Followed the directions explicitly...

Didn't work at all.

O.o?

---

### Post by crimesaucer on 2007-06-25
> **71CH said:**
> Hi
Do I need to uninstall beryl first or does it not matter?

The short answer is that it helps.

I was running Beryl when I first installed Compiz fusion. It installed perfectly and I didn't even lose my Emerald windows. I started it with:

```
compiz --replace
```

Then, when trying to configure some of the "plug-in settings" and the hot key bindings that run the plug-ins (like super key + E for reflection), I had many problems with them not working...the cube caps...the reflection..and all sorts of other things.

Then I opened up my Xfce menu and clicked my Beryl Settings Manager just to see what it said. I noticed it still said that I was using Beryl as the window manager.

So I clicked the xfwm4 setting to use my default Window Manager which is "xfwm4" for xubuntu.

Then I used that same compiz --replace command and also the emerald -- replace command and everything worked perfectly.

Then I removed Beryl since Compiz feels better.


-EDIT for xubuntu uses: 

the command compiz --replace won't work if you have compositing turned on in your xfwm4 for xfce4.

---

### Post by studiesrule on 2007-06-25
> **jtraub said:**
> 
But last step of this guide ends with following errors
```

mikv@hawk:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

```

Any ideas?
Check this out:
[Not ATI]("http://forums.opencompositing.org/viewtopic.php?f=12&t=878#p6240") 
[ATI]("http://forums.opencompositing.org/viewtopic.php?f=12&t=878#p6454") 

If it works, then statically link the libGL.1.2.so to libGL.1.so and libGL.so :
```

sudo ln -sf /path/to/libGL.1.2.so /usr/lib/libGL.1.so
sudo ln -sf /path/to/libGL.1.2.so /usr/lib/libGL.so

```

CAUTION: remember that order, if you reverse it, you screw your mesa libGL (because of the -f(orce) flag, which is needed to override a existing file. In any case of any doubt, man it.

I hope that helps.

---

### Post by feest on 2007-06-25
okay it works and i think it's totally awsome however i've got some problems with my dual screen setting, see for yourself in attachment... it shows 8 sides on 2 cubes where only 4 sides can be used, beryl had something like dual screen support, is this also "fused in" into compiz fusion? or is there another way to solve this annoying problem?

thx in advance, 
     Sven van de Scheur

---

### Post by tpg on 2007-06-25
I'm using a farily clean install of Kubuntu, nVidia graphics card with drivers (working properly). Neither compiz nor beryl have been installed. 
After following the instructions, I don't get any window borders. I've tried compiz --replace and compiz --replace -c emerald, but neither works. I have tried running sudo apt-get install emerald emerald-themes as well, but that doesn't seem to help.
Anybody have any ideas? Thanks.

---

### Post by thatsPipe on 2007-06-25
I've got dual monitors also and am getting the same sort of thing with 2 desktop cubes. The way Beryl handled multi monitors was great and it would be nice to have the same. Beryl had was a check-box somewhere to indicate that you want a single cube across multiple monitors. Hopefully this feature will be included soon.

> **feest said:**
> okay it works and i think it's totally awsome however i've got some problems with my dual screen setting, see for yourself in attachment... it shows 8 sides on 2 cubes where only 4 sides can be used, beryl had something like dual screen support, is this also "fused in" into compiz fusion? or is there another way to solve this annoying problem?

thx in advance, 
     Sven van de Scheur

EDIT: Something I noticed with the behavior of the Application Switcher plugin but not too sure if its because of my dual monitors. Anyways, when alt-tabbing, it skips every other window. So if I have an odd number open, I can eventually get to all of them but when there is an even number open, I can only alt-tab to half of them and it doesn't matter what desktop they are on. I'm not sure if this is a general problem with the plugin or its just happening because of my dual monitors.

---

### Post by ashwin_cse on 2007-06-25
These efects are nothing new. I was using them during edgy eft period in beryl . Just the name has changed from beryl to compiz fusion. After seeing this video, I feel compiz has been stealing some of the good ideas from beryl & branding them as compiz own idea. I know compiz & beryl have agreed to merge. But shouldn't they be renamed in a more neutral way?

---

### Post by ivesjd on 2007-06-25
> **ashwin_cse said:**
> These efects are nothing new. I was using them during edgy eft period in beryl . Just the name has changed from beryl to compiz fusion. After seeing this video, I feel compiz has been stealing some of the good ideas from beryl & branding them as compiz own idea. I know compiz & beryl have agreed to merge. But shouldn't they be renamed in a more neutral way?

I have to agree with you. I dont think it should be name Compiz, maybe bepiz, or comryl. Although it is nice to have all of the effects included. And most of them working out-of-the-box.

---

### Post by euthyfro on 2007-06-25
It seems i've run into the worst of all possible worlds w/my compiz fusion attempts.  Not only have all the title bars disappeared, everything opens in the upper left corner covering all the menus, the bottom taskbar remains empty regardless of what programs i have open, none of the windows i open can be moved (even when holding alt down) & to beat all: alt-f2 does nothing.
Wait it gets better...
So i said "screw this, desktop effects aren't that important 2 me", removed every compiz package in synaptic, restarted & all the above crap is still happening as if i  had never removed compiz.
There's my living nightmare, i know y'all are up to it. thanx in advance.  

amd duo core 4200
nforce-4 sli board
2.5 gb ram
geforce 7300le video card

---

### Post by gkiller on 2007-06-25
> **euthyfro said:**
> It seems i've run into the worst of all possible worlds w/my compiz fusion attempts.  Not only have all the title bars disappeared, everything opens in the upper left corner covering all the menus, the bottom taskbar remains empty regardless of what programs i have open, none of the windows i open can be moved (even when holding alt down) & to beat all: alt-f2 does nothing.
Wait it gets better...
So i said "screw this, desktop effects aren't that important 2 me", removed every compiz package in synaptic, restarted & all the above crap is still happening as if i  had never removed compiz.
There's my living nightmare, i know y'all are up to it. thanx in advance.  

amd duo core 4200
nforce-4 sli board
2.5 gb ram
geforce 7300le video card
You probably didn't start metacity after removing compiz. Just somehow run "metacity --replace" after logging in and everything should be normal. Or put it in the Sessions Autostart.

---

### Post by euthyfro on 2007-06-25
thought it'd be something simple i was just over looking. that got me back
but i got 
 "Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
after doing metacity --replace

---

### Post by de4th on 2007-06-25
I Just enabled it and it's ******* great!
Big thanks for this guide!

@euthyfro: Try to execute ccsm, go to "Profile & Backend" and in backend select flat-file configuration.
Press Alt + F2 and try to execute replace again. Hope this solve your problem.

---

### Post by ivesjd on 2007-06-25
When I add either "compiz --replace and in another emerald --replace &" or "comiz --replace -c emerald &" to the start-up menu. It boots up, lets me log in, then I get a black screen with my cursor. I can sometimes restart X and everything is fine. Usually when I restart X though, I get a problem with the top and bottom panels. I can boot into standard metacity and then run the command "comiz --replace -c emerald &" and it switches to compiz just fine. It is quite frustrating.

---

### Post by greg.hagen on 2007-06-25
This guide did some really unhappy things to my amd64 xgl ati machine. A lot of the amd64 packages aren't available. Upon reinstalling the old compiz 0.5, some of the plugins don't work properly (including desktop zoom, alt-tab, cube.)

Could you add a big warning for 64-bit Ubuntu uses please?

---

### Post by the8thstar on 2007-06-25
I typed this:

> root@the8thstar-laptop:/home/the8thstar# compiz --replace
Fatal: Compiz can't be ran using VESA or VGA divers.

I'm using an Intel 945M chipset so why is compiz acting like a crybaby? Is something wrong with my xorgconf file?

---

### Post by el_itur on 2007-06-25
Maybe I misunderstood something. But by now, compiz fusion is only beryl but with another fancy name.
The whole thing behind the merge was that compiz was for the core, beryl (or whatever its name where), would be for all the fancy plugins.
So all that I'm getting with this guide is beryl with a fancy name. 

So what about me that I'm being using copiz and I'm not want to get other thing that compiz but just want some of the compiz fusion plugins?

Please, I'm not tring to flame on anything. I'm just asking for a doubt I have.

---

### Post by AriciU on 2007-06-25
Doesn't work for me at all. Reinstalled emerald too...

Lame standard window borders + no effect whatsoever.... wobbly windows, cube, rotating cube, etc etc

It's like it hasn't loaded at all.

I've set it to autostart in Sessions and rebooted (compiz --replace and emerald --replace &).

I'm having no problems running Beryl. Dunno wtf can be wrong with this.

I'm getting this message when running "compiz --replace" in the console btw:

> Adding core settings (General Options)
Adding plugin annotate (annotate)
Adding plugin blur (blur)
Adding plugin clone (clone)
Adding plugin cube (cube)
Adding plugin dbus (dbus)
Adding plugin decoration (decoration)
Adding plugin fade (fade)
Adding plugin fs (fs)
Adding plugin glib (glib)
Adding plugin inotify (inotify)
Adding plugin minimize (minimize)
Adding plugin move (move)
Adding plugin place (place)
Adding plugin plane (plane)
Adding plugin png (png)
Adding plugin regex (regex)
Adding plugin resize (resize)
Adding plugin rotate (rotate)
Adding plugin scale (scale)
Adding plugin screenshot (screenshot)
Adding plugin svg (svg)
Adding plugin switcher (switcher)
Adding plugin video (video)
Adding plugin water (water)
Adding plugin wobbly (wobbly)
Adding plugin zoom (zoom)
Adding plugin animation (animation)
Adding plugin expo (expo)
Adding plugin imgjpeg (imgjpeg)
Adding plugin neg (neg)
Adding plugin opacify (opacify)
Adding plugin put (put)
Adding plugin resizeinfo (resizeinfo)
Adding plugin ring (ring)
Adding plugin scaleaddon (scaleaddon)
Adding plugin snap (snap)
Adding plugin text (text)
Adding plugin thumbnail (thumbnail)
Adding plugin vpswitch (vpswitch)
Adding plugin wall (wall)
Adding plugin winrules (winrules)
Adding plugin addhelper (addhelper)
Adding plugin bench (bench)
Adding plugin crashhandler (crashhandler)
Adding plugin cubereflex (cubereflex)
Adding plugin extrawm (extrawm)
Adding plugin fadedesktop (fadedesktop)
Adding plugin firepaint (firepaint)
Adding plugin group (group)
Adding plugin mblur (mblur)
Adding plugin reflex (reflex)
Adding plugin showdesktop (showdesktop)
Adding plugin splash (splash)
Adding plugin trailfocus (trailfocus)
Adding plugin fakeargb (fakeargb)
Adding plugin snow (snow)
Adding plugin tile (tile)
Backend     : ini
Integration : true
Profile     : default
Initializing core options...done
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device


Switched back to Beryl and found out that my window borders dissapeared when using Emerald. They used to work before installing fusion and updating emerald with the package from these new repo's.

Now i have to use the GTK window manager with Beryl. I should've just stayed put ffs :mad:

---

### Post by Skavenger on 2007-06-25
hi, i have a question
what's the diference between compiz, compiz git and compiz fusion?

---

### Post by Sokraates on 2007-06-26
> **Skavenger said:**
> hi, i have a question
what's the diference between compiz, compiz git and compiz fusion?

Compiz is the core application with only the most basic eye candy. Think of it as Compiz Fusion's kernel.

Compiz Fusion is the project formed by the merger of Compiz Extras and Beryl. Compiz Fusion provides all the advanced effects and eye candy. It is built on Compiz and requires Compiz to run.

Compiz git is the source-tree, where development happens. AFAIK only Compiz Fusion uses git. Often used alternatives to git are svn or cvs. The builds we use today are biult from the git-tree, since there is no official release of Compiz Fusion yet.

---

### Post by AriciU on 2007-06-26
> **ivesjd said:**
> When I add either "compiz --replace and in another emerald --replace &" or "comiz --replace -c emerald &" to the start-up menu. It boots up, lets me log in, then I get a black screen with my cursor. I can sometimes restart X and everything is fine. Usually when I restart X though, I get a problem with the top and bottom panels. I can boot into standard metacity and then run the command "comiz --replace -c emerald &" and it switches to compiz just fine. It is quite frustrating.

Open the Konsole -> gconf-editor -> desktop/gnome/applications/window_manager

Set "current" and "default" to /usr/bin/metacity

System / Preferences / Sessions / add "compiz --replace -c emerald &"

ctrl+alt+backspace or /etc/init.d/gdm restart and everything should be loading fine.

Worked for me anyway.

---

### Post by Robert Doucette on 2007-06-26
Hello,

I followed this tutorial and everything seemed to install fine, however compiz doesn't seem to want to start.  this is the out put of compiz --replace

robert@ubuntu:~$ compiz --replace
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

I have beryl installed and running on my machine (a Dell Inspiron 5100 with an ATI card) and it has never given me problems.  When I try to switch to compiz I lose the borders on my windows and I can't change between windows.  The libdecorations package is up todate (because I saw early in this post that it could be a problem) and I am not too sure what to do.  If this could help here is the output of glxinfo |grep rendering

robert@ubuntu:~$ glxinfo |grep rendering
direct rendering: Yes

I am relatively new to Ubuntu and Linux so any help would be greatly appreciated.  I love Ubuntu and think the guys at Canonical have done a wonderful job.

---

### Post by JGT on 2007-06-26
Hi

I'm new to Linux and have been experimenting happily with my new "dual boot" set-up for a few weeks.

Can you please tell me if it's worth my while installing Compix Fusion. I don't have a dedicated graphics card; instead I have a cheapo Dell 3100 with an Intel Pentium 4 630 (3GHz) processor and integrated Intel Graphics Media Accelerator 900, with 512 RAM.

Dell only gave me two PCI slots (no spares), so a dedicated graphics card is out of the question at the moment.

The default  7.04 "Desktop Effects" Cube and wobbly windows work fine. 

Can Compix Fusion run on my set up, or do I need a graphics card?

Many thanks

John

---

### Post by pcfreak on 2007-06-26
I did everything stated in the guide, and when I try to run 'compiz --replace', everything on the desktop disappears, the bar at the top over the program I run (wich was firefox, since I was reading the thread) dissipears, then after a short while compiz fusion freezes and throws me out to the login screen, and I have to log in again, then the standard gnome desktop appears, if I try again, the same happens again.

I am using Ubuntu 7.04 Feisty, I even tried installing emerald, emerald-themes and xserver-xgl, even though it was staded for other problems... still does'nt work... Any idea how to solve this?

---

### Post by Imarri01 on 2007-06-26
my cude doesnt work, it seems like i only have 1 desktop, any ideas how to fix this?

---

### Post by HotShot on 2007-06-26
> **AriciU said:**
> Open the Konsole -> gconf-editor -> desktop/gnome/applications/window_manager

Set "current" and "default" to /usr/bin/metacity


GREAT! :D

This solve my problem that the session start of ```
compiz --replace
``` didnt work without delay. Now i got compiz fusion at startup! Cool!

HAPPY HS
EDIT: This delay is the bug reported [here]("http://forums.opencompositing.org/viewtopic.php?f=48&t=729"). Can anyone confirm?

---

### Post by AriciU on 2007-06-26
> **pcfreak said:**
> I did everything stated in the guide, and when I try to run 'compiz --replace', everything on the desktop disappears, the bar at the top over the program I run (wich was firefox, since I was reading the thread) dissipears, then after a short while compiz fusion freezes and throws me out to the login screen, and I have to log in again, then the standard gnome desktop appears, if I try again, the same happens again.

I am using Ubuntu 7.04 Feisty, I even tried installing emerald, emerald-themes and xserver-xgl, even though it was staded for other problems... still does'nt work... Any idea how to solve this?

Go to System / Administration / Synaptic packet manager and search for "libdecoration". You will find 2 entries, libdecoration and libdecoration-dev. Mark them both and click apply. It will update to version 0.5 if you don't have it already.

Fixed compiz for me and made it load fine. Let me know if it works...

---

### Post by 213374U on 2007-06-26
Searched the entire thread and couldn't find an answer to my question. To "Add Keys" simply copy and paste into terminal, correct? If so, after I do that, it adds one key. Then when I run 

```
sudo apt-get update
```

It gives me this

```

Get:1 http://us.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US           
Get:2 http://security.ubuntu.com feisty-security Release.gpg [191B]            
Ign http://security.ubuntu.com feisty-security/main Translation-en_US          
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US             
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US 
Get:3 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US       
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Hit http://us.archive.ubuntu.com feisty Release                      
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US      
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US    
Get:4 http://download.tuxfamily.org feisty Release.gpg [189B]                  
Ign http://download.tuxfamily.org feisty/eyecandy Translation-en_US            
Hit http://security.ubuntu.com feisty-security Release                         
Hit http://us.archive.ubuntu.com feisty-updates Release             
Get:5 http://download.tuxfamily.org feisty Release [10.5kB]                    
Hit http://security.ubuntu.com feisty-security/main Packages               
Hit http://us.archive.ubuntu.com feisty/main Packages                      
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Hit http://us.archive.ubuntu.com feisty/main Sources                       
Hit http://us.archive.ubuntu.com feisty/restricted Sources                 
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Ign http://download.tuxfamily.org feisty Release                      
Hit http://us.archive.ubuntu.com feisty/universe Packages             
Hit http://us.archive.ubuntu.com feisty/universe Sources
Hit http://us.archive.ubuntu.com feisty/multiverse Packages          
Hit http://us.archive.ubuntu.com feisty/multiverse Sources           
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages   
Hit http://security.ubuntu.com feisty-security/multiverse Sources    
Get:6 http://download.tuxfamily.org feisty/eyecandy Packages [14.3kB]
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Get:7 http://download.tuxfamily.org feisty/eyecandy Sources [37B]
Fetched 25.1kB in 1s (20.2kB/s)
Reading package lists... Done
[b]W: GPG error: http://download.tuxfamily.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems[/b]

```

Tried getting this running before and couldn't. I'm now on a fresh Ubuntu install (Feisty) and I still got this. Haven't proceeded any further because I think this is where the hang up is.

---

### Post by Vorian on 2007-06-26
you need the key

do this in a terminal
```
KEY=81836EBF; gpg --keyserver subkeys.pgp.net --recv $KEY && gpg --export --armor $KEY | sudo apt-key add -


```

and then

```
sudo apt-get update
```

---

### Post by 213374U on 2007-06-26
That's exactly what I did, and upon update, it gave me the error messages (missing key) listed in my last post.

---

### Post by BOBSONATOR on 2007-06-26
thanks for this great how-to

---

### Post by c.dric on 2007-06-27
> **213374U said:**
> That's exactly what I did, and upon update, it gave me the error messages (missing key) listed in my last post.

it happened to me a couple of times too ...

repeat those two commands once or twice until the error goes away (it worked for me)
```
KEY=81836EBF; gpg --keyserver subkeys.pgp.net --recv $KEY && gpg --export --armor $KEY | sudo apt-key add -
sudo apt-get update
```

---

### Post by KriZo on 2007-06-27
Hi i'm having a lot of problems now

krizo@krizo:~$ sudo apt-get install compiz # compiz-gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  compiz: Depends: compiz-decorator
  compiz-gnome: Depends: compiz-gtk (= 1:0.3.6-1ubuntu13) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


krizo@krizo:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  compiz-gnome
The following packages will be upgraded:
  compiz-gnome
1 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
1 not fully installed or removed.
Need to get 0B/165kB of archives.
After unpacking 1294kB of additional disk space will be used.
Do you want to continue [Y/n]? y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_DK"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
(Reading database ... 135410 files and directories currently installed.)
Preparing to replace compiz-gnome 1:0.3.6-1ubuntu13 (using .../compiz-gnome_1%3a0.5.1+git20070626~3v1ubuntu0_i386.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070626~3v1ubuntu0_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070626~3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


please help me i can't install any other applications now.

---

### Post by smartboyathome on 2007-06-27
remove the # from the line and try installing again.

---

### Post by KriZo on 2007-06-27
#136

didn't work

krizo@krizo:~$ sudo apt-get install compiz compiz-gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz is already the newest version.
The following packages will be upgraded:
  compiz-gnome
1 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
1 not fully installed or removed.
Need to get 0B/165kB of archives.
After unpacking 1294kB of additional disk space will be used.
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_DK"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
(Reading database ... 135410 files and directories currently installed.)
Preparing to replace compiz-gnome 1:0.3.6-1ubuntu13 (using .../compiz-gnome_1%3a0.5.1+git20070626~3v1ubuntu0_i386.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070626~3v1ubuntu0_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070626~3v1ubuntu0_i386.deb
W: Duplicate sources.list entry [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages (/var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_feisty_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by pvravi on 2007-06-27
Need some help, please.

Had beryl. Followed the guide, removed Beryl from Startup and compiz --replace gives this:

```
~$ compiz --replace
Adding core settings (General Options)
Adding plugin annotate (annotate)
Adding plugin blur (blur)
Adding plugin clone (clone)
Adding plugin cube (cube)
Adding plugin dbus (dbus)
Adding plugin decoration (decoration)
Adding plugin fade (fade)
Adding plugin fs (fs)
Adding plugin glib (glib)
Adding plugin inotify (inotify)
Adding plugin minimize (minimize)
Adding plugin move (move)
Adding plugin place (place)
Adding plugin plane (plane)
Adding plugin png (png)
Adding plugin regex (regex)
Adding plugin resize (resize)
Adding plugin rotate (rotate)
Adding plugin scale (scale)
Adding plugin screenshot (screenshot)
Adding plugin svg (svg)
Adding plugin switcher (switcher)
Adding plugin video (video)
Adding plugin water (water)
Adding plugin wobbly (wobbly)
Adding plugin zoom (zoom)
Adding plugin animation (animation)
Adding plugin expo (expo)
Adding plugin imgjpeg (imgjpeg)
Adding plugin neg (neg)
Adding plugin opacify (opacify)
Adding plugin put (put)
Adding plugin resizeinfo (resizeinfo)
Adding plugin ring (ring)
Adding plugin scaleaddon (scaleaddon)
Adding plugin snap (snap)
Adding plugin text (text)
Adding plugin thumbnail (thumbnail)
Adding plugin vpswitch (vpswitch)
Adding plugin wall (wall)
Adding plugin winrules (winrules)
Adding plugin addhelper (addhelper)
Adding plugin bench (bench)
Adding plugin crashhandler (crashhandler)
Adding plugin cubereflex (cubereflex)
Adding plugin extrawm (extrawm)
Adding plugin fadedesktop (fadedesktop)
Adding plugin firepaint (firepaint)
Adding plugin group (group)
Adding plugin mblur (mblur)
Adding plugin reflex (reflex)
Adding plugin showdesktop (showdesktop)
Adding plugin splash (splash)
Adding plugin trailfocus (trailfocus)
Adding plugin fakeargb (fakeargb)
Adding plugin snow (snow)
Adding plugin tile (tile)
Backend     : gconf
Integration : true
Profile     : default
Initializing core options...done
Initializing decoration options...done
Initializing minimize options...done
Initializing move options...done
Initializing place options...done
Initializing resize options...done
Initializing wobbly options...done
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/friction. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/spring_k. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Initializing zoom options...done
Initializing fade options...done
Initializing cube options...done
Initializing rotate options...done
Initializing scale options...done
Initializing switcher options...done

```

I see NO window decorations whatsoever - there are tool tips at those place, but  nothing visible. No cube either - I had it in beryl. Compizconfig-Backend-Gconf is selected. I haven't touched the default settings otherwise.

Help! Please!

thanks
pvravi

---

### Post by pvravi on 2007-06-27
Update: I selected GTK window decorator and metacity in beryl, and quit beryl. Then I issued the compiz --replace command. 

Still the same console output as above, but I do see the default human theme decorators. No Cube still. 

Still Need Help!

Thanks
pvravi

---

### Post by pvravi on 2007-06-27
OK. Cube worked by changing the gconf-editor hsize.

Now for the window decorations. How can I change 'em? Are there beryl-like themes I can get?

thanks
pvravi

---

### Post by smartboyathome on 2007-06-27
you should be able to use emerald to get themes for it.

---

### Post by dbbolton on 2007-06-27
> **jtraub said:**
> I have ATi X1900 XT and proprietary drivers installed on my machine (default from Feisty repositories)
```

mikv@hawk:~$ glxinfo | grep rendering
direct rendering: Yes
mikv@hawk:~$ glxinfo | grep texture_from_pixmap
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 

```
But last step of this guide ends with following errors
```

mikv@hawk:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

```

Any ideas?
i have a different card, but almost the same issue. did you ever figure this out?

---

### Post by the8thstar on 2007-06-27
I give up. Way too much hassle, problems, etc. This program sucks.

:mad:

---

### Post by got_nix on 2007-06-27
> **johntelthorst said:**
> I'm getting the same errors,  I have an ATI Radeon Xpress 200M

> **jtraub said:**
> I have ATi X1900 XT and proprietary drivers installed on my machine (default from Feisty repositories)
```

mikv@hawk:~$ glxinfo | grep rendering
direct rendering: Yes
mikv@hawk:~$ glxinfo | grep texture_from_pixmap
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 

```
But last step of this guide ends with following errors
```

mikv@hawk:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

```

Any ideas?


same issue. hre. ati x1300.. yet again ati gets left in the shadows? we had similar issues with beryl.. couldn't get beryl working as easy as the other cards could :(

---

### Post by PRGUY85 on 2007-06-27
Hey there:

I installed Compiz-Fusion and have it working wonderfully on my laptop.  Yet, it doesn't start automatically every time I boot up Ubuntu.  I have to do the following command every time on my terminal:

compiz --replace -c emerald &

I added the command to my startup list on Preferences---Sessions, yet it doesn't work.  I have to do it on terminal each time.

How do I make Compiz-Fusion work everytime I log on?

---

### Post by Innova on 2007-06-27
I am having problems getting fusion running.  I currently have Beryl .2 rc3 working, but I like having the latest and greatest:

```

wesley@mediacenter:~$ sudo apt-get -y remove compiz-core desktop-effects
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  compiz: Depends: compiz-core but it is not going to be installed
          Depends: compiz-decorator
  compiz-gnome: Depends: compiz-gtk (= 1:0.3.6-1ubuntu13) but it is not going to be installed
  compiz-plugins: Depends: compiz-core (= 1:0.3.6-1ubuntu13) but it is not going to be installed
  ubuntu-desktop: Depends: desktop-effects but it is not going to be installed
                  Recommends: gimp-print but it is not going to be installed
                  Recommends: totem-mozilla but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
wesley@mediacenter:~$ 

```

Then when I try sudo apt-get -f install:

```

wesley@mediacenter:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  compiz-gnome
The following packages will be upgraded:
  compiz-gnome
1 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.
1 not fully installed or removed.
Need to get 0B/165kB of archives.
After unpacking 1294kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 144505 files and directories currently installed.)
Preparing to replace compiz-gnome 1:0.3.6-1ubuntu13 (using .../compiz-gnome_1%3a0.5.1+git20070626~3v1ubuntu0_i386.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070626~3v1ubuntu0_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070626~3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
wesley@mediacenter:~$ 

```

I guess I'm not sure where to go from here...

Edit:  I just started up Synaptic and it said that I had two broken packages.  I clicked on edit->fix broken packages:

```

E: /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070626~3v1ubuntu0_i386.deb: trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins

```

---

### Post by kevinlang21 on 2007-06-27
I get no titlebars. I tried everything in this thread, but it still doesn't work. this is my error message:

```

kevin@computer:~$ compiz --replace -c emerald &
[1] 14627
kevin@computer:~$ Adding plugin splash (splash)
Adding plugin thumbnail (thumbnail)
Adding plugin opacify (opacify)
Adding plugin cubereflex (cubereflex)
Adding plugin video (video)
Adding plugin wobbly (wobbly)
Adding plugin neg (neg)
Adding plugin resizeinfo (resizeinfo)
Adding plugin glib (glib)
Adding plugin group (group)
Adding plugin png (png)
Adding plugin snow (snow)
Adding plugin reflex (reflex)
Adding plugin scaleaddon (scaleaddon)
Adding plugin screenshot (screenshot)
Adding plugin regex (regex)
Adding plugin zoom (zoom)
Adding plugin clone (clone)
Adding plugin extrawm (extrawm)
Adding plugin fakeargb (fakeargb)
Adding plugin imgjpeg (imgjpeg)
Adding plugin rotate (rotate)
Adding plugin bench (bench)
Adding plugin fade (fade)
Adding plugin fadedesktop (fadedesktop)
Adding plugin firepaint (firepaint)
Adding plugin dbus (dbus)
Adding plugin switcher (switcher)
Adding plugin blur (blur)
Adding plugin addhelper (addhelper)
Adding plugin trailfocus (trailfocus)
Adding plugin showdesktop (showdesktop)
Adding plugin move (move)
Adding plugin minimize (minimize)
Adding plugin water (water)
Adding plugin text (text)
Adding plugin fs (fs)
Adding plugin inotify (inotify)
Adding plugin put (put)
Adding plugin resize (resize)
Adding plugin decoration (decoration)
Adding plugin animation (animation)
Adding plugin svg (svg)
Adding plugin vpswitch (vpswitch)
Adding plugin plane (plane)
Adding plugin cube (cube)
Adding plugin expo (expo)
Adding plugin scale (scale)
Adding plugin crashhandler (crashhandler)
Adding plugin winrules (winrules)
Adding plugin place (place)
Adding plugin ring (ring)
Adding plugin annotate (annotate)
Adding plugin mblur (mblur)
Adding plugin wall (wall)
Adding plugin tile (tile)
Adding plugin snap (snap)
Adding core settings (General Options)
Backend     : ini
Integration : true
Profile     : default
Initializing core options...done
Initializing zoom options...done
Initializing move options...done
Initializing minimize options...done
Initializing resize options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
Initializing decoration options...done
Initializing place options...done
Initializing wobbly options...done
Initializing fade options...done
Initializing cube options...done
Initializing scale options...done
Initializing rotate options...done
Initializing switcher options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32

```

Thanks for your help

---

### Post by detyabozhye on 2007-06-28
> **the8thstar said:**
> I give up. Way too much hassle, problems, etc. This program sucks.

:mad:

Doesn't this make any sense?:

> **Vorian said:**
> ... Compiz Fuzion is [SIZE=3][COLOR=Red]**NOT for Beginners**[/COLOR][/SIZE].  It is in development now, and is not stable.
...
[COLOR=Red][SIZE=3]** Use at your own risk**[/SIZE][/COLOR] ...

---

### Post by detyabozhye on 2007-06-28
> **the8thstar said:**
> I typed this:

```
root@the8thstar-laptop:/home/the8thstar# compiz --replace
Fatal: Compiz can't be ran using VESA or VGA divers.
```

I'm using an Intel 945M chipset so why is compiz acting like a crybaby? Is something wrong with my xorgconf file?

You should run compiz as a regular user, not as root. And check which driver you are using in your xorg.conf file.

---

### Post by dexter on 2007-06-28
> **kevinlang21 said:**
> I get no titlebars. I tried everything in this thread, but it still doesn't work. this is my error message:

```

kevin@computer:~$ compiz --replace -c emerald &
[1] 14627
kevin@computer:~$ Adding plugin splash (splash)
Adding plugin thumbnail (thumbnail)
Adding plugin opacify (opacify)
Adding plugin cubereflex (cubereflex)
Adding plugin video (video)
Adding plugin wobbly (wobbly)
Adding plugin neg (neg)
Adding plugin resizeinfo (resizeinfo)
Adding plugin glib (glib)
Adding plugin group (group)
Adding plugin png (png)
Adding plugin snow (snow)
Adding plugin reflex (reflex)
Adding plugin scaleaddon (scaleaddon)
Adding plugin screenshot (screenshot)
Adding plugin regex (regex)
Adding plugin zoom (zoom)
Adding plugin clone (clone)
Adding plugin extrawm (extrawm)
Adding plugin fakeargb (fakeargb)
Adding plugin imgjpeg (imgjpeg)
Adding plugin rotate (rotate)
Adding plugin bench (bench)
Adding plugin fade (fade)
Adding plugin fadedesktop (fadedesktop)
Adding plugin firepaint (firepaint)
Adding plugin dbus (dbus)
Adding plugin switcher (switcher)
Adding plugin blur (blur)
Adding plugin addhelper (addhelper)
Adding plugin trailfocus (trailfocus)
Adding plugin showdesktop (showdesktop)
Adding plugin move (move)
Adding plugin minimize (minimize)
Adding plugin water (water)
Adding plugin text (text)
Adding plugin fs (fs)
Adding plugin inotify (inotify)
Adding plugin put (put)
Adding plugin resize (resize)
Adding plugin decoration (decoration)
Adding plugin animation (animation)
Adding plugin svg (svg)
Adding plugin vpswitch (vpswitch)
Adding plugin plane (plane)
Adding plugin cube (cube)
Adding plugin expo (expo)
Adding plugin scale (scale)
Adding plugin crashhandler (crashhandler)
Adding plugin winrules (winrules)
Adding plugin place (place)
Adding plugin ring (ring)
Adding plugin annotate (annotate)
Adding plugin mblur (mblur)
Adding plugin wall (wall)
Adding plugin tile (tile)
Adding plugin snap (snap)
Adding core settings (General Options)
Backend     : ini
Integration : true
Profile     : default
Initializing core options...done
Initializing zoom options...done
Initializing move options...done
Initializing minimize options...done
Initializing resize options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
Initializing decoration options...done
Initializing place options...done
Initializing wobbly options...done
Initializing fade options...done
Initializing cube options...done
Initializing scale options...done
Initializing rotate options...done
Initializing switcher options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32

```

Thanks for your help

Do you have an nvidia card and did you let nvidia-settings overwrite your xorg.conf ?

---

### Post by astralsin on 2007-06-28
```
root@odin:/var/www# apt-get -y install compiz compiz-gtk compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz-gtk: Depends: compiz-core (= 1:0.3.6-1ubuntu13) but 1:0.5.1+git20070627~3v1ubuntu0 is to be installed
E: Broken packages

```

anyone got a fix for this one?

---

### Post by wvengen on 2007-06-28
astralsin: I bet you're having a 64 bit system, for which most packages are unavailable yet unfortunately.
  $ uname -m
  x86_64

---

### Post by VDVsx on 2007-06-28
> **astralsin said:**
> ```
root@odin:/var/www# apt-get -y install compiz compiz-gtk compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz-gtk: Depends: compiz-core (= 1:0.3.6-1ubuntu13) but 1:0.5.1+git20070627~3v1ubuntu0 is to be installed
E: Broken packages

```

anyone got a fix for this one?

I have the same problem:( ...

---

### Post by Vorian on 2007-06-28
My mistake!  sorry :redface:

replace compiz-gtk with compiz-gnome

full code
```
sudo apt-get -y install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf
```

---

### Post by Kayne on 2007-06-28
Hm, it seems that today's update broke the "compatibility" with emerald, Compiz runs fine but it does only load the metacity title bars.

---

### Post by outphase on 2007-06-28
> **dexter said:**
> Do you have an nvidia card and did you let nvidia-settings overwrite your xorg.conf ?

This question helped me fix my similar problem of window decorations not working, Thanks!

---

### Post by VDVsx on 2007-06-28
> **Vorian said:**
> My mistake!  sorry :redface:

replace compiz-gtk with compiz-gnome

full code
```
sudo apt-get -y install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf
```

Tanks a lot, everything works fine now :p .

---

### Post by smithman89 on 2007-06-28
Okay, so everything works fine except one thing.  Once again, my titlebars disappeared.  The only difference between now and the previous time that this happened, is that the code that fixed it last time is still in the xorg file.  So, what do i do?
Edit:  I figured it out, all i had to do is turn on Window Decorations.  Thanks again for the guide, this thing is awesome!

---

### Post by beerorkid on 2007-06-28
for the dual monitor dual cube with bunches of sides problem I found this over at their forum:
CCSM &#8211;> general options &#8211;> display settings &#8211;> uncheck detect outputs (have not tested it myself yet)

Thanks for the howto.  The git stuff confuzzled me, good ole trevino and his uber repository lets me stay in my apt-get comfort zone.

---

### Post by gkiller on 2007-06-28
> **KriZo said:**
> Hi i'm having a lot of problems now

krizo@krizo:~$ sudo apt-get install compiz # compiz-gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  compiz: Depends: compiz-decorator
  compiz-gnome: Depends: compiz-gtk (= 1:0.3.6-1ubuntu13) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Did you follow the Howto exactly, ie. did you remove the old compiz and desktop-effects packages first before installing the new ones? If yes and it still doesn't work, try this:
Remove the Treviño repositories from your sources.list, then go into Synaptic and search for compiz by name. Mark everything that is related to compiz for removal. Do the same with everything related to beryl and emerald. After that click apply.
Then add the Trev. repos again and start from the top of the howto.

If this still doesn't work either your package management is messed up pretty bad or compiz is not installable at the moment for some reason. Try asking in the [Opencompositing.org forums' Ubuntu package topic]("http://forums.opencompositing.org/viewtopic.php?f=14&t=131")

BTW after you're done, you might want to install ubuntu-desktop again which will certainly get removed while you are doing all this.

> **PRGUY85 said:**
> Hey there:

I installed Compiz-Fusion and have it working wonderfully on my laptop.  Yet, it doesn't start automatically every time I boot up Ubuntu.  I have to do the following command every time on my terminal:

compiz --replace -c emerald &

I added the command to my startup list on Preferences---Sessions, yet it doesn't work.  I have to do it on terminal each time.

How do I make Compiz-Fusion work everytime I log on?
Try the following in Sessions autostart:
```
compiz --replace && sleep 2 && emerald --replace
```
I don't know why this would work and the other one not, but it's a try. That command starts compiz, then waits 2 seconds before starting emerald.

---

### Post by sab0403 on 2007-06-28
Hi.

When I get to the **Install compiz fusion** step, I get this message (sorry if it's not accurate, I'm translating from spanish):

```
compizconfig-settings-manager -- PACKAGE NOT FOUND
```

Any help? I already modified the sources.list... Everything else installed just fine. Entire code I entered when the error happened:

```
sudo apt-get -y install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf
```

EDIT: Just got it working, I did another update/upgrade and that did it. Continuing installation now...

---

### Post by astralsin on 2007-06-28
yep, changing to compiz-gnome worked, thanks :)

---

### Post by tetsura on 2007-06-28
thanks for the awesome how-to, everything worked perfectly, hasnt even crashed yet :S. wobble is a bit dodge but im sure itll improve soon :)

---

### Post by quaid on 2007-06-29
```
quaid@avion:~$ compiz --replace -c emerald &[1] 9178
quaid@avion:~$ grep: /proc//smaps: No existe el fichero ó directorio
Adding core settings (General Options)
Adding plugin annotate (annotate)
Adding plugin blur (blur)
Adding plugin clone (clone)
Adding plugin cube (cube)
Adding plugin dbus (dbus)
Adding plugin decoration (decoration)
Adding plugin fade (fade)
Adding plugin fs (fs)
Adding plugin glib (glib)
Adding plugin inotify (inotify)
Adding plugin minimize (minimize)
Adding plugin move (move)
Adding plugin place (place)
Adding plugin plane (plane)
Adding plugin png (png)
Adding plugin regex (regex)
Adding plugin resize (resize)
Adding plugin rotate (rotate)
Adding plugin scale (scale)
Adding plugin screenshot (screenshot)
Adding plugin svg (svg)
Adding plugin switcher (switcher)
Adding plugin video (video)
Adding plugin water (water)
Adding plugin wobbly (wobbly)
Adding plugin zoom (zoom)
Adding plugin animation (animation)
Adding plugin expo (expo)
Adding plugin imgjpeg (imgjpeg)
Adding plugin neg (neg)
Adding plugin opacify (opacify)
Adding plugin put (put)
Adding plugin resizeinfo (resizeinfo)
Adding plugin ring (ring)
Adding plugin scaleaddon (scaleaddon)
Adding plugin snap (snap)
Adding plugin text (text)
Adding plugin thumbnail (thumbnail)
Adding plugin vpswitch (vpswitch)
Adding plugin wall (wall)
Adding plugin winrules (winrules)
Adding plugin addhelper (addhelper)
Adding plugin bench (bench)
Adding plugin crashhandler (crashhandler)
Adding plugin cubereflex (cubereflex)
Adding plugin extrawm (extrawm)
Adding plugin fadedesktop (fadedesktop)
Adding plugin firepaint (firepaint)
Adding plugin group (group)
Adding plugin mblur (mblur)
Adding plugin reflex (reflex)
Adding plugin showdesktop (showdesktop)
Adding plugin splash (splash)
Adding plugin trailfocus (trailfocus)
Adding plugin fakeargb (fakeargb)
Adding plugin snow (snow)
Adding plugin tile (tile)
Backend     : ini
Integration : true
Profile     : default
Initializing core options...done
Initializing decoration options...done
/usr/bin/compiz: line 671:  9260 Segmentation Fail  (core dumped) $*

```

Any suggestion?

---

### Post by xtrm_redbull on 2007-06-29
First of all thanks Vorian for this great how to. I installed the compiz fusion today, and starting to play with it :p. Can anyone suggest to me an alternative key to windows key, I have an ibm r50e laptop with no windows key. Since beryl I used the shift key as super key, but now I want to try out the new plugin's in compiz fusion like the ring switcher but some of the key commands uses a combination of Shift+Alt+Super+Tab.

I hope someone with similar problem can enlighten me on this one. I'd like to know what do you guys use as an alternative to the windows key, that has less or no command conflicts with other plugin's.

As always thank you very much. :D

---

### Post by diablo75 on 2007-06-29
I'm having a problem with Compiz Fusion that may have been covered in this thread, but it's a long thread....

My window borders don't show up on any windows after it loads.  This happened to me when I ran beryl.  I had to make some changes to the nvidea configuration xorg.conf and I think one other, making it 24bit, and a few other things, and that solved the problem.

But now compiz fusion does this now on my HP zd7000 which has a GeForce Go 5700.  Beryl runs perfectly on it.

Any ideas?

---

### Post by catanzag on 2007-06-29
@ quaid & diablo75
I've got a similar problem (though I got it with gconf backend and with the default gtk-window-decorator), which was solved upgrading the libdecoration0 with the last version (I think from the same 3vin0 repository)

```
$sudo apt-get install libdecoration0
```

regards

catanzag

---

### Post by SRX on 2007-06-29
How do you install compiz themes?

---

### Post by smithman89 on 2007-06-29
Ok, so it works fine, but i have to ask, is anyone else's nautilus startup taking like at least 2 minutes to load?  My prob is that it is very slow to start up, and it is only after that loads then the other startup programs load.

---

### Post by kevinlang21 on 2007-06-29
> **dexter said:**
> Do you have an nvidia card and did you let nvidia-settings overwrite your xorg.conf ?

I'm not sure, I downloaded the nvidia driver from automatix.

---

### Post by kronepils on 2007-06-29
> **xtrm_redbull said:**
> First of all thanks Vorian for this great how to. I installed the compiz fusion today, and starting to play with it :p. Can anyone suggest to me an alternative key to windows key, I have an ibm r50e laptop with no windows key. Since beryl I used the shift key as super key, but now I want to try out the new plugin's in compiz fusion like the ring switcher but some of the key commands uses a combination of Shift+Alt+Super+Tab.

I hope someone with similar problem can enlighten me on this one. I'd like to know what do you guys use as an alternative to the windows key, that has less or no command conflicts with other plugin's.

As always thank you very much. :D


I use my caps key for super. I have this in my .xmodmaprc:
! No Caps Lock
clear lock
! Caps Lock as Win key
add mod4 = Caps_Lock

Then I have this command in my session:
xmodmap ~/.xmodmaprc

It works wonders for me!

---

### Post by dimmanramone on 2007-06-29
Hi and thx for the very good guide, 

I installed compiz fusion without any problem, but i have one question...
is it possible to make different settings for screen 0 and screen 1? screen 1 is my tvout that i'm running it as a separate xserver but i dont really need compiz fusion there...when i use my tvout my system is getting very slow, 3-4 delay in menus for example...

any idea if i can do something about that?

/dimman

---

### Post by haran_elessar on 2007-06-29
Hi guys and gals,

I'm trying to install this and I'm getting an error on the third step of the instructions. When I put in the code to get the key 

KEY=81836EBF; gpg --keyserver subkeys.pgp.net --recv $KEY && gpg --export --armor $KEY | sudo apt-key add -

 it tells me there was an error because the server took too long to respond and the operation timed out...it seems the servers are down or something...for that reason I can't keep on going with the installation...did someone else have this problem? I noticed some of you had a successful installation a few minutes ago...I've been trying to do that step since the last two days and I keep getting the same message...can anyone help?

---

### Post by Orfeus on 2007-06-30
When I m trying to install the packages i get this

sudo apt-get install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz is already the newest version.
compiz-gnome is already the newest version.
E: Couldn't find package compizconfig-settings-manager

But the package is in the directory. Why do i get it?

---

### Post by sab0403 on 2007-06-30
> **Orfeus said:**
> When I m trying to install the packages i get this

sudo apt-get install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz is already the newest version.
compiz-gnome is already the newest version.
E: Couldn't find package compizconfig-settings-manager

But the package is in the directory. Why do i get it?

I got the exact same error as you. A simple

```
sudo apt-get update
sudo apt-get upgrade
```

Should fix it.

---

### Post by brt on 2007-06-30
amaaaaazinnng !



**now with the right repositories, it rocks in  64bit !**

---

### Post by jarocooke on 2007-06-30
> **smithman89 said:**
> Ok, so it works fine, but i have to ask, is anyone else's nautilus startup taking like at least 2 minutes to load?  My prob is that it is very slow to start up, and it is only after that loads then the other startup programs load.

Hi folks, the problem is that when installing Compiz Fusion it sets itself as the default window manager, though for some reason it doesn't actually start properly.  The solution therefore is to reset the default window manager to metacity in gconf and then start compiz fusion using a session startup command.  See below (this is  mentioned somewhere in one of the earlier posts.

Open the Konsole -> gconf-editor -> desktop/gnome/applications/window_manager

Set "current" and "default" to /usr/bin/metacity

System / Preferences / Sessions / add "compiz --replace -c emerald &"

---

### Post by jrochet on 2007-06-30
For anyone who is not able to get pictures working for skydomes, make sure you have the image type enabled in the compiz settings manager.  The options are on the main settings page near the bottom.

---

### Post by xtrm_redbull on 2007-07-01
Thanks for the tip kronepils, it really solves my problem.:p

---

### Post by Beatbreaker on 2007-07-01
this guide was great - i had a problem with emerald at first but got that sorted mainly with the reccommended comend

> compiz --replace -c emerald &

there's some things i preferred Beryl for - i haven't done a full play around with Fusion yet, but i liked how in Beryl i could swap workplaces with my scroll wheel, i also liked how windows would pop out and could be made 3D when using the cube

there seems to be a bug with my shade window affect - it dosen't work every time. I'd actually like to have it so when i double click in the title bar i get it to maxamise/minimise - but i don't think that's a Fusion problem it seems to probably be more like a setting i can change somewhere else (i don't remember where it is yet)

eitherway it's been great to get it going and to play around with, i think the reflection effect is awesome aslo the ring switcher looks amazing

---

### Post by KhaaL on 2007-07-01
Is there a way to revery to beryl, once compiz fusion is installed and all the packages is updated to treviños repository?

---

### Post by slibuntu on 2007-07-01
> **ashwin_cse said:**
> These efects are nothing new. I was using them during edgy eft period in beryl . Just the name has changed from beryl to compiz fusion. After seeing this video, I feel compiz has been stealing some of the good ideas from beryl & branding them as compiz own idea. I know compiz & beryl have agreed to merge. But shouldn't they be renamed in a more neutral way?

Couldn't agree more, the way it looks now is as tho Compiz has swallowed up Beryl, not that they are co-operating

---

### Post by MysteriousMystery on 2007-07-01
My problem is after starting compiz I lose my minizmize, close and mazimize buttons, I know I can hit ctrl to drag or whatever else, but I prefer having the buttons accessible to me. This is in Kubuntu using KDE, is there anyway to keep that running while also using compiz?

---

### Post by Hillbilly Tilley on 2007-07-01
When I run the compiz --replace command I get this

```
barry@barry-laptop:~$ compiz --replace
Adding plugin resizeinfo (resizeinfo)
Adding plugin clone (clone)
Adding plugin animation (animation)
Adding plugin cube (cube)
Adding plugin imgjpeg (imgjpeg)
Adding plugin inotify (inotify)
Adding plugin scale (scale)
Adding plugin tile (tile)
Adding plugin group (group)
Adding plugin put (put)
Adding plugin firepaint (firepaint)
Adding plugin fade (fade)
Adding plugin plane (plane)
Adding core settings (General Options)
Adding plugin png (png)
Adding plugin resize (resize)
Adding plugin annotate (annotate)
Adding plugin expo (expo)
Adding plugin svg (svg)
Adding plugin rotate (rotate)
Adding plugin move (move)
Adding plugin video (video)
Adding plugin snap (snap)
Adding plugin place (place)
Adding plugin zoom (zoom)
Adding plugin showdesktop (showdesktop)
Adding plugin dbus (dbus)
Adding plugin wall (wall)
Adding plugin fs (fs)
Adding plugin crashhandler (crashhandler)
Adding plugin thumbnail (thumbnail)
Adding plugin decoration (decoration)
Adding plugin bench (bench)
Adding plugin neg (neg)
Adding plugin fakeargb (fakeargb)
Adding plugin winrules (winrules)
Adding plugin scaleaddon (scaleaddon)
Adding plugin cubereflex (cubereflex)
Adding plugin trailfocus (trailfocus)
Adding plugin ring (ring)
Adding plugin screenshot (screenshot)
Adding plugin mblur (mblur)
Adding plugin switcher (switcher)
Adding plugin reflex (reflex)
Adding plugin splash (splash)
Adding plugin vpswitch (vpswitch)
Adding plugin water (water)
Adding plugin regex (regex)
Adding plugin text (text)
Adding plugin wobbly (wobbly)
Adding plugin minimize (minimize)
Adding plugin opacify (opacify)
Adding plugin blur (blur)
Adding plugin extrawm (extrawm)
Adding plugin addhelper (addhelper)
Adding plugin fadedesktop (fadedesktop)
Adding plugin glib (glib)
Adding plugin snow (snow)
Backend     : gconf
Integration : true
Profile     : default
Initializing core options...done
Initializing firepaint options...done
Initializing resize options...done
Initializing move options...done
Initializing place options...done
Initializing zoom options...done
Initializing thumbnail options...done
Initializing decoration options...done
Initializing neg options...done
Initializing ring options...done
Initializing reflex options...done
Initializing water options...done
Initializing wobbly options...done
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/friction. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/spring_k. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Initializing minimize options...done
Initializing snow options...done

```

Most things seem to work, some do not

The fire writing does not work any suggestions how to clean the errors up?

---

### Post by Hillbilly Tilley on 2007-07-01
In the CompizConfig Settings Manager under the paint fire on screen section under the action tab initate key is set to  disable.  How do I enable this?

---

### Post by airtonix on 2007-07-02
> Couldn't agree more, the way it looks now is as tho Compiz has swallowed up Beryl, not that they are co-operatingumm 


Im not sure i even care now..

i notice i doesn't lag anywhere near like it did before....

i think thats more important than what the name is.

---

### Post by fishyf on 2007-07-02
I installed this following the instructions and it mostly worked but there was a problem switching workspaces. CTRL ALT right, left and UP don't work (only CTRL ALT DOWN to see the workspaces worked). I could switch workspaces by rotating the cube using the mouse (CTRL ALT left button).

So I disabled the cube and went with desktop plane instead. Fine.

Another problem is that after booting, none of the startup programs start until about 2 mins in.  Once they start, I can run compiz --replace etc.

Desktop effects prior to compiz-fusion were quite usable. (using the default ubuntu setup)

This is all on a DELL d400 laptop with a 82852/855GM Integrated Intel Graphics Device.

Thanks for any insights.

---

### Post by LaneLester on 2007-07-02
> **mostwanted said:**
> Not getting any window decorations... :(
You don't say what kind of graphics card you have, but with my nvidia, I had to follow the instructions in [this forum FAQ thread]("http://forums.opencompositing.org/viewtopic.php?f=51&t=439") to get the window decs.

Lane

---

### Post by KyleBrandt on 2007-07-02
> **crimesaucer said:**
> I fixed my Xine movie palyer like this: The Settings-->--Set Up-->--Video-->--I changed the driver from "auto" to "xshm"  and it worked for playback.

I also fixed the transparent video like this: ccsm-->--General-->--Opacity Settings-->--Window Opacities-->-- then edit the string and take "Unkown" off of the list.

When I went into those opacity settings, and removed all the menu options as well as "unknown", I was able to use the xv driver.  Although it doesn't respond to any of the 3d effects, playback is still fine.  I like this option because on my system the video playback quality is much better.  I have a radeon mobility 9600 and I am using the "ati" driver in my xorg.conf.

---

### Post by c.dric on 2007-07-02
> **Beatbreaker said:**
> there's some things i preferred Beryl for - i haven't done a full play around with Fusion yet, but i liked how in Beryl i could swap workplaces with my scroll wheel, i also liked how windows would pop out and could be made 3D when using the cube

you should be able to switch workplaces with the wheel if you enable Viewport mouse switch in the compiz settings.

---

### Post by eentonig on 2007-07-02
I installed Compiz following this howto and it works... sort off.

I do get composite imaging when I start Compiz. However, it seems like none of the options from the settings manager work. I can't switch cube, ...

However, my left top screencorner is still a 'hot corner' that gives me an overview of open applications. When running compiz, this animation is slighty different (and better) then when running Beryl.

Anybody an idea what could be wrong?

---

### Post by KhaaL on 2007-07-02
> **eentonig said:**
> I installed Compiz following this howto and it works... sort off.

I do get composite imaging when I start Compiz. However, it seems like none of the options from the settings manager work. I can't switch cube, ...

However, my left top screencorner is still a 'hot corner' that gives me an overview of open applications. When running compiz, this animation is slighty different (and better) then when running Beryl.

Anybody an idea what could be wrong?

Try to switch to flat-file backend. it solved my problems that were similiar to yours,

---

### Post by eentonig on 2007-07-02
Were do I do that?

---

### Post by KhaaL on 2007-07-02
open CCSM, backend & profile, backend and then choose flat-file configuration

---

### Post by astralsin on 2007-07-02
i've done everything i can find on this post pertaining to the problem but i still cant get window borders.  anyone else having this problem?

---

### Post by KyleBrandt on 2007-07-02
Anyone know how to get "Show windows from current workspace" under the window list preferences from gnome panel to work properly with Compiz running? At the moment it just shows the windows running on all workspaces, and I want it just to show the ones on my current workspace.

---

### Post by ShiftyPowers on 2007-07-02
> **KhaaL said:**
> open CCSM, backend & profile, backend and then choose flat-file configuration

that worked like a charm! thanks man.  so much better than beryl!

---

### Post by sabarig on 2007-07-03
> **astralsin said:**
> i've done everything i can find on this post pertaining to the problem but i still cant get window borders.  anyone else having this problem?



I too had the same problem. Try adding "compiz --replace -c emerald &"   to your startup. That fixed my problem.

---

### Post by skymera on 2007-07-03
im only having cube problems...
my pc freezes and becomes unresponsive...

---

### Post by AvalonSkies on 2007-07-03
Woot, my first post on UbuntuForums!

So check this out. I couldn't get Compiz to work. I couldn't get Beryl to work. But Fusion? Perfect! Awesome guide. Some of the effects didn't work for me either at first, but a lot of them did, so I knew I *installed* it right... so basically I jiggled all the settings bars (*cough*General --> DesktopSize *cough*) until everything worked, muahah.

I've been running Ubuntu on my little Compaq v6000 notebook for all of... like 2 days. I'm a *nixnewb who fought through learning (the hard way) why I should ignore 64bit software, and I did the NVIDIA thing (tseliot is an angel), and I did the... frickin' Broadcom WiFi thing, and now I did the Compiz thing, and I can't even give you a straight answer as to why [FONT="Courier New"]sudo[/FONT] is magical yet. Thanks for the help! This forum rocks!

That... and desktop effects for the win. :popcorn:

---

### Post by Istari.6 on 2007-07-03
Hi Guys

I've had Compiz Fusion working perfectly but a reinstall of my Feisty was necessary, and now I'm getting the following error when following the step by step instructions. It's at the step where I have to do and apt-get upgrade. I'm getting an MD5 Checksum error and hence cannot proceed with the install.

Can anyone help?

---

### Post by Nekiruhs on 2007-07-03
Aah! I killed Emerald somehow!
```
nekiruhs@kUbuntu:~$ emerald --replace
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Segmentation fault (core dumped)

```
What should I do?
EDIT: Reinstalling Emerald and messing with some setings fixed it.

---

### Post by bimmerd00d on 2007-07-03
Apparently deselecting "Detect Refresh Rate" made my refresh setting skyrocket to 200.  I guess my machine didn't like that too much.  Changed that and added "Detect Output" and all is well again.  The problem was that i could only see about 20% of my screen at the top left.  I think it has something to do with the setting under output of 640x480.  I want to set that to match my screens, but i'll have to wait for some help or do some reading.  

NVidia 7900GS + Viewsonic 20.1" 4:3 and an Olevia 27" LCD at 1280x720 with a VGA adapter.

---

### Post by trinaryouroboros on 2007-07-04
Ah ha, there we go!

64-bit is in the hizzy, good times!

I also did the remove Beryl from startup and add compiz --replace and emerald --replace to startup, everythings pretty happy, I'm diggin it!

:popcorn:

---

### Post by iceportal on 2007-07-04
I'm still getting the following error with my ATI card (default drivers that Ubuntu had me install):

Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

Any ideas? Please, I need to fix this ASAP!

---

### Post by Alex Fernandez on 2007-07-04
> **iceportal said:**
> I'm still getting the following error with my ATI card (default drivers that Ubuntu had me install):

Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

Any ideas? Please, I need to fix this ASAP!


I'm getting that now, despite compiz working perfectly about a day ago (until apt updated it)

---

### Post by t.rei on 2007-07-04
Same here. Worked smoothly 30 Minutes ago, now I'm back to metacity & gtk-window-decorator. :/

---

### Post by egonkasper on 2007-07-04
It is not working for me either since apt updated it about 2 this morning.

---

### Post by digital_exhaust on 2007-07-04
Quick question....will Fusion work with the fglrx driver?

---

### Post by javier.david on 2007-07-04
Do I have to type compiz --replace every time I log into my account?? How can set as a default windows manager??.

Appreciate your help.

---

### Post by Alex Fernandez on 2007-07-04
> **javier.david said:**
> Do I have to type compiz --replace every time I log into my account?? How can set as a default windows manager??.

Appreciate your help.


add it to be auto-run on session start

---

### Post by PuppyFromHell on 2007-07-04
I'm getting unmet dependencies all over the place and when I go into aptitude it says that they aren't available and won't be installed.
```

dw@dw-laptop:~$ sudo apt-get install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz: Depends: compiz-core but it is not going to be installed
          Depends: compiz-plugins but it is not going to be installed
  compiz-fusion-plugins-extra: Depends: compiz-core but it is not going to be installed
                               Depends: compiz-fusion-plugins-main but it is not going to be installed
                               Depends: libc6 (>= 2.5-0ubuntu1) but 2.4-1ubuntu12.3 is to be installed
                               Depends: libcairo2 (>= 1.4.0) but 1.2.4-1ubuntu2 is to be installed
                               Depends: libglib2.0-0 (>= 2.12.9) but 2.12.4-0ubuntu1 is to be installed
                               Depends: libpango1.0-0 (>= 1.16.2) but 1.14.5-0ubuntu1 is to be installed
                               Depends: libpng12-0 (>= 1.2.13-4) but 1.2.8rel-5.1ubuntu0.2 is to be installed
                               Depends: libxcomposite1 (>= 1:0.3-1) but 1:0.3-0ubuntu1 is to be installed
                               Depends: libxml2 (>= 2.6.27) but 2.6.26.dfsg-2ubuntu4 is to be installed
                               Depends: libxrandr2 (>= 2:1.2.0) but 2:1.1.1-0ubuntu1 is to be installed
                               Depends: libxslt1.1 (>= 1.1.20) but 1.1.17-2build1 is to be installed
  compiz-gnome: Depends: libatk1.0-0 (>= 1.13.1) but 1.12.3-0ubuntu1 is to be installed
                Depends: libc6 (>= 2.5-0ubuntu1) but 2.4-1ubuntu12.3 is to be installed
                Depends: libcairo2 (>= 1.4.0) but 1.2.4-1ubuntu2 is to be installed
                Depends: libdbus-1-3 (>= 0.94) but 0.93-0ubuntu3.1 is to be installed
                Depends: libdbus-glib-1-2 (>= 0.73) but 0.71-1ubuntu1 is to be installed
                Depends: libdecoration0 but it is not going to be installed
                Depends: libfontconfig1 (>= 2.4.0) but 2.3.2-7ubuntu2 is to be installed
                Depends: libglib2.0-0 (>= 2.12.9) but 2.12.4-0ubuntu1 is to be installed
                Depends: libgnome-keyring0 (>= 0.7.1) but 0.6.0-0ubuntu2 is to be installed
                Depends: libgnomeui-0 (>= 2.17.1) but 2.16.1-0ubuntu2 is to be installed
                Depends: libgnomevfs2-0 (>= 1:2.17.90) but 2.16.1-0ubuntu7 is to be installed
                Depends: libpango1.0-0 (>= 1.16.2) but 1.14.5-0ubuntu1 is to be installed
                Depends: libxrandr2 (>= 2:1.2.0) but 2:1.1.1-0ubuntu1 is to be installed
  compizconfig-settings-manager: Depends: compiz-plugins but it is not going to be installed
                                 Depends: python-compizconfig but it is not going to be installed
  libcompizconfig-backend-gconf: Depends: libc6 (>= 2.5-0ubuntu1) but 2.4-1ubuntu12.3 is to be installed
                                 Depends: libcompizconfig0 but it is not going to be installed
                                 Depends: libglib2.0-0 (>= 2.12.9) but 2.12.4-0ubuntu1 is to be installed
                                 Depends: libpng12-0 (>= 1.2.13-4) but 1.2.8rel-5.1ubuntu0.2 is to be installed
                                 Depends: libxcomposite1 (>= 1:0.3-1) but 1:0.3-0ubuntu1 is to be installed
                                 Depends: libxml2 (>= 2.6.27) but 2.6.26.dfsg-2ubuntu4 is to be installed
                                 Depends: libxrandr2 (>= 2:1.2.0) but 2:1.1.1-0ubuntu1 is to be installed
                                 Depends: libxslt1.1 (>= 1.1.20) but 1.1.17-2build1 is to be installed
E: Broken packages

```

---

### Post by acidburner on 2007-07-04
So compiz fusion works amazingly... but Imade the mistake ofbinding space to an action (the fire writing clear action)... now it wont let me unbind it... which sucks cause now space doesnt work with any program... and im using ctrl+v to create these spaces... its probably something stupid to fix and I cant find anyway to fix it (google, or searching these forums). rebinding the action still doesnt solve the issue... ill try restarting X now.

Edit: Ok so the combination of Restarting X and rebinding that action to a different key band-aided my problem.

---

### Post by Hillbilly Tilley on 2007-07-04
After I use the compiz --replace command I get this
```
barry@barry-laptop:~$ compiz --replace
Adding plugin resizeinfo (resizeinfo)
Adding plugin clone (clone)
Adding plugin animation (animation)
Adding plugin cube (cube)
Adding plugin imgjpeg (imgjpeg)
Adding plugin inotify (inotify)
Adding plugin scale (scale)
Adding plugin tile (tile)
Adding plugin group (group)
Adding plugin put (put)
Adding plugin firepaint (firepaint)
Adding plugin fade (fade)
Adding plugin plane (plane)
Adding core settings (General Options)
Adding plugin png (png)
Adding plugin resize (resize)
Adding plugin annotate (annotate)
Adding plugin expo (expo)
Adding plugin svg (svg)
Adding plugin rotate (rotate)
Adding plugin move (move)
Adding plugin video (video)
Adding plugin snap (snap)
Adding plugin place (place)
Adding plugin zoom (zoom)
Adding plugin showdesktop (showdesktop)
Adding plugin dbus (dbus)
Adding plugin wall (wall)
Adding plugin fs (fs)
Adding plugin crashhandler (crashhandler)
Adding plugin thumbnail (thumbnail)
Adding plugin decoration (decoration)
Adding plugin bench (bench)
Adding plugin neg (neg)
Adding plugin fakeargb (fakeargb)
Adding plugin winrules (winrules)
Adding plugin scaleaddon (scaleaddon)
Adding plugin cubereflex (cubereflex)
Adding plugin trailfocus (trailfocus)
Adding plugin ring (ring)
Adding plugin screenshot (screenshot)
Adding plugin mblur (mblur)
Adding plugin switcher (switcher)
Adding plugin reflex (reflex)
Adding plugin splash (splash)
Adding plugin vpswitch (vpswitch)
Adding plugin water (water)
Adding plugin regex (regex)
Adding plugin text (text)
Adding plugin wobbly (wobbly)
Adding plugin minimize (minimize)
Adding plugin opacify (opacify)
Adding plugin blur (blur)
Adding plugin extrawm (extrawm)
Adding plugin addhelper (addhelper)
Adding plugin fadedesktop (fadedesktop)
Adding plugin glib (glib)
Adding plugin snow (snow)
Backend     : gconf
Integration : true
Profile     : default
Initializing core options...done
Initializing imgjpeg options...done
Initializing firepaint options...done
Initializing resize options...done
Initializing svg options...done
Initializing move options...done
Initializing place options...done
Initializing zoom options...done
Initializing thumbnail options...done
Initializing decoration options...done
Initializing neg options...done
Initializing ring options...done
Initializing reflex options...done
Initializing water options...done
Initializing wobbly options...done
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/friction. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/spring_k. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Initializing minimize options...done
Initializing snow options...done

(gtk-window-decorator:7434): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7434): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7434): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7434): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7434): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7434): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7434): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7434): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7434): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7434): Wnck-WARNING **: Unhandled action type (nil )
Initializing animation options...done
Initializing fade options...done
Initializing trailfocus options...done
Initializing opacify options...done
Initializing addhelper options...done
Initializing cube options...done
Initializing scale options...done
Initializing expo options...done
Initializing rotate options...done
Initializing cubereflex options...done
Initializing switcher options...done


```

Most stuff works but some do not.....does anyone know what the errors are and how to fix them?

---

### Post by complexgeek on 2007-07-05
I see others are having difficulty at the moment as well. I just upgraded and now when compiz is running I get no window decorations, either through emerald or kde-window-decorator. Hopefully they fix this soon.

---

### Post by bimmerd00d on 2007-07-05
I just noticed that this uses a LOT less ram and CPU than Beryl or oldschool Compiz did.   Keep up the good work, can't wait to see waht's in store for the future.  Also for some reason it runs a lot better on my NVidia Quadro NVS 120m in my Latitude D820 where Beryl lagged a bit.  Turning on cube transparency still slows it down a lot, maybe there are some Nvidia options i could play with, but it's working right now.  If any of you Nvidia gurus want to help me out that'd be cool :D

---

### Post by 5h4rk on 2007-07-05
k, I've installed it, and it's kind of NOT working...

Can anyone tell me how to uninstall beryl, compiz, esmerald, or whatever it takes to start over a clean installation please?

Thanks.

---

### Post by bjtuna on 2007-07-05
I'm loading compiz --replace and emerald --replace in my session startup.  Once compiz/emerald have loaded up, certain dialogs no longer accept keyboard input.  Specifically, if I hit ALT-F2 for "run program", I can't type into the dialog box.

I discovered this because I have "ssh-add" running from my session startup too, which brings up gnome-ssh-askpass. I can't type into that dialog either, once compiz and emerald have started up.

---

### Post by BlahMan_of.Doom on 2007-07-05
The cube does not work at all for me. It's loaded, but I can't CTRL ALT LCLICK to rotate the cube.

---

### Post by smithman89 on 2007-07-05
Ok, so now i have a new question.  And im wondering if anyone else is having this problem.  With the cube, i try to change the top image to some other png file that isnt the default one.  But after i do so, it reverts back to the default color (not the default pic) instantly.  And when i manually change it in the gconf-editor, it just doesnt listen to me.  Any thoughts?

---

### Post by pnix on 2007-07-05
great howto, it work fine on my system.

---

### Post by trinaryouroboros on 2007-07-05
> **PuppyFromHell said:**
> I'm getting unmet dependencies all over the place and when I go into aptitude it says that they aren't available and won't be installed.
```

dw@dw-laptop:~$ sudo apt-get install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf
Reading package lists... Done
,,,
...
The following packages have unmet dependencies:
  compiz: Depends: compiz-core but it is not going to be installed
          Depends: compiz-plugins but it is not going to be installed
  compiz-fusion-plugins-extra: Depends: compiz-core but it is not going to be installed
...
...
E: Broken packages

```

Sounds like a bit of a mess, I'm no major expert, but I've found these type of dependency problems occur for only a few reasons. First, make sure you get and correctly apply 3v1n0's /etc/apt/sources.list - and check there's no errors.

The link below is for Feisty Fawn, click the title bar of web page for other dists:

[http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/](http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/)

Sidenote: If you are using 64-bit make sure you add two lines under download.tuxfamily.org/3v1n0's eyecandy lines, they should look identical, but, instead of "eyecandy" replace that with "eyecandy-amd64"

Once you're sure that's squared away, then try:

```
sudo apt-get update
sudo apt-get upgrade -f
```

See if that works. If not, you could also go into System -> Admin > Synaptic, and from the menu bar on top there should be an option in one of those that says "Fix broken packages", try clicking that and then hit the big Apply button. 

Else, it may require some rooting around to fix those dependency issues. You might have to fish through synaptic for each problem and strip em/reinstall/etc.

Like I said, though, I'm not an expert, but, I would try the above in this case.

> **5h4rk said:**
> k, I've installed it, and it's kind of NOT working...

Can anyone tell me how to uninstall beryl, compiz, esmerald, or whatever it takes to start over a clean installation please?

Thanks.

Sure thing,

```
sudo apt-get remove beryl compiz emerald
sudo apt-get autoremove
```

Note: The second line will wipe any other installed programs that are no longer used, be sure to note what's actually being removed before you do that.

Then start at the how-to again for compiz, and, don't forget to remove "Beryl" and "Beryl Manager" from the System -> Preferences -> Sessions -> Startup

You will replace Beryl in the start up with two new ones:

Name: Compiz
Launch: ```
compiz --replace
```

Name: Emerald
Launch: ```
emerald --replace
```

Then do a reboot, should be merry happy compiz fusion galore!

:popcorn:

---

### Post by trinaryouroboros on 2007-07-05
> **smithman89 said:**
> Ok, so now i have a new question.  And im wondering if anyone else is having this problem.  With the cube, i try to change the top image to some other png file that isnt the default one.  But after i do so, it reverts back to the default color (not the default pic) instantly.  And when i manually change it in the gconf-editor, it just doesnt listen to me.  Any thoughts?

I am also having similar problems, I suspected this was just another bug to be squashed by the compiz-fusion team, so in the meantime I setup 2 additional Horizontal Workspaces (General Options, I think) and let the cube be a 6 sided thingamajig. I was also hoping they would fix the caps for more-than-cube setup's like that, too.

If this is not a bug, then I stand corrected, but, I'd appreciate a PM to tell me what I'm doing wrong as well in this case.

:KS

Thanks!

---

### Post by crhumber on 2007-07-05
I've installed compiz fusion using this guide and everything seemed to go smoothly, but when I start compiz the titlebars and borders around my windows immediately disappear.  I've searched for a solution, but nothing seems to work.  I have Nvidia with accelerated graphics enabled.  Can anyone help??

---

### Post by greg.hagen on 2007-07-05
> **crhumber said:**
> I've installed compiz fusion using this guide and everything seemed to go smoothly, but when I start compiz the titlebars and borders around my windows immediately disappear.  I've searched for a solution, but nothing seems to work.  I have Nvidia with accelerated graphics enabled.  Can anyone help??

I was unable to get emerald to work with compiz fusion. It just says they have incompatible dates or something. You can try running "gtk-window-decorator --replace" instead. It's not quite as pretty or customizable, but it works for me.

---

### Post by guru369 on 2007-07-05
> **crhumber said:**
> I've installed compiz fusion using this guide and everything seemed to go smoothly, but when I start compiz the titlebars and borders around my windows immediately disappear.  I've searched for a solution, but nothing seems to work.  I have Nvidia with accelerated graphics enabled.  Can anyone help??
Make sure you have:
```

    Option         "AddARGBGLXVisuals" "True"

```

Under the screen section in xorg.conf

---

### Post by crhumber on 2007-07-05
Thanks for the tip.  I'm trying to get compiz working first so I can then get kiba-dock or awn to run without a black bar behind it.  Any other ideas?

---

### Post by Mostlyharmless42 on 2007-07-05
i'm having a small difficulty w/ the install

```
root@Merlin-In-a-Tux:/home/jred42# sudo apt-get install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz-gnome is already the newest version.
compiz-gnome set to manual installed.
E: Couldn't find package compizconfig-settings-manager

```

---

### Post by ajesh on 2007-07-06
I am getting the following error on compiz --replace. Does anyone know what the error implies and how to get it fixed?

Adding plugin animation (animation)
Adding plugin scale (scale)
Adding plugin gotovp (gotovp)
Adding plugin bs (bs)
Adding plugin png (png)
Adding plugin keybinding (keybinding)
Adding plugin firepaint (firepaint)
Adding plugin neg (neg)
Adding plugin mousegestures (mousegestures)
Adding plugin screenshot (screenshot)
Adding plugin video (video)
Adding plugin reflex (reflex)
Adding plugin move (move)
Adding plugin fs (fs)
Adding plugin gears (gears)
Adding plugin inotify (inotify)
Adding plugin trailfocus (trailfocus)
Adding plugin colorfilter (colorfilter)
Adding plugin wobbly (wobbly)
Adding plugin resizeinfo (resizeinfo)
Adding plugin clone (clone)
Adding plugin water (water)
Adding plugin expo (expo)
Adding plugin vpswitch (vpswitch)
Adding plugin thumbnail (thumbnail)
Adding plugin crashhandler (crashhandler)
Adding plugin annotate (annotate)
Adding plugin ring (ring)
Adding plugin group (group)
Adding plugin quickchange (quickchange)
Adding plugin flash (flash)
Adding core settings (General Options)
Adding plugin zoom (zoom)
Adding plugin opacify (opacify)
Adding plugin addhelper (addhelper)
Adding plugin decoration (decoration)
Adding plugin fade (fade)
Adding plugin blur (blur)
Adding plugin text (text)
Adding plugin dbus (dbus)
Adding plugin place (place)
Adding plugin wall (wall)
Adding plugin fakeargb (fakeargb)
Adding plugin atlantis (atlantis)
Adding plugin screensaver (screensaver)
Adding plugin rotate (rotate)
Adding plugin tile (tile)
Adding plugin scaleaddon (scaleaddon)
Adding plugin minimize (minimize)
Adding plugin put (put)
Adding plugin snap (snap)
Adding plugin notification (notification)
Adding plugin bench (bench)
Adding plugin mswitch (mswitch)
Adding plugin mblur (mblur)
Adding plugin cube (cube)
Adding plugin imgjpeg (imgjpeg)
Adding plugin plane (plane)
Adding plugin cubereflex (cubereflex)
Adding plugin resize (resize)
Adding plugin glib (glib)
Adding plugin switcher (switcher)
Adding plugin wallpaper (wallpaper)
Adding plugin 3d (3d)
Adding plugin regex (regex)
Adding plugin snow (snow)
Adding plugin svg (svg)
Adding plugin extrawm (extrawm)
Adding plugin winrules (winrules)
Adding plugin kiosk (kiosk)
Adding plugin splash (splash)
Adding plugin cheatsheet (cheatsheet)
Adding plugin fadedesktop (fadedesktop)
Adding plugin showdesktop (showdesktop)
Backend     : ini
Integration : true
Profile     : default
Initializing core options...done
Initializing move options...done
Initializing water options...done
Initializing thumbnail options...done
Initializing zoom options...done
Initializing decoration options...done
Initializing place options...done
Initializing minimize options...done
Initializing resize options...done
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Initializing video options...done
Initializing wobbly options...done
Initializing fade options...done
Initializing cube options...done
Initializing switcher options...done
Initializing scale options...done
Initializing expo options...done
Initializing group options...done
Initializing opacify options...done
Initializing rotate options...done
/usr/bin/compiz: line 686: 22099 Segmentation fault      (core dumped) $*
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

---

### Post by ajesh on 2007-07-06
Ok, I got it fixed, once I updated some packages pushed by the update manager. 

The window borders were missing with "compiz --replace", but then I added the "-c emerald" option and now everything works great.

Thanks.....

---

### Post by Hobo Joe on 2007-07-06
I found a bug, pretty small, but it's a big deal for me.
I'm unable to change the 'Window Menu' shortcut. No matter what i do, I can't get rid of the 'button3' option. I really need to be able to change it though, becuase a program I use has to have that as a function.

Any help would be awesome.

---

### Post by trinaryouroboros on 2007-07-06
> **crhumber said:**
> I've installed compiz fusion using this guide and everything seemed to go smoothly, but when I start compiz the titlebars and borders around my windows immediately disappear.  I've searched for a solution, but nothing seems to work.  I have Nvidia with accelerated graphics enabled.  Can anyone help??

At a terminal:
```
emerald --replace
```

If it works, add that to your startup - also make sure Beryl is Removed!

If that doesn't work, try:
```
sudo apt-get remove emerald && sudo apt-get autoremove && sudo apt-get install emerald && emerald --replace
```

Also be sure to note the reply you received in this thread earlier, for your xorg.conf

> **Hobo Joe said:**
> I found a bug, pretty small, but it's a big deal for me.
I'm unable to change the 'Window Menu' shortcut. No matter what i do, I can't get rid of the 'button3' option. I really need to be able to change it though, becuase a program I use has to have that as a function.

Any help would be awesome.

I had trouble reassigning key bindings, the problem seems that sometimes it doesn't tell you another plugin is accidentally using that key binding. You'll have to go into each CompizConfig shortcut, click on Actions, and see if Button 2 is anywhere else. Definitely worthy to report this on bugzilla to them.

---

### Post by rude_lee on 2007-07-06
compiz not working i get this output


rude@rude-laptop:~$ sudo wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -
--18:00:47--  [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg)
           => `-'
Resolving download.tuxfamily.org... 88.191.250.18
Connecting to download.tuxfamily.org|88.191.250.18|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,180 (4.1K) [text/plain]

100%[====================================>] 4,180         --.--K/s             

18:00:48 (36.99 KB/s) - `-' saved [4180/4180]

OK
rude@rude-laptop:~$ sudo apt-get update
Get:1 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B]
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US       
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release                        
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources                 
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 4B in 0s (5B/s)  
Reading package lists... Done
rude@rude-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rude@rude-laptop:~$ sudo apt-get install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager

---

### Post by trinaryouroboros on 2007-07-06
> **rude_lee said:**
> compiz not working i get this output



E: Couldn't find package compizconfig-settings-manager

Those of you experiencing this problem, are you using 64-bit Feisty, or 32-bit?

---

### Post by rude_lee on 2007-07-06
64 bit fiesty

---

### Post by trinaryouroboros on 2007-07-06
> **rude_lee said:**
> 64 bit fiesty

There's a line or four in your **/etc/apt/sources.list** for: _3v1n0's eyecandy repository_, should be something like download.tuxfamily.org/3v1n0 or something. 

Is it set to **eyecandy-amd64** on the deb lines? 

If not, change it to that and reinstall compiz.

Since the beginning of compiz-fusion we were getting uninstallable components, until the 64-bit version was fully loaded. By then, the repository for amd64 was added as a new repository called "eyecandy-amd64" - and a quick switch did the trick, all components should install.

If not, I'm not sure where else to look, but, you could start by asking over at [3v1n0's repository]("http://3v1n0.tuxfamily.org/") regarding the missing compizconfig-manager.

---

### Post by crhumber on 2007-07-06
> **trinaryouroboros said:**
> At a terminal:
```
emerald --replace
```

If it works, add that to your startup - also make sure Beryl is Removed!

If that doesn't work, try:
```
sudo apt-get remove emerald && sudo apt-get autoremove && sudo apt-get install emerald && emerald --replace
```

Also be sure to note the reply you received in this thread earlier, for your xorg.conf



I had trouble reassigning key bindings, the problem seems that sometimes it doesn't tell you another plugin is accidentally using that key binding. You'll have to go into each CompizConfig shortcut, click on Actions, and see if Button 2 is anywhere else. Definitely worthy to report this on bugzilla to them.


Do i issue the emerald --replace command while compiz is running? thanks

---

### Post by Delirious on 2007-07-07
just did a sudo apt-get update and sudo apt-get upgrade, and now my windows borders have disappeared and i cant get them back using any of the --replace commands.:sad: So much for it working perfectly.

---

### Post by firmwire on 2007-07-07
Yep. I know what you mean.
 Here is a post I did a few minutes before you. All my borders disappeared and when I opened a window it was stuck in the upper left of my desktop and I couldn't move them. Also the cube didn't work anymore. Even though when I did an fresh install a few hours ago compiz fusion was working like a champ.

[http://ubuntuforums.org/showthread.php?t=488385&page=2](http://ubuntuforums.org/showthread.php?t=488385&page=2)

---

### Post by Delirious on 2007-07-07
> **firmwire said:**
> Yep. I know what you mean.
 Here is a post I did a few minutes before you. All my borders disappeared and when I opened a window it was stuck in the upper left of my desktop and I couldn't move them. Also the cube didn't work anymore. Even though when I did an fresh install a few hours ago compiz fusion was working like a champ.

[http://ubuntuforums.org/showthread.php?t=488385&page=2](http://ubuntuforums.org/showthread.php?t=488385&page=2)

The first batch of updates i did yesterday didnt hurt anything, everything was working until i did the update.

This is what i get when i run this from the Terminal, 

user@Ubuntu1:~$ compiz --replace -c emerald &
[2] 7482
user@Ubuntu1:~$ /usr/bin/compiz.real (core) - Error: Can't load plugin 'ccp' because it is built for ABI version 20070606 and actual version is 20070706
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'

---

### Post by firmwire on 2007-07-07
I get pretty much get the same message.

---

### Post by Dyegov on 2007-07-07
Everything works wonderful, even the cube in a 64mb integrated nvidia video card, but I've got just 1 problem: I have no title bar, no minimize, maximize or close button. I need them!!! How do I fix it?

Edit: I restarted and now they show normally. Now I want to know, how do I do so I don't have to "Alt + F2 -> compiz --replace" every time I turn my computer on?

---

### Post by adityavpratap on 2007-07-07
thanks cwood06,
Mine is ATI card. As per your suggestion, I tried to change the backend to gconf. But I found that it was already selected. So I switched to Flat-file configuration backend, and my rotating cube started to work!

---

### Post by Do0odz on 2007-07-07
I've tried installing the repos for i368 but I keep getting this 

 deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
bash: deb: command not found


help please !?

---

### Post by Do0odz on 2007-07-07
I've tried installing the repos for i368 but I keep getting this 

 deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
bash: deb: command not found


help please !?

---

### Post by AMMOnium on 2007-07-07
Do0odz, read carefully

> **add the following to your _/etc/apt/sources.list_**

for i386

```
# Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs... 
deb http://download.tuxfamily.org/3v1deb feisty eyecandy 
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```

---

### Post by Do0odz on 2007-07-07
> **AMMOnium said:**
> Do0odz, read carefully


Lol thank u :) .. 
ok after I've done this .. I run the update and I get the following error  Some index files failed to download, they have been ignored, or old ones used instead.

any idea how to solve this !?

---

### Post by Delirious on 2007-07-07
> **Dyegov said:**
> Everything works wonderful, even the cube in a 64mb integrated nvidia video card, but I've got just 1 problem: I have no title bar, no minimize, maximize or close button. I need them!!! How do I fix it?

Edit: I restarted and now they show normally. Now I want to know, how do I do so I don't have to "Alt + F2 -> compiz --replace" every time I turn my computer on?

Its in the first page of the guide, systems > pref > sessions > new > paste compiz --replace for the command and give it a name.

---

### Post by firmwire on 2007-07-07
I have also been posting in another topic dealing mostly with ATI and XGL.
Since an update last night, I lost my borders on my windows and I have no cube, and whenever I open any window, it is stuck in the upper left corner and I can't move it and I can't see any of the menu options for the window. I tried another fresh install and it didn't solve my issue. That new update didn't work well with my system, even though earlier in the day ( off a fresh install) I have everything working.

adityavpratap wrote:
> **adityavpratap said:**
> Actually, lost window borders issue was sorted out by the following command -
$ compiz --replace -c emerald
If it still doesn't work, try to run compiz with indirect rendering

Do you think this will fix my issue, once I reload again on a fresh install tonight? And what is the best way to go about running compiz with indirect rendering?

---

### Post by Delirious on 2007-07-07
Just tried removing compiz fusion and reinstalling with no luck.

Beware the updates people!

---

### Post by Murador on 2007-07-07
> **Delirious said:**
> The first batch of updates i did yesterday didnt hurt anything, everything was working until i did the update.

This is what i get when i run this from the Terminal, 

user@Ubuntu1:~$ compiz --replace -c emerald &
[2] 7482
user@Ubuntu1:~$ /usr/bin/compiz.real (core) - Error: Can't load plugin 'ccp' because it is built for ABI version 20070606 and actual version is 20070706
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'

Same thing here :(
I installed compiz fusion yesterday, worked great.

Today I got the updates, but the windows borders have disappeared. Launching Beryl instead of compiz doesn't work either.
And I got the same "ccp plugin not working" as you

I'm running feisty amd64 / nVidia graphics

---

### Post by Dyegov on 2007-07-07
> **Delirious said:**
> Its in the first page of the guide, systems > pref > sessions > new > paste compiz --replace for the command and give it a name.

Already did, someone else told me. Thanks anyway, It worked perfectly :KS

---

### Post by trinaryouroboros on 2007-07-07
> **crhumber said:**
> Do i issue the emerald --replace command while compiz is running? thanks

Yeah, you can do that, no worries.

> **Murador said:**
> Same thing here :(
I installed compiz fusion yesterday, worked great.

Today I got the updates, but the windows borders have disappeared. Launching Beryl instead of compiz doesn't work either.
And I got the same "ccp plugin not working" as you

I'm running feisty amd64 / nVidia graphics

To fix a bunch of problems I got rid of beryl. Also someone stated they had to specifically get rid of libberyldecorations0 to fix things too, maybe that's related? Not sure.

---

### Post by Cresho on 2007-07-07
Thanks vorian!

Appearantly, this compiz-fusion runs way better than beryl.  I'm glad both teams got together and slaped this thing together.  It's laggless on my system, feels lean, and it runs under my 3d games just fine.

---

### Post by Shiverz on 2007-07-07
Hello all,

This is my first post here on the Ubuntu forums. Thank you for this easy install guide, I can't stop playing with all my new desktop toys now!

I was wondering what the "Super"-key was, but someone in my native ubuntu IRC channel kindly enlightened me ;).

I have one question though, does Compiz Fusion "trick" the Workspace Manager? The latter seems to think there's only one workspace.

I think I'll go tinker with the CompizConfig Settings Manager some more now!

Regards,

~Shiverz.

---

### Post by brt on 2007-07-07
> **Delirious said:**
> 
user@Ubuntu1:~$ compiz --replace -c emerald &
[2] 7482
user@Ubuntu1:~$ /usr/bin/compiz.real (core) - Error: Can't load plugin 'ccp' because it is built for ABI version 20070606 and actual version is 20070706
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'

same here :(

but i found out when i **apt-get remove libcompizconfig0** i can start compiz again, but no more configuration :(

---

### Post by firmwire on 2007-07-07
> **brt said:**
> same here :(

but i found out when i **apt-get remove libcompizconfig0** i can start compiz again, but no more configuration :(

So are you saying that  you got everything to work again, but you just had to set it up? Or no configuration means...nothing worked?

---

### Post by brt on 2007-07-07
> **firmwire said:**
> So are you saying that  you got everything to work again, but you just had to set it up? Or no configuration means...nothing worked?

well compiz & emerald are running but all settings are missing, some plugins not loaded, no possibility to configure anything :(  

meanwhile i managed to compile using:  (comp²)fusion - A Compiz Fusion Build Script with Crash Reco

[http://forums.opencompositing.org/viewtopic.php?f=12&t=1123]("http://forums.opencompositing.org/viewtopic.php?f=12&t=1123")

but i also had a look at needed dependencies here:

[http://compiz.org/Compiling]("http://compiz.org/Compiling")

and i had to edit the ccf file to use 
SUPRESS="false"
COMPIZARGS="--prefix=/usr --enable-librsvg"
GENERICARGS="--prefix=/usr"  

i also commented out compiz-scripts as there is nothing to compile there.

if you are familiar with compile errors give it a go, but **be warned it will not just work "right out of the box"** i also had to compile some of the directories manually... 

compiz-scripts contains the compiz-manager script, after compilation was successful i placed it at /usr/local/bin and added it to my startup-scripts and it works fine.

**edit:**

but maybe this is even more worth a try:
> Build Debian Packages of Compiz Fusion GIT w/ MakeFusionDebs
[http://forums.opencompositing.org/viewtopic.php?f=14&t=1076&start=0&st=0&sk=t&sd=a]("http://forums.opencompositing.org/viewtopic.php?f=14&t=1076&start=0&st=0&sk=t&sd=a")


---

### Post by EnderTheThird on 2007-07-07
Anyone able to help those of us getting the 'ccp' plugin error after the updates...?

---

### Post by Impulse666 on 2007-07-07
> **Vorian said:**
> 
***Edit***
If you have trouble getting your window decorations working, and use beryl 
alt+F2
```
compiz --replace -c emerald &
```

THANK YOU for such an easy to follow guide! that last bit fixed window decorations for me. :D

---

### Post by nox-Hand on 2007-07-08
It took me a long time of pleading around in IRC channels, and I'd like to thank all the people that tried to help - but I  also found what I was looking for:

```
07:22 < trench-> sudo nvidia-xconfig --add-argb-glx-visuals -d 24
07:22 < trench-> then restart X

```

That was all I needed, then it worked :) 

Hope it helps anyone?

---

### Post by firmwire on 2007-07-08
I wish I still had my nVidia BFG 6800 GT OC, instead of this PCI express ATI X1600.

---

### Post by narehart on 2007-07-08
I'm having a problem in fusion.  Whenever I play a video be it in Mplayer or VLC the screen is translucent even when maximized.  I've played around with the settings manager trying to adjust this.  The only luck I've had though is if I check or uncheck the video plugin it will become opaque but as soon as I click something else it becomes trans again.  Anybody else have this problem???

---

### Post by firmwire on 2007-07-08
> **Murador said:**
> Same thing here :(
I installed compiz fusion yesterday, worked great.

Today I got the updates, but the windows borders have disappeared. Launching Beryl instead of compiz doesn't work either.
And I got the same "ccp plugin not working" as you

I'm running feisty amd64 / nVidia graphics


Has anyone that had received the error above, fixed their issue?
I have an ATI x1600, and that same error occured. Lost all windows border and cube.
I tried formatting and reinstalling again last night and doing all the "fixes" that I could find, but nothing worked. I did see some new "fixes" in the forums this morning that I haven't tried. Hopefully those will work.
I then even tried reinstalling and getting Beryl to work last night, using both methods; fxgl and the open source driver, but nothing worked. 

Since Compiz Fusion is the way to go, I really would like to get it working again.

---

### Post by brt on 2007-07-08
> **firmwire said:**
> Has anyone that had received the error above, fixed their issue?

only by removing all compiz related packages and compiling everything from source.

---

### Post by firmwire on 2007-07-08
> **brt said:**
> only by removing all compiz related packages and compiling everything from source.

I think I tried that.  I saw yesterday you had run a couple of scripts and made some changes. But you still couldn't do some things. I'm assuming you got everything to work again.

If you have time, could you explain your proceedure?

---

### Post by Murador on 2007-07-08
I solved by removing compiz and installing the older versions of the packages from the archive under /var/cache/apt/archives

Now everything is working again.

I will obviously wait a couple of days before updating again

---

### Post by brt on 2007-07-08
[LIST]
[*]open synaptic do a search for compiz and remove all the packages related to compiz, e.g. also emerald etc.
[*]install the following packes:
[/LIST]

```
sudo apt-get install git-core autoconf automake intltool automake1.9 build-essential libtool libglib2.0-dev libxrender-dev libpng12-dev libxcomposite-dev libxfixes-dev libxdamage-dev libxrandr-dev libicecc-dev libsm-dev libstartup-notification0-dev libxinerama-dev fakeroot debhelper cdbs x11proto-gl-dev libgconf2-dev libgl1-mesa-dev python-pyrex python-all-dev libdbus-1-dev python-cairo-dev libglu1-mesa-dev libjpeg-dev libwnck-dev libglitz1-dev python-gtk2-dev libmetacity-dev libxslt1-dev libdbus-1-dev libdbus-glib-1-dev librsvg2-dev libdbus-glib-1-dev libmetacity-dev libwnck-dev libgnome-window-settings-dev libpango1.0-dev libgtk2.0-dev libgnome-desktop-dev libdbus-glib-1-dev 

```
next:
```
wget http://joeyjwc.x3fusion.com/software/ccf/ccf-1.0b.tgz
tar -xzf ccf-1.0b.tgz
cd ccf

```

now you have to edit the ccf file:
```
gedit ccf
```

this is what i have changed:
(i am using gnome, so i disabled kde, if you are using kde you may need to install additional *-dev packages)
```

SUPRESS="false"   # afaik, it will not work when this is set to true
#ITEMS="$ITEMS fusion/compizconfig/compizconfig-backend-kconfig"   # i commented this line out (using gnome)
COMPIZARGS="--prefix=/usr --enable-librsvg --disable-kde"
GENERICARGS="--prefix=/usr"

```

save & exit, now run ccf:
```
./ccf
```

this should fetch latest sources, build and install all the parts.

if there are errors you must try to figure out what went wrong (e.g. missing *.h file=*-dev package), correct the problem and run ccf again. it keeps a log of build items in a file called .built.

compare the content of this file with the folders in the ccf directory. 

change into each directory which is not listed in the .built file and run the commands:
(you may skip: compiz-scripts, viewport-switcher)
```
./autogen.sh --prefix=/usr
make
sudo make install
```

i had to do this for the folders 3d, gears, mswitch (./autogen.sh was not needed as there is already a Makefile)

once you are done without errors, copy the compiz-manager script:
```
sudo cp compiz-scripts/manager/compiz-manager /usr/local/bin
```

and add it to your session-startup.

fingercrossing, relogin and you should have compiz running again :)

good luck!

---

### Post by firmwire on 2007-07-08
Found this in a similiar topic:

> **blackdevil said:**
> Talked to Trevinho, and the problem is that the deb isnt updated in  the script. He is apparently working on it now and the fix should be out soon hopefully.

---

### Post by firmwire on 2007-07-08
Thanks brt for your instructions.

---

### Post by person68 on 2007-07-08
I had the "Couldn't activate plugin 'ccp'" problem but found a solution (for myself anyway).

I found that the whole problem stemmed from the libcompizconfig0 package being held back due to a conflict with compizconfig-plugin.  I resolved the conflict by marking the problematic package for removal in synaptic and then updated libcompizconfig0, and that fixed the problem for me.  

I don't know if this my problem was the same as everyone else's but I did get that error after updating today and I thought I would put this out there.

---

### Post by PuppyFromHell on 2007-07-08
I fixed my dependency problem but now I'm getting this error:
```
Preparing to replace compiz 1:0.3.6-1ubuntu13 (using .../compiz_1%3a0.5.1+git20070706~3v1ubuntu3_all.deb) ...
Unpacking replacement compiz ...
dpkg: compiz-gtk: dependency problems, but removing anyway as you request:
 compiz-gnome depends on compiz-gtk (= 1:0.3.6-1ubuntu13).
(Reading database ... 146045 files and directories currently installed.)
Removing compiz-gtk ...
(Reading database ... 146035 files and directories currently installed.)
Preparing to replace compiz-gnome 1:0.3.6-1ubuntu13 (using .../compiz-gnome_1%3a0.5.1+git20070706~3v1ubuntu3_i386.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070706~3v1ubuntu3_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
Selecting previously deselected package compiz-fusion-plugins-main.
Unpacking compiz-fusion-plugins-main (from .../compiz-fusion-plugins-main_0.0.1+git20070708~3v1ubuntu1_i386.deb) ...
Selecting previously deselected package compiz-fusion-plugins-extra.
Unpacking compiz-fusion-plugins-extra (from .../compiz-fusion-plugins-extra_0.0.1+git20070708~3v1ubuntu1_i386.deb) ...
Selecting previously deselected package libcompizconfig0.
Unpacking libcompizconfig0 (from .../libcompizconfig0_0.0.1+git20070707~3v1ubuntu1_i386.deb) ...
Selecting previously deselected package python-compizconfig.
Unpacking python-compizconfig (from .../python-compizconfig_0.0.1+git20070704~3v1ubuntu0_i386.deb) ...
Selecting previously deselected package compizconfig-settings-manager.
Unpacking compizconfig-settings-manager (from .../compizconfig-settings-manager_0.1.0+git20070708~3v1ubuntu2_i386.deb) ...
Selecting previously deselected package libcompizconfig-backend-gconf.
Unpacking libcompizconfig-backend-gconf (from .../libcompizconfig-backend-gconf_0.1+git20070708~3v1ubuntu1_i386.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070706~3v1ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by KyleBrandt on 2007-07-08
> **narehart said:**
> I'm having a problem in fusion.  Whenever I play a video be it in Mplayer or VLC the screen is translucent even when maximized.  I've played around with the settings manager trying to adjust this.  The only luck I've had though is if I check or uncheck the video plugin it will become opaque but as soon as I click something else it becomes trans again.  Anybody else have this problem???

Narehart: If you look earlier in this thread there is an answer, you need to change CompizConfig Settings Manager:General Options:Opacity Settings: Window  Opacities and then remove some of the first entries, I think If I remember correctly, Unknown is the key one to remove,  hope this helps!

---

### Post by SpanishFranks on 2007-07-08
after entering
```
 compiz --replace
```

I get the errors
```
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":1.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

```

I have a RADEON 9700 MOBILITY card, fglrx and xubuntu. XGL works fine and I have removed Beryl

I have seen other similar posts to this in this thread but no solutions

---

### Post by Survivalism on 2007-07-08
Okay.  It's installed and works like a dream (so far).  It was a hell of a lot easier than the Beryl install I did on Edgy.  Now I just have 2 questions...

1.  Is there a guide somewhere for this?  I want to know what all of these effects are and how to use them.

2.  Is it safe for me to let the updates take place?  When I ran Beryl in Edgy, if I ever updated, everything broke (and I was just left with the 2 pieces).  

I have only been using Ubuntu for about 8 months, so I'm not too familiar with everything (but that won't keep me from Compiz).

---

### Post by Vorian on 2007-07-08
> **Survivalism said:**
> 
2.  Is it safe for me to let the updates take place?  When I ran Beryl in Edgy, if I ever updated, everything broke (and I was just left with the 2 pieces).  

I have only been using Ubuntu for about 8 months, so I'm not too familiar with everything (but that won't keep me from Compiz).
1st, let me say OH - IO!  :) I love Ohio

2nd, It is very beta right now.  If you are using my repository, I test the packages before I push them out.  There will be a lot of updates as it is in heavy development right now.  As with any alpha software, expect it to break.  

Have Fun!

---

### Post by gimfred on 2007-07-09
Where you have a command using gedit, could you follow it with a similar command for Kubuntu? i.e, 
```
kdesu kwrite /etc/apt/sources.list
```

I notice you have written a separate option for the apt command in kubuntu but not the first editing command. It will help prevent others stumbling when they don't have gedit. ;)

---

### Post by Bardobrave on 2007-07-09
Hi.

I'm trying to get compiz in my fresh ubuntu 7.04 and, after following the guide I obtain no response from the system when try to run compiz --replace.

If I run it in terminal I obtain the following message:

Fatal: Failed Test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

It seems like some type of compatibility problem?

I've an ATIx800 Card with propietary drivers installed and enabled.
Any suggestions will be appreciated.

Thank you.

---

### Post by Bastaard on 2007-07-09
Thanks for the tutorial! Compiz fusion is up and running now for several days already, but I'm having one little, very annoying problem:

I was changing the key settings for "Rotate cube", I tried changing the Initiate function to a combination of mouse buttons only, which didn't work out. When I tried to change it back to Ctrl+Alt+Button1 but it didn't work! It said <Ctrl><Alt>Button1 but it actually still used the old binding, which shows again when I quit the Rotate Cube configuration and open it agian. I can actually change this binding to ANYTHING I want (Ctrl+Button1 and Alt+Button1, for example) except for  <Ctrl><Alt>Button1. Very annoying!

Does anyone know a solution to this? Is there a config file where I can change these keybindings? Thanks for the help!

---

### Post by mukiex on 2007-07-09
NVM it all I fixed my issue with the following :

Mini lack-of-window decoration fix :

mv ~/.compizconfig/ ~/.compizconfig_backup/ # Not sure if this is NEEDED
sudo apt-get remove compiz*

copy and paste the following into an executable script:
```

KEY=81836EBF; gpg --keyserver subkeys.pgp.net --recv $KEY && gpg --export --armor $KEY | sudo apt-key add -

sudo apt-get update

sudo apt-get remove compiz-core

sudo apt-get install compiz-gnome

sudo apt-get install compizconfig-settings-manager # compizconfig-backends-* ?!

sudo apt-get install compiz-fusion-*


```

And finally, run compiz --replace

If none of your options are sticking, delete the ~/.compizconfig folder and restart compiz again.

---

### Post by moisessalum on 2007-07-09
How can I add more desktops to the cube?
Because now I have 2 :confused:

Never mind, I found it on General Options>Desktop Size

---

### Post by EnderTheThird on 2007-07-09
I tried brt's instructions but with no luck.  Then I tried reinstalling from the repo and get this error now:

```

phil@phil-desktop:~$ compiz --replace
Adding plugin 3d (3d)
Adding plugin gears (gears)
Adding plugin mswitch (mswitch)
Adding plugin thumbnail (thumbnail)
Adding plugin imgjpeg (imgjpeg)
Adding plugin bench (bench)
Adding core settings (General Options)
Adding plugin cubereflex (cubereflex)
Adding plugin rotate (rotate)
Adding plugin atlantis (atlantis)
Adding plugin expo (expo)
Adding plugin put (put)
Adding plugin decoration (decoration)
Adding plugin annotate (annotate)
Adding plugin flash (flash)
Adding plugin water (water)
Adding plugin inotify (inotify)
Adding plugin tile (tile)
Adding plugin wallpaper (wallpaper)
Adding plugin widget (widget)
Adding plugin cube (cube)
Adding plugin gotovp (gotovp)
Adding plugin screensaver (screensaver)
Adding plugin scale (scale)
Adding plugin splash (splash)
Adding plugin mousegestures (mousegestures)
Adding plugin firepaint (firepaint)
Adding plugin colorfilter (colorfilter)
Adding plugin mblur (mblur)
Adding plugin animation (animation)
Adding plugin showdesktop (showdesktop)
Adding plugin wall (wall)
Adding plugin addhelper (addhelper)
Adding plugin snow (snow)
Adding plugin crashhandler (crashhandler)
Adding plugin kiosk (kiosk)
Adding plugin quickchange (quickchange)
Adding plugin screenshot (screenshot)
Adding plugin wobbly (wobbly)
Adding plugin video (video)
Adding plugin neg (neg)
Adding plugin glib (glib)
Adding plugin resize (resize)
Adding plugin switcher (switcher)
Adding plugin plane (plane)
Adding plugin fadedesktop (fadedesktop)
Adding plugin bs (bs)
Adding plugin opacify (opacify)
Adding plugin fs (fs)
Adding plugin group (group)
Adding plugin snap (snap)
Adding plugin scalefilter (scalefilter)
Adding plugin text (text)
Adding plugin zoom (zoom)
Adding plugin move (move)
Adding plugin png (png)
Adding plugin clone (clone)
Adding plugin blur (blur)
Adding plugin workarounds (workarounds)
Adding plugin fade (fade)
Adding plugin trailfocus (trailfocus)
Adding plugin reflex (reflex)
Adding plugin keybinding (keybinding)
Adding plugin vpswitch (vpswitch)
Adding plugin svg (svg)
Adding plugin cheatsheet (cheatsheet)
Adding plugin ring (ring)
Adding plugin extrawm (extrawm)
Adding plugin place (place)
Adding plugin fakeargb (fakeargb)
Adding plugin dbus (dbus)
Adding plugin minimize (minimize)
Adding plugin winrules (winrules)
Adding plugin scaleaddon (scaleaddon)
Adding plugin resizeinfo (resizeinfo)
Adding plugin regex (regex)
Backend     : gconf
Integration : true
Profile     : default
Initializing core options...done
/usr/bin/compiz: line 729: 16077 Segmentation fault      (core dumped) $*
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: "" found in configuration database is not a valid value for keybinding "panel_run_dialog"

```

I'm not sure if that's because of what I tried to do manually via brt's suggestion or not.  I'll admit I've always been a little spoiled with repos and haven't had to do much building from source.  How do I get rid of what I did while following brt's advice so I can just start from scratch?  Thanks in advance for the help!  It's really frustrating cause right now I can't even get Beryl working either (which is uninstalled now though, so that's not the problem).

---

### Post by l-fever on 2007-07-09
Great install guide! Everything is working great!

---

### Post by Vorian on 2007-07-09
> **EnderTheThird said:**
> I tried brt's instructions but with no luck.  Then I tried reinstalling from the repo and get this error now:

```

phil@phil-desktop:~$ compiz --replace
```

1st, you need to run the command via alt+F2
2nd, try this command:
```
compiz --replace -c emerald &
```
see if this works :)

---

### Post by EnderTheThird on 2007-07-09
Still no dice.

Another weird thing is that now when I install and run Beryl, I can't get any window decorations either.  I have all of the necessary changes made to my xorg.conf too, so I have no idea what's going on.  

*Sigh*, I should have waiting until Gutsy to mess with this!  This is my MythTV backend too, which complicates things.  Maybe I should move the master backend to my living room seeing as I don't mess with that one so much, heh.

---

### Post by DjBones on 2007-07-10
Compiz Fusion is soo awesome
puts beryl in the dirt ;]
thanks for writin this guide!

---

### Post by brt on 2007-07-10
> **EnderTheThird said:**
> 

 How do I get rid of what I did while following brt's advice so I can just start from scratch?  


1st remove all compiz related packages with synaptic, just do a search for compiz and remove everything related.

2nd:
go into each directory in your ccf folder, like 3d, bcop, ccsm, compiz, ....  and do a:
```

sudo make uninstall

```

(3rd) alternatively you could also (or additionally as it will also remove any zombiefiles from earlier installations)
```

find /usr/bin/ /usr/lib /usr/include/ /usr/share /usr/local/ -name "*compiz*" -exec rm {} \;
find /usr/bin/ /usr/lib /usr/include/ /usr/share /usr/local/ -name "*emerald*" -exec rm {} \;
find /usr/bin/ /usr/lib /usr/include/ /usr/share /usr/local/ -name "*ccsm*" -exec rm {} \;
find /usr/bin/ /usr/lib /usr/include/ /usr/share /usr/local/ -name "*bcop*" -exec rm {} \;
find /usr/bin/ /usr/lib /usr/include/ /usr/share /usr/local/ -name "*emerald*" -exec rm {} \;

```

i hope this helps ...

was your compilation using ccf successful and/or did you get any errors?

---

### Post by bimmerd00d on 2007-07-10
Maybe i missed it, but the option to have one big cube or individual ones for multiple desktops.

---

### Post by kyousukun on 2007-07-10
i got an error
```
xxxxx@ubuntu-desktop:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.
xxxxx@ubuntu-desktop:~$ 

```
what should i do? can anyone help me? im using ati radeon x550.

---

### Post by EnderTheThird on 2007-07-10
brt:

Thanks for the help!  I appreciate your effort with the mini-guide you posted, but it just wouldn't work for me.  And I'm sorry but I don't remember the errors I got during compilation (if any).  

[quote=kyousukun]
i got an error

```

xxxxx@ubuntu-desktop:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.
xxxxx@ubuntu-desktop:~$

```

what should i do? can anyone help me? im using ati radeon x550.[/quote]

I think that's because the ATI driver doesn't support Compiz/Beryl without using XGL.  Try to find a guide specifically for ATI systems if you're having trouble.  I'm new to Compiz Fusion though (Beryl user before), so I could use backup on this in case Compiz Fusion is supposed to automatically set up XGL for ATI systems or something crazy like that.  Sorry I couldn't be more help, but hopefully that can set you in the right direction.

---

### Post by Vorian on 2007-07-10
> **kyousukun said:**
> i got an error
```
xxxxx@ubuntu-desktop:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.
xxxxx@ubuntu-desktop:~$ 

```what should i do? can anyone help me? im using ati radeon x550.Your card is supported by the open driver.  If you are using the restricted driver, turn it off.  You should get it working then.

---

### Post by narehart on 2007-07-11
> **crimesaucer said:**
> I also fixed the transparent video like this: ccsm-->--General-->--Opacity Settings-->--Window Opacities-->-- then edit the string and take "Unkown" off of the list.

Thanks, I've been looking for weeks for a fix like this.  Maybe there should be a separate thread for this.

---

### Post by Lunatrix on 2007-07-11
hi, uhm when i did that BIG CODE (sudo apt-get install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf) 

I GOT


reading package listing. . .done
building dependency tree
reading state information. . . done
package compiz-gnome is not available, but is referred to another package.
this may mean that the package is missing,has been obsoleted, or
is only available from another source
however the following packages replaced it: 
    compiz-gtk compiz-plugins
E:package compiz-gnome has no installation candidate.

then the step with the ALT+F2 that didnt work for me neither, help please? thanks.

---

### Post by Vorian on 2007-07-11
> **Lunatrix said:**
> hi, uhm when i did that BIG CODE (sudo apt-get install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf) 

I GOT


reading package listing. . .done
building dependency tree
reading state information. . . done
package compiz-gnome is not available, but is referred to another package.
this may mean that the package is missing,has been obsoleted, or
is only available from another source
however the following packages replaced it: 
**     compiz-gtk compiz-plugins**
E:package compiz-gnome has no installation candidate.

then the step with the ALT+F2 that didnt work for me neither, help please? thanks.did you do this step?
```
sudo apt-get remove compiz-core desktop-effects
```

The package is available....

---

### Post by Lunatrix on 2007-07-11
i just did that step and it says that compiz-core and desktop-effects are removed already.

and what do you mean a package is availiable? can you get me a link?

---

### Post by Vorian on 2007-07-11
> **Lunatrix said:**
> i just did that step and it says that compiz-core and desktop-effects are removed already.

and what do you mean a package is availiable? can you get me a link?This is what I meant by the package is available....

```
vorian@MachineCrusade:~$ sudo apt-get install compiz-gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz-gnome is already the newest version.
compiz-gnome set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by Lunatrix on 2007-07-11
sp type what you typed in in a terminal? k

---

### Post by Lunatrix on 2007-07-11
im still getting the same error lol. do you think you can go on aim?

---

### Post by trinaryouroboros on 2007-07-11
> **Lunatrix said:**
> i just did that step and it says that compiz-core and desktop-effects are removed already.

and what do you mean a package is availiable? can you get me a link?

If you're using 64-bit Ubuntu, please check the line in your /etc/apt/sources.list where it says download.tuxfamily.org/3v1n0 eyecandy, replace eyecandy with eyecandy-64

Otherwise, you will not be able to find the proper package.

I feel like a broken record..

---

### Post by Vorian on 2007-07-11
follow the howto:

1. remove compiz-core and desktop-effects
2. add the sources to your sources.list
3. add the key
4. update your system
5."sudo apt-get install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf"

alt+f2 and enter "compiz replace"

---

### Post by Lunatrix on 2007-07-11
so u kan only get compiz with 64 bit?

---

### Post by Lunatrix on 2007-07-11
when you say add the key, where do i add the key?

---

### Post by andytof47 on 2007-07-11
ok all installed and I used remove for beryl etc


but after running alt-f2 it runs well for 10 -15 secs and theneverything just goes so slooooooooowwwwwwwww


can any one help?


It's certainly not this method because I tried the other day while beryl was still installed and got the same thing --- so kudos for the quick howto but I just need to get this sorted so I can start to use this properly


also is there a "compiz-manager" like a gui for the settings???? or is there a comprehensive command guide because from what i see on the youtube video there is heaps you can do with this new addition to compiz

cheers all

---

### Post by coder_cotton on 2007-07-12
> **andytof47 said:**
> ok all installed and I used remove for beryl etc


but after running alt-f2 it runs well for 10 -15 secs and theneverything just goes so slooooooooowwwwwwwww


can any one help?


It's certainly not this method because I tried the other day while beryl was still installed and got the same thing --- so kudos for the quick howto but I just need to get this sorted so I can start to use this properly


also is there a "compiz-manager" like a gui for the settings???? or is there a comprehensive command guide because from what i see on the youtube video there is heaps you can do with this new addition to compiz

cheers all

System -> Preferences -> CompizConfig Settings Manager

Does anyone know what setting gets the windows to stand off from the cube during rotation?

Now for the real post:

My compiz busted.  Like halfway.  For some reason, starting w/ the 7/9/07 (and the current 7/11/07) binaries from the repos in OP, my compiz has been slow, around half the framerates I was getting.  My monitor is 85Hz and it was pegged at that FPS, and now since the 7/9 update I'm getting 30-45 fps.  Its running fine... just sloooow.  It was running like silk before, maxed my refresh rate as stated before.

Alternatively, is there a way to revert to the older packages?  Are they saved somewhere?

---

### Post by LordMau on 2007-07-12
> **Vorian said:**
> Compiz Fusion is a very exciting new advancement in Desktop Effects.  Be that as it may, Compiz Fuzion is [SIZE=3][COLOR=Red]**NOT for Beginners**[/COLOR][/SIZE].  It is in development now, and is not stable. 

---snip---

 [B][I]add the folloing to your /etc/apt/sources.list
[/I][/B]```
sudo gedit /etc/apt/sources.list
```** for i386**```
# Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs.
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

```Packages at: [http://3v1n0.tuxfamily.org/dists/feisty/eyecandy]("http://3v1n0.tuxfamily.org/dists/feisty/eyecandy/index.html")

**for amd64**```
# Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs.
deb http://download.tuxfamily.org/3v1deb feisty eyecandy-amd64
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy-amd64

```Packages at: [http://3v1n0.tuxfamily.org/dists/feisty/eyecandy-amd64/](http://3v1n0.tuxfamily.org/dists/feisty/eyecandy-amd64/)

**Add the key **
```
gpg --keyserver subkeys.pgp.net --recv-keys 81836EBF
gpg --export --armor 81836EBF | sudo apt-key add -
```**Update your system**

---snip---


:lolflag:

just started to follow this guide word for word about 5 hours ago. bjorked my beryl install as all items are correct BUT the window decorator won't show. 

Checked this thread again and the above repos were just changed. Now all seems ok with beryl.

Could you add a note at this post that the repos did change? Thanks.

---

### Post by ltk5 on 2007-07-12
> **sanford42 said:**
> And I answered my own question!

need to start gconf-editor, 
select /apps/compiz/general/screen0/options/ and change the value of hsize from 1 to 4.

works like a charm :D

That worked for me too!! Thanks :D!
Now I can finally have my own 4-sided cube, and not just a triangle :D

---

### Post by Vorian on 2007-07-12
> **LordMau said:**
> 
Could you add a note at this post that the repos did change? Thanks.
If you want to use my repository, just visit the howto on my blog.  [http://vorian.org/?p=82](http://vorian.org/?p=82)

---

### Post by SkiesOfAzel on 2007-07-12
I also recommend Vorian's repo to anyone that has instability / performance problems, the builds he includes are usually more stable then Trevino's .
  Another way to improve performance for nvidia users is to start compiz with : ```
__GL_YIELD="NOTHING" compiz --replace -c emerald &
```
Dont try running this through alt+F2 though, it wont work. Instead open Gedit copy the command, save it to your home directory as compiz.sh and then press alt+f2 and type :
```
bash compiz.sh
``` You can also add bash compiz.sh to your session startup if this command does improve performance for you .

---

### Post by Sunflower1970 on 2007-07-12
Wow. Compiz-Fusion is pretty cool. Followed this guide last night, and have it running on my laptop. 

Thanks for the guide! :)

---

### Post by LordMau on 2007-07-12
> **Vorian said:**
> If you want to use my repository, just visit the howto on my blog.  [http://vorian.org/?p=82](http://vorian.org/?p=82)

To clarify, the guide on the 1st page as written when I started out did indicate the *vorian *repos as indicated in the blog. The files  on that repo were what borked the beryl install. During my search to fix this issue, upon returning to the first page of this thread hours later the repos were changed to trevino's, which solved my issues with beryl at least. I then went thru figuring out that beryl-manager can't be used as the launcher for fusion - although it can load the  WM it somehow interferes with the  window decorator.

Once I sort this out I'll try out those vorian repos again.

---

### Post by SkiesOfAzel on 2007-07-12
Your issues had probably nothing to do with the repo but with your version of beryl. Compiz fusion comes with a version of emerald that is incompatible with beryl 0.21. Trevino's repository also has beryl 0.30 which is compatible with latest emerald but it's pretty unstable for me at least. So to sum it up, if you want to use both beryl and compiz fusion with emerald , you are stuck with trevino's .

---

### Post by rne1223 on 2007-07-12
Hi, 

I don't really know what is going on here. Could someone please help me. This message appeared when I was trying to put the key. 


code
ubkeys.pgp.net --recv-keys 81836EBF
gpg: lock not made: link() failed: Function not implemented
gpg: can't lock `/home/rtellezrodriguez/.gnupg/secring.gpg'
gpg: DBG: oops, `/home/rtellezrodriguez/.gnupg/secring.gpg.lock' is not locked
gpg: keyblock resource `/home/rtellezrodriguez/.gnupg/secring.gpg': general error
gpg: lock not made: link() failed: Function not implemented
gpg: can't lock `/home/rtellezrodriguez/.gnupg/pubring.gpg'
gpg: DBG: oops, `/home/rtellezrodriguez/.gnupg/pubring.gpg.lock' is not locked
gpg: keyblock resource `/home/rtellezrodriguez/.gnupg/pubring.gpg': general error
gpg: requesting key 81836EBF from hkp server subkeys.pgp.net
gpg: no writable keyring found: eof
gpg: error reading `[stream]': general error
gpg: Total number processed: 0
rtellezrodriguez@ucmerced152-057:/mnt/local_user/UCMEng_lab01$

---

### Post by psyopper on 2007-07-13
I'm having the same dependency problem trying to install from trevino's repo's:

```

$ sudo apt-get install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz: Depends: compiz-plugins but it is not going to be installed
  compiz-fusion-plugins-extra: Depends: compiz-fusion-plugins-main but it is not going to be installed
  compiz-fusion-plugins-unofficial: Depends: compiz-fusion-plugins-main but it is not going to be installed
  compizconfig-settings-manager: Depends: compiz-plugins but it is not going to be installed
E: Broken packages

```

I have used these repos on a different machine with no problems. I did disable the repos on that system a while ago because I was happy with how things were running so they haven't been updated on that system in a while.

I'm helping a friend install on his uber-machine but the repos just aren't working. It is seeing the repos and finding compiz, it just seems that it can't find the rest of the dependancies...

Any ideas?

EDIT: nevermind... I included the above listed missing dependencies to the apt-get. Only to find out that I also needed libfuse2. Once I installed libfuse2 the install is currently downloading.

I think the above directions need to be updated maybe...

---

### Post by Choad on 2007-07-13
OH NO!

this guide has broken apt!

```
......<cut the beginning out>....
Selecting previously deselected package libcompizconfig-backend-gconf.
Unpacking libcompizconfig-backend-gconf (from .../libcompizconfig-backend-gconf_0.1+git20070710~3v1ubuntu0_i386.deb) ...
[B]Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070712~3v1ubuntu1_i386.deb
 /var/cache/apt/archives/compiz-fusion-plugins-unofficial_0.0.1+git20070711~3v1ubuntu0_i386.deb[/B]
E: Sub-process /usr/bin/dpkg returned an error code (1)
richard@richard-laptop:~$ **sudo apt-get install -f**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following packages were automatically installed and are no longer required:
  libgnome-compiz-manager0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  compiz-gnome
The following packages will be upgraded:
  compiz-gnome
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
23 not fully installed or removed.
Need to get 0B/165kB of archives.
After unpacking 1278kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 141034 files and directories currently installed.)
Preparing to replace compiz-gnome 1:0.3.6-1ubuntu13 (using .../compiz-gnome_1%3a0.5.1+git20070712~3v1ubuntu1_i386.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing [B]/var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070712~3v1ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070712~3v1ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]
richard@richard-laptop:~$ 

```

what do i do now!?

---

### Post by Choad on 2007-07-13
ok aparently apt wasnt broken... it let me remove everything i had added

```
sudo apt-get remove compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf

sudo apt-get install -f

sudo apt-get autoremove

```

all good again. phew

---

### Post by Endimion on 2007-07-13
I followed the tutorial step by step.. and my screen is "masked" or something like that, I included an image attachment... I was having problems with the windows decorations also.. but now is fixed... one for another. :(

EDIT: Never mind... I entered CompizConfig Settings Manager in the "General" Options in the "Display Settings" the Output was 800x600 ¬_¬ I checked "Detect Outputs" and now Compiz-Fusion is working great.

---

### Post by martijntje on 2007-07-13
For some reason the Compiz Fusion screensaver won't start automatically. I've checked the box 'Start Automatically' and changed the value for 'After' to 1.0000  After two minutes nothing has happened. When i place the mouse in the bottom-left corner and click it works great.  Anybody know how to fix this? I'm running feisty 64

---

### Post by yzx on 2007-07-14
I have clear install of kubuntu feisty and latest nvidia legacy drivers.
I tried to install it,passed only updating because it's too long. I get this when I tried to run it
```

root@yzny-desktop:/home/yzny# compiz –replace -c emerald &
[1] 6626
root@yzny-desktop:/home/yzny# Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

xset:  unable to open display ":0.0"
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

xdpyinfo:  unable to open display ":0.0".
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

xvinfo:  Unable to open display :0.0
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

xdpyinfo:  unable to open display ":0.0".
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

xdpyinfo:  unable to open display ":0.0".
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

xdpyinfo:  unable to open display ":0.0".
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

xdpyinfo:  unable to open display ":0.0".
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

xdpyinfo:  unable to open display ":0.0".
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

xdpyinfo:  unable to open display ":0.0".
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.
```
**Why?** Is there something to do for running it?
Edit: I suspect my xorg.conf It's here;
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"tr"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"ARM-1772"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Monitor		"ARM-1772"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by Beatbreaker on 2007-07-14
ok i don't know what's going on with my one - i had Compiz fusion working then i was convinced by someone to try to reinstall my Nvidia drivers which just about stuffed everything up. I've got the NVIDIA driver up and running again but now my Compiz Fusion is not working anymore. 

when i try compiz --replace i get this:

```
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

```

i'll post xorg.conf ar anyting else up by request - should i just reinstall my fusion & Emerald? will i loose all of the settings if i do that?

---

### Post by yzx on 2007-07-14
> ok i don't know what's going on with my one - i had Compiz fusion working then i was convinced by someone to try to reinstall my Nvidia drivers which just about stuffed everything up. I've got the NVIDIA driver up and running again but now my Compiz Fusion is not working anymore.

when i try compiz --replace i get this:

Code:

Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

i'll post xorg.conf ar anyting else up by request - should i just reinstall my fusion & Emerald? will i loose all of the settings if i do that?
**I got the same problem!**
I solved my first thread which I posted  few hours ago.
And I have that problem now.
The only difference is I have never run it on my computer :D
Please help
**[COLOR="Red"]Beatbreaker , what is your driver's version when you run it correctly?[/COLOR]**

---

### Post by Beatbreaker on 2007-07-14
> **yzx said:**
> **I got the same problem!**
I solved my first thread which I posted  few hours ago.
And I have that problem now.
The only difference is I have never run it on my computer :D
Please help
**[COLOR="Red"]Beatbreaker , what is your driver's version when you run it correctly?[/COLOR]**

FIXED: see [http://ubuntuforums.org/showthread.php?p=3018722#post3018722](http://ubuntuforums.org/showthread.php?p=3018722#post3018722) post 194

---

### Post by yzx on 2007-07-14
Thanks, I solved the problem too , but a bit different way
I removed the old drivers and  downloaded 9639 from nvidia's site. Then I installed it from 
ctrl+alt+f6
 
It runs correctly now. Thanks again

---

### Post by Quickdood on 2007-07-15
The repository is not working, does anyone know of a back up?

---

### Post by Pekay on 2007-07-15
Yeah the repository is working for me either when I update my side.
> Err [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg
  Could not connect to download.tuxfamily.org:80 (88.191.250.18). - connect (111 Connection refused)
Err [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Translation-en_GB
  Could not connect to download.tuxfamily.org:80 (88.191.250.18). - connect (111 Connection refused)
Fetched 192B in 5s (37B/s)                                
Failed to fetch [http://download.tuxfamily.org/3v1deb/dists/feisty/Release.gpg](http://download.tuxfamily.org/3v1deb/dists/feisty/Release.gpg)  Could not connect to download.tuxfamily.org:80 (88.191.250.18). - connect (111 Connection refused)
Failed to fetch [http://download.tuxfamily.org/3v1deb/dists/feisty/eyecandy/i18n/Translation-en_GB.bz2](http://download.tuxfamily.org/3v1deb/dists/feisty/eyecandy/i18n/Translation-en_GB.bz2)  Could not connect to download.tuxfamily.org:80 (88.191.250.18). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.


---

### Post by smithman89 on 2007-07-15
Ok, so here is another performance issue that i am having with Fusion.  If i go into expo mode, then afterwards go back to any of my workspaces, if i click and box select things on the desktop with my mouse, it starts lagging on the desktop if i make the selection box to big.  This continues for me only until i run a compiz --replace .  Anyone else having this problem?  Once again, other than that compiz is working flawlessly for me :D

---

### Post by Vorian on 2007-07-15
> **Quickdood said:**
> The repository is not working, does anyone know of a back up?I have one set up... [http://vorian.org/?p=82](http://vorian.org/?p=82)

---

### Post by PuppyFromHell on 2007-07-15
does anyone know anything about the water effect?  I clicked on it and nothing happened.

---

### Post by Vorian on 2007-07-15
> **PuppyFromHell said:**
> does anyone know anything about the water effect?  I clicked on it and nothing happened.
shift+f9 to turn it on/off
shift+f8 for the wiper

---

### Post by PuppyFromHell on 2007-07-15
I did that but it didn't look like anything happened.

---

### Post by lunaticitizen on 2007-07-15
Hello, thank you Vorian for your guide. I followed it and now it's running really smoothly :) Btw, could you tell me how to activate Focus Effect: Dodge? I'm using Japanese Edition of Ubuntu and the whole part of CompizConfig Settings Manager is also translated into Japanese, and I don't know the effect name in Japanese, either T-T In what section is it located? Window Management? What is the icon for the effect?

Thanks in advance :)

---

### Post by razeshkale on 2007-07-16
This is really helpful for Newbies of BERYL!!!

---

### Post by jcrow on 2007-07-16
I thought I'd share this info since it didn't come up in the search. After installing Compiz fusion, any time I would try to edit the configuration, the whole system would lock up. I had to change the backend configuration to flat file. I hope this helps someone.

---

### Post by smithman89 on 2007-07-16
> **lunaticitizen said:**
> Hello, thank you Vorian for your guide. I followed it and now it's running really smoothly :) Btw, could you tell me how to activate Focus Effect: Dodge? I'm using Japanese Edition of Ubuntu and the whole part of CompizConfig Settings Manager is also translated into Japanese, and I don't know the effect name in Japanese, either T-T In what section is it located? Window Management? What is the icon for the effect?

Thanks in advance :)

It is found in the Animations panel.  Click the button with the picture of a magic lamp.  Then go to the Focus Animation Tab, its the 3rd one.  Double click the item that says None, and change none to dodge in the dropdown menu.  Animation must be activated to be able to use it.

---

### Post by ianmidd on 2007-07-16
I have  a small issue with lag on one of my screens.

Here is my setup:

Feisty AMD64
GeForce 7300GT
Dual Acer AL1916W monitors - configured as 2 separate X sessions through nvidia-settings.

On Screen 0 I get a 2 second lag before any animation (menu opening, minimize, maximize).

I do not get the same lag on Screen 1.

Does anyone have any idea what could be causing the delay on only one screen?

I have checked my xorg.conf and both screen sections are identical except for what needs to be different.

---

### Post by el mariachi on 2007-07-16
I already activated 4 desktops but only 2 are active. Where should I activate de desktops in order to get a cube:confused:

---

### Post by butol1 on 2007-07-16
Hi i'm new to linux and i got compiz fusion installed and working.  I would like to know 

"Some quick tricks:
- Hold CTRL + ALT keys and with the left mouse button rotate the cube
- Super + E activates the Expo plugin
- Hold Super + Shift and with your mouse paint fire on your desktop
- Super + Shift + C will erase the fire paint
- Super + Tab activates the Ring Switcher plugin"

what is the "super" key      what button is that

---

### Post by Vorian on 2007-07-16
the "windows" key

---

### Post by butol1 on 2007-07-16
awsome  thx

---

### Post by jg1395 on 2007-07-16
this fixed my window decorations on my nvidia videocard

[http://forums.opencompositing.org/viewtopic.php?f=12&t=808](http://forums.opencompositing.org/viewtopic.php?f=12&t=808)

Run:

> 
Code: Select all
    sudo nvidia-xconfig --add-argb-glx-visuals -d 24

Then restart X

(White terminals diagnoses that as the problem.)

---

### Post by hardKNOXbz on 2007-07-16
omg.. thanks a lot.... i love this works very smoothly...

i couldnt get beryl installed due to my ati X1400 card, but who cares now.. i'm in love...

good bye windows vista partition

---

### Post by lunaticitizen on 2007-07-17
> **smithman89 said:**
> It is found in the Animations panel.  Click the button with the picture of a magic lamp.  Then go to the Focus Animation Tab, its the 3rd one.  Double click the item that says None, and change none to dodge in the dropdown menu.  Animation must be activated to be able to use it.

Aww thank you so much! :)

---

### Post by Gorgo13 on 2007-07-17
Hi there,

sorry if this has already been discussed, but I experience starnge issues with my newly installed compiz-fusion. Some of the System preferences do not simply appear with their GUI. To be clearer, it started with the Compiz-Fusion config manager. When I launched it System>Preferences>CompizConfig, then nothing appears. Other settings, like System>Administration>Language Support requires to log in admin (I have the login prompt appearing), but then, the screen stays grayed, and no language manager appears. After some times, and clicking around/hitting keys, I don't know exactly, the desktop is no more grayed and I can use it again. If I launch language config again, then everything's fine. But still no CompizConfig manager :(

Anyone aware of these issues?...

---

### Post by QwUo173Hy on 2007-07-17
Thank you. I've been giggling like an idiot for the last 30 minutes at all these effects. I'm very fond of expo and fire :)

---

### Post by makinasvp on 2007-07-17
I'm currently running Ubuntu Feisty Fawn with Beryl. Do I have to uninstall Beryl? Or can I just follow the instructions on the first page and install Compiz Fusion and run it?

---

### Post by BlahMan_of.Doom on 2007-07-17
You don't have to uninstall beryl although it is preferred that you do. Just make sure that it's not running. And make sure you have emerald installed. Then follow the guide.

And help me: I can only have 2 faces on my 'cube' :(

---

### Post by Gadren on 2007-07-17
> **BlahMan_of.Doom said:**
> And help me: I can only have 2 faces on my 'cube' :(

In the settings manager:
General Options > Desktop Size > Horizontal Virtual Size = 4

---

### Post by BlahMan_of.Doom on 2007-07-17
> **Gadren said:**
> In the settings manager:
General Options > Desktop Size > Horizontal Virtual Size = 4

Thanks :D

---

### Post by trinaryouroboros on 2007-07-17
> **el mariachi said:**
> I already activated 4 desktops but only 2 are active. Where should I activate de desktops in order to get a cube:confused:

If you open the Compiz Config Manager from System -> Preferences, you should see in the General section a tab for horizontal workspace, make sure it's set to 5 for a cube, though you can technically set yourself any shape, like a hexagon/pentagon/etc. - all the way up to 32 sides I believe.

:guitar:

---

### Post by ryoung on 2007-07-17
i just followed these installation instructions after the rotating cube effect started to fail in the original installation of 7.04.

The rotation effect now works with Compiz but the title bars went away.  I would prefer to have them back as I am used to moving windows with only the mouse.

Can someone tell me how to get the title bars back, please?

Thanks.

Ron

---

### Post by smithman89 on 2007-07-17
> **ryoung said:**
> i just followed these installation instructions after the rotating cube effect started to fail in the original installation of 7.04.

The rotation effect now works with Compiz but the title bars went away.  I would prefer to have them back as I am used to moving windows with only the mouse.

Can someone tell me how to get the title bars back, please?

Thanks.

Ron

Go to System>Preferences>Compiz Config Manager.  Enable window decorations.  Or install Emerald for more themes.

---

### Post by el mariachi on 2007-07-18
What command do I put in sessions to make compiz-fusion startup? it always starts normal compiz, even though I think I already uninstaled it:confused:*double checks*

---

### Post by nothing_pt on 2007-07-18
> **el mariachi said:**
> What command do I put in sessions to make compiz-fusion startup? it always starts normal compiz, even though I think I already uninstaled it:confused:*double checks*

 compiz --replace

---

### Post by trinaryouroboros on 2007-07-18
You folk might also want to put:

```
emerald --replace
```

In your Startup also, and make sure beryl and/or beryl manager are removed from startup - if you were using that before.

---

### Post by ChaOConnor on 2007-07-18
Do I need to use Emerald w/ Compiz Fusion?  What if I just install Compiz Fusion, would it then use Metacity and I wouldn't need Emerald?  What does Emerald do for me aside from "eye-candy" so to speak?  Thanks!

---

### Post by Azakus on 2007-07-18
> **ChaOConnor said:**
> Do I need to use Emerald w/ Compiz Fusion?  What if I just install Compiz Fusion, would it then use Metacity and I wouldn't need Emerald?  What does Emerald do for me aside from "eye-candy" so to speak?  Thanks!

You don't need emerald, but it looks way better than metacity when it comes to themes. Emerald can have transparent borders and drop shadows that much improve the look of windows compared to metacity.

---

### Post by the_lex on 2007-07-18
Hey all, sorry to noob it up, but:

I have compiz fusion installed, and I can open the settings manager GUI and all that. However, when i type: compiz --replace I get 

   alex@ThinkPad:~$ compiz --replace
   Fatal: Compiz can't be ran using VESA or VGA drivers.

I tried running:  sudo dpkg-reconfigure xserver-xorg  and selecting the i810 driver (I have an Intel 945GM), and OK'ing the rest of the config until it is done, but each time I try to run compiz or return to the xserver configuration, it claims I am running on vesa drivers again! 

Is there something I need to do to save the changes I make, or write them to the config file? (and yes I have tried restarting my session with ctrl+alt+backspace)

Thanks in advance

---

### Post by Azakus on 2007-07-18
You have to restart your xserver, not just your session to use the new driver choice. To do that, just hit Alt + F2, then run this
```
sudo /etc/init.d/gdm restart
```
This will restart your xserver to use the new driver.

---

### Post by broinkrist on 2007-07-18
hi. 

i am also quite new to the whole ubuntu platform, but got it working without problems. i only ran it for a few hours before updating it with compiz fusion. the install had some problems, but they were network related internally. once those were solved, compiz fusion ran as well as i suppose it's supposed to run except something is causing ubuntu to crash, alot.

this system crashing just completely freezes up the system and i need to hard reset each time. there is no pattern to when the system freezes, upon logging into ubuntu, when i'm watching a movie, when i'm opening up a program, when i'm typing posts like this...all the time, and it usually pretty frequent, as in ever 10 or so minutes.

i also tried viewing system logs to see if i could spot the problem, but don't know how to decifer what is written in the logs.
i also ran the memtest after reading around and found there were no problems with memory consistency.

any help would be appreciated.

dell dimension 5100.
P 4 3GHz
512MB RAM
ATI Radeon X600

i'll post up what the log files say the next time it crashes.

---

### Post by tarek on 2007-07-18
Hi, How do I remove compiz fusion and restore the original Desktop Effects?

Thanks
TK

---

### Post by makinasvp on 2007-07-19
> **trinaryouroboros said:**
> If you open the Compiz Config Manager from System -> Preferences, you should see in the General section a tab for horizontal workspace, make sure it's set to 5 for a cube, though you can technically set yourself any shape, like a hexagon/pentagon/etc. - all the way up to 32 sides I believe.

:guitar:

I don't know how much to thank you for helping me setup Compiz Fusion. You rock. Thank you for this wonderful write up and to the Beryl and Compiz team.
Although I am not a big fan of the name "Compiz Fusion", but it sure does wonders.

---

### Post by slowz3r on 2007-07-19
Install went fine, but instead of being a 4 sided cube, it appears just as a pane, front and back.  Also, The minimize, maximize, and exit buttons on the windows no longer appear, not a big deal, but extremely annoying, how can i get them back.  

Finally most important, what command to i put in the session preferences to get this to start on login?

sorry if these where answered before, i really didn't wanna read through the previous 36 pages of this thread, and the search turend up nothing for me :(

Thanks-slowz3r

---

### Post by tarek on 2007-07-19
> **slowz3r said:**
> Install went fine, but instead of being a 4 sided cube, it appears just as a pane, front and back.  Also, The minimize, maximize, and exit buttons on the windows no longer appear, not a big deal, but extremely annoying, how can i get them back.  

Finally most important, what command to i put in the session preferences to get this to start on login?

sorry if these where answered before, i really didn't wanna read through the previous 36 pages of this thread, and the search turend up nothing for me :(

Thanks-slowz3r

I can help you with the startup question. Go to System > Preferences > Sessions Add a new item and enter the command: compiz --replace

TK

---

### Post by QwUo173Hy on 2007-07-19
> **broinkrist said:**
> hi. 

... something is causing ubuntu to crash, alot.

...this system crashing just completely freezes up the system and i need to hard reset each time. there is no pattern to when the system freezes.


This has been an ongoing problem for the last few months and Ubuntu isn't the only distro with this problem.

There is a [thread here]("http://ubuntuforums.org/showthread.php?t=412125") discussing possible causes, but it's quite long so set some time aside for yourself. Get a pen and paper and make a list of things to try. I suggest you try the methods one at a time to ensure you know what actually fixed it for you.

[Here's]("http://ubuntuforums.org/showthread.php?t=405993&highlight=ubuntu+randomly") another thread discussing the same topic.

Regards,
Jarlath

---

### Post by bimmerd00d on 2007-07-19
Small bug on Compiz-Fusion.....on teh multi-output part of the Desktop Cube, one of the options is "On Big Cube"....should be "One big cube."   No big deal, but add the letter in there when you get bored devs.

---

### Post by slowz3r on 2007-07-19
> **tarek said:**
> I can help you with the startup question. Go to System > Preferences > Sessions Add a new item and enter the command: compiz --replace

TK

I reinstalled it, i fixed the Minimize, Max, and escape buttons, but i still odnt know why it wont show up as a cube

---

### Post by QwUo173Hy on 2007-07-19
Go to the General section and pick the Desktop Size tab. 

The Horizontal Virtual Size needs to be 4 for a cube.

<edit> Come to think of it, I never use more than 3 so I'm changing it. Expo looks great that way too. </edit>

---

### Post by slowz3r on 2007-07-19
thanks

---

### Post by DeathWarden on 2007-07-19
Ok, I am a bit of a newb but I followed the instructions for compiz fusion installation exactly. I type in 

compiz --replace

and get the response

Fatal: Failed test: Composite extension
Checks indicate that it's impossible to start compiz on your system.

Now my system should be able to handle it, I have ubuntu fiesty fawn 7.04 and followed the instructions on how to disable my integrated intel gpu and use my nvidia geforce fx 5200 256mb one. Am I doing something wrong? I have ubuntu dual booted with windows xp if that matters.

Thanks

---

### Post by Azakus on 2007-07-19
> **DeathWarden said:**
> Ok, I am a bit of a newb but I followed the instructions for compiz fusion installation exactly. I type in 

compiz --replace

and get the response

Fatal: Failed test: Composite extension
Checks indicate that it's impossible to start compiz on your system.

Now my system should be able to handle it, I have ubuntu fiesty fawn 7.04 and followed the instructions on how to disable my integrated intel gpu and use my nvidia geforce fx 5200 256mb one. Am I doing something wrong? I have ubuntu dual booted with windows xp if that matters.

Thanks

Run this in your terminal prompt
```
glxinfo | grep direct
```
If it says "direct rendering: No"
Then run this command.
```
sudo nvidia-xconfig --add-argb-glx-visuals
```
and then restart X.org
```
sudo /etc/init.d/gdm restart
```
That should enable Compiz Fusion to start.

---

### Post by Auax on 2007-07-19
I've followed all the instructions and installed compiz... but I don't get any effects at all.

I'm using Kubuntu 7.04 and have a Radeon X1100 card.

I get this error message: ```
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.
```

---

### Post by Azakus on 2007-07-19
> **Auax said:**
> I've followed all the instructions and installed compiz... but I don't get any effects at all.

I'm using Kubuntu 7.04 and have a Radeon X1100 card.

I get this error message: ```
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.
```

Oh, you have an ATI card. You need to install XGL to use an ATI card.
You need to follow this guide then.
[http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)

---

### Post by broinkrist on 2007-07-20
> **jarlath said:**
> This has been an ongoing problem for the last few months and Ubuntu isn't the only distro with this problem.

There is a [thread here]("http://ubuntuforums.org/showthread.php?t=412125") discussing possible causes, but it's quite long so set some time aside for yourself. Get a pen and paper and make a list of things to try. I suggest you try the methods one at a time to ensure you know what actually fixed it for you.

[Here's]("http://ubuntuforums.org/showthread.php?t=405993&highlight=ubuntu+randomly") another thread discussing the same topic.

Regards,
Jarlath

i read alot of threads about possible causes of crashing and the hardware issues that my dell 5100 may have with ubuntu and compiz fusion.

i removed compiz fusion and did the xgl update that many have said is needed to run the ati cards, although i didn't have a problem with compiz fusion running before. i selected the correct ati driver, and am logged into gnome with xgl...i'll keep everyone updated on if this fixed the crashing problem.

---

### Post by trinaryouroboros on 2007-07-20
> **makinasvp said:**
> I don't know how much to thank you for helping me setup Compiz Fusion. You rock. Thank you for this wonderful write up and to the Beryl and Compiz team.
Although I am not a big fan of the name "Compiz Fusion", but it sure does wonders.

Anytime, compadre

:popcorn:

---

### Post by Stolie on 2007-07-20
I have an interesting problem I have yet to find a solution to. I've posted on the Compiz forums, but figured I'd throw something out here too..

Since my install of Compiz, my super-key hasn't worked. I have the win-key mapped to be the super, and it works in Beryl (which sadly, has been discontinued...) and Metacity, but not in Compiz. It's almost as if Compiz nullifies it... As you all most likely know, a lot of things depend on the Super-Key to operate!

I feel lost without it! Help if you can!

Cheers,

---

### Post by Azakus on 2007-07-20
> **Stolie said:**
> I have an interesting problem I have yet to find a solution to. I've posted on the Compiz forums, but figured I'd throw something out here too..

Since my install of Compiz, my super-key hasn't worked. I have the win-key mapped to be the super, and it works in Beryl (which sadly, has been discontinued...) and Metacity, but not in Compiz. It's almost as if Compiz nullifies it... As you all most likely know, a lot of things depend on the Super-Key to operate!

I feel lost without it! Help if you can!

Cheers,

I had a similar problem where Compiz was overwriting my keyboard layout. I solved it by making a script run after Compiz started that reset my keyboard back to it's normal setting.
It looks like this
```
#!/bin/bash
sleep 5
setxkbmap -model pc105

```

---

### Post by Stolie on 2007-07-20
That did it! Thanks a million!

---

### Post by jw5801 on 2007-07-20
Help!!
```

jw5801@jw5801-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       jw5801@jw5801-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  compiz: Depends: compiz-decorator
  compiz-gnome: Depends: compiz-gtk (= 1:0.4.0-0ubuntu2~upure64) but it is not installed
E: Unmet dependencies. Try using -f.
jw5801@jw5801-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  compiz-gnome
The following packages will be upgraded:
  compiz-gnome
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
8 not fully installed or removed.
Need to get 0B/171kB of archives.
After unpacking 1339kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 124152 files and directories currently installed.)
Preparing to replace compiz-gnome 1:0.4.0-0ubuntu2~upure64 (using .../compiz-gnome_1%3a0.5.1+git20070716~jbs1_amd64.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070716~jbs1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070716~jbs1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  compiz: Depends: compiz-decorator
  compiz-gnome: Depends: compiz-gtk (= 1:0.4.0-0ubuntu2~upure64) but it is not installed
E: Unmet dependencies. Try using -f.
jw5801@jw5801-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  compiz-gnome
The following packages will be upgraded:
  compiz-gnome
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
8 not fully installed or removed.
Need to get 0B/171kB of archives.
After unpacking 1339kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 124152 files and directories currently installed.)
Preparing to replace compiz-gnome 1:0.4.0-0ubuntu2~upure64 (using .../compiz-gnome_1%3a0.5.1+git20070716~jbs1_amd64.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070716~jbs1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070716~jbs1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I tried removing all the packages that I installed at the start of this how-to, but all I got was the same error I got upon attempting upgrade.

---

### Post by jw5801 on 2007-07-20
Ok problem is solved. (I think it was caused by me stupidly not reading the first few lines of the how-to :oops:).
I needed to manually uninstall the bad packages (compiz-plugins & compiz-gnome) from /var/cache/apt/archives using "sudo dpkg -r" as apt-get remove didn't want to work.
Then I uninstalled all the compiz related packages, went back to the start and removed compiz-core like I was supposed to and now everything works teriffically! This should keep me amused fiddling with for a while.

---

### Post by trinaryouroboros on 2007-07-20
> **jw5801 said:**
> ```
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070716~jbs1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
```

You know, I have a similar problem with nvidia-glx now that occurred on a box I recovered using a backup tar. It's something to do with the /usr/lib sonames and, since I've toyed with that department before concerning 32-bit/64-bit, I was about to just wipe everything and grin and bear it, doing everything from scratch again.

I tried sudo dpkg -r, but, it gives me the same results - almost similar error, except it exits with error code 2.

Anyone have any ideas on this? If not, heck, I'll just wipe it tonight. I don't think my tar backup was properly restoring things, if you get my drift.

---

### Post by jw5801 on 2007-07-20
The way I did it was to cd to /var/cache/apt/archives/ and have a look around. I then put in the "sudo dpkg -r compiz-" and hit tab a couple of times to see what I could play with. Turns out I could remove "compiz-plugins" which is a package that shouldn't exist (it's meant to be integrated into compiz-gnome, but it's a dependancy of the old "compiz-core" and "desktop-effects" packages, which is why we're meant to remove them I think.) I'm pretty sure I couldn't remove compiz-gnome manually, but I could remove compiz-plugins, so try:
```
cd /var/cache/apt/archives/
sudo dpkg -r compiz-plugins
```
Otherwise yeah wiping it might help, but check that you actually have the library that's causing the error first :p I didn't, and I think my error was caused because there were two packages both trying to write the same library upon running "apt-get -f install."

---

### Post by boob11 on 2007-07-21
Thank you very much for a clean and a neat guide for installing.

---

### Post by weblordpepe on 2007-07-21
> **jw5801 said:**
> The way I did it was to cd to /var/cache/apt/archives/ and have a look around. I then put in the "sudo dpkg -r compiz-" and hit tab a couple of times to see what I could play with. Turns out I could remove "compiz-plugins" which is a package that shouldn't exist (it's meant to be integrated into compiz-gnome, but it's a dependancy of the old "compiz-core" and "desktop-effects" packages, which is why we're meant to remove them I think.) I'm pretty sure I couldn't remove compiz-gnome manually, but I could remove compiz-plugins, so try:
```
cd /var/cache/apt/archives/
sudo dpkg -r compiz-plugins
```
Otherwise yeah wiping it might help, but check that you actually have the library that's causing the error first :p I didn't, and I think my error was caused because there were two packages both trying to write the same library upon running "apt-get -f install."

Whewf! Saved my skin :) And my Ubuntu installation :D

---

### Post by Helmi on 2007-07-21
Hi,

i installed the packages from the first post with gnome. After reboot i get a non moving mouse - the desktop loads and all startup programs load, but the mouse doesn't work at all. 

any idea?

---

### Post by AMMOnium on 2007-07-21
Hi
I have a strange behaviour of menus with compiz-fusion and gnome (videocard is nvidia 6600 with latest drivers)
All the menus in gnome apps under gnome or kde session (everything is ok with kde apps and even kde apps under gnome session work as usual) appear ONLY if the window they belong to is out of focus. E.g. to access a menu on a window I have to make the window *inactive* and click on the menu bar while it is inactive. I tried different combinations of focus-related settings, disabled/enabled effects and animations but no results. :confused:

---

### Post by madc on 2007-07-21
working like a charm...as i was following the first post, i installed everything that was mentioned...when i have done that i've removed the "the beryl-manager" from the sessions menu and i've added two orders: "compiz --replace" and "emerald --replace"...and after rebooting i have fully functional compiz-fusion!:guitar:

btw, i still have installed beryl...

---

### Post by uglykigjoe on 2007-07-21
this is awesome..
easiest step i ever followed!!
thank you very much for this guide.
:popcorn:


::::::::::::::::::::::::::::::::::::::::::::::::::::::::
Feisty7.04
Vista Home Basic <-- Piece of crap!!
AMD Athlon 64X2
nVidia 7300Ge Force
2G RAM
--------------------------------------------------------

---

### Post by boob11 on 2007-07-22
Thank you for the nice easy guide.

---

### Post by lunamystry on 2007-07-22
The fire on the desktop thing does not work with me, but thats not my problem, I am using Kubuntu and adept notifier decided it wants it own window after I installed compiz, this is more irritating than a problem, i dont want that green little ball thinking it can do what it want on MY pardus. how do i put it on the panel that also disappered after the compiz, or should I ask how do i get the panel that disappeared with the compiz install, its an extra panel, my main panel (KDE disadvantage) is still there. 

To avoid any ambiguity i'll ask again: 
>> how do i close the adept notifier window, its too small to have its own window
>> How do i get my bottom panel back. it dissappered with the compiz installation. 

Thank you

---

### Post by Matty02 on 2007-07-22
I get this error when trying to run compiz. I am using Ubuntu Gutsy 7.10 Tribe 3


```
matt@matt-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Converting gconf plugin list: '' 
Checking for nVidia: present. 
Checking for Xgl: not present. 

***MEMORY-WARNING***: gtk-window-decorator[6471]: GSlice: g_thread_init() must be called before all other GLib functions; memory corruption due to late invocation of g_thread_init() has been detected; this program is likely to crash, leak or unexpectedly abort soon...
Segmentation fault (core dumped)

***MEMORY-WARNING***: metacity[6445]: GSlice: g_thread_init() must be called before all other GLib functions; memory corruption due to late invocation of g_thread_init() has been detected; this program is likely to crash, leak or unexpectedly abort soon...

```

---

### Post by jimbojimbo on 2007-07-22
Alright I'm having a bit of a problem here.  I followed the guide, didn't get any errors, but nothing happens.  Even once I run the "compiz --replace" nothing happens... no errors, no desktop effects... just nothing.  I can go into the compizconfig settings manager and change all the settings, but nothing seems to do anything at all.

The only problem I did run into while following the guide was a couple of 404 errors.  Could they be what is causing the problem?  If they are, is there anything I can do?  Just wait it out until hopefully the files come back up?

EDIT: The files that are giving me the 404 errors are from compiz.info... which apprently doesn't exist anymore (it fowards to a generic site).  Any ideas?

---

### Post by WinterWeaver on 2007-07-22
Compiz is Great... 1 problem though... I need a workaround for JRE6. Whenever I run a java app. I just get a grey window. There is a workaround for JRE5, but it does not work for me.

anyone know how I can fix this?

---

### Post by DaH-RaT on 2007-07-22
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070719~3v1ubuntu0_i386.deb
 /var/cache/apt/archives/compiz-fusion-plugins-unofficial_0.0.1+git20070717~3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

i did sudo apt-get install -f and got this now...

Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070719~3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

yay!!! the notorious  "no boredered programs" now woohoo!

---

### Post by misfitpierce on 2007-07-22
Not entriely sure... Sometimes when I run a java app on compiz on java 6 it just takes a bit to load. I throw it on second desktop and it can load there... But it happens rarely to me.

---

### Post by jw5801 on 2007-07-22
> **DaH-RaT said:**
> Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070719~3v1ubuntu0_i386.deb
 /var/cache/apt/archives/compiz-fusion-plugins-unofficial_0.0.1+git20070717~3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

i did sudo apt-get install -f and got this now...

Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070719~3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

yay!!! the notorious  "no boredered programs" now woohoo!

Scan back a page or 2 and you'll find where I had the same issue and solved it :p
Basically you need to go into /var/cache/apt/archives and manually dpkg -r the bad packages.

---

### Post by sparks0548 on 2007-07-22
Awesome guide.  Fusion runs so much better on my AMD-64 HP system than the latest release of Compiz.  With the repository and this guide I was up and running in about 10 minutes.  Now I just have to get Emerald working properly...LOL.

Thanks again!!

---

### Post by possessedskier on 2007-07-22
WinterWeaver - To show Java screens in Compiz:

Edit the environment file in the etc directory by typing the following in a terminal session:
gksudo gedit /etc/environment

Then add the following line below the path line:  
AWT_TOOLKIT=”MToolkit”

Save the file and exit. You may have to restart Linux, I don't remember.

---

### Post by WinterWeaver on 2007-07-22
> **possessedskier said:**
> WinterWeaver - To show Java screens in Compiz:

Edit the environment file in the etc directory by typing the following in a terminal session:
gksudo gedit /etc/environment

Then add the following line below the path line:  
AWT_TOOLKIT=”MToolkit”

Save the file and exit. You may have to restart Linux, I don't remember.

OMG dude I Love you!! That worked perfectly!! I have been looking everywhere forever, and could not find a solution...

Thanks a Million!!

^_^

WW

---

### Post by jjjhackkk on 2007-07-23
tnx for the info and vid.

i wanna try this!!hehe windOWS doesnt hav like this w/c is suck!haha by the way what system PC our using?
regards :)

---

### Post by jimbojimbo on 2007-07-23
Alright I'm having a bit of a problem here. I followed the guide, didn't get any errors, but nothing happens. Even once I run the "compiz --replace" nothing happens... no errors, no desktop effects... just nothing. I can go into the compizconfig settings manager and change all the settings, but nothing seems to do anything at all.

The only problem I did run into while following the guide was a couple of 404 errors. Could they be what is causing the problem? If they are, is there anything I can do? Just wait it out until hopefully the files come back up?

EDIT: The files that are giving me the 404 errors are from compiz.info... which apprently doesn't exist anymore (it fowards to a generic site). Any ideas?

Could the 404 errors be my problem or is it something else?

---

### Post by jw5801 on 2007-07-23
> **possessedskier said:**
> WinterWeaver - To show Java screens in Compiz:

Edit the environment file in the etc directory by typing the following in a terminal session:
gksudo gedit /etc/environment

Then add the following line below the path line:  
AWT_TOOLKIT=”MToolkit”

Save the file and exit. You may have to restart Linux, I don't remember.

I tried this method and now I get this error whenever I try to run a java app:
```
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b670a5cd385, pid=8465, tid=1076017472
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.6.0-b105 mixed mode)
# Problematic frame:
# C  [libc.so.6+0x2f385]  catgets+0x15
#
# An error report file with more information is saved as /tmp/hs_err_pid8465.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
/usr/bin/jarnal: line 17:  8465 Aborted                 (core dumped) java -Xmx192m -jar ${JARNALDIR}/jarnal.jar -g -t ${TEMPLATESDIR}/templates/default.jaj "$1" "$2" "$3" "$4" "$5"
```
I have sun java 6 installed as well as blackdown java (it has a plugin for 64-bit firefox) ```
jw5801@jw5801-laptop:~$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0-b105, mixed mode)
```
Any ideas? Having to run "metacity --replace" every time I want to use matlab or jarnal (which I use to annotate pdf lecture notes) at uni is starting to bug me.

---

### Post by abrichr on 2007-07-23
> **Miles800 said:**
> Anyone know how to get "Show windows from current workspace" under the window list preferences from gnome panel to work properly with Compiz running? At the moment it just shows the windows running on all workspaces, and I want it just to show the ones on my current workspace.

bump

---

### Post by bheremans on 2007-07-23
> **jw5801 said:**
> I tried this method and now I get this error whenever I try to run a java app:
```
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b670a5cd385, pid=8465, tid=1076017472
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.6.0-b105 mixed mode)
# Problematic frame:
# C  [libc.so.6+0x2f385]  catgets+0x15
#
# An error report file with more information is saved as /tmp/hs_err_pid8465.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
/usr/bin/jarnal: line 17:  8465 Aborted                 (core dumped) java -Xmx192m -jar ${JARNALDIR}/jarnal.jar -g -t ${TEMPLATESDIR}/templates/default.jaj "$1" "$2" "$3" "$4" "$5"
```
I have sun java 6 installed as well as blackdown java (it has a plugin for 64-bit firefox) ```
jw5801@jw5801-laptop:~$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0-b105, mixed mode)
```
Any ideas? Having to run "metacity --replace" every time I want to use matlab or jarnal (which I use to annotate pdf lecture notes) at uni is starting to bug me.

I think the problem is resolved in java 1.6.1

---

### Post by jw5801 on 2007-07-23
> **bheremans said:**
> I think the problem is resolved in java 1.6.1

Ok cool! Can you point me to where I can get it? The version I have appears to be the most up to date in the repositories. I found some stuff on the sun website, but there's no .deb, and the tar.gz had no makefile, or any of the other methods of installing that I'm familiar with, just some files and libraries which I have no idea where to put.

---

### Post by zolistir on 2007-07-23
Hi!

I installed compiz fusion following the howto posted here, but it doesn't really work. When I type "compiz --replace" it gives the following output:

Backend     : ini
Integration : true
Profile     : default
Adding plugin snap (snap)
Adding plugin trailfocus (trailfocus)
Adding plugin cubereflex (cubereflex)
Adding plugin wall (wall)
Adding plugin decoration (decoration)
Adding plugin blur (blur)
Adding plugin imgjpeg (imgjpeg)
Adding plugin rotate (rotate)
Adding plugin winrules (winrules)
Adding plugin notification (notification)
Adding plugin regex (regex)
Adding plugin zoom (zoom)
Adding plugin wallpaper (wallpaper)
Adding plugin text (text)
Adding plugin crashhandler (crashhandler)
Adding plugin fade (fade)
Adding plugin resizeinfo (resizeinfo)
Adding plugin bench (bench)
Adding plugin quickchange (quickchange)
Adding plugin screenshot (screenshot)
Adding plugin opacify (opacify)
Adding plugin colorfilter (colorfilter)
Adding plugin minimize (minimize)
Adding plugin mousegestures (mousegestures)
Adding plugin firepaint (firepaint)
Adding plugin svg (svg)
Adding plugin kiosk (kiosk)
Adding plugin 3d (3d)
Adding plugin vpswitch (vpswitch)
Adding plugin ring (ring)
Adding plugin png (png)
Adding plugin reflex (reflex)
Adding plugin wobbly (wobbly)
Adding plugin inotify (inotify)
Adding plugin showdesktop (showdesktop)
Adding plugin expo (expo)
Adding plugin neg (neg)
Adding plugin plane (plane)
Adding plugin cheatsheet (cheatsheet)
Adding plugin addhelper (addhelper)
Adding plugin fs (fs)
Adding plugin gotovp (gotovp)
Adding plugin keybinding (keybinding)
Adding plugin scaleaddon (scaleaddon)
Adding plugin switcher (switcher)
Adding plugin extrawm (extrawm)
Adding plugin glib (glib)
Adding plugin put (put)
Adding plugin place (place)
Adding plugin fadedesktop (fadedesktop)
Adding plugin water (water)
Adding plugin animation (animation)
Adding core settings (General Options)
Adding plugin scale (scale)
Adding plugin fakeargb (fakeargb)
Adding plugin splash (splash)
Adding plugin atlantis (atlantis)
Adding plugin flash (flash)
Adding plugin move (move)
Adding plugin cube (cube)
Adding plugin workarounds (workarounds)
Adding plugin video (video)
Adding plugin annotate (annotate)
Adding plugin thumbnail (thumbnail)
Adding plugin clone (clone)
Adding plugin scalefilter (scalefilter)
Adding plugin group (group)
Adding plugin snow (snow)
Adding plugin mblur (mblur)
Adding plugin tile (tile)
Adding plugin dbus (dbus)
Adding plugin screensaver (screensaver)
Adding plugin resize (resize)
Adding plugin widget (widget)
Initializing core options...done
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

---

### Post by AriciU on 2007-07-23
Update libdecoration from the Update Manager.

---

### Post by Bohlio on 2007-07-23
Whenever I try to start compiz, My screen flickers a little bit, and then I get this and compiz doesn't start up... :(
```
chad@chad-desktop:~$ compiz --replace
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display localhost:1.0
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: Log level 16: Unable to locate theme engine in module_path: "aurora",

```

---

### Post by weblordpepe on 2007-07-23
> **Bohlio said:**
> Whenever I try to start compiz, My screen flickers a little bit, and then I get this and compiz doesn't start up... :(
```
chad@chad-desktop:~$ compiz --replace
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display localhost:1.0
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: Log level 16: Unable to locate theme engine in module_path: "aurora",

```

I've been messing around with drivers heaps lately on my ATi card and I got this exact message. Are you on ATi? If so you gotta make sure that you got the right driver loaded.

I think the command glxinfo will let you show the OpenGL renderer in use. Make sure it is Mesa. Um. My best advice if you're on a ATi card (if ya on nVidia, forget my post :)) is to install the restricted driver, and remove it again. 

You need to not have the restricted driver running. While you can get compiz to work with the restricted ATi driver, its really buggy, half there, & not worth your trouble.

---

### Post by Bohlio on 2007-07-23
```
chad@chad-desktop:~$ glxinfo
name of display: localhost:1.0
Xlib:  extension "XFree86-DRI" missing on display "localhost:1.0".
display: localhost:1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X300/X550/X1050 Series
OpenGL version string: 1.2 (2.0.6334 (8.34.8))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
```
I dont see "mesa" in there anywhere... so that could be a problem...

I had the restricted driver running earlier with the older version of Compiz and it worked just fine, Only anything using OpenGL made it crash, which I could handle. I tried to get the latest ATI driver from the website, and that gave me a fuzzy and messed up XGL session, so I went back to an older version of FGLRX. So now you say that I need to get rid of fglrx completely? I thought you needed it for compiz?

---

### Post by saserlite on 2007-07-24
My experience may help someone...

[LIST=1]
[*]Installed compiz fusion as per original message
[*]Lost window decorations
[*]Resolved this issue by installing emerald
[*]Restarting machine meant that I had to manually restart compiz (by compiz --replace) (obviously because I hadn't set compiz to start automatically)
[*]Manually starting compiz caused my machine to **freeze**, although I could still move the mouse
[*]Removing compiz fusion: ```
sudo apt-get remove compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf
``` and then reinstalling: ```
sudo apt-get install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf
``` fixed the issue
[*]Added to start-up by System>Preferences>Sessions, and add ```
compiz --replace -c emerald &
```
[/LIST]

---

### Post by Arasa on 2007-07-24
Hi All,

Firstly, I want to thank all those people for putting this together and those that helping sort issues out.

My questions:
1. I have an extremely slow load from gdm screen to actual active desktop - similar to windoz.. so do I need to set default as metacity and then "compiz --replace" in sessions to solve this? Or is there something else? I have changed to flat-file config in backend.

2. At first I had a single workspace in cube mode which I rotated. I tried to initate a cube with 4 workspaces and now, I have one workspace again, cant rotate in space - nothing. I have enabled cube. I tried to change h-size to 4 and it just hung.. any ideas? I know compiz is around as I can wobble windows and opacity change. 

3. Shall I just sod all and reinstall?

---

### Post by Puppy fam on 2007-07-24
Yesterday my upgrade manager told me that the Compiz Fusion repository had been updated. I installed the updates and now have lost the ability to control the animation plug-in.

Any ideas? :confused:

---

### Post by BDNiner on 2007-07-24
> **Azakus said:**
> Run this in your terminal prompt
```
glxinfo | grep direct
```
If it says "direct rendering: No"
Then run this command.
```
sudo nvidia-xconfig --add-argb-glx-visuals
```
and then restart X.org
```
sudo /etc/init.d/gdm restart
```
That should enable Compiz Fusion to start.

What should i do if it says "direct rendring:yes" but i still can't run compiz fusion. I have an nvidia fx5200. The error mesage i receive is 

Fatal: Failed test: Composite extension
Checks indicate that it's impossible to start compiz on your system.

---

### Post by |2A|N on 2007-07-24
How do you get Compiz-Fusion to startup automatically in KDE version? Im still new to Linux about a week now so any details would be greatly appreciated thanks.

---

### Post by Andrew07 on 2007-07-24
Everything installs fine, but when I run compiz --replace I get the following in the terminal:

andrew@andrew-desktop:~$ compiz --replace
Fatal: Failed test: Composite extension
Checks indicate that it's impossible to start compiz on your system.

------------------

Both Compiz and Beryl have ran fine on this system before. Is there something that I just don't know about? This is with Kubuntu.. and a pretty much 100% clean install. The only thing installed so far is the updated nVidia drivers.

---

### Post by BDNiner on 2007-07-24
A reboot fixed all my issues, now i am going to get it working on startup. It took a while to dig through the various posts about it in the forum. 

Thank you everyone for your help.

---

### Post by deviousz on 2007-07-24
I'm getting this error too:

compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.


But I have an ATI on a T60 so the Nvidia fix obviously won't work for me.  

Anyone have the same issue?

---

### Post by Andrew07 on 2007-07-24
> **deviousz said:**
> I'm getting this error too:

compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.


But I have an ATI on a T60 so the Nvidia fix obviously won't work for me.  

Anyone have the same issue?

Well, it must not be a graphic card issue as we have two differant cards, but the same error.

---

### Post by Deadmode on 2007-07-25
Thank you for the help :) runs nice!

---

### Post by jdzitro on 2007-07-25
I get this same message in terminal too. 

WHAT MUST WE DO PEOPLE??

---

### Post by rahhot on 2007-07-25
If I change settings in compizconfig, nothing actually changes...

---

### Post by Arasa on 2007-07-25
I'm a bit of a newb but those of you wondering about the error in the terminal when doing replace... well it clearly says earlier in the guide that you should do that command in alt+f2 box.. I did that and my problems are totally different.. 

To recap:

PRESS ALT+F2, then type "compiz --replace -c emerald &"

NOT IN TERMINAL!!

My question is that I think I should add this command to sessions as suggested earlier and set metacity as default as compiz fusion seems to take an age to boot from gdm, someone said it's got some issues on startup.. Can anyone confirm or deny this? 

Also no-cube issues seem to be common, anyone have a definitive how-to on that? Inlcuding common things like flat-file backend and h-size set to 4 or 5?

---

### Post by rahhot on 2007-07-25
Also, it doesn't appear as a cube, but instead a single flat square with 2 sides.

---

### Post by n0xx on 2007-07-25
Please update the tutorial!

Nvidia users might want to start up compiz using the --indirect-rendering flag... like this:
[FONT="Courier New"]
compiz --replace --indirect-rendering [/FONT]

if you're starting compiz through a terminal you might want to add a '&' to the end of that line, like this:

[FONT="Courier New"]compiz --replace --indirect-rendering&[/FONT]

You may find that it boosts performance dramatically.

---

### Post by zeusconnection on 2007-07-25
Hi guys 
interesting post 
I fallow all process, everything install completely but when I get to the point of running"compiz --replace" by pressing alt + F2 nothing happen. I try it to the terminal I get this error message: 

Fatal: Failed test: non-power-of-two texture support Checks indicate that it's impossible to start compiz on your system.

Another thing I running this command " dpkg-query -s xserver-xorg-video-ati|grep Version"
to see my driver I get this : Version: 1:6.6.3-2ubuntu6
I don't know if it make compiz running on my comp

Any help please .......     Thanks in advance

---

### Post by oiler920 on 2007-07-25
Nice guide! Works perfectly on my machine! :)

---

### Post by Apex-jb on 2007-07-25
> **rahhot said:**
> Also, it doesn't appear as a cube, but instead a single flat square with 2 sides.Im getting this problem. Anyone tell us how to fix it?

---

### Post by £Xo7XEEQK38037M# on 2007-07-25
After walking through this guide I've got Compiz to work. However whenever I boot up I need to manually start compiz via the terminal, because the decorations are not showing (Alt+F2 doesn't work then). After that I need to press Alt+F2 kill the terminal and start compiz with compiz --replace and after that emerald --replace. 

I followed steps on getting compiz to start automatically, but that doesn't do it's job. I started Compiz and Emerald and saved that session. Since then I have to follow the above procedure to get it going again. Does anyone have any ideas on how to properly get Compiz and Emerald to start when booting up? 

Running latest compiz that came with the updates on Feisty.

---

### Post by Frak on 2007-07-25
> **Apex-jb said:**
> Im getting this problem. Anyone tell us how to fix it?
Stop Compiz, right click on your Workspace Switcher, increase it to 4 Spaces, then restart Compiz Fusion.

---

### Post by Apex-jb on 2007-07-25
> **Frak said:**
> Stop Compiz, right click on your Workspace Switcher, increase it to 4 Spaces, then restart Compiz Fusion.How do I stop it, what is the command?

---

### Post by Frak on 2007-07-25
Assuming your using Gnome, goto System->Administration->System Monitor then select Compiz and "End Process".

---

### Post by Apex-jb on 2007-07-25
Thanks, that fixed it.

---

### Post by The Exorcist on 2007-07-25
Hi, I've installed Compiz Fusion on my Kubuntu 7.04, using this guide - [http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml](http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml) 

All is fine until I enter 'compiz --replace' in the Run Command window...not much happens. The Konsole returns this - 'Compiz can't be ran using VESA or VGA divers' and putting in - ' lspci | grep -i vga' ...gives this - 01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)

In XP, this is using 93.71_forceware_winxp2k_international_whql.exe driver (just thought I'd throw that in :))

Position is now....I out of my depth. I've only been using Kubuntu a few weeks and I managed to set up everything else OK, so I thought I'd try this good stuff. But...having read some other stuff...I'm scared to Logoff or reboot, in case I can't get back in! 

Please advise best course of action now...even if that is how to remove Compiz Fusion. I'd much rather keep it and see it actually working, but I'd also like not to lose my present setup :P

Thanks...I'll wait around :)

---

### Post by jamesnewell on 2007-07-26
Hi.
I get the following error trying to install the compiz packages:

compiz-plugins:
 Depends: libfuse2 (>=2.6) but it is not installable

---

### Post by Azakus on 2007-07-26
You have to install the nvidia drivers for your system. In a terminal type ```
sudo aptitude install nvidia-glx
sudo nvidia-xconfig --add-argb-glx-visuals
```

---

### Post by upthelum on 2007-07-26
I followed these instructions but after "sudo apt-get upgrade" it said, " The following packages have been kept back, Linux-image-server".
So i ran "sudo apt-get install compiz compiz-kde compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-kconfig", which displayed a "Broken Package " message.

root@linuxhomepc:/# sudo apt-get install compiz compiz-kde compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-kconfig
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz: Depends: compiz-core but it is not going to be installed
          Depends: compiz-plugins but it is not going to be installed
  compiz-fusion-plugins-extra: Depends: compiz-core but it is not going to be installed
                               Depends: compiz-fusion-plugins-main but it is not going to be installed
                               Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is to be installed
                               Depends: libcairo2 (>= 1.4.0) but 1.0.4-0ubuntu1 is to be installed
                               Depends: libglib2.0-0 (>= 2.12.9) but 2.10.3-0ubuntu1 is to be installed
                               Depends: libpango1.0-0 (>= 1.16.2) but 1.12.3-0ubuntu3 is to be installed
                               Depends: libxcomposite1 (>= 1:0.3-1) but 1:0.2.2.2-0ubuntu2 is to be installed
                               Depends: libxfixes3 (>= 1:4.0.1) but 1:3.0.1.2-0ubuntu3 is to be installed
                               Depends: libxml2 (>= 2.6.27) but 2.6.24.dfsg-1ubuntu1 is to be installed
                               Depends: libxrandr2 (>= 2:1.2.0) but 1:1.1.0.2-0ubuntu4 is to be installed
                               Depends: libxslt1.1 (>= 1.1.20) but 1.1.15-1ubuntu1 is to be installed
  compiz-fusion-plugins-unofficial: Depends: compiz-core but it is not going to be installed
                                    Depends: compiz-fusion-plugins-main but it is not going to be installed
                                    Depends: libatk1.0-0 (>= 1.13.1) but 1.11.4-0ubuntu1 is to be installed
                                    Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is to be installed
                                    Depends: libcairo2 (>= 1.4.0) but 1.0.4-0ubuntu1 is to be installed
                                    Depends: libdbus-1-3 (>= 0.94) but it is not installable
                                    Depends: libdbus-glib-1-2 (>= 0.73) but 0.60-6ubuntu8.1 is to be installed
                                    Depends: libfontconfig1 (>= 2.4.0) but 2.3.2-1.1ubuntu12 is to be installed
                                    Depends: libgcc1 (>= 1:4.1.2) but 1:4.0.3-1ubuntu5 is to be installed
                                    Depends: libglib2.0-0 (>= 2.12.9) but 2.10.3-0ubuntu1 is to be installed
                                    Depends: libgtk2.0-0 (>= 2.10.3) but 2.8.20-0ubuntu1.1 is to be installed
                                    Depends: liborbit2 (>= 1:2.14.1) but 1:2.14.0-0ubuntu1 is to be installed
                                    Depends: libpango1.0-0 (>= 1.16.2) but 1.12.3-0ubuntu3 is to be installed
                                    Depends: libstdc++6 (>= 4.1.2) but 4.0.3-1ubuntu5 is to be installed
                                    Depends: libxcomposite1 (>= 1:0.3-1) but 1:0.2.2.2-0ubuntu2 is to be installed
                                    Depends: libxfixes3 (>= 1:4.0.1) but 1:3.0.1.2-0ubuntu3 is to be installed
                                    Depends: libxml2 (>= 2.6.27) but 2.6.24.dfsg-1ubuntu1 is to be installed
                                    Depends: libxrandr2 (>= 2:1.2.0) but 1:1.1.0.2-0ubuntu4 is to be installed
                                    Depends: libxslt1.1 (>= 1.1.20) but 1.1.15-1ubuntu1 is to be installed
  compiz-kde: Depends: compiz-core (= 1:0.5.1+git20070726~3v1ubuntu0) but it is not going to be installed
              Depends: kdelibs4c2a (>= 4:3.5.5-1) but 4:3.5.2-0ubuntu18.4 is to be installed
              Depends: kwin (>= 4:3.5.5-1) but 4:3.5.2-0ubuntu27 is to be installed
              Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is to be installed
              Depends: libdbus-1-3 (>= 0.94) but it is not installable
              Depends: libdbus-qt-1-1c2 (>= 0.62.git.20060814) but 0.60-6ubuntu8.1 is to be installed
              Depends: libdecoration0 but it is not going to be installed
              Depends: libgcc1 (>= 1:4.1.2) but 1:4.0.3-1ubuntu5 is to be installed
              Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but 3:3.3.6-1ubuntu6.2 is to be installed
              Depends: libstdc++6 (>= 4.1.2) but 4.0.3-1ubuntu5 is to be installed
              Depends: libxcomposite1 (>= 1:0.3-1) but 1:0.2.2.2-0ubuntu2 is to be installed
              Depends: libxfixes3 (>= 1:4.0.1) but 1:3.0.1.2-0ubuntu3 is to be installed
  compizconfig-settings-manager: Depends: compiz-plugins but it is not going to be installed
                                 Depends: python-compizconfig but it is not going to be installed
  libcompizconfig-backend-kconfig: Depends: kdelibs4c2a (>= 4:3.5.5-1) but 4:3.5.2-0ubuntu18.4 is to be installed
                                   Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is to be installed
                                   Depends: libcompizconfig0 but it is not going to be installed
                                   Depends: libfontconfig1 (>= 2.4.0) but 2.3.2-1.1ubuntu12 is to be installed
                                   Depends: libfreetype6 (>= 2.2) but 2.1.10-1ubuntu2.4 is to be installed
                                   Depends: libgcc1 (>= 1:4.1.2) but 1:4.0.3-1ubuntu5 is to be installed
                                   Depends: libpng12-0 (>= 1.2.13-4) but 1.2.8rel-5ubuntu0.2 is to be installed
                                   Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but 3:3.3.6-1ubuntu6.2 is to be installed
                                   Depends: libstdc++6 (>= 4.1.2) but 4.0.3-1ubuntu5 is to be installed
                                   Depends: libxcomposite1 (>= 1:0.3-1) but 1:0.2.2.2-0ubuntu2 is to be installed
                                   Depends: libxfixes3 (>= 1:4.0.1) but 1:3.0.1.2-0ubuntu3 is to be installed
                                   Depends: libxml2 (>= 2.6.27) but 2.6.24.dfsg-1ubuntu1 is to be installed
                                   Depends: libxrandr2 (>= 2:1.2.0) but 1:1.1.0.2-0ubuntu4 is to be installed
                                   Depends: libxslt1.1 (>= 1.1.20) but 1.1.15-1ubuntu1 is to be installed
E: Broken packages

I run xubuntu server with 1gb ram, asus board, onboard VIA K8M890 graphics and athlon 64, can anyone tell me how to repair plese, thanks...

---

### Post by jbysmith on 2007-07-26
Short version, pretty freaking sweet.  A lot of improvements since Beryl, seems a bit speedier too.  

Thanks for the how-to

---

### Post by Frak on 2007-07-26
> **upthelum said:**
> I followed these instructions but after "sudo apt-get upgrade" it said, " The following packages have been kept back, Linux-image-server".
So i ran "sudo apt-get install compiz compiz-kde compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-kconfig", which displayed a "Broken Package " message.

root@linuxhomepc:/# sudo apt-get install compiz compiz-kde compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-kconfig
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz: Depends: compiz-core but it is not going to be installed
          Depends: compiz-plugins but it is not going to be installed
  compiz-fusion-plugins-extra: Depends: compiz-core but it is not going to be installed
                               Depends: compiz-fusion-plugins-main but it is not going to be installed
                               Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is to be installed
                               Depends: libcairo2 (>= 1.4.0) but 1.0.4-0ubuntu1 is to be installed
                               Depends: libglib2.0-0 (>= 2.12.9) but 2.10.3-0ubuntu1 is to be installed
                               Depends: libpango1.0-0 (>= 1.16.2) but 1.12.3-0ubuntu3 is to be installed
                               Depends: libxcomposite1 (>= 1:0.3-1) but 1:0.2.2.2-0ubuntu2 is to be installed
                               Depends: libxfixes3 (>= 1:4.0.1) but 1:3.0.1.2-0ubuntu3 is to be installed
                               Depends: libxml2 (>= 2.6.27) but 2.6.24.dfsg-1ubuntu1 is to be installed
                               Depends: libxrandr2 (>= 2:1.2.0) but 1:1.1.0.2-0ubuntu4 is to be installed
                               Depends: libxslt1.1 (>= 1.1.20) but 1.1.15-1ubuntu1 is to be installed
  compiz-fusion-plugins-unofficial: Depends: compiz-core but it is not going to be installed
                                    Depends: compiz-fusion-plugins-main but it is not going to be installed
                                    Depends: libatk1.0-0 (>= 1.13.1) but 1.11.4-0ubuntu1 is to be installed
                                    Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is to be installed
                                    Depends: libcairo2 (>= 1.4.0) but 1.0.4-0ubuntu1 is to be installed
                                    Depends: libdbus-1-3 (>= 0.94) but it is not installable
                                    Depends: libdbus-glib-1-2 (>= 0.73) but 0.60-6ubuntu8.1 is to be installed
                                    Depends: libfontconfig1 (>= 2.4.0) but 2.3.2-1.1ubuntu12 is to be installed
                                    Depends: libgcc1 (>= 1:4.1.2) but 1:4.0.3-1ubuntu5 is to be installed
                                    Depends: libglib2.0-0 (>= 2.12.9) but 2.10.3-0ubuntu1 is to be installed
                                    Depends: libgtk2.0-0 (>= 2.10.3) but 2.8.20-0ubuntu1.1 is to be installed
                                    Depends: liborbit2 (>= 1:2.14.1) but 1:2.14.0-0ubuntu1 is to be installed
                                    Depends: libpango1.0-0 (>= 1.16.2) but 1.12.3-0ubuntu3 is to be installed
                                    Depends: libstdc++6 (>= 4.1.2) but 4.0.3-1ubuntu5 is to be installed
                                    Depends: libxcomposite1 (>= 1:0.3-1) but 1:0.2.2.2-0ubuntu2 is to be installed
                                    Depends: libxfixes3 (>= 1:4.0.1) but 1:3.0.1.2-0ubuntu3 is to be installed
                                    Depends: libxml2 (>= 2.6.27) but 2.6.24.dfsg-1ubuntu1 is to be installed
                                    Depends: libxrandr2 (>= 2:1.2.0) but 1:1.1.0.2-0ubuntu4 is to be installed
                                    Depends: libxslt1.1 (>= 1.1.20) but 1.1.15-1ubuntu1 is to be installed
  compiz-kde: Depends: compiz-core (= 1:0.5.1+git20070726~3v1ubuntu0) but it is not going to be installed
              Depends: kdelibs4c2a (>= 4:3.5.5-1) but 4:3.5.2-0ubuntu18.4 is to be installed
              Depends: kwin (>= 4:3.5.5-1) but 4:3.5.2-0ubuntu27 is to be installed
              Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is to be installed
              Depends: libdbus-1-3 (>= 0.94) but it is not installable
              Depends: libdbus-qt-1-1c2 (>= 0.62.git.20060814) but 0.60-6ubuntu8.1 is to be installed
              Depends: libdecoration0 but it is not going to be installed
              Depends: libgcc1 (>= 1:4.1.2) but 1:4.0.3-1ubuntu5 is to be installed
              Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but 3:3.3.6-1ubuntu6.2 is to be installed
              Depends: libstdc++6 (>= 4.1.2) but 4.0.3-1ubuntu5 is to be installed
              Depends: libxcomposite1 (>= 1:0.3-1) but 1:0.2.2.2-0ubuntu2 is to be installed
              Depends: libxfixes3 (>= 1:4.0.1) but 1:3.0.1.2-0ubuntu3 is to be installed
  compizconfig-settings-manager: Depends: compiz-plugins but it is not going to be installed
                                 Depends: python-compizconfig but it is not going to be installed
  libcompizconfig-backend-kconfig: Depends: kdelibs4c2a (>= 4:3.5.5-1) but 4:3.5.2-0ubuntu18.4 is to be installed
                                   Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is to be installed
                                   Depends: libcompizconfig0 but it is not going to be installed
                                   Depends: libfontconfig1 (>= 2.4.0) but 2.3.2-1.1ubuntu12 is to be installed
                                   Depends: libfreetype6 (>= 2.2) but 2.1.10-1ubuntu2.4 is to be installed
                                   Depends: libgcc1 (>= 1:4.1.2) but 1:4.0.3-1ubuntu5 is to be installed
                                   Depends: libpng12-0 (>= 1.2.13-4) but 1.2.8rel-5ubuntu0.2 is to be installed
                                   Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but 3:3.3.6-1ubuntu6.2 is to be installed
                                   Depends: libstdc++6 (>= 4.1.2) but 4.0.3-1ubuntu5 is to be installed
                                   Depends: libxcomposite1 (>= 1:0.3-1) but 1:0.2.2.2-0ubuntu2 is to be installed
                                   Depends: libxfixes3 (>= 1:4.0.1) but 1:3.0.1.2-0ubuntu3 is to be installed
                                   Depends: libxml2 (>= 2.6.27) but 2.6.24.dfsg-1ubuntu1 is to be installed
                                   Depends: libxrandr2 (>= 2:1.2.0) but 1:1.1.0.2-0ubuntu4 is to be installed
                                   Depends: libxslt1.1 (>= 1.1.20) but 1.1.15-1ubuntu1 is to be installed
E: Broken packages

I run xubuntu server with 1gb ram, asus board, onboard VIA K8M890 graphics and athlon 64, can anyone tell me how to repair plese, thanks...
sudo apt-get -f install
That will install all of your unmet dependencies.

---

### Post by crsd36 on 2007-07-27
I have 4 workspaces but still only have 2 sides to my cube.  I have seen how to change this before but can't seem to remember where :redface:.  Thanks in advance

---

### Post by Frak on 2007-07-27
> **crsd36 said:**
> I have 4 workspaces but still only have 2 sides to my cube.  I have seen how to change this before but can't seem to remember where :redface:.  Thanks in advance
One page back, last post.
EDIT
#428-#430

---

### Post by the yawner on 2007-07-27
vorian, i'm having issues on the latest update on your repository. running it on terminal gives me the following error:

/usr/bin/compiz.real (core) - Error: Can't load plugin 'ccp' because it is built for ABI version 20070707 and actual version is 20070708
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'

please advise. many thanks in advance =)

---

### Post by jimisdead on 2007-07-27
I'm running a new installation of Kubuntu with a nVidia 6800 go, and I didn't get any window decorations... it drove me nuts.

Until I realized that for some reason my screen was running in 16 bits... so I fixed that with a simple change in xorg.conf and voila... problem solved.

---

### Post by ashdezign on 2007-07-27
Hi I installed Compiz recently and ever since I have beryl-settings-simple indicating it has an update available, but when I go to update it I get the following error message:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be upgraded:
  beryl-settings-simple 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/33.5kB of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 285689 files and directories currently installed.)
Preparing to replace beryl-settings-simple 0.2.1+git20070318-0ubuntu2 (using .../beryl-settings-simple_0.3.0+git20070320~3v1ubuntu2_i386.deb) ...
Unpacking replacement beryl-settings-simple ...
dpkg: error processing /var/cache/apt/archives/beryl-settings-simple_0.3.0+git20070320~3v1ubuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/share/beryl-settings-simple/level2.Profile', which is also in package beryl-ubuntu
Errors were encountered while processing:
 /var/cache/apt/archives/beryl-settings-simple_0.3.0+git20070320~3v1ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
```My source list is as follows:
```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb http://ph.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://ph.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ph.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://ph.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ph.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://ph.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ph.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://ph.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ph.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://ph.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
deb http://blognux.free.fr/debian unstable main
deb http://elisa.fluendo.com/packages feisty main



#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt feisty main

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
deb http://archive.ubuntustudio.org/ubuntustudio feisty main
deb http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/ ./

# Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs.
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```When I remove Trevino's Repositories (actually I just comment them out) the problem goes away. 

```
# Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs.
# deb http://download.tuxfamily.org/3v1deb feisty eyecandy
# deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```By goes away I mean that ubuntu no longer says it needs to update that package and says the system is up to date. It does not fix the problem of installing the update.

Is the update even needed? I already have beryl simple settings manager installed.

If it is needed how can I update it?

I am still quite the noobie and can't help feeling I am missing something really obvious.

Many thanks in advance for any help you can give me!

---

### Post by MrCrussell on 2007-07-27
I'm getting the same thing here, also, no window decorations of any sort which renders my desktop unusable - no flaming text, no wobbly windows, no fish in the cube *sigh*

... help ...

> **the yawner said:**
> vorian, i'm having issues on the latest update on your repository. running it on terminal gives me the following error:

/usr/bin/compiz.real (core) - Error: Can't load plugin 'ccp' because it is built for ABI version 20070707 and actual version is 20070708
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'

please advise. many thanks in advance =)

---

### Post by MissDjax on 2007-07-27
> **deviousz said:**
> I'm getting this error too:

compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

Anyone have the same issue?

same error here :(
ATI x800pro

---

### Post by MrCrussell on 2007-07-27
missdjax - are you sure you have the environment set up properly? If I try to run compiz from a standard Gnome session I get the same error. Follow the instructions here : [http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314) and it should be ok ...

In other news, I'm getting "Can't load ccp built for ABI version 20070707, actual version is 20070708" - when I try to access Vorian's repo it looks ... utterly broken!!!! wonder if it's the root cause of my probs...

---

### Post by crsd36 on 2007-07-27
> **Frak said:**
> One page back, last post.
EDIT
#428-#430

I followed that and am still having issues..

---

### Post by possessedskier on 2007-07-27
The last compiz fusion update from Travino's repository appears to be broken.  When attempting to start after the latest update:

compiz --replace -c emerald &

I get this result:

/usr/bin/compiz.real (core) - Error: Can't load plugin 'ccp' because it is built for ABI version 20070707 and actual version is 20070708
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'

---

### Post by Raineer on 2007-07-27
> **crsd36 said:**
> I followed that and am still having issues..

Away from my system at the moment so this is from memory but...

Try opening the Compiz settings from the Preferences menu. The top selection in the Compiz Fusion menu should be something like "General settings"

This menu should now have tabs across the top, I think the 3rd tab or so says something about Displays or Workspaces... The top setting should be "Desktop Horizontal Width", which is likely set to the default of 2 and needs to be 4.

Sorry I can't be more specific, but look around for the Horizontal Width and you should find it, it may even say "Virtual Width" or something like that.

---

### Post by Raineer on 2007-07-27
> **possessedskier said:**
> The last compiz fusion update from Travino's repository appears to be broken.  When attempting to start after the latest update:

compiz --replace -c emerald &

I get this result:

/usr/bin/compiz.real (core) - Error: Can't load plugin 'ccp' because it is built for ABI version 20070707 and actual version is 20070708
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'

Yeah I'm not sure but there might be a problem with his repository, I just freshly loaded a machine and Fusion just refuses to work properly, lots of strange things that didn't happen on my other box I setup months ago.

---

### Post by ashdezign on 2007-07-27
Compiz seems to work fine... mostly, but it is obviously still unstable as it crashes some times, such as when I enable the cheat sheet or wallpaper. And the water effect seems to be limited to rain, the title wave does not work. The Atlantis plugin works nicely though :) .

Also when  I installed compiz-fusion Beryl seems to also have upgraded which gave me some new features when i run beryl, (though unstable ones) and the beryl splash screen has changed and now says Beryl SVN

All in all Beryl is still much more stable but I am looking forward to when Compiz-Fusion is ready as it seems to bring some definite improvements!

---

### Post by Frak on 2007-07-27
> **ashdezign said:**
> All in all Beryl is still much more stable but I am looking forward to when Compiz-Fusion is ready as it seems to bring some definite improvements!

+1
Same here, I don't like Compiz Fusion ATM, it broke my machine many times.

---

### Post by LordRajaGoombaI on 2007-07-28
I have an ATI 9550 with 256mb RAM:

I tried the walkthrough then realised I had to install XGL and it wasn't really helpful, it still played up and I couldn't get it to work.

I logged out and back into gnome session, and ran ```
metacity --replace
```

Unticked the boxes I made for emerald and compiz in the sessions box.

Logged out and back in to XGL session, and ran the metacity --replace code in that.  That had me all back to square one.

Logged out and back into XGL.  It was running metacity (because I unticked the compiz and emerald boxes.

Then I ran the 
```
sudo apt-get remove compiz-core desktop-effects
```

again.

Then I reran the key as stated.

Then sudo'ed update and upgrade.

Reran the ```
sudo apt-get install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf
``` code.

Ran the Alt-f2 box with the ```
compiz –replace
```

Obviously to those with more Ubuntu experience than me, that left my windows without any proper title bars, so I ran in the Alt-f2 box ```
emerald --replace
```.

That fixed my window borders up.

Now I saw everything was working, reticked the boxes I created in sessions that create the compiz --replace and emerald --replace codes at login automatically.

Logged out and back in, and we were all fixed up.

The emerald thing is a little finicky, I've found, when you want to replace your theme, but I do it before I logout and then next time on the computer, my new theme works.  Crap workaround, but that's okay, I do turn the computer on and off, because my use of it is spasmodic.

Hope this helps some peoples. I'm not quite a newb after just over a year + a half, but I'm certainly no expert.

---

### Post by weblordpepe on 2007-07-28
My compiz fusion is broken again since the last update. Dunno what to do now.

---

### Post by the yawner on 2007-07-28
I suppose we'll just have to wait :(

---

### Post by kekojeep on 2007-07-28
> **the yawner said:**
> I suppose we'll just have to wait :(

Waiting here too.. same problem with "ccp plugin".

[ ]'s

---

### Post by crsd36 on 2007-07-28
> **Raineer said:**
> Away from my system at the moment so this is from memory but...

Try opening the Compiz settings from the Preferences menu. The top selection in the Compiz Fusion menu should be something like "General settings"

This menu should now have tabs across the top, I think the 3rd tab or so says something about Displays or Workspaces... The top setting should be "Desktop Horizontal Width", which is likely set to the default of 2 and needs to be 4.

Sorry I can't be more specific, but look around for the Horizontal Width and you should find it, it may even say "Virtual Width" or something like that.


Aaaah, that was it!  Thank you very much!

---

### Post by martijntje on 2007-07-28
Something broke. I don't know how long it has been, but i can no longer access the 'Animations' options. The plugin is activated, but if i click the button nothing happens. I can access other plugins' configuration just fine.

---

### Post by xster on 2007-07-28
I did everything as the guide describes. Then when I do compiz --replace from alt-f2. no error message but nothing happens. There is also no compiz process that starts after running compiz --replace. Running emerald --replace creates a emerald process but still with no visual effects. Tried restarting and nothing happens. Everything installed with no errors, what's wrong??

---

### Post by eks on 2007-07-28
> **jimisdead said:**
> I'm running a new installation of Kubuntu with a nVidia 6800 go, and I didn't get any window decorations... it drove me nuts.

Until I realized that for some reason my screen was running in 16 bits... so I fixed that with a simple change in xorg.conf and voila... problem solved.

DUDE!! THANKS A LOT!!!!!! It worked!!! \\:D/

I was trying everything to get the decorators to work until I found your comment on this thread. I tried manually to change to 32bits, but my board would not work with that (because of dual monitors?). On the nvidia-settings the highest color depth it could accept was 24, but it worked nevertheless. :D


eks
PS: just one big sign for future travelers:

[COLOR="DarkRed"]
[CENTER]**[SIZE="4"]IF YOU HAVE PROBLEM WITH DECORATORS TRY CHANGING MONITOR COLOR DEPTH[/SIZE]**[/CENTER][/COLOR]

---

### Post by frazle on 2007-07-28
I tried ALT+F2 to run compiz and it does nothing, but when I run it in terminal it flags this error:
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

Have looked around but cant find a definitive solution to my problem; i'm using ATI x1950 crossfire

cheers in advance for any help.

---

### Post by ashdezign on 2007-07-28
I notice significantly higher cpu usage when i manually rotate the cube in compiz compared to beryl. Anyone else notice this?

Beryl on rotate: cpu usage 8-22%

Compiz on rotate (with Atlantis and reflection plugins turned off) : cpu usage 75-86%

Also anyone else miss the title wave water effect on grab/ungrab windows?

---

### Post by Frak on 2007-07-28
> **ashdezign said:**
> I notice significantly higher cpu usage when i manually rotate the cube in compiz compared to beryl. Anyone else notice this?

Beryl on rotate: cpu usage 8-22%

Compiz on rotate (with Atlantis and reflection plugins turned off) : cpu usage 75-86%

Also anyone else miss the title wave water effect on grab/ungrab windows?
I noticed it, and I also miss the the tittle wave effect, that is why I'm still using Beryl, its actually more stable.
EDIT
My cube is jumpy, which it isn't in Beryl.

---

### Post by Kayne on 2007-07-29
Sorry, if this was already posted, but any info about the new plugins that came out recently?
I'm especially interested in Shift Switcher, it provides a Flip3d like feature like in Vista and a Cover Flow feature, which will be used in Leopard.

[[IMG]http://img337.imageshack.us/img337/9771/flib3das7.th.png[/IMG]](http://img337.imageshack.us/my.php?image=flib3das7.png) [[IMG]http://img337.imageshack.us/img337/9369/flib4dsmalluu6.th.png[/IMG]](http://img337.imageshack.us/my.php?image=flib4dsmalluu6.png) [[IMG]http://img337.imageshack.us/img337/6999/flib5dsmallhn3.th.png[/IMG]](http://img337.imageshack.us/my.php?image=flib5dsmallhn3.png)

More info here:
[http://smspillaz.wordpress.com/2007/07/25/compiz-fusion-community-news-edition-9-for-july-23-2007-breaking-news-forums-posts-go-down-by-half-due-to-a-lack-of-posts-asking-for-aquariums/](http://smspillaz.wordpress.com/2007/07/25/compiz-fusion-community-news-edition-9-for-july-23-2007-breaking-news-forums-posts-go-down-by-half-due-to-a-lack-of-posts-asking-for-aquariums/)

Unfortunately I don't know how to include new plugins...

---

### Post by weblordpepe on 2007-07-29
Hah!!! Awesome! I cannot wait to do flip 3D so I can give one final :P to vista.

---

### Post by ashdezign on 2007-07-29
After further testing it seems Compiz Fusion uses whatever it can of the CPU.

The load on the CPU remains the same (%) regardless of how I scale the frequency.

I am running a Dell Inspiron E1505 with a dual core cpu each at 1.66GHz. When I scale down to 1 GHz Copmiz makes the same demand on the CPU in percentage terms as it does if I scale at 1.33 GHz or 1.66GHz.

Don't know if that's a good thing or bad: Compiz Fusion seems to make the most of whatever is available.

Another test.

Both CPU's scaled to 1.66GHz

VLC playing movie
Firefox (10 tabs opened), Evolution, Gaim, Amorak(updating music libary), Azureus (downloading/uploading) Liferea, 2 file browser windows, Open Office (with document open) and Adobe Reader (with document open) all open,

Running gdesklets Ram monitor and Screenlets CPU monitor

Running Avant Window Manager

Running Compiz Fusion with Emerald

various applets running in various panels

CPU fluctuating between 25 and 40, Ram usage at 782 M (I have 2 Gigs on this machine)

Manual cube rotate by clicking button 1 and 2 on mouse and dragging the screen spikes CPU up to 99% but no slow down on anything. 

Movie still plays without any discernible loss of quality in video or audio even while transparency settings makes video semi- transparent.

Bottom line I cant complain. With Windows XP on this machine I could never have done so much using so little of my systems resources.

Actually that I do have one complaint/observation. Is it actually possible to use all 2 Gigs of my Ram? I have yet to see usage go over 800M since I installed Ubuntu!

---

### Post by weblordpepe on 2007-07-29
Yeah I havent maxxed out mine either.
I tell ya what...Having an nVidia card is starting to become a must for me. I think I'll be ditching this ATI powered laptop.

---

### Post by johannes_ on 2007-07-29
Hi,

I'm getting the following and my window-decorator disappears :-/

johannes@antares:~$ compiz --replace
compiz (core) - Warn: Unable to parse XML metadata from file "core.xml"
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

My graphics accelerator is an Intel GMA 945. Any suggestions? I already enabled the window-decorator plugin with emerald (the packages emerald and emerald-themes are already installed) and the part from my xorg.conf file that's maybe important:

Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option 		"AddARGBGLXVisuals" "True"
EndSection

I'm also not sure if the xlg-server starts, but I have installed the package (and I'm not sure if I really need it) ...

best regards,
Johannes

---

### Post by kevmaster on 2007-07-29
I've written another another article on [How To Enable compiz-fusion on Ubunuty Feisty]("http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/") with a lot of screen shots. I hope it might help someone.

---

### Post by the yawner on 2007-07-29
> **Kayne said:**
> Sorry, if this was already posted, but any info about the new plugins that came out recently?
I'm especially interested in Shift Switcher, it provides a Flip3d like feature like in Vista and a Cover Flow feature, which will be used in Leopard.

[[IMG]http://img337.imageshack.us/img337/9771/flib3das7.th.png[/IMG]](http://img337.imageshack.us/my.php?image=flib3das7.png) [[IMG]http://img337.imageshack.us/img337/9369/flib4dsmalluu6.th.png[/IMG]](http://img337.imageshack.us/my.php?image=flib4dsmalluu6.png) [[IMG]http://img337.imageshack.us/img337/6999/flib5dsmallhn3.th.png[/IMG]](http://img337.imageshack.us/my.php?image=flib5dsmallhn3.png)

More info here:
[http://smspillaz.wordpress.com/2007/07/25/compiz-fusion-community-news-edition-9-for-july-23-2007-breaking-news-forums-posts-go-down-by-half-due-to-a-lack-of-posts-asking-for-aquariums/](http://smspillaz.wordpress.com/2007/07/25/compiz-fusion-community-news-edition-9-for-july-23-2007-breaking-news-forums-posts-go-down-by-half-due-to-a-lack-of-posts-asking-for-aquariums/)

Unfortunately I don't know how to include new plugins...

That's the exact reason why I updated my Compiz Fusion. Got the plugin allright, but then ccp plugin wont work due to invalid version(?). Since I made the update 2 days ago, I've received 2 more additional updates. But none fixed the problem.. So, still waiting. Heh.

---

### Post by £Xo7XEEQK38037M# on 2007-07-29
> **tneo said:**
> After walking through this guide I've got Compiz to work. However whenever I boot up I need to manually start compiz via the terminal, because the decorations are not showing (Alt+F2 doesn't work then). After that I need to press Alt+F2 kill the terminal and start compiz with compiz --replace and after that emerald --replace. 

I followed steps on getting compiz to start automatically, but that doesn't do it's job. I started Compiz and Emerald and saved that session. Since then I have to follow the above procedure to get it going again. Does anyone have any ideas on how to properly get Compiz and Emerald to start when booting up? 

Running latest compiz that came with the updates on Feisty.Can anyone help on this, I can't find any solutions for this so far...

---

### Post by the yawner on 2007-07-29
> *I followed steps on getting compiz to start automatically, but that doesn't do it's job.* I started Compiz and Emerald and saved that session. Since then I have to follow the above procedure to get it going again. Does anyone have any ideas on how to properly get Compiz and Emerald to start when booting up?

Just to be clear, have you added compiz and emerald on the Startup Programs under Sessions?

---

### Post by ashdezign on 2007-07-29
[COLOR=#000000]For those who have noticed heavy CPU usage with Compiz Fusion and who have a dual core cpu:[/COLOR]

[http://news.softpedia.com/news/Optimize-Ubuntu-Feisty-Fawn-for-Speed-53836.shtml](http://news.softpedia.com/news/Optimize-Ubuntu-Feisty-Fawn-for-Speed-53836.shtml)

Step 4: Concurrent Booting.

[COLOR=#000000] Since I made that one change my CPU demand stays between 40 and 55% even on manual cube rotate with Atlantis enabled versus 99% before.[/COLOR]

---

### Post by MissDjax on 2007-07-29
> **MrCrussell said:**
> missdjax - are you sure you have the environment set up properly? If I try to run compiz from a standard Gnome session I get the same error. Follow the instructions here : [http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314) and it should be ok ...

In other news, I'm getting "Can't load ccp built for ABI version 20070707, actual version is 20070708" - when I try to access Vorian's repo it looks ... utterly broken!!!! wonder if it's the root cause of my probs...

ya, I'm 100% sure I set up everything properly.

---

### Post by Kayne on 2007-07-29
> **Kayne said:**
> Sorry, if this was already posted, but any info about the new plugins that came out recently?
I'm especially interested in Shift Switcher, it provides a Flip3d like feature like in Vista and a Cover Flow feature, which will be used in Leopard.

[[IMG]http://img337.imageshack.us/img337/9771/flib3das7.th.png[/IMG]](http://img337.imageshack.us/my.php?image=flib3das7.png) [[IMG]http://img337.imageshack.us/img337/9369/flib4dsmalluu6.th.png[/IMG]](http://img337.imageshack.us/my.php?image=flib4dsmalluu6.png) [[IMG]http://img337.imageshack.us/img337/6999/flib5dsmallhn3.th.png[/IMG]](http://img337.imageshack.us/my.php?image=flib5dsmallhn3.png)

More info here:
[http://smspillaz.wordpress.com/2007/07/25/compiz-fusion-community-news-edition-9-for-july-23-2007-breaking-news-forums-posts-go-down-by-half-due-to-a-lack-of-posts-asking-for-aquariums/](http://smspillaz.wordpress.com/2007/07/25/compiz-fusion-community-news-edition-9-for-july-23-2007-breaking-news-forums-posts-go-down-by-half-due-to-a-lack-of-posts-asking-for-aquariums/)

Unfortunately I don't know how to include new plugins...
Just to answer my own question, I just saw today in synaptics, that there was a unofficial compiz-plugin package, that wasn't installed yet. And in there included are these two plugins.
For me it works without any problems...
Take that, Vista :D

[[IMG]http://img517.imageshack.us/img517/7537/flip3ddz3.th.png[/IMG]](http://img517.imageshack.us/my.php?image=flip3ddz3.png) [[IMG]http://img517.imageshack.us/img517/7884/coverflowki0.th.png[/IMG]](http://img517.imageshack.us/my.php?image=coverflowki0.png)

---

### Post by chiinox on 2007-07-29
New to Ubuntu, but can follow instructions pretty good ;-)  Looks like I am running compiz fusion now.  Even thought only login in to xgl session, for the most part works ok, with quirks like no Super button and 2 sided cube only.  Running on a T60 IBM, Radeon Mobility x1400, using Ubuntu restricted ATI drivers.  My question is there a way to run compiz fusion with out having to log in to an xgl session?  Will that help with the problems like the 2 sided cube?

Thanks

---

### Post by geetarista on 2007-07-29
> **Kayne said:**
> Just to answer my own question, I just saw today in synaptics, that there was a unofficial compiz-plugin package, that wasn't installed yet. And in there included are these two plugins.
For me it works without any problems...
Take that, Vista :D


Thanks Kayne!  That worked for me!

---

### Post by SiRiuS-233 on 2007-07-29
Hi there

managed to get my default theme back with : compiz --replace -c emerald &
but emerald still doesent let me change to another theme.

any ideas on how to fix that?

many thx

---

### Post by johannes_ on 2007-07-29
> Hi,

I'm getting the following and my window-decorator disappears :-/

johannes@antares:~$ compiz --replace
compiz (core) - Warn: Unable to parse XML metadata from file "core.xml"
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

My graphics accelerator is an Intel GMA 945. Any suggestions? I already enabled the window-decorator plugin with emerald (the packages emerald and emerald-themes are already installed) and the part from my xorg.conf file that's maybe important:

Section "Device"
Identifier "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
Driver "i810"
BusID "PCI:0:2:0"
Option "AddARGBGLXVisuals" "True"
EndSection

I'm also not sure if the xlg-server starts, but I have installed the package (and I'm not sure if I really need it) ...

best regards,
Johannes

Doesn't someone has any suggestions? I'm really getting crazy :-/

---

### Post by the yawner on 2007-07-29
> **chiinox said:**
> New to Ubuntu, but can follow instructions pretty good ;-)  Looks like I am running compiz fusion now.  Even thought only login in to xgl session, for the most part works ok, with quirks like no Super button and 2 sided cube only.  Running on a T60 IBM, Radeon Mobility x1400, using Ubuntu restricted ATI drivers.  My question is there a way to run compiz fusion with out having to log in to an xgl session?  Will that help with the problems like the 2 sided cube?

Thanks

I'm running Ubuntu on an R51e Thinkpad which unfortunately also has an ATI video card. For now we have no choice but to run XGL to get Compiz Fusion. That is, until AMD releases a better driver (or code).

---

### Post by Frak on 2007-07-29
Have you tried disabling compiz and increasing the desktops then restarting it?
And for the AMD thing, don't hold your breath.

---

### Post by chiinox on 2007-07-29
> **the yawner said:**
> I'm running Ubuntu on an R51e Thinkpad which unfortunately also has an ATI video card. For now we have no choice but to run XGL to get Compiz Fusion. That is, until AMD releases a better driver (or code).

I guess we are stuck with the crappy end of the stick then!!  I was able to install on my PC which has Nvidia card.  I used different method of install thought, used a script on this thread.  Worked pretty good and have an icon that shows up to run manager and ccsm.   Was going to give it a try on laptop but if the driver is the issue then won't even bother.  Do you know if Beryl runs better with ATI cards?


[http://ubuntuforums.org/showthread.php?t=508769](http://ubuntuforums.org/showthread.php?t=508769)

---

### Post by Drone4four on 2007-07-30
> **mevets said:**
> For those that **can't** get emerald to draw window decorations try:
```

compiz  --indirect-rendering --replace

```
When I ran this it ran Compiz with kwin drawing the decorations. Its not emerald, but kwin is still nice.

Decorations still don't render with this compiz command....what else could I try?

---

### Post by Drone4four on 2007-07-30
My decorations do not show up.  Here is my error message for compiz --replace:```
drone4four@kubuntu:~$ compiz --replace
/usr/bin/compiz: line 777: 13720 Segmentation fault      (core dumped) $*
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
Fatal: Can't run metacity
Backend     : gconf
Integration : true
Profile     : default
Adding plugin atlantis (atlantis)
Adding plugin group (group)
Adding plugin svg (svg)
Adding plugin fs (fs)
Adding plugin splash (splash)
Adding plugin animation (animation)
Adding plugin dbus (dbus)
Adding plugin opacify (opacify)
Adding plugin shift (shift)
Adding plugin gotovp (gotovp)
Adding plugin clone (clone)
Adding plugin place (place)
Adding plugin reflex (reflex)
Adding plugin widget (widget)
Adding plugin annotate (annotate)
Adding plugin scaleaddon (scaleaddon)
Adding plugin cube (cube)
Adding plugin png (png)
Adding plugin ezoom (ezoom)
Adding plugin firepaint (firepaint)
Adding plugin minimize (minimize)
Adding plugin put (put)
Adding plugin glib (glib)
Adding plugin cheatsheet (cheatsheet)
Adding plugin move (move)
Adding plugin ring (ring)
Adding plugin quickchange (quickchange)
Adding plugin screenshot (screenshot)
Adding plugin resize (resize)
Adding plugin colorfilter (colorfilter)
Adding plugin workarounds (workarounds)
Adding plugin keybinding (keybinding)
Adding plugin screensaver (screensaver)
Adding plugin wall (wall)
Adding plugin scalefilter (scalefilter)
Adding plugin text (text)
Adding plugin extrawm (extrawm)
Adding plugin inotify (inotify)
Adding plugin switcher (switcher)
Adding plugin wobbly (wobbly)
Adding plugin gears (gears)
Adding plugin 3d (3d)
Adding plugin wallpaper (wallpaper)
Adding plugin mblur (mblur)
Adding plugin blur (blur)
Adding plugin zoom (zoom)
Adding plugin fade (fade)
Adding plugin trailfocus (trailfocus)
Adding plugin neg (neg)
Adding plugin thumbnail (thumbnail)
Adding plugin kiosk (kiosk)
Adding plugin expo (expo)
Adding plugin addhelper (addhelper)
Adding core settings (General Options)
Adding plugin showdesktop (showdesktop)
Adding plugin rotate (rotate)
Adding plugin vpswitch (vpswitch)
Adding plugin fadedesktop (fadedesktop)
Adding plugin water (water)
Adding plugin crashhandler (crashhandler)
Adding plugin winrules (winrules)
Adding plugin video (video)
Adding plugin plane (plane)
Adding plugin resizeinfo (resizeinfo)
Adding plugin snap (snap)
Adding plugin scale (scale)
Adding plugin imgjpeg (imgjpeg)
Adding plugin mousegestures (mousegestures)
Adding plugin bs (bs)
Adding plugin decoration (decoration)
Adding plugin cubereflex (cubereflex)
Adding plugin flash (flash)
Adding plugin regex (regex)
Adding plugin bench (bench)
Initializing core options...done
Initializing place options...done
Initializing minimize options...done
Initializing move options...done
Initializing resize options...done
Initializing workarounds options...done
Initializing zoom options...done
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Initializing video options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
Initializing decoration options...done
Initializing wobbly options...done
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/friction. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/spring_k. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Initializing fade options...done
Initializing cube options...done
Initializing switcher options...done
Initializing rotate options...done
Initializing scale options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Info: Couldn't bind redirected window 0x440018f to texture
``` Here is compiz --replace -c emerald &:
```
drone4four@kubuntu:~$ compiz --replace -c emerald &
[1] 14639
drone4four@kubuntu:~$ Backend     : gconf
Integration : true
Profile     : default
Adding plugin atlantis (atlantis)
Adding plugin group (group)
Adding plugin svg (svg)
Adding plugin fs (fs)
Adding plugin splash (splash)
Adding plugin animation (animation)
Adding plugin dbus (dbus)
Adding plugin opacify (opacify)
Adding plugin shift (shift)
Adding plugin gotovp (gotovp)
Adding plugin clone (clone)
Adding plugin place (place)
Adding plugin reflex (reflex)
drone4four@kubuntu:~$ Adding plugin widget (widget)
Adding plugin annotate (annotate)
Adding plugin scaleaddon (scaleaddon)
Adding plugin cube (cube)
Adding plugin png (png)
Adding plugin ezoom (ezoom)
Adding plugin firepaint (firepaint)
Adding plugin minimize (minimize)
Adding plugin put (put)
Adding plugin glib (glib)
Adding plugin cheatsheet (cheatsheet)
Adding plugin move (move)
Adding plugin ring (ring)
Adding plugin quickchange (quickchange)
Adding plugin screenshot (screenshot)
Adding plugin resize (resize)
Adding plugin colorfilter (colorfilter)
Adding plugin workarounds (workarounds)
Adding plugin keybinding (keybinding)
Adding plugin screensaver (screensaver)
Adding plugin wall (wall)
Adding plugin scalefilter (scalefilter)
Adding plugin text (text)
Adding plugin extrawm (extrawm)
Adding plugin inotify (inotify)
Adding plugin switcher (switcher)
Adding plugin wobbly (wobbly)
Adding plugin gears (gears)
Adding plugin 3d (3d)
Adding plugin wallpaper (wallpaper)
Adding plugin mblur (mblur)
Adding plugin blur (blur)
Adding plugin zoom (zoom)
Adding plugin fade (fade)
Adding plugin trailfocus (trailfocus)
Adding plugin neg (neg)
Adding plugin thumbnail (thumbnail)
Adding plugin kiosk (kiosk)
Adding plugin expo (expo)
Adding plugin addhelper (addhelper)
Adding core settings (General Options)
Adding plugin showdesktop (showdesktop)
Adding plugin rotate (rotate)
Adding plugin vpswitch (vpswitch)
Adding plugin fadedesktop (fadedesktop)
Adding plugin water (water)
Adding plugin crashhandler (crashhandler)
Adding plugin winrules (winrules)
Adding plugin video (video)
Adding plugin plane (plane)
Adding plugin resizeinfo (resizeinfo)
Adding plugin snap (snap)
Adding plugin scale (scale)
Adding plugin imgjpeg (imgjpeg)
Adding plugin mousegestures (mousegestures)
Adding plugin bs (bs)
Adding plugin decoration (decoration)
Adding plugin cubereflex (cubereflex)
Adding plugin flash (flash)
Adding plugin regex (regex)
Adding plugin bench (bench)
Initializing core options...done
Initializing place options...done
Initializing minimize options...done
Initializing move options...done
Initializing resize options...done
Initializing workarounds options...done
Initializing zoom options...done
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Initializing video options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
Initializing decoration options...done
Initializing wobbly options...done
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/friction. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/spring_k. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Initializing fade options...done
Initializing cube options...done
Initializing switcher options...done
Initializing rotate options...done
Initializing scale options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
``` My error message is like kevin21's: > **kevinlang21 said:**
> I get no titlebars. I tried everything in this thread, but it still doesn't work. this is my error message:```
kevin@computer:~$ compiz --replace -c emerald &
[1] 14627
kevin@computer:~$ Adding plugin splash (splash)
Adding plugin thumbnail (thumbnail)
Adding plugin opacify (opacify)
Adding plugin cubereflex (cubereflex)
Adding plugin video (video)
Adding plugin wobbly (wobbly)
Adding plugin neg (neg)
Adding plugin resizeinfo (resizeinfo)
Adding plugin glib (glib)
Adding plugin group (group)
Adding plugin png (png)
Adding plugin snow (snow)
Adding plugin reflex (reflex)
Adding plugin scaleaddon (scaleaddon)
Adding plugin screenshot (screenshot)
Adding plugin regex (regex)
Adding plugin zoom (zoom)
Adding plugin clone (clone)
Adding plugin extrawm (extrawm)
Adding plugin fakeargb (fakeargb)
Adding plugin imgjpeg (imgjpeg)
Adding plugin rotate (rotate)
Adding plugin bench (bench)
Adding plugin fade (fade)
Adding plugin fadedesktop (fadedesktop)
Adding plugin firepaint (firepaint)
Adding plugin dbus (dbus)
Adding plugin switcher (switcher)
Adding plugin blur (blur)
Adding plugin addhelper (addhelper)
Adding plugin trailfocus (trailfocus)
Adding plugin showdesktop (showdesktop)
Adding plugin move (move)
Adding plugin minimize (minimize)
Adding plugin water (water)
Adding plugin text (text)
Adding plugin fs (fs)
Adding plugin inotify (inotify)
Adding plugin put (put)
Adding plugin resize (resize)
Adding plugin decoration (decoration)
Adding plugin animation (animation)
Adding plugin svg (svg)
Adding plugin vpswitch (vpswitch)
Adding plugin plane (plane)
Adding plugin cube (cube)
Adding plugin expo (expo)
Adding plugin scale (scale)
Adding plugin crashhandler (crashhandler)
Adding plugin winrules (winrules)
Adding plugin place (place)
Adding plugin ring (ring)
Adding plugin annotate (annotate)
Adding plugin mblur (mblur)
Adding plugin wall (wall)
Adding plugin tile (tile)
Adding plugin snap (snap)
Adding core settings (General Options)
Backend     : ini
Integration : true
Profile     : default
Initializing core options...done
Initializing zoom options...done
Initializing move options...done
Initializing minimize options...done
Initializing resize options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
Initializing decoration options...done
Initializing place options...done
Initializing wobbly options...done
Initializing fade options...done
Initializing cube options...done
Initializing scale options...done
Initializing rotate options...done
Initializing switcher options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
```Thanks for your help

---

### Post by Drone4four on 2007-07-30
This script didn't fix my decorations problem.  > **mukiex said:**
> NVM it all I fixed my issue with the following :

Mini lack-of-window decoration fix :

mv ~/.compizconfig/ ~/.compizconfig_backup/ # Not sure if this is NEEDED
sudo apt-get remove compiz*

copy and paste the following into an executable script:
```

KEY=81836EBF; gpg --keyserver subkeys.pgp.net --recv $KEY && gpg --export --armor $KEY | sudo apt-key add -

sudo apt-get update

sudo apt-get remove compiz-core

sudo apt-get install compiz-gnome

sudo apt-get install compizconfig-settings-manager # compizconfig-backends-* ?!

sudo apt-get install compiz-fusion-*


```

And finally, run compiz --replace

If none of your options are sticking, delete the ~/.compizconfig folder and restart compiz again.

---

### Post by Drone4four on 2007-07-30
> **jg1395 said:**
> this fixed my window decorations on my nvidia videocard

[http://forums.opencompositing.org/viewtopic.php?f=12&t=808](http://forums.opencompositing.org/viewtopic.php?f=12&t=808)

Run:



Then restart X

(White terminals diagnoses that as the problem.)
This solved the problem of decorations not showing up!

---

### Post by the yawner on 2007-07-30
> **chiinox said:**
> I guess we are stuck with the crappy end of the stick then!!  I was able to install on my PC which has Nvidia card.  I used different method of install thought, used a script on this thread.  Worked pretty good and have an icon that shows up to run manager and ccsm.   Was going to give it a try on laptop but if the driver is the issue then won't even bother.  Do you know if Beryl runs better with ATI cards?


[http://ubuntuforums.org/showthread.php?t=508769](http://ubuntuforums.org/showthread.php?t=508769)
Now that you mentioned it, there's actually a way to run Beryl without installing/running XGL. The process requires that you use the open source driver for ATI. But then, when I tested that, it was horribly slower than the one with XGL. Could be a different story for you though.


=====
To those getting the error:
> /usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
Are you using 32-bit color depth? If so, could you try running it on 24-bit color depth?

---

### Post by frazle on 2007-07-30
> **chiinox said:**
> I guess we are stuck with the crappy end of the stick then!!  I was able to install on my PC which has Nvidia card.  I used different method of install thought, used a script on this thread.  Worked pretty good and have an icon that shows up to run manager and ccsm.   Was going to give it a try on laptop but if the driver is the issue then won't even bother.  Do you know if Beryl runs better with ATI cards?


What's this XGL you speak of? Sorry i'm a bit of an ubuntunoob, not quite up to scratch with all of the terms and aspects of linux yet!

---

### Post by el mariachi on 2007-07-30
> **frazle said:**
> What's this XGL you speak of? Sorry i'm a bit of an ubuntunoob, not quite up to scratch with all of the terms and aspects of linux yet!
[http://en.wikipedia.org/wiki/XGL](http://en.wikipedia.org/wiki/XGL)

---

### Post by Mrs Harris on 2007-07-30
Hey, great how to thanks... all working like a dream.

Just wondering if there's a quick way to enable/disable compiz?

---

### Post by Kieran M on 2007-07-30
Hello all!
Today, I followed the guide found here [http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/#comments](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/#comments)

This worked, partially. It was a great, easy to follow tutorial, but I'm having a problem. I am unable to close/move/maximise/minimise windows without right clicking on them on the taskbar. In other words, the effects and cube etc are working beautifully, but the window border has completely disappeared! Despite the horror stories I have heard, I am certain that this is no fault of Envy, as this exact same problem has happened when I used Beryl and Compiz in the past. I will be happy to provide any information that may help you work out exactly what the devil is going on!
Thank you all in advance :)

---

### Post by £Xo7XEEQK38037M# on 2007-07-30
> **the yawner said:**
> Just to be clear, have you added compiz and emerald on the Startup Programs under Sessions?Yes I added compiz --replace and an option emerald --replace in the startup session.

---

### Post by the yawner on 2007-07-30
That's odd. It should be running at start-up by now.

=====
Got another update on Vorian's repo, and this time the ccp-plugin error is gone. Compiz Fusion's running again, and I got the chance to test the shift plugin. Nice.

---

### Post by Vorian on 2007-07-30
> **the yawner said:**
> 
Got another update on Vorian's repo, and this time the ccp-plugin error is gone. Compiz Fusion's running again, and I got the chance to test the shift plugin. Nice.

glad to hear it :)

---

### Post by jet2230 on 2007-07-30
thanks for guide, i got it working on a 6 year old (maybe older) Pentium III 500mhz + 128mb nvidia card (agp). effects are smashing. i never thought this would have worked on this machine - runs exactly the same as it does on my core-duo laptop. i am gob-smacked :) ?!?

---

### Post by r4p70r on 2007-07-31
hey guys i would add this to the top of the tutorial you need to install this program called Envy, it updates your nvidia and / or ATI drivers automatically then promps you to edit xorg then promps to restart. fixes the GLX depth 32 problem and funky window and white screen problems as well. heres a link. [http://kevin.vanzonneveld.net/techbl...ubuntu_feisty/](http://kevin.vanzonneveld.net/techbl...ubuntu_feisty/)

go there and follow the first step and you should be good to go.

hope this helps ya.

---

### Post by meono on 2007-07-31
hi everyone,

first of thank you for the howto. it is really easy and clear. effects are amazing and it works smoothly,

well, most of the time :(

I have few problems, One of them is borders, for amsn no border is displayed. and it also doesn't show in application switcher. one other problem is for an application called VMD. It starts up as usual in the terminal but shuts down without errors. When i kill all compiz.real, emerald, and run xfwm4 it works as usual.

can anybody help me solve this.

---

### Post by kalleball on 2007-07-31
I followed the instructions but when i run compiz --replace nothing happens.

Pretty sure the graphics drivers are installed (there's something about Radeon 9800 XT and ATI technologies in the Device Manager and the Catalyst Control Center is working it seems) and i did everything in the instructions, 10 packages installed or something...

---

### Post by £Xo7XEEQK38037M# on 2007-07-31
> **the yawner said:**
> That's odd. It should be running at start-up by now.

=====
Got another update on Vorian's repo, and this time the ccp-plugin error is gone. Compiz Fusion's running again, and I got the chance to test the shift plugin. Nice.

Does the option "Flat File" have influence on this? In order to overcome some issues related to keyboard settings I picked that, so I don't have to reconfigure that as well after boot-up.

---

### Post by screaminj3sus on 2007-07-31
Does anyone else have problems using any of the switchers with minimized windows? This includes right,shift switchers and alt tab when tere is windows minimized instead of a preview of the window it just shows a very blurry icon. The window preview plugin actually doesn't even work with minimized windows either.

For example banshee works fine in the switcher when not minimized, but when it is minimized I get no preview and can't even select it

[[IMG]http://img234.imageshack.us/img234/6451/screenshothowtocompizfucc4.png[/IMG]](http://imageshack.us)

---

### Post by Frak on 2007-07-31
It just does that, its been doing that since Compiz and Beryl were seperate.

---

### Post by £Xo7XEEQK38037M# on 2007-07-31
> **Kayne said:**
> Just to answer my own question, I just saw today in synaptics, that there was a unofficial compiz-plugin package, that wasn't installed yet. And in there included are these two plugins.
For me it works without any problems...
Take that, Vista :D

[[IMG]http://img517.imageshack.us/img517/7537/flip3ddz3.th.png[/IMG]](http://img517.imageshack.us/my.php?image=flip3ddz3.png) [[IMG]http://img517.imageshack.us/img517/7884/coverflowki0.th.png[/IMG]](http://img517.imageshack.us/my.php?image=coverflowki0.png)

I got the right screenshot as well, but not the left, which option is that?

---

### Post by musther on 2007-07-31
I have a strange problem.  I've installed compiz fusion as per this thread, and it seems to work, at least mostly, but when using Firefox my mouse cursor tends to disappear.  Usually after I click a link, it vanishes (not always), and then only appears when I mouseover text items and things, after a while, it appears again, and then after a while, disappears again.

Any suggestions?

-----EDIT-----
Actually, it seems that the cursor vanishes until the page has completely finished loading.

---

### Post by diegogarvar on 2007-07-31
Hi guys i change from windows to ubuntu fiesty recently and i have been in love with it :D
this is awesome
i installed compiz fusion and it worked perfectly, since today...
i dont have the window colorfull bars anymore and when i open the terminal it shows a white space only 
my video card is an nvidia 7300 GT 
here's a screenshot 
[[IMG]http://img108.imageshack.us/img108/8867/screenshotmr4.th.png[/IMG]](http://img108.imageshack.us/my.php?image=screenshotmr4.png)

i hope u guys can help me out!

---

### Post by ggkrapface on 2007-07-31
I seem to be having the same problem.  I'm a ubuntu noob but seem to be proficient enough to diagnose most problems.  Here is what my terminal spits out when i run "compiz --replace"

```
/usr/bin/compiz: line 777: 13119 Segmentation fault      (core dumped) $*
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
```

Been working on getting this running for a few days now.  Any help would be greatly appreciated!

Edit:  Tight, thanks Frak on the code blocks.

---

### Post by Frak on 2007-07-31
Replace < with [ and > with ].

---

### Post by diegogarvar on 2007-08-01
frak do u have any clue to how to solve my problem??

---

### Post by Frak on 2007-08-01
No idea, but at least I'd try to help ggkrapface with his BB code issues.

---

### Post by ggkrapface on 2007-08-01
I'm pretty sure it has something to do with Xinerama.  When it's enabled, my basic desktop effects don't work.  When it's off, they do.  I'll try compiz again with Xinerama off.  Any word on getting fusion up with Xinerama?

---

### Post by diegogarvar on 2007-08-01
:( i cant get it working

---

### Post by Lonthong on 2007-08-01
> **Kayne said:**
> Just to answer my own question, I just saw today in synaptics, that there was a unofficial compiz-plugin package, that wasn't installed yet. And in there included are these two plugins.
For me it works without any problems...
Take that, Vista :D

[[IMG]http://img517.imageshack.us/img517/7537/flip3ddz3.th.png[/IMG]](http://img517.imageshack.us/my.php?image=flip3ddz3.png) [[IMG]http://img517.imageshack.us/img517/7884/coverflowki0.th.png[/IMG]](http://img517.imageshack.us/my.php?image=coverflowki0.png)

I enabled shift switcher already.
What keys should I press to get those 2 images???

---

### Post by Kayne on 2007-08-01
> I got the right screenshot as well, but not the left, which option is that?
Shift Switcher settings -> Swichter Mode "Cover" to "Flip"

> What keys should I press to get those 2 images???
Simply the "print screen" button ;)

---

### Post by Lonthong on 2007-08-01
> **Kayne said:**
> Shift Switcher settings -> Swichter Mode "Cover" to "Flip"


Simply the "print screen" button ;)

LOL........
I mean pressing keys to get into those 3d flips

Edit:
Nevermind, I figured it out already. Shift + Super + S
coooooolllllll

---

### Post by clevin on 2007-08-01
great guide.


at this stage I have two questions:

1. compiz fusion feels a little bit sluggish on my acer aspire 3680, with GMA950, especially when I rotate cubes, it just feels not as smooth as beryl, any tweak?

2. is there a setting anywhere that allows me to see **all** windows (including minimized windows) on **all** virtual spaces through hot-corner screen (moving mouse to the upper right corner of the screen). There are so many options, I got lost.....:lolflag:

---

### Post by £Xo7XEEQK38037M# on 2007-08-01
> **tneo said:**
> Yes I added compiz --replace and an option emerald --replace in the startup session.

Got one part of the issue resolved by running metacity --replace. But still upon startup no Compiz Fusion running...

---

### Post by Azakus on 2007-08-01
> **tneo said:**
> Got one part of the issue resolved by running metacity --replace. But still upon startup no Compiz Fusion running...

Have a script run when you startup.
Name the script ".compiz.sh" with the leading "." to make it invisible in your home folder
The contents of the script should look like this:
```

#!/bin/bash
compiz --replace -c emerald &

```
And add it to your session: System >> Preferences >> Sessions >> New
Name: StartCompiz
Command: sh ~/.compiz.sh
That will start compiz after X starts.

---

### Post by Frak on 2007-08-01
Why not just go to sessions and
Name: StartCompiz
Command: compiz --replace -c emerald &
This will also start compiz after X starts, but it will save a step.

---

### Post by niyi on 2007-08-01
E: Couldn't find package compizconfig-settings-manager


What does that mean, because of that error I can't even change the settings of compuiz. I used the ubuntuguide.org site BTW.

---

### Post by outphase on 2007-08-01
Ever since the 7.30 update, has anyone else's full screen VLC been under the panels? Full screen used to be on top of everything including AWN, but now it's behind. Is there anyway to change that? Using the "Alternate fullscreen method" in VLC doesn't work very well as it sometimes restarts X if I flip to fullscreen too fast (~3 sec).

If not, is there anyway I can rollback?

---

### Post by rne1223 on 2007-08-01
Thanks so much...It is working like a charm. However, I was wandering where can I find the emerald themes. I don't see to have it install.

---

### Post by jw5801 on 2007-08-01
> **outphase said:**
> Ever since the 7.30 update, has anyone else's full screen VLC been under the panels? Full screen used to be on top of everything including AWN, but now it's behind. Is there anyway to change that? Using the "Alternate fullscreen method" in VLC doesn't work very well as it sometimes restarts X if I flip to fullscreen too fast (~3 sec).

If not, is there anyway I can rollback?

Refer [this](http://ubuntuforums.org/showthread.php?t=87085) thread. I posted my solution [here.](http://ubuntuforums.org/showthread.php?p=2877880#post2877880) I've never seen the problem under compiz... but it's a known issue for VLC under metacity.

---

### Post by the yawner on 2007-08-02
> **rne1223 said:**
> Thanks so much...It is working like a charm. However, I was wandering where can I find the emerald themes. I don't see to have it install.

try sudo apt-get install emerald-themes

---

### Post by burzum on 2007-08-02
I have two problems:

#1 If i click on any menu it takes 2-3 seconds to open it. 
#2 The cube is not displayed, i have only one side

My PC is for sure not to slow to open the menus quicker, its an AMD X² 3800+ with a Geforce7800GTS.

---

### Post by £Xo7XEEQK38037M# on 2007-08-02
> **Frak said:**
> Why not just go to sessions and
Name: StartCompiz
Command: compiz --replace -c emerald &
This will also start compiz after X starts, but it will save a step.

This did it. Compiz started with boot-up now. Thanks. :D

---

### Post by Brazilian Joe on 2007-08-02
Thread maintainer & all:

The machine where I could get Compiz working is a notebook with a Radeon 9600 with 64mb of Video memory. 

One long standing problem which I had was the fact that, when I enabled xorg with AIGLX using the open-source ATI driver, it kept complaining about missing texture_from_pixmap support. The error only went away after I uninstalled the fglrx driver. So, maybe it should be addedto the first post that if the texture_from_pixmap persists, the user should uninstall fglrx drivers? At least that is what solved the issuefor me. Oh, I also force-reinstalled the open source radeon driver package...

So, folks, if your ati video card is not from the X1000 series, give the open source drivers another go, remove the proprietary drivers and, if the texture from pixmap message persists, force reinstall the open source drivers.

I am happy with all this eye candy now. :)

---

### Post by gecko94 on 2007-08-02
every time I try to start compiz fusion I get this error
```
 compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

```
Also, I have an ati card. any help?

---

### Post by Frak on 2007-08-02
@Brazilian Joe, the reason why the Open Source ones work better is because ATI drivers are designed so horridly that Open Source ones had to be developed even further than ATI's standpoint. They are still unstable and XGL has to be used, but they are better.
At least Dell and other companies are pushing for ATI to develop better drivers.

---

### Post by Frak on 2007-08-02
> **burzum said:**
> I have two problems:

#1 If i click on any menu it takes 2-3 seconds to open it. 
#2 The cube is not displayed, i have only one side

My PC is for sure not to slow to open the menus quicker, its an AMD X² 3800+ with a Geforce7800GTS.
Stop Compiz-Fusion by going to System-Administration->Process Manager then click Compiz-Fusion and then kill process (or whatever the button is in the lower right hand corner)
That should return your desktop to the normal way it was.
Now, right click on your Workspaces and choose properties, increase it to four.
Now run
```
compiz --replace
```
If you have emerald
```
compiz --replace -c emerald &
```
And the second of delay could come from Compiz-Fusion being slightly more resource intensive than Beryl or Compiz was.
Hopefully that should work.

---

### Post by dr. wiley on 2007-08-02
i was able to install easy enough, but it freezes every time i run compiz --replace :(
i had been running beryl prior to this (no emerald), but that's removed now.

any ideas as to what's wrong?

(running an inspiron 640m)

---

### Post by Frak on 2007-08-02
> **dr. wiley said:**
> i was able to install easy enough, but it freezes every time i run compiz --replace :(
i had been running beryl prior to this (no emerald), but that's removed now.

any ideas as to what's wrong?

(running an inspiron 640m)
Could you post more specific details about your laptop, I looked at dell's site, but the specifications have too much range to just guess your hardware with.

---

### Post by dr. wiley on 2007-08-02
> **Frak said:**
> Could you post more specific details about your laptop, I looked at dell's site, but the specifications have too much range to just guess your hardware with.

it's ok, i figured it out :D :D

silly me, got rid of beryl but not compiz.. reinstalled fusion and now it's rockin!  

thanks anyway :)

---

### Post by Lonthong on 2007-08-03
> **Brazilian Joe said:**
> Thread maintainer & all:

The machine where I could get Compiz working is a notebook with a Radeon 9600 with 64mb of Video memory. 

One long standing problem which I had was the fact that, when I enabled xorg with AIGLX using the open-source ATI driver, it kept complaining about missing texture_from_pixmap support. The error only went away after I uninstalled the fglrx driver. So, maybe it should be addedto the first post that if the texture_from_pixmap persists, the user should uninstall fglrx drivers? At least that is what solved the issuefor me. Oh, I also force-reinstalled the open source radeon driver package...

So, folks, if your ati video card is not from the X1000 series, give the open source drivers another go, remove the proprietary drivers and, if the texture from pixmap message persists, force reinstall the open source drivers.

I am happy with all this eye candy now. :)

I am using X 1100. 
open source driver + xgl + compiz = upper part of the windows with minimized, maximised, & closed button did not show properly
open source + xgl + beryl = WSOD
open source + xgl + compiz-fusion = works like a charm

In any case, I never faced "missing texture_from_pixmap support"

---

### Post by kosekiseiji on 2007-08-03
I'm having trouble getting the bling to work.... compiz --replace& works, I can see it doing stuff and Ican see compiz is now running under the system monitor, but nothing seems to have changed.... no effects, or anything different going on at all.

I've got a radeon 9600 if that helps.... I did have wobbly windows etc with the default fesity install but wanted more.

please help or point me in the right direction.

- Tim

---

### Post by outphase on 2007-08-03
> **jw5801 said:**
> Refer [this](http://ubuntuforums.org/showthread.php?t=87085) thread. I posted my solution [here.](http://ubuntuforums.org/showthread.php?p=2877880#post2877880) I've never seen the problem under compiz... but it's a known issue for VLC under metacity.

Doesn't seem to have an effect. Thanks though. Also, !(state=fullscreen) no longer has an effect on the opacity of fullscreen vlc, neither does name=wxvlc.

---

### Post by st33med on 2007-08-03
I can't get anything to work. No borders appear (when I use Compiz window manager), I can't rotate the cube, nothing. However, when compiz is selected as my windows manager, the change desktop becomes 'flat'.

What do I do?

---

### Post by chickmagntwannab on 2007-08-03
ive been using beryl on my machine and had it working up until i heard about compiz fusion and decided to swtich over...ive followed many tutorials similar to yours and they have all not worked...i dont get anything to work and im still a little new to ubuntu (only been using it a few months)
i have a dell pc with a 3.4 ghz processor
ati x600 graphics card
1 Gb ram

please help

---

### Post by RavanH on 2007-08-03
Wow! This tutorial removed ubuntu-desktop ... which I REALLY didn't want to happen :(

How do I reïnstall ubuntu-desktop without all its (false) dependancies like network-manager, gaim and... **desktop-effects**!?!?! I don't want to go though all the hassle of uninstalling those again and reïnstalling wicd - which will be removed when network-manager gets installed.

Bother!

---

### Post by pedrogl on 2007-08-04
Hi, I also have this weird issue with mouse cursor and firefox, quite annoying. Any ideas??

(nvidia w/drivers from official repositories)

Edit: It also happens with epiphany, but not with konqueror, could it be a geko "feature"??

> **musther said:**
> I have a strange problem.  I've installed compiz fusion as per this thread, and it seems to work, at least mostly, but when using Firefox my mouse cursor tends to disappear.  Usually after I click a link, it vanishes (not always), and then only appears when I mouseover text items and things, after a while, it appears again, and then after a while, disappears again.

Any suggestions?

-----EDIT-----
Actually, it seems that the cursor vanishes until the page has completely finished loading.

---

### Post by ronmarley1 on 2007-08-04
Thanks Vorian.  Works great on IBM Thinkpad R51 with Intel 855 graphics.
Go Buckeyes!

---

### Post by DMaster on 2007-08-04
> **niyi said:**
> E: Couldn't find package compizconfig-settings-manager


What does that mean, because of that error I can't even change the settings of compuiz. I used the ubuntuguide.org site BTW.
I am having that same problem with:

E: Couldn't find package  compizconfig-settings-manager

I also noticed that when i simply tried to install compiz itself using this command:

sudo apt-get install compiz  * compiz-gnome AND/OR compiz-kde

I get this error message:

The following packages have unmet dependencies:
   compiz: depends: compiz-decorator but it is not installable
E: Broken packages

---

### Post by Johnny p on 2007-08-04
No desktop effects are being displayed after installation Help please! Im using Envy as my nvidia driver.

---

### Post by sefs on 2007-08-04
Is anyone using USP (ubuntu system panel) if so do you have the problem where when you click it it loads behind the other windows.  How did you solve that problem.

Thanks.

---

### Post by bruckwine on 2007-08-04
Great guide! The biggest thing was getting the borders for windows back - as I had Beryl installed first I switched back to it, used it to switch back to metacity then enable compiz fusion - now I'm in eye candy heaven - thanks all!

---

### Post by rshields on 2007-08-05
Thanks, this guide worked for me in general - Xubuntu and AIGLX on a Thinkpad X60s, previously using Beryl. However, I have a couple of problems, and apologies if this has been covered already:

1. None of the super key (windows key) shortcuts are working
2. How do I change the window title bar font size? It seems to ignore the font size I have set up in XFCE User Interface Settings and I can't find the setting in CompizConfig Settings Manager.

Any ideas? Thanks.

---

### Post by ronmarley1 on 2007-08-05
> **rshields said:**
> 
2. How do I change the window title bar font size? It seems to ignore the font size I have set up in XFCE User Interface Settings and I can't find the setting in CompizConfig Settings Manager.


This is done in the settings for your window decorator.  In my case, I'm using Emerald.

---

### Post by rshields on 2007-08-05
Thanks for that, I just had to reinstall emerald and run "emerald --replace". I had removed emerald along with beryl :roll: :oops:

---

### Post by speedup on 2007-08-06
Hi to everyone I am just a newbie on linux, I am having problems making Rotate Cube using Compiz to work, please can anyone help me. I am using Nvidia 8800GTS video card is there any problem with this video card and with compiz? Any help would be greatly appreciated. Thank you in advance

---

### Post by santiagoward2000 on 2007-08-06
Hi everyone. I have a question about a specific plugin in compiz-fusion. Can the widget plugin be used with adesklets, or is it only for screenlets?
Thanks!

---

### Post by RobNyc on 2007-08-06
Worked great here..running UbuntuStudio

---

### Post by morrius on 2007-08-07
Cube not working in Compiz Fusion. Why?
ATI 9600XT

---

### Post by Sam Liu on 2007-08-07
Note to some people with dependency problems:

This is what I had to do because it wouldn't install (or remove some stuff for that matter)

```
sudo aptitude
```

then go in there, hit "g"
then hit shift+1 (!)

check and make sure its not removing packages you want. if it is, use your mouse to use the menus to remove them. hit "." to get a second solution scenario.

You're gonna need to do this a few times.

---

### Post by morrius on 2007-08-07
compiz --replace
```

Backend     : gconf
Integration : true
Profile     : default
Adding plugin cubecaps (cubecaps)
Adding plugin atlantis (atlantis)
Adding plugin winrules (winrules)
Adding plugin wobbly (wobbly)
Adding plugin opacify (opacify)
Adding plugin neg (neg)
Adding plugin ring (ring)
Adding plugin put (put)
Adding plugin resizeinfo (resizeinfo)
Adding plugin addhelper (addhelper)
Adding plugin minimize (minimize)
Adding plugin vpswitch (vpswitch)
Adding plugin ezoom (ezoom)
Adding core settings (General Options)
Adding plugin gears (gears)
Adding plugin scale (scale)
Adding plugin svg (svg)
Adding plugin mblur (mblur)
Adding plugin fs (fs)
Adding plugin zoom (zoom)
Adding plugin reflex (reflex)
Adding plugin place (place)
Adding plugin kiosk (kiosk)
Adding plugin cheatsheet (cheatsheet)
Adding plugin dbus (dbus)
Adding plugin quickchange (quickchange)
Adding plugin plane (plane)
Adding plugin png (png)
Adding plugin cubereflex (cubereflex)
Adding plugin snap (snap)
Adding plugin scalefilter (scalefilter)
Adding plugin scaleaddon (scaleaddon)
Adding plugin water (water)
Adding plugin glib (glib)
Adding plugin switcher (switcher)
Adding plugin notification (notification)
Adding plugin splash (splash)
Adding plugin 3d (3d)
Adding plugin colorfilter (colorfilter)
Adding plugin trailfocus (trailfocus)
Adding plugin keybinding (keybinding)
Adding plugin shift (shift)
Adding plugin text (text)
Adding plugin fadedesktop (fadedesktop)
Adding plugin thumbnail (thumbnail)
Adding plugin cube (cube)
Adding plugin widget (widget)
Adding plugin screensaver (screensaver)
Adding plugin resize (resize)
Adding plugin regex (regex)
Adding plugin expo (expo)
Adding plugin group (group)
Adding plugin video (video)
Adding plugin wall (wall)
Adding plugin crashhandler (crashhandler)
Adding plugin flash (flash)
Adding plugin gotovp (gotovp)
Adding plugin visualevent (visualevent)
Adding plugin workarounds (workarounds)
Adding plugin clone (clone)
Adding plugin animation (animation)
Adding plugin extrawm (extrawm)
Adding plugin imgjpeg (imgjpeg)
Adding plugin fade (fade)
Adding plugin annotate (annotate)
Adding plugin blur (blur)
Adding plugin mousegestures (mousegestures)
Adding plugin rotate (rotate)
Adding plugin decoration (decoration)
Adding plugin firepaint (firepaint)
Adding plugin showdesktop (showdesktop)
Adding plugin wallpaper (wallpaper)
Adding plugin move (move)
Adding plugin screenshot (screenshot)
Adding plugin inotify (inotify)
Adding plugin bench (bench)
Initializing core options...done
Initializing ring options...done
Initializing zoom options...done
Initializing place options...done
Initializing shift options...done
Initializing resize options...done
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Initializing video options...done
Initializing workarounds options...done
Initializing decoration options...done
Initializing move options...done
Initializing wobbly options...done
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/friction. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/spring_k. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Initializing animation options...done
Initializing fade options...done
Initializing cube options...done
Initializing expo options...done
Initializing rotate options...done
Initializing scale options...done
Initializing switcher options...done

```

Cube not workin. Why?

---

### Post by Salarzae on 2007-08-07
**Whenever I try to start it, my system freezes to death!... any remedy..???**

---

### Post by morrius on 2007-08-07
> **morrius said:**
> compiz --replace
Cube not workin. Why?

Decision of this problem:
1. Disable compiz
```
metacity --replace
```
2. Right click on table canger at the right-bottom corner. 
 Prefences. Change quantity of work places at 4.
3. Enable compiz
```
compiz --replace
```
I think what it's stupid mistake:)

---

### Post by ozzloy on 2007-08-07
> **thatsPipe said:**
> I've got dual monitors also and am getting the same sort of thing with 2 desktop cubes. The way Beryl handled multi monitors was great and it would be nice to have the same. Beryl had was a check-box somewhere to indicate that you want a single cube across multiple monitors. Hopefully this feature will be included soon.



EDIT: Something I noticed with the behavior of the Application Switcher plugin but not too sure if its because of my dual monitors. Anyways, when alt-tabbing, it skips every other window. So if I have an odd number open, I can eventually get to all of them but when there is an even number open, I can only alt-tab to half of them and it doesn't matter what desktop they are on. I'm not sure if this is a general problem with the plugin or its just happening because of my dual monitors.

i'm having the exact same problem with alt+tab skipping a window.  did you ever find a solution?  it's extremely annoying.  thanks!

another weird behavior.  if i hit f8 to go into scale, hitting f8 again doesn't return from scale.  i have to choose a window and hit <enter> or click it with the mouse.  how do i fix that?

---

### Post by ozzloy on 2007-08-07
> **ozzloy said:**
> i'm having the exact same problem with alt+tab skipping a window.  did you ever find a solution?  it's extremely annoying.  thanks!


ok, i fixed it.  short explanation:  application switching default hot key for "Next Window" and "Next Window (All windows)" are both Alt+Tab.  change one.
more detailed fix:
System->
Preferences->
CompizConfig Settings Manager->
(left hand side) Category:Window Management->
(main window to right of left hand side menu) Application Switcher ->
(tab at top) Actions (to right of "General" tab) ->
(under "Name" category in "Actions" tab) General drop down menu ->
Next Window ->
(under "Key" category) click "Alt+Tab" ->
on the keyboard press Super+1, now the cell ["Next Window", "Key"] should say "Super+1"

---

### Post by reference2myself on 2007-08-07
I just got some updates for compiz today.  I went ahead and installed them without thinking and now compiz doesn't work. It turns most of the screen black and turns my mouse cursor into the text icon and i can't do anything but move the mouse around.  Anyone know what happened?  I had like 5 updates for compiz that the update manager found on it's own.  I tried uninstalling and reinstalling everything and it does the exact same thing, maybe I need to delete some config files?  Any ideas?

---

### Post by reference2myself on 2007-08-07
I just fixed it, I had  the uPure64 Repository at Janvitus [http://www.janvitus.netsons.org/repository/](http://www.janvitus.netsons.org/repository/) and it had some updates to compiz not in Trevino's repository.  It was updating compiz to 1.5.2 which apparently has some issues with fusion.  Maybe someone wants to look into this for future.

---

### Post by proalan on 2007-08-07
I have to say this is awsome. I followed this guide

[http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/)

I was amazed to see it all work smoothly on my very low end laptop with a crummy integrated Intel 64MB Graphics card.

At first glance there seems to be less options to tinker with than beryl, but I'm sure its all there. 

Is compiz fusion still beta?

p.s. I love how my terminal is truly transparent now rather than just relative to the desktop background.

---

### Post by Frak on 2007-08-07
Alpha

---

### Post by wajiw on 2007-08-08
In case this will help anyone, after I installed CF it would take me like 4-5 times restarting gnome to get it to work.  I could log in and when I ran compiz --replace it would freeze on me.  

To fix it I went into symantic and did a search for compiz.  I removed all the programs that were installed, restarted, and went over the steps to install and it actually starts up fine now.

I think the problem was I didn't have desktop-effects removed or there was some kind of conflict with the older version of compiz I was running.

---

### Post by amyfan on 2007-08-08
whne i installed compiz fusion the toolbar or titalebar the one with the X - and square went away and now i cant get it back anyone know how?

---

### Post by RobNyc on 2007-08-08
Cube is enabled here but its not working
Also I would like to see if I can get the emerald themes or something ? 
I have the default theem and its getting kinda boring.

UbuntuStudio
NVIDIA 7950GT

---

### Post by Vorian on 2007-08-08
sure, you can apt-get install emerald emerald-themes.

---

### Post by naseem on 2007-08-09
hy
When I run the command:sudo apt-get install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf emerald emerald-themes

I get an erroro code:E: /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070730~3v1ubuntu0_i386.deb: tentata sovrascrittura di `/usr/lib/compiz/libgconf.so', che si trova anche nel pacchetto compiz-plugins

I get the same if I try to uninstal compiz.
Some help on how to fix this (broken pkgs) please...

_just solved with some patience_

---

### Post by RobNyc on 2007-08-09
> **Vorian said:**
> sure, you can apt-get install emerald emerald-themes.

thanks

---

### Post by maduranga on 2007-08-10
okk... i got compiz fusion installed. ( I have followed this guide several times to install compiz fusion as i reinstalled ubuntu, and every time it worked perectly.) but this time, at the moment of running compiz after the installation, there was two workspaces. then I changed it into 4. And now I have 4 workspaces and everything working fine except workspaces changing. I have missed compiz's workspaces changing system. 4 workspaces are still operated from each other and when i change a workspace, it changes without any animation, just in the usual way..


someone pls help me to correct this prob..

---

### Post by Frak on 2007-08-10
Just try to restart compiz (such as logging out and back in)

---

### Post by maduranga on 2007-08-10
i did that. even system restart didn't help me.  but when i select a open window in another workspace, it rotate in to the workspace, but even i cant find out in what workspace I'm working on.

---

### Post by chockri on 2007-08-10
please how to view cube

---

### Post by unabatedshagie on 2007-08-10
Apologies if this has been asked already but has anyone using Treviño&#8217;s repo been getting any updates in the last maybe 2-3 days?

---

### Post by Frak on 2007-08-10
> **chockri said:**
> please how to view cube
ctrl+alt+(hold) left click
and just move the mouse to move the cube.

---

### Post by gtrtx on 2007-08-10
> **unabatedshagie said:**
> Apologies if this has been asked already but has anyone using Treviño’s repo been getting any updates in the last maybe 2-3 days?

I too  am curious about this. When I first installed CF, I got updates on a pretty regular basis. For me there hasn't been an update for some time. I'm thinking longer that 2-3 days even. Closer to a week or so.

---

### Post by ShaolinF on 2007-08-10
Hi Guys,

I installed it but nothing works.. Its still the same old brown ubuntu theme. Im running Feisty 32bit

And on the first post where the user tells me to add the following keys:

gpg --keyserver subkeys.pgp.net --recv-keys 81836EBF
gpg --export --armor 81836EBF | sudo apt-key add -

Where do I add them ? Into terminal ?


EDIT: I tried the following instead in terminal: compiz --replace -c emerald &

This is the output I got:

Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

Im using vmware btw.

---

### Post by Amaranth on 2007-08-10
Check out [https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion) for a better guide.

---

### Post by unabatedshagie on 2007-08-10
> **gtrtx said:**
> I too  am curious about this. When I first installed CF, I got updates on a pretty regular basis. For me there hasn't been an update for some time. I'm thinking longer that 2-3 days even. Closer to a week or so.
Yeah, it has been longer, I got the last update on the 1st of August.

Hey who knows maybe he's taking a holiday :)

---

### Post by Vorian on 2007-08-10
[CENTER][SIZE=5][COLOR=Red]*Updated* Compiz Fusion Guide[/COLOR][/SIZE]
_[COLOR=Red]**[SIZE=3]Please see first post again![/SIZE]**[/COLOR]_

**[SIZE=4][COLOR=RoyalBlue]And a big thanks to Amaranth![/COLOR][/SIZE]**
[/CENTER]

---

### Post by maduranga on 2007-08-10
AHHHH....!!!! Great.. things have got updated.... and Vorian's profile pic too... thanks...

---

### Post by tekkenlord on 2007-08-10
So, this updated guide can be used for Kubuntu as well? Or do I need to install some extra packages? Thanks!

---

### Post by siralphred on 2007-08-10
thanks for the guide but i have a few questions; why is trevinos repositories being purged? and also does this amaranth repository have compiz extra plugins and beryl emerald themes? and also the compiz fusion icon if it does can you edit the guide to reflect it or tell how its done, thanks

---

### Post by jeremy1138 on 2007-08-10
Hi I have an hp laptop model # dv5020us.  This laptop has the amd turion 64 bit uprocessor and the ati radeon xpress 200m video card.  I got compiz to install per the instructions on this thread but it doesn't seem to do anything to my computer...  I can get to the configuration screen and I got through the install with no errors but I don't know what to do now...  Does anyone have any ideas?  Do I need to have that xgl or whatever it is installed?  Thanks for any help anyone can give!

---

### Post by siralphred on 2007-08-10
> **jeremy1138 said:**
> Hi I have an hp laptop model # dv5020us.  This laptop has the amd turion 64 bit uprocessor and the ati radeon xpress 200m video card.  I got compiz to install per the instructions on this thread but it doesn't seem to do anything to my computer...  I can get to the configuration screen and I got through the install with no errors but I don't know what to do now...  Does anyone have any ideas?  Do I need to have that xgl or whatever it is installed?  Thanks for any help anyone can give!

i have a similar notebook but with nvidia, and i had to enable desktop effects for it to work, if not then u wanna try to various commands to invoke compiz   ie    compiz --replace  and the other variants  also did u follow the guide for the 64bit? jus double checking. and another thing is  even though on the notebook there is a logo saying  Turion64x2 it is still a 32bit notebook so pls double check dat before  good luck

---

### Post by jackhynes on 2007-08-10
Okay that seems to have broken my compiz... I'm just gonna try a restart now...

---

### Post by jackhynes on 2007-08-10
Restarting X didn't help -- too tired to try and fix it, anyone got a simple solution?

---

### Post by jeremy1138 on 2007-08-10
when I try to enable desktop effects I get an error that says "the composite extension is not available".  What do I do about that?  Also I'm sure that my laptop is a 64 bit machine...  I'm running a 64 bit linux version and I pay dearly for it every time i try to get something to work...  Is there a tutorial somewhere specifically for a 64 bit machine?  Could someone post a link?  Any other suggestions would be greatly appreciated!

---

### Post by siralphred on 2007-08-10
> **jeremy1138 said:**
> when I try to enable desktop effects I get an error that says "the composite extension is not available".  What do I do about that?  Also I'm sure that my laptop is a 64 bit machine...  I'm running a 64 bit linux version and I pay dearly for it every time i try to get something to work...  Is there a tutorial somewhere specifically for a 64 bit machine?  Could someone post a link?  Any other suggestions would be greatly appreciated!

i will suggest you get xgl working then, i am not very familiar with ati but i remember my friend having to go through hell before he got it working, ur graphic is very  notorious hehe but the xgl should work so find a guide for that

---

### Post by jeremy1138 on 2007-08-10
ok I just tried this command:

compiz --replace -c emerald &

and I got this out:[1] 8311
Checking for Xgl: jeremy@jeremy-laptop:~$ not present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
metacity: Unknown option -c

What does this mean?  Also I have installed xgl but I can't get that to work either...  When I try to start my session with xgl the screen gets all garbled with horizontal lines and I can't see a thing...  Any ideas anyone?  I'd be very thankful for any help...

---

### Post by siralphred on 2007-08-10
> **jeremy1138 said:**
> ok I just tried this command:

compiz --replace -c emerald &

and I got this out:[1] 8311
Checking for Xgl: jeremy@jeremy-laptop:~$ not present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
metacity: Unknown option -c

What does this mean?  Also I have installed xgl but I can't get that to work either...  When I try to start my session with xgl the screen gets all garbled with horizontal lines and I can't see a thing...  Any ideas anyone?  I'd be very thankful for any help...

watever guide u used to install the xgl make sure ur graphic card is supported

---

### Post by Scott00 on 2007-08-10
Question... Other guides tell you to remove desktop effects first, is this a required step? and if so it removed ubuntu-desktop as well. When you install ubuntu-desktop again it will reinstall desktop effects with it. Is this OK?

---

### Post by siralphred on 2007-08-10
do a google search for "install xgl for ati xpress 200"  and also u may want to install beryl instead of compiz cos like i said i had a friend with similar notebook and really went through hell to get it working.....maybe compiz dont play well if that card

---

### Post by djrobthaman on 2007-08-10
Hey there,

I tried to install compiz fusion from trevino's repositories but when I added them couldn't actually find any compiz fusion files (highly irregular).  I noticed that up until recenly this how-to recommended using those repos.  I installed it suing the new how-to and it works but compiz is really unstable.  Trev's version was 100% rock solid (almost:) )  Anybody know what happened to his repos, or if I'm just dumbb and did something wrong?

Thanks

---

### Post by jeremy1138 on 2007-08-10
yes the guide that I used to install xgl listed my card as supported and xgl did work for a while but then I messed around with installing the correct driver for my video card and now it doesnt work...  The ati proprietary driver works and I can use the ATI config panel and all that but I can't get xgl, beryl or compiz to work...  The settings panel for compiz will open and I can set the number of desktops that I have and that works fine but I can't get the desktop cube or any of the effects to work...

---

### Post by djrobthaman on 2007-08-10
Hello again,

I had another quick question.  For some reason compiz-core is supposed to be upgradable but when I check it says that the new version is the same as the installed version.  So unless I lock the package I have a perpetual upgrade icon on my gnome panel.   Anyone know how to fix that?

Thanks again

---

### Post by jeremy1138 on 2007-08-10
> **djrobthaman said:**
> Hello again,

I had another quick question.  For some reason compiz-core is supposed to be upgradable but when I check it says that the new version is the same as the installed version.  So unless I lock the package I have a perpetual upgrade icon on my gnome panel.   Anyone know how to fix that?

Thanks again

I have the same problem...  The update icon is always there and I can install it all I want but it keeps coming back... I'm lost...

---

### Post by jackhynes on 2007-08-10
> **jeremy1138 said:**
> I have the same problem...  The update icon is always there and I can install it all I want but it keeps coming back... I'm lost...

Same here, plus my compiz is broken!

---

### Post by tekkenlord on 2007-08-10
I have the same problem with the compiz-core update. Also, what is the public key for amaranth's repositories?

---

### Post by Frak on 2007-08-10
> **jeremy1138 said:**
> yes the guide that I used to install xgl listed my card as supported and xgl did work for a while but then I messed around with installing the correct driver for my video card and now it doesnt work...  The ati proprietary driver works and I can use the ATI config panel and all that but I can't get xgl, beryl or compiz to work...  The settings panel for compiz will open and I can set the number of desktops that I have and that works fine but I can't get the desktop cube or any of the effects to work...
ATi drivers suck out loud. Use the open source ones, they work much better.

---

### Post by janbockaert on 2007-08-10
same problem, compiz keeps updating itself. Also, Why was the post updated? The trevino repo was the only-one i used on ubuntu that had no problems with the cube. And it looks like it had a lot more plugins?

---

### Post by janbockaert on 2007-08-10
according to trevino's blog (or the babelfishtranslation of his blog - i don't speek Italian:)), he is on holiday, and you can keep updating fusion with the makefusiondebs (i guess in his repositories).

---

### Post by Paul133 on 2007-08-10
Now I'm confused. I installed Compiz Fusion earlier today following this guide: [http://ubuntu1501.blogspot.com/2007/08/compiz-fusion-in-fiesty-with-xgl.html](http://ubuntu1501.blogspot.com/2007/08/compiz-fusion-in-fiesty-with-xgl.html) Not sure what the reps were. Should I reinstall Compiz Fusion using Amaranth's reps?

---

### Post by Vorian on 2007-08-10
Amaranth is the Ubuntu Developer and Maintainer for Compiz.  I think the choice is fairly easy. :)

---

### Post by gtrtx on 2007-08-10
I used the updated instructions and upgraded CF(was previously using the Trevino repos). I had several issues after I did this:

-compiz-core update that won't go away(as mentioned above)

-Unable to log out -- caused my Desktop to freeze. I was able to log in via ssh and kill Xorg.

-compiz-replace won't work with xfce

-video from TV-tuner card slightly choppy.

Prior to this I had very little trouble with my system. I was up for over a week without incident. 

I've since reverted back to the Trevino repos and everything appears to be working fine again.....

Just thought I'd share my experience in case others had similar issues.

---

### Post by Apex-jb on 2007-08-10
So exactly which steps do i follow and which one do I stop at if I installed CF from the old guide? Do I just change the repo.?

---

### Post by Arthur Archnix on 2007-08-10
Rotate cube not working. Other effects are. It's enabled... is something broken?

---

### Post by Scott00 on 2007-08-10
I keep getting the same version I already have in update manager with this repo..  WTF?

---

### Post by bmannering on 2007-08-10
Hello. I have just installed compiz. But nothing is running none of the effects are present and as with a couple others my update manager says i have a compiz update even though I installed it. I need help, thanks.

---

### Post by bakster on 2007-08-11
Same here.I locked package compiz-core but it doesn't help.

---

### Post by atomicscissors on 2007-08-11
So I tried to install Compiz Fusion last night using the "old" way that was described in the first post before it was updated.  Everything worked except I didn't have my window decorations.

When I saw the new Amaranth way of installing CF today, I followed it and now nothing works!

I haven't been getting the update icon like some users have reported but when I go to System > Administration > Update Manager it does tell me to upgrade and when I do and it finishes, it continues to tell me to upgrade.

Plus when installing and upgrading Compiz Fusion the system tells me that the software can not be authenticated.  Anyone else experience this?

---

### Post by Frak on 2007-08-11
The authentication just means you don't have the GPG key for that software.

---

### Post by atomicscissors on 2007-08-11
> **Frak said:**
> The authentication just means you don't have the GPG key for that software.

How does one get the GPG key?

---

### Post by Frak on 2007-08-11
Well since the .asc file wasn't included in the howto, I couldn't tell you.
All a GPG ([GNU Privacy Guard]("http://en.wikipedia.org/wiki/GNU_Privacy_Guard")) is just a safeguard to make sure the software isn't malicious. You can just ignore the warnings if you know its safe.

---

### Post by isaacj87 on 2007-08-11
It's really annoying...compiz fusion from this repo isn't as good from trevinos...my settings won't save, my wobbly windows are really weird and it keeps telling me to update the version I already have installed!?

Ahhhh...this version is sooo frustrating...everything seems broken...

---

### Post by Frak on 2007-08-11
Well if they were built right, there should be absolutely no difference, exept...
I heard about a recent change in the latest update that doesn't work well with Feisty's Kernel.

---

### Post by Scott00 on 2007-08-11
> **isaacj87 said:**
> It's really annoying...compiz fusion from this repo isn't as good from trevinos...my settings won't save, my wobbly windows are really weird and it keeps telling me to update the version I already have installed!?

Ahhhh...this version is sooo frustrating...everything seems broken...

I agree, this one sucks. What are the steps to go back to trevinos or some other better one without screwing anything up?

---

### Post by isaacj87 on 2007-08-11
I hate that we're not getting updates...I like trevinos repo, it's stable and easy, but like I said no updates...I don't like amaranth's so I just gave up and went back to trevinos....

Just edit your /etc/apt/sources.list
and remove amaranth's repo
re-add trevinos repo (i just commented it out so i could have it if i needed it, if you deleted the lines in your sources.list just google "trevinos repo" and on his site it tells you how to add his repo)

completely remove all traces of compiz and emerald

do a sudo apt-get update

and then reinstall compiz and it should be back to regular trevinos!

---

### Post by ayoli on 2007-08-11
> **Vorian said:**
> Amaranth is the Ubuntu Developer and Maintainer for Compiz.  I think the choice is fairly easy. :)

that's good point, but what about the problems mentioned above ?

---

### Post by walkerk on 2007-08-11
> **ayoli said:**
> that's good point, but what about the problems mentioned above ?

everything works fine. my only issues is the update compiz-core never going away. 

ccsm remembers my settings w/out problem (I did need to go back in there and make all the settings again, but that is to be expected with a fresh install)

for people trying to use emerald.. this line doesn't seem to work anymore:
```
compiz --replace -c emerald &
```

instead you can make a small script, effects.sh:
```
#/bin/bash
compiz --replace &
sleep 2
emerald --replace &
```

make that script executable:
```
chmod +x effects.sh
```

now run that script at startup (or whenever you like):
```
/path/to/effects.sh
```

Compiz Fusion w/ Emerald

---

### Post by ayoli on 2007-08-11
> **walkerk said:**
> everything works fine. my only issues is the update compiz-core never going away. 

ccsm remembers my settings w/out problem (I did need to go back in there and make all the settings again, but that is to be expected with a fresh install)

for people trying to use emerald.. this line doesn't seem to work anymore:
```
compiz --replace -c emerald &
```

instead you can make a small script, effects.sh:
```
#/bin/bash
compiz --replace &
sleep 2
emerald --replace &
```

make that script executable:
```
chmod +x effects.sh
```

now run that script at startup (or whenever you like):
```
/path/to/effects.sh
```

Compiz Fusion w/ Emerald

To keep my config i use a flat file config so it's easy to backup it (in ccsm go to profile & backend choose "flat file configuration backend" and now your config is in ~/.compizconfig).
But the never going away update issue is really annoying

---

### Post by walkerk on 2007-08-11
> **ayoli said:**
> To keep my config i use a flat file config so it's easy to backup it (in ccsm go to profile & backend choose "flat file configuration backend" and now your config is in ~/.compizconfig).
But the never going away update issue is really annoying

Yea, I just commented out the repos in my sources.list.. I'll wait until the issue is resolved as I don't really care about most of the new plugins.. Who really uses them?

---

### Post by Amaranth on 2007-08-11
[LIST]
[*]The constant upgrade thing is a problem with the PPA system. Hopefully it'll be fixed soon.
[*] The only time I've seen crash on logout is when using the nvidia 100.14.11 drivers.
[*] For problems with settings not taking effect or not working right try running this to reset your settings to stock:```
gconftool-2 --recursive-unset /apps/compiz && rm -rf .compiz .compizconfig
``` After that things should work alright.
[*] You can use this with KDE just install it like this:```
sudo apt-get install compiz compiz-kde compizconfig-settings-manager
``` Specifing compiz-kde will make apt choose it over compiz-gnome to resolve the dependency and compiz-kde also pulls in the kconfig backend for libcompizconfig.
[*] As for my repo not being signed, that's by design. You cannot sign PPA repos. It's to make it obvious what software you're using isn't official.
[*] Also, I only include things we have in gutsy. We don't have the -unsupported set of plugins because they are, obviously, unsupported upstream. The -unofficial package Trevinho has is even worse, the plugins in -unsupported are at least guaranteed to compile. We currently do not have an emerald-themes package in gutsy but the one in feisty should work fine. We don't have fusion-icon because it's not needed.
[/list]

---

### Post by Amaranth on 2007-08-11
Oh, and if you previously used Trevinho's repo you have to compltely purge his packages before using mine.```
sudo apt-get --purge remove compiz* libcompizconfig*
```

---

### Post by vortex_noob on 2007-08-11
I installed compiz fusion without a hitch using the guide in this thread (thank you!). I've used Beryl before trying this out.

I've tried compiling using CF-Updater (somewhere in this forum) to no avail. 

Everything work fine except for the CompizConfig Settings Manager. I can't seem to access the general settings. Some (if not all) other configuration can be accessed. What do u think is the main culprit?

I also would like to change the skydome image, and the image behind the cube and the level of transparency in the cube. Anyone can tell me how?

Btw, in Beryl there is a glitch that I cant move windows to another viewport using the right-click on the title-bar like metacity. Fixed it by downgrading the libwnck to earlier version. In CompizFusion, same thing happened but I still cant access it even when I downgraded the libwnck package. Anyone have any idea?

Seems like a lot of questions, huh? Any help will be much appreciated.

Thanks!

---

### Post by ayoli on 2007-08-11
> **vortex_noob said:**
> I installed compiz fusion without a hitch using the guide in this thread (thank you!). I've used Beryl before trying this out.

I've tried compiling using CF-Updater (somewhere in this forum) to no avail. 

Everything work fine except for the CompizConfig Settings Manager. I can't seem to access the general settings. Some (if not all) other configuration can be accessed. What do u think is the main culprit?

I also would like to change the skydome image, and the image behind the cube and the level of transparency in the cube. Anyone can tell me how?

Btw, in Beryl there is a glitch that I cant move windows to another viewport using the right-click on the title-bar like metacity. Fixed it by downgrading the libwnck to earlier version. In CompizFusion, same thing happened but I still cant access it even when I downgraded the libwnck package. Anyone have any idea?

Seems like a lot of questions, huh? Any help will be much appreciated.

Thanks!
when a window have focus, hold <Ctrl><Alt><Shift> and left arrow OR right arrow to move it on the left or right viewport.

---

### Post by isaacj87 on 2007-08-11
> **Amaranth said:**
> Oh, and if you previously used Trevinho's repo you have to compltely purge his packages before using mine.```
sudo apt-get --purge remove compiz* libcompizconfig*
```

I tried that in terminal, and it gave me an error...

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compiz.sh~


---

### Post by couzin2000 on 2007-08-11
> **walkerk said:**
> Nice write up. I'm now running Compiz Fusion on a Dell 6400 w/ intergrated 945GM video. :D

ok, WalkerK, I've got the same setup, I ran thru the same steps as described, but mine won't start - it just instantly reverts back to Metacity. Everything seems installed, but nothing works. Also, I,ve got the Ubuntu update notification icon always on, and no matter how many times I run it, it just won't update the file: compiz-core 1:0.5.2-0ubuntu2-ppal. 

What am I missing here?

EDIT: tried running compiz --replace, here's what I got:

```
sebastien@sebastien-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Converting gconf plugin list: '' 
Checking for nVidia: not present. 
Checking for Xgl: not present. 
Segmentation fault (core dumped)

(gtk-window-decorator:6559): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6559): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6559): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6559): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6559): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6559): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6559): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6559): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6559): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6559): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6559): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6559): Wnck-WARNING **: Unhandled action type (nil)

```

---

### Post by jantmm on 2007-08-11
Hi,

I'm an Ubuntu newbie and I am having the same problem as couzin2000, I ran the steps as described but when I am running compiz --replace I'm getting the following output

```

Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
aborting and using fallback: /usr/bin/metacity 

```

On the other hand, I'm having an update notification but despite of installing it several times the notification does not disappear.
```

compiz-core (versión1:0.5.2-0ubuntu2~ppa1) será actualizado a la versión 1:0.5.2-0ubuntu2~ppa1

```

Any ideas, thx in advance.

---

### Post by Frak on 2007-08-11
I got a similar warning as above as couzin2000.

P4 1.8GHz
512MB
Geforce FX 5500

Compiz Fusion does work, because I've gotten it to work before.

```
frak@frak-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Converting gconf plugin list: '' 
Checking for nVidia: present. 
Checking for Xgl: not present. 

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)
Backend     : ini
Integration : true
Profile     : default
Adding plugin animation (animation)
Adding plugin mblur (mblur)
Adding plugin cube (cube)
Adding plugin opacify (opacify)
Adding plugin dbus (dbus)
Adding plugin resize (resize)
Adding plugin text (text)
Adding plugin splash (splash)
Adding plugin rotate (rotate)
Adding plugin group (group)
Adding plugin trailfocus (trailfocus)
Adding plugin addhelper (addhelper)
Adding plugin zoom (zoom)
Adding plugin cubereflex (cubereflex)
Adding plugin screenshot (screenshot)
Adding plugin extrawm (extrawm)
Adding plugin annotate (annotate)
Adding plugin minimize (minimize)
Adding plugin ring (ring)
Adding plugin expo (expo)
Adding plugin scaleaddon (scaleaddon)
Adding plugin regex (regex)
Adding plugin move (move)
Adding plugin plane (plane)
Adding plugin thumbnail (thumbnail)
Adding plugin inotify (inotify)
Adding plugin glib (glib)
Adding plugin showdesktop (showdesktop)
Adding plugin svg (svg)
Adding plugin blur (blur)
Adding plugin vpswitch (vpswitch)
Adding plugin scale (scale)
Adding plugin imgjpeg (imgjpeg)
Adding plugin crashhandler (crashhandler)
Adding plugin fadedesktop (fadedesktop)
Adding plugin fade (fade)
Adding plugin put (put)
Adding plugin wobbly (wobbly)
Adding plugin water (water)
Adding core settings (General Options)
Adding plugin video (video)
Adding plugin fs (fs)
Adding plugin png (png)
Adding plugin snap (snap)
Adding plugin clone (clone)
Adding plugin switcher (switcher)
Adding plugin bench (bench)
Adding plugin place (place)
Adding plugin firepaint (firepaint)
Adding plugin neg (neg)
Adding plugin reflex (reflex)
Adding plugin decoration (decoration)
Adding plugin wall (wall)
Adding plugin winrules (winrules)
Adding plugin resizeinfo (resizeinfo)
Initializing core options...done

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)
Initializing resize options...done
Initializing zoom options...done
Initializing move options...done
Initializing svg options...done
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Initializing video options...done
Initializing switcher options...done
Initializing place options...done
Initializing neg options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
Initializing decoration options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
Initializing wall options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
Segmentation fault (core dumped)
```

Any Ideas.

---

### Post by Zalbor on 2007-08-11
I did this, but there's a problem: the package compiz-core always wants to upgrade to its currently installed version. i.e. the icon about the update notifications appears, compiz-core is there, but even if I "upgrade" it remains there. Please fix this.

---

### Post by Frak on 2007-08-11
They're trying, its a bug.
@Vorian
You should place a disclaimer on the front page warning about the updates.

---

### Post by walkerk on 2007-08-11
n/m. i see that it tried indirect-rendering automatically. :/

---

### Post by jantmm on 2007-08-11
Hi, solved the issue with running compiz. I've added the following lines to xorg.conf file:

```
Section "Extensions"
Option "Composite" "Enable"
EndSection
```

---

### Post by appzattak on 2007-08-11
I have the desktop effects working rather well, without doing any of the stuff in this thread. In the past I did this tut and some stuff stopped working, shoudl I aplly this if I already have most features working out of the box?

---

### Post by Frak on 2007-08-11
IMHO, I would recommend you stay with what you have now. I tried switching and it just broke some packages and annoys me with updates.

---

### Post by jackhynes on 2007-08-11
> **jantmm said:**
> Hi, solved the issue with running compiz. I've added the following lines to xorg.conf file:

```
Section "Extensions"
Option "Composite" "Enable"
EndSection
```

Has no effect for me. Still receiving the same error output as above. There should definitely be a warning on the post considering the amount of people this has effected!

---

### Post by techstop on 2007-08-11
I have come back to ubuntu after a short break with a fresh install of feisty, plus the nvidia driver. I thought I would try Compiz Fusion after reading about the "de-forking" of Beryl. I have just wasted a couple of hours trying to get it working. My issues are;

-window decorations don't work on my main monitor (I have set up the startup script posted above) until I go to a terminal and run 'emerald --replace'
-window decorations don't work at all on my second monitor, no matter what (I have a dual monitor setup without twinview, ie two independent desktops)
-emerald theme manager seems broken somehow, themes do not get applied when I select them, and occasionally it reverts back to some standard theme
-slow menus on my second desktop (the one without window decorations)

It is very disappointing. This whole compiz / beryl / compiz fusion thing seems to be going around in circles. We are now in a situation that is worse than the very early days of beryl IMHO. I hope the situation improves, because it has only gotten worse since I ran beryl successfully on edgy a year or so ago. I'll uninstall and wait for further progress. :rolleyes:

Otherwise, there seems to be an improvement in performance, but that is the only encouraging sign. On the whole, very disappointed with compiz fusion.

---

### Post by satkata on 2007-08-12
I have just upgraded my compiz* packages from the new repository and everything is working like a charm as before.

As the guide says, you should remove every previously installed compiz-related package and after that install the new ones.

I did that from the console, because I thought it would probably be weird to remove compiz while running compiz and I didn't want to mess the things up.

BTW, what's with the unofficial and unsupported fusion packages, have they been merged into the main package, because there no such anymore.

The only thing is, that some of my previously enabled plugins were disabled or with changed configuration, like window-decorations and some other stuff, which make me think some bad things, but after enabling them again, it was all fine. Also the "Virtual Desktop Size" was reset to 2 and I had to correct this. But these are minor things, I think everybody should check his configuration to see if everything is as before and eventually correct it.

The only very annoying thing is the update-icon for the compiz-core package, which always wants to update itself.

I hope this will get fixed soon.

---

### Post by eeeeepuk on 2007-08-12
Just upgraded to the new ropistory, and everything is working - well, nearly. The big problem for me is that the workarounds plugin has vanished. This plugin let me run MythTV at the same time as compiz fusion without having Gnomes panels visible at all times.

If anyone knows any other workarounds to the Mythtv/Compiz problem please let me know, and please consider adding the plugin back in!

---

### Post by ayoli on 2007-08-12
maybe we can play with [this]("http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin") to avoid this compiz-core update til there is a proper fix for this problem.
I'lll try it out when i'll have time tonight or tomorrow.

---

### Post by erfahren on 2007-08-12
I got this working with my fglrx driver with XGL session, (originally using [jtraub's guide](http://ubuntuforums.org/showthread.php?t=482773) ). This one was much more CPU intensive for me though. XGL was using ~60% when I didn't have any windows open. I installed the new driver with Envy, and also tried resetting the configurations back to default as per [Amaranth's post](http://ubuntuforums.org/showpost.php?p=3171088&postcount=619).

I reverted back to Treviño&#8217;s until I see some more folks get this working well with similar ati cards.

I did notice that when I first purged Treviño&#8217;s packages it took out ubuntu-desktop as well so I brought that back after installing the new packages. I also noticed that it replaced libdecoration when I did a apt-get upgrade before installing the new packages (it got updated with Treviño&#8217;s packages -- jtraub mentions that at the bottom of his guide). I don't know if that means anything.

---

### Post by houms on 2007-08-12
I got it working really good.  I can do all the options... Takes some time to figure out all the "options", but well worth it I followed this howto,
[http://erusan.googlepages.com/ubuntuhowto.html#nvidia](http://erusan.googlepages.com/ubuntuhowto.html#nvidia)
Worked flawlessly with my nvidia 5200 on a inspiron laptop.EXCEPT, instead of running 
compiz --replace
 I ran 
compiz --replace --indirect-rendering
With compiz --replace I was getting a lot of bad behavior like black windows, menus showing up black if they were opened over an active window, I was disappointed until i tried the above command....
Now I just added it to the session startup and it works beautifully...

---

### Post by petit.padavoine on 2007-08-12
Great how-to, but you forgot to include the command to install the compiz fusion plugins packages :D.

sudo apt-get install compiz-fusion-plugins-*

---

### Post by AriciU on 2007-08-12
> **Frak said:**
> I got a similar warning as above as couzin2000.

P4 1.8GHz
512MB
Geforce FX 5500

Compiz Fusion does work, because I've gotten it to work before.

```
frak@frak-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Converting gconf plugin list: '' 
Checking for nVidia: present. 
Checking for Xgl: not present. 

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)
Backend     : ini
Integration : true
Profile     : default
Adding plugin animation (animation)
Adding plugin mblur (mblur)
Adding plugin cube (cube)
Adding plugin opacify (opacify)
Adding plugin dbus (dbus)
Adding plugin resize (resize)
Adding plugin text (text)
Adding plugin splash (splash)
Adding plugin rotate (rotate)
Adding plugin group (group)
Adding plugin trailfocus (trailfocus)
Adding plugin addhelper (addhelper)
Adding plugin zoom (zoom)
Adding plugin cubereflex (cubereflex)
Adding plugin screenshot (screenshot)
Adding plugin extrawm (extrawm)
Adding plugin annotate (annotate)
Adding plugin minimize (minimize)
Adding plugin ring (ring)
Adding plugin expo (expo)
Adding plugin scaleaddon (scaleaddon)
Adding plugin regex (regex)
Adding plugin move (move)
Adding plugin plane (plane)
Adding plugin thumbnail (thumbnail)
Adding plugin inotify (inotify)
Adding plugin glib (glib)
Adding plugin showdesktop (showdesktop)
Adding plugin svg (svg)
Adding plugin blur (blur)
Adding plugin vpswitch (vpswitch)
Adding plugin scale (scale)
Adding plugin imgjpeg (imgjpeg)
Adding plugin crashhandler (crashhandler)
Adding plugin fadedesktop (fadedesktop)
Adding plugin fade (fade)
Adding plugin put (put)
Adding plugin wobbly (wobbly)
Adding plugin water (water)
Adding core settings (General Options)
Adding plugin video (video)
Adding plugin fs (fs)
Adding plugin png (png)
Adding plugin snap (snap)
Adding plugin clone (clone)
Adding plugin switcher (switcher)
Adding plugin bench (bench)
Adding plugin place (place)
Adding plugin firepaint (firepaint)
Adding plugin neg (neg)
Adding plugin reflex (reflex)
Adding plugin decoration (decoration)
Adding plugin wall (wall)
Adding plugin winrules (winrules)
Adding plugin resizeinfo (resizeinfo)
Initializing core options...done

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:29801): Wnck-WARNING **: Unhandled action type (nil)
Initializing resize options...done
Initializing zoom options...done
Initializing move options...done
Initializing svg options...done
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Initializing video options...done
Initializing switcher options...done
Initializing place options...done
Initializing neg options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
Initializing decoration options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
Initializing wall options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
Segmentation fault (core dumped)
```

Any Ideas.

Don't blame the repo ;)

You need the latest libwnck installed... that's why those errors appear (wnck-warning). apt-get install libwnck and libwnck-dev (if it exists of course).

---

### Post by Frak on 2007-08-12
Thanks, I'll try that, I was about to reinstall (again...) anyways, so I didn't worry about it.

---

### Post by Boshetunmay on 2007-08-12
Sorry, didn't check all the 65 pages for whether this question was already asked...
When I use the blur plugin after some random time all the transparent surfaces turn to opaque grey (I use alpha blur rather than focus blur). I haven't noticed any connection with my actions. When I disable and then re-enable the blur plugin, everything goes back to normal state. No blur settings seem to affect the situation. I read somewhere that disabling video playback plugin may help, but no luck.
Any solutions?

---

### Post by AriciU on 2007-08-12
> **Frak said:**
> Thanks, I'll try that, I was about to reinstall (again...) anyways, so I didn't worry about it.

libwnck-dev not libwnck btw.

---

### Post by Frak on 2007-08-12
OK thanks.

---

### Post by steveneddy on 2007-08-12
This is the worst version yet! I noticed that I haven't been getting the updates for fusion so there was a notice of updated repos for fusion. OK - I've never had a problem before, even with Beryl.

Boy - you guys toasted it this time. The system says there is an update available but it won't install it even after I DL it.

The video is choppy and tearing, it locks up and, well, this thing is a POS now.

I was always very happy with the last version with Trevinio's repos, and it was working very well. 

What happened?

I'm locking this version in my sources list until there is a fix.

Do something about this in a hurry or I'm going back to a version of Beryl that I saved, a version before the "merger".

---

### Post by Frak on 2007-08-13
Works fine for me... now...

---

### Post by petit.padavoine on 2007-08-13
Stevendeddy I totally agree.
This repo
1. Has very little plugins
2. Keeps saying there's an update to compiz-core when there isn't
3. Has nothing better than the others.
Why should we use it?

---

### Post by ayoli on 2007-08-13
> **petit.padavoine said:**
> Stevendeddy I totally agree.
This repo
1. Has very little plugins
2. Keeps saying there's an update to compiz-core when there isn't
3. Has nothing better than the others.
Why should we use it?

i guess because:
> **Vorian said:**
> Amaranth is the Ubuntu Developer and Maintainer for Compiz.  I think the choice is fairly easy. :)
;)

---

### Post by Vorian on 2007-08-13
There are two important things to note.
1) Compiz with Fusion plugins will be available in Gutsy in two months
2) If you want Compiz Fusion with feisty, you have two options -(a) compile the packages yourself or (b) use a third party repository.

Amaranth has the most trusted repository, again, as he is the developer and maintainer for compiz.  

There are plenty of guides and repositories available.  However, I feel it is important to advise people on what the most reliable and trusted way to install compiz with fusion plugins via 3rd party repository.

Ideally, a person would just compile the packages from the source.

<2cent>

---

### Post by bluetrevian on 2007-08-13
Hey Vorian great post. Worked almost perfectly the first time, but you left out the plugins on your original instructions... what gives!?!

```
sudo apt-get --purge remove compiz* libcompizconfig*

sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install compiz compizconfig-settings-manager compiz-fusion-plugins-extra

compiz --replace -c emerald &
```

Thanks again!

---

### Post by Azakus on 2007-08-13
Compiz fusion is officially released now (version 0.5.2).
[http://smspillaz.wordpress.com/2007/08/13/compiz-fusion-our-first-release-052/](http://smspillaz.wordpress.com/2007/08/13/compiz-fusion-our-first-release-052/)

---

### Post by vapore0n on 2007-08-13
soo...
not that a final release is out, anyone know how to install it? since all the instructions point to an outdated source

---

### Post by Frak on 2007-08-13
[You may want to just compile it from source.]("http://ace2016.net/tutorials/linux/how-to-install-compiz-fusion")

---

### Post by isaacj87 on 2007-08-13
Interesting...that link gave another link to tarballs...

Is Amaranth's repo updated to the latest version?

---

### Post by walkerk on 2007-08-13
> **isaacj87 said:**
> Interesting...that link gave another link to tarballs...

Is Amaranth's repo updated to the latest version?

It's stable. I doesn't have the unsupported plugins.. only the stuff that will be released with Gutsy.

---

### Post by isaacj87 on 2007-08-13
> **walkerk said:**
> It's stable. I doesn't have the unsupported plugins.. only the stuff that will be released with Gutsy.

I see, is there a repo available that has 0.5.2 with all of the unsupported plugins? I really want to try their release without having to download all the tarballs.

---

### Post by walkerk on 2007-08-13
> **isaacj87 said:**
> I see, is there a repo available that has 0.5.2 with all of the unsupported plugins? I really want to try their release without having to download all the tarballs.
trevino keeps pretty up to date: [http://ubuntuforums.org/showthread.php?t=481615&highlight=trevino+compiz+fusion](http://ubuntuforums.org/showthread.php?t=481615&highlight=trevino+compiz+fusion) :)

---

### Post by Vorian on 2007-08-13
I just added links to the tarballs on the OP for those that want to compile the first release.

(at the bottom)

---

### Post by isaacj87 on 2007-08-13
I check one of those tarballs...it doesn't seem like you have to compile anything...there's a python script inside that just installs?? If I do it that way I can't upgrade...can someone tell me how to uninstall if I choose to use the tarballs?

EDIT: My apologies...seems to only be that way with the CCSM...but even so...how would I go about uninstall the compiled version?

---

### Post by clintonthegeek on 2007-08-13
Installing 0.5.2 from your repositories JUST now works great EXCEPT that KWM keep freezing whenever I start compiz! I can't get any window-decorations going. :(

Here's the dubug info from the KDE Crash Handler - [http://pastebin.com/m325e5d64](http://pastebin.com/m325e5d64)

Any ideas?

-Clinton

EDIT: Silly me... I should be using Emerald anyways! Lemme just figure out how to get that going ;)

---

### Post by fredzer on 2007-08-13
i installed it fine and it all looks fine but nothing actually works 
i push the buttons and nothing changes at all 

but i get the errors
```

Checking for Xgl: not present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present.
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```
:(

help would be appreciated

---

### Post by Frak on 2007-08-13
Which version of Ubuntu are you running.

---

### Post by Tomkin on 2007-08-13
I type "compiz --replace" into the run prompt and nothing happens. Unless compiz starts up instantly and looks and acts exactly like Kubuntu Feisty. Can someone help?

Oh, and what directory is the config application in? I want to assign it to a keyboard shortcut in KDE.

---

### Post by joshuachad on 2007-08-13
Ok, Im not an expert on Compiz but i did mange to get it running so Ill give a crack at fixing this.
1. Make sure you have Xgl installed and also make sure you load it with your session. If you just intalled Xgl from synaptic it does nothing for ya unless you create a session for it or customize you gdm. 
Here is a link that has great instructions for all of the above which i used. All this needs to be done prior to installing compiz or Beryl. So if you dont have Xgl installed & configured properly i would uninstall Beryl, compiz, emerald etc. and complete the first steps then reinstall. You will most likely have to edit your xorg.conf file also which is covered in the below links. Basically everything you need to get going is found there.

for Nvidia cards: [http://compiz.org/NVidia](http://compiz.org/NVidia)
for ATI cards: [http://compiz.org/ATI](http://compiz.org/ATI)
For Intel cards: [http://compiz.org/Intel](http://compiz.org/Intel)

Once you have that squared away install compiz thru synaptic and you should be square. Personally I control every thing thru Beryl-manager which you can also intall and it lets you enable indirect-rendering, pixmaps etc etc. And you can swap between window managers on the fly. It works really well for me in feisty. If you have any questions getting going let me know.

---

### Post by Frak on 2007-08-13
Nvidia users don't need Xgl because a modded version of AIGLX is built into the driver.

---

### Post by atomicscissors on 2007-08-13
> **joshuachad said:**
> 
for Nvidia cards: [http://compiz.org/NVidia](http://compiz.org/NVidia)


I followed this and now Compiz Fusion works!  Woo hoo!

---

### Post by erfahren on 2007-08-13
> **fredzer said:**
> i installed it fine and it all looks fine but nothing actually works 
i push the buttons and nothing changes at all ...


What video card do you have? (you can find out by typing " lspci " into the terminal and look for something like "VGA compatible controller".)

If your card is an ATI you can use the old guide to set up an XGL session: [http://ubuntuforums.org/showthread.php?t=482773](http://ubuntuforums.org/showthread.php?t=482773)

this guide (which is kind of the same) shows a way to run compiz-fusion at startup but with a short delay (it works better for me at least): [http://ubuntuforums.org/showthread.php?t=501925](http://ubuntuforums.org/showthread.php?t=501925)

---

### Post by Tomkin on 2007-08-13
It's telling me I need dbus-x11 or my xsession will terminate on startup, but I can't find dbus-x11 with Adept.

On a mostly unrelated note, trying to access openGL info causes my computer to reboot. Fun, fun, fun. ](*,)

EDIT: and the Intel page tells me nothing about Compiz, only which card I need to have.

EDIT2: And the Compiz-core package always appears to be upgradable, even though I intalled it less than one minute ago. ](*,) ](*,) ](*,)

---

### Post by Zettablade on 2007-08-13
> **Tomkin said:**
> And the Compiz-core package always appears to be upgradable, even though I intalled it less than one minute ago. ](*,) ](*,) ](*,)

Same for me

---

### Post by Frak on 2007-08-13
It's a bug, they're trying to solve it.

---

### Post by acowboydave on 2007-08-13
Installed Compiz, never got it to work right. Didn't uninstall it or should say remove it and installed Beryl and Beryl setting manager with Add and Remove. Now Compiz is working  can trade off with Beryl Manager as far as selecting window manager, is this wrong? Beryl works, Compiz works and can go back to Metacity

---

### Post by Tomkin on 2007-08-13
The page for XGL says those with Intel chips should use AIGLX instead, but I see no AIGLX page for Feisty. And how do I tell if my driver supports GLX_EXT_texture_from_pixmap?

EDIT: Wow, I missed the second line. It's been merged into Xorg.

EDIT2: ****, I screwed up my xorg.conf file like the idiot I am. Now when I boot up Kubuntu it gives me the Empty Command-Line of Death, no prompt character, nothing. What is the fastest way to reset it (or even better, get it to launch AIGLX correctly)? I have a non-screwed up Windows XP on the same machine, and if I can acces xorg.conf in a text editor I'll be fine, but I can't access my Linux partition from it right now... Am I totally screwed?

---

### Post by steveneddy on 2007-08-13
> **steveneddy said:**
> This is the worst version yet! I noticed that I haven't been getting the updates for fusion so there was a notice of updated repos for fusion. OK - I've never had a problem before, even with Beryl.

Boy - you guys toasted it this time. The system says there is an update available but it won't install it even after I DL it.

The video is choppy and tearing, it locks up and, well, this thing is a POS now.

I was always very happy with the last version with Trevinio's repos, and it was working very well. 

What happened?

I'm locking this version in my sources list until there is a fix.

Do something about this in a hurry or I'm going back to a version of Beryl that I saved, a version before the "merger".

I don't care who maintains the repo's for Compiz, trevinio's repos work better and have more stuff. Trevinio's repos were the one's I was using for Beryl and his always worked best.

I'm staying with Trevinio. I learned my lesson.

[Here's the best repo]("http://forum.compiz-fusion.org/showthread.php?t=1012"). Go to Trevinio.

Here's Trevinio's key

```
sudo wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -

```

After installing - copy this script and put it in your Home folder - 

```
 

#!/bin/sh

# click to start, click to stop

if pidof compiz.real | grep [0-9] > /dev/null
then
 exec metacity --replace
else
 exec compiz --replace -c emerald

fi

 
```

Name it fission,

Then make a launcher for your desktop or toolbar

in the launcher - to launch the script - browse for your script in the Home folder.

Use the icon provided here.

Good as gold. Now go use it and have fun.

---

### Post by boob11 on 2007-08-13
thnx

---

### Post by Frak on 2007-08-13
Instead of putting fission in the home directory, why not /usr/bin/? Then it could be run from the CLI from any directory.

---

### Post by steveneddy on 2007-08-13
> **walkerk said:**
> trevino keeps pretty up to date: [http://ubuntuforums.org/showthread.php?t=481615&highlight=trevino+compiz+fusion](http://ubuntuforums.org/showthread.php?t=481615&highlight=trevino+compiz+fusion) :)

Trevinio is the way to go here for the folks who want all of the extras.

It's well worth it.

---

### Post by steveneddy on 2007-08-14
Hey Frak? That's the Oklahoma warranty, FYI. LOL

All my advise comes with the _Texas_ Warranty: If it breaks you get to keep both pieces.

Should read **Oklahoma** warranty.

---

### Post by AriciU on 2007-08-14
The only way to go is to compile yourself from git every plugin that you want. I don't understand why you people insist on using someone's repo and end up depending on the guy when you could just as easily do it yourself !?

---

### Post by Frak on 2007-08-14
> **steveneddy said:**
> Hey Frak? That's the Oklahoma warranty, FYI. LOL

All my advise comes with the _Texas_ Warranty: If it breaks you get to keep both pieces.

Should read **Oklahoma** warranty.
You're just jealeous because Chuck Norris lives in Oklahoma ;)

---

### Post by luckyd on 2007-08-14
ok, im retarted and i switched repos without backing up my config :( Can one of you guys with a near vanilla install from trevino's repos give me your config settings file. I like his defaults better than this new repos.

edit: ps steveneddy your script always gives me metacity back, how can I fix this?

---

### Post by Frak on 2007-08-14
I have to agree, Travino's is faster, has more plugins, and doesn't bother me with updates.

---

### Post by morrius on 2007-08-14
Emerald not working with Compiz from new repo(((

---

### Post by erfahren on 2007-08-14
I mentioned in a previous post that I when tried Amaranth's packages my XGL's cpu usage was intensive so I reverted back to Trevino's. Someone mentioned that a new Compiz Fusion version was released yesterday so I decided to try Amaranth's again and it's working very well for me now.

I did clear out my old settings first by using the following as Amaranth suggested:
```

gconftool-2 --recursive-unset /apps/compiz && rm -rf .compiz .compizconfig

```
maybe that should be mentioned as a troubleshooting tip in the HowTo.

I had one question; purging the old packages removed the ubuntu-desktop and desktop-effects packages as well. I brought them back because [jtraub's HowTo](http://ubuntuforums.org/showthread.php?t=482773) mentioned it. How important is that though? Should that be included in this guide?

This one *is* working good for me though (just wanted to reiterate that). I think some of the unsupported or unofficial plugins in Trevino's made it a little buggy for me. (Sometimes the skydome and cubecaps wouldn't show and the cube wouldn't even initiate with the Ctrl+Alt+left).

---

### Post by Frak on 2007-08-14
I don't see the big deal about ubuntu-desktop, its just a meta-package. So if you have all of the apps that it provides, its just a waste of space, and removing it wouldn't change one thing.

---

### Post by ev5unleash1 on 2007-08-14
Yea, I put in these codes

```
deb http://ppa.dogfood.launchpad.net/amaranth/ubuntu feisty main restricted universe multiverse
deb-src http://ppa.dogfood.launchpad.net/amaranth/ubuntu feisty main restricted universe multiverse
```

But after the first one it said deb-src is not valid or something. And I only got some of the effects of Compiz. I very little amount. When I typed the first one in again is said deb is not valid I'm not sure how this is happening.

---

### Post by whiffy badger on 2007-08-14
I think that this update has really screwed up my Compiz fusion.  Approach with caution! 

[http://ubuntuforums.org/showthread.php?t=523892](http://ubuntuforums.org/showthread.php?t=523892)

---

### Post by isaacj87 on 2007-08-14
Just like everyone else here...I'm not too sure about Amaranth's repo (I don't mean to offend amaranth either). So, I went and explored other possible repos, such as the Repository of Shame, which is well maintained (even though it's for Sidux). But, I can't even install that version! My dependencies (libc6, libxml2, and so on) are not up-to-date enough to install Compiz-Fusion from that repo. I like the fact that Amaranth's repo is updated, but it's missing alot from the actual release of Compiz 0.5.2! And I know that many of us are hesitant to compile the latest version, and many, like myself, cannot do it due to lack of dependencies and the inability to install those dependencies...Does anyone have any suggestions on what we should do, it's kind of a shame that I'm still stuck at 0.5.1... :(

---

### Post by clintonthegeek on 2007-08-14
Yup, thirding the update problem.

I've tried clearing out my downloaded debs (apt-get clean), and it still downloads compiz-core, installs it, but still thinks it needs to be updated.

---

### Post by couzin2000 on 2007-08-14
From what I've been reading here, this entire thread has been launched *before* the Compiz-Fusion app was even stabilized, or to be politically correct -- launched _prematurely_.

I'm only starting out with this form of troubleshooting (through forums, I mean) so I haven't really checked for any other Howtos and such. But from what I understand, none of us would even be able to *compile* this app because of missing dependencies? Maybe we should start from scratch, then; how bout listing the dependencies, where to get them and how to install them; then going through the motions of *actually testing* the compile process, seeing if it works, listing troubleshooting issues, **THEN** posting all this stuff? Wouldn't this save a whole lotta pages on the forum?

I'm far from being the guy who should complain, but I'm just sending my 2¢ here. I've been trying up and down to make this work, and even my terminal is outta breath! Installed XGL, tried different versions, different repos... Perhaps settling on a way to show everybody how to do it would help?

---

### Post by isaacj87 on 2007-08-14
> **couzin2000 said:**
> 
I'm far from being the guy who should complain, but I'm just sending my 2¢ here. I've been trying up and down to make this work, and even my terminal is outta breath! Installed XGL, tried different versions, different repos... Perhaps settling on a way to show everybody how to do it would help?

Perhaps, I can help...I've got compiz fusion running both on aiglx and xgl. Could you tell me what video card you are using? It's one thing to have compiz fusion running and not have bleeding edge, but it's another to not even have it running at all! Which sucks!

If I knew your video card situation, maybe I could help you better. :)

---

### Post by Frak on 2007-08-14
> **couzin2000 said:**
> From what I've been reading here, this entire thread has been launched *before* the Compiz-Fusion app was even stabilized, or to be politically correct -- launched _prematurely_.

I'm only starting out with this form of troubleshooting (through forums, I mean) so I haven't really checked for any other Howtos and such. But from what I understand, none of us would even be able to *compile* this app because of missing dependencies? Maybe we should start from scratch, then; how bout listing the dependencies, where to get them and how to install them; then going through the motions of *actually testing* the compile process, seeing if it works, listing troubleshooting issues, **THEN** posting all this stuff? Wouldn't this save a whole lotta pages on the forum?

I'm far from being the guy who should complain, but I'm just sending my 2¢ here. I've been trying up and down to make this work, and even my terminal is outta breath! Installed XGL, tried different versions, different repos... Perhaps settling on a way to show everybody how to do it would help?
If you want to see what dependencies it needs, make a script in the Compiz Fusion tarball that contains this.

```
       strace -f -o /tmp/log ./configure
       # or make instead of ./configure, if the package doesn't use autoconf
       for x in `dpkg -S $(grep open /tmp/log|\
                           perl -pe 's!.* open\(\"([^\"]*).*!$1!' |\
                           grep "^/"| sort | uniq|\
                           grep -v "^\(/tmp\|/dev\|/proc\)" ) 2>/dev/null|\
                           cut -f1 -d":"| sort | uniq`; \
             do \
               echo -n "$x (>=" `dpkg -s $x|grep ^Version|cut -f2 -d":"` "), "; \
             done
```
chmod +x it and run it from the terminal, inside the source directory of the compiz fusion extracted tarball.
And download and install everything that ends with a -dev. And you might even consider doing a 
```
sudo apt-get build-dep <development package here>
```
to get it to work.

---

### Post by lawr_rawr on 2007-08-14
> **morrius said:**
> Emerald not working with Compiz from new repo(((

It should work if you start emerald with
```
emerald --replace
```
I had this problem after using Amaranth's repository, and it continued even after I removed the new stuff and reinstalled from Trevino's repository. 

(I was practically banging my head against the desk until I tried this super easy change... my compiz+emerald startup script did not include the "--replace", and I got errors about "no valid displays" or something similar when starting emerald manually)

---

### Post by steveneddy on 2007-08-14
> **luckyd said:**
> 
edit: ps steveneddy your script always gives me metacity back, how can I fix this?

This script isn't mine, and I can't remember where I got it, but it's on these forums.

But, the script should start Compiz-Fusion and Emerald at the same time. 

[Here is the original thread]("http://ubuntuforums.org/showthread.php?t=489341") about the script by the original author.

I find it easier to start without Compiz-Fusion and turn it on when I want it on.

---

### Post by steveneddy on 2007-08-14
> **Frak said:**
> I don't see the big deal about ubuntu-desktop, its just a meta-package. So if you have all of the apps that it provides, its just a waste of space, and removing it wouldn't change one thing.

I always reinstall ubuntu-desktop when messing around with compiz or fusion.

Everything seems to work better for me if I do.

---

### Post by Frak on 2007-08-14
> **steveneddy said:**
> I always reinstall ubuntu-desktop when messing around with compiz or fusion.

Everything seems to work better for me if I do.
Weird, I usually uninstall ubuntu-desktop after every clean installation I do (At least 3 times a week :P)
It frees up about 975KB, not much, but it is freed space, plus, I'll never get conflicting packages statements about ubuntu-desktop.

---

### Post by steveneddy on 2007-08-14
> **Frak said:**
> Weird, I usually uninstall ubuntu-desktop after every clean installation I do (At least 3 times a week :P)
It frees up about 975KB, not much, but it is freed space, plus, I'll never get conflicting packages statements about ubuntu-desktop.

I just don't get conflicting package statements, and I have ubuntu-desktop installed. 

All of the machines here run better, in my experience, if it is installed.

Did you get Emerald working with the script?

I left a link to the original thread for the script if you need more answers.

Basically, things just run well on the machines I use, so the script worked great for me.

EDIT - where in OK are you?

---

### Post by Frak on 2007-08-14
No I didn't get Emerald to work, as I really don't have a need for it.
And Ada, southern part of OK.

---

### Post by z0phi3l on 2007-08-14
Does this repo have all the extra and experimental plugins, and if so, what is the names of the packages, I'm missing some features that are in the extra packages.

---

### Post by steveneddy on 2007-08-14
> **z0phi3l said:**
> Does this repo have all the extra and experimental plugins, and if so, what is the names of the packages, I'm missing some features that are in the extra packages.

AFAIK - Trevenio's repos have the most up tp date extras for Feisty that you can get.

IMHO - it is also the most stable repo you can get for Ubuntu Feisty.

---

### Post by z0phi3l on 2007-08-14
> **steveneddy said:**
> AFAIK - Trevenio's repos have the most up tp date extras for Feisty that you can get.

IMHO - it is also the most stable repo you can get for Ubuntu Feisty.

Yea BUT Trevino's aren't up to date forcompiz core :/

---

### Post by steveneddy on 2007-08-14
> **Frak said:**
> Instead of putting fission in the home directory, why not /usr/bin/? Then it could be run from the CLI from any directory.

It doesn't matter where you put the script. The launcher will run the script if it points to where it is.

---

### Post by Frak on 2007-08-14
> **z0phi3l said:**
> Yea BUT Trevino's aren't up to date forcompiz core :/
AFAIK, this one isn't either. Ubuntu can't support over 0.5.2.

---

### Post by iamjfarrell on 2007-08-15
I am having a little trouble understanding how to get the 0.5.2 installed and working on my computer.. im kind of a linux newbie

---

### Post by Scotty562 on 2007-08-15
The updated howto for 0.5.2 workes great but I can't find the option to change how many sides my cube has anymore. I only have 2! It looks really funny :).

---

### Post by isaacj87 on 2007-08-15
I tried the CF script and it works great! 0.5.2 and all the plugins!! I recommend at least trying it out.

and to get the cube again...goto the setting manager->General Options->Desktop Size and change the Horizontal setting to "4" and the 2 others to "1"

---

### Post by Nigmah on 2007-08-16
[COLOR=DarkOrange][B]This has probably been askedon before but i have compiz installed i've tried it with normal gnome and xgl, i used to get woblly windows and opacity, as well as folding out box in xgl, but nothing else and i could change/enable any other effects.
Now i don't even get anything in xgl or gnome.
As well i always have a update for compiz-core from 5.2 to 5.2 no matter how many time i install it.

Also is aiglx part of gnome or is there a guide to install it because it take up less sys resources then xgl.

Using 8800 gts
[/B][/COLOR]

---

### Post by ayoli on 2007-08-16
> **Nigmah said:**
> [COLOR=DarkOrange][B]

Also is aiglx part of gnome or is there a guide to install it because it take up less sys resources then xgl.

[/B][/COLOR]

Aiglx is a part of Xorg so nothing to install, XGL is now only recommended for ATI cards.

---

### Post by cursebg on 2007-08-16
How do I get the cube working? I mean, I've enabled it, but thereare no key sequences to rotate it :?

---

### Post by fredzer on 2007-08-16
error
```
Checking for Xgl: not present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present.
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
```

> **Frak said:**
> Which version of Ubuntu are you running.

using the latest one 7.04

My graphics card is
ATI Radeon 1800X GTO 
Got dual screen up

---

### Post by starscalling on 2007-08-16
> **cursebg said:**
> How do I get the cube working? I mean, I've enabled it, but thereare no key sequences to rotate it :?

enable plugin cube rotate - then its same as gnome defaults: <control><alt>left/right [down unfolds and is kinda funneh :P]

> **Frak said:**
> No I didn't get Emerald to work, as I really don't have a need for it.
And Ada, southern part of OK.

real easy! put in emerald-themes + emerald
if the bugger refuses to work:

```

sudo nano /usr/bin/cpr

```

in that put

```

compiz --replace
emerald --replace

```

save, and make executable:

```

sudo chmod +x /usr/bin/cpr

```

now when you change emerald themes via the emerald-theme-manager it should auto change with it - if it does not make this :P [yes yes ive had lots of trouble between my machine and my roomates lol]

```

sudo nano /usr/bin/emr

```

put this in there:

```

emerald --replace

```

then you can run that anytime and it will update // execute emerald ^_^


> **steveneddy said:**
> AFAIK - Trevenio's repos have the most up tp date extras for Feisty that you can get.

IMHO - it is also the most stable repo you can get for Ubuntu Feisty.

ummm...
well i run intel d946gzis mobo with the onboard gma 3000 + 2 gigs ram + e2160 [dual core 1.8ghz {the baby core 2 duo lol}] and for me the most stable is amaranth's repo - i just wish it had the cube caps and the shift switcher - but even without a dedicated vid card with amaranth's i can use compiz 24-7 :>



and for the record - eff vista its got nothing on nix :P
also please keep making us awesome stuff and updating our compiz ^_^

---

### Post by cursebg on 2007-08-16
> enable plugin cube rotate - then its same as gnome defaults: <control><alt>left/right [down unfolds and is kinda funneh :P

man, do you have a spare gun? :D I need something to shoot myself with, it has been in front of me all the time :P

---

### Post by qopit on 2007-08-16
When I try and do the install I get a warning about the packages not being authenticated...

```
russ@russbuntu:~$ sudo apt-get install compiz compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins libcompizconfig-backend-gconf libcompizconfig0 libdecoration0 python-compizconfig
Suggested packages:
  nvidia-glx
The following NEW packages will be installed:
  compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compizconfig-settings-manager libcompizconfig-backend-gconf libcompizconfig0 libdecoration0 python-compizconfig
0 upgraded, 11 newly installed, 0 to remove and 0 not upgraded.
Need to get 2063kB of archives.
After unpacking 12.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  compiz-core libdecoration0 compiz-plugins libcompizconfig0 libcompizconfig-backend-gconf compiz-gnome compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz python-compizconfig compizconfig-settings-manager
Install these packages without verification [y/N]? 

```

Based on a guide elsewhere I also grabbed the key below, but it didn''t help.
```
sudo wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -

```What gives?  Why can't the packages be authenticated?

And I'm running ATI's fglrx... why would it suggest nvida-glx?  Is that a semi-subtle jibe from the packager against ATI?

---

### Post by GFree678 on 2007-08-17
> **qopit said:**
> What gives?  Why can't the packages be authenticated?
They cannot be authenticated because the repository has changed several days ago, and so the authentication key you added no longer applies. Doesn't matter though, you can still use them even without authentication.

---

### Post by Amaranth on 2007-08-17
The repo is unsigned by design. It makes it fairly obvious what packages come from me and not the main Ubuntu repo. The Suggests for nvidia-glx is there because compiz only works (without Xgl) on the 'ati', 'intel', and 'nvidia' drivers but the 'nvidia' one isn't installed by default.

---

### Post by dasunst3r on 2007-08-17
Amaranth's repository was problem-ridden at best for me.  I was unable to log out without pressing the power button to shut down and restart and the update simply wouldn't go away regardless of how many times I clicked on "Apply Updates."  For those of you wishing to revert to the old repository, here are the procedures: [http://ubuntuforums.org/showthread.php?t=481615](http://ubuntuforums.org/showthread.php?t=481615)

---

### Post by volle on 2007-08-18
hello.  everything work out ok, but when i leave this in repo: [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) i get the update symbol, and it wants to update Compiz Core, but infact there is 0 bytes in the update. Whats wrong here ?
Should I disable that repo ?

Best regards Volle

---

### Post by s_spiff on 2007-08-18
When I do the 'compiz --replace' in the terminal I get this error :
```

$ compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
aborting and using fallback: /usr/bin/metacity 


```

---

### Post by Bram77 on 2007-08-18
I guess you have a ati card?

---

### Post by FuturePilot on 2007-08-18
It keeps saying I have an update available but after I install it, it still says I have an update available. compiz-core.

---

### Post by bimmerd00d on 2007-08-18
> **FuturePilot said:**
> It keeps saying I have an update available but after I install it, it still says I have an update available. compiz-core.

I have this issue as well

---

### Post by couzin2000 on 2007-08-18
> **isaacj87 said:**
> Perhaps, I can help...I've got compiz fusion running both on aiglx and xgl. Could you tell me what video card you are using? It's one thing to have compiz fusion running and not have bleeding edge, but it's another to not even have it running at all! Which sucks!

If I knew your video card situation, maybe I could help you better. :)

Intel 945gm... I've tried installing XGL on my laptop, and it does appear as one of the session choices -- but it readliy tells me that XGL cant be started because it can't find /usr/blablabla/startxgl.sh (which I JUST put in there).

I don't have any choices as far as AIGLX.
I'm running the latest version of my video driver, I think which is the i910 or something to that effect.

If you need the content of certain specific files, lemme know as well.


One quick thing... I'm not planning on reinstalling until Gutsy comes out, so for those of you who are really trying to help me, thanks, but I'll wait for now -- just too much damn hassle.

HOWEVER we can still try to get it to work.

**EDIT1:** I've been re-reading the thread, and many seem to think I should be running Compiz Fusion with AIGLX if I have and Intel card (which I do -- i945GM)... however I followed this from the start, and it told me to configure Compizfusion to use XGL, which doesn't seem to work. So, shouldn't I be reconfiguring Compiz Fusion to use AIGLX instead? 
here's what I get in terminal:
```
sebastien@sebastien-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Converting gconf plugin list: '' 
Checking for nVidia: not present. 
Checking for Xgl: not present. 

(gtk-window-decorator:6957): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6957): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6957): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6957): Wnck-WARNING **: Unhandled action type (nil)
Segmentation fault (core dumped)

(gtk-window-decorator:6957): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6957): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6957): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6957): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6957): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6957): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6957): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6957): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6957): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6957): Wnck-WARNING **: Unhandled action type (nil)
```
So, what now? There's gotta be something REAL easy we are all missing here.
If this gets too rough, I'll just wait for Gutsy Gibbons, in which all this should already be built-in... right?

---

### Post by dougfractal on 2007-08-18
From what I've read XGL doesn't work to well with intel.
[B]
System Info grabber[/B]
can you post me *xinfo.tar.gz 
```
mkdir ~/Xinfo
cd ~/Xinfo
echo 'echo "Enter your Ubuntu name:"; read ubuntuname; 
rm *info.tar.gz installed.txt *.info  ; 
touch "$ubuntuname"X.info ; 
echo "$ubuntuname" > "$ubuntuname"X.info; 
lsb_release -d > "$ubuntuname"X.info # version
uname -r >> "$ubuntuname"X.info # kernel
lspci -nn >> "$ubuntuname"X.info # list hardware
glxinfo | head -4 >> "$ubuntuname"X.info
script -c " glxgears &  sleep 11 ;  pkill -15 glxgears"   
cat typescript | grep FPS >> "$ubuntuname"X.info
rm typescript
cp /etc/X11/xorg.conf ./   # graphics file
cp /var/log/Xorg.0.log ./
cp /etc/modprobe.d/blacklist ./
cp /etc/apt/sources.list ./
aptitude search ~imesa ~ixorg ~invidia ~iflgrx ~idbus ~icompiz -F "%20p %10v %10V %20d" > installed.txt
tar -czf "$ubuntuname"xinfo.tar.gz "$ubuntuname"X.info xorg.conf Xorg.0.log installed.txt blacklist sources.list ' | tee xinfo.sh
sed -i '1i#!/bin/bash' xinfo.sh
chmod a+x xinfo.sh
./xinfo.sh
echo -en "\nplease attach $PWD/";echo -n "$ubuntuname"; echo "xinfo.tar.gz"

```
*[COLOR="DimGray"]If anyone knows how to get more hardware data (like mainbord, laptop id) I would really appreciate it. Please let me know[/COLOR]*

---

### Post by g2g591 on 2007-08-18
> **couzin2000 said:**
> 
If this gets too rough, I'll just wait for Gutsy Gibbons, in which all this should already be built-in... right?

Its in the gutsy repos :)

---

### Post by Frak on 2007-08-18
> **g2g591 said:**
> Its in the gutsy repos :)
It was preinstalled for me :)

---

### Post by coffee on 2007-08-18
I have gotten compiz up and running but can not get the settings manager to open.

This is what I get:

dad@dads-den:~$ ccsm
Info: No sexy-python package found, don't worry it's optional.
Backend     : gconf
Integration : true
Profile     : default
Adding plugin crashhandler (Crash handler)
Adding core settings (General Options)
Adding plugin annotate (Annotate)
Adding plugin blur (Blur Windows)
Adding plugin clone (Clone Output)
Adding plugin cube (Desktop Cube)
Adding plugin dbus (Dbus)
Adding plugin decoration (Window Decoration)
Adding plugin fade (Fading Windows)
Adding plugin fs (Userspace File System)
Adding plugin glib (GLib)
Adding plugin inotify (Inotify)
Adding plugin minimize (Minimize Effect)
Adding plugin move (Move Window)
Adding plugin place (Place Windows)
Adding plugin plane (Desktop Plane)
Adding plugin png (Png)
Adding plugin regex (Regex Matching)
Adding plugin resize (Resize Window)
Adding plugin rotate (Rotate Cube)
Adding plugin scale (Scale)
Adding plugin screenshot (Screenshot)
Adding plugin svg (Svg)
Adding plugin switcher (Application Switcher)
Adding plugin video (Video Playback)
Adding plugin water (Water Effect)
Adding plugin wobbly (Wobbly Windows)
Adding plugin zoom (Zoom Desktop)
Adding plugin animation (Animations)
Adding plugin expo (Expo)
Adding plugin imgjpeg (JPEG)
Adding plugin neg (Negative)
Adding plugin opacify (Opacify)
Adding plugin put (Put)
Adding plugin resizeinfo (Resize Info)
Adding plugin ring (Ring Switcher)
Adding plugin snap (Snapping Windows)
Adding plugin text (Text)
Adding plugin thumbnail (Window Previews)
Adding plugin wall (Desktop Wall)
Adding plugin winrules (Window Rules)
Adding plugin scaleaddon (Scale Addons)
Adding plugin vpswitch (Viewport mouse switch)
Adding plugin addhelper (ADD Helper)
Adding plugin bench (Benchmark)
Adding plugin fadedesktop (Fade to Desktop)
Adding plugin extrawm (Extra WM Actions)
Adding plugin firepaint (Paint fire on the screen)
Adding plugin group (Group and Tab Windows)
Adding plugin mblur (Motion blur)
Adding plugin reflex (Reflection)
Adding plugin splash (Splash)
Adding plugin trailfocus (Trailfocus)
Adding plugin showdesktop (Show desktop)
Adding plugin cubereflex (Cube Reflection)
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 43, in <module>
    mainWin = ccm.MainWin(context)
  File "/usr/local/lib/python2.5/site-packages/ccm/Window.py", line 84, in __init__
    self.ResetMainWidgets()
  File "/usr/local/lib/python2.5/site-packages/ccm/Window.py", line 178, in ResetMainWidgets
    self.BuildTable(pluginsVPort)
  File "/usr/local/lib/python2.5/site-packages/ccm/Window.py", line 230, in BuildTable
    pluginEnable.set_sensitive(self.Context.AutoSort)
AttributeError: 'compizconfig.Context' object has no attribute 'AutoSort'

thanks

---

### Post by akiratheoni on 2007-08-19
I'm able to install Compiz on 7.04 but I get this error when I use compiz --replace

> Checking for Xgl: not present. 
Blacklisted 'vesa' driver is in use 
aborting and using fallback: /usr/bin/metacity 

Funny thing is, I also have Fedora 7 with Beryl, and it works... I'm not sure about Compiz though.

---

### Post by hyperair on 2007-08-19
Good grief. It doesn't include the unofficial plugins!

---

### Post by Dark Star on 2007-08-19
Thnaks author will install CF now :) Just a question Beryl runs on my COmp @ 256Mb ram :) well will CF will run :(

---

### Post by 5h4rk on 2007-08-19
Where can I get information of what each option of CF is for?

Thanks.

---

### Post by readitsideways on 2007-08-19
I had Compiz fusion install and working great how I like it, then this morning there was an update and all my settings were overwritten :-(. 

So I set them all again but now 3D Windows won't activate. I can tick it but it's unticked as soon as I make any other setting change, and even when it's ticked the effect isn't there. Very irritating..

Is this a bug or a setting conflict? I'm not getting any error messages.

Duncan

---

### Post by GFree678 on 2007-08-19
> **readitsideways said:**
> I had Compiz fusion install and working great how I like it, then this morning there was an update and all my settings were overwritten :-(.
They weren't overwritten - this new version stores its config in a different location apparently.

Previous build: ~/.conpizconfig
New build: ~/.config/compiz/compizconfig

---

### Post by pvincent on 2007-08-19
I've recently updated my feisty system which contains KDE and compiz-fusion.
However it fails on **libfreetype6** needed for **libcompizconfig-backend-kconfig**

Here are the logs :
```

sudo aptitude install libcompizconfig-backend-kconfig
...
The following packages have unmet dependencies:
  libcompizconfig-backend-kconfig: Depends: libfreetype6 (>= 2.3.5) but 2.2.1-5ubuntu1.1 is installed.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.

```

As far as I understand, it seems libfreetype6>=2.3.5 is only available on *gutsy*.
What should I do next if I still want to keep my feisty up-to-date and compiz-fusion in the meantime ? Thx in advance.

---

### Post by Gonzell on 2007-08-19
Yeah, when I updated this morning a lot of things stopped working for me. A lot of plugins won't even turn on (like the screensaver one) and a lot of my settings seem to have been lost. And there doesn't seem to me much saved in those config files you mentioned...all that is in mine is:

> [gnome_session]
profile = 
plugin_list_autosort = true

When I go into some of the plugins, the "Actions" tab is missing. For example, for the "Scale" plugin. That tab is missing but in the "General" tab it has check boxes for things like "Initiate Window Picker For All Windows". This doesn't make any sense...these settings are suppose to be set under "Actions" as a keyboard key or mouse gesture. So, now I'm unable to use the "Scale" plugin because I can't set an action to it...

Anyone else having these issues or am I just one big poor soul?

---

### Post by Smiecho on 2007-08-19
> **Gonzell said:**
> Anyone else having these issues or am I just one big poor soul?You're not the only one... 3D Windows and  Screen Saver are not working. And some settings are messed. For example when I move my mouse to upper right screen corner I can see windows from active viewport, but I want to see all windows from all viewports...

---

### Post by soro2005 on 2007-08-19
Assuming that you're also using Treviño's repository:

I have removed the compiz-compcomm-plugins-main and installed the several packages that start with compiz-fusion-plugins... In fact, I've gone through all the compiz packages in Synaptic and weeded out all those that were older than git200708something. That brought back most functions. I had to enable them individually, though. I think they've just changed the entire organization of the plugins while Treviño was away.

I'm still without the ability to define keybindings in the CompizConfig Settings Manager, though. If anyone has a lead there...

---

### Post by Smiecho on 2007-08-19
Yesss... I was using Trevino's repository. But 15 minutes ago I tried to switch to another repo. Check this post on Compiz forum: [http://forum.compiz-fusion.org/showthread.php?t=3153](http://forum.compiz-fusion.org/showthread.php?t=3153)

It seems some problems have disappeared.

---

### Post by isaacj87 on 2007-08-19
I don't know if it has already been mentioned...but Trevino is back!

And he's updated this Compiz Fusion all the way to 0.5.3...at least that's what mine is at. So you guys might want to try his repo if you are having problems...

---

### Post by soro2005 on 2007-08-19
The problems came up with Treviño's big update from yesterday. I think there's a huge backlog of changes, and something broke. As I say, I could get almost everything back by enabling the compiz-fusion-plugins... packages. I've also changed to flat file configuration backend (under preferences) to get standard settings.

I didn't figure out, though, how to get full support for keybindings back. For example: In the "general" tab of the "General Options" section in the configuration manager, I have the list with checkboxes and actions that can be enabled (including the "Run Command"s), but the field in which to define the key binding to use to run a given action has just disappeared.

I'm sticking with Treviño's repository, of course. He seems to be close to the action, and I fully trust him to sort this out for me without me taking any real action :-) . Just seems there're some reverberations here of his having a hopefully nice and beautiful vacation on an Italian beach. :lolflag:

---

### Post by volle on 2007-08-19
i have nVidia 7600go on my labtop, and the restricted driver is enabled.
Beryl worked fine and is removed, Compiz works fine, its just that update thing.

---

### Post by Leed on 2007-08-19
Also using Trevinos Packages here, however the package that enables 3D Windows is possibly from another source (compiz-fusion-unofficial 0.0.1), don't know why it's missing in the standard packages, but why care, I got it. After removing this plugin and reinstalling it, the 3D effects were back. 

However I have the same problem as you guys with the Keybindings. Hopefully it's fixed soon, it may put me off to return from holidays and finding out my Compiz doesn't work as it should, but the guys behind it are doing a great job and have my full trust, that it'll be back to normal soon.

---

### Post by Dimitriid on 2007-08-19
I have a huge problem, i seem to be trapped on broken packages :(

I tried to follow the guide for amd 64 firefox and flash 9 and installing java 1.4 but I still got no flash.

After that I tried to install compiz fusion and I got an error message about broken dependencies on mozilla.

Ok so I go to Adept Manager ( im running Kubuntu feisty 64bit ) found that java thing that was broken, try to install....stupid  adept gives me  an error. 

I tried apt-get -f install to get it on console and stupid sun wanted me to accept the eula but its impossible to click or select ok ( common issue ) Now I remember fixing this easily on Ubuntu ( just use synaptic to install java and it does lets you agree to their bullshit eula ) but damn adept manager doesn't lets me. So I tried to install synaptic, no go.

Now I cant do anthing, everytime I try to use apt-get update or something it sends me to this:

```

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up bcm43xx-fwcutter (006-1) ...
--14:18:19--  http://boredklink.googlepages.com/wl_apsta.o
           => `wl_apsta.o'
Resolving boredklink.googlepages.com... 72.14.203.118
Connecting to boredklink.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
14:18:20 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

that was what I successfully used to install my broadcom wireless ( up and working as we speak ) but now I just cant do anything to get past that. Any ideas?

---

### Post by Senor Jefe on 2007-08-19
I too installed the updates today and it screwed everything up.  I'm some what of a nub to the compiz/beryl scene.  About how long does it take for them to fix these kind of problems and a have a working package again?

---

### Post by cresny on 2007-08-19
When using Trevino's pre-0.5.2 packages with NVidia 7600 restricted driver all woked fine. I messed with Amaranth's packages for a while, but I got sporadic lock-ups (even after downgrading the NVIDIA driver) plus the phantom compiz-core "update available".

Now I did a complete purge of Amaranth's build (sudo apt-get remove --purge compiz* libcompizconfig*, rm .compiz) and edited /etc/apt/sources.list to comment amaranth and uncomment trevino and re installed. at first most plugin were missing, until i realized you have to do an apt-get install compiz-fusion-plugins-extra and -unofficial (didn't mess with -unsupported).

Now everything works beautifully as it did before, including "compiz --replace -c emerald", and now I have all   the plugins, best performance, zero lockups, an no more nagging phantom update.

Great Job, Trevino, and welcome back!

---

### Post by luckyd on 2007-08-19
with the newest version from trevino's repos, when firefox is loading a page the mouse pointer dissapears. Anyone else experiencing this?

---

### Post by adolfofoliaco on 2007-08-19
Could somebody help with this please this is what happening

[http://ubuntuforums.org/showthread.php?p=3217240#post3217240](http://ubuntuforums.org/showthread.php?p=3217240#post3217240)

with my installation..

---

### Post by cresny on 2007-08-19
> **adolfofoliaco said:**
> Could somebody help with this please this is what happening

[http://ubuntuforums.org/showthread.php?p=3217240#post3217240](http://ubuntuforums.org/showthread.php?p=3217240#post3217240)

That's the "phantom update" from Amaranth's repo. As I mentioned earlier, all is working great for me with a purge/update to Trevino's repo. If anyone is not happy with their current compiz install, I suggest:

1. purge:

sudo apt-get --purge remove compiz* libcompizconfig*

2. edit /etc/apt/sources.list to reestablish Trevino's repo:

deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

#deb [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse
#deb-src [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse

3. update and upgrade (this also upgraded emerald, which I did not remove):

sudo apt-get update && sudo apt-get dist-upgrade

4. install:

 sudo apt-get install compiz compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial

This made both my NVDIA desktop and Intel laptop very happy. YMMV!

---

### Post by adolfofoliaco on 2007-08-19
ok but what went worn with the UPdate

---

### Post by hyperair on 2007-08-19
@Cresny: You don't seem to be having any problems at all. Can you tell me whether the CompizConfig Settings Manager is garbled for you? (mostly keybinding stuff)

---

### Post by adolfofoliaco on 2007-08-19
sorry but how do I do that I just newbi....

---

### Post by cresny on 2007-08-19
> **hyperair said:**
> @Cresny: You don't seem to be having any problems at all. Can you tell me whether the CompizConfig Settings Manager is garbled for you? (mostly keybinding stuff)

drat! spoke too soon. :( yes, keybindings are whacked. Hopefully, there will be new packages soon.

---

### Post by wajiw on 2007-08-19
For people who can't use Amaranth's repo for 0.5.2 Trevino just updated his repo with the new version!

go to his website to find out how to reinstall his version: 
[http://3v1n0.tuxfamily.org/dists/feisty/eyecandy/]("http://3v1n0.tuxfamily.org/dists/feisty/eyecandy/")

---

### Post by Senor Jefe on 2007-08-19
I got it working again with reinstalling compiz-fusion, just like others have said to reinstall trevino's, but now any time i start a program of any sorts, it crashes.  Any solutions?

---

### Post by b0uncyfr0 on 2007-08-19
Hey guys is Trevinos repo down? I just tried to update to 0.5.3 and it broke my compiz-kde. Could someone and update or maybe its just me.

---

### Post by nimajiman on 2007-08-19
Yes I am getting errors connecting to Trevinos repository as well. It seems as though the server is down.

Can anyone confirm this?

---

### Post by Garyx on 2007-08-19
Having the same issues here, the trevino page is currently down.

Edit: Seems that the servers isn't down though since it still replies to ping, but the page is still unavailable.

---

### Post by Frak on 2007-08-19
It may be that there is a problem with the updated package, therefore the responsible mantainer would take his/her repo's offline.

---

### Post by Mr. Mojo on 2007-08-19
First let me say I'm a true Linux noob. I've been running Ubuntu Feisty for 2 days now and fighting Beryl and Compiz for 99% of it.

I have an Intel C2D CPU, 64 bit Ubuntu, and a Radeon x1950Pro. 

> mojo@Mojo-Linux:~$ glxinfo | grep renderingdirect rendering: Yes
mojo@Mojo-Linux:~$ glxinfo | grep texture_from_pixmap
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
mojo@Mojo-Linux:~$ 


That should mean I'm good to go for drivers right? When I check the restricted drivers manager, it shows an ATI accelerated graphics driver as enabled and in use. However, when I try to start compiz, I get the following: 

> Checking for Xgl: not present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

Also, I constantly see compiz-core in my update manager. I install the update and it doesn't give any errors, but as soon as it checks again, it's back. I followed the tutorial on page 1 of this thread step-by-step, so I'm not sure what the problem is.

Edit: this is on a fresh install of Feisty. I tried following about a dozen different tutorials and figured I'd scrambled everything so I blew it away and started from scratch. Since the re-install, this is the only tutorial I've tried.

---

### Post by st33med on 2007-08-19
> **Mr. Mojo said:**
> 
Also, I constantly see compiz-core in my update manager. I install the update and it doesn't give any errors, but as soon as it checks again, it's back. I followed the tutorial on page 1 of this thread step-by-step, so I'm not sure what the problem is.

Hmmm... The compiz-core package in the Amaranth's repositories maybe out of date. This gives the Update manager an alarm, but it always tries to update using Amaranth's repository. So it goes in circles.

So, my advise would be to comment out the repository for now, and:
```
sudo apt-get update
sudo apt-get upgrade
```

Then uncomment the repositories, and it should be set.

EDIT: This fixes it asking you for an update, but doesn't update compiz...
Am I missing something?

---

### Post by st33med on 2007-08-19
Also, I'm having a bit of a problem. I try ccsm, but it comes up with this error and doesn't launch:
```
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 37, in <module>
    import compizconfig
ImportError: /usr/local/lib/python2.5/site-packages/compizconfig.so: undefined symbol: ccsSetPluginListAutoSort
```

---

### Post by b0uncyfr0 on 2007-08-20
Does anyone know of any repos that have 0.5.3? Does Amaranth's repo have this or is it still 0.5.2?

---

### Post by isaacj87 on 2007-08-20
Trevinos has it.

---

### Post by Mr. Mojo on 2007-08-20
I believe my problem is that the version of compiz (5.2) in amaranth's repository is corrupt or something, because it isn't actually installing even when it says it is. I tried using the updater [here]("http://ubuntuforums.org/showthread.php?t=508769&highlight=compiz"), but it tells me none of the files are present. So my thinking is that I need to know a way to get a working copy of compiz as it appears Trevino's repository is down.


Edit: I was able to get close by following the instructions found [here]("http://ubuntuforums.org/showthread.php?t=488385&highlight=Instal+Compiz+ati"). When I got to the point where it says to check the files by logging out and selecting GNOME with XGL, I do it and my screen bugs out (looks like it is covered in artifacts). This is the first time I've even seen that it tries to do anything.

---

### Post by Dark Star on 2007-08-20
Why only Cube working here :( None of fire paint expo and other s are working :(

---

### Post by Dark Star on 2007-08-20
> **Dark Star said:**
> Why only Cube working here :( None of fire paint expo and other s are working :(
In Compiz Fusion only cube is there and few more similar to beryl but Expo I enabled it from Manager but it ain't working :(

---

### Post by readitsideways on 2007-08-20
does any one know where 3d Windows disapeared to? I switched to amaranth's repo like the first post in this guide says and now a bunch of options are not there (like 3d windows).

What's the reason for not using trevino's repo?

Also, compiz-core keeps wanting to update, from the current version to the current version. So frustrating

---

### Post by GuiPoM on 2007-08-20
These two things are clearly explained by the guys that maintain compiz-fusion backport

compiz-core keeps wanting to update: bug of update system, will be solved soon
3d Windows disapeared: part of unofficial package of compiz (unstable) so not available.

---

### Post by IamAcoconut on 2007-08-20
How do you enable **cube rotation** on middle-mouse-click at the desktop, instead of the silly Ctrl+Alt+Button1 combo? The way it was in Beryl. 

I had it adjusted just before the latest compiz update (from [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) eyecandy repos) but now my settings are gone. *Initiate plugin action* (under Viewport switcher) is bind to *Button2* which stands for MiddleMB. Scrolling to next and previous viewport from the desktop works fine, but Button2 doesn't at all.

BTW, wherever I try to change key bindings, the columns for screen edge and edge key are always grey and untouchable. Why's that?

---

### Post by hyperair on 2007-08-20
You mean you even have the Actions tab? I don't!

---

### Post by complexgeek on 2007-08-20
> **hyperair said:**
> You mean you even have the Actions tab? I don't!

I can only see it on some plugins. It's there for Expo and Desktop Wall (and probably some others), but not for Desktop Cube or Scale, which are the two plugins I use the most. I think the last update badly broke the Compiz Setting Manager. Hopefully it gets fixed soon, because things are pretty much unusable (for me) until then.

---

### Post by hyperair on 2007-08-20
Yeah. I've reverted to Vorian's for the time being. Take a look at this: [http://smspillaz.wordpress.com/2007/08/19/compiz-fusion-community-news-edition-12-for-august-19-2007-radical-changes/](http://smspillaz.wordpress.com/2007/08/19/compiz-fusion-community-news-edition-12-for-august-19-2007-radical-changes/)

Explains the issues we have.

---

### Post by complexgeek on 2007-08-20
> **hyperair said:**
> Yeah. I've reverted to Vorian's for the time being. Take a look at this: [http://smspillaz.wordpress.com/2007/08/19/compiz-fusion-community-news-edition-12-for-august-19-2007-radical-changes/](http://smspillaz.wordpress.com/2007/08/19/compiz-fusion-community-news-edition-12-for-august-19-2007-radical-changes/)

Explains the issues we have.
It certainly does. Would have been nice if the package manager had warned me in some way that updating would badly break things *sigh*

Could you please explain how you reverted your installation? I'm still kinda new at Linux (especially package management)

---

### Post by wajiw on 2007-08-20
to revert follow these steps:


1. purge:

sudo apt-get --purge remove compiz* libcompizconfig*

2. edit /etc/apt/sources.list to reestablish Trevino's repo:

deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

#deb [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse
#deb-src [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse

3. update and upgrade (this also upgraded emerald, which I did not remove):

sudo apt-get update && sudo apt-get dist-upgrade

4. install:

sudo apt-get install compiz compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial

---

### Post by complexgeek on 2007-08-20
I'm already using Trevino's repository. That's where the update that broke things came from. Won't reinstalling from there just leave me right back where I am now?

---

### Post by IamAcoconut on 2007-08-20
> **complexgeek said:**
> I'm already using Trevino's repository. That's where the update that broke things came from. Won't reinstalling from there just leave me right back where I am now?
It will. Exactly those repos broke my ccsm.

---

### Post by GFree678 on 2007-08-20
Come on Trev, get debuggin'!

/cracks whip

:)

---

### Post by oderus on 2007-08-20
Not to hijack the thread but I've been using Compiz/Beryl/Compiz-Fusion since it's early days I must say, the BEST walk through for Compiz-Fusion is here ([http://www.theopensourcerer.com/2007/08/16/compiz-fusion-052-from-source-on-ubuntu-feisty/](http://www.theopensourcerer.com/2007/08/16/compiz-fusion-052-from-source-on-ubuntu-feisty/))

It's a compile from scratch process but it's very easy and not only am I running 0.5.2 (all repo's are 0.5.1) but the CCSM is gone and replaced with a Beryl-like interface that kicks ****! There are options in the manager for indirect rendering for us Nvidiots and it works very well with Emerald themes.

I highly recommend it to anyone that wants the best Compiz-Fusion around.

FYI: I didn't swear. I said it kicks a-r-s-e. Damn censorship.

---

### Post by readitsideways on 2007-08-20
Woohoo, switched to vorian's repos as outlined here : [http://ubuntuforums.org/showthread.php?t=529299](http://ubuntuforums.org/showthread.php?t=529299)

and all is back:3D windows, shift switcher etc! Will go back to trevino when it's sorted.

I just gotta say something: We got our first local Apple iStore recently and I went to check it out expecting to be impressed, but Compiz fusion as ruined me for other UI's. Mac looked pretty primitive in comparison and I think CF make handling windows so much more user friendly. Amazing work guys.

Not having my favourite effects and tools for a day just drove home how great this stuff is.

 Duncan

---

### Post by sc00ter on 2007-08-20
Hi,

I've successfully performed a manual roll-back of CF from 0.52 to 0.51 on Trevino's repo, by going to the following URL:

[http://download.tuxfamily.org/3v1deb/pool/feisty/eyecandy/](http://download.tuxfamily.org/3v1deb/pool/feisty/eyecandy/)

and manually pulling the .deb packages dated 31-July-2007. Here are the deb files (gnome only):

compiz_0.5.1+git20070730~3v1ubuntu0_all.deb
compizconfig-settings-manager_0.1.0+git20070729~3v1ubuntu1_i386.deb
compiz-core_0.5.1+git20070730~3v1ubuntu0_i386.deb
compiz-fusion-plugins-extra_0.0.1+git20070730~3v1ubuntu1_i386.deb
compiz-fusion-plugins-main_0.0.1+git20070730~3v1ubuntu1_i386.deb
compiz-fusion-plugins-unofficial_0.0.1+git20070731~3v1ubuntu0_i386.deb
compiz-fusion-plugins-unsupported_0.0.1+git20070730~3v1ubuntu0_i386.deb
compiz-gnome_0.5.1+git20070730~3v1ubuntu0_i386.deb
compiz-plugins_0.5.1+git20070730~3v1ubuntu0_i386.deb
emerald_0.3.0+git20070728~3v1ubuntu1_i386.deb
libcompizconfig0_0.0.1+git20070728~3v1ubuntu0_i386.deb
libcompizconfig-backend-gconf_0.1+git20070710~3v1ubuntu0_i386.deb
libdecoration0_0.5.1+git20070730~3v1ubuntu0_i386.deb
libemeraldengine0_0.3.0+git20070728~3v1ubuntu1_i386.deb
python-compizconfig_0.1.0+git20070617~3v1ubuntu0_i386.deb

Make sure you download the .deb files into a separate folder. Then open a terminal session and cd into the directory that contains the downloaded files and type:

sudo dpkg -i *.deb

This will then downgrade your CF installation to the previous (working) version.

This version also reverts back to the .compizconfig file that resides at /home/your username/

If you want to stop update-manager picking up the broken version, then use synaptics package manager to "lock" the current version once you've rolled-back.

However you will need to unlock these packages to receive further updates, so the best thing is to keep an eye on the community forums for news of when the fixed version has been released (and tested).

Logout and log back in again for the changes to take place.

I know it's the long-way round, but I didn't want to remove the Trevino repo and start messing around with other repos.

**EDIT: You may end up with CCSM not functioning. But atleast CF will pick up you original settings. This is only temporary until a newer (working) version becomes available.**

---

### Post by austin1030 on 2007-08-20
I don't know this is some sort of magic...

When I upgrade to compiz-manager setting to 0.5.2, all settings were messed up.
When I click on "screen saver"then 3D setting get un-checked. It was similar with other settings.

Then, I went back to first page of this thread and remove all packages relate to compiz fusion, and re-installed all again with Trevino's repository and guess what? IT WORKS!!!

All my settings and configurations are working as I want. hm...wonder what happen.

Well, only thing I can say is...DO NOT UPGRADE...RE-INSTALL

Austin

---

### Post by scb0825 on 2007-08-20
After the upgrade mucked things up, I removed and reinstalled from Trevino's repos and everything is good....

---

### Post by st33med on 2007-08-20
How do I get Shift and Screensaver plugins?

---

### Post by Amaranth on 2007-08-20
The shift plugin should be available in a few hours, screensaver is not supported upstream so not in my repo.

---

### Post by volanin on 2007-08-20
> **scb0825 said:**
> After the upgrade mucked things up, I removed and reinstalled from Trevino's repos and everything is good....

I did that and everything is OK.
But I can't set different keybinding in compiz-settings-manager.
It does not even me show the field to do that, just the action (Ex: Rotate Left) with a checkbox.

How can I change the keybindings?

---

### Post by st33med on 2007-08-20
> **Amaranth said:**
> The shift plugin should be available in a few hours, screensaver is not supported upstream so not in my repo.

Thanks. The shift plugin is the one I really wanted.

---

### Post by st33med on 2007-08-20
> **volanin said:**
> I did that and everything is OK.
But I can't set different keybinding in compiz-settings-manager.
It does not even me show the field to do that, just the action (Ex: Rotate Left) with a checkbox.

How can I change the keybindings?

That's a bug in Trevino's repository. You really can't change anything.

---

### Post by wikwam on 2007-08-21
ok, this probably sounds like the STUPIDEST thing...but what the hell is the SUPER key? :confused: I'm really embarrassed to ask it, but I really have no idea...

---

### Post by bromix on 2007-08-21
Super Key is the WIndows key, ;)

---

### Post by readitsideways on 2007-08-21
> Super Key is the WIndows key

I always thought "Super" was the stupidist name for a Windows key. How about "evil key" or "that key"

.. or is it being sarcastic?

:-)

---

### Post by judabuddhist on 2007-08-21
well, this version is stable at least. Neither Trevino no Vorians repos give me a working version right now. Trevino's used to work, but now I've got the same checkbox issue as everyone else, and the version from Vorian's repository seems to crash constantly. I miss the 3D windows and shift plugins though. Why aren't they included in this, are they not stable?

---

### Post by GuiPoM on 2007-08-21
You're right, 3d cube and shift are unstable so not into stable package but unofficial one.
I noticed that 3d cube seems to suffer from memory leaks. 

But I guess they will become stable in a short time. Fusion is growing up very fast :)

---

### Post by c.ovidiu on 2007-08-21
Any ideas when the Actions bug will be fixed? It's really annoying...

---

### Post by fabertawe on 2007-08-21
Hi folks,

I've had an incredibly annoying problem for the last couple of days since I tried Compiz-Fusion from Amaranth's guide. I purged the previous version (Trevino's) and installed Amaranth's but was getting constant freezes (mouse pointer movement but no keyboard) on logging out, shutdown or configuring. So I removed (and purged) this version and decided to go back to Metacity for the time being.

The problem I'm having is that pressing the Return key anywhere (even just on the desktop) results in an error box with only the message "**Text was empty (or contained only whitespace)**". The Enter key works as per normal. This is only resolved by re-installing Compiz-Fusion and using it but it's too unstable here to be bearable. I should add this didn't happen with Trevino's version (which I've not tried since) but I don't want to use it just to get rid of this problem!

If anyone could shed any light on this I'd be most grateful! I'm using 'Linux ubuntu 2.6.20-16-lowlatency #2 SMP PREEMPT Thu Jun 7 19:03:17 UTC 2007 x86_64 GNU/Linux' btw.

Cheers ... Paul

---

### Post by vapore0n on 2007-08-21
sounds like a keyb shortcut problem.
Check your settings make sure any one not used say Disabled.

---

### Post by fabertawe on 2007-08-21
> **vapore0n said:**
> sounds like a keyb shortcut problem.
Check your settings make sure any one not used say Disabled.

Thanks for the suggestion but I already checked keyboard settings, shortcuts and I've been through everything with gconf-editor but couldn't spot anything obvious.

**EDIT:** Ok, apologies for undue diligence! Went through everything in gconf-editor again and found '/apps/metacity/keybinding_commands/command_10' set to 'Return' with a blank action. Not sure how this got set mind but sanity restored :)

---

### Post by volanin on 2007-08-21
> **volanin said:**
> I did that and everything is OK.
But I can't set different keybinding in compiz-settings-manager.
It does not even me show the field to do that, just the action (Ex: Rotate Left) with a checkbox.

How can I change the keybindings?

> **st33med said:**
> That's a bug in Trevino's repository. You really can't change anything.

What about Amaranth's repository?
Is this bug present there as well?

---

### Post by matemargo on 2007-08-21
When I run **compiz --replace** nothing seems to happen.

If I run it from a terminal I get this output:

```

Segmentation fault (core dumped)
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

I have Nvidia card and direct render is ok.
Any ideas?

---

### Post by st33med on 2007-08-21
> **volanin said:**
> What about Amaranth's repository?
Is this bug present there as well?

No. It should work fine.

---

### Post by satkata on 2007-08-21
Hi,

I've just updated the compizconfig package and now it won't start.

On the first run:

satkata@satmobile:~$ ccsm 
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 42, in <module>
    context = ccs.Context(screens)
  File "compizconfig.pyx", line 830, in compizconfig.Context.__new__
  File "compizconfig.pyx", line 881, in compizconfig.Context.UpdateProfiles
KeyError: ''

Then I deleted the 'compiz' folder under ~/.config

and tried again:

[email]satkata@satmobile:~/.conf[/email]ig$ ccsm 
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 42, in <module>
    context = ccs.Context(screens)
  File "compizconfig.pyx", line 830, in compizconfig.Context.__new__
  File "compizconfig.pyx", line 881, in compizconfig.Context.UpdateProfiles
KeyError: '\x80\xeb1H'

It seems that my old profile under ~/.compizconfig does not get ported/updated to the new directory because after the failed run of ccsm, there is no 'Default.ini' file under
~/.config/compiz/compizconfig. There is only the 'config' file  and in it is no entry for the profile entry.

It staye only:
profile = ...

while in the old config

profile = ini stays.

I hope there are still some packages to update, so that this gets fixed.

Oh and if manually move my current "Default.ini" to the new folder and try to start ccsm, following comes:

satkata@satmobile:~$ ccsm 
Segmentation fault (core dumped)


:) :)

Hi sorry for the post before,

python-compizconfig wasn't updated therefore the failed start.

It's ok now, although my settings weren't taken over, so I had to check everything again.

And this was the output on the console:

satkata@satmobile:~$ ccsm 
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/ccm/Utils.py", line 138, in Update
    changedSettings = self.Context.ChangedSettings
AttributeError: 'compizconfig.Context' object has no attribute 'ChangedSettings'
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/ccm/Utils.py", line 138, in Update
    changedSettings = self.Context.ChangedSettings
AttributeError: 'compizconfig.Context' object has no attribute 'ChangedSettings

---

### Post by st33med on 2007-08-21
```
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 42, in <module>
    context = ccs.Context(screens)
  File "compizconfig.pyx", line 830, in compizconfig.Context.__new__
  File "compizconfig.pyx", line 881, in compizconfig.Context.UpdateProfiles
KeyError: ''
```

Same error. What to do???

Also, it has reverted to my 'old' settings. The settings I have now were from a script that compiled it for me, and I would've been fine, except that my desktop only has 2 faces.

---

### Post by adolfofoliaco on 2007-08-21
/usr/bin/compiz.real (core) - Error: Can't load plugin 'ccp' because it is built for ABI version 20070708 and actual version is 20070815
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'
 please somebody helps with this error it was working fine until update manger updated

---

### Post by Dark Star on 2007-08-21
Ok here are my thoughts CF is way bettter :0 Though neeeed to be polished a bit ;) but its   bettere tha Beryl in Stabiliy and features :D

---

### Post by jg1395 on 2007-08-21
this thread is a mess...

it should be locked and reopened with Official Amaranth's guide and another thread unofficial Trevino's guide.

---

### Post by techstop on 2007-08-21
> **jg1395 said:**
> this thread is a mess...

it should be locked and reopened with Official Amaranth's guide and another thread unofficial Trevino's guide.

Agreed! :idea:

---

