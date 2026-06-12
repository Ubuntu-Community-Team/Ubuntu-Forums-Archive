---
title: "XGL Install and General Tips For Gnome and Nvidia"
date: 2006-02-16
forum: Desktop Environments
---

### Post by poofyhairguy on 2006-02-16
[B]My guide is REALLY outdated. Instead use this site:

[http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit)

Thank you![/B]



Hello Nvidia Users. If you are a ATI user then please use this guide instead:

[http://www.ubuntuforums.org/showthread.php?p=739758](http://www.ubuntuforums.org/showthread.php?p=739758)

AMD64 Users look here:

[http://www.ubuntuforums.org/showthread.php?t=131659](http://www.ubuntuforums.org/showthread.php?t=131659)

A few notes: 

You must compile the newest CVS version of glitz to get this to work with Nvidia cards that lack Pixel Shaders (aka anything older than a 5200 FX). Hopefully this will be updated in the repository soon.

THIS BREAKS XINERAMA AND TWINVIEW so dual head use is more annoying. 

Proceed at you own risk. This is new experimental stuff and I hope you are a little command line savy (or can call someone that is) because if something messes up you might be stuck on the command line.

Don't say I didn't warn you.

Also I assume you have installed the newest Nvidia driver from the repos. To get it, this command:

```
sudo apt-get install nvidia-kernel-common nvidia-glx
```

Now lets edit some xorg.conf. First thing is to open it with this command:

```
sudo gedit /etc/X11/xorg.conf
```
 
Find the “Module” section. Comment out the “Glcore” and “dri “ modules and make sure a “glx” module is there. So basically like this:
```
#       Load    "GLcore"
#       Load    "dri" 
          Load "glx"
```

Now find the “Devices” section.

Change every line but the “Identifier” line to look just like mine:

```
Section "Device"
	Identifier- leave this line alone!
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option 		"RenderAccel" 		"true"
EndSection
```


**IF LATER ON COMPIZ DOES NOT WORK FOR YOU (and complains about composite extension):**

Add this to the very bottom:
```

Section "Extensions"
          Option  "Composite" "Enable"
EndSection
```

**DON'T ADD IT OTHERWISE**

VERY IMPORTANT:

Make sure your default color depth is 24!

Now save and close the file.

Now on to the second part- install XGL.

I pretty sure this line will do it. I tried it on a clean install:

```
sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome
```


Thats pretty easy. Next step is the making it start when Gnome starts. I get this from the ATI guide with modification. Thanks JoWilly!

First a command:

```
sudo gedit /etc/gdm/gdm.conf-custom
```

Make it look JUST like this. Delete all thats in the file and past all I have posted:
```

# GDM Configuration Customization file.
#
# This file is the appropriate place for specifying your customizations to the
# GDM configuration.   If you run gdmsetup, it will automatically edit this
# file for you and will cause the daemon and any running GDM GUI programs to
# automatically update with the new configuration.  Not all configuration
# options are supported by gdmsetup, so to modify some values it may be
# necessary to modify this file directly by hand.
#
# To hand-edit this file, simply add or modify the key=value combination in
# the appropriate section in the template below.  Refer to the comments in the
# gdm.conf file for information about each option.  Also refer to the reference
# documentation.
#
# If you hand edit a GDM configuration file, you should run the following
# command to get the GDM daemon to notice the change.  Any running GDM GUI
# programs will also be notified to update with the new configuration.
#
# gdmflexiserver --command="UPDATE_CONFIG <configuration key>"
#
# For example, the "Enable" key in the "[debug]" section would be specified by
# "debug/Enable".
#
# You can also run gdm-restart or gdm-safe-restart to cause GDM to restart and
# re-read the new configuration settings.  You can also restart GDM by sending
# a HUP or USR1 signal to the daemon.  HUP behaves like gdm-restart and causes
# any user session started by GDM to exit immediately while USR1 behaves like
# gdm-safe-restart and will wait until all users log out before restarting GDM.
#
# For full reference documentation see the gnome help browser under
# GNOME|System category.  You can also find the docs in HTML form on
# [http://www.gnome.org/projects/gdm/](http://www.gnome.org/projects/gdm/)
#
# NOTE: Lines that begin with "#" are considered comments.
#
# Have fun!

[daemon]

[security]

[xdmcp]

[gui]

[greeter]

[chooser]

[debug]

[servers]# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX). 
0=Xgl 

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo 
flexible=true
```

That has a special line that I found works best for Nvidia cards- this might solve acceleration issues some people have!

Time for the last step: make compiz work! This part will work for ATI users as well.

Two ways to do that. Either go by what this post says (thanks g14) or use my small script:

This:

[http://www.ubuntuforums.org/showpost.php?p=760273&postcount=507](http://www.ubuntuforums.org/showpost.php?p=760273&postcount=507)

Or:

First this command:
```

sudo gedit /usr/bin/thefuture
```

And empty file should appear. Fill it with this:
```

#!/bin/bash
gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &
```

Now save the file. Now use this command:
```

sudo chmod 755 /usr/bin/thefuture
```

Read the rest of this paragraph then reboot. After login in GDM, open a terminal and enter this (credit to rjtd):

```
xmodmap /usr/share/xmodmap/xmodmap.<language>
```

replacing you country code for language. For US English I use this command:

```
xmodmap /usr/share/xmodmap/xmodmap.us
```

Now put this command in the terminal to get compiz love:

thefuture

That should make compiz start working. If not, just keep using that command (maybe up to 20 times) till it does work. If you have problems, post them in thread so you can get help.

Try it out. Here are the basic key commands:

CTRL + ALT + Left/right arrow key. Switches to the new side of the cube for me. 

CTRL + ALT + SHIFT + Left/Right arrow key- Takes the in focused app around cube.

CTRL + ALT + Left Click on Desktop - allows you to use the mouse to rotate cube.

F12 - uses the Expose like trick

Alt- Tab - switcher Vista-style

Now is to solve some general issues. One is the fact that the wobble seems off to many people with Nvidia cards. There is an easy fix thanks to roberTO:

Run the command:
```

gconf-editor
```

Now go to:

apps>compiz>general>screen0>option

Then turn off the "detect_refresh_rate" option. 

Then set the "refresh_rate" to 60

It will work like a charm. Here is a neat trick if you want to take screenshots from npodges.

Go in the gconf-editor to:

apps>compiz>general>screen0>options

Change “command0” into"gnome-screenshot"

Then change “run_command0” into"Print"

Now the PrintScr button will take screenshots.  More helpful advice on the different gconf-editor options can be found on this page:

[http://gentoo-wiki.com/HOWTO_XGL](http://gentoo-wiki.com/HOWTO_XGL)

I hope you enjoyed the guide.

**To Undo**

This command:

> sudo gedit /etc/gdm/gdm.conf-custom

Then clear the file and save it.

---

### Post by woedend on 2006-02-16
PHG.  You have no idea how helpful this was to me.  Thanks so much.  You are great asset to the community.  One quick note / question. compiz gives an error about libmenu.so missing, although it still runs perfectly.  Ah well.  Thanks again sooo much
woe.

---

### Post by awakatanka on 2006-02-16
Thanks for the guide, hope someone will make one for the kubuntu users to soon.

The community did a good job to get Xgl to work , thanks for those people to.

A :KS :KS :KS :KS :KS  rated

---

### Post by encho on 2006-02-16
OK, I'm the unlucky one. All I got is this message:

$ thefuture
$ compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

And it kills my gnome-panel, nautilus, and metacity. Maybe I am missing something?
Oh yeah, and I can not find apps>compiz in my gconf-editor :-(

---

### Post by Belfagor on 2006-02-16
thanks for this guide... i was unlucky to get compiz run... tried running thefuture even for 30 times.. sometimes compizreal appears for 5 second in the running applications list then disapperas... any idea? thanks again...

---

### Post by poofyhairguy on 2006-02-16
[QUOTE=encho]OK, I'm the unlucky one. All I got is this message:

$ thefuture
$ compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

And it kills my gnome-panel, nautilus, and metacity. Maybe I am missing something?[/QUOTE]

Yeah, I get that sometimes. Just keep running the command till it goes away. Even if thats like twenty times. It will eventually go away.

---

### Post by frodon on 2006-02-16
really nice.

I have 2 questions regarding Xgl/compiz :
1- Do you get the same FPS with xgl and does the game works well ?
2- How to undo that, i mean to make xserver and metacity load as usual ?

Thank you for this neat guide.

---

### Post by encho on 2006-02-16
[QUOTE=poofyhairguy]Yeah, I get that sometimes. Just keep running the command till it goes away. Even if thats like twenty times. It will eventually go away.[/QUOTE]
You're my hero \\:D/ 
Finally works!
What now? :-k  I'll just play with the windows and wobbling ... 3 hours later ... still wobbling. :mrgreen:  Seriously, everything works smoothly, changing desktops, transparency, task switching. BTW, is there an easy way to do transparency change on per window basis? And are there any keyboard shortcuts? And why not to <shift> <backspace>? I'm really curious :p

---

### Post by scrooch on 2006-02-16
This is the first how-to take gets me everything set up... And only under a 3 minutes! :D

> 
Read the rest of this paragraph then reboot. when you computer reboots all you should have to do is put this command in the terminal to get compiz love:

thefuture

A little detail; It wasn't really clear for me when to enter this command exactly. Maybe you should insert 'After login in GDM, open a terminal and enter'...


Resizing windows hasn't improved in performance though, that's a real turndown :( Maybe some sort of plugin will show up which handels resizing windows/using xgl.

---

### Post by Belfagor on 2006-02-16
is xgl really broken for amd64?

---

### Post by poofyhairguy on 2006-02-16
[QUOTE=woedend]PHG.  You have no idea how helpful this was to me.  Thanks so much.  You are great asset to the community.  [/QUOTE]

Thanks

> One quick note / question. compiz gives an error about libmenu.so missing, although it still runs perfectly.  Ah well.  Thanks again sooo much
woe.

I can't find what the problem is in Google, but if it harms nothing to big deal!

---

### Post by codejunkie on 2006-02-16
xgl is running infact the gui seems more responsive and faster than with the normal xserver  but when i run compiz i get a black screen if i right click i see the context menu but the rest of the screen is black any help would be very appreicated.

---

### Post by poofyhairguy on 2006-02-16
[QUOTE=scrooch]
A little detail; It wasn't really clear for me when to enter this command exactly. Maybe you should insert 'After login in GDM, open a terminal and enter'...
[/QUOTE]

Thanks!

---

### Post by poofyhairguy on 2006-02-16
[QUOTE=frodon]really nice.

I have 2 questions regarding Xgl/compiz :
1- Do you get the same FPS with xgl and does the game works well ?[/QUOTE]

I don't really game in Linux, but maybe someone else can say?

> 
2- How to undo that, i mean to make xserver and metacity load as usual ?

Thank you for this neat guide.

Thanks and this command:

```
metacity --replace
```

to go back.

---

### Post by Aphelion on 2006-02-16
Hi fellow Xgl users ;)

I managed to install Xgl and run compiz with this tutorial. It al works fine except some strange redraw? problems. Please look at the attached screenshot. Does anyone know how to fix this problem?

---

### Post by encho on 2006-02-16
I've noticed that running some gl apps kills the server, like glx-gears. But in split second when it runs, I see that fps has gone up by 50%!
Just to ask you a quick question: how to enable screen edge sticking? I've seen it was working in demo video and I'm kinda used to it with dapper.

---

### Post by subjectdenied on 2006-02-16
press ctrl and alt while moving windows

---

### Post by encho on 2006-02-16
[QUOTE=subjectdenied]press ctrl and alt while moving windows[/QUOTE]
Thanks, but is it possible to make it default? Without keys?

---

### Post by ploum on 2006-02-16
hmm... I followed this tuto but :

1) Xgl process is taking 100% of the CPU
2) xterm is not working anymore (a black window)
3) launching "thefuture" bring me a black screen with a cursor, nothing else.

---

### Post by poofyhairguy on 2006-02-16
[QUOTE=ploum]hmm... I followed this tuto but :

1) Xgl process is taking 100% of the CPU
2) xterm is not working anymore (a black window)
3) launching "thefuture" bring me a black screen with a cursor, nothing else.[/QUOTE]

What video card hardware do you have?

---

### Post by ploum on 2006-02-16
poofyhairguy > 

0000:02:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2)


(anyway, thanks a lot for your howto and for your time :-) )

---

### Post by poofyhairguy on 2006-02-16
[QUOTE=ploum]poofyhairguy > 

0000:02:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2)


(anyway, thanks a lot for your howto and for your time :-) )[/QUOTE]

No problem. One suggestion. Add this to the "device" section of you xorg.conf:

```
Option "NvAGP" "1"
```

---

### Post by lewiz on 2006-02-16
Out of interest, does anybody know if Xinerama/TwinView will be supported at a later date?  Does this require work from nvidia or more work to Xgl?

Thanks for the HOWTO (the other thread was getting a little cluttered!).

---

### Post by Aphelion on 2006-02-16
I actually have my desktop running with twinview. Works perfectly Although you get a span and no dualview. 

Could anybody please answer to my problem to? Please ask me for more details / configuration if needed:
Note this is my laptop problem:

> 
Hi fellow Xgl users

I managed to install Xgl and run compiz with this tutorial. It al works fine except some strange redraw? problems. Please look at the attached screenshot. Does anyone know how to fix this problem?


---

### Post by ploum on 2006-02-16
thank for your suggestion but it doesn't change anything :-(  still the black xterm and black screen

(by the way, it doesn't take 100% of CPU. It's something else not related)

Strangely, my scrollwheel doesn't work in xgl. I don't really understand but this is a minor issue.

(for people who have the same "black screen" when launching "thefuture", the solution is to :

1) "killall compiz.real" in a terminal
2) Back to Xgl
3) "metacity &"

)

---

### Post by poofyhairguy on 2006-02-16
[QUOTE=Aphelion]I actually have my desktop running with twinview. Works perfectly Although you get a span and no dualview. 
[/QUOTE]

Yeah, thats what I mean by broken. Its annoying.

---

### Post by Spark* on 2006-02-16
[QUOTE=frodon]I have 2 questions regarding Xgl/compiz :
1- Do you get the same FPS with xgl and does the game works well ?
2- How to undo that, i mean to make xserver and metacity load as usual ?[/QUOTE]

I don't have many games installed right now, but things look really bad (Geforce 4 Ti4600):
- 2D SDL games are distorted.
- No fullscreen game properly changes the resolution (black frame).
- Nexuiz pulls up a black screen and then hangs.
- Chromium starts but is unusably slow and the menu is all distorted.
- PPRacer starts but is unusably slow.
- Cedega (WarCraft 3) doesn't work at all.

Additionally all movie display slows down the system to a crawl (switching to :fbo accel didn't even seem to make any difference). I wonder if my card is just too old for this (lack of DX9 features) or if there is still hope. Otherwise everything runs perfectly.

---

### Post by aent on 2006-02-16
[QUOTE=lewiz]Out of interest, does anybody know if Xinerama/TwinView will be supported at a later date?  Does this require work from nvidia or more work to Xgl?

Thanks for the HOWTO (the other thread was getting a little cluttered!).[/QUOTE]
Well right now Xorg seems to be loading the Xinerama extension. I think the problem is that Xgl is creating a full screen window on X... I was hoping it would be something simple like getting Xgl to load the Xinerama plugin but I think its a bit more complicated than that. Hopefully someone will come up with a fix or a workaround for this real soon so I can start using Xgl all the time.


It seems as if Compiz isn't loading plugins for me... there is only gconf in the gconf-editor active_plugins... how do I get more plugins to load?
Edit: fixed that, just reloaded compiz and it was fine...

Very cool stuff :D

---

### Post by pecanov on 2006-02-16
[QUOTE=ploum]thank for your suggestion but it doesn't change anything :-(  still the black xterm and black screen

(by the way, it doesn't take 100% of CPU. It's something else not related)

Strangely, my scrollwheel doesn't work in xgl. I don't really understand but this is a minor issue.

(for people who have the same "black screen" when launching "thefuture", the solution is to :

1) "killall compiz.real" in a terminal
2) Back to Xgl
3) "metacity &"

)[/QUOTE]

Just to confirm that this problem is present on GeForce 2 MX cards also.

---

### Post by DeeZiD on 2006-02-16
Great news for owners of older nvidia-cards :)

```
2006-02-16  David Reveman  <davidr@novell.com>

	* src/glitz.h (GLITZ_REVISION): Bump version to 0.5.3.

	* configure.in: Bump version to 0.5.3.

	* src/glitz_texture.c: Fix so that GL_ARB_texture_rectangle
	and GL_ARB_texture_border_clamp are not required for texture
	object creation.

	* TODO: Add note about removing some complexity.

	* src/glitz_pixel.c (glitz_get_pixels): Patch together clipped
	fetching of pixels.
```

Now you can even use your older cards for Xgl \\:D/ 
(I will test my old Geforce2MX in a few moments)

regards Dennis

---

### Post by vtechstu on 2006-02-16
[QUOTE=poofyhairguy]


[QUOTE=encho]
OK, I'm the unlucky one. All I got is this message:

$ thefuture
$ compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

And it kills my gnome-panel, nautilus, and metacity. Maybe I am missing something?
[/quote]
Yeah, I get that sometimes. Just keep running the command till it goes away. Even if thats like twenty times. It will eventually go away.[/QUOTE]

Ok my problem is pretty much the same.  The first time i run thefuture, i get the above output.  All other attempts i get this:
```

thefuture
gnome-window-decoraor: Another window decorator is already running
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

```

Any idea's what I could do?  I followed the steps exactly I think.  Might something from other wm attempts before, or compmgr attemps be messing this up?  Thanks.  Please help.

---

### Post by rjwood on 2006-02-16
EDIT: disregard this message---sry

---

### Post by pecanov on 2006-02-16
[QUOTE=DeeZiD]Great news for owners of older nvidia-cards :)

```
2006-02-16  David Reveman  <davidr@novell.com>

	* src/glitz.h (GLITZ_REVISION): Bump version to 0.5.3.

	* configure.in: Bump version to 0.5.3.

	* src/glitz_texture.c: Fix so that GL_ARB_texture_rectangle
	and GL_ARB_texture_border_clamp are not required for texture
	object creation.

	* TODO: Add note about removing some complexity.

	* src/glitz_pixel.c (glitz_get_pixels): Patch together clipped
	fetching of pixels.
```

Now you can even use your older cards for Xgl \\:D/ 
(I will test my old Geforce2MX in a few moments)

regards Dennis[/QUOTE]

Could you please post the result? I have the same card.

Thanx

---

### Post by DeeZiD on 2006-02-16
Now my geforce2MX200 works with Xgl :p 
And it is as fast as my geforce6600 gt!!!

(Image-quality without DVI is really bad imho ;) )

regards Dennis

---

### Post by DeeZiD on 2006-02-16
But Xvideo is damn slow without pixelshader.
It doesn't matter if I use xv:pbuffer or xv:fbo - it's too slow.


regards Dennis

---

### Post by rjwood on 2006-02-16
Thanks PHG---I've been waiting for this from you:D

---

### Post by Norm 2782 on 2006-02-16
cool it works with the latest Glitz ! :D
I don't get the black screen anymore... I DO however get ugly artifacts instead of icons etc, so it's not really useable (although the wobbly window is cool :p), but it's better than an entire black screen :p

---

### Post by bites on 2006-02-16
Thanks Poofy!  Everything's working great here!  Except my scrollwheel.. :)  But I'm too amazed with all this eyecandy to bother with that now :)

---

### Post by gnumdk on 2006-02-16
Ploum, may help you ;)

gnumdk@lisa:~$ cat /usr/bin/xgl.sh
#!/bin/bash
Xgl :1 -ac -accel glx:pbuffer -accel xv:pbuffer &
/bin/su gnumdk /usr/bin/xglgnome.sh
gnumdk@lisa:~$ cat /usr/bin/xglgnome.sh
#!/bin/bash
DISPLAY=:1 LD_LIBRARY_PATH=/usr/lib/opengl/xorg-x11/lib compiz --replace switcher decoration wobbly fade minimize cube rotate zoom scale move resize place menu &
DISPLAY=:1 gnome-window-decorator &
DISPLAY=:1 gnome-session
gnumdk@lisa:~$

---

### Post by gnumdk on 2006-02-16
```


#!/bin/bash
Xgl :1 -ac -accel glx:fbo -accel xv:fbo &
export DISPLAY=:0
export LD_LIBRARY_PATH=/usr/lib/opengl/xorg-x11/lib
compiz --replace switcher decoration wobbly fade minimize cube rotate zoom scale move resize place menu &
gnome-window-decorator &
gnome-session


```

Seems to work much better like this ;)

Some bugs...

---

### Post by nikopol on 2006-02-16
I think there's a problem with this install in that it installed me a US keyboard by default. When I switched to the correct keyboard (UK), it's caused a huge problem with the gnome-settings-daemon as it won't start at all anymore leaving me with a rather basic desktop! I'm looking into resolving this but this error is a pain in the butt to sort out IIRC..

---

### Post by gnumdk on 2006-02-16
Ok, fix all the strange bug setting my X depth to 24.

---

### Post by jsgotangco on 2006-02-16
I got this running nicely by following the steps from the first post but I had terrible refresh rate. What I did was reconfigure xserver-xorg and I got it running nicely. Thanks a lot! This is ultimate "bling" for now :mrgreen:

---

### Post by bonzodog on 2006-02-16
I just found a Devel post from the guy that built XGL/compiz for the repos, with a how-to for dapper.
> 
Hi,

I've recently uploaded packages of Xgl and compiz to universe for 
Dapper. These are highly experimental packages and are not recommended 
for casual use. However, if you want to start developing for this new 
technology, then do the following:

1) Make sure that you have the latest mesa, libglitz1 and libglitz-glx1 
installed
2) After installing xserver-xgl, replace /etc/X11/X with a symlink to 
/usr/bin/Xgl
3) Restart gdm
4) From a terminal, do compiz --replace gconf place move decoration resize minimize wobbly fade cube rotate zoom
5) Run gnome-window-decorator

You'll want to add these to your session startup if you want it on every 
login.

To get back to sanity:

1) Replace /etc/X11/X with a symlink to /usr/bin/Xorg
2) Restart gdm

As noted before, these are highly experimental packages. If it crashes, 
this is unsurprising. Please do feel free to file bugs, but right now 
they'll probably just be forwarded upstream. Please do not be surprised 
if it doesn't work. If you're running binary drivers, things get even 
more complicated and there's a reasonable chance that things will fail 
to work in strange and unexpected ways.

Have fun, and start thinking of ways that this technology can be used 
for the force of good.
-- 
Matthew Garrett | mjg59 at srcf.ucam.org


I hope you people find this useful, the post can be found at:

[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2006-February/000079.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2006-February/000079.html)

---

### Post by Rotarychainsaw on 2006-02-16
I tried this and got the error:

 gnome-window-decorator, Failed to load shadow images
compiz.real: No composite extension

Should I add composite to my xorg.conf?

*edit - added composite and now I get the Texture error. getting closer.

---

### Post by nikopol on 2006-02-16
[QUOTE=nikopol]I think there's a problem with this install in that it installed me a US keyboard by default. When I switched to the correct keyboard (UK), it's caused a huge problem with the gnome-settings-daemon as it won't start at all anymore leaving me with a rather basic desktop! I'm looking into resolving this but this error is a pain in the butt to sort out IIRC..[/QUOTE]

Hmmm - no go. This is well and truly screwed up. Some problem with xkb I think interacting with the new setup. Problem is coming back to where we once began which doesn't seem to be simple. I'd advise AGAINST changing your keyboard setup in XGL :)

---

### Post by Rob2687 on 2006-02-16
When I changed teh kb in XGL, it wouldn;t even start anymore so I had to recompile with --disable-xkb :(

---

### Post by Fedup on 2006-02-16
[QUOTE=DeeZiD]Great news for owners of older nvidia-cards :)

```
2006-02-16  David Reveman  <davidr@novell.com>

	* src/glitz.h (GLITZ_REVISION): Bump version to 0.5.3.

	* configure.in: Bump version to 0.5.3.

	* src/glitz_texture.c: Fix so that GL_ARB_texture_rectangle
	and GL_ARB_texture_border_clamp are not required for texture
	object creation.

	* TODO: Add note about removing some complexity.

	* src/glitz_pixel.c (glitz_get_pixels): Patch together clipped
	fetching of pixels.
```

Now you can even use your older cards for Xgl \\:D/ 
(I will test my old Geforce2MX in a few moments)

regards Dennis[/QUOTE]

Well, I'm about ready to completely wipe Linux and go back to Windows ;) 

Just tried downloading the latest glitz from cvs, it seems to compile correctly.. but then 
```
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
```

:evil:  :evil:  ](*,) 

so I guess I'm not doing something right - and at a guess Its still using the older glitz library... so how do I tell it to use the newer ones?
:-k

---

### Post by anders.ostling on 2006-02-16
Just a quick "mee too". Have a laptop with a GF 4200Go, and this is really amazing. No artefacts whatsoever, wobbling and fading is smooth and stable. Really cool!

The only problem I have found is that my Swedish keyboard has been configured as US, and I need to manually change that when X starts ...

Anders

---

### Post by MadMan2k on 2006-02-16
thats how I did it:
[http://www.madman2k.net/?module=article&id=19#p2](http://www.madman2k.net/?module=article&id=19#p2)

---

### Post by mgalvin on 2006-02-16
Seems I am the unlucky one. Oh well.

I followed the instructions but when I run thefuture or compiz manually compiz just crashes. It just dies without doing or saying anything and I end up with no window manager, switcher, or anything other then windows with no borders that I cannot move. I can just restart metacity and killall the gnome bits to get working again but no neat effects.

I am on an amd64 machine (Xeon really) with an NVIDIA Corporation NV37GL [Quadro FX 330] card with TwinView and all the rest.

When using Xgl TwinView stops working and I just get a spanned desktop across the two heads. No biggie as this was expected since the first post said as much. I also tried turning off all the TwinView stuff which made no difference.

Since compiz just keeps crashing no matter what I try or how many times I run it, I straced' it.

Hopefully this strace output might help diagnose the issue.

[http://www.simplifiedcomplexity.com/lumber/compiz.strace.txt](http://www.simplifiedcomplexity.com/lumber/compiz.strace.txt)

---

### Post by Florob on 2006-02-16
Well, it was always working for me, but this howto was helpfull, too.
I'm just wondering if it's normal for Xgl to use a lot of the CPU when I do something with compiz (It uses up to 90% from just moving a window).

Also I have some comments on the howto itself:
> Change every line but the &#8220;Identifier&#8221; line to look just like mine:
One shouldn't change the BusID line either, because it changes from machine to machine and will not always work with this values.

> Find the &#8220;Module&#8221; section. Comment out the &#8220;Glcore&#8221; and &#8220;dri &#8220; modules and make sure a &#8220;glx&#8221; module is there.
Why is this neccessary I have read this in many places, but it makes no difference for me whether I comment out Glcore and dri or not.

> sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1
You actually only need to do ```
sudo apt-get install compiz xserver-xgl
``` the rest is handeld by dependancies.

---

### Post by chrisrx on 2006-02-16
Has anyone made a deb for the newest glitz?

---

### Post by nikopol on 2006-02-16
Solved the keyboard bug which seems to be a gnome bug more than anything else.

If one tried to put another keyboard higher than the US one in the keyboard config, the gnome-settings-daemon will crash and no longer work until one puts the US keyboard back on top. You can set the other keyboard as default without any trouble which is good. It's a pretty major bug so I'd better file it. I imagine the XGL messing around probably generated the new keyboard?

Less seriously, I wonder if it's some overly patriotic developer who inserted this bug for anyone who as the temerity to put the US "down"! :D

---

### Post by thekiller on 2006-02-16
When i run "thefuture", it brings me a full black screen with a cursor (kinda similar to somebody else's problem posted earlier). I have an NViDia NV11 GeForce2 MX/MX 400 graphics card.

Any ideas/suggestions ?

EDIT : Funny thing is even after getting a black screen, when i move my cursor around it changes to an arrow. I move back the arrow to the place it changed to a cursor, and i retyped "thefuture" in the blind, and it shows me the outline of the terminal but then again goes black. I started moving around the cursor again, and apparently on double-clicking the mouse somewhere towards right-top, shows a white rectangular box for like a split second and then it goes away. I am sure something is there, but is messed up on my computer. Any ideas ? I also pressed CTRL+ALT+left and something changed for sure, cos i cant get my arrow back to a cursor, so i guess something did move here. lol :)

---

### Post by ubuntu_monkey on 2006-02-16
I Have the same problem with my Nvidia Geforce Mx. 

The xserver works, but as soon as I start compiz, all windows goes black. If i press <Alt> and drag the windows I get the wobbling window moving effect. So Compiz works, it's just window bitmaps doesn't get rendered on the screen.

Probably this is a to old card.  But let's hope for a fix!

---

### Post by thekiller on 2006-02-16
ok now i see an error, when i type "killall compiz.real" in the blind. It complains about "Couldnt find redirected window 0xc0003c to texture". and "pixmap cant be bound to texture".

I think many had this error while playin with compiz. And I think i have ran "thefuture" a million times now, and i can say its probably an old card that i have. :(

EDIT : Now im thinking "Do i have the correct drivers installed ?" Cos I know before i used to see an Nvidia splash screen on killing the x server, NOW, not anymore !!!! Can somebody else point that please ??

---

### Post by chrisrx on 2006-02-16
They are all bugs to do with the lack of pixel shading in older cards.  If I understand correctly the newer glitz might fix this, but I'm waiting on someone to release a deb to confirm this.

---

### Post by ubuntu_monkey on 2006-02-16
[QUOTE=chrisrx]They are all bugs to do with the lack of pixel shading in older cards.  If I understand correctly the newer glitz might fix this, but I'm waiting on someone to release a deb to confirm this.[/QUOTE]

I tried to build it from the cvs. And I can confirm that it does work. :)

---

### Post by Rotarychainsaw on 2006-02-16
monkey, did you just build glitz from cvs and it worked? or did you have to build glitz and reinstall xgl and compiz?

---

### Post by chrisrx on 2006-02-16
Hey ubuntu_monkey, what graphics card are you using?

---

### Post by mrogers on 2006-02-16
Did this on a fresh install of Dapper nightly 2/15/06, I've got a GF6600GT and the eyecandy itself works great. Two serious problems:

- I have dual monitors. As noted before, it is most definitely broken. What I want to know is: why? And when might it be fixed?

- My other serious problem is that I can't move dialog boxes. Any non-standard window -- the About FireFox dialog, the Themes window, etc -- that doesn't have normal Minimize/Maximize/Close buttons *cannot be moved* from where it initially appears on the screen. Any ideas on how to fix this?

---

### Post by poofyhairguy on 2006-02-16
[QUOTE=Florob]
I'm just wondering if it's normal for Xgl to use a lot of the CPU when I do something with compiz (It uses up to 90% from just moving a window)..[/QUOTE]

For now, yes.

> 
One shouldn't change the BusID line either, because it changes from machine to machine and will not always work with this values..

Thanks.

> 
Why is this neccessary I have read this in many places, but it makes no difference for me whether I comment out Glcore and dri or not..

Its an Nvidia thing. I suggest doing it.

> 
You actually only need to do ```
sudo apt-get install compiz xserver-xgl
``` the rest is handeld by dependancies.

Thanks. I wasn't sure about that.

---

### Post by ubuntu_monkey on 2006-02-16
[QUOTE=chrisrx]Hey ubuntu_monkey, what graphics card are you using?[/QUOTE]

An old Geforce 2 Mx. 

I compiled glitz with: ./autogen --prefix=/usr
So that the ubunut package would be overwritten. I think you should run ldconfig after the install and then try to run compiz again.

 - Mr Monkey

---

### Post by poofyhairguy on 2006-02-16
[QUOTE=mrogers]Did this on a fresh install of Dapper nightly 2/15/06, I've got a GF6600GT and the eyecandy itself works great. Two serious problems:

- I have dual monitors. As noted before, it is most definitely broken. What I want to know is: why? And when might it be fixed?

- My other serious problem is that I can't move dialog boxes. Any non-standard window -- the About FireFox dialog, the Themes window, etc -- that doesn't have normal Minimize/Maximize/Close buttons *cannot be moved* from where it initially appears on the screen. Any ideas on how to fix this?[/QUOTE]

I wish I knew the answer to both of these questions, as it affects me too. All I can say is to wait for the next set of drivers...

---

### Post by thekiller on 2006-02-16
Hey PHG, do u know if i need to do sth special for my NVIDA NV11 MX 400 card ? I am not able to get "thefuture" working !

---

### Post by salsafyren on 2006-02-16
[QUOTE=DeeZiD]Now my geforce2MX200 works with Xgl :p 
And it is as fast as my geforce6600 gt!!!

(Image-quality without DVI is really bad imho ;) )

regards Dennis[/QUOTE]

Could you tell which nvidia driver you use?

I've had problems with the new drivers.

/Chris

---

### Post by aamukahvi on 2006-02-16
[QUOTE=mrogers]- My other serious problem is that I can't move dialog boxes. Any non-standard window -- the About FireFox dialog, the Themes window, etc -- that doesn't have normal Minimize/Maximize/Close buttons *cannot be moved* from where it initially appears on the screen. Any ideas on how to fix this?[/QUOTE]
Hold Alt then drag the window. Don't know how to do this without modifer, tho.

---

### Post by Das Oracle on 2006-02-16
it works perfectly except for one tiny thing. when i watch movies and fullscreen them the audio gets behind...i put it back to a window and its fine. never did this prior to xgl but still thanks a ton for the howto

---

### Post by JDay on 2006-02-16
Well, it *mostly* works fine for me. All the plugins seems to work, except for cube, zoom and fade. The workspace-switcher applet also refuses to work (only shows one workspace). Any ideas?

---

### Post by bruce89 on 2006-02-16
It doesn't work at all for me, but that's probably because I am using the AMD64 version.  I have a screenshot here.

---

### Post by monchichi on 2006-02-16
What's the word on AMD64 Xgl? I tried to compile cvs but just ran into more headaches. Can we get updated source uploaded to the build farm please please please pleasssseee?

---

### Post by soulglo83 on 2006-02-16
i commented out the composite enable lines @ the bottom of my xorg.conf from the terrax howto, so it would match with this howto. which cleared up the GLX_EXT_texture_from_pixmap not found errors from compiz, that was preventing compiz from running. but now it doesnt run either, i receive a different error 'compiz: No composite extension' (since i updated and reloaded x).  i use an nvidia geforce 5500 fx agp card, and have managed to receive the same results with both the cvs compiles of mesa and xserver-glx and compiz, and the precompiled debs.  am i missing something? this error has been reported by two others in this post who haven't remedied this as well.  this does recurr, even after 20 or more attempts. how do i get a composite manager working with my hardware? i though with nvidia this was well supported

EDIT: since compiz wont start and its barking about a composite extension ive left xorg w/ the composite lines active in the bottom of my xorg, GLX_EXT_texture_from_pixmap is present in glxinfo, however compiz still complains that GLX_EXT_texture_from_pixmap.... is not found....

---

### Post by dzoe on 2006-02-16
I'm happy to report that ubuntu_monkey's suggestion (compiling CVS glitz) is working perfectly here (on an NV18 [GeForce4 MX 4000 AGP 8x]).

Yay!

---

### Post by salsafyren on 2006-02-16
[QUOTE=ubuntu_monkey]An old Geforce 2 Mx. 

I compiled glitz with: ./autogen --prefix=/usr
So that the ubunut package would be overwritten. I think you should run ldconfig after the install and then try to run compiz again.

 - Mr Monkey[/QUOTE]

Hey,

Which nvidia driver do  you use?

/Chris

---

### Post by chrisrx on 2006-02-16
thanks ubuntu_monkey it works for me :D.  Buythe screen is to distorted for it to be used
salsafyren You should probably use the newest nvidia module because the stability with composite has been improved

---

### Post by poofyhairguy on 2006-02-16
[QUOTE=JDay]Well, it *mostly* works fine for me. All the plugins seems to work, except for cube, zoom and fade. The workspace-switcher applet also refuses to work (only shows one workspace). Any ideas?[/QUOTE]


It changes the Gnome panel. Clicking where the other workspaces should be still works.

---

### Post by poofyhairguy on 2006-02-16
[QUOTE=thekiller]Hey PHG, do u know if i need to do sth special for my NVIDA NV11 MX 400 card ? I am not able to get "thefuture" working ![/QUOTE]
 
All people with cards that are older (not weaker) than a 5200 FX (aka anything not a Directx 9 card) have to compile the newest glitz from cvs first.

I try to keep my guides simple (aka I abhor telling people how to compile things) but since people like to use Linux with older harder if someone will give me a small guide on whats needed to compile glitz I will add it to the main guide.

---

### Post by chrisrx on 2006-02-16
Is anyone else with a geforce2 having major graphical glitches.  Firefox is unusable for me because the window is just filled with glitches and stretched out things.

Is anyone having problems with amsn aswell?  I think it's xgl related because I never had a problem before but now tcl/tk throws up an error
```
Application initialization failed: this isn't a Tk application
```

Also what video driver should I use in mplayer for (moderately) smooth video playback.  I used to use xv but now it gives me choppy playback and gl just crashes altogether

---

### Post by pomalin on 2006-02-16
Thanks ubuntu_monkey it work perfectly and smoothly with your trick ./autogen.sh --prefix=/usr on my nvidia4 488 Go.

So happy :D

---

### Post by Mattias on 2006-02-16
Thank You for the guide everything is ok on my computer. All effects seem to be there (and they are really impressive )The only thing  is that processor usage of xgl is almost 100% when trying to play movies. It's so bad that the playback is slow. Is this to be expected normally ?

---

### Post by Rotarychainsaw on 2006-02-16
It seems the gconf plugin is not letting compiz start on my system. This is all repo stuff, and without the gconf plugin everything seems to work. I was wondering if there is a gconf related package that needs to be installed. thanks

---

### Post by ubuntu_monkey on 2006-02-16
[QUOTE=salsafyren]Hey,

Which nvidia driver do  you use?

/Chris[/QUOTE]
ii  linux-restricted-modules-2.6.12-10-386-nvidia-legacy 2.6.12.4-11.1                        Non-free Linux 2.6.12 NVIDIA legacy module o
ii  nvidia-glx                                           1.0.8178+2.6.15.5-2                  NVIDIA binary XFree86 4.x/X.Org driver
ii  nvidia-kernel-common                                 20051028+1                           NVIDIA binary kernel module common files

---

### Post by thekiller on 2006-02-16
i think im gonna give up tryin to make it work on my old pc. i installed the glitz from cvs, and followed the trick by ubuntu_monkey, but apparently my x is not coming up anymore. It just shows a hung up weird screen with my the clock (cursor) stuck in the middle of the screen. 

Anyway thats it, i wasted all day long in tryin to make it work.

next step :

apt-get remove xserver-xgl compiz ....  :)

Im happy with what i have. Thanks all for the help though !

---

### Post by ShanghaiTeej on 2006-02-16
I can confirm that following this guide and launching typing "thefuture" is giving just a black screen and a cursor on GeForce4 MX 440 graphics cards.  The link in Poofyhairguy's walkthrough does state that there are mass bugs with this graphics card and xgl.  So we probably have to wait awhile, which sucks.  Thanks for the walk through though.

---

### Post by thekiller on 2006-02-16
[QUOTE=ShanghaiTeej]I can confirm that following this guide and launching typing "thefuture" is giving just a black screen and a cursor on GeForce4 MX 440 graphics cards.  The link in Poofyhairguy's walkthrough does state that there are mass bugs with this graphics card and xgl.  So we probably have to wait awhile, which sucks.  Thanks for the walk through though.[/QUOTE]

Just commenting more on this one : (cos nobody mentioned this anywhere)

While installing glitz from CVS, make sure you have automake-1.9 installed, and which requires aclocal-1.9 as well.

So make necessary changes in autogen.sh, by changing 
> 
ACLOCAL=${ACLOCAL-aclocal}
AUTOMAKE=${AUTOMAKE-automake}


TO
> 
ACLOCAL=${ACLOCAL-aclocal-1.9}
AUTOMAKE=${AUTOMAKE-automake-1.9}


But apparently, it didnt work out for me for old Nvidia card.

---

### Post by lucas on 2006-02-16
Thanks for an exelent guide, I will try this as soon as the dapper download has finnished.

---

### Post by chrisrx on 2006-02-16
[QUOTE=thekiller]Just commenting more on this one : (cos nobody mentioned this anywhere)

While installing glitz from CVS, make sure you have automake-1.9 installed, and which requires aclocal-1.9 as well.

So make necessary changes in autogen.sh, by changing 


TO


But apparently, it didnt work out for me for old Nvidia card.[/QUOTE]
don't forget ldconfig

---

### Post by plb on 2006-02-16
After running "thefuture" all titlebars and panels disppear and I have to restart gnome...might have something to do with amd64..dunno

---

### Post by JDay on 2006-02-16
[QUOTE=poofyhairguy]It changes the Gnome panel. Clicking where the other workspaces should be still works.[/QUOTE]
Well, it doesn't for me. Oh, well. The fade effect working for anyone else?

---

### Post by endy on 2006-02-16
[quote=plb]After running "thefuture" all titlebars and panels disppear and I have to restart gnome...might have something to do with amd64..dunno[/quote]

If you type "metacity --replace &" in the terminal you'll get your titlebars back.

I too haven't got this running on my native AMD64 partition yet :( I've tried a fair bit of tweaking and recompiling but I guess it isn't ready for AMD64 yet... until it is I'll have to rely on my PowerBook for eye candy goodness but it would be nice to see Gnome have a piece of that oh so tastey pie :)

---

### Post by nikopol on 2006-02-16
I find the graphics to be very slow if I'm not running thefuture script - is that normal?

So far crashing or messed up programs:
**MythTV (frontend)** (completely crashes X :twisted: )
**Xine** - the control panel is scrambled up making it unusable.
**Enemy Territory** - ok I was asking for trouble there :D X dies immediately.

---

### Post by aamukahvi on 2006-02-16
Hey NVidia fellaz,

how are your videos playing on Xgl? I have ATI with no xv, videos are choppy and processor usage is off the charts. I was thinking about buying an nvidia card but someone here said that he had problems with video playback even with his nvidia card.

---

### Post by nikopol on 2006-02-16
Video isn't great - the sound goes out of synch and there is some dragback every few seconds. I kinda don't have a problem with it though since it's experimental so I'd expect this to be ironed out relatively soon. I wouldn't use as my fulltime X config due to these issues I guess...

---

### Post by aamukahvi on 2006-02-16
Ok thanks. Won't go shopping just yet -- wait and see I guess... I think the next round of drivers may work wonders. But when is that? :roll:

---

### Post by Technoviking on 2006-02-16
I'm getting the same thing, any ideas?

[Nevermind switching to 24 bit fixed it]

[QUOTE=Aphelion]Hi fellow Xgl users ;)

I managed to install Xgl and run compiz with this tutorial. It al works fine except some strange redraw? problems. Please look at the attached screenshot. Does anyone know how to fix this problem?[/QUOTE]

---

### Post by gripner on 2006-02-16
Hi, I followed this howto in every step. Only thing i do is compile the nvidia drivers myself since i have to

Have a dual core P4 with 6600gt card.

WHen gmd starts it exits with the error that it can not find /usr/lib/xorg/modules/xgl/libglx.so

that file does not exists there altho it does exist in /usr/lib/xorg/modules/extension i think it was. makeing a symlink will not work, get an error undefined symbol xf86 or summing

oh also /usr/lib/xorg/modules/extension/libglx.so is a symlink to libglx.so.nvidiasdrivenumber

help pleas!

---

### Post by kamstrup on 2006-02-16
Hey worked great! . . . Until...

I removed (and readded) the wobbly plugin from gconf, and then my titlebars disappeared!

They don't even get back when I log out and log back in! Anyone? gnome-window-decorator is definitely running. Killing it and restarting it has no effect either...

PS: Perhaps someone should also write up a list with all the fancy tricks... Desktop rotation, stick-to-edges, etc.

---

### Post by TheDude on 2006-02-16
Thank you so much PHG (and all others)\\:D/

---

### Post by aent on 2006-02-16
[QUOTE=chrisrx]Is anyone else with a geforce2 having major graphical glitches.  Firefox is unusable for me because the window is just filled with glitches and stretched out things.[/QUOTE]
I believe this is because of glitz bugs and is fixed in CVS. I'd wait till the next version of glitz and maybe even wait for the next Xgl for GeForce 2 and older cards. It is still usable but you have to learn how to use around it... like launch Firefox from the menu rather than from a launcher, the affect from the launcher screws it up... avoid the minimize affect from metacity, and stuff like that. I can't wait for this stuff to stabilize... I can't wait for it... I need Xinerama for my modern desktop and the new glitz for my laptop... must resist CVS :twisted:

---

### Post by Rotarychainsaw on 2006-02-16
Video plays awesome for me. No slowdows or anything, even while wobbling. I have a 6800gt (nvidia).

---

### Post by covox on 2006-02-16
aamukahvi: Video works great. MPlayer + accelerated XV can withstand any amount of compiz-related punishment thrown at it. MPlayer + XImage also works, but requires 2x the CPU. (GeForce 6600 w/256mb, Athlon XP 1800)

A silver sixpence for whichever saint fixes that blasted Shift+Backspace bug in Xgl. It's 110% unbearable if you've grown dependant on Ctrl-Backspace to remove words. (I'm assuming it's in Xgl, as it's still crashing when only running xterm)

---

### Post by lord_crow on 2006-02-16
Can anyone **PLEASE** confirm if this works under amd64 ? 

( and i mean repo's packages )

thanks :rolleyes:

---

### Post by mjg59 on 2006-02-16
[QUOTE=lord_crow]Can anyone **PLEASE** confirm if this works under amd64 ? [/QUOTE]

Currently? No. It needs a fix to mesa and then for xgl to be rebuilt. I'll probably have time to do that over the weekend.

---

### Post by lord_crow on 2006-02-16
[QUOTE=mjg59]Currently? No. It needs a fix to mesa and then for xgl to be rebuilt. I'll probably have time to do that over the weekend.[/QUOTE]

Well, at least i know that someone is taking care of it \\:D/ , thanks for your reply

---

### Post by alvinblank on 2006-02-16
Anyone willing to post a CVS version of glitz?

---

### Post by chanders on 2006-02-16
[QUOTE=alvinblank]Anyone willing to post a CVS version of glitz?[/QUOTE]

Hey I second that! But I am willing to compile it myself if I can find some steps? Anyone? I am sure it wont take 5 mins to write up the steps for us guys...

:o

---

### Post by jasay on 2006-02-16
[QUOTE=kamstrup]Hey worked great! . . . Until...

I removed (and readded) the wobbly plugin from gconf, and then my titlebars disappeared!

They don't even get back when I log out and log back in! Anyone? gnome-window-decorator is definitely running. Killing it and restarting it has no effect either...

PS: Perhaps someone should also write up a list with all the fancy tricks... Desktop rotation, stick-to-edges, etc.[/QUOTE]
Did you put wobbly back in the same place in the list of plugins?  I guess some of the plugins depend on others having alrewady loaded so make sure wobbly is listed right after decoration.

---

### Post by codejunkie on 2006-02-16
[QUOTE=alvinblank]Anyone willing to post a CVS version of glitz?[/QUOTE]
i've attached the latest version of glitz from cvs.

[QUOTE=chanders]Hey I second that! But I am willing to compile it myself if I can find some steps? Anyone? I am sure it wont take 5 mins to write up the steps for us guys...
:o[/QUOTE]
and to compile it extract the archive cd to the glitz dir and run
```
./autogen.sh --prefix=/usr
```
then
```
make
```
and last
```
sudo make install
```
if it complains about dependency issues when you compile run
```
sudo apt-get install libx11-6 libx11-dev libxau-dev libxau6 libxcomposite-dev libxcomposite1 libxcursor-dev libxcursor1 libxdamage-dev libxdamage1 libxdmcp-dev libxdmcp6 libxext-dev libxext6 libxfixes-dev libxfixes3 libxfont-dev libxfont1 libxft-dev libxft2 libxi-dev libxi6 libxinerama-dev libxinerama1 libxkbfile-dev libxkbfile1 libxklavier10 libxmu-dev libxmu-headers libxmu6 libxmuu-dev libxmuu1 libxp6 libxpm-dev libxpm4 libxrandr-dev libxrandr2 libxrender-dev libxrender1 libxres1 libxss1 libxt-dev libxt6 libxtrap-dev libxtrap6 libxtst-dev libxtst6 libxv-dev libxv1 libxvmc1 libxxf86dga1 libxxf86misc1 libxxf86vm1 x11proto-bigreqs-dev x11proto-composite-dev x11proto-core-dev x11proto-damage-dev x11proto-fixes-dev x11proto-fonts-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-record-dev x11proto-render-dev x11proto-resource-dev x11proto-scrnsaver-dev x11proto-randr-dev x11proto-record-dev x11proto-render-dev x11proto-resource-dev x11proto-scrnsaver-dev x11proto-trap-dev x11proto-video-dev x11proto-xcmisc-dev x11proto-xext-dev x11proto-xinerama-dev libpng12-dev build-essential gcc gcc-3.4 libncurses5 libncurses5-dev libqt3-mt-dev m4 autoconf automake1.7 autotools-dev libtool libxfont-dev xtrans-dev libfreetype6-dev zlib1g-dev libgl1-mesa-dev gconf libgconf-dev gconf-editor cvs libgconf2-dev libwnck-dev
```

---

### Post by joakim2 on 2006-02-16
Hohoho - Xgl started up fine, launching gnome-decorator no problem, launching compiz: black screen with a cursor and something flashing a little when right clicking on the "desktop" and such. I launched compiz with error redirection to a file which when I looked at it is packed with:

compiz.real: pixmap 0x260000c can't be bound to texture
compiz.real: pixmap 0x2600018 can't be bound to texture
compiz.real: pixmap 0x2600084 can't be bound to texture
compiz.real: pixmap 0x2a00037 can't be bound to texture
compiz.real: Couldn't bind redirected window 0xc0003c to texture
compiz.real: pixmap 0x2a00039 can't be bound to texture
compiz.real: Couldn't bind redirected window 0xc00003 to texture
compiz.real: pixmap 0x2a0003b can't be bound to texture
compiz.real: Couldn't bind redirected window 0x240000c to texture
compiz.real: pixmap 0x2a0003d can't be bound to texture
compiz.real: Couldn't bind redirected window 0xe00030 to texture
compiz.real: pixmap 0x2a00037 can't be bound to texture

etc etc etc...

NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]

---

### Post by codejunkie on 2006-02-16
[QUOTE=joakim2]Hohoho - Xgl started up fine, launching gnome-decorator no problem, launching compiz: black screen with a cursor and something flashing a little when right clicking on the "desktop" and such. I launched compiz with error redirection to a file which when I looked at it is packed with:

compiz.real: pixmap 0x260000c can't be bound to texture
compiz.real: pixmap 0x2600018 can't be bound to texture
compiz.real: pixmap 0x2600084 can't be bound to texture
compiz.real: pixmap 0x2a00037 can't be bound to texture
compiz.real: Couldn't bind redirected window 0xc0003c to texture
compiz.real: pixmap 0x2a00039 can't be bound to texture
compiz.real: Couldn't bind redirected window 0xc00003 to texture
compiz.real: pixmap 0x2a0003b can't be bound to texture
compiz.real: Couldn't bind redirected window 0x240000c to texture
compiz.real: pixmap 0x2a0003d can't be bound to texture
compiz.real: Couldn't bind redirected window 0xe00030 to texture
compiz.real: pixmap 0x2a00037 can't be bound to texture

etc etc etc...

NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x][/QUOTE]
i've got the same video card and i was having the same errors until i compiled glitz from cvs now it's working fine it's just a little slow when using the wobbly effect.

---

### Post by Rotarychainsaw on 2006-02-16
Joakim2, did you install the glitz in the post above yours? I didn't really read the thread, but that is your problem.

---

### Post by onandon on 2006-02-16
[COLOR="Red"]HELP[/COLOR]
I follow "Default XGL Install and General Tips For Gnome and Nvidia " posted by poofyhairguy to install XGL. After rebooting, when i typed "thefuture", error comes as follows:
[COLOR="Red"]"compiz: No composite extension
gnome-window-decorator, Failed to load shadow images"[/COLOR]

could anyone help? Thank you.

Ps: Gnome+NVIDIA Corporation NV43 [GeForce 6600 GT]

---

### Post by Rotarychainsaw on 2006-02-16
yeah, you have to enable composite in your xorg.conf. I forget the excact lines offhand, but do a search and you will find it.

---

### Post by drizek on 2006-02-16
wow, thanks so much poofy. i have been waiting around all day for suse 10.1 beta 4(it was supposed to be released today damn it!) and it is still not out. im leaving on vacation tomorrow at 5am so here i am again, about to install dapper for the third time to try xgl out.

---

### Post by poofyhairguy on 2006-02-16
[QUOTE=Rotarychainsaw]yeah, you have to enable composite in your xorg.conf. I forget the excact lines offhand, but do a search and you will find it.[/QUOTE]

I did not have to for my 6600 GT, but I promise it does not hurt. 

Look to my older guide to find out how to do this....

---

### Post by poofyhairguy on 2006-02-16
[QUOTE=aamukahvi]Hey NVidia fellaz,

how are your videos playing on Xgl? I have ATI with no xv, videos are choppy and processor usage is off the charts. I was thinking about buying an nvidia card but someone here said that he had problems with video playback even with his nvidia card.[/QUOTE]

On my 6600 GT videos are as smooth as can be with my guide. Wobble and everything. Could not ask for more.

I think the trick is to buy a 6xxx series Nvidia card if you want to be sure everything with "Just Work" well once its all set up. That group has some problems, but by far less than any other group.

The day Compiz was released my 6600 GT payed for itself!

---

### Post by zentagonist on 2006-02-16
I still keep getting the following error: 

compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

It doesn't matter how many times I run 'thefuture' ... I've probably ran it 70-some times now.
Any help would be appreciated.:D

---

### Post by Ainvar on 2006-02-16
Awesome howto, I am doing this running Dapper Drake on a Dell Precision Workstation M70 laptop that is sporting a nvidia quadro fx go 1400 video card.
I am running everything stock and nothing manually compiled or anything.

Sweet howto, cedega does run like but until you restart X, but movies do play when running under thefuture script. Awesome howto and this is how eyecandy is suppose to be in linux :) :)

Awesome howto!! had to say it once again.

---

### Post by joakim2 on 2006-02-16
[QUOTE=Rotarychainsaw]Joakim2, did you install the glitz in the post above yours? I didn't really read the thread, but that is your problem.[/QUOTE]

Durrrr, of course that is my problem, I can't believe I missed it.  :( It works with that glitz and I don't think it's very slow either, pretty smooth if you ask me. The only thing that seems a bit off is the fuzziness of text in menus and such until you have rolled over the text once, then it becomes sharp again. Oh well, I guess that will be fixed eventually. Pretty cool stuff all in all.

---

### Post by poofyhairguy on 2006-02-16
[QUOTE=zentagonist]I still keep getting the following error: 

compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

It doesn't matter how many times I run 'thefuture' ... I've probably ran it 70-some times now.
Any help would be appreciated.:D[/QUOTE]

First:

1. What card do you have?

2. Go in synaptic and search for GLX. Install anything that starts "libglx...."

---

### Post by poofyhairguy on 2006-02-16
[QUOTE=Ainvar]Awesome howto, I am doing this running Dapper Drake on a Dell Precision Workstation M70 laptop that is sporting a nvidia quadro fx go 1400 video card.
I am running everything stock and nothing manually compiled or anything.

Sweet howto, cedega does run like but until you restart X, but movies do play when running under thefuture script. Awesome howto and this is how eyecandy is suppose to be in linux :) :)

Awesome howto!! had to say it once again.[/QUOTE]

Thanks I a lot. I wasn't going to make a guide till I could do it right. 

Actually, I decided I wasn't going to do a guide until I could find a way to not leave out ATI users. That other thread gave me my chance. I lack an ATI card for a reason and a year after my first guide I still hate telling ATI people again and again that "your card's drivers are poorer, so this might not work well for you." It makes ME feel bad, even though its ATI's fault.

I hope XGL will even that up some. FORCE ATI to make better drivers with user demand. Just not enough people asked for EXA support- Nvidia did it without anyone asking.

---

### Post by varunus on 2006-02-16
Is anyone else having glx crashes with compiz on?  GLX works just fine when metacity is run as the window manager; compiz is what triggers the crashes.  (Anything that uses opengl, be it glxgears or the screensaver, causes the crash.)

---

### Post by poofyhairguy on 2006-02-16
[QUOTE=kamstrup]
PS: Perhaps someone should also write up a list with all the fancy tricks... Desktop rotation, stick-to-edges, etc.[/QUOTE]


I started it on the doc site where it belongs. If other people know whats going on, please add to it.

The Gentoo wiki page for compiz is way better. The friendly rivalry between our distro and theirs will hopefully motivate people to share what they know!

---

### Post by zentagonist on 2006-02-16
[QUOTE=poofyhairguy]First:

1. What card do you have?

2. Go in synaptic and search for GLX. Install anything that starts "libglx...."[/QUOTE]
wow, that was a quick response!

ok:
1. NVidia GeForce4 MX

2. Ok, done

I tried again ... same result :-/

---

### Post by chrisrx on 2006-02-17
Have you upgraded to the newest version of glitz?

---

### Post by chrisrx on 2006-02-17
[QUOTE=codejunkie]```
sudo apt-get install libx11-6 libx11-dev libxau-dev libxau6 libxcomposite-dev libxcomposite1 libxcursor-dev libxcursor1 libxdamage-dev libxdamage1 libxdmcp-dev libxdmcp6 libxext-dev libxext6 libxfixes-dev libxfixes3 libxfont-dev libxfont1 libxft-dev libxft2 libxi-dev libxi6 libxinerama-dev libxinerama1 libxkbfile-dev libxkbfile1 libxklavier10 libxmu-dev libxmu-headers libxmu6 libxmuu-dev libxmuu1 libxp6 libxpm-dev libxpm4 libxrandr-dev libxrandr2 libxrender-dev libxrender1 libxres1 libxss1 libxt-dev libxt6 libxtrap-dev libxtrap6 libxtst-dev libxtst6 libxv-dev libxv1 libxvmc1 libxxf86dga1 libxxf86misc1 libxxf86vm1 x11proto-bigreqs-dev x11proto-composite-dev x11proto-core-dev x11proto-damage-dev x11proto-fixes-dev x11proto-fonts-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-record-dev x11proto-render-dev x11proto-resource-dev x11proto-scrnsaver-dev x11proto-randr-dev x11proto-record-dev x11proto-render-dev x11proto-resource-dev x11proto-scrnsaver-dev x11proto-trap-dev x11proto-video-dev x11proto-xcmisc-dev x11proto-xext-dev x11proto-xinerama-dev libpng12-dev build-essential gcc gcc-3.4 libncurses5 libncurses5-dev libqt3-mt-dev m4 autoconf automake1.7 autotools-dev libtool libxfont-dev xtrans-dev libfreetype6-dev zlib1g-dev libgl1-mesa-dev gconf libgconf-dev gconf-editor cvs libgconf2-dev libwnck-dev
```[/QUOTE]
wow all i needed was xserver-xorg-dev  :p  You can go easy on the rest

---

### Post by JLB on 2006-02-17
absolutely easiest thing to enable. Thanks for the how-to Poof!
But this whole thing is just to annoying to keep. I am using twinview here and it is totally disruptive to use. Hopefully, twinview support will be forthcoming soon.

---

### Post by jamesshuang on 2006-02-17
hey poofy, I think you should probably make a note that if nothing happens, but compiz seems to have worked, you should go into the gconf and add the plugins there... I had issues with that on both my computers (probably a result of trying compiz before), and in any case nothing happened until I did that.

Just a note to think about ;)

---

### Post by zentagonist on 2006-02-17
[QUOTE=chrisrx]Have you upgraded to the newest version of glitz?[/QUOTE]

sure  have.

actually, when I did the search in synaptic, the only thing I didn't have installed was the glitz-dev package ... I installed that too then

---

### Post by codejunkie on 2006-02-17
[QUOTE=chrisrx]wow all i needed was xserver-xorg-dev  :p  You can go easy on the rest[/QUOTE]
i was just being lazy :-\" i didn't know the exact dependency so i just copied over all the packages i used when i compiled xgl and compiz.

---

### Post by Gandalf on 2006-02-17
Had anyone tried another (non-ati/nvidia) card? i have an Intel integrated one on my HP :(

---

### Post by chrisrx on 2006-02-17
[QUOTE=zentagonist]sure  have.

actually, when I did the search in synaptic, the only thing I didn't have installed was the glitz-dev package ... I installed that too then[/QUOTE]
the version in synaptic isn't the newest version

to do that try this
```
apt-get install build-essential libtool automake1.9 xserver-xorg-dev cvs
cvs -d :pserver:anoncvs@cvs.freedesktop.org:/cvs/cairo login
cvs -z3 -d :pserver:anoncvs@cvs.freedesktop.org:/cvs/cairo co glitz
cd glitz
./autogen.sh --prefix=/usr
make
sudo make install
sudo ldconfig
```

just a note to say I've completely forgotten the deps but I think it's automake that you need otherwise it complains about aclocal. libtool I put in the just to be safe.

---

### Post by jacrider on 2006-02-17
Ok.  Please bear with me, but I have tried to follow the many threads about xlg and compiz, and am still missing a fundamental issue - does any of this work in Breezy yet?

I am not really interested in moving at this point to Badger, but would like to be able to install both xgl and compiz.

Thanks.

---

### Post by chrisrx on 2006-02-17
[QUOTE=jacrider]Ok.  Please bear with me, but I have tried to follow the many threads about xlg and compiz, and am still missing a fundamental issue - does any of this work in Breezy yet?

I am not really interested in moving at this point to Badger, but would like to be able to install both xgl and compiz.

Thanks.[/QUOTE]
Yes it does.  Check out the xgl success thread.  I think if you're going to have problems with anything it'll be in upgrading to breezy in the first place.  Otherwise you might be lucky and it wil just be a case of changing your repositorys to breezy and doing an apt-get dist-upgrade

---

### Post by zentagonist on 2006-02-17
[QUOTE=chrisrx]the version in synaptic isn't the newest version

to do that try this
```
apt-get install build-essential libtool automake1.9 xserver-xorg-dev cvs
cvs -d :pserver:anoncvs@cvs.freedesktop.org:/cvs/cairo login
cvs -z3 -d :pserver:anoncvs@cvs.freedesktop.org:/cvs/cairo co glitz
cd glitz
./autogen.sh --prefix=/usr
make
sudo make install
sudo ldconfig
```

just a note to say I've completely forgotten the deps but I think it's automake that you need otherwise it complains about aclocal. libtool I put in the just to be safe.[/QUOTE]

well ... at first I thought this worked.
I ran 'thefuture' right after doing all your steps (which went through without a hitch btw), and I didn't get any errors.  However, I did loose my panels, and the panes at the top of any window that let me drag anything around, those went away too.
I rebooted, ran 'thefuture' again.  And now I'm back to getting the "no manegable display" error again. :confused: 

Thanks for all your help guys! seriously!

---

### Post by Tonio on 2006-02-17
Installed on a fresh dapper, everything working perfectly ... :) :) :) :) :) 

The only thnig which was'nt in the tutorial was to add the composite extension in xorg.conf


Thank you very much for that :):)

---

### Post by poofyhairguy on 2006-02-17
[QUOTE=zentagonist]well ... at first I thought this worked.
I ran 'thefuture' right after doing all your steps (which went through without a hitch btw), and I didn't get any errors.  However, I did loose my panels, and the panes at the top of any window that let me drag anything around, those went away too.
I rebooted, ran 'thefuture' again.  And now I'm back to getting the "no manegable display" error again. :confused: 

Thanks for all your help guys! seriously![/QUOTE]

That is bad. Keep running it and give me your ENTIRE error so I can tell whats going on.

---

### Post by poofyhairguy on 2006-02-17
[QUOTE=jamesshuang]hey poofy, I think you should probably make a note that if nothing happens, but compiz seems to have worked, you should go into the gconf and add the plugins there... I had issues with that on both my computers (probably a result of trying compiz before), and in any case nothing happened until I did that.

Just a note to think about ;)[/QUOTE]

Hmmm....I have been thinking of a better way to do all of this. I just wanted to get a guide out there, but improvements will come soon.

---

### Post by Wesley on 2006-02-17
hi

it worked perfectly last night, 

but this morning, boot up the laptop and "thefuture"

got this error

> wesley@ubuntu:~$ gnome-window-decorator, Failed to load shadow images
compiz.real: No composite extension


what's up with it?

---

### Post by poofyhairguy on 2006-02-17
> 

what's up with it?


My fault. I took Novell's advice. I changed the guide to fix that problem. Do exactly what I say to the xorg.conf

---

### Post by aamukahvi on 2006-02-17
[QUOTE=poofyhairguy]On my 6600 GT videos are as smooth as can be with my guide. Wobble and everything. Could not ask for more.

I think the trick is to buy a 6xxx series Nvidia card if you want to be sure everything with "Just Work" well once its all set up. That group has some problems, but by far less than any other group.

The day Compiz was released my 6600 GT payed for itself![/QUOTE]
Well, poofy, after much contemplation I ordered an AGP GF6200. Cost me 62&#8364;.(how's that for a coincidence, lol)

Anyway, one more question popped up. Do you (yourself) have to start compiz  multiple times like some seem to have to, or does it "just work"?

---

### Post by rel on 2006-02-17
@ Zentagonist!

Try removing "gconf" from the line in thefuture script. Helped here.
Best solution is to add the plugins in gconf database in the right order, (see gentoo wiki about compiz on this) and start compiz in the script with: 
gnome-window-decorator ; compiz --replace gconf

---

### Post by poofyhairguy on 2006-02-17
[QUOTE=aamukahvi]Do you (yourself) have to start compiz  multiple times like some seem to have to, or does it "just work"?[/QUOTE]

Recently for me it all just works.

---

### Post by aamukahvi on 2006-02-17
[QUOTE=poofyhairguy]Recently for me it all just works.[/QUOTE]
K thx. :KS

---

### Post by teppic on 2006-02-17
A couple of points I've found:

o Don't enable the Composite extension in xorg.conf for nvidia cards. Xgl already has it in and doesn't work properly if you enable the extension.

o I had problems with opengl apps crashing the server. According to compiz notes, it's best to start the Xgl on nvidia with:

```
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
```

The change from the howto here is from fbo to pbuffer for glx.

---

### Post by encho on 2006-02-17
[QUOTE=Gandalf]Had anyone tried another (non-ati/nvidia) card? i have an Intel integrated one on my HP :([/QUOTE]
I've just tryed it on my laptop (i855 integrated), and it works!!! Just do not do 2 things:
1. Do not enter <Option	"RenderAccel" "true">, as it is nvidia-related (at least I think so)
2. Do not out-comment dri in your xorg.conf or server won't start at all.

When you run 'thefuture' you may also need to press <alt><f4> to refresh your desktop, at least I had to.

Sometimes it seems to me as it works better on my laptop than on desktop with nvidia 6200 :???: Some opengl apps are just crashing the comp on each of them.

---

### Post by aamukahvi on 2006-02-17
[QUOTE=encho]Sometimes it seems to me as it works better on my laptop than on desktop with nvidia 6200 :???: Some opengl apps are just crashing the comp on each of them.[/QUOTE]
Hmm. Which apps? Just asking coz I ordered a GF6200 :D

---

### Post by curtis on 2006-02-17
Seems to be working nicely here on boot now... must be when I removed the entries from ~/.Xsession and changed it to session statup entries.
Compiz really is nice, F12 is a life saver when you have 20 windows open.

---

### Post by gnumdk on 2006-02-17
>Do not enter <Option "RenderAccel" "true">, as it is nvidia-related (at
>least I think so)

No it's not an nvidia option, it's an Xorg option and Xgl use Xorg...

Things will be smoother with this options enabled.

---

### Post by woedend on 2006-02-17
PHG, I think teppic's post was of great importance to the howto, for me it was at least.  I read up a little(for once. :) ) and it is recommended to comment out composite, and for glx use pbuffer.  With or without composite made no difference to me, but the pbuffer thing was a lifesaver.  With glx:fbo, the xserver would crash when screensavers initiated and when using opengl output video(just playing around with it).  With it it works well.  The opensuse site recommends it with pbuffer.  In all honesty, is there  a big difference between the two?  Im throwing terms without knowing much about what i am saying as noticed :p.  cant wait for transparency! thanks again.

---

### Post by gnumdk on 2006-02-17
```


gnumdk@lisa:~$ tail -n 8 /etc/gdm/gdm.conf-custom
[servers]
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl -ac -accel glx:pbuffer -accel xv:fbo
flexible=true


gnumdk@lisa:~$ cat /usr/share/xsessions/Xgl.desktop
[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Name[fr]=Xgl
Exec=/usr/bin/Xgl.sh
# no icon yet, only the top three are currently used
Icon=
Type=Application


gnumdk@lisa:~$ cat /usr/bin/Xgl.sh
#!/bin/bash
compiz --replace switcher decoration wobbly fade minimize cube rotate zoom scale move resize place menu &
gnome-window-decorator &
sleep 5 && keyboard &
gnome-session


gnumdk@lisa:~$ cat /usr/bin/keyboard
#!/bin/bash
#tree times !?! :(
setxkbmap -model pc105 -layout fr -variant basic
setxkbmap -model pc105 -layout fr -variant basic
setxkbmap -model pc105 -layout fr -variant basic

gnumdk@lisa:~$ cat /proc/driver/nvidia/cards/0
Model:           GeForce FX Go5200
IRQ:             11
Video BIOS:      04.34.20.42.c1
Card Type:       AGP

```
When i play videos, all is really fast!!!

I have this in glxinfo:
```

gnumdk@lisa:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
client glx vendor string: NVIDIA Corporation
client glx version string: 1.3
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
GLX version: 1.2
GLX extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_SGIX_fbconfig, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce FX Go5200/AGP/SSE2
OpenGL version string: 1.2 (2.0.1 NVIDIA 81.78)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow,
    GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color,
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,
    GL_EXT_texture3D, GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, GL_EXT_texture_lod,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array,
    GL_HP_occlusion_test, GL_IBM_texture_mirrored_repeat, GL_NV_blend_square,
    GL_NV_texgen_reflection, GL_NV_texture_rectangle,
    GL_NV_texture_env_combine4, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod,
    GL_SGIX_depth_texture, GL_SGIX_shadow
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```
I think that's why all is working perfectly, no mesa glx, only nvidia...

When i resize windows, it's fast too !

I've got a Gforce 4 at home, with black windows :( but glx info give me Mesa as opengl renderer :(

Don't really understand how it works as i have read everywhere that it can't work with nvidia glx ...

---

### Post by kamstrup on 2006-02-17
[QUOTE=jasay]Did you put wobbly back in the same place in the list of plugins?  I guess some of the plugins depend on others having alrewady loaded so make sure wobbly is listed right after decoration.[/QUOTE]

Thanks, jasay! That was it. Also for some reason "decoration" was also removed from my gconf entry... I don't remember doing that my self, but restoring the options as listed in "thefuture" made everything work perfectly again :-D

---

### Post by Ainvar on 2006-02-17
Ok, quick question that may or may not be stupid. How can I get Cedega working again so I can play Guild Wars. Since I have made the changes Cedega crashes when I try and load a game.

Here is the error I recieve. I have tried undoing the gdm.conf-custom along with restart the computer and not running "thefuture" on the cli after booting up.

> 
X Error of failed request:  BadImplementation (server does not implement operati on)
  Major opcode of failed request:  129 (MIT-SHM)
  Minor opcode of failed request:  5 (X_ShmCreatePixmap)
  Serial number of failed request:  3669
  Current serial number in output stream:  3675
X Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request:  55 (X_CreateGC)
  Resource id in failed request:  0x3a0035c
  Serial number of failed request:  3672
  Current serial number in output stream:  3675



Also one thing I have noticed this morning since I am using my intelimouse is that my forward and back buttons no longer work. Scrolling still works very well, just not forward and back.

Any ideas?

---

### Post by Frafra on 2006-02-17
I'm Dapper on a amd64, and it doesn't work for me. What I must do?

---

### Post by Uuranor on 2006-02-17
Is normal that after 5 minutes of compiz use all become really slow? O.o
I've got a Ge Force FX 5700...

---

### Post by gnumdk on 2006-02-17
Here is a package for dapper of current compiz cvs.

Zoom is much better!

[http://hibbert.univ-lille3.fr/~cbellegarde/compiz_0.0.2-cvs-0_i386.deb](http://hibbert.univ-lille3.fr/~cbellegarde/compiz_0.0.2-cvs-0_i386.deb)

---

### Post by mikalh on 2006-02-17
[QUOTE=Frafra]I'm Dapper on a amd64, and it doesn't work for me. What I must do?[/QUOTE]

If you're comfortable with building software from source, try my [HOWTO: Build Xgl and Compiz from CVS on AMD64]("http://www.ubuntuforums.org/showthread.php?t=131659").

**I have Xgl and compiz both working on AMD64** using this method.

---

### Post by jacrider on 2006-02-17
[QUOTE=chrisrx]Yes it does.  Check out the xgl success thread.  I think if you're going to have problems with anything it'll be in upgrading to breezy in the first place.  Otherwise you might be lucky and it wil just be a case of changing your repositorys to breezy and doing an apt-get dist-upgrade[/QUOTE]
Chrisrx:  Thanks for your reply.  However, I am on Breezy, and when I tried the apt-get for compiz, I received an error that it wasn't found.  Yet I have all the repositories enabled ... I think.  Is that my problem?

---

### Post by Swatje on 2006-02-17
Working on a GeForce 2 GO laptop video card.
with the CVS glitz

---

### Post by Swatje on 2006-02-17
[QUOTE=jacrider]Chrisrx:  Thanks for your reply.  However, I am on Breezy, and when I tried the apt-get for compiz, I received an error that it wasn't found.  Yet I have all the repositories enabled ... I think.  Is that my problem?[/QUOTE]

Compliz work only with the latest dapper, because you need the last X.org server. It's only included in dapper.

---

### Post by poofyhairguy on 2006-02-17
[QUOTE=teppic]A couple of points I've found:

o Don't enable the Composite extension in xorg.conf for nvidia cards. Xgl already has it in and doesn't work properly if you enable the extension.

o I had problems with opengl apps crashing the server. According to compiz notes, it's best to start the Xgl on nvidia with:

```
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
```

The change from the howto here is from fbo to pbuffer for glx.[/QUOTE]

Thanks! I changed the guide to use pbuffer. Everyone update you gdm-custom file.

 I originally tried not enabling the composite extension, but many people with Nvidia cards have contacted me saying that Compiz demands it so I had to add it back to my guide. I know Novell and everyone says that the extension is not needed and its bad, but when you have a problem like this:

[http://www.ubuntuforums.org/showpost.php?p=742992&postcount=140](http://www.ubuntuforums.org/showpost.php?p=742992&postcount=140)

come up more than once, you just give in and add the composite extension. I personally have tried with it both in and out of my Xorg.conf and personally it is more stable for me with the composite extension in. So......

---

### Post by Ainvar on 2006-02-17
poofy,
   How can I undo the changes so I can get cedega running again? I backed up the gdm.conf-custom so I could switch back and forth but I am still getting the error I pasted a few posts back.

---

### Post by poofyhairguy on 2006-02-17
[QUOTE=Ainvar]poofy,
   How can I undo the changes so I can get cedega running again? I backed up the gdm.conf-custom so I could switch back and forth but I am still getting the error I pasted a few posts back.[/QUOTE]

So did you delete the gdm.conf-custom? That plus a restart should put you back into regular X....

---

### Post by encho on 2006-02-17
[QUOTE=aamukahvi]Hmm. Which apps? Just asking coz I ordered a GF6200 :D[/QUOTE]
Basicaly all of the opengl. Like glxgears. And some screensavers. Although I have noticed (in split second before it crashes) that the FPS has gone up from 1500 to 16000 when switching to xgl. But we should not be panicking, as I believe it is a driver issue that will be fixed. It is still too early to make any decisions (although I've bought this card to be able to run xgl :cool:  )

[QUOTE=gnumdk]No it's not an nvidia option, it's an Xorg option and Xgl use Xorg...

Things will be smoother with this options enabled.[/QUOTE]
Thanks for clearing that up.

---

### Post by Greg T. on 2006-02-17
This is the script I'm using to start XGL and compiz these days. I have this in my home directory and fire it up at a prompt after hitting Ctrl + Alt + F1. Be sure to make it executable before you try it and precede the script name (whatever you call it) with a "./" (sorry for stating the obvious, but you never know who's reading). 

```
#!/bin/bash
sudo /etc/init.d/gdm stop
sudo killall Xgl &
sudo killall Xorg &
sleep 2
sudo Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo &
sleep 4
DISPLAY=:0 gnome-window-decorator &
DISPLAY=:0 compiz gconf &
sleep 4
DISPLAY=:0 dbus-launch gnome-session
```

YMMV. I'm using an NVIDIA 6600. This might not work with older cards and ATI.

The dbus-launch reference on the last line helps solve problems I was having with some crashers at startup, such as gnome-power-manager.

---

### Post by Technoviking on 2006-02-17
Is there a easy way to make panels (aka gnome-panel) and windows translucent   with xgl?

---

### Post by nicky.7 on 2006-02-17
I'm running xgl on a nvidia 5500. I've these problems:

1)
The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadImplementation (server does not implement operation)'.
Running firefox sometime i get this error:

(Details: serial 36 error_code 17 request_code 129 minor_code 5)
(Note to programmers: normally, X errors are reported asynchronously;
that is, you will receive the error a while after causing it.
To debug your program, run it with the --sync command line
option to change this behavior. You can then get a meaningful
backtrace from your debugger if you break on the gdk_x_error() function.)

2) video playback (speed problem). 

3) In nautilus i don't have home and computer icon anymore.

4) Speed (render) is not costant. Sometimes it become slow for a while then it restart to work slightly.

Does anybody know a solution? Thanks

---

### Post by varunus on 2006-02-17
[QUOTE=poofyhairguy]Thanks! I changed the guide to use pbuffer. Everyone update you gdm-custom file.

 I originally tried not enabling the composite extension, but many people with Nvidia cards have contacted me saying that Compiz demands it so I had to add it back to my guide. I know Novell and everyone says that the extension is not needed and its bad, but when you have a problem like this:

[http://www.ubuntuforums.org/showpost.php?p=742992&postcount=140](http://www.ubuntuforums.org/showpost.php?p=742992&postcount=140)

come up more than once, you just give in and add the composite extension. I personally have tried with it both in and out of my Xorg.conf and personally it is more stable for me with the composite extension in. So......[/QUOTE]

Thanks for the pbuffer thing.  That lets me use opengl while compiz is running.  Now, the only bug I'm really seeing is the shift-backspace thing...(though, my keyboard is easy, so i'm immune to that.)

---

### Post by Milamber_Cubed on 2006-02-17
This is my first post on here, I just had to get on here and offer my thanks for this howto it worked absolutely perfectly (once I sorted out my typos!).

Also a general thanks from me to everyone on here - I have never had to post before because I have always found the answers to my questions. 

Anyway, to summarise this is my hardware:

6600GT (AGP)
ASUS A8V Deluxe
AMD Athlon 64 3500+

Followed this guide straight after a clean install of Dapper Flight 3 - i386 version, because the 64-bit install for Xgl seems a bit more involved ;) and it "just worked". I am a very happy camper. Haven't tried video yet, but glxgears runs without causing crashes as reported by others on this thread.

Only thing is that when I ran the "thefuture" script after logging in, I got a mwssage about limbenu.so not being found. This doesn't seem to be having any disasterous effects so I am not too worried, but would still like to know what is causing it. Any ideas?

Would I gain anything from installing the latest CVS versions of any of these things?

---

### Post by DeeZiD on 2006-02-17
Just one question.

Is it possible to prevent Shift+Backslash from killing Xgl on Ubuntu?
On Gentoo nothing happens when hitting them together.
On Ubuntu it crashes the whole Xgl :( 


regards Dennis

---

### Post by c0nfused on 2006-02-17
Over on the Gentoo forums ([here]("http://forums.gentoo.org/viewtopic-t-432300-start-150.html")), there are claims that the black windows problem on certain Nvidia cards (Geforce4MX Series) has been fixed in the latest version of glitz.  Has anyone had the black windows problem on Dapper and managed to get it fixed?

---

### Post by Ainvar on 2006-02-17
PHG,
   I got it working again by rebooting after renaming the gdm.conf-custom file. After that I can rename the file and just restart the X server as I need to when playing guild wars in cedega. I just cant wait till I can just stay in xgl server for everything. It makes everything just so bling bling bling.

People at work are loving it, now how to get my boss on the linux bandwagon......

---

### Post by codejunkie on 2006-02-17
[QUOTE=c0nfused]Over on the Gentoo forums ([here]("http://forums.gentoo.org/viewtopic-t-432300-start-150.html")), there are claims that the black windows problem on certain Nvidia cards (Geforce4MX Series) has been fixed in the latest version of glitz.  Has anyone had the black windows problem on Dapper and managed to get it fixed?[/QUOTE]
yes it has been fixed with the new version of glitz and it seems to work very welll except xvideo is a little slow. here's the link to the post i made with the glitz package attached and how you compile it.
[http://ubuntuforums.org/showpost.php?p=742304&postcount=109](http://ubuntuforums.org/showpost.php?p=742304&postcount=109)
hope this helps.

---

### Post by Frafra on 2006-02-17
When I can use Xgl on my amd64 without recompile all?

---

### Post by poofyhairguy on 2006-02-17
[QUOTE=Frafra]When I can use Xgl on my amd64 without recompile all?[/QUOTE]

Only the developers know that one.

---

### Post by poofyhairguy on 2006-02-17
[QUOTE=Ainvar]PHG,
   I got it working again by rebooting after renaming the gdm.conf-custom file. After that I can rename the file and just restart the X server as I need to when playing guild wars in cedega. I just cant wait till I can just stay in xgl server for everything. It makes everything just so bling bling bling.

People at work are loving it, now how to get my boss on the linux bandwagon......[/QUOTE]


Glad to here you fixed it!

---

### Post by TheDude on 2006-02-17
I spent about an hour last night getting this working (with the help of PHG) on my 6 year old Gateway desktop.  Thankfully, about 6 months ago he talked me into getting an Nvidia 5200 and now I'm really reaping the benefits...It was well worth every penny.  Compiz is amazing!  Thanks PHG!\\:D/

---

### Post by codejunkie on 2006-02-17
poof i followed your howto and after compiling glitz everything is working great except video, no matter what player i use video playback is really slow and xgl eats 100% cpu you wouldn't know a quick fix to this problem would you.
im using a GeForce4 MX 4000 with the latest nvidia driver.

---

### Post by poofyhairguy on 2006-02-17
[QUOTE=codejunkie]poof i followed your howto and after compiling glitz everything is working great except video, no matter what player i use video playback is really slow and xgl eats 100% cpu you wouldn't know a quick fix to this problem would you.
im using a GeForce4 MX 4000 with the latest nvidia driver.[/QUOTE]

Hmm....I honestly know that pre-Directx9 Nvidia cards (aka anything Geforce and older) are having some problems, but I don't know why.

We might actually be hitting the limit of some of this hardware! A Geforce4 MX 4000 is more like a Geforce 2 than a Geforce 4 so I might have trouble accerating video.

---

### Post by vendetta red on 2006-02-17
I just have one small question. How do I get the top of the cube to display an svg? I have tried putting the path to several different svg's in apps/compiz/pluigns/cube/screen0/options/svgs but the top still displays gray. I tried deleting the color value, that didn't help. I can change the color value and make the top and bottom of the cube whatever I want, but I would really like to be able to put a svg up top.

---

### Post by poofyhairguy on 2006-02-17
[QUOTE=vendetta red]I just have one small question. How do I get the top of the cube to display an svg? I have tried putting the path to several different svg's in apps/compiz/pluigns/cube/screen0/options/svgs but the top still displays gray. I tried deleting the color value, that didn't help. I can change the color value and make the top and bottom of the cube whatever I want, but I would really like to be able to put a svg up top.[/QUOTE]

This has bugged me too. I don't think you can do it with the repo compiz. If someone can found out how then tell me, but for now I am trying to get it to work with a third party deb.

---

### Post by poofyhairguy on 2006-02-17
[QUOTE=TheDude]I spent about an hour last night getting this working (with the help of PHG) on my 6 year old Gateway desktop.  Thankfully, about 6 months ago he talked me into getting an Nvidia 5200 and now I'm really reaping the benefits...It was well worth every penny.  Compiz is amazing!  Thanks PHG!\\:D/[/QUOTE]

No problem. My official recommendation for those who can't get compiz to work with ATI cards and older Nvidia cards is to go buy a 5200 or 5500 FX (with 128+ ram if you can afford it). These cards come in PCI and AGP flavors and are really cheap- I bought a 5200 FX for $30 on Ebay in the middle of last year.

For me its not worth the pain getting it to work on an old Nvidia card unless its in your laptop. Then I feel you- find a way to get it to work for you and I will add it to the guide.

Here is a good cheap 5200 FX from a famous retailer with 128mb of RAM and a 128 bit bus:

[http://www.newegg.com/Product/Product.asp?Item=N82E16814150041](http://www.newegg.com/Product/Product.asp?Item=N82E16814150041)

---

### Post by codejunkie on 2006-02-17
[QUOTE=poofyhairguy]Hmm....I honestly know that pre-Directx9 Nvidia cards (aka anything Geforce and older) are having some problems, but I don't know why.

We might actually be hitting the limit of some of this hardware! A Geforce4 MX 4000 is more like a Geforce 2 than a Geforce 4 so I might have trouble accerating video.[/QUOTE]
i think i might have found it, on the opensuse xgl wiki it says that 
> XVideo will be very slow if hardware acceleration **(pixel shaders)** is not available. If using a composite manager, it will only be fast if FBOs or pBuffers are available and activated.my card dosen't have pixel shader support, i've heard that anything below a geforce 5200 dosen't have this, so it looks like anyone with cards lower than a geforce 5200 will be suffering with this video problem they listed somethings to try to improve it i'll post back if it works or not.

---

### Post by poofyhairguy on 2006-02-17
There I fixed me guide. The backspace shift bug is gone and I made it clear that not everyone should add the composite extension!

MOST BUGS ARE GONE!

---

### Post by poofyhairguy on 2006-02-17
[QUOTE=Mike Basinger]Is there a easy way to make panels (aka gnome-panel) and windows translucent   with xgl?[/QUOTE]

Transset and opacity pluggin.

---

### Post by fimbulvetr on 2006-02-17
Hello,

I too am experiencing the:

```

compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

```

problem. I've done everything in the howto. Here's my custom file:

```

ubuntu:~$ egrep -v "^#" /etc/gdm/gdm.conf-custom

[daemon]

[security]

[xdmcp]

[gui]

[greeter]

[chooser]

[debug]

[servers]# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX).
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true

```

My 'thefuture':

```

ubuntu:~$ cat `which thefuture`
#!/bin/bash
gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher &

```

My hardware:

```

0000:01:00.0 VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 4200 Go AGP 8x] (rev a1) (prog-if 00 [VGA])
        Subsystem: Dell: Unknown device 0179
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop+ ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 248 (1250ns min, 250ns max)
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at f0000000 (32-bit, prefetchable) [size=64M]
        Expansion ROM at fd000000 [disabled] [size=128K]
        Capabilities: <available only to root>

```

Which, btw, nvidia claims it to have vertex and pixel shader support:
[http://www.nvidia.com/page/geforce4go.html](http://www.nvidia.com/page/geforce4go.html)

I have these in my xorg:

```

Section "Extensions"
        Option  "Composite" "Enable"
EndSection

```

```

Section "Device"
        Identifier      "GeForce 4200 Go Single"
        #Driver          "nv"
        Driver          "nvidia"
        Option          "NoLogo"                        "1"
        Option          "RenderAccel"                   "true"
        Option          "AllowGLXWithComposite" "true"
        Option          "UseEdidFreqs"                  "on"
        Option          "NvAgp"                         "2"
        Option          "DigitalVibrance"               "0"
        Option          "TwinView"                      "0"
        Option          "Monitor"                       "1"
EndSection

```

```

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        #Load   "v4l"
        #Load   "vbe"
EndSection

```

I've also compiled and install the newest glitz from cvs per poofyhairedguy's instructions.

Suggestions, anyone?

---

### Post by aent on 2006-02-17
[QUOTE=Swatje]Working on a GeForce 2 GO laptop video card.
with the CVS glitz[/QUOTE]
How fast is it? Also, anyone know when the next glitz packages will get into the repo? Can't wait to see this work decently on my laptop.

---

### Post by skwid on 2006-02-17
dumb question but what repo do i put in my sources.list to get compiz and things?

---

### Post by Technoviking on 2006-02-17
[QUOTE=poofyhairguy]Transset and opacity pluggin.[/QUOTE]
you don't mean the old transset program from xcompmgr?

---

### Post by Technoviking on 2006-02-17
[QUOTE=poofyhairguy]
F11 - uses the Expose like trick
[/quote]
The only thing it does for me is full screen the focused app. I assune it supposed to do something else.

Mike

---

### Post by Rotarychainsaw on 2006-02-17
f12 is the expose like trick. Maybe I jumped into the middle of a conversation. but hey. ;)

---

### Post by el3ktro on 2006-02-17
Wow thanks for this guide, it works almost perfectly on my Dapper test install. There's one small annoying prolem though:

The wobbling windows are very smooth as long as I have the mouse button pressed, but as soon as the mouse button is release and the window slowly stops wobbling, it get's very laggy. Also the fadein/fadeout is sometimes laggy. Has anyone experienced the same problems? This only happens sometimes, but the CPU never goes over 10%.

Tom

---

### Post by iMil on 2006-02-17
Ok here is a tip solving the "compiz: GLX_EXT_texture_from_pixmap is missing" once and for all (here at last ;)

The fact is nvidia-glx removes libgl1-mesa's /usr/lib/libGL.so.1.2, and makes libGL.so.1 point to NVidia's libGL.so.1.0.8178, which does NOT support GLX_EXT_texture_from_pixmap function.

Simple trick, nvidia-glx moves /usr/lib/libGL.so.1.2 to /usr/lib/nvidia/libGL.so.1.2.xlibmesa, so just 

ln -sf /usr/lib/nvidia/libGL.so.1.2.xlibmesa usr/lib/nvidia/libGL.so.1

Use the original doc from this thread, and you're done.
Please note i've not tested yet if this has side effects over other OpenGL apps like games and such.

---

### Post by .k2600. on 2006-02-17
[QUOTE=iMil]
The fact is nvidia-glx removes libgl1-mesa's /usr/lib/libGL.so.1.2, and makes libGL.so.1 point to NVidia's libGL.so.1.0.8178, which does NOT support GLX_EXT_texture_from_pixmap function.

Simple trick, nvidia-glx moves /usr/lib/libGL.so.1.2 to /usr/lib/nvidia/libGL.so.1.2.xlibmesa, so just 

ln -sf /usr/lib/nvidia/libGL.so.1.2.xlibmesa usr/lib/nvidia/libGL.so.1
[/QUOTE]

What about ati? I tried replacing libGL.so.1.2 which fglrx put in /usr/lib with one from libgl1-mesa package, i get some error and xgl won't start anymore ...

---

### Post by vendetta red on 2006-02-17
[QUOTE=.k2600.]What about ati? I tried replacing libGL.so.1.2 which fglrx put in /usr/lib with one from libgl1-mesa package, i get some error and xgl won't start anymore ...[/QUOTE]

ATI guide right here:

[http://ubuntuforums.org/showthread.php?t=131253](http://ubuntuforums.org/showthread.php?t=131253)

---

### Post by Jedeye on 2006-02-17
I don't make it very far :???:  I got to the step that says 
```
sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1
```and I get...
```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package compiz
jon@dapper:~$
```

do I need to enable some more repositories? any help would be much appreciated.

---

### Post by el3ktro on 2006-02-17
Yes, I think it's in the universe repo afaik, just enable all you can find in sources.list

Tom

---

### Post by Jedeye on 2006-02-17
ahh yes... activating the universe repo was all it needed... rest of the guide workedl ike a charm. cant wait to show my osx buddies ;)

---

### Post by .k2600. on 2006-02-17
[QUOTE=vendetta red]ATI guide right here:

[http://ubuntuforums.org/showthread.php?t=131253](http://ubuntuforums.org/showthread.php?t=131253)[/QUOTE]


jep .. tried that and got 
compiz: GLX_EXT_texture_from_pixmap is missing
that's why I asked is there any flgrx fix for it ...

---

### Post by Jedeye on 2006-02-17
CTRL + Left Click makes the select window snap to screen edges and other windows

---

### Post by Heretushi on 2006-02-18
Sorry if this sounds completely newbish, but I saw the video and want to try this out on my desktop. I read the FULL 21 pages of the thread. Yeah, each and every post. But I still want to ask : is the guide on the first page "the complete package"? I mean... is it updated to include all the little fixes the 21 pages have brought upon?

Thanks. I'll try that a bit later. :) Then, I'll try to make it work on my laptop... Not sure how this will come out and don't know if this guide will help me as it's a 915 based graphic card. I hope, I hope.

---

### Post by vendetta red on 2006-02-18
[QUOTE=Heretushi]Sorry if this sounds completely newbish, but I saw the video and want to try this out on my desktop. I read the FULL 21 pages of the thread. Yeah, each and every post. But I still want to ask : is the guide on the first page "the complete package"? I mean... is it updated to include all the little fixes the 21 pages have brought upon?

Thanks. I'll try that a bit later. :) Then, I'll try to make it work on my laptop... Not sure how this will come out and don't know if this guide will help me as it's a 915 based graphic card. I hope, I hope.[/QUOTE]

Yes the guide on the front page is up-to-date and if you follow it you should be good to go. Oh and if you think this thread was long to read through, this one was created to clarify the massive 80 page thread that had the first tutorial (involving compiling) for Xgl and Compiz. ;)

---

### Post by Rotarychainsaw on 2006-02-18
ahh yes, those were the good old days.

---

### Post by Bruno Silva on 2006-02-18
Hi, I'm having a problem running this command in Dapper Drake:

sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 

it says that it can't find the components or something :s
anyway I tried to install some debs linked in this topic but as soon as I restarted gdm crashed complaining about something with xserver, I guess I'll have to reinstall Dapper Drake again (I'm new to this Linux world :))

Thanks in advance

Bruno Silva

---

### Post by Heretushi on 2006-02-18
Did you add extra repository for your apt-get?

---

### Post by Bruno Silva on 2006-02-18
No, what is that extra repository?

Thanks :)

---

### Post by Milamber_Cubed on 2006-02-18
[QUOTE=Heretushi]Sorry if this sounds completely newbish, but I saw the video and want to try this out on my desktop. I read the FULL 21 pages of the thread. Yeah, each and every post. But I still want to ask : is the guide on the first page "the complete package"? I mean... is it updated to include all the little fixes the 21 pages have brought upon?

Thanks. I'll try that a bit later. :) Then, I'll try to make it work on my laptop... Not sure how this will come out and don't know if this guide will help me as it's a 915 based graphic card. I hope, I hope.[/QUOTE]

I just posted my experiences of installing Xgl/compiz on a Intel 915GM based laptop in this thread: [http://ubuntuforums.org/showthread.php?t=132074](http://ubuntuforums.org/showthread.php?t=132074)

In short, the guide in this thread is **very** helpful, but you may need to make some tweaks. ;)

---

### Post by aent on 2006-02-18
It requires that you use universe in dapper.

---

### Post by quannum on 2006-02-18
I'm seeing the same issues:

robsh@daedalus:/usr/lib/nvidia$ compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :1.0

With a 6600GT (agp) and the latest update from the dapper repository. Any ideas?

**EDIT:** Turns out I was logging into display 1 (CTRL-F8) instead of the xgl server on display 0 (CTRL-F7) - how do i stop the second display starting?

---

### Post by Bruno Silva on 2006-02-18
Sorry to be asking again, but how can I add the needed repository for the apt-get? :confused: 

Thanks :)

---

### Post by aamukahvi on 2006-02-18
[QUOTE=Bruno Silva]Sorry to be asking again, but how can I add the needed repository for the apt-get? :confused:[/QUOTE]
You will find lots of these things in the ubuntu breezy forums (beginner forum etc). But here goes.

Execute this on the command line:
sudo gedit /etc/apt/sources.list

edit the file so it contains these lines:
```
## Universe
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe
```
Alternatively you can add "universe" to these lines, to the end.
```
## Main & Restricted
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted
```

---

### Post by poofyhairguy on 2006-02-18
[QUOTE=Heretushi]Sorry if this sounds completely newbish, but I saw the video and want to try this out on my desktop. I read the FULL 21 pages of the thread. Yeah, each and every post. But I still want to ask : is the guide on the first page "the complete package"? I mean... is it updated to include all the little fixes the 21 pages have brought upon?
[/QUOTE]

 Its the best I can do for Nvidia cards.

---

### Post by Bruno Silva on 2006-02-18
[QUOTE=aamukahvi]You will find lots of these things in the ubuntu breezy forums (beginner forum etc). But here goes.

Execute this on the command line:
sudo gedit /etc/apt/sources.list

edit the file so it contains these lines:
```
## Universe
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe
```
Alternatively you can add "universe" to these lines, to the end.
```
## Main & Restricted
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted
```[/QUOTE]

Thanks a lot, it worked :) I'm installing everything now :)

---

### Post by campusloop on 2006-02-18
If anybody is interested in using Xgl with kde the taskbar and system tray problems can be solved by.

taskbar - go to kcontrol->desktop->taskbar->check "show windows from all desktops". taskbar entries in kicker then should be created properly.

system tray - there is an attached patch for kdelibs/kdeui/ksystemtray.cpp.
1. unpack kdelibs-3.5.1.tar.bz2 ( from download.kde.org )
2. rename ksystemtray-xgl.txt to ksystemtray-xgl.diff
2. apply patch from within kdelibs-3.5.1 directory - patch -p1 < ksystemtray-xgl.diff 
3. configure
4. cd kdeui; make; sudo make install ( there is no need to compile whole of kdelibs )
5. restart kde.


EDIT 1 -- make sure x11proto-core-dev and libx11-dev are installed ( sudo apt-get install x11proto-core-dev libx11-dev )

EDIT 2 - update patch and instructions are at [http://www.ubuntuforums.org/showpost.php?p=758925&postcount=21](http://www.ubuntuforums.org/showpost.php?p=758925&postcount=21)

---

### Post by Koybe on 2006-02-18
Hello, everything seems to work well but those keys won't work. 
> CTRL + ALT + Left/right arrow key. Switches to the new side of the cube for me.

CTRL + ALT + SHIFT + Left/Right arrow key- Takes the in focused app around cube.

Alt- Tab - switcher Vista-style

When i try moving the cube or windows with the mouse + CTRL + ALT, everything is working. When i use only keyboard nothing is working? Any idea?

Also... I don't know how to set windows transparency as i saw in some videos?

And Many thanks for the howto... and the universe debs ;-)

---

### Post by Blind-Summit on 2006-02-18
Hey guys. This seems a good thread to ask about dual screen setups. I have posted this else where with no reply so I wanted to ask how I can setup dual monitors on my GeForce 4 Ti4600. I have an AOC Spectrum 17" @ 1280x1024 and an Iiyama VisionMaster 500 21" at 1600x1200

All the other threads I have read have caused me errors. I have used their code and substituded my settings in, but it fails. 

Any ideas please?

---

### Post by MamiyaOtaru on 2006-02-18
[QUOTE=campusloop]
system tray - there is an attached patch for kdelibs/kdeui/ksystemtray.cpp.
1. unpack kdelibs-3.5.1.tar.bz2 ( from download.kde.org )
2. rename ksystemtray-xgl.txt to ksystemtray-xgl.diff
2. apply patch from within kdelibs-3.5.1 directory - patch -p1 < ksystemtray-xgl.diff 
3. configure
4. cd kdeui; make; sudo make install ( there is no need to compile whole of kdelibs )
5. restart kde.[/QUOTE]
You could drop step 2a and have step 2b be 2. apply patch from within kdelibs-3.5.1 directory - patch -p1 < ksystemtray-xgl.**txt**  ;)

Doesn't compile here though.
```

/usr/src/kdelibs-3.5.1/./kdeui/ksystemtray.cpp: In constructor 'KSystemTray::KSystemTray(QWidget*, const char*)':
/usr/src/kdelibs-3.5.1/./kdeui/ksystemtray.cpp:77: error: 'None' was not declared in this scope
/usr/src/kdelibs-3.5.1/./kdeui/ksystemtray.cpp:86: error: 'None' was not declared in this scope
/usr/src/kdelibs-3.5.1/./

```

Link to the origin of this patch please?

---

### Post by lucas on 2006-02-18
This worked fine on my old computer with a geforce2 mx. i had to install new glitz with [deb1](http://cas.pluxbox.org/xgl/libglitz1_cvs_i386.deb) and [deb2](http://cas.pluxbox.org/xgl/libglitz-glx1_cvs_i386.deb), beware though. this will install overwrite the universe ones, so be sure to uninstall glitz and glitz-glx first.

I havent got video to work yet though, opengl games are painfully slow and alt-gr does only semi-work. However, this still rocks! :)

---

### Post by Gurke on 2006-02-18
Did all this. I'm using a MX400 and I installed the glitz debs from one post above, because with the universe ones I only get the nice black screen and hourglass. 
When I run compiz, there are no errors. But the only thing that changes is that my windows don't have decorations anymore. No effects at all...

---

### Post by Koybe on 2006-02-18
[QUOTE=Koybe]Hello, everything seems to work well but those keys won't work. 


When i try moving the cube or windows with the mouse + CTRL + ALT, everything is working. When i use only keyboard nothing is working? Any idea?

Also... I don't know how to set windows transparency as i saw in some videos?

And Many thanks for the howto... and the universe debs ;-)[/QUOTE]

Got this corrected with 
```
setxkbmap -model pc105 -layout be
```

I still don't know how to get window transparency anyway...

---

### Post by SuperDiscoMachine V.5.7-3 on 2006-02-18
Just wanted to say thanks for the great howto.
After compiling glitz from cvs everything now works like a charm and I'm having a constant eyegasm. :-D

---

### Post by DiGiTaLFX on 2006-02-18
Thanks it works really well. GeForce2Ti here. Had to compile glitz from cvs (note I had to get libgl-mesa-dev as well as the xserver dev package).
Thanks very much for the guide!

---

### Post by DeeZiD on 2006-02-18
Thanks for your HowTo, works great ;) 
I've deleted my gentoo a few minutes ago (don't need it anymore)


regards Dennis

---

### Post by jannone on 2006-02-18
If you're having a **GLX_EXT_texture_from_pixmap** error, and you have the **nvidia-glx** package installed, try this:

```
LD_LIBRARY_PATH=/usr/lib/nvidia compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher
```

If the error is gone, but compiz seems to be frozen, try **not** loading the "gconf" plugin (just remove it from the command above and try again).

Do not forget to start gnome-window-decorator, or else you won't notice compiz running. Also, after both start running, the window title bar from your maximized windows might be cut out of the screen (and you'll think it's not working when in fact it is). Just press Alt while dragging the window and you'll get to the title bar again.

---

### Post by Heretushi on 2006-02-18
[QUOTE=poofyhairguy]Its the best I can do for Nvidia cards.[/QUOTE]
And I'm sure it will work just fine! Thanks for this guide. I'm gonna try it a bit later. :KS

---

### Post by byen on 2006-02-18
Hey poofy,
I think you just got dugg! great work man... keep up the great work!

---

### Post by Henrik on 2006-02-18
Has anyone been able to capture some video of this running on an Ubuntu system? 

If we could get some decent footage in ogg format I can add it to [https://wiki.ubuntu.com/DapperExampleContent](https://wiki.ubuntu.com/DapperExampleContent) (which will be included on the final CD) as a special preview. Novel has some nice videos, but we obviously cannot use those ...

---

### Post by campusloop on 2006-02-18
> **MamiyaOtaru]You could drop step 2a and have step 2b be 2. apply patch from within kdelibs-3.5.1 directory - patch -p1 < ksystemtray-xgl.**txt**   said:**
> 
Here is an updated version of the patch.. Can you please try with this.

[QUOTE=MamiyaOtaru]
Link to the origin of this patch please?


I created the patch myself.  
Anyway.. This patch modifies KSystemTray to use freedesktop.org hints to embed themselves in the tray.

EDIT 1 -- make sure x11proto-core-dev and libx11-dev are installed ( sudo apt-get install x11proto-core-dev libx11-dev )

EDIT 2 - Another patch update and instructions are at [http://www.ubuntuforums.org/showpost.php?p=758925&postcount=21](http://www.ubuntuforums.org/showpost.php?p=758925&postcount=21)

---

### Post by plb on 2006-02-18
I get this when building xgl on amd64

xglcompose.c; \
then mv -f ".deps/xglcompose.Tpo" ".deps/xglcompose.Po"; else rm -f ".deps/xglcompose.Tpo"; exit 1; fi
xglcompose.c: In function ‘xglCompositeGeneral’:
xglcompose.c:134: error: ‘union _SourcePict’ has no member named ‘source’
xglcompose.c:172: error: ‘union _SourcePict’ has no member named ‘source’
make[3]: *** [xglcompose.o] Error 1
make[3]: Leaving directory `/home/plb/build/xserver/xorg/hw/xgl'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/plb/build/xserver/xorg/hw/xgl'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/plb/build/xserver/xorg/hw'
make: *** [all-recursive] Error 1

---

### Post by deepbluepixel on 2006-02-18
when I do "setxkbmap -model pc105 -layout se" I get "Error loading new keyboard description"

---

### Post by Bigredman74 on 2006-02-18
poofyhairguy,

Thanks for taking the time to start and support this thread.

Your guide works great, but I did have a couple issues with a fresh install of Dapper Drake Flight 3.

First I had to enable the universe repositories to get compiz.

Ref: [http://www.ubuntuforums.org/showpost.php?p=746207&postcount=212](http://www.ubuntuforums.org/showpost.php?p=746207&postcount=212)

Then I had to change the default color depth to 24 to prevent a redraw problem with my nVidia NV28 [GeForce4 Ti 4200 Go AGP 8x] on my Dell Latitude D800. After setting it to 24 and restarting, the error libmenu.so missing also went away.

Ref: [http://www.ubuntuforums.org/showthread.php?p=746483#post746483](http://www.ubuntuforums.org/showthread.php?p=746483#post746483)

Thanks again to you and thanks to everyone who made this possible. My computer has never looked better!

All the best,
Tim

---

### Post by Blind-Summit on 2006-02-18
[QUOTE=Blind-Summit]Hey guys. This seems a good thread to ask about dual screen setups. I have posted this else where with no reply so I wanted to ask how I can setup dual monitors on my GeForce 4 Ti4600. I have an AOC Spectrum 17" @ 1280x1024 and an Iiyama VisionMaster 500 21" at 1600x1200

All the other threads I have read have caused me errors. I have used their code and substituded my settings in, but it fails. 

Any ideas please?[/QUOTE]

Anyone?

---

### Post by [S2] on 2006-02-18
Hello! 
I installed it and it works, but it is very slow. I have a i810 and glxinfo says that Direct Rendering is not on when I run the Xgl server (it is on when i run Xorg). Does Xgl support DRI for the i810 chipset?

---

### Post by poofyhairguy on 2006-02-18
[QUOTE=Blind-Summit]Hey guys. This seems a good thread to ask about dual screen setups. I have posted this else where with no reply so I wanted to ask how I can setup dual monitors on my GeForce 4 Ti4600. I have an AOC Spectrum 17" @ 1280x1024 and an Iiyama VisionMaster 500 21" at 1600x1200

All the other threads I have read have caused me errors. I have used their code and substituded my settings in, but it fails. 

Any ideas please?[/QUOTE]

You can't share a destkop between the two unless they share a resolution.

If that is the case, search the forum for Twinview!

---

### Post by Milamber_Cubed on 2006-02-18
[QUOTE=Bigredman74]

Then I had to change the default color depth to 24 to prevent a redraw problem with my nVidia NV28 [GeForce4 Ti 4200 Go AGP 8x] on my Dell Latitude D800. After setting it to 24 and restarting, the error libmenu.so missing also went away.

Ref: [http://www.ubuntuforums.org/showthread.php?p=746483#post746483](http://www.ubuntuforums.org/showthread.php?p=746483#post746483)

[/QUOTE]

I think that what happens here is that after the first timne you try to run compiz it will stop paying attention to what modules you tell it to load in the "the future" script. If you run gconf-editor apps>compiz>general>allscreens>options and look at the "actiuve_plugins" setting you will see that menu is in fact not on there. The menu library isn't actually installed (have a look in /usr/lib/compiz to confirm) if you use the debs, but this doesn't seem to break anything, so I gues it's no problem really.

Has anyone got the menu plugin working after compiling compiz from source? If so, did you have to compile any of the other packages or just stick with the debs?

---

### Post by poofyhairguy on 2006-02-18
[QUOTE='[S2]']Hello! 
I installed it and it works, but it is very slow. I have a i810 and glxinfo says that Direct Rendering is not on when I run the Xgl server (it is on when i run Xorg). Does Xgl support DRI for the i810 chipset?[/QUOTE]

Not yet.

---

### Post by [S2] on 2006-02-18
[QUOTE=poofyhairguy]Not yet.[/QUOTE]

Thanks

---

### Post by plb on 2006-02-18
Anyone want to create a working amd64 deb pkg for xgl?

---

### Post by Koybe on 2006-02-18
[QUOTE=deepbluepixel]when I do "setxkbmap -model pc105 -layout se" I get "Error loading new keyboard description"[/QUOTE]

Try it two times. First time I got an error, second time it worked well.

GL.

---

### Post by prateek51 on 2006-02-18
Hey, im trying to get compiz etc. from apt-get. But whenever i try i get this error:

```

$ sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1

Reading package lists... Done
Building dependency tree... Done
libgl1-mesa is already the newest version.
xserver-xorg is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz: Depends: libbonobo2-0 (>= 2.13.0) but 2.10.1-0ubuntu1 is to be installed
          Depends: libcairo2 (>= 1.0.2-2) but 1.0.2-0ubuntu1 is to be installed
          Depends: libgcc1 (>= 1:4.0.2) but 1:4.0.1-4ubuntu9 is to be installed
          Depends: libglib2.0-0 (>= 2.9.3) but 2.8.3-0ubuntu1 is to be installed          Depends: libgnomeui-0 (>= 2.13.0) but 2.12.0-0ubuntu1 is to be installed
          Depends: libgnomevfs2-0 (>= 2.13.4) but 2.12.1-0ubuntu2 is to be installed
          Depends: libpango1.0-0 (>= 1.11.5) but 1.10.1-0ubuntu1 is to be installed
          Depends: libqt4-core (>= 4.1.0) but it is not going to be installed
          Depends: libqt4-gui (>= 4.1.0) but it is not going to be installed
          Depends: libstdc++6 (>= 4.0.2-4) but 4.0.1-4ubuntu9 is to be installed          Depends: libwnck18 (>= 2.13.91) but 2.12.1-0ubuntu2 is to be installed          Depends: libxml2 (>= 2.6.23) but 2.6.21-0ubuntu1 is to be installed
  libglitz-glx1: Depends: libglitz1 (>= 0.5.1+cvs20060213) but 0.4.4-0ubuntu3 is to be installed
  xserver-xgl: Depends: libglitz1 (>= 0.5.1+cvs20060213) but 0.4.4-0ubuntu3 is to be installed
E: Broken packages

```

---

### Post by aent on 2006-02-18
[QUOTE=poofyhairguy]You can't share a destkop between the two unless they share a resolution.

If that is the case, search the forum for Twinview![/QUOTE]
Yes you can, I used to have that setup before I got a new second monitor (unless its something Xgl specific)

Use the metamodes option in xorg.conf specifying each monitor by its name (if they are both CRTs, use CRT-0: and CRT-1: and just flip them around if its not working, try both with a lower resolution that they both support while you work each one up)

---

### Post by kalphegor on 2006-02-18
/usr/bin/thefuture: line 2: gnome-window-decorator: command not found
/usr/bin/thefuture: line 2: compiz: command not found

i install everything mentioned here, but i can't get it working :-k

---

### Post by aent on 2006-02-18
[QUOTE=kalphegor]/usr/bin/thefuture: line 2: gnome-window-decorator: command not found
/usr/bin/thefuture: line 2: compiz: command not found

i install everything mentioned here, but i can't get it working :-k[/QUOTE]
It looks like you are missing the compiz package. Install compiz from the package manager or apt-get install compiz

---

### Post by kalphegor on 2006-02-18
[QUOTE=aent]It looks like you are missing the compiz package. Install compiz from the package manager or apt-get install compiz[/QUOTE]
i re-install compiz package

sudo apt-get remove compiz
sudo apt-get install compiz

thanks, now it works well :)

---

### Post by liquidcable on 2006-02-18
I can't get compiz to download.

Error message is :
E: Couldn't find package compiz

--
heath

---

### Post by kalphegor on 2006-02-18
[QUOTE=liquidcable]I can't get compiz to download.

Error message is :
E: Couldn't find package compiz

--
heath[/QUOTE]
add extra repositories
```
sudo gedit /etc/apt/sources.list
```
replace everything with
```
# 
# deb cdrom:[Ubuntu 6.04 _Dapper Drake_ - Alpha i386 (20060115)]/ dapper main restricted

deb cdrom:[Ubuntu 6.04 _Dapper Drake_ - Alpha i386 (20060115)]/ dapper main restricted

deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```
update the repositories list
```
sudo apt-get update
```

---

### Post by poofyhairguy on 2006-02-18
[QUOTE=aent]Yes you can, I used to have that setup before I got a new second monitor (unless its something Xgl specific)

Use the metamodes option in xorg.conf specifying each monitor by its name (if they are both CRTs, use CRT-0: and CRT-1: and just flip them around if its not working, try both with a lower resolution that they both support while you work each one up)[/QUOTE]


Thanks for the tip!

---

### Post by wermerskoch on 2006-02-18
Prateek51 said:  "Hey, im trying to get compiz etc. from apt-get. But whenever i try i get this error:"

I'm getting the exact same message.  I just tried editing my sources.list to include all the dapper repositories that someone else just mentioned (a couple posts up, I think), and now I'm just getting :

  The following packages have unmet dependencies:
  compiz: Depends: libgnomeui-0 (>= 2.13.0) but 2.12.0-0ubuntu1 is to be installed
          Depends: libgnomevfs2-0 (>= 2.13.4) but 2.12.1-0ubuntu2 is to be installed

Any ideas anyone?  Thanks!

  Warner

---

### Post by andydude117 on 2006-02-18
Yeah, I'm gettin the same thing wermerskoch said.  I'm running the LiveCD on a G5.  I would insall it, but I can't because of the yaboot bug.  I don't want to repartition my internal HD, so I'm stuck with OS X.

Is the problem because I'm using a LiveCD and on a G5?

Thanks,
Andy

---

### Post by MamiyaOtaru on 2006-02-18
[QUOTE=campusloop]I created the patch myself.  [/quote]
Good work then.  If I sounded dubious it's only cause I couldn't have done it ;)

Still not compiling, same error.  
```
/usr/src/kdelibs-3.5.1/./kdeui/ksystemtray.cpp: In constructor 'KSystemTray::KSystemTray(QWidget*, const char*)':
/usr/src/kdelibs-3.5.1/./kdeui/ksystemtray.cpp:76: error: 'None' was not declared in this scope

```

Where is None defined anyway?  I can't quite track it down..

---

### Post by deepbluepixel on 2006-02-18
anybody know how to get a transparent terminal like the videos show? only the background transparent, not the text...

---

### Post by raha on 2006-02-18
Hi, I installed the ubuntu again.
When I want to get the compiz this error comes up. I think there is something wrong with server :(

raha@ubuntu:~$ sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package compiz

---

### Post by DeeZiD on 2006-02-18
A few posts ago...
[http://www.ubuntuforums.org/showpost.php?p=747859&postcount=247](http://www.ubuntuforums.org/showpost.php?p=747859&postcount=247)


regards Dennis

---

### Post by dontpanic on 2006-02-18
I've installed all that required in this howto and when i''m going to start thefuture i dont have a windomanager...

[[IMG]http://img69.imageshack.us/img69/3599/immagine0og.th.jpg[/IMG]](http://img69.imageshack.us/my.php?image=immagine0og.jpg)

compiz is started, i must lauch "metacity --replace"

anyone with this problem??


edit: if I lauch:
$ compiz.real --replace
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

---

### Post by KrazyPenguin on 2006-02-18
I followed the guide and restarted my computer.
Logged in and opened a terminal:

typed: xmodmap /usr/shar/xmodmap/xmodmap.us
thefuture

and the screen went black with a cursor in the center.

It looks like compiz is working since I did get the keyboard commands to work, and I seen a cube, but there was no desktop.  I can rotate the cube etc, but I see no desktop.  
Just wondering why I can't see my desktop??
Must be somekind of configuration i messed up.
Anybody know of hand??
Thanks.

---

### Post by KrazyPenguin on 2006-02-18
My card is a Geforce mx4000. 
So I suppose I have to compile cvs version of glitz??

---

### Post by plb on 2006-02-18
[QUOTE=dontpanic]I've installed all that required in this howto and when i''m going to start thefuture i dont have a windomanager...

[[IMG]http://img69.imageshack.us/img69/3599/immagine0og.th.jpg[/IMG]](http://img69.imageshack.us/my.php?image=immagine0og.jpg)

compiz is started, i must lauch "metacity --replace"

anyone with this problem??


edit: if I lauch:
$ compiz.real --replace
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0[/QUOTE]

I have the same exact problem as you

---

### Post by ceemos on 2006-02-18
I have not been able to get direct rendering support via the latest nvidia drivers (from apt-get)

glxinfo | grep direct always returns a no

everything seems to work just fine, just obviously not hardware accelerated

do I need to revert to older drivers, or compile new ones?

or am I just missing something ;)

edit: I guess mentioning that I have a geforce 6800 gt would be helpful :)

---

### Post by codejunkie on 2006-02-18
[QUOTE=KrazyPenguin]My card is a Geforce mx4000. 
So I suppose I have to compile cvs version of glitz??[/QUOTE]
yes compiling glitz from cvs will fix it, it works great for me now except for xvideo is really slow on any card that doesn't have pixel shader so as of right now watching movies is a no with xgl and old hardware but everything else seems fine, but this might even get fixed with more development and driver's that support xgl.

---

### Post by quietglow on 2006-02-18
> compiz is started, i must lauch "metacity --replace"

anyone with this problem??

Same problem here. The problem is that when I restart metacity, the compiz effects are gone. 

Any ideas?

---

### Post by ivangodfather on 2006-02-18
Hey, when i try kdelibs-3.5.1# ./configure i get this message:
 checking if ld supports unversioned version maps... yes
checking for aRts-1.1... ./configure: line 42045: cd: /usr/local/kde: No such file or directory
configure: error: aRts 1.1 not installed in the same prefix as KDE!
Please reinstall aRts in the same prefix as KDE, different prefixes are not
supported right now.

(kdelibs prefix is /usr/local/kde, aRts prefix is /usr)


any ideas ?

---

### Post by Milamber_Cubed on 2006-02-18
[QUOTE=quietglow]Same problem here. The problem is that when I restart metacity, the compiz effects are gone. 

Any ideas?[/QUOTE]

It would seem (to me, anyway) that either gnome-window-decorator is not running OR that the decoration module for compiz isn't being loaded.

Try running gnome-window-decorator from a terminal and see what happens and if you get any errors.

Also, run gconf-editor and check out apps>compiz>general>allscreens>options and look at the "active_plugins" option - is decoration in the list?

---

### Post by vendetta red on 2006-02-19
Just a quick update. Did a fresh install on my testing partition with the newly released Flight 4. To get Compiz working I **did** have to add the composite extension line at the bottom of my xorg.conf file. I also needed to fetch the 10 available updates before compiz would work. I was still receiving one error about a plugin not loading (can't remember the exact text) but it doesn't seem to have affected anything. Gotta love bleeding edge! :mrgreen:

---

### Post by campusloop on 2006-02-19
[QUOTE=MamiyaOtaru]Good work then.  If I sounded dubious it's only cause I couldn't have done it ;)

Still not compiling, same error.  
```
/usr/src/kdelibs-3.5.1/./kdeui/ksystemtray.cpp: In constructor 'KSystemTray::KSystemTray(QWidget*, const char*)':
/usr/src/kdelibs-3.5.1/./kdeui/ksystemtray.cpp:76: error: 'None' was not declared in this scope

```

Where is None defined anyway?  I can't quite track it down..[/QUOTE]


None is defined in <X11/X.h> included from <X11/Xlib.h>
Funny.. it compiled without problem on my dapper system. make sure 
x11proto-core-dev and libx11-dev are installed

---

### Post by idn on 2006-02-19
Hi, 

Everything looks good, thanks for the great guide. The wobbly windows and transparency is fine, so is switching desktops by ctrl, alt and dragging. 

However tab and alt does nothing, as does f11 or f12. 

Anyone else with the same behavious?

---

### Post by Heretushi on 2006-02-19
[QUOTE=Milamber_Cubed]I just posted my experiences of installing Xgl/compiz on a Intel 915GM based laptop in this thread: [http://ubuntuforums.org/showthread.php?t=132074](http://ubuntuforums.org/showthread.php?t=132074)

In short, the guide in this thread is **very** helpful, but you may need to make some tweaks. ;)[/QUOTE]
Yeah so the results are in : guys, you rock!
I got this to work on my laptop!

It's a bit on the slow side and the only acceleration I see in my videos is the one on my laptop fan when the CPU hit 100% the whole time! :P

But still, wobbly windows and cubed desktop is slick. Can't wait to show it off at work! Hahaha.

Thanks for this more than great tutorial and thanks for the subtle but very effective touch to make it work on Centrino laptops! :) Now, if only I could get my sound working...

---

### Post by aent on 2006-02-19
I just tried the CVS glitz debs posted above and I still get artifacts on my GeForce 2 Go, but its not too bad, its usable now at least. But there's another problem... when I try to start compiz, it kills metacity but compiz won't start... it never dispays the window borders and terminal says:
compiz.real: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.

Anyone have any idea how to fix that?

---

### Post by jmrush on 2006-02-19
I have xgl installed.I make it work using terminal commands,but when I try to use gnome-window-decorations it says that the command is not found.Its on gconf so ???.
Cannot make transparent windows,nor the cube running,because my 4 virtual desktops become just one when compiz starts.
Any hints.
A big thank you

---

### Post by klaxnek on 2006-02-19
As you can see the fonts are blurred during an effect. Here is a tip that I believe makes the effects cleaner (tested with nVidia).
Doesn't looks good when rotating freely the cube.
Needs restart of compiz to take effect the change.

Go to gconf-editor
Go to apps->compiz->general->allscreens->options
Change texture_filter from 'Good' to 'Fast'

---

### Post by cutOff on 2006-02-19
[QUOTE=klaxnek]As you can see the fonts are blurred during an effect. Here is a tip that I believe makes the effects cleaner (tested with nVidia).
Doesn't looks good when rotating freely the cube.

Go to gconf-editor
Go to apps->compiz->allscreens->options
Change texture_filter from 'Good' to 'Fast'[/QUOTE]
apps->compiz->allscreens->options doesn't exist for me. Nevertheless Compiz is installed.

---

### Post by codejunkie on 2006-02-19
[QUOTE=klaxnek]As you can see the fonts are blurred during an effect. Here is a tip that I believe makes the effects cleaner (tested with nVidia).
Doesn't looks good when rotating freely the cube.

Go to gconf-editor
Go to apps->compiz->allscreens->options
Change texture_filter from 'Good' to 'Fast'[/QUOTE]
after you've done that go to gconf-editor apps/compiz/plugins/wobbly/scree0/options and set friction .5 or 1 it will make the windows like jelly and you can sling them around to different desktops it serves no real purpose but it's fun.
[QUOTE=cutOff]apps->compiz->allscreens->options doesn't exist for me. Nevertheless Compiz is installed.[/QUOTE]
it's apps->compiz->general->allscreens->options

---

### Post by klaxnek on 2006-02-19
Yep sorry. It's inside apps->compiz->general->allscreens->options

---

### Post by cutOff on 2006-02-19
[QUOTE=codejunkie]it's apps->compiz->general->allscreens->options[/QUOTE]
No luck. 'Compiz' key does not exist into 'apps' key. Any clue?

---

### Post by SuperDiscoMachine V.5.7-3 on 2006-02-19
[QUOTE=cutOff]No luck. 'Compiz' key does not exist into 'apps' key. Any clue?[/QUOTE]
Just guessing, but you have to start compiz with gconf (that is, compiz --replace gconf wobbly etc...) at least once for it to show up in gconf.

---

### Post by codejunkie on 2006-02-19
[QUOTE=cutOff]No luck. 'Compiz' key does not exist into 'apps' key. Any clue?[/QUOTE]
press alt+f2 and enter ```
gconf-editor
```navigate to the apps section it should be in there if it installed correctly if not try reinstalling compiz with
```
sudo apt-get install --reinstall compiz
```

---

### Post by krausest on 2006-02-19
Thanks for the HOWTO. It looks great - but I have one major problem:
glxinfo returns OpenGL version string: 1.2 (2.0.1 NVIDIA 81.78) and indeed all OpenGL 1.4 - 2.0 extensions are missing and all programs requiring those extensions won't run (pixel/vertex shader etc.). 
This happens as soon as Xgl runs (no matter if compiz runs).
Has anyone a solution?

---

### Post by dontpanic on 2006-02-19
[QUOTE=krausest]Thanks for the HOWTO. It looks great - but I have one major problem:
glxinfo returns OpenGL version string: 1.2 (2.0.1 NVIDIA 81.78) and indeed all OpenGL 1.4 - 2.0 extensions are missing and all programs requiring those extensions won't run (pixel/vertex shader etc.). 
This happens as soon as Xgl runs (no matter if compiz runs).
Has anyone a solution?[/QUOTE]

same problem for me...

---

### Post by MamiyaOtaru on 2006-02-19
[QUOTE=campusloop]None is defined in <X11/X.h> included from <X11/Xlib.h>
Funny.. it compiled without problem on my dapper system. make sure 
x11proto-core-dev and libx11-dev are installed[/QUOTE]

They are installed.  It's quite baffling for me why it isn't finding the definition.  I just gave up and copied the definition to ksystemtray.h and it compiles.

Anyway, it works as advertised once compiled :)  Systray functions, and starting an app that places an icon there doesn't freeze konqueror!  

Everything is quite functional now except the desktop switcher.  Maybe I'll do something about that, I edited KDE's switcher once to work with 3ddesktop, maybe I can figure out compiz.

Glad you got the systray worked out.  Do you see it as the kind of fix that might make its way upstream, or more of a temporary fix until compiz is patched somehow?

---

### Post by prateek51 on 2006-02-19
I'm now at the stage where you have type in thefuture in the terminal but when i do i get:

```

gnome-window-decorator, Failed to load shadow images
$compiz.real: N composite extension

```

---

### Post by opera118 on 2006-02-19
This worked "ok" last night, but today no. Things are actually pretty broken.

First of all ubuntu's glx-packages all depends on kernel-stuff. I have to use my own compiled kernel, since ubuntu's can't find neither my sata controller or network card. Anyway, I've downloaded the packages and forces them in with dpkg.
Now, I installed 2.6.16-rc4 since it has native support for my NIC, and the ubuntu nvidia-glx package depends on nvidia driver 8178 (which doesn't work with 2.6.16, but I patched it).

8178 doesn't respect my screen resolution, with or without glx/xgl and it says it opens 1400x1050 (which I want) in the Xorg.0-log, but it's rather 1280 where the rest of the screen is outside the monitor, and I can't scroll there...
This, is disasterous. Hard to work on this machine now. And the old 7676 simply won't install now, dunno why.

It's rather unstable, it crashes every once in a while (this is the third time I write this).
And compiz is out of the question, same error as many others with GLX_EXT-stuff and bitmaps missing...

Why can't the nivida-glx packages have some kind of "soft-dependency" or preferably "recommends"? Every new package I want to install won't, since I have a "broken" package now since it's forced in...

This guide really became a lesson for me - to stick-to-the-default-settings-and-not-mess-around...
Anger and sadness, I dunno.. Maybe it's a bit of both. I remember configuring my first X 10 years ago... I hated it back then, and I still do.
And another thing, when I use the BusID option for the gfx-card, the scrollwheel on the mouse becomes left-right buttons. Without the BusID it works... Yeah.
And the keyboard is a little shaky too...
Any hints on what I'm supposed to do, except go mad and start breaking things in my surroundings? ;)

---

### Post by rasher on 2006-02-19
[QUOTE=codejunkie]i've attached the latest version of glitz from cvs.

and to compile it extract the archive cd to the glitz dir and run
```
./autogen.sh --prefix=/usr
```
[/QUOTE]
Wouldn't a cleaner solution be to use --prefix=/usr/local, then add /usr/local/lib to /etc/ld.so.conf and run ldconfig (as root), so as to avoid overwriting files installed by dpkg?

Minor nitpick anyway, happy to report that everything seems to be working.

---

### Post by cutOff on 2006-02-19
[QUOTE=opera118]And compiz is out of the question, same error as many others with GLX_EXT-stuff and bitmaps missing...[/QUOTE]
Same here even having compiled glitz stuff from cvs.

:-k

---

### Post by vendetta red on 2006-02-19
[QUOTE=prateek51]I'm now at the stage where you have type in thefuture in the terminal but when i do i get:

```

gnome-window-decorator, Failed to load shadow images
$compiz.real: N composite extension

```[/QUOTE]

It actually tells you what to do if you see this on the front page guide of this thread. Look there, you need to add a couple lines to your xorg.conf file.

---

### Post by opera118 on 2006-02-19
[QUOTE=vendetta red]It actually tells you what to do if you see this on the front page guide of this thread. Look there, you need to add a couple lines to your xorg.conf file.[/QUOTE]

If you're refering to the Composite extension section, I am happy to announce that it doesn't really change anything.
Now, I'm not using ubuntu's nvidia drivers but rather those from their site, together with all the latest patches for it from the nvnews forum [http://www.nvnews.net/vbulletin/showthread.php?t=62021](http://www.nvnews.net/vbulletin/showthread.php?t=62021) but I'd like to use ubuntu's. But that means I'd "have" to use ubuntu's kernel, which I would actually also like to. But functional ahci/ich6 support as well as the sky2 driver is necessary then, and that seems very much unprioritized by ubuntu's kernel devs.

---

### Post by campusloop on 2006-02-19
[QUOTE=MamiyaOtaru]They are installed.  It's quite baffling for me why it isn't finding the definition.  I just gave up and copied the definition to ksystemtray.h and it compiles.

Anyway, it works as advertised once compiled :)  Systray functions, and starting an app that places an icon there doesn't freeze konqueror!  

Everything is quite functional now except the desktop switcher.  Maybe I'll do something about that, I edited KDE's switcher once to work with 3ddesktop, maybe I can figure out compiz.

Glad you got the systray worked out.  Do you see it as the kind of fix that might make its way upstream, or more of a temporary fix until compiz is patched somehow?[/QUOTE]

Actually.. i am looking into this.. but it is more of a temporary solution right now. It was the easiest fix. freedesktop.org system tray specifies that SYSTEM_TRAY_REQUEST_DOCK event can be used by apps to be put into the dock. The systray patch add calls to send SYSTEM_TRAY_REQUEST_DOCK message ( in addition to custom KDE dock messages ). This protocol is the reason kde is able to put gnome apps into the dock since they use SYSTEM_TRAY_REQUEST_DOCK. But considering that kde apps can be docked into gnome system tray, they too must be following the same protocol( unless there is a workaround in gnome for kde systray apps ). Probably compiz is messing with the window hints attached to kde systray apps.

But what really baffles me is .. compiz was released and it worked perfectly with gnome and when using it from within kde it made it completely useless ( no systray, taskbar, virtual desktops ). Does no one at Novell use KDE anymore or nobody who used KDE got to test Xgl/compiz beforehand

---

### Post by Heretushi on 2006-02-19
In the Novell Video, the guy can right-click on the title bars and select the transparency level. I can't do that. Any idea why I don't have this option?

Thanks.

And I didn't have ANY trouble when installing. It worked like a charm. I just have this "libmenu.so" error that does nothing visible to it. Maybe it's this thing that is missing...?

Another edit... How can I make "thefuture" start by default? Each time I reboot, I have to start it manually by going into a console...

Thanks! :)

---

### Post by varunus on 2006-02-19
[QUOTE=opera118]This worked "ok" last night, but today no. Things are actually pretty broken.

First of all ubuntu's glx-packages all depends on kernel-stuff. I have to use my own compiled kernel, since ubuntu's can't find neither my sata controller or network card. Anyway, I've downloaded the packages and forces them in with dpkg.
Now, I installed 2.6.16-rc4 since it has native support for my NIC, and the ubuntu nvidia-glx package depends on nvidia driver 8178 (which doesn't work with 2.6.16, but I patched it).

8178 doesn't respect my screen resolution, with or without glx/xgl and it says it opens 1400x1050 (which I want) in the Xorg.0-log, but it's rather 1280 where the rest of the screen is outside the monitor, and I can't scroll there...
This, is disasterous. Hard to work on this machine now. And the old 7676 simply won't install now, dunno why.

It's rather unstable, it crashes every once in a while (this is the third time I write this).
And compiz is out of the question, same error as many others with GLX_EXT-stuff and bitmaps missing...

Why can't the nivida-glx packages have some kind of "soft-dependency" or preferably "recommends"? Every new package I want to install won't, since I have a "broken" package now since it's forced in...

This guide really became a lesson for me - to stick-to-the-default-settings-and-not-mess-around...
Anger and sadness, I dunno.. Maybe it's a bit of both. I remember configuring my first X 10 years ago... I hated it back then, and I still do.
And another thing, when I use the BusID option for the gfx-card, the scrollwheel on the mouse becomes left-right buttons. Without the BusID it works... Yeah.
And the keyboard is a little shaky too...
Any hints on what I'm supposed to do, except go mad and start breaking things in my surroundings? ;)[/QUOTE]

The nvidia-glx packages are designed to work only with Ubuntu kernels.  If you're running a custom kernel, use nvidia's installer from their website to install a kernel.

Generally, its not a "don't change from default" thing but a "don't try to make the packages work with source-compiled software."

You should be able to fix your broken packages with a "sudo apt-get -f install" in a terminal; it will remove some packages.

Then, anything that depends on Ubuntu's kernel, you're going to have to compile yourself from source.  That's the pain of not using a precompiled kernel...

---

### Post by varunus on 2006-02-19
[QUOTE=Heretushi]In the Novell Video, the guy can right-click on the title bars and select the transparency level. I can't do that. Any idea why I don't have this option?

Thanks.

And I didn't have ANY trouble when installing. It worked like a charm. I just have this "libmenu.so" error that does nothing visible to it. Maybe it's this thing that is missing...?[/QUOTE]

Unfortunately, I think they took the menu plugin out.  It was in the compiz changelog a little while back.  The "opacity for compiz" howto in the dapper forums works well as a replacement though.

---

### Post by McQuaid on 2006-02-19
I haven't tried this yet as I'm still on breezy, but some stuff I'd like to know.

1) more reports from people on games.  Do they work? Worse/better/same? Fullscreen hosed? 

2) I use fast user switch a lot so I was wondering if this has a problem with multiple X screens.  Do both get gl accelerated? What affect does that have on performance? Does only one get accelerated?  Does the other screen die or default to non accelerated?

3) Anyone look at temperature difference of their cards? As they are now running opengl mode all the time.


And not to flog a dead horse, but IF one wanted to try this with breezy could one not backport x.org from dapper sources with jdong's backport script (ubp-build.py).  If not why not?

---

### Post by idn on 2006-02-19
Hi,

I was jsut wondering how do I put an iage on the top of the cube, and what format can this be in?

Is it the plugins > cube > screen0 > optons > svgs option i need to change?

---

### Post by KrazyPenguin on 2006-02-19
[QUOTE=codejunkie]yes compiling glitz from cvs will fix it, it works great for me now except for xvideo is really slow on any card that doesn't have pixel shader so as of right now watching movies is a no with xgl and old hardware but everything else seems fine, but this might even get fixed with more development and driver's that support xgl.[/QUOTE]

Can somebody please give me a link to compiling glitz from cvs or paste a quick how-to.
Thank you in advance.

---

### Post by raha on 2006-02-19
I could use Xgl and compiz and it is really cool and nice.
I have few question now:
1- Does Xgl and compiz work on 5.10 ubuntu as well (I tried it on 6.10 Ubuntu Dapper Drake Flight CD3)?

2- I am updating my system now. will Xgl and compiz work like before or it will stop workig ?

---

### Post by Heretushi on 2006-02-19
I haven't been able to use in on Breezy because it requires Xorg 7. And it's not in Breezy.

I updated twice since I made it work and it still does.

---

### Post by cutOff on 2006-02-19
A guy have managed to install in breezy 

[http://cerocoma.blogspot.com/2006/02/cambios-y-errores.html](http://cerocoma.blogspot.com/2006/02/cambios-y-errores.html) (In spanish)

I'm not sure if it works though. BEWARE ANYWAY!

---

### Post by TravisNewman on 2006-02-19
this is an amazing howto Jonathan. Works like a dream (After compiling glitz, for me).

---

### Post by Milamber_Cubed on 2006-02-19
[QUOTE=cutOff]A guy have managed to install in breezy 

[http://cerocoma.blogspot.com/2006/02/cambios-y-errores.html](http://cerocoma.blogspot.com/2006/02/cambios-y-errores.html) (In spanish)

I'm not sure if it works though.[/QUOTE]

XGL WORKING ON BREEZY!

Just tried it.. after installing all the stuff with apt-get, i basically followed the instructions on this guide (note: this method installs the Xgl binary in /usr/X11R6/bin/Xgl - need to change gdm.conf to reflect this) and it's working!

There is a problem loading libcube and as a result zoom and rotate are not loaded  but the other effects are working.

UPDATE::

I replaced the cube, rotate and zoom module files with the ones from my desktop (running dapper) and all plugins now load correctly. Woo Hoo!!

ANOTHER UPDATE::

I just realised this is a bit off-topic for this thread... Sorry! I thought it would be best to respond to the initial post by cutOff in the same thread.

---

### Post by idn on 2006-02-19
Has anyone noticed that BMP doesnt wobble when you move it about? This kinda sucks, as I kinda use it alot. Anyone have any ideas ao to why?

---

### Post by hectorC on 2006-02-19
Thanks a lot for this guide! It's working for me with almost no problems using my nvidia 6600. The only strange (maybe not) thing that I found is that there are almost no options in the nvdia-settings control panel! There is only one page  with very simple options related only to the panel itself... beside that everything else is gone. At the console I get this:

~$ nvidia-settings

ERROR: NV-CONTROL extension not found on this Display.


(nvidia-settings:5303): Gdk-CRITICAL **: gdk_window_invalidate_rect: assertion `window != NULL' failed

I realized about this when I tried to run a video game and tried to set the OpenGL options.

Is this part of the development process?

thanks for any help!

Hector.

---

### Post by MamiyaOtaru on 2006-02-19
[QUOTE=idn]Has anyone noticed that BMP doesnt wobble when you move it about?[/QUOTE]
Same with XMMS.  Presumable because it isn't handled by gnome-window-decoration (no standard windecos) so there is no gnome-window-decoration to drag.

Note that it does wobble if you go straight to compiz by using alt-left click to drag.

---

### Post by KrazyPenguin on 2006-02-19
[QUOTE=codejunkie]yes compiling glitz from cvs will fix it, it works great for me now except for xvideo is really slow on any card that doesn't have pixel shader so as of right now watching movies is a no with xgl and old hardware but everything else seems fine, but this might even get fixed with more development and driver's that support xgl.[/QUOTE]

What do I have to do to compile glitz from cvs???

---

### Post by angkor on 2006-02-19
:shock: :shock: 

Oh wow, this is _really_ something....didn't think this would be available so soon. I especially installed dapper to see this...and it is better than I expected.

Works really well with my old nvidia card (thanks for putting up the cvs glitz)

Thanks again Poofy, and all the coders who make this happen!

I'll be wobbling my windows til next morning I think  :)\\:D/

---

### Post by KrazyPenguin on 2006-02-19
All I get is a black, grey and white screen and a cursor.

I can rotate the cube, etc, but I cant' see a desktop 

:(

---

### Post by angkor on 2006-02-19
[QUOTE=KrazyPenguin]What do I have to do to compile glitz from cvs???[/QUOTE]

I downed the glitz.tgz from page 11 (thanks Codejunkie) of this thread and it worked flawlessly

---

### Post by KrazyPenguin on 2006-02-19
[QUOTE=angkor]I downed the glitz.tgz from page 11 (thanks Codejunkie) of this thread and it worked flawlessly[/QUOTE]

thx now at least I have a starting point

;-)

---

### Post by monkotronic on 2006-02-19
i have a nvidia geforce 4mmx video card on an x86 machine.  i followed all of the steps, but every time i type 'thefuture' my screen turns black.  i still have a mouse and when i point and click where a menu would be on the screen, a white box momentarily appears.  also, when i run my mouse over where the terminal screen was, it gets a text hash; but the screen remains black.

i built glitz 5.3 as a solution with no luck.  i could not remove the other glitz package, though, cause it kept wanting to remove the xserver as well.  i dont know if that is the problem. 

anyway, anyone got something for me to shoot at?

thanx.

---

### Post by KrazyPenguin on 2006-02-19
[QUOTE=monkotronic]i have a nvidia geforce 4mmx video card on an x86 machine.  i followed all of the steps, but every time i type 'thefuture' my screen turns black.  i still have a mouse and when i point and click where a menu would be on the screen, a white box momentarily appears.  also, when i run my mouse over where the terminal screen was, it gets a text hash; but the screen remains black.

i built glitz 5.3 as a solution with no luck.  i could not remove the other glitz package, though, cause it kept wanting to remove the xserver as well.  i dont know if that is the problem. 

anyway, anyone got something for me to shoot at?

thanx.[/QUOTE]

Nice we are working on this at the same time.
I just went through the guide on page one again and for the hell of it did the xmodmap /usr/share/xmodmap/xmodmap.us
once again and then 'thefuture' and it works.
No rebooting or anything like that.
Try it and let me know if this helps.
;-)

Edited: just want to add that i compiled the glitz and did thefuture and it DIDN"T work.
You have to do the xmodmap blahblahblah command first.

---

### Post by raha on 2006-02-19
I did follow this tutorial and everything worked fine for me.
I am installing Ubuntu Dapper Drake Flight CD4 and it says it comes with Xgl and Compiz. What does that mean and how can I get it working ?

Do I need to follow the same howto ?

Thanks

---

### Post by jlas9 on 2006-02-19
Hi.
I follow your explanations poofyhairguy, but when gdm are trying get up again, after editing /etc/gdm/gdm.conf-custom and /etc/X11/xorg.conf, i get this error:

Couldn't open RGB_DB '/usr/share/X11/rgb'

Could this be cos i don't have the accelerated 'nvidia' driver installed and i use the default 'nv' or this is not related?.

Thanks in advance.

Best regards.

---

### Post by scaine on 2006-02-19
[QUOTE=hectorC]
~$ nvidia-settings

ERROR: NV-CONTROL extension not found on this Display.


(nvidia-settings:5303): Gdk-CRITICAL **: gdk_window_invalidate_rect: assertion `window != NULL' failed[/QUOTE]

It's not much help, but I get the same.  It's a pain, cos my monitor is too bright by default and I use this to lower the brightness.

Does anyone have any ideas as to why the NV-Control extension wouldn't work anymore?  I'm using screen 0, but specifying that screen to the nvidia-settings program makes no difference.

---

### Post by monkotronic on 2006-02-19
WOOOHOOOO after running the xmodmap command again it worked!  very cool.  thanx soo much.

[QUOTE=KrazyPenguin]Nice we are working on this at the same time.
I just went through the guide on page one again and for the hell of it did the xmodmap /usr/share/xmodmap/xmodmap.us
once again and then 'thefuture' and it works.
No rebooting or anything like that.
Try it and let me know if this helps.
;-)

Edited: just want to add that i compiled the glitz and did thefuture and it DIDN"T work.
You have to do the xmodmap blahblahblah command first.[/QUOTE]

---

### Post by Rahu on 2006-02-19
Is there any way I can use this on the live cd? I've managed everything up to the point where it says to reset, but that just seems like a bad idea. Can I just restart xorg or something?(If so, how? I'm pretty clueless :))

---

### Post by Milamber_Cubed on 2006-02-19
[QUOTE=Rahu]Is there any way I can use this on the live cd? I've managed everything up to the point where it says to reset, but that just seems like a bad idea. Can I just restart xorg or something?(If so, how? I'm pretty clueless :))[/QUOTE]

I got this working on a livecd a few days ago when it tells you to reboot just switch to tty1 (ctrl+alt+F1) and do the following.

```

sudo killall gdm

```

keep doing that until you see something along the lines of 

```

no processes killed

```

to get things going then do
```
sudo /etc/init.d/gdm start
```

If everything is well X should restart and after logging in you should be able to open a terminal and run "thefuture"

---

### Post by poofyhairguy on 2006-02-19
[QUOTE=panickedthumb]this is an amazing howto Jonathan. Works like a dream (After compiling glitz, for me).[/QUOTE]


Thanks. Glad you like. Your posts have helped me compile eye candy often!

---

### Post by Heretushi on 2006-02-19
Is there a way to get "thefuture" to run by default? Because right now, on both my laptop and desktop, each time I log on, I have to open a console and type "thefuture" to get it to start.

Thanks!

(BTW: Thanks again poofy, got this working on my desktop in 15 minutes. It works ab-so-lu-te-ly beautifully. It really gorgeous to look at this without any lag.)

---

### Post by Milamber_Cubed on 2006-02-19
[QUOTE=Heretushi]Is there a way to get "thefuture" to run by default? Because right now, on both my laptop and desktop, each time I log on, I have to open a console and type "thefuture" to get it to start.

Thanks!

(BTW: Thanks again poofy, got this working on my desktop in 15 minutes. It works ab-so-lu-te-ly beautifully. It really gorgeous to look at this without any lag.)[/QUOTE]


That's the easy bit! Well it was the only bit left for me to figure out for myself anyway.. :rolleyes:

System-->Preferences-->Sessions

Select the "Startup Programs" tab and add "thefuture" to the list. Works like a charm for me :)

EDIT: And I would like to agree about the ease of installation thanks to this thread! THANKS!!

---

### Post by Rahu on 2006-02-19
Sadly, it didn't run properly on my Geforce 2 :( I just got a grey screen with a cursor. The keyboard shortcuts to switch the side of the cube made the cursor disappear for a second, and right click made a white box pop up for a little bit.

---

### Post by chanders on 2006-02-19
[QUOTE=idn]Has anyone noticed that BMP doesnt wobble when you move it about? This kinda sucks, as I kinda use it alot. Anyone have any ideas ao to why?[/QUOTE]

LOL, yeah I noticed the same with XMMS too... anyone?

---

### Post by Rob2687 on 2006-02-19
Maybe that's why this this in still in development. Jeez...this thing is like not in even beta stage and you people expect it to work perfectly with everything.

---

### Post by hectorC on 2006-02-19
[QUOTE=hectorC]Thanks a lot for this guide! It's working for me with almost no problems using my nvidia 6600. The only strange (maybe not) thing that I found is that there are almost no options in the nvdia-settings control panel! There is only one page  with very simple options related only to the panel itself... beside that everything else is gone. At the console I get this:

~$ nvidia-settings

ERROR: NV-CONTROL extension not found on this Display.


(nvidia-settings:5303): Gdk-CRITICAL **: gdk_window_invalidate_rect: assertion `window != NULL' failed

I realized about this when I tried to run a video game and tried to set the OpenGL options.

Is this part of the development process?

thanks for any help!

Hector.[/QUOTE]

sorry if I'm being impatient... just that this seems to be a busy thread and my posting could have passed unnoticed.

sorry.

---

### Post by veikkou on 2006-02-20
I did a search and did not find a note about this, but I could have overlooked it on any one of the 32 pages of replies.

A little note for me, everything was perfect except the keyboard.  I had to use:

xmodmap /usr/share/xmodmap/xmodmap.us-101

which could be a little decieving as there are several US keybard maps.  Just thought I would share.  Great guide! Props to all of the developers, fantastic work.

---

### Post by Rob2687 on 2006-02-20
I've noticed high CPU usage from Xgl when dragging windows and using the zoom plugin. Has anyone else noticed similar results.

I'm guessing that means it's going to software rendering or something?




Another thing. The nvagp option seems to disable AGP.
With it set to "1", nvclock shows that AGP 8x is disabled.
I set it to "3" and it was enabled at 8x

Before:
```
-- AGP info --
Status:         Disabled
Rate:           0X
AGP rates:      4X 8X
Fast Writes:    Disabled
SBA:            Disabled

```

After
```
-- AGP info --
Status:         Enabled
Rate:           8X
AGP rates:      4X 8X
Fast Writes:    Disabled
SBA:            Enabled

```

---

### Post by K.Mandla on 2006-02-20
WOW! That was so cool. It didn't work perfectly for me, but it was a LOT of fun. 

The cube would spin and I had nifty wobble, but I was getting the strange redraw effects. Since Firefox was useless under those conditions, I couldn't troubleshoot it. 

I've got the 7800 GTX, by the way. I think I'll be back in a while, when I've got a better handle on the details. Thanks for the ride!

---

### Post by DarkB on 2006-02-20
XGL seems to brake emacs for me ... something about "black" not being defined:(

---

### Post by Qrk on 2006-02-20
I decided to jump the gun and upgrade just for these effects. Good thing they finally work. There are a few bugs, like not every window has a functioning titlebar. But its really cool, and thats all that matters.

---

### Post by neocsr on 2006-02-20
[QUOTE=Milamber_Cubed]XGL WORKING ON BREEZY!

Just tried it.. after installing all the stuff with apt-get, i basically followed the instructions on this guide (note: this method installs the Xgl binary in /usr/X11R6/bin/Xgl - need to change gdm.conf to reflect this) and it's working!

There is a problem loading libcube and as a result zoom and rotate are not loaded  but the other effects are working.

UPDATE::

I replaced the cube, rotate and zoom module files with the ones from my desktop (running dapper) and all plugins now load correctly. Woo Hoo!!

ANOTHER UPDATE::

I just realised this is a bit off-topic for this thread... Sorry! I thought it would be best to respond to the initial post by cutOff in the same thread.[/QUOTE]


Yes, I'm having the same problem with Breezy... almost everything works fine... there are some problems with [COLOR="DarkRed"]libcube.so[/COLOR] and [COLOR="DarkRed"]libmenu.so[/COLOR]:

/opt/fdo/bin/compiz: [COLOR="Blue"]Couldn't load plugin 'libcube.so'[/COLOR]
/opt/fdo/bin/compiz: 'rotate' plugin must be loaded after 'cube' plugin
/opt/fdo/bin/compiz: Can't activate 'rotate' plugin due to dependency problems
/opt/fdo/bin/compiz: 'zoom' plugin must be loaded after 'cube' plugin
/opt/fdo/bin/compiz: Can't activate 'zoom' plugin due to dependency problems
/opt/fdo/bin/compiz: dlsym: /usr/lib/libmenu.so: undefined symbol: getCompPluginInfo
/opt/fdo/bin/compiz: Failed to lookup getCompPluginInfo in 'libmenu.so' plugin

Can anybody put their libcube.so and libmenu.so from Dapper to try it in Breezy?


Thx. :-k

---

### Post by wout.wepsait.com on 2006-02-20
I used to experience lots of little strange things using firefox.... I switced to epiphany and it cleared the skies.

I miss a few extensions but it surfs a lot better now.

---

### Post by poofyhairguy on 2006-02-20
[QUOTE=Rob2687]I've noticed high CPU usage from Xgl when dragging windows and using the zoom plugin. Has anyone else noticed similar results.

I'm guessing that means it's going to software rendering or something?
[/QUOTE]

Yeah. No driver supports it 100% yet.

---

### Post by opera118 on 2006-02-20
I've noticed (when it worked on saturday) that my desktop became very fast and not slow... Cpu usage is almost rudely low. I think this "window on gl instead of gl on window" is something we've been waiting for longer than we know..
Anyway, got lots of work to do, seems X 7 is to blame for my screen resolution being messed up. Tried to "disable" EDID stuff, but it just won't work yet..

---

### Post by | MM | on 2006-02-20
Oh thanks soo much phg, this works beautifully!!

I sure hope XGL progresses rapidly, this is a serious coup for Linux on the desktop in my opinion.

I haven't noticed any issues that would not make me use XGL in its current state.  I am very happy and looking forward to future devlopments.

Also i am very happy with Flight 4!  Except i rather liked the new GNOME logout window with its colourful icons.  In flight 4 its reverted to the bland old little buttons. 

I am getting closer and closer to a world without WindowsXP.

Anyway cheers, and keep up the great work on the forums.

---

### Post by Milamber_Cubed on 2006-02-20
[QUOTE=neocsr]Yes, I'm having the same problem with Breezy... almost everything works fine... there are some problems with [COLOR="DarkRed"]libcube.so[/COLOR] and [COLOR="DarkRed"]libmenu.so[/COLOR]:

/opt/fdo/bin/compiz: [COLOR="Blue"]Couldn't load plugin 'libcube.so'[/COLOR]
/opt/fdo/bin/compiz: 'rotate' plugin must be loaded after 'cube' plugin
/opt/fdo/bin/compiz: Can't activate 'rotate' plugin due to dependency problems
/opt/fdo/bin/compiz: 'zoom' plugin must be loaded after 'cube' plugin
/opt/fdo/bin/compiz: Can't activate 'zoom' plugin due to dependency problems
/opt/fdo/bin/compiz: dlsym: /usr/lib/libmenu.so: undefined symbol: getCompPluginInfo
/opt/fdo/bin/compiz: Failed to lookup getCompPluginInfo in 'libmenu.so' plugin

Can anybody put their libcube.so and libmenu.so from Dapper to try it in Breezy?


Thx. :-k[/QUOTE]

This is what I did and it worked - I plugins from the dapper debs (I guess you can find this on the repositories somehow?) into the compiz libs folder. libmenu is no longer required according to the CVS notes, so I think you can safely ignore that message.

I will attach the contents of my breezy /usr/lib/compiz folder for you - if you trust me ;) you can use that. You will need to add cube, rotate and zoom  (in that order) to the list of loaded plugins in gconf-editor after you put these in though - otherwise it will not try to load them. So in short:

1. copy libs from tar.gz into /usr/lib/compiz
2. run gconf-editor and add cub,rotate,zoom to list of loaded pluigins
3. run "thefuture" again
4. have fun!

Hope that helps

---

### Post by teppic on 2006-02-20
It seems that compiz has been changed in universe (unfortunately not the new version) and the decorator programs have been taken out. You now have to install compiz-gnome as well.

Guide needs updating as a result.

---

### Post by aamukahvi on 2006-02-20
Just replaced my R9500 for a GF6200. Everything is now smooth, even the videos. The app-startup animation is smooth as well. Oh yeahhhh... :mrgreen:

One more advantage. My computer's now quieter, too. No fan on the GF6200, just heatsinks :)

I guess I'm just saying that if you're thinking about switching; do it. ATI don't deserve your money ;)

---

### Post by Subbu.exe on 2006-02-20
Everything Works fine! I'm Using Dapper Flight-4.
the only Gripe is sometimes the text gets _blurred_ for around a second
it recovers though.

P.S->Wobble Rocks! even my girlfriend loves it!

---

### Post by jdong on 2006-02-20
[QUOTE=McQuaid]
And not to flog a dead horse, but IF one wanted to try this with breezy could one not backport x.org from dapper sources with jdong's backport script (ubp-build.py).  If not why not?[/QUOTE]

I think you _could_; start from xserver-xgl, and backport any packages it demands.

The problem would be that you'll need to backport maybe 50+ source packages and recompile another 100 or so before your system is stable again, due to cross and reverse dependencies. Backporting something as huge as X will cause a big ripple of dependency issues :)


If you really want to do that, cool. I wouldn't bother :). If you're gonna test an unstable feature, might as well use the development branch :)

---

### Post by Subbu.exe on 2006-02-20
Hmmm, How do i set the Transparency. the Opacity option isnt Present in the Window-RightClick Menu.

---

### Post by opera118 on 2006-02-20
I can boot up X!!! I'm happy. Can you digg it? I'm on the 'nv' driver...

It turned out to be completely the nvidia driver (as usual). 8178 is _completely_ broken to its bones... 7676 works though, but xgl doesn't seem to work well on that version, or am I missing something here? Would like to stick to 7676 for a while until nvidia releases a new even buggier driver.. It's funny, I started using their kernel like 5-6 years ago or so (it feels like that at least). And the suckiness seems to be rather linear to the version counter. Or maybe it's just me.

---

### Post by mrogers on 2006-02-20
I've used 8178 for weeks without a single problem. I say it's the best driver so far. No composite manager crashes since I installed 8178.

---

### Post by aamukahvi on 2006-02-20
Hey guys, I just noticed I can run glxgears now. Long live Nvidia :)

---

### Post by opera118 on 2006-02-20
[QUOTE=mrogers]I've used 8178 for weeks without a single problem. I say it's the best driver so far. No composite manager crashes since I installed 8178.[/QUOTE]

Lol, you say it's the best... Well the moon might stop spinning.
It doesn't really matter, and I certainly don't give a whissle if it works for you. The driver _has_ issues that many others have experienced. I just wanted to notice people that if they get the same problem with resolutions and find a sollution they are welcome to share it.
So far I've tried every combination I can think of. 

Comments like yours aren't helping anyone with anything. Offcourse 8178 works for a lot of people, it's the freaking default so far in ubuntu. *sigh*

---

### Post by OneSeventeen on 2006-02-20
So after trying to get this up and running an an old Pentium 3 with an integrated nVidia chip, I just get all sorts of X errors, mainly centering around the nvidia driver not working.

Since I'm sure it would have been slow as anything anyway, I gave up and uninstalled compix and xserver-xgl.  Unfortunately I had replaced /etc/X11/X with a symlink to /usr/bin/Xorg so it can't start X anymore.

Tips on restoring /etc/X11/X  ?

---

### Post by MamiyaOtaru on 2006-02-20
> Tips on restoring /etc/X11/X ?
apt-get -reinstall install xserver-common

---

### Post by xophos on 2006-02-20
[QUOTE=Ainvar]Awesome howto, I am doing this running Dapper Drake on a Dell Precision Workstation M70 laptop that is sporting a nvidia quadro fx go 1400 video card.
I am running everything stock and nothing manually compiled or anything.

Sweet howto, cedega does run like but until you restart X, but movies do play when running under thefuture script. Awesome howto and this is how eyecandy is suppose to be in linux :) :)

Awesome howto!! had to say it once again.[/QUOTE]
I have the exact same machine but i get (with the newest packages out of universe) these graphical errors (see attached picture) that make it totally unuseable. 
I have tried every combination xorg.conf options and start-options for Xgl that i could find. 
The shown error is repeatable with Xgl allone or with compiz and gnome-window-decorator loaded. It is most extreme with scrolling, mouse-over and window-resizing (in that order). 
Running fullscreen or not, running directly from gdm or from a running x-session make no difference.
Could anyone give me a hint, i'm stuck for now. 
:cry: 

xophos

---

### Post by gnumdk on 2006-02-20
>I haven't noticed any issues that would not make me use XGL in its
>current state. I am very happy and looking forward to future
>devlopments.

You want one issue?

Try to build something with gcc or use an app that eat cpu time, you will see Xgl be slow, really slow!!!

But, it's not an Xgl bug, try to play quake3 while building.

---

### Post by fenwik on 2006-02-20
[QUOTE=KrazyPenguin]All I get is a black, grey and white screen and a cursor.

I can rotate the cube, etc, but I cant' see a desktop 

[/QUOTE]

I have the same problem, with a Nvidia Geforce4 440go. Using xmodmap /usr/share/xmodmap/xmodmap.us that was suggested to fix the problem earlier in the thread doesn't work.

---

### Post by Rob2687 on 2006-02-20
I think the xmodmap is mean to solve keyboard issues. Not graphical errors.

---

### Post by KageKeeper on 2006-02-20
I am just wondering if anyone has any advice for me.. :)

I followed the howto and everything works, Xgl is lovely!

Here's my issue.

I am not sure if I am using hardware acceleration. When I enable compiz and try to scroll through a webpage, for example, it's very choppy.

Also, I did a 'glxinfo | grep direct' and I get a 'no'.

I use an nVidia 6200 card, so I am not sure what is going on.

cat /proc/drivers/nvidia/agp/status gives me this:

```
Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Enabled
SBA:             Enabled

```

So any advice would be helpful. :)

Other than that, great howto!

---

### Post by raha on 2006-02-20
I have a problem.
I installed the Xgl and Compiz and it works very well.
The only problem is that the top bar (minimize, close, unmaximise) is no longer available.

I did the same thing before and everything was fine but this time the bar is gone by doing the same thing.

Thanks

---

### Post by cutOff on 2006-02-20
[QUOTE=OneSeventeen]So after trying to get this up and running an an old Pentium 3 with an integrated nVidia chip, I just get all sorts of X errors, mainly centering around the nvidia driver not working.

Since I'm sure it would have been slow as anything anyway, I gave up and uninstalled compix and xserver-xgl.  Unfortunately I had replaced /etc/X11/X with a symlink to /usr/bin/Xorg so it can't start X anymore.

Tips on restoring /etc/X11/X  ?[/QUOTE]
Are you sure /etc/X11/X points to /usr/bin/Xorg?? Did you remove /etc/X11/X before create the new symlink?

```
ls -l /etc/X11/X
```

[QUOTE="MamiyaOtaru]apt-get -reinstall install xserver-common[/QUOTE]
I think it's 

apt-get --reinstall install xserver-common

---

### Post by chrisrx on 2006-02-20
[QUOTE=xophos]I have the exact same machine but i get (with the newest packages out of universe) these graphical errors (see attached picture) that make it totally unuseable. 
I have tried every combination xorg.conf options and start-options for Xgl that i could find. 
The shown error is repeatable with Xgl allone or with compiz and gnome-window-decorator loaded. It is most extreme with scrolling, mouse-over and window-resizing (in that order). 
Running fullscreen or not, running directly from gdm or from a running x-session make no difference.
Could anyone give me a hint, i'm stuck for now. 
:cry: 

xophos[/QUOTE]
Change from 16 bit colour  to 24 bit colour.

Kagekeeper:  I have the exact same problem.  I can't start stepmania because it says that I don't have direct rendering enabled

---

### Post by DeeZiD on 2006-02-20
@KageKeeper:

That's normal if you use Xgl. Firefox and OpenOffice are damn slow here.
We have to wait for new drivers from ATi and NVIDIA optimized for Xgl.

 regards Dennis

---

### Post by Rob2687 on 2006-02-20
They are both slow anyways. It's especially noticable on older machines.

---

### Post by KageKeeper on 2006-02-20
All right. :)

I shall do that.

Now..anyone have a fix for the Shift-Backspace killing the xserver?

I thought I saw one somewhere, and now I cannot find it. :-k

---

### Post by DeeZiD on 2006-02-20
Firefox is as fast as under WinXP in X11 when RenderAccel is active.
With Xgl Firefox and many other programs don't seem to be accelerated.
New drivers should fix that issue.

@KageKeeper
Just read the HowTo on the first page of this thread (xmodmap)


regards Dennis

---

### Post by xophos on 2006-02-20
> Change from 16 bit colour to 24 bit colour.

That would be a very good idea had i ever used 16 bit color.
But since that isn't the case, i am as stuck as before. :-(

---

### Post by granite230 on 2006-02-20
I tried this before from another howto but I failed miserably.

This new howto looks a lot clearer but there is one thing I would like to see in more detail:

*You must compile the newest CVS version of glitz to get this to work with Nvidia cards that lack Pixel Shaders (aka anything older than a 5200 FX). Hopefully this will be updated in the repository soon.*

I have a Nvidia Geforce 4 MX 440, is that older than the 5200FX? I think it is but I'm really not into hardware at all so I wouldn't know.

And how exactly do I compile the newest CVS version of glitz?
I encounter 'CVS' lots of times but I still don't know what it is or how it works... everytime I try to do something with it in the command line it asks me for a 'CVS password'. I don't get it. I always get stuck when I read 'CVS' in howto's... I'm almost afraid of that word.

The rest is perfectly clear :)

---

### Post by scaine on 2006-02-20
[QUOTE=opera118]Comments like yours aren't helping anyone with anything. Offcourse 8178 works for a lot of people, it's the freaking default so far in ubuntu. *sigh*[/QUOTE]

Jeez - first it's "Broken to it's bones", then after mrogers' comment you admit it works for a lot of people?  So which is it?  You should decide before you slag people off for trying to help.

Good luck getting it going though.  This Compiz stuff is mind blowing.

---

### Post by DeeZiD on 2006-02-20
@granite230
Just install the new glitz-release from universe (0.5.3).
It contains all needed fixes :)
(allready tested on my good ol' Geforce2MX200 :cool:)

regards Dennis

---

### Post by cutOff on 2006-02-20
[QUOTE=DeeZiD]@granite230
Just install the new glitz-release from universe (0.5.3).
It contains all needed fixes :)
(allready tested on my good ol' Geforce2MX200 :cool:)

regards Dennis[/QUOTE]
Great! I didn't know. Thanks for the info.

---

### Post by KageKeeper on 2006-02-20
Ah.

There was just an update to compiz..

And now it seems to be broken.

thefuture gets me

```
/usr/bin/thefuture: line 2: gnome-window-decorator: command not found
rob@kagekeeper:~$ compiz.real: Couldn't load plugin 'libgconf.so'
compiz.real: dlsym: /usr/lib/libmenu.so: undefined symbol: getCompPluginInfo
compiz.real: Failed to lookup getCompPluginInfo in 'libmenu.so' plugin

```

And I have no title bars now. On anything.

---

### Post by roidelapluie on 2006-02-20
When I launch "the future":

compiz.real: Couldn't load plugin 'libgconf.so'
compiz.real: Couldn't load plugin 'libmenu.so'

All works... but I haven't any Window Border !! (Not border selector in "themes péférences").

Its very sad :'(. How to arrange the problem?

---

### Post by DeeZiD on 2006-02-20
Compiz was splitted into compiz-kde and compiz-gnome.
Just install the needed files and it works again. ;)


regards Dennis

---

### Post by granite230 on 2006-02-20
The latest version of Glitz I can find with Synaptic is 0.4.4
How can I obtain 0.5.3?

---

### Post by DeeZiD on 2006-02-20
Are your universe-repos enabled?

---

### Post by KageKeeper on 2006-02-20
[QUOTE=DeeZiD]Compiz was splitted into compiz-kde and compiz-gnome.
Just install the needed files and it works again. ;)


regards Dennis[/QUOTE]

Ahh!

Thanks DeeZiD!

---

### Post by granite230 on 2006-02-20
They are all enabled, including this one:

[I]deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe[/I]

I think you mean these. I removed the '#' in front of them. So yes they are enabled. I also did an apt-get update/upgrade. I did not reboot.

---

### Post by aamukahvi on 2006-02-20
[QUOTE=granite230]They are all enabled, including this one:

[I]deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe[/I]

I think you mean these. I removed the '#' in front of them. So yes they are enabled. I also did an apt-get update/upgrade. I did not reboot.[/QUOTE]
You need to be using Dapper. They aren't available for Breezy.

---

### Post by granite230 on 2006-02-20
[QUOTE=aamukahvi]You need to be using Dapper. They aren't available for Breezy.[/QUOTE]

So there's no way I can get Xgl/Compiz working on Breezy?
Is it possible to dist-upgrade to the latest Dapper?

---

### Post by | MM | on 2006-02-20
Hey i noticed there was a patch for compiz in synaptic.  After downloading the entire list of updates, i was promtped to restart.  I did so.

After the restart i too have the libmenu.so glitch.

```
matthew@ubuntu:~$ compiz.real: Couldn't load plugin 'libgconf.so'
compiz.real: Couldn't load plugin 'libmenu.so'

```

It was working flawlessly for me prior ... doh.


Any thoughts?

---

### Post by aamukahvi on 2006-02-20
[QUOTE=granite230]So there's no way I can get Xgl/Compiz working on Breezy?[/QUOTE]
Basically, no.
[QUOTE=granite230]Is it possible to dist-upgrade to the latest Dapper?[/QUOTE]
Yes. Do so at your own risk. At least make backups ;)

---

### Post by vendetta red on 2006-02-20
[QUOTE=| MM |]
Hey i noticed there was a patch for compiz in synaptic. After downloading the entire list of updates, i was promtped to restart. I did so.

After the restart i too have the libmenu.so glitch.

Code:

matthew@ubuntu:~$ compiz.real: Couldn't load plugin 'libgconf.so' compiz.real: Couldn't load plugin 'libmenu.so'


It was working flawlessly for me prior ... doh.


Any thoughts?
[/QUOTE]

[QUOTE=DeeZiD]Compiz was splitted into compiz-kde and compiz-gnome.
Just install the needed files and it works again. ;)


regards Dennis[/QUOTE]

I believe this fixes that problem.

---

### Post by raha on 2006-02-20
[QUOTE=raha]I have a problem.
I installed the Xgl and Compiz and it works very well.
The only problem is that the top bar (minimize, close, unmaximise) is no longer available.

I did the same thing before and everything was fine but this time the bar is gone by doing the same thing.

Thanks[/QUOTE]

Hi, anybody know the answer to this problem ?

---

### Post by DeeZiD on 2006-02-20
sudo apt-get install compiz-gnome
killall compiz.real
thefuture

---

### Post by | MM | on 2006-02-20
Wow.  Thanks for the quick reply.  It has worked and i am a happy camper once agin.


Again.  Many Thanks.

---

### Post by Ainvar on 2006-02-20
[QUOTE=xophos]I have the exact same machine but i get (with the newest packages out of universe) these graphical errors (see attached picture) that make it totally unuseable. 
I have tried every combination xorg.conf options and start-options for Xgl that i could find. 
The shown error is repeatable with Xgl allone or with compiz and gnome-window-decorator loaded. It is most extreme with scrolling, mouse-over and window-resizing (in that order). 
Running fullscreen or not, running directly from gdm or from a running x-session make no difference.
Could anyone give me a hint, i'm stuck for now. 
:cry: 

xophos[/QUOTE]

That does looks strange, I have attached my xorg.conf that I use on the M70. This is one I put together in Gentoo and it works lovely in ubuntu as well with a few changes to the fonts area. Since the last update I had to install the compiz-gnome package also to make things happy again. Without further wait here is my conf file.

[HTML]Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Internal Screen" 0 0
	InputDevice    "Mouse" "CorePointer"
	InputDevice    "Touchpad" "AlwaysCore"
	InputDevice    "Keyboard" "CoreKeyboard"
	Option      "BlankTime"    "1"
	Option	    "StandbyTime"  "20"
	Option	    "SuspendTime"  "30"
	Option      "OffTime"      "40"

EndSection

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "glx"
#	Load  "record"
	Load  "extmod"
	Load  "dbe"
#	Load  "xtrap"
	Load  "freetype"
	Load  "type1"
	Load  "synaptics"
#	Load  "GLcore"
         Load  "ddc"
#	Load  "int10"
#	Load  "vbe"
EndSection

#Section "ServerFlags"
#EndSection

Section "InputDevice"
	Identifier  "Keyboard"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse"
	Driver      "mouse"
	Option	    "Protocol"  "ExplorerPS/2"
	Option	    "Device"  "/dev/input/mice"
	Option	    "Emulate3Buttons"  "true"
	Option      "Buttons"  "7"
	Option	    "ZAxisMapping"  "4 5"

EndSection

Section "InputDevice"
	Identifier  "stick"
	Driver	    "synaptics"
        Option      "Protocol"  "event"
	Option      "Device"  "/dev/input/event1"
	Option      "Emulate3Buttons"  "false"
EndSection

Section "InputDevice"
	Identifier  "Touchpad"
	Driver	    "synaptics"
	Option      "Device"  "/dev/input/event2"
	Option      "Protocol"  "auto-dev"
#     Option      "Protocol"  "event"
#     Option      "SendCoreEvents"
	
	#Allows to disable touchpad while typing.
	Option	    "LeftEdge" "130"
	Option	    "RightEdge" "840"
	Option	    "TopEdge"  "130"
	Option      "BottomEdge"  "640"
        Option	    "FingerLow"  "7"
        Option      "FingerHigh"  "8"
	Option      "MaxTapTime"  "180"
        Option      "MaxTapMove"  "110"
	Option      "EmulateMidButtonTime"  "75"
	Option      "VertScrollDelta"  "20"
	Option	    "HorizScrollDelta"  "20"
        Option      "MinSpeed"  "0.65"
	Option      "MaxSpeed"  "1.10"
	Option	    "AccelFactor"  "1.5"
	Option      "EdgeMotionMinSpeed" "200"
	Option      "EdgeMotionMaxSpeed" "200"
	Option      "UpDownScrolling"  "1"
	Option      "CircularScrolling"  "1"
	Option      "CircScrollDelta"  "0.1"
	Option      "CircScrollTrigger"  "2"
	Option      "SHMConfig"  "on"
	Option      "Emulate3Buttons"  "on"
EndSection

Section "Monitor"
	Identifier   "Dell LCD WUXGA"
	VendorName   "Dell"
	ModelName    "WUXGA"
	DisplaySize  507 317
        HorizSync  31.5-90.0
        VertRefresh  60-60
	Option  "DPMS"
	ModeLine     "1280x800" 107.2 1280 1360 1496 1712 800 801 804 835
	ModeLine     "1280x800" 123.4 1280 1368 1504 1728 800 801 804 840
        ModeLine     "1280x800" 147.9 1280 1376 1512 1744 800 801 804 848
        ModeLine     "1680x1050" 147.1 1680 1784 1968 2256 1050 1051 1054 1087
        ModeLine     "1680x1050" 188.1 1680 1800 1984 2288 1050 1051 1054 1096
        ModeLine     "1680x1050" 214.5 1680 1800 1984 2288 1050 1051 1054 1103
        ModeLine     "1680x1050" 256.2 1680 1808 1992 2304 1050 1051 1054 1112
	Modeline     "1920x1200" 193.16 1920 2048 2256 2592 1200 1201 1204 1242  
	+Hsync +Vsync
#	Modeline "1920x1200" 162 1920 1984 2176 2480 1200 1201 1204 1250 +hsync +vsync
EndSection

Section "Device"
	Identifier  "nVIDIA Quadro FX Go 1400"
	Driver	    "nvidia"
#	Driver      "nv"
	VendorName  "nVidia Corporation"
	BoardName   "Quadro FX Go 1400"
	BusID       "PCI:1:0:0"
	VideoRam    262144

	Option      "Coolbits"      "true"
	Option      "HWcursor"      "true"
	Option      "AllowGLXWithComposite"   "true"
	Option      "RenderAccel"   "true"
	Option	    "CursorShadow"  "true"
	Option      "NoLogo"        "true"
#	Option	    "NvAGP"         "2"
	Option      "FlatPanel"     "true"
	Option	    "FlatPanelProperties"  "Scaling = aspect scaled"
	Option	    "UseEdidFreqs"  "true"
	Option	    "DPI"  "96 x 96"
EndSection

Section "Extensions"
	Option     "Composite"      "true"
	Option     "RENDER"         "true"
EndSection

Section "Screen"
	Identifier "Internal Screen"
	Device     "nVIDIA Quadro FX Go 1400"
	Monitor    "Dell LCD WUXGA"

	DefaultDepth 24

	SubSection "Display"
		Depth  24
		Modes  "1920x1200" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"

	EndSubSection
EndSection

Section "DRI"
	Group   "video"
	Mode	0666
EndSection   
[/HTML]

---

### Post by OneSeventeen on 2006-02-20
[QUOTE=cutOff]Are you sure /etc/X11/X points to /usr/bin/Xorg?? Did you remove /etc/X11/X before create the new symlink?

```
ls -l /etc/X11/X
```


I think it's 

apt-get --reinstall install xserver-common[/QUOTE]
ls -l /etc/X11/X shows:
/etc/X11/X -> /usr/bin/Xgl

I did not remove /etc/X11/X before creating the symlink... I just ran:
sudo ln -sf /usr/bin/Xgl /etc/X11/X
As instructed from the [XglHowto](https://wiki.ubuntu.com/XglHowto)

Hindsite, I should have just followed the instructions on this thread and seen if it worked.

So any ways to remedy the situation?  xserver-common "is not available, but is referred to by another package"

Any chance of getting it to work on an onboard graphics chip from a pentium 3?  (TNT2 I think)

---

### Post by astron on 2006-02-20
Thanks, I followed this tutorial and it works.

However, I didn't have gnome-window-decorator.
problem solved with : apt-get install compiz-gnome

Moreover at first, I had plenty of refresh problems, which were solved by switching from 16bpp to 24bpp in xorg.conf

My system : fresh install of Dapper from Flight CD 4
laptop TOSHIBA SATELLITE 2410-514 :
Pentium 4 (2GHz) 256MB RAM with NVIDIA GeForce 4 420 Go (32MB)
I use the nvidia-glx-legacy, since nvidia-glx doesn't work with this card (even though the legacy is said to be for GeForce 2 and below only)

I can play ppracer, but I don't get as many FPS as usual. I get around 30 FPS (Planet Penguin Racer in a 800x600 window) when I am not moving the cube or the windows, less when I am.
The xine-ui interface (not the video window) shows only garbage in XGL, but the xine engine  works quite OK (with xshm or opengl; for some video the XV driver shows only garbage)

Anyone with a similar card that can manage to play a DVD smoothly on XGL without the system responsivity being very low?

---

### Post by funkyou on 2006-02-20
Today i have installed Flight-4 and right after that Xgl and Compiz...

Xgl runs simply (nearly) perfect on my box, no glitches or graphical
bugs :) and the performance is just astonishing, it runs a lot faster
than the standard Xorg with nvidia-driver... I have noticed only once 
a short refresh-problem with firefox by now, but when i moved a 
window over the not-refreshed area, all was good...

Thanks for this howto :KS 

Here are the specs of my box:
Athlon XP 1600+
512MB
nVidia GeForceFX 5200 LE
VIA KT-133a Mobo-Chipset
Fresh Dapper Flight-4 Install

Everything´s running perfect...
So, i just wait to get this under KDE, and I am happy \\:D/

---

### Post by coder_cotton on 2006-02-20
Hey all,

I'm trying to get xgl up on this new 5.1 install, but keeps giving me this message:
> jason@ubuntu:~$ sudo apt-get install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xserver-xgl
jason@ubuntu:~$
I've already uncommented the universe lines in /etc/apt/sources.list, and have apt-get update and apt-get upgrade.

What am I missing here?

New to ubuntu, got tired of waiting for compiles...

---

### Post by pecanov on 2006-02-20
For a long time, compiz was very "unfriendly" to me poor little geforce2 mx.
It always gave a blank screen.
A few days ago (or was it today?) an upgrade of glitz in ubuntu repositories gave me hope that it might just work.
I killed gdm, started xgl from command line, and started compiz and gnome-window-decorator ... my jas hit the floor instantly as I saw that it actually worked.
After playing with it for a while, I adjusted gdm.conf-custom according to the HOWTO in the first post and restarted my computer.

Now it doesn't work anymore :( . Both compiz and gnome-window-decorator start, but no border around the windows is displayed (no shortcuts work also).
No errors in console too.

What happened? Was there a new dapper upgrade (HAL maybe) that affected these two after the restart?

Please ... after seeing it run for once, now I'm even more desperate.

---

### Post by Milamber_Cubed on 2006-02-20
Just to clarify... you CAN get this working on Breezy, just not using the details in this How-To. I can make another thread if people are interested?

---

### Post by Rob2687 on 2006-02-20
Go for it. Or put it in the Breezy how tos. Does it involve changing to the Dapper repos and installing a ton of dependencies?

---

### Post by saads on 2006-02-20
Anyone getting crazy slow video playback when running compiz?  CPU is low when I'm doing cool effects like wobbly and cube - but when I run a video it shoots up to 100% and the computer nearly hangs.

---

### Post by funkyou on 2006-02-20
Well, before the update i did just some minutes ago, everything
went fine with compiz/xgl...

But now compiz claims the it cannot find libgconf.so and the
gnome-window-decorator can also not be found... The FX are
working even, but a lot slower than before the update...

Just so you know, better don´t update ;) 
... If you want to keep your eye-candy...

---

### Post by vendetta red on 2006-02-20
[QUOTE=funkyou]Well, before the update i did just some minutes ago, everything
went fine with compiz/xgl...

But now compiz claims the it cannot find libgconf.so and the
gnome-window-decorator can also not be found... The FX are
working even, but a lot slower than before the update...

Just so you know, better don´t update ;) 
... If you want to keep your eye-candy...[/QUOTE]

sudo apt-get install compiz-gnome

Ctrl + Alt + Backspace

Problem solved.

---

### Post by pecanov on 2006-02-20
[QUOTE=saads]Anyone getting crazy slow video playback when running compiz?  CPU is low when I'm doing cool effects like wobbly and cube - but when I run a video it shoots up to 100% and the computer nearly hangs.[/QUOTE]

Have you tried using gl2 for video playback?
That solved the issue with video playback on xgl for me. Now it's very smooth. Too bad I can't do that with gstreamer, but I use mplayer anyway.

---

### Post by pecanov on 2006-02-20
[QUOTE=vendetta red]sudo apt-get install compiz-gnome

Ctrl + Alt + Backspace

Problem solved.[/QUOTE]

No, actually it isn't.
I have compiz-gnome installed.

---

### Post by raha on 2006-02-20
[QUOTE=funkyou]Today i have installed Flight-4 and right after that Xgl and Compiz...

Xgl runs simply (nearly) perfect on my box, no glitches or graphical
bugs :) and the performance is just astonishing, it runs a lot faster
than the standard Xorg with nvidia-driver... I have noticed only once 
a short refresh-problem with firefox by now, but when i moved a 
window over the not-refreshed area, all was good...

Thanks for this howto :KS 

Here are the specs of my box:
Athlon XP 1600+
512MB
nVidia GeForceFX 5200 LE
VIA KT-133a Mobo-Chipset
Fresh Dapper Flight-4 Install

Everything´s running perfect...
So, i just wait to get this under KDE, and I am happy \\:D/[/QUOTE]

Hi, I have very similare hardware to yours.
But I tried the same Howto on Flight-4 and it didnt work and crashed. I think I need to change something in howto to get it working on Flight-4. I tried the same howto  with Fligh3 and everything was fine but not with Flight4.

Any help or suggestions ?

---

### Post by vendetta red on 2006-02-20
[QUOTE=pecanov]No, actually it isn't.
I have compiz-gnome installed.[/QUOTE]

I was responding to funkyou, are you having the same problem? If so then there must have been another update since I left, cause I just got the updates a couple hours ago and compiz-gnome was the fix then....

---

### Post by funkyou on 2006-02-20
**vendetta red:**
> 
sudo apt-get install compiz-gnome

Ctrl + Alt + Backspace

Problem solved.

THX :) that solved it for me...



**raha:**
I don't know... I followed the howto and it just worked out of the box...
Do you tried to start it without GDM from console? When the Xgl-Server
starts this way, you could start compiz manually and look for errors...

---

### Post by pecanov on 2006-02-20
[QUOTE=vendetta red]I was responding to funkyou, are you having the same problem? If so then there must have been another update since I left, cause I just got the updates a couple hours ago and compiz-gnome was the fix then....[/QUOTE]

Sorry ... just very anxious for an answer

---

### Post by poofyhairguy on 2006-02-20
Fixed guide.

---

### Post by cutOff on 2006-02-20
[QUOTE=Milamber_Cubed]Just to clarify... you CAN get this working on Breezy, just not using the details in this How-To. I can make another thread if people are interested?[/QUOTE]
I agree with you.

---

### Post by raha on 2006-02-20
I tried this and my Nvidia driver didnt work after that on Flight4 but worked on Flight3:

sudo apt-get install nvidia-kernel-common nvidia-glx

and after that when I go to : sudo gedit /etc/X11/xorg.conf there is no "GLcore" so I cant comment it out.

this is when I ran that line again:

> sudo apt-get install nvidia-kernel-common nvidia-glx Password:
Reading package lists... Done
Building dependency tree... Done
nvidia-kernel-common is already the newest version.
nvidia-glx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


---

### Post by Milamber_Cubed on 2006-02-20
[QUOTE=cutOff]I agree with you.[/QUOTE]

My "guide" for getting Xgl working under Breezy is here [http://www.ubuntuforums.org/showthread.php?p=755176#post755176](http://www.ubuntuforums.org/showthread.php?p=755176#post755176)

Based heavily on this one - I hope you don't mind PHG! :D

---

### Post by funkyou on 2006-02-20
Has anyone experienced this too?:
Since the last update, and installing compiz-gnome, i can
no longer use the exposè (F12) and the task-switcher (ALT-TAB),
they just don´t work...

I have already tried to use other keys for this since i thought a short
time after noticing this, that maybe my keyboard is broken a bit ;) but 
re-assignment of keys was no solution, and my keyboard isn´t broken :) 
btw: i have already assigned the correct xmodmap...

when i open a terminal and press F12 inside it, i just get a beep out
of my speakers and a "~" written... quite strange...

---

### Post by tr4veler on 2006-02-20
[QUOTE=poofyhairguy]**BIG EDIT: WORST BUGS ARE GONE!**

You must compile the newest CVS version of glitz to get this to work with Nvidia cards that lack Pixel Shaders (aka anything older than a 5200 FX). Hopefully this will be updated in the repository soon.
[/quote]

My GF3 works? with the compiz 0.0.2 .deb (which I'm not sure I needed) linked in this thread and everything else out of dapper.

I haven't figgured out what settings will get me playing video properly (either good audio sync and choppy video or audio way way out of sync) and resize is very, very slow & laggy.

I'm guessing that my video issues are processor/bus related (AXP 1500 100mhz bus).

There was a question earlier about thefuture erroring out no matter how often it was run.  Rebooting fixed that for me.  At first I though that because I was allready running nividia biniary driver a ctrl-alt-backspace would load the rest of the changes, It apparently doesn't.

---

### Post by BetaguyGZT on 2006-02-20
May we have the commandline entry to compile glitz from CVS? Please?? Pretty please?? :D

Some of us don't know how exactly that's done. (*me...**cough**cough*)

Thanks.

---

### Post by funkyou on 2006-02-20
> 
Has anyone experienced this too?:
Since the last update, and installing compiz-gnome, i can
no longer use the exposè (F12) and the task-switcher (ALT-TAB),
they just don´t work...

I have already tried to use other keys for this since i thought a short
time after noticing this, that maybe my keyboard is broken a bit but
re-assignment of keys was no solution, and my keyboard isn´t broken
btw: i have already assigned the correct xmodmap...

when i open a terminal and press F12 inside it, i just get a beep out
of my speakers and a "~" written... quite strange...


Ok, i have tracked it down... I don´t know why this happens, but after
killing the Xserver or a reboot it works again...

---

### Post by cutOff on 2006-02-20
[QUOTE=Milamber_Cubed]My "guide" for getting Xgl working under Breezy is here [http://www.ubuntuforums.org/showthread.php?p=755176#post755176](http://www.ubuntuforums.org/showthread.php?p=755176#post755176)

Based heavily on this one - I hope you don't mind PHG! :D[/QUOTE]
Thanks a lot-

---

### Post by MetalMusicAddict on 2006-02-20
**[SIZE="6"]THIS IS THE COOLEST THING EVER!!![/SIZE]**

I have a couple of hick-ups but nothing major. I want to show everyone I know this. I almost cant wait till Dapper to have this as my full-time desktop.

Thanx a **[SIZE="6"]TON[/SIZE]** Poofyhairguy. \m/ This whole community benifits from the work you[SIZE="1"] [COLOR="Silver"](and the Novel guys)[/COLOR][/SIZE] do. :)

---

### Post by hectorC on 2006-02-20
> Thanks a lot for this guide! It's working for me with almost no problems using my nvidia 6600. The only strange (maybe not) thing that I found is that there are almost no options in the nvdia-settings control panel! There is only one page with very simple options related only to the panel itself... beside that everything else is gone. At the console I get this:

~$ nvidia-settings

ERROR: NV-CONTROL extension not found on this Display.


(nvidia-settings:5303): Gdk-CRITICAL **: gdk_window_invalidate_rect: assertion `window != NULL' failed

I realized about this when I tried to run a video game and tried to set the OpenGL options.

Is this part of the development process?

thanks for any help!

Hector.

I posted this message a day ago and I was wondering if any of you using XGL and a nvdia card is not experiencing this problem. Do you have all the options available in the nvidia-settings control panel (OpenGL, Antialiasing etc)?

Thank you,


Hector.

---

### Post by funkyou on 2006-02-20
**hectorC:**
> I posted this message a day ago and I was wondering if any of you using XGL and a nvdia card is not experiencing this problem. Do you have all the options available in the nvidia-settings control panel (OpenGL, Antialiasing etc)?

Thank you,

I get the same error and the same very simple options here...

---

### Post by mstlyevil on 2006-02-20
Just created a new partiton to install Dapper on to try this out. All I can say is **WOW**! This s**t rocks. I now will have to buy a regular laser mouse with a scroll wheel so I can play with the transparencies. This has Kwin beat all to hades and back. Thank you Poofy for another great guide.

---

### Post by poofyhairguy on 2006-02-20
[QUOTE=Milamber_Cubed]My "guide" for getting Xgl working under Breezy is here [http://www.ubuntuforums.org/showthread.php?p=755176#post755176](http://www.ubuntuforums.org/showthread.php?p=755176#post755176)

Based heavily on this one - I hope you don't mind PHG! :D[/QUOTE]

No problem. I personally won't tell people to do it, but glad that niches are being filled.

---

### Post by poofyhairguy on 2006-02-20
[QUOTE=MetalMusicAddict]**[SIZE="6"]THIS IS THE COOLEST THING EVER!!![/SIZE]**

I have a couple of hick-ups but nothing major. I want to show everyone I know this. I almost cant wait till Dapper to have this as my full-time desktop.

Thanx a **[SIZE="6"]TON[/SIZE]** Poofyhairguy. \m/ This whole community benifits from the work you[SIZE="1"] [COLOR="Silver"](and the Novel guys)[/COLOR][/SIZE] do. :)[/QUOTE]


Glad you like it!

---

### Post by MetalMusicAddict on 2006-02-20
[QUOTE=hectorC]I posted this message a day ago and I was wondering if any of you using XGL and a nvdia card is not experiencing this problem. Do you have all the options available in the **nvidia-settings** control panel (OpenGL, Antialiasing etc)?

Thank you,


Hector.[/QUOTE]
I couldnt install nvidia-settings. It (apt) wanted to uninstall nvidia-glx.

What should I do?

---

### Post by Rob2687 on 2006-02-20
Cry in the corner.


Or..... Wait until somebody fixes it. I think it's been like that for a while now.

---

### Post by RAOF on 2006-02-20
I seem to recall that nvidia-settings is now *included* in nvidia-glx, which is why it conflicts.  If you've got nvidia-glx installed, you should be able to run nvidia-settings.  Unless that plays badly with Xgl - all sorts of things crash my Xgl server ;)

---

### Post by thumbsoup on 2006-02-20
I have the same problem as jlas9 did yesterday (prior post).  

When I reboot, I get an X error message:

Couldn't open RGB_DB '/usr/share/X11/rgb' 

Any ideas on how to solve this?

*********************
From prior post by jlas9:

 Default  Re: XGL Install and General Tips For Gnome and Nvidia
Hi.
I follow your explanations poofyhairguy, but when gdm are trying get up again, after editing /etc/gdm/gdm.conf-custom and /etc/X11/xorg.conf, i get this error:

Couldn't open RGB_DB '/usr/share/X11/rgb'

Could this be cos i don't have the accelerated 'nvidia' driver installed and i use the default 'nv' or this is not related?.

---

### Post by opera118 on 2006-02-20
[QUOTE=scaine]Jeez - first it's "Broken to it's bones", then after mrogers' comment you admit it works for a lot of people?  So which is it?  You should decide before you slag people off for trying to help.[/QUOTE]

Precisely so it is. This is a major problem with nvidia, and I'm thinking of buying a non-linux supported gfx card for my next machine (that I will not use any gfx-stuff on) just for the sake of it.
I've had these problems since my TNT. The oldest drivers worked perfectly, but as the driver version number increased, the number of problems increased. It seems nvidia only "supports" the cards they like, usually the newer cards. They "depricate" old cards as they like, and the implementation of new features is very unprofessional. They could need a lesson from the kernel hackers.
For instance, the new EDID checks they do - probably works good for a lot of people, but for those it doesn't work for, for them it's not just a bug, for them X won't start.
I'm not satisfied with nvidias linux support, the driver feels like a constant beta with a build-counter just increasing. I've paid for two nvidia cards, I expect a driver version 1.0 that supports _everything_ in the chips (at least that they support on windows). But that simply won't happen.
This is not the right forum to bash nvidia over their lousy customer relations, but the fact remains that new nvidia drivers come with new nice features for a lot of people and disastrous crashes for others. People need to know this.
"Works fine for me" isn't really fitting in I think.

[QUOTE=scaine]Good luck getting it going though.  This Compiz stuff is mind blowing.[/QUOTE]

It worked on saturday with a twisted resolution with some weird combo of X 6.9 and 7.0 with ubuntu glx and nvidia 7676. Don't want to go there again. But I know how it feels. It's sure great.
Novell and the community is working hard, I appreciate it highly. It's just funny, I never paid them. I paid nvidia, and they ain't doing jack sh*t. Ironic ;)

---

### Post by RAOF on 2006-02-20
[QUOTE=thumbsoup]I have the same problem as jlas9 did yesterday (prior post).  

When I reboot, I get an X error message:

Couldn't open RGB_DB '/usr/share/X11/rgb' 

Any ideas on how to solve this?

*********************
From prior post by jlas9:

 Default  Re: XGL Install and General Tips For Gnome and Nvidia
Hi.
I follow your explanations poofyhairguy, but when gdm are trying get up again, after editing /etc/gdm/gdm.conf-custom and /etc/X11/xorg.conf, i get this error:

Couldn't open RGB_DB '/usr/share/X11/rgb'

Could this be cos i don't have the accelerated 'nvidia' driver installed and i use the default 'nv' or this is not related?.[/QUOTE]
That error is becuase rgb.txt is actually in /usr/lib/X11/rgb.txt.  If you symlink /usr/share/X11/rgb.txt to /usr/lib/X11/rgb.txt, the error goes away and emacs works :)

Secondly, Xgl **surely** won't work on the "nv" drivers - they don't support 3d acceleration, which is the whole point of Xgl!

---

### Post by romulognomo on 2006-02-20
It was working perfectly but slow, so there was an update on compiz and glitz and then it is really really faster, but the window decoration has gone. Anyone with  the same problem? Can you help?

---

### Post by pecanov on 2006-02-21
[QUOTE=romulognomo]It was working perfectly but slow, so there was an update on compiz and glitz and then it is really really faster, but the window decoration has gone. Anyone with  the same problem? Can you help?[/QUOTE]

Yep ... I have the same problem. Already made a post.
No reply, though.

---

### Post by opera118 on 2006-02-21
[QUOTE=romulognomo]It was working perfectly but slow, so there was an update on compiz and glitz and then it is really really faster, but the window decoration has gone. Anyone with  the same problem? Can you help?[/QUOTE]

Are you starting thefuture from a terminal? If not, do so. If so, do you get an error message? Not that I can help you as I got more basic problems, but it might help others to solve it.

---

### Post by vendetta red on 2006-02-21
after the last update, you need to install compiz-gnome because gnome-window-decorator is no longer included in just compiz. It's been split into compiz-gnome and compiz-kde. I'm not sure how many times this has been posted, I know I've typed it at least 3 times today. Please look through previous posts to see if your problem has already been solved.

---

### Post by tr4veler on 2006-02-21
[QUOTE=tr4veler]My GF3 works? with the compiz 0.0.2 .deb (which I'm not sure I needed) linked in this thread and everything else out of dapper.[/QUOTE]

don't use that .deb or uninstall it and reinstall ubunut's.  It version isn't right so apt won't upgrade it in favor of the newer ubuntu packages (compiz-gnome)

---

### Post by pecanov on 2006-02-21
[QUOTE=vendetta red]after the last update, you need to install compiz-gnome because gnome-window-decorator is no longer included in just compiz. It's been split into compiz-gnome and compiz-kde. I'm not sure how many times this has been posted, I know I've typed it at least 3 times today. Please look through previous posts to see if your problem has already been solved.[/QUOTE]

And this is the second time I post this:
I have compiz-gnome as soon as it was uploaded in repository and the problem is still present.
The problem is there is no error message in console, everything starts, but gnome-window-decorator just hangs there without drawing any window decorations.
The only thing that is actually changed is the desktop switcher applet on gnome panel, but I guess that is changed because of compiz.

---

### Post by vendetta red on 2006-02-21
yes, well unfortunately I don't know why it isn't working for you, when it has fixed it for most people. I just wanted romulognomo to see it and see if it worked for him, and was simply asking him to look through past questions/solutions and apply them before posting.

---

### Post by KageKeeper on 2006-02-21
Ok..this may not be the proper thread for this question, so please forgive me....

I have, as stated above, Xgl working grand.

However, I am an avid player of nwn online and it seems that Xgl has an issue drawing some of the custom content the world I play in uses.

I have verified this by disabling Xgl and retrying.

So, my problem is this. If I do that (by commenting out the gdm.conf-custom) file, I get absolutely no title bars on my windows at all. This makes life somewhat difficult.

So, anyone have a workaround for:

A) getting Xgl and nwn to play nice

or

B) getting my title bars back when I disable Xgl?

Thanks!

EDIT: Would installing older drivers be helpful? I have a 6200, so the newest should be fine. Comments?

---

### Post by opera118 on 2006-02-21
[QUOTE=KageKeeper]I have, as stated above, Xgl working grand.

...

So, anyone have a workaround for:

A) getting Xgl and nwn to play nice

[/QUOTE]

As people, have stated above, Xgl is rather unstable, it's new work, it's not supposed to work well, dapper is not complete yet, nvidia drivers xgl support is not really good at all yet, and so forth.
It will not work yet. So you have to choose between gaming and wobbling windows.

[QUOTE=KageKeeper]

B) getting my title bars back when I disable Xgl?

[/QUOTE]

As people, have stated above, metacity --replace

---

### Post by dr_kabuto on 2006-02-21
Hi everyone,
today with the latest updates i finally got this xgl thing working (I have a old NVidia Quadro4). As result of this, playing videos is sloow (both with totem-gstreamer and xine), and the desktop switcher show only 1 desktop, even configuring the applet to show more. Running metacity i have my all 4 desktop.

---

### Post by aamukahvi on 2006-02-21
Hey. About nvidia-settings... I can start it but there are only options concerning the nvidia-settings program, not the graphical options. When I quit it, i get this in the console:
```
$ nvidia-settings

ERROR: NV-CONTROL extension not found on this Display.


(nvidia-settings:5642): Gdk-CRITICAL **: gdk_window_invalidate_rect: assertion `window != NULL' failed
```
Do I need to enable NV-CONTROL in xorg.conf or something? And how? Thanks :)

---

### Post by vixx on 2006-02-21
Ok, I've managed to get xgl working on my old GF 420Mx card. It's working great except moving windows is kinda slow (well, it's acctualy fast when I drag windows around, but when I stop dragging window then it goes like a slow motion movie, you know that rubber effect?) I think it's wobbly effect, right? Is there any "hack" to make wobbly effects run smoother, except disabling it or buying new card? :)

---

### Post by risbac on 2006-02-21
[QUOTE=vixx]Is there any "hack" to make wobbly effects run smoother, except disabling it or buying new card? :)[/QUOTE]

Yes, check post 1, you can change the refresh rate from what you have to 60. I was at 75 or 85, can't remember, and the change to 60 indeed helped a lot. Now it's almost as smooth as it could be.

---

### Post by vixx on 2006-02-21
[QUOTE=risbac]Yes, check post 1, you can change the refresh rate from what you have to 60. I was at 75 or 85, can't remember, and the change to 60 indeed helped a lot. Now it's almost as smooth as it could be.[/QUOTE]


Ok, thanks, however my eyes will bleed on that refresh rate. :)

---

### Post by aamukahvi on 2006-02-21
[QUOTE=vixx]Ok, thanks, however my eyes will bleed on that refresh rate. :)[/QUOTE]
It doesn't change (I think) the refresh rate of your monitor, hence no probs. :)

---

### Post by risbac on 2006-02-21
For your information, the xmodmap command didn't work for me on my french keyboard:

before, I was not able to type @ or € anymore, which was quite annoying (especially for the first one...). Not to say about [, #, { which can be useful also for programming : )

So I tried the xmodmap command with the "fr" code, it solved all the keyboard problems. But then F12 didn't expose anything, and Ctrl + Alt + Right/Left didn't rotate anything anymore. Arghhhhh gimme back my compiz toys!

So finally, I found this solution on the gentoo Xgl Wiki (good address also, recommended):

setxkbmap -model pc105 -layout dk -variant basic

dk being for denmark, I let you change to yours. 
Now I can type @ as you can see, F12 is back, my cube rotates like hell. One more problem solved. Maybe it would be useful to include this command as an alternative in the first post, as I was not the only one with this problem I think.

---

### Post by chaumurky on 2006-02-21
So far X bombs out with the error "Error opening security policy file '/etc/xserver/SecurityPolicy'". The only 'SecurityPolicy' I see is /usr/lib/xserver/SecurityPolicy. Any pointers?


EDIT: Ahh, I had 'TwinView' enabled.

[SIZE=4]EDIT: OMG it's really REAL!! IT WORKS!!! [SIZE=2]Only on one monitor thoughbut I knew that's would be the trade off. I hope they fix that really soon!!![/SIZE][/SIZE]

---

### Post by xophos on 2006-02-21
[QUOTE=Ainvar]That does looks strange, I have attached my xorg.conf that I use on the M70. This is one I put together in Gentoo and it works lovely in ubuntu as well with a few changes to the fonts area. Since the last update I had to install the compiz-gnome package also to make things happy again. Without further wait here is my conf file.
--snip--
[/QUOTE]
Thank you oh so very much, it works like a charm with your config :-D
I have no idea what was wrong with mine.

Edit:
    One thing is still not perfect: under Xgl (i start it directly from gdm now) glxinfo reports "Direct rendering: No" with no error or warning related to it in the logfiles and any opengl program i run crashes X.
    If i just have to wait for better packages, that's ok, but if there is a workaround i really would like to know.

---

### Post by neocsr on 2006-02-21
[QUOTE=Milamber_Cubed]This is what I did and it worked - I plugins from the dapper debs (I guess you can find this on the repositories somehow?) into the compiz libs folder. libmenu is no longer required according to the CVS notes, so I think you can safely ignore that message.

I will attach the contents of my breezy /usr/lib/compiz folder for you - if you trust me ;) you can use that. You will need to add cube, rotate and zoom  (in that order) to the list of loaded plugins in gconf-editor after you put these in though - otherwise it will not try to load them. So in short:

1. copy libs from tar.gz into /usr/lib/compiz
2. run gconf-editor and add cub,rotate,zoom to list of loaded pluigins
3. run "thefuture" again
4. have fun!

Hope that helps[/QUOTE]

Bad news... It doesnt' work for me.... I spent much time trying... after copying the files the only message I get is:

/opt/fdo/bin/compiz: [COLOR="Red"]GLX_EXT_texture_from_pixmap is missing[/COLOR]
/opt/fdo/bin/compiz: Failed to manage screen: 0
/opt/fdo/bin/compiz: No managable screens found on display :0
:-? 
So... there's no choice...  I will move to Dapper... thnx anyway...

---

### Post by marianoi on 2006-02-21
HI Guys,

This is really COOOOLLLL!

The only thing I cannot find is how to make windows transparent. Does anyone know how to do it?

Thanks, :)

---

### Post by risbac on 2006-02-21
[QUOTE=marianoi] Does anyone know how to do it?[/QUOTE]

Yes, you need to add a plugin. You will find it in this forum, search for a topic with "compiz" and "opacity", you should find it. It's an "howto".

---

### Post by b0rsten on 2006-02-21
everything worked fine for me...
but the key-commands don't work...

no alt + ctr +  left/rgiht
no alt + tab

etc.

---

### Post by Rob2687 on 2006-02-21
About this whole GLX_EXT_texture_from_pixmap thing.
There where some busted symlinks in /usr/lib/nvidia with the libGL files so followed them around with the ls -l command and fixed the broken symlink. 
I pointed LD_LIBRARY_PATH to /usr/lib/nvidia and now compiz starts succesfully everytime.
No need to keep entering the command until it finally works.

---

### Post by risbac on 2006-02-21
> everything worked fine for me...
but the key-commands don't work...


Did you do a xmodmap to set your keyboard?

---

### Post by Denamite on 2006-02-21
Seems like the latest apt-get upgrade changed 'gnome-window-decorator' to 'gnome-wm' and substituting 'gnome-window-decorator' with 'gnome-wm' in /usr/bin/thefuture doesn't seem to work, also get complains about unable to load plugin libgconf.so

Everything worked OK before the apt-get upgrade tough.

X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  148 (GLX)
  Minor opcode of failed request:  2 (X_GLXRenderLarge)
  Serial number of failed request:  89
  Current serial number in output stream:  90
Window manager warning: Screen 0 on display ":0" already has a window manager; try using the --replace option to replace the current window manager.
compiz.real: Couldn't load plugin 'libgconf.so'
compiz.real: dlsym: /usr/lib/libmenu.so: undefined symbol: getCompPluginInfo
compiz.real: Failed to lookup getCompPluginInfo in 'libmenu.so' plugin

---

### Post by b0rsten on 2006-02-21
[QUOTE=risbac]Did you do a xmodmap to set your keyboard?[/QUOTE]

yes...
but when gnome loads a window pops up with an "error", that gnome is using an other keyboard-layout than my xorg.conf... maybe this is the error?

---

### Post by risbac on 2006-02-21
> but when gnome loads a window pops up with an "error", that gnome is using an other keyboard-layout than my xorg.conf... maybe this is the error?

Mmm i don't think so. I posted a message sooner today about this keyboard problem. I didn't use xmodmap, it's not working, so I used another command. Maybe you should try it?

---

### Post by b0rsten on 2006-02-21
[QUOTE=risbac]Mmm i don't think so. I posted a message sooner today about this keyboard problem. I didn't use xmodmap, it's not working, so I used another command. Maybe you should try it?[/QUOTE]

```
setxkbmap -model pc105 -layout de -variant basic
``` worked fine for me :) thanks a lot...

---

### Post by Elcoco on 2006-02-21
i have the same problem as denamite, the new upgrades killed compiz. any idea on how to fix it?

---

### Post by risbac on 2006-02-21
> any idea on how to fix it?

Wait maybe ? : ) I see more and more new packaging arriving at each apt-get update. It's probably safer to wait until all the key packages for Xgl are updated to see if some modifications are needed?

---

### Post by ethridgt on 2006-02-21
Hey Borston,

You said:
> everything worked fine for me...
but the key-commands don't work...

no alt + ctr + left/rgiht
no alt + tab

etc.

I had the exact same problem.  It was because gconf was ignoring plugins passed to it on the command line.  See: [http://gentoo-wiki.com/XGL#Plugins_loading_order](http://gentoo-wiki.com/XGL#Plugins_loading_order)

So what I did was run gconf-editor.  Then navigate to apps/compiz/general/allscreens/options and update the active plugins to the proper order.

    The current order in which the plugins should be loaded: 
    gconf,decoration,wobbly,fade,minimize,cube,rotate,zoom,scale,move,resize,place,switcher

Hope that helps.

-- tale

---

### Post by bites on 2006-02-21
Hi!

I've played around with xgl and compiz for a few days now and I've only run into two oddities:
- everything works, but I can't rotate the cube manually (alt+ctrl+leftclick)
- the focus is out of order when I rotate.  The window which had the focus is at the bottom (still has focus, according to the titlebar).  When I click on the focused window, it pops up again.  When I click it again, one of the non-focused windows steals the focus.

I'm using the nvidia drivers and xgl and compiz packages from the repository.  Anyone else who has had these problems?

---

### Post by drfoz on 2006-02-21
when i install glx compiz it kills nvidia setup. i cant play ut2004 after its installed and that aint cool. also it changes nvidia-settings and i cant see any of the options thats there before i install xgl. i followed the how-to to the T and it worked great but seems to have messed up nvidia's drivers pretty bad. anyone else had that problem?  i have nvidia 7800

---

### Post by UbuntuUX on 2006-02-21
[QUOTE=drfoz]when i install glx compiz it kills nvidia setup. i cant play ut2004 after its installed and that aint cool. also it changes nvidia-settings and i cant see any of the options thats there before i install xgl. i followed the how-to to the T and it worked great but seems to have messed up nvidia's drivers pretty bad. anyone else had that problem?  i have nvidia 7800[/QUOTE]

OpenGL games seem to be a no,no with Xgl at the moment, UT dont play for me and Quake3 plays the demo but playing the game is unplayable. I guess DavidR will work out these issue since it's experimental. it's a case of dropping out Xgl and playing games in Xorg for now.

---

### Post by Paulus on 2006-02-21
did anyone notice the compiz-gnome and compiz-kde packages?  As you'd expect you have to install them to get gnome-window-decoration and likewise for kde, might explain any problems!  

btw anyone have any idea whether nvidia are working on a accelerated xgl driver?

---

### Post by UbuntuUX on 2006-02-21
[QUOTE=Paulus]did anyone notice the compiz-gnome and compiz-kde packages?  As you'd expect you have to install them to get gnome-window-decoration and likewise for kde, might explain any problems!  

btw anyone have any idea whether nvidia are working on a accelerated xgl driver?[/QUOTE]

Xgl is accelerated because it's OpenGL and "GLX_EXT_texture_from_pixmap" feature in comiz will be in the next driver release according to NVIDIA. It's more Xgl, compiz and glitz that need to speed improvements.

---

### Post by denisesballs on 2006-02-21
Anyone know why my alt + whatever isnt working? I used the right keyboard i think, im us. I can't even do alt+f2 to run command, but compiz and xgl both work. Also, how do you change the transparencies?

---

### Post by Havoc on 2006-02-21
I love you and want to bear your child, Poofy. :D

---

### Post by aamukahvi on 2006-02-21
[QUOTE=Havoc]I love you and want to bear your child, Poofy. :D[/QUOTE]
Whoa

---

### Post by Milamber_Cubed on 2006-02-21
[QUOTE=aamukahvi]Whoa[/QUOTE]
Yeah, what he said ^^^^ :shock:

---

### Post by Havoc on 2006-02-21
And yours, Milamber_Cubed, for making XGL work under Breezy.

GET IN LINE! ;)

---

### Post by hectorC on 2006-02-21
[QUOTE=drfoz]when i install glx compiz it kills nvidia setup. i cant play ut2004 after its installed and that aint cool. also it changes nvidia-settings and i cant see any of the options thats there before i install xgl. i followed the how-to to the T and it worked great but seems to have messed up nvidia's drivers pretty bad. anyone else had that problem?  i have nvidia 7800[/QUOTE]

I been complaining about the same problem (nvidia-settings showing no options), and as you can see in my previous posts, there has been no answer. I sent a PM to Poofyhairguy but I haven't got any reply. It seems to be a problem related to the XGL configuration and nvidia-settings not finding the display. If I switch to Xorg the problem disappears. I was trying to play TC-Elite under XGL and it won't run fullscreen and there is a lot of shading missing.

Hector

---

### Post by nissem on 2006-02-21
HI!
Sorry for such a noob question. I follow the guide but when type in the terminal > sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome
I get that the package couldn't be found. I have done apt-get update and I suspekt I need some development respitories? I'm rather new to Ubunto and I've just installed 5.10.

---

### Post by bites on 2006-02-21
You'll have to enable the Dapper repositories.  You can find more about that, right [here](http://www.ubuntuforums.org/showthread.php?t=134232).

---

### Post by teppic on 2006-02-21
[QUOTE=hectorC]I been complaining about the same problem (nvidia-settings showing no options), and as you can see in my previous posts, there has been no answer. I sent a PM to Poofyhairguy but I haven't got any reply. It seems to be a problem related to the XGL configuration and nvidia-settings not finding the display. If I switch to Xorg the problem disappears. I was trying to play TC-Elite under XGL and it won't run fullscreen and there is a lot of shading missing.

Hector[/QUOTE]

Xgl runs on top of X.Org. The Xgl server is not supported directly by the nvidia drivers.

This is pre-alpha software. You can't expect everything to work yet, it's not even finished.

---

### Post by hectorC on 2006-02-21
[QUOTE=nissem]HI!
Sorry for such a noob question. I follow the guide but when type in the terminal 
I get that the package couldn't be found. I have done apt-get update and I suspekt I need some development respitories? I'm rather new to Ubunto and I've just installed 5.10.[/QUOTE]

Be careful! This guide is only for Dapper (the next version of Ubuntu, still under development). If you want to make XGL work under Breezy (5.10) then you could follow [this guide]("http://www.ubuntuforums.org/showthread.php?t=133772&highlight=breezy+xgl") but it might give you some problems.

Hector.

---

### Post by hectorC on 2006-02-21
[QUOTE=teppic]Xgl runs on top of X.Org. The Xgl server is not supported directly by the nvidia drivers.

This is pre-alpha software. You can't expect everything to work yet, it's not even finished.[/QUOTE]

Thanks for the explanation. I know it is still under development and I don't expect it to work 100%. I just wanted to find out if someone got a solution (while I'm trying to find it).

Hector.

---

### Post by jdong on 2006-02-21
[QUOTE=hectorC]I been complaining about the same problem (nvidia-settings showing no options), and as you can see in my previous posts, there has been no answer. I sent a PM to Poofyhairguy but I haven't got any reply. It seems to be a problem related to the XGL configuration and nvidia-settings not finding the display. If I switch to Xorg the problem disappears. I was trying to play TC-Elite under XGL and it won't run fullscreen and there is a lot of shading missing.

Hector[/QUOTE]

Umm, I have reinstalled a bunch of kernel packages and nvidia-glx/nvidia-kernel-common packages, and it started working again.

But confirmed; after installing either mesa or glitz, nvidia GLX registration dies and NVidia users lose GLX support. That means VERY painful video  performance for me :)

---

### Post by Icetec on 2006-02-21
$ compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

This is the error I get aswell. I've read all the 46 pages of this thread and still haven't found an answer that solves it. No matter how many times I run thetruth I still get this error, and the titlebars of the windows disappear and I can't switch between which windows are on top. I have followed the guide on the first page on Ubuntu 6.04 with a 6800LE. I would be happy if anyone knew a sollution as the only reason I installed Linux again was to test this :)

---

### Post by Rob2687 on 2006-02-21
Have you guys tried running games on this?

Quake 3 runs fine but there are some textures missing.

---

### Post by mstlyevil on 2006-02-21
The beautiful thing about compiz is that all you have to do is reboot and not start it and then play your games. It should cause no problems as long as you do not execute it before playing.

---

### Post by nuzzy on 2006-02-21
I'm getting the same error as Denemite mentioned on page 45:

> compiz.real: dlsym: /usr/lib/libmenu.so: undefined symbol: getCompPluginInfo
compiz.real: Failed to lookup getCompPluginInfo in 'libmenu.so' plugin

Any ideas how to fix this?

---

### Post by chanders on 2006-02-21
[QUOTE=Icetec]$ compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

This is the error I get aswell. I've read all the 46 pages of this thread and still haven't found an answer that solves it. No matter how many times I run thetruth I still get this error, and the titlebars of the windows disappear and I can't switch between which windows are on top. I have followed the guide on the first page on Ubuntu 6.04 with a 6800LE. I would be happy if anyone knew a sollution as the only reason I installed Linux again was to test this :)[/QUOTE]

OK... quick fix... if this doesnt work nothing will :-D 

1. Install Dapper (Flight 3 or 4)
2. Enable all the repositories
3. Do a dist-update
4. Do a dist-upgrade. Reboot. Install your Nvidia Driver. Make changes to your xorg.conf
5. Install from the repository
  (i) compiz
  (ii) compiz-gnome
  (iii) mesa
  (iv) glitz
  (v) all the rest from this guide...
6. Reboot
7. Make all changes as per the guide to start Xgl
8. Make the script to run compiz...
9. Run the script...

Let us know the errors that show up..

---

### Post by Brain_Recall on 2006-02-21
Hello everyone.
I just wanted to say how estatic I am over this. But before I go into my little saga, let me explain some of my undertakings with Linux.
Honestly, almost every previous version (amoung different distributions) of GNU/Linux has practically let me down. Unsupported hardware, some obscure unfixable error, or major inconviences kept pushing me away.

A few days ago, I saw the large XGL demo video, and I knew I had to have it. To my supprise, somehow I stubled across this forum post. I immediately grabbed a DapperFlight4 ISO and burned away. I wasn't going to even try to install this on my main box (Athlon 64 X2, Geforce 7800GT, with the big Linux-killer nForce4 RAID 0 array), so I grabbed my Dell Inspirion 5150 laptop. I used PartionMagic 8 and opened up a 8GB courner and started to install. With a few minor confusions of the installer, Ubuntu DapperFlight4 was up and running. Supprisingly, it was up and running without a single complaint, something I never experienced before (and this from a beta release!).

I followed the guide, and being new to the apt-get experience, I didn't realize the Dapper universe repositories were commented out. I got everyhting going as far as I could tell, but, a reboot showed I had killed X. No worries, so I tried the ever-present option, format and reinstall.

I followed the guide again, and it works wonderfuly! I had some problems with screen corruption like others in this thread, and like others manually edition xorg.conf to set the color bit-depth to 24 bits fixed it perfectly.

I would like to follow this up by saying it's absolutely astounding to me that an beta-release distro is running a experimental windower as smoothly and as refined as Ubuntu is running XGL.

My hats go off to you all. Keep up the amazing work!

---

### Post by chanders on 2006-02-21
[QUOTE=Brain_Recall]Hello everyone.
I just wanted to say how estatic I am over this. But before I go into my little saga, let me explain some of my undertakings with Linux.
Honestly, almost every previous version (amoung different distributions) of GNU/Linux has practically let me down. Unsupported hardware, some obscure unfixable error, or major inconviences kept pushing me away.

A few days ago, I saw the large XGL demo video, and I knew I had to have it. To my supprise, somehow I stubled across this forum post. I immediately grabbed a DapperFlight4 ISO and burned away. I wasn't going to even try to install this on my main box (Athlon 64 X2, Geforce 7800GT, with the big Linux-killer nForce4 RAID 0 array), so I grabbed my Dell Inspirion 5150 laptop. I used PartionMagic 8 and opened up a 8GB courner and started to install. With a few minor confusions of the installer, Ubuntu DapperFlight4 was up and running. Supprisingly, it was up and running without a single complaint, something I never experienced before (and this from a beta release!).

I followed the guide, and being new to the apt-get experience, I didn't realize the Dapper universe repositories were commented out. I got everyhting going as far as I could tell, but, a reboot showed I had killed X. No worries, so I tried the ever-present option, format and reinstall.

I followed the guide again, and it works wonderfuly! I had some problems with screen corruption like others in this thread, and like others manually edition xorg.conf to set the color bit-depth to 24 bits fixed it perfectly.

I would like to follow this up by saying it's absolutely astounding to me that an beta-release distro is running a experimental windower as smoothly and as refined as Ubuntu is running XGL.

My hats go off to you all. Keep up the amazing work![/QUOTE]

If I must say so myself...Excellent job...Either you work in IT or you really love computers.... Good job in picking up the stuff so fast...

---

### Post by krye on 2006-02-21
It finally worked.

It looks [SIZE="5"]BEAUTILFUL[/SIZE]. :cry: 

Thanks a LOT PHG!!!

---

### Post by Milamber_Cubed on 2006-02-21
[QUOTE=nuzzy]I'm getting the same error as Denemite mentioned on page 45:



Any ideas how to fix this?[/QUOTE]

You can safely ignore this, i think. I was poking around the CVS and saw comments to the effect that the menu plugin had been removed. I don't know why it was removed, maybe the functionality it provided was merged into another plugin, or maybe it was only there for testing purposes... Either way, this shouldnt cause you any problems.

---

### Post by poofyhairguy on 2006-02-21
[QUOTE=Icetec]$ compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
[/QUOTE]

I have that problem before I upgraded my Mesa. Make sure you have the newest Mesa.

---

### Post by poofyhairguy on 2006-02-21
[QUOTE=hectorC]I been complaining about the same problem (nvidia-settings showing no options), and as you can see in my previous posts, there has been no answer. I sent a PM to Poofyhairguy but I haven't got any reply. It seems to be a problem related to the XGL configuration and nvidia-settings not finding the display. [/QUOTE]

Yeah. I hacked on that problem last night (aka installed Nvidia settings just to help) but then reading a post on the Nvidia forum I learned that its broken till at least the next driver release. Many of the Nvidia specific stuff are broken!

---

### Post by poofyhairguy on 2006-02-21
[QUOTE=Havoc]I love you and want to bear your child, Poofy. :D[/QUOTE]

First time I have heard that one.

---

### Post by i3dmaster on 2006-02-21
This is an OMG change to my desktop. Haven't seen Linux can get such close to OSX on eye candy. You've absolutely done a great job!!!!

---

### Post by hectorC on 2006-02-21
[QUOTE=poofyhairguy]Yeah. I hacked on that problem last night (aka installed Nvidia settings just to help) but then reading a post on the Nvidia forum I learned that its broken till at least the next driver release. Many of the Nvidia specific stuff are broken![/QUOTE]

Thanks for your time hacking on this one. I'm just curious, why did you say "installed Nvidia settings"? AFAIK nvidia-settings is installed as part of the nvidia-glx package (the nvidia-settings one in the repos should be removed).

---

### Post by grendelkhan on 2006-02-21
[QUOTE=Elcoco]i have the same problem as denamite, the new upgrades killed compiz. any idea on how to fix it?[/QUOTE]
DAMMIT

If I had read this I would have never restarted.

Oh well, there's always tomorrow.

---

### Post by poofyhairguy on 2006-02-21
[QUOTE=hectorC]Thanks for your time hacking on this one. I'm just curious, why did you say "installed Nvidia settings"? AFAIK nvidia-settings is installed as part of the nvidia-glx package (the nvidia-settings one in the repos should be removed).[/QUOTE]


Oh, I thought you were talking about the package in the repos.

Either way, we have a whole pile of problems that I hope the next Nvidia driver will solve. Expectations apon them have never been higher!

---

### Post by mstlyevil on 2006-02-22
Have you figured out a way  for existing windows to become translucent when you open a new window like kwin does? Or are we going to have to wait for a new pluggin? Just thought I would ask because it would sure be a pain to do this manually on every window.

---

### Post by opera118 on 2006-02-22
I'm thinking about why my nvidia driver isn't working at all after I've tried literally everything... It worked with breezy (X.org 6.8 iirc) with 7676, but now not even that nvidia driver works. I've read that both nvidia and X.org have added more strict EDID checks, and I've tried to disable them on the nvidia driver, but maybe X is the key here...
Still the 'nv' driver works for my native resolution (1400x1050).
Mplayer, vlc and a few other tools segfaults on start, and I've started wondering if all of this can be due to conflicting C library versions...
Haven't had this mess in a long time, surely wobbling windows looks great but unfortunately it ain't changing the depressingly far away state from "desktop ready" GNU/Linux's currently at.

Anyone have any thoughts on this C/X.org/nvidia stuff? I haven't manage to find any resource on this conserning the update from 6.8 to 7.0 of X.org. But it just feels to be part of the mess...
I'm wondering how much pain this will cause users of Dapper when it's released, if their LCD/TFT monitors resolution isn't respected due to a new X...
But maybe it's just me.

---

### Post by mstlyevil on 2006-02-22
[QUOTE=opera118]I'm thinking about why my nvidia driver isn't working at all after I've tried literally everything... It worked with breezy (X.org 6.8 iirc) with 7676, but now not even that nvidia driver works. I've read that both nvidia and X.org have added more strict EDID checks, and I've tried to disable them on the nvidia driver, but maybe X is the key here...
Still the 'nv' driver works for my native resolution (1400x1050).
Mplayer, vlc and a few other tools segfaults on start, and I've started wondering if all of this can be due to conflicting C library versions...
Haven't had this mess in a long time, surely wobbling windows looks great but unfortunately it ain't changing the depressingly far away state from "desktop ready" GNU/Linux's currently at.

Anyone have any thoughts on this C/X.org/nvidia stuff? I haven't manage to find any resource on this conserning the update from 6.8 to 7.0 of X.org. But it just feels to be part of the mess...
I'm wondering how much pain this will cause users of Dapper when it's released, if their LCD/TFT monitors resolution isn't respected due to a new X...
But maybe it's just me.[/QUOTE]

You have to edit your xorg.conf to tell it to use the nvidia driver. I had the same problem until I done just that.

```
sudo gedit /etc/X11/xorg.conf
```

Go to the devices section and look for Driver.

```
Section "Device"
	Identifier- leave this line alone!
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option 		"RenderAccel" 		"true"
	Option 		"AllowGLXWithComposite" "true" 
EndSection
```

If the driver section says "nv" change it to "nvidia" and then reboot. That should start the nvidia driver if it is installed corectly.

---

### Post by poofyhairguy on 2006-02-22
[QUOTE=mstlyevil]Have you figured out a way  for existing windows to become translucent when you open a new window like kwin does? Or are we going to have to wait for a new pluggin? Just thought I would ask because it would sure be a pain to do this manually on every window.[/QUOTE]


The Alt-TAB thing kinda does it, but yeah we will have to wait for a pluggin. 

I always prefered the window border translucency to that is Kwin so Compiz is right up my alley.

---

### Post by Icetec on 2006-02-22
[QUOTE=chanders]OK... quick fix... if this doesnt work nothing will :-D 

1. Install Dapper (Flight 3 or 4)
2. Enable all the repositories
3. Do a dist-update
4. Do a dist-upgrade. Reboot. Install your Nvidia Driver. Make changes to your xorg.conf
5. Install from the repository
  (i) compiz
  (ii) compiz-gnome
  (iii) mesa
  (iv) glitz
  (v) all the rest from this guide...
6. Reboot
7. Make all changes as per the guide to start Xgl
8. Make the script to run compiz...
9. Run the script...

Let us know the errors that show up..[/QUOTE]

gnome-window-decorator: Another window decorator is already running
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

Still. I've done everything from the guide. Is the gdm.conf-custom supposed to be called -custom or should I replace it with the regular one? It's called -custom now.. Isn't there any known answer to why this problem appears?

---

### Post by aamukahvi on 2006-02-22
[QUOTE=Icetec]Is the gdm.conf-custom supposed to be called -custom or should I replace it with the regular one? It's called -custom now...[/QUOTE]
Maybe you should re-read the HOWTO? To check if there's something you missed. Anyways, the answer is 1) yes 2) no.

---

### Post by peekj on 2006-02-22
This is wicked!! My F11 doesn't work but that's fine. I love the new ALT-Tab style and moving windows around a cube is just plain cool.

Nice tutorial!

Some side-effects seem to be that I can't type properly in my deskbar applet anymore... I can paste stuff into it and then edit that (no cursor though), but can't type something in when it's blank.

Again, great work!

---

### Post by opera118 on 2006-02-22
[QUOTE=mstlyevil]You have to edit your xorg.conf to tell it to use the nvidia driver. I had the same problem until I done just that.[/QUOTE]

No no, I know perfectly what I'm doing, but I think either the nvidia folks or the x.org folks don't ;)
I use the nv for now, since nvidia doesn't work well with x.org 7.0...
Maybe I should downgrade my dapper X to 6.8 to see if it works better, but that seems painful.

---

### Post by risbac on 2006-02-22
> My F11 doesn't work but that's fine.

Expose is F12, not F11. PHG changed this shortcut, but forgot to put the default one in the howto. I messaged him about that, he will fix it soon.

---

### Post by jujubinche on 2006-02-22
[QUOTE=Icetec]gnome-window-decorator: Another window decorator is already running
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

Still. I've done everything from the guide. Is the gdm.conf-custom supposed to be called -custom or should I replace it with the regular one? It's called -custom now.. Isn't there any known answer to why this problem appears?[/QUOTE]

OK.
Quick fix and explanation :
for some reason, nvidia-glx package "relink" your libGL.
To get the famous "GLX_EXT_texture_from_pixmap" extension working, you must, by hand, link the good lib (my english is poor, i know..).

cd /usr/lib
rm libGL.so libGL.so.1
ln -sf nvidia/libGL.so.1.2.xlibmesa libGL.so

et voila !

---

### Post by poofyhairguy on 2006-02-22
[QUOTE=risbac]Expose is F12, not F11. PHG changed this shortcut, but forgot to put the default one in the howto. I messaged him about that, he will fix it soon.[/QUOTE]

Done.

---

### Post by opera118 on 2006-02-22
[QUOTE=jujubinche]OK.
Quick fix and explanation :
for some reason, nvidia-glx package "relink" your libGL.
To get the famous "GLX_EXT_texture_from_pixmap" extension working, you must, by hand, link the good lib (my english is poor, i know..).

cd /usr/lib
rm libGL.so libGL.so.1
ln -sf nvidia/libGL.so.1.2.xlibmesa libGL.so
ln -sf nvidia/libGL.so.1.2.xlibmesa libGL.so.1

et voila ![/QUOTE]

And for us without the directory /usr/lib/nvidia?
Yes, some people use their own kernels and nvidia drivers...
I'm still waiting for the devs of these packages to give some details in how things are linked and are supposed to be, so that the rest of us can mimic that. Together with what "nvidia-glx enable" does... Could be helpful.

---

### Post by aent on 2006-02-22
[QUOTE=mstlyevil]You have to edit your xorg.conf to tell it to use the nvidia driver. I had the same problem until I done just that.

```
sudo gedit /etc/X11/xorg.conf
```

Go to the devices section and look for Driver.

```
Section "Device"
	Identifier- leave this line alone!
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option 		"RenderAccel" 		"true"
	Option 		"AllowGLXWithComposite" "true" 
EndSection
```

If the driver section says "nv" change it to "nvidia" and then reboot. That should start the nvidia driver if it is installed corectly.[/QUOTE]
On seemingly older cards
	Option 		"AllowGLXWithComposite" "true" 
causes artifacts on X. If you have any X artifacts, remove that line, and if you're loading the composite extension, remove that too. It fixed the problem on my laptop.

I'm still having a problem with loading the gconf plugin.... when the gconf plugin tries to load, compiz will never load anything else and just gets stuck (no decorations, no error, etc)... if I remove the gconf plugin from loading, everything else loads no problem, but I want to be able to configure the stuff... anyone have any ideas of what to do?

---

### Post by sapo on 2006-02-22
Hi guys, everything was fine here before the last dapper update, after updating the xorg and some packages i m getting this error:

```
sapo@ubuntu:~$ thefuture
/usr/bin/thefuture: line 2: gnome-window-decorator: command not found
sapo@ubuntu:~$ compiz.real: Couldn't load plugin 'libgconf.so'
compiz.real: dlsym: /usr/lib/libmenu.so: undefined symbol: getCompPluginInfo
compiz.real: Failed to lookup getCompPluginInfo in 'libmenu.so' plugin
```

Any ideas how to solve this?

thanx in advance

---

### Post by Denamite on 2006-02-22
Anybody with similar problems to mine, i did a
```
sudo apt-get install gnome-compiz
```
solved it and everything is working again.

Having some problems with the keybindings tough, seems like some keys doesn't want to work together with others, like <Alt>Tab and <Control>Tab and such.
Does anybody know what keykode the win key has? Xev said <Select> but that does nothing for me.

---

### Post by poofyhairguy on 2006-02-22
[QUOTE=Denamite]
Does anybody know what keykode the win key has? .[/QUOTE]

Super_L

---

### Post by aamukahvi on 2006-02-22
Left super, right super, menu key.

keycode 115 = Super_L
keycode 116 = Super_R
keycode 117 = Multi_key

---

### Post by jujubinche on 2006-02-22
[QUOTE=opera118]And for us without the directory /usr/lib/nvidia?
Yes, some people use their own kernels and nvidia drivers...
I'm still waiting for the devs of these packages to give some details in how things are linked and are supposed to be, so that the rest of us can mimic that. Together with what "nvidia-glx enable" does... Could be helpful.[/QUOTE]

I think only the "mesa" libGL.so work at this time, but, Nvidia drivers link this lib with their own libGL.
On my system, it's libGL.so.1.0.7174 (driver version ..).

You can link libGL.so to **libGL.so.1.2 from the libgl1-mesa ** package, as you don't have nvidia directory.

**Perhaps reinstalling  libgl1-mesa package is enough ... **


Note :
On my computer, linking libGL.so.1 to mesa lib libGL.so.1.2 make X crash.
so, 
libGL.so ----> nvidia/libGL.so.1.2.xlibmesa     **OR**    libGL.so ---> libGL.so.1.2 (from libgl1-mesa deb)
**and **
libGL.so.1 --> libGL.so.1.0.7174 (nvidia driver libGL)


ReNote :

glxinfo

name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
...
 
See the last line from mesa output ? yeah ! GLX_EXT_texture_from_pixmap ! maybe a clue ... ;)

---

### Post by jujubinche on 2006-02-22
[QUOTE=aent]On seemingly older cards
	Option 		"AllowGLXWithComposite" "true" 
causes artifacts on X. If you have any X artifacts, remove that line, and if you're loading the composite extension, remove that too. It fixed the problem on my laptop.

I'm still having a problem with loading the gconf plugin.... when the gconf plugin tries to load, compiz will never load anything else and just gets stuck (no decorations, no error, etc)... if I remove the gconf plugin from loading, everything else loads no problem, but I want to be able to configure the stuff... anyone have any ideas of what to do?[/QUOTE]

If you load gconf plugin, you **must** configure compiz in gconf-editor.



load plugins in this order :

[I]gconf key :

/apps/compiz/general/allscreens/options/active_plugins

value :
[gconf,decoration,minimize,move,resize,wobbly,fade,switcher,opacity,cube,rotate,scale,place,zoom][/I]


then , just load compiz --replace gconf to get all effects.

---

### Post by opera118 on 2006-02-22
[QUOTE=jujubinche]I think only the "mesa" libGL.so work at this time.

...

See the last line from mesa output ? yeah  !  GLX_EXT_texture_from_pixmap ![/QUOTE]

Wow. I had no idea that had to do with mesa, thought glx was glx and... Well...
This is the wonderful world of *nix where all of this is so very well documented...
Thanks anyway, that might help a lot, with that problem.

I just wonder, the other problems I have. Maybe there's an app somewhere that I'm supposed to find, or some document somewhere that I'm supposed to read... THAT major problem with *nix, novell didn't fix. Hah.

---

### Post by opera118 on 2006-02-22
This is hilarious... Now when I'm using the 'nv' driver (to be able to use X at all, thanks nvidia and xorg) my gnome has gone insane.. At startup it starts complaining about missing icons, and the metacity is totally crazy, starts changing from brown to blue scheme maybe 30 times, and the panels are the same. They end up looking like crap without the theme I'm used to... I'll look around gconf for a minute, then I give up... And .bashrc doesn't seem to load for the root user, only normal users... The world is ******* against me, and I'll have my revenge.....

---

### Post by Denamite on 2006-02-22
Thanks guys, <Super> worked fine, also had opacity load in the wrong order.
But I can't seem to get switcher to work with any keyboardshortcut at all, got the expose future to work tough so no worries really.
btw, has anybody noticed that deskbar-applet stoped taking input with Xgl running?

---

### Post by jujubinche on 2006-02-22
[QUOTE=opera118]This is hilarious... Now when I'm using the 'nv' driver (to be able to use X at all, thanks nvidia and xorg) my gnome has gone insane.. At startup it starts complaining about missing icons, and the metacity is totally crazy, starts changing from brown to blue scheme maybe 30 times, and the panels are the same. They end up looking like crap without the theme I'm used to... I'll look around gconf for a minute, then I give up... And .bashrc doesn't seem to load for the root user, only normal users... The world is ******* against me, and I'll have my revenge.....[/QUOTE]

I'm not Novell but ;) :
You start xgl (with gdm.conf-custom) without a supported driver (nv) ... so results could be weird ;) .. no ?

---

### Post by BetaguyGZT on 2006-02-22
INCREDIBLE !!!! I mean....WOW !!!

Works like a champ on my GF4-MX440 ! Worked right out of the restart (after typing 'thefuture' in a terminal of course)....

Brilliant! Superb! Ten thumbs up!

Poofy, I could kiss you. But I won't. You've got enough baby offers. hehe.... \\:D/ 

:KS  for you buddy.

---

### Post by opera118 on 2006-02-22
[QUOTE=jujubinche]I'm not Novell but ;) :
You start xgl (with gdm.conf-custom) without a supported driver (nv) ... so results could be weird ;) .. no ?[/QUOTE]

No, not even close. I don't know why I keep going in this thread, but I left xgl long ago... I got some serious sh*t going on here... My gconf seems to have broken down. So I thought I would try gconf-sanity-check-2 (which is supposed to be in /usr/lib/gconf2/gconf-sanity-check-2, at least in breezy) from the gconf2 package (which I have), but I don't have the directory /usr/lib/gconf2/... I'm getting tired of this.
Where is gconf-sanity-check-2 in dapper? Are things supposed to be this broken?
I could start a dozen new threads from all my problems, but... Well, I'm lazy.

EDIT: Found it. It's in /usr/lib/libgconf2-4/gconf-sanity-check-2 in Dapper for some reason. I love such changes, I wonder if there'll be a massive changelog with stuff like this.

---

### Post by poofyhairguy on 2006-02-22
[QUOTE=opera118]Are things supposed to be this broken?
[/QUOTE]

Yes. You are trying to use eye candy that cannot even be considered to be at a beta stage on a development distro thats has not hit its big freeze.

Everything about it screams "just might not work." I hoped my guide could help those who it can work for, but at this point no one can expect that much.

---

### Post by poofyhairguy on 2006-02-22
[QUOTE=Denamite]
btw, has anybody noticed that deskbar-applet stoped taking input with Xgl running?[/QUOTE]

It seems that applet is tied to Metacity.

---

### Post by opera118 on 2006-02-22
[QUOTE=poofyhairguy]Yes. You are trying to use eye candy that cannot even be considered to be at a beta stage on a development distro thats has not hit its big freeze.[/QUOTE]

No, I'm not, I have given up Xgl. But breezy->dapper in general seems to have breaked a LOT of things. That, I was actually not really prepared for. I thought dapper was about to be released in a couple of weeks.
And yeah, another thing in my nightmare of messiness. Apt-get stopped working, so I had to set its cache size manually... Do you still have to do that? In the year 2006? Jee.. I remember doing that in debian like 5 years ago. Things are still depending on stupid static values...
Maybe I should just quit all my other projects I'm working on and start fixing these things. I'm surprised we aren't moving faster.

---

### Post by nuzzy on 2006-02-22
[QUOTE=Denamite]Anybody with similar problems to mine, i did a
```
sudo apt-get install gnome-compiz
```
solved it and everything is working again.

Having some problems with the keybindings tough, seems like some keys doesn't want to work together with others, like <Alt>Tab and <Control>Tab and such.
Does anybody know what keykode the win key has? Xev said <Select> but that does nothing for me.[/QUOTE]


Hmmm...didn't work for me.  I even tried removing compiz, compiz-gnome and compiz-kde and reinstalling, but still get the libmenu.so error.

By the way, anyone using the kde-window-decorator??

---

### Post by suoko on 2006-02-22
Is any of you using nvidia legacy drivers with renderaccel option enabled?
I wanted to know if only my system hangs with that option enabled. 
The strange thing is that it hangs after an unpredictable amount of time. It can be after 1 hour or after 5 mins.
And I'm sure it's that option which causes the freeze since without it the pc can stay on for days.
If I'm the only one I suspect it could be a problem of the geforce256 card, not of the driver...

---

### Post by g14 on 2006-02-22
Dapper runs fine. I have ran it every day for the past 2 months without any major issues except when they did the 2.6.12 --> 2.6.15/removal of hotplug transitions and the x.org overhaul. The Dapper development cycle seems more sane and stable than the Breezy development cycle.

I run Xgl/compiz and it runs fine with Deskbar. I hit F3 and the deskbar searchbar pops up. If you want, I'll attach a screenshot after I get home.

To poofyhairguy... Making a shell script (/usr/bin/thefuture) and having it run under your session is very hackish. Try this instead:

1.) ALT F2 and put in 
> compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher
2.) System --> Preferences --> Sessions --> Startup Programs --> Add. Put in **gnome-window-decorator** and then add in another containing **compiz gconf**.
3.) Logout and then back in to gnome.
4.) Profit :) 

Same effect, less hackish, just my 0.3 cents.

---

### Post by Milamber_Cubed on 2006-02-22
[QUOTE=nuzzy]Hmmm...didn't work for me.  I even tried removing compiz, compiz-gnome and compiz-kde and reinstalling, but still get the libmenu.so error.

By the way, anyone using the kde-window-decorator??[/QUOTE]

Once again, I would like to point out that the menu plugin DOES NOT EXSIST in the debs, which I assume are build from quite recent CVS snapshots. If you don't believe me look at the changelog dated 2006-02-16 for compiz here:

[http://webcvs.freedesktop.org/xorg/app/compiz/ChangeLog?rev=1.14&view=markup](http://webcvs.freedesktop.org/xorg/app/compiz/ChangeLog?rev=1.14&view=markup)

You COULD download the compiz source code, modify the configure.ac file and then build it with the menu plugin... but I assume it has been taken out of the default build for a reason. :D 

PHG : Maybe the menu option should be removed from the guide??

---

### Post by sapo on 2006-02-22
[QUOTE=Denamite]Anybody with similar problems to mine, i did a
```
sudo apt-get install gnome-compiz
```
solved it and everything is working again.

Having some problems with the keybindings tough, seems like some keys doesn't want to work together with others, like <Alt>Tab and <Control>Tab and such.
Does anybody know what keykode the win key has? Xev said <Select> but that does nothing for me.[/QUOTE]
Thanx it worked, but its:

```
sudo apt-get install compiz-gnome
```

---

### Post by Havoc on 2006-02-22
One -no relation- question.

Does XGL (and Compiz for that matter) *need* a Nvdia (or ATI) graphics card?
I'm thinking of buying an old HP laptop, but it's equipped with a Trident card, quite nicely supported under open source drivers.
But, do I *need* a Nvidia or ATI card? Are there any "driver dependant" features or whatever?

Thanks. :D

---

### Post by sapo on 2006-02-22
[QUOTE=Havoc]One -no relation- question.

Does XGL (and Compiz for that matter) *need* a Nvdia (or ATI) graphics card?
I'm thinking of buying an old HP laptop, but it's equipped with a Trident card, quite nicely supported under open source drivers.
But, do I *need* a Nvidia or ATI card? Are there any "driver dependant" features or whatever?

Thanks. :D[/QUOTE]
I think it needs openGL, and i dont think a trident vga would have a good openGL support.

---

### Post by rastx on 2006-02-22
OK i got it installed and working pretty good (Amazing stuff!!!!)...

But, the system always locks up after a while. Completely frozen/unresponsive.

It happens consistently but somewhat  randomly, usually (but not always) when using OpenGL/accelerated apps such as 3D screensavers or XGL...

This seems to be happening with all my Linux installs, so is it a bug with OpenGL or the NVIDIA driver? Can anyone reccommend a fix? A more stable version of the NVIDIA driver perhaps?

Thanks guys!

2GHz AthlonXP / GeForce FX 5200 (256MB) / 1 GB RAM

---

### Post by denisesballs on 2006-02-22
The only real "bug" I've noticed is when a window is minimized it shows up on all the workspaces instead of staying on it's own. Anyone else notice that?

---

### Post by Athropos on 2006-02-22
[QUOTE=denisesballs]The only real "bug" I've noticed is when a window is minimized it shows up on all the workspaces instead of staying on it's own. Anyone else notice that?[/QUOTE]

I see this also, but everything else is just fine :p

---

### Post by Heretushi on 2006-02-22
[QUOTE=poofyhairguy]There I fixed me guide. The backspace shift bug is gone and I made it clear that not everyone should add the composite extension!

MOST BUGS ARE GONE![/QUOTE]
I still have the Shift + Backspace issue. I've not followed the whole guide though. What command/configuration should fix this issue? I had to reboot 3 times just to write this message as I have a high tendency to do this error.

Thanks! :)

---

### Post by grendelkhan on 2006-02-22
Finally!

Went into /var/cache/apt/archive, installed the old versions of mesa, ripped out compiz, deleted the debs out of cache, and then apt-get installed compiz-gnome and everything works again.

Yeesh.

There are moments I hate being bleeding edge.

---

### Post by woland on 2006-02-22
There is a problem with Nvidia legacy drivers. There are no restricted legacy modules for 2.6.15-xx core versions and compiling drivers from Nvidia wouldn't help (for new versions) or work (for older). 

Xorg did load with XGL with 2.6.12-10 in Breezy, but wouldn't work in Dapper. All my other attempts ended with Xorg failing to load. Had a nice blue screen telling me that there are no compatible drivers.

I have Athlon XP with Gforce 2 MX 400. Quite an oldie, but should be enough.

---

### Post by poofyhairguy on 2006-02-22
[QUOTE=Heretushi]I still have the Shift + Backspace issue. I've not followed the whole guide though. What command/configuration should fix this issue? I had to reboot 3 times just to write this message as I have a high tendency to do this error.

Thanks! :)[/QUOTE]

Solution is in my guide. This command solved it for me:

```
xmodmap /usr/share/xmodmap/xmodmap.us
```

Use that everytime you start XGL.

---

### Post by poofyhairguy on 2006-02-22
[QUOTE=rastx]OK i got it installed and working pretty good (Amazing stuff!!!!)...

But, the system always locks up after a while. Completely frozen/unresponsive.

It happens consistently but somewhat  randomly, usually (but not always) when using OpenGL/accelerated apps such as 3D screensavers or XGL...

This seems to be happening with all my Linux installs, so is it a bug with OpenGL or the NVIDIA driver? Can anyone reccommend a fix? A more stable version of the NVIDIA driver perhaps?

Thanks guys!

2GHz AthlonXP / GeForce FX 5200 (256MB) / 1 GB RAM[/QUOTE]

Do you have the composite extension enabled in your Xorg.conf. If so, remove it.

---

### Post by poofyhairguy on 2006-02-22
[QUOTE=g14]
To poofyhairguy... Making a shell script (/usr/bin/thefuture) and having it run under your session is very hackish.[/QUOTE]

What can I say, I love to use shell script hacks in my guides. They work well for me. 

But just so people have the option I link to your post on the front page!

---

### Post by poofyhairguy on 2006-02-22
[QUOTE=woland]There is a problem with Nvidia legacy drivers. There are no restricted legacy modules for 2.6.15-xx core versions and compiling drivers from Nvidia wouldn't help (for new versions) or work (for older). 

Xorg did load with XGL with 2.6.12-10 in Breezy, but wouldn't work in Dapper. All my other attempts ended with Xorg failing to load. Had a nice blue screen telling me that there are no compatible drivers.

I have Athlon XP with Gforce 2 MX 400. Quite an oldie, but should be enough.[/QUOTE]

I hate to be the one to tell you this, but if you have a Nvidia card so old that its not supported by the current drivers then eventually you will HAVE to upgrade to really enjoy XGL. Even if you get it to work somehow, when the next Nvidia driver comes will full support for XGL (aka no more mesa) you will be missing out.

---

### Post by poofyhairguy on 2006-02-22
[QUOTE=Havoc]One -no relation- question.

Does XGL (and Compiz for that matter) *need* a Nvdia (or ATI) graphics card?
I'm thinking of buying an old HP laptop, but it's equipped with a Trident card, quite nicely supported under open source drivers.
But, do I *need* a Nvidia or ATI card? Are there any "driver dependant" features or whatever?

Thanks. :D[/QUOTE]

I plan to buy a laptop soon and the rule I established is that the video card can't be weaker than a 5200 FX.

---

### Post by poofyhairguy on 2006-02-22
[QUOTE=Milamber_Cubed]

PHG : Maybe the menu option should be removed from the guide??[/QUOTE]

Done.

---

### Post by Heretushi on 2006-02-22
[QUOTE=poofyhairguy]Solution is in my guide. This command solved it for me:

```
xmodmap /usr/share/xmodmap/xmodmap.us
```

Use that everytime you start XGL.[/QUOTE]
Could I include this line in the shell script "hack" ? :P Would this work without me having to retype the command everytime I start my Linux?

Thanks! :)

---

### Post by Koybe on 2006-02-22
[QUOTE=Aphelion]Hi fellow Xgl users ;)

I managed to install Xgl and run compiz with this tutorial. It al works fine except some strange redraw? problems. Please look at the attached screenshot. Does anyone know how to fix this problem?[/QUOTE]

Hello, how do you get rid of that problem?

---

### Post by poofyhairguy on 2006-02-22
[QUOTE=Heretushi]Could I include this line in the shell script "hack" ? :P Would this work without me having to retype the command everytime I start my Linux?

Thanks! :)[/QUOTE]

I don't know. If it works tell me and I will add that to my guide.

---

### Post by Brain_Recall on 2006-02-22
[QUOTE=Koybe]Hello, how do you get rid of that problem?[/QUOTE]

Koybe, I had the same problem, and the person you quoted fixed it. Here's how:

Fire up a terminal, enter the following:
sudo gedit /etc/X11/xorg.conf

Scroll down to "Section "Screen""

Change the DefaultDepth to 24 instead of 16.

Save, reboot, and enjoy!

---

### Post by flying_nomad on 2006-02-22
Can somebody tell me wich of the guide's i have to follow ?

I know i have to use the Nvidia guide, but it seems like there is a wiki out too.

How about that wiki, is that so short because of it's a package  ??

[https://wiki.ubuntu.com/XglHowto](https://wiki.ubuntu.com/XglHowto)


Thanks for explaining (and all the hard work done out there)

Pat

---

### Post by stoffe on 2006-02-22
Two quick questions: 

* the wobbly fade effect on everything (tooltips, windows, dropdown menus... everything) that is the fade plugin right? I can't seem to get rid of it, or at least tweak it to only do windows and not tooltips/menus. Does anyone have any enlightenment on this? It's very annoying on tooltips and say the URL bar in FF, but ok on windows and dialogs. But i can't seem to make any changes in gconf, although the delay value does have effect.

* I use "stay on top" a *lot* as well as some other similar features of other window managers. I see "on top" when right-clicking window bar but it's grayed out - is it just a placeholder or is it possible to activate somehow?

All in all, I'm looking forward to when someone starts to write (more) usability features for this, that is going to make my desktop rock. Spinning a cube or wobble a window is cute but gets boring in about a minute, and it quickly gets annoying instead when features are missing. I can wait though. :)

Thanks.

---

### Post by Milamber_Cubed on 2006-02-22
[QUOTE=stoffe]Two quick questions: 

* the wobbly fade effect on everything (tooltips, windows, dropdown menus... everything) that is the fade plugin right? I can't seem to get rid of it, or at least tweak it to only do windows and not tooltips/menus. Does anyone have any enlightenment on this? It's very annoying on tooltips and say the URL bar in FF, but ok on windows and dialogs. But i can't seem to make any changes in gconf, although the delay value does have effect.
[/QUOTE]

To get rid of this, I think you can run gconf-editor and go to apps>compiz>plugins>wobbly>screen0 and edit the map_effect value and set it to "None". If it's already like that then change it to "Shiver" adn then to "None" and it should do SOME what you want i.e. get rid of the wobbly effect. The fade will still be there, but you can either speed that up or mess around with the settings of window_types in the fade plugin settings until you get what you want.

Hope it helps :)

---

### Post by stoffe on 2006-02-22
[QUOTE=Milamber_Cubed]To get rid of this, I think you can run gconf-editor and go to apps>compiz>plugins>wobbly>screen0 and edit the map_effect value and set it to "None". If it's already like that then change it to "Shiver" adn then to "None" and it should do SOME what you want i.e. get rid of the wobbly effect. The fade will still be there, but you can either speed that up or mess around with the settings of window_types in the fade plugin settings until you get what you want.

Hope it helps :)[/QUOTE]
Perfect, thanks a lot! Exactly what I wanted. :D

---

### Post by pecanov on 2006-02-22
I've noticed that some windows, sometimes, fade to colorless.
Now, my question is, who holds this feature (compiz, a plugin of compiz, the decorator?), and how can I disable it?

It really affects fullscreen video performance. I think that without this, it will run very smoothly, since if I resize the window manually, performance is inaffected.

---

### Post by aent on 2006-02-23
I believe that would be the fade plugin of compiz. Its only supposed to fade when a window stops responding (for example, a program crashed, is busy and wouldn't respond to anything you do, or if its stopped)

---

### Post by pecanov on 2006-02-23
I've disabled the fade plugin.
Windows still turn colorless.

---

### Post by Koybe on 2006-02-23
[QUOTE=Brain_Recall]Koybe, I had the same problem, and the person you quoted fixed it. Here's how:

Fire up a terminal, enter the following:
sudo gedit /etc/X11/xorg.conf

Scroll down to "Section "Screen""

Change the DefaultDepth to 24 instead of 16.

Save, reboot, and enjoy![/QUOTE]

Thank you, I haven't found this anwser. I'll give it a try after work. ;)

---

### Post by shodekiagari on 2006-02-23
Hey, I guess I'm one of the few to try this on kde. I upgraded from breezy tonight and it's working really smoothly except that my windeco (the menu bar, and the open/minimize/close buttons) is gone. 

Anybody else had that error? Anyone know how to fix it? Thank you.

edit: Answer is in this thread. [http://www.ubuntuforums.org/showthread.php?t=132771&page=2](http://www.ubuntuforums.org/showthread.php?t=132771&page=2)

I just can't get kde to compile though...

---

### Post by drizek on 2006-02-23
I get

compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

anyone?

---

### Post by flying_nomad on 2006-02-23
[QUOTE=flying_nomad]Can somebody tell me wich of the guide's i have to follow ?

I know i have to use an Nvidia way, **but it seems like there is a wiki out too**

How about that wiki, is that so short because of it's a complete package  ??

[https://wiki.ubuntu.com/XglHowto](https://wiki.ubuntu.com/XglHowto)


Thanks for explaining (and all the hard work done out there)

Pat[/QUOTE]

Can somebody clear this up for me, i will be gratefull for that

---

### Post by UbuntuUX on 2006-02-23
Here is the Xgl startup script I stripted down and loads up GNOME with gnome session. Nothing special just neat and simple and it's for people with Dapper repo packages.

Just take the .txt of the end and make it execuable

---

### Post by Tymon on 2006-02-23
I just followed the guide and everything works! Wow, I'm amazed at how smooth everything runs on my crappy FX5200!!! Especially if you'd compare it to Vista's crap compositing engine. And to imagine it's alpha/beta code, I'm really amazed!

---

### Post by miscz on 2006-02-23
XGL works quite good, there are 3 showstoppers for me tough:
-VLC doesn't have window decorations (no other app seems to have this problem)
-KDE TV output is messed, other TV apps work fine but KDE TV is just better than others
-Amarok doesn't appear in notification area and creates little windows for it's icon

Anybody experiencing this issues? I'd be grateful for any suggestions.

---

### Post by ShanghaiTeej on 2006-02-23
Is anyone else having problems with their screensaver?  My screen saver still shows the gnome-panels when it turns on and just covers the desktop.  I'm using dapper with a geforce4 mmx 440 card.

---

### Post by Paulus on 2006-02-23
[quote=ShanghaiTeej]Is anyone else having problems with their screensaver? My screen saver still shows the gnome-panels when it turns on and just covers the desktop. I'm using dapper with a geforce4 mmx 440 card.[/quote]

yeah, I have the same problem here.

---

### Post by golfbuf on 2006-02-23
I'm running dapper (daily updated) Xgl and using kde and having a lot of fun with it on KDE.  I have an 800 mhz PIII with an Nvidia GF4 MX 4000 pci card (never have gotton agp to work) which works well under dapper with the normal Xorg with the nvidia-glx package.

I needed glitz version 0.5.3 to get compiz working on this nvidia.

I tried loading Xgl by following the wiki suggestion of changing the link /usr/bin/Xgl -> /etc/X11/X.  This started ok, but kdm just cycles through the login screen in an endless loop.  I also could not figure out how to get the Xgl -accel options to work.  My options appear as:

:~$ ps aux | grep X
root     24707  8.6 19.7  85544 75824 ?        RL   12:36   0:41 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
root     24743  0.8  3.5  17320 13780 tty7     SLs+ 12:36   0:04 /usr/bin/Xorg -br vt7 -auth /tmp/.Xgl-auth-yQ72LJ -nolisten tcp -dpms -v -s 0 :93 -terminate

After starting "thefuture", it runs, but some of the 3D stuff like chromium is slow and causes X crashes.

So, I switched to gdm and am using this thread's recommended gdm.conf-custom to start Xgl.  Now my running Xgl is:

:~$ ps aux | grep X
root      8069 10.2 15.7  69840 60528 ?        RL   08:52   3:22 /usr/bin/Xgl :0 :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
root      8073  1.3  3.5  17316 13796 tty7     SLs+ 08:52   0:26 /usr/bin/Xorg vt7 -auth /tmp/.Xgl-auth-xShNFG -nolisten tcp -dpms -v -s 0 :93 -terminate

So, I'm using this thread's (and Suse) recommended -accel options.

Even before starting compiz, I notice that KDE 2D acceleration is slower than Xorg (windows move with a bit of jerkiness, scrolling a document with arrow keys is slow and occasionally text disappears .. things like that), but 3D acceleration (ppracer, chromium, frozen-bubbles, GL screensavers) run fine.

I like to use the Win key to popup my menu, but Xgl stops this.  I find that kcontrol uses a command like "setxkbmap -option lv3:lwin_switch" to set this up, and it isn't executing.  So, I added 'Option "XkbOptions" "lv3:lwin_switch" to xorg.conf, and now I can use kcontrol to set this preference.  But, this has the downside of making the Super key unavailable for the zoom module in compiz.

I use "thefuture" with these changes to load compiz:

compiz --replace gconf decoration wobbly fade minimize move place resize scale switcher cube rotate zoom
sleep 2
nohup gnome-window-decorator &

I needed to use this order of modules (from the wiki) to get all of them to load.  I was having difficulty getting the switcher module to load.  As it turns out, kde-window-decorator does not work (someone pointed out that the cvs version has comments in it saying it's not done), but gnome decorator works just as good as it does in gnome for KDE.

After loading compiz, I still see the same slower 2D acceleration, but 3D acceleration is still ok (ppracer, chromium, and gl screensavers, but frozen-bubble will not open in fullscreen and in a window, it is transparent, but still seems to play).  But, sometimes (not always) opening a GL screensaver will crash X.

I also have some random crashes of X, even when no GL or video programs are running.

When I check top, I see < 10% cpu usage with Xgl arout 8% and compiz < 1%.  When I move windows, the cpu will jump to about 80% and most of that is Xgl.  If I have a lot of firefox tabs open, I can get to 100%, but it's not too bad.  But, this also happens with Xorg and a lot of firefox's (firefox can be a hog).  Now I'm trying to use konqueror more.

As far as multimedia, flash movies play ok, .mid plays as usual with timidity, .mov play, but the video is poor quality with lines along the top, .ogg plays fine but while playing the cpu went to a 100% and gnome-window-decorator crashed (I could restart it to get the window frames back), .mp4 will play with the same video line problem as .mov, .mp3 audio is fine.  As I understand, these video problems will be fixed in a future release.

I like this enough to keep working with it despite the occasional crashes.  I would like to get the improved 2D acceleration.  My impression from other posters to this thread is that 2D is ok.  Is there anything different I should try to improve the 2D acceleration on my nvidia?

regards,

---

### Post by rastaman on 2006-02-23
I have a littal problem trying to folow these instructions. :cry: 
~$ sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package compiz

---

### Post by mstlyevil on 2006-02-23
[QUOTE=rastaman]I have a littal problem trying to folow these instructions. :cry: 
~$ sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package compiz[/QUOTE]

Go to your sources list and remove the # from in front of each source. The sources will be at the bottom of each comment (Usually in pairs of two.)

```
sudo gedit etc/apt/sources.list
```

Then save the file and type into the terminal

```
sudo apt-get update
```

After that try it again. If that does not work then delete those sources and add these instead.

```
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb http://ubuntu.tower-net.de/ubuntu/ breezy java

#not available until official release
#deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
```

Make sure you save these new sources.

Run sudo apt-get update again and I guarantee you will get it then. Also if you are having trouble getting Mplayer, Java or Flash from the first sources then skip the first step and use these sources.

---

### Post by rastaman on 2006-02-23
mstlyevil: 
thanks that worked :)

---

### Post by opera118 on 2006-02-23
Status of mess.

(this is not about xgl. this is not about xgl. this post, is not about xgl.)
(this post is not about compiz. i don't care about compiz atm. this post is not about compiz.)
(it's about ubuntu and nvidia)

Panels works and everything is fine when using nvidias libGL.so. However it doesn't contain the texture_from_bitmap. Using the libGL.so from xserver-xgl makes it possible to run compiz (if one would like to) however that file causes panels to crash as gconf completely crashes on startup. I get about 10 message dialogs about panels already loaded and "I will kill myself" etc.. No panels, broken gconf, themes a complete mess.
With nvidias libGL.so, no problemo.

Again, **it would be nice to know from where the ubuntu devs take the libGL.so they're using in xserver-xgl and how they link these things.**

But that won't happen, no devs here I'm afraid. I just wanted people to know, if someone gets the same problems with manually compiled nvidia drivers, you know now, you're not alone.

---

### Post by Athropos on 2006-02-24
[QUOTE=miscz]XGL works quite good, there are 3 showstoppers for me tough:
-VLC doesn't have window decorations (no other app seems to have this problem)
[/QUOTE]

I have the same problem with an app I am developping with wxGTK. I believe this will happen with all apps using this lib, but I don't know why...

---

### Post by EZbrain on 2006-02-24
angelus@netLIN:~$ thefuture
/usr/bin/thefuture: line 2: gnome-window-decorator: command not found
/usr/bin/thefuture: line 2: compiz: command not found
angelus@netLIN:~$ whereis compiz
compiz: /usr/lib/compiz /opt/fdo/bin/compiz


wat?

why do iget compiz command not found if its installed
and gnome-window-decorator:cry:

---

### Post by EZbrain on 2006-02-24
i did everything again, now it says : 

The following packages have unmet dependencies:
  compiz-gnome: Depends: libgnomeui-0 (>= 2.13.0) but 2.12.0-0ubuntu1 is to be installed
                Depends: libgnomevfs2-0 (>= 2.13.4) but 2.12.1-0ubuntu2 is to be installed
                Depends: compiz (= 0.0.2-4ubuntu2) but 0.0.3-1 is to be installed
E: Broken packages
:-k

---

### Post by DeeZiD on 2006-02-24
Just one question.
Can somebody send me the xmodmap.de file, I've deleted mine :rolleyes: 

regards Dennis

---

### Post by denisesballs on 2006-02-24
I think something really cool to be able to do would make all inactive windows like 25% transparent. That would give the desktop a really cool feel.

---

### Post by astron on 2006-02-24
a small update on my experience with Xgl. The system is now quite usable, but it's still slower than it was before Xgl.

My system : fresh install of Dapper from Flight CD 4
laptop TOSHIBA SATELLITE 2410-514 :
Pentium 4 (2GHz) 256MB RAM with NVIDIA GeForce 4 420 Go (32MB)
+ about 500 MB SWAP
I use the nvidia-glx-legacy, since nvidia-glx doesn't work with this card (even though the legacy is said to be for GeForce 2 and below only)

*Xorg config : 
I had to switch from 16bpp to 32bpp. With 16bpp, I experienced plenty of refresh problem. 
I had to remove (quote) these lines from my xorg.conf:
> 
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"

With these options, the system was too slow. I don't think Xgl uses Render or GLXWithComposite.

* Compiz : the svg plugin is not working. 

* Games : PPRacer runs OK (around 30 fps in a 800x600 window) but slower than usual. Supertux is OK with the opengl engine but is not playable with the sdl engine. Frozen Bubble is not playable. Flightgear starts and its graphics are OK but the system gets almost unresponsive. 

*Video Players:
-video output:
xshm and opengl work. xshm is the best. xv is too slow and for some video the XV driver shows only garbage
-players: totem-xine and gxine are OK. The xine-ui interface (not the video window) shows only garbage in XGL, but the videos play well. VLC is OK except it doesn't have window decorations.
-playing DVD with xshm is quite smooth (even with transparent windows).

---

### Post by r4ik on 2006-02-24
I got this baby working on a MSI MX4000-T128 card thanks for the guide !
One question about Mplayer it keeps telling me "to many video packets in the frame  
buffer" and changing the driver does not work.
Any suggestions about this please ?

---

### Post by golfbuf on 2006-02-24
[QUOTE=astron]The system is now quite usable, but it's still slower than it was before Xgl.

Yes, this is the same problem I am having (and reported yesterday).  Any ideas if it can be improved, or is this it for now?

regards,

---

### Post by daedalusman on 2006-02-24
Ok, well I have followed everything suggestion on this forum concerning my problem but to no avail. No matter what I keep getting this error...

```
gnome-window-decorator: Another window decorator is already running
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
```

This is with an dist-ugrade from breezy. I think I may try a clean install with flight 4 or wait till the next release and try again. If anybody has any other ideas concerning this problem that haven't already been covered, please post, thanks.

---

### Post by duff on 2006-02-24
[QUOTE=EZbrain]angelus@netLIN:~$ thefuture
/usr/bin/thefuture: line 2: gnome-window-decorator: command not found
/usr/bin/thefuture: line 2: compiz: command not found
angelus@netLIN:~$ whereis compiz
compiz: /usr/lib/compiz /opt/fdo/bin/compiz


wat?

why do iget compiz command not found if its installed
and gnome-window-decorator:cry:[/QUOTE]

You're missing something

```
$ which compiz
/usr/bin/compiz
```

---

### Post by tdg on 2006-02-25
Most of the things work smoothly here with my GeForce FX 5900 XT but I have two problems.

1) I can't use the zoom effect. It seems, I can't press the Super key(int. keyboard). Super key works fine in normal X, and I used xmodmap thingie.(Now that I think about it the combination for " is also different)

2) Xgl really slows down when I do a cpu intensive operation(like compiling, etc). 

I don't really care about the first, but the second makes an otherwise perfectly smooth system unusable for me. Any ideas?

---

### Post by campusloop on 2006-02-25
[QUOTE=tdg]Most of the things work smoothly here with my GeForce FX 5900 XT but I have two problems.

1) I can't use the zoom effect. It seems, I can't press the Super key(int. keyboard). Super key works fine in normal X, and I used xmodmap thingie.(Now that I think about it the combination for " is also different)

2) Xgl really slows down when I do a cpu intensive operation(like compiling, etc). 

I don't really care about the first, but the second makes an otherwise perfectly smooth system unusable for me. Any ideas?[/QUOTE]

1. I had the same problem on my system... it was because of improperly installed xkb files. I had a self compiled Xgl binary installed in /opt/xserver so i made a link
ln -s /etc/X11/xkb /opt/xserver/share/X11 and the problem was solved and now my hp internet keyboard works flawlessly. So make sure Xgl is able to find the xkb related files. I found it out by running an strace.. but say if Xgl is installed in /opt/fdo you can try
ln -s /etc/X11/xkb /opt/fdo/share/X11/ and see if it works..

2. Even i am facing the same problems. If the cpu is under load Xgl slows down terribly.. IMHO this is a major problem. I wonder if this is solved by EXT_texture_from_pixmap that needs to be added to nvidia/ati drivers.

---

### Post by croperz on 2006-02-25
I just updated my compiz from the repositories and now I have no gnome-window-decorator.

What's going on, where has it gone? :)

---

### Post by Omer on 2006-02-25
[QUOTE=croperz]I just updated my compiz from the repositories and now I have no gnome-window-decorator.

What's going on, where has it gone? :)[/QUOTE]

get compiz-gnome.

---

### Post by croperz on 2006-02-25
[QUOTE=Omer]get compiz-gnome.[/QUOTE]

Thanks, that fixed it.

I had looked for gnome-window-decorator in the repositories with no luck.

---

### Post by jdong on 2006-02-25
[QUOTE=tdg]
2) Xgl really slows down when I do a cpu intensive operation(like compiling, etc). 
[/QUOTE]

Confirmed here. Not even nicing Xgl to -15 fixes this problem.

---

### Post by gustavold on 2006-02-25
hi all

i installed the glitz0.5.3 from the dapper repo, but i'm still having the black screen.

can anyone tell me if this glitz version works?

nVidia Corporation NV17 [GeForce4 MX 440]

---

### Post by [Knuckles] on 2006-02-25
Thanks for the great guide!

I was playing around and installing some packages and messing with xbindkeys and some other things, and when I restarted, compiz no longer recognizes NO keybindings (even things like alt+f2 don't work anymore).

Can anyone help me?

---

### Post by drfoz on 2006-02-25
ive had this installed and running great... but it messes up opengl. my question is, is there a way to enable/disable this so when im not playing ut2004 its on then i cant shut it off when i wanna play a game?

---

### Post by [Knuckles] on 2006-02-25
Ok, I found out what was causing my problem. If anyone has problems with loosing compiz keybindings, don't use xmodmap to set the keymap, use the gnome preferences or something like that, because xmodmap was messing it up for me.

---

### Post by moebis on 2006-02-25
[QUOTE='[Knuckles]']Ok, I found out what was causing my problem. If anyone has problems with loosing compiz keybindings, don't use xmodmap to set the keymap, use the gnome preferences or something like that, because xmodmap was messing it up for me.[/QUOTE]

Ok I've having a similar problem. I used this guide and used the xmodmap, but lost any chance now of changing the keyboard layout in Gnome (I used to use the Microsoft Multimedia Keyboard setting) and that worked to enable the Win key, but now I can't use the Win key or anything but the very basic keys in Gnome +compiz, and when I try to use the Keyboard settings it doesn't list anything anymore. Any ideas?

---

### Post by mam28 on 2006-02-25
[FONT="Arial"][/FONT] I fouund if you install the i686 kernel from apt-get that it helps performance greatly. My firefox scrolling speed was fixed by this. Give it a try.:)

---

### Post by dolson on 2006-02-25
Hi, I apologize for not reading all 57 pages of the thread, but I can't easily browse this site.. Lucky I bookmarked the thread before I restarted X.

So, the problem is that if I move the cursor with the GNOME MouseKeys, Xgl crashes. I opened a ticket already for it in Malone, but I was wondering if anyone had a workaround? I can't use my PC like this, so I guess I'm going to disable it so I can actually click on things, but I'm going to try searching a bit first.

So if you have a solution, would you be kind and email it to me? I would appreciate it. [email]dana@ubuntustudio.com[/email]

Thanks for the how-to, I tried another one before and it didn't work right. :)

---

### Post by greenpenguin on 2006-02-25
This rocks.. and it worked perfectly straight off...
*big thanks* :).

i cant stop grinning now... :D

---

### Post by moebis on 2006-02-25
[QUOTE=greenpenguin]This rocks.. and it worked perfectly straight off...
*big thanks* :).

i cant stop grinning now... :D[/QUOTE]

Been running this for the last 3 weeks..... I still haven't stopped grinning. ;)

---

### Post by palomar on 2006-02-25
I have installed XGL on my XP1800 with nvidia Ti4200. Actually it runs good at first sight, but scrolling in Firefox and other apps is going a bit slower then before. As far as I can see I have set up al the optimalisation tips, like:
- K7 kernel + restricted modules
- 60fps (tried from 30 to 100)
- xorg.conf: RenderAccel, AllowGLXWithComposite, NvAGP enabled
- /etc/gdm/gdm.conf-custom from the startpost

and I'm using the nvidia driver from the repositories. I installed Dapper and XGL today, so I think I have downloaded the most recent versions.

Are there some other optimalisations I can try? Or is my hardware (ti4200) just a bit too slow or does have missing features?

---

### Post by dolson on 2006-02-25
Okay, I have now searched through all 58 pages, and the only mention I found of MouseKeys was my post... No one on IRC seems to respond to my questions, so if anyone here could help, I'd appreciate it. I had to disable it for now.

---

### Post by Yogarine on 2006-02-25
I installed Xgl + Compiz two days ago, and everything is swinging! I have a Pentium 4 1.5 GHz + 512MB RAM + NVIDIA GeForce FX 5200 and everything runs lightning fast (as long as I'm not compiling :P)

And ohh... The sound of my friends' jaws hitting the floor when they see me messing around...
(Tip: If you really want to impress, put both FF7:AC and Lilo & Stitch 2 on a corner, make one of them transparent and then rotate to show the cube corner. ;))

BUT, now there is just one thing that I need to figure out:
Is it possible to create multiple Xgl sessions? Right now I have everything set up to have one Xgl session and make all other sessions basic Xorg sessions, because I couldn't get Xgl to open a second session on another display. Any way to make this work?

Thanks people!

---

### Post by golfbuf on 2006-02-25
[QUOTE=gustavold]hi all

i installed the glitz0.5.3 from the dapper repo, but i'm still having the black screen.

can anyone tell me if this glitz version works?

nVidia Corporation NV17 [GeForce4 MX 440][/QUOTE]

Yes, it did here on my GF4 MX 4000

---

### Post by jdong on 2006-02-25
[QUOTE=Yogarine]
(Tip: If you really want to impress, put both FF7:AC and Lilo & Stitch 2 on a corner, make one of them transparent and then rotate to show the cube corner. ;))
[/QUOTE]

LOL, funny story about that... I showed two transparent movies playing over each other on a cube edge to one of my science/physics/animation-savvy buddies, and the first reaction was a complaint about artifacts with wobbly transparent windows when dragged at a high speed, and second was some remark about alpha blending not done correctly when two movies are playing over each other. I gave him a blank stare, and he's like "just kidding... I've never seen anything like it before!"

---

### Post by idn on 2006-02-25
I have installed the nvidia drivers like you said,  however performance can be slow sometimes even though I have a 7800gtx PCI-E

I also fail the cedega setup screen - I fail the Open GL Direct Redning. My xorg file is as follows:

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    Option 		"RenderAccel" 		"true"
    Option 		"AllowGLXWithComposite" "true" 

EndSection

Any ideas was to how I can fix this?

---

### Post by mrkite on 2006-02-25
Just a few notes that I haven't seen covered elsewhere.

If Xgl is taking up all your cpu, make sure you aren't using Mesa software rendering:

glxinfo | grep client

should have "client glx vendor string: NVIDIA Corporation"  not Mesa.

Second, if wobbly windows cause text to be a bit blurry for a few seconds, go to gconf-editor /apps/compiz/general/allscreens/options
and set texture_filter to "Pretty".

---

### Post by Rob2687 on 2006-02-25
Cool but it makes the jaggies show up even more. :/

---

### Post by mrkite on 2006-02-25
Well.. the three options for texture_filter are:

Fast  /  Good  /  Pretty

Pick the one that you like the best.

---

### Post by TerminX on 2006-02-26
[QUOTE=mrkite]Second, if wobbly windows cause text to be a bit blurry for a few seconds, go to gconf-editor /apps/compiz/general/allscreens/options
and set texture_filter to "Pretty".[/QUOTE]
The only two valid settings for this key are "Fast" and "Good" -- "Pretty" is invalid and nets you the same effect as "Fast"; i.e lower quality filtering.

---

### Post by Rob2687 on 2006-02-26
There is Best too. I find that works best =)

---

### Post by mrkite on 2006-02-26
[QUOTE=TerminX]The only two valid settings for this key are "Fast" and "Good" -- "Pretty" is invalid and nets you the same effect as "Fast"; i.e lower quality filtering.[/QUOTE]

[http://webcvs.freedesktop.org/xorg/app/compiz/src/display.c?rev=1.4&view=markup](http://webcvs.freedesktop.org/xorg/app/compiz/src/display.c?rev=1.4&view=markup)

The latest version of compiz uses Fast / Good / Best

---

### Post by TerminX on 2006-02-26
[QUOTE=mrkite][http://webcvs.freedesktop.org/xorg/app/compiz/src/display.c?rev=1.4&view=markup](http://webcvs.freedesktop.org/xorg/app/compiz/src/display.c?rev=1.4&view=markup)

The latest version of compiz uses Fast / Good / Best[/QUOTE]
Aha.  I had actually tried Best earlier after running strings on the compiz binary but had thought it to be invalid when I didn't notice any improvement over the "Good" setting.

---

### Post by palomar on 2006-02-26
Is it, besides my other 'problem' that scrolling goes a bit slow, normal that movies also play at very low framerate on a geforce ti4200? Is it usefull to  try out a lot of optimalization thing or is my hardware just nog good enough? Are there other people around with a Geforce ti4200 and XGL desktop?

---

### Post by Kinimod on 2006-02-26
> Is it, besides my other 'problem' that scrolling goes a bit slow, normal that movies also play at very low framerate on a geforce ti4200? Is it usefull to try out a lot of optimalization thing or is my hardware just nog good enough? Are there other people around with a Geforce ti4200 and XGL desktop?
I've got a Ti4200 and an XGL desktop running. Yes, movies play at a low framerate here, too. And scrolling lags a little bit.

---

### Post by palomar on 2006-02-26
ok, then I'll give up trying to make it go faster ;) Just limitations of the hardware as I expected.I'll give it a try on my other computer, an Athlon64 with Radeon 9800. Hope it goes faster.

I also have another question: this interface uses a lot of your VGA-card resources. I you run it 24/7, will the card reach high temperatures just like running 3D-games? Some graphics cards do have poor cooling sollutions, so does it increase the chance of a system crash due to overheating?
And the graphics card of to today consume lots of power. Will it increase your energy costs?  And system crashes due to cheap PC power supplies that are now running on their max capacity all the time?

---

### Post by Yogarine on 2006-02-26
So does anyone have a clue on how to get Xgl to open more than one session? (So I can use fast user switching between Xgl sessions?)

---

### Post by dolson on 2006-02-26
Could someone just *try* MouseKeys in Gnome and tell me if I'm the only one who has this problem? I would be very appreciative to get this figured out...

---

### Post by palomar on 2006-02-26
What do you mean with 'MouseKeys' ? I can't find it in repository or Gnome menu. I would test it for you, but don't know what to test ;)

---

### Post by dguido on 2006-02-26
I have an Dapper, an NVIDIA 6600GT with the latest nvidia drivers, and Xgl installed and working fine except for two things:

1. I cannot resize my windows
2. Video playback is extremely slow and brings the CPU to 100%

I'm not sure if the options I added to /etc/gdm/gdm.conf-custom are working properly because they were supposed to fix the video playback part.  The additions I made were:

```
[servers]
0=Xgl

name=Xgl server 
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true
```

I am starting Xgl by switching the symlinks on /etc/X11/X.  I also turned off dri and the composite extension in my xorg.conf.

For the video playback problem, I tried switching mplayer to using the gl2 output plugin and it caused a cascading crash.  Xine doesnt change if I use its default or its gl output.

Does anyone know what else I can do to fix these problems (mainly the video playback problem)?  Thanks.

---

### Post by tnasniv on 2006-02-26
Thanks a lot for this how to.
It's now working by default on my dapper, nvidia ti4200 64mo agp 4x.
Videos are slow, games a bit slow (chromium = ok, tuxracer = ok etc...)
Some applications have no menus (vlc, amule) but i think it's only a dapper beta dependant problem...

glxinfo say this :
```

vincent@ubuntu:/tmp/MPlayer-1.0pre7try2$ glxinfo
name of display: :0.0
display: :0  screen: 0
**direct rendering: No**
server glx vendor string: SGI
server glx version string: 1.2

```

Which (perhaps) means that because of xgl use opengl the other apps (like games) cant use it ... ?

---

### Post by dolson on 2006-02-26
[QUOTE=palomar]What do you mean with 'MouseKeys' ? I can't find it in repository or Gnome menu. I would test it for you, but don't know what to test ;)[/QUOTE]
Go to System > Preferences > Keyboard > Accessibility, Enable Keyboard Accessibility Features, then go to Mouse Keys, and Enable Mouse Keys. Now you can try using your NumPad to move your mouse cursor. Tell me if it works with no problems for you. Thanks!

---

### Post by scav on 2006-02-26
For those of you who miss a plugin were you can fade all windows except the focused one, check this script [http://www.ubuntuforums.org/showpost.php?p=611712&postcount=325](http://www.ubuntuforums.org/showpost.php?p=611712&postcount=325)

it works great, looks SEXY


Does the trick for me, untill something like this gets implemented in compiz

---

### Post by palomar on 2006-02-26
[QUOTE=dolson]Go to System > Preferences > Keyboard > Accessibility, Enable Keyboard Accessibility Features, then go to Mouse Keys, and Enable Mouse Keys. Now you can try using your NumPad to move your mouse cursor. Tell me if it works with no problems for you. Thanks![/QUOTE]
My X-server did also crash/restart when I hit numpad, so I think it is a real bug ;)

---

### Post by poofyhairguy on 2006-02-26
[QUOTE=scav]For those of you who miss a plugin were you can fade all windows except the focused one, check this script [http://www.ubuntuforums.org/showpost.php?p=611712&postcount=325](http://www.ubuntuforums.org/showpost.php?p=611712&postcount=325)

it works great, looks SEXY


Does the trick for me, untill something like this gets implemented in compiz[/QUOTE]

Good job!

---

### Post by dolson on 2006-02-26
[QUOTE=palomar]My X-server did also crash/restart when I hit numpad, so I think it is a real bug ;)[/QUOTE]
Thank you very much!

If you have a Launchpad account, get some karma by confirming the bug I opened: [https://launchpad.net/distros/ubuntu/+source/xserver-xgl/+bug/31907](https://launchpad.net/distros/ubuntu/+source/xserver-xgl/+bug/31907)

Thanks again... I wish there was a solution right now for this.

---

### Post by palomar on 2006-02-26
How about buying a mouse? :p

---

### Post by vendetta red on 2006-02-26
[QUOTE=scav]For those of you who miss a plugin were you can fade all windows except the focused one, check this script [http://www.ubuntuforums.org/showpost.php?p=611712&postcount=325](http://www.ubuntuforums.org/showpost.php?p=611712&postcount=325)

it works great, looks SEXY


Does the trick for me, untill something like this gets implemented in compiz[/QUOTE]

Could you explain how to set this up. i.e. what to save (I'm assuming BOTH files are needed) the files as, and whether they need editing to work with Compiz. I'd really like to give this a go, looks cool.

---

### Post by wylie348 on 2006-02-26
Oddly enough, I followed the directions to a t (I am using an inspiron 8600 with nvidia go5250), and XGL works great when dragging windows around and flipping desktops, but the login screen is all garbled, and so is any screen containing text.  Using firefox I have to continually minimize and maximize the screen to see the words properly.  
Anyone with a workaround?  I would really appreciate it!
Thanks!
;)

---

### Post by tnasniv on 2006-02-26
[OK]
I just had to re-add them with the gnome menu "Add to panel" :D

----
I just lost my desktop switch bar and the "return to desktop" icon, i dont know how, it just appears in front of me, i've made a reboot but it's the same.
It's not so important because i can still switch desktop (ctrl + alt + arrows) but that's strange
[[img]http://pix.nofrag.com/f4/73/6efa5009a639a5d92309cf98ce07t.jpg[/img]](http://pix.nofrag.com/f4/73/6efa5009a639a5d92309cf98ce07.html)

[[img]http://pix.nofrag.com/cd/36/160068e11fa93d7cb77298996614t.jpg[/img]](http://pix.nofrag.com/cd/36/160068e11fa93d7cb77298996614.html)

:confused: :rolleyes:

PS: for videos, with mplayer and "gl2" set in options it works well !

---

### Post by Iandefor on 2006-02-26
Excellent! Thank you (yet again!) poofy!

---

### Post by dolson on 2006-02-26
[QUOTE=palomar]How about buying a mouse? :p[/QUOTE]
If everyone had mice all the time, there would be no need for Mouse Keys. GNOME should just remove it if it's that useless, since they remove things that people want and need such as screensaver configurability. :evil: 

My mouse is on order. I ordered from an out-of-town store because it is much cheaper ($8CDN for a Logitech optical mouse). Yes, it will be great once it gets here, but this is still a bug in Xgl, and a pretty bad one, at that.

The real lesson is to not rely on Microsoft optical mice.

---

### Post by mstlyevil on 2006-02-26
I tried both ways to fix the wobbly windows and poofy's worked. The other one did not do a thing to correct it.

---

### Post by o_fortuna on 2006-02-27
So, I'm loving compiz :KS 

It's really fun and easy to impress your friends. Except when I'm typing a reply and I accidently hit Shift+Backspace, and the whole thing shuts down. Is there any way to get rid of that? I'm afraid to make typing mistakes :???:

---

### Post by mstlyevil on 2006-02-27
[QUOTE=o_fortuna]So, I'm loving compiz :KS 

It's really fun and easy to impress your friends. Except when I'm typing a reply and I accidently hit Shift+Backspace, and the whole thing shuts down. Is there any way to get rid of that? I'm afraid to make typing mistakes :???:[/QUOTE]

Open the terminal and enter this command everytime you boot

```
xmodmap /usr/share/xmodmap/xmodmap.<language>
```

For example I live in the US so here is my code

```
xmodmap /usr/share/xmodmap/xmodmap.us
```

If you want to just have this code executed at startup go to -->System -->Preferences -->Sessions. Click on the startup programs tab and then click on the Add button. Enter this command in the dialog box and click ok. You can also add Compiz to the startup by clicking on Add and then entering thefuture in the dialog box. It works like a charm for me.

---

### Post by scav on 2006-02-27
[QUOTE=vendetta red]Could you explain how to set this up. i.e. what to save (I'm assuming BOTH files are needed) the files as, and whether they need editing to work with Compiz. I'd really like to give this a go, looks cool.[/QUOTE]


You only need the first script, the other is for use with xcompmgr, which I doubt many use atm ;)

just copy and paste the script to a file, and make the file excecutable..(chmod +x file)

Then download transset-df from here:
[http://forchheimer.se/transset-df/](http://forchheimer.se/transset-df/)

compile it and your set to go, it works like a charm.

Only bug is when you minimize a window when it focused, creates some weird stuff from time to time.

---

### Post by saads on 2006-02-27
[QUOTE=dguido]
Does anyone know what else I can do to fix these problems (mainly the video playback problem)?  Thanks.[/QUOTE]
What you should have in your gdm.conf-custom is this:

```
[servers]
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true

```

I believe you're missing a line.  Then restart your computer - be sure to restart and not just restart X as that won't work.  You have to restart the gdm, which you can also do using the /etc/init.d/gdm script but i suggest just restarting the comp.  

To get good video playback in totem, modify the ~/.gnome2/totem_config file.  Look for the section starting with "# video driver to use" and replace it with:

```
[servers]# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX).
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true

```

For the other video apps (Mplayer and VLC), they have options in their GUI's that allow you to change the video output to OpenGL - I believe it's called gl2.

---

### Post by Cyberlink on 2006-02-27
[QUOTE=wylie348]Oddly enough, I followed the directions to a t (I am using an inspiron 8600 with nvidia go5250), and XGL works great when dragging windows around and flipping desktops, but the login screen is all garbled, and so is any screen containing text.  Using firefox I have to continually minimize and maximize the screen to see the words properly. [/QUOTE]

I have exactly the same problem on my Samsung X30 notebook...and it also has a nvidia go5250 built in.

What I of course can do is to remove the 0=Xgl line in my gdm.conf-custom file..well but I'm if I'm doing so, I get the annoying
compiz.real: GLX_EXT_texture_from_pixmap is missing
error.

Would be great if someone has an idea how to fix this as I just started loving this wobble thingy ;)

Btw. Thx for this great Tutorial :)

---

### Post by vendetta red on 2006-02-27
> **scav]You only need the first script, the other is for use with xcompmgr, which I doubt many use atm  said:**
> http://forchheimer.se/transset-df/[/url]

compile it and your set to go, it works like a charm.

Only bug is when you minimize a window when it focused, creates some weird stuff from time to time.

Thank you for the reply. I'll try this out ASAP. :)

---

### Post by jroes on 2006-02-27
Hey guys,

I just wanted to add that if you don't run the xmodmap line, shift+backspace will probably kill your X session.  It does for me.

If you -do- run the xmodmap line, though, you won't have a lot of other shortcuts working.

"casimir" on #ubuntu-xgl offers this suggestion, which works for us (instead of running the xmodmap line):

```
xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"
```

The original poster of this thread might want to change that xmodmap line so no one else has the same problems.

--Jonathan Roes

---

### Post by dolson on 2006-02-27
Awesome, thanks!

---

### Post by bunkee on 2006-02-27
anyone notice that the lock screen doesn't work while compiz is running

---

### Post by drizek on 2006-02-27
[QUOTE=bunkee]anyone notice that the lock screen doesn't work while compiz is running[/QUOTE]


it does in kde... 

you just have to press esc

---

### Post by Cyberlink on 2006-02-28
[QUOTE=Cyberlink]I have exactly the same problem on my Samsung X30 notebook...and it also has a nvidia go5250 built in.

What I of course can do is to remove the 0=Xgl line in my gdm.conf-custom file..well but I'm if I'm doing so, I get the annoying
compiz.real: GLX_EXT_texture_from_pixmap is missing
error.

Would be great if someone has an idea how to fix this as I just started loving this wobble thingy ;)

Btw. Thx for this great Tutorial :)[/QUOTE]

Fixed this Problem.
It seems to be a bug in Dapper so it configures X11 to use 16bit instead of 24bit color depth by using a nvidia go card.

So to get rid of this open your xorg.conf
go to the Screen-Section and change the DefaultDepth from 16 to 24.
Reboot and enjoy  ....wobbeling :D

---

### Post by Kurt` on 2006-02-28
[QUOTE=bunkee]anyone notice that the lock screen doesn't work while compiz is running[/QUOTE]
Yes, very annoying, as I lock my PC every time I walk away from it. :/

Also, some windows (viewing profiles in gAIM for example) can't be moved/resized.

Has anyone figured out how to prevent Shift-Backspace from killing X? I added the DontZap option to xorg.conf, but that only stops Ctrl-Alt-Backspace.

---

### Post by fizz on 2006-02-28
Just a tip for those using a dell 2005FPW wide aspect ratio monitor. I couldnt for the life of me figure out why wobbly was so slow, and looked awefull. I added the resolution of 1680x1050 to my xorg.conf and ctrl-alt-backspace to reload, and now everything is good.


One MAJOR gripe, is that i have hit shift backspace and killed x a few times, and even had to restart this thread once because of it.

---

### Post by dolson on 2006-02-28
[QUOTE=fizz]Just a tip for those using a dell 2005FPW wide aspect ratio monitor. I couldnt for the life of me figure out why wobbly was so slow, and looked awefull. I added the resolution of 1680x1050 to my xorg.conf and ctrl-alt-backspace to reload, and now everything is good.


One MAJOR gripe, is that i have hit shift backspace and killed x a few times, and even had to restart this thread once because of it.[/QUOTE]
Scroll up like 4 or 5 posts... There is a solution to that Backspace+Shift issue....

---

### Post by nrvale0 on 2006-02-28
Still having "GLX_EXT_texture_from_pixmap is missing" issues:

$ while true; do compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher; sleep 2; pkill -TERM compiz; ps -e | grep compiz; done
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

That can go on forever and compiz never gets happy. 

Any ideas?

---

### Post by fizz on 2006-02-28
Anyone else notice that Vino (Remote Desktop) breaks upon setting up xgl? Someone mentioned it might be part of the mod to gdm...

I searched this thread but didnt find anyone with the same problem.

---

### Post by vnbuddy2002 on 2006-02-28
[QUOTE=nrvale0]Still having "GLX_EXT_texture_from_pixmap is missing" issues:

$ while true; do compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher; sleep 2; pkill -TERM compiz; ps -e | grep compiz; done
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

That can go on forever and compiz never gets happy. 

Any ideas?[/QUOTE]

Here is a couple of things you will have to do:
if you use nvidia-glx,
........sudo ln -sf /usr/lib/nvidia/libGL.* /usr/lib/

Make sure that your /etc/X11/xorg.conf has the composite option turned on:
........Driver		"nvidia"
........Option 		"RenderAccel" 		"true"
........Option 		"AllowGLXWithComposite" "true"

then reinstall the packages from the first post

........sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome --reinstall

then, reboot your computer, if the problem still occur
try to reinstall the packages again. 

........make sure "/etc/gdm/gdm.conf-custom" correct specified.

then, reboot once again. It should work.

---

### Post by tronica on 2006-02-28
i have gotten everything to work, but it leaves me without the top bar on apps. is there something i can do to make them come back?

---

### Post by jstueve on 2006-02-28
> gnome-window-decorator &

---

### Post by tronica on 2006-02-28
i take you ment add that to sessions, so i did and no change. i put in the terminal and just gave me 

> lyle@ubuntu:~$ gnome-window-decorator &
[1] 7283
bash: gnome-window-decorator: command not found
lyle@ubuntu:~$



---

### Post by Technoviking on 2006-02-28
New xserver-xgl and metacity from sudo apt-get update. Wonder if metacity will have compositing enable.

---

### Post by tronica on 2006-02-28
should i just reinstalling this, has anyone had this problem

---

### Post by aamukahvi on 2006-02-28
[QUOTE=Mike Basinger]New xserver-xgl and metacity from sudo apt-get update. Wonder if metacity will have compositing enable.[/QUOTE]
Damn it. My Compiz shortcuts stopped working after the update.
Ok fixed it. My xmodmap file had been updated too it seems.

---

### Post by dolson on 2006-02-28
Install compiz-gnome as it says in the tutorial.

---

### Post by mannheim on 2006-02-28
I have the same problem as tronica. Things like the "cube" workspace switcher and the "wobble" are working just fine. But the window borders and title-bar are not being drawn.

gnome-window-decorator is running: it launched without complaint. I can also kill it and restart it. But whatever, it isn't decorating my windows.

---

### Post by DeeZiD on 2006-02-28
Is it possible to use Xgl with kdm instead of gdm?

I added the following to my kdmrc:
```
ServerCmd=/usr/bin/Xgl -ac -br -accel glx:pbuffer -accel xv:fbo
```

Kdm seems to start with Xgl after that (kdm crashed when I pressed Shift and Backspace).

But when I want to login it just returnes to the kdm-login-screen instead starting kde :( 


regards Dennis

---

### Post by Patryk996 on 2006-02-28
[QUOTE=poofyhairguy]Yeah, I get that sometimes. Just keep running the command till it goes away. Even if thats like twenty times. It will eventually go away.[/QUOTE]

\\:D/ Actually, I didn't like that answer. Things shouldn't work if you just **beat** them down repeatedly. So I did a little research online and it appears the French figured it out:
[http://imil.net/wp/archives/72]("http://imil.net/")
I can't honeslty tell you exactly WHY you need to do this, but I just did it and it worked:

[FONT="Courier New"]apt-get install libgl1-mesa[/FONT]
(make sure you also have libglitz1 and libglitz-glx1)
It's going also install libgl1-mesa-dri as well. It'll probbly uninstall a bunch of important (seeming) packages --do it.

You won't need to restart anything, just run "thefuture" again (or start compiz) and you should be all set!

Please let me know if this doesn't work for you!

In addition:
**[SIZE="6"]DEBIAN USERS!![/SIZE]**
I'm actually running Debian myself. To get this up and running on your DEBIAN system, you need to take some risks and be a little ballsy with your system:

Setup a pair (deb & deb-src) of Ubuntu repositories in your sources.list file for apt-get / synaptic and have them pull from the dapper version.
Install xserver-xgl, compiz, compiz-gnome and anything else that's required (I believe it'll prevent you from installing those unless you also install xserver-xorg [I think there are a few differences from debian xorg and ubuntu's xorg]).
Now you're almost done. Pretty much follow the instructions here, and then you should be all set.

you'll actually also need to install the nvidia-kernel-common and nvidia-glx as mentioned above because downloading the nvidia driver install packages from nvidia.com will place it in the correct location for debian, not for ubuntu.

I'm going to try and write up some more specific instructions and post them up somewhere, when I do I'll make the URL available. In the meantime, you should be able to get through it with what you have in this forum!
Best of luck! --it's SLICK :-D  (although you can tell it's still alpha: resizing windows isn't nearly as nice as moving them around :-# )

---

### Post by zaziork on 2006-02-28
[QUOTE=chrisrx]I
Is anyone having problems with amsn aswell?  I think it's xgl related because I never had a problem before but now tcl/tk throws up an error
```
Application initialization failed: this isn't a Tk application
```
[/QUOTE]

Yes, my aMSN is no longer starting, even when I'm not in compliz. Anyone have any ideas?

Lack of aMSN is a small price to pay though.. :D

EDIT: Just found the answer to the aMSN issue, as posted in another thread by Greg T:

```
sudo ln -s /etc/X11/rgb.txt /usr/share/X11/
```

---

### Post by bradx3 on 2006-03-01
Oh this is freaking awesome. It worked first go and now I'm just spinning around and around and around haha.

Thanks for the howto and tips to everyone involved.

---

### Post by GoA on 2006-03-01
OMG. This is something unbelievable. Works like a charm on my computer: Athlon 2800 XP, 1 gig ram, geforce 5200 FX. Is there any use to upgrade the display adapter to geforce 6800le? I own one but it isn't currently attached to the system. Would overcloking give much more speed to the system? Just great. I have just been laughing at home now. :D Got to go to the gym now and play after for more with computer. Thank you so much from the guide poofy and devs.

---

### Post by dolson on 2006-03-01
No, the 6800 is crap! Send it to me! ;)

I have a FX 5200 and it woks ok on my system, but I'd pop in that 6800 ASAP, if it were mine. :)

---

### Post by poofyhairguy on 2006-03-01
Am I the only one that already can't imagine going back to a world before windows wobbled?

---

### Post by zAo on 2006-03-01
[QUOTE=poofyhairguy]Am I the only one that already can't imagine going back to a world before windows wobbled?[/QUOTE]
No, you are not. I miss it at work. Somehow; don't know what or why I miss it :) I just love it I guess ;) 

I only the times that I use a lot of CPU time and XGL slows down :-#

---

### Post by denisesballs on 2006-03-01
Has anyone thought of a way to make inactive windows transparent automatically? Like when you remove focus, they automatically become opaque? That would be so awesome, how would that even be done?

---

### Post by aamukahvi on 2006-03-01
[QUOTE=denisesballs]Has anyone thought of a way to make inactive windows transparent automatically? Like when you remove focus, they automatically become opaque? That would be so awesome, how would that even be done?[/QUOTE]
I think if someone just wrote a simple plugin for Compiz (or modified the Opacity-plugin) that would be it.

---

### Post by mstlyevil on 2006-03-01
[QUOTE=poofyhairguy]Am I the only one that already can't imagine going back to a world before windows wobbled?[/QUOTE]

I completely wiped Windows and Breezy off of my hard drive because I just cant go back to a system with no XGL/Compiz and all the awesome eye candy.:mrgreen:

---

### Post by markr on 2006-03-01
Hi,

I've just installed Dapper under VMWare workstation and would like to try out the XGL stuff (Looks cool!).  

However, I believe that VMWare runs it's own video driver (i.e. I can't download and install the NVidia driver for Ubuntu).  Before I risk breaking my system, does anyone know if XGL will work under VMWare?

Thanks

Mark.

---

### Post by zAo on 2006-03-01
[QUOTE=markr]Hi,

I've just installed Dapper under VMWare workstation and would like to try out the XGL stuff (Looks cool!).  

However, I believe that VMWare runs it's own video driver (i.e. I can't download and install the NVidia driver for Ubuntu).  Before I risk breaking my system, does anyone know if XGL will work under VMWare?

Thanks

Mark.[/QUOTE]
Since VMware emulates even you VGA card, you can't run XGL on VMware.

---

### Post by GoA on 2006-03-01
[QUOTE=dolson]No, the 6800 is crap! Send it to me! ;)

I have a FX 5200 and it woks ok on my system, but I'd pop in that 6800 ASAP, if it were mine. :)[/QUOTE]

Otherwise yes, but it makes noise. :D 5200 is passive and I wouldn't put a passive heatsink on that baby. But anyway, Currently everything is going on smoothly and very responsively. I'm just thinking that would the 6800 do the rendering better and using lesser cpu power etc. So is there any reason for switch if I don't play games?

And poofy, yes, now windows and breezy feel very very dull. I just like to move windows for fun. :D

---

### Post by scav on 2006-03-01
[QUOTE=denisesballs]Has anyone thought of a way to make inactive windows transparent automatically? Like when you remove focus, they automatically become opaque? That would be so awesome, how would that even be done?[/QUOTE]


Ive got this working with a script posted earlier in this thread.. it bugs abit if you dont remove the fade plugin from compiz, but else it works really great!

---

### Post by tronica on 2006-03-01
I got this installed and it works fine now, however playing video is a different story. Either the video won't play or is jumbled up. but then some vids are fine heres a screenshot of one video.

[http://itransfer.ath.cx/screens/messed-up_video.png]("http://itransfer.ath.cx/screens/messed-up_video.png")

---

### Post by DeeZiD on 2006-03-01
I've got everything working now under Dapper.
Even the scaler key (F12) works (under OpenSuSe 10.1 it doesn't).
I even applied the kdelibs patch, so there no more kde-systray-issues.

But there's still one big problem.
I cannot use Xv, because it is horrible slow :(.
I've followed the how-to of course.

I want to use Xine with DVB and deinterlacing.
Is there any other way (I don't want mplayer for it, since it isn't a backend for Kaffeine, which works very fine in dapper :))

Even glxgears won't work.
Only a black window pops up.


I've noticed the following:
If I don't install "libgl1-mesa" I got the famous ..texture_from_pixmap...bla-bug and compiz won't work. 
But Xv is still very fast and glxgears works.

After an installation of  "libgl1-mesa" compiz works but glxgears doesn't and Xv (and OpenGl and Xhsm and SDL etc...) are very slow :(


This problem doesn't happen on OpenSuSE. But I don't want to switch to OpenSuSE 10.1 again (BUGS!!!!!!!) and Kubuntu is so fine. ;)


Am I the only one with this (ubuntu-specific)-bug?


regards Dennis

---

### Post by DeeZiD on 2006-03-01
I'm now trying to compile everything from cvs.
Maybe that works :)


regards Dennis

---

### Post by bradx3 on 2006-03-01
[QUOTE=poofyhairguy]Am I the only one that already can't imagine going back to a world before windows wobbled?[/QUOTE]
I can't. How did we ever live like that?

---

### Post by tseliot on 2006-03-01
Wonderful guide! I'm really fond of my Dapper and XGL.

Thanks for the guide!

---

### Post by poofyhairguy on 2006-03-01
[QUOTE=tseliot]Wonderful guide! I'm really fond of my Dapper and XGL.

Thanks for the guide![/QUOTE]

That means a lot coming from the king of Ubuntu guides!

---

### Post by dolson on 2006-03-01
[QUOTE=bradx3]I can't. How did we ever live like that?[/QUOTE]
OH COME ON! It's *JUST* a bit of eye candy... This isn't anything to write home about... This is really nothing that you haven't seen before. Ooo, windows "wobble" when you move them... Oh my, I better act like it's the end of the world. Microsoft is the leader of innovation, you'll see when Vista SE comes out, it will have the wobble effects and all that stuff, because Microsoft innovates. Blah blah blah.




...





OK, You're Right! I Admit It!!! I love my Xgl! It is really super! :D ;)

---

### Post by bhursey on 2006-03-01
I have it working fine.  But here's what I want working, and I would love if any one have gotten any of this to work..

I got mplayer working by editing this line 
```
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo 
```

To
```
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:gl2
```

But here is my question. I watch alot of tv on my system tvtime, vlc, totem, XawTV all have scribbled video. My question is how can I get all of these to work. Note this is not slow video it is scribbled. 

Here is a screenshot of what I am seeing.. Any ideas?
[img]http://static.flickr.com/38/106578724_47c9cc06c1.jpg[/img]

Thanks for the help..

---

### Post by bradx3 on 2006-03-01
[QUOTE=dolson]OH COME ON! It's *JUST* a bit of eye candy... This isn't anything to write home about... This is really nothing that you haven't seen before. Ooo, windows "wobble" when you move them... Oh my, I better act like it's the end of the world. Microsoft is the leader of innovation, you'll see when Vista SE comes out, it will have the wobble effects and all that stuff, because Microsoft innovates. Blah blah blah.
...
OK, You're Right! I Admit It!!! I love my Xgl! It is really super! :D ;)[/QUOTE]
Hehe I wasn't being 100% serious.

Even if it's just a bit of a novelty. I am missing my boxed desktop at work here. :-(

---

### Post by opera118 on 2006-03-01
By the way, has anyone gotten AIGLX to run?
I don't really like the idea of XGL as it's a completely new X. Movies messed up? Keyboard messed up (shift-backspace)? Well, if you're gonna rewrite X, there's a _lot_ of work to do. AIGLX doesn't really have these issues afaik. Even mouse-stuff never worked well for me in XGL.
Maybe in a few years from now it'll be smooth.
I dunno about the status of AIGLX tho.

---

### Post by poofyhairguy on 2006-03-01
[QUOTE=opera118]
I don't really like the idea of XGL as it's a completely new X. [/QUOTE]

Not really. It runs on top of the old X- it adds OpenGL extentions to the old X. 

Xegl is the "completely new X" and that project is dead as far as I know.

---

### Post by opera118 on 2006-03-02
[QUOTE=poofyhairguy]Not really. It runs on top of the old X- it adds OpenGL extentions to the old X.[/QUOTE]

No. It's not an extension, it is in fact a new server. You don't start X (or implicitly with startx) but Xgl. A new server. That is, in my perspective the reason why a lot of things don't work well (mouse for me, keyboard for most, image damage). It is not an extension to the old X, you're refering to glx. That's the extension. Xgl is the new server.
Aiglx is an extension however. Hence my reason to post.

[QUOTE=poofyhairguy]Xegl is the "completely new X" and that project is dead as far as I know.[/QUOTE]

Xegl is "the nice way" of doing Xgl which is a hack right now. And as for as I know about dead, it's rather the other way around. The fedora people seems to work on the aiglx while novell works on xgl. Nvidia officially praises the aiglx thought over xgl, and might stop supporting xgl (I think) if aiglx turns out to work well. It works better with their driver development.

Don't get me wrong tho, I think Xgl is very interesting and it sure demonstrates what can be done. Still, I wonder if anyone got aiglx to work or if it's not up to par for usage yet.

EDIT: Also, X.org seems to be planning on releasing aiglx in the mainstream X.org, but not Xgl. This is reason enough to start investigating aiglx further.

---

### Post by foffa on 2006-03-02
[QUOTE=ploum]thank for your suggestion but it doesn't change anything :-(  still the black xterm and black screen

(by the way, it doesn't take 100% of CPU. It's something else not related)

Strangely, my scrollwheel doesn't work in xgl. I don't really understand but this is a minor issue.

(for people who have the same "black screen" when launching "thefuture", the solution is to :

1) "killall compiz.real" in a terminal
2) Back to Xgl
3) "metacity &"

)[/QUOTE]

Copy rgb.txt from /etc/X11/ to /usr/share/X11/ will help you with the problem in xterm.

---

### Post by wmf521 on 2006-03-02
Hi,
Thanks for such useful posting, though despite this I still have the same error that a lot of others have seen but I can't resolve,

 compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0


I am running ubuntu dapper and the latest nvidia driver (NVIDIA 5700LE) which I installed from the nvidia site, I am not using the ubuntu packaged nvidia deb.  I made the additions to gdm, and I compiled the glitz myself from the cvs source as advertised....any ideas?

Thanks so much.

---

### Post by caish5 on 2006-03-02
I just got all this working and it rocks!! Great Guide...

Just one small thing though...

How can i slow my mouse pointer down?
The usual System->Preferences->Mouse no longer works and it's moving around waaay to fast.

Thanks 
Andy

---

### Post by tnasniv on 2006-03-02
[QUOTE=wmf521]Hi,
Thanks for such useful posting, though despite this I still have the same error that a lot of others have seen but I can't resolve,

 compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0


I am running ubuntu dapper and the latest nvidia driver (NVIDIA 5700LE) which I installed from the nvidia site, I am not using the ubuntu packaged nvidia deb.  I made the additions to gdm, and I compiled the glitz myself from the cvs source as advertised....any ideas?

Thanks so much.[/QUOTE]

sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome --reinstall

I did exactly this when i get the same error...
Because all was working (gfx card, screen) well except this error. I though there's must be something wrong with the install.

---

### Post by wmf521 on 2006-03-02
Yeah this still doesn't fix the problem, 

thanks though.

---

### Post by karthik085 on 2006-03-02
Thanks, it works for me. I used proprietary nvidia drivers, instead of the ones in respos. It removed libGL.so.1.2. So, I removed and installed libgl1-mesa. This time, I copied libGL.so.1.2 to a temp directory. Then, I reinstalled the nvidia drivers. I copied back libGL.so.1.2 and 
ln -sf /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1
Then, followed the instructions. Damn, there it was :-)

P.S.: I did Ctrl+Alt+F1. Pointed the link from libGL.so.1 to libGL.so.1.2. Restarted GDM. But, X server crashed. This is because of removing the symbolic link libGL.so.1, pointing to libGL.so.1.0.8178. So, it is safe, always to keep this symbolic link and change only when you need to run compiz, after you start gdm. If you want to run compiz, every time you reboot, you can make the link libGL.so.1 point to libGL.so.1.2 and at the time of shutdown, point back to libGL.so.1.0.8178. 

[QUOTE=iMil]Ok here is a tip solving the "compiz: GLX_EXT_texture_from_pixmap is missing" once and for all (here at last ;)

The fact is nvidia-glx removes libgl1-mesa's /usr/lib/libGL.so.1.2, and makes libGL.so.1 point to NVidia's libGL.so.1.0.8178, which does NOT support GLX_EXT_texture_from_pixmap function.

Simple trick, nvidia-glx moves /usr/lib/libGL.so.1.2 to /usr/lib/nvidia/libGL.so.1.2.xlibmesa, so just 

ln -sf /usr/lib/nvidia/libGL.so.1.2.xlibmesa usr/lib/nvidia/libGL.so.1

Use the original doc from this thread, and you're done.
Please note i've not tested yet if this has side effects over other OpenGL apps like games and such.[/QUOTE]

---

### Post by opera118 on 2006-03-02
A general rule for new *nix users is not to delete or copy files, but to move and symlink. Not always, but often. Don't copy rgb for instance, symlink it.

This texture_from_pixmap stuff is interesting. Why it doesn't work with 8178 is because nvidia hasn't implemented it yet. Instead you're using the mesa alternative (software GL). I wonder how much better things will work when it gets native support from the hardware... Probably reduce CPU a lot (making Xgl less cpu dependent - not causing it to suck when compiling for instance)...
We'll just have to wait and see.

---

### Post by RAOF on 2006-03-03
[QUOTE=opera118]...
This texture_from_pixmap stuff is interesting. Why it doesn't work with 8178 is because nvidia hasn't implemented it yet. Instead you're using the mesa alternative (software GL). I wonder how much better things will work when it gets native support from the hardware... Probably reduce CPU a lot (making Xgl less cpu dependent - not causing it to suck when compiling for instance)...
We'll just have to wait and see.[/QUOTE]
I believe that the texture_from_pixmap support will bring world peace.

Or, at least, make resizing almost windows as fast as moving them around, among other things.

---

### Post by jnk on 2006-03-03
Everything works perfect here... Running a cool desktop on an old GeForce3Ti200 card.
But yesterday I noticed that all movies are realy slow. and I mean lagging so badly that it would take 4h to watch a 4min clip.
Could this be because the gfxcard is busy with drawing the desktop or w00t.?
I use the glitz from the repos... could this be the problem.?

---

### Post by Kebabji on 2006-03-03
your guide has made me fall in love with my ubuntu linux all over again. thank you.

---

### Post by hellfire_bg on 2006-03-03
Thanks for this wonderfull HOWTO and the advises i found in the posts after the howto which helped me to get this working. I have only one problem and it is gaming. Before i installed XGL i could play Unreal Tournament 2004 and some games with cedega including Warcraft III, Homeworld 1,2 Battlefiel 1942. I tried to start UT2004, but i couldn`t. I got:
Assertion failed: InPos<=Size [File:../../Core/Inc/FFileManagerLinux.h] [Line: 82]

History:

Exiting due to error

I haven`t tried cedega, but i suppose it won`t work too. Is there any way to stop XGL withowt restarting the x server (i start manually XGL with thefuture scrip everytime i start ubuntu; i haven`t added it to the list of startup programs). If it matters my video card is FX5200.


Edit from 13:41 GMT+2 Fri 3 Mar
I tried the same before i ran thefurure scrip and i got the same results. However maybe the reason is not in the script but in the modifications i did as described in the HOWTO.

---

### Post by byoon on 2006-03-03
[QUOTE=hellfire_bg]Thanks for this wonderfull HOWTO and the advises i found in the posts after the howto which helped me to get this working. I have only one problem and it is gaming. Before i installed XGL i could play Unreal Tournament 2004 and some games with cedega including Warcraft III, Homeworld 1,2 Battlefiel 1942. I tried to start UT2004, but i couldn`t. I got:
Assertion failed: InPos<=Size [File:../../Core/Inc/FFileManagerLinux.h] [Line: 82]

History:

Exiting due to error

I haven`t tried cedega, but i suppose it won`t work too. Is there any way to stop XGL withowt restarting the x server (i start manually XGL with thefuture scrip everytime i start ubuntu; i haven`t added it to the list of startup programs). If it matters my video card is FX5200.


Edit from 13:41 GMT+2 Fri 3 Mar
I tried the same before i ran thefurure scrip and i got the same results. However maybe the reason is not in the script but in the modifications i did as described in the HOWTO.[/QUOTE]

You can try to run the games in a separate X server and that should solve your problem.  You can either set it up and manually run the second X server and your game or you can do some initial setup and let xgame (a perl script) launch the second X server and your game.

Follow this thread:

[http://www.ubuntuforums.org/showthread.php?t=137296]("http://www.ubuntuforums.org/showthread.php?t=137296")

I am having problems running Cedega with kernel 2.6.15-16-k7, but it works with kernel 2.6.16-14-k7.

---

### Post by Technoviking on 2006-03-03
I'm having a strange window problem when I turn on XGL. When a program opens up a second window the new window's title bar is blank, also the new window is unmovable. This is kinda annoying if the window is opened in a bad position, or it is covering something you need to get to.

Is this normal behavior for XGL, or weirdness at my end.

---

### Post by zAo on 2006-03-03
[QUOTE=Mike Basinger]I'm having a strange window problem when I turn on XGL. When a program opens up a second window the new window's title bar is blank, also the new window is unmovable. This is kinda annoying if the window is opened in a bad position, or it is covering something you need to get to.

Is this normal behavior for XGL, or weirdness at my end.[/QUOTE]
I think this is normal for Compiz. You can move the window with ALT + L.Mouse

---

### Post by charlieg on 2006-03-03
The howto worked well but in Compiz I only have one workspace available (as opposed to 4 when Metacity is running). Any Tips? (Apologies for being lazy... I had a brief look already but I'm really busy and shouldn't even be throwing any time at this, tho it is fun.)

---

### Post by Devilotx on 2006-03-03
what is the command to make the window transparent?

I saw it in here, but now it's missing, I can enable all the GLX features with thefuture in the terminal, but I cannot remember the terminal command to let me click a window to make it transparent

thanks

---

### Post by chesko on 2006-03-04
to configure opacity follow this guide: [http://www.ubuntuforums.org/showthread.php?t=132063](http://www.ubuntuforums.org/showthread.php?t=132063)
It works fine :D

---

### Post by chesko on 2006-03-04
I have a very weird problem with a sparkle 6600 gt:

When I move a window it works fine until I stop moving it. Then It seems that the deformation isn't hardware accelerated and causes major slow-downs.

I think this happens because in a 6600 gt the 3D engine isn't always working, but only when needed. And It seems that the 3D engine is disconected before the deformation of the window has finished.

To try this a bit more I play a video at the same time. Since It uses 3D acceleration there aren't any problems if the video is running, because the 3D engine of the card is working all the time.
If I play a video I can run as many accelerated things as I want. All works perfect without slow-downs... I can play four movies with different opacities, I can move windows with deformations, all at the same time without problems.

I don't want to always have a video window running to fully enjoy the Xgl advantages... any hints on how to solve this?

---

### Post by chesko on 2006-03-04
[QUOTE=chesko]I have a very weird problem with a sparkle 6600 gt:

When I move a window it works fine until I stop moving it. Then It seems that the deformation isn't hardware accelerated and causes major slow-downs.

I think this happens because in a 6600 gt the 3D engine isn't always working, but only when needed. And It seems that the 3D engine is disconected before the deformation of the window has finished.

To try this a bit more I play a video at the same time. Since It uses 3D acceleration there aren't any problems if the video is running, because the 3D engine of the card is working all the time.
If I play a video I can run as many accelerated things as I want. All works perfect without slow-downs... I can play four movies with different opacities, I can move windows with deformations, all at the same time without problems.

I don't want to always have a video window running to fully enjoy the Xgl advantages... any hints on how to solve this?[/QUOTE]


ok, I can solve this as explained in the very first post of this thread :p :

Now is to solve some general issues. One is the fact that the wobble seems off to many people with Nvidia cards. There is an easy fix thanks to roberTO:

Run the command:
Code:

gconf-editor


Now go to:

apps>compiz>general>screen0>option

Then turn off the "detect_refresh_rate" option.

Then set the "refresh_rate" to 60

And now it works fine, but it still seems to me a very weird thing because with video on it worked fine even I tried to overload the graphic card

---

### Post by Sav on 2006-03-04
Thanks a lot.
I made it works in few minutes.
I love it.

---

### Post by ohsnapninjas on 2006-03-05
One more thing to do is get truly transparent terminal windows!
   1.  I installed the following Deb package: [http://geek.fi/urxvt/rxvt-unicode_7.6-1_i386.deb]("http://geek.fi/urxvt/rxvt-unicode_7.6-1_i386.deb")
   2. I took the .Xdefaults that [this guy]("http://geek.fi/urxvt/") had as well since without them I got a &#8220;no such color, using pink instead&#8221; message.
   3. Next step was to reload the .Xdefaults for the session: &#8220;xrdb -load ~/.Xdefaults&#8221;
   4. Now I can launch truly transparent windows! Personally I like the look of the following:
   5. urxvt -depth 32 -fg rgba:ffff/ffff/ffff/ffff -bg rgba:0000/0000/0000/7777

Here is some multiple color overlapping a Starcraft session in Wine
[IMG]http://ohsnapninjas.com/files/rgbstarcraft_thumb.png[/IMG]

---

### Post by jroes on 2006-03-05
You know, I was just thinking.  It would make a lot of sense to put that xmodmap line at the end of the /usr/bin/thefuture script.

---

### Post by gheorghe_pop on 2006-03-05
For me it doesen't work.
I tried running thefuture script as much as 40 times and the best that i get is:

```
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
gnome-window-decorator: Another window decorator is already running

```

---

### Post by Jaidee on 2006-03-05
Hello,

I've followed all the steps in this guide and also for installing the newest NVidia drivers, as described on the Latest-NVidia-Dapper wiki page. Here is my xorg.conf:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Dec 14 16:39:22 PST 2005

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
#	Load	"dri"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV17 [GeForce4 420 Mac 32M/GeForce 440 Go 64M]"
    Driver         "nvidia"
	BusID		"PCI:1:0:0"
 	Option 		"RenderAccel" 		"true"
	Option 		"AllowGLXWithComposite" "true" 
	Option		"IgnoreEDID"		"true"
	Option		"IgnoreEdidFreqs"	"true"
	Option		"GenerateRTList"	"0"
	Option		"OverridePolarity"	"1"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV17 [GeForce4 420 Mac 32M/GeForce 440 Go 64M]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768"
    EndSubSection
EndSection

```

I get the error that no display modes were found. Looking at the errors, it seems that the vsync and hrefresh are not in range?

I'll add more to this post if I need to. Please help!

---

### Post by GoA on 2006-03-05
You are having allowglx and renderaccel in device partition AND in screen part of xorg. It has to be only in the device part for what I have understand. So remove those two from the screen part.

---

### Post by chair on 2006-03-05
[QUOTE=gheorghe_pop]For me it doesen't work.
I tried running thefuture script as much as 40 times and the best that i get is:

```
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
gnome-window-decorator: Another window decorator is already running

```[/QUOTE]

I copied the /opt/fdo/lib directory from the mesa deb from [here]("http://battlehorse.homelinux.net/w/Wiki.jsp?page=Xgl#section-Xgl-25Feb2006FreshAndUntested") into /usr/lib


Can someone tell me what's meant to be in gconf-editor? The key shortcuts don't work and I've got no key bindings in gconf-editor. Will the keybindings work in KDE?

---

### Post by UbuntuUX on 2006-03-05
Anyone know how to get the messagebus working for Epiphany in Xgl?, tried putting the dbus line in there but still get this message.

> Startup failed because of the following error:
Unable to determine the address of the message bus

---

### Post by alphazero on 2006-03-05
I guess I'm one of the lucky one but everything worked out for me. Thanks much for the sweet eye candy.

---

### Post by opera118 on 2006-03-05
[QUOTE=Jaidee]I get the error that no display modes were found. Looking at the errors, it seems that the vsync and hrefresh are not in range?

I'll add more to this post if I need to. Please help![/QUOTE]

The latest version of the nvidia driver is almost completely broken. It has many bugs in different areas, a new version will probably come in a few days (3 days many people think). Shouldn't be much more than a week at the most anyway.

Try using the 'nv' driver and see if it works with the same settings.

---

### Post by FLeiXiuS on 2006-03-06
I can only run thefuture in an emulating root session via sudo.  Running compiz as a normal user resulted in compiz not being able to grab the Xgl screen.  

But it's giving me problems right now.  I'm unable to use my keyboard shortcuts.  :-(

---

### Post by poofyhairguy on 2006-03-06
[QUOTE=jroes]You know, I was just thinking.  It would make a lot of sense to put that xmodmap line at the end of the /usr/bin/thefuture script.[/QUOTE]

I honestly just have the future and that line run when my computer starts.

You can add it to the script, or just add it to your sessions.

---

### Post by mega on 2006-03-07
I'm giving up on ati

what's the cheapest pci express x16 nvidia that will support all the g-wiz features of xgl + compwiz ?

---

### Post by jdong on 2006-03-07
considering how my Geforce4 does it fine, I'd be willing to say ANY pci-x nvidia!

---

### Post by mega on 2006-03-08
[QUOTE=jdong]considering how my Geforce4 does it fine, I'd be willing to say ANY pci-x nvidia![/QUOTE]

It'll be pushing a widescreen lcd at 1600x1200 not sure a geforce4 will do that well, and enable all the neat features


the geforce 7300GS seems cheap, but I cant tell if it really works, it's not in the list of supported cards, but the XGL info page says it is supported

the xgl info page also said the ati x300 works too, but it most definitely does NOT work

---

### Post by malte on 2006-03-08
Got it working with a GeForce4 MX 440SE AGP 8x and standard dapper repository version of required packages!
Just didn't have to xmodmap my layout, but used the GNOME configuration dialog...

---

### Post by poofyhairguy on 2006-03-08
[QUOTE=mega]I'm giving up on ati

what's the cheapest pci express x16 nvidia that will support all the g-wiz features of xgl + compwiz ?[/QUOTE]


I would suggestion a 6200 WITHOUT Turbocache. Avoid those cards like the plague!

---

### Post by Micro Rotors on 2006-03-08
poofyhairguy,

I have her up and running on  a PNY Verto 6800 GS overclocked version without a hitch. The guide was simple and perfect as usual from you.

Thanks
Bill

---

### Post by binarymelon on 2006-03-08
My key bindings don't work.  I had a test partition that I installed dapper on and everything worked fine and I just upgraded by breezy install to dapper and now things aren't working.  I can't perform any of the keyboard shortcuts.  Does anyone have any suggestions?

edit: And just incase anyone asks I'm running xmodmap /usr/share/xmodmap/xmodmap.us everytime I start.

---

### Post by gr8whitesavage on 2006-03-09
+1 more person to have Dapper w/ XGL installed. I must say I am impressed.

My machine is Athlon XP 2100, 512mb ram, GeForce FX 5500 256mb. The setup runs great.

The only hitch I had is that Dapper took my WinXP entry out of grub. I'm pretty sure I know how to put it back so no problem.

Thanks for the howto!

---

### Post by RockinRob2258 on 2006-03-09
The bad thing about this thread is it distracts me from my Computer Science project and makes me want to tweak my Dapper Drake installation...That being said, I only edited the config file and saved a copy as something in progress.  Hope this works Friday when I get to play around with it again.  
So far, very easy to use and well thought out.  Good practice for the new kids with learning how the xconfig file works.

---

### Post by salsafyren on 2006-03-09
I got this working using your howto. It's very cool!

I am using a Geforce 2 Pro/Ultra card and had to use the nvidia-glx-legacy driver.

The CPU load is pretty high, maybe a newer compiz will lower the load?

/Chris

---

### Post by Greg T. on 2006-03-09
A few tidbits:

I just tried the MAME (arcade emulator) in Compiz / XGL. Works, but some backgrounds are now completely translucent. Very strange, but oddly attractive.

From the freedesktop xorg mailing list: David Reveman says that "you'll see support for multiple screens sometime soon." [http://lists.freedesktop.org/archives/xorg/2006-March/013645.html](http://lists.freedesktop.org/archives/xorg/2006-March/013645.html) . That would seem to be good news.

There's been some initial success getting Compiz to run on AIGLX. [http://lists.freedesktop.org/archives/xorg/2006-March/013577.html](http://lists.freedesktop.org/archives/xorg/2006-March/013577.html) . Because AIGLX is a more incremental approach than XGL, it might eventually turn out to be the way many of us run Compiz. So it seems noteworthy.

Finally, it looks like there is some code sharing going on between AIGLX and XGL. See this thread: [http://lists.freedesktop.org/archives/xorg/2006-March/013624.html](http://lists.freedesktop.org/archives/xorg/2006-March/013624.html) . I haven't seen a good explanation of what's going on (seems like it has something to do with DRI), but something might be landing as early as tomorrow.

---

### Post by ae+ on 2006-03-09
hiya

i tried this about a week ago and X refused to load no matter what i did - in the end i just reinstalled dapper.  i'm using a NV43 [GeForce 6600], GV-NX66128DP Turboforce Edition.

my question is, has anyone with a 6600 had success and is the process (because of updates etc) less risky then it was say a week ago (i've noticed lots of updates coming down the line via apt-get)? I've made enough changes to my current system that i would hate to reinstall or spend a day in terminal mode :)

also - how far away is this process from becoming automated or because of the nature of it - is it too hard to make automated?

thanks
andrew

---

### Post by enzobelmont on 2006-03-09
today nvidia released new geforce GPUs: 7600 & 7900 with a new windows driver. do anyone knows if nvidia releades a new linux driver???

sorry my english...;)

---

### Post by SqRt7744 on 2006-03-09
Hey I'm having this wierd problem... 
When I minimize a window it just disappears!  Gone!  Poof!  No indication of its existence on the program bar thingy along the bottom of the screen (gnome).  In fact no windows, even open ones, show up on the bar along the bottom.  They're still running, as ps reports, but they are nowhere to be seen.  Does this happen to everybody, or is my computer being especially cruel to me?  Is there a keyboard shortcut to revive them again?  (Alt-tab doesn't help).

Other than that annoyance Xgl works great!  My MAC acquaintances are all indignant etc etc, still refuse to admit that Macs blow chunks because they invested too much money, y'know how it is.

---

### Post by drizek on 2006-03-10
[QUOTE=enzobelmont]today nvidia released new geforce GPUs: 7600 & 7900 with a new windows driver. do anyone knows if nvidia releades a new linux driver???

sorry my english...;)[/QUOTE]

not yet. 

a new driver should come out soon though, probably before the end of this month.

---

### Post by Sutekh on 2006-03-10
=D>   =D>   =D>

How on earth could something so freakin awesome become so easy to setup!

I finally stopped wobbling windows and taking focussed apps from one desktop to the next to post this   

....Firefox goes left, Firefox goes right, Firefox goes left, Firefox goes right...

Big thanks to PHG and contributors!!

---

### Post by merlyn on 2006-03-10
[quote=opera118]No. It's not an extension, it is in fact a new server. You don't start X (or implicitly with startx) but Xgl. A new server. That is, in my perspective the reason why a lot of things don't work well (mouse for me, keyboard for most, image damage). It is not an extension to the old X, you're refering to glx. That's the extension. Xgl is the new server.
Aiglx is an extension however. Hence my reason to post.



Xegl is "the nice way" of doing Xgl which is a hack right now. And as for as I know about dead, it's rather the other way around. The fedora people seems to work on the aiglx while novell works on xgl. Nvidia officially praises the aiglx thought over xgl, and might stop supporting xgl (I think) if aiglx turns out to work well. It works better with their driver development.

Don't get me wrong tho, I think Xgl is very interesting and it sure demonstrates what can be done. Still, I wonder if anyone got aiglx to work or if it's not up to par for usage yet.

EDIT: Also, X.org seems to be planning on releasing aiglx in the mainstream X.org, but not Xgl. This is reason enough to start investigating aiglx further.[/quote] 
[Here]("http://www.freesoftwaremagazine.com/free_issues/newsletters/accelerated_x/index_p1.html") is a useful article that describes 'in a nutshell', the differences between Xgl and aiglx.

Cheers.

---

### Post by F for Fragging on 2006-03-11
poofyhairguy, you rule! Thanks a lot!

[https://wiki.ubuntu.com/XglHowto](https://wiki.ubuntu.com/XglHowto) -> I tried this first, and it didn't work for me, X wouldn't start anymore. Maybe you should get your Xgl guide on that wiki page?

One more question, after I startup GNOME and before typing 'thefuture' in the terminal, the graphics on my desktop look corrupted (no window titles). After I type 'thefuture' everything is fine again. Is there any way to execute 'thefuture' automatically at startup?

---

### Post by vnbuddy2002 on 2006-03-11
Add the future command to your bashrc which locate in your home directory..


/home/`whoami`/.bashrc

---

### Post by QUASAR_FREAK on 2006-03-11
[QUOTE=F for Fragging]poofyhairguy, you rule! Thanks a lot!

[https://wiki.ubuntu.com/XglHowto](https://wiki.ubuntu.com/XglHowto) -> I tried this first, and it didn't work for me, X wouldn't start anymore. Maybe you should get your Xgl guide on that wiki page?

One more question, after I startup GNOME and before typing 'thefuture' in the terminal, the graphics on my desktop look corrupted (no window titles). After I type 'thefuture' everything is fine again. Is there any way to execute 'thefuture' automatically at startup?[/QUOTE]

Just add thefuture in gnome-session-properties in start programs

---

### Post by F for Fragging on 2006-03-12
Ok, thanks.

---

### Post by bashi on 2006-03-12
[http://img215.imageshack.us/img215/651/screenshot2no.png](http://img215.imageshack.us/img215/651/screenshot2no.png)

Hi guys :)

thx for your beautiful tutorial :)
but look, i've a little problem ;'(

Look on top of the window...
and it isn't work (deformations etc... ) 

Help me plz :)

bashi

---

### Post by DigitalDuality on 2006-03-12
:) and :(

I got it working and it's wonderful.  But one complaint.

Applications now seem to take longer opening.  I might get used to it.  But is there a reason for this?  I would think that adding in a 128mb nvidia card that this wouldn't be the case.

---

### Post by jcooper on 2006-03-13
[QUOTE=bashi][http://img215.imageshack.us/img215/651/screenshot2no.png](http://img215.imageshack.us/img215/651/screenshot2no.png)

Hi guys :)

thx for your beautiful tutorial :)
but look, i've a little problem ;'(

Look on top of the window...
and it isn't work (deformations etc... ) 

Help me plz :)

bashi[/QUOTE]

Is it just the window border is offscreen? If so, hold down control, then click and drag anywhere on the window to move it.

Otherwise, open a terminal and run gnome-window-decorator and see if there are errors.

---

### Post by DigitalDuality on 2006-03-13
^
I'm experiencing this problem too.. and it seems to only be in VLC.  The entire window bar is just completely missing.  It doesn't do this in any other app.  Not totem, kaffine, etc..


Also, before all this, i was able to watch dvds in Dapper.  Now i cannot.

---

### Post by jlintz on 2006-03-13
after my latest upgrade in dapper I noticed that the switcher no longer works and neither does the cube.  The plugins are shown in gconf as being loaded.  Anyone have any clues how to fix this?

---

### Post by jlintz on 2006-03-13
oh the cube works when I click on the desktop switcher applet, so it seems to be a problem with it recognizing the hot keys

--update , I got it working by changing the keyboard type in the gnome keyboard settings, xmodmap didn't seem to be enough

---

### Post by DagaZ on 2006-03-13
Everything.. almost everything, seems to work for me except the boring fact that I can't move the windows around at all. I can maximize the window by double-clicking but I can't seem to move it. Anyone else having this problem?

---

### Post by muldy on 2006-03-13
Hi!

Just installed drake and added the XGL, following this tutorial, all is working well...

Except now when i press shitft + backspace X crashes/closes?

Looks like a ctrl+alt+backspace

Does anyone else has this problem?

---

### Post by DigitalDuality on 2006-03-13
^
I've had that problem too.  And it's quite annoying.  If i'm typing (especially on forums or e-mails) i have a tendency to hold down shift while backspacing if i typed a capital letter somewhere.

For instance.

If i Type This.

Then wish to backspace and erase the word "This" i might hold down the shift key while doing so.  I managed to re-start X 7 times last night by accident b/c of this.

---

### Post by muldy on 2006-03-13
I solved my own problem:

you have to :
xmodmap /usr/share/xmodmap/xmodmap.pt

every session, im portuguese ;) = PT

---

### Post by fizz on 2006-03-13
This has been mentioned a ton in this thread, but the other person is correct, you need to run xmodmap everytime, however the better thing to do is modify your "thefuture" scripts, and add a line at the end

xmodmap /usr/share/xmodmap/xmodmap.<language>

This way you dont have to worry about it..




For those of you experiencing problems with not being able to move windows, and not having any window decorations, try this

Open gconf-editor
goto apps/compiz/general/allscreens/options

Active plugins, remove opacity, and then restart x (ctrl+alt+backspace) or simply logout and back in and see if that helps.

---

### Post by mstlyevil on 2006-03-13
[QUOTE=fizz]This has been mentioned a ton in this thread, but the other person is correct, you need to run xmodmap everytime, however the better thing to do is modify your "thefuture" scripts, and add a line at the end

xmodmap /usr/share/xmodmap/xmodmap.<language>

This way you dont have to worry about it..
[/QUOTE]

I just added both thefuture and the xmodmap command to the startup programs list seperately and they both work fine upon every boot.

---

### Post by chiisu on 2006-03-13
I got it successfully running on my GeForce6600  :)  However, a few niggles:

1. The key combos don't have any affect, not even Alt-Tab
2. Workspace Switcher isn't working right.  No matter what # of spaces I set it on, on the panel it has space for four workspaces, but it'll switch b/w those successfully w/ the neat spinning cube effect.
3. Gaim Away window is now fixed in the middle of the screen, it can't be moved or minimized
4. XaoS is now almost completely translucent, can hardly see anything

---

### Post by andradelipe on 2006-03-14
I have the same problems too =]
But I can't make anithing translucent. 
Somenthing like Alt+Shift+Scroll down/up?

---

### Post by zAo on 2006-03-14
[QUOTE=andradelipe]I have the same problems too =]
But I can't make anithing translucent. 
Somenthing like Alt+Shift+Scroll down/up?[/QUOTE]
Load the plugin manually. There is a thread about the plugin somewhere on the Dapper forums.

---

### Post by aamukahvi on 2006-03-14
[QUOTE=chiisu]I got it successfully running on my GeForce6600  :)  However, a few niggles:

1. The key combos don't have any affect, not even Alt-Tab
2. Workspace Switcher isn't working right.  No matter what # of spaces I set it on, on the panel it has space for four workspaces, but it'll switch b/w those successfully w/ the neat spinning cube effect.
3. Gaim Away window is now fixed in the middle of the screen, it can't be moved or minimized
4. XaoS is now almost completely translucent, can hardly see anything[/QUOTE]
1. you need to use the xmodmap tricks, see all over the forum :p
2. you need to set the workspaces with gconf (/apps/compiz/general/screen0/options/size) EDIT: (ah sorry misinterpreted)
3. Hold Alt then grab the window. To resize, hold Alt and use right mouse button
4. never heard of xaos, sorry. There are some problems with programs using other toolkits than gtk & qt. For example Pixel is see-through.

---

### Post by beerorkid on 2006-03-14
[QUOTE=zAo]Load the plugin manually. There is a thread about the plugin somewhere on the Dapper forums.[/QUOTE]

opacity plugin?  urvxt?

BTW this is really cool.  thanks for the great guide poofyhairguy

---

### Post by beerorkid on 2006-03-14
figuring this is what I am looking for:
[http://www.downwithnumbers.com/news.php?id=41](http://www.downwithnumbers.com/news.php?id=41)
will check it out

---

### Post by fizz on 2006-03-14
[QUOTE=andradelipe]I have the same problems too =]
But I can't make anithing translucent. 
Somenthing like Alt+Shift+Scroll down/up?[/QUOTE]

actually **ctrl+shift+scrollwheel** \\:D/

---

### Post by luposovs on 2006-03-14
[QUOTE=fizz]actually **ctrl+shift+scrollwheel** \\:D/[/QUOTE]
Actually Alt-o
             Alt-p :))

---

### Post by pwrstick on 2006-03-14
*Load the plugin manually. There is a thread about the plugin somewhere on the Dapper forums.*

Which plugin?  xmodmap?

---

### Post by chaumurky on 2006-03-14
Has there been any word on a fix for twinview users? Where should I look for updates on this issue?

---

### Post by enzobelmont on 2006-03-14
[QUOTE=pwrstick]*Load the plugin manually. There is a thread about the plugin somewhere on the Dapper forums.*

Which plugin?  xmodmap?[/QUOTE]

opacity external pluginis not needed more, now is integrated in compiz CVS.

---

### Post by vpit on 2006-03-14
Hello, I'm in need of some help.  2 weeks new to linux/ubuntu, windows sysadmin for a long time before.  I have been attempting to get this Xgl/Complix eye candy working, no luck.  Below is what I have run in terminal, note the errors related to font and font folders missing, can anyone direct??

much abliged!
*********************************************************************

chris@Dell9300:~$ #!/bin/sh
chris@Dell9300:~$ # Start up Xgl, compiz, and GNOME
chris@Dell9300:~$ # Run Xgl server on :1, on top of normal X
chris@Dell9300:~$ Xgl :1 -fullscreen -ac -accel xv:fdo -accel glx:pbuffer &
[1] 6627
chris@Dell9300:~$ # Tell subsequent X programs to access the Xgl server at :1
chris@Dell9300:~$ DISPLAY=:1
chris@Dell9300:~$ # Start Compiz window manager
chris@Dell9300:~$ gnome-window-decorator &
[2] 6628
chris@Dell9300:~$ compiz gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher &
[3] 6629
chris@Dell9300:~$ # Start GNOME
chris@Dell9300:~$ exec gnome-sessionCould not init font path element /usr/lib/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/lib/X11/fonts/OTF, removing from list!
Could not init font path element /usr/lib/X11/fonts/CID/, removing from list!

---

### Post by enzobelmont on 2006-03-15
[QUOTE=vpit]Hello, I'm in need of some help.  2 weeks new to linux/ubuntu, windows sysadmin for a long time before.  I have been attempting to get this Xgl/Complix eye candy working, no luck.  Below is what I have run in terminal, note the errors related to font and font folders missing, can anyone direct??

much abliged!
*********************************************************************

chris@Dell9300:~$ #!/bin/sh
chris@Dell9300:~$ # Start up Xgl, compiz, and GNOME
chris@Dell9300:~$ # Run Xgl server on :1, on top of normal X
chris@Dell9300:~$ Xgl :1 -fullscreen -ac -accel xv:fdo -accel glx:pbuffer &
[1] 6627
chris@Dell9300:~$ # Tell subsequent X programs to access the Xgl server at :1
chris@Dell9300:~$ DISPLAY=:1
chris@Dell9300:~$ # Start Compiz window manager
chris@Dell9300:~$ gnome-window-decorator &
[2] 6628
chris@Dell9300:~$ compiz gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher &
[3] 6629
chris@Dell9300:~$ # Start GNOME
chris@Dell9300:~$ exec gnome-sessionCould not init font path element /usr/lib/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/lib/X11/fonts/OTF, removing from list!
Could not init font path element /usr/lib/X11/fonts/CID/, removing from list![/QUOTE]
the font errors of OTF & CID aren't critical, you can run compiz without these font families

---

### Post by at10ti0n on 2006-03-15
denis@ubuntu:~$ sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome
Reading package lists... Done
Building dependency tree... Done
compiz is already the newest version.
E: Couldn't find package xserver-xgl

where is this xserver-xgl? :) i cant get past this...

[edit] the problem was that i needed to enable univers repositories... i got xgl working like a charm :) ... thanks so MUCH!!!!
btw ...  i  cant get  ctrl+alt+left/right arrow keys and all the other shortcuts working... should i set-up them from configuration editor?
[edit2] DONE!! its working... xmodmap /usr/share/xmodmap/xmodmap.ro :))

---

### Post by Bandit on 2006-03-15
Hello Everyone,
Forgive me if I missed this fix in the thread. I tried to read it the best I could since its 6am here.. To early for me..

I set everything up just like in the instructions, word for word, dot for dot and even triple checked everything.
But when I start the "thefuture" script metacity disapears and no other window manager appears.
Even the task bar dispears. 
When running the terminal I still do not get any error msg. I mean 0 error msg's.
I have to run "metacity --replace" to get my taskbar and and window frames back.

My video card is a Gigabyte nVidia FX5500, AGP8x, 256-DDR, DVI & VGA connectors (using DVI).

Of course you can see the rest of the system specs at the bottum.

Thanks,
Joey

---

### Post by beerorkid on 2006-03-15
so I have a logitech m510 mouse.  I have used this howto to fix the thumb buttons in many installs of breezy:
[http://ubuntuforums.org/showthread.php?t=65471](http://ubuntuforums.org/showthread.php?t=65471)

you mess with the settings in xorg.conf.  It does not seem to work anymore (get the borked xorg.config upon reboot).  I am figuring this has something to do with compiz/xgl.

No biggie cuz how fricking awesome my dapper/XGL machine is now.  just thought somebody might have a clue on it.

---

### Post by ToniVR on 2006-03-15
I have Xgl and Compiz up and running on 2 machines now, but om my laptop, it gave strange errors.
Xgl doesn't like non 4:3 resolutions, because 1920x1200 gave weird problems (gdm which was only shown in pieces, Gnome which had all f#cked up graphics). Changing to 1600x1200 solved that part.

So if you have a widescreen laptop, you will not be able to run on the widescreen resolution when using Xgl and Compiz. Hopefully that 'not' is a 'not yet'.

---

### Post by zAo on 2006-03-15
[QUOTE=ToniVR]I have Xgl and Compiz up and running on 2 machines now, but om my laptop, it gave strange errors.
Xgl doesn't like non 4:3 resolutions, because 1920x1200 gave weird problems (gdm which was only shown in pieces, Gnome which had all f#cked up graphics). Changing to 1600x1200 solved that part.

So if you have a widescreen laptop, you will not be able to run on the widescreen resolution when using Xgl and Compiz. Hopefully that 'not' is a 'not yet'.[/QUOTE]
I'm running Xgl + Compiz at 1680x1050 with no problems at all. Up and running for 2 weeks now, I think.

---

### Post by ndhskp on 2006-03-15
I had to uninstall this eye candy because it don't work with xine-ui and xmms very well on my computer.  The xine-ui had extreme corruption and xmms simply froze.

Also when I tried to move the window of a program and it becomes jello like, the waving sides of the windows have rips or tears.  That new live cd called korra or something does not have this problem.  You know the live cd that shows off xgl and all that, it don't have rips or tears.  I really wanted the eye candy but it seems I will have to wait another day.  Aww shucks.  :cry: 

[IMG]http://www.nathaniel-homier.net/images/xine-ui-corruption.png[/IMG]

---

### Post by mstlyevil on 2006-03-15
[QUOTE=ndhskp]I had to uninstall this eye candy because it don't work with xine-ui and xmms very well on my computer.  The xine-ui had extreme corruption and xmms simply froze.

Also when I tried to move the window of a program and it becomes jello like, the waving sides of the windows have rips or tears.  That new live cd called korra or something does not have this problem.  You know the live cd that shows off xgl and all that, it don't have rips or tears.  I really wanted the eye candy but it seems I will have to wait another day.  Aww shucks.  :cry:[/QUOTE]

I haven't found a fix for the control bar for xine but if you set the driver to open gl in the settings menu it will fix the choppy video problems and videos will play smooth. To access the menu right click on the screen and select settings-->setup. In the dialog box that opens go to video and on the very yop of the box is the driver setting. You will have to do this with each video player.

---

### Post by Vidar on 2006-03-15
[QUOTE=Bandit]Hello Everyone,
Forgive me if I missed this fix in the thread. I tried to read it the best I could since its 6am here.. To early for me..

I set everything up just like in the instructions, word for word, dot for dot and even triple checked everything.
But when I start the "thefuture" script metacity disapears and no other window manager appears.
Even the task bar dispears. 
When running the terminal I still do not get any error msg. I mean 0 error msg's.
I have to run "metacity --replace" to get my taskbar and and window frames back.

My video card is a Gigabyte nVidia FX5500, AGP8x, 256-DDR, DVI & VGA connectors (using DVI).

Of course you can see the rest of the system specs at the bottum.

Thanks,
Joey[/QUOTE]

I'm getting the exact same problem, everything seems to run fine except that the gnome-window-decorator doesn't work (but it is running). Only way to get back to a working desktop is by invoking "metacity --replace"...

I'm on a ASUS nVidia FX5700, AGP8x, 256-DDR, DVI & VGA.

Any ideas?

/Vidar

---

### Post by ndhskp on 2006-03-15
[quote=mstlyevil]I haven't found a fix for the control bar for xine but if you set the driver to open gl in the settings menu it will fix the choppy video problems and videos will play smooth. To access the menu right click on the screen and select settings-->setup. In the dialog box that opens go to video and on the very yop of the box is the driver setting. You will have to do this with each video player.[/quote]Thank you.  I know the keyboard shortcuts for xine so I will just use those for now.  So yes I re-setup the eye candy.

Does anybody know how to setup this eye candy in such a way that you don't need GDM.  I have removed the startup links in rc.d ect. for GDM because I prefer to boot into a console.  So in order to get the eye candy I have to type "sudo /etc/init.d/gdm start", that is not what I want to do.  I want to skip GDM completely and just use the "startx" command.  However if I use "startx" then I don't get the eye candy and it's a real chore to have to type "sudo /etc/init.d/gdm start" every time.

---

### Post by aamukahvi on 2006-03-15
[QUOTE=ndhskp]I want to skip GDM completely and just use the "startx" command.  However if I use "startx" then I don't get the eye candy and it's a real chore to have to type "sudo /etc/init.d/gdm start" every time.[/QUOTE]
Why don't you use a script like this:
```
#!/bin/bash
sudo /etc/init.d/gdm start
```
You can name it startxgl :mrgreen:

---

### Post by ndhskp on 2006-03-15
[quote=aamukahvi]Why don't you use a script like this:
```
#!/bin/bash
sudo /etc/init.d/gdm start
``` You can name it startxgl :mrgreen:[/quote]Awsome!  Just one thing though how would I set this script up so that I don't have to enter my password.  If it's not possible no big deal still saves on a ton of typing.

---

### Post by aamukahvi on 2006-03-15
[QUOTE=ndhskp]Awsome!  Just one thing though how would I set this script up so that I don't have to enter my password.  If it's not possible no big deal still saves on a ton of typing.[/QUOTE]
I guess you could modify the execute rights on gdm but somehow I feel that's highly unadvisable.
EDIT: It seems gdm is world-executable, but there's a reason it must be run as root. Someone else might be able to clarify...

---

### Post by ndhskp on 2006-03-15
[quote=aamukahvi]I guess you could modify the execute rights on gdm but somehow I feel that's highly unadvisable.[/quote]Ok your probably right about that, thanks anyway.  Love the script and I didn't realize bash was that easy so I will have to do some playing around with it.

---

### Post by beerorkid on 2006-03-16
when I tsclient (rdp) my winders HTPC it is about 50% transparent and it is really hard to work on.

Anybody else have this issue?

I has installed transset and the opaciry plugin.  I ran transet once in the term.  if that is any help.

I do not know what transset does or is capable of.

EDIT: when I use the default color depth it works.  Sure it is a little messed up, but I am not remoting into a winders box to play games when XGL is so cool.  
Still kind of a bug type thing.

---

### Post by obley on 2006-03-16
Am I missing something? I keep getting this...

```
obley@maximus:~$ sudo apt-get install compiz
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package compiz
obley@maximus:~$ sudo apt-get install xserver-xgl
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xserver-xgl

```

I have tried apt-get update. Am I missing somthing in my source list?

Other then Automatix and easy ubuntu, this is a pretty fresh install. 

thanks

---

### Post by Sutekh on 2006-03-16
Have you enabled the universe repositories?

You need to backup and edit your sources.list 
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo nano /etc/apt/sources.list
```
and uncomment (remove the #) in front of the lines containing **universe**.  Then update the sources.list
```
sudo apt-get update
```

---

### Post by nuzzy on 2006-03-16
Dumb question - g14 mentioned this in his post:


> 1.) ALT F2 and put in

[QUOTE]compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher
[/QUOTE]

What is "ALT F2" supposed to do?

---

### Post by aamukahvi on 2006-03-16
[QUOTE=nuzzy]What is "ALT F2" supposed to do?[/QUOTE]
"Run"

---

### Post by sniper85 on 2006-03-16
I was just wondering if this how to only applies to Dapper or can I try it under 5.10? Thanks.

---

### Post by nuzzy on 2006-03-16
[QUOTE=aamukahvi]"Run"[/QUOTE]


:(   Doesn't work for me...

---

### Post by beerorkid on 2006-03-16
[QUOTE=sniper85]I was just wondering if this how to only applies to Dapper or can I try it under 5.10? Thanks.[/QUOTE]

with some severe updating I have read it is possible.  But you basicaly dist-upgrade to do it.  So starting out with dapper might be your best bet.

---

### Post by sniper85 on 2006-03-16
Ok I thought so. Thanks

---

### Post by funkenstein on 2006-03-16
:confused: Strange thing - as soon as I add the ```
    Option         "RenderAccel"         "true"
    Option         "AllowGLXWithComposite" "true" 
``` lines to my xorg.conf, I lose all sight of my other tty's (1 through 6), although I can still type in them - as in I type blindly.

EDIT: running athlonXP2400/FX5700Ultra, forgot to mention, 
*and another thing*: 
```
Section "Device"
    Identifier    "NVIDIA Corporation NV36.1 [GeForce FX 5700 Ultra]"
    Driver        "nvidia"
**    BusID         "PCI:2:0:0"**
    Option        "RenderAccel"        "true"
    Option        "AllowGLXWithComposite"    "true"
EndSection
``` does anyone else have that busID?

---

### Post by Milamber_Cubed on 2006-03-16
[QUOTE=sniper85]I was just wondering if this how to only applies to Dapper or can I try it under 5.10? Thanks.[/QUOTE]

Yes :)

[http://www.ubuntuforums.org/showthread.php?t=133772](http://www.ubuntuforums.org/showthread.php?t=133772)

It's a bit buggy for me, but I think that's because of my graphics card being so lame (Intel i810 driver). Other people on the thread have had varying degrees of success with it as well.

---

### Post by Bandit on 2006-03-16
[QUOTE=Vidar]I'm getting the exact same problem, everything seems to run fine except that the gnome-window-decorator doesn't work (but it is running). Only way to get back to a working desktop is by invoking "metacity --replace"...

I'm on a ASUS nVidia FX5700, AGP8x, 256-DDR, DVI & VGA.

Any ideas?

/Vidar[/QUOTE]
At the momment I still dont know.
I thought it may have something to do with me using dist-upgrade. 
So I did a fresh install and will be trying it again.

---

### Post by poofyhairguy on 2006-03-16
[QUOTE=sniper85]I was just wondering if this how to only applies to Dapper or can I try it under 5.10? Thanks.[/QUOTE]

It only applies to Dapper. I recommend forcing XGL onto Breezy like I recommend putting a nail through your hand.

---

### Post by sniper85 on 2006-03-16
Ugh that makes the possible 6 week extension on the release of Dapper that much worse.

---

### Post by masooga on 2006-03-16
So I know I'm a newbie but I am trying my best to get to the level of fluency with ubuntu that I had with windows.  I figure the best way to do that is just to learn by doing.  

I followed all the instructions in the first post (except for the "thefuture" command) and I am left with  a distorted screen and no eyecandy.  I then tried to compile the newest version of glitz from cvs and I'm left with the same distorted screen.

My video card is a 256MB NVIDIA 6800 for Dell Inspiron.

Help please?

---

### Post by haputanlas on 2006-03-16
I have a Dell XPS Gen2 Laptop with a Geforce card. Everything from XGL and Compiz appears to be working fine. Unfortunately, I am receiving graphical clitches that are very similar to the users who are having Xine title bar issues. Only I am getting these glitches all over every app and the menus. I looked around for images that are similar to what I am having but with no luck. Is this common? and how do I fix this?

---

### Post by beerorkid on 2006-03-16
[QUOTE=sniper85]Ugh that makes the possible 6 week extension on the release of Dapper that much worse.[/QUOTE]

you can always grab flight 5, that is what I did

[http://www.ubuntu.com/testing/flight5?highlight=%28dapper%29](http://www.ubuntu.com/testing/flight5?highlight=%28dapper%29)

---

### Post by Sutekh on 2006-03-16
[QUOTE=nuzzy]Dumb question - g14 mentioned this in his post:

What is "ALT F2" supposed to do?[/QUOTE]

[quote=nuzzy] Doesn't work for me...[/QUOTE]

Alt + F2 actually means to press teh Alt and F2 keys on your keyboard.  It should open a small dialog box where you can enter the command.


[QUOTE=funkenstein]
*and another thing*: 
```
Section "Device"
    Identifier    "NVIDIA Corporation NV36.1 [GeForce FX 5700 Ultra]"
    Driver        "nvidia"
**    BusID         "PCI:2:0:0"**
    Option        "RenderAccel"        "true"
    Option        "AllowGLXWithComposite"    "true"
EndSection
``` does anyone else have that busID?[/QUOTE]
My BusID is "PCI:5:0:0", this is not a problem for me.  It probably depends on the motherboard as to where the graphics card is.

---

### Post by poofyhairguy on 2006-03-16
[QUOTE=masooga]So I know I'm a newbie but I am trying my best to get to the level of fluency with ubuntu that I had with windows.  I figure the best way to do that is just to learn by doing.  

I followed all the instructions in the first post (except for the "thefuture" command) and I am left with  a distorted screen and no eyecandy.  I then tried to compile the newest version of glitz from cvs and I'm left with the same distorted screen.

My video card is a 256MB NVIDIA 6800 for Dell Inspiron.

Help please?[/QUOTE]

You have to have the Nvidia drivers installed.

And you need thefuture

---

### Post by poofyhairguy on 2006-03-16
[QUOTE=haputanlas]I have a Dell XPS Gen2 Laptop with a Geforce card. Everything from XGL and Compiz appears to be working fine. Unfortunately, I am receiving graphical clitches that are very similar to the users who are having Xine title bar issues. Only I am getting these glitches all over every app and the menus. I looked around for images that are similar to what I am having but with no luck. Is this common? and how do I fix this?[/QUOTE]

You need to make sure your default color depth is 24 in your Xorg.conf.

---

### Post by haputanlas on 2006-03-16
[QUOTE=poofyhairguy]You need to make sure your default color depth is 24 in your Xorg.conf.[/QUOTE]



You are awesome! That fixed it.  Thanks a lot.

---

### Post by poofyhairguy on 2006-03-16
[QUOTE=haputanlas]You are awesome! That fixed it.  Thanks a lot.[/QUOTE]

No problem.

---

### Post by nuzzy on 2006-03-16
[QUOTE=Sutekh]Alt + F2 actually means to press teh Alt and F2 keys on your keyboard.  It should open a small dialog box where you can enter the command.[/QUOTE]

Yep, That I know - however it still doesn't bring anything up :-k

---

### Post by Sutekh on 2006-03-16
[QUOTE=nuzzy]Yep, That I know - however it still doesn't bring anything up :-k[/QUOTE]
Try checking the Run Application shortcut (Keyboard Prefs)?

---

### Post by masooga on 2006-03-16
[QUOTE=poofyhairguy]You have to have the Nvidia drivers installed.

And you need thefuture[/QUOTE]

So if I update my Nvidia drivers, follow the code including thefuture and then compile glitz from cvs, it should work?

---

### Post by nuzzy on 2006-03-16
[QUOTE=Sutekh]Try checking the Run Application shortcut (Keyboard Prefs)?[/QUOTE]
 
:(  It's listed but not working for me ::sigh::

Does anyone know what the actual command is so I can see if I can type it in a terminal window?

---

### Post by poofyhairguy on 2006-03-16
[QUOTE=masooga]So if I update my Nvidia drivers, follow the code including thefuture and then compile glitz from cvs, it should work?[/QUOTE]

Yes, you need to install the Nvidia drivers (I recommend the repo ones). For your card, don't compile glitz. Just leave that step out. Its not needed.

Just make sure your Xorg.conf is using the "nvidia" driver not the "nv" driver.

---

### Post by masooga on 2006-03-16
[QUOTE=poofyhairguy]Yes, you need to install the Nvidia drivers (I recommend the repo ones). For your card, don't compile glitz. Just leave that step out. Its not needed.

Just make sure your Xorg.conf is using the "nvidia" driver not the "nv" driver.[/QUOTE]

Okay, followed your instructions and when I typed in the xmod command it said:

hmasuga@Rilo:~$ xmodmap /usr/share/xmodmap.us
xmodmap:  unable to open file '/usr/share/xmodmap.us' for reading
xmodmap:  1 error encountered, aborting.

I typed in future and my toolbars went away.

Thank you so much for your help and patience, PHG. :-D

---

### Post by poofyhairguy on 2006-03-16
[QUOTE=masooga]Okay, followed your instructions and when I typed in the xmod command it said:

hmasuga@Rilo:~$ xmodmap /usr/share/xmodmap.us
xmodmap:  unable to open file '/usr/share/xmodmap.us' for reading
xmodmap:  1 error encountered, aborting.

I typed in future and my toolbars went away.

Thank you so much for your help and patience, PHG. :-D[/QUOTE]

Lets get this to work. 

Please install the Compiz packages from this thread, reboot and try to run the future again:

[http://ubuntuforums.org/showthread.php?t=139265](http://ubuntuforums.org/showthread.php?t=139265)

---

### Post by MetalMusicAddict on 2006-03-16
Just a FYI. I had to uninstall the Compiz and Compiz-gnome packages first before  the new ones would install right.

Hey PHG. I was hoping you would add the .debs from the link you posted to this HOWTO. :) So people would use them off the bat.

---

### Post by poofyhairguy on 2006-03-16
[QUOTE=MetalMusicAddict]
Hey PHG. I was hoping you would add the .debs from the link you posted to this HOWTO. :) So people would use them off the bat.[/QUOTE]

I'm scared of dependancy problems if I do that.

Soon I hope for a repo for this stuff, then I will tell people to add that.

---

### Post by MetalMusicAddict on 2006-03-16
[QUOTE=poofyhairguy]I'm scared of dependancy problems if I do that.

Soon I hope for a repo for this stuff, then I will tell people to add that.[/QUOTE]
Well if this helps any heres what I did yesterday. Installed Dapper-F5. Used your guide. Then installed the new .debs from the link with that new .deb installer. Nothing other than a base install was done then the XGL-Compiz stuff. *Then* I installed all my favorite apps. Everything is going great so far. :) Even after a dist-upgrade today.

---

### Post by mstlyevil on 2006-03-16
The new packages seem to be working fine on my system after replacing the version of compiz in poofy's guide. I am still using all his scripts and the xmodmap command.

---

### Post by funkenstein on 2006-03-17
Silly question in the vein of "Where is the *any* key?"... but in gconf, under the zoom plugin, I get *Initiate* as being *<Super>Button3* and *terminate* as being *<Release>Button3* . Now, when I change initiate to only be Button3 then the right click of my mouse zooms perfectly. so, the question is, what *is* the <Super> key? I've tried pretty much every combo I could think of, to no avail.... :-k

---

### Post by aamukahvi on 2006-03-17
[QUOTE=funkenstein]Silly question in the vein of "Where is the *any* key?"... but in gconf, under the zoom plugin, I get *Initiate* as being *<Super>Button3* and *terminate* as being *<Release>Button3* . Now, when I change initiate to only be Button3 then the right click of my mouse zooms perfectly. so, the question is, what *is* the <Super> key? I've tried pretty much every combo I could think of, to no avail.... :-k[/QUOTE]
Super is the Windows key.

---

### Post by masooga on 2006-03-17
[QUOTE=poofyhairguy]Lets get this to work. 

Please install the Compiz packages from this thread, reboot and try to run the future again:

[http://ubuntuforums.org/showthread.php?t=139265](http://ubuntuforums.org/showthread.php?t=139265)[/QUOTE]

Okay did that, when I run thefuture I get

hmasuga@Rilo:~$ compiz: GLX_EXT_texture_from_pixmap is missing
compiz: Failed to manage screen: 0
compiz: No managable screens found on display :0.0

and naturally my toolbar disappeared :)

---

### Post by wylie348 on 2006-03-17
Compiz works like a charm on my inspiron 8600 with nvidia go 5200.  Unfortunately my keyboard shortcuts do not work, and if I lock my screen, and then try to unlock I get a black screen and cannot access the machine unless I reboot?!
Thanks for any hints!
:-D

---

### Post by mega on 2006-03-17
I think it's working, compiz fires up, but cpu seems to be doing the work, is this normal?

with xgl/compiz I get this from glxinfo

name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
bunch of stuff...
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 7300 GS/PCI/SSE2
OpenGL version string: 1.2 (2.0.1 NVIDIA 81.78)

glxgears peaks the CPU at 100 %

if I start a normal session direct rendoring says Yes

everything works, but screensavers and glxgears are very slow, if I drag a window around really fast the cpu hits about 35 %

not sure if this is normal or not, it seems fine except for the screensavers are extreemly slow

---

### Post by aamukahvi on 2006-03-17
[QUOTE=mega]I think it's working, compiz fires up, but cpu seems to be doing the work, is this normal?

with xgl/compiz I get this from glxinfo
(INFO)

glxgears peaks the CPU at 100 %

everything works, but screensavers and glxgears are very slow, if I drag a window around really fast the cpu hits about 35 %[/QUOTE]
I think that's normal. At least I have the same symptoms. We have to get new drivers so that most everything is handled by the GPU.

---

### Post by WillemM on 2006-03-17
[QUOTE=poofyhairguy]I wish I knew the answer to both of these questions, as it affects me too. All I can say is to wait for the next set of drivers...[/QUOTE]

Just a quick note: You can move the dialogboxes, although not without using a keybinding. Press <Alt> and move the window. It works, even for windows without a border :)

---

### Post by aamukahvi on 2006-03-17
[QUOTE=WillemM]Just a quick note: You can move the dialogboxes, although not without using a keybinding. Press <Alt> and move the window. It works, even for windows without a border :)[/QUOTE]
But the real fun comes from alt-rightmousebutton-resizing those windows to a little capsule and THEN dragging them around :mrgreen:

---

### Post by slew on 2006-03-17
Am I the only one that got this error?

slew@pimpnet:~$ sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome
Reading package lists... Done
Building dependency tree... Done
compiz is already the newest version.
E: Couldn't find package xserver-xgl
E: Couldn't find package compiz-gnome

I have multi and universe repositories enabled. Where else can I find these files?

---

### Post by aamukahvi on 2006-03-17
[QUOTE=slew]Am I the only one that got this error?

slew@pimpnet:~$ sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome
Reading package lists... Done
Building dependency tree... Done
compiz is already the newest version.
E: Couldn't find package xserver-xgl
E: Couldn't find package compiz-gnome

I have multi and universe repositories enabled. Where else can I find these files?[/QUOTE]
They are in dapper/universe. Did you do an apt-get update?

---

### Post by slew on 2006-03-17
[QUOTE=aamukahvi]They are in dapper/universe. Did you do an apt-get update?[/QUOTE]

Sorry, my mistake. I'm using Breezy still, and in the swarm of all these commands and options I totally forgot this was a Dapper forum. 

I did, however, get the Xgl to work in Breezy. Thanks!

---

### Post by nchase on 2006-03-17
Xgl works for me, but a lot of the effects do not work. When I try to rotate the desktop using CTRL + ALT + arrow nothing happens. The same goes for a few of the other affects. I do have the F12 Expose feature though...anyone know why some of these aren't working for me?

---

### Post by poofyhairguy on 2006-03-17
[QUOTE=masooga]Okay did that, when I run thefuture I get

hmasuga@Rilo:~$ compiz: GLX_EXT_texture_from_pixmap is missing
compiz: Failed to manage screen: 0
compiz: No managable screens found on display :0.0

and naturally my toolbar disappeared :)[/QUOTE]

Just keep trying. Sometimes it does not work teh first time.

---

### Post by masooga on 2006-03-18
[QUOTE=poofyhairguy]Just keep trying. Sometimes it does not work teh first time.[/QUOTE]

PHG you're the best thing since sliced bread.  I reinstalled the compiz packages (not from source this time) and it worked like a charm, first try.  This is a thing of beauty, thank you so much!

---

### Post by poofyhairguy on 2006-03-18
[QUOTE=masooga]PHG you're the best thing since sliced bread.  I reinstalled the compiz packages (not from source this time) and it worked like a charm, first try.  This is a thing of beauty, thank you so much![/QUOTE]

Thanks. I do my best to help the community in the areas I actually can.

---

### Post by cerebrix on 2006-03-18
0_o

holy crap this is my computer doing this killer stuff?  huh?

wow man thanks for the faq seriously this rocks.

quick question.  do you know if the enable sli extension works in the drivers in the repos?

---

### Post by krusbjorn on 2006-03-18
Now i've been giggling like a little girl, playing with the effects for half an hour. Enough of that, and on to the problems ;)

The theme manager crashes all the time. The default human theme seems to be the only one working. Before I installed xgl and compiz, I used clearlooks (with the *blended *window borders), but with xgl/compiz, i got no window title bar or borders at all, meaning i couldnt resize, minimize or close windows except from the menus. The human theme in dapper looks really neat (and works great), but does anyone know how to make it work with clearlooks?

PHG, lemme buy you a pizza if you ever end up in sweden.

---

### Post by Hender on 2006-03-18
:KS

This is amazing! I didn't have an Nvidia card , but I just had to try ... and your howto was by far the most comprehensible, so I followed your instructions.

Every single effect works (though there are bugs, especially with the Expose thing), but my real problem is that it seems to be slow. This is maybe because I have an intel integrated graphics card.

Just want to say thanks for the great howto, though! I will show it to everyone who is impressed by this sort of stuff! :D

---

### Post by adprs4 on 2006-03-18
[QUOTE=varunus]Is anyone else having glx crashes with compiz on?  GLX works just fine when metacity is run as the window manager; compiz is what triggers the crashes.  (Anything that uses opengl, be it glxgears or the screensaver, causes the crash.)[/QUOTE]

I started to experience that with the screensaver flurry. I thought it was due to something with power management, but that wasn't the case.

I'm also having issues with mythfrontend and anything fullscreen plays behind the top and bottom panel bars, but I may be mentioning that prematurely as I have yet to search on a solution.

I have an nvidia fx5700, 1.7ghz pentium 4 mobile, 1gb ram, 250gb sata seagate hd. Running breezy with 2.6.12-10.

Oh yeah. GREAT how-to. Worked flawlessly (as far as the install goes).

---

### Post by adprs4 on 2006-03-18
**nchase:**

The only thing I could think of were the settings in gconf-editor (if you're using gnome) Applications -> System Tools -> Configuration Editor -> apps -> compiz -> plugins and check out the stuff in there. Did you follow thefuture script exactly?

---

### Post by Brunellus on 2006-03-18
[QUOTE=beerorkid]so I have a logitech m510 mouse.  I have used this howto to fix the thumb buttons in many installs of breezy:
[http://ubuntuforums.org/showthread.php?t=65471](http://ubuntuforums.org/showthread.php?t=65471)

you mess with the settings in xorg.conf.  It does not seem to work anymore (get the borked xorg.config upon reboot).  I am figuring this has something to do with compiz/xgl.

No biggie cuz how fricking awesome my dapper/XGL machine is now.  just thought somebody might have a clue on it.[/QUOTE]
Just wanted to say the thumb buttons issue is something I have observed, also.  For the moment, it means that I'm switching my default browser to firefox instead of epiphany (the mousegestures extension in firefox takes care of this by giving me opera-like "mousewalking" through the history), but I'd be interested to hear if this is really an XGL issue, or if it's just me being retarded.

---

### Post by Hender on 2006-03-18
So I've tested Compiz and Xgl a bit more rigirously now, and I've found a few peeves:
[LIST=1]
[*]The screensaver is slow and doesn't work properly.
[*]Big windows don't wobble properly, and are generally slow.
[*]Dialogs never have any buttons, which renders Inkscape, for instance, useless.
[*]The Zoom plugin doesn't work ... it's meant to zoom at Super + Right click, but it doesn't.
[/LIST]
I can live with all of them, but if anyone has some magic tricks to make them go away, then that would be awesome. :cool: If not, it can stand as a warning to those who have yet to try Compiz. :D

---

### Post by sailor420 on 2006-03-18
Managed to get this installed with a minimum of fuss; it was much easier than I had thought.

I really like it--it's unlike anything I've ever seen on Linux. It's still buggy as hell, and like Hender said, it doesn't work great all the time, but it's definitely fun to play with, and works well enough that you can actually use it.

---

### Post by krusbjorn on 2006-03-19
[QUOTE=Hender][*]The Zoom plugin doesn't work ... it's meant to zoom at Super + Right click, but it doesn't.[/QUOTE]

System->Preferences->Keyboard->Layout Options->Alt/Win key behavior->"Meta is mapped to the win keys" did the trick for me.

---

### Post by Hender on 2006-03-19
[QUOTE=krusbjorn]System->Preferences->Keyboard->Layout Options->Alt/Win key behavior->"Meta is mapped to the win keys" did the trick for me.[/QUOTE]
That worked, thanks a bunch!

---

### Post by sYs^ on 2006-03-19
Hi!

I can't understand this:

```
$ thefuture
$ compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
```

I have NVidia 6600 GT, my xorg.conf:

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"

        # path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "hu"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Emulate3Buttons" "false"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Driver         "nvidia"
    Option         "NvAgp" "true"
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "FlatPanel" "true"
    Option         "NoLogo"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    #SubSection     "Display"
    #    Depth       1
    #    Modes      "1280x1024" "1024x768" "800x600" "640x480"
    #EndSubSection
    #SubSection     "Display"
    #    Depth       4
    #    Modes      "1280x1024" "1024x768" "800x600" "640x480"
    #EndSubSection
    #SubSection     "Display"
    #    Depth       8
    #    Modes      "1280x1024" "1024x768" "800x600" "640x480"
    #EndSubSection
    #SubSection     "Display"
    #    Depth       15
    #    Modes      "1280x1024" "1024x768" "800x600" "640x480"
    #EndSubSection
    #SubSection     "Display"
    #    Depth       16
    #    Modes      "1280x1024" "1024x768" "800x600" "640x480"
    #EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

I tried to run the command for hundread times 

Could it be a problem, i dont have this file: libGL.so.1.2 ?

What could be the problem?

---

### Post by t_z on 2006-03-19
sYs^,

```
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
```

I was having the same problem when I came across your post a few hours ago.  Your mention of libGL.so.1.2 gave me an idea.

The package libgl1-mesa, which I have installed, is supposed to contain libGL.so.1.2, but I too was missing this file (anyone know why?).  Reinstalling the package did not help.  Instead, I manually extracted it to a temporary directory and copied the file over:
```
dpkg --extract /var/cache/apt/archives/libgl1-mesa_6.4.1-0ubuntu6_i386.deb tempdir
sudo cp -a tempdir/usr/lib/libGL.so.1.2 /usr/lib/
sudo chown root:root /usr/lib/libGL.so.1.2
rm -rf tempdir
```
I did not update any symlinks.  libGL.so.1 still points to libGL.so.1.0.8178 as before, otherwise I found Xgl wouldn't start.

compiz.real now works like a charm!  I must say, it is suprisingly fast, even on my GeForce FX 5200.  Good stuff!

t_z

P.S. I would have responding to you sooner, but I was having too much fun playing with the spinning cube! \\:D/

---

### Post by Fudgie on 2006-03-19
[QUOTE=Hender]So I've tested Compiz and Xgl a bit more rigirously now, and I've found a few peeves:
[LIST=1]
[*]Dialogs never have any buttons, which renders Inkscape, for instance, useless.
[*]The Zoom plugin doesn't work ... it's meant to zoom at Super + Right click, but it doesn't.
[/LIST]
[/QUOTE]

Try Alt-F4 to close dialogs without buttons. To move them, alt-leftclick & move mouse.
Make sure you're running a 105 key keyboard and not a 101/102 key one to enable the super (windows) key.

---

### Post by sYs^ on 2006-03-19
no problem, i just figured it out too, it's working fine now for me too :p

when i scroll in firefox it's shacking a little , is it possible to fix it?

---

### Post by thoffmeyer on 2006-03-19
Awsome guide, works like a charm on my 6600gt :)

---

### Post by sYs^ on 2006-03-20
Hi!

[IMG]http://phun.sysonline.hu/temp/xgl.jpg[/IMG]

Is this normal on fullscreen movie playing? (with gmplayer)
The audio is being played normaly but the video starts to late.

My comp: 
[LIST]
[*]Athlon 2500+ @ 2300 MHz
[*]Gefore 6600 GT
[*]512 DDR
[/LIST]

If i turn off Xgl everything is ok

---

### Post by guzerat on 2006-03-20
[QUOTE=sYs^]Hi!

[IMG]http://phun.sysonline.hu/temp/xgl.jpg[/IMG]

Is this normal on fullscreen movie playing? (with gmplayer)
The audio is being played normaly but the video starts to late.

My comp: 
[LIST]
[*]Athlon 2500+ @ 2300 MHz
[*]Gefore 6600 GT
[*]512 DDR
[/LIST]

If i turn off Xgl everything is ok[/QUOTE]

Try using gl2 for video output

---

### Post by sYs^ on 2006-03-20
Thanks for the quick answer, but i'm kinda noob :D so, where can I set that?

Edit: ok , I found it: -vo gl2

eh: Error opening/initializing the selected video_out (-vo) device.

---

### Post by guzerat on 2006-03-20
[QUOTE=sYs^]Thanks for the quick answer, but i'm kinda noob :D so, where can I set that?

Edit: ok , I found it: -vo gl2

eh: Error opening/initializing the selected video_out (-vo) device.[/QUOTE]

strange... are you running mplayer as root or something? you could also try out -vo x11

---

### Post by sYs^ on 2006-03-20
I'm running it as a normal user, x11 is working but same problem as before :\

---

### Post by guzerat on 2006-03-20
[QUOTE=sYs^]I'm running it as a normal user, x11 is working but same problem as before :\[/QUOTE]

I'm getting about the same for Xgl but only like 8-9% for mplayer when running fullscreen with x11... and my specs are not impressive :)

p3 733Mhz
geforce 256 ddr
576 Mb

---

### Post by eqisow on 2006-03-20
Everything is working great for me (with a GeForce MX440, for reference) except the cube thingy. Fopr some reason whenever gnome starts the number of virtual desktops always gets set to one. I can set it to four, but at this point it seems a bit late for the cube to be implemented; and it goes right back to one if I restart gnome. Any ideas?

---

### Post by straver on 2006-03-20
[QUOTE=sYs^]no problem, i just figured it out too, it's working fine now for me too :p

when i scroll in firefox it's shacking a little , is it possible to fix it?[/QUOTE]
Have you tried using the official firefox version instead of dapper's. I found it to scroll much smoother.

edit: take a look at this [thread]("http://www.ubuntuforums.org/showthread.php?t=134627")

---

### Post by shenki on 2006-03-20
I have been using Xgl on dapper since compiz came out, and have always experienced slowdowns - specifically, whenever the CPU usage gets hight, it seemed that Xgl would fight to use more CPU, resulting in a very slow desktop.

After many hours of fiddling, I gave up. Stoped using Xgl, and settled with plain xorg.

But today, while reading through the mailing list ([http://bhhdoa.org.au/pipermail/ck/](http://bhhdoa.org.au/pipermail/ck/), thread titled "Xgl and process starvation") of the ck kernel patchset, I found a small gem. Specifically, they discovered that the nvidia driver was making bad system calls which resulted in Xorg having less CPU time than it deserved. A fix for this was posted to the mailing list, that patched the kernel, however it is unnecessary as there has been a fix commited to Xgl cvs fixing the problem. Alteast until Nvidia releases a fixed version of their driver.

Yay for open source! Boo for binary only drivers.

---

### Post by sYs^ on 2006-03-21
[QUOTE=straver]Have you tried using the official firefox version instead of dapper's. I found it to scroll much smoother.

edit: take a look at this [thread]("http://www.ubuntuforums.org/showthread.php?t=134627")[/QUOTE]

thanks, i'll try it

---

### Post by magomago on 2006-03-22
a

---

### Post by idn on 2006-03-23
I was wondering if anyone knows how to fix the super key problem - my superkey doesnt work on my keyboard  - so I cant zoom in, anybody have any recommendations on what to do?

---

### Post by krusbjorn on 2006-03-23
Look in System->Preferences->Keyboard->Layout Options or change the zoom hotkey in gconf-editor (apps->compiz->plugins->zoom)

---

### Post by Sonique on 2006-03-23
Does anyone know anything about my problem: (sorry if this is a repeat but i don't have the time to read 50 or so pages of this thread)

```

$ thefuture
$ compiz.real: GLX_EXT_texture_from_pixmap is missing compiz.real: Failed to manage screen: 0 compiz.real: No managable screens found on display :0.0
```

Cheers

---

### Post by vendetta red on 2006-03-23
[QUOTE=Sonique]Does anyone know anything about my problem: (sorry if this is a repeat but i don't have the time to read 50 or so pages of this thread)

```

$ thefuture
$ compiz.real: GLX_EXT_texture_from_pixmap is missing compiz.real: Failed to manage screen: 0 compiz.real: No managable screens found on display :0.0
```

Cheers[/QUOTE]

You could just try using the search thread button and that error line.....

---

### Post by fabs0028 on 2006-03-23
[QUOTE=Sonique]Does anyone know anything about my problem: (sorry if this is a repeat but i don't have the time to read 50 or so pages of this thread)

```

$ thefuture
$ compiz.real: GLX_EXT_texture_from_pixmap is missing compiz.real: Failed to manage screen: 0 compiz.real: No managable screens found on display :0.0
```

Cheers[/QUOTE]

It is a problem with the opengl libs your are trying to use when you launch compiz ... what is your system? have you installed the latest mesa packages gave with xgl and how are you launching compiz ?

---

### Post by idn on 2006-03-23
[QUOTE=krusbjorn]Look in System->Preferences->Keyboard->Layout Options or change the zoom hotkey in gconf-editor (apps->compiz->plugins->zoom)[/QUOTE]

Thanks this is working now, altough the zoom isnt that smooth, kinda jumps right in or out, now way to smooth zoom in

---

### Post by krusbjorn on 2006-03-23
[QUOTE=idn]Thanks this is working now, altough the zoom isnt that smooth, kinda jumps right in or out, now way to smooth zoom in[/QUOTE]

I dont think it is meant to "smooth zoom". You should be able to zoom in three times from normal view.

---

### Post by web250 on 2006-03-23
You probably get asked this a lot, but none of my keyboard shortcuts work (ctrl-alt-arrow, f12, nothing)...

Everything else works great, and looks phenominal. How do I get the keys to work?
Yes, I ran the xmodmap command

---

### Post by bbzbryce on 2006-03-23
I have a similar problem.  If I run xmodmap /usr/share/xmodmap/xmodmap.us then I cannot use <Control><Alt>left/right to move around and my other short cuts do not work. However the odd thing is if i <Control><Alt> and drag the mouse then the cube will move around, and if I don't let go of control and alt I can then use the over keys. However not being able to alt-tab I am better off not running xmodmap /usr/share/xmodmap/xmodmap.us

But I have the <Shift><Backspace> problem.  Is there a way to fix the shift backspace problem without compromising other shortcuts?

Thanks.

---

### Post by web250 on 2006-03-23
Fixed it with:
setxkbmap -model pc104 -layout us

did that twice, then it worked. 
XGL is impressive.

---

### Post by web250 on 2006-03-23
XGL breaks my TV Tuner...
I get sound, but no video. Anyone wanna take a guess at this one?

Also: Tuner does not work when XGL is unloaded.

---

### Post by cerebrix on 2006-03-23
try using an opengl renderer as the output for your tv tuner software

---

### Post by web250 on 2006-03-24
[QUOTE=cerebrix]try using an opengl renderer as the output for your tv tuner software[/QUOTE]
Could you suggest something?

---

### Post by mehaga on 2006-03-25
I can't reed through all the 80+ pages of the thread to find out if someone else had this problem, so I'll just ask, ok? :)
First of all, thanks for great tutorial :)

Java (swing) apps don't work with this setting. Netbeans, for example. You see the main window but not the widgets inside it :S Eclipse, on the other hand, works as it used to, so I guess only swing apps are affected.

I set everyhing up at 4 AM, together with upgrade from breezy to dapper, so I wasn't thinking about what I was doing. But, if I understand well, compiz thing is started when you type 'thefuture'. Well, if that is the case, compiz makes no diference cause netbeans doesn't work even if you start it before compiz.

Any suggestions on how to fix this?

One more thing. Is there any way to configure compiz, change or modify effects?
Any online guides about this?

PS It looks beautifull :)

---

### Post by krusbjorn on 2006-03-25
[QUOTE=vekaz]Java (swing) apps don't work with this setting. Netbeans, for example. You see the main window but not the widgets inside it :S Eclipse, on the other hand, works as it used to, so I guess only swing apps are affected.

One more thing. Is there any way to configure compiz, change or modify effects?
Any online guides about this?[/QUOTE]

Do a forum search for "java swing compiz" and then search the threads if they are too long. There has been some discussion about this :)

To configure your compiz settings go to Applications->System Tolls->Configuration Editor. Then make your way through Apps->Compiz-> and there you have it. It looks a little complicated at first but you will get the hang of it.

---

### Post by bogoliubov on 2006-03-25
Nice guide!
However my X server won't start after I have edited the gdm-conf-custom file.
If I comment out the 
[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true
it works...

Also, after I had set up my xorg.conf (with the nvidia utility) I have this as device section:

Section "Device"
    Identifier     "NVIDIA Corporation NV40? [Unknown nVidia Card]"
    Driver         "nvidia"
    BusID               "PCI:1:0:0"
    Option              "RenderAccel"           "true"
    Option              "AllowGLXWithComposite" "true"
EndSection

I have an Asus N6200 card, but what should I put in the Identifer? Does it matter what I put there or is it just for info?

---

### Post by bogoliubov on 2006-03-25
I got it working now, seems I hadn't edited /etc/apt/sources.list before installing stuff...

The Identifier I still don't know about though...

---

### Post by foundation on 2006-03-25
i receive this error when trying to install xgl.
> sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome
Reading package lists... Done
Building dependency tree... Done
compiz is already the newest version.
E: Couldn't find package xserver-xgl
fresh install of dapper too. D:

---

### Post by mehaga on 2006-03-25
[QUOTE=krusbjorn]Do a forum search for "java swing compiz" and then search the threads if they are too long. There has been some discussion about this :)

To configure your compiz settings go to Applications->System Tolls->Configuration Editor. Then make your way through Apps->Compiz-> and there you have it. It looks a little complicated at first but you will get the hang of it.[/QUOTE]

Thanks :)

I don't have Configuration Editor in my menu :(

---

### Post by krusbjorn on 2006-03-25
[QUOTE=vekaz]I don't have Configuration Editor in my menu :([/QUOTE]

Are you using gnome or KDE? If you are in gnome, run gconf-editor from a terminal. If you are in kde, i cant help you :P

---

### Post by MetalMusicAddict on 2006-03-25
Im tryin to work out some bugs with my laptop. Its not an nVidia card though. Intel "i810" driver is what Im using.

I followed the guide except installing nVidia drivers. When I try to run **thefuture** I get:

```
[SIZE="1"]user@PC:~$ thefuture
/usr/bin/thefuture: line 1: !/bin/bash: No such file or directory
mma@ash:~$ gnome-window-decorator, Failed to load shadow images
compiz.real: No composite extension[/SIZE]
```
So I added:

```
[SIZE="1"]
Section "Extensions"
          Option  "Composite" "Enable"
EndSection[/SIZE]
```

Then X wont start. If I comment out those 3 lines X will run but **compiz.real: No composite extension**.

```
[SIZE="1"]# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option 		"RenderAccel" 		"true"
	Option 		"AllowGLXWithComposite" "true" 
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

#Section "Extensions"
#          Option  "Composite" "Enable"
#EndSection[/SIZE]

```

Any Ideas? Im hoping to get a good guide together.

---

### Post by mehaga on 2006-03-25
[QUOTE=krusbjorn]Are you using gnome or KDE? If you are in gnome, run gconf-editor from a terminal. If you are in kde, i cant help you :P[/QUOTE]

I knew that! I don't need your help! :-D 

Thanks again

PS GNOME, after few years of KDE ;)

---

### Post by Skerit on 2006-03-25
It's just not working... I might have done it in a wrong order, I installed the files from the "XGL CVS faster" thread first and all but still, after a lot of tweaking it still does not work, the GDM doesn't even want to start so... shouldn't someone make a new thread with new installation guidelines? Dapper has gotten so many updates these last 2 weeks, which is perfectly normal, that I doubt everything is as compatible as it should, and I don't really want to read 85 pages worth of posts :S

It worked perfectly 2 weeks ago though ..

---

### Post by krusbjorn on 2006-03-25
I'm running it without problems on a dapper installation i dist-upgrade every day, so there shouldnt be any issues there. Try posting your hardware specs as well as the error messages you got and people might be able to help you. Also, check out [QuinnStorms repos]("http://ubuntuforums.org/showthread.php?t=148472").

---

### Post by bogoliubov on 2006-03-26
This is really nice and cool! Looks better than OSX, though it still needs a bit of polishing perhaps. What I still miss is the "active corners" that I have in OSX, that is really a nice thing when switching applications.

Also, an Exposé thing but with all workspaces next to each other at the same time would be really practical.

I have noticed some strange things though.
When I run xlg and compiz, unreal tournament 2004 doesn't work very well; the textures are screwed up and everything is really slow. Why is it like this?

And the nvidia-settings can't do anything, only minimal info is displayed. 

Also, when I watch a movie in Mplayer and switch from fullscreen to windowed mode, the last fullscreen frame is still displayed in the background. Moving some window about erases this, but it is still a bug I guess...

Another question in case someone knows: the nvidia-xconfig couldn't find my card. So in xorg.conf my identifier is "NVIDIA Corporation NV40? [Unknown nVidia Card]". How can I find out what to change it to, and does it really matter what the Identifier says?  I have an Asus N6200 card.

Anyway, it seems that Dapper can be really cool!

---

### Post by FFuser on 2006-03-26
Hi
I have one problem:
I'm using the computer with multiple users. When the user who logins first lock his screen, and someone else change user and login, the new login is started in Xorg. (So only the first user have compiz)
Someone knows how I can start Xgl as standard?

---

### Post by GAMaus on 2006-03-26
Hi! 
I noticed that opengl apps like xscreensaver and glxgears kill my Xserver everytime i try to run them.

I found out how to solve the Problem:

In the howto on the first page it says to use the following lines in gdm.conf-custom:
```
[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo 
flexible=true
```

I use the following lines instead and everything works fine:
```
[server-Xgl] 
name=Xgl server 
**command=/usr/bin/Xgl :0 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer**
flexible=true

```

Hope that helps!

---

### Post by g14 on 2006-03-26
[QUOTE=bogoliubov]This is really nice and cool! Looks better than OSX, though it still needs a bit of polishing perhaps. What I still miss is the "active corners" that I have in OSX, that is really a nice thing when switching applications.
[/QUOTE]
[http://www.ubuntuforums.org/showthread.php?t=148351](http://www.ubuntuforums.org/showthread.php?t=148351) CTRL F MacOS and you will find what you are looking for :-)

---

### Post by bogoliubov on 2006-03-27
[QUOTE=g14][http://www.ubuntuforums.org/showthread.php?t=148351](http://www.ubuntuforums.org/showthread.php?t=148351) CTRL F MacOS and you will find what you are looking for :-)[/QUOTE]

Thank's! I'll try that when I come home from work today.

---

### Post by GAMaus on 2006-03-27
Does anyone know how (or where) to get the water effect in this Video? :
[http://www.heartsaffection.com/Xgl.Compiz.Xdesktopwaves.Cairo-clock.mpeg](http://www.heartsaffection.com/Xgl.Compiz.Xdesktopwaves.Cairo-clock.mpeg) (25MB)

And where can i get new compiz plugins?


GAMaus

---

### Post by muted on 2006-03-28
haha... this didnt work pretty fast

> jacob@ubuntu:~$ sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package compiz


---

### Post by poofyhairguy on 2006-03-28
[QUOTE=GAMaus]Does anyone know how (or where) to get the water effect in this Video? :
[http://www.heartsaffection.com/Xgl.Compiz.Xdesktopwaves.Cairo-clock.mpeg](http://www.heartsaffection.com/Xgl.Compiz.Xdesktopwaves.Cairo-clock.mpeg) (25MB)
[/QUOTE]

In my guide:

[http://www.ubuntuforums.org/showthread.php?t=112333](http://www.ubuntuforums.org/showthread.php?t=112333)

---

### Post by kosac on 2006-03-29
i have used the "thefuture" command  more than 100 times and it still doesnt work :(

i get the following message:

gnome-window-decorator: Another window decorator is already running
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

can anyone help me? :s

thanks

---

### Post by mstlyevil on 2006-03-29
[QUOTE=kosac]i have used the "thefuture" command  more than 100 times and it still doesnt work :(

i get the following message:

gnome-window-decorator: Another window decorator is already running
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

can anyone help me? :s

thanks[/QUOTE]

Update XGL/Compiz to the latest packages. Here is the link to get those packages.

[http://www.ubuntuforums.org/showthread.php?t=148472]("http://www.ubuntuforums.org/showthread.php?t=148472")

---

### Post by kosac on 2006-03-29
a thousand thanks!!!!!!! 

btw, how can i make it default on startup?

---

### Post by mstlyevil on 2006-03-29
[QUOTE=kosac]a thousand thanks!!!!!!! 

btw, how can i make it default on startup?[/QUOTE]

Just go to System-->Preferences-->Sessions and click on the stratup programs tab. Then you just click Add and type thefuture into the dialog box then click OK. You can also add your xmodmap command to keep from crashing X when you hit Alt+Backspace. After that Compiz will work upon every startup.

---

### Post by Grog140 on 2006-03-29
When using the command to install XGL I get:

E: Couldn't find package compiz

Anyone know whats up?

---

### Post by mips on 2006-03-30
Before I start I would like to apologise for not reading the entire thread.

Will this guide work if I have the latest nvidia drivers installed as per the guide by tseliot ???
Will it overwrite the nvidia driver with the standard nv one ???

---

### Post by t-mow on 2006-03-30
hi there... 

first: sorry for my English, i'm from Germany, hope you might understand me anyway ;)

I installed XGL by using the HowTo from [https://wiki.ubuntu.com/XglHowto]("https://wiki.ubuntu.com/XglHowto") ... i've also updated to the newest version of compiz and xserver-xgl (a link has been postet in this forum...) When i log out and type in "compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher" i get this message: compiz.real: Couldn't open display. 

I already used the search function here, but i didn't find anything helping me out... I'm using a Nvidia 4200Ti with 64 MB!

Here is my xorg.conf: [http://timoziemann.de/xorg.conf]("http://timoziemann.de/xorg.conf")

Hope you will help me..

---

### Post by t-mow on 2006-03-30
I got it ;) (it was the mesa problem)

Anyways, videos are very slow... :-|

---

### Post by robio376 on 2006-03-30
Anybody know how to totally undo the installation? Or better yet help me fix mine? After the reboot I only get console..no gdm. Tried startx and I get the no monitors found error. Using a FX 5200. thanks

---

### Post by robio376 on 2006-03-30
[QUOTE=robio376]Anybody know how to totally undo the installation? Or better yet help me fix mine? After the reboot I only get console..no gdm. Tried startx and I get the no monitors found error. Using a FX 5200. thanks[/QUOTE]
I am using Dapper also

---

### Post by bryanchapman9999 on 2006-03-30
Works great here. 

Dapper with Nvidia 440SE card....some questions....

How can I have gkrelm showing on every desktop without multiple instances of it?

Can I turn the cube off and just have normal desktop switching?

Can I use sloppy focus somehow?

And finally, can I still use a double click on the window title to shade the window.

BTW these things are only minor and it all looks amazing - many thanks for the thread.

Thanks in advance
bryan

---

### Post by Milamber_Cubed on 2006-03-31
[QUOTE=robio376]I am using Dapper also[/QUOTE]

If you followed this guide correctly, all you should have to do is undo the changes to the xorg.conf (you made a backup, right?) and remove/rename the /etc/gdm/gdm.conf-custom file. Then reboot or restart gdm. Should do the trick.

EDIT: You might not actually need to undo the xorg.conf changes - I didn't - I just put that in for completeness , in case simple renaming the gdm file doesn't do it.

---

### Post by bryanchapman9999 on 2006-03-31
[QUOTE=bryanchapman9999]Works great here. 

Dapper with Nvidia 440SE card....some questions....

How can I have gkrelm showing on every desktop without multiple instances of it?

Can I turn the cube off and just have normal desktop switching?

Can I use sloppy focus somehow?

And finally, can I still use a double click on the window title to shade the window.

BTW these things are only minor and it all looks amazing - many thanks for the thread.

Thanks in advance
bryan[/QUOTE]


Well I've played and answered my own questions! - most of them

1. By starting the 'thefuture' script on startup I've managed to get gkrellm on every desktop.

2. By speeding the cube rotation up - it bugs me less, I know it looks cool, but I found it distracting for real work.

3. Upgrading to the latest compiz - I've got sloppy focus back.

4. Still cant find a way to shade windows - anyone know?

Cheers
Bryan

---

### Post by ispmarin on 2006-03-31
here works the shadown and opacity, but not zoom...

---

### Post by rab on 2006-03-31
[QUOTE=Grog140]When using the command to install XGL I get:

E: Couldn't find package compiz

Anyone know whats up?[/QUOTE]

Same here

---

### Post by xOrphenochx on 2006-04-01
Well, I got my drivers working, and Xgl and Compiz, but...some of the screen gets mangled. I tried the Xgl demo and that didn't happen.

Dapper test flight 5
2.6.15-19-386
Nvidia Gforce4 MX 4000
Latest Nvidia Drivers

---

### Post by RjBanker18 on 2006-04-01
Hi, I followed all instructions word-for-word but I get this error message after I type "thefuture"

Xlib:  extension "GLX" missing on display ":0.0".
compiz.real: root visual is not a GL visual
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on dispay :0.0

It was a clean install of Dapper 6, I enabled all the repositories, I updated everything, I rebooted and started following the tutorial at the begining of this post.
Im running GeForce FX Go5200 (which i heard runs GLX great)

Hopefully I'm didnt missing anything...
Please Help!!!:confused:

::EDIT::
It seems I did not install the latest nvidia drivers.
Now im getting the
GLX_EXT_texture_from_pixmap is missing
error!

---

### Post by peRosine on 2006-04-02
I got the same error. It's about the worst error you can get because their can be a lot of sources..

This can be a solution:

Reinstall libgl1-mesa
```
sudo apt-get install libgl1-mesa --reinstall
```

Then somewhere on your PC should be a file named: "libGL.so.1.2.xlibmesa"
to find it, type:
```

updatedb
locate libGL.so.1.2.xlibmesa
```

Then I saved it to my home directory.
```

cp /blablabla/libGL.so.1.2.xlibmesa /home/your_username/

```

Then u'll have to change your /usr/lib/libGL.so.1 file to this. (for example by creating a simlink)

```
sudo ln -sf /home/your_username/libGL.so.1.2.xlibmesa /usr/lib/libGL.so.1
```

Reboot and hope for the best! Good luck!

(above guide is the one I got from sYs^, all credits go to him).

---

### Post by cleentrax on 2006-04-02
Everything seemed to go fine, but when I reboot and type "thefuture" I get: 

> /bin/bash: gnome-window-decorator & compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize: No such file or directory



Any thoughts?

---

### Post by rikiller on 2006-04-03
I am having an error come up when I am loading xgl that says:

> compiz.real: Couldn't load plugin 'libmenu.so'


Also I can't get the windows transperancy to work. 

Any ideas?

Everything else seems to be sweet.

---

### Post by ispmarin on 2006-04-03
Try to install the libncurses5 library and sees if it works.

---

### Post by rikiller on 2006-04-03
I tried that and now it says:

> compiz.real: dlsym: /usr/lib/libmenu.so: undefined symbol: getCompPluginInfo
compiz.real: Failed to lookup getCompPluginInfo in 'libmenu.so' plugin

(I am new to linux, so please go easy)

---

### Post by tlo on 2006-04-04
i have a problem with downloading the packages. ```

tristan@tlo-ubuntu:~$ sudo apt-get install compiz xserver-xgl libgll-mesa xserver-xorg libglitz-glxl compiz-gnome
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libgll-mesa
tristan@tlo-ubuntu:~$

```

when i get rid of libgll-mesa, the libglitz does the same thing!

---

### Post by ninja_indiano on 2006-04-05
I had XGL working in Flight 5; call me crazy I did a fresh instation with Flight 6, and when I restart X with XGL my X gets all messed up.  

I reintall Fligh6 again and the problem still goes one, any clues why this is happening?  It does not give me an error, just the screen all mesed up.

---

### Post by dexter on 2006-04-06
[QUOTE=tlo]i have a problem with downloading the packages. ```

tristan@tlo-ubuntu:~$ sudo apt-get install compiz xserver-xgl libgll-mesa xserver-xorg libglitz-glxl compiz-gnome
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libgll-mesa
tristan@tlo-ubuntu:~$

```

when i get rid of libgll-mesa, the libglitz does the same thing![/QUOTE]

I'm also having repo problems (compiz, xserver-xgl, ...). This is my apt sources list :

```

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb http://be.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://be.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://be.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://be.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://be.archive.ubuntu.com/ubuntu breezy universe
deb-src http://be.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://be.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://be.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```

any missing ?

---

### Post by Sutekh on 2006-04-06
That's becuase you have the wrong sources for doing this.

Those XGL packages are available in the Dapper repositories not the Breezy ones.

I think some people have gotten the packages from the Dapper repositories on the Breezy machines, and been able to get it working.  You should try and find those posts.

Although that's probably a *really* bad idea to try.

---

### Post by bvucinic on 2006-04-06
did a dist-upgrade which updated xgl to 7. ubuntu9 and now when I start a video in a player (vlc, totem) X crashes:confused: .
Any thoughts? TIA

---

### Post by tajreed on 2006-04-07
Everything seems to have been set up properly on my Geoforce 6200 card. But in the gconf/compiz/plug-ins there is config data for any of the plug-ins. Only shows screen0. There is config for compiz/general/allscreens/options. 

Hence, I cannot get any of the plug-ins working. 

What have I missed here? I have followed the Poofyhairguys great instructions with nary a blip or problem.

Thanks

---

### Post by [Yatta] on 2006-04-09
I had xgl/compiz working earlier. i upgraded but now when i start 'thefuture'  i lose ALL window decorations i can move any windows and i also can't  minimize any windows.
The only difference this time is that i'm using QuinnStorm compiz packages. window borders disappear and compiz doesn't seem to do anything.
Anyoen have any clue what i MAY be doing  wrong?

**edit**
well i removed some libopacity* files that were in /usr/lib/compiz... by following Omar Compiz Opacity --- > [http://www.ubuntuforums.org/showthread.php?t=132063](http://www.ubuntuforums.org/showthread.php?t=132063)
i also removed opacity from gconf gconf->apps->compiz->general->allscreens->active_plugins

---

### Post by dr_d on 2006-04-10
Hello guys.

I've got XGL working (cube blows my mind:)) but I can't move any windows on the screen. I'm told this means that I havn't got compiz running.

This makes sense, because when I run:

```

#!/bin/bash
gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &
```
[/CODE]

I get the error message:

 gnome-window-decorator: Another window decorator is already running


Any suggestions would be greatly appreciated.
Cheers.

---

### Post by Fudgie on 2006-04-10
If you do have the cube spinning, compiz is running but failing to load the plugins which handle decoration, movement etc. Check your active_plugins key in gconf.

---

### Post by dr_d on 2006-04-10
I think I may have found the cause of the problem. When looking in gconf-editor for:
/apps/compiz/general/allscreens/options/active_plugins


I noticed that /apps/compiz does not exist!!

Any suggestions?

---

### Post by ubernoob on 2006-04-10
i skipped the step that says
```
sudo apt-get install nvidia-kernel-common nvidia-glx
```

Which i guess would only reinstall old nvidia drivers. I have installed the new drivers from this guide: [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")

when i do the step with

```
sudo gedit /etc/gdm/gdm.conf-custom
```

x-server won't start. Removing that one fixes the problem, but leaves me without Xgl.

---

### Post by dr_d on 2006-04-10
W00T!! I AM TYPING THIS FROM A WOBBLY FIREFOX WINDOW!!

To anyone else still experiencing problems (these are the things that helped me):

1. Make sure your default color depth is 24. Set this in /etc/X11/xorg.conf. If it's not set to the correct value you will get redraw issues.

2. Make sure you get the right drivers. Check out [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

3. When you run compiz for the first time, use: compiz --replace gconf. This way it gets added to gconf. Later on use it with all the options. More about this at [http://en.opensuse.org/Compiz](http://en.opensuse.org/Compiz)

4. (most importantly) XGL/Compiz rocks! Don't give up until you are wobbling on your way!!

---

### Post by hallon on 2006-04-10
Hi!

Ive followed the guide posted at the beginning.

Im using a nvidia 6800 and compiz works, its just that when I move windows, and get this cool jelly effect, it works smooth aslong as I keep moving the window around but whenever I stop, or let go of the window, the wobbling animation gets really slow and thats quite annoying accually. Is there any way to turn off the wobbling when moving windows cuz there dont seem to be any problem with other effects. Id still like to have this effect running though.. :( just not sluggish when I release windows or stop moving windows. Im running 24bit colour depth.

Please forgive me for not reading all 80 pages in this thread :-#

---

### Post by mstlyevil on 2006-04-10
[QUOTE=hallon]Hi!

Ive followed the guide posted at the beginning.

Im using a nvidia 6800 and compiz works, its just that when I move windows, and get this cool jelly effect, it works smooth aslong as I keep moving the window around but whenever I stop, or let go of the window, the wobbling animation gets really slow and thats quite annoying accually. Is there any way to turn off the wobbling when moving windows cuz there dont seem to be any problem with other effects. Id still like to have this effect running though.. :( just not sluggish when I release windows or stop moving windows. Im running 24bit colour depth.

Please forgive me for not reading all 80 pages in this thread :-#[/QUOTE]

If you used poofy's guide and installed the ones from the repos, they are outdated. To get the latest versions go to this web site and add quinns repos to your sources list. Then you can get the latest which fixes a lot of problems that were common with the original packages.

[http://compiz.ed3n.com/viewtopic.php?id=2]("http://compiz.ed3n.com/viewtopic.php?id=2")

---

### Post by poofyhairguy on 2006-04-10
[QUOTE=mstlyevil]If you used poofy's guide and installed the ones from the repos, they are outdated. To get the latest versions go to this web site and add quinns repos to your sources list. Then you can get the latest which fixes a lot of problems that were common with the original packages.

[http://compiz.ed3n.com/viewtopic.php?id=2]("http://compiz.ed3n.com/viewtopic.php?id=2")[/QUOTE]


This is correct. I soon plan to change my guide to take into account the new repo.

---

### Post by hallon on 2006-04-11
Thank you for your quick replies :)

After a few hours of search I found this page [http://xgl.compiz.info/](http://xgl.compiz.info/) it had all the files I needed to install the new Compiz :)  I missed the libsvg and libsvg-cairo but now it works!  thank you again!  Now I must spend the rest of the night moving windows around :P

---

### Post by iverson2 on 2006-04-11
Great post.  I followed all of your instructions and came out perferct!

---

### Post by mdmarmer on 2006-04-11
I have the same problem in gentoo/kororaa

See here for fix in vlc

Mike

[http://forums.kororaa.org/viewtopic.php?t=693](http://forums.kororaa.org/viewtopic.php?t=693)

---

### Post by da2na on 2006-04-11
[QUOTE=g14]Dapper runs fine. I have ran it every day for the past 2 months without any major issues except when they did the 2.6.12 --> 2.6.15/removal of hotplug transitions and the x.org overhaul. The Dapper development cycle seems more sane and stable than the Breezy development cycle.

I run Xgl/compiz and it runs fine with Deskbar. I hit F3 and the deskbar searchbar pops up. If you want, I'll attach a screenshot after I get home.

To poofyhairguy... Making a shell script (/usr/bin/thefuture) and having it run under your session is very hackish. Try this instead:

1.) ALT F2 and put in 

2.) System --> Preferences --> Sessions --> Startup Programs --> Add. Put in **gnome-window-decorator** and then add in another containing **compiz gconf**.
3.) Logout and then back in to gnome.
4.) Profit :) 

Same effect, less hackish, just my 0.3 cents.[/QUOTE]

...great suggestion.  I followed your directions, but had to add "**compiz --replace gconf**" under Startup Programs in order for it to work.  Hope this helps someone else...

---

### Post by rjwood on 2006-04-12
can anyone help with this

E: /var/cache/apt/archives/xserver-xgl_7.0.0-0ubuntu5_i386.deb: trying to overwrite `/usr/share/man/man1/Xserver.1x.gz', which is also in package xserver-xorg-core

---

### Post by krusbjorn on 2006-04-12
[QUOTE=rjwood]can anyone help with this

E: /var/cache/apt/archives/xserver-xgl_7.0.0-0ubuntu5_i386.deb: trying to overwrite `/usr/share/man/man1/Xserver.1x.gz', which is also in package xserver-xorg-core[/QUOTE]
sudo dpkg-divert --package xserver-xorg-core --divert /usr/share/man/man1/Xserver.1x.gz.xgl --rename /usr/share/man/man1/Xserver.1x.gz

---

### Post by rjwood on 2006-04-12
[quote=krusbjorn]sudo dpkg-divert --package xserver-xorg-core --divert /usr/share/man/man1/Xserver.1x.gz.xgl --rename /usr/share/man/man1/Xserver.1x.gz[/quote]

Thanks krusbjorn- I apprieciate the help:). I am still getting the same error message though. Is there something else I shoud do??

---

### Post by krusbjorn on 2006-04-12
[QUOTE=rjwood]Thanks krusbjorn- I apprieciate the help:). I am still getting the same error message though. Is there something else I shoud do??[/QUOTE]

I installed it by using the --force-overwrite option. Could look something like this:

sudo dpkg -i --force-overwrite /var/cache/apt/archives/xserver-xorg-core_1%3a1.0.2-0ubuntu5_i386.deb

(depending on the name/version of the package you are trying to install)

---

### Post by Andeim_ on 2006-04-12
hello all!
I have a problem with XGL installation. I have installed all packages and modified xorg.conf, gdm.conf-custom and gdm.conf thanks to [http://forum.ubuntu-fr.org/viewtopic.php?id=34380&p=1]("http://forum.ubuntu-fr.org/viewtopic.php?id=34380&p=1") which seems to workfor a few persons. Next I read you post and I verify all steps and i create the script thefuture to launch compiz and gnome-window-decorator when I want. But there is a little problem which is when I open a session, I note that XGL don't appear in *System>Administration>system monitor*. So my question is how to launch XGL instead of Xserver.
I'm sorry for the grammar mistakes but i've not a good level in English. Soory and Thank you for your help!

---

### Post by hallon on 2006-04-12
Ok now I might be asking for the impossible but...

Is it possible to run any other openGL application while I'm using Xgl and compiz? I'm interested in running doom3 (navite) and maybe world of warcraft (through wine) but none of them starts. WoW says it cant initialize the 3d acceleration. Doom3 gets segmentation fault and I know I had it working with slackware and a regular X installation with composite extention turned on. I also have the "AllowGLXWithComposite" set to true under xorg.conf. Quake3 seem to run fine though..  abit sluggish but it runs, and I think it runs with open gl accelleration cuz it looks like it does.

Would it be possible to make a second X session for those games, just a regular X sessiton, no GLX and start them from there? I mean switch between Xgl and X for 3d games? Or in some way release the gfx card from Xgl while playing games?

EDIT: UT2004 (native) seem to run too, but slow, as every other 3d game that starts. glgears runs pretty slow too :/   maybe I'll just have to accept it.

Any kind of help is appreciated :)

Happy Easter

---

### Post by Stormy Eyes on 2006-04-13
If you want to smooth things out, try the following:

1. sudo gedit /etc/environment

2. alter the file so that it looks like this:
```
LANGUAGE="en"
LANG=en_US.UTF-8
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
__GL_FSAA_MODE="2"
__GL_LOG_MAX_ANISO="1"
__GL_SYNC_TO_VBLANK="1"
```

You can adjust the first two __GL variables depending on how uber your nVidia card is; consult the documentation included with nVidia's binary driver for details. Turning on Full Scene Antialiasing and Anitroscopic Filtering will smooth animations and provide readable fonts for windows currently being animated by Compiz. Try it out.

---

### Post by Stormy Eyes on 2006-04-13
[QUOTE=Andeim_]But there is a little problem which is when I open a session, I note that XGL don't appear in *System>Administration>system monitor*. So my question is how to launch XGL instead of Xserver.[/QUOTE]

Open a terminal and try the following command, please, and tell us the results:
```
sudo ps aux | grep Xgl
```

---

### Post by dandaman32 on 2006-04-13
I'm using Knoppix 4.0.2 (similar to ubuntu) and I know this isn't normally the place for knoppix support but I couldn't find anywhere else to ask for help.

It's taken alot of work, but I successfully built and installed glitz, mesa, compiz, and Xgl, and currently my box is running the Xgl server OK, but whenever I start compiz I get the error:
```
/opt/Xgl/bin/compiz: No GLXFBConfig for default depth, this isn't going to work.
/opt/Xgl/bin/compiz: Failed to manage screen: 0
/opt/Xgl/bin/compiz: No managable screens found on display :0.0
```
I modified the source and made it print out the color depth it wants, and that depth is 16bit! However whenever I change my xorg.conf DefaultColorDepth to 16, Xorg crashes.

System specs:
Knoppix 4.0.2
AMD Athlon XP 2500+
NVidia GeForce FX 5200 video card
2 (old) monitors - normally run with TwinView but running just one for now because of X server crashes
1GB RAM

Any ideas?

-dandaman32

---

### Post by Andeim_ on 2006-04-13
It is the result of  *sudo ps aux | grep Xgl*
```
damien@ubuntu:~$ sudo ps aux | grep Xgl
Password:
root      4569  4.4  3.3  70244 34660 ?        SL   07:09   0:03 /usr/bin/Xgl :0 :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
root      4591  1.0  0.9  43548  9860 tty7     SLs+ 07:09   0:00 /usr/bin/Xorg vt7 -auth /tmp/.Xgl-auth-qICFG5 -nolisten tcp -dpms -v -s 0 :93 -terminate
damien    5363  0.0  0.0   5020   948 pts/0    R+   07:10   0:00 grep Xgl
damien@ubuntu:~$

```

---

### Post by ninja_indiano on 2006-04-13
Got the same problem as dandaman
```

ninja@xacazulo:~$ thefuture
ninja@xacazulo:~$ compiz.real: No GLXFBConfig for default depth, this isn't going to work.
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

```

Runing lateste dapper...

When I start X I have no windows title bares, the I ran metacity to be able to work in X.  However when I restart thefure (xgl), I get the above error msg and the windows title bar go away...

Any ideias...

Just upgrade to the latest compiz.

---

### Post by Stormy Eyes on 2006-04-13
[QUOTE=Andeim_]It is the result of  *sudo ps aux | grep Xgl*
```
damien@ubuntu:~$ sudo ps aux | grep Xgl
Password:
root      4569  4.4  3.3  70244 34660 ?        SL   07:09   0:03 /usr/bin/Xgl :0 :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
root      4591  1.0  0.9  43548  9860 tty7     SLs+ 07:09   0:00 /usr/bin/Xorg vt7 -auth /tmp/.Xgl-auth-qICFG5 -nolisten tcp -dpms -v -s 0 :93 -terminate
damien    5363  0.0  0.0   5020   948 pts/0    R+   07:10   0:00 grep Xgl
damien@ubuntu:~$

```[/QUOTE]

You have Xgl running under process ID 4569. You don't have to worry. :)

---

### Post by Stormy Eyes on 2006-04-13
[QUOTE=ninja_indiano]
Any ideias...

Just upgrade to the latest compiz.[/QUOTE]

I had this problem when I upgraded last night. Use the repositories listed on [this page](http://compiz.ed3n.com/viewtopic.php?id=74), and do apt-get dselect-upgrade. Then reboot, and compiz should work again. The latest compiz needs an updated libmesa.

---

### Post by sjoeboo on 2006-04-13
when using those repos you linked to, i'm getting 404's on running an apt-get update.....any ideas?

---

### Post by Stormy Eyes on 2006-04-13
[QUOTE=sjoeboo]when using those repos you linked to, i'm getting 404's on running an apt-get update.....any ideas?[/QUOTE]

The server might be down. Be patient.

---

### Post by guX on 2006-04-13
Hey, I'm had that GLXFBConfig problem, but I realised that I had upgraded compiz last night. It's working fine now once I downgraded compiz. Try downgrading to version 0.0.9-0ubuntu1. 0.0.9-0ubuntu2 doesn't seem to work.

---

### Post by guX on 2006-04-13
Okay, it worked initially, but now I can't get into Xgl at all (well, I can, but as soon as it tries to load Compiz I get a black screen), so I'm just using normal Xorg for now. Anyone have any idea what might be wrong? Xgl was working perfectly just last night.

---

### Post by guX on 2006-04-13
Okay, I can't get it working at all now with compiz_0.0.9-ubuntu1, it just crashes, and compiz_0.0.9-ubuntu2 just gives that error, so I'm just running plain old metacity for now.

---

### Post by angkor on 2006-04-13
here's the fix:

[http://www.ubuntuforums.org/showthread.php?t=159512](http://www.ubuntuforums.org/showthread.php?t=159512)

---

### Post by Andeim_ on 2006-04-14
Thank you for the information **Stormy Eyes**. Now when I launch the script thefuture, 
I have : 
[INDENT]*damien@ubuntu:~$ gnome-window-decorator: Another window decorator is already running*
[/INDENT]
[INDENT]And I have no border and my menu has disappeared.[/INDENT]

PS : I upgrade compiz gnome-compiz with the link [http://compiz.ed3n.com/viewtopic.php?id=74](http://compiz.ed3n.com/viewtopic.php?id=74)

---

### Post by Stormy Eyes on 2006-04-14
[QUOTE=Andeim_]Thank you for the information **Stormy Eyes**. Now when I launch the script thefuture, 
I have : 
[INDENT]*damien@ubuntu:~$ gnome-window-decorator: Another window decorator is already running*
[/INDENT]
[INDENT]And I have no border and my menu has disappeared.[/INDENT]

PS : I upgrade compiz gnome-compiz with the link [http://compiz.ed3n.com/viewtopic.php?id=74](http://compiz.ed3n.com/viewtopic.php?id=74)[/QUOTE]

Save whatever documents you have open and issue the following command from a terminal:
```
sudo /etc/init.d/gdm restart
```

This will restart X. Login again and run "thefuture", and all should be well.

---

### Post by curiita on 2006-04-14
Hi, i'm really new in Linux so here's my problem:

 - from what i've understood, Xgl is that cool thing that allow us to play with the desktops like a cube (like iBook), right? But the thing is, i don't have Nvidia nor ATI :\ i've a self integrated video card 64MB (Silicon Integrated Systems (SiS) 65x/M650/740 PCI/AGP VGA Display). Is it possible to get xgl?

hail []

---

### Post by Stormy Eyes on 2006-04-14
[QUOTE=curiita]Hi, i'm really new in Linux so here's my problem:

 - from what i've understood, Xgl is that cool thing that allow us to play with the desktops like a cube (like iBook), right? But the thing is, i don't have Nvidia nor ATI :\ i've a self integrated video card 64MB (Silicon Integrated Systems (SiS) 65x/M650/740 PCI/AGP VGA Display). Is it possible to get xgl?

hail [][/QUOTE]

Probably not. If you upgrade, go with nVidia; ATI's Linux drivers are shit.

---

### Post by Jott on 2006-04-14
Hi everyone,

I've been having some adventures with XGL.  I got through nmost of them ok with help from these forums, but I appear to be stuck now.

I had gotten everything working by following the Nvidia how to on the 'one thread to rule them all' post.  Then I added Quinn's repos and did a dist-upgrade.  It killed everything.  Fixed that by getting the new mesa from reggeamons repos.  Everything is back ,except that I have to titlebars - nothing to grab and wobble around, no min-max, no little x in the corner.  I found a post saying to remove the extra opacity libs, but I don't think I have any opacity libs.  Another post said to unset the active plugins key in gconf-editor/ apps compiz/ general/ allscreens/ options.  I tried that, but the key doesn't unset - I right click, choose unset key, and it's still there.  I restart, still no titlebars.

Any ideas?

---

### Post by Andeim_ on 2006-04-15
[QUOTE=Stormy Eyes]Save whatever documents you have open and issue the following command from a terminal:
```
sudo /etc/init.d/gdm restart
```

This will restart X. Login again and run "thefuture", and all should be well.[/QUOTE]

Hmmmm, it doesn't function I always have [CODE][    damien@ubuntu:~$ gnome-window-decorator: Another window decorator is already running

    And I have no border and my menu has disappeared./CODE]

But I have a question how can I launch xgl when I am in  only terminal mode ?
[INDENT]For exemple when I do ctrl+alt+F2[/INDENT]
Thank you

---

### Post by Jott on 2006-04-15
I had a problem with no border and no menu - see my post just above this one (maybe two above).

What I ended up doing is adding these repositories:

deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

and doing an update & deselect upgrade - I think this gave me a new version of mesa, which I needed.  Then I commented those out and added these:

deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb-src [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main

After another apt-get update, I removed compiz, and reinstalled compiz (apt-get remove, apt-get install).  I believe this gave me quinnstorms compiz package, which seems to work better for me for inexplicable reasons.

This is probably an incredibly kludgey fix, and I certainly make no gaurantee - it's just what worked for me.

good luck!

---

### Post by Dr Gonzo on 2006-04-16
This option:```
Option "AllowGLXWithComposite" "true"
```is no longer necessary, since we're on X11R7. [quote="nVidia"]This option is intended for use on X.Org X servers older than X11R6.9.0. On X11R6.9.0 or newer X servers, NVIDIA's OpenGL implementation interacts properly by default with the Composite X extension and this option should not be needed. However, on X11R6.9.0 or newer X servers, support for GLX with Composite can be disabled by setting this option to False.[/quote]Just thought you might like to know.

---

### Post by mstlyevil on 2006-04-16
[QUOTE=Dr Gonzo]This option:```
Option "AllowGLXWithComposite" "true"
```is no longer necessary, since we're on X11R7. Just thought you might like to know.[/QUOTE]

Thanks for the information. I tested it and you are correct.

---

### Post by pwrstick on 2006-04-16
Anyone else having problems with the transparency settings using Alt-Mouse Wheel?

I also cannot set the transparency from alt-clicking the title bar...

---

### Post by Andeim_ on 2006-04-17
I just do an upgrade with your repositories and I had 
```
[Sélection du paquet xserver-xgl précédemment désélectionné.
(Lecture de la base de données... 63714 fichiers et répertoires déjà installés.)
Dépaquetage de xserver-xgl (à partir de .../xserver-xgl_7.0.0-0ubuntu14_amd64.de b) ...
dpkg : erreur de traitement de /var/cache/apt/archives/xserver-xgl_7.0.0-0ubuntu 14_amd64.deb (--unpack) :
 tentative de remplacement de « /usr/share/man/man1/Xserver.1x.gz », qui apparti ent aussi au paquet xserver-xorg-core
dpkg-deb: sous-processus paste tué par le signal (Relais brisé (pipe))
Des erreurs ont été rencontrées pendant l'exécution :
 /var/cache/apt/archives/xserver-xgl_7.0.0-0ubuntu14_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
So i decided to remove him and reinstall xserver-xgl but I have the same problem....

How can I corect this message ?

---

### Post by Bazon on 2006-04-17
[QUOTE=Andeim_]I just do an upgrade with your repositories and I had 
```
[Sélection du paquet xserver-xgl précédemment désélectionné.
(Lecture de la base de données... 63714 fichiers et répertoires déjà installés.)
Dépaquetage de xserver-xgl (à partir de .../xserver-xgl_7.0.0-0ubuntu14_amd64.de b) ...
dpkg : erreur de traitement de /var/cache/apt/archives/xserver-xgl_7.0.0-0ubuntu 14_amd64.deb (--unpack) :
 tentative de remplacement de « /usr/share/man/man1/Xserver.1x.gz », qui apparti ent aussi au paquet xserver-xorg-core
dpkg-deb: sous-processus paste tué par le signal (Relais brisé (pipe))
Des erreurs ont été rencontrées pendant l'exécution :
 /var/cache/apt/archives/xserver-xgl_7.0.0-0ubuntu14_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
So i decided to remove him and reinstall xserver-xgl but I have the same problem....

How can I corect this message ?[/QUOTE]

Probably that way:
#sudo dpkg -i --force-all  /var/cache/apt/archives/xserver-xgl_7.0.0-0ubuntu14_amd64.deb

I haven't tried it, but read it [here](http://forum.ubuntuusers.de/topic/29179/) (if your speaking not only french and english, but german, too... :wink:) and it worked there.

---

### Post by thunderduck3141 on 2006-04-17
wow gteat guide man
this is so COOL
wobble wobble
hehehe
world domination just go that much closer
to the zeplin

---

### Post by poofyhairguy on 2006-04-17
[QUOTE=Dr Gonzo]This option:```
Option "AllowGLXWithComposite" "true"
```is no longer necessary, since we're on X11R7. Just thought you might like to know.[/QUOTE]

Thanks. I thought that this was the case, but I wanted to play it safe. Its gone from my guide....

---

### Post by Andeim_ on 2006-04-18
It's function !! I am happy !
I just have any problems I can't move the cube, switcher and scale don't funtion very well I downloaded gset-compiz to correct these problems but I can't activate the function cube....
Thank you all.

---

### Post by fsman on 2006-04-18
[QUOTE=poofyhairguy]Thanks. I thought that this was the case, but I wanted to play it safe. Its gone from my guide....[/QUOTE]

Is it safe to remove the "Option "AllowGLXWithComposite" "true" " line from xorg with nvidia. Its still in this thread's guide (but not in the 64-bit guide).

I thought I would check before I delete from my xorg.

---

### Post by dandaman32 on 2006-04-18
Alright, I have another problem.  I pretty much just ignored it and commented out the troublesome lines before, but I think that's part of the reason this isn't working at all for me.  Here's the error I'm getting, including the last couple command lines:
```
if /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -I../include -I../include -I../include -I../include -I../include -I../include    -DHAVE_DIX_CONFIG_H  -DXGLServer  -D_BSD_SOURCE -DHAS_FCHOWN -DHAS_STICKY_DIR_BIT   -I../include -I../include -I../Xext -I../composite -I../damageext -I../xfixes -I../Xi -I../mi -I../miext/shadow  -I../miext/damage -I../render -I../randr -I../fb  -I/usr/include/GL -MT cursor.lo -MD -MP -MF ".deps/cursor.Tpo" \
  -c -o cursor.lo `test -f 'cursor.c' || echo './'`cursor.c; \
then mv -f ".deps/cursor.Tpo" ".deps/cursor.Plo"; \
else rm -f ".deps/cursor.Tpo"; exit 1; \
fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -I../include -I../include -I../include -I../include -I../include -I../include -DHAVE_DIX_CONFIG_H -DXGLServer -D_BSD_SOURCE -DHAS_FCHOWN -DHAS_STICKY_DIR_BIT -I../include -I../include -I../Xext -I../composite -I../damageext -I../xfixes -I../Xi -I../mi -I../miext/shadow -I../miext/damage -I../render -I../randr -I../fb -I/usr/include/GL -MT cursor.lo -MD -MP -MF .deps/cursor.Tpo -c cursor.c  -fPIC -DPIC -o .libs/cursor.o
cursor.c: In function 'ProcXFixesHideCursor':
cursor.c:840: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
cursor.c:840: error: 'stuff' undeclared (first use in this function)
cursor.c:840: error: (Each undeclared identifier is reported only once
cursor.c:840: error: for each function it appears in.)
cursor.c:840: error: 'xXFixesHideCursorReq' undeclared (first use in this function)
cursor.c:840: error: expected ';' before 'client'
cursor.c: In function 'SProcXFixesHideCursor':
cursor.c:879: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
cursor.c:879: error: 'stuff' undeclared (first use in this function)
cursor.c:879: error: 'xXFixesHideCursorReq' undeclared (first use in this function)
cursor.c:879: error: expected ';' before 'client'
cursor.c: In function 'ProcXFixesShowCursor':
cursor.c:892: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
cursor.c:892: error: 'stuff' undeclared (first use in this function)
cursor.c:892: error: 'xXFixesShowCursorReq' undeclared (first use in this function)
cursor.c:892: error: expected ';' before 'client'
cursor.c: In function 'SProcXFixesShowCursor':
cursor.c:923: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
cursor.c:923: error: 'stuff' undeclared (first use in this function)
cursor.c:923: error: 'xXFixesShowCursorReq' undeclared (first use in this function)
cursor.c:923: error: expected ';' before 'client'
make: *** [cursor.lo] Error 1
```
And later on, after cursor.c is forcibly removed from Makefile:
```
 gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -I../include -I../include -I../include -I../include -I../include -I../include -DHAVE_DIX_CONFIG_H -DXGLServer -D_BSD_SOURCE -DHAS_FCHOWN -DHAS_STICKY_DIR_BIT -I../include -I../include -I../Xext -I../composite -I../damageext -I../xfixes -I../Xi -I../mi -I../miext/shadow -I../miext/damage -I../render -I../randr -I../fb -I/usr/include/GL -MT xfixes.lo -MD -MP -MF .deps/xfixes.Tpo -c xfixes.c  -fPIC -DPIC -o .libs/xfixes.o
xfixes.c:97: error: 'X_XFixesShowCursor' undeclared here (not in a function)
xfixes.c:136: warning: excess elements in array initializer
xfixes.c:136: warning: (near initialization for 'ProcXFixesVector')
xfixes.c:137: warning: excess elements in array initializer
xfixes.c:137: warning: (near initialization for 'ProcXFixesVector')
xfixes.c:199: warning: excess elements in array initializer
xfixes.c:199: warning: (near initialization for 'SProcXFixesVector')
xfixes.c:200: warning: excess elements in array initializer
xfixes.c:200: warning: (near initialization for 'SProcXFixesVector')
make: *** [xfixes.lo] Error 1
```

I configured it with this line:
```
PKG_CONFIG_PATH=/opt/Xgl/lib/pkgconfig ./autogen.sh --enable-xgl --disable-xorg --disable-xprint --enable-glx --enable-dri --with-mesa-source=/opt/Xgl/src/Mesa -with-release-snap=1 --disable-xvfb --disable-xnest --enable-xglx --enable-xkb --disable-kdriveserver --prefix=/opt/Xgl
```
That failed, so I ran it with ./configure instead:
```
PKG_CONFIG_PATH=/opt/Xgl/lib/pkgconfig **_./configure_** --enable-xgl --disable-xorg --disable-xprint --enable-glx --enable-dri --with-mesa-source=/opt/Xgl/src/Mesa -with-release-snap=1 --disable-xvfb --disable-xnest --enable-xglx --enable-xkb --disable-kdriveserver --prefix=/opt/Xgl
```
I have the latest Mesa sources from CVS and nV driver 8756. My card is an nV GeForceFX 5200 PersonalCinema.

Anyone get this error?

-dandaman32

---

### Post by thunderduck3141 on 2006-04-19
hi all, i have xgl and compiZ working great, but i have problems w/ enemy territory

heres a print out 

h4x0r@ubuntu:~$ et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/h4x0r/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Xlib:  extension "XFree86-VidModeExtension" missing on display ":0.0".
Xlib:  extension "XFree86-DGA" missing on display ":0.0".
Failed to detect XF86DGA Mouse
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce FX 5700LE/AGP/SSE/3DNOW!
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...GL_EXT_compiled_vertex_array not found
...GL_NV_fog_distance not found
... GL_EXT_texture_filter_anisotropic not found
Initializing GLX extensions
... GLX_SGI_swap_control not found
... GLX_SGI_video_sync not found

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce FX 5700LE/AGP/SSE/3DNOW!
GL_VERSION: 1.2 (2.0.2 NVIDIA 87.56)
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_imaging GL_ARB_multitexture GL_ARB_po int_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_texture_border_clamp GL_ ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_te xture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_EXT_abgr GL_E XT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT _blend_subtract GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_ar rays GL_EXT_packed_pixels GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_se parate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_texture3D G L_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EX T_texture_env_dot3 GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_obj ect GL_EXT_vertex_array GL_HP_occlusion_test GL_IBM_texture_mirrored_repeat GL_N V_blend_square GL_NV_texgen_reflection GL_NV_texture_rectangle GL_NV_texture_env _combine4 GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_S GIX_shadow
GLX_EXTENSIONS: GLX_ARB_multisample GLX_EXT_visual_info GLX_EXT_visual_rating GL X_EXT_import_context GLX_SGIX_fbconfig GLX_ARB_get_proc_address
GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: software w/ 0 overbright bits
CPU:
rendering primitives: multiple glArrayElement
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: disabled
texenv add: disabled
compressed textures: disabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
32768 samples
   16 samplebits
    1 submission_chunk
22050 speed
0x0xb0958000 dma buffer
No background file.
----------------------
Sound memory manager started
Sys_LoadDll(/home/h4x0r/.etwolf/etmain/ui.mp.i386.so)...
Sys_LoadDll(/home/h4x0r/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/h4x0r/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No su ch file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xaedc6f40
Sys_LoadDll(ui) succeeded!
Found high quality video and fast CPU
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: ubuntu.chn.comcast.net
Alias: ubuntu
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
Couldn't write etconfig.cfg.
execing preset_high.cfg
r_colorbits will be changed upon restarting.
r_depthbits will be changed upon restarting.
r_picmip will be changed upon restarting.
r_mode will be changed upon restarting.
r_texturebits will be changed upon restarting.
RE_Shutdown( 1 )
Hunk_Clear: reset the hunk ok
----- Initializing Renderer ----
-------------------------------
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 6: 1024 768
Xlib:  extension "XFree86-VidModeExtension" missing on display ":0.0".
Using 4/4/4 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce FX 5700LE/AGP/SSE/3DNOW!
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...GL_EXT_compiled_vertex_array not found
...GL_NV_fog_distance not found
... GL_EXT_texture_filter_anisotropic not found
Initializing GLX extensions
... GLX_SGI_swap_control not found
... GLX_SGI_video_sync not found

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce FX 5700LE/AGP/SSE/3DNOW!
GL_VERSION: 1.2 (2.0.2 NVIDIA 87.56)
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_imaging GL_ARB_multitexture GL_ARB_po int_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_texture_border_clamp GL_ ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_te xture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_EXT_abgr GL_E XT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT _blend_subtract GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_ar rays GL_EXT_packed_pixels GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_se parate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_texture3D G L_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EX T_texture_env_dot3 GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_obj ect GL_EXT_vertex_array GL_HP_occlusion_test GL_IBM_texture_mirrored_repeat GL_N V_blend_square GL_NV_texgen_reflection GL_NV_texture_rectangle GL_NV_texture_env _combine4 GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_S GIX_shadow
GLX_EXTENSIONS: GLX_ARB_multisample GLX_EXT_visual_info GLX_EXT_visual_rating GL X_EXT_import_context GLX_SGIX_fbconfig GLX_ARB_get_proc_address
GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 6, 1024 x 768 fullscreen hz:N/A
GAMMA: software w/ 0 overbright bits
CPU:
rendering primitives: multiple glArrayElement
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 32
multitexture: enabled
compiled vertex arrays: disabled
texenv add: disabled
compressed textures: disabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----
Sys_LoadDll(/home/h4x0r/.etwolf/etmain/ui.mp.i386.so)...
Sys_LoadDll(/home/h4x0r/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/h4x0r/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No su ch file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xaebc4f40
Sys_LoadDll(ui) succeeded!
Couldn't write etconfig.cfg.
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
execing preset_normal_ui.cfg
execing preset_high_ui.cfg
Couldn't write etconfig.cfg.
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console
h4x0r@ubuntu:~$


note: i kill it at the end there
the pointer doesnt work (refuses to move mostly, but will budge with constant mouse movement), and i kill it from inside the game, and the game works the same way if i do it in a term and out of a term
please help

---

### Post by akurashy on 2006-04-19
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0


i get that error 

i tried one of your answer "keep trying" but it just won't go and when i try to start X it gives me an error

---

### Post by Darkbird on 2006-04-20
[quote='poofyhairguy']CTRL + ALT + Left/right arrow key. Switches to the new side of the cube for me.

CTRL + ALT + SHIFT + Left/Right arrow key- Takes the in focused app around cube.

F12 - uses the Expose like trick

Alt- Tab - switcher Vista-style[/quote]

all of these don't seem to work for me unless I click on the title bar while doing them...
EDIT:
weird, after logging out/back in, they started to work...

---

### Post by sanmadjack on 2006-04-21
Aight, I followed these instructions but when I type in thefuture, the window borders dissapear for about a second, then X restarts. The terminal doesn't show any errors before it dissapears, so I have no idea what might b wrong. Any help? 

I just installed Dapper Beta today, and I have a Geforce 6800. I'm using the latest drivers fro nvidia.com, as well as using QuinnStorm's compiz packages which I obtained (at least the repository address) from [http://compiz.ed3n.com/viewtopic.php?id=2](http://compiz.ed3n.com/viewtopic.php?id=2)

---

### Post by ktulu1115 on 2006-04-21
Great thread guys, I got it working (sorta) without any problems.  Sorry if this has been addressed before, I havn't seen anything - one question however:

Beginning of the thread the following was stated: "THIS BREAKS XINERAMA AND TWINVIEW so dual head use is more annoying."

I have dual displays setup, but as two seperate X servers (no xinerama or twinview).  Is it possible to use Xgl with this configuration??

I tried editing the gdm.conf-custom to duplicate the lines, adding one for the second X screen, but no luck.  The first one comes up fine (screen 0), but then it kicks back to the text-based blue-on-black "unable to load X, check configuration, blah blah".  Then it kicks back to X on screen 0 with screen 1 displaying the white & black hash pattern thing.

---

### Post by Sushi on 2006-04-21
I don't know what I'm doing wrong here... I had it working beautifully before, but I didn't use it for long. Now I wanted to re-try it, but when I run "thefuture", all the windecs disappear, as well as panels and I can't bascially do anything. Apps do still work.

---

### Post by detyabozhye on 2006-04-21
[QUOTE=fsman]Is it safe to remove the "Option "AllowGLXWithComposite" "true" " line from xorg with nvidia. Its still in this thread's guide (but not in the 64-bit guide).

I thought I would check before I delete from my xorg.[/QUOTE]
Yes, this line is obselete (that's what the official Xgl or Compiz guys say).

---

### Post by Wieldop on 2006-04-22
I've installed the latest beta of DD and installed XGL+Compiz. Everything (regarding Compiz) is working fine but I can't seem to make windows transparent. What I understand is that you can use Alt+Shift wheel-up/down to make windows transparent but that doesn't work for me. I'm using 'compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher' to start Compiz. I have an NVidia 7800Go. How can I make the transparency feature work?

---

### Post by detyabozhye on 2006-04-22
AFAIK, the transparent windows are disabled in the Compiz package in the Dapper repositories, you'll have to get another package or compile it yourself for the transparent windows.

---

### Post by DigitalDuality on 2006-04-22
ok ok, i'm on dapper beta now, with the gnome desktop.  clean install.

when i follow the above guide, the moment i turn on "thefuture" i get the window bars that i should, but the entire screen freezes.  I can't open any menus, files, icons.  Can't switch between open windows.  Nothing.  I have to kill X just to do anything what so ever.

Any ideas?

---

### Post by EnTheEnd on 2006-04-23
Hey 

I'm using Dapper Beta, I've got 5200 FX.

I followed the guide and when I tried to reboot X didn't load and I got message 'FATAL: Module nvidia not found'. It's weird, when I followed the guide on Flight 6 everything worked perfectly. I have installed the drivers using the command in the guide... What could be the reason?

---

### Post by Laterix on 2006-04-23
[QUOTE=EnTheEnd]Hey 

I'm using Dapper Beta, I've got 5200 FX.

I followed the guide and when I tried to reboot X didn't load and I got message 'FATAL: Module nvidia not found'. It's weird, when I followed the guide on Flight 6 everything worked perfectly. I have installed the drivers using the command in the guide... What could be the reason?[/QUOTE]
Your error message indicates that your nvidia driver module is not loaded. So the problem is your display driver not compiz.

---

### Post by EnTheEnd on 2006-04-23
Right, is there any way to "fix" the driver? Tried to reinstall nvidia-glx, didn't help...

---

### Post by mirak63 on 2006-04-23
hi, anyone manage to run Xgl through the gdmflexiserver command ? (new login screen)
It fails for me.

---

### Post by izmaelis on 2006-04-23
[QUOTE=EnTheEnd]Right, is there any way to "fix" the driver? Tried to reinstall nvidia-glx, didn't help...[/QUOTE]
I had just the same problem. Somehow I though about installing linux-restricted-modules for my kernel version and it helped. Try:
```
sudo apt-get install nvidia-glx linux-restricted-modules-`uname -r`

```
in the console. I think that will help you out. Good luck!

---

### Post by qiemem on 2006-04-23
When I first set this up, everything was working fine. I restarted my computer, ran "thefuture", and got that error message that a lot people seem to be getting (to whom the advice is simply to keep running it over and over; this didn't work for me) anyway, so I updated first using "http://xgl.compiz.info/ dapper main" (as I couldn't find the key for quinstorm's) then did update w/ "http://www.beerorkid.com/compiz dapper main" when I found the key. 

With both, everything goes fine except when updating xserver-xgl in which I get the following error: 
```
E: /var/cache/apt/archives/xserver-xgl_7.0.0-0ubuntu5_i386.deb: trying to overwrite `/usr/share/man/man1/Xserver.1x.gz', which is also in package xserver-xorg-core
```

Now, everytime I run "thefuture", my screen looks like this:
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=8690&stc=1&d=1145826909[/IMG]

And I have to just restart x.

Any thoughts?

---

### Post by no1peanut on 2006-04-24
Okay - I have been playing with compiz xgl for a couple of weeks now - Now I wanna play with the latest compiz(I have 0.0.5 I believe) 
Where do I find the devel-repository for compiz ?

---

### Post by i386DX on 2006-04-24
I installed XGL following this thread.
It has some nice features (arrange windows with F12, ALT-TAB). But I hate those wobbly windows... How can i select wich feature I want and wich not?

I tried to remove the wobbly in thefuture, but the function remains...

---

### Post by The_Major on 2006-04-24
[QUOTE=no1peanut]Okay - I have been playing with compiz xgl for a couple of weeks now - Now I wanna play with the latest compiz(I have 0.0.5 I believe) 
Where do I find the devel-repository for compiz ?[/QUOTE]

You need to enable quinns repo's, go [here ]("http://compiz.net/viewtopic.php?id=2")for details. The search function also helps ;)

---

### Post by The_Major on 2006-04-24
[QUOTE=i386DX]I installed XGL following this thread.
It has some nice features (arrange windows with F12, ALT-TAB). But I hate those wobbly windows... How can i select wich feature I want and wich not?

I tried to remove the wobbly in thefuture, but the function remains...[/QUOTE]

Fire up Configuration Editor then select apps>compiz>general>allscreens>options and edit the active_plugins key and remove wobbly.

---

### Post by Paool on 2006-04-24
[QUOTE=EnTheEnd]Right, is there any way to "fix" the driver? Tried to reinstall nvidia-glx, didn't help...[/QUOTE]

Try **sudo depmod -a** and then **sudo modprobe nvidia**. works for me:mrgreen:

---

### Post by Corey on 2006-04-24
I've got an nvidia 5200 and I am getting this error:

compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

I've tried installing my own glitz from cvs and editing thefuture script with LD_LIBRARY_PATH=/usr/lib/nvidia in front of compiz but still no luck. I've also ran thefuture script about a thousand times! =)

Any other solutions for this problem?

---

### Post by playmesumch00ns on 2006-04-26
I have an nvidia geforece 6800 GO on a dell inspiron 9300 laptop.

After installing the 8756 drivers via method 2, i followed the guide here to gte xgl/compiz installed. Everything installed OK, but when trying to start compiz I got the ```
compiz.real: GLX_EXT_texture_from_pixmap is missing
``` error as well.

I then added the beerokid and compiz forums repos to my apt and updated my mesa, glitz and xserver-xgl to the latest versions synaptci would find.

After doing this compiz started but all the windows were borked: i could see about half the window decoration on each window with thick black borders around the outside, and the window contents were blank white. Although I could move the windows around and see them wobbling! And flip the cube (very cool). A quick ```
metacity --replace
``` brought my windows back, and in the terminal i had the error ```
compiz.real: Failed to bind redirected window xXXXXXXXX to texture
```

I tried fiddling around trying to update anything connected with compiz/xserver, but to no avail. Then after a reboot, X failed to start, or at least i was just left with a black screen!

I think I'll wait till dapper goes final before trying this again :)

---

### Post by s|k on 2006-04-26
transparency adjustements aren't working for me (cntrl+shift and mousewheel)

Everything else seems to though. Anyone know how to make that work?
Thanks. :)

---

### Post by Passenger on 2006-04-26
[QUOTE=s|k]transparency adjustements aren't working for me (cntrl+shift and mousewheel)

Everything else seems to though. Anyone know how to make that work?
Thanks. :)[/QUOTE]

Maybe you should try alt+shift and scrollwheel? :)

---

### Post by s|k on 2006-04-26
Actually not everything is fine. Everything worked at first, but after rebooting and typing 'thefuture' I just get a black screen. I have to hit cntrl+alt-backspace and log back into gnome to get it back to normal. What happened? Why doesn't it work anymore?

---

### Post by garba on 2006-04-27
just come back home with my brand new, humble nvidia 5200 and blam, everyhting seems to be working flawlessly, I'm kinda disappointed because i thought this would take some major tweaking but it wasn't the case wtf poofy your spoiling all the fun for us...

nice, very nice, but resizing windows is still too slow and not hardware accelerated, it's clear there's still much work left to do

---

### Post by JNik on 2006-04-28
Thanks for the guide. Everything works like a charm!

---

### Post by siorai on 2006-04-28
Would it still be a lost cause to install this with a dual monitor setup?

---

### Post by amp_man on 2006-04-29
[QUOTE=DigitalDuality]ok ok, i'm on dapper beta now, with the gnome desktop.  clean install.

when i follow the above guide, the moment i turn on "thefuture" i get the window bars that i should, but the entire screen freezes.  I can't open any menus, files, icons.  Can't switch between open windows.  Nothing.  I have to kill X just to do anything what so ever.

Any ideas?[/QUOTE]

I'm having the exact same issue, except that my install worked at first, but somehow got screwed in the few days that I was playing with other things (prelink/preload, themes, etc). Also, I've managed to get varying stages of this problem using other versions and settings. The closest I've gotten to having it work again was compiz removed all my window borders, but I could still use open apps (but not menus or anything on the taskbars), and transparency worked (I have a clock goes transparent when compiz runs), but desktop switching doesn't work at all (no effects nor does it change desktops). I've also posted this in the compiz forums, but I don't think it can hurt to post it here too.

---

### Post by dpm on 2006-04-29
Unfortunately, I did not use the script but the first method:

> Two ways to do that. Either go by what this post says (thanks g14) or use my small script:

This:

[http://www.ubuntuforums.org/showpost...&postcount=507]("http://www.ubuntuforums.org/showpost.php?p=760273&postcount=507") 
Well, that completely screwed my system.

The situation at the moment is that there's something wrong with the window manager: new windows appear without the title bar (i.e. I cannot close, minimize, maximize, resize or move windows), so I think there is something wrong with the window manager.

Also windows do not appear on the bottom panel window list as they used to and I've lost the workspace switcher. Also the usual GNOME shortcuts (I especially miss ALT+F2) are not working.

At the moment my system is a bit of a mess. Windows appear on top of each other, but I have no way of bringing focus to the ones in the background other than closing the ones on top.

I expected major breakage getting compiz to work, but unfortunately, I got the breakage even before getting to see it!

Any help will be greatly appreciated.

Thanks.

EDIT: I think it may have something to do with the compiz --replace bit, but unfortunately 'compiz --help' does not even tell me what 'replace' does and my knowledge of window managers is somehow limited. Am I still running metacity?

---

### Post by dpm on 2006-04-29
Ok, I sorted out my problem.

I noticed that metacity was not running, so I did a 
```

metacity --replace
``` and then logged out and back in again. Now my system is working as usual

I also uninstalled compiz and removed the gdm.conf-custom file.

The only confusing thing to me is that when I had the problem I couldn't see any window manager running. Why did compiz not show up in a 'ps -fe' command?

---

### Post by dpm on 2006-04-29
Ok, I do not learn.

Instead of forgetting about it, I went on and gave this whole compiz/Xgl thing another go.

No major breakage this time. I followed the guide up till the point where thefuture is executed. The problem is, when I do that the window titlebars disappear completely, which renders any window unusable. New windows appear on top of each other and there is no way to bring focus to the ones in the background. Don't panic. Ok, after my previous problem, I understand that there is a problem with the window manager. So, killing **compiz.real** and **gnome-window-decorator **and executing metacity from the terminal brings my system back to life. 

So, the question is: why does the window manager screw up when I launch 'thefuture'? 

Oh, I forgot to say: I've got a relatively old graphics card with the GeForce2 MX/MX 400 chipset, but I don't think that's the issue, since at least the driver (version 8756) seems to work fine. I firstly installed it in Breezy from the repos (can't remember which was the version back then) and then I reinstalled it in Dapper when I did the upgrade, also from the repos.

Thanks.

---

### Post by s|k on 2006-04-29
Has anyone solved how to get around the black screen?

---

### Post by ispmarin on 2006-04-29
It worked for me, but not very well...

---

### Post by PurpleMoggy on 2006-04-30
thanks, poofyhairguy, great guide......... it got me up and running very quickly :)


I've since moved on to the
> deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
repositories, and the [compiz](https://wiki.ubuntu.com/compiz) wiki entry, but this guide definately got me up and running :D


i'm amazed at how well this runs on my 32MB geforce2

---

### Post by woutervanwijk on 2006-04-30
If you have problems starting some apps, and get a complaint about colors, do this: sudo ln -s /usr/lib/X11/rgb.txt /usr/share/X11/rgb.txt

---

### Post by no1peanut on 2006-05-01
Well - I have now added the quinn repo's ... 
But something must be wrong here !!
Xgl wont start - and Xorg starts at VT2 instead of VT7?!

Is there somewhere I can find complete xorg.conf and gdm.conf and gdm.conf-custom so I can just replace mine to test out ?

At some point X screamed at me that nvidia was at a different version than my kernel modules ?? - but this has gone now ...
When gdm tries to start xgl I get no reason for why X cant start - just: fatal server error - couldnt open display 0

Pleazee... anyone

---

### Post by Przemekc1 on 2006-05-01
I think the best you should do is wait for stable version. I installed XGL twice and it never worked more then two days :(
But maybe somebody know what should I do with this error (after try of instaling XGL)
```
Fatal server error:
Could not open default font 'fixed'
XIO: Fatal IO error 104 (Connection reset by peer) on X server ":93.0"
after 0 requests (0 know processed) with 0 events remaining.
giving up.
```

---

### Post by louis_nichols on 2006-05-02
[COLOR="Red"]EDIT:[/COLOR]Strike the following please! It's sorted. It needed a Ctrl+Alt+Backspace and now works Grrrrreat. :D OMFG!!!

Hi! I followed the tutorial and, well... it starts. But all I get is this:

[[IMG]http://louis-nichols.uv.ro/compiz/Screenshot-1.jpeg[/IMG]]("http://louis-nichols.uv.ro/compiz/Screenshot-1.png")

The console spits out errors like ```
compiz.real: Couldn't bind redirected window 0x3600001 to texture
compiz.real: Couldn't bind redirected window 0x3a00001 to texture
compiz.real: Couldn't bind redirected window 0x3c00001 to texture
compiz.real: Couldn't bind redirected window 0x340001e to texture
compiz.real: Couldn't bind redirected window 0x3000001 to texture

```

Other than this, the wobbly effect is there. I mean, I can see window edges and things behave like I think they are supposed to, except that I can't really see them.

Please help! I've been dying to get this working!

---

### Post by hamil on 2006-05-02
Hello!

Followed this guide without problem, but ends up with some errors...
When restarting the machine, GDM is not able to start up.
I edited xorg,conf, and put nv instead of nvidia, and then I was able to startx.
I have read some of the posts, and decided to try the commands:
sudo depmod -a
sudo modprobe nvidia (after editing xorg.conf back to nvidia)

When restarting the machine again, I still am not able to startx, I get the following error message:
```
 /usr/bin/Xgl: error while loading shared libraries: 
libglitz.so.1: cannot open shared object file: 
No such file or directory
```

Editing nvidia to nv in the xorg.conf, lets me startx again.

Any help is highly appreciated!

Lasse

---

### Post by garba on 2006-05-02
[QUOTE=louis_nichols][COLOR="Red"]EDIT:[/COLOR]Strike the following please! It's sorted. It needed a Ctrl+Alt+Backspace and now works Grrrrreat. :D OMFG!!!

Hi! I followed the tutorial and, well... it starts. But all I get is this:

[[IMG]http://louis-nichols.uv.ro/compiz/Screenshot-1.jpeg[/IMG]]("http://louis-nichols.uv.ro/compiz/Screenshot-1.png")

The console spits out errors like ```
compiz.real: Couldn't bind redirected window 0x3600001 to texture
compiz.real: Couldn't bind redirected window 0x3a00001 to texture
compiz.real: Couldn't bind redirected window 0x3c00001 to texture
compiz.real: Couldn't bind redirected window 0x340001e to texture
compiz.real: Couldn't bind redirected window 0x3000001 to texture

```

Other than this, the wobbly effect is there. I mean, I can see window edges and things behave like I think they are supposed to, except that I can't really see them.

Please help! I've been dying to get this working![/QUOTE]


mmm just giving it a shot: try removing the "miniwin" plugin, just remove it from the list when starting compiz, who knows, maybe it will help, it did for me

---

### Post by krusbjorn on 2006-05-02
[QUOTE=hamil]Hello!

Followed this guide without problem, but ends up with some errors...
When restarting the machine, GDM is not able to start up.
I edited xorg,conf, and put nv instead of nvidia, and then I was able to startx.
I have read some of the posts, and decided to try the commands:
sudo depmod -a
sudo modprobe nvidia (after editing xorg.conf back to nvidia)

When restarting the machine again, I still am not able to startx, I get the following error message:
```
 /usr/bin/Xgl: error while loading shared libraries: 
libglitz.so.1: cannot open shared object file: 
No such file or directory
```

Editing nvidia to nv in the xorg.conf, lets me startx again.

Any help is highly appreciated!

Lasse[/QUOTE]

Are you sure you installed the glitz packages? If you did, try symlinking /usr/lib/libglitz.so.1 to /usr/lib/libglitz.so.1.0.0:

sudo ln -s /usr/lib/libglitz.so.1.0.0 /usr/lib/libglitz.so.1

---

### Post by hamil on 2006-05-02
[QUOTE=krusbjorn]Are you sure you installed the glitz packages? If you did, try symlinking /usr/lib/libglitz.so.1 to /usr/lib/libglitz.so.1.0.0:

sudo ln -s /usr/lib/libglitz.so.1.0.0 /usr/lib/libglitz.so.1[/QUOTE]

I am 100% sure that glitz was installed, checked with apt-get, and it returns that all is up to date and that it does not need to update anything.
Issuing the symlink command gives this output:
lasse@njord:~$ sudo ln -s /usr/lib/libglitz.so.1.0.0 /usr/lib/libglitz.so.1
ln: creating symbolic link «/usr/lib/libglitz.so.1» to «/usr/lib/libglitz.so.1.0.0»: File exists

Thanks for the reply, but I am not sure that my problem is solved yet, since it tells me that the file already exists??

Lasse

---

### Post by LordMau on 2006-05-03
Upgrading the following:

libgl1-mesa
libgl1-mesa-dri
libglu1-mesa

to the latest version at this time: *6.5.1-0ubuntu5 (dapper)* breaks compiz from QuinnStorm/ reggaemanu.

Had to Downgrade back to *6.5.1-0ubuntu4 (xgl.compiz.info)*

Guess we need to be careful in mixing repos for compiz.

---

### Post by tarasis on 2006-05-03
Anyone else find XGL broken this morning? I had been running fine for the last week, initially with these [instructions]("http://www.ubuntuforums.org/showthread.php?t=131267"), then moving to [QuinnStorm's]("http://compiz.net/viewtopic.php?id=2") repositorys.

Today, following an "apt-get update ; apt-get dist-upgrade" and restarting X & GDM, I get the following errors:

> :~$ compiz.real: No GLXFBConfig for default depth, this isn't going to work.
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0


I can see that GDM, libgl1-mesa, libgl1-mesa-dri, libglu1-mesa where upgraded

> 2006-05-03 10:51:13 upgrade libgl1-mesa-dri 6.5.1-0ubuntu4 6.5.1-0ubuntu5
2006-05-03 10:51:15 upgrade libgl1-mesa 6.5.1-0ubuntu4 6.5.1-0ubuntu5
2006-05-03 10:51:15 upgrade libglu1-mesa 6.5.1-0ubuntu4 6.5.1-0ubuntu5
2006-05-03 10:50:52 upgrade gdm 2.14.4-0ubuntu2 2.14.4-0ubuntu3

Is there any way to track this down, other than wait to see if the next upgrade fixes it?

Many thanks

Rob

---

### Post by Laterix on 2006-05-03
[QUOTE=tarasis]Anyone else find XGL broken this morning?[/QUOTE]
Yes, this is common problem after update. I downgraded mesa back to -ubuntu4 and it works just fine again. You can do this with synaptic's "Force version...".

Downgrade to these
libgl1-mesa-dri 6.5.1-0ubuntu4 6.5.1-0ubuntu4
libgl1-mesa 6.5.1-0ubuntu4 6.5.1-0ubuntu4
libglu1-mesa 6.5.1-0ubuntu4 6.5.1-0ubuntu4

I also had developement packages installed so I downgraded those too.

---

### Post by zeusave on 2006-05-03
Great post ... really great post it works perfectly over an ubuntu 6.06
Thanx a lot.

---

### Post by louis_nichols on 2006-05-03
[QUOTE=garba]mmm just giving it a shot: try removing the "miniwin" plugin, just remove it from the list when starting compiz, who knows, maybe it will help, it did for me[/QUOTE]

thanks for the advice, but it worked after a ctrl+alt+backspace.

I'm amaized!!!

---

### Post by garba on 2006-05-03
[QUOTE=louis_nichols]thanks for the advice, but it worked after a ctrl+alt+backspace.

I'm amaized!!![/QUOTE]

great! yeah compiz is coming along nicely can't wait to get opengl acceleration support for all cairo based apps :)

---

### Post by Vurdak829 on 2006-05-03
I wanna excuse myself because i haven't read all the posts...but i've a problem

```
vurdak@cthulhu:~$ thefuture
vurdak@cthulhu:~$ gnome-window-decorator: Another window decorator is already running
compiz.real: No GLXFBConfig for default depth, this isn't going to work.
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

```

---

### Post by louis_nichols on 2006-05-03
[QUOTE=garba]great! yeah compiz is coming along nicely can't wait to get opengl acceleration support for all cairo based apps :)[/QUOTE]


I'm not that much into technicalities, so I don't really know what that would mean. :)
================================================

Perhaps someone can help:

How is it they do the snap-to effects? I saw them in an animation and liked it. It had snap to another window's border and screen's edge.


Also, how can I rotate to the cube side on top? Saw that in a presentation too. :)

---

### Post by garba on 2006-05-03
[QUOTE=Vurdak829]I wanna excuse myself because i haven't read all the posts...but i've a problem

```
vurdak@cthulhu:~$ thefuture
vurdak@cthulhu:~$ gnome-window-decorator: Another window decorator is already running
compiz.real: No GLXFBConfig for default depth, this isn't going to work.
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

```[/QUOTE]

vurdak, i was having the same problem, then i used the following repos and everything works ok now, that's because of mesalib not being up-to-date... add the following to /etc/apt/sources.list:

deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

well, at least that's where i got my xgl stuff from, stuff i got from the beerorkid website didn't work for me

---

### Post by Vurdak829 on 2006-05-03
[QUOTE=garba]vurdak, i was having the same problem, then i used the following repos and everything works ok now, that's because of mesalib not being up-to-date... add the following to /etc/apt/sources.list:

deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

well, at least that's where i got my xgl stuff from, stuff i got from the beerorkid website didn't work for me[/QUOTE]

Done, but it doesn't works...same problem yet...

---

### Post by ghostzapper on 2006-05-03
Hi,

having the same GLXFBConfig problem since today's update. Can anyone confirm this? Using the repo's from xgl.compiz.info

thx

Ghostzapper

---

### Post by garba on 2006-05-03
[QUOTE=ghostzapper]Hi,

having the same GLXFBConfig problem since today's update. Can anyone confirm this? Using the repo's from xgl.compiz.info

thx

Ghostzapper[/QUOTE]

count me in... ](*,) ](*,) ](*,) ](*,) 

just did an apt-get upgrade from the xgl.compi.info repos and now that nasty glxfbconfig thingis is back, too bad... oh well

---

### Post by tarasis on 2006-05-03
Laterix provided the answer for me on the previous page. To quote:
> 

[QUOTE]
Originally Posted by tarasis
Anyone else find XGL broken this morning?

Yes, this is common problem after update. I downgraded mesa back to -ubuntu4 and it works just fine again. You can do this with synaptic's "Force version...".

Downgrade to these
libgl1-mesa-dri 6.5.1-0ubuntu4 6.5.1-0ubuntu4
libgl1-mesa 6.5.1-0ubuntu4 6.5.1-0ubuntu4
libglu1-mesa 6.5.1-0ubuntu4 6.5.1-0ubuntu4

I also had developement packages installed so I downgraded those too.[/QUOTE]

---

### Post by tarasis on 2006-05-03
Fantastic, new update available (Quinn's compiz) that fixes the broken XGL, very fresh it wasn't available less than an hour ago!

---

### Post by louis_nichols on 2006-05-03
[QUOTE=tarasis]Fantastic, new update available (Quinn's compiz) that fixes the broken XGL, very fresh it wasn't available less than an hour ago![/QUOTE]


Quinn's compiz? Dude, I'm seriously behind all this stuff!! :)

Unfortunately, mine broke after an upgrade also. So I guess I need quinn's update, too. Can you please tell me where to get it?

EDIT: typo

---

### Post by mrogers on 2006-05-03
I got this working way back when (Flight 4, I think), but never used it because Dapper was too "young" for me then. Now I have a fresh installation of Dapper, and I can't get XGL to work. All software packages are current as of today. I have nvidia drivers installed and working, but whenever I try to load the compiz window manager (using thefuture script), X crashes and resets. I've poked around but I'm not really sure where to start. Any help would be appreciated.

---

### Post by Vurdak829 on 2006-05-04
I have updated to Quinn's compiz's debs and all works ;)

---

### Post by louis_nichols on 2006-05-04
[QUOTE=Vurdak829]I have updated to Quinn's compiz's debs and all works ;)[/QUOTE]

same here! phew, what a relief.

---

### Post by garba on 2006-05-04
just did an apt-get upgrade and now it works again :) there repos are moving targets, it's normal u end up with some breakage from time to time

---

### Post by hamil on 2006-05-04
Well, hope that someone can help me..

I have an AMD64 machine, with Ubuntu 6.06 beta installed.
Followed the guide in the first post, but can not get anything to work.
After a reboot, my machine does not want to start x, I have to manualle type in startx.
X gives this erroroutput:
/usr/bin/xgl: error while loading shared libraries: 
libglitz.so.1: cannot open shared object file:
No such file or directory

I did try the symlinking as explained earlier in this thread.

If I am not able to make it work, is there a nice way to undo everything here, so I do not have to manually startx at every boot?

Thank you all
Lasse

---

### Post by krusbjorn on 2006-05-04
@hamil

Are you using the 64bit version of Ubuntu or the standard i386 one? Are your installed libglitz packages all version 0.5.5-0ubuntu2? What output do you get if you do "ls /usr/lib/libglitz*" in the terminal?

---

### Post by hamil on 2006-05-04
[QUOTE=krusbjorn]@hamil

Are you using the 64bit version of Ubuntu or the standard i386 one? Are your installed libglitz packages all version 0.5.5-0ubuntu2? What output do you get if you do "ls /usr/lib/libglitz*" in the terminal?[/QUOTE]


Hello!

I asked in another post, and was told to use the i386 version, since I have installed Ubuntu i386 on my AMD64 machine.

The libglitz packages is 0.5.3-0-ubuntu2, which is the newest available for me..

ls /usr/lib/libglitz* has this output:
```

/usr/lib/libglitz.a         /usr/lib/libglitz-glx.so.1.0.0
/usr/lib/libglitz-glx.a     /usr/lib/libglitz.la
/usr/lib/libglitz-glx.la    /usr/lib/libglitz.so
/usr/lib/libglitz-glx.so    /usr/lib/libglitz.so.1
/usr/lib/libglitz-glx.so.1  /usr/lib/libglitz.so.1.0.0

```

My sources.list, is like this:
```

deb http://archive.ubuntu.com/ubuntu dapper main restricted
# deb-src http://no.archive.ubuntu.com/ubuntu dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
# deb-src http://no.archive.ubuntu.com/ubuntu dapper-updates main restricted


##############
## Universe ##
##############
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
# deb-src http://no.archive.ubuntu.com/ubuntu dapper universe


##############
## Security ##
##############
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security multiverse


################
## Multiverse ##
################
deb http://archive.ubuntu.com/ubuntu dapper multiverse
# deb-src http://no.archive.ubuntu.com/ubuntu dapper multiverse

##############################
## Penguin Liberation Front ##
##############################
# deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
# deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

# deb ftp://ftp.free.fr/pub/Distributions_Lin … buntu/plf/ breezy free non-free
# deb-src ftp://ftp.free.fr/pub/Distributions_Lin … buntu/plf/ breezy free non-free

## Freecontrib, funny packages by the Ubuntu PLF Team
# deb ftp://ftp.free.fr/pub/Distributions_Lin … eecontrib/ breezy free non-free
# deb-src ftp://ftp.free.fr/pub/Distributions_Lin … eecontrib/ breezy free non-free


################
## Multimedia ##
################
# deb ftp://ftp.nerim.net/debian-marillat/ sarge main
# deb ftp://ftp.nerim.net/debian-marillat/ sid main
# deb ftp://ftp.nerim.net/debian-marillat/ etch main


#####################
## Multimedia/ DVD ##
#####################
# deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free


##########
## Java ##
##########
# deb http://ubuntu.tower-net.de/ubuntu/ breezy java


###############
## Backports ##
###############
# deb http://ubuntu-backports.mirrormax.net/ dapper-backports main universe multiverse restricted
# deb http://ubuntu-backports.mirrormax.net/ dapper-extras main universe multiverse restricted


#########
## E17 ##
#########
# deb http://ubuntu.nooms.de/ hoary/


############################
## Freemind, mind-mapping ##
############################
# deb http://eric.lavar.de/comp/linux/debian/ experimental/

###########
## Opera ##
###########
# deb http://deb.opera.com/opera/ etch non-free
# deb http://no.archive.ubuntu.com/ubuntu breezy main restricted

```

Thanks for your reply!

Lasse

---

### Post by krusbjorn on 2006-05-04
Lasse,

Most people are using QuinnStorm's and Reggaemanu's repositories to get the latest compiz, glitz, xserver-xgl, mesa etc. They put up forums on a separate place, since the xgl/compiz threads were littering these forums too much (and to be more distro-neutral).

[Here]("http://compiz.net/index.php") are the fourms, and you are probably interested in [this]("http://compiz.net/viewtopic.php?id=2") and [this]("http://compiz.net/viewtopic.php?id=74") thread.

---

### Post by pkallakuri on 2006-05-04
Somehow this doesn't work for me. As soon as I create the gdm.conf-custom and restart X or even do a full reboot, X starts up but gdm cannot. Below is what my gdm.log says: 

```
root@ion:/home/praveen # cat /var/log/gdm/\:0.log.2
Couldn't open RGB_DB '/usr/share/X11/rgb'

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux ion 2.6.15-21-386 #1 PREEMPT Fri Apr 21 16:43:33 UTC 2006 i686
Build Date: 16 March 2006
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.93.log", Time: Thu May  4 17:46:52 2006
(==) Using config file: "/home/praveen/xorg.conf"
Could not init font path element unix/:7100, removing from list!

Fatal server error:
no screens found
X connection to :93.0 broken (explicit kill or server shutdown).
root@ion:/home/praveen #
```

---

### Post by Alexander Grundner on 2006-05-04
**Poofyhairguy, thanks for the how-to!** It fixed my video player problems. Every player I tried lauching a video in would automatically close once I double clicked on the file. Previously, I was using an ATI 9800 card with the basic "ati" driver and had no problems, but for some reason Ubuntu doesn't have the same support for NVIDIA using "nv". FYI, I'm running a GeForce 6200 card now.

Funny thing, though... now when my PC boots up I see an NVIDIA splash screen before the Ubuntu login screen.

I'm also curious if others stopped at the point in the how-to where you use Poofyhairguy's "[small script](http://www.ubuntuforums.org/showpost.php?p=760273&postcount=507)" to get compiz to work. Everything seems to be working correctly, so I guess I did every thing right.

---

### Post by paperp on 2006-05-05
I followed the guide and installed everything right on a mepis 6.0, but whe I run thefuture, on the desktop appears a weird compositing of small squre , as the system trying to draw a lot of squares, after that , I find a lot of untitled windos on the bottom bar minimized but unrecognised, the terminal says:

.........
Event added!
Processing the next event...
InitializeMindow event received!
Event added!
Processing the next event...
CheckMindow event received!
Event added!
Processing the next event...
GL: GL_TEXTURE_RECTANGLE_ARB
Trying to create a mindow from a window
Event added!
Processing the next event...
CreateMindow event received!
Trying to create a simple mindow
Trying to initialize a mindow
Event added!
Processing the next event...
CreateMindow event received!
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
compiz.real: miniwin.c:970: miniwinCreateMindow: Assertion `dpy' failed.


...after that no decorations on the windows and the graphical reactyveness , is very difficult..often X crash...any idea??I got amd athlon and nvidia geforce 2 gts....: -((...help.

P.S. sorry for my terrible english.

---

### Post by garba on 2006-05-05
[QUOTE=paperp]I followed the guide and installed everything right on a mepis 6.0, but whe I run thefuture, on the desktop appears a weird compositing of small squre , as the system trying to draw a lot of squares, after that , I find a lot of untitled windos on the bottom bar minimized but unrecognised, the terminal says:

.........
Event added!
Processing the next event...
InitializeMindow event received!
Event added!
Processing the next event...
CheckMindow event received!
Event added!
Processing the next event...
GL: GL_TEXTURE_RECTANGLE_ARB
Trying to create a mindow from a window
Event added!
Processing the next event...
CreateMindow event received!
Trying to create a simple mindow
Trying to initialize a mindow
Event added!
Processing the next event...
CreateMindow event received!
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
compiz.real: miniwin.c:970: miniwinCreateMindow: Assertion `dpy' failed.


...after that no decorations on the windows and the graphical reactyveness , is very difficult..often X crash...any idea??I got amd athlon and nvidia geforce 2 gts....: -((...help.

P.S. sorry for my terrible english.[/QUOTE]

i was having the same problem, try removing the miniwin plugin

---

### Post by paperp on 2006-05-05
I have no miniwin plugin wrote signed in  my /usr/bin/thefuture file ,even the minize is over...:confused:

---

### Post by Mr. Polite on 2006-05-07
I'd like to keep XGL/Compiz installed, but video playback has been ruined on my machine. If its not possible to restore video playabck and keep XGL/Compix, I'd like to completely undo everything I've done. Any help is appreciated.

---

### Post by cyberdude on 2006-05-07
[QUOTE=Mr. Polite]I'd like to keep XGL/Compiz installed, but video playback has been ruined on my machine. If its not possible to restore video playabck and keep XGL/Compix, I'd like to completely undo everything I've done. Any help is appreciated.[/QUOTE]

are all videos messed up? on my setup ,it's just .wmv files that are messed upped:(

---

### Post by Mr. Polite on 2006-05-07
,wmv playback is messed up. Other formats play, but at a very low frame rate.

---

### Post by bowlby on 2006-05-09
My video was messed up too for wmv's. But changing the videodriver to opengl fixed that.

---

### Post by xOrphenochx on 2006-05-09
I haven't messed with it in a month or so, and in that time I did a large update, and installed the nvidia drivers from the site instead of the repo. Now whenever I try to start Xgl, it fails at loading glx. Simple as that.

---

### Post by ScarfaceIII on 2006-05-09
[QUOTE=Aphelion]Hi fellow Xgl users ;)

I managed to install Xgl and run compiz with this tutorial. It al works fine except some strange redraw? problems. Please look at the attached screenshot. Does anyone know how to fix this problem?[/QUOTE]

I have "the_exactly_same_problem"...but reading the following pages, :-k  I didn't understand if it's possible to solve or not, and, more important, HOW!!!:confused: :confused: :confused: 
...please HELP me...](*,) ](*,) ](*,)

---

### Post by sethmahoney on 2006-05-09
[QUOTE=xOrphenochx]I haven't messed with it in a month or so, and in that time I did a large update, and installed the nvidia drivers from the site instead of the repo. Now whenever I try to start Xgl, it fails at loading glx. Simple as that.[/QUOTE]

I would recommend going over the steps where you edit xorg.conf again and making sure they look like they do in the examples at the beginning of this thread.  Its possible that the driver installer messed them up.

---

### Post by xOrphenochx on 2006-05-09
I always keep a backup, nothing has changed. Sigh...only if it were that simple.

---

### Post by barsanuphe on 2006-05-09
[QUOTE=Mr. Polite]I'd like to keep XGL/Compiz installed, but video playback has been ruined on my machine. If its not possible to restore video playabck and keep XGL/Compix, I'd like to completely undo everything I've done. Any help is appreciated.[/QUOTE]

i had horrible video playback, but then i enable vsync and used the gl2 video engine in mplayer. 
now everything works like a charm and without tearing.

---

### Post by Mr. Polite on 2006-05-10
[QUOTE=barsanuphe]i had horrible video playback, but then i enable vsync and used the gl2 video engine in mplayer. 
now everything works like a charm and without tearing.[/QUOTE]

I was able to switch to the gl2 video engine in mplayer. But how do I enable vsync?

---

### Post by barsanuphe on 2006-05-10
i have a nvidia card so i just had to add:

export __GL_SYNC_TO_VBLANK=1

to my /etc/init.d/gdm. dont know if this works with ati cards. if it doesnt, theres probably an equivalent.

---

### Post by keshav0001 on 2006-05-10
[QUOTE=xOrphenochx]I haven't messed with it in a month or so, and in that time I did a large update, and installed the nvidia drivers from the site instead of the repo. Now whenever I try to start Xgl, it fails at loading glx. Simple as that.[/QUOTE]

just install the nvidia drivers from scratch..it will solve your problem

1. Ctrl+Alt+F2
2. sudo /etc/init.d/gdm stop
3. sudo apt-get remove nvidia-*
4. sudo NVIDIA-Linux-x86-1.0-8756-pkg1.run
5. sudo apt-get install linux-restricted-modules-'uname -a'
6. sudo apt-get install nvidia-glx

**and let any dependencies to be installed or uninstalled**
restart ur computer and u are done!

---

### Post by keshav0001 on 2006-05-10
one thing more you'll have to reinstall **mesa** packages as nvidia drivers messes with them..and you will have your compiz working again like a charm

---

### Post by keshav0001 on 2006-05-10
[QUOTE=paperp]I followed the guide and installed everything right on a mepis 6.0, but whe I run thefuture, on the desktop appears a weird compositing of small squre , as the system trying to draw a lot of squares, after that , I find a lot of untitled windos on the bottom bar minimized but unrecognised, the terminal says:

.........
Event added!
Processing the next event...
InitializeMindow event received!
Event added!
Processing the next event...
CheckMindow event received!
Event added!
Processing the next event...
GL: GL_TEXTURE_RECTANGLE_ARB
Trying to create a mindow from a window
Event added!
Processing the next event...
CreateMindow event received!
Trying to create a simple mindow
Trying to initialize a mindow
Event added!
Processing the next event...
CreateMindow event received!
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached
compiz.real: miniwin.c:970: miniwinCreateMindow: Assertion `dpy' failed.


...after that no decorations on the windows and the graphical reactyveness , is very difficult..often X crash...any idea??I[/QUOTE]



Install gset to configure compiz
on terminal
1.  sudo apt-get install Gset-Compiz
2.  gset-compiz

then disable miniwin
hope this helps

---

### Post by ScarfaceIII on 2006-05-10
[QUOTE=Aphelion]Hi fellow Xgl users ;)

I managed to install Xgl and run compiz with this tutorial. It al works fine except some strange redraw? problems. Please look at the attached screenshot. Does anyone know how to fix this problem?[/QUOTE]

Me and Aphelion asked more than once how to solve the problem...PLEASE, could anyone help us??? Just for reference the post I quoted is #15 on the second page...look at the screenshot, I really can't understand what's wrong with that...
I've read many pages (not ALL the pages) in the forum, but noboby talks about this...

---

### Post by xOrphenochx on 2006-05-10
Ok, no more GLX loading error, but it's still busted. Nothing seems to happen when I use this .Xsession like I did previous(and it worked). The xorg log shows no errors.

```
#!/bin/sh
# Start up Xgl, compiz, and GNOME
# Run Xgl server on :1, on top of normal X
Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo &
# Tell subsequent X programs to access the Xgl server at :1
DISPLAY=:1
# Start Compiz window manager
gnome-window-decorator &
compiz gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher &
# Start GNOME 
exec gnome-session
```

---

### Post by yusufk on 2006-05-11
[QUOTE=desp]Ok, I do not learn.

Instead of forgetting about it, I went on and gave this whole compiz/Xgl thing another go.

No major breakage this time. I followed the guide up till the point where thefuture is executed. The problem is, when I do that the window titlebars disappear completely, which renders any window unusable. New windows appear on top of each other and there is no way to bring focus to the ones in the background. Don't panic. Ok, after my previous problem, I understand that there is a problem with the window manager. So, killing **compiz.real** and **gnome-window-decorator **and executing metacity from the terminal brings my system back to life. 

So, the question is: why does the window manager screw up when I launch 'thefuture'? 

Oh, I forgot to say: I've got a relatively old graphics card with the GeForce2 MX/MX 400 chipset, but I don't think that's the issue, since at least the driver (version 8756) seems to work fine. I firstly installed it in Breezy from the repos (can't remember which was the version back then) and then I reinstalled it in Dapper when I did the upgrade, also from the repos.

Thanks.[/QUOTE]

I use XGL when my laptop is un-docked and use a script to return to normal X when docked because I then use twinview and XGL is not working perfectly on twinview yet. Anyway, recently the window manager gnome-wm stopped loading automatically and after some scratching around I figured that it has something to do with the gnome session settings. 

To cut a long story short, this fixed it:
```

rm .gnome2/session

```

Hope this helps

oh and you can open a shell as soon as you boot and type gnome-wm for a temp fix (till u reboot)

---

### Post by xOrphenochx on 2006-05-12
I tried doing a nested one and I got this, I'm sure this is the root of my problems. But alas, I haven't found a working solution to it.

```
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  1 (X_GLXRender)
  Serial number of failed request:  92
  Current serial number in output stream:  93
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":10.0"
      after 0 requests (0 known processed) with 0 events remaining.
Couldnt get a file descriptor referring to the console

```

---

### Post by OffHand on 2006-05-13
when I run thefuture in the terminal I get this error:

admin@dapper:~$ thefuture
admin@dapper:~$ gnome-window-decorator: Another window decorator is already running
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

It kills gnome. Anyone know how to solve this?

Edit: I tried to fix it with this:
admin@dapper:~$ ln -sf /usr/lib/nvidia/libGL.so.1.2.xlibmesa usr/lib/nvidia/libGL.so.1
ln: creating symbolic link `usr/lib/nvidia/libGL.so.1' to `/usr/lib/nvidia/libGL.so.1.2.xlibmesa': No such file or directory
Like you can see that didn't work.

---

### Post by Scunizi on 2006-05-14
I need to regress here a little...  I've got XGL & compiz working great with one exception.  The how to's at the beginning mention using xmodmap /usr/share/xmodmap/xmodmap.us for US keyboards.  When I did this I lost the ability to use /, *, -, & + from the numeric keypad... Any thoughts? or solutions?

---

### Post by alingatong on 2006-05-15
I need help running xgl+compiz in my laptop. Its a dell c840 with nvidia geforce4 440 with 32mb vram i think. It has 512 RAM and is pentium 4 2.0 ghz. I run xgl and compiz but after sometime of use (say about 20 seconds), when I maximize application windows I get a black screen when I minimize it I see the application. When I launch new apps my screen goes black only a cursor will show. When I move my cursor to the panel location, i see that the icons are slowly coming back. 

Why is this? can i run xgl+compiz with this grafix card? please i need help. I wanted to have this laptop because it has an nvidia card and hoping to run xgl+compiz but everything seems not right. what can I do?

---

### Post by Pausanias on 2006-05-16
[QUOTE=poofyhairguy]

**To Undo**

This command:
> 
sudo rm /etc/gdm/gdm.conf-custom



[/QUOTE]

A bunch of discovered that this method of undoing xgl/compiz causes gdmsetup to segfault when it's run. Apparently in the current version GDM, there **needs** an /etc/gdm/gdm.conf-custom file for gdmsetup. So, the solution is to backup your old gdm.conf-custom file before using the xgl/compiz instructions, and restore it if you want to undo.

For more info on this headache, see the following thread and bug report:

[http://ubuntuforums.org/showthread.php?t=172368](http://ubuntuforums.org/showthread.php?t=172368)
[https://launchpad.net/products/gdm/+bug/42712](https://launchpad.net/products/gdm/+bug/42712)

---

### Post by hitman012 on 2006-05-17
I've just installed Dapper from the liveCD and followed the instructions on the first post, but unfortunately running compiz (compiz --replace or thefuture) removes the borders on all the windows that I have open, but nothing more.

I can reset this by using metacity --replace, but it is confusing that compiz refuses to work. I have seen other people with the same problem in this thread, but no real solution - does anyone have an ideas?

---

### Post by Scunizi on 2006-05-17
After running "compiz --replace gconf miniwin decoration transset wobbly fade minimize cube rotate zoom scale move resize place switcher trailfocus water"  you should then run "nohup gnome-window-decorator &"... works for me.

---

### Post by hitman012 on 2006-05-18
[QUOTE=Scunizi]After running "compiz --replace gconf miniwin decoration transset wobbly fade minimize cube rotate zoom scale move resize place switcher trailfocus water"  you should then run "nohup gnome-window-decorator &"... works for me.[/QUOTE]
That fixed it right away :). Thanks for the quick response.

---

### Post by troorl on 2006-05-18
Hi!
Sorry, my English is very bad :(
My problem: I have allready install XGL on my Ubuntu Dapper. But animation in windows is very slow, video in Totem is very slow too (specialy in fullscreen). This problem doesn't exist when Compiz is not running (when nothing in the top of the windows). Tell me, what is wrong?? 
And also in Tvtime (Avermedia 203) scene isn't exist – only green fake...

My video card is Nvidia Geforce 6600, drivers is ok.

PS. I'm speak Ukrainian and Russian.

---

### Post by michaelharg on 2006-05-18
Hey! I'm struggling to get XGL+Compiz set up, my graphics card is a Geforce Ti4200 8xAGP so i think i have to install Glitz, how do i do this?

I have tried "sudo apt-get install glitz" and googled around but still cant find anything.

Any help would be great... Thanks!

---

### Post by hitman012 on 2006-05-18
[QUOTE=michaelharg]I have tried "sudo apt-get install glitz" and googled around but still cant find anything.

Any help would be great... Thanks![/QUOTE]
I downloaded the latest version from [here]("http://www.freedesktop.org/wiki/Software/glitz"), extracted it and then used make to compile it. You'll need to apt-get *gcc*, *build-essential* and *make* before you can do that. Once they're downloaded, go to the extracted glitz directory and type "./configure", then "make" and then "make -install" once it's done without errors.

---

### Post by michaelharg on 2006-05-18
Which version did you use? The only downloads i can find are the development snapshots..

---

### Post by hitman012 on 2006-05-18
I used the glitz-0.5.3.tar.gz snapshot.

---

### Post by michaelharg on 2006-05-18
I get an error message saying:
--
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
---

What do i do now?

---

### Post by hitman012 on 2006-05-18
Did you apt-get build-essential?

---

### Post by michaelharg on 2006-05-18
No, i hadn't. 

Ive done "make" and "make install" without any errors now so it should be done now. Is there any way i can check?

Should i just continue with the install as per the HOWTO in this thread?

Much thanks Matey..

---

### Post by michaelharg on 2006-05-18
I'm just going through the second part of the HOWTO and i dont have the GLcore or dri modules on my xorg.conf file. This shouldn't make a difference because they are commented out but i just want to be careful because i have allready broken one install by trying to get xgl up and running...

---

### Post by hitman012 on 2006-05-18
Yep, once I'd installed I continued with the howto and it worked fine. As for GLcore and dri - I definitely didn't have GLcore but I think that I did have dri. I wouldn't worry about it.

---

### Post by michaelharg on 2006-05-18
Ive got it all up and running now, thanks very much for your help!

---

### Post by albyrock87 on 2006-05-19
Java with Swing GUI can't output anything with Compiz window Manager..](*,) 
Anyone have the solution??
Thanks..]

---

### Post by userundefine on 2006-05-21
OK, I've got XGL set up (thanks to the great guides here!) and working beautifully, but have a small issue.  A "blank" window on the dock appears while moving between windows and I can't really identify where it comes from, and it won't go away.  Anyway, when I mouseover it on the dock XGL crashes along with my window titles.  I can restart it quickly with 'thefuture', but it'd be nice if there was a workaround or fix.

Has anyone else experienced this?

---

### Post by Alexander Grundner on 2006-05-21
[QUOTE=jroes]Hey guys,

I just wanted to add that if you don't run the xmodmap line, shift+backspace will probably kill your X session.  It does for me.

If you -do- run the xmodmap line, though, you won't have a lot of other shortcuts working.

"casimir" on #ubuntu-xgl offers this suggestion, which works for us (instead of running the xmodmap line):

```
xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"
```

The original poster of this thread might want to change that xmodmap line so no one else has the same problems.

--Jonathan Roes[/QUOTE]

Is there a quick way to make this permanent? When I reboot the changes are gone.

---

### Post by xOrphenochx on 2006-05-22
Ok, it works now, but I still have a weird mouse problem. You can see the glitch if you look in the middle of the screen, stuff like that follows my mouse when ever I move it, and it isn't static. Any idea as to how I can fix this?

Screenshot:
[http://img238.imageshack.us/img238/1235/screenshot6fh.jpg](http://img238.imageshack.us/img238/1235/screenshot6fh.jpg)

---

### Post by lithorus on 2006-05-22
[QUOTE=albyrock87]Java with Swing GUI can't output anything with Compiz window Manager..](*,) 
Anyone have the solution??
Thanks..][/QUOTE]
Depends on the app. Eg. jEdit have the option to use swing for the window border which fixes it.

---

### Post by Bazon on 2006-05-22
[QUOTE=troorl]Hi!
Sorry, my English is very bad :(
My problem: I have allready install XGL on my Ubuntu Dapper. But animation in windows is very slow, video in Totem is very slow too (specialy in fullscreen). This problem doesn't exist when Compiz is not running (when nothing in the top of the windows). Tell me, what is wrong?? 
And also in Tvtime (Avermedia 203) scene isn't exist – only green fake...

My video card is Nvidia Geforce 6600, drivers is ok.[/QUOTE]
Hi troorl and welcome to the forums!

Fullscreen video playback is a generall issue in XHL and is not solved yet, because ther is no xv driver for XGL. (Direct rendering in XGL is only available to compiz, but not to applications as glxinfo will tell you....)

Therefore I suggest you to be able to run a Xorg session, in which you can watch fullscreen videos or run 3-D games.

Ther are two ways:

1. Decide at login at GDM whether to run Xorg or a fullscreen nested XGL session. (see [here](https://wiki.ubuntu.com/XglHowto) ot [there](http://www.ubuntuforums.org/showthread.php?t=174233))
2. Start two X-Servers: Xorg and XGL to switch between with CTRL+ALT+F(7/8__) (see [here](http://www.ubuntuforums.org/showpost.php?p=1035288&postcount=30))

I'm using the second method (and recommend it as you don't have to logout to run Xorg, simply switch to it.)

---

### Post by lithorus on 2006-05-22
[QUOTE=Bazon]Hi troorl and welcome to the forums!

Fullscreen video playback is a generall issue in XHL and is not solved yet, because ther is no xv driver for XGL. (Direct rendering in XGL is only available to compiz, but not to applications as glxinfo will tell you....)

Therefore I suggest you to be able to run a Xorg session, in which you can watch fullscreen videos or run 3-D games.

Ther are two ways:

1. Decide at login at GDM whether to run Xorg or a fullscreen nested XGL session. (see [here](https://wiki.ubuntu.com/XglHowto) ot [there](http://www.ubuntuforums.org/showthread.php?t=174233))
2. Start two X-Servers: Xorg and XGL to switch between with CTRL+ALT+F(7/8__) (see [here](http://www.ubuntuforums.org/showpost.php?p=1035288&postcount=30))

I'm using the second method (and recommend it as you don't have to logout to run Xorg, simply switch to it.)[/QUOTE]
There is another possibility. I just tested this with my ATI/fglrx setup. Start mplayer with the following command gives me fullscreen output but not through the Xgl session.
> DISPLAY=:0 gmplayer -fs -vo xv filename
I would believe the same thing is possible with an Nvidia setup.

---

### Post by sciyoshi on 2006-05-23
Hey subsonic and anyone else with GLX_EXT_texture_from_pixmap problems:

The new nvidia packages have files in different locations. Here's the command I used to get things working:
```

sudo ln -sf /usr/lib/nvidia/libGL.so.1.2.xlibmesa /usr/lib/libGL.so.1
```

---

### Post by gadget_me on 2006-05-23
thanks a lot! xgl and compiz working fine for me. but "F12" for mapping windows doesn't seem to work! help me please...

---

### Post by xOrphenochx on 2006-05-23
Fixed my problem. Is dual head really broken right now? I have it set up for tvout and I can't access :0.1 anymore, is there any work around?

---

### Post by ubuntnoob on 2006-05-24
Sorry if this has been posted before but ths thread is REALLY long and I don't have 6 hours to kill reading through it.

I followed the instructions and XGL works perfectly. EXCEPT it changed the resolution on my laptop to 1024x768.  How can I change it back to the native 1280x800?

Also "Alt-wheel" and "super-wheel" do not work for transparency and zoom.

My video card is Geforce go7600.
In my xorg.conf it still shows the correct res where it should but the option for 1280x800 doesn't appear in System > Preferences > Screen Resolution

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x768" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x768" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x768" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x768" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x768" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x768" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
```

Any help would be greatly appreciated.

---

### Post by ubuntnoob on 2006-05-24
Ok. I fixed my problem. I just removed all other resolutions from the 24bit line and restarted.

---

### Post by tuxcantfly on 2006-05-25
Xgl and compiz work fine with just about everything for me; it's all nice and smooth, except with openoffice.org. For some reason, while all other apps start just as fast as normally, openoffice starts, and takes a very long time to draw its widgets, and while I scroll, it constantly pauses for a few seconds and redraws them. Removing openoffice.org-gnome and openoffice.org-gtk helped speed up the widget-drawing process, and by disabling compiz, it stops rerendering them, yet xgl still performs by far slower on openoffice.org than on standard xorg. It's not my graphics card; it's a geforce 6500, and I have all the latest drivers, and all the eye candy works fine and fast for me. I tried lots of apps, and the problem only occurs with openoffice.org. Has anybody else had this problem, and is it an issue with xgl or openoffice.org?

---

### Post by Alexander Grundner on 2006-05-25
I asked this question earlier but no one has responded. How do you **make the following command permenant** to resolve X rebooting when holding down both **SHIFT + Backspace**?

```
xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"
```

I tried altering keycode 22 in the xmodmap.us file, but it still had no effect.

---

### Post by ErikTheRed on 2006-05-25
Anyone had success using kde-window-decorator yet? It doesn't work at all for me.

---

### Post by E-Jey on 2006-05-26
I've tried "thefuture" script for almost 30 times. But is doensn't work. There are some errors in my .xscreen-error files. Does anybody know how to solve this problem?

My .xscreen-error file: 
```

  GNU nano 1.3.10                                 File: /home/erik/.xsession-errors

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "erik"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/erik:/tmp/.ICE-unix/4792
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
compiz.real: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
compiz.real: No managable screens found on display :0.0

(gnome-panel:4861): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(gnome-panel:4861): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -21 and height 24

```

Thanks in advance!

---

### Post by panurge77 on 2006-05-26
compiz.real: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.

Are you using the --replace option at your script?

---

### Post by E-Jey on 2006-05-26
[QUOTE=panurge77]compiz.real: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.

Are you using the --replace option at your script?[/QUOTE]

Yes, i'm absolutely sure! I forgot to say that i'm running Twinview

---

### Post by mcarlson on 2006-05-26
Hmm.. I've tried this a number of times and failed.
I've read through this whole thread (and a few others) and I am not sure what my problem is so I'm finally going to ask for help in tracking it down.

I have an onboard GeForce 6100
I have installed the newest drivers (1.0-8762) using tseliots script.
I have updated my xorg.conf
I have installed xgl using the apt-get command on the first page of this howto
I created gdm.conf-custom (cut and paste from the howto)
I created thefuture, rebooted a number of times, and kept on trying...

What I get:
The dreaded "compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0"

Then my mouse stops allowing me to change window focus, and I have to clt-alt-back to get things working again.

Does anyone see what I'm doing wrong???
](*,) 

Thanks

---

### Post by thero on 2006-05-26
If you are using something like thefuture script to start compiz, you could add that line under the compiz start line in the file.

---

### Post by panurge77 on 2006-05-26
try searching twinview how-to's. there might be some specific needs about that...

that may help:
[http://www.ubuntuforums.org/showthread.php?t=172026&highlight=twinview+xgl+nvidia](http://www.ubuntuforums.org/showthread.php?t=172026&highlight=twinview+xgl+nvidia)

also, be sure you're running the latest debs around. it might help

---

### Post by Nelson-Ray on 2006-05-28
Hey thanks for this guide it worked like a charm for me....I have one question. While using the xgl stuff I like the rotating cubes a lot, the transparency is ok....and the wobbing effect I dont care for at all (when programs open). Is it possible to disable that portion and still have the rotating desktop and transparency? thanks...

---

### Post by Horizon on 2006-05-28
[QUOTE=Nelson-Ray]Hey thanks for this guide it worked like a charm for me....I have one question. While using the xgl stuff I like the rotating cubes a lot, the transparency is ok....and the wobbing effect I dont care for at all (when programs open). Is it possible to disable that portion and still have the rotating desktop and transparency? thanks...[/QUOTE]
Incase you haven't already you can apt-get install gset-compiz and use it to customize compiz to your likes.

---

### Post by smitty1276 on 2006-05-29
You said to make your xorg.conf "Device" section look exactly like yours, aside from Identifier.  DoOes that include the BusID? (It seems like it couldn't but maybe I'm missing something) Mine is "PCI:2:0:0".  If I change it to say "PCI:1:0:0" like yours does my X server won't start. If I don't change it then X will start but I keep getting the ...

"GLX_EX_texture_from_pixmap is missing ... Failed to manage screen: 0 ... No managable screens found on display :0.0" 

... error that has been mentioned earlier.

I am running with a GeForce 6600GT AGP. What's the story with the missing extension?

---

### Post by dr_d on 2006-05-29
hi lads... sorry i'm not up to date with this thread or the status of xgl/compiz on ubuntu.

would i be correct in assuming from Nelson-Ray's post that we finally have transparency working in dapper? if so, does it work by default, or does it have to be enabled somehow?

cheers!

---

### Post by Horizon on 2006-05-29
[QUOTE=dr_d]hi lads... sorry i'm not up to date with this thread or the status of xgl/compiz on ubuntu.

would i be correct in assuming from Nelson-Ray's post that we finally have transparency working in dapper? if so, does it work by default, or does it have to be enabled somehow?

cheers![/QUOTE]

Everything is working...probably better than breezy

---

### Post by slimsam1 on 2006-05-29
When I close a window, there is a good chance that the X server will crash. I think it might have something to do with a plugin, but even when I disabled all but gconf, it still happened. I also don't like the panel at the bottom with tiny copies of all the windows. I'd like to get rid of it. Any ideas?

---

### Post by Ma_USMC on 2006-05-29
I just wanted to post that I used a combination of this tutorial and the tutorial located [here]("http://compiz.net/viewtopic.php?id=652").  I am now in complete amazement at how versatile this app is.  Thank you to those who have taken the time to write these.

---

### Post by moclippa on 2006-05-30
Thanks a lot! This is great! Wasn't expecting it all to be this cool at all.... 

For your info this seems to work perfectly fine on a Toshiba Tecra Laptop... so other laptop users shouldnt have much trouble at all!

---

### Post by moclippa on 2006-05-30
By the way, this guide also fixed up some video problems I was having with my Nvidia card... so it killed two birds with one stone! I know this is beta, but I havent had much of a problem with it so far, the window wobble is not too much of a bother once you get the refresh rate right (as in the guide)

Running on Daper 6.06 like a charm :)

(Hope the Alt-Tab switcher gets fixed up though... the thumbnails arent perfectly clear for me, so sometimes it can be irritating trying to figure out what window I'm switching into.... 

*Another Suggested Fix* Instead of having a view of 3 windows at a time in the switcher, it would be nice to have them all laid out in small tab form... that way I know where everything is and how many Tabs its going to take to get there

---

### Post by kart3r on 2006-05-30
I've done everything right, but when i try to do thefuture it says that Gtk.blabla cannot sart display''
 :(

---

### Post by moclippa on 2006-05-30
Is it just me? Did anyone else loose functionality in DeskBar after doing this? I seem to not be able to type into it anymore :-?

---

### Post by PriceChild on 2006-05-30
```
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
``` 
[quote=vtechstu]Ok my problem is pretty much the same.  The first time i run thefuture, i get the above output.  All other attempts i get this:
```

thefuture
gnome-window-decoraor: Another window decorator is already running
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

``` 
Any idea's what I could do?  I followed the steps exactly I think.  Might something from other wm attempts before, or compmgr attemps be messing this up?  Thanks.  Please help.[/quote] 
I'm getting this same problem... and this thread is soooo HUGE that i can't find an answer anywhere near :(

---

### Post by dr_d on 2006-05-31
does anyone know how to solve the following problems?
(in order of importance)


1) vlc media player does not have a title bar when xgl/compiz is running. this means it is effectively useless and i cannot play music or watch videos

2) transparency is either not enabled or doesn't work

3) certain short cut keys dont work (i had the super key open up a terminal... while my other short cuts work, this one does not work when xgl/compiz is running)

4) gnome 'themes' do not work. for example if i set my ordinary desktop to have the clearlooks theme, the minute i fire up xgl/compiz it is lost

5) screen goes blank when shutting down. the nice ubuntu splash screen does not play in reverse any more



I know a lot of these problems are just cosmetic, and probably there is no fix as of yet for most of them, but if there are any fixes out there I'd really like to know about it. Especially for the first two issues.

Thanks!

---

### Post by thomashauk on 2006-05-31
Which repo is compriz in because apt-get doesn't find it?
I'm wrecking the old breezy install.

---

### Post by arctu on 2006-05-31
[QUOTE=PriceChild]```
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
``` 
 
I'm getting this same problem... and this thread is soooo HUGE that i can't find an answer anywhere near :([/QUOTE]


After 2 days, I managed to get down to this problem. The reason for this to happen is because of libGL (mesa and nvidia).

How to fix it:
> 
[LIST]
[*]Reinstall the latest NVidia driver (8762) from the dapper repo. [COLOR="Red"]**IMPORTANT** I have try installing it using NVidia's own sh installer and it totally broke OpenGL.[/COLOR]
[*]Reinstall libgl1-mesa
[/LIST]


This works for me. It seems that the dapper repo 8762 is compatible with the latest libgl1-mesa([http://xgl.compiz.info/](http://xgl.compiz.info/)) while NVidia's official ones don't. OR maybe, I missed something.

Now I face this problem where the compiz shortcuts won't work. Anybody got a fix for this? I'm using the latest pkg from [http://xgl.compiz.info/](http://xgl.compiz.info/).

---

### Post by PriceChild on 2006-05-31
Thankyou so much arctu!!!

This is sooo much cooler than anticipated and little/no performance hit on full screen games!

Love you all, Pricey

---

### Post by olterman on 2006-05-31
I installed this on my machine without a hitch everything rocked and I wobble till I bleed .... but installing on my wifes machine it all worked fine until I tried to run a video with mplayer, the only vo driver that works is X11 but since that doesn't resize that sucks, gl2 runs ok speed to but the whole screen flashes with white screens randomly anyone got this and can help 

0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)

Got the latest packages of dapper for all the other stuff

---

### Post by katzman on 2006-05-31
Hello; I just found about XGL this morning and found this guide, I followed it on a old media box / file server and it worked fine but when i tried it on my laptop....not so hot. When i use Xgl as the server the graphics and corrupted.  Lines are staaggerd so that the pixels do not line up and you can't make heads or tails of it. I am wondering if this has anyhting to do with the latest nvidia drivers from the repos since my other linux machine has the older one still
here is a sample of the corruption:
[IMG]http://img287.imageshack.us/img287/9877/screwed4rm.jpg[/IMG]
Specs:
Nvidia 6600 go with the 8762 driver
pentium-M 1.86
kernel 2.6.15-23.39 , 686

---

### Post by PriceChild on 2006-06-01
Im' using the newer linux drivers from the repos... try reinstalling the nvidia drivers?

---

### Post by katzman on 2006-06-01
I tried reinstalling the drivers with no success. also tried connecting my laptop to a CRT monitor to see if it had anything to do with  my laptop's screen but identical behaivour

in addtion I also tried using a nested XGL window to connect to a XDMCP server (both client and server using regular Xorg server) and got similar results
[IMG]http://img213.imageshack.us/img213/4159/screenshotxglx4qm.png[/IMG]

some output
Couldn't open RGB_DB '/usr/share/X11/rgb'
No matching visual for __GLcontextMode with visual class = 4 (32770), nplanes = 24
No matching visual for __GLcontextMode with visual class = 4 (32770), nplanes = 24

---

### Post by renzokuken on 2006-06-01
just before i attempt this, i need to clear something up.

i have set up dual monitors (TFT monitor as main and TV as secondary) via tseliot's excellent guide here  --> [http://www.ubuntuforums.org/showthread.php?t=98456&highlight=nvidia](http://www.ubuntuforums.org/showthread.php?t=98456&highlight=nvidia)

will this effect my ability to install and use xgl/compiz???

thanks

---

### Post by ViGiLnT on 2006-06-01
I've just followed this guide and everything went well besides one thing:

The shortcuts <ctrl>-<alt>-<left> or <ctrl>-<alt>-<right> to rotate the cube doesn't work. I can use the <ctrl>-<alt> and use the mouse to rotate it but not the above command...

I already went to see if the shortcuts were assigned on the gconf-editor and they were! The transparency shortcut don't work too...

What can I do ?

On another note, I've read that dual screen with the quinn's xgl/compiz work well. Is that true ? What must I do to change to the CVS available at quinn's repos ?

Thanks.

---

### Post by ViGiLnT on 2006-06-01
Ok. I've rebooted and everything but the transparency is working like a charm :P

I've got another question... The transparency that i saw on kororaa is a plugin for compiz right ? Pressing shift and mouse wheel up and down i mean, and changing the window transparency.

---

### Post by 23meg on 2006-06-01
[QUOTE=ViGiLnT]Ok. I've rebooted and everything but the transparency is working like a charm :P

I've got another question... The transparency that i saw on kororaa is a plugin for compiz right ? Pressing shift and mouse wheel up and down i mean, and changing the window transparency.[/QUOTE]
If you're using the version of Compiz from the Dapper repos that feature isn't available. You can update to the latest CVS build to have it. Check out [http://forum.compiz.net](http://forum.compiz.net)

---

### Post by ViGiLnT on 2006-06-02
With the "deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
" repo in my sources.list I have the last CVS build of compiz.

I am now running xgl at full speed with xinerama support on my dual-screen setup.

It's perfect!

My specs:
- nvidia GeForce 6600 GT 128MB AGP
- 2 x Samsung SyncMaster 753DFX

---

### Post by TripleE on 2006-06-02
XGL is working great.  It took a little playing though.  Good how to.

_____________
Thanks,
TripleE

AMD Athlon64 3000+, 1 GB RAM, Asus A8S-X
BFG Geforce 7300 GS pci-e x16
Raid0 2x 80gb SATA HD

---

### Post by encompass on 2006-06-02
> Change every line but the &#8220;Identifier&#8221; line to look just like mine:

Code:

Section "Device" Identifier- leave this line alone! Driver "nvidia" BusID "PCI:1:0:0" Option "RenderAccel" "true" EndSection


I just wanted to say that the busID setting is fine unless your running something like pci.  Like me.  The fix was easy becuase after looking at the error log I noticed I just needed to use nano and changed it to PCI:2:7:0 and now it all works fine.

BTW... in 6.06 they won't even let your screensave start and I don't have what I use often 'Always on top'  Sucky...
But hey, looks cool for my friends.  And it will work great for my demo at the linux seminar this september.
You may or may not want to mention that one in your howto.

Noticed some other things:  Try getting you menu to unstick from the file drop down.  Like in dia.  Click the little arrow to remove the menu and use it in a differnet location... you can't it will get stuck there.

I have also noticed that popup windows that have no close, minimize or icon on the left, for instance when copying files in nautilus.  You can't move those windows.
Quick update... you CAN move those popups wiht the ALT+Click feature.  So That error is really no big deal.

---

### Post by nami on 2006-06-02
[QUOTE=ViGiLnT]With the "deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
" repo in my sources.list I have the last CVS build of compiz.

I am now running xgl at full speed with xinerama support on my dual-screen setup.

It's perfect!

My specs:
- nvidia GeForce 6600 GT 128MB AGP
- 2 x Samsung SyncMaster 753DFX[/QUOTE]

I'm planning on trying out xgl/compiz tonight.  Can you please give instructions on how you got it to work properly with twinview?

thanks

---

### Post by ViGiLnT on 2006-06-02
It was really simple.

Just followed this guide and everything worked right away on my single screen setup, except for the plugins that are only available on the quinn's repository.

Then i updated my sources.list to include the quinn's repo. I added:

deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
deb-src [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main

I did like it is explained on [http://xgl.compiz.info/](http://xgl.compiz.info/) to had those repos, the difference was that I added the "deb-src" one.

Then i did sudo apt-get update and all my compiz packages were updated to the ones on quinn's repos.

The I got xinerama working.

I did like i always do, i followed this guide (now I don't need it anymore, cause i already know how to do it, but i learned from there) - [https://www.linux-magazine.com/issue/17/DualHead.pdf](https://www.linux-magazine.com/issue/17/DualHead.pdf)

Here's my xorg.conf:

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon May 15 13:23:42 PDT 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "left"
    Screen         "right" RightOf "left"
    Option         "Xinerama" "on"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"

    # path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "pt"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "monitor0"
    Option         "DPMS"
    ModelName      "SYNCMASTER 753DFX"
    VendorName     "SAMSUNG"
    HorizSync	   30-71
    VertRefresh    50-160
EndSection

Section "Monitor"
    Identifier     "monitor1"
    Option         "DPMS"
    ModelName      "SYNCMASTER 753DFX"
    VendorName     "SAMSUNG"
    HorizSync	   30-71
    VertRefresh    50-160
EndSection

Section "Device"
    Identifier     "device0"
    Driver         "nvidia"
    VendorName     "NVidia"
    BoardName      "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    BusID 	   "PCI:1:0:0"
    Option	   "RenderAccel" "True"
    Screen         0
EndSection

Section "Device"
    Identifier     "device1"
    Driver         "nvidia"
    VendorName     "NVidia"
    BoardName      "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    BusID 	   "PCI:1:0:0"
    Option	   "RenderAccel" "True"
    Screen         1
EndSection

Section "Screen"
    Identifier     "left"
    Device         "device0"
    Monitor        "monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "right"
    Device         "device1"
    Monitor        "monitor1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```

---

### Post by ViGiLnT on 2006-06-02
Now I've got only one question.

Is it ok for me to add "thefuture" command to the startup sequence of gnome on sessions, so that i don't have to type "thefuture" every time I boot ubuntu ?

Another thing:

"xmodmap /usr/share/xmodmap/xmodmap.pt"

When i run this one now, I can't alt-tab and fade windows with alt-mouse wheel.
What does that do ? Do I need it ? I'm running xgl without doing that with no problems...

---

### Post by nami on 2006-06-02
ViGiLnT - Thanks for the info.  I will give this a try tonight!

About adding "thefuture" to the startup.  I DO remember reading something about it.  For example, it should be added late in the startup sequence.

That's about all I remember.  :)

---

### Post by PriceChild on 2006-06-02
[quote=ViGiLnT]Now I've got only one question.

Is it ok for me to add "thefuture" command to the startup sequence of gnome on sessions, so that i don't have to type "thefuture" every time I boot ubuntu ?

[/quote]

Hmm.... it should be ok. However, i haven't... just incase my nvidia drivers are updated, i won't want it enabled always at startup just incase something goes wrong.

For example, after a kernel upgrade, i will need to reconfigure x, reinstall my nvidia drivers, which i would prefer to do in a terminal in gnome, rather than in tty1.

Pricey

---

### Post by Mr. Polite on 2006-06-02
Wow, this thread is a monster.

I've tried searching but haven't seen a fix to my problem. Everything works fine, except _some_ windows like the font dialog in Inkscape, or the connect dialog in XChat don't have window controls. No minimize, no close, and the window can not be moved. This is only a problem in Inkscape, where the dialog window may be coving part of a drawing I'm working on.

Any help is appreciated.

---

### Post by mayo on 2006-06-02
Thanks for this great guide. Worked like a charm.
Although compiz doesn't seem to be ready for productive use. Where most of the apps work great (and look great) I'm experiencing a lot of graphical glitches in multimedia players (e.g. the menus are all messed up).

---

### Post by nami on 2006-06-02
Hi

I am trying to follow the instructions on the first page.  I got to the bit where it says type the following in the terminal

sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome

But when I do it says 

Couldn't find package compiz

Why is this happening?

nami

---

### Post by nami on 2006-06-02
ok i got that bit working

but how do i do this?

Make sure your default color depth is 24!

Anyway, I did everything else,  for the language but insteadof typing .us i typed in .uk

Is that correct?

then i did everything else restarted and everything

then i typed

thefuture over 100 times and it just breaks gnome in that i dont have any titlebar or window frame and gives me this error

compiz.real: GLS_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

Why is it not working for me?

---

### Post by Esurnir on 2006-06-02
I'm trying to install it but the compiz can't be download through the aptget program it seems :-k

---

### Post by nami on 2006-06-02
Yeah I had the same problem, I forgot to enable ALL the repos! :D

---

### Post by Gijith on 2006-06-02
Hey Everybody

I'm trying to follow this guide. I've got pretty fresh dapper install. nvidia 6600. I used Automatix. That's about all I've touched.

It seemed to be going fine. I followed everything to the letter. But when it came time to reboot, X wouldn't start. When I turned my computer on, it showed me this:

Couldn't open RGB-DB '/usr/share/X11/rgb'

I'm not sure if this is the extent of the problem. I did a search for this error, but couldn't find anything. Any help would be greatly appreciated. 
Thanks.

---

### Post by nami on 2006-06-03
> You must compile the newest CVS version of glitz to get this to work with Nvidia cards that lack Pixel Shaders (aka anything older than a 5200 FX). Hopefully this will be updated in the repository soon.

I have a GeForce 4 Ti 4200

So does this mean I have to compile the newest CVS version of glitz?

If yes, it that the reason why I break gnome each time I run "thefuture"?

PLEASE HELP - I'm dying to get this working!

nami

---

### Post by panoz on 2006-06-03
[QUOTE=Gijith]Hey Everybody

I'm trying to follow this guide. I've got pretty fresh dapper install. nvidia 6600. I used Automatix. That's about all I've touched.

It seemed to be going fine. I followed everything to the letter. But when it came time to reboot, X wouldn't start. When I turned my computer on, it showed me this:

Couldn't open RGB-DB '/usr/share/X11/rgb'

I'm not sure if this is the extent of the problem. I did a search for this error, but couldn't find anything. Any help would be greatly appreciated. 
Thanks.[/QUOTE]

I just finished installing it on a fresh installation of 6.06, and it works like a charm on an athlon XP 3200+ with nvidia 6600 GT !!

Many thanks for a wonderfull guide =D> \\:D/

---

### Post by marciano on 2006-06-03
[QUOTE=nami]I have a GeForce 4 Ti 4200

So does this mean I have to compile the newest CVS version of glitz?

If yes, it that the reason why I break gnome each time I run "thefuture"?

PLEASE HELP - I'm dying to get this working!

nami[/QUOTE]

I have the same card, and did not have to recompile anything. (This on a Dell P4 2.8Ghz. The only problem is that you don't get accelerated xv, which means that e.g. mplayer is quite slow.

The "thefuture" script works fine here. Also, perhaps it's just my impression, but there seems to be a speedup e.g. in Firefox redraws and rendering in general. Is this possible? 

Overall, I'd say FANTASTIC JOB GUYS, even though this is still a bit alphaish quality. [Or maybe the Ti 4200 is really a bit too long in the tooth for this kind of stuff...]

M

---

### Post by 3cHeLoN on 2006-06-03
Hi, thanks for your wonderful guide.

I think  xgl is installed correctly, everything works. Except, when I run nvidia-settings I get the message:
> ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.

Also there are some options missing. I have a xfx geforce 5500 128mb.
Do you now how I can solve this?

P.S.
Does anybody know how to add transparacy (for the terminal) in xgl/compiz?

---

### Post by nami on 2006-06-03
[QUOTE=marciano]I have the same card, and did not have to recompile anything. (This on a Dell P4 2.8Ghz. The only problem is that you don't get accelerated xv, which means that e.g. mplayer is quite slow.

The "thefuture" script works fine here. Also, perhaps it's just my impression, but there seems to be a speedup e.g. in Firefox redraws and rendering in general. Is this possible? 

Overall, I'd say FANTASTIC JOB GUYS, even though this is still a bit alphaish quality. [Or maybe the Ti 4200 is really a bit too long in the tooth for this kind of stuff...]

M[/QUOTE]

That can only mean that I am doing something wrong.  What am I doing wrong?

---

### Post by ike on 2006-06-03
It all seems to work very well. I have one problem though. My "Alt Gr" key does not seem to work. I suspect that it has got something to do with the xmodmap command.

Any ideas?

---

### Post by heretic9 on 2006-06-03
I followed the howto for xgl in the ubuntu wiki. When I launch compiz it results in a white screen with my only my mouse being displayed. The mouse moves and everything but I can't access anything, the screen is just white.

I'm running kubuntu (64 bit version) on an acer laptop with nvidia 7300

oh and is there any way to check if xgl is actually running? top doesn't show xgl but it doesn't show xorg either.

---

### Post by ScarfaceIII on 2006-06-03
Hi everybody!!! 
I used this guide (except for the fact that I add the repo for new xgl packages) multiple times on the same PC, every time it worked well, except last time, when I installed the brand new 6.06 LTS. everything goes fine, I boot up, login, enter the Xgl session, but sometimes, when I close a window (not all the times, only sometimes!!!) seems like the X session crashes and it restarts from the login screen (like when you press Ctrl-Alt-Del). Does anyone know something about this? Could anyone help me? please! I really can't figure out what went wrong!

THANX very much!

---

### Post by Hazzybo on 2006-06-03
Hey guys. I am a amd64 user with an nvidia card, i just installed the final release of 6.06 and tried to install xlg following the howto guide on the ubuntu website. When i log out and change the session to xgl and log on, it just hangs for about 10 seconds with the curser and the default orange background before returning back to the log on screen. Help! 

Cheers

---

### Post by dimaash on 2006-06-03
Hi everyone.

I am new to ubuntu (but not linux) and currently running Ubuntu 6.06. I am trying to get Xgl/compiz working but so far I've been unsuccessful. My first, and for the moment only, question is what nvidia driver is compatible with Xgl/compiz? Cause poofyhairguy says to get the nvidia driver from ubuntu repository. My driver was built using Nvidia's NVIDIA-Linux-x86-1.0-8762-pkg1.run script. Then i edited /etc/X11/xorg.conf and downloaded compiz, xserver-xgl, libgl1-mesa,  libglitz-glx1 & compiz-gnome just like it says in this howto. Then i edited /etc/gdm/gdm.conf-custom accordingly and when i rebooted the X told me the following:
```
(EE)Failed to initialize GLX extension. Compatible NVIDIA X driver not found.
```
Note, i did have 
```
Option 		"RenderAccel"
```
and 
```
Option  "Composite" "Enable"
```
in my xorg.conf together and separately. 

So what i am doing wrong here? Any help is appriciated.

By the way, i have GeForce FX 5600. (just in case)

---

### Post by ike on 2006-06-04
[QUOTE=heretic9]I followed the howto for xgl in the ubuntu wiki. When I launch compiz it results in a white screen with my only my mouse being displayed. The mouse moves and everything but I can't access anything, the screen is just white.

I'm running kubuntu (64 bit version) on an acer laptop with nvidia 7300
[/QUOTE]

Did you install compiz-kde?

---

### Post by kakulacis on 2006-06-04
I'v got error:
$ compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

I actually don't even have compiz property set in gconf-editor/apps

I'v vanilla kernel 2.6.16.11 and nvidia 8762 video driver, followed few howtos but no luck ](*,) Maybe problem with my graphic card? I'v MX440, which in my opinion do not have pixel shaders.

---

### Post by double0seven on 2006-06-04
everytime i run xgl i get a segmentation fault. but it shows no other errors, any ideas what could be wrong?

---

### Post by michelk on 2006-06-04
[QUOTE=encho]OK, I'm the unlucky one. All I got is this message:

$ thefuture
$ compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
[/QUOTE]

Haven't browsed the whole thread to see whether the solution I found worked, but I had this same problem pop up after messing about with my nvidia video drivers because of another problem. The solution I has was to reinstall the mesa libraries with ```
sudo apt-get --reinstall install libgl1-mesa
```. It took me several hours to think of this solution so I thought I'd better mention it here for future reference.

---

### Post by nami on 2006-06-04
OK, I want to try this one more time.

I have installed another fresh uptodate install of ubuntu 6.06

I followed this guide:
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html](http://www.albertomilone.eu/europeo/nvidia_scripts1.html)

to install nvidia drivers 8762_32 for dapper drake 6.06

and I have added a repository to my sources.list file so I have the LATEST cvs for libglitz

deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

What do I do now?  Do I follow the guide on the first page again?

Do I need to do: sudo apt-get install nvidia-kernel-common nvidia-glx

or should I leave that out as I have already got the drivers working?

and I live in the uk so is this line accurate for uk users
xmodmap /usr/share/xmodmap/xmodmap.**uk**

???

Any advice will be appreciated greatly!

Thanks

nami

p.s. how do i check which kernal i have?

---

### Post by ferre on 2006-06-04
I've a little problem..?The command "thefuture" run the xgl but every time when I start some application the sistem crash and it return to the log-in screen...there's somethings to do?..

---

### Post by ferre on 2006-06-04
[QUOTE=dimaash]Hi everyone.

I am new to ubuntu (but not linux) and currently running Ubuntu 6.06. I am trying to get Xgl/compiz working but so far I've been unsuccessful. My first, and for the moment only, question is what nvidia driver is compatible with Xgl/compiz? Cause poofyhairguy says to get the nvidia driver from ubuntu repository. My driver was built using Nvidia's NVIDIA-Linux-x86-1.0-8762-pkg1.run script. Then i edited /etc/X11/xorg.conf and downloaded compiz, xserver-xgl, libgl1-mesa,  libglitz-glx1 & compiz-gnome just like it says in this howto. Then i edited /etc/gdm/gdm.conf-custom accordingly and when i rebooted the X told me the following:
```
(EE)Failed to initialize GLX extension. Compatible NVIDIA X driver not found.
```
Note, i did have 
```
Option 		"RenderAccel"
```
and 
```
Option  "Composite" "Enable"
```
in my xorg.conf together and separately. 

So what i am doing wrong here? Any help is appriciated.

By the way, i have GeForce FX 5600. (just in case)[/QUOTE]
Try to cancel Option "Composite" "Enable"
I had this problem too and i've resolve it doing this operation...good luck...

---

### Post by nami on 2006-06-04
Im in the uk and am not sure if i am supposed to do

xmodmap /usr/share/xmodmap/xmodmap.**uk**
or
xmodmap /usr/share/xmodmap/xmodmap.**gb**

---

### Post by vikking on 2006-06-04
Okay, it doesn't work, I compiled glitz from CVS, I did sudo apt-get install nvidia-kernel-common nvidia-glx, I changed xorg.conf (there wasn't a GLcore module, is that bad?), set my depth to 24 in the xorg.conf, changed the device in that same file, I did sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome, changed gdm.conf-custom, made the thefuture command, and when I restarted, the X server (or gdm) wouldn't start, the screen kept blank... What am I doing wrong?
I have a GeForce4 420 Go.

---

### Post by nami on 2006-06-04
I CANT BELIEVE IT FINALY WORKED!!!  I musted have reinstalled ubuntu over 20 times! lol

However, when i type "thefuture" in the terminal it says

> nami@nami-desktop:~$ thefuture
nami@nami-desktop:~$ compiz.real: water: GL_ARB_fragment_program is missing

Anyone know why this happens?

nami

---

### Post by kakulacis on 2006-06-04
[QUOTE=michelk]Haven't browsed the whole thread to see whether the solution I found worked, but I had this same problem pop up after messing about with my nvidia video drivers because of another problem. The solution I has was to reinstall the mesa libraries with ```
sudo apt-get --reinstall install libgl1-mesa
```. It took me several hours to think of this solution so I thought I'd better mention it here for future reference.[/QUOTE]

Found this solution in other forum, tried to reinstall everything but no luck :-k 

glxinfo says:
GLX_ARB_get_proc_address, GLX_EXT_import_context, GLX_EXT_visual_info,
GLX_EXT_visual_rating, GLX_SGI_make_current_read, GLX_SGI_swap_control,
GLX_SGI_video_sync, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
[COLOR="Red"]**GLX_EXT_texture_from_pixmap** [/COLOR]:confused:

---

### Post by ike on 2006-06-04
[QUOTE=ike]It all seems to work very well. I have one problem though. My "Alt Gr" key does not seem to work. I suspect that it has got something to do with the xmodmap command.

Any ideas?[/QUOTE]

I think I found a solution. I changed back to swedish keyboard layout in gnome-keyboard-properties. Somehow the layout was changed to something I didn't want (think it was US)..

---

### Post by nami on 2006-06-04
try adding


deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

to your sources.list

---

### Post by varunmittal91 on 2006-06-04
I am using NVIDIA GEforce fx 5200 graphic card.
When I try running compiz in the terminal I get the following error message.

varun@edubuntu:~$ compiz.real: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
compiz.real: No managable screens found on display :0.0

what should I do.
I am using edubuntu 6.06 LTS fina release version.

---

### Post by Ska87 on 2006-06-04
I'm trying to install xgl and compiz with Quinn's packages.
I've installed all the packages that I need, I've configured xorg.conf, I've modded gdm.conf-custom to run xgl xserver, but when I load compiz and gnome-window-decorator, nothing happens No errors, but I lost only metacity that is killed.
So I've tried to view compiz script, and I've seen that it preload the libGL that it need. So I tried to launch manually that command, and I obtain this:
```

ska@ska-pc:~$ LD_PRELOAD=/usr/lib/nvidia/libGL.so.1.2.xlibmesa compiz.real --replace gconf
Segmentation fault

```

There is something wrong I think... but what?
I'm using a dapper from long time, my last fresh install was dapper flight 6, and then I've only updated the system. I haven't a fresh install of dapper final...

This is my xorg.conf, it was configured to run a old version of compiz, the 0.0.7 one, but at that time it worked.
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
    FontPath    "/usr/share/X11/fonts/misc"
    FontPath    "/usr/share/X11/fonts/cyrillic"
    FontPath    "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/Type1"
    FontPath    "/usr/share/X11/fonts/100dpi"
    FontPath    "/usr/share/X11/fonts/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load    "i2c"
    Load    "bitmap"
    Load    "ddc"
    Load    "dbe"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "type1"
    Load    "vbe"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "logiitc"
    Option        "XkbLayout"    "it"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "Device"
    Identifier    "NVIDIA Corporation NV36.2 [GeForce FX 5700]"
    Driver        "nvidia"
    BusID            "PCI:1:0:0"
    Option        "RederAccel"    "true"
    Option        "PageFlip"         "on"
    Option        "NvAGP"                "1"
    Option        "NoLogo"            "1"
    Option        "AllowGLXWithComposite"        "true"
EndSection

Section "Monitor"
    Identifier    "Acer AL1916W"
    Option        "DPMS"
    Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
    HorizSync    30.0 - 82.0
    VertRefresh  56.0 - 76.0
    DisplaySize  144 90
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation NV36.2 [GeForce FX 5700]"
    Monitor        "Acer AL1916W"
    DefaultDepth    24
    SubSection "Display"
        Depth        24
        Modes        "1440x900"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Extensions"
    Option  "Composite" "Enable"
EndSection

```

---

### Post by nami on 2006-06-04
you just need to add

> deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main

to your sources.list and you will have the most uptodate packages including Quinns packages!

---

### Post by codecaine on 2006-06-04
I followed all the instructions it worked for my laptop for my desktop when I try to do the keyboard command its does nothing any suggestions?

---

### Post by codecaine on 2006-06-04
I got everything to work only thing that don't work is alt + ctrl and left mouse to  rotate the desktop anybody know how I can manually config it?

---

### Post by fuuma_monou on 2006-06-04
I'm using a 32MB GeForce2 MX 400 (nVidia NV11). Compiz works fine for the most part, though video playback is slow. For some reason VLC's title bar is missing; the Dapper package seems to be buggy (keyboard shortcuts only work with the the mouse pointer over the video area). Starting aMule maxes out CPU usage, making the system unusable until I switch back to Metacity.

Guess I'll have to wait for future versions of Xgl and Compiz that work better with older cards, or just bite the bullet and get a GeForce FX5500.

---

### Post by totempole on 2006-06-04
Thanks for all the info contained in this thread, however I have come across an unusual bug (dont know if it is one yet). Right after I installed and got xgl and compiz working with my Dell E1705 (nvidia geforce 7900 GS) laptop, deskbar seems not to work. It shows in my toolbar but i cant click "into" it and type suff.
Anyone have any similar problems and any suggestions?

Thanks in advance.

---

### Post by ferre on 2006-06-05
[QUOTE=ScarfaceIII]Hi everybody!!! 
I used this guide (except for the fact that I add the repo for new xgl packages) multiple times on the same PC, every time it worked well, except last time, when I installed the brand new 6.06 LTS. everything goes fine, I boot up, login, enter the Xgl session, but sometimes, when I close a window (not all the times, only sometimes!!!) seems like the X session crashes and it restarts from the login screen (like when you press Ctrl-Alt-Del). Does anyone know something about this? Could anyone help me? please! I really can't figure out what went wrong!

THANX very much![/QUOTE]
I have the same problem...Does anyone can help we?thanks...

---

### Post by Ska87 on 2006-06-05
[QUOTE=Ska87]I'm trying to install xgl and compiz with Quinn's packages.
I've installed all the packages that I need, I've configured xorg.conf, I've modded gdm.conf-custom to run xgl xserver, but when I load compiz and gnome-window-decorator, nothing happens No errors, but I lost only metacity that is killed.
So I've tried to view compiz script, and I've seen that it preload the libGL that it need. So I tried to launch manually that command, and I obtain this:
```

ska@ska-pc:~$ LD_PRELOAD=/usr/lib/nvidia/libGL.so.1.2.xlibmesa compiz.real --replace gconf
Segmentation fault

```

There is something wrong I think... but what?
I'm using a dapper from long time, my last fresh install was dapper flight 6, and then I've only updated the system. I haven't a fresh install of dapper final...

This is my xorg.conf, it was configured to run a old version of compiz, the 0.0.7 one, but at that time it worked.
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
    FontPath    "/usr/share/X11/fonts/misc"
    FontPath    "/usr/share/X11/fonts/cyrillic"
    FontPath    "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/Type1"
    FontPath    "/usr/share/X11/fonts/100dpi"
    FontPath    "/usr/share/X11/fonts/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load    "i2c"
    Load    "bitmap"
    Load    "ddc"
    Load    "dbe"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "type1"
    Load    "vbe"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "logiitc"
    Option        "XkbLayout"    "it"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "Device"
    Identifier    "NVIDIA Corporation NV36.2 [GeForce FX 5700]"
    Driver        "nvidia"
    BusID            "PCI:1:0:0"
    Option        "RederAccel"    "true"
    Option        "PageFlip"         "on"
    Option        "NvAGP"                "1"
    Option        "NoLogo"            "1"
    Option        "AllowGLXWithComposite"        "true"
EndSection

Section "Monitor"
    Identifier    "Acer AL1916W"
    Option        "DPMS"
    Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
    HorizSync    30.0 - 82.0
    VertRefresh  56.0 - 76.0
    DisplaySize  144 90
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation NV36.2 [GeForce FX 5700]"
    Monitor        "Acer AL1916W"
    DefaultDepth    24
    SubSection "Display"
        Depth        24
        Modes        "1440x900"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Extensions"
    Option  "Composite" "Enable"
EndSection

```[/QUOTE]
...up

---

### Post by jstroot on 2006-06-05
Hey all, 
My screensaver will not activate, and I also cannot lock my screen.

Any ideas?

---

### Post by smartalecks on 2006-06-05
how would you "turn off" compiz? (using a launcher)
its a bit too heavy sometimes.

---

### Post by tomasmekean on 2006-06-05
I am a noob to ubuntu and to linux.  I tried to follow this guide and now when I reboot I get this error.  Failed to start the X Server (your graphical interface).  It is likely that it is not set up correctly.

anyway this is where I am.  and I do not know what to do but reinstall.

Please help

---

### Post by TeeAhr1 on 2006-06-05
I hope this hasn't been covered upthread (it probably has :roll: ), but 114 pages looked a little daunting.  Anyway, I got as far as reboot, whereupon the X server promptly puked on my carpet, leaving this (log file excerpt follows):
```
(EE) Failed to initialize GLX extension (compatible NVIDIA X driver not found)
Error opening security policy file /etc/X11/xserver/SecurityPolicy
(EE) xf860OpenSerial: Cannot open device /dev/wacom
no such file or directory
(EE) xf860OpenSerial: Cannot open device /dev/wacom
no such file or directory
*Note: six more of that, ending with a thud:*
Fatal server error:
no visual format found
```
I removed the gdm.conf-custom file, which got me back here.  But I am flummoxed.  Anyone know where to go from here?  Thx in advance, as always...

-pete

---

### Post by katzman on 2006-06-06
[QUOTE=smartalecks]how would you "turn off" compiz? (using a launcher)
its a bit too heavy sometimes.[/QUOTE]



metacity --replace &

---

### Post by mmcmonster on 2006-06-06
Thanks for the great tutorial.  Looks great so far.

For those of you who notice that the wheel on their mouse no longer works after this, try the alternate step 5 in [my post on another thread]("http://www.ubuntuforums.org/showpost.php?p=1069100&postcount=5").

---

### Post by nickdr on 2006-06-06
wow this is freaking amazing, and makes me love ubuntu this much more *holds hands as far apart as can*
anyways my only problem is .wmv video playback. in totem i get sound and some video, i don't know how to describe it other then when you put your refresh rate too high and you get two of everything. i hope you guys know what i am talking about. i tried the video in other players like mplayer or vlc, but i only got audio, which is working perfectly.
is there any fix to this? all other format seem to be working, .mpg, .avi, etc etc.

---

### Post by phoenix_1983 on 2006-06-07
OMG... this is amazing..

Thanks for this thread... Why get vista when you Linux looks as pretty as this...

only issue is that i can't change my desktop themes... is there a work around that someone has found??

---

### Post by gullf1sk on 2006-06-07
[QUOTE=vtechstu]Ok my problem is pretty much the same.  The first time i run thefuture, i get the above output.  All other attempts i get this:
```

thefuture
gnome-window-decoraor: Another window decorator is already running
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

```

Any idea's what I could do?  I followed the steps exactly I think.  Might something from other wm attempts before, or compmgr attemps be messing this up?  Thanks.  Please help.[/QUOTE]

OK, i got the same problem as this guy here.. It says another window decorator is already running. This is probably answered somewhere in the thread, but i gotta be somewhere next month so i dont have the time to browse through 107 pages of possible sollutions. 

Does anyone know what could be causing this?

---

### Post by winfree on 2006-06-07
[QUOTE=ferre]I have the same problem...Does anyone can help we?thanks...[/QUOTE]

Computer with XGL on GeForce4 MX 440 AGP8.
I my case, I've installed in dapper, xgl and compiz with Quinn's packages.  Installed all required packages needed. I configured xorg.conf and gdm.conf-custom to run xgl xserver. Also, set up Sessions to run xgl from start up.

When I start the computer, it stops at the remote login window, scans for hosts with XDMCP, finds none and nothing else can be done, just rebooting.

What can I change to show the regular login screen.

Anyone any idea? I cannot login to dapper, had to reboot to w2k to access this forum.

---

### Post by gullf1sk on 2006-06-07
[QUOTE=gullf1sk]OK, i got the same problem as this guy here.. It says another window decorator is already running. This is probably answered somewhere in the thread, but i gotta be somewhere next month so i dont have the time to browse through 107 pages of possible sollutions. 

Does anyone know what could be causing this?[/QUOTE]

OK, i think i figured it out.
I had to add a repository. 

deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

After that i ran apt-get update.
After a while it said that some updates were available, so i updated, and viola!
It worked. I hope this will help someone with this frustrating problem!

---

### Post by nami on 2006-06-07
You might want to add this iswell:
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main

Will give you all the latest stuff! :)

---

### Post by gullf1sk on 2006-06-07
Will do! :)
I ran in to a few crashes tho. Like when i am using VLC, after i close it, i get booted outta X, and it restarts.

---

### Post by nami on 2006-06-07
In the terminal try typing:

> xmodmap /usr/share/xmodmap/xmodmap.**us**

the .**us** is your country, so if you are in the uk you will need to type:

> xmodmap /usr/share/xmodmap/xmodmap.**uk**

Does this stop you from getting booted out?

If yes, then add it into your compiz start script so it runs each time.

---

### Post by gullf1sk on 2006-06-07
I'll give it a try.

edit: Still getting tossed out and strange behaviour of windows

---

### Post by rudefyet on 2006-06-07
just installed ubuntu and set up xgl/compiz

Noticed the opacity adjustment via alt-mouswheel isn't working

I ran gconf-editor and there isn't anything mapped to <Alt>Button4 or <Alt>Button5

Where the heck is my opacity?!

---

### Post by myyr on 2006-06-07
Hi


I did everything as mentioned in the how-to in the beginning and it works BUT....
ofcourse theres a BUT....
when i try to change the decorations the system-preferences-theme thingy gives me an error and it shows me that i have 'custom' theme WITHOUT any decorations.
the real problem is that i can't move some of the windows - usually those smaller ones like the themes -window and others also, like 'open...' -window. the colored bar above window is teher but i can't 'grab' it to move the window, also there are no controls on it eg 'close', 'minimize' etc. 

and then theres the fullscreen thing - some programs can't do fullscreen anymore (like f-spot partially). there's a smallish 'window' in the upper left corner but no fullscreen....

ps. sorry it these issues heve been addressed in earlier post but over 100 pages are too much to read through...

---

### Post by gullf1sk on 2006-06-07
I get this error from time to time "No pixmap found! This can be fatal! Don't do that!"
Sometimes it just spams 10 lines of it, but xgl still works, other times i get booted from xgl back to normal X. Anyone know what causes this?

---

### Post by BitTorrentBuddha on 2006-06-07
I can't get this working for the life of me, for starters, my xorg.conf doesn't have any "dri" or "GLcore" so I ignored that, then I followed the rest of the instructions, and when trying to run thefuture, I just keep getting
```
gnome-window-decorator: Another window decorator is already running
compiz.real: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
compiz.real: No managable screens found on display :0.0

```
I've done it over 50 times and still nothing. Any suggestions, I'm really eager to play with my new video card :D .

---

### Post by myyr on 2006-06-08
[QUOTE=BitTorrentBuddha]I can't get this working for the life of me, for starters, my xorg.conf doesn't have any "dri" or "GLcore" so I ignored that, then I followed the rest of the instructions, and when trying to run thefuture, I just keep getting
```
gnome-window-decorator: Another window decorator is already running
compiz.real: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
compiz.real: No managable screens found on display :0.0

```
I've done it over 50 times and still nothing. Any suggestions, I'm really eager to play with my new video card :D .[/QUOTE]

I had the same problem but check that u have **--**replace in your thefuture -script.  bBasically i copy-pasted my thefuture again and it started working.

---

### Post by ketsugi on 2006-06-08
When I run the compiz command, my gnome panels disappear, and my title bars for all windows disappear. I can no longer alt-tab or switch windows by clicking. I can no longer switch desktops. All applications continue to function otherwise as per normal (I'm typing this in a Firefox window with no title bar now).

---

### Post by Klaidas on 2006-06-08
YAY!!!! :mrgreen: 
I finally got XGL to work. I didn't even think I could do that and not break my system!!
Thanks poofyhairguy!!!!

---

### Post by xerum on 2006-06-09
Bit of a noob here and I was wondering if I could get some assistance. I recently installed xgl and compiz and for some reason i can't seem to get the cube desktop to display. I issued the following command at the prompt and got the error listed below 'compiz gconf' Thanks in advance


compiz.real: Connection Error (No reply within specified time)
compiz.real: Couldn't initiate D-BUS connection
compiz.real: Disabling D-BUS Service
Finishing dbus10786: arguments to dbus_bus_release_name() were incorrect, assert ion "connection != NULL" failed in file dbus-bus.c line 789.
This is normally a bug in some application using the D-BUS library.
10786: arguments to dbus_connection_close() were incorrect, assertion "connectio n != NULL" failed in file dbus-connection.c line 1934.
This is normally a bug in some application using the D-BUS library.
compiz.real: No composite extension

---

### Post by Jaidee on 2006-06-09
Hello,

I've had Xgl and Compiz working on this laptop about two months ago, did a clean Dapper 6.06 install and now I'm having issues getting back to where I was in Beta 2.

I've installed the NVidia proprietary drivers, they work fine.

I've installed Xgl, and I'm booting it up as a session using the instructions from the wiki.

I've installed Compiz and the beerorkid and compiz repos, and updated everything to the latest version.

When I try and issue the command:

```
gnome-window-decorator &
```

my X just crashed and reboots. I don't know where to look for an error code. I haven't even got to replacing gconf with Compiz yet as this command causes some sort of crash.

Please help, and tell me if I'm being too vague!

---

### Post by SamMessing on 2006-06-10
I am trying to install XGL, but I am running into a simple problem:

When I try and run:
```
sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome

```

I get the following error:
```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package compiz

```

anyone know how to solve this? Sorry if this is a somewhat obvious question, I am still very new to linux.

---

### Post by yteh on 2006-06-10
poofyhairguy...... thanks for the howto!!!!!

---

### Post by Toe on 2006-06-10
works perfectly for me!

thanks a lot! :)

---

### Post by tsunade on 2006-06-10
The compiz effects work for me, but i have a bug with my mouse pointer. When compiz is running, i can't see my mouse pointer :-k . If compiz is **not** running, the 'picture' underneath the pointer doesn't update immediately.

Also, the xmodmap changes each time on reboot.

Any suggestions? :rolleyes:

---

### Post by MasterOfDisaster on 2006-06-10
thanks for the help

---

### Post by someusernoob on 2006-06-10
Want to say thanx for the tutorial. I did it a few times now, can set it up in under 2 minutes. That's amazing, and no problems at all with it. Thumbs up (Y)

---

### Post by BarfBag on 2006-06-10
Working perfectly for me.  Very clear, easy to understand instructions.  THANKS!  :mrgreen:

---

### Post by tzyn on 2006-06-10
Nice guide. Thats my 6. guide i tried, but I finally got it.

But I got a little problem why I can't use Xgl at all.

if I use the "switcher" with alt+tab the frame (where I normally can move the window) disappears and the whole system seems to be hanging. But I can do something in the open windows. Some things disappears (even i closed them with alt+f4). I hope you understand what I mean.

The other functions of Xgl work fine. 

Someone got that problem, too?

---

### Post by BarfBag on 2006-06-10
I've run into a problem.  Key shortcuts don't work at all.  How do I fix this?

---

### Post by Visceral Monkey on 2006-06-10
This guide: [http://chromakode.blogsome.com/2006/02/16/howto-compiz-xgl-on-ubuntu-for-the-morbidly-lazy-2/](http://chromakode.blogsome.com/2006/02/16/howto-compiz-xgl-on-ubuntu-for-the-morbidly-lazy-2/)

Worked for me the first time and takes less than 5 minutes to do. Just another method for those having trouble with the other methods. Also note, I've updated using Quinns stuff and it all works fine.

---

### Post by SamMessing on 2006-06-10
I was following the installation instructions and when I got to the place right before the command:

```
xmodmap /usr/share/xmodmap/xmodmap.<language>
```

I rebooted, as it says to do. Upon booting up GDM fails to load and I get the following error:

(==) Log file: "/var/log/Xorg.93.log",
(==) Using config file: "/etc/X11/xorg.conf"
FATAL: Module nvidia not found
(EE) NVIDIA(0): Failed to load NVIDIA kernel module!
(EE) NVIDIA(0): *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration

Fatal server error:
no screens found
XIO: fatal IO error 104 (Connection reset by peer) on X server ":93.0"^m after 0 requests (0 known processed) with 0 events remaining.^M



I tried reconfiguring GDM to see if it that would get it to work, but upon rebooting it still failed to load.

What should I do?

Thanks,

---

### Post by chollis888 on 2006-06-11
Thanks a ton Poofy, this is great. Only one draw back did/nt like rebooting to turn it off so here's a little how-to of my own. Trying to do my part for the community, and thought others might find this useful also.

This is a toggle script to turn the great features on and off.

Step 1:

Put this command in the terminal:

```
gedit toggle_compiz.bash 
``` 
Step 2:
Copy this into the empty file:


```
#!/bin/bash
#
# Checks to see if process "compiz.real" is running.
# If it is, it will kill it.
# If it isn't, it will start it.
#
# By Ubuntu Community

if ps -A | grep -e " compiz.real$" > /dev/null; then
    killall gnome-window-decorator
    metacity --replace &

else
        thefuture 
        
fi

``` Step 3:
Now save the file to your home folder. Close gedit. Put this command in the terminal:

```
sudo mv toggle_compiz.bash /usr/bin/

``` Then this:

```
sudo chmod +x /usr/bin/toggle_compiz.bash
``` 
Then right click on gnome panel and add a shortcut, choose custom launcher in the menu and add:

```
/usr/bin/toggle_compiz.bash

``` 
in the command field. You can make a desktop launcher by right clicking on the desktop, choosing “create launcher” then use the same command.

Now each time you click on the icon compiz & XGL are toggled on/off! This is essential and its the only way around many bugs.

---

### Post by senzapadroni on 2006-06-11
Useful HowTo; I've only encountered this problem:
```
$ thefuture
$ compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
```
that I've solved by reinstalling mesa libraries with:```
sudo apt-get --reinstall install libgl1-mesa
```
Now XGL works like a charm on my Asus A6JC with Nvidia GeForce 7300 :cool:

---

### Post by kakulacis on 2006-06-11
I have a problem with alt-tab switching and minimizing, when i minimize window it just disappears, it's not killed, but it is not visible anymore (can see process in system monitor). When i try alt-tab, compiz crashes and kills all panels and toolbars. Does anyone have same issue? How i can solve it? Thanks!

---

### Post by kakulacis on 2006-06-12
Switched to miniwin instead of dock, alt+tabbing now is working, minimizing window sometimes result in notification tab (or watever it is called) going to bottom (as it should be) panel, sometimes on that other "thing" (compiz related, probably it's calld window switcher :D ). But atleast now it is working more or less. :-&

---

### Post by mootchell on 2006-06-12
[QUOTE=Rotarychainsaw]I tried this and got the error:

 gnome-window-decorator, Failed to load shadow images
compiz.real: No composite extension

Should I add composite to my xorg.conf?

*edit - added composite and now I get the Texture error. getting closer.[/QUOTE]

Hi, seems I have that same problem. However, I am a complete noob and I have no idea what adding a composite means. PLEASE let me know what you did, as i've been at this for a while (and i've learned a crapload) and just can't get it to work.

thanks.

---

### Post by kakulacis on 2006-06-12
[QUOTE=mootchell]Hi, seems I have that same problem. However, I am a complete noob and I have no idea what adding a composite means. PLEASE let me know what you did, as i've been at this for a while (and i've learned a crapload) and just can't get it to work.

thanks.[/QUOTE]

Probably it means adding this:

[COLOR="Red"]Section "Extensions"
    Option "Composite" "Enable"
EndSection[/COLOR]

to your xorg.conf file

If your have Nvidia drivers from official site (newest one's) not from ubuntu repositories, then you probably have to do LD_PRELOAD before running xgl or make a simlink to your libGL.so*.
But in my opinion problem is in fact, that you do not even run xgl, i had the same :) Composite is build in xgl, so you probably do not need to add it in your xor.conf file.

---

### Post by senzapadroni on 2006-06-12
[QUOTE=senzapadroni]Useful HowTo; I've only encountered this problem:
```
$ thefuture
$ compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
```
that I've solved by reinstalling mesa libraries with:```
sudo apt-get --reinstall install libgl1-mesa
```
Now XGL works like a charm on my Asus A6JC with Nvidia GeForce 7300 :cool:[/QUOTE]
Yesterday I talked too soon.:-( 
Xgl worked since I didn't turn off my laptop: today I've turned it on and when i run thefuture script it goes back to gdm window.
Is there anyone who has the same problem??:confused: :confused: :confused:

---

### Post by Sukarn on 2006-06-12
OK, whats really annoying me is that none of this is working -
[quote=poofyhairguy]
Try it out. Here are the basic key commands:

CTRL + ALT + Left/right arrow key. Switches to the new side of the cube for me. 

CTRL + ALT + SHIFT + Left/Right arrow key- Takes the in focused app around cube.

CTRL + ALT + Left Click on Desktop - allows you to use the mouse to rotate cube.

F12 - uses the Expose like trick

Alt- Tab - switcher Vista-style
[/quote]
 And on top of it, minimizing an application makes it disappear from the list of open tabs/applications on the taskbar. This is fine for Opera, as I can get it back by just clicking on the icon, that makes it open a new tab, but for other applications its a real mess.
And, 118 pages of a thread are just too much to read to solve a problem.

---

### Post by mootchell on 2006-06-12
[QUOTE=kakulacis]Probably it means adding this:

[COLOR="Red"]Section "Extensions"
    Option "Composite" "Enable"
EndSection[/COLOR]

to your xorg.conf file

If your have Nvidia drivers from official site (newest one's) not from ubuntu repositories, then you probably have to do LD_PRELOAD before running xgl or make a simlink to your libGL.so*.
But in my opinion problem is in fact, that you do not even run xgl, i had the same :) Composite is build in xgl, so you probably do not need to add it in your xor.conf file.[/QUOTE]

I added that line to the xorg.conf.. got nothing. I'm an extreme noob and i'm not sure what those other two things you said mean?

Now I'm getting a new error:
```

mitch@mitch-desktop:~$ thefuture
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
```

Then, abruptly, my panels dissapear and the visbile part of all windows open shrinks to about half their size.

What does it mean!?!

---

### Post by kakulacis on 2006-06-12
[QUOTE=Sukarn]OK, whats really annoying me is that none of this is working -

 And on top of it, minimizing an application makes it disappear from the list of open tabs/applications on the taskbar. This is fine for Opera, as I can get it back by just clicking on the icon, that makes it open a new tab, but for other applications its a real mess.
And, 118 pages of a thread are just too much to read to solve a problem.[/QUOTE]

Same for me :) You can set "miniwin" plugin instead of "dock". Result is described in my post above, but anyway problem reappears when minimized/maximized window is closed and also in some other circumstances which probably are not random :) For a moment i thought that this proble is actual only for me :D

P.S. "compiz --replace gconf" brings windows back to life, but only until mentioned operation (minimizing or alt tabbing) :)

---

### Post by kakulacis on 2006-06-13
[QUOTE=mootchell]I added that line to the xorg.conf.. got nothing. I'm an extreme noob and i'm not sure what those other two things you said mean?

Now I'm getting a new error:
```

mitch@mitch-desktop:~$ thefuture
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
```

Then, abruptly, my panels dissapear and the visbile part of all windows open shrinks to about half their size.

What does it mean!?![/QUOTE]

Well i'm also a noob :D Maybe not extreme, but noob.
All i can do is give you review of my actions, maybe something is right for you.

First of all i have latest drivers from official nvidia site, so probably this is problem why i need to do LD_PRELOAD for module i marked with red, by default xgl would use libGL.so.1, which i my situation is not right.

```

kakulacis@Sesks:~$ ls -l /usr/lib/libGL.so*
lrwxrwxrwx 1 root root     10 2006-06-08 07:39 /usr/lib/libGL.so -> libGL.so.1
lrwxrwxrwx 1 root root     12 2006-06-08 07:39 /usr/lib/libGL.so.1 -> libGL.so.1.2
-rwxr-xr-x 1 root root 543564 2006-06-07 21:37 [COLOR="Red"]/usr/lib/libGL.so.1.0.8762[/COLOR]
-rw-r--r-- 1 root root 408688 2006-06-08 06:06 /usr/lib/libGL.so.1.2

```

So I:
1) added 
```

deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main

```
to my /etc/apt/sources.list files
2)added authentication key
```

wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -  

```
3) installed all packs:
apt-get install libglitz1 libglitz-glx1 xserver-xgl libgl1-mesa libsvg libsvg-cairo compiz compiz-gnome gset-compiz
4) 
Created startup script
gedit /usr/bin/startxgl.sh
```

#!/bin/bash
LD_PRELOAD=/usr/lib/libGL.so.1.0.8762 /usr/bin/Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:fbo & sleep 2 && 
DISPLAY=:1
gnome-window-decorator &
compiz gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher &
exec gnome-session

```
As you see in my situation with newest drivers i need to add LD_PRELOAD before running Xgl with libGL.so.1.0.8762, otherwise you may change that to libGL.so.1 or delete everything before Xgl command ("LD_PRELOAD=/usr/lib/libGL.so.1.0.8762" part)

chmod +x /usr/bin/startxgl.sh to make it executable

5) gedit /usr/share/xsessions/xgl.desktop to make startup choice of Xgl in login screen

Add
```

[Desktop Entry]  
Encoding=UTF-8 
Name=Xgl
Comment=Start an Xgl Session
Exec=/usr/bin/startxgl.sh 
Icon= 
Type=Application 

```
Make it executable 
chmod +x /usr/share/xsessions/xgl.desktop

If you made changes to xorg.conf then restart X (restarting only gdm will not be enough) or better restart pc. At login screen under sessions choose Xgl, which we created and log in, hope it works out.

Main source
[https://wiki.ubuntu.com/CompositeManager/Xgl](https://wiki.ubuntu.com/CompositeManager/Xgl)
with minor modifications

---

### Post by mootchell on 2006-06-13
[QUOTE=kakulacis]
If you made changes to xorg.conf then restart X (restarting only gdm will not be enough) or better restart pc. At login screen under sessions choose Xgl, which we created and log in, hope it works out.
[/QUOTE]

Wow, thanks a *lot*. Only one thing. When I reboot I am brought first to the command line and from there log in and start x with the usual "startx" command.. but.. You were saying to choose Xgl, implying that i'd be in some kind of GUI. Is there any way to sart Xgl from the command line, or a way to get this thing to boot into the graphical log in screen (which i used to have)?

From there everything should work out...

THANKS again.


edit:
I thought I should include, although it was implied, that after using startx i am getting no compiz/xgl effects.
could that have something to do with this?:

```
E: Couldn't find package libsvg
```

I get that when I did all of the apt-get'ting mentioned in your post.

thanks yet again

---

### Post by mootchell on 2006-06-13
And.. here's another fun fact. When I put "startxgl.sh" into the terminal, a huge blue window appears that cannot fit on my screen. The terminal gives me this nice, compact list of errors:
```

mitch@mitch-desktop:~$ startxgl.sh
Couldn't open RGB_DB '/usr/share/X11/rgb'
Could not init font path element /usr/lib/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/lib/X11/fonts/OTF, removing from list!
Could not init font path element /usr/lib/X11/fonts/CID/, removing from list!
gnome-session: you're already running a session manager
FreeFontPath: FPE "/usr/lib/X11/fonts/misc/" refcount is 2, should be 1; fixing.Couldn't open RGB_DB '/usr/share/X11/rgb'
mitch@mitch-desktop:~$ Could not init font path element /usr/lib/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/lib/X11/fonts/OTF, removing from list!
Could not init font path element /usr/lib/X11/fonts/CID/, removing from list!
compiz.real: Couldn't load plugin 'libmenu.so'
X connection to :0.0 broken (explicit kill or server shutdown).
The application 'gnome-window-decorator' lost its connection to the display :1.0;
most likely the X server was shut down or you killed/destroyed
the application.
X connection to :1.0 broken (explicit kill or server shutdown).

```

Hahaha..
Well, if any one can help me (again).. I'd appreciate it!
Far too timid to try fix any of *that* on my own.

---

### Post by kakulacis on 2006-06-13
[QUOTE=mootchell]Wow, thanks a *lot*. Only one thing. When I reboot I am brought first to the command line and from there log in and start x with the usual "startx" command.. but.. You were saying to choose Xgl, implying that i'd be in some kind of GUI. Is there any way to sart Xgl from the command line, or a way to get this thing to boot into the graphical log in screen (which i used to have)?

From there everything should work out...

THANKS again.


edit:
I thought I should include, although it was implied, that after using startx i am getting no compiz/xgl effects.
could that have something to do with this?:

```
E: Couldn't find package libsvg
```

I get that when I did all of the apt-get'ting mentioned in your post.

thanks yet again[/QUOTE]

You do not have login screen GUI? :O
Anyway if you are in a pure terminal, then try to run command /etc/init.d/gdm stop
then /etc/init.d/gdm start
It should automatically start login screen, what do you see when you change your session in terminal with alt+F9? Only black screen?

---

### Post by mootchell on 2006-06-13
[QUOTE=kakulacis]You do not have login screen GUI? :O
Anyway if you are in a pure terminal, then try to run command /etc/init.d/gdm stop
then /etc/init.d/gdm start
It should automatically start login screen, what do you see when you change your session in terminal with alt+F9? Only black screen?[/QUOTE]

So very strange. I'm getting this when I put /etc/init.d/gdm start into the pure terminal...

```
}root@mitch-desktop:~# sudo /etc/init.d/gdm start
 * Starting GNOME Display Manager... /etc/init.d/gdm: line 49:  6594 Segmentation fault      start-stop-daemon --start --quiet --oknodo --pidfile $PIDFILE --name gdm $SSD_ARG -- $CONFIG_FILE >/dev/null 2>&1
                                                                         [fail]

```

What I meant by login GUI was that I do not get an interface for loging in when i reboot, all i get is a terminal login screen.. from which i have to start x. i tried putting "startxgl.sh" into it, but i got a bunch of odd errors that I don't know how to copy when in the pure terminal, if you even can..

I am extremley lost!

---

### Post by m94mni on 2006-06-13
Anyone noted that the instructions on

[https://wiki.ubuntu.com/CompositeManager/Xgl](https://wiki.ubuntu.com/CompositeManager/Xgl)

use the command

```
command=/usr/bin/Xgl :0 -fullscreen -ac -br -accel xv:fbo -accel glx:pbuffer **-kb**
```

That "-kb" disables XKB, and just doesn't make any sense. Shouldn't it be removed?

---

### Post by kakulacis on 2006-06-13
[QUOTE=mootchell]
What I meant by login GUI was that I do not get an interface for loging in when i reboot, all i get is a terminal login screen.. from which i have to start x.[/QUOTE]
I know what you meant :)

Can your run X at all? Maybe gdm dont't start X automatically?
Then you should run startx at first, then switch from X to console with ctrl+alt+F1 to F4, then run /etc/init.d/gdm stop and /etc/init.d/gdm start. What is result then? Does login screen appear?
You can also try to add /usr/share/xsessions/xgl.desktop contenct to your /home/username/.Xsession and make ir executable chmod +x /home/username/.Xsession

.Xsession is default session, maybe starting from login screen default session result in using .Xsession contenc for session, but i do not know wether it will start up from running startx from terminal :(

You ca try [http://www.tectonic.co.za/view.php?id=916](http://www.tectonic.co.za/view.php?id=916) quick tutorial, maybe it will work for you. 
And last, you can configure your /etc/gdm/gdm.conf-custom
Maybe something like that

[servers]
1=Xgl
[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true

Try to find how to make working X login screen, seems like you have bunch of other misconfiguration or missing components :O

As you see nothing goes right when noob is trying to help a noob :)

---

### Post by mootchell on 2006-06-13
[QUOTE=kakulacis]You ca try [http://www.tectonic.co.za/view.php?id=916](http://www.tectonic.co.za/view.php?id=916) quick tutorial, maybe it will work for you. 
[/QUOTE]

WOW, somehow, this worked. First time with it, it gave me some error and took me back to the command line, saying that "*something* is 2, should be 1. Fixing." Then i re-started X and now i'm back and it seems to be working.

I'm a bit worried as when I start X and the small window which says what in Ubuntu has loaded comes up, it stops on "window manager." Once I click it, it goes away, but I doubt that's actually fixing anything. I doubt, too, that it's hurting anything either.

I still don't get a graphical log in screen, which is just odd, but I'm a bit afraid to start messing with the /.Xsession, as i just edited it a bit during that tutorial.

Anyway, it works now, so THANKS.. I have conqured xgl!

---

### Post by mootchell on 2006-06-13
One small thing. Now that I've got it working all I can do it switch between desktops using the desktop chooser on the panel. How do I edit whatever it is I have to edit to  change the settings for effects? Any tutorial or other thread (that isn't 400 pages) about that?

---

### Post by mootchell on 2006-06-13
Breakthrough. Upon restarting, x will not load. It is telling me something about the directory "/usr/bin/X11/font" and it's **refcount** being 2 when it should be one. I cannot paste the exact output here as I don't think you can copy from the pure terminal and paste once x (root account) starts up.

**EDIT**
I feel like I have too many problems to still be a part of this thread. Also, I was hoping I could catch more attention in a new one. So, if anyone reads this and thinks they can help me, replying here is fine but at [http://ubuntuforums.org/showthread.php?p=1135701](http://ubuntuforums.org/showthread.php?p=1135701) would be preferred. Thanks!

---

### Post by JoshHendo on 2006-06-14
I installed it, and it worked for a little while.

After a little while I stopped and decided to keep it for when I was bored. When I tried it again, the bar of the terminal became transparent, and the mouse would move, but I couldn't do anything.

Anything that I should do? Thanks :)

---

### Post by kvonb on 2006-06-14
I would really like to add drop shadows ONLY to my desktop in the simplest way possible.  Can this be done without all the spinning cube stuff?

Regards,

Kev :)

EDIT:  Don't worry, I found a thread, tried it, and unfortunately it doesn't work with gdesklets so I dumped shadows :(

---

### Post by nohope_no on 2006-06-14
[QUOTE=poofyhairguy]
"Originally Posted by encho
OK, I'm the unlucky one. All I got is this message:
 
 $ thefuture
 $ compiz.real: GLX_EXT_texture_from_pixmap is missing
 compiz.real: Failed to manage screen: 0
 compiz.real: No managable screens found on display :0.0
 
 And it kills my gnome-panel, nautilus, and metacity. Maybe I am missing something?"

Yeah, I get that sometimes. Just keep running the command till it goes away. Even if thats like twenty times. It will eventually go away.[/QUOTE]
I have the same problem. However, this is when I try to run compiz, without any window decorator.. When I try to run gnome-window-decorator i get this:

```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
The application 'gnome-window-decorator' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed

```
The mainproblem is however, to get compiz working.. 
anyone that knows the reason to why I get theese errors?

(Kubuntu dapper)

---

### Post by SamMessing on 2006-06-14
After rebooting, Xserver fails and I get the following message:

```
(EE) NVIDIA (0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA (0): *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.


Fatal server error:

no screens found
```

Here is a copy of the MODULES section of my /etc/x11/xorg.conf file:

```
Section "Module"
     Load "bitmap"
     Load "ddc"
#   Load "dri"
     Load "extmod"
     Load "freetype"
     Load "glx"
     Load "int10"
     Load "type1"
     Load "nvidia"
     Load "vbe"
```

I'm still pretty new, so let me know if more information is required. What should I do to fix this? Originally it was failing w/o

```
Load "nvidia"

```
in the xorg.conf file, so I added it, but it doesn't seem to make much difference. I have also made sure that I have the latest nvidia drivers, which I do, but I am not sure if that would have made any sort of difference.

Thanks!

Sam

---

### Post by fakie_flip on 2006-06-15
Does this guide work for Xfce4 or only Gnome?

---

### Post by rivethead on 2006-06-15
Anyone know how to update this after the new Kernel upgrade that was just released? i cant seem to get mine working again after.

-Rvt

---

### Post by link6502 on 2006-06-17
Wow, that went very smoothly. I think having an actual Nvidia 5200 videocard helped.

Anyway, XGL finally makes Gnome on this PIII run a WHOLE lot faster and so much more elegantly. I turned off "wobbly" because I thought it was overkill (but fun to play with for a while.) But I love how moving windows, minimizing/restoring is so much smoother. Resizing apps with complicated content (eg firefox) is still sluggish (as I expected) but not worse than before. I think scrolling is smoother, but I'm not sure.

Surprisingly mplayer works pretty well, except when the playback control window overlaps the video window. Moving the mouse over it seems to make it a little choppy too. I'm using -vo=xv.

The most unfortunate thing is that mplayer does run noticably slower :( I used to be able to run video smoothly at 1280x1024, now I have to drop down to 1024x768 to play a movie, but even then I still see some tearing in the image. Maybe playing with the refresh rate could help this? It's at 85Hz right now.

It would be nice to be able to turn off XGL when I want to play a movie. Any command to quit 'thefuture'?

Anyway, great howto. Thanks a lot!

---

### Post by chakkid on 2006-06-17
it didn't work out. I can't add this to the GNOME, and i have a NVIDIA card and everything. How do i add it again in another way?

---

### Post by chakkid on 2006-06-17
forget it. I only have to go **System** » **Preferences** » **Sessions** » **Startup applications** » click on **Add** and write **thefuture**. And there's another way to add this to the GNOME startup.:p 

Good topic.;)  And too good idea.:idea:

---

### Post by senzapadroni on 2006-06-18
Hi sam, set up your xorg.conf file:
- Go in the module section and erase
```
Load "nvidia"
```
- Go in the *Device Section* and check out that the nvidia driver is configured:
```
    Driver         "nvidia"
```

Don't forget to control that nvidia module is loaded; do that with
```
lsmod | grep nvidia
```
If it's not loaded you've to install correctly Nvidia drivers.

---

### Post by Mikeynewbie on 2006-06-18
Hey there just wanted to thank you thank you thank you after multiple attempts to get this going I finally got it working with your howto.  Thank you so much, and keep up the good work.

---

### Post by fakie_flip on 2006-06-19
what are the video card requirements and other spec requirements for using xgl? Also, will xgl work on xfce4 using this guide?

---

### Post by Thought_Criminal on 2006-06-19
Thanks for putting this together man, it worked great for me.
Thanks again for taking the time and sharing your knowledge.=D>

---

### Post by Sean-Michael on 2006-06-19
Man I love the effects of this, but I think there should have been instructions for updating and upgrading.... ?

I found this thread to be a little more in depth and now I think Im in a lil better shape, I mean to say I think Im up to date with XGL,  could you add a few things to your origional post/guide to get updates for this!

Here's the guide I later found that I then followed... [Lookie Here.]("http://www.compiz.net/viewtopic.php?id=652%3Cbr%20/%3E")

---

### Post by michaelharg on 2006-06-19
I got XGL set up and working fine but i cannot play movies whilst it is running, anybody know how to fix this?

Thanks!

---

### Post by genesiss on 2006-06-19
can anyone tell me what this means?? and how to fix it??
thanks

W: GPG error: [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
W: GPG error: [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
W: You may want to run apt-get update to correct these problems

---

### Post by ralex on 2006-06-19
Hey everybody, I'm new to this and when I get to this part
```
sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome
```


I get this error
```
Reading package lists... 
Done Building dependency tree...
Done E: Couldn't find package compiz
```

Any help would be greatly appreciated. Thanks.

---

### Post by senzapadroni on 2006-06-20
[QUOTE=genesiss]can anyone tell me what this means?? and how to fix it??
thanks

W: GPG error: [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
W: GPG error: [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
W: You may want to run apt-get update to correct these problems[/QUOTE]
```
wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
```

---

### Post by senzapadroni on 2006-06-20
[QUOTE=ralex]Hey everybody, I'm new to this and when I get to this part
```
sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome
```


I get this error
```
Reading package lists... 
Done Building dependency tree...
Done E: Couldn't find package compiz
```

Any help would be greatly appreciated. Thanks.[/QUOTE]

Edit your /etc/apt/sources.list adding this repositories:
```
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main
deb-src http://xgl.compiz.info/ dapper main
```

---

### Post by matrooswolf on 2006-06-20
[QUOTE=senzapadroni]```
wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
```[/QUOTE]
Hi Senzapadroni,
I get the same missing key error, tried your code, but I still get the same error as above.
Did I miss something?

---

### Post by sethmahoney on 2006-06-20
Hey all, got everything working, and hey, it rocks!  But, for some reason with RenderAccel enabled my system will spontaneously freeze up after a few seconds, especially if firefox is active.  Anyone have any ideas for a workaround?  I'm running a PCI-e GeForce 6200 TurboCache with 256mb video ram and the 8762 NVIDIA driver, if that helps.

---

### Post by HondaWang on 2006-06-21
I have a slightly serious problem here.

Everything seems to go smoothly throughout the whole process, no errors, no freezing, nothing until I get to the reboot process. I reboot my system and then I get a serious error where X Server fails to load and there is no graphical user interface waiting for me, let alone a Compiz/XGL ready system. I've been doing this on a clean Dapper 6.06 system, Intel, and with an Nvidia GeForce Go 6200.

I will post the exact text later, once I get some sleep... ](*,)

---

### Post by senzapadroni on 2006-06-21
[QUOTE=matrooswolf]Hi Senzapadroni,
I get the same missing key error, tried your code, but I still get the same error as above.
Did I miss something?[/QUOTE]
No, that should be correct... #-o

---

### Post by senzapadroni on 2006-06-21
[QUOTE=HondaWang]I have a slightly serious problem here.

Everything seems to go smoothly throughout the whole process, no errors, no freezing, nothing until I get to the reboot process. I reboot my system and then I get a serious error where X Server fails to load and there is no graphical user interface waiting for me, let alone a Compiz/XGL ready system. I've been doing this on a clean Dapper 6.06 system, Intel, and with an Nvidia GeForce Go 6200.

I will post the exact text later, once I get some sleep... ](*,)[/QUOTE]
Did you get a situation like [this one]("http://ubuntuforums.org/showpost.php?p=1128566&postcount=1173")?
If it is, try this  [method by kakulacis]("http://www.ubuntuforums.org/showpost.php?p=1131768&postcount=1177")

---

### Post by HondaWang on 2006-06-21
No, umm, the error says:

Couldn't open RGB_DB ' /usr/share/X11/rgb'

And then a lot of other stuff that seems unnecesary to type at the moment. This seems to happen every time that I get to a step where I have to restart, no matter the way to install Compiz+XGL. Could somebody please help me with this? If you need more info, please specify what, and I'll happily comply.

---

### Post by senzapadroni on 2006-06-21
[QUOTE=HondaWang]No, umm, the error says:

Couldn't open RGB_DB ' /usr/share/X11/rgb'

And then a lot of other stuff that seems unnecesary to type at the moment. This seems to happen every time that I get to a step where I have to restart, no matter the way to install Compiz+XGL. Could somebody please help me with this? If you need more info, please specify what, and I'll happily comply.[/QUOTE]

Hmm...#-o 
Try to search on google for that error.
In the meanwhile read [this post]("http://www.ubuntuforums.org/showthread.php?p=1125151")

---

### Post by Tech_gogi on 2006-06-21
Great how-to!

a couple of minor problems. instead of 

> BusID		"PCI:1:0:0"

i had to use 

> BusID		"PCI:2:0:0"

i'm running a leadtek 5700le on an asus a7n8x board.

another problem, is that the keyboard commands don't seem to be working... any ideas as to why? i'm using a generic keyboard, ps/2... nothing fancy.... :edit: i've also ran the xmodmap command, no joy..
followed the  instructions exactly, only change was to the busID...

---

### Post by [L|eWiOn] on 2006-06-22
Hmm ok i followed this [https://help.ubuntu.com/community/CompositeManager/InstallingCompiz](https://help.ubuntu.com/community/CompositeManager/InstallingCompiz)
and everything that follows that.. problem is cube etc are not working, nor do i know how to get this working.. the commands given in the latest section of the guide are not working... alt-tab does work however... i cannot seem to get it.. i used Method B in first guide Method A in 2nd ... dunno where to start now...](*,)

---

### Post by PoisoN2003 on 2006-06-25
i get this when i try to launch thefuture any idea whats happening?
```
poison@ubuntu:~$ compiz.real: No composite extension
/home/poison/.themes/Tactile/gtk-2.0/gtkrc:1046: Unable to locate image file in pixmap_path: "spin_button_up_arrow_prelight.png"
/home/poison/.themes/Tactile/gtk-2.0/gtkrc:1050: Overlay image options specified without filename
/home/poison/.themes/Tactile/gtk-2.0/gtkrc:1056: Unable to locate image file in pixmap_path: "spin_button_down_arrow_prelight.png"
/home/poison/.themes/Tactile/gtk-2.0/gtkrc:1060: Overlay image options specified without filename

(gnome-window-decorator:5062): Pango-CRITICAL **: pango_color_parse: assertion `spec != NULL' failed

```

---

### Post by turbojugend_gr on 2006-06-25
My issue is that I get the composite error, when I enable composite it crashes. Actually I 've replaced the metacity with compiz before starting gnome-window-decorator, i get the no boarder issue, if I enable the decorator it crashes again.
Plz provide me with some help here.

---

### Post by Cene on 2006-06-25
I'm having an annoying problem. I did not see anyone else having it, as I tried with search and looked for about ten first and few last pages of this thread:
XGL/Compiz installs fine, reboot goes fine. 
When I entered the command to start Compiz, it gave me an error about composite missing or something.. 
I enabled the composite from xorg.conf and got an another problem when trying to start Compiz. 
When I type the command to start it, it gives me some error for a second, goes too fast to be able to read it and X restarts.
What's the matter?

Edit: Oh, and I'm running Dapper with nVidia FX 5200

---

### Post by tuxcantfly on 2006-06-25
the new cvs version (I'm using quinstorm xgl and compiz-vanilla) doesn't screw up openoffice.org, but the current one does (icon rendering slows down to the point that you can see the open and save buttons being drawn). interesting. also, I found some nifty places which tell you how to run sdl and opengl apps normally with xgl running:

[http://www.ubuntuforums.org/showthread.php?t=51486](http://www.ubuntuforums.org/showthread.php?t=51486)

(for the xinit method)

[http://linux.net.pl/~harnir/2006-04-22/how-to-run-sdl-and-opengl-based-games-under-xgl/](http://linux.net.pl/~harnir/2006-04-22/how-to-run-sdl-and-opengl-based-games-under-xgl/)

(for the XLIB_SKIP_ARGB_VISUALS=1 method)

---

### Post by turbojugend_gr on 2006-06-25
[QUOTE=Cene]I'm having an annoying problem. I did not see anyone else having it, as I tried with search and looked for about ten first and few last pages of this thread:
XGL/Compiz installs fine, reboot goes fine. 
When I entered the command to start Compiz, it gave me an error about composite missing or something.. 
I enabled the composite from xorg.conf and got an another problem when trying to start Compiz. 
When I type the command to start it, it gives me some error for a second, goes too fast to be able to read it and X restarts.
What's the matter?

Edit: Oh, and I'm running Dapper with nVidia FX 5200[/QUOTE]

Lol just above you is my post, and it is the same!!!!!!
Anyway someone give us a hand here...

---

### Post by Cene on 2006-06-25
[QUOTE=turbojugend_gr]Lol just above you is my post, and it is the same!!!!!!
Anyway someone give us a hand here...[/QUOTE]
Oh, I just tought that your problem was the same style crshes as others, that something from Gnome crashes, not the whole X.

---

### Post by Doovoo on 2006-06-25
I'm getting an error when I boot the computer, and I'm stuck on the command line, so I'm just trying to uninstall now. This is what I'm getting.

"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"

"yes"

"GDM: Xserver not found: /usr/local/bin/Xgl :0 :0 -fullscreen -ac -accel xv -accel glx: pbuffer -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
Error: Command could not be executed!
Please install the X server or correct GDM configuration and restart GDM."

I've reconfigured GDM and xserver-xorg and neither has worked.

Anyone have an idea of what I should do? I don't care about getting Xgl to work, I just kinda want to be able to use the computer again.

---

### Post by Cene on 2006-06-25
[QUOTE=Doovoo]I'm getting an error when I boot the computer, and I'm stuck on the command line, so I'm just trying to uninstall now. This is what I'm getting.

"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"

"yes"

"GDM: Xserver not found: /usr/local/bin/Xgl :0 :0 -fullscreen -ac -accel xv -accel glx: pbuffer -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
Error: Command could not be executed!
Please install the X server or correct GDM configuration and restart GDM."

I've reconfigured GDM and xserver-xorg and neither has worked.

Anyone have an idea of what I should do? I don't care about getting Xgl to work, I just kinda want to be able to use the computer again.[/QUOTE]

I had similiar problem earlier. Try this:
```
sudo nano /etc/gdm/gdm.conf-custom
```
Clear everything inside it, then save (CTRL+O), and quit (CTRL+X)

```
sudo apt-get remove --purge gdm
```
Then
```
sudo apt-get install kdm && sudo dpkg-reconfigure kdm
```

Then reboot. Now you should have yourself in KDM without Compiz. If you want to have gdm back after it, you should try:
```
sudo apt-get install gdm && sudo apt-get remove --purge kdm && sudo dpkg-reconfigure gdm
```
And then reboot.

---

### Post by Doovoo on 2006-06-25
That worked! Thanks!

---

### Post by turbojugend_gr on 2006-06-25
Well, I started this all over, now I have other issues...

when I go "thefuture", I loose my window frames, and I am getting a whole load of output, the last lines of which is:
```
GL: GL_TEXTURE_2D
Trying to initialize a mindow
Event added!
Processing the next event...
InitializeMindow event received!
Event added!
Processing the next event...
CheckMindow event received!
Event added!
Processing the next event...
GL: GL_TEXTURE_2D
Trying to initialize a mindow
Event added!
Processing the next event...
InitializeMindow event received!
Event added!
Processing the next event...
CheckMindow event received!
Event added!
Processing the next event...
GL: GL_TEXTURE_2D
Trying to create a mindow from a window
Event added!

```
I then have to restar X, as it doesn't proceed.
 any help on this? I want it to run...:(

---

### Post by [L|eWiOn] on 2006-06-25
[QUOTE='[L|eWiOn]']Hmm ok i followed this [https://help.ubuntu.com/community/CompositeManager/InstallingCompiz](https://help.ubuntu.com/community/CompositeManager/InstallingCompiz)
and everything that follows that.. problem is cube etc are not working, nor do i know how to get this working.. the commands given in the latest section of the guide are not working... alt-tab does work however... i cannot seem to get it.. i used Method B in first guide Method A in 2nd ... dunno where to start now...](*,)[/QUOTE]
I need to get help....

---

### Post by turbojugend_gr on 2006-06-26
Well, step by step.... I had an update yesterday and boom XGL - Compiz are Gracefully working. It is awesome!

Only little thing , I can't get the miniwin and the Dock working... When I change the order in the plugin loading I get no changes? I add the miniwin for instance yet it is not there after a minute??? Anyway it ROCKS!

---

### Post by turbojugend_gr on 2006-06-26
[QUOTE='[L|eWiOn]']I need to get help....[/QUOTE]

Are you sure you got Compiz working??? MOst propably you are wher I was, you have xgl but compiz is not working....

Try adding both the links (whereas the composer in that wiki says one of them), you should get an update notification, update everything then follow the howto for your configuration (e.g nvidia Gnome, Ati KDE AMD64,etc) as suggested by the first post and you should get it working, although I miss some plugins I am workng it gracefully despite that.

---

### Post by Dragineez on 2006-06-26
Thanx! Worked perfectly, now I can see why everyone is so excited about this technology - seriously cool.

---

### Post by gurgle on 2006-06-27
i followed the first post and now my VNC doesnt work. can someone help me?

---

### Post by citizenkeith on 2006-06-27
I ran into some issues.... first, my xorg.conf didn't have these lines:

```
       Load    "GLcore"
       Load    "dri" 
          Load "glx"
```

So there was nothing to comment out. Instead, I had:

```
Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection
```

When I rebooted, I experienced the same issue that DooVoo experienced ("Failed to start the X server..." etc). Luckily, I had backed up my old copy of xorg.conf, so I was able to delete the new one and replace it from the command line.

I had already changed gdm.conf-custom, so I decided to plow ahead and see what happened. I booted, and continued with your directions. I have Wobbly windows! :) But none of the short cuts work (Control-Alt-arrow keys, etc). I have no idea if that's related to the differences in xorg.conf.

Any ideas? I have a vGA MX4200.

---

### Post by citizenkeith on 2006-06-28
Bueller?


:D

---

### Post by Eleka on 2006-06-29
Excuse me people if this question is before answered, but using the thread search I have not answer for it.

I installed Xgl and Compiz following all the steps and now I have a script called start_compiz wich runs compiz.

When I run it, it looks like work: my workspace switcher changes, the windows have effects when I move them .... but I have not other effects, like the pretty switcher, move windows with alt+left button of my mouse, rotate the cube (I don't know if I have any cube) ... it looks like it's some plugins loaded and others not ... is this possible?

How can I make it work? I have other Xgl/Compiz in a amd64 and it works fine ... what am I doing wrong?

Edit: I have tested more and more and I foend some useful info: if I run it without a script, executing "line to line" the compiz_start script, it works, but when I do the "xmodmap", it don't works. The Zoom (that is configured with the super button) don't work both (with and without xmodmap). How can I solutionate this?

---

### Post by bocmaxima on 2006-06-29
Man, this would be so bitchin to use if it didnt kill any sort of funtionality of my comp outside of web browsing. I cant play UT2k4 and I cant watch DVDs.

Whats the point of this, to wow people while word Processing? :p

---

### Post by battletux on 2006-06-30
<offtopic>This has to be quite possibly the longest thread in this place. </offtopic>

Ok thank you sooo much for this install went really smoothly and most features are working fine. :p  =D> 

For me the issue I am having is with the cube desktop switcher. It just will not work.

When I first ran 'thefuture' I had an error message about the cube plugin not working due to some dependancies, unfortunately i was too distracted by the wobble on dragging stuff to make a note of the actual error.

Since a reboot and re-run of 'thefuture' it no longer gives the dependancy error but the cube plugin just will not work. Is there a log file anywhere i can check?

Does anyone know of any way to re-install it, as i realy want to have this feature as without it i am stuck to only one workspace :(

---

### Post by gotgenes on 2006-07-03
Compiz is not playing well with gconf. When I issue the following command
```
gnome-window-decorator & compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &
```
None of the plugins seem to load, keenly noticeable by the lack of a titlebar and window decorations around the application windows, but also no wobbly or cube or any such goodness. Opening the gconf-editor, I notice there's no plugins entry in apps>compiz>general>allscreens or >screen0

Running, instead,
```
gnome-window-decorator & compiz --replace decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &
```
that is, the same command, sans gconf, activates all the compiz plugins in their wondrous glory.

I followed the HOWTO step-by-step. Crossed every I, dotted every T.

Is there some way to get gconf and compiz to talk to each other? I would appreciate the help. I would also be interested to know if someone else is experiencing this problem.

Thanks in advance,
Chris

---

### Post by gotgenes on 2006-07-04
Well, I deleted the .gconf directory in my home directory, logged out, logged back in, did xmodmap and retried the command and it works; the compiz plugins now appear in gconf-editor. Perhaps there was a more elegant way to do it. I did lose some of my customizations of the desktop.

---

### Post by th3t1nm4n on 2006-07-05
Hi, thanks for this awesome guide, it was easy to follow and truely what I'd been looking for. I'm having a problem with xgl/compiz though and need some help, I aparently only have one workspace once I run it, only one workspace is visible on the applet in my gnome-panel, and the cube spinning function isn't working for me as many of the other key-features aren't.
Any ideas on making the workspaces/cube work?
Also, how do you enable the scroll-wheel transparency? I've been looking for info on that too.

---

### Post by speedsix on 2006-07-05
When I change the /etc/gdm/gdm.conf-custom file to get xgl to start on boot, the second screen of my dualhead setup starts up as the black/white hatched X screen with the X cursor instead of a second metacity display as usual. I presume this is a conflict in screen no.s? Is there a way round this?

Thanks

---

### Post by gotgenes on 2006-07-05
[QUOTE=th3t1nm4n]I aparently only have one workspace once I run it, only one workspace is visible on the applet in my gnome-panel, and the cube spinning function isn't working for me as many of the other key-features aren't.
Any ideas on making the workspaces/cube work?[/QUOTE]
It sounds like the plugins aren't loading. Instead of running the thefuture script or compiz-start.py after logging in, try the following in a terminal and see if you get all the plugins to load:

Have you checked to see if those plugins loaded into gconf? Open the gconf-editor (Alt+F2, gconf-editor) and see if they are listed under Apps>compiz>plugins

If they aren't listed you'll probably need to nuke your gconf (rm -rf ~/.gconf), log out, log in, do your xmodmap command, and then enter:
```
gnome-window-decorator & compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &
```

If that still doesn't work, make sure you have the plugins in the first place by logging out, logging in, doing your xmodmap, and then entering the following in the terminal:
```
gnome-window-decorator & compiz --replace decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &
```
which is the same thing, without going through gconf though.

---

### Post by th3t1nm4n on 2006-07-05
Got it working, had to update some stuff and reboot.

---

### Post by mouhahaha on 2006-07-05
this is what i get when i run thefuture:

mouhahaha@afh:~$ thefuture 
mouhahaha@afh:~$ compiz.real: No composite extension gnome-window-decorator: Screen 0 on display ":0.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.

mouhahaha@afh:~$

i added :
Section "Extensions"
          Option  "Composite" "Enable"
EndSection
at the end of xorg.conf, when i try logging in gdm, it plays the login sound and returns back to the gdm screen without actually logging in...
whats the solution ? im on a toshiba m60 laptop with nvidia 6600...
any help would be greatly appreciated.  :roll:

---

### Post by bill barsch on 2006-07-06
[QUOTE=kakulacis]Found this solution in other forum, tried to reinstall everything but no luck :-k 

glxinfo says:
GLX_ARB_get_proc_address, GLX_EXT_import_context, GLX_EXT_visual_info,
GLX_EXT_visual_rating, GLX_SGI_make_current_read, GLX_SGI_swap_control,
GLX_SGI_video_sync, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
[COLOR="Red"]**GLX_EXT_texture_from_pixmap** [/COLOR]:confused:[/QUOTE]

hello!!
the libGL.so.1.2 have GLX_EXT_texture_from_pixmap and compix have to find it!
the problem is: nvidia's packages replaces libGL.so.1 (a link) with the libGL.so.1.0.8762
this "old version" of libGL.so is used to run Xgl but not the compiz...
you have to bakup libGL.so.1.2 (mesa) and libGL.so.1.0.xxxx (nvidia)
and start Xgl with:

#LD_PRELOAD=/usr/lib/backupNVIDIA/libGL.so.1.0.xxxx
#Xgl :1 -ac bla bla bla...

to run compiz you have to set this var:

#LD_PRELOAD=/usr/lib/backupMESA/libGL.so.1.2
#DISPLAY=:1 compiz gconf &

ok??? 
good rotates with the cube!!! hahaha

---

### Post by PandorsBox on 2006-07-06
To my surprise, it worked like a charm for my ATI 9800 XT... Driver install was picture perfect too.

---

### Post by _simon_ on 2006-07-06
I haven't read the enire thread as it's very long but I came accross a totally different HOWTO on this here:

[http://tazforum.thetazzone.com/viewtopic.php?t=2189](http://tazforum.thetazzone.com/viewtopic.php?t=2189)

Scroll down to "Turning Up The Graphics" it would appear that this way does not affect your default gnome session but instead gives you an XGL session of it's own?

Not sure which of the 2 is best or if they are just as good as each other?

---

### Post by keras on 2006-07-06
I also have not read the entire thread, I will continue to read it right after I am finished with this post, if I find my answer somewhere in this MASSIVE thread, then I'll edit this message.

I've encountered a weird problem which is the fact that I cannot press certain keys after I start up compiz.

Right now, I'm functioning with no enter key... at least, not the one most people use (the one above the Left Shift).  I'm forced to use the numpad Enter key.
This was after a reboot, before the reboot when I started compiz, I could not press the 'Z' key...

Anyways, I hope there's a fix for this. :)
Thanks in advance.

---

### Post by Glueeater on 2006-07-07
When I type thefuture, I get this and all my windows bug out...

```
compiz.real: No managable screens found on display :0.0

(gnome-window-decorator:7868): Pango-CRITICAL **: pango_color_parse: assertion `spec != NULL' failed

(gnome-window-decorator:7868): Pango-CRITICAL **: pango_color_parse: assertion `spec != NULL' failed

(gnome-window-decorator:7868): Pango-CRITICAL **: pango_color_parse: assertion `spec != NULL' failed

(gnome-window-decorator:7868): Pango-CRITICAL **: pango_color_parse: assertion `spec != NULL' failed

(gnome-window-decorator:7868): Pango-CRITICAL **: pango_color_parse: assertion `spec != NULL' failed

(gnome-window-decorator:7868): Pango-CRITICAL **: pango_color_parse: assertion `spec != NULL' failed

(gnome-window-decorator:7868): Pango-CRITICAL **: pango_color_parse: assertion `spec != NULL' failed

(gnome-window-decorator:7868): Pango-CRITICAL **: pango_color_parse: assertion `spec != NULL' failed

(gnome-window-decorator:7868): Pango-CRITICAL **: pango_color_parse: assertion `spec != NULL' failed

(gnome-window-decorator:7868): Pango-CRITICAL **: pango_color_parse: assertion `spec != NULL' failed

(gnome-window-decorator:7868): Pango-CRITICAL **: pango_color_parse: assertion `spec != NULL' failed

(gnome-window-decorator:7868): Pango-CRITICAL **: pango_color_parse: assertion `spec != NULL' failed

(gnome-window-decorator:7868): Pango-CRITICAL **: pango_color_parse: assertion `spec != NULL' failed

(gnome-window-decorator:7868): Pango-CRITICAL **: pango_color_parse: assertion `spec != NULL' failed

```

Now, I'm getting this:
```
carlo@CARLO:~$ gnome-window-decorator: Screen 0 on display ":0.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.
compiz.real: No composite extension

```

I already added the line to the xorg.conf for composite extension error.

---

### Post by pedwards on 2006-07-07
any chance of a installer showing up in automatix for compiz?

---

### Post by jstroot on 2006-07-07
Howdy. I've installed a few programs since runing XGL (which works fine), and I cannot see the fonts in these programs (Scorched3d and stellarium). The fonts are nothing but funky symbols, completely unreadable. 

I've posted to the stellarium forum, and the other person who replied is also running XGL. 

Just wondering if this is a coincidence, or if someone else has run into this problem.

jstroot

---

### Post by panurge77 on 2006-07-07
> **keras said:**
> I also have not read the entire thread, I will continue to read it right after I am finished with this post, if I find my answer somewhere in this MASSIVE thread, then I'll edit this message.

I've encountered a weird problem which is the fact that I cannot press certain keys after I start up compiz.

Right now, I'm functioning with no enter key... at least, not the one most people use (the one above the Left Shift).  I'm forced to use the numpad Enter key.
This was after a reboot, before the reboot when I started compiz, I could not press the 'Z' key...

Anyways, I hope there's a fix for this. :)
Thanks in advance.

You needto tell xmodmap to use your keyboard map, search the forum for 'xgl xmodmap' and you'll find the answers

---

### Post by i.Hack on 2006-07-09
tek@3080:~$ thefuture
compiz.real: No composite extension
tek@3080:~$ gnome-window-decorator, Failed to load shadow images

Anyone have any suggestions on how to fix this?

---

### Post by freedom.sr on 2006-07-10
At first place I want to say thank you for this great howto. 
In my case, everything works great by now, but there is one little bug that bothers me: when I execute "thefuture" script,  I get all the xgl stuff, but windows position isn't correct. Maximized windows are bigger than my screen, and unmaximized windows are to high, so I can't see their title bars. When I change size of it, and then maximize, it fits to the screen. Did anybody have the same problem? Is there any way to fix it? [-o< 

P.S. I have nvidia card and nvidia drivers (non-free). Is that problem, maybe?

Thank you in advance

---

### Post by yawie on 2006-07-11
In this thread, I have seem many people complaning about glxinfo returning "direct render : no".

I didn't see any clear answer. Would it be possible to have opengl games and screensavers to run with xgl and gnome ?
If it's really not possible it would be nice to tell about this in the first post.

Don't you think?

---

### Post by ubun_nv on 2006-07-13
does not work.
i got this error

compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

---

### Post by mzm2000 on 2006-07-13
It works!

Thanks for this guide. XGL Rocks! Ive never *seen* anything quite like it and all those screenshots out there dont do it enough justice!

---

### Post by utnubu001 on 2006-07-14
help me please!!

when i run thefuture i lose metacity my desktop switcher amd my window borders-am i missing something?

plaese help

---

### Post by RAOF on 2006-07-14
> **yawie said:**
> In this thread, I have seem many people complaning about glxinfo returning "direct render : no".

I didn't see any clear answer. Would it be possible to have opengl games and screensavers to run with xgl and gnome ?
If it's really not possible it would be nice to tell about this in the first post.

Don't you think?
Ok, here's a clear answer.  

[size=4]You **can** run OpenGL games and screensavers under XGL.[/size]

Due to the lack of direct rendering they will be a little bit slower (there's more overhead because everything has to talk to the XGL server first), but you can certainly run OpenGL programs under XGL.

---

### Post by utnubu001 on 2006-07-14
help needed

when i run the command thefuture

it messes up my metacity and i lose my desktop switcher and my window borders...

HELP ME PLEASE!!!!!!!!!

---

### Post by TomDooley on 2006-07-14
Hi there,

that is a great XGL howto for Nvidia cards. Thanks a lot poofyhairguy.

Everything worked fine with your instructions, I have just one thing to add, which might be particularily helpful for users with a non-US keyboard. 
I have a German keyboard and several keys (e.g. F12, CTRL, Super) did not work as expected.

Maybe you can add something like the following below your explanation of the key commands:
If you are using a non-US keyboard, go to System->Settings->Keyboard and select the appropriate keyboard layout and model.

Thanks again,
Tom

---

### Post by adab on 2006-07-14
I cant have XGL session after custom kernel compile.

gdm returns:
```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "rtfranco"
/etc/gdm/Xsession: Beginning session setup...
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  1 (X_GLXRender)
  Serial number of failed request:  97
  Current serial number in output stream:  98

(gnome-session:9487): Gtk-WARNING **: cannot open display:

```
My kernel version is this
```

:~$ uname -r
2.6.16-ck12

```
Thanks.

---

### Post by filips01 on 2006-07-14
Just wanted to say a BIG thank you for this How-To, i must have tried about 15 different tutorials and alwasy ended up breaking the gui. This How-To worked perfectly the first time around. THANK YOU!:D

---

### Post by utnubu001 on 2006-07-15
alwright

i got it working but only if i use
sudo thefuture
not
thefuture

---

### Post by uab999 on 2006-07-15
Does anybody know if XGL/compiz will with the nvidia legacy driver?  I noticed at the beginning of the howTo, when you are instructed to get the nvidia drivers, that it only specifies the nvidia glx driver.  Is there a way to make it work for the legacy drivers?  

Thanks

---

### Post by utnubu001 on 2006-07-15
dose any one know why 
compiz dose this
if i type thefuture i lose my window borders
but if i type
sudo thefuture it works fine 
i have checked the permissions

PLEASE HELP

btw this eyecandy is cooooool

---

### Post by phildacey on 2006-07-15
I followed this thread and everything worked except for video playback. While compiz was running video was horribly out of synch with audio; I tried all of the video players I have with the same result. 

The fix? I just ran apt-get dist upgrade and it magicked video goodness into my system. I'd reccomend this to anyone who has installed xgl & compiz as I suspect it could fix one or two niggling problems... although to be fair I'm only basing that suggestion on my limited experience of that one problem...still, it can't hurt to keep updated though, eh?

Many thanks to poofyhairguy for posting this howto, this wobbly cubic graphical voodoo is just grand. And all on a crappy GeForce4 MX440. Get in.

---

### Post by mnk0 on 2006-07-15
mnk0@root:~$ compiz.real: No composite extension
gnome-window-decorator, Failed to load shadow images


--help!!

---

### Post by TomDooley on 2006-07-18
Hi there, 

I have two questions and are happy for any feedback:

1. I currently have a nVidia Gforce 4 MX440 card and it works fine with xgl/compiz as long as I do not play any videos, because they are terribly slow (even if I do not rotate the cube while watching them :)
I will test the "apt-get dist upgrade" command proposed by phildacey, but I believe that a lot of the eye-candy effects are rendered in software by the nvidia driver for my card, which also causes the bad performance.
Can anybody recommend any low-cost card that works fine with ubuntu/XGL and has an AGP port? I do not play any 3D games or need the card for anything else than nice desktop effects and would like to pay as little as possible.

2. As long as I still have my current card, I would like to be able to switch between the XGL/compiz 3D desktop and the regular Gnome 2D desktop when booting my PC. Does anybody know how I can add a possibility to select which X-server setup to use during the boot process? 

Any ideas are highly appreciated!

Thanks,
Tom

---

### Post by saintxaero on 2006-07-18
now...how would i remove this?

---

### Post by Owdy on 2006-07-18
> **g14 said:**
> 
To poofyhairguy... Making a shell script (/usr/bin/thefuture) and having it run under your session is very hackish. Try this instead:

1.) ALT F2 and put in 
 That opens that run program GUI. Where do i put that?

---

### Post by dominicguy on 2006-07-19
](*,) 

I Get This:
```
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,
/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,
/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
```

And
```
(II) NVIDIA X Driver  1.0-8762  Mon May 15 13:09:21 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 00:05:0
(WW) NVIDIA: No matching Device section for instance (BusID PCI:0:5:0) found
(EE) No devices detected.

Fatal server error:
no screens found
```

:-k

---

### Post by koaster on 2006-07-19
after following your instructions, i get this silly error:

thefuture
gnome-window-decorator: Screen 0 on display ":0.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.
fix@xiryx:~$ compiz.real: water: GL_ARB_fragment_program is missing

---

### Post by jimbob on 2006-07-19
> **TomDooley said:**
> Hi there, 

2. As long as I still have my current card, I would like to be able to switch between the XGL/compiz 3D desktop and the regular Gnome 2D desktop when booting my PC. Does anybody know how I can add a possibility to select which X-server setup to use during the boot process? 

Thanks,
Tom

  I too would like an answer to this if anyone knows.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by MaxFun73 on 2006-07-19
> **jimbob said:**
> I too would like an answer to this if anyone knows.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

Me too!

---

### Post by cechico on 2006-07-19
I cant make XGL and GNOME work, everytime i do all the steps when i reboot a got a blue window saying "Failed to start the X Server (your graphical interface). I have try it 3 times and i got the same error, thank God i have backup all files. Any Help me or give me a tip to make it work.

---

### Post by TomDooley on 2006-07-19
Hi there,

great to hear that my second issue seems to be of common interest.

I just wanted to give you an update on my 1st issue with slow videos. Slow videos were not my only problem, I also had some videos that were displayed totally scrambled, as if a 300 pixel wide video is mapped onto a 290 pixel wide screen with the last 10 pixels being shown on the left hand side of the next line.

I am using Kaffeine with a xine engine for video playback and have changed the video driver in Settings->xine Engine Parameters->Video Options->Beginner Options from "auto" to "xshm". Whatever that does, but now video playback is smooth (even with rotated cube!) and clear.

Regards,
Tom

---

### Post by senzapadroni on 2006-07-19
> **cechico said:**
> I cant make XGL and GNOME work, everytime i do all the steps when i reboot a got a blue window saying "Failed to start the X Server (your graphical interface). I have try it 3 times and i got the same error, thank God i have backup all files. Any Help me or give me a tip to make it work.

Give a look to /var/log/Xorg.93.log and search for some errors: they are marked with **(EE)**

---

### Post by Owdy on 2006-07-19
> **poofyhairguy said:**
> 
Change every line but the “Identifier” line to look **just like mine**:

```
Section "Device"
    Identifier- leave this line alone!
    Driver        "nvidia"
    BusID        "PCI:1:0:0"
    Option         "RenderAccel"         "true"
EndSection
```  My busID was PCI:3:0:0. I changed it to 1:0:0 like you sayd, and xserver gives blue screen. I turned it back to 3:0:0 and everything works. So i recommend everyone use that busID what are there and not change that.

---

### Post by jstroot on 2006-07-19
hey all,

This is my second post regarding an issue, and I have a couple more.

Some programs which run fine without Xgl have problems running with Xgl. For example, Stellarium and Scorched3D will load fine with Xgl running, but their fonts are all unreadable. All of the fonts change to symbols. I have sifted through this forum, as well as the Gentoo Xgl how-to with no results. 
Any ideas welcome.

Second issue. Xgl does not allow window border/application theme settings. When I try to change the theme, the theme application terminates unexpectadely. 
Any ideas welcome.

Last issue. Some of my shortcuts do not work under Xgl. For example, I usually open a terminal with my windows button. Under Xgl, nothing happens.
I've tried a few different keyboard models, and none of them will work.
Any ideas welcome.

Have a good one,
jstroot

---

### Post by tuxcantfly on 2006-07-19
the reason Scorched3D and other games don't work with xgl is because they use opengl, and xgl/compiz prevent other apps from using opengl, so it uses software rendering. the way to avoid this is to do this:

[http://ubuntuforums.org/showthread.php?t=51486](http://ubuntuforums.org/showthread.php?t=51486)

as for the window decorations, they don't work because compiz is a window manager which replaces metacity (the default gnome one) and doesn't use metacity settings

---

### Post by beowulf62381 on 2006-07-20
> **jimbob said:**
> I too would like an answer to this if anyone knows.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]
Try this
[http://christer.homeip.net/index.php/xgl-on-dappernvidia/]("http://christer.homeip.net/index.php/xgl-on-dappernvidia/")
it shows you how to setup up xgl/compiz as a session from gdm

---

### Post by dominicguy on 2006-07-20
it took me 1  day and 7hrs to getting working... : )
[thisTutorial]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")
all I did is follow this tutorial for installing the Nvidia driver, and if I had the package it was install, i just re-install it...

after that I came back to this thread went straight to the
[COLOR="Red"]sudo gedit /etc/X11/xorg.conf [/COLOR]    step

made sure everything was cool with the Modules section..

then added ```
Option 		"RenderAccel" 		"true"
```

to the Device section...

my BusID was different then the one in this tutorial so I lefted like it was and it worked..

Thanks everyone, you guys are great.:cool:

---

### Post by jimbob on 2006-07-20
Just as a side note, prior to installing Xgl/Compiz I was getting 800+ frames-per-second running glxgears.

Now I am getting a steady 1300+ FPS!  Wow, I'm impressed.  And all this on a lowly GeForce2 M/MX-400 card.

Talk about steroids!
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by jstroot on 2006-07-20
> **tuxcantfly said:**
> the reason Scorched3D and other games don't work with xgl is because they use opengl, and xgl/compiz prevent other apps from using opengl, so it uses software rendering. the way to avoid this is to do this:

[http://ubuntuforums.org/showthread.php?t=51486](http://ubuntuforums.org/showthread.php?t=51486)

as for the window decorations, they don't work because compiz is a window manager which replaces metacity (the default gnome one) and doesn't use metacity settings

I have been searching for awhile now, so thanks mucho for the explanation!!! 
I tried out the new xserver deal and it works. No more funky font problems. Performance is a bit of an issue, but that's not the problem.
Thanks for the info, it's very much appreciated.

-jstroot

---

### Post by aeto on 2006-07-21
xgl/compiz is great. fantastic look. everything works even faster..except for 3d games. even if i change back to metacity..the games dont recognize the change since compiz is setup in the machine. to uninstall compiz do i just do the "Undo"?

---

### Post by michaeltrainor on 2006-07-21
I have converted...the same power in linux...better GUI experience...by far the clearest tutorial ever written..THANKS

---

### Post by sameeer_s on 2006-07-22
i just spent 6 hours going through the first half of the forum, and realise i need help..

i did everything as per the tutorial, but have lots huge black regions on my screen.. they are mostly caused by the trails left when moving windows.. i tried to make out as much as I could through the black regions, and turning, wobbling, switching etc seem to be working fine.. its just not even close to being usable, and looks ugly due to the black regions..

I've got an nvidia go 7600 card.. 

Please someone help me fix this problem. I can tell you anything more u need, like xorg.conf or whatever.. It sucks to be sooo close, yet so far...

Thanks a lot..

---

### Post by kopinux on 2006-07-23
it worked!!

i guess the key is the nvidia must be good and configured 100%.
can xgl do this? how? [http://www.pinoylinux.com/files/snapshot1_135.png]("http://www.pinoylinux.com/files/snapshot1_135.png")

---

### Post by xomnia on 2006-07-23
Ok I tried setting this up and when i got to the restart step i restarted and now my GDM cant start or x server.  Is there some way I can undo everything from the console?

---

### Post by xomnia on 2006-07-23
Wow major brain fart.  The reason it wasnt working was because I copied the xorg.conf exactly and my pci was supposed to be 5:0:0.  All fixed now and compiz works PERFECTLY!! except for that part of the guide...perfect.  Thanks for this its awesome.

---

### Post by aeto on 2006-07-24
and should AGP users be careful abt that line too? or is the agp slot considered pci bus 1:0:0?

---

### Post by RAOF on 2006-07-24
> **jimbob said:**
> Just as a side note, prior to installing Xgl/Compiz I was getting 800+ frames-per-second running glxgears.

Now I am getting a steady 1300+ FPS!  Wow, I'm impressed.  And all this on a lowly GeForce2 M/MX-400 card.

Talk about steroids!

Which is just another example why glxgears is a **rubbish** OpenGL benchmark (there is the --iacknoledgethistoolisnotabenchmark command-line switch ;)).  XGL will **degrade** your OpenGL performance in anything that matters - you lose direct-rendering.  Note all the threads/questions about "OpenGL games in XGL/Compiz" on compiz.net :)

---

### Post by TOPPEL on 2006-07-24
I'm having an issue with things like totem not keeping their original form after they have been launched.  they will not clearly display visualizations and everything else, the menu list at top will disappear and there will be horizontal type lines splatting out the rest of the totem music player.  i have not tried playing a video, though if i used totem which is lightweight -- it wouldn't work.  i followed the instructions to get it running from the first part of this thread.  it worked just fine.  prior to that i had latest nvidia from repo correct xorg.conf and correct refresh/sync rates.  i am not using the composite option for my geforce 6200 128 agp evga.  i've got 2.8ghz of cpu power and i was going to put in a dual core just to get the redraw working ?  eek.  help please.  i'd love to use this graphical manager.  

](*,)

---

### Post by Burgresso on 2006-07-24
This may have been touched on, but I could not find in this string...:) 

I have and AMD64 chipset, but am using the 32 bit ubuntu. Therefore, would I follow the directions on this thread or not?

edit: for grammar

---

### Post by yumigator on 2006-07-24
I have the NVidia 32MB GeForce2 Go in my Inspiron 8100. I tried the repository version of glitz, but that didn't work.

Then I went to the freedesktop site and found the CVS server, downloaded the files.

Can anyone walk me through the process of compiling and installing the CVS version? Thanks.

I had already installed the other packages, so if those need to be removed first, please let me know.

---

### Post by brownbear on 2006-07-24
Got it working but ...  

1 - I have a problem where you can move the windows under the bar at the top.  I'd prefer it if the maximum they could go was the bar.  Any way of altering a config file to do this?

2 - wmv files are split vertically in two using gxine (0.5.1).  The left side of the video is on the right hand side and the right side of the video is on the left.  If I resize the video the two halves start to interlace.  Sound is fine for wmv.  Sound and picture is fine for mpg in movie player (1.4.1).  Is there a way to play wmv files correcty?

3 - I've lost direct rendering.  Is that meant to be the case?

4 - The workspace switcher on the bar doesn't display the minature versions of what is displayed on that particular screen.  It's now just a blank grey box.

Linux Distribution = Ubuntu 6.06
Graphics make/model/memory/driver version = nVidia/Geforce 3/64MB/NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT
CPU model / CPU Memory = Pentium 4 1.5GHZ / 512MB

Thanks in advance,
bb.

---

### Post by LORD_PoLvO on 2006-07-25
OMG


i use the command the future and i get the erro on scrren 0 message and there is no compiz in gconfig or w/e i have run the command hundreds of times and still the same error whats going on please help ;(

---

### Post by Footissimo on 2006-07-29
This HOWTO doesn't work at all for me (32bit, Dapper, NV5700VE) - soon as I run thefuture script, I just lose the window bar on all my windows - kinda hoping that isn't the future, as it makes it more of a pain to close and minimise apps. ;)

Bah, anyway, I'll stick with boring old Gnome.

---

### Post by Metroid48 on 2006-07-29
Hey, just before I go ahead to install this thought I'd ask:

Is there a tutorial for Intel-based cards, or Intel Mobile Graphic Chipsets?

Thanks,
-Metroid48

---

### Post by IeU on 2006-08-02
```

felipe@felipe-pc:~$ sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package compiz

```

what am i doin wrong ?

---

### Post by IeU on 2006-08-02
my problem :

everything seems to working good.

but the "basic commands" arent working . . .
not even alt-tab.

i did at this step . . .
"xmodmap /usr/share/xmodmap/xmodmap.<language>"
"xmodmap /usr/share/xmodmap/xmodmap.de"

since im from germany and ive a german keyboard . . .

how do i fix this and also edit the commands ?

i ll be searching throught the 33 pages :P


thanks in forward.

---

### Post by bmonkey on 2006-08-02
my install went great - cept my netbeans no longer works? :( i tried reinstalling and nothing

---

### Post by BoomerAus on 2006-08-03
You da man.

Thanks, your script got XGL working nicely. 

:-)

---

### Post by loserboy on 2006-08-04
so sweet, works perfect so far thanks

---

### Post by wyk on 2006-08-04
did anyone try to run it on tnt2? i tryed but it worked kind of wrong.. is it my mistake or the card is unsupported?

---

### Post by foxy123 on 2006-08-04
> **poofyhairguy said:**
> 
Read the rest of this paragraph then reboot. After login in GDM, open a terminal and enter this (credit to rjtd):

```
xmodmap /usr/share/xmodmap/xmodmap.<language>
```

replacing you country code for language. For US English I use this command:

```
xmodmap /usr/share/xmodmap/xmodmap.us
```

Now put this command in the terminal to get compiz love:

thefuture

That should make compiz start working. If not, just keep using that command (maybe up to 20 times) till it does work. If you have problems, post them in thread so you can get help.

I wonder if I use two languages and want to switch between two keyboard layouts, what should I do?

---

### Post by loserboy on 2006-08-04
just a few questions now

1. how do I add more plugins

2. is there a theme manager for compiz

3. skydome?

I've seen some threads about these but I don't know how to tie them in to work with this howto.... (read - i dont know what i'm doing)

---

### Post by TJGuitarZ on 2006-08-04
Um... I think I messed up the "module" section. Was I supposed to delete all the code underneath there? If not, could someone tell me exactly what I'm supposed to have under there?

Thanks for your help, TJ

---

### Post by foxy123 on 2006-08-05
> **loserboy said:**
> just a few questions now

1. how do I add more plugins

2. is there a theme manager for compiz

3. skydome?

I've seen some threads about these but I don't know how to tie them in to work with this howto.... (read - i dont know what i'm doing)

look here [http://www.compiz.net/index.php](http://www.compiz.net/index.php) it is a compiz forum.

For theme manager you have to install cgwd and cgwd-themes.

---

### Post by dexter on 2006-08-05
> **bmonkey said:**
> my install went great - cept my netbeans no longer works? :( i tried reinstalling and nothing

My netbeans also just gives me a blank screen with Xgl. You can try using Eclipse instead, I find it better then netbeans (faster :p).

---

### Post by n8wood on 2006-08-05
In gimp when I try to do something that opens a new window (like adjusting curves), the window with the image I'm working on loses focus, so it gets desturated. In this case the GUI eye candy is getting in my way. 

Is there any way to disable that feature on gimp screens only? If not, how do I disable only that function in Gset-compiz?

thanks.

---

### Post by louis_nichols on 2006-08-05
anyone know what I should do when I get this error:```
 cgwd: Screen 0 on display ":0.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

```
here's my xorg.conf

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"

#   Load "GLcore" 
    Load           "bitmap"
    Load           "dbe"
    Load           "ddc"
#   Load "dri" 
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "record"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "DELL P791"
    Option         "DPMS"
EndSection

Section "Device"

#	BusID		"PCI:2:0:0"
    Identifier     "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
    Option	   "RenderAccel" "true"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "DELL P791"
    DefaultDepth    24
    Option         "RenderAccel" "true"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


```

---

### Post by waltervalderrama on 2006-08-05
Everything went ok, but amarok stopped working since compiz. I really like amarok, what can i do????????

---

### Post by smeager on 2006-08-05
While I haven't read all 132 pages of this post, I am sure that there are a lot of helpful hints on how to get XGL/Compiz working, but the problem I have is that while I like to have the new "goodness" I don't like the idea of changing settings, so that XGL/Compiz start when Gnome loads and not have a way out if something goes wrong. I've set my system up so XGL/Compiz loads in its own seesion, accessiable from the login menu, so just in case something goes wrong I still have a fully functional session to use to fix things. 

I am currently writing a howto on how I set up my Ultimate Ubuntu System. Here is a pdf for people to read and use. (its still a work in progress)

---

### Post by saracen on 2006-08-06
does anyone know if the NVIDIA GeForce MX 440 uses the newest binary drivers or the legacy ones?

---

### Post by jstroot on 2006-08-06
> **saracen said:**
> does anyone know if the NVIDIA GeForce MX 440 uses the newest binary drivers or the legacy ones?

It can use both, but for XGL it is probably best to use the Nvidia drivers from the repository. I had XGL running with the repository Nvidia drivers, and later installed the latest Nvidia drivers. The installation broke XGL, and I haven't spent the time to fix it.

jstroot

---

### Post by saracen on 2006-08-06
I guess I wasn't clear.  In the repos there is nvidia-glx and nvidia-glx-legacy.  I'm not sure whether or not the GeForce MX 440 uses the legacy driver or not.

---

### Post by davidsampson on 2006-08-06
Err,  it worked fine until I tried to install the packages:

```
admin@athlon:~$ sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package compiz

```

I just installed ubuntu today, 6.06.  Other packages installed fine, and I'm connected to the internet.  I tried removing some of the packages from the list, but it can't find any of them.  Is there anything I can do?

EDIT:  Fixed by adding repositories.:cool:

---

### Post by jstroot on 2006-08-07
> **saracen said:**
> I guess I wasn't clear.  In the repos there is nvidia-glx and nvidia-glx-legacy.  I'm not sure whether or not the GeForce MX 440 uses the legacy driver or not.

With the GeForce MX 440 Go, I used the non-legacy drivers and it worked fine.
I haven't seen anywhere that implies that one HAS to use one or the other. However, most other users with this card use the non-legacy or they use the proprietary nvidia drivers,

---

### Post by FeestBijtje on 2006-08-07
Took me about 7 reboots to get compiz working and i gave up the hope... till i exedently hitted the shortcut for the command "thefuture" and now it works lol :)
After 8 times total :D

---

### Post by jstroot on 2006-08-08
These videos just got dugg. if yo haven't seen them, you need to!!

[http://digg.com/linux_unix/Dual_head_with_Compiz_XGL_Video](http://digg.com/linux_unix/Dual_head_with_Compiz_XGL_Video)
[http://youtube.com/watch?v=lawkc3jH3ws](http://youtube.com/watch?v=lawkc3jH3ws)

The second link is some cutting edge stuff.


I have no idea if this stuff is available yet.

---

### Post by Blue1k on 2006-08-08
> **smeager said:**
> While I haven't read all 132 pages of this post, I am sure that there are a lot of helpful hints on how to get XGL/Compiz working, but the problem I have is that while I like to have the new "goodness" I don't like the idea of changing settings, so that XGL/Compiz start when Gnome loads and not have a way out if something goes wrong. I've set my system up so XGL/Compiz loads in its own seesion, accessiable from the login menu, so just in case something goes wrong I still have a fully functional session to use to fix things. 

I am currently writing a howto on how I set up my Ultimate Ubuntu System. Here is a pdf for people to read and use. (its still a work in progress)


Your instructions for XGL don't work or maybe I am bit confused. I am not too sure of your instructions after the point of having to print out the file. Do you have to do the last bit of instructions in verbose mode?
I am little confused


EDIT...Installed XGL using the Ubuntuguide with the future script. However very few of the features work. Rotation or translucency doesn't work and only 1 window can be highlighted at a time.

---

### Post by DSn0wMan on 2006-08-10
This worked on the first try. One thing though, now my desklets float on top of my application widows. I'd rather have them stick to the desktop. Any suggestions?

---

### Post by Jeremiah478 on 2006-08-10
this was a great howto, it looks amazing, thanks

---

### Post by smeager on 2006-08-10
> **Blue1k said:**
> Your instructions for XGL don't work or maybe I am bit confused. I am not too sure of your instructions after the point of having to print out the file. Do you have to do the last bit of instructions in verbose mode?
I am little confused


EDIT...Installed XGL using the Ubuntuguide with the future script. However very few of the features work. Rotation or translucency doesn't work and only 1 window can be highlighted at a time.

After you did everything for installing XGL did you log out and then log back into the newly created XGL. You have to be in your XGL session before you can set up Compiz. 

Once your in your XGL session open a terminal and (If you haven't already done so) install compiz, compiz-gnome, gset-compiz.

```
sudo apt-get install compiz compiz-gnome gset-compiz
```

After everything is installed you have to is setup **gnome-window-decorator**.

Type:
```
gnome-window-decorator &
*press enter*
```

This effectivily starts the Compiz Window Manager under Gnome. Then you are going enter the following exaclty as shown. If you don't Compiz will not work. (Certain plugins have to load before others).

```
compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher trailfocus water bs neg & 
*press enter*
```

Now you have XGL/Compiz running with all of its eyecandy goodness.

Now that you have that done you can add two simple commands to your users startup session. To do this navigate to System->Preference->Sessions or if you are using the new menu navigate to Control Panel->Preference->Sessions. Click on the right most tab Startup Programs and create new entries with the following commands:

```
gnome-window-decorator
*and*
compiz --replace gconf
```.

That's it. If you have anymore questions just ask.

[IMG]http://img.photobucket.com/albums/v486/smeager/logon.png[/IMG]

[IMG]http://img.photobucket.com/albums/v486/smeager/sessions.png[/IMG]

---

### Post by marytgras on 2006-08-11
Okay, bear with me because I'm really new to Ubuntu.  I've loaded it onto several old machines that I would call franken-puters from spare parts.  But this is the first one that I thought might have the requirements to run compiz.  First off, here's my setup:

A Dell Latitude C810 with a Pentium 3 mobile @ 1.13 GHZ w/ 512 MB RAM with a Nvidia GeForce 2 Go w/ 32MB running Ubuntu Dapper.

I was able to follow along without a hitch until I opened up a terminal in Gnome and entered 'thefuture'

marty@destroyer:~$ compiz.real: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.

Plus, here's the response I got from opening up a shell (CTRL-ALT-F1):

(gnome-window-decorator:5032): Gtk-WARNING **: cannot open display:
marty@destroyer:~$ compiz.real: Couldn't open display

What do I need to do to fix this?

---

### Post by Cutter77 on 2006-08-11
Great Guide, just what I needed.  And great thread too.
Thanks.

---

### Post by Flipper on 2006-08-11
Hi all, thx for this fine tutorial!
I can get the windows "jingle" etc , but i cant make the cube commands work :\

when i type:
thefuture

it says :

compiz.real:Couldn't load plugin 'librotation.so'

Does anyone have a solution for this?
thx a million :D

---

### Post by thsman on 2006-08-11
I only just heard about compiz today... then I saw the video and was very impressed..... then I came across this post and thought I'd try it out... I've been using Ubuntu for less than two weeks so wasn't that confident in making such a radical changed but ..... it worked straight off and I'm sitting here with the biggest grin since connecting to another computer via a 1200 baud modem about 18-20 years ago for the first time. Toooo mucking fuch!

---

### Post by Big_J on 2006-08-12
I just installed this and it worked good, except for one thing.
My keyboard no longer works correctly, I have to hold the shift key to use the space bar. 
Anyone know how tofix This?
I already rebooted three times, and XGL is Not running right now

---

### Post by Big_J on 2006-08-12
never mind I got it fixed now, I had the space bar as a part of a keyboard shortcut while XGL is running, so the option wasn't there when it wasn't running and I couldn't use the space bar.
all good now

/Edit
Programs running under wine don't run with compiz, so how do I stop it without restarting x?

---

### Post by offramp13 on 2006-08-14
I tried this on my 64 bit Ubuntu, and now it doesnt boot, i dont know what is going on. It gets some error message and wont start GDM, then says i need to repare something and restart gdm. I am very much a noob to this. This is the second time trying it with this guide getting the same problem, i reformatted last time and reinstalled it. But now i have files i want to keep on my system and dont want to reformat. I would appreciate it if someone could help me out.

---

### Post by Contrid on 2006-08-14
I don't know why this is happening, but after I restarted, my x server was disabled, and I was in the GDM. So I typed :

> xmodmap /usr/share/xmodmap/xmodmap.us

It's giving me the following error :

> xmodmap: unable to open display ' '

Right now I cannot log into Ubuntu anymore. Or atleast I have no idea how to do it. I guess I shouldn't be fiddling with these things with my limited knowledge and experience.

Can someone tell me how to fix this or how to do a rollback?

Thanks. All help is GREATLY appreciated.

All the best,
Contrid

---

### Post by Contrid on 2006-08-14
Man...I really hope that I don't have to reload my Ubuntu AGAIN :(

---

### Post by Pnut on 2006-08-16
I get the same error you were getting encho.  I tried executing "thefuture" over 60x.  Am I doing something wrong?

---

### Post by phenolholic on 2006-08-17
I FINALLY got mythbackend and mythfrontend to load. However, when I try to go into View TV in myth's main menu, I get a menu saying

WARNING: something is already using /dev/dsp, retrying.

with two options, continue without audio & return to menu. i click 'continue without audio' and all of a sudden I get logged out of X (i see the CLI login). also, something to note, when I run mythbackend in a terminal, I get:

2006-08-15 03:57:57.776 New DB connection, total: 1
Starting up as the master server.
2006-08-15 03:57:57.785 New DB connection, total: 2
Error getting inputs for the capturecard. Perhaps you have
forgotten to bind video sources to your card's inputs?
2006-08-15 03:57:57.797 New DB scheduler connection
bttv is defined, but isn't attached to a cardinput.
2006-08-15 03:57:57.799 mythbackend version: 0.18.1.20050510-1 [www.mythtv.org](www.mythtv.org)
2006-08-15 03:57:57.800 Enabled verbose msgs : important general
2006-08-15 03:57:59.799 Reschedule requested for id -1.
2006-08-15 03:57:59.806 Scheduled 0 items in 0.0 = 0.00 match + 0.00 place
2006-08-15 03:57:59.808 Seem to be woken up by USER


Notice the 'Error getting inputs for the capturecard. Perhaps you have
forgotten to bind video sources to your card's inputs?' and the 'bttv is defined, but isn't attached to a cardinput.' ..maybe that's the reason. Also, my tv card works under xawtv. Any info would be greatly appreciated!

---

### Post by fandelau on 2006-08-18
On February 28th, 2006 at 08:49 PM, zaziork said...
> 
Yes, my aMSN is no longer starting, even when I'm not in compliz. Anyone have any ideas?

Lack of aMSN is a small price to pay though..

EDIT: Just found the answer to the aMSN issue, as posted in another thread by Greg T:

```
sudo ln -s /etc/X11/rgb.txt /usr/share/X11/
```


I did that and amsn worked... the problem now is that I can't use backspace, enter or any other key... I get \b, \r, and the arrow key won't work... 
Unfortunately no aMSN is a big price to pay for me as that is how I communicate with family and friends abroad... any one has an idea on how to work this out? please!!!

---

### Post by akademy on 2006-08-19
That's really great! Only saw the video of the features last week - now I can play around with them too!

(Had one small problem where I couldn't figure out how to change the colour depth - so I left it assuming it was on 24 bit... it wasn't and the screen totally messed up on restart, luckilly I could see enough to switch it over - it now looks great! (I'm using Nvidia on a widescreen laptop if you're interested)

Thanks again for this tutorial :D 

PS - Does anyone now where theres a manual of all the features? I'm trying to work out how wo make a window transparent...

---

### Post by The Pinny Parlour on 2006-08-20
Great how-to. Thanks to PHG.  :) 

Everything works fine, except it appears my nvidia driver settings (nvidia X server settings) are not there anymore, Application>System Tools> NVIDIA Settings.  Any ideas?

Also, my pc does not boot straight into XGL, I have to enter in Terminal "thefuture" everytime I want it to work.  Is this normal?
It would be great from time to time, to be able to disable, (turn off) "thefuture".  How does one do that?  

Thanks for YOUR help answering my Q's.

---

### Post by hitman012 on 2006-08-20
I notice that [this page]("http://www.freedesktop.org/wiki/Software_2fXgl") lists:

> GLX - Accelerated indirect GLX rendering - 90%

Does this mean we will finally be able to watch videos without massive CPU usage? That'd make it a winner for 24/7 use ;)

---

### Post by autocrosser on 2006-08-20
For anyone that wants to use Compiz with the new CGWD & CGWD Themes---
Install cgdw & cgdw-themes--*code*
sudo apt-get install cgdw cgdw-themes  (requires the "extra" repositories)

Modify the "thefuture" script by adding--

cgwd --replace &      at the end--in other words, the full script should look like---

#!/bin/bash
gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place 

switcher &
cgwd --replace &     <-----added line----->

Enjoy!!!

(note: this only works right with Poofy's way of starting compiz)

---

### Post by RAOF on 2006-08-23
> **phenolholic said:**
> ...

WARNING: something is already using /dev/dsp, retrying.

with two options, continue without audio & return to menu. i click 'continue without audio' and all of a sudden I get logged out of X (i see the CLI login). ...

The first problem is that mythtv uses OSS, which is old, crusty, and won't let two programs access the soundcard at the same time.  Install "alsa-oss", and run mythfronted as "aoss mythfrontend".  That will load the ALSA-OSS emulation layer, which will allow mythtv to use the soundcard.  Which will make you run into the second problem more often :).

The second problem is that XGL **hates** the way mythtv uses XV acceleration.  Crashes XGL every time, without fail.  You can make mythfrontend not use XV acceleration by running:
"NO_XV=1 aoss mythfrontend"
That will then run, but be a bit slower.

I may be wrong with "NO_XV".  I might be "XV_NO" or something similar.  I forget :(

---

### Post by fatboysmith on 2006-08-23
I have Compiz/Xgl working fine with 6.06 Dapper on an Nvidia 6800GT. I've scoured the forums for a way to change the default keys.  I use an older "bucking spring" 101 keyboard (I like the click-click noise), it does not have Super a.k.a. Windows key.  Where or how do I change the default keys?

Dennis

---

### Post by JNasci7906 on 2006-08-24
whenever i push alt the in focus window moves around the cube, no need to push ctrl...any quick fixes??? thanks!

---

### Post by SaiaGo on 2006-08-24
First of all, hi!
Im new to ubuntu, and linux generally.
Im also just a 14 years old guy from israel, so sorry for any spelling mistakes or anything else about my english.

Now, to the topic:
I followed your guide until the point where I need to install xgl.
I pasted the code, and it sais:
```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package compiz

```
It might be a stupid problem, cuz I dont really know what is compiz and xgl and where to get these programs(or whatever they are).

Thanks for anyone who helps.

---

### Post by Eleka on 2006-08-24
> **SaiaGo said:**
> First of all, hi!
Im new to ubuntu, and linux generally.
Im also just a 14 years old guy from israel, so sorry for any spelling mistakes or anything else about my english.

Now, to the topic:
I followed your guide until the point where I need to install xgl.
I pasted the code, and it sais:
```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package compiz

```
It might be a stupid problem, cuz I dont really know what is compiz and xgl and where to get these programs(or whatever they are).

Thanks for anyone who helps.

U saw that compiz packages have changed its names: now, compiz is not a necessary package, and now exist other compiz packages, like compiz-core or compiz-gnome or compiz-plugins that replace the compiz one.

Your problem would be respository foult or that the packages names have changed

---

### Post by Eleka on 2006-08-24
With the latest issues with xserver-xorg-core I lost my Xgl :(

If I start gdm without modify the /etc/gdm/gdm.conf-custom file, I have hardware acceleration and about 7500 FPS, but, if I modify the file, I can't start compiz and only have 3500 FPS ... What can I do to restore my Xgl and Compiz?

Is it a problem to me or they are more people as me?

---

### Post by philipgm on 2006-08-24
I've been trying to get Xgl and compiz working on my nvidia Riva TNT2 M64 card, which is supported, according to the gentoo wiki. Everything seems to be installed and I can start an xgl session. But when I start compiz I get this message.

compiz.real: Support for non power of two textures missing
compiz.real: Failed to manage screen: 0
compiz.real: No manageable screens found on display :0.0

Apparently this was fixed for nvidia cards in libglitz5.3. I have 5.6 installed from the repos.

Anyone with any ideas for how to get this working? or is it off to spend more money on ebay?

---

### Post by Family_Guy on 2006-08-25
> familyguy@ubuntu:~$ gnome-window-decorator, Failed to load shadow images
compiz.real: No composite extension

Hardware: NVIDIA Corporation NV34 [GeForce FX 5500]

any ideas? Sorry if it's been mentioned before, 135 pages is a lot to look through.

---

### Post by Gnelg on 2006-08-25
Having a few troubles with xgl+Compiz

XGL is starting up fine but compiz is segfaulting with the following message:

Aug 25 01:50:01 localhost kernel: [  514.052490] compiz.real[5381]: segfault at 0000000000000000 rip 00002aaaab7b87b3 rsp 00007ffffff767e8 error 4

The other problem is that The Title bar decoration has been removed from all windows opened and no windows can be moved.

pc specs in case there is something I don't know about yet:

AMD64 FX-55 CPU
EVGA GeforceFX 6800 GT
2GB ram

The binary nvidia drivers are loading and I can see that the xlg server is running with ps -aux

edit: The above does not happen until the thefuture script is run. So I think mine may be missing something. Here is my script:

#!/bin/bash
gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &
xmodmap /usr/share/xmodmap/xmodmap.us

Any ideas would be helpful

Glen

---

### Post by Gnelg on 2006-08-25
> **offramp13 said:**
> I tried this on my 64 bit Ubuntu, and now it doesnt boot, i dont know what is going on. It gets some error message and wont start GDM, then says i need to repare something and restart gdm. I am very much a noob to this. This is the second time trying it with this guide getting the same problem, i reformatted last time and reinstalled it. But now i have files i want to keep on my system and dont want to reformat. I would appreciate it if someone could help me out.


It sounds similar to what I first ran into after rebooting.  The way that I resolved it is by editing the /etc/X11/xorg.conf file and commenting out 2 of the lines as shown below:

Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
#	Option		"RenderAccel"		"true"
#	Option		"AllowGLXWithComposite" "true"
	BusID		"PCI:1:0:0"
EndSection

Hope this helps.

Gnelg

---

### Post by Family_Guy on 2006-08-25
> 
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0


I lose all window decorations, they snap to the top of the screen.

---

### Post by Eleka on 2006-08-25
Hello.

I have posted it in other two posts, because I want a solution. My situation is not very popular ...

I broke my system a days ago when the upgrade of the famouse package xserver-xorg-core. I upgraded it to a newer version and then, restored my Xorg, nvidia direct rendering .... but, only running xorg. when I try to run Xgl at the startup, my direct rendering go to "no" and I have no more hardware acceleration, and don't Compiz too ...

Is somebody in the same situation or knows how to fix that?

---

### Post by philipgm on 2006-08-25
direct rendering always says no under Xgl. 

Boot into gnome and run glxgears there.

---

### Post by Eleka on 2006-08-25
Thanks, I fix the problem ... in my init compiz script I forget to delete the arguments of compiz and then it didn't work for me.

thanks a lot for your answer!

---

### Post by Family_Guy on 2006-08-26
> 
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0


I lose all window decorations, they snap to the top of the screen.

---

### Post by The Pinny Parlour on 2006-08-26
It doesn't work for me.  here is what I get:

gnome-window-decorator, Failed to load shadow images
compiz.real: No composite extension


Yes I have loaded the:  

Section "Extensions"
          Option  "Composite" "Enable"
EndSection

at the end of xorg.conf


Any suggestions?

---

### Post by The Pinny Parlour on 2006-08-26
I rebooted, now I get this:
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

---

### Post by greenwom on 2006-08-26
(Love Compiz)
I installed via this HowTo and everything worked well (I had a dual head and I lost twinview)

I started poking around other threads and forums to get twinview going, and I broke compiz.

GDM wouldn't start but I could "sudo startx"....
I deleted gdm.conf-custom and all was back to normal

I've restarted the Howto in the hopes of getting this going again but when I run thefuture X crashes.  (Same with startcompiz)

Here's what I have

```
# ///////////////////////////Xorg.ConF\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/ttyS0"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/ttyS0"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/ttyS0"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
EndSection

Section "Device"
	Identifier	"Nvidia GeForce FX5500 PCI"
	Driver		"nvidia"
	BusID		"PCI:2:11:0"
	Option 		"TwinView" "True" 
	Option 		"TwinViewOrientation" "RightOf" 
	Option 		"UseEdidFreqs" "True" 
	Option 		"MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
	Option 		"UseDisplayDevice" 	"CRT"
	Option 		"RenderAccel"		"true"
EndSection

Section "Monitor"
	Identifier	"eView 17f"
	Option		"DPMS"
	HorizSync	30-72
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Nvidia GeForce FX5500 PCI"
	Monitor		"eView 17f"
	DefaultDepth	24
	SubSection	"Display"
		Depth		24
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

##I've tried with this enabled and commented out
Section "Extensions"
          Option  "Composite" "Enable"
EndSection

```

From gdm.conf-custom
This doesn't work at all```
 [servers]# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX). 
0=Xgl 
[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo 
flexible=true 
```

This works```
[servers]
0=Xgl 

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
flexible=true
```

thefuture
```
#!/bin/bash
gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimiz$
```

startcompiz
```
#!/bin/bash
gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimiz$
```

Any clue how to get this going with twinview? or even without.

---

### Post by Saibot on 2006-08-26
I changed thefuture startup script to this

```
#!/bin/bash
cgwd &  compiz --replace gconf &
```

Use Configuration Editor under Apps/compiz/general/allscreens/options/active plugins to change the plugins you want to load.  Mine is [gconf,dbus,blur,decoration,wobbly,fade,minimize,cube,rotate,zoom,scale,move,resize,place,switcher,trailfocus,water,showdesktop,put]

---

### Post by Clark Nova on 2006-08-26
Works for me! Thanks sooo much :D

---

### Post by dannyboy79 on 2006-08-26
Hey guys, I was having trouble figureing out Compiz and when I found [www.compiz.net](www.compiz.net) I was able to get it all working. It is awesome!!!! I love the Cube effect, and the water effect is cool but can't handle it for 2 long. I'll tell you what though, I think it is way better to start Compiz as it's own session instead of having it run automatically when you start your normal session. This way, you can go to options before you log in and go to choose session, then pick Xgl and log in. I do know this, if you log in and you windows don't have borders and no minimize or X to close it down and they are stuck in the upper left hand corner it's because you don'thave a theme loaded. Go to a terminal and type in metacity and you;ll get a normal Gnome Session. After that happened to me, I just decided to look for another guide and start over. THat's when I found a guide at compiz.net. Good Luck!

---

### Post by siucdude on 2006-08-26
This thing is awesome.  I have used linux on and off but now its on all the time.

Thanks

---

### Post by WPAStrangla on 2006-08-27
When you say:

> 
Find the “Module” section. Comment out the “Glcore” and “dri “ modules and make sure a “glx” module is there. So basically like this:
Code:

# Load "GLcore"
# Load "dri" 
  Load "glx"


I have:

```
Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection
```

Should I deleate everything and add

# Load "GLcore"
# Load "dri" 
  Load "glx"

And how am i supposed to do this?

> You must compile the newest CVS version of glitz to get this to work with Nvidia cards that lack Pixel Shaders (aka anything older than a 5200 FX). Hopefully this will be updated in the repository soon.

Or what do you mean? Im confused :-k

Im also Running:

Geforce 4 MX 440 With AGP8x

---

### Post by Mandoscottie on 2006-08-27
just wanted to say your walkthrough works flawlessly :) 

thank you dood you are a :KS 

Got it working with a 7800GT 512mbr, P4 3ghz (running 686 smp kernel) & 2gb DDR400 ram @1920x1440@75hz. 
Only been using Linux/Ubuntu for approx a week and I gotta say this ROCKS)

thing is when I spin to next workspace my stomach churns LOL :cool: 

once again cheers buddy :)

---

### Post by WPAStrangla on 2006-08-27
Never mind my above post. I got XGL working from this thread 

[http://tazforum.thetazzone.com/viewtopic.php?t=2189](http://tazforum.thetazzone.com/viewtopic.php?t=2189)

Its great! =D>

---

### Post by mpcd on 2006-08-27
FYI

I installed the latest 8774 nVidia drivers using [another tutorial]("http://www.ubuntuforums.org/showthread.php?t=139264") found on these forums. I reinstalled all of the components required to run compiz based on this thread:

```
sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome --reinstall
```

After doing so I noticed that launching compiz would crash the X server. After some digging and experimenting, I found that the mesa libGL was the cause. In order to fix this I had to grab the latest mesa from CVS:

```
cvs -d :pserver:anoncvs@cvs.freedesktop.org:/cvs/mesa co Mesa
```

I've never built Mesa before so I don't know all of the build options, but doing a:

```
make linux-dri-x86 
```

from the newly checked out Mesa directory will build a number of new binaries. Inside of the "Mesa/lib" directory, a new libGL.so.1.2 library will be generated. I did not do a make install for fear that some of the nvidia driver components would be overwritten, so I manually copied the new libGL.so.1.2 to /usr/lib and ensured that the symlinks for libGL.so and libGL.so.1 pointed to this new library.

I hope this helps anyone who ends up having the same problem as me. If anyone who follows this method is brave enough to do a sudo checkinstall on mesa (the way it probably SHOULD be done), it would be helpful to post your results.

---

### Post by hoagie on 2006-08-27
Hello, your guide is great, it work perfectly for me...
My only problem is that when I use compiz/xgl the top bar of every application (where the close/naximize/minimize buttons are) dissapears...
Please help me out

---

### Post by Eleka on 2006-08-27
Some things have changed on the latest compiz releases. See the ubuntu wiki to get help and install it correctly:

[Installing Compiz]("https://help.ubuntu.com/community/CompositeManager/InstallingCompiz")

---

### Post by smiley2billion on 2006-08-27
> After doing so I noticed that launching compiz would crash the X server. 

Oh yes, very true for me as well.

Nvidia 6800 GS

This is also the card that HATES the "nv" driver that Ubuntu uses by default.  I'm not sure why this hasn't been fix yet.  Oh well.

When I try to build the new libs from the CVS checkout of mesa I get a world of errors, including such hits as:

```

Package libdrm was not found in the pkg-config search path.
Perhaps you should add the directory containing `libdrm.pc'
to the PKG_CONFIG_PATH environment variable

makedepend: warning:  glcontextmodes.c (reading /usr/include/bits/types.h, line 31): cannot find include file "stddef.h"

makedepend: warning:  glxcmds.c (reading /usr/include/limits.h, line 124): cannot find include file "limits.h"

makedepend: warning:  glxcmds.c (reading ../../../src/mesa/main/glheader.h, line 72): cannot find include file "float.h"

make: *** [linux-dri-x86] Error 2


```

So, if you could post/email that libGL.so.1.2 somewhere that'd be great (namely smiley2billion [at] gmail [dot] com), thanks!

---

### Post by The Pinny Parlour on 2006-08-28
> **dannyboy79 said:**
> Hey guys, I was having trouble figureing out Compiz and when I found [www.compiz.net](www.compiz.net) I was able to get it all working. It is awesome!!!! I love the Cube effect, and the water effect is cool but can't handle it for 2 long. I'll tell you what though, I think it is way better to start Compiz as it's own session instead of having it run automatically when you start your normal session. This way, you can go to options before you log in and go to choose session, then pick Xgl and log in. I do know this, if you log in and you windows don't have borders and no minimize or X to close it down and they are stuck in the upper left hand corner it's because you don'thave a theme loaded. Go to a terminal and type in metacity and you;ll get a normal Gnome Session. After that happened to me, I just decided to look for another guide and start over. THat's when I found a guide at compiz.net. Good Luck!

Thanks dannyboy79,

Followed some guides there and all went very nicely.  \\:D/

---

### Post by The Pinny Parlour on 2006-08-28
I'm still to get an answer on one question though.
How does one STOP the eye candy once you have started it.  It must be the most simplest command I'm sure.

TIA

---

### Post by louis_nichols on 2006-08-28
> **The Pinny Parlour said:**
> I'm still to get an answer on one question though.
How does one STOP the eye candy once you have started it.  It must be the most simplest command I'm sure.

TIA

I think that would be
```
metacity --replace &
```

---

### Post by strictlyr00ts on 2006-08-28
Thanks for this.. and all who contributed. /respect
I followed the guide exactly and it worked np.

XGL and Compiz are now up and running on my sager laptop.
Its running 1650x1080 on my NVIDIA 7800gtx go card. 



To get the widescreen to work I had to edit my 
/etc/X11/xorg.conf file and replaced "1024x768" with "1680x1050" in each of the mode entries.

---

### Post by gusto5 on 2006-09-02
i did it like, 50 times
stephen@stephen-laptop:~$ compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
gnome-window-decorator: Another window decorator is already running

and it wont stop.

edit-

ok, i went through the tutorial again, and once i hit the "thefuture" step, it appears to simply restart gdm. whats going on?

---

### Post by thegreatnorth on 2006-09-03
I am new to Ubuntu and read about XGL. I searched and found this guide. I am using a ASUS A7N8X-E with an AMD 3200+ 1gb ram and a MSI nVidia FX5600 video card.

This guide worked perfectly on the first try!
Excellent work!

---

### Post by Ian Hadaway on 2006-09-03
I Have a problem,

I followed your script on my first install of dapper and had no problem then i wiped went to install agian and got to xgl and got this error message on loading up my machine.

"GDM: Xserver not found: /usr/bin/Xgl :0 :0 -fullscreen -ac -accel
glx:pbuffer -accel xv:fbo -auth /var/lib/gdm :0 xauth -no listen tcp vt?
Error: Command could not be executed!
Please install the X server or correct GDM configuration and restart GDM."

so I re-installed dapper and did the xgl tutorial agian and got the same problem but this time i saw the link between the ending on your gdm.conf-custom file and what it was trying to do, now further up in the installation that line of installs it couldn't find compiz xserver-xgl and compiz gnome.

I also looked in the /usr/bin/ and Xgl didn't exsist.

please can you help.

cheers Ian

---

### Post by Ian Hadaway on 2006-09-03
sorry about the smiley it should be this 

"GDM: Xserver not found: /usr/bin/Xgl :0 :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt?
Error: Command could not be executed!
Please install the X server or correct GDM configuration and restart GDM "

---

### Post by greyash99 on 2006-09-03
How do you get the water effects to work?

---

### Post by neo4386 on 2006-09-04
Thanks a lot for this splendid instruction! I got my XGL working at last! The only problem I have now is that, when I use the cube, fades, wobble it works perfectly fine. But then when I try to use F12 (arrange), move focused app to another workspace, zoom, app switcher, I cant get it to work! I tried the shortcuts all over but didnt get them to work at all... I tried restarting the box though, and got the switcher and app-move to work, but i cant zoom (huhuhu).... Now I tried restarting once more, and I got the same problem. I tried modifying gconf-editor, but with no improvement...  

can somebody please help me??...

---

### Post by feest on 2006-09-04
sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome

is says that is can't find package compiz?

---

### Post by kwalo on 2006-09-04
**neo4386**, open gconf-editor. In apps->compiz->plugins->scale->allscreens->options you have options responsible for scaleing.
Option 'initiate_all_key' will show you all windows from all workspaces. It defaults to F11.
Option 'initiate_key' shows windows from current workspace.
It won't work, until you disable another option, which uses F12 key. I can't remember where it was, that option (Windows Key + F12, or something) turned on window, which was showing fps. Can't remember where it was.

For zooming, I went to: apps->compiz->plugins->zoom->allscreens->options
And set keys:
zoom_in_button to <Control><Alt>Button4
zoom_out_button to <Control><Alt>Button5
Now, when I scroll the mouse with both Control and Alt buttons pressed, I zoom in/out the screen. That's more handy than zooming with mouse button 2.

---

### Post by mcuerdo on 2006-09-05
Hi, I followed this guide and got a white screen after system boots. I tried to restore original xorg.conf and gdm.conf.custom, but problem still remains :???: 

Has anyone had the same problem? How can I restore previous configuration (no compiz no xgl...)

Thanks

---

### Post by 7he on 2006-09-05
Hi!
Thanks for this guide, I followed it and it works. It's very nice and beautiful. However, I got crashes all the time. The system stops responding...   
And I have to reset my computer!!

Is it the case for other people?  
Do I have to change some settings?

Will Xgl be default on 6.10 ?

Thanks
7he

---

### Post by 7he on 2006-09-05
> **mcuerdo said:**
> Hi, I followed this guide and got a white screen after system boots. I tried to restore original xorg.conf and gdm.conf.custom, but problem still remains :???: 

Has anyone had the same problem? How can I restore previous configuration (no compiz no xgl...)

Thanks

TO undo , just follow the guide:

> To Undo

This command:

Quote:
sudo gedit /etc/gdm/gdm.conf-custom

Then clear the file and save it. 

After that you may have to reconfigure your Xserver
I did it with:   
```
 
sudo dpkg-reconfigure xserver-xorg

```

---

### Post by suhaib on 2006-09-05
I used various guides to install compiz and xgl.  When one method didn't work, I'd undo the changes and move on.  However I didn't remove any of the packages I downloaded in the process.  I got multiple problems now though lol (since the compiz update I received today).

---

### Post by bulldog on 2006-09-05
The updates require some other compiz startup.

When everything worked before the updates try the folowing.

Go to preferences->sessions->startup apps and remove everything what is pointing to your compiz startup [thefuture.compiz-start.py]

On the middle tab of your sessions menu remove everything that points to your compiz [thefuture/compiz-start.py or what ever]

Now put the folowing in sessions starting apps   /usr/bin/compiz-start

Log out and login again and it should be working again.

You can configure your plugins with 'csm' in your terminal which starts a configuration app.

gsetcompiz can be removed because it's no longer in use anymore.

If the changes you make in csm don't stick do

chmod 755 ~/.compiz -R 

and it should.

Hope this will help.

---

### Post by suhaib on 2006-09-05
> **bulldog said:**
> The updates require some other compiz startup.

When everything worked before the updates try the folowing.

Go to preferences->sessions->startup apps and remove everything what is pointing to your compiz startup [thefuture.compiz-start.py]

On the middle tab of your sessions menu remove everything that points to your compiz [thefuture/compiz-start.py or what ever]

Now put the folowing in sessions starting apps   /usr/bin/compiz-start

Log out and login again and it should be working again.

You can configure your plugins with 'csm' in your terminal which starts a configuration app.

gsetcompiz can be removed because it's no longer in use anymore.

Hope this will help.

Thank you.  I'll try this when I am able, and will let you know what happens.

Take care.

---

### Post by djRobbieF on 2006-09-05
This really *is* awesome - thank you for such an easy to follow guide.

The only thing that was missing was adding other repositories to apt-get, but that was a breeze.

I feel like XGL is the answer to what I've always wanted my computer to act like.  I've been *longing* to have such gorgeous video effects, coupled with very fast speed.  This will make me so much more productive.  I am intending to virtualize a couple of the cube sides and add Windows XP and a full-screen eyeOS.

A few simple questions, as I've only been running XGL a few minutes  :)  :

- I have seen some users' video shots of XGL and they have skyboxes installed somehow.  Do you know how to do this?  (In otherwords, rather than the cube floating in darkness, it is floating in space, or in a sunny landscape)

- Is there a way to replace the Novell logo on the top and bottom with something of my own?  Even with another desktop, perhaps?  But more importantly, just getting rid of that Novell logo and putting a Ubuntu logo, or my company logo would be nice.

THANKS AGAIN - you made installing and running XGL so insanely EASY for me.

---

### Post by bulldog on 2006-09-05
Well you should have 'csm' as configuration tool.

Typr csm in your terminal and the re should be a tool coming up.
Go to Desktop Cube -> String Lists and you see your Novell pic.

Remove it and replace it with something you wish,a background pic or screenshot or whatever you like.

Walk to all the options of csm and see what you can change but be carefull and change only when you know what the plugin does,otherwise you get strange behavior and you won't know what you changed.

---

### Post by djRobbieF on 2006-09-05
Thanks bulldog - this utility is superb!  NICE.  And I found the skybox feature too.

Just in case anyone else flubs, I got the common "My title bars are gone" problem.  It turned out I simply forgot to apt-get compiz-gnome.  I fixed it, and now it's better.

I am officially running Ubuntu 6.06 with the 686-smp kernel, my wireless and all other hardware working, and XGL with Compiz and it's BEAUTIFUL and fast.  Plus, this is the first time I get to take advantage of the hyperthreading features of my processor, with the SMP extension!!

---

### Post by djRobbieF on 2006-09-05
Bulldog; none of the settings I make in csm stick; any ideas?  When I launch thefuture, I get an error couldn't load plugin 'gconf' - think that might have anything to do with it?  I'm at a loss.  Thanks!

UPDATE - NVM, I got it: I loaded using compiz-start instead, and everything looks great!

---

### Post by mcuerdo on 2006-09-06
> **7he said:**
> TO undo , just follow the guide:



After that you may have to reconfigure your Xserver
I did it with:   
```
 
sudo dpkg-reconfigure xserver-xorg

```

I did it as you told me, but I keep getting white screen. After booting I see a the brown screen and the clock... normally it should appear the login screen but I get the white one. Any ideas?

thks

---

### Post by suhaib on 2006-09-06
> **bulldog said:**
> The updates require some other compiz startup.

When everything worked before the updates try the folowing.

Go to preferences->sessions->startup apps and remove everything what is pointing to your compiz startup [thefuture.compiz-start.py]

On the middle tab of your sessions menu remove everything that points to your compiz [thefuture/compiz-start.py or what ever]

Now put the folowing in sessions starting apps   /usr/bin/compiz-start

Log out and login again and it should be working again.

You can configure your plugins with 'csm' in your terminal which starts a configuration app.

gsetcompiz can be removed because it's no longer in use anymore.

If the changes you make in csm don't stick do

chmod 755 ~/.compiz -R 

and it should.

Hope this will help.

Yeah everything is sorted now.  I only followed the first step though (changing the startup).  Thanks again.

---

### Post by tomBorgia on 2006-09-06
WOW!!!! thanks for the guide... worked like a charm! 

Watch out with the xmodmap! if u get it wrong then you´ll be typing gobledegook! go into the system>preferences>keyboard to sort it out!

Thanks again... this even impresses widoze junkies!:-D

---

### Post by geek777 on 2006-09-06
Hi Fellas,

I have xgl and compwiz working on my nvidia geforce 5500FX pci card with twinview and am generally impressed :cool: 

I have couple of small issues i can't work out how to resolve:

1. Windows positions with TwinView:

Certain windows (gconf-editor is one) go the the exact center of my twinview display...which is mid-way between my 2 19" Dell FP...due to the border of the two monitors....it is very hard to read and enter data when windows are positioned here...I am not able to dragg such app windows elsewhere....the gdm login propmpt is the same way...dead center of my 2 displays.

2. Panel spans both displays with TwinView:

I had TwinView working before compwiz & XGL in such a way as to only one display (display 0, on left) had the dock and panel...now, the dock and panel span both displays....

3. xmodmap /usr/share/xmodmap/xmodmap.us

Can this be set in a init.d runlevel startup script or something?  Shift-Backspace has KILLED me 3 times now.....usually at the tail end of a lengthy email ](*,) .  I know I will forget to run this command...so would love to set automagically.

I think I might be stuck with the above behavior due to the fact that compwiz needs to "see" both monitors as "one" larger display for work space rotation and such to work....the worst issue is application window positions which forced to front and when they can't be moved within the UI to a more readable location...versus dead center of two displays.


Any help greatly appreciated!

---

### Post by djRobbieF on 2006-09-06
With regards to autostarting the xmodmap command, just click System --> Preferences --> Sessions, choose the Startup Programs tab, and add the xmodmap command.

I also added **xmodmap -e keycode 22 = BackSpace** just in case.  That resolves the SHIFT+BackSpace problem.

I have unfortunately had no luck getting window positions to be automated in XGL / compiz yet.  I was hoping devilspie would do it, but no.  Neither will wmctrl.

I have hopes that the XGL *state* plugin / command will do it, but I have yet to figure it out.  Perhaps that will start you in the right direction?  If anyone figures it out, please post here so I can know  :)

---

### Post by jperez on 2006-09-10
I just installed it and had absolutely NO problems and the script provided on page one ran on the first try!  Thanks so much!  I can't wait to show it off to all my friends!

Jesse~

---

### Post by aaronbeekay on 2006-09-11
> **TeeAhr1 said:**
> I hope this hasn't been covered upthread (it probably has :roll: ), but 114 pages looked a little daunting.  Anyway, I got as far as reboot, whereupon the X server promptly puked on my carpet, leaving this (log file excerpt follows):
```
(EE) Failed to initialize GLX extension (compatible NVIDIA X driver not found)
Error opening security policy file /etc/X11/xserver/SecurityPolicy
(EE) xf860OpenSerial: Cannot open device /dev/wacom
no such file or directory
(EE) xf860OpenSerial: Cannot open device /dev/wacom
no such file or directory
*Note: six more of that, ending with a thud:*
Fatal server error:
no visual format found
```
I removed the gdm.conf-custom file, which got me back here.  But I am flummoxed.  Anyone know where to go from here?  Thx in advance, as always...

-pete

Same here. I'm running 3ddesk without a problem (GeForce 6600, proprietary drivers) and I followed the how-to, but I get the exact same security policy error.

Ack!

---

### Post by kwalo on 2006-09-11
I had to add```
        Option          "UseFBDev"              "true"
```To nvidia section in /etc/X11/xorg.conf. Xgl displayed strange things without it.

---

### Post by raintheory on 2006-09-13
Just so you know, this worked great on my Toshiba Satellite P15 S420 Laptop (nVIDIA GeForce FX GO 5100).

No problems or setbacks, works perfect!  

Thanks so much, I've already astounded my fiance who is a hard-core Mac user.  :)

---

### Post by memi on 2006-09-13
now how to switch back the kezboard form english to slovene:confused:

---

### Post by memi on 2006-09-13
OK...did it...TNX!

---

### Post by Waste on 2006-09-14
Hi, I have a couple of questions.
I was running nvidia-settings before using this to get mmy screen's brightness to not be so dark on my monitor. (Very good monitor, but it's a tad dark.)
Where and how can I change the brightness of my desktop as compiz has diabled all use of nvidia-settings.


Also, is there a way to make gdesklets work with this?
Currently the desklets show up above my windows.

---

### Post by encompass on 2006-09-14
I get this...

dlopen: /usr/lib/xorg/modules/xgl/libglx.so: cannot open shared object file: No such file or directory

I have setup my nvidia drivers with the envy script... which works well, but removes all your restricted stuff... but have tried this install later that puts all the drivers back, I have the restricted stuff installed now and acceleration.
But I get that error when setting up the system.  I little search shows that the file with problem is the /etc/gdm/gdm.conf-costum, I restored my backup and I am back.  Any ideas?
Nvidia fx5200 PCI btw I had to edit the PCI location so it would work properly too.  For all you pci card users.
Any ideas? I have had this working before.

---

### Post by ccerinojr on 2006-09-15
Has anyone else experience amarok not working because of xgl/compiz

---

### Post by David Valentine on 2006-09-16
Great guide!!!  I had only one issue with xorg.conf, which was that my BusID was set to 2:0:0 and had to stay there instead of changing to 1:0:0 as suggested.  Thanks!

---

### Post by brm on 2006-09-17
If you are annoyed by beginners' questions, please skip immediately to the next message.

1. A couple of hours of Googling and of scanning fora has not provided any answer to how to restore borders to windows. I installed XGL/Compiz uneventfully using Automatix Bleeder, but in the XGL session which it creates, windows have no title bar, no status bar, no min/max/close buttons and the customary KDE keyboard shortcuts (such as Alt-F3) do not work either.
2. As a complete newcomer to XGL/Compiz, (but not to Linux), I am interested in other readers' favourite articles on the functionality and benefits of XGL/Compiz. I have a system powerful enough to allow eye candy.

Thanks in advance.

---

### Post by totalnewbie on 2006-09-18
OMG i've read it all from 1 to last page, please i need help.

I've follewed the step by step and no luck i get some error like this
xuser@linuxbox:~$ thefuture
gnome-window-decorator: Screen 0 on display ":1.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.
xuser@linuxbox:~$ XGL Absent, assuming AIGLX
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
compiz: glXCreateContext failed
compiz: Failed to manage screen: 0
compiz: No manageable screens found on display :1.0

My video card is a fx550, running on ubuntu dd 6.06, please any help is really appreciated, thank you very much in advance.

After looking previous post i tried to do the automatix-bleeder install, rebooted selected Xgl on my session start and then did the toggle-compiz-nvidia command and i get this error now:

xuser@linuxbox:~$ toggle-compiz-nvidia
/usr/bin/toggle-compiz-nvidia: line 6: cgwd: command not found
xuser@linuxbox:~$ XGL Absent, assuming AIGLX
compiz: GLX_EXT_texture_from_pixmap is missing
compiz: Failed to manage screen: 0
compiz: No manageable screens found on display :1.0

:frown: ](*,)

---

### Post by Crooksey on 2006-09-18
Anyone know if this card is fully supported with XGL?

[http://www.novatech.co.uk/novatech/specpage.html?NOV-79GT](http://www.novatech.co.uk/novatech/specpage.html?NOV-79GT)

Or will i be able to run all the affects, without lag, 1GB ram and 3.6o GHZ 64bit HT, will that setup plus that gfx card leave me lagless?

---

### Post by brm on 2006-09-18
> **brm said:**
> 1. A couple of hours of Googling and of scanning fora has not provided any answer to how to restore borders to windows. I installed XGL/Compiz uneventfully using Automatix Bleeder, but in the XGL session which it creates, windows have no title bar, no status bar, no min/max/close buttons and the customary KDE keyboard shortcuts (such as Alt-F3) do not work either.
2. As a complete newcomer to XGL/Compiz, (but not to Linux), I am interested in other readers' favourite articles on the functionality and benefits of XGL/Compiz. I have a system powerful enough to allow eye candy.

Answers found:
1. use compiz-manager which has recently (within the last week) toggle-compiz-nvidia;
2. the following looks good: [http://en.opensuse.org/Compiz](http://en.opensuse.org/Compiz).

---

### Post by aleska on 2006-09-19
Thank you for the guide.  
While compiz seems to be running, I can flip the cube, wobbly windows, etc. I think I might have a problem.  When I run "thefuture" the following appears in my terminal
> XGL Present
compiz: Couldn't load plugin 'gconf'

Did I miss an update that didn't make it into the original post.  I read on compiz.net that compiz doesn't use gconf anymore but csm.  Is the code in the "thefuture" script supposed to be changed to reflect csm instead of gconf?
Also, I don't know if this is related, but changes I make in csm don't appear to work.  Specifically, I tried changing the skydome graphic and the graphic on top of the cube.  I make changes in csm, but they don't seem to work.  Did I need to logout and login again? 
Any advice aprpeciated.  Thanks!

---

### Post by dmichaels on 2006-09-19
i did everything correctly as displayed on the forum, i run an nvidia 5700. now i cant even get into my ubuntu desktop. i get past the boot session but then says xserver not found. install xserver or configure gdm. so now im stuck, and have no knowledgable way to get into ubuntu. i have to run ubuntu off the cd now just to get into these forums.

---

### Post by bananajams on 2006-09-19
I have a problem trying to use this guide. Everything works fine until this part of the instructions to install XGL

sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome

I get

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package compiz


I dont know what to do. I cannot move on. Any suggestions?

---

### Post by renxokuken on 2006-09-20
Hi there.

I have a problem with **rotating cube**. When i try to rotate the cube, the screnn just flicker and the workspace jumps here and there (not switching to the desired workspace). When I move my mouse to the left, right, top and bottom edge of my screen, the mouse cursor just stuck there and cannot be seen until I press the Escape key.

If I disable the cube and rotating cube plugin from the CSM, everything works fine and the workspace can be switched with sliding animation. However, the Alt+Tab window switcher somehow acts weird sometimes (some black strip flickering at the bottom).

I already tried so many how-tos and guides, and none had solve this problem. I already check my CSM settings and defaulted it back a few times, but still nothing change. The other plugin works great, except for the water and reflection, and blur...but I assume the plugins are yet to be stable, and seeing that it is disabled by default, so I wont bother bout that.

FYI, Im using ubuntu dapper with Nvidia GeForce2 400MX, 1G Ram and running on Pentium4.

My repos are set to these;
```
deb http://www.beerorkid.com/compiz dapper main
deb http://ubuntu.compiz.net/ dapper main
```

and also I have tried on these;
```

deb http://www.beerorkid.com/compiz dapper main
deb http://media.blutkind.org/xgl/ dapper main
deb http://ubuntu.compiz.net/ dapper main
```

still, it doesn't solve the problem.

My xorg.conf are set as follows;
```
[...]
Section "Module"

	# Load	"dri"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
	# Load	"GLcore"
    Load           "glx"
    Load           "extmod"
    Load           "freetype"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection
[...]
Section "Device"
    Identifier     "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
    Monitor        "Acer 77e"
    DefaultDepth    24
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    [...]
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
[...]
Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

If somebody could help me, I will be very gratefull.

Thanks a lot in advance.

---

### Post by kwalo on 2006-09-20
**renxokuken**, It looks like you're trying to use AIGLX with nvidia card. It's not supported yet.

Before you try to make any changes, make sure you have backup of your xorg.conf file.```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
Now try to change theese values. I marked them red```
[...]
Section "Module"

    [COLOR="Red"]Load	   "dri"[/COLOR]
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "glx"
    Load           "extmod"
    Load           "freetype"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection
[...]
Section "Device"
    Identifier     "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
    Driver         "nvidia"
[COLOR="Red"]#Set this option only if you have problems with Xgl[/COLOR]
[COLOR="Red"]    Option         "UseFBDev"        "true"[/COLOR]
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
    Monitor        "Acer 77e"
    DefaultDepth    24
[COLOR="Red"]    #Option         "RenderAccel" "true"
    #Option         "AllowGLXWithComposite" "true"[/COLOR]
    [...]
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
[...]
[COLOR="Red"]#Section "Extensions"
#    Option         "Composite" "Enable"
#EndSection[/COLOR]

```Now try to Install Xgl according to [this]("https://help.ubuntu.com/community/CompositeManager/Xgl")

---

### Post by bananajams on 2006-09-20
Hey kwalo, I have an Nvidia 6600GT, will it still work?

---

### Post by madc on 2006-09-21
omg, it's working...!:p 
so, this is my xorg.conf file...nvidia FX5600...


# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"ctrl:nocaps"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV31 [GeForce FX 5600]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"RenderAccel"	"true"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
	HorizSync	30-71
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV31 [GeForce FX 5600]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection


it's working "out of the box"...so, i think it will be helpfull for someone!;) 
brgds from croatia!

---

### Post by madc on 2006-09-21
wow...this can't be true....

look at my "glxgears" before the cube...
11358 5.0=2273.510
11345 5.0=2267.676

and now with the cube....
18760 5.0=3723.020
19608 5.0=3439.451...

wtf? is that ok?
for me, it's working perfectly...:p

---

### Post by louis_nichols on 2006-09-22
> **madc said:**
> wow...this can't be true....

look at my "glxgears" before the cube...
11358 5.0=2273.510
11345 5.0=2267.676

and now with the cube....
18760 5.0=3723.020
19608 5.0=3439.451...

wtf? is that ok?
for me, it's working perfectly...:p

It is correct. I get the same. Looks pretty amazing, but hey! I ain't complainin'! :D

---

### Post by totalnewbie on 2006-09-22
Yeah mine is working now i made this changes to thefuture script and now it loasd everything:

```
#!/bin/bash
cgwd &  compiz --replace dbus csm decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &
```

i had to add dbus so skydome works.

---

### Post by gogogo111 on 2006-09-23
I need help. Fast.

I did exactly what this guide said (the ubuntu forums one) and when i restarted, and did the command, then "thefuture", my windows screwed up. They dont have a top anymore. No minimize, maximize, or close, no info about it. I cant drag anything (cant do it with alt + mouse either). 

luckily i had the terminal open. it said cant find plugin gconf. I did 

sudo apt-get install gconf

Installed it, tried thefuture again, and didnt work, saying coudnt find plugin gconf. Please help!!!

---

### Post by gogogo111 on 2006-09-23
Ok i just restarted X and it got me back to normal. However, It still does it when i type thefuture.


Any help on this? Here is my xorg.conf:
EDIT: I am following the other guide now since I didn't read the "This guide is old, use this one instead!"

So this is the one Im using

[http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit)

I am at the part where you have to 
```

sudo apt-get install xserver-xgl compiz-gnome cgwd cgwd-themes csm

```

But it says this...

```
matt@matt-desktop:~$ sudo apt-get install xserver-xgl compiz-gnome cgwd cgwd-themes csm
Reading package lists... Done
Building dependency tree... Done
xserver-xgl is already the newest version.
compiz-gnome is already the newest version.
Package cgwd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package cgwd has no installation candidate
matt@matt-desktop:~$
```


What do I do from there? :confused:

---

### Post by mesh on 2006-09-24
Howdy,

I followed the guide and now i cant stop moving windows around and rotating throught the various desktops :D. The only thing i find strange is that when i open **gconf-editor i dont see apps > compiz** . Anyone know why? When i initially ran thefuture i received an error, but i just rebooted and everything seems to be working fine. When i run thefuture now, i just get a msg saying its already running. Anyway.  Anyone have any idea why i dont see apps > compiz? Thanks again for this guide, im lovin' this :D. Peace and thanks in advance to all who help.

UPDATE: I found compiz. The reason i couldnt find it is becuase i ran gconf-editor with as SU. I guess it tied to your profile.

---

### Post by eraser_rx on 2006-09-24
> **gogogo111 said:**
> Ok i just restarted X and it got me back to normal. However, It still does it when i type thefuture.


Any help on this? Here is my xorg.conf:
EDIT: I am following the other guide now since I didn't read the "This guide is old, use this one instead!"

So this is the one Im using

[http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit)

I am at the part where you have to 
```

sudo apt-get install xserver-xgl compiz-gnome cgwd cgwd-themes csm

```

But it says this...

```
matt@matt-desktop:~$ sudo apt-get install xserver-xgl compiz-gnome cgwd cgwd-themes csm
Reading package lists... Done
Building dependency tree... Done
xserver-xgl is already the newest version.
compiz-gnome is already the newest version.
Package cgwd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package cgwd has no installation candidate
matt@matt-desktop:~$
```


What do I do from there? :confused:

well..it's clearly written

```
Package cgwd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
```

they removed the pakages because they are working on the new release for 6.10

---

### Post by manwanis on 2006-09-27
took me a lot to read...

---

### Post by drdaz on 2006-09-28
> **eraser_rx said:**
> well..it's clearly written

```
Package cgwd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
```

they removed the pakages because they are working on the new release for 6.10

You managed not to answer his question. So if you're looking to install right now, you can't? Or is there another repo?

/drdaz

---

### Post by Eleka on 2006-09-28
Hi people!

I have a little problem upgrading my compiz packages from the repos. On my system I have installed the compiz-core package version 0.0.13.52, but in the repo the latest one is 0.0.13.38. I have installed that package with apt-get or update-manager ... it means that it were a downgrade of one version for some reaseon that I don't know?

The last is that I can't upgrade the compiz-plugins package because my compiz-core version is OLD ... and the repository version is older than mine ...

Somebody have the same problem?

---

### Post by LostJot on 2006-09-28
Is it (essentially) impossible to install xgl offline? All I see in all the instructions is lines of repositries and apt get commands, so I'm assuming it would be near enough impossible.

---

### Post by kellykamay on 2006-09-29
this is the error i get after running thefuture

(gnome-window-decorator:6250): Gdk-WARNING **: locale not supported by Xlib

(gnome-window-decorator:6250): Gdk-WARNING **: cannot set locale modifiers
gnome-window-decorator: Screen 0 on display ":0.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.
compiz.real: Couldn't load plugin 'gconf'
compiz.real: Couldn't load plugin 'decoration'
compiz.real: Couldn't load plugin 'wobbly'
compiz.real: Couldn't load plugin 'fade'
compiz.real: Couldn't load plugin 'minimize'
compiz.real: Couldn't load plugin 'cube'
compiz.real: Couldn't load plugin 'rotate'
compiz.real: Couldn't load plugin 'zoom'
compiz.real: Couldn't load plugin 'scale'
compiz.real: Couldn't load plugin 'move'
compiz.real: Couldn't load plugin 'resize'
compiz.real: Couldn't load plugin 'place'
compiz.real: Couldn't load plugin 'switcher'

how will i solve this?..pls help..thanks

---

### Post by vinodmenon on 2006-10-01
My Laptop is a Dell Inspiron 510m and i have a dual boot system. My Laptop specs are follows:

Features/Specs: Pentium M 1.6GHz; 512MB RAM; 15in screen; 64MB shared Intel Extreme Graphics 2; 60GB hard drive; DVD-RW/CD-RW

If i want to get XGL to be installed on it, would it work? My system is up to date with the latest patches.

Any Ideas?

---

### Post by kwalo on 2006-10-03
**kellykamay**, looks like you didn't install compiz-plugins package.

**vinodmenon**, you should try AIGLX instead of Xgl. AIGLX should be better. Check [Ubuntu Wiki]("https://help.ubuntu.com/community/CompositeManager") for more details.

Check what kind of driver your card uses. Use the following command```
grep Driver /etc/X11/xorg.conf
``` There should be a driver like i830, or i915 (starting with i for certain) and take a look at [what cards](http://fedoraproject.org/wiki/RenderingProject/aiglx#head-43a98eb9adc0264c802bf5918f1cc57bddbbc129) AIGLX works with.

---

### Post by dreadhead90 on 2006-10-18
hmm... some of my windows are missing boarders... anyone know what to do about it???

---

### Post by DSn0wMan on 2006-10-18
I am not sure why it happens, but for me it happens all the time with amaroK while beryl is running. It did the same thing with compiz.

---

### Post by dmorlow on 2006-10-24
I have an HP DV4000 laptop that has an Intel video card in it.  I did the instructions on the website and it's working but my computer is now dawg slow.  I have a bar at the bottom (kxdocker), and that now appears as just jibberish lines and cannot be used anymore.  Minimizing windows and moving stuff around the screen goes terribly slow.  The computer is a P4 2 GHz with 1 GB RAM.  It should go a little faster. I think the acceleration for video isn't working.

BTW, I attached a screenshot so you can see what my desktop looks like right now.

---

### Post by dmorlow on 2006-10-24
I'm having a problem where after I applied the steps, my OS now is going extremely slow and the bottom bar I had to mimic the bar in OS X and in Vista, is all black horizontal lines.  I think the video acceleration is not enabled.  I have a DV4000 laptop with an Intel video card.  How do I fix this?  The computer (like I said in my last post) is a P4 2 GHz with 1 gig of ram.  It should be able to do a lot better.

P.S. I put a screenshot below so you can see what my screen looks like...

Thanks,

David

---

### Post by neo4386 on 2006-11-08
Hei guyz thanks for your replies! The problem on my configuration was because of some bogus keyboard configuration and tried to remove xmodmap from my startup and everything just worked. Made use of your suggestions though...

---

### Post by siaush on 2006-11-09
Hi, if I followed the guide on [http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit)

How can I uninstall/undo it if I wanted to?

---

### Post by bobp0303 on 2006-11-18
[QUOTE=poofyhairguy;739831][B]My guide is REALLY outdated. Instead use this site:

[http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit)

Thank you![/B]



Hello Nvidia Users. If you are a ATI user then please use this guide instead:

...

I created a simple file called /usr/bin/thepast with the following contents:

```

#!/bin/bash
gnome-window-decorator & compiz --replace compiz.real decoration &

```

It reverses the effect of thefuture -- obviously you have to edit, create, and set the executable bits via

```

sudo chmod +x /usr/bin/thepast

```
but having done so, you can now swap back and forth between the two effects.  Dunno if you get your memory back though...

Bob.

---

### Post by mgimera on 2006-11-21
I had this running like a charm in 6.06, then I did a fresh install of Edgy. -formatted drive etc.

Now when I try to run 'thefuture' I get:
gnome-window-decorator: Screen 0 on display ":0.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No manageable screens found on display :0.0

I've done the gconf-config suggestions.
I don't understand the error; 'thefuture' uses the --replace option... so what's this stupid error talking about?

---

### Post by vangos on 2006-12-07
I was able to successfully install XGL as per the  [http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit) guide. Everything looks great, I am impressing everybody around the house, and suddenly as I am moving some windows around, I get a white screen. The system is still active as  I can reboot the X server (with ctrl+alt+bksp). But when I relogon, I get the white screen. I somehow got myself in a console and I was able to change the X-Gnome-autostart-enabled=false in the beryl-manager.desktop file, so that I can at least get into my wm so I can work. Looks like something in the beryl-manager settings (or something related) got messed-up, because every time I invoke it by running beryl-manager I get the same white screen. In the meantime I accepted several  updates that were recommended by the update manager (which included several x-related modules as well as a couple compiz related updates). Also I reinstalled the beryl-manager, but I am still getting the "white screen". I saw in the xsessionserrors file multiple redirection errors initially. Then later as I made all the changes I am getting a compiz.real crash.

Anybody had the same problem? Can someone point me to a direction so I can restore my XGL. I know it can work with my NVIDIA 5200 card. My system is the 6.10 Edgy. It is setup on a dual PIII 1 GHz old Dell system.

Thank you in advance

Evangelos

---

### Post by M0nk3yM4n on 2006-12-09
Hey guys I messed up.. ](*,) 

I'm a pretty new user and I thought I could do this and I followed all the instructions but now I'm SOL I think...

So now I start Ubuntu and it gets to the loading screen then it goes to a black screen and prints out

Buffer Error I/O device sdb2 partition 
multiple times...

Then it goes to this blue and red screen and says that it failed to start the X server because it is probably no set up correctly (well thank you computer), It says view server output? yes/no? then I say yes and it says in the text...

Fatal: Error running install command for Nvidia.
Failed to load the Nvidia kernel module!
***Aborting***

No Screens found.

Then it says if I want to see the xserver advanced output then I say no and then it's just a black screen with nothing but I can type stuff...

What do I do? Is there anyway to revert back to just normal Ubuntu? Or is it easier to just keep going forward and configure XGL properly? 

Help me!

---

### Post by mo_roodi on 2007-02-01
Ok I need some help please. 

I'm a complete newb! I've followed this How-To to the letter and everything seems to have gone very smoothly, except when I try to start compiz I receive the error 
```
gnome-window-decorator: Screen 0 on display ":0.0" already has a decoration manager; try using the --replace option to replace the current decoration manager 
```.

I'm sorry if this has already been answered, I've been looking of hours but to no avail. 

Please help!

Thanks,
Mo

---

### Post by asistentu on 2007-03-30
I find it awful to search a quick answer to my question. You should open another thread with only the essentials. :lolflag:

---

### Post by hyperair on 2007-04-22
[quote=M0nk3yM4n]
Hey guys I messed up..

I'm a pretty new user and I thought I could do this and I followed all the instructions but now I'm SOL I think...

So now I start Ubuntu and it gets to the loading screen then it goes to a black screen and prints out

Buffer Error I/O device sdb2 partition
multiple times...

Then it goes to this blue and red screen and says that it failed to start the X server because it is probably no set up correctly (well thank you computer), It says view server output? yes/no? then I say yes and it says in the text...

Fatal: Error running install command for Nvidia.
Failed to load the Nvidia kernel module!
***Aborting***

No Screens found.

Then it says if I want to see the xserver advanced output then I say no and then it's just a black screen with nothing but I can type stuff...

What do I do? Is there anyway to revert back to just normal Ubuntu? Or is it easier to just keep going forward and configure XGL properly?

Help me![/quote]

Which instructions did you follow? If you by chance installed nvidia-glx-new and then replaced it with nvidia-glx it may have left a file (/lib/linux-restricted-modules/.nvidia_new_installed). Delete that file (sudo rm /lib/linux-restricted-modules/.nvidia_new_installed). Then restart your system. It should work  I think.

---

### Post by GvsE on 2007-04-22
Should i use this guide witch was posted in first page to install xgl on my ubuntu feisty or is it out of date?

---

### Post by glenby on 2007-04-24
Gnome and general speed difference is awesome - but in my case problematic.
I'm running feisty - amd 2500+ 1gb ram nvidia 6600gt.

Was running standard xserver - crossgraded to xgl - everything in foreground runs fast.
3 or 4 times faster - sounds nice except that cpu is constantly maxed out and
any background apps stutter - the gimp is appalling even in foreground.
Typing this is maxing my cpu - goes from 2 to 3% load to 100% just typing.:( 

any ideas on how I can balance things out a bit?
I did a search around but cannot find the correct terminology to get a decent hit.

many thanks.


==============NOTE===============

I had turned off GL Deskctop in preferences to avoid compiz problems.
once re-enabled - works great. awaiting compiz problems.


will see how it goes now.

---

### Post by VoiceOvGod on 2007-06-25
And how is this done in KDE?

---

### Post by sayad on 2008-02-29
> **GvsE said:**
> Should i use this guide witch was posted in first page to install xgl on my ubuntu feisty or is it out of date?

well i used the guide...but i still have the same question...
thanks




--
[Webkinz Recipes](http://www.thewebkinzblog.com)

---

### Post by CyberAgeVoodoo on 2008-04-28
I've run "thefuture" over 20 times and this is what I get:

```
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: freedesktop
/usr/bin/compiz.real (core) - Warn: Plugin 'core' already active
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

---

