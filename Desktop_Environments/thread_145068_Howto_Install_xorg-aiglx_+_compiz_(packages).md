---
title: "Howto Install xorg-aiglx + compiz (packages)"
date: 2006-03-15
forum: Desktop Environments
---

### Post by gandalfn on 2006-03-15
Howto Install xorg-aiglx + compiz (packages)

To install compiz on aiglx in dapper :

[Howto compiz + aiglx on dapper]("http://gandalfn.wordpress.com/howto-compiz-aiglx-on-dapper/")

to install compiz on aiglx in edgy :

[Howto compiz + aiglx on edgy]("http://gandalfn.wordpress.com/howto-compiz-aiglx-on-edgy/")

[COLOR="Red"]Warning !! compiz-quinn-aiglx and compiz-vanilla-aiglx are now deprecated ! 
[Gnome Compiz Manager]("http://gandalfn.wordpress.com/gnome-compiz-manager/") replace them ![/COLOR]

to migrate on it, you may remove first compiz-quinn-aiglx :

> sudo aptitude purge compiz-quinn-aiglx

or compiz-vanilla-aiglx:

> sudo aptitude purge compiz-vanilla-aiglx

and install gnome-compiz-manager :

> sudo apt-get install gnome-compiz-manager

Have fun

EDIT: 06/03/2006 
- add Composite options in xorg.conf configuration (thanks jstueve)

update compiz-aiglx 0.0.6-ubuntu2 packages
- resync with new compiz debs from ubuntu forums (compiz-0.0.6-0ubuntu7) 
- add opacity plugins in package
- add compiz-aiglx-kde package

EDIT 16/03/2006
update xserver-xorg-air_0.99-ubuntu3
- suppress buggy libmesa-aiglx packages and dependencies don't need (thanks Jeff250)
- modify xorg config to break dri 
- add patched xserver-xorg-driver-ati

EDIT 16/03/2006
- add forgot module listin xorg configuration

EDIT 20/03/2006
update compiz-aiglx 0.0.7 ubuntu1
- resync with new compiz debs from ubuntu forums (compiz-0.0.7-0ubuntu1)
- add LIBGL_ALWAYS_INDIRECT=TRUE in start aiglx (thanks Jeff250)
- replace vi by gedit (old user practice ;) )

EDIT 25/03/2006
update xorg-air 0.99.1
- resync xorg-air with lasted cvs snapshot which include some bug fixes, optimisation and security fix 
- mesa-aiglx-sources depends is removed this package is now obsolote
- to rebuild xorg-air from source you need this packages 
[x11proto-gl-dev_1.4.6-0ubuntu1_all.deb]("http://gandalfn.club.fr/ubuntu/x11proto-gl-dev_1.4.6-0ubuntu1_all.deb")
[x11proto-composite-dev_0.3-0ubuntu1_all.deb]("http://gandalfn.club.fr/ubuntu/x11proto-composite-dev_0.3-0ubuntu1_all.deb")
[x11proto-fixes-dev_4.0-0ubuntu1_all.deb]("http://gandalfn.club.fr/ubuntu/x11proto-fixes-dev_4.0-0ubuntu1_all.deb")
update compiz-aiglx 0.0.7 ubuntu2
- resync with the fantastic quinn compiz packages ;)
- compiz-aiglx-start script is now in package it's automatically started in gnome startup session to disabled it remove /etc/xdg/autostart/compiz-aiglx.desktop file
- patched gnome-session is now needed by compiz-aiglx-gnome
update xserver-xorg-driver-ati 
- rebuild with aiglx dri init patch

EDIT 25/03/2006
update compiz-aiglx 0.0.7 ubuntu3
- add a sleep 2 to make sure gnome-window-decoration-aiglx is started before compiz-aiglx

EDIT 28/03/2006
update compiz-aiglx 0.0.7 ubuntu4
- resynchronise with quinn compiz 0.0.7 ubuntu11 package
- improved compiz-aiglx-start script with notification area configuration tool to activate plugins (screenshots attached)

EDIT 31/03/2006
update compiz-aiglx 0.0.7 ubuntu6
- resynchronise with quinn compiz 0.0.7 ubuntu13 package
- water plugin is desactivated for now, not work with aiglx :(
update xorg-air 0.99.1 ubuntu2
- sync CVS HEAD
- comment GLcore module, it can crash X if not have latest DRI driver

EDIT 08/04/2006
update xorg-air 0.99.1 ubuntu3
- fixes some bugs and memory leaks
WARNING !! use only official libgl1 debs with it
update gnome-session 2.14.0 ubuntu3
- rebuild latest gnome-session deb with logout_no_grab patch to prevent hang   in logout
update xserver-xorg-driver-ati_6.5.7.3 0ubuntu5
- build latest package with radeon-prefer-db-visuals patch
update compiz-aiglx 0.0.9 ubuntu1
- resync with latest official compiz
- rework of compiz-aiglx-change patch now compiz-aiglx use copySubBuffer to refresh region (minor performance improvenement)
- remove of quinn patch for now
EDIT 08/04/2006
update compiz-aiglx 0.0.9 ubuntu2
- resync with quinn package (thanks very much iXce)
EDIT 18/04/2006
update xorg-air 1.0.99.2 ubuntu2
- resync with xorg server-1.1 branch
- mesa 6.5 is now needed to work
- cvs mesa kernel module are needed too
add xserver-driver-i810 1.6.0 ubuntu1
- needed to work with latest compiz-aiglx
update compiz-aiglx 0.0.9 ubuntu3
- resync with quinn package
- rework of compiz-aiglx to work with latest compiz
- add accelerated-indirect-rendering option 
update gnome-session 2.4.1 ubuntu3
- resync with latest ubuntu package

EDIT 02/05/2006
All compiz-aiglx are now deprecated, meta package compiz-vanilla-aiglx replace them. it's integrate a new compiz-start script (screenshots attached).
Add firefox hang tip (thanks Permafrost91)

EDIT 03/05/2006
xgl.compiz.net repos really updated with xorg-air 1.0.99.902 ubuntu02
- rework of aiglx-compiz patch to conform latest tfp spec
- 24 depth rework now with compiz-vanilla

EDIT 17/05/2006
xorg-air 1.0.99.903
- copy sub buffer support added
- firefox hang resolved
linux-dri-modules 
- new dri modules packages
- suppress dri modules compilation howto
compiz
- add compiz-quinn-aiglx install
- suppress firefox howto

EDIT 08/06/2006
linux-dri-modules 20060606:
xserver-xorg-drivers-ati 6.6.0:
good news aiglx compiz work now on ati radeon graphic card !

EDIT 28/08/2006
redirected on my blog howto.
add edgy howto
compiz-quinn-aiglx and compiz-vanilla-aiglx deprecated, gnome-compiz-manager replace it !

---

### Post by jstueve on 2006-03-15
I got this to work... compiz effects are very stable on my i855gm, no flickering at all.

Videos in totem don't work, get a glimpse and then a black screen.

also don't mixup compiz packages, the XGL compiz (compiz-real packages from this forum) ends up drawing any bitmaps upside down and backwards (which is sort of a neat effect, really... DaVinci would love it!)

Good how-to, thanks.

I didn't do a start up script, but added the compiz-aiglx and gnome-window-decorator-aiglx into my .gnomerc and it worked fine (after I fiddled with using the correct compiz to start-up)

---

### Post by bijoux on 2006-03-15
EDIT: hehe.. nevermind ^


[IMG]http://angelface.servebeer.com/Screenshot.png[/IMG]


thanks again - bijoux

---

### Post by jstueve on 2006-03-15
another thing that works with aiglx that didn't with xgl:

glxgears actually shows gears spinning (always was a black box before)

> glxgears -printfps
3377 frames in 5.1 seconds = 665.470 FPS
3472 frames in 5.2 seconds = 669.511 FPS
3460 frames in 5.2 seconds = 670.507 FPS


Not a bad fps for my card, IIRC 720fps is normal under Xorg for me.

However, Direct rendering is still not happening.  (under xorg it is enabled, under Xgl it isn't)

> $ glxinfo | grep direct
direct rendering: No


Testing games...

---

### Post by saads on 2006-03-15
any thoughts on how this compares to xgl?  Will it work on NVidia cards - i read somewhere that nvidia doesn't work under aiglx

---

### Post by jstueve on 2006-03-15
okay updates on video:
mplayer worked fine, so I replace totem-gstreamer with totem-xine and viola, real working video, even full screen.  

In XGL-compiz I could get it, but it would lag horribly unless i did half-resolution, then it would work fine, even on the edge of the cube. 

in AIGLX-compiz it works even in full screen (it doesn't bend around the corner of the cube, it just blanks the screen...) audio is mostly sync'd, just a tad bit off... might be the encoding though.

wobbly works really smooth, the cube spinning is really smooth
Expose/switch is much smoother than XGL

Things I can't get to work:
- opacity isn't working.
- expose, switch with a video disconnects from the running video... the video updates, but doesn't scale down to the new window, to the effect is a window into the running video, and blue screen for parts of the screen that don't have the video playing.

---

### Post by elanthis on 2006-03-15
For those of you using proprietary drivers, I'd like to note that AIGLX will not be usable with your drivers until sometime after X.org 7.1 is released and new drivers are released.

X.org 7.1 is breaking compatibility with binary modules.  The open source drivers included with X.org will work fine, but binary drivers need small changes made in order to work with the new X server.

It is possible that this change is why NVIDIA isn't releasing new drivers within the next few weeks, but that's purely speculation.  It's also quite likely that NVIDIA is waiting for the XGL/AIGLX extension chaos to settle down so that they only need to release one version of the new GLX extensions those servers use.

Also note that this change will somewhat affect XGL, too; if Ubuntu upgrades to X.org 7.1 before new proprietary drivers are out, XGL will also break, since XGL uses the native X.org server for driver interfacing.  XGL will continue to run on top of X.org 7.0 and the current drivers, of course.

---

### Post by jstueve on 2006-03-15
[QUOTE=saads]any thoughts on how this compares to xgl?  Will it work on NVidia cards - i read somewhere that nvidia doesn't work under aiglx[/QUOTE]

Somethings work much better than XGL on my intel card.  But on XGL things on the video card were wonky in places (mostly from a lack of direct rendering).

AIGLX handles this better (glxgears actually showing up, videos playing in full resloution) but drops some of the keen compiz effects (video running while doing 3D effects, opacity...  

hmmm... lemme try something.

---

### Post by elanthis on 2006-03-15
> expose, switch with a video disconnects from the running video... the video updates, but doesn't scale down to the new window, to the effect is a window into the running video, and blue screen for parts of the screen that don't have the video playing.

You'll likely notice a similar effect if you drag a video window around really fast, on Linux or Windows.

This is because you are still using Xv instead of OpenGL to render the video.  The advantage is fully accelerated hardware video decoding.  The disadvantage is that compiz can't muck around with the video content, because it's going straight from the video decoder to your monitor.

Try running with OpenGL output in your video player (any of the bazillion XGL howtos should explain how to do that) and see if it works.

(Can't test myself, being an NVIDIA user.  Have to wait for X.org 7.1 and the next NVIDIA driver release.  ~_^ )

---

### Post by DeeZiD on 2006-03-15
@elanthis:
I don't have any problems with xv when wobbling, scaling or zooming under Xgl with the latest nvidia-driver.

I works really nice. There is only one problem. Xv Sync to Vblank doesn't work with it.


regards Dennis

---

### Post by jstueve on 2006-03-15
video.driver.opengl in totem_config breaks totem

Also opacity isn't working.   libopacity is missing from /usr/lib/compiz

In xorg.conf you must have:
```

Section "Extensions"
        Option  "Composite" "Enable"
EndSection

```
is required.

---

### Post by jstueve on 2006-03-15
using the libopacity.so from the file in [this thread]("http://ubuntuforums.org/showthread.php?t=132063&highlight=opacity+XGL") made it work.

---

### Post by DeeZiD on 2006-03-15
Opacity is already included in latest cvs. So compiz doesn't require it.
But you have to use the following command now (which is not configureable).

Alt+Mousewheel


regards Dennis

---

### Post by aamukahvi on 2006-03-15
I have a R8500 on my 2nd computer and it refuses to run Xgl+Compiz with fglrx and open drivers too, I think. Does Xair work with radeon driver?

---

### Post by jocko on 2006-03-15
[QUOTE=DeeZiD]Opacity is already included in latest cvs. So compiz doesn't require it.
But you have to use the following command now (which is not configureable).

Alt+Mousewheel


regards Dennis[/QUOTE]

It is configurable... in gconf-editor browse to /apps/compiz/general/screen0/options

---

### Post by DeeZiD on 2006-03-15
ahhh, thanks for the info :)

---

### Post by dentaku65 on 2006-03-15
I've install all the deb but I'm on KDE.
The AIGLX works fine directly from kdmrc
but when I launch compiz the screen became completely blank-white :confused: 
...and even if I kill the gnome-window-decorator then swithing back to AIGLX I loose the kde default window decoration, all my windows are only with menus and application, no upper window decoration.
Maybe I have to wait for kde compiz [-(

---

### Post by elanthis on 2006-03-15
> I don't have any problems with xv when wobbling, scaling or zooming under Xgl with the latest nvidia-driver.

XGL doesn't use *any* of the host X.org server's 2D drivers.  That includes the hardware accelerated Xv driver.  All of XGL's 2D rendering is done over OpenGL.  The hardware video decoder is completely unused under XGL.

In XGL, when an application uses Xv, it's basically just using OpenGL, except instead of the application using OpenGL itself, the app instead is having XGL do it.

The same goes for all other 2D drawing.  You can use XGL and have all your apps automatically render using OpenGL, *or* you can use a Cairo-based toolkit (like gtk+) with glitz (the library which backs XGL), or another OpenGL-capable toolkit like Qt4, and get the exact same OpenGL acceleration that XGL gives you, but applications will be able to directly access the DRI drivers and should get better over-all performance.

X.org+AIGLX doesn't force all rendering through OpenGL, so things like Xv still work like they used to using the good old hardware video overlay, and normal 2D acceleration, *and* allows apps to use OpenGL and allows accelerated indirect rendering.

So far as DRI, I believe that drivers must support the GLX_EXT_texture_from_pixmap extension before AIGLX will be able to support compositing and DRI at the same time.  Another cool thing about AIGLX that XGL fans should love is that the AIGLX work merged with XGL might even allow DRI to work under XGL.

---

### Post by elanthis on 2006-03-15
> I have a R8500 on my 2nd computer and it refuses to run Xgl+Compiz with fglrx and open drivers too, I think. Does Xair work with radeon driver?

Short answer: yes.

Long answer: yes, but whatever problem you ran into with XGL/Compiz could also affect Xair/Compiz.

---

### Post by gandalfn on 2006-03-15
> Maybe I have to wait for kde compiz
I 'll just updated compiz kde package ;-)
> 
but when I launch compiz the screen became completely blank-white


do you add the AIGLX in corg.conf ServeurLayout section ?

---

### Post by jstueve on 2006-03-15
thanks for the updated devs.

---

### Post by mstlyevil on 2006-03-15
This should be stickied by the Dapper Mods.

---

### Post by vendetta red on 2006-03-15
[QUOTE=elanthis]XGL doesn't use *any* of the host X.org server's 2D drivers.  That includes the hardware accelerated Xv driver.  All of XGL's 2D rendering is done over OpenGL.  The hardware video decoder is completely unused under XGL.

In XGL, when an application uses Xv, it's basically just using OpenGL, except instead of the application using OpenGL itself, the app instead is having XGL do it.

The same goes for all other 2D drawing.  You can use XGL and have all your apps automatically render using OpenGL, *or* you can use a Cairo-based toolkit (like gtk+) with glitz (the library which backs XGL), or another OpenGL-capable toolkit like Qt4, and get the exact same OpenGL acceleration that XGL gives you, but applications will be able to directly access the DRI drivers and should get better over-all performance.

X.org+AIGLX doesn't force all rendering through OpenGL, so things like Xv still work like they used to using the good old hardware video overlay, and normal 2D acceleration, *and* allows apps to use OpenGL and allows accelerated indirect rendering.

So far as DRI, I believe that drivers must support the GLX_EXT_texture_from_pixmap extension before AIGLX will be able to support compositing and DRI at the same time.  Another cool thing about AIGLX that XGL fans should love is that the AIGLX work merged with XGL might even allow DRI to work under XGL.[/QUOTE]

What I am getting from this is that with AIGLX I wouldn't be able to watch a movie and wobble the window around with it still playing perfectly, is that correct? I sure hope not, I like having fully accelerated video.

---

### Post by elanthis on 2006-03-15
> What I am getting from this is that with AIGLX I wouldn't be able to watch a movie and wobble the window around with it still playing perfectly, is that correct? I sure hope not, I like having fully accelerated video.

I figured this would be easy to figure out from the explanation provided, but since it apparantly isn't, let me spell it out more clearly:

Set your video player (gstreamer/xine) to use an OpenGL output driver and things will work identically under AIGLX as they do under XGL.

---

### Post by jstueve on 2006-03-15
[QUOTE=vendetta red]What I am getting from this is that with AIGLX I wouldn't be able to watch a movie and wobble the window around with it still playing perfectly, is that correct? I sure hope not, I like having fully accelerated video.[/QUOTE]

yeah, currently in Aiglx, the videos don't wobble, or change opacity, or wrap around the cube :/  but it is much faster (for all the reasons above, not having sv stuff go through OpenGL calls...) than my experience with XGL (which worked, but videos would only play at half-resolution (though they would wobble, and opaque) 

I can't get any video players to use openGl (gl or gl2) and still play a movie, and flightgear isn't playing at all...

Can anyone point me to a place to make the xserver setable be session?  Like normal login Aiglx, another session for XGL and yet another for normal Xorg with DRI enabled (for 3d games).  

On my 700m Dell there isn't one setup that will work completely.  (Intel  855GM)  I'll have to wait for fully accelerated drivers to get everything working right.

---

### Post by setenza on 2006-03-15
Hi,

Anywhere have recorded a video from there desktop on a successfull install of AIGLX ?

---

### Post by vinbuntu on 2006-03-15
I think this should be the official compiz on intel integrated graphics thread.  It works beautifully.  Thank you, and I second that this should be a sticky.

---

### Post by idlewild on 2006-03-15
Thanks to the packagers and devs, XP now looks archaic. All effect render at a good rate including wobbly which I had to disable on Xgl. All this on a lowly 855gm.
For the video playback, opengl would not work for me so for wobbly windows and other effect I went with xshm.

There is one very annoying bug where if I switch to another terminal (eg. ctrl+alt+1) then when I switch back I just get a black screen and can no longer switch back to another terminal so it requires me to hard reset.

Also opengl apps run at only a couple fps and flicker. Is there anything I can do to improve the performance?

Thanks

---

### Post by Hobbes on 2006-03-15
I agree that this should be stickied, then all those laptop (with intel graphics) wielding forum goers can also share in the compiz experience.

Crazy how one minute I (maybe it was just me) am thinking to myself that the Linux Desktop was dearly lacking in the eye-candy department, then seemingly out of nowhere this new Xorg drops and more and more eye-candy is coming by the minute. Sweet.

---

### Post by jstueve on 2006-03-15
:x

xshm --- ahhh.. now video works...  lol...  couldn't make out what the settings were on the first page...

---

### Post by no1wantdthisname on 2006-03-16
Wow, works much better than Xgl for my laptop's i915 video card.  Thanks.
Small question though, any way to enable dri?

---

### Post by zAo on 2006-03-16
Great! Gonna try this later today :)

---

### Post by poofyhairguy on 2006-03-16
Very Nice! I'm glad this was produced, as I hoped for this solution to turn up eventually. Good job.

Now I must ask...anyone have this working with the "radeon" driver? I have a 256mb 9200 thats itching to try to flip the cube!

---

### Post by the_maassk on 2006-03-16
I followed the method to the dot and here is what I get when I run the script:

$ /usr/bin/gnome-window-decorator-aiglx, Failed to load shadow images
/usr/bin/compiz-aiglx: No composite extension

I know I'm missing something stupidly simple! I've added the "Extensions" section to xorg.conf. What can be wrong?

---

### Post by aamukahvi on 2006-03-16
[QUOTE=poofyhairguy]Now I must ask...anyone have this working with the "radeon" driver? I have a 256mb 9200 thats itching to try to flip the cube![/QUOTE]
I haven't seen anyone claim this but I have a 8500 and would like to try this since Xgl+Compiz+fglrx kills my card. Maybe I'll try it today. Elanthis thinks this should possibly work :p

---

### Post by Luzbel on 2006-03-16
Will it work with E17? Anyone tried?

---

### Post by dentaku65 on 2006-03-16
[QUOTE=gandalfn]I 'll just updated compiz kde package ;-)


do you add the AIGLX in corg.conf ServeurLayout section ?[/QUOTE]

I'll try the new package :-D 

Yes I add that line :confused:

---

### Post by aamukahvi on 2006-03-16
I'm doing this now on my R8500. Help would be appreciated. Here's the problem: xair starts, and I can login via GDM. The screen is in some weird widescreen resolution (I've got a 1280x1024 LCD). Plus there's a nice "Input Not Supported" popup sailing across the screen. :) 

EDIT: I could change the screen resolution back to normal using the Screen Resolution applet.

Glxgears runs, but glxinfo throws me back to GDM login.

When I try to run compiz-aiglx-start, I get the following errors:
```
toni@kookos:~$ compiz-aiglx-start
toni@kookos:~$ /usr/bin/compiz-aiglx: Root visual is not a double buffered GL visual
/usr/bin/compiz-aiglx: Failed to manage screen: 0
/usr/bin/compiz-aiglx: No managable screens found on display :0.0
```

I figured the display 0/1 thing on Xgl doesn't apply to AIGLX, so this is what I have in gdm.conf-custom:```
[servers]
## AIGLX
0=aiglx

[server-aiglx]
name=aiglx server
command=/usr/bin/Xorg-air :0
flexible=true
```

And finally, my xorg.conf:
```
Section "ServerLayout"
	Identifier     "Default Layout"
	Option "AIGLX" "true"
	Screen      0  "aticonfig Screen 0" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

............

Section "Module"

#	Load	"GLcore"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
	Load  "dbe"
EndSection

...............................................

Section "Device"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "radeon"
	Option "DRI" "true"
	Option "XAANoOffscreenPixmaps"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Graphics Adapter 0"
	Monitor    "Acer AL1715"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig Screen 0"
	Device     "ATI Graphics Adapter 0"
	Monitor    "aticonfig Monitor 0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection
```

Here's my /var/log/Xorg.0.log (a snippet). dbe seems to load ok:
```
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg-air/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension DOUBLE-BUFFER
```

Ok, so that's it. If anyone can figure this out it would be great. What option to disable/enable? Etc.

Cheers, ak

---

### Post by Fudgie on 2006-03-16
The error message is that your display isn't double buffered, and you're not using "Load dbe" in the modules section which provides it. Try with that module enabled, and see how it goes.

---

### Post by aamukahvi on 2006-03-16
[QUOTE=Fudgie]The error message is that your display isn't double buffered, and you're not using "Load dbe" in the modules section which provides it. Try with that module enabled, and see how it goes.[/QUOTE]
Ok, thanks. I added that (edited my previous post to reflect this) but it still gives me the same error. I've tried with GLcore enabled, too. I've tried display :1 but that didn't help either.  :(  I'm out of ideas.

---

### Post by Fudgie on 2006-03-16
Seems the Radeon dri driver needs a patch to select a double buffered root visual ([http://people.freedesktop.org/~ajax/radeon-prefer-db-visuals-1.patch)](http://people.freedesktop.org/~ajax/radeon-prefer-db-visuals-1.patch)), guess we'll have to compile a custom xserver-xorg-driver-ati for this to work.

---

### Post by aamukahvi on 2006-03-16
[QUOTE=Fudgie]Seems the Radeon dri driver needs a patch to select a double buffered root visual ([http://people.freedesktop.org/~ajax/radeon-prefer-db-visuals-1.patch)](http://people.freedesktop.org/~ajax/radeon-prefer-db-visuals-1.patch)), guess we'll have to compile a custom xserver-xorg-driver-ati for this to work.[/QUOTE]
Oh, crap. :lol: How does one go about doing that then? Complicated?

Here's what I would try since my knowledge is limited:
1. cvs checkout xorg-driver-ati.
2. get the patch and manually apply it to said file (radeon_dri.c)
3. compile

Of course I'm way off and you can spank me for that.

---

### Post by Jeff250 on 2006-03-16
Great How-to!

edit:  Doing the below has given me a white screen upon rebooting, but DRI was working fine until then.  Be careful.

The reason why DRI isn't working is because the mesa libs need to be compiled with the right DRI directory set.  Temporary fix:
```
sudo mkdir -p /usr/X11R6/lib/modules/dri/
sudo cp /usr/lib/dri/i915_dri.so /usr/X11R6/lib/modules/dri/
```
(or substitude your driver name .so).
Permanent solution will be to change a setting in the Mesa source before compiling.  Edit Mesa/configs/linux-dri and where it says DEFINES=, add to the list:
```
-DDEFAULT_DRIVER_DIR=\"/usr/lib/dri\"
``` Then "make clean" "make linux-dri-x86" etc. as usual.  DRI should then work out of the box.

---

### Post by no1wantdthisname on 2006-03-16
[QUOTE=Jeff250]Great How-to!

The reason why DRI isn't working is because the mesa libs need to be compiled with the right DRI directory set.  Temporary fix:
```
sudo mkdir -p /usr/X11R6/lib/modules/dri/
sudo cp /usr/lib/dri/i915_dri.so /usr/X11R6/lib/modules/dri/
```
(or substitude your driver name .so).
Permanent solution will be to change a setting in the Mesa source before compiling.  Edit Mesa/configs/linux-dri and where it says DEFINES=, add to the list:
```
-DDEFAULT_DRIVER_DIR=\"/usr/lib/dri\"
``` Then "make clean" "make linux-dri-x86" etc. as usual.  DRI should then work out of the box.[/QUOTE]

Thanks.  Dri works with the fix, but I end up with a white screen.  Applications are loading, but I can't see them.  Any ideas?  :-|

---

### Post by Fudgie on 2006-03-16
[QUOTE=aamukahvi]Oh, crap. :lol: How does one go about doing that then? Complicated?

Here's what I would try since my knowledge is limited:
1. cvs checkout xorg-driver-ati.
2. get the patch and manually apply it to said file (radeon_dri.c)
3. compile
[/QUOTE]

I did a really quick hack to test this
1. apt-get source xserver-xorg-driver-ati
2. patch the file in the extracted directory
3. apt-get --build source xserver-xorg-driver-ati
4. dpkg -i ./xserver-xorg-driver-ati_6.5.7.3-0ubuntu2_i386.deb

Unfortunately, I'm not getting a double buffered root visual even with that hack, so maybe there's some option I'm not setting for the radeon driver.

---

### Post by jamesshuang on 2006-03-16
Ok, so what am I doing wrong...

I followed the instructions on the front page perfectly. Xorg-air is running right now.

However, any attempts to run compiz-aiglx crashes out the Xserver, and just restarts GDM for me. I don't even get any debug messages. Any ideas?

---

### Post by aamukahvi on 2006-03-16
[QUOTE=Fudgie]I did a really quick hack to test this
1. apt-get source xserver-xorg-driver-ati
2. patch the file in the extracted directory
3. apt-get --build source xserver-xorg-driver-ati
4. dpkg -i ./xserver-xorg-driver-ati_6.5.7.3-0ubuntu2_i386.deb

Unfortunately, I'm not getting a double buffered root visual even with that hack, so maybe there's some option I'm not setting for the radeon driver.[/QUOTE]
I searched around the forums for possible Device options:
```
Option		"AGPMode" 		"4"
	Option		"AGPFastWrite"		"yes"
	Option		"EnablePageFlip"	"true"
	Option		"RenderAccel"		"true"
	Option	    "UseFBDev"			 "true"
    Option      "AllowGLXWithComposite" "true"
```
Some of them might be related to our DBE (UseFBDev perhaps?).

---

### Post by jstueve on 2006-03-16
[QUOTE=no1wantdthisname]Thanks.  Dri works with the fix, but I end up with a white screen.  Applications are loading, but I can't see them.  Any ideas?  :-|[/QUOTE]

Same experience with the white screen.

---

### Post by Jeff250 on 2006-03-16
I just rebooted and got the white screen too.  Bah! :x  It seems like it works as long as I don't reboot though.  Then I have to switch it back.

---

### Post by jamesshuang on 2006-03-16
okay, slight improvement. I'm at the white screen as well. The Cube extension actually works, I can see the white cube spin. I can kill compiz-aiglx, and the error message is as follows:

/usr/bin/compiz-aiglx: glXBindTexImage failed

This seems to be repeated many times. Any more directions?

---

### Post by jstueve on 2006-03-16
I confirm the spinning white cube, and the error message

The error message seems to indicate that with direct rendering enabled, the textures aren't being grabbed, and so the cube can't be rendered.

---

### Post by elanthis on 2006-03-16
> Seems the Radeon dri driver needs a patch to select a double buffered root visual ([http://people.freedesktop.org/~ajax/...suals-1.patch)](http://people.freedesktop.org/~ajax/...suals-1.patch)), guess we'll have to compile a custom xserver-xorg-driver-ati for this to work.

If it helps any, it seems that this is going to change very soon, as Compiz, Metacity, and other compositing managers are now going to use the new compositor overlay window (similar to the screensaver overlay window) which was committed to CVS a few days ago by Deron Johnson of Sun's Looking Glass fame.

Like I've said before, *all* of this GL/compositing stuff is very experimental and still subject to large architectural changes before XGL/AIGLX/Compiz/etc will be anywhere near stable and ready for production use. ;-)

> /usr/bin/compiz-aiglx: glXBindTexImage failed

Make sure you've got both the latest DRI drivers and the latest Mesa libraries from CVS.  That's the C entry point for the GLX_EXT_texture_from_pixmap extension.  I don't know what exactly would cause that call to fail, but my best educated guess is a library/driver mismatch.

---

### Post by jstueve on 2006-03-16
> **elanthis]
Like I've said before, *all* of this GL/compositing stuff is very experimental and still subject to large architectural changes before XGL/AIGLX/Compiz/etc will be anywhere near stable and ready for production use.  said:**
> 
Thank you for the disclaimer. :)  Understood.  Wonderful toy to play with, which is why God made computers... (not for 'productivity' sheeeesh ;) )

[quote]Make sure you've got both the latest DRI drivers and the latest Mesa libraries from CVS.  That's the C entry point for the GLX_EXT_texture_from_pixmap extension.  I don't know what exactly would cause that call to fail, but my best educated guess is a library/driver mismatch.

Good hint, the drivers in my /usr/lib/dri are a few weeks older.  I'll see if I can try to compile from source... I'm not good at that step, beyond 

[LIST=1]
[*]./configure
[*]make
[*]make install
[/LIST]

LOL.

---

### Post by zAo on 2006-03-16
Thanks, tried it, but it compiz doesnt draw window-borders. It starts with a message:
```
$ /usr/bin/compiz-aiglx --replace gconf
/usr/bin/compiz-aiglx: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
```
Hardware:
```
$ lspci | grep -i vga
0000:00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
```
Any ideas? Thanks in advance.

---

### Post by elanthis on 2006-03-16
You need to run gnome-window-decorator to get window borders.

---

### Post by zAo on 2006-03-16
[QUOTE=elanthis]You need to run gnome-window-decorator to get window borders.[/QUOTE]
I know, I run it on another machine with Xgl :) When I do so, it complains that there is one running already. When I check, there is one running:
```
# ps -ef | grep window-decor
me       4759     1  0 19:58 ?        00:00:00 /usr/bin/gnome-window-decorator-aiglx
```

EDIT: Killed it, run it in terminal to see some messages, but none are given. It just runs fine.

---

### Post by lizardking on 2006-03-16
Some screenshots with the effects that we gets?

---

### Post by jstueve on 2006-03-16
[QUOTE=lizardking]Some screenshots with the effects that we gets?[/QUOTE]

See attached picture.  The video capture was garbled, but in reality, smooth in a semi-transparent, around the edge grab.  The rest of the experience is like any other compiz demos.  Wobbly windows, 3D cube, Opacity, etc..

---

### Post by poofyhairguy on 2006-03-16
[QUOTE=Fudgie]Seems the Radeon dri driver needs a patch to select a double buffered root visual ([http://people.freedesktop.org/~ajax/radeon-prefer-db-visuals-1.patch)](http://people.freedesktop.org/~ajax/radeon-prefer-db-visuals-1.patch)), guess we'll have to compile a custom xserver-xorg-driver-ati for this to work.[/QUOTE]

Arg!

---

### Post by poofyhairguy on 2006-03-16
[QUOTE=elanthis]If it helps any, it seems that this is going to change very soon, as Compiz, Metacity, and other compositing managers are now going to use the new compositor overlay window (similar to the screensaver overlay window) which was committed to CVS a few days ago by Deron Johnson of Sun's Looking Glass fame.[/QUOTE]

Great!

---

### Post by elanthis on 2006-03-16
Poofy: It might be a while before Xgl and Compiz are updated, though.  :-(

---

### Post by jstueve on 2006-03-16
Another fun little screenshot, WindowsXP (VMWare Guest) full screen on one side of the cube.  XGL had problems getting VMWare full screen.  Also Videos are watchable full screen (some slow down from the rendering, xshm in totem-xine)  The cube can be rotated and the video stays on the workspace it was launched fullscreen on.

---

### Post by Twiggy794 on 2006-03-16
Seems like that patch link for the ati driver is dead, does anybody have a deb they can post?  I'm stuck using the open source radeon driver so it seems like AIGLX is the better pick of the two, I'd love to try this out.

---

### Post by aamukahvi on 2006-03-16
[QUOTE=jstueve]Another fun little screenshot, WindowsXP (VMWare Guest) full screen on one side of the cube. [/QUOTE]
At first I thought a semi-transparent Jessica Alba in a teeny weeny bikini was on the WinXP grass fields...WTF...That was until I realized it was my desktop background looming through the browser. Damn Compiz :mrgreen:

EDIT: screenie for jstueve ;)

---

### Post by jstueve on 2006-03-16
LOL... I think THAT needs a screenshot!

---

### Post by mlind on 2006-03-16
well, that screeshot inspired me to try aiglx :mrgreen:
Great job guys!

---

### Post by poofyhairguy on 2006-03-16
[QUOTE=elanthis]Poofy: It might be a while before Xgl and Compiz are updated, though.  :-([/QUOTE]

Too bad. I would like for Compiz to keep up with these developments, as I think in the long run that might be THE biggest contribution from Dave.

Compiz on Aiglx is a great thing for many reasons. The biggest is that until KDE 4 (and maybe still after) it will remain the most "flashy" of any window manager.

I often think in my head of the famous Metacity quote:

"Boring window manager for the adult in you. Many window managers are like Marshmallow Froot Loops; Metacity is like Cheerios." 

Using that metaphor, Compiz is like raw sugar in a bowl! I hope that ways for more people to use it are found!

---

### Post by Jeff250 on 2006-03-16
I've been doing some playing around, and the only reason why Dapper's default mesa libs won't work with this guide is because they have working DRI, since they point to the right DRI directory.  The mesa libs that we want for this need to have broken DRI else they will cause the white screen of death.  Fortunately, it's easy to break DRI without needing to install extra mesa libs!

Proof of concept:

```
gedit /etc/ld.so.conf
```
Move the "/opt/aiglx/lib" line from the top to the very bottom.
Save, close.
```
sudo ldconfig
sudo gedit /etc/X11/xorg.conf
```
Comment out these lines like so:
```
#Section "DRI"
#       Mode    0666
#EndSection
```

Press ctrl+alt+f1, login, and then:
```
sudo /etc/init.d/gdm restart
```
You are now using the default Dapper mesa libs without DRI.

I haven't found any differences between the performance or looks of the default Dapper mesa libs vs. the ones included in this guide.

Unfortunately, the mesa libs included in this guide cannot be uninstalled without also uninstalling xorg-air, since xorg-air is set up to depend upon the mesa lib package in this guide.  I think that this dependancy should be removed to allow the user to have the discretion of using his or her preferred mesa libs.  Also, if there are no issues with the Dapper mesa libs, it's probably best to stick with them and just have the requirement of commenting out DRI in the xorg.conf file.

---

### Post by jstueve on 2006-03-16
I don't understand what you just did, what does this do?

Enable direct rendering? or not?

---

### Post by Jeff250 on 2006-03-16
After doing that, it's still disabled, but now you're using the default Dapper mesa libs, making the ones downloadable in this thread extraneous.

---

### Post by jstueve on 2006-03-16
looking at the debs (Gracias to Dapper's new Deb Package Installer) there is no DRI drivers included in the debs on the first post of the thread (at least not in libmesa-aiglx or xserver-xorg-air)

So I think the problem is that the drivers in /usr/lib/dri are from the default dapper repos, and not something new to this thread.  

So, it would be great if we could get a package with the dri drivers from the latest CVS... I'm not having any luck building them.

ADDED:
The package that needs updated is libgl1-mesa-dri or so it seems...

---

### Post by Tr1cH on 2006-03-16
Hi, I just folloowed this how/to, but I cant get my borders working and "Opacity" is the only thing that's working. I looked in the gconf-editor to change the keys for compiz, but Opacity was the only one available (but a lot of Command*). 

So, when I boot, I dont have any border. I guest my xorg.conf is correct if I can enter a gnome session. 
In my /etc/gdm/gdm.conf, I changed:
[servers]
0=(something)
to 0=aiglx

and I added (under this line):
the four other lines in the how-to.

By the way, in the howto, you create the script /usr/bin/compiz-aiglx-start, but you chmod /usr/bin/compiz-start-aiglx. Not an important mistake, I know, but just in case some1 ask...

anyone with the same problem?

---

### Post by jstueve on 2006-03-16
are you running gnome-window-decorator-aiglx ?

---

### Post by silvaran on 2006-03-16
I have the same problem.. glxinfo shows:

```
direct rendering: No
OpenGL renderer string: Mesa DRI Intel(R) 865G 20050225
```

which is rather odd... the only way I can get DRI working is if I remove /opt/aiglx/lib from /etc/ld.so.conf and re-run ldconfig, and only run regular X, which kind of defeats the idea of using AIGLX in the first place :).

And if I run the usual gnome-window-decorator-aiglx and compiz-aiglx --replace gconf, I end up with no window borders, and no effects whatsoever.

---

### Post by gandalfn on 2006-03-16
hi,

i updated first page with new xserver-aiglx package who remove dependencies on libmesa-aiglx. I will encourage to remove libmesa-aiglx from your system it's too buggy :???: (thanks very much Jeff250)
you should too comment out the dri section and dri option in your device section

I'll add too the patched ati driver, i couldn't test it ! any feedback ?

For inactivation of dri in glxinfo it's normal ! but my poor english prevent to explain why :( 

If any french in assistance :p 

have fun

---

### Post by silvaran on 2006-03-16
I know a bit of french, you could write an entire post in french, translate it through google and get someone to clean it up! :)

---

### Post by gandalfn on 2006-03-16
[QUOTE=silvaran]I know a bit of french, you could write an entire post in french, translate it through google and get someone to clean it up! :)[/QUOTE]
LOL i don't think it's a solution ! bad explanation of the totem config and all my post are good example LOL

---

### Post by aamukahvi on 2006-03-16
[QUOTE=gandalfn]For inactivation of dri in glxinfo it's normal ! but my poor english prevent to explain why :( 

If any french in assistance :p[/QUOTE]
Bah, explique! Je promets que nous te comprenions :mrgreen:

---

### Post by silvaran on 2006-03-16
Yeah I'm still getting blank windows with no decorations, no effects, along with the error message
```
/usr/bin/compiz-aiglx: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
```
However, here's a new one:
```
libGL error: open DRM failed (Operation not permitted)
libGL error: reverting to (slow) indirect rendering
```

Eh?

---

### Post by silvaran on 2006-03-16
Ooh wait, now I get a new, nifty effect... I did a sudo chmod 0666 /dev/dri/card0 ... now I still get the "No stencil buffer" error, but no more DRM errors, and I get a pure white screen with a mouse cursor.  Fun fun fun.  Ohh, and a whole crapload of "/usr/bin/compiz-aiglx: glXBindTexImage failed" :(

---

### Post by silvaran on 2006-03-16
I got rid of the "No stencil buffer" error by increasing video memory ("VideoRam 65536") ... I still get the white screen and "glXBindTexImage failed".

---

### Post by gandalfn on 2006-03-16
Bon en francais alors !

à l'instard du serveur Xgl, aiglx utilise 2 couches pour l'affichage des fenêtres, pour faire une comparaison je reprend le fonctionnement de Xgl. lors de son lancement celui-ci lance un serveur X classique avec lequel toutes les applications communiquent, le serveur Xgl recupère ensuite l'affichage du serveur classique pour effectuer le rendu OpenGL. les drivers DRI etant utilisé par le serveur X classique ils sont inactif sur le serveur XGL.
aiglx utilise une methode similaire lors du lancement du serveur aiglx celui-ci demarre le module glx qui s'occupe du rendu opengl et garde le serveur classique en avant plan et c'est le module glx qui utilise exclusivement le driver DRI. Le rendu est assuré par l'utilisation du module damage qui averti le module glx du changement sur une portion de l'ecran. 
Pour les videos l'utilisation de xshm est du par le fait que Xvideo n'est pas géré par le module damage, idem pour l'opengl. Le rendu dans ce genre de fenetre est fait par le deplacement du contour de la fenetre. Pour visualiser le phénomène essayer de lancer glxgear et deplacer la fenetre :-D 

Le fonctionnement de Xgl et aiglx etant pas très different finalement, le compiz a donc pu etre corrigé pour qu'il fonctionne sous aiglx

Je vais essayer maintenant d'enlever toutes les dependances au paquet mesa-aiglx et plus particulièrement pour la construction du paquet car il est d'aucune utilité, je l'ai construit simplement par manque de temps :p 

Voila

---

### Post by silvaran on 2006-03-16
[QUOTE=gandalfn]Je vais essayer maintenant d'enlever toutes les dependances au paquet mesa-aiglx et plus particulièrement pour la construction du paquet car il est d'aucune utilité[/QUOTE]

I can't speak it, but I can read it :)

Would this mean the mesa-aiglx package is still useful, or necessary for that matter?

I noticed I had to UNCOMMENT the 'Section "DRI" ... 0666" thing to get DRI working.  I still get:

- Blank, white screen.
- glXBindTexImage failed.

Quelle programme vous utilisez pour entrer les lettres avec accents?

---

### Post by aamukahvi on 2006-03-16
[QUOTE=gandalfn]Bon en francais alors !
......
Voila[/QUOTE]
Merci bien. Je croix que j'ai tout compri. Presque :)

---

### Post by jstueve on 2006-03-16
Updating totally broke everything for me.  

I had to revert to the previous xserver-xorg-air-core and grabbed libmesa from gandalfn's site.  things back up now.

---

### Post by gandalfn on 2006-03-16
> I noticed I had to UNCOMMENT the 'Section "DRI" ... 0666" thing to get DRI working. I still get:

- Blank, white screen.
- glXBindTexImage failed.

it's normal because when you uncomment it's xorg server who get dri drivers and not glx module. effect  : a blank, white screen -> glx render without dri drivers 

> Quelle programme vous utilisez pour entrer les lettres avec accents?
simply configure french keyboard in gnome keyboard settings

---

### Post by aamukahvi on 2006-03-16
[QUOTE=silvaran]Quelle programme vous utilisez pour entrer les lettres avec accents?[/QUOTE]
J'utilise mon clavier finlandais, tout à fait :mrgreen: C'est cool, ça. :p

---

### Post by gandalfn on 2006-03-16
[QUOTE=jstueve]Updating totally broke everything for me.  

I had to revert to the previous xserver-xorg-air-core and grabbed libmesa from gandalfn's site.  things back up now.[/QUOTE]
have you comment dri section and disable dri option in device section when you try it ?

else do not forget to activate dbe module too

---

### Post by jstueve on 2006-03-16
yes, I disabled DRI, and it didn't work, got the white cube as mentioned above.  Logged out, rebooted, the xserver froze, and couldn't even Ctrl-Alt-F1 to a command line, had to remove the and reinstall from the Recovery comand line, re-edit the xorg.conf (enabling DRI) and then restart.

I'm heading home... I'll be back tomorrow... thanks for your hard work. :)

---

### Post by silvaran on 2006-03-16
I tried commenting out the Option "DRI" "true" from the Device section, and commenting out Section "DRI".  No effect.  Although I get a DRI error when I try to run compiz-aiglx.

Additionally, I tried 'Option "DRI" "false"' explicitly, and when I try running Xorg-air server, I get a signal 11 and a backtrace (argh)... so close...  I even tried chmod 0666 /dev/dri/* from inside, and THEN running compiz-aiglx, and I get the white screen.  Maybe a little copy/paste would help:

[http://pastebin.com/606407](http://pastebin.com/606407)

There 'tis :).

---

### Post by foxy123 on 2006-03-16
[QUOTE=zAo]Thanks, tried it, but it compiz doesnt draw window-borders. It starts with a message:
```
$ /usr/bin/compiz-aiglx --replace gconf
/usr/bin/compiz-aiglx: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
```
Hardware:
```
$ lspci | grep -i vga
0000:00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
```
Any ideas? Thanks in advance.[/QUOTE]
I've got exactly the same problem with exactly same graphic chip. Maybe rev 02 is not compatible with compiz? anyway if anyone manage to make it with with this chip, please, please post it here...

---

### Post by silvaran on 2006-03-16
Hmmm...
```
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg-air/modules/extensions/libGLcore.so
dlopen: /usr/lib/xorg-air/modules/extensions/libGLcore.so: undefined symbol: _glapi_Dispatch
(EE) Failed to load /usr/lib/xorg-air/modules/extensions/libGLcore.so
(II) UnloadModule: "GLcore"
(EE) Failed to load module "GLcore" (loader failed, 7)
```

---

### Post by gandalfn on 2006-03-16
[QUOTE=silvaran]I tried commenting out the Option "DRI" "true" from the Device section, and commenting out Section "DRI".  No effect.  Although I get a DRI error when I try to run compiz-aiglx.

Additionally, I tried 'Option "DRI" "false"' explicitly, and when I try running Xorg-air server, I get a signal 11 and a backtrace (argh)... so close...  I even tried chmod 0666 /dev/dri/* from inside, and THEN running compiz-aiglx, and I get the white screen.  Maybe a little copy/paste would help:

[http://pastebin.com/606407](http://pastebin.com/606407)

There 'tis :).[/QUOTE]
first try to load dbe before dri and glx in module like this :

Section "Module"
        Load    "GLcore"
        Load    "bitmap"
        Load    "ddc"
        Load    "dbe"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

and effectly uncomment this line :

Option  "XAANoOffscreenPixmaps"

and don't forget to uninstall libmesa-aiglx when you try the new package :

sudo dpkg -r libmesa-aiglx

---

### Post by gandalfn on 2006-03-16
[QUOTE=foxy123]I've got exactly the same problem with exactly same graphic chip. Maybe rev 02 is not compatible with compiz? anyway if anyone manage to make it with with this chip, please, please post it here...[/QUOTE]
have you start gnome-window-decorator-aiglx and activated decoration plugin in gconf ?

try this :
gnome-window-decorator-aiglx & 
compiz-aiglx --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher opaquefocus opacity &

---

### Post by Donald on 2006-03-16
My Laptop has a i915GM graphics adapter.
Starting compiz-aiglx via console as root with

"sudo /usr/bin/compiz-aiglx-start"   (-> gives me white screen)

just gives me a totally white screen.

It has to be started without "sudo" for me to work, i.e. just

"/usr/bin/compiz-aiglx-start"           (works o.k.)


@Gandalfn: perhaps you can clearify this point in your excellent documentation, because it just says "Start it"??


Before aiglx i tried Xgl. Xgl runs very smooth on my Desktop with an ATI Radeon 9800 Pro, but Xgl performed very poor on my Laptop with Intel i915GM. xorg-aiglx is very much speedier if you are using Intel integrated graphics right now.

I still get these messages but compiz seems to be working alright.

Donald@t43:~$ /usr/bin/compiz-aiglx-start
Donald@t43:~$ libGL error: open DRM failed (Operation not permitted)
libGL error: reverting to (slow) indirect rendering
/usr/bin/compiz-aiglx: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.

---

### Post by silvaran on 2006-03-16
OK here's my current status:
```
scott@silvaran:~$ ./compiz-aiglx-start
```
(At this point, all the decorations disappear, and the screen won't update at all)
So I blindly type 'metacity --replace&' and see this:
```
scott@silvaran:~$ ./compiz-aiglx-start
scott@silvaran:~$ libGL error: open DRM failed (Operation not permitted)
libGL error: reverting to (slow) indirect rendering
/usr/bin/compiz-aiglx: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.

scott@silvaran:~$ metacity --replace&
[1] 13702
scott@silvaran:~$

```
Now when I do "chmod 0666 /dev/dri/card0", and try the same thing, I get the white screen.  So I blindly type "metacity --replace&" again, and I see this:
```
/usr/bin/compiz-aiglx: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
/usr/bin/compiz-aiglx: glXBindTexImage failed
/usr/bin/compiz-aiglx: glXBindTexImage failed
(about 50 more of those)
```

Yeeeargh...

---

### Post by gandalfn on 2006-03-16
[QUOTE=silvaran]OK here's my current status:
```
scott@silvaran:~$ ./compiz-aiglx-start
```
(At this point, all the decorations disappear, and the screen won't update at all)
So I blindly type 'metacity --replace&' and see this:
```
scott@silvaran:~$ ./compiz-aiglx-start
scott@silvaran:~$ libGL error: open DRM failed (Operation not permitted)
libGL error: reverting to (slow) indirect rendering
/usr/bin/compiz-aiglx: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.

scott@silvaran:~$ metacity --replace&
[1] 13702
scott@silvaran:~$

```
Now when I do "chmod 0666 /dev/dri/card0", and try the same thing, I get the white screen.  So I blindly type "metacity --replace&" again, and I see this:
```
/usr/bin/compiz-aiglx: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
/usr/bin/compiz-aiglx: glXBindTexImage failed
/usr/bin/compiz-aiglx: glXBindTexImage failed
(about 50 more of those)
```

Yeeeargh...[/QUOTE]
try to launch compiz like this :
gnome-window-decorator-aiglx &
compiz-aiglx --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher opaquefocus opacity &

---

### Post by ykpaiha on 2006-03-16
just a stupid question:
As eye candie point of view what is the aim to get aiglx ?
does it have such difference with xgl that we can see effectivly ?
Unless that i rather prefer to stick with xgl, looking more mature (hummm! almost)
any screen shot or video avalaible somewhere?

anyway great to see so much people willing to improve our desktop.
thanks to all of you!:mrgreen:

---

### Post by silvaran on 2006-03-16
That didn't have any effect...
```
scott@silvaran:~$ gnome-window-decorator-aiglx &
[1] 14064
scott@silvaran:~$ compiz-aiglx --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher opaquefocus opacity &
[2] 14067
scott@silvaran:~$ libGL error: open DRM failed (Operation not permitted)
libGL error: reverting to (slow) indirect rendering
compiz-aiglx: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.

scott@silvaran:~$
scott@silvaran:~$ metacity --replace&
[3] 14072
scott@silvaran:~$

```

Found a couple weird things in Xorg.0.log:
```
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg-air/modules/extensions/libGLcore.so
dlopen: /usr/lib/xorg-air/modules/extensions/libGLcore.so: undefined symbol: _glapi_Dispatch
(EE) Failed to load /usr/lib/xorg-air/modules/extensions/libGLcore.so
(II) UnloadModule: "GLcore"
(EE) Failed to load module "GLcore" (loader failed, 7)
```
```
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
```
```
(WW) I810(0): Detected stolen memory (8000 kB) doesn't match what the BIOS reports (12288 kB)
(II) I810(0): Kernel reported 238848 total, 1 used
(II) I810(0): Checking Available AGP Memory: 955388 kB available (total 955392 kB, used 4 kB)
(--) I810(0): Pre-allocated VideoRAM: 8060 kByte
(**) I810(0): VideoRAM: 65536 kByte
```
```
(II) I810(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) I810(0): Extended BIOS function 0x5f05 failed.
```
```
(WW) I810(0): PGTBL_ER is 0x00000029
```

Paste bin is my friend (I included "dmesg" too): [http://pastebin.com/606471](http://pastebin.com/606471)

I think I'm going to take a dip into my BIOS.

---

### Post by silvaran on 2006-03-16
> As eye candie point of view what is the aim to get aiglx?
Special effects like windows wobbling when they move, cube rotation to switch desktops/workspaces, expose (Mac OSX) interface, fade-in/fade-out, etc, etc. :)

> does it have such difference with xgl that we can see effectivly ?
Xgl seems to have better performance with proprietary drivers (NVidia's 'nvidia', ATI's 'fglrx') and poor performance with open source drivers.  AIGLX seems to be the opposite.

> Unless that i rather prefer to stick with xgl, looking more mature (hummm! almost)
Same stuff, different approaches.  See above about OSS versus proprietary drivers.  They both provide opengl-based compositing to the X-server in different ways.  It's compiz that has the effects.

> any screen shot or video avalaible somewhere?

I don't have any off-hand.  Novell had some really nice ones available for xgl.

> anyway great to see so much people willing to improve our desktop.
thanks to all of you!:mrgreen:

Thank gandalf especially, he's been monitoring the forum every minute :)

---

### Post by gandalfn on 2006-03-16
[QUOTE=silvaran]That didn't have any effect...
```
scott@silvaran:~$ gnome-window-decorator-aiglx &
[1] 14064
scott@silvaran:~$ compiz-aiglx --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher opaquefocus opacity &
[2] 14067
scott@silvaran:~$ libGL error: open DRM failed (Operation not permitted)
libGL error: reverting to (slow) indirect rendering
compiz-aiglx: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.

scott@silvaran:~$
scott@silvaran:~$ metacity --replace&
[3] 14072
scott@silvaran:~$

```

Found a couple weird things in Xorg.0.log:
```
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg-air/modules/extensions/libGLcore.so
dlopen: /usr/lib/xorg-air/modules/extensions/libGLcore.so: undefined symbol: _glapi_Dispatch
(EE) Failed to load /usr/lib/xorg-air/modules/extensions/libGLcore.so
(II) UnloadModule: "GLcore"
(EE) Failed to load module "GLcore" (loader failed, 7)
```
```
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
```
```
(WW) I810(0): Detected stolen memory (8000 kB) doesn't match what the BIOS reports (12288 kB)
(II) I810(0): Kernel reported 238848 total, 1 used
(II) I810(0): Checking Available AGP Memory: 955388 kB available (total 955392 kB, used 4 kB)
(--) I810(0): Pre-allocated VideoRAM: 8060 kByte
(**) I810(0): VideoRAM: 65536 kByte
```
```
(II) I810(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) I810(0): Extended BIOS function 0x5f05 failed.
```
```
(WW) I810(0): PGTBL_ER is 0x00000029
```

Paste bin is my friend (I included "dmesg" too): [http://pastebin.com/606471](http://pastebin.com/606471)

I think I'm going to take a dip into my BIOS.[/QUOTE]
i'll not see any message who explain your problem only VideoRAM 65536 have you VideoRam line in your xorg.conf ? if you have disable it

---

### Post by ykpaiha on 2006-03-16
thanks silvaran...
I will sick with XGL stuff great working apps actually.
I run it on a daily basis and have (almost) no prob at all...
it was just to get some more info about aiglx

ps:
when I said cheers to all I include of course this forum and all the betatesters we here are all.....lol
\\:D/

---

### Post by silvaran on 2006-03-16
[QUOTE=gandalfn]i'll not see any message who explain your problem only VideoRAM 65536 have you VideoRam line in your xorg.conf ? if you have disable it[/QUOTE]

Removed it.  No effect.

Just to be clear, I have:
1. Load "dri" in the modules section
2. NO DRI line whatsoever in the "Device" section.
3. COMMENTED OUT Section "DRI"

When I start Xorg-air, I get this:
```
scott@silvaran:~$ sudo lsof /dev/dri/card0
COMMAND   PID USER   FD   TYPE DEVICE SIZE  NODE NAME
Xorg-air 5110 root  mem    CHR  226,0      10521 /dev/dri/card0
```

Is that normal?

---

### Post by gandalfn on 2006-03-16
[QUOTE=silvaran]Removed it.  No effect.

Just to be clear, I have:
1. Load "dri" in the modules section
2. NO DRI line whatsoever in the "Device" section.
3. COMMENTED OUT Section "DRI"

When I start Xorg-air, I get this:
```
scott@silvaran:~$ sudo lsof /dev/dri/card0
COMMAND   PID USER   FD   TYPE DEVICE SIZE  NODE NAME
Xorg-air 5110 root  mem    CHR  226,0      10521 /dev/dri/card0
```

Is that normal?[/QUOTE]
yes normal 

perhaps you don't add  Option "XAANoOffscreenPixmaps" in device section i can see your xorg.conf ?

---

### Post by silvaran on 2006-03-16
[QUOTE=gandalfn]perhaps you don't add  Option "XAANoOffscreenPixmaps" in device section i can see your xorg.conf ?[/QUOTE]

It's in there:

Option "XAANoOffscreenPixmaps"

The only difference that makes is that the screen will still draw.  But I still get:
- No special effects
- No window borders

Even with "compiz-aiglx --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher opaquefocus opacity &"

I think I'm just out of luck :(.

---

### Post by gandalfn on 2006-03-16
[QUOTE=silvaran]It's in there:

Option "XAANoOffscreenPixmaps"

The only difference that makes is that the screen will still draw.  But I still get:
- No special effects
- No window borders

Even with "compiz-aiglx --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher opaquefocus opacity &"

I think I'm just out of luck :(.[/QUOTE]
well lets Option "XAANoOffscreenPixmaps"

and don't forget to launch gnome-window-decorator-aiglx before compiz-aiglx

good luck

---

### Post by silvaran on 2006-03-16
[QUOTE=gandalfn]well lets Option "XAANoOffscreenPixmaps"

and don't forget to launch gnome-window-decorator-aiglx before compiz-aiglx

good luck[/QUOTE]

I put it in, made sure I'm launching the decorator first.. nothing works.  It could just be my video card simply doesn't work with it (yet, maybe never):

Intel Corporation 82865G Integrated Graphics Controller (rev 02)

So I give up.  Thanks a lot for your help, you've been incredibly kind.

One thing that bugs me.  What the heck !!!! is

```
libGL error: open DRM failed (Operation not permitted)
libGL error: reverting to (slow) indirect rendering
```

And this:

```
/usr/bin/compiz-aiglx: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
```

Anyways, I give up.   Thanks again!

---

### Post by Tr1cH on 2006-03-16
I have an Intel 915GM chipset and it doesnt seems to work for me. :(
I still have no border when I follow this howto and the only effect I have is Opacity... Arg!

---

### Post by elanthis on 2006-03-16
> As eye candie point of view what is the aim to get aiglx ?

AIGLX has almost nothing to do with eye-candy directly.  It's an effort to allow Accelerated Indirect Rendering (AIR).  Which has quite a few uses; one of which is that you can run a client app on one machine and have it display with full OpenGL hardware acceleration on another machine.

AIR happens to be an important part of getting efficient desktop OpenGL compositing, and XGL happens to provide AIR.

> does it have such difference with xgl that we can see effectivly ?

Thare are absolutely huge differences between AIGLX and XGL architecurally, but there are absolutely no differences between them so far as what a user will see once both projects are stable.

AIGLX is a project which adds AIR to X.org.  There is some *other* work going on to enhance the GLX support in X.org for some of the new features necessary for the desktop bling.  There is also some *other* work going on working on compositing updates.  Altogether, that makes X.org capable of doing all the fancy stuff XGL can do.

XGL on the other hand is a different project with the goal of ripping out X.org's driver backend and replacing it with only an OpenGL stack.  There are two XGL servers: Xglx and Xegl.  The Xgl that everyone is running is Xglx.

Xglx is a prototype X server; it's essentially just an OpenGL based version of Xnest.  Xegl instead is a stand-alone X server that depends on a whole new OpenGL driver stack that doesn't yet exist.

> Unless that i rather prefer to stick with xgl, looking more mature (hummm! almost)

For now.  :-)

(Just to piss off the XGL fanboys: it's a lot easier to get a prototype hack up and running than it is to get the final polished product out the door. ~_^ )

> any screen shot or video avalaible somewhere?

What exactly do you want to see?  The X server itself doesn't do anything interesting at all from a user perspective.  All of the "bling" that people want is *entirely* the result of running a compositing manager like Compiz.  Every screenshot and video you've seen of "XGL" is exactly what Compiz on AIGLX looks like.

---

### Post by poofyhairguy on 2006-03-16
[QUOTE=elanthis]
(Just to piss off the XGL fanboys: it's a lot easier to get a prototype hack up and running than it is to get the final polished product out the door. ~_^ )
[/QUOTE]

My return shot:

At least the hack called XGL works somewhat with the (closed source) ATI drivers. If ATI decides to never support Aiglx then it will never be "the solution." And they were REALLY good about supporting EXA, Composite, etc. till now. Not.

The future of Linux eye candy HAS TO go through the closed source ATI and Nvidia drivers. Not a single PCI Express card has open source drivers (and none will unless someone starts to sell add in Intel cards).

---

### Post by elanthis on 2006-03-16
> At least the hack called XGL works somewhat with the (closed source) ATI drivers. If ATI decides to never support Aiglx then it will never be "the solution."

Which isn't really possible, unless ATI stopped supporting Linux altogether.

See, "AIGLX" isn't a piece of software.  It's the name of a CVS branch used to develop a feature which is now part of X.org CVS.  The only reason that ATI doesn't support "AIGLX" is because X.org CVS broke binary driver compatibility for all drivers due to some (AIGLX-unrelated) driver interface changes.

So either ATI *will* support "AIGLX," or it will never support any version of X.org newer than X.org 7.0.  Which is, in about 6-8 weeks, going to become unmaintained and unsupported when X.org 7.1 is officially released.

To turn that into a kick in the balls for XGL users, since Xglx (XGL) cannot run without having X.org run underneath it, once Debian/Ubuntu upgrades to the X.org 7.1 release, Xglx will also cease to run on the ATI drivers for everyone.

Let's not also forget that Xglx is going to be officially released as part of X.org 7.1 or 7.2, and it's entirely possible (though not at all a given) that the final stable version of Xglx won't even be capable of running on top of X.org 7.0 or older.

It isn't possible for a driver vendor to support Xglx down the road without also supporting X.org 7.1/AIGLX.

---

### Post by poofyhairguy on 2006-03-16
[QUOTE=elanthis]Which isn't really possible, unless ATI stopped supporting Linux altogether.

See, "AIGLX" isn't a piece of software.  It's the name of a CVS branch used to develop a feature which is now part of X.org CVS.  The only reason that ATI doesn't support "AIGLX" is because X.org CVS broke binary driver compatibility for all drivers due to some (AIGLX-unrelated) driver interface changes.

So either ATI *will* support "AIGLX," or it will never support any version of X.org newer than X.org 7.0.  Which is, in about 6-8 weeks, going to become unmaintained and unsupported when X.org 7.1 is officially released.

To turn that into a kick in the balls for XGL users, since Xglx (XGL) cannot run without having X.org run underneath it, once Debian/Ubuntu upgrades to the X.org 7.1 release, Xglx will also cease to run on the ATI drivers for everyone.

Let's not also forget that Xglx is going to be officially released as part of X.org 7.1 or 7.2, and it's entirely possible (though not at all a given) that the final stable version of Xglx won't even be capable of running on top of X.org 7.0 or older.

It isn't possible for a driver vendor to support Xglx down the road without also supporting X.org 7.1/AIGLX.[/QUOTE]


You are so much fun elanthis. With just a little jab, you give the best explainations.

But I will say I personally never want to rely on ATI for anything. The newest series of cards have been sitting on the shelf for months without Linux support. If for some reason it takes them a while to support Xorg 7.x+ I would not be surprised.

Some ATI people might be stuck with Xorg 7.0 and XGL for longer than they would like.....

---

### Post by Tr1cH on 2006-03-16
just a question, is it possible that it doesnt work for me because I updated to gnome 2.14 or it's not related? I hope that you understand my bad english! ;)

---

### Post by elanthis on 2006-03-16
> ust a question, is it possible that it doesnt work for me because I updated to gnome 2.14 or it's not related? I hope that you understand my bad english! 

The version of GNOME or the applications you run should be completely unrelated to getting the X server or Compiz running.

It's almost certainly mismatched or out-dated Mesa/DRI libraries.

---

### Post by Tr1cH on 2006-03-16
I have the same problem than Silvaran.

when I try:
sudo /usr/bin/compiz-aiglx-start
I have a white screen with a cursor

and when I try:
/usr/bin/compiz-aiglx-start
I have no border with only Opacity working
and this error
```

libGL error: open DRM failed (Operation not permitted)
libGL error: reverting to (slow) indirect rendering
/usr/bin/compiz-aiglx: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.

```

and I have this in my  /var/log/Xorg.0.log about GLcore that we need to load in xorg.conf
```

(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg-air/modules/extensions/libGLcore.so
dlopen: /usr/lib/xorg-air/modules/extensions/libGLcore.so: undefined symbol: _glapi_Dispatch
(EE) Failed to load /usr/lib/xorg-air/modules/extensions/libGLcore.so
(II) UnloadModule: "GLcore"
(EE) Failed to load module "GLcore" (loader failed, 7)

```

---

### Post by silvaran on 2006-03-16
Tr1cH:

My only guess is that this is a problem with our video cards... and I suspect it will be fixed in the future, but I'm rather tentative to hold my breath.  When I get back into work tomorrow (Friday) I'll give it another go (the only machine I have with the video chipset I stated earlier) and let you know if I can get it working.  Especially that garbage about the undefined symbol (glx_dispatch or whatever the heck).

Trying to get something like this running on a Friday is, well, "asking for it," quite frankly :).

---

### Post by Tr1cH on 2006-03-16
Do you know witch package install the library libGLcore.so? Or if some1 else know...

---

### Post by Senori on 2006-03-17
[QUOTE=Tr1cH]I have an Intel 915GM chipset and it doesnt seems to work for me. :(
I still have no border when I follow this howto and the only effect I have is Opacity... Arg![/QUOTE]
My guess- and this is what I did as well- is that you haven't added the plugins to your GConf registry. Try running compiz-aiglx with all the plugins except gconf- if that works, it's probably your issue right there.

edit: The GConf key you want to be editing is /apps/compiz/general/allscreens/options/active_plugins. Using the GConf editor, you should double-click the key (it can be done with gconftool-2 too, but this is easier) and "Add" the various plugins; the recommended order, I hear, is decoration wobbly fade minimize cube rotate zoom scale move resize place switcher.

---

### Post by bugmenot on 2006-03-17
Nice howto,
thanks a lot and thanks especially for the source debs.

I'm going to give this a try tonight, but before I do, has anyone tried to get this to work on ppc and if so, did it work?

P.S.:
And please poofyhairyguy, stop taking this thread off topic.
It's rather frustrating for people trying to get information to constantly be confronted with your off topic and uninformed comments.

---

### Post by poofyhairguy on 2006-03-17
[QUOTE=bugmenot]
And please poofyhairyguy, stop taking this thread off topic.
It's rather frustrating for people trying to get information to constantly be confronted with your off topic and uninformed comments.[/QUOTE]

Sure. I'll even go as far as to delete my own off topic posts in this thread- that make it better? Except for this post of course. I mean...you did say the magic word!

---

### Post by dentaku65 on 2006-03-17
I still get white screen after loading the compiz-aiglx-start script (both kde & gnome); this is my xorg.conf:

```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
#	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
#	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
#	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
#	Load	"GLcore"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dbe"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
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
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option	"XVideo"        "On"
	Option "XAANoOffscreenPixmaps"
#	Option "AllowGLXWithComposite" "true"
#	Option	"MonitorLayout"        "LFP,CRT"
#	Option	"DevicePresence"    "On"
#	Option	"AccelMethod" "EXA"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Option "AIGLX" "true"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection

Section "Extensions"
Option "Composite" "Enable"
Option "RENDER" "Enabled"
Option "DAMAGE" "Enabled"
EndSection

```

I really hope that someone can give some help :-|

---

### Post by bugmenot on 2006-03-17
[QUOTE=poofyhairguy]Sure. I'll even go as far as to delete my own off topic posts in this thread- that make it better?[/QUOTE]
Definately.
Or just split them to an other post in a more appropriate forum.
And don't forget to delete this post here too. ;)

---

### Post by aamukahvi on 2006-03-17
[QUOTE=elanthis](Just to piss off the XGL fanboys: it's a lot easier to get a prototype hack up and running than it is to get the final polished product out the door. ~_^ )[/QUOTE]
I'm sure people realize by now, that either one is good and just use what works best for them in any given situation.

[-o< \\:D/ 8-[ :shock:

---

### Post by househead on 2006-03-17
Quick question...

Can I safely install the provided debs alongside the compiz / xgl packages I currently have installed?

I am using Nvidia, and I have got xserver-xorg-air to actually run.

---

### Post by aamukahvi on 2006-03-17
[QUOTE=househead]Quick question...

Can I safely install the provided debs alongside the compiz / xgl packages I currently have installed?

I am using Nvidia, and I have got xserver-xorg-air to actually run.[/QUOTE]
I don't believe it's possible without modification of some sort. The package names are identical (if my memory serves me right). Mind telling us how you got nvidia running aiglx? :o

---

### Post by househead on 2006-03-17
[QUOTE=aamukahvi]I don't believe it's possible without modification of some sort. The package names are identical (if my memory serves me right). Mind telling us how you got nvidia running aiglx? :o[/QUOTE]

K, cheers.

I did nothing extraordinary. I installed xserver-xorg-air, then ran

sudo Xorg-air :1

from a terminal in gnome.

I am yet to get a window manager etc running, but I can start xterms etc. This is why I am baffled when it's noted that Nvidia doesn't work with AIGLX.

---

### Post by aamukahvi on 2006-03-17
[QUOTE=househead]K, cheers.

I did nothing extraordinary. I installed xserver-xorg-air, then ran

sudo Xorg-air :1

from a terminal in gnome.

I am yet to get a window manager etc running, but I can start xterms etc. This is why I am baffled when it's noted that Nvidia doesn't work with AIGLX.[/QUOTE]
Ok, this just occurred to me: maybe it's just all the GL stuff that's not possible on AIGLX/nvidia? I mean I got AIGLX running quite fine on the R8500 but Compiz wasn't possible.

---

### Post by househead on 2006-03-17
[QUOTE=aamukahvi]Ok, this just occurred to me: maybe it's just all the GL stuff that's not possible on AIGLX/nvidia? I mean I got AIGLX running quite fine on the R8500 but Compiz wasn't possible.[/QUOTE]

I've only tried the normal version of compiz which had previously worked with Xgl. I'm just hitting some updates, so after this I plan to remove the existing compiz packages and try the ones on this thread with AIGLX.

I'm really keen to try AIGLX as I like Xgl, but the performance is just not upto scratch for me. It hogs the CPU like mad and screensavers and movies have a hell of a time running (and yes, I am using glx output for mplayer etc).

I'm running a GeForce Go FX 5600 on a H/T P4 3.2Ghz with 1Gb of RAM (laptop), so performance should be much better than I've experienced. I've also enabled SBA and FastWrites, and I am using NvAGP with the latest drivers.

---

### Post by Tr1cH on 2006-03-17
it's now working for me! :D 
special thanks to Senori and of course, gandalfn for this great howto.

I did it by following the howto but with this script:
```

#!/bin/bash
/usr/bin/gnome-window-decorator-aiglx &
/usr/bin/compiz-aiglx --replace decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &

```

Dont abuse of this at work, because Terry Tate is watching you! ;)

---

### Post by Jeff250 on 2006-03-17
[QUOTE=househead]Quick question...

Can I safely install the provided debs alongside the compiz / xgl packages I currently have installed?

I am using Nvidia, and I have got xserver-xorg-air to actually run.[/QUOTE]

Yes you can.  The Xorg-air package will upgrade the Xorg-air package you have installed if you have one already installed (such as the one from the Dapper repositories).  But it will only replace other *Xorg-air* packages, so this shouldn't a problem, since regular Xorg and Xgl will be unaffected.

The compiz-aiglx package will not overwrite the ordinary compiz, since all of its binaries, library directories, etc. are appended with "-aiglx", and you can install it along side the traditional compiz in the package manager.

So there is no reason why you shouldn't be able to try this out along side your current setup.

---

### Post by Twiggy794 on 2006-03-17
> 
Yes you can. The Xorg-air package will upgrade the Xorg-air package you have installed if you have one already installed (such as the one from the Dapper repositories). But it will only replace other Xorg-air packages, so this shouldn't a problem, since regular Xorg and Xgl will be unaffected.

The compiz-aiglx package will not overwrite the ordinary compiz, since all of its binaries, library directories, etc. are appended with "-aiglx", and you can install it along side the traditional compiz in the package manager.

So there is no reason why you shouldn't be able to try this out along side your current setup.The libmesa package provided on this forum broke Xgl for me, that was the only quirk I had.

On another note, any news yet on anybody getting the double-buffered error to go away with low-end ATI cards?  Just trying to use the open source radeon driver here.

---

### Post by Jeff250 on 2006-03-17
I've done some digging and discovered a solution to the DRI debacle.  There is an environment variable that can be used to disable DRI.  So all that is required is to set this variable only for compiz, and then everything else can still use DRI!

So basically, enable DRI in the /etc/X11/xorg.conf file.  If you've commented out anything enabling DRI, uncomment it!

Now modify the script that you use to start compiz.  To use the example in this guide...
```
sudo gedit /usr/bin/compiz-aiglx-start
```
(Yes, we all know that vi is better, but not everyone knows how to use it ;) .)

Change it from:
```
#!/bin/bash
/usr/bin/gnome-window-decorator-aiglx &
/usr/bin/compiz-aiglx --replace gconf &
```
To:
```
#!/bin/bash
/usr/bin/gnome-window-decorator-aiglx &
LIBGL_ALWAYS_INDIRECT=TRUE /usr/bin/compiz-aiglx --replace gconf &
```
Save and quit.

Press ctrl+alt+f1, login, type:
```
sudo /etc/init.d/gdm restart
```
to restart the X server*.  When things come up, you should have a working compiz, should have not experienced a white screen of death, and have working DRI.  Type in glxgears at a console and watch those gears spin so smoothly. :D 

* I've noticed that with this aiglx/compiz setup, restarting the X server in this manner can sometimes cause it to crash, so give things a full hard reboot before giving up.

Strangely enough, doing this also seemed to solve a visual anomaly I was experiencing at the top left corner and the right side of my windows when using compiz.  Let's hope it stays that way.

---

### Post by Jeff250 on 2006-03-17
[QUOTE=Twiggy794]The libmesa package provided on this forum broke Xgl for me, that was the only quirk I had.[/QUOTE]

Installing that package is no longer a part of the guide.  If you followed an earlier version of it, download and update the xorg-air package in the first post of this thread and then uninstall the libmesa-aiglx package.

---

### Post by idlewild on 2006-03-17
On my 855gm I can not switch to another tty terminal and back again without the xserver hanging. This also occurs when resuming from hibernation. Is everyone having the same trouble as me?

---

### Post by Jeff250 on 2006-03-17
[QUOTE=idlewild]On my 855gm I can not switch to another tty terminal and back again without the xserver hanging. This also occurs when resuming from hibernation. Is everyone having the same trouble as me?[/QUOTE]

Yes.  I can switch to tty1, but switching back to tty7 crashes.  (The only exception is when I restart gdm from tty1.)  Also, I haven't tried out hiberation, but suspend to RAM also crashes on resume.

---

### Post by jstueve on 2006-03-17
[QUOTE=Jeff250]Yes.  I can switch to tty1, but switching back to tty7 crashes.  (The only exception is when I restart gdm from tty1.)  Also, I haven't tried out hiberation, but suspend to RAM also crashes on resume.[/QUOTE]

Same here, is there a place to report bugs, since this is an upstream problem and not a Dapper problem?

---

### Post by Tr1cH on 2006-03-17
Thanks Jeff250 for the trick about DRI! \\:D/

---

### Post by jstueve on 2006-03-17
[QUOTE=Jeff250]I've done some digging and discovered a solution to the DRI debacle.  There is an environment variable that can be used to disable DRI.  So all that is required is to set this variable only for compiz, and then everything else can still use DRI!
[/QUOTE]

Great! thanks for this Jeff.

---

### Post by Tr1cH on 2006-03-17
But, I have some flickering when I play games :(

---

### Post by jstueve on 2006-03-17
yeah, same here, more a problem with compiz, than AIGLX.

I startup compiz in my .gnomerc, and then can play games fine in another account (with an empty .gnomerc) and they play without flicker.  In compiz, flicker happens, because (this is my pet theory, others may blow it away) compiz is trying to redraw the screen below, then the game redraws the screen above, and so the fight each other...

Turn off compiz to play the 3d games.

---

### Post by melalcoolique on 2006-03-17
Hi there !

I did work Xgl on an ATI 9200 with OSS drivers and on Nvidia GeForce3 TI200 and GeForce4 4200.

However, on my laptop with a S3 Savage  (S3 Inc. 86C270-294 Savage/IX-MV rev 13), both Xgl and  AIGLX  "definitively" don't work.

On [Fedora page]("http://fedoraproject.org/wiki/RenderingProject/aiglx"), no extra information:
> via, s3 savage, sis. No intrinsic reason why these wouldn't work, as far as we know, but no one has tested them yet.

Anyone has tried AIGLX on something else than a NVidia, ATI or Intel GPU? Thanks

---

### Post by elanthis on 2006-03-17
> I am using Nvidia, and I have got xserver-xorg-air to actually run.

And are you using the proprietary 'nvidia' driver?  From the sounds of how slow things are for you even with XGL, it sounds like you're not getting any acceleration at all.

The 'nvidia' driver certainly shouldn't be able to load under Xair at this point.  Unless you're running an older version from before the compatibility breaks.  Or if the compatibility breaks were reversed when I wasn't looking. ;-)

> I've done some digging and discovered a solution to the DRI debacle. There is an environment variable that can be used to disable DRI. So all that is required is to set this variable only for compiz, and then everything else can still use DRI!

Nice!  I was wondering why DRI wasn't working under the Xair server; I had thought it was simply disabled if hardware-accelerated GLX_EXT_tfp wasn't available.

Which driver/hardware are you using?

If you run Compiz, do the DRI windows become subject to all the Compiz effects?

Are you getting the usual DRI performance out of your apps under Xair+Compiz as you do under Xorg?

---

### Post by jstueve on 2006-03-17
[QUOTE=elanthis]
Which driver/hardware are you using?[/quote]
Intel 855GM

> 
If you run Compiz, do the DRI windows become subject to all the Compiz effects?
It seems that way, glxgears runs smoothly, without any flickering, but fgfs and torcs run with flickery jitters... not running compiz-aiglx enables the use of the games without flickering...

> Are you getting the usual DRI performance out of your apps under Xair+Compiz as you do under Xorg?
Under the Xair server without compiz, yeah... with compiz some 3d games flicker.

---

### Post by silvaran on 2006-03-17
[QUOTE=Tr1cH]it's now working for me! :D 
special thanks to Senori and of course, gandalfn for this great howto.

I did it by following the howto but with this script:
```

#!/bin/bash
/usr/bin/gnome-window-decorator-aiglx &
/usr/bin/compiz-aiglx --replace decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &

```

Dont abuse of this at work, because Terry Tate is watching you! ;)[/QUOTE]

Hi Tr1cH,

Could you do me a favor and pastebin your xorg.conf and lspci?  I'd like to give this one last shot... thanks

---

### Post by drizek on 2006-03-17
BTW, silvaran, its not just your card. i have the intel 950GM and i get the same error as you.

---

### Post by silvaran on 2006-03-17
[QUOTE=drizek]BTW, silvaran, its not just your card. i have the intel 950GM and i get the same error as you.[/QUOTE]

Yeah... I tried again today, just on a whim, still doesn't work... but now I get different errors, like "No GL visual for depth 32" and "Couldn't bind redirected window 0x????? to texture"... argh yet again.

---

### Post by Jeff250 on 2006-03-17
[QUOTE=elanthis]Nice!  I was wondering why DRI wasn't working under the Xair server; I had thought it was simply disabled if hardware-accelerated GLX_EXT_tfp wasn't available.

Which driver/hardware are you using?

If you run Compiz, do the DRI windows become subject to all the Compiz effects?

Are you getting the usual DRI performance out of your apps under Xair+Compiz as you do under Xorg?[/QUOTE]

I'm using the i915 drivers with an i915.  The DRI rendering stays in the same spot, while a window with blackness where the rendering used to be leaves with the compiz effects applied to it.  Once the window stops moving, the DRI rendering appears on top of it again.  I really don't play any games, so I can't judge performance.

---

### Post by jstueve on 2006-03-17
One interesting effect I've noticed is the skydome image (when applied) appears vertically reveresed... much like the effect noticed when using the xgl-compiz packages on aiglx.

---

### Post by elanthis on 2006-03-17
> I'm using the i915 drivers with an i915. The DRI rendering stays in the same spot, while a window with blackness where the rendering used to be leaves with the compiz effects applied to it. Once the window stops moving, the DRI rendering appears on top of it again. I really don't play any games, so I can't judge performance.

Ah, that's what I figured.

---

### Post by elanthis on 2006-03-17
> One interesting effect I've noticed is the skydome image (when applied) appears vertically reveresed... much like the effect noticed when using the xgl-compiz packages on aiglx.

That's a Compiz bug.  The aiglx version of the package is patched to remove the bug.  The problem is that XGL sets inverted Y coordinates by default, and Compiz just assumes inverted coordinates are in use without checking the visual's settings.

The skydome plugin also probably needs to be fixed to remove the assumption about the y axis direction.

---

### Post by vinbuntu on 2006-03-17
Anyone have an idea about how we can get suspend to ram to work with this.  I really can't think of anything.

---

### Post by no1wantdthisname on 2006-03-17
[QUOTE=Jeff250]I've done some digging and discovered a solution to the DRI debacle.  There is an environment variable that can be used to disable DRI.  So all that is required is to set this variable only for compiz, and then everything else can still use DRI!

So basically, enable DRI in the /etc/X11/xorg.conf file.  If you've commented out anything enabling DRI, uncomment it!

Now modify the script that you use to start compiz.  To use the example in this guide...
```
sudo gedit /usr/bin/compiz-aiglx-start
```
(Yes, we all know that vi is better, but not everyone knows how to use it ;) .)

Change it from:
```
#!/bin/bash
/usr/bin/gnome-window-decorator-aiglx &
/usr/bin/compiz-aiglx --replace gconf &
```
To:
```
#!/bin/bash
/usr/bin/gnome-window-decorator-aiglx &
LIBGL_ALWAYS_INDIRECT=TRUE /usr/bin/compiz-aiglx --replace gconf &
```
Save and quit.

Press ctrl+alt+f1, login, type:
```
sudo /etc/init.d/gdm restart
```
to restart the X server*.  When things come up, you should have a working compiz, should have not experienced a white screen of death, and have working DRI.  Type in glxgears at a console and watch those gears spin so smoothly. :D 

* I've noticed that with this aiglx/compiz setup, restarting the X server in this manner can sometimes cause it to crash, so give things a full hard reboot before giving up.

Strangely enough, doing this also seemed to solve a visual anomaly I was experiencing at the top left corner and the right side of my windows when using compiz.  Let's hope it stays that way.[/QUOTE]

Thanks.  Works perfectly.  When I want to run war3 I just kill compiz/gnome-window-decorator.  Gives same performance in Xorg-air as under regular Xorg.  
I can use Xorg-air as my main xserver now.

---

### Post by Tr1cH on 2006-03-17
for silvaran:

lspci
```

0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
0000:00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
0000:03:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
0000:03:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller
0000:03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)

```

xorg.conf (witout dri)
```

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
	Load 	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
        LOad    "dbe"
	Load	"dri"
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
	Option 		"AutoRepeat" "500 30"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"ca(fr)"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"IMPS/2"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"Carte video generique"
	Driver		"i810"
	VideoRam        65536
	#Option 		"DRI" "true"
	BusID           "PCI:0:2:0"
	Option 		"XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
	Identifier	"ecran generique"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Carte video generique"
	Monitor		"ecran generique"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Option 		"AIGLX" "true"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection

```

I still have an error with GLcore (module isnt loading) but compiz is working.

---

### Post by jstueve on 2006-03-17
[QUOTE=vinbuntu]Anyone have an idea about how we can get suspend to ram to work with this.  I really can't think of anything.[/QUOTE]

One possibility is to kill compiz-aiglx and gnome-windo-decorator-aiglx before running suspend.  (or adding a script that kills those processes prior to engaging suspend)

Then upon restart, re-starting compiz and the decorator.

it worked for me... manually, not automatically... but to get it to work with the shutting of the laptop lid, would mean some scripting...

---

### Post by elanthis on 2006-03-17
> I still have an error with GLcore (module isnt loading) but compiz is working.

I don't believe GLcore is used anymore.  Or, at least, it won't be; possibly it's still in transition.

GLcore is the old GLX driver for the unaccelerated indirect rendering support.  Now with AIR (AIGLX) the X server uses the Mesa DRI libraries and their built-in software fallback instead of GLcore.

---

### Post by foxy123 on 2006-03-17
wow! I finally managed to make it work with your help guys! and it looks pretty cool... The problem now is that it does not log out me from the session.

---

### Post by Donald on 2006-03-17
My Laptop (IBM T43) has a i915GM graphics adapter.
Using gandalfn's start-script as root like

"sudo /usr/bin/compiz-aiglx-start"   (-> gives me a white screen)

just gives me a totally white screen.

It has to be started without "sudo" for me to work, i.e. just

"/usr/bin/compiz-aiglx-start"           (works)


@Gandalfn: perhaps you can clearify this in your excellent documentation, instead of saying "Start it"?


Before aiglx i tried Xgl. Xgl runs very smooth on my Desktop with an ATI Radeon 9800 Pro, but Xgl performed very poor on my Laptop with Intel i915GM. xorg-aiglx is very much speedier if you are using Intel integrated graphics right now.

I still get these messages but compiz seems to be working alright.

Donald@t43:~$ /usr/bin/compiz-aiglx-start
Donald@t43:~$ libGL error: open DRM failed (Operation not permitted)
libGL error: reverting to (slow) indirect rendering
/usr/bin/compiz-aiglx: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.

---

### Post by iXce on 2006-03-17
I've just found how to solve that issue :)
Just do : sudo chgrp video /dev/dri/card0
and check that your user is in group video in /etc/group
That should work :)

Anyway, great great howto, i had Xgl on my Latitude X1 (i915GS) and that was so often slowwww that it was unusable. Now with aiglx that works really smooth, thats great :D Thanks!

Does anyone plans to package new compiz 0.0.7 for AIGLX? That would be great.

---

### Post by jstueve on 2006-03-17
I changed the group and made sure I was a member.  It goes to suspend, and wakes up, but the screen doesnt refresh...  only a hard reset gets it back.

---

### Post by iXce on 2006-03-18
My reply was for Donald ;) I'm gonna try to have suspend working soon:D

---

### Post by foxy123 on 2006-03-18
I decided to attach the screenshot.

Also is it is possible to fix mplayer playback like totem's? when I move mplayer window, it does not show anything. The same is when I rotate the cube.

---

### Post by Tr1cH on 2006-03-18
Can you guys tell me if you can still go to this website using firefox, mozilla or epiphany? [http://www.osnews.com](http://www.osnews.com)
using aiglx and compiz...

---

### Post by foxy123 on 2006-03-18
I can, no problem with firefox...

---

### Post by Tr1cH on 2006-03-18
When I go on a website that use flash, my browser is crashing (when I'm using aiglx and compiz). When I run a "normal" X-server (witout aiglx), it doesnt crash and I can see the flash animations. :( 
Maybe I have the wrong plugin for flash...

---

### Post by elanthis on 2006-03-18
Make sure you have the latest version.

I recall there being some bug or another from a year or two ago with flash and ARGB visuals.

Hopefully that has actually been fixed by now...

---

### Post by Senori on 2006-03-18
[QUOTE=foxy123]I decided to attach the screenshot.

Also is it is possible to fix mplayer playback like totem's? when I move mplayer window, it does not show anything. The same is when I rotate the cube.[/QUOTE]
mplayer -vo x11

---

### Post by foxy123 on 2006-03-18
[QUOTE=Senori]mplayer -vo x11[/QUOTE]
thanks, it's nice... the only problem with this option it does not fit the picture to the full screen, keeping the original size. Is there any option to fit the size to the screen?

---

### Post by egsgaard on 2006-03-18
when running compiz-aiglx-start i get this error:
/usr/bin/compiz-aiglx: glXBindTexImageEXT is missing
/usr/bin/compiz-aiglx: Failed to manage screen: 0
/usr/bin/compiz-aiglx: No managable screens found on display :0.0

if i run the two commands seperatly i get this:

(gnome-window-decorator-aiglx:10647): Gdk-WARNING **: locale not supported by Xlib

(gnome-window-decorator-aiglx:10647): Gdk-WARNING **: cannot set locale modifiers
/usr/bin/gnome-window-decorator-aiglx: Another window decorator is already running

[2]+  Exit 1                  /usr/bin/gnome-window-decorator-aiglx
jk@psi:~$ /usr/bin/compiz-aiglx --replace gconf &
[2] 10650
jk@psi:~$ /usr/bin/compiz-aiglx: glXBindTexImageEXT is missing
/usr/bin/compiz-aiglx: Failed to manage screen: 0
/usr/bin/compiz-aiglx: No managable screens found on display :0.0


the effect of running it is, that the border of the windows dissappears, and keyboard shortcuts stop works... can anybody help me?

And, gnome appears to load a lot quiker, and feels quiker when loaded :D
i have an i810

---

### Post by Senori on 2006-03-18
[QUOTE=egsgaard]when running compiz-aiglx-start i get this error:
/usr/bin/compiz-aiglx: glXBindTexImageEXT is missing
/usr/bin/compiz-aiglx: Failed to manage screen: 0
/usr/bin/compiz-aiglx: No managable screens found on display :0.0

if i run the two commands seperatly i get this:

(gnome-window-decorator-aiglx:10647): Gdk-WARNING **: locale not supported by Xlib

(gnome-window-decorator-aiglx:10647): Gdk-WARNING **: cannot set locale modifiers
/usr/bin/gnome-window-decorator-aiglx: Another window decorator is already running

[2]+  Exit 1                  /usr/bin/gnome-window-decorator-aiglx
jk@psi:~$ /usr/bin/compiz-aiglx --replace gconf &
[2] 10650
jk@psi:~$ /usr/bin/compiz-aiglx: glXBindTexImageEXT is missing
/usr/bin/compiz-aiglx: Failed to manage screen: 0
/usr/bin/compiz-aiglx: No managable screens found on display :0.0


the effect of running it is, that the border of the windows dissappears, and keyboard shortcuts stop works... can anybody help me?

And, gnome appears to load a lot quiker, and feels quiker when loaded :D
i have an i810[/QUOTE]
Do you have the GConf keys set for decoration and whatnot?

[quote=foxy123]thanks, it's nice... the only problem with this option it does not fit the picture to the full screen, keeping the original size. Is there any option to fit the size to the screen?[/quote]
The -zoom option should take care of that.

Keep in mind that this will generally be dramatically slower than xv- for normal use, I wouldn't suggest it.

---

### Post by egsgaard on 2006-03-18
[QUOTE=Senori]Do you have the GConf keys set for decoration and whatnot?
[/QUOTE]

Where is these keys, and what values should the have?

thank you

EDIT:

aiglx is running, i think:
jk@psi:~$ ps -A | grep ai
  118 ?        00:00:00 aio/0
12613 tty7     00:02:52 Xorg-air

---

### Post by Senori on 2006-03-18
[QUOTE=egsgaard]Where is these keys, and what values should the have?

thank you

EDIT:

aiglx is running, i think:
jk@psi:~$ ps -A | grep ai
  118 ?        00:00:00 aio/0
12613 tty7     00:02:52 Xorg-air[/QUOTE]
The GConf key you want to be editing is /apps/compiz/general/allscreens/options/active_plugins. Using the GConf editor, you should double-click the key (it can be done with gconftool-2 too, but this is easier) and "Add" the various plugins; the recommended order, I hear, is decoration wobbly fade minimize cube rotate zoom scale move resize place switcher.

---

### Post by egsgaard on 2006-03-18
[QUOTE=Senori]The GConf key you want to be editing is /apps/compiz/general/allscreens/options/active_plugins. Using the GConf editor, you should double-click the key (it can be done with gconftool-2 too, but this is easier) and "Add" the various plugins; the recommended order, I hear, is decoration wobbly fade minimize cube rotate zoom scale move resize place switcher.[/QUOTE]

Thanks, but they where added, and in that order. 
I have got compiz to work, when i start Xgl and compiz at the same time im running aiglx. it is way faster than xgl and compiz alone, but everything is mirror-reversed both horizontly and verticaly...

---

### Post by naked on 2006-03-18
Hooray!  Everything works and it works very well!  Except...:

My gnome-panel is blank now and it doesn't respond to any clicks.  I've tried killing it and restarting but nothing seems to work.  Any thoughts?

Also, when moving windows, they don't seem to 'magnitize'.

Any thoughts?

Thanks everyone!

L

---

### Post by jstueve on 2006-03-18
[QUOTE=egsgaard]Thanks, but they where added, and in that order. 
I have got compiz to work, when i start Xgl and compiz at the same time im running aiglx. it is way faster than xgl and compiz alone, but everything is mirror-reversed both horizontly and verticaly...[/QUOTE]
That happened with me, I was using the compiz compiled for XGL.  Try using the  compiz-aiglx in the provided packages on the original post on this thread.

---

### Post by egsgaard on 2006-03-18
[QUOTE=jstueve]That happened with me, I was using the compiz compiled for XGL.  Try using the  compiz-aiglx in the provided packages on the original post on this thread.[/QUOTE]

When i do that, i get the error mentioned in my first post... i guess the window manager dosn't start (the windows manger should be compiz, right?)

---

### Post by Senori on 2006-03-18
[QUOTE=naked]Hooray!  Everything works and it works very well!  Except...:

My gnome-panel is blank now and it doesn't respond to any clicks.  I've tried killing it and restarting but nothing seems to work.  Any thoughts?

Also, when moving windows, they don't seem to 'magnitize'.

Any thoughts?

Thanks everyone!

L[/QUOTE]
No clue about Gnome Panel, but for sticky windows you have to be holding Ctrl when you drag (or set it so that you just need to drag).

---

### Post by bhaagensen on 2006-03-19
Thanks for providing the packages. Really nice. It's useful on my 855gm int. graph. laptop. A few questions/comments:

1. Openoffice performance is really bad. Even drawing the ui is very slow. Any thought on this?

2. K. Høgsbergs patches seem to be applicable also to latext compiz, i.e. 0.0.7 with the exceptions of the changes to decorations.c. I've succesfully compiled and installed with K.H. patchset (and leaving decorations.c untouched). It works for me. (Is compiz going to be aiglx compatible i.e. no patching). I can't provide the package as I have no where to host it. 

3. What are the changes in 0.0.7? The changelog is not very informative, and I see no new features. Is is bug-fix release only?

4. Occasionally when running on batteries, the computer seems to randomly decide to shut down. I think I saw something about this somewhere, but can't find it now. Thoughts and advice on this matter is appreciated.

Thanks,

Bjørn

---

### Post by foxy123 on 2006-03-19
I've got another problem. Some dialogue boxes do not have any way to close it. See the image attached. How should I close it?

---

### Post by zAo on 2006-03-19
[QUOTE=foxy123]I've got another problem. Some dialogue boxes do not have any way to close it. See the image attached. How should I close it?[/QUOTE]
Move with Alt+left click. Close with Alt + F4.

---

### Post by foxy123 on 2006-03-19
[QUOTE=zAo]Move with Alt+left click. Close with Alt + F4.[/QUOTE]
thanks a lot!

Also I noticed that devilspie does no work with compiz. Does compiz use a different way to assign work spaces?

---

### Post by vinbuntu on 2006-03-19
Regarding suspend to ram,
Is there anyway I can kill compiz-aiglx an gnome-window-decorator-aiglx within one of the settings in /etc/default/acpi-support
I've tried adding them in the processes section but I'm not getting any luck.
I would love to get suspend to ram to work without manually killing compix and window decorator before I suspend (i.e. get suspend to work on laptop lid close with aiglx).

---

### Post by elanthis on 2006-03-19
All these little window management issues are why its going to be better to NOT put Compiz as teh default WM in any OS for a long time to come.  Metacity has many many-years of effort put into it to handle all sorts of crazy stuff X apps like to do, and Compiz lacks most of that window management logic.

The lack of close buttons on dialogs is intentional, its part of Compiz' design.  Use the Close/Ok/Cancel/Whatever button that's part of the dialog (and if there is none, file a bug against the application for being retarded).

For any other weird X things that aren't working, like text overlays or such, just file a bug and pray somebody with the knowledge finds the time and drive to fix it in Compiz.

If you want a stable and fully-functional desktop, use Metacity or another stable fully-developed window manager.

---

### Post by bhaagensen on 2006-03-19
elanthis, what are you talking about? I don't think I saw anyone in this tread advocating that compiz should be the default wm for anything. Neither have I seen anyone claiming that compiz is at the level of metacity w.r.t. window management logic etc. I'm sorry, but I just found the tone in your post a little harsh and unnecassary.

---

### Post by Jeff250 on 2006-03-19
[QUOTE=vinbuntu]Regarding suspend to ram,
Is there anyway I can kill compiz-aiglx an gnome-window-decorator-aiglx within one of the settings in /etc/default/acpi-support
I've tried adding them in the processes section but I'm not getting any luck.
I would love to get suspend to ram to work without manually killing compix and window decorator before I suspend (i.e. get suspend to work on laptop lid close with aiglx).[/QUOTE]

The scripts for suspend and resume and other nifty things are /etc/acpi/*.sh.

---

### Post by elanthis on 2006-03-19
> I'm sorry, but I just found the tone in your post a little harsh and unnecassary.

Harsh?  Against what, exactly?  Did I hurt Compiz's feelings?

Next you're going to say that filing a bug against Ubuntu is being overly-critical and rude. ;-)

---

### Post by FISH on 2006-03-19
I have a problem on the first dep install as according to the instructions. And im surprised correct me if im wrong but it says im using xfree! 

Selecting previously deselected package xserver-xorg-air -core.
dpkg: regarding xserver-xorg-air-core_0.99-0ubuntu3_i386 .deb containing xserver-xorg-air-core:
 xserver-xorg-air-core conflicts with xserver-xfree86
  xserver-xorg-core provides xserver-xfree86 and is inst alled.
dpkg: error processing xserver-xorg-air-core_0.99-0ubunt u3_i386.deb (--install):
 conflicting packages - not installing xserver-xorg-air- core
Errors were encountered while processing:
 xserver-xorg-air-core_0.99-0ubuntu3_i386.deb

this is a clean install btw, the only thing ive added was easyubuntu script. Would this have cause my error?



XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

THIS COULD BE ALL DUE TO THE FACT THAT IM USING BREEZY :P Ill upgrade through apt to dapper.

---

### Post by jstueve on 2006-03-20
Great work on these packages Gandalfn, are you going to compile and publish the new compiz 0.0.7 deb?

---

### Post by gandalfn on 2006-03-20
well

fresh compiz-aiglx 0.0.7 are here [http://www.ubuntuforums.org/showthread.php?t=145068]("http://www.ubuntuforums.org/showthread.php?t=145068")! for the changelog see here : [http://www.ubuntuforums.org/showthread.php?t=139265]("http://www.ubuntuforums.org/showthread.php?t=139265")

have fun !

---

### Post by aamukahvi on 2006-03-20
[QUOTE=gandalfn]well

fresh compiz-aiglx 0.0.7 are here [http://www.ubuntuforums.org/showthread.php?t=145068]("http://www.ubuntuforums.org/showthread.php?t=145068")! for the changelog see here : [http://www.ubuntuforums.org/showthread.php?t=139265]("http://www.ubuntuforums.org/showthread.php?t=139265")

have fun ![/QUOTE]
Sais-tu quand on peut utiliser le driveur "radeon" au AIGLX?

EDIT: driveur? I'm sure that's not proper french. what's the word, please enlighten me :)

---

### Post by gandalfn on 2006-03-20
[QUOTE=aamukahvi]Sais-tu quand on peut utiliser le driveur "radeon" au AIGLX?

EDIT: driveur? I'm sure that's not proper french. what's the word, please enlighten me :)[/QUOTE]

Sorry, for now radeon patch driver it's apparently too unstable, and I don't have  unfortunately a PC with this card at disposal :cry:. For now if you use Xgl continue with it else if any willing to patching it ? It's with pleasure, i'll made a deb for it ;)  or to offer my web site to post a package same for ppc and amd64 packages.

else in french driver = pilote ;-)

---

### Post by idlewild on 2006-03-20
Thanks gandalfn, I had a go at compiling and packaging them myself but got stuck at getting the correct paths to all the files. Anyway thanks a lot! Despite the occasional crash, I can't not work without compiz now! :)

---

### Post by FISH on 2006-03-21
1.when i restart gdm all i get is a black terminal screen

quote
sudo gedit /usr/bin/compiz-aiglx-start
sudo chmod +x /usr/bin/compiz-start-aiglx
/quote

these to commands are in conflict in your how to. umm
yea so I did all this and restarted tried the script it said cant start compiz-aiglx. So I don't know where i went wrong everything accept gdm seemed to go well. I have no gdm gui anymore. I don't know if thats normal for this script to work.

---

### Post by deepclutch on 2006-03-21
will AIGLX project gets merged into XGL.also this guy seems achieved XGL running using latest snapshot of "i810" driver.:
[http://ubuntuforums.org/showthread.php?t=134069&highlight=i810](http://ubuntuforums.org/showthread.php?t=134069&highlight=i810)

Also i have a small doubt-me got 915GAV mobo uses only 8 MB Ram for Grafix.how do i add more memory for Video..Thanks All of You

---

### Post by elanthis on 2006-03-21
> will AIGLX project gets merged into XGL.

AIGLX is mostly merged into XGL.  (Sort of.  That's not a particularly precise way to phrase it, but it gets the idea across.)

---

### Post by Jingo on 2006-03-22
Did any of you got aiglx working on Radeon 7500 (RV100), using open source radeon driver ?
I seem to have troubles, and yes I did install the ATI package in the 1. post!

The R100-r200 chips are statet to work! What am I missing? ](*,)

---

### Post by foxy123 on 2006-03-22
compiz works strangely with workk spaces. For example I put four different programmes on 4 different work spaces. They are restored. If I click on the programmes on the task bar the cube is roteting between different work space. Then I minimise all four programmes and again click on them on the task bar. They now open on the same work space. Is it a bug or a feature?

---

### Post by Tharna on 2006-03-22
[QUOTE=Jingo]Did any of you got aiglx working on Radeon 7500 (RV100), using open source radeon driver ?
I seem to have troubles, and yes I did install the ATI package in the 1. post!

The R100-r200 chips are statet to work! What am I missing? ](*,)[/QUOTE]

I have also problems getting this working with radeon drivers (I have 9000pro). Xair runs fine, but compiz complains about root window not double buffered (dbe loads fine in xorg.log). Also any opengl thingie gives warning about not having visual 0x4b. (I hope I remembered those correctly).
I've tested with .deb given in first post and also with latest snapshot (yesterdays) from [http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/).

---

### Post by Jingo on 2006-03-22
[QUOTE=Tharna]I have also problems getting this working with radeon drivers (I have 9000pro). Xair runs fine, but compiz complains about root window not double buffered (dbe loads fine in xorg.log). Also any opengl thingie gives warning about not having visual 0x4b. (I hope I remembered those correctly).
I've tested with .deb given in first post and also with latest snapshot (yesterdays) from [http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/).[/QUOTE]

Maybe the dri snapshots are not up to date?
Anyone tried the xorg-driver-ati cvs branch?

What is missing?
When will the radeon driver be ready?
AIGLX was originaly only working with radeon, now no more?

Will dapper get Xorg 7.1, I guess it should be releases in 6 weeks or so (what I read on the mailinglist, correct me if I'm wrong)?

---

### Post by stu on 2006-03-22
[QUOTE=foxy123]compiz works strangely with workk spaces. For example I put four different programmes on 4 different work spaces. They are restored. If I click on the programmes on the task bar the cube is roteting between different work space. Then I minimise all four programmes and again click on them on the task bar. They now open on the same work space. Is it a bug or a feature?[/QUOTE]
What settings do you have in your gnome-panel window list? Right click the dragger on the left side of  your window list. Sounds like a bug to me, but check that changing those settings doesn't do anything for you.

---

### Post by Senori on 2006-03-22
[QUOTE=stu]What settings do you have in your gnome-panel window list? Right click the dragger on the left side of  your window list. Sounds like a bug to me, but check that changing those settings doesn't do anything for you.[/QUOTE]
All applications on all desktops appear in the taskbar with compiz, so I'd assume this isn't a bug (though the "appear on all desktops" thing could be considered one).

---

### Post by bijoux on 2006-03-24
could someone resync the newest compiz debs? thanks

---

### Post by FISH on 2006-03-24
I get this error when starting the script 

> 
ashley@home:~$ /usr/bin/compiz-aiglx: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.


Ive double checked and followed the instructions twice, i didn't find any errors that i followed. Perhaps someone can help me. Thanks.:)

---

### Post by gandalfn on 2006-03-25
hi,

i'll updated debs in first page

update xorg-air 0.99.1
- resync xorg-air with lasted cvs snapshot which include some bug fixes, optimisation and security fix
- mesa-aiglx-sources depends is removed this package is now obsolote
- to rebuild xorg-air from source you need this packages
x11proto-gl-dev_1.4.6-0ubuntu1_all.deb
x11proto-composite-dev_0.3-0ubuntu1_all.deb
x11proto-fixes-dev_4.0-0ubuntu1_all.deb

update compiz-aiglx 0.0.7 ubuntu2
- resync with the fantastic quinn compiz packages
- compiz-aiglx-start script is now in package it's automatically started in gnome startup session to disabled it remove /etc/xdg/autostart/compiz-aiglx.desktop file
- patched gnome-session is now needed by compiz-aiglx-gnome

update xserver-xorg-driver-ati
- rebuild with aiglx dri init patch

have fun !

EDIT: oups! i forgot 
you could uncomment dri section now dri is now active
> 
 glxinfo |grep direct
direct rendering: Yes


---

### Post by gandalfn on 2006-03-25
[QUOTE=FISH]I get this error when starting the script 



Ive double checked and followed the instructions twice, i didn't find any errors that i followed. Perhaps someone can help me. Thanks.:)[/QUOTE]

ignore this message, is normal ;)

---

### Post by Jingo on 2006-03-25
[QUOTE=gandalfn]hi,

i'll updated debs in first page

update xorg-air 0.99.1
- resync xorg-air with lasted cvs snapshot which include some bug fixes, optimisation and security fix
- mesa-aiglx-sources depends is removed this package is now obsolote
- to rebuild xorg-air from source you need this packages
x11proto-gl-dev_1.4.6-0ubuntu1_all.deb
x11proto-composite-dev_0.3-0ubuntu1_all.deb
x11proto-fixes-dev_4.0-0ubuntu1_all.deb

update compiz-aiglx 0.0.7 ubuntu2
- resync with the fantastic quinn compiz packages
- compiz-aiglx-start script is now in package it's automatically started in gnome startup session to disabled it remove /etc/xdg/autostart/compiz-aiglx.desktop file
- patched gnome-session is now needed by compiz-aiglx-gnome

update xserver-xorg-driver-ati
- rebuild with aiglx dri init patch

have fun !

EDIT: oups! i forgot 
you could uncomment dri section now dri is now active[/QUOTE]


I seem to have troubles getting this to run on my Radeon 7500 laptop!
Just freezes.
I removed the gnome-seesion autostart file, put when I manually run compiz-aiglx-start from a terminal... it hangs xorg!!!
What can I do?

---

### Post by enjoy_linux on 2006-03-25
i'll installed the new debs. but wenn gnome starts the gnome-window-decoration is missing.

and wenn i try to aktivate the compiz effects with "compiz-aiglx --replace" i get a white screen.

what can i do to fix this?


[QUOTE=gandalfn]hi,

i'll updated debs in first page

update xorg-air 0.99.1
- resync xorg-air with lasted cvs snapshot which include some bug fixes, optimisation and security fix
- mesa-aiglx-sources depends is removed this package is now obsolote
- to rebuild xorg-air from source you need this packages
x11proto-gl-dev_1.4.6-0ubuntu1_all.deb
x11proto-composite-dev_0.3-0ubuntu1_all.deb
x11proto-fixes-dev_4.0-0ubuntu1_all.deb

update compiz-aiglx 0.0.7 ubuntu2
- resync with the fantastic quinn compiz packages
- compiz-aiglx-start script is now in package it's automatically started in gnome startup session to disabled it remove /etc/xdg/autostart/compiz-aiglx.desktop file
- patched gnome-session is now needed by compiz-aiglx-gnome

update xserver-xorg-driver-ati
- rebuild with aiglx dri init patch

have fun !

EDIT: oups! i forgot 
you could uncomment dri section now dri is now active[/QUOTE]

---

### Post by vinbuntu on 2006-03-25
Thanks gandalfn for this, this is a great update.  I am however having problems with the minimize plugin now, it seems to fade out on minimize as opposed to the old effect of minimizing into the taskbar.  I like the old effect better..any ideas?  I couldn't change any keys for compiz plugins in gconf-editor to make it work.

---

### Post by gandalfn on 2006-03-25
[QUOTE=enjoy_linux]i'll installed the new debs. but wenn gnome starts the gnome-window-decoration is missing.

and wenn i try to aktivate the compiz effects with "compiz-aiglx --replace" i get a white screen.

what can i do to fix this?[/QUOTE]

oups ! stupid bug !
i updated debs to add a sleep of 2 second in compiz-aiglx-start script to make sure gnome-window-decorator-aiglx is started before compiz-aiglx

else i you start compiz-aiglx manually you should launch like this :
> 
LIBGL_ALWAYS_INDIRECT=TRUE /usr/bin/compiz-aiglx --replace gconf decoration transset wobbly fade minimize move place resize scale switcher cube rotate zoom opaquefocus opacity &


---

### Post by gandalfn on 2006-03-25
[QUOTE=vinbuntu]Thanks gandalfn for this, this is a great update.  I am however having problems with the minimize plugin now, it seems to fade out on minimize as opposed to the old effect of minimizing into the taskbar.  I like the old effect better..any ideas?  I couldn't change any keys for compiz plugins in gconf-editor to make it work.[/QUOTE]

it's seem the new quinn compiz package desactivate it ! try  [http://www.ubuntuforums.org/showthread.php?t=148472]("http://www.ubuntuforums.org/showthread.php?t=148472") to known how re-enable it.

---

### Post by enjoy_linux on 2006-03-25
[QUOTE=gandalfn]oups ! stupid bug !
i updated debs to add a sleep of 2 second in compiz-aiglx-start script to make sure gnome-window-decorator-aiglx is started before compiz-aiglx

else i you start compiz-aiglx manually you should launch like this :[/QUOTE]

reinstalled the new ones, but the same problem, just to make sure you understand what i mean, i edit a screenshot.

the window-decoration is missing, and also no effects! 

the window-decoration was also missing with the debs from yesterday.

any idea? have a intel onboard card

---

### Post by gandalfn on 2006-03-25
[QUOTE=enjoy_linux]reinstalled the new ones, but the same problem :(

the window-decoration is missing, and also no effects! 

the window-decoration was also missing with the debs from yesterday.

any idea? have a intel onboard card[/QUOTE]
check if decoration plugins is actived in gconf 
edit with gconf-editor and check if you have in apps/compiz/general/allscreens/options/active_plugins in this order :
[gconf decoration transset wobbly fade minimize move place resize scale switcher cube rotate zoom opaquefocus opacity]

---

### Post by enjoy_linux on 2006-03-25
[QUOTE=gandalfn]check if decoration plugins is actived in gconf 
edit with gconf-editor and check if you have in apps/compiz/general/allscreens/options/active_plugins in this order :
[gconf decoration transset wobbly fade minimize move place resize scale switcher cube rotate zoom opaquefocus opacity][/QUOTE]


seems to be missing, but how can i change it?

---

### Post by Jingo on 2006-03-25
[QUOTE=gandalfn]
update xserver-xorg-driver-ati
- rebuild with aiglx dri init patch
[/QUOTE]

In Xorg.log:
```
...
(==) RADEON(0): Backing store disabled
(WW) RADEON(0): Direct rendering disabled
(**) RADEON(0): Setting up final surfaces
(**) RADEON(0): Initializing Acceleration
(II) RADEON(0): Render acceleration enabled
...
(EE) AIGLX: Screen 0 is not DRI capable
...

```

When I start compiz-aiglx-start... only mouse and keyboard functions... Seems like everything but the Screen work... though it is very importent for the screen to work i think.

Anyone else using the radeon driver?
](*,)

AND... if I run glxinfo... Xorg restarts!

---

### Post by Jingo on 2006-03-25
Commented all driver options... and now it seems in Xorg.log that direct rendering is enabled.. 

But then:
```

$ LIBGL_ALWAYS_INDIRECT=TRUE /usr/bin/compiz-aiglx --replace gconf decoration transset wobbly fade minimize move place resize scale switcher cube rotate zoom opaquefocus opacity &
[1] 5846
/usr/bin/compiz-aiglx: Root visual is not a double buffered GL visual
/usr/bin/compiz-aiglx: Failed to manage screen: 0
/usr/bin/compiz-aiglx: No managable screens found on display :0.0

```

??

Xorg.log and xorg.conf attached!

---

### Post by SnEptUne on 2006-03-25
Aiglx works on mine ... until I type anything using the keyboard.  I am using ATI Radeon 9000, and whenever I tried to type something in the gnome-terminal, it will freeze.  The mouse will still move, but the screen will freeze up, even if I have kill X, gdm, etc.  In fact, the screen stay frozen until the computer reboots.  And nothing is taking up cpu time either.

I think this is a bug on the ATI driver.  For the time begin, I will just go back to the slow plan xorg without aiglx.

---

### Post by iXce on 2006-03-25
[QUOTE=Jingo]Commented all driver options... and now it seems in Xorg.log that direct rendering is enabled.. 

But then:
```

$ LIBGL_ALWAYS_INDIRECT=TRUE /usr/bin/compiz-aiglx --replace gconf decoration transset wobbly fade minimize move place resize scale switcher cube rotate zoom opaquefocus opacity &
[1] 5846
/usr/bin/compiz-aiglx: Root visual is not a double buffered GL visual
/usr/bin/compiz-aiglx: Failed to manage screen: 0
/usr/bin/compiz-aiglx: No managable screens found on display :0.0

```

Xorg.log and xorg.conf attached![/QUOTE]

Hmm I think that i've read that dbe MUST be loaded before dri in xorg.conf
Good luck!

---

### Post by Senori on 2006-03-25
[QUOTE=enjoy_linux]seems to be missing, but how can i change it?[/QUOTE]
Double-click it, or if that causes it to crash, right click and click edit.

---

### Post by linuxmad on 2006-03-25
Hi,
I have a 915 and it was working very good until... i updated to the new debs... it does not work any more.
when i:

LIBGL_ALWAYS_INDIRECT=TRUE /usr/bin/compiz-aiglx --replace gconf decoration transset wobbly fade minimize move place resize scale switcher cube rotate zoom opaquefocus opacity &

i loose the window manager..???

and get this output:

/usr/bin/compiz-aiglx: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.

I even tried revert to old debs but with no sucess

---

### Post by Senori on 2006-03-25
Are you running Gnome Window Decorator?

---

### Post by linuxmad on 2006-03-25
when the session starts it should start automatically...or not??

---

### Post by Jingo on 2006-03-25
[QUOTE=iXce]Hmm I think that i've read that dbe MUST be loaded before dri in xorg.conf
Good luck![/QUOTE]

Unfortunately didn't help!

All I see in the log file is Loading Extension DOUBLE BUFFER. I never see a SUCCESS!!
What could wrong?

Also.. I load the radeonfb kernel module.. xorg driver seems to have problems, every xorg restart starts with a scrambled screen. Switching to vt1 and back restores the screen!? :-k


and glxinfo gives me this:
```
name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x4b
Error: Unsupported depth 0... exiting
```

---

### Post by linuxmad on 2006-03-25
i don't have any trouble when i do :

/usr/bin/gnome-window-decorator-aiglx &
[1] 13020

but again when i :
IBGL_ALWAYS_INDIRECT=TRUE /usr/bin/compiz-aiglx --replace gconf decoration transset wobbly fade minimize move place resize scale switcher cube rotate zoom opaquefocus opacity &

i get the above error:
/usr/bin/compiz-aiglx: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.

Really don't know :(
It was working so good ... me and my updates.....

---

### Post by Senori on 2006-03-25
[QUOTE=linuxmad]i don't have any trouble when i do :

/usr/bin/gnome-window-decorator-aiglx &
[1] 13020

but again when i :
IBGL_ALWAYS_INDIRECT=TRUE /usr/bin/compiz-aiglx --replace gconf decoration transset wobbly fade minimize move place resize scale switcher cube rotate zoom opaquefocus opacity &

i get the above error:
/usr/bin/compiz-aiglx: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.

Really don't know :(
It was working so good ... me and my updates.....[/QUOTE]
Just to make sure, try running compiz without the gconf plugin.

edit: also, the opacity plugin is now built-in and shouldn't be loaded.

---

### Post by linuxmad on 2006-03-25
Ok tried it out without gconf and i get a blank screen, however I am able to switch desktops, rotate the cube... etc... but no windows ... only a blank white screen with the mouse pointer:confused:

---

### Post by linuxmad on 2006-03-25
I managed to ge it to work like this:

the script goes like this:

#!/bin/bash
/usr/bin/gnome-window-decorator-aiglx &
sleep 2
LIBGL_ALWAYS_INDIRECT=TRUE /usr/bin/compiz-aiglx --replace decoration wobbly fade minimize move place resize scale switcher cube rotate zoom opaquefocus opacity &

...That is ...I am missing gconf transset ... 

Can someone help??

---

### Post by linuxmad on 2006-03-25
...Sorry to insist ... but ...
Is anyone else having this problem of not being able to load the gconf and transset plugin ?????

---

### Post by bijoux on 2006-03-25
mine works just fine.. the option i pass to compiz is  "--replace gconf" every plugin seems to work just fine. i have a i810 machine by the way
 
on another note i'd like to say thanks to those who keep us updated and those who create packages from source codes.  we appreciate you :)

---

### Post by foxy123 on 2006-03-25
gconf does not work for me, but all others do...

---

### Post by Senori on 2006-03-25
Keep in mind; if you have the gconf plugin loaded, compiz will ignore any other plugins specified by the command line and load only those plugins specified in /apps/compiz/general/allscreens/active_plugins.

---

### Post by dabear on 2006-03-25
OMG! That's all I have to say. Aiglx+compiz is just so much quicker than XGL+compiz. This is great. Even quicker than metacity. i810 card btw

---

### Post by sitedesign on 2006-03-26
struggle on a laptop with Intel graphics.
I am running a fresh install of Dapper flight 5 on an Acer Travelmate 2410 laptop.

When I follow the instructions on first page I get windows without title bars, no cube, programs don't show up on the task bar.

lspci says my vid card is:
Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller

I have attached my xorg.conf file.

Any help appreciated.

---

### Post by scav on 2006-03-26
why have you commented out the aiglx option? it wont get enabled then

---

### Post by foxy123 on 2006-03-26
[QUOTE=sitedesign]struggle on a laptop with Intel graphics.
I am running a fresh install of Dapper flight 5 on an Acer Travelmate 2410 laptop.

When I follow the instructions on first page I get windows without title bars, no cube, programs don't show up on the task bar.

lspci says my vid card is:
Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller

I have attached my xorg.conf file.

Any help appreciated.[/QUOTE]

if you use a script to start compiz-aiglx, then try to remove gconf. My script looks like that:
```
#!/bin/bash
/usr/bin/gnome-window-decorator-aiglx &
sleep 2
LIBGL_ALWAYS_INDIRECT=TRUE /usr/bin/compiz-aiglx --replace decoration transset wobbly fade minimize move place resize scale switcher cube rotate zoom opaquefocus opacity &

```

---

### Post by LordRaiden on 2006-03-26
I'm using Kubuntu Dapper. I followed all the instructions short of getting compiz-gnome and gnome-sessions. I think I have to get KDE start Xorg-air instead of X, but how?

---

### Post by foxy123 on 2006-03-26
i've got a feeling that new packages make it slower.

---

### Post by LordRaiden on 2006-03-26
I got the Xorg-aiglx server 'functioning' (replacing normal X) in KDE thanks to chadwick359's "**XGL/Compiz in KDE**" post. 

In /etc/kde3/kdm/kdmrc, I changed the the ServerCmd to

```
ServerCmd=/usr/bin/Xorg-aiglx :0
``` 
BTW, I am using S3 ProSavageDDR drivers w/DRI.

Unfortunately, glxgears does not work (oddly i get 497 fps (normally 510-516) although the gears are not moving). I get the following error: 

```
libGL error: open DRM failed (Operation not permitted)
libGL error: reverting to (slow) indirect rendering
X connection to :0.0 broken (explicit kill or server shutdown).
``` 
I tried compiz-aiglx, I get the same error + i lose window borders.

Video works perfectly (using kaffeine-xine).

That's pretty much it from me. Considering Fedora's site says that savage drivers have been untested, I might very well be the first. :)

EDIT: Poking around in Xorg.0.log found 3 interesting things

1)
(II) SAVAGE(0): Direct rendering enabled
(WW) SAVAGE(0): Option "XAANOffscreenPixmaps" is not used
(==) RandR enabled

2)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
error opening security policy file /usr/lib/xserver/SecurityPolicy

3)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg-air/modules/libddc.so
(--) SAVAGE(0): No DDC signal


EDIT 2:

Warcraft III under wine does not work (loads and all just kills X after going into a game). Wasn't really expecting it to work, just wanted to try.

---

### Post by linuxmad on 2006-03-26
Ok for those not getting gconf plugin...

Think i have found a solution... Simple one...

Open up nauilus and enable "show hidden files" ctrl+h and find .gconf folder. open up apps folder inside it and delete compiz folder.
After that restart compiz-aiglx the normal way and gconf plugin should work.;) 

...Now another question... what is the plugin that gets windows being raiseid or minimized with an animation effect??? I had that effect with the old debs but now it is missing:(

---

### Post by sitedesign on 2006-03-26
I only took out the aiglx part so that I could startx and send the post to this forum.

I also tried creating a script as mentioned to start compiz-aiglx but when I run that I get:
GTK-Warning cannot open display.

I assume the script is run instead of startx.

I do put the aiglx option back in when trying to start X.

Sorry to sound like a noob with this!

---

### Post by tvon on 2006-03-26
> ...Now another question... what is the plugin that gets windows being raiseid or minimized with an animation effect??? I had that effect with the old debs but now it is missing

That's the minimize plugin, and it seems to be broken with the latest debs (won't load here).

---

### Post by Jeff250 on 2006-03-26
Anyone wanting a specific fix to suspend/hibernate can do the following (it's a hack, I know :-( ):
Add:
```
killall compiz
killall gnome-window-decorator
```
... just under the first line of /etc/acpi/prepare.sh
and add:
```
sudo -u YOURUSERNAME /usr/THERESTOFYOURPATHNAME
```
... at the end of /etc/acpi/resume.sh, being sure to replace YOURUSERNAME with your actual user name.  This won't fly in a multi-user environment, but there's no easy way that I know of to get your user's name from the environment, since this script is being run by a non-you user in the system.  Also, replace THERESTOFYOURPATHNAME with the path to your compiz script that presumably launches both gnome-window-decorator and compiz.

---

### Post by NMUrugbysteve on 2006-03-26
Does this also stop anyone else's screensaver from activating? I can't blank my screen either, it just blanks for a few minutes and comes back for no apparant reason.

---

### Post by sitedesign on 2006-03-26
[QUOTE=sitedesign]struggle on a laptop with Intel graphics.
I am running a fresh install of Dapper flight 5 on an Acer Travelmate 2410 laptop.

When I follow the instructions on first page I get windows without title bars, no cube, programs don't show up on the task bar.

lspci says my vid card is:
Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller

I have attached my xorg.conf file.

Any help appreciated.[/QUOTE]

I have noticed that in my xorg.conf file the display dirver is using the vesa default.
I have tried changing this to i810 but it fails to load tyhe i810....so file and loads the default instead.

I assume this is the reason I can't get the AIXGL & composite stuff to work.

should I be using a different script to start X windows or is startx OK.

I have tried creating a script:
/etc/xdg/autostartx/compiz-aiglx.desktop (containing)
#!/bin/bash
/usr/bin/gnome-window-decorator-aiglx &
sleep 2
LIBGL_ALWAYS_INDIRECT=TRUE /usr/bin/compiz-aiglx --replace decoration transset wobbly fade minimize move place resize scale switcher cube rotate zoom opaquefocus opacity &

However if I try to run that instead of startx then I get the error: can't open display or something.

I would love to see this working.

---

### Post by sitedesign on 2006-03-26
[QUOTE=scav]why have you commented out the aiglx option? it wont get enabled then[/QUOTE]
I just dummied it out so that I could startx and post a note on the forum.

---

### Post by linuxmad on 2006-03-27
Is anyone else having this problem??
Login to gdm.... session starts, no panels and no compiz...
It happens ... frequently.. but not always... 
Is this thing related with the gnome-window-decoration-aiglx not starting before compiz-aiglx??? 
Apparently the sleep 2 instruction in the script should take care of this... BUT....:confused: 
Am i right ??? Have you guys experienced this behavior?

---

### Post by foxy123 on 2006-03-27
[QUOTE=linuxmad]Is anyone else having this problem??
Login to gdm.... session starts, no panels and no compiz...
It happens ... frequently.. but not always... 
Is this thing related with the gnome-window-decoration-aiglx not starting before compiz-aiglx??? 
Apparently the sleep 2 instruction in the script should take care of this... BUT....:confused: 
Am i right ??? Have you guys experienced this behavior?[/QUOTE]
I do not use Gnome but after update to the recent debs I sometimes have to kill all compiz-aiglx stuff and run the script again. I guess it's the same problem....

---

### Post by tvon on 2006-03-27
[QUOTE=sitedesign]
I have tried creating a script:
/etc/xdg/autostartx/compiz-aiglx.desktop (containing)
#!/bin/bash
/usr/bin/gnome-window-decorator-aiglx &
sleep 2
LIBGL_ALWAYS_INDIRECT=TRUE /usr/bin/compiz-aiglx --replace decoration transset wobbly fade minimize move place resize scale switcher cube rotate zoom opaquefocus opacity &
[/QUOTE]

Files under /etc/xdg/autostart are .desktop files, not scripts.  Look at some other files in there and compare the contents.

---

### Post by idlewild on 2006-03-27
[QUOTE=linuxmad]
...Now another question... what is the plugin that gets windows being raiseid or minimized with an animation effect??? I had that effect with the old debs but now it is missing:([/QUOTE]

To enable the minimise effect use gconf-editor to open /apps/compiz/plugins/minimise/screen0/options and add ModalDialog to window_types key.

---

### Post by jstueve on 2006-03-27
Minimize and Wobbly aren't loading for me, I've done a reinstall with the updated Debs on the first page.  They are in the load string in the script, but don't show up in gconf-editor.  The plugins are in the /usr/lib/compiz-aiglx directory.

Any help?

---

### Post by idlewild on 2006-03-27
[QUOTE=jstueve]Minimize and Wobbly aren't loading for me, I've done a reinstall with the updated Debs on the first page.  They are in the load string in the script, but don't show up in gconf-editor.  The plugins are in the /usr/lib/compiz-aiglx directory.

Any help?[/QUOTE]

Have you checked gconf key /apps/compiz/general/allscreens/options/active_plugins for wobbly and minimize?

---

### Post by gandalfn on 2006-03-27
hi,

i updated compiz-aiglx with last quinn's modification in first page.
compiz-aiglx-start was improved too, it's included a small configuration tool to activate plugins (screenshot attached)

have fun !

---

### Post by jstueve on 2006-03-27
[QUOTE=idlewild]Have you checked gconf key /apps/compiz/general/allscreens/options/active_plugins for wobbly and minimize?[/QUOTE]

yeah, I checked that... It wouldn't stick, until I got the order correct.  

All seems good now, gonna load the new stuff.  The compiz control looks great Gandalfn!

UPDATE:  Works GREAT.  The configuration icon works well.

---

### Post by idlewild on 2006-03-27
Thanks gandalfn. The new packages work great. I normally have to edit the compiz-aiglx-start script but the new one work beautifully! Thanks for continually packaging everything :D You've got me checking daily for any new features/bugfixes.  :)

---

### Post by TheK on 2006-03-27
[QUOTE=Jingo]```
name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x4b
Error: Unsupported depth 0... exiting
```[/QUOTE]

bingo, same here. ATI Radeon 9250. Any solution around?

---

### Post by dentaku65 on 2006-03-28
Hi, I did still not upgraded to the new compiled compiz (I do not have my machine here), but I have a couple of issues with compiz and KDE:

1 when I use the icon "close to desktop" does not work
2 superkaramba desklets stay on top of the loaded apps with compiz (eg. firefox, konsole, etc...)

TIA for any suggestions

---

### Post by foxy123 on 2006-03-28
thanks gandalfn! new packages are superb. I reinstalled everything and now even gconf plugin works for me. Now more editing of the script :D

---

### Post by linuxmad on 2006-03-28
gandalfn!... you are the MAN...
Everything working :p  and i haven't experienced the session start problems....
...
about the trailfocus plugin ... what does it do???

---

### Post by hafz99 on 2006-03-28
hello everyone, 
i'm new here... :) 

I've done all the step u'd posted, i have matched step by step..
but now I have a problem..
my screen become totally white.. 
can someone help me? pleeeease.. i'm screwed and confused.. ](*,)

---

### Post by dentaku65 on 2006-03-28
[QUOTE=dentaku65]Hi, I did still not upgraded to the new compiled compiz (I do not have my machine here), but I have a couple of issues with compiz and KDE:

1 when I use the icon "close to desktop" does not work
2 superkaramba desklets stay on top of the loaded apps with compiz (eg. firefox, konsole, etc...)

TIA for any suggestions[/QUOTE]

I've installed the new packages and WOW, works great! But the two issues described above are still here; anyway AIGLX is much much faster than glx, at least with i810 card and kde; anyway I remember in glx the effect of the menu that have a little movement when selected... at last I really hope in a fix on "show desktop" icon and for superkaramba desklets...

---

### Post by Kannisto on 2006-03-29
Anyone else having memory leaks? I probed with xrestop and it said that wnck-applet was taking huge bitmaps. Xorg-air starts consuming about 50% of my memory if it has been running long. I killed wnck-applet and no leaks for now, but is this a bug in aiglx or in wnck-applet?

---

### Post by idlewild on 2006-03-29
[QUOTE=Kannisto]Anyone else having memory leaks? I probed with xrestop and it said that wnck-applet was taking huge bitmaps. Xorg-air starts consuming about 50% of my memory if it has been running long. I killed wnck-applet and no leaks for now, but is this a bug in aiglx or in wnck-applet?[/QUOTE]

I haven't had any trouble, after checking wnck-applet is taking up 386kB.

---

### Post by MeijUbuntu on 2006-03-29
Thanx Gandalfn,

I think you should earn a medal.

I Thnink aiglx is much better then Xgl.

Will Nvidia and Ati (fglrx) also be supported ?

Again many thnx

---

### Post by Milamber_Cubed on 2006-03-29
Thanks a million for this!

I installed a couple of days ago and thought... Would be good if window zooming went to/from the middle of where the window will be or is already. 2 days later its there! Coolio!

Anyway, I have a minor niggle to do with the mapped SVGS on the top of the cube. They seem to be inverted when mapped onto the top. See the attached screenshot to see what I mean.

If you look at the original svg - open in a window on my desktop - and the one on top of the cube you will see that the head and the tail of the fox are in the same orientation (left and right respectively), but that the image on the top of the cube seems to be upsidedown. It's not actually upsidedown, because then the head and tail location would be reversed and I could just rotate the SVG in karbon and be happy. It's more like a mirror in the vertical plane.

Is this a problem with the svg libs or compiz/aiglx? Any ideas would be greatly appreciated. This is much better than my XGL experience already (a lot of stuff was unusable on my graphics card - integrated 915GM with 8MB of RAM) but would be cool iof somone could give me a fix for this - even if it's just a way of inverting the image myself before applying it to the top of the cube.

Thanks again!

EDIT: Actually attaching the picture would be a good start! I do that in emails ALL the time!

---

### Post by jstueve on 2006-03-29
Yeah, I've experienced the same thing.  

My fix:  Open the graphic in Inkscape, select all, flip verticle, save as.

Yeah, I know... but it fixes the problem. :)

---

### Post by foxy123 on 2006-03-29
btw, how do you guys put an image on the top of the cube?

---

### Post by iXce on 2006-03-29
Hmm i've a strange issue
When opening a new Window in Firefox or when opening apps like gedit the inner content just doesnt fit the window
I join 2 screenshots illustrating the problem
Any idea?

---

### Post by iXce on 2006-03-29
[QUOTE=foxy123]btw, how do you guys put an image on the top of the cube?[/QUOTE]

Add a svg file path (such as /home/you/mysvgpicture.svg) in /apps/compiz/plugins/cube/screenX/options/svgs and enjoy:)

Edit : sorry for the 2 posts in a row :$

---

### Post by rockyrobin on 2006-03-29
I've been using Compiz installed on a Centrino laptop for a few days and am very impressed - thanks Gandalfn :D
Problem I now have is i'm getting itchy fingers wanting to try out the new "water effect" described in QuinnStorm's thread "New(er)est compiz packages".
I was wondering if anyone here in this thread has tried adding the repository address on that thread and whether they have got it working.
Would be nice to stay current with the updates.

---

### Post by iXce on 2006-03-29
It won't work that way ;) The compiz cvs has to be patched in order to run under AIGLX.
BTW I'm trying to compile it right now, but the new water.c refuses to compile atm.

Edit : Ok i think that i've fixed the compilation issue, gtg eat and then check my deb ;)

---

### Post by rockyrobin on 2006-03-29
**iXce** - Shame about it needing to be tweaked for either XGL or aiGLX. I was kind of hoping it was totally independent of which you use.
Let us know how you get on with the new packages.

Cheers,

RR

---

### Post by iXce on 2006-03-29
Hmm it looks like there are some more patches to apply to compiz in order to work with aiglx
It compiled well but whenever i run compiz it just crash with a beautiful segfault
I hope that gandalfn is gonna build them soon :)

Edit : i've just changed a small thing and it runs well after make install, package is building.. (it's a real package like gandalfn's ones, not checkinstall ones)
Edit 2 : i was stuck with my compiz (not aiglx debs) blocking the -gnome package to install. However on my Latitude X1 water plugin fails with a GL_ARB_fragment_program.. won't upload the debs until i've found if i can solve this error
Edit 3 : i included the trailfocus_hover patch and it compiles well :) the GL error seems to happen on others comp, so i just drop the debs now and hope it will work :)

---

### Post by Aldoo on 2006-03-29
Hi !

I juste registered on this Ubuntu forum because that one of the rare forums on the net discussing AIGLX, but I am a Gentoo user ( :p ).
I've read that you could not run AIGLX+compiz with the radeon dri driver.

I had the same problem, but I somehow managed to get a little further.

May I suggest you a link to a thread on the Gentoo forum, where I spoke about what I did ?
[http://forums.gentoo.org/viewtopic-t-445372.html]("http://forums.gentoo.org/viewtopic-t-445372.html")

It would be interesting if you tried doing the same hack as me, and say whether you manage to make compiz work. Thanks !

---

### Post by Jingo on 2006-03-29
Thanks a lot Aldoo!

Just installed compiz again after reading you posts at gentoo forums... setting the color depth to 16 made this work on my Radeon 7500 mobility on my thinkpad t42... sweet. Runs quite smooth too! ;-)

Great job.

Edit: I too get the stencil error:
```
$ compiz-aiglx-start
/usr/bin/compiz-aiglx-start: line 117:  5672 Segfault        /usr/bin/gnome-window-decorator-aiglx
/usr/bin/compiz-aiglx: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
```

---

### Post by Aldoo on 2006-03-29
You know you can also run it in 32bpp, if you modify radeon_dri.c :

line 215 :
        for (db = 0; db <= use_db; db++) {
becomes
        for (db = use_db; db >= 0; db--) {

Now I am interested in your conf, since it is working, and not mine !

May I see your xorg.conf, or any interesting detail ?

---

### Post by dentaku65 on 2006-03-29
Hi all, silly thing: the Compiz AIGLX Configuration icon in tray area is in my case not so very good... there is a way to change it?

---

### Post by kecci on 2006-03-29
[QUOTE=Aldoo]You know you can also run it in 32bpp, if you modify radeon_dri.c :

line 215 :
        for (db = 0; db <= use_db; db++) {
becomes
        for (db = use_db; db >= 0; db--) {

Now I am interested in your conf, since it is working, and not mine !

May I see your xorg.conf, or any interesting detail ?[/QUOTE]

It's also working for me with ati open source drivers on a 9250 setting color depth to 16 bit. Must I recompile dri to get it work in 32bpp mode?

---

### Post by Aldoo on 2006-03-29
I think you have to recompile the radeon dri driver (in xorg cvs : driver/xf86-video-ati) with the suggested modification.

But It does not work on my pc : all windows are white...
However, since I have the same problem in 16bpp, and you manage to run it fine in 16bpp, you should as well be able to run it in 32bpp. So try it, you never know.

Now I want to understand what is lacking in my config !!! Why does it work everywhere else ???

---

### Post by tvon on 2006-03-29
[QUOTE=dentaku65]Hi all, silly thing: the Compiz AIGLX Configuration icon in tray area is in my case not so very good... there is a way to change it?[/QUOTE]

It's setup by the compiz-aiglx-start script.  If you use the old startup method you won't get it... or just edit the current script.

---

### Post by Aldoo on 2006-03-29
[QUOTE=tvon]It's setup by the compiz-aiglx-start script.  If you use the old startup method you won't get it... or just edit the current script.[/QUOTE]

How can I get this script ?

(I am a gentoo user... I don't have the same packaging as you... )

---

### Post by Jingo on 2006-03-29
[QUOTE=Aldoo]How can I get this script ?

(I am a gentoo user... I don't have the same packaging as you... )[/QUOTE]

Sorry for the wait!

The script is in the .deps. and I attached it.
And also my xorg.conf.

I get trouble when Firefox enters flash sites... flash adds!! :(
Anyone having Firefox issues when running aiglx, this happens even before I start compiz?

Here is what I get:
```
The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 118 error_code 8 request_code 144 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

---

### Post by dentaku65 on 2006-03-30
[QUOTE=Jingo]Sorry for the wait!

The script is in the .deps. and I attached it.
And also my xorg.conf.

I get trouble when Firefox enters flash sites... flash adds!! :(
Anyone having Firefox issues when running aiglx, this happens even before I start compiz?
[/QUOTE]

Have you set transset plugin on firefox? If yes maybe this can cause the error...

---

### Post by Aldoo on 2006-03-30
Thank you, Jingo !

That was missing in my case was the environment variable LIBGL_ALWAYS_INDIRECT set to TRUE.

Now it is working... almost. Windows content get messed up, if they weren't already here before starting compiz. Maybe I have done something unneeded ;-)

Anyway, what I wanted to test gave me disappointing results : no xv acceleration when compiz is on, and no acceleration either for glxgears.. :(

---

### Post by Jingo on 2006-03-30
[QUOTE=dentaku65]Have you set transset plugin on firefox? If yes maybe this can cause the error...[/QUOTE]

No I did not enable the transset plugin!

Aldoo: Glad it worked... AIGLX is merged into xorg head by now... hopefully it will have xv accelleration by xorg 7.1.
Could this be causing my problems with firefox?

---

### Post by Aldoo on 2006-03-30
[QUOTE=Jingo]No I did not enable the transset plugin!

Aldoo: Glad it worked... AIGLX is merged into xorg head by now... hopefully it will have xv accelleration by xorg 7.1.
Could this be causing my problems with firefox?[/QUOTE]

Xv ? Definetely not. Firefox doesn't play videos !

---

### Post by Kannisto on 2006-03-30
[QUOTE=Kannisto]Anyone else having memory leaks? I probed with xrestop and it said that wnck-applet was taking huge bitmaps. Xorg-air starts consuming about 50% of my memory if it has been running long. I killed wnck-applet and no leaks for now, but is this a bug in aiglx or in wnck-applet?[/QUOTE]
Reported with generic ubuntu packages so it isn't anyway related to Aiglx

---

### Post by dentaku65 on 2006-03-30
[QUOTE=Aldoo]Xv ? Definetely not. Firefox doesn't play videos ![/QUOTE]

Again, my own experience, maybe is not important:

1 firefox with transset plugin video does not work
2 firefox without transset plugin video works

---

### Post by Jingo on 2006-03-30
[QUOTE=Aldoo]Anyway, what I wanted to test gave me disappointing results : no xv acceleration when compiz is on, and no acceleration either for glxgears.. :([/QUOTE]

Hmm... my glxgears -printfps gives me more fps under aiglx and compiz than before! ;)
without aiglx and compiz: ~850 fps
with aiglx and compiz: ~1000 fps

---

### Post by tvon on 2006-03-30
For anyone passing by, two annoying bugs I've noticed in the more recent releases:

**Window Stacking:**  (ubuntu4) When I have a number of windows open and I'm "cubing" through desktops, I can switch away and back to a desktop and the stacking of the windows will be completely different from how I left it.  When I attempt to click on the window that appears to be on top, the click will bring another window to the top and register there.  Clicking the same spot again can send the new top window back down to another layer... it seems I have to do this with every window on the desktop at least once before things start behaving normally.  This one is pretty bad and has me on the verge of going back to Metacity for a wihle.

**Window Decorations where they shouldnt be:**  (ubuntu3-ubuntu4) Sometimes the gnome-session splash screen gets a window border, sometimes it doesnt.  When changing GTK themes I get window borders around the panels and gdesklets.  On occasion the gnome foot menu will get a border (just the gnome-menu icon in the panel, it's very odd).


Is anyone else having similar problems?

---

### Post by Aldoo on 2006-03-30
I do, for the two bugs (excepted the decoration problem was with KDE's kicker and with cairo-clock).

Though I am using gentoo ;-). So that's not an Ubuntu packaging problem. And though I was using compiz on xgl. That means it's not an AIGLX bug but rather a compiz bug.

---

### Post by GeorgeNorton on 2006-03-30
[QUOTE=tvon]For anyone passing by, two annoying bugs I've noticed in the more recent releases:

**Window Stacking:**  (ubuntu4) When I have a number of windows open and I'm "cubing" through desktops, I can switch away and back to a desktop and the stacking of the windows will be completely different from how I left it.  When I attempt to click on the window that appears to be on top, the click will bring another window to the top and register there.  Clicking the same spot again can send the new top window back down to another layer... it seems I have to do this with every window on the desktop at least once before things start behaving normally.  This one is pretty bad and has me on the verge of going back to Metacity for a wihle.[/QUOTE]

The windows are staying in the same order that they were left it, only they are being drawn in some different order (creation order?)!

I get the other bug too.

-George

---

### Post by tvon on 2006-03-30
[QUOTE=Aldoo]
Though I am using gentoo ;-). So that's not an Ubuntu packaging problem. And though I was using compiz on xgl. That means it's not an AIGLX bug but rather a compiz bug.
[/QUOTE]

Yeah, I didn't mean to imply that it was a problem with the packages themselves so much as new bugs introduced into compiz (or the aiglx patches).

---

### Post by Aldoo on 2006-03-30
It seems AIGLX takes a lot more CPU than Xgl...
Is it the same on your PCs ?

Moreover, I can't swith to console and then to Xorg again without freezing it... grrr...

It's really because Xv works under AIGLX that I'm using it !

---

### Post by linuxmad on 2006-03-31
> It seems AIGLX takes a lot more CPU than Xgl... 
Are you using nvidia, ati or intel graphics??

Mine is the opposite .. i have an intel 915 and with XGL wobbly takes the cpu to the maximum.. and the experience of running compiz with XGL is .. at least ....disappointing... I have a fully functional AIGLX working with compiz and it flies...and i get no cpu overload.. it runs smooth:D

---

### Post by dentaku65 on 2006-03-31
Any chance to have the resync of compiz with the newest QuinnStorm for AIGLX?

---

### Post by LordRaiden on 2006-03-31
I installed the latest .debs and followed the instructions as posted. However, I get this error in glxinfo

libGL warning: 3D driver claims to not support visual 0x42

However, it does say direct rendering enabled. Any suggestions as to what is wrong? 

Thanks in advance

---

### Post by TheFifth on 2006-03-31
Hi All,

Finally got Compiz working again after a fresh Dapper install.  To be honest the whole machine seems to be running a little better too!

When I was using Compiz on my original install, windows that were not in focus would fade back and also become transparent.  In my new install they only fade back.  Transset seems to be working as I can manually set a transparency using the mouse wheel, but there is not one activated by default.  I've looked at the Transset section of Gconf and there is only an empty 'App' field in there.

Is it possible by default to have the in focus app being 100% opaque and all apps without focus at say 50% transparency?

Cheers,

Rich

---

### Post by jstueve on 2006-03-31
from the **[Wiki]("https://wiki.ubuntu.com/compiz#head-338631a4befcabee6061dc14b16823ede0e2b40b")**

> **apps** - List applications and how opaque they will be on startup. The format is <application> <opacity>, e.g. Gnome-terminal 80. For help on how to find out the name you should fill in see "Find out the name of an application" above.

also look at the information for [Trailfocus]("https://wiki.ubuntu.com/compiz#head-07573f326f9041573bad5cd7c92f4c8e4b232a20")

---

### Post by TheFifth on 2006-03-31
Thank you!  Trailfocus is the one I'm looking for.

Only searched the forums, never thought of looking in the Wiki... Sorry... it's been a long day! ](*,) 

Cheers!

---

### Post by gandalfn on 2006-03-31
hi, 

first page is updated with last debs

Xorg-air -> sync with CVS head
compiz-aiglx -> sync with quinns debs (ubuntu13), water plugin is desactivated because it don't work with aiglx :(

Is radeon user arrived to run compiz-aiglx ? I would like made a correct deb for this card .

Have fun !

---

### Post by iXce on 2006-03-31
[QUOTE=gandalfn]hi, 

first page is updated with last debs

Xorg-air -> sync with CVS head
compiz-aiglx -> sync with quinns debs (ubuntu13), water plugin is desactivated because it don't work with aiglx :(

Is radeon user arrived to run compiz-aiglx ? I would like made a correct deb for this card .

Have fun ![/QUOTE]

Thanks for this :) (I already had my own ubuntu6 package :p) However it's really strange for water plugin, in my glxinfo the GL_ARB_fragment_program is there :/ Maybe should it be implemented in AIGLX to run?

Small question : is your Xorg-air from current Xorg CVS head?

---

### Post by gandalfn on 2006-03-31
[QUOTE=iXce]Thanks for this :) (I already had my own ubuntu6 package :p) However it's really strange for water plugin, in my glxinfo the GL_ARB_fragment_program is there :/ Maybe should it be implemented in AIGLX to run?
[/QUOTE]
don't forget you run compiz-aiglx with LIBGL_ALWAYS_INDIRECT=TRUE try to run glxinfo with it and you see is don't active :-k perhaps with dri snapshots, i'll try it.
[QUOTE=iXce]
Small question : is your Xorg-air from current Xorg CVS head?[/QUOTE]
yes aiglx is now in xorg CVS head

---

### Post by iXce on 2006-03-31
Same, I'll try!
(It would be great if we could communicate more directly :))

Edit : ok, i've seen the glxinfo with that env, i'm gonna check latest DRI

---

### Post by LordRaiden on 2006-03-31
bump? any suggestions to my post above?

---

### Post by Jingo on 2006-04-01
[QUOTE=gandalfn]
Is radeon user arrived to run compiz-aiglx ? I would like made a correct deb for this card .
[/QUOTE]

Aldoo gave the hints... With current dep we can only run at 16bpp color.

To enable 32bpp look at this post: [270]("http://ubuntuforums.org/showpost.php?p=874013&postcount=270") all on page 14

Would be very great if included! Thanks a lot.

---

### Post by foxy123 on 2006-04-01
Sometimes I've got 2 and even 3 compiz AIGLX configuration icons in my systray, see the image attached. Does anyone else experience this?

---

### Post by sitedesign on 2006-04-01
Has any one managed to get this working with a fresh install of flight 5 on a laptop with a 915GM graphics card?

I notice that my xorg.conf file is using the vesa driver instead of the i810. changed that to say i810 instead of vesa no problem. glxinfo now shows lots of details without problems.

tried this about 3 weeks ago but couldn't get it working.

Any ideas if it will work now?

Regards Peter King

---

### Post by macewan on 2006-04-01
Have you had problems with compiz not displaying window borders?

[quote=linuxmad]Are you using nvidia, ati or intel graphics??

Mine is the opposite .. i have an intel 915 and with XGL wobbly takes the cpu to the maximum.. and the experience of running compiz with XGL is .. at least ....disappointing... I have a fully functional AIGLX working with compiz and it flies...and i get no cpu overload.. it runs smooth:D[/quote]

---

### Post by guix on 2006-04-02
Anyone has aiglx + compiz working with gandalfn packages and ATI radeon 7000/7200/7500/8500 using free drivers ?
X works but without compiz effects, I don't have any window titlebars and my gnome notes won't disappear clicking on the desktop.

---

### Post by guix on 2006-04-02
[QUOTE=sitedesign]Has any one managed to get this working with a fresh install of flight 5 on a laptop with a 915GM graphics card?[/QUOTE]

Yes and it ROCKS on my ThinkPad Z60t ! Aiglx + compiz = fantastic on this wuite weak graphic processor. Some minor issues (gnome keybindings to open a terminal and the menu don't work anymore + some flickering with some accelerated games like Xmoto).

I followed gandafn's instructions on page 1 on a fresh install of flight 5. You should check you haven't missed anything.

---

### Post by simplyw00x on 2006-04-02
Try running compiz-aiglx-start in a terminal - you may have the same problem as me.

---

### Post by guix on 2006-04-02
simplyw00x : are you talking about issues with radeon or i915 ? if it is with radeon can you post your xorg.conf ?

---

### Post by Jingo on 2006-04-02
[QUOTE=guix]Anyone has aiglx + compiz working with gandalfn packages and ATI radeon 7000/7200/7500/8500 using free drivers ?
X works but without compiz effects, I don't have any window titlebars and my gnome notes won't disappear clicking on the desktop.[/QUOTE]

Yes it works quite good on my T42 with Radeon 7500.
look at post [276]("http://ubuntuforums.org/showpost.php?p=874926&postcount=276")

Sometimes gnome-window-decorator dies. And Firefox dies when opening flash! Else its very smooth.

---

### Post by simplyw00x on 2006-04-02
[QUOTE=guix]simplyw00x : are you talking about issues with radeon or i915 ? if it is with radeon can you post your xorg.conf ?[/QUOTE]
I'm talking about radeon (9200). I hadn't seen your post, I'll take a look at your xorg.conf and see how it differs.

---

### Post by guix on 2006-04-02
Thanks Jingo, it works !!!
Smooth even on a ATI Radeon 7200 on an Athlon 1Ghz + 1Ghz RAM !!! Except when new large windows open, which is not *perfectly* smooth ;-)

I just have some issues with trailfocus I don't have on the ThinkPad. The gnome keybindings for terminal + menu don't work either, so it must be a compiz bug ?

---

### Post by simplyw00x on 2006-04-02
The keybindings are metacity/compiz - you need to re-make them in gconf-editor.

Jingo, I still get the good old 
```
libGL warning: 3D driver claims to not support visual 0x4b
/usr/bin/compiz-aiglx: Root visual is not a double buffered GL visual
/usr/bin/compiz-aiglx: Failed to manage screen: 0
/usr/bin/compiz-aiglx: No managable screens found on display :0.0
```
using your files. Any ideas?

---

### Post by Jingo on 2006-04-02
Hmm... no. The problem for me was the colordepth, after changing to 16bpp it worked.
Are you using the latest ati-driver from post 1 ?

---

### Post by simplyw00x on 2006-04-02
Man you are such a legend. I'd installed those, then compiled from source, then changed the colour depth to 16, and was completely stuck. Now I have compiz back, and with funky DRI as well! w00t!

---

### Post by iXce on 2006-04-03
I've built new AIGLX-packages with latest improvements.
They can be found there : [http://compiz.ed3n.com/viewtopic.php?pid=315#p315](http://compiz.ed3n.com/viewtopic.php?pid=315#p315)

---

### Post by macewan on 2006-04-03
omg, this is so fun

this is on a stock Dell Dimension 2400

I used this compiz-aiglx:
[http://compiz.ed3n.com/attachment.php?item=25](http://compiz.ed3n.com/attachment.php?item=25)

With this compiz-aiglx-gnome:
[http://compiz.ed3n.com/attachment.php?item=26](http://compiz.ed3n.com/attachment.php?item=26)

with:
[http://gandalfn.club.fr/ubuntu/libsvg_0.1.4-0_i386.deb](http://gandalfn.club.fr/ubuntu/libsvg_0.1.4-0_i386.deb)
[http://gandalfn.club.fr/ubuntu/libsvg-cairo_0.1.5-0_i386.deb](http://gandalfn.club.fr/ubuntu/libsvg-cairo_0.1.5-0_i386.deb)
[http://gandalfn.club.fr/ubuntu/gnome-session_2.14.0-0ubuntu2_i386.deb](http://gandalfn.club.fr/ubuntu/gnome-session_2.14.0-0ubuntu2_i386.deb)
[http://gandalfn.club.fr/ubuntu/xserver-xorg-air-core_0.99.1-0ubuntu2_i386.deb](http://gandalfn.club.fr/ubuntu/xserver-xorg-air-core_0.99.1-0ubuntu2_i386.deb)

---

### Post by guix on 2006-04-03
Thanks iXce. I'm still having some issues with the shadows like in the attached screenshot (ati radeon 7200), someone has this too ?

---

### Post by kronepils on 2006-04-03
[QUOTE=guix]Thanks iXce. I'm still having some issues with the shadows like in the attached screenshot (ati radeon 7200), someone has this too ?[/QUOTE]

Yeah, still the same problem for me as well. Radeon 7500 (Mobility M7)

---

### Post by guix on 2006-04-03
kronepils: thanks. On my ThinkPad it works with i915. So trailfocus must use a function badly implemented in DirectX7 compatible cards. Just disable the trailfocus plugin... snif... or someone else has a clue ?

---

### Post by guix on 2006-04-03
kronepils: do you have the same moving grey lines ?

---

### Post by linuxmad on 2006-04-04
Has anyone managed to get water plugin to work??
I've installed lastest debs from here:
[http://compiz.ed3n.com/viewtopic.php?id=44](http://compiz.ed3n.com/viewtopic.php?id=44)
but i can't get it to work:mad:

---

### Post by foxy123 on 2006-04-04
does anyone know how to switch between users in aiglx? If I run gnomeflexiserver, it offered two options:

1. standard X server
2. aiglx server

If I pick up standard X server I can switch to another user, but cannot switch back. As soon as I log off from the second user I found myself in text mode without any way to go back to aiglx.

If I pick up the second option, nothing happens or it says that cannot start another session (I am not sure as I am writing from another PC).

Can anyone switch between users successfully?

---

### Post by zachtib on 2006-04-04
will this work with a radeon mobility 9000? with either open/closed drivers?

---

### Post by zachtib on 2006-04-04
i followed these instructions on a radeon mobility 9000, and while it does start up fine, gnome-window-decorator doesn't seem to be working properly.

all windows have no borders and are anchored to the top left of the screen\

```

zach@notapowerbook:~$ compiz-aiglx-start
/usr/bin/compiz-aiglx: Root visual is not a double buffered GL visual
/usr/bin/compiz-aiglx: Failed to manage screen: 0
/usr/bin/compiz-aiglx: No managable screens found on display :0.0
/usr/bin/compiz-aiglx: Root visual is not a double buffered GL visual
/usr/bin/compiz-aiglx: Failed to manage screen: 0
/usr/bin/compiz-aiglx: No managable screens found on display :0.0


```

---

### Post by dentaku65 on 2006-04-04
[QUOTE=zachtib]i followed these instructions on a radeon mobility 9000, and while it does start up fine, gnome-window-decorator doesn't seem to be working properly.

all windows have no borders and are anchored to the top left of the screen\

```

zach@notapowerbook:~$ compiz-aiglx-start
/usr/bin/compiz-aiglx: Root visual is not a double buffered GL visual
/usr/bin/compiz-aiglx: Failed to manage screen: 0
/usr/bin/compiz-aiglx: No managable screens found on display :0.0
/usr/bin/compiz-aiglx: Root visual is not a double buffered GL visual
/usr/bin/compiz-aiglx: Failed to manage screen: 0
/usr/bin/compiz-aiglx: No managable screens found on display :0.0


```[/QUOTE]

Try to delete the entry compiz.aiglx in the sessions panel of gnome and replace it with compiz.aiglx.start then re-run X ...worked for me :-)

---

### Post by zachtib on 2006-04-04
[QUOTE=dentaku65]Try to delete the entry compiz.aiglx in the sessions panel of gnome and replace it with compiz.aiglx.start then re-run X ...worked for me :-)[/QUOTE]

compiz-aiglx-start is already in my session...

---

### Post by simplyw00x on 2006-04-04
[QUOTE=zachtib]i followed these instructions on a radeon mobility 9000, and while it does start up fine, gnome-window-decorator doesn't seem to be working properly.

all windows have no borders and are anchored to the top left of the screen\

```

zach@notapowerbook:~$ compiz-aiglx-start
/usr/bin/compiz-aiglx: Root visual is not a double buffered GL visual
/usr/bin/compiz-aiglx: Failed to manage screen: 0
/usr/bin/compiz-aiglx: No managable screens found on display :0.0
/usr/bin/compiz-aiglx: Root visual is not a double buffered GL visual
/usr/bin/compiz-aiglx: Failed to manage screen: 0
/usr/bin/compiz-aiglx: No managable screens found on display :0.0


```[/QUOTE]
What card are you using?

---

### Post by zachtib on 2006-04-04
[QUOTE=simplyw00x]What card are you using?[/QUOTE]
radeon mobility 9000

---

### Post by simplyw00x on 2006-04-04
If you're using the fglrx driver then it can't possibly work yet. If you're using the radeon driver, make sure you load dbe and also set the default colour depth to 16 - radeon can't do 24 or 32 bit colour yet.

---

### Post by zachtib on 2006-04-04
[QUOTE=simplyw00x]If you're using the fglrx driver then it can't possibly work yet. If you're using the radeon driver, make sure you load dbe and also set the default colour depth to 16 - radeon can't do 24 or 32 bit colour yet.[/QUOTE]

im using the radeon oss drivers, and changing the color depth to 16 did change anything.

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

Section "ServerLayout"
	Identifier     "Default Layout"
	Option "AIGLX" "true"
	Screen      0  "aticonfig Screen 0" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dbe"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection


Section "Monitor"
	Identifier   "aticonfig Monitor 0"
EndSection


Section "Device"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "radeon"
	Option "XAANoOffscreenPixmaps"
	BusID       "PCI:1:0:0"
EndSection


Section "Screen"
	Identifier "aticonfig Screen 0"
	Device     "ATI Graphics Adapter 0"
	Monitor    "aticonfig Monitor 0"
	DefaultDepth     16
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection



```

---

### Post by simplyw00x on 2006-04-04
Have you installed all the packages from the front page? Also, there are sections missing from that conf. AIGLX needs to be in serverlayout, which you don't seem to have. Try this one [http://ubuntuforums.org/showpost.php?p=874926&postcount=276](http://ubuntuforums.org/showpost.php?p=874926&postcount=276)

---

### Post by zachtib on 2006-04-04
serverlayout is at the top of my conf

---

### Post by simplyw00x on 2006-04-04
Man, I need to learn to read. Try fiddling the order of the module loads, and maybe also check /var/log/Xorg.0.log for Xorg loading errors.

---

### Post by zachtib on 2006-04-04
[QUOTE=simplyw00x]Man, I need to learn to read. Try fiddling the order of the module loads, and maybe also check /var/log/Xorg.0.log for Xorg loading errors.[/QUOTE]
:) will do

---

### Post by zachtib on 2006-04-04
```

zach@notapowerbook:/$ cat /var/log/Xorg.0.log | grep '(EE)'
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) RADEON: Failed to load module "theatre_detect" (module does not exist, 0)
(EE) RADEON(0): Unable to load Rage Theatre detect module

```
Not sure if the 93 log is important here, but:
```

zach@notapowerbook:/$ cat /var/log/Xorg.93.log | grep '(EE)'
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(EE) fglrx(0): === [R200DALSetControllerConfigForRemap] === CWDDC ControllerSetConfig failed: 6 - 0

```

---

### Post by zvjer on 2006-04-05
I have big problem here with ati R250 mobile radeon 9000card.
I removed compiz and compiz-gnome and installed aiglx versions.
I managed to run it somehow through Xgl and it works but upsidedown everything.

[[IMG]http://img76.imageshack.us/img76/6784/untitled0li.th.jpg[/IMG]](http://img76.imageshack.us/my.php?image=untitled0li.jpg)

How can I fix this please?
Note: I have removed the "old" compiz.

---

### Post by jstueve on 2006-04-05
see the first page of this thread, make sure you are running the compiz-aiglx versions of compiz.

---

### Post by simplyw00x on 2006-04-05
The theatre_detect module error is normal (for some reason) and the 93 log appears to be an old one. I'm a bit stumped there I guess.

---

### Post by kronepils on 2006-04-05
You need to use the xserver-ati driver from page 1 in this thread.
That's what made my 7500 mobility work.
Remember to add         Option          "ColorTiling"           "false"
to your xorg.conf device section. Otherwise my display got all garbled...

---

### Post by zvjer on 2006-04-06
2 jstueve: read my post one more time. I have removed all the compiz stuff and installed all aiglx versions.
2 kronepils: I am using that driver.

---

### Post by Juanito on 2006-04-06
I just got this to work on my X41 on both KDE and gnome.

Works wonderfully!! Wait until all my friends see this! :P

There are still a few bugs... such as the logout screen not showing up, and sometimes window borders don't draw.

It seems to do fully things to my two favorite apps: katapult and yakuake, other than that! it's pretty damn awesome.

---

### Post by TheFifth on 2006-04-07
I've used the Compiz updates from this thread:

[http://compiz.ed3n.com/viewtopic.php?id=44&p=1](http://compiz.ed3n.com/viewtopic.php?id=44&p=1)

All seems to be working great, however I'm having the Log Out screen not showing problem.  Anyone know a solution to this or even of another (graceful) way of shutting the computer down?

---

### Post by linuxmad on 2006-04-07
The problem with gnome-session is that you upgraded it;) . Please use the one gandalf posted in the first page of this post...it should work:)

---

### Post by jstueve on 2006-04-07
[QUOTE=zvjer]2 jstueve: read my post one more time. I have removed all the compiz stuff and installed all aiglx versions.
2 kronepils: I am using that driver.[/QUOTE]
Are you running XGL or Xorg-air?

---

### Post by TheFifth on 2006-04-07
That sorted it, thanks!

As soon as I reverted, the update manager instantly popped up telling me that there is a newer gnome-session version available online.  The odd thing is the version it wants to install has the same version number as the one I have just re-installed.  What's the difference, is it just trying to install a Dapper specific one that isn't compatible with aiglx?

Is there any way of telling the update manager to ignore this update and stop bugging me about it.  There's gonna be a lot of updates to Dapper between now and release and you can bet I forget to deselect the update box on the gnome session manager at least once!

---

### Post by jstueve on 2006-04-07
create/edit the file /etc/apt/preferences:

> 
Package: gnome-session
Pin: version 2.14.0
Pin-Priority: 1001


---

### Post by dabear on 2006-04-07
Hm, usig the patchd ati-driver, I'm getting this:
> 
bjorninge@ubuntudesktop:~$ compiz-aiglx --replace
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
compiz-aiglx: glXBindTexImageEXT is missing
compiz-aiglx: Failed to manage screen: 0
compiz-aiglx: No managable screens found on display :0.0



Any idea?

---

### Post by Jingo on 2006-04-08
[QUOTE=dabear]Hm, usig the patchd ati-driver, I'm getting this:


Any idea?[/QUOTE]
Page 14 in this thread might hold the answers!

---

### Post by iXce on 2006-04-08
Looks like there will be a new xorg-air soon ^^
I was just about to build it ^^

---

### Post by gandalfn on 2006-04-08
first sorry for last response

I updated first page with latest Xorg-air who fixes some bugs and memory leaks, and ati radeon driver with aiglx patch
WARNING !! use only official libgl1 debs with it

I rebuild latest gnome-session deb with logout_no_grab patch to prevent hang in logout

I made to compiz-aiglx 0.0.9 ubuntu1 where I made a litttle rework of aiglx-compiz-change to use copySubBuffer on refresh. Warning ! this package is only based on official compiz try iXce packages it's include to quinn modification.

edit: compiz-aiglx 0.0.9 ubuntu2 who integrate quinn modification are now avaible on first page (thanks iXce)

---

### Post by Jingo on 2006-04-08
[QUOTE=gandalfn]
I made to compiz-aiglx 0.0.9 ubuntu1 where I made a litttle rework of aiglx-compiz-change to use copySubBuffer on refresh. Warning ! this package is only based on official compiz try iXce packages it's include to quinn modification.
[/QUOTE]

Sorry to say...

gandalf compiz-package has troubles on radeon.
iXce package works great.

Seems like it only updates one of two screen buffers, result... it blinks! giving bad artifacts of last screen images!

---

### Post by idlewild on 2006-04-08
I'm having some trouble with the latest packages. The screen goes solid white and I get the following error:
```
libGL warning: 3D driver claims to not support visual 0x4b
compiz-aiglx: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
compiz-aiglx: glXBindTexImage failed

```

*Edit:
FIXED: Reinstalled xserver-xorg-driver-i810 and it started working. Strange...

---

### Post by foxy123 on 2006-04-08
After updating to the latest packages from the first page the switcher becomes sticky almost every time I use it. See the screenshot attached.

---

### Post by Juanito on 2006-04-08
On this update, the switcher appears but never disappears :( 

Does anyone have the taskbar as having the 4 desktops showing on KDE? When I go to set number of desktops, it's 1 even though the cube works fairly well... when I set it to 4, it goes back to 1.

I guess I'll wait until everything stabilizes before I use it again :p 
 ](*,) 

Loved it while it lasted though!!

---

### Post by linuxmad on 2006-04-08
> On this update, the switcher appears but never disappears  

This one is easy:
delete splash in windows types from fade's plugin;)

---

### Post by linuxmad on 2006-04-08
About the water effect ... is anyone able to use it?? yet??

---

### Post by tigrux on 2006-04-08
[QUOTE=linuxmad]About the water effect ... is anyone able to use it?? yet??[/QUOTE]


What is that effect?
I have never seen it. :(

---

### Post by zvjer on 2006-04-08
[QUOTE=jstueve]Are you running XGL or Xorg-air?[/QUOTE]
XGL!

---

### Post by jstueve on 2006-04-08
then don't use compiz-aiglx, just use the regular compiz compiz-gnome packages.

---

### Post by mgsfan on 2006-04-09
I can use the raindrops just fine..but if I use the other it works but I have to kill it to get out of it

---

### Post by damagedspline on 2006-04-09
i've installed the 0.0.7 last week which gave me a hard time with it's sudden crashes and the lack of the logout screen. after the upgrade to 0.0.9 it's way-way more stable.
the removal of Splash from the fade plugin as suggested before came in handy to fix the alt-tab switching "issue".
i realy am quite pleased with the way my desktop looks and feels after the aiglx+compiz update, gandalfn and iXce - thank u both.

only 3 problems left (which probably won't be solved with current Xorg7.0):
1) libGL warning: 3D driver claims to not support visual 0x4b
     ---whats the point of indirect accelation if the driver recognize none to 
          use
2) hibernation restore
     ---never worked on my ](*,) ATI Radeon IGP340M, and probably never 
         will
3)while using aiglx+compiz, when i switch to another console and return to the graphical session - everything freezes, the only thing that worked is pressing ctrl-alt-delete several times, it looks stuck but it actually boot cleanly...

ubuntu dapper on a Compaq Evo N1020v

---

### Post by Jingo on 2006-04-09
Am I the only one experiencing troubles with Firefox Flash and xorg-air ?

Everytime I open up a website containing flash, firefox quits, when running xorg-air, not with ubuntu xorg ! And with or without compiz loaded.
:-k

---

### Post by simplyw00x on 2006-04-09
same. Really, really annoying.

---

### Post by kecci on 2006-04-09
[QUOTE=damagedspline]2) hibernation restore
     ---never worked on my ](*,) ATI Radeon IGP340M, and probably never 
         will
3)while using aiglx+compiz, when i switch to another console and return to the graphical session - everything freezes, the only thing that worked is pressing ctrl-alt-delete several times, it looks stuck but it actually boot cleanly...
[/QUOTE]

For the hibernation restore issue, you can try to modify /etc/acpi/prepare.sh by adding at the top of it
```
killall compiz-aiglx
killall gnome-window-decorator-aiglx
killall zenity
```
and also modify /etc/acpi/resume.sh by adding at the bottom
```
sudo -u yourusername compiz-aiglx-start
```

It works on my laptop (dell 630m with i915 graphic card), but it breaks decoration for the open windows.
I'm also having the console switching bug, for which i haven't found any soultion yet...

---

### Post by damagedspline on 2006-04-10
[QUOTE=kecci]For the hibernation restore issue, you can try to modify /etc/acpi/prepare.sh by adding at the top of it[/QUOTE]

[QUOTE=kecci]and also modify /etc/acpi/resume.sh by adding at the bottom[/QUOTE]
...didn't work as expected... the lcd backlight is on, but the screen stays black.
i've worked with opensuse and mandriva on this laptop - in their case the screen became garbled and locked the entire system.
the error in my case right now might be connected with the tty switching problems, or the lack of it (maybe switching to tty1 before the mass murder of aiglx).

[QUOTE=kecci]It works on my laptop (dell 630m with i915 graphic card), but it breaks decoration for the open windows.
I'm also having the console switching bug, for which i haven't found any soultion yet...[/QUOTE]
try this: press on the light bulb (the compiz conf thingy) change something and press ok.... when i used 0.0.7 it sometimes resored the missing window-decoration, but the other thing that happend was that the windows started ignoring the panel's existance when moved or maximized

---

### Post by murataht on 2006-04-10
First thanks everybody for making effort to get this working!!!

I have been using aiglx + compiz  with i810 driver and it was so cool before i upgrade to the new version the other day. I upgraded to the 
                   compiz-aiglx_0.0.7-0ubuntu6_i386.deb
                  compiz-aiglx-gnome_0.0.7-0ubuntu6_i386.deb
                  xserver-xorg-air-core_0.99.1-0ubuntu2_i386.deb
and i also upgraded the dapper. then the window in the gnome stop moving. I mean i can not move the windows with mouse leftbutton-drag. I also tried the alt+mouse-drag thing, but it didn't work either. then I tried the switcher alt-tab it didn't work either. but my alt key is working perfectly. and my mouse is working perfectly too. I tried to downgrade it, and use the gnome-session provided in this thread, but nothing worked. 

today I tried the newest packages, still it is not working either. so, if anybody experienced the same problem, or  know something about that it would be great. any suggestion will do. thanks in advance.

---

### Post by Jingo on 2006-04-10
Is the move plugin enabled?

---

### Post by murataht on 2006-04-10
[QUOTE=Jingo]Is the move plugin enabled?[/QUOTE]
thanks man. I checked the plugins and the "move" is not there. I enabled it, and it is working now. :oops:

---

### Post by foxy123 on 2006-04-10
I've got a problem with Quod Libet Album Cover Display plugin and MacSlow's clock. In  both cases I have only a white square instead of the picture. Does anyone experience that?

---

### Post by dabear on 2006-04-10
[QUOTE=foxy123]I've got a problem with Quod Libet Album Cover Display plugin and MacSlow's clock. In  both cases I have only a white square instead of the picture. Does anyone experience that?[/QUOTE]
Yeah, me too. I solved the issue in the cairo clock by moving it a bit around and then changing the size of the clock in properties

---

### Post by dudus on 2006-04-10
Does it work for ati radeon 9200SE?
It seems that XGL work for every ati card over 9200SE.
Bad luck?

---

### Post by dabear on 2006-04-10
[QUOTE=dudus]Does it work for ati radeon 9200SE?
It seems that XGL work for every ati card over 9200SE.
Bad luck?[/QUOTE]
Oh boy, if you get it working under that card, PLEASE PM me. I haven't had any luck installing neither xgl+compiz nor aiglx+compiz with that card on my desktop pc. However, aiglx+compiz runs smooth on my intel 810, so I really don't care :D

---

### Post by Tuonorosso on 2006-04-11
Hi all.

I've a problem, i don't have the compiz-aixgl.desktop.

so, i try to do: compiz-aixgl-start and i have this message:

/usr/bin/compiz-aiglx: Root visual is not a double buffered GL visual
/usr/bin/compiz-aiglx: Failed to manage screen: 0
/usr/bin/compiz-aiglx: No managable screens found on display :0.0


Can you help me?

Thanks

---

### Post by murataht on 2006-04-11
[QUOTE=Tuonorosso]Hi all.

I've a problem, i don't have the compiz-aixgl.desktop.

so, i try to do: compiz-aixgl-start and i have this message:

/usr/bin/compiz-aiglx: Root visual is not a double buffered GL visual
/usr/bin/compiz-aiglx: Failed to manage screen: 0
/usr/bin/compiz-aiglx: No managable screens found on display :0.0


Can you help me?

Thanks[/QUOTE]

if you think, this is the problem of not having "compiz-aixgl.desktop", then here is the copy of it. hope it would be of some help:

[Desktop Entry]
Name=compiz-aiglx
Encoding=UTF-8
Version=1.0
Exec=/usr/bin/compiz-aiglx-start
X-GNOME-Autostart-enabled=true

---

### Post by kronepils on 2006-04-12
[QUOTE=Tuonorosso]Hi all.

I've a problem, i don't have the compiz-aixgl.desktop.

so, i try to do: compiz-aixgl-start and i have this message:

/usr/bin/compiz-aiglx: Root visual is not a double buffered GL visual
/usr/bin/compiz-aiglx: Failed to manage screen: 0
/usr/bin/compiz-aiglx: No managable screens found on display :0.0


Can you help me?

Thanks[/QUOTE]

Do you have "dbe" in your xorg.conf? See the first page.
If you have a ati card, you need the patched driver, again get it from page 1.

Good luck!

---

### Post by kecci on 2006-04-12
Please can someone make a patched version for gnome-session 2.14.1-0 as it is impossible to log out ATM if you upgrade the package...

---

### Post by kecci on 2006-04-12
i'll reply to myself: in gandalfn's package archive there are already both patched gnome-session 2.14.1 and a new version of xserver-xorg-air-core

---

### Post by macewan on 2006-04-13
[QUOTE=Jingo]Am I the only one experiencing troubles with Firefox Flash and xorg-air ?

Everytime I open up a website containing flash, firefox quits, when running xorg-air, not with ubuntu xorg ! And with or without compiz loaded.
:-k[/QUOTE]
Same here, it's very irritating. There is a thread that discusses this - basicly composite doesn't get along with flash with aiglx - or something to that effect.

---

### Post by macewan on 2006-04-13
same here, I've tried to change some of the settings but nothing works

[quote=foxy123]I've got a problem with Quod Libet Album Cover Display plugin and MacSlow's clock. In  both cases I have only a white square instead of the picture. Does anyone experience that?[/quote]

---

### Post by dentaku65 on 2006-04-14
[QUOTE=macewan]same here, I've tried to change some of the settings but nothing works[/QUOTE]

see here ;) 
[http://ubuntuforums.org/showthread.php?t=159580&highlight=cairo-clock](http://ubuntuforums.org/showthread.php?t=159580&highlight=cairo-clock)

---

### Post by bazmonkey on 2006-04-14
For what it's worth to people looking to make this a usable solution, compiz seems to be what's causing the lock when you switch to a virtual terminal.  Or perhaps it is the server, but only when some compositing feature of it (compiz) is actually happening.  I dunno.

Has anyone here tried Metacity with it?  It's wierd that the bulk of the discussion about actually using aiglx is here and not on a Fedora site.  I'm not interested in the different eye-candy so much as whether or not some of these problems go away when compiz isn't in the picture.

---

### Post by Jingo on 2006-04-15
[QUOTE=bazmonkey]For what it's worth to people looking to make this a usable solution, compiz seems to be what's causing the lock when you switch to a virtual terminal.  Or perhaps it is the server, but only when some compositing feature of it (compiz) is actually happening.  I dunno.

Has anyone here tried Metacity with it?  It's wierd that the bulk of the discussion about actually using aiglx is here and not on a Fedora site.  I'm not interested in the different eye-candy so much as whether or not some of these problems go away when compiz isn't in the picture.[/QUOTE]
My problems are related to aiglx and not compiz. (The flash problem)

I start compiz manually from the terminal, this way its more easy to test whether its compiz or aiglx whos buggy!

---

### Post by wiebel on 2006-04-15
[QUOTE=foxy123]After updating to the latest packages from the first page the switcher becomes sticky almost every time I use it. See the screenshot attached.[/QUOTE]

Hi there,

I seem to have the same issue as you're discribing here.
Did you (ore anyone else) find a solution for this?

Cheers,
Joris

---

### Post by iXce on 2006-04-15
For the switcher problem, just remove Splash from you Fade plugin windows_type list in gconf-editor.. (much problems with Quinn's packages or Compiz are listed on compiz.net, and every known solution is listed there too, search feature is your friend :))

---

### Post by wiebel on 2006-04-15
[QUOTE=iXce]For the switcher problem, just remove Splash from you Fade plugin windows_type list in gconf-editor.. (much problems with Quinn's packages or Compiz are listed on compiz.net, and every known solution is listed there too, search feature is your friend :))[/QUOTE]

great, I've got it working :)
Yet another question though;
Is it possible to use transset in a way that al gnome-terminals that are started are default started with a transset 0.75? So I don't have to set it manualy all the time?

Cheers,
Joris

---

### Post by json684 on 2006-04-17
So I tried to find a fix for this bug, with no luck so far: When I minimize a window the representation of it shows up hovering over the bottom panel, and it stays there until it is maximized, and also it is displayed upside down. So any ideas on that? 

And also the editing of the appearance of gnome isnt working for me. When I go to System->Preferences->Theme the menu opens up until I click on anything. And then it registers the click and will change the theme but then the program crashes. I don't know if this is a side effect of compiz, but I suspect it is. My machine has the i915 video set. 

Thanks for the Howto. It was awesome! And now I got Linux going, woo hoo!!

---

### Post by FISH on 2006-04-17
[QUOTE=json684]So I tried to find a fix for this bug, with no luck so far: When I minimize a window the representation of it shows up hovering over the bottom panel, and it stays there until it is maximized, and also it is displayed upside down. So any ideas on that? 

And also the editing of the appearance of gnome isnt working for me. When I go to System->Preferences->Theme the menu opens up until I click on anything. And then it registers the click and will change the theme but then the program crashes. I don't know if this is a side effect of compiz, but I suspect it is. My machine has the i915 video set. 

Thanks for the Howto. It was awesome! And now I got Linux going, woo hoo!![/QUOTE]

I get the same upside down windows, but in my opinion its to big and ugly anyways so i turned it off. I don't know how to turn off opaque windows. I tried to turn off focus but that didn't help . i don't know how to turn it off, but im getting used to it

---

### Post by Senori on 2006-04-18
[QUOTE=json684]So I tried to find a fix for this bug, with no luck so far: When I minimize a window the representation of it shows up hovering over the bottom panel, and it stays there until it is maximized, and also it is displayed upside down. So any ideas on that? 

And also the editing of the appearance of gnome isnt working for me. When I go to System->Preferences->Theme the menu opens up until I click on anything. And then it registers the click and will change the theme but then the program crashes. I don't know if this is a side effect of compiz, but I suspect it is. My machine has the i915 video set. 

Thanks for the Howto. It was awesome! And now I got Linux going, woo hoo!![/QUOTE]
That's the miniwin plugin. You can disable the plugin through the usual process.

If you like having little graphical representations of the applications, though, you can switch the "runs_on_aiglx" option in the plugin's gconf, so that they aren't upside-down.

---

### Post by lorenzo on 2006-04-18
Hi,
I followed exactly the instructions on page 1. I have an ati radeon igp320 (oss driver "radeon"). 
As other people in this forum I am stuck at this point:

~$ compiz-aiglx-start
/usr/bin/compiz-aiglx: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz-aiglx: Failed to manage screen: 0
/usr/bin/compiz-aiglx: No managable screens found on display :0.0

and I have no window decorations at all. Any suggestion? ](*,)

Thanks,
Lorenzo

---

### Post by Jingo on 2006-04-18
[QUOTE=lorenzo]Hi,
I followed exactly the instructions on page 1. I have an ati radeon igp320 (oss driver "radeon"). 
As other people in this forum I am stuck at this point:

~$ compiz-aiglx-start
/usr/bin/compiz-aiglx: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz-aiglx: Failed to manage screen: 0
/usr/bin/compiz-aiglx: No managable screens found on display :0.0

and I have no window decorations at all. Any suggestion? ](*,)

Thanks,
Lorenzo[/QUOTE]
Color-depth ?

Should be 16bpp for radeon driver !
And ... gandalf compiz packages seems to give troubles on radeon (on mine 7500 it does), so you might consider iXce's from [http://compiz.net](http://compiz.net)

---

### Post by gandalfn on 2006-04-18
First sorry for later response but haven't many time for compiz-aiglx :( 

I just updated first page with latest compiz-aiglx and xorg-air packages this debs needs now latest mesa and dri kernel modules, moreover you need to start xorg-aiglx in 16 depth it's necessary, all explain are in first page.

the compiz-aiglx is now compatible with official compiz package, i'll just post the patch in compiz mailing list. If accepted it's the last compiz-aiglx package. 

have fun

---

### Post by jstueve on 2006-04-18
great work, **gandalfn** I reinstalled using the instructions on the first page, and things are working again.  

Can you explain why the depth has to be 16 instead of 24?  I just notice a bit of unsharpness on some fonts, might just be an illusion.

So after this patch is accepted into the compiz CVS, we should be able to use compiz-vanilla from reggaemanu's repo, or from quinn's repo?

again, great job.

EDIT: Video (using totem-xine and xshm driver) is playing fullspeed in a window and full screen with this update... woo!  I can move to Compiz fulltime. :D

---

### Post by tvon on 2006-04-18
This is driving me nuts.  I followed your new instructions but I'm getting the famous mesa error:

compiz-aiglx: No GLXFBConfig for default depth, this isn't going to work.
compiz-aiglx: Failed to manage screen: 0
compiz-aiglx: No managable screens found on display :0.0

However I do have the latest mesa packages from the compiz.info repo:

tvon@leo:~$ dpkg -l | grep mesa
ii  libgl1-mesa                            6.5.1-0ubuntu1  A free implementation of the OpenGL API -- GLX r
ii  libgl1-mesa-dev                        6.5.1-0ubuntu1  A free implementation of the OpenGL API -- GLX d
ii  libgl1-mesa-dri                        6.5.1-0ubuntu1  A free implementation of the OpenGL API -- DRI m
ii  libglu1-mesa                           6.5.1-0ubuntu1  The OpenGL utility library (GLU)
ii  libglu1-mesa-dev                       6.5.1-0ubuntu1  The OpenGL utility library -- development suppor
ii  libosmesa6                             6.5.1-0ubuntu1  Mesa Off-screen rendering extension
ii  mesa-common-dev                        6.5.1-0ubuntu1  Developer documentation for Mesa
ii  mesa-utils                             6.3.2-0ubuntu6  Miscellaneous Mesa GL utilities


I've rebooted, re-installed mesa... what gives?

---

### Post by wiebel on 2006-04-18
Hi,

Is there a way to get flash working with the latest release?
In the previous release I could run in 24bits mode and flash worked like a charm.
Now, with the latest release, I have to run in 16 bits modes and firefox crashes as soon as I open an flash thingie. Hope someone can help here :)

Cheers,
Joris

---

### Post by bhaagensen on 2006-04-18
tvon, did you follow ALL the instructions on the first page. In particular did you download,  compile, and install the latest kernel drm-modules. And the updated xserver/driver ? You may also need to restart, at least reload the i915 kernel-module.
 
wiebel, hmm. What version flash are you using. I'm using 7.0r63 (and epiphany) with no issues. The 16 depth limitations still annoying though.

gandalfn, thanks for providing such great packages and thourough instructions. Particulary including uninstall instructions is nice if one "regrets".

---

### Post by psyke83 on 2006-04-18
Hi,

I've installed and set up AIGLX and Compiz from the latest instructions and things are working fine. Before this update I was running AIGLX in 24 bit depth (on an 865G). My problem is that under 16 bit resolution, xv output shows a series of blue dots over the picture, which wasn't present at 24bit depth. Can someone help? The xshm driver's output when fullscreen is pretty bad, the picture looks pixellated.

Regards,
psyke83

---

### Post by tvon on 2006-04-18
[QUOTE=bhaagensen]tvon, did you follow ALL the instructions on the first page. In particular did you download,  compile, and install the latest kernel drm-modules. And the updated xserver/driver ? You may also need to restart, at least reload the i915 kernel-module.
[/QUOTE]

Yup, I did it all and even rebooted to make sure the new module was being used.

FWIW, I tried compiz CVS from source (unpatched, oops) about a week ago and promptly uninstalled it, but since then I have not been able to get compiz-aiglx to work, though it had been working well for me before that (and for along time!).

*sigh*, I wonder what I broke...

**update:**

Attaching my log and conf

---

### Post by tigrux on 2006-04-19
Before upgrading xorg-xserver-i810, libdrm2 and the other stuff, glxgears reported
1700 frames per second.

After the upgrade, it was degraded to just 700 fps

Is it normal, or am forgetting something?

My card is an intel 950 which uses i915.

---

### Post by Jingo on 2006-04-19
Gandalf ... what about radeon driver ?

---

### Post by Tharna on 2006-04-19
[QUOTE=Jingo]Gandalf ... what about radeon driver ?[/QUOTE]

I would be interested in that too.

---

### Post by dentaku65 on 2006-04-19
[QUOTE=psyke83]Hi,

I've installed and set up AIGLX and Compiz from the latest instructions and things are working fine. Before this update I was running AIGLX in 24 bit depth (on an 865G). My problem is that under 16 bit resolution, xv output shows a series of blue dots over the picture, which wasn't present at 24bit depth. Can someone help? The xshm driver's output when fullscreen is pretty bad, the picture looks pixellated.

Regards,
psyke83[/QUOTE]

Same thing here; I've tried to put xorg.conf with 24bit but the top windows will disappear :-?

---

### Post by nappsoft on 2006-04-19
[QUOTE=tvon]This is driving me nuts.  I followed your new instructions but I'm getting the famous mesa error:

compiz-aiglx: No GLXFBConfig for default depth, this isn't going to work.
compiz-aiglx: Failed to manage screen: 0
compiz-aiglx: No managable screens found on display :0.0

However I do have the latest mesa packages from the compiz.info repo:
[/QUOTE]

I have the same problem with my i915-notebook (newest drm, your driver, newest mesa packages, ...). However: If I use the old compiz packages (0.0.9-0ubuntu2 instead of ubuntu3) with the new driver and the new xserver-xorg-air-core, it's all working again!

Also my Xserver now (since the mesa updates) crashes (and restarts) after stopping glxgears.

Edit: The update of the other packages fixed some older problems for me: I wasn't able to switch back to the X-Server after Console-Switching (Ctrl+Alt+F1). And: I'm impressed, how smoth aiglx+compiz runs on my i915 notebook... I even made a demo-video to impress my friends: I want them to switch to linux :-)

---

### Post by dentaku65 on 2006-04-19
Just a queston on the first page.
is staed to use this repo:

> deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

But on the reggeamanu described here [http://compiz.ed3n.com/viewtopic.php?id=74](http://compiz.ed3n.com/viewtopic.php?id=74)
is stated about aiglx to use this:
> deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main aiglx

any idea?

---

### Post by Kannisto on 2006-04-19
After yesterday console switching finally works on my i830M. Expect for one little problem, after switching tty:s hardware accelerated video freezes X (Hardware accelerated video has some black dots, but I lack some serious horsepower for using xshm and it usually works just fine). I've had this problem before with hibernate but I can't remember if I resolved it or how I did it.

---

### Post by Jingo on 2006-04-19
Did an update using
deb http:/xgl.compiz.info dapper main aiglx

Works great ...
and always a BUT.... now it burns my gpu. The fan on my laptop is always on now, due to gpu getting very hot, I didn't have that before !?
Performance increase is not that much better for it to use more power!!! :-k :-?

---

### Post by dentaku65 on 2006-04-19
[QUOTE=Jingo]Did an update using
deb http:/xgl.compiz.info dapper main aiglx

Works great ...
and always a BUT.... now it burns my gpu. The fan on my laptop is always on now, due to gpu getting very hot, I didn't have that before !?
Performance increase is not that much better for it to use more power!!! :-k :-?[/QUOTE]

Mee too; I've noted that with this last version of AIGLX/Compiz with mesa and drm that the performance is not so great than before; 16bit is really not good for me and I have a lot of flickering using GL apps (eg glxgears); maybe I'll do a roll back :-k

---

### Post by tvon on 2006-04-19
FYI, the glxgears app comes from mesa-utils which is not rebuilt against the latest mesa packages.  Maybe if you rebuilt it, the performance would be better?

---

### Post by Jingo on 2006-04-19
[QUOTE=tvon]FYI, the glxgears app comes from mesa-utils which is not rebuilt against the latest mesa packages.  Maybe if you rebuilt it, the performance would be better?[/QUOTE]
I am not talking about glxgears performance. I am talking about overall performance, moving windows around etc.
The improvement is not nearly so great that it should burn my gfx-card hot !
On a laptop, this is quite crucial. Hot gpu = greater power consumption = BAD !
The performance his quite good before the update, and the power consumption fair ! So I guess the new mesa or compiz doesn't let the gpu sleep enough.

---

### Post by linuxmad on 2006-04-19
Why is compiz only able to run with 16 million colors?
Don't know if it is just me, but it is uggly. For instances the cairo clock looks really uglly and the fonts aren't as smooth as before.

---

### Post by tigrux on 2006-04-19
[QUOTE=linuxmad]Why is compiz only able to run with 16 million colors?
Don't know if it is just me, but it is uggly. For instances the cairo clock looks really uglly and the fonts aren't as smooth as before.[/QUOTE]

>>> 2**16
65 536


>>> 2**24
16 777 216

---

### Post by tigrux on 2006-04-19
I have more information about the changes in the 3D performance

Before upgrading, using either xorg or xorg-air:
glx reported 1700 fps

After the upgrade, using xorg (direct rendering):
glx reports 700 fps

After th upgrade, using xorg-air and compiz (indirect rendering):
glx reported 1000 fps


Isn't it strange?

Why the performance has decayed so much?
And why is it working better when using indirect rendering?

---

### Post by tvon on 2006-04-19
[QUOTE=nappsoft]I have the same problem with my i915-notebook (newest drm, your driver, newest mesa packages, ...). However: If I use the old compiz packages (0.0.9-0ubuntu2 instead of ubuntu3) with the new driver and the new xserver-xorg-air-core, it's all working again![/QUOTE]

I re-built the ubuntu3 package from source ([here]("http://gandalfn.club.fr/ubuntu/compiz-aiglx_0.0.9-0ubuntu3.tar.gz")) and it all works fine, though it does seem a bit choppier than it was with the old mesa.

---

### Post by scav on 2006-04-19
why does it only work with 16bit now? before it worked with 24?

---

### Post by wiebel on 2006-04-19
[QUOTE=bhaagensen]
wiebel, hmm. What version flash are you using. I'm using 7.0r63 (and epiphany) with no issues. The 16 depth limitations still annoying though.
[/QUOTE]

Hi, 

Thanks for your reply
I'm running Shockwave Flash 7.0 r25.
What do you mean with epiphany?

Cheers,
Joris

---

### Post by enjoy_linux on 2006-04-19
[QUOTE=wiebel]Hi, 

Thanks for your reply
I'm running Shockwave Flash 7.0 r25.
What do you mean with epiphany?

Cheers,
Joris[/QUOTE]


have the same problem! firefox crashs but epiphany has no problem with flash!

any idea?

---

### Post by nappsoft on 2006-04-19
[QUOTE=tvon]I re-built the ubuntu3 package from source ([here]("http://gandalfn.club.fr/ubuntu/compiz-aiglx_0.0.9-0ubuntu3.tar.gz")) and it all works fine, though it does seem a bit choppier than it was with the old mesa.[/QUOTE]

If I add LD_PRELOAD=/usr/lib/libGL.so.1.2 before aiglx-compiz-start, it works for me. (But the color of my window-decoration looks somewhat uggly, perhaps because of 16 bit...)

---

### Post by tvon on 2006-04-19
[QUOTE=scav]why does it only work with 16bit now? before it worked with 24?[/QUOTE]

gnome-window-decorator-aiglx seems to be the only thing that requires 16 here, otherwise it works fine at 24..

---

### Post by wiebel on 2006-04-19
[QUOTE=tvon]gnome-window-decorator-aiglx seems to be the only thing that requires 16 here, otherwise it works fine at 24..[/QUOTE]

Is it possible to use another window decorator? metacity for example? :)

Cheers,
Joris

---

### Post by wiebel on 2006-04-19
yet another question :)

If I use mplayer -vo xv I get blue-isch haze through my video.
when using -vo x11 all seems fine. Is there a way to use xv?

Cheers,
Joris

---

### Post by conmiweb on 2006-04-20
I'm doing the same questions than wiebel, can somebody answer them.?
I'm running perfectly with a 855GM intel graphics. But it has some bugs:

-Task switcher, gets frozen, and i've to restart gdm.
-Miniwin doesn't works.
-Opening a Flash page in firefox, it closes firefox.
-In Wine, i get this error : *libGL warning: 3D driver claims to not support visual 0x4b*
-All the other...perfectly, can somebody hrelp me with theese errors?
EDIT:
-VMware doesn't works.

What I've to do if I want to use gnome without AIGLX, for use the programs that doesn't work?until a new release of aiglx correect the bugs.

---

### Post by alimh on 2006-04-20
I'm also running an 855gm card and... it is impressive! So smooth!

[QUOTE=conmiweb]
-Task switcher, gets frozen, and i've to restart gdm.[/QUOTE]
If by "frozen" you mean the task switcher won't dissappear but everything else works, then try this:
Open gconf-editor and navigate to Apps->Compiz->Plugins->Fade->Screen0, and remove splash from the "window types" key.
[QUOTE=conmiweb]
-Miniwin doesn't works.[/QUOTE]
I disabled it for now.
[QUOTE=conmiweb]
-Opening a Flash page in firefox, it closes firefox.[/QUOTE]
Type "sudo gedit /usr/bin/firefox" and add the line so your file now should look like this:
```

export XLIB_SKIP_ARGB_VISUALS=1
MOZ_DIST_BIN="/usr/lib/mozilla-firefox"
MOZ_PROGRAM="/usr/lib/mozilla-firefox/firefox-bin"

```
And i'm not sure about Wine or VMWare.

Hope this helps. Credit goes to others on the forum. :cool:

---

### Post by bhaagensen on 2006-04-20
[QUOTE=wiebel]Hi, 

Thanks for your reply
I'm running Shockwave Flash 7.0 r25.
What do you mean with epiphany?

Cheers,
Joris[/QUOTE]

epiphany is "the" gnome-browser. It's quite nice... Anyway I just discovered that firefox crashes also for me, so...another good reaon for running epiphany:)

---

### Post by hanexar on 2006-04-20
For firefox crashs, it seems there's a conflict between flash and the composite extension.

See this tread for work around.
[http://www.ubuntuforums.org/showthread.php?t=142721](http://www.ubuntuforums.org/showthread.php?t=142721)

---

### Post by linuxmad on 2006-04-20
Running vmware from console:
root@ubuntu:/home/jt/vmware-any-any-update101# vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
root@ubuntu:/home/jt/vmware-any-any-update101#

Any thoughts??:confused:

---

### Post by jstueve on 2006-04-20
its been asked and answered elsewhere... but the jist is to mv the existing files, (libgcc_s.so.1 and libpng12.so.0) and rename them.  (I think vmware then uses the default library...)

```

sudo mv /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1.vm
sudo mv /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0 /usr/lib/vmware/libpng12.so.0/libpng12.so.0.vm

```

Try and see if it works... if not:
```

sudo ln -sf /usr/lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
sudo ln -sf /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0

```

---

### Post by tonyo46 on 2006-04-20
Hello

thanks a lot for this very good HowTo !
I installed it on my laptop and it works quite fine. I just have a problem with totem because I think I didn't understand what it is necesary to make it work well...
I have to replace the line "#video.driver:auto" by which line ?

I send a screenshot of what I see. I put the blue points myself with gimp.
[[IMG]http://img212.imageshack.us/img212/5520/pantallazo9fp.th.png[/IMG]](http://img212.imageshack.us/my.php?image=pantallazo9fp.png)

tonyo

---

### Post by jstueve on 2006-04-20
```
video.driver:xshm

```

---

### Post by tonyo46 on 2006-04-20
[QUOTE=jstueve]video.driver:xshm[/QUOTE]
yes, that's it...

---

### Post by linuxmad on 2006-04-20
```


sudo mv /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1.vm 
sudo mv /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0 /usr/lib/vmware/libpng12.so.0/libpng12.so.0.vm


```

YEP ....works like a charm=D> 
Thanks

---

### Post by TheTilde on 2006-04-21
THANK YOU.
Hi all
I just registered to say big thanks to Gandalfn and others who helped making this how-to.
It's working impressively with my DELL610 + i915.

I'd like to point just some quirks I came across:

- nothing worked until I rebooted, it's surely related with the reload of the i915 driver. That's nothing, but I think it's important to noobs like me, because I was going to mess with the .debs if I didn't think of rebooting.

- during the part where I "dpkged -i" the xserver*deb, I had to remove the existing official packages.

Anyway now it works fine. I hope it will be possible to run it at 24bit in a next release.

Thank you Mister Gandalfn

---

### Post by artelsj on 2006-04-21
I followed the tutorial in the first post to get an idea what Compiz and aiglx look like. I got everything to work but after a while I decided to uninstall the packages again and run a more stable environment for the time being. Uninstall succeeded and everything now works as it should, except for an error in synaptic: there is one package (compiz-aiglx-gnome) that I can't remove from my system (it's listed in the "broken" category in synaptic), upon trying I get the following error:

[INDENT]E: compiz-aiglx-gnome: subprocess post-removal script returned error exit status 1[/INDENT]

When doing "sudo apt-get remove compiz-aiglx-gnome", i get the following output:

[INDENT]sudo apt-get remove compiz-aiglx-gnome
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED
  compiz-aiglx-gnome
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 217kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 111945 files and directories currently installed.)
Removing compiz-aiglx-gnome ...
Uninstalling gconf schemas...
Resolved address "xml:merged:/etc/gconf/gconf.xml.defaults" to a writable configuration source at position 0
I/O warning : failed to load external entity "/usr/share/gconf/schemas/compiz.schemas"
Failed to open `/usr/share/gconf/schemas/compiz.schemas': No such file or directory
dpkg: error processing compiz-aiglx-gnome (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 compiz-aiglx-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)[/INDENT]

Any way to fix this?

---

### Post by ljsoares on 2006-04-21
[QUOTE=artelsj]I followed the tutorial in the first post to get an idea what Compiz and aiglx look like. I got everything to work but after a while I decided to uninstall the packages again and run a more stable environment for the time being. Uninstall succeeded and everything now works as it should, except for an error in synaptic: there is one package (compiz-aiglx-gnome) that I can't remove from my system (it's listed in the "broken" category in synaptic), upon trying I get the following error:

[INDENT]E: compiz-aiglx-gnome: subprocess post-removal script returned error exit status 1[/INDENT]

When doing "sudo apt-get remove compiz-aiglx-gnome", i get the following output:

[INDENT]sudo apt-get remove compiz-aiglx-gnome
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED
  compiz-aiglx-gnome
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 217kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 111945 files and directories currently installed.)
Removing compiz-aiglx-gnome ...
Uninstalling gconf schemas...
Resolved address "xml:merged:/etc/gconf/gconf.xml.defaults" to a writable configuration source at position 0
I/O warning : failed to load external entity "/usr/share/gconf/schemas/compiz.schemas"
Failed to open `/usr/share/gconf/schemas/compiz.schemas': No such file or directory
dpkg: error processing compiz-aiglx-gnome (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 compiz-aiglx-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)[/INDENT]

Any way to fix this?[/QUOTE]



I found a way to get passed this.

1st: dpkg-deb --extract "deb package name" /newdir
2nd: copy compiz.schemas from the extracted deb package to /usr/share/gconf/schemas/ 
3rd:  apt-get -f install

this worked for me hopes it works for you.

---

### Post by kiddyfurby on 2006-04-21
Thanks for the work!!
AIGLX runs on 855GME much smoother than XGL in dapper respo

I messed up my compiz before (flight 6), so I did a clean install of dapper beta
Will these packages work in dapper beta?

---

### Post by iXce on 2006-04-21
Gandalfn built new packages for xorg-aiglx and gnome session.

Just use the packages in this repo :

```
deb http://xgl.compiz.info/ dapper main aiglx
```

And upgrade :)

---

### Post by dengar on 2006-04-21
I followed the tutorial, and it installed alright (there were still some packets I needed to get for some dependencies even after doing the full upgrade however). Anyways, I restarted, however I have two problems. I don't have the main program bar (the one on the top of windows that lets you move the windows around) and I don't know how to control any of the effects besides opacity. I keep hearing about a fix for the lack of window decorations (although the gnome-window-decorator for aiglx is running) but I can't find the instructions of what actually, and specifically to do. It might also be nice to post the instructions on the main page for others in the future. 40 thread pages to look through is quite a bit.

As for whether the other extensions are there, apart from gconf how can I tell whether an extension is loaded/whether its going to work?

---

### Post by reedlaw on 2006-04-22
I am getting an error with the compiz-aiglx-gnome package:
```
Errors were encountered while processing:
 compiz-aiglx-gnome_0.0.9-0ubuntu3_i386.deb

```
I tried copying the schemas manually as found in this thread but it still didn't work. Any other workarounds?

---

### Post by nappsoft on 2006-04-22
[QUOTE=dengar] I don't have the main program bar (the one on the top of windows that lets you move the windows around) and I don't know how to control any of the effects besides opacity. I keep hearing about a fix for the lack of window decorations (although the gnome-window-decorator for aiglx is running) but I can't find the instructions of what actually, and specifically to do.
[/QUOTE]

You can move the window by pressing alt and clicking with your mouse onto the window. ThereAnd: Is your Xserver running in 16bit-mode? With 24bit compiz works, but the gnome-window-decorator doesn't (it runs, but is not visible. So with 24bit I have exactly the same "symptoms").

You can find details about keyboard shortcuts here: [http://en.opensuse.org/Compiz](http://en.opensuse.org/Compiz)

---

### Post by artelsj on 2006-04-22
[QUOTE=ljsoares]I found a way to get passed this.

1st: dpkg-deb --extract "deb package name" /newdir
2nd: copy compiz.schemas from the extracted deb package to /usr/share/gconf/schemas/ 
3rd:  apt-get -f install

this worked for me hopes it works for you.[/QUOTE]

This worked. Thanks!

---

### Post by mkools on 2006-04-22
Hope someone can help me out, I can't get it to work on my notebook.
(Thinkpad Z60m with Intel915 graphics PCI-E).

I followed the entire manual, starting from a clean Ubuntu Dapper Beta release, and completed the guide without running into any errors.

Now, when I restart GDM it starts, but when I for example start a terminal it sits in the upperleft corner of my screen without any borders so I can't move it.
I checked my Xorg.log.0 and it keeps saying:

(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29

I get the same message when running glxgears although glxgears works and fast.

This is my Xorg device section, my card should support it:

> 
Section "Device"
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Driver          "i810"
Option  "XAANoOffscreenPixmaps"
        BusID           "PCI:0:2:0"
EndSection


Hope somebody can help me out on this, thanks in advance!

---

### Post by foureight84 on 2006-04-22
I tried this on my latitude x1 and it doesn't work. jsut crashes/

---

### Post by foxy123 on 2006-04-22
[QUOTE=iXce]Gandalfn built new packages for xorg-aiglx and gnome session.

Just use the packages in this repo :

```
deb http://xgl.compiz.info/ dapper main aiglx
```

And upgrade :)[/QUOTE]
I did that and now I cannot make window-decoration work... how can I roll back? What packages I need to downgrade? it worked fine with the previous version....

---

### Post by mkools on 2006-04-22
[QUOTE=mkools]Hope someone can help me out, I can't get it to work on my notebook.
(Thinkpad Z60m with Intel915 graphics PCI-E).

I followed the entire manual, starting from a clean Ubuntu Dapper Beta release, and completed the guide without running into any errors.

Now, when I restart GDM it starts, but when I for example start a terminal it sits in the upperleft corner of my screen without any borders so I can't move it.
I checked my Xorg.log.0 and it keeps saying:

(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29

I get the same message when running glxgears although glxgears works and fast.

This is my Xorg device section, my card should support it:



Hope somebody can help me out on this, thanks in advance![/QUOTE]

Ok, seems that error hasn't to do anything with it, I just forgot to add the plugins with gconf-editor to compiz, I did that and now it works.
The warnings keep coming but I think it's safe to just ignore them.

Performance is amazing, I run the same on my regular workstaiton with a GF6800GT and that is much more slower and choppier than my notebook with I915i.
Even when cubing around the CPU is almost idle!! Great job guys!

Can't stop playing with the effects :)

---

### Post by foureight84 on 2006-04-22
okay, I got it working but I am having several problems.

when i hit alt tab for the task switcher, the task switcher window stays open even after I release the alt tab buttons. I looked in the config and switcher termination is set when <Release>Alt_L. I don't see anything wrong with this, why won't it close after I release alt tab?

Second problem, I run glxgears and I get this error:

```
libGL warning: 3D driver claims to not support visual 0x4b

```

I also notice that glxgears window flickers as well. How do I fix these errors?

---

### Post by dengar on 2006-04-22
[QUOTE=nappsoft]You can move the window by pressing alt and clicking with your mouse onto the window. ThereAnd: Is your Xserver running in 16bit-mode? With 24bit compiz works, but the gnome-window-decorator doesn't (it runs, but is not visible. So with 24bit I have exactly the same "symptoms").

You can find details about keyboard shortcuts here: [http://en.opensuse.org/Compiz](http://en.opensuse.org/Compiz)[/QUOTE]

I followed the guide to the letter, including changing the 24bit thing to 16 bit (unless there was something more that wasn't put in the guide. I suspect the gnome-window-decorator is running because there is a gnome panel that works, it just doesn't show the bar at the top of the windows that usually let me move the window. The alt-click drag also doesn't move the desktop.

---

### Post by dersonbsb on 2006-04-22
If Switcher does not terminate after activating it (ALT+TAB):

    * Run gconf-editor
    * Under apps > compiz > plugins > fade > screen0 > options > window_types remove 'Splash from the list of of window_types

---

### Post by nappsoft on 2006-04-22
[QUOTE=dengar]I followed the guide to the letter, including changing the 24bit thing to 16 bit (unless there was something more that wasn't put in the guide. I suspect the gnome-window-decorator is running because there is a gnome panel that works, it just doesn't show the bar at the top of the windows that usually let me move the window. The alt-click drag also doesn't move the desktop.[/QUOTE]

Which means, that compiz isn't working at all i think... (you should even be able to use the shortcuts gnome-window-decorator-aiglx wasn't running)

what happens, if you tipe "compiz-aiglx --replace" into a terminal? (perhaps with "killall -9 compiz-aiglx" before)

---

### Post by psyke83 on 2006-04-22
dengar,

Open the Compiz AIGLX configuration window and disable transset, trailfocus and miniwin. Does that fix your problem? When I did a fresh reinstall and followed this guide again gnome-window-decorator wouldn't display until I disabled those plugins.

---

### Post by psyke83 on 2006-04-22
I have a question for anyone with an Intel chipset, have you tried running in 24 bit depth? Putting aside the fact that the window decorator doesn't work, try running ppracer in fullscreen - when I try it here I get a terrible black banding effect which makes it almost impossible to see the game. This is caused by the latest Mesa and/or Intel driver, I think.. I'm curious if it happens to other people with Intel cards and not just an 865G chipset like me...

Additionally, does anyone notice that the screen refresh is slightly laggy compared to normal Xorg (for example, scrolling in firefox or any other application)? It's not very laggy, just a bit slower than usual. Disabling wobbly and moving windows around shows a kind of refresh/vsync problem here, does anyone else notice?

---

### Post by foureight84 on 2006-04-22
[QUOTE=dersonbsb]If Switcher does not terminate after activating it (ALT+TAB):

    * Run gconf-editor
    * Under apps > compiz > plugins > fade > screen0 > options > window_types remove 'Splash from the list of of window_types[/QUOTE]

=) i got it! thanks!!!

Does anyone know how to fix that libGL error? my compiz is a little laggy. Here is the error that appears when i run glxgears "libGL warning: 3D driver claims to not support visual 0x4b"

---

### Post by foxy123 on 2006-04-23
I have completely butchered my compiz. It did not work after I updated from the repositories provided in this thread, so I decided to roll back. I removed some packages which were updated (though I am not sure if I found all of them) and installed 
compiz-aiglx_0.0.9-0ubuntu2_i386.deb
compiz-aiglx-gnome_0.0.9-0ubuntu2_i386.deb

But alas, now compiz-aiglx and libgconfd2 consume 100% CPU and nothing happens. Any help please? I want my nicey compiz back!!!

---

### Post by wiebel on 2006-04-23
Hi again,

It seems that trailfocus isn't working for me.
Plugin is loaded but it just doenst work.
Any hints? :)

Cheers,
Joris

---

### Post by conmiweb on 2006-04-23
Hello i've a problem, I love, aiglx and compiz, but, in screensavers and glxgears, it's flickering and glxgears showme this error:

```
libGL warning: 3D driver claims to not support visual 0x4b

```

The same with Wine and GoogleEarth and like....How can I fix this error message that produces flickering?

What happent if I use 24 deph color? Thanks!

---

### Post by dentaku65 on 2006-04-23
Someone as been able to get the stuff described in first page with the new kernel 2.6.15-21? I follow all the steps with this new kernel but I'm not able to get to work.. I've no problem with the kernel 2.6.15-20 :-k

---

### Post by givré on 2006-04-23
It seems that compiz-aiglx has a problem with the new kernel (2.6.15-21)

```


/usr/bin/compiz-aiglx: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz-aiglx: Failed to manage screen: 0
/usr/bin/compiz-aiglx: No managable screens found on display :0.0
/usr/bin/compiz-aiglx: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz-aiglx: Failed to manage screen: 0
/usr/bin/compiz-aiglx: No managable screens found on display :0.0


```

don't know what to do to get it working

---

### Post by dentaku65 on 2006-04-23
... I answer on my issue of the new kernel... you have to do the

> cd drm/linux-core
make

inside with the new kernel otherwise will not work... fixed for me :mrgreen:

---

### Post by givré on 2006-04-23
Thanks for the fix, but how do you do that:
```

cd drm/linux-core
make
```
can you tell me where i can find drm/linux-core?

---

### Post by givré on 2006-04-23
I'm stupid, didn't think that you were speaking about updating the drm module.
Many thanks, it's fix for me.

---

### Post by dengar on 2006-04-23
[QUOTE=nappsoft]Which means, that compiz isn't working at all i think... (you should even be able to use the shortcuts gnome-window-decorator-aiglx wasn't running)

what happens, if you tipe "compiz-aiglx --replace" into a terminal? (perhaps with "killall -9 compiz-aiglx" before)[/QUOTE]

I did yours and then the cd drm/linux-core make thing, and then it started working.

The weird thing is I definitly did a make thing as the guide suggested when I installed it. After I did it this time I noticed a light bulb thing on my gnome bar which I clicked, and then saw that all the plugins were enabled. And then it magically worked.

I am literally amazed. This reaffirms my love of linux. Oh my god aiglx rocks!

(i'm also scarred to update lest I break it... can I somehow save a configuration ala windows system restore in case something later on goes wrong?)

---

### Post by foxy123 on 2006-04-23
[QUOTE=dengar](i'm also scarred to update lest I break it... can I somehow save a configuration ala windows system restore in case something later on goes wrong?)[/QUOTE]
I spent a few hours trying to roll back the last update until I succeeded.

---

### Post by jstueve on 2006-04-23
<strike>I'm down hard... on 21... trying to start on 20 is a blankscreen...

back to metacity for a spell then.</strike>

actually, it was a sessions problem, it is up and working on the new kernel now.

---

### Post by oscarBravo on 2006-04-24
Hi all - after a couple of days' trial and error, compiz is running very nicely here - big up to gandalfn for the hard work!

One small niggle - there doesn't seem to be a window menu; that is, the icon to the left of the title bar of each window doesn't drop down a menu. I can get a similar menu by right-clicking on the title bar, but I don't see options like "move to workspace left/right", or "move to another workspace".

Is this just the way compiz is, or have I broken something?

---

### Post by foxy123 on 2006-04-24
one question: why is new version is supposed to work with 16 depth? though it did not work for me at all (I guess it might be  because I have not followed the howto from the first page but just added the repository and upgraded), but in the process I changed the colour depth and noticed that my wallpaper looked ugly with it. What is the point to downgrade the colour depth? Is there gained more than lost by that?

---

### Post by magicrobotmonkey on 2006-04-24
[QUOTE=dentaku65]Someone as been able to get the stuff described in first page with the new kernel 2.6.15-21? I follow all the steps with this new kernel but I'm not able to get to work.. I've no problem with the kernel 2.6.15-20 :-k[/QUOTE]

Yea just got it running last night. I had previous had xgl+compiz going but it ran like crap. Then I found this thread. Nice! I had some conflicts when install the compiz-gnome-decorator deb, but i just did a force-all and got it in there and now she's beautiful. 

I do have that flash crashes firefox problem though, and that other thread didn't help. I'd like to find a solution to it, but I hate flash anyways so its not all bad.

Also, the little update manager keeps yelling at me to update gnome-session, which I suppose I probably can't do and still have this working, correct? What can/can't I update in the future?


just a note I'm running on an Inspiron 6400 core due with a gig of memory and the intel 945gm chipset and its like butter!

---

### Post by tonyo46 on 2006-04-24
Hello !

I just want to know if Blender works on your computers ? if yes, how can I make it work ?
thanks

tonyo46

---

### Post by t3rror on 2006-04-24
I have just followed these directions, and am in gnome, but all of my windows are without their header bar.  I cannot move, resize, minimize, maximize close any window.  I am also not able to use any of the compiz effects even though they are enabled.

---

### Post by dengar on 2006-04-24
That happened to me, after doing

what happens, if you tipe "compiz-aiglx --replace" into a terminal? (perhaps with "killall -9 compiz-aiglx" before)
(I don't know whether this part actually did something though)

and then

cd drm/linux-core
make

After which it worked. Look for the light bulb icon in the gnome panel (next to the battery icon and the network icon)

---

### Post by conmiweb on 2006-04-25
[QUOTE=conmiweb]Hello i've a problem, I love, aiglx and compiz, but, in screensavers and glxgears, it's flickering and glxgears showme this error:

```
libGL warning: 3D driver claims to not support visual 0x4b

```

The same with Wine and GoogleEarth and like....How can I fix this error message that produces flickering?

What happent if I use 24 deph color? Thanks![/QUOTE]
THANKS!

---

### Post by RAOF on 2006-04-25
[QUOTE=foxy123]one question: why is new version is supposed to work with 16 depth? though it did not work for me at all (I guess it might be  because I have not followed the howto from the first page but just added the repository and upgraded), but in the process I changed the colour depth and noticed that my wallpaper looked ugly with it. What is the point to downgrade the colour depth? Is there gained more than lost by that?[/QUOTE]
16bpp will look uglier, but run faster.  And some cards can't do 3d in full 24bit colour (or, at least, not at a decent resolution), so 16bpp is all they can manage :(

---

### Post by TheEclypse on 2006-04-25
I have a few questions...

Is there any way I can stop the miniwin being enabled everytime I restart? because I dont want to use it, and have to disable it everytime I start the laptop.

And secondly, my window borders arent as pretty as they used to be..is this a result of using 16bit colour depth ?

---

### Post by foxy123 on 2006-04-25
after yesterday's upgrade compiz stopped working for me for good :( I mean I disable the compiz repository and rolled back to the previous version which worked fine. But after dist-upgrade it ceased to do so. 

I tried the howto from the first page without any success. So I wiped out aiglx and compiz from my system for time being. Now metacity works fine but I have a trouble with xfwm4. It is a shame.

I will try again as I love compiz, but either I do something wrong or new version became incompatible with my 855GM chip.

---

### Post by blierp on 2006-04-25
it's working like a charm on my system (compaq evo with radeon mobility 7500) but i don't think it's ready for everyday usage. How do you guys manage with crashing browsers (firefox+flash), buggy opengl applications (lot's of flickering) and weird video issues?
Can't wait untill this becomes mainstream!

---

### Post by foxy123 on 2006-04-25
[QUOTE=blierp]it's working like a charm on my system (compaq evo with radeon mobility 7500) but i don't think it's ready for everyday usage. How do you guys manage with crashing browsers (firefox+flash), buggy opengl applications (lot's of flickering) and weird video issues?
Can't wait untill this becomes mainstream![/QUOTE]
of all you mentioned my only problem was flickering opengl apps, but I do not use them much. I had no problem with video and firefox. Alas until compiz stopped working for me at all...

---

### Post by dengar on 2006-04-25
Two questions:

When I manually move the cube, is there a way to get it to stay in a position and not snap back to one of the desktop screens (I see all those nice screenshots of a cube in the middle of being rotated and what to leave my like that if I wish)

Blierp: I don't have many opengl apps (at least I don't think I do) but I haven't had any stablility issues with compiz, except that if I use alt-tab I can't make the box that opens up go away without force quitting one of the programs it displays. No firefox crashes as of yet, although I haven't stress tested it.

---

### Post by Kannisto on 2006-04-25
[QUOTE=dengar]Two questions:

When I manually move the cube, is there a way to get it to stay in a position and not snap back to one of the desktop screens (I see all those nice screenshots of a cube in the middle of being rotated and what to leave my like that if I wish)

Blierp: I don't have many opengl apps (at least I don't think I do) but I haven't had any stablility issues with compiz, except that if I use alt-tab I can't make the box that opens up go away without force quitting one of the programs it displays. No firefox crashes as of yet, although I haven't stress tested it.[/QUOTE]
The screenshots have been taken with delay option eg. ```
gnome-screenshot --delay=5
```
For the switcher bug, you must remove splash from fade plugin options, browse this thread for more info.

---

### Post by blierp on 2006-04-25
hmm.. i must be doing something wrong then :)
If i open a opengl application (glxgears for example) it "flashes" constantly, couldn't find a fix for that. And if i open a website that contains flash my browser crashes (couldn't find a fix for that either).
Maybe it's because i use the radeon driver while must of you guys are using the intel one.

---

### Post by Permafrost91 on 2006-04-25
I fixed Firefox this way (it's somewhere in this very long thread). Open /usr/bin/firefox with your favorite text editor and add the "export" line as shown below into the Variables section (fairly early on, it was one Page-Down for me).
```

##
## Variables
##
export XLIB_SKIP_ARGB_VISUALS=1
MOZ_DIST_BIN="/usr/lib/firefox"
MOZ_PROGRAM="${MOZ_DIST_BIN}/firefox-bin"
```

---

### Post by t3rror on 2006-04-25
No manageable screens found on 0:0.  

The weird thing is that I have the lightbulb in my toolbar.  When I do a killall -9 compipz-aigolx, there is no process to kill.  This tells me that compiz isn't running.  I am inda lost and have limited GUI functioniality.  I can still operate from the CLI, so it doens't really matter.  This is a development box that I play with.  Hopefully someone can help me solve this issue.  Thanks.

[QUOTE=dengar]That happened to me, after doing

what happens, if you tipe "compiz-aiglx --replace" into a terminal? (perhaps with "killall -9 compiz-aiglx" before)
(I don't know whether this part actually did something though)

and then

cd drm/linux-core
make

After which it worked. Look for the light bulb icon in the gnome panel (next to the battery icon and the network icon)[/QUOTE]

---

### Post by Kannisto on 2006-04-25
On one update stage I had to reboot, try it.

---

### Post by t3rror on 2006-04-25
[quote=Kannisto]On one update stage I had to reboot, try it.[/quote] 
After toying around with it a while, I finally figured that it was the compiz-aiglz autostart in /etc/xdg/ that was causing my problems.

I removed it, and now everything is back as it should be (i am able to resize, move, max/min windows) running aiglx, but with no compiz.  I am going to attempt to manually start compiz and see what happens.....

This is the output when I try to manually start compiz:
```

harrison@ssc-harrisontux2:~$ sudo compiz-aiglx
compiz-aiglx: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
compiz-aiglx: No managable screens found on display :0.0
```

When i attempted to add the --replace to the above command, it went back to no toolbars and no way to move the open windows.  When I attempted to do this with glx, there were some more flags that needed to be called.  Is that the way it should be here?  Thanks!

---

### Post by earth_walker on 2006-04-25
T3error, I'm having exactly the same error messages when I try to start compiz-aiglx. Meanwhile, just running 'metacity' will get you a working desktop while you're troubleshooting.

---

### Post by dengar on 2006-04-25
t3rror did you do the 

cd drm/linux-core
make

thing? After I first completed the guide I didn't have the menu heads either but I think that fixed it. Also, when I upgrade to a new kernel the menu heads left, but to solve that I just reverted back to using the old one in grub.

---

### Post by conmiweb on 2006-04-25
[QUOTE=jstueve]its been asked and answered elsewhere... but the jist is to mv the existing files, (libgcc_s.so.1 and libpng12.so.0) and rename them.  (I think vmware then uses the default library...)

```

sudo mv /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1.vm
sudo mv /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0 /usr/lib/vmware/libpng12.so.0/libpng12.so.0.vm

```

Try and see if it works... if not:
```

sudo ln -sf /usr/lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
sudo ln -sf /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0

```[/QUOTE]

I've updated the new kernel and compiz, and de vmware doesn't works with this trick, how can i run vmware now?please help me Thanks!

---

### Post by t3rror on 2006-04-25
[QUOTE=dengar]t3rror did you do the 

cd drm/linux-core
make

thing? After I first completed the guide I didn't have the menu heads either but I think that fixed it. Also, when I upgrade to a new kernel the menu heads left, but to solve that I just reverted back to using the old one in grub.[/QUOTE]

I have done the step above.  On the other note, how do I start metacity?

---

### Post by Permafrost91 on 2006-04-25
run
```
$ metacity --replace &
```
in gnome-terminal (or whatever else you're using, doing it on tty1/2/3/etc won't work) to start metacity.

On a second note, I'm happy to announce that I can send my computer to Sleep (Suspend-To-RAM) successfully with 0.0.9-ubuntu3 and the 2.6.15-21-686 Dapper kernel! :D

---

### Post by t3rror on 2006-04-25
[QUOTE=Permafrost91]run
```
$ metacity --replace &
```
in gnome-terminal (or whatever else you're using, doing it on tty1/2/3/etc won't work) to start metacity.

On a second note, I'm happy to announce that I can send my computer to Sleep (Suspend-To-RAM) successfully with 0.0.9-ubuntu3 and the 2.6.15-21-686 Dapper kernel! :D[/QUOTE]

i was able to get metacity to run, no problem.  I am still not able to get any of the compiz effects to go though.  Maybe there will be a new build before too long.

---

### Post by jstueve on 2006-04-25
[QUOTE=conmiweb]I've updated the new kernel and compiz, and de vmware doesn't works with this trick, how can i run vmware now?please help me Thanks![/QUOTE]

Did you re-run vmware-install.sh after the new kernel update?

---

### Post by roax on 2006-04-25
Working fine with radeon 7500 mobile. A lot of thanks gandalfn.

---

### Post by galo on 2006-04-25
I'm having a problem with my logout screen with aiglx with 855gm. It doesn't show up but if I click on the screen it shuts down, reboots, etc.. But it's kinda sad having to guess where the buttons are.. :D

Anyone got any ideas ?

I have not read the whole thread, so sorry if this is already been answered.

---

### Post by ruffneck on 2006-04-26
galo,

Did u use the latest patched gnome-session provided by gandalf? If not, give it a try, It might correct the log-out screen problems you are having.

---

### Post by ruffneck on 2006-04-26
Anyone know if it's possible to use compiz-vanilla instead of compiz-aiglx? I am using compiz-aiglx on my laptop with i810 video driver and it works ok for the most part. However, I was just wondering if compiz-vanilla would work better? 

Has anyone tried to swap one for the other?

---

### Post by conmiweb on 2006-04-26
[QUOTE=jstueve]Did you re-run vmware-install.sh after the new kernel update?[/QUOTE]
Thanks! it was!What happens if i set the depth color into 24 ¿?

---

### Post by galo on 2006-04-26
[QUOTE=ruffneck]galo,

Did u use the latest patched gnome-session provided by gandalf? If not, give it a try, It might correct the log-out screen problems you are having.[/QUOTE]

Yeah, I'm using gandalf gnome-session. I even tried to download it again to see if it's the same version I have, and it is the latest.

I also tried to adjust the transparency, but it still doesn't show up. 

Kind of weird, the rest works perfectly.

---

### Post by TheEclypse on 2006-04-26
The world as we know it ends...I was wondering the same thing actually.  From what ive read, some graphics cards cant do it, so you will end up without window borders.

---

### Post by foxy123 on 2006-04-26
I tried to reinstall everything following the howto from the first page. When I try to run compiz I've got the following:
```
:~$ compiz-aiglx
libGL warning: 3D driver claims to not support visual 0x4b
compiz-aiglx: GLX_EXT_texture_from_pixmap is missing
compiz-aiglx: Failed to manage screen: 0
compiz-aiglx: No managable screens found on display :0.0

```

---

### Post by alimh on 2006-04-26
Galo,

I was having the same problem with the same card. I reinstalled the gnome-session package from the first page of this thread. Even though it has the same version number, doing that corrected the problem. Consequently, the update manager will keep telling you to update the gnome-session... just ignore. 

Please post on your results.

---

### Post by nicky.7 on 2006-04-26
It worked for me too. After a reboot.

---

### Post by t3rror on 2006-04-26
```
harrison@ssc-harrisontux2:~$ compiz-aiglx --replace
compiz-aiglx: GLX_EXT_texture_from_pixmap is missing
compiz-aiglx: Failed to manage screen: 0
compiz-aiglx: No managable screens found on display :0.0

```


This is still what I am getting after following the entire tutorial again.  I can restart metacity now, and things are fine.  What is causing compiz to not work correctly?  Thanks.

---

### Post by foxy123 on 2006-04-26
it worked out for me... I have compiz up and running again :), though I had to remove all my old xfce4 config :(

---

### Post by galo on 2006-04-26
[QUOTE=alimh]Galo,

I was having the same problem with the same card. I reinstalled the gnome-session package from the first page of this thread. Even though it has the same version number, doing that corrected the problem. Consequently, the update manager will keep telling you to update the gnome-session... just ignore. 

Please post on your results.[/QUOTE]

Thanks, it works now. :D

The animation is very slow, but it works. And it asks me to update the package, is the new version broken ?

---

### Post by Permafrost91 on 2006-04-26
from my understanding, the gnome-session package posted here is patched to work with compiz while the official dapper package is not:

[see this thread for more info]("http://www.ubuntuforums.org/showthread.php?p=901793&highlight=gnome-session#post901793")

---

### Post by ruffneck on 2006-04-26
[QUOTE=Permafrost91]from my understanding, the gnome-session package posted here is patched to work with compiz while the official dapper package is not:

[see this thread for more info]("http://www.ubuntuforums.org/showthread.php?p=901793&highlight=gnome-session#post901793")[/QUOTE]

precisely!

---

### Post by ZoZo on 2006-04-26
Keep up the good work! Providing the sources is nice, I'm able to modify something the code to make it work with my i915 chipset which has a problem with the normal X.org 7.x. Thanks! ;)

---

### Post by BigErn on 2006-04-26
Gandalfn, first I'd like to say awesome job on this aiglx thing!

Secondly, can you post a deb of your patched radeon driver that has the modification that allows more than 16-bit color? (mentioned on page 27 of this thread).   I made the attempt to compile it myself with your source and your diff, but configure started complaining about not finding the headers for xorg, xproto, etc, and it looked like it would get too hairy for me.  Also, I think others would like to download it.

Thanks

---

### Post by galo on 2006-04-27
[QUOTE=Permafrost91]from my understanding, the gnome-session package posted here is patched to work with compiz while the official dapper package is not:

[see this thread for more info]("http://www.ubuntuforums.org/showthread.php?p=901793&highlight=gnome-session#post901793")[/QUOTE]

Thanks to all, I'm kinda of a newbie regarding aiglx.
Gandalfn says it crashes, and it looks like it, but it doesn't. It just got stuck and didn't show up. You can still select the options if you know their position and if you press Esc you return to your desktop. 
I'm guessing it has something to do with that little animation of your computer shutting down by lowering the brightness, that doesn't like aiglx.

---

### Post by Grey on 2006-04-27
Thanks for the howto... working great on my laptop.  (A few issues of course, but everyone is having them)

---

### Post by alimh on 2006-04-27
I downloaded all the packages from the first post in this thread and everything works great! Now...
How do I get the "latest" compiz packages/plugins? What do I need to download and what do I need to reinstall?
I figured out that when the kernel is upgraded you have to re-"make" in the drm/ folder after downloading the new kernel headers.
HOw bout for compiz?

---

### Post by Balachmar on 2006-04-27
I have followed this how-to and Compiz is working nicely.
However, the switcher (using Alt+Tab) does go away after releasing ALT.
Also I cannot log out using System--> Log Out.
If I do that, it just hangs.
Anybody know how to solve these problems?
Also how can I stop in at the corner of the cube?

---

### Post by ruffneck on 2006-04-27
[QUOTE=Balachmar]I have followed this how-to and Compiz is working nicely.
However, the switcher (using Alt+Tab) does go away after releasing ALT.[/QUOTE]

Remove "Splash" from the Fade plugin  in the Configuration Editor under /apps/compiz

[QUOTE=Balachmar]Also I cannot log out using System--> Log Out.
If I do that, it just hangs.[/QUOTE]

Grab the latest patched gnome-session deb provided by gandalf in the 1st post. Use that to replace the one you've got.

---

### Post by wiebel on 2006-04-27
Hi,

Did anyone got gset-compiz to work with aiglx?
As soon as I click a button it crashes.

Cheers,
Joris

---

### Post by BigErn on 2006-04-27
I tried to revert back to non-aiglx, and I've got some font related problems in gnome apps.  

If I go to gnome-font-properties and set my gnome fonts to monochrome (my preference), in every *gnome* app, all of the text only shows the first word- the remaining words are just not there at all. Gnome panel menus, firefox, everything gnome. Imagine looking at a webpage in Firefox, where each line you only see the first word of the line. There is no problem if I turn hinting back on.

Now if I drag the mouse and "label" over the text area, sometimes some of the words will pop into existence.

It seems like I've tried everything- 'apt-get --reinstall'ing aiglx and compiz packages, dpkg-reconfiguring the originals, etc. Does anyone else have this problem?  Can someone try running gnome-font-properties and selecting monochrome and see if they get this too?

](*,)  ](*,)  ](*,)

---

### Post by Balachmar on 2006-04-28
My earlier problems are solved, but now FireFox crashes with some pages. Probably because of some graphics I guess like Flash.
This is the error I recieve:
The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 118 error_code 8 request_code 145 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Fix for Firefox:
Sorry this thread is too large to read it all...
[http://www.ubuntuforums.org/showpost.php?p=956061&postcount=475]("http://www.ubuntuforums.org/showpost.php?p=956061&postcount=475")

Does anyone know what to do?
And maybe there is a way to start a program from within Gnome that uses compix, to not use compiz?

---

### Post by ruffneck on 2006-04-28
[QUOTE=Balachmar]My earlier problems are solved, but now FireFox crashes with some pages. Probably because of some graphics I guess like Flash.
[/QUOTE]

add:

```
export XLIB_SKIP_ARGB_VISUALS=1
```

to /usr/bin/firefox

Insert that near the top section of the file.

---

### Post by Balachmar on 2006-04-28
OK here I am again...
My next problem has something to do with java.
One program doesn't maximize as it should, creating a large grey area.
And Eclipse, my IDE, doesn't load properly!
It is running, but it looks minimized...
And I can't maximize it.
Also another IDE, netbeans, loads but shows only a white window.
Does anybody know how to fix this java issue?

---

### Post by foxy123 on 2006-04-29
[QUOTE=RAOF]16bpp will look uglier, but run faster.  And some cards can't do 3d in full 24bit colour (or, at least, not at a decent resolution), so 16bpp is all they can manage :([/QUOTE]
I can live with a bit uglier interface. But the problem is with video as it is so poor on 16bpp. I have to make a change in my xorg.conf every time I want to watch a movie :(

---

### Post by ruffneck on 2006-04-29
Has anyone tried replacing the *compiz-aiglx_0.0.9-0ubuntu3_i386.deb* package with *compiz-vanilla-aiglx_0.0.9-0ubuntu2_i386.deb* on their system with success?

Any differences between the two?

---

### Post by afterburn on 2006-04-30
I tried this, but I still get a blank screen whenever I try logging out :( I also have this after the screensaver.

but maybe this is a different problem, because I do see the logout buttons and stuff, and I see my session closing, but I just don't make it to the login screen again...

---

### Post by nik on 2006-05-01
just tried following the howto, but I get no window borders...
When trying to run compiz-aiglx-start from a terminal I get this error:
```

nik@ubuntu:~$ compiz-aiglx-start
/usr/bin/compiz-aiglx: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz-aiglx: Failed to manage screen: 0
/usr/bin/compiz-aiglx: No managable screens found on display :0.0


```

Sorry if this has been answered before, but these threads are getting too long...

---

### Post by t3rror on 2006-05-01
nik,

Hopefully you will get a better response than I did.  I posted about this problem a couple of weeks ago, but recieved no working solution.  Maybe someone will enlighten us.

---

### Post by Permafrost91 on 2006-05-01
Has anyone gotten this to work with Metacity? Red Hat claims that AIGLX should work with metacity ... if so, how could that be set up?

Also, is there a way to start programs on specific desktops?

---

### Post by ruffneck on 2006-05-01
After the latest round of updates (a lot of X11 and xserver-org stuff) the logout  screen stops working again. I think maybe we need another patched gnome-session?

---

### Post by afterburn on 2006-05-01
nik, I also have no borders but can fix this by running this in the terminal:

nohup gnome-window-decorator &

I installed a fresh ubuntu 6.06 beta on saturday and using my ATI 9700 pro I ran these two tutorials like they are:

[https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI](https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI)
[https://wiki.ubuntu.com/xglati](https://wiki.ubuntu.com/xglati)

pretty straightforward, no weird stuff happens when doing so.

and then did not have the borders untill I run the command above. And there's still the no logout problem. It's particularly anoying because the complete system seems to freeze.

i realize i don't do any aiglx stuff, but who knows, maybe this is not an aiglx problem? (or i do use aiglx but just don't understand what aiglx is :) )

---

### Post by no1wantdthisname on 2006-05-01
[QUOTE=nik]just tried following the howto, but I get no window borders...
When trying to run compiz-aiglx-start from a terminal I get this error:
```

nik@ubuntu:~$ compiz-aiglx-start
/usr/bin/compiz-aiglx: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz-aiglx: Failed to manage screen: 0
/usr/bin/compiz-aiglx: No managable screens found on display :0.0


```

Sorry if this has been answered before, but these threads are getting too long...[/QUOTE]

Same, I think the latest update to xorg broke aiglx.  It was working perfectly before I updated.  Damn, bad idea upgrading.

---

### Post by foxy123 on 2006-05-01
[QUOTE=no1wantdthisname]Same, I think the latest update to xorg broke aiglx.  It was working perfectly before I updated.  Damn, bad idea upgrading.[/QUOTE]
you have to follow a howto from the first page. Set default colour depth to 16, compile dri modules etc. I could not make compiz work again without it after a recent upgrade.

---

### Post by no1wantdthisname on 2006-05-01
[QUOTE=foxy123]you have to follow a howto from the first page. Set default colour depth to 16, compile dri modules etc. I could not make compiz work again without it after a recent upgrade.[/QUOTE]

Yeah, I got it working again.  I had to downgrade xserver-xorg-air-core from the newer one in the repo to the one in this thread.  Guess I have to lock version for a while.

---

### Post by t3rror on 2006-05-01
I believe that trying to get this to work will be a total crapshoot until it is officially supported by an ubuntu release.  Otherwise, we will constantly be fighting new updates.

---

### Post by Permafrost91 on 2006-05-01
you just have to recompile the DRI module every time you upgrade your kernel (and X?) ... at least that fixes the problem nik reported with AIGLX not working for me

---

### Post by dentaku65 on 2006-05-01
[QUOTE=no1wantdthisname]Yeah, I got it working again.  I had to downgrade xserver-xorg-air-core from the newer one in the repo to the one in this thread.  Guess I have to lock version for a while.[/QUOTE]

has been worked for me; you must do the upgrade/dist-upgrade with the reggaemenu repos as stated in the first page BEFORE to do the dpkg of the last xorg-air deb

---

### Post by psyke83 on 2006-05-02
Just to let everyone know, it seems that the latest compiz-vanilla works well with Xorg-air :).

First of all you need to download the newest Xorg-air package here (it's not in the repo yet):
[http://gandalfn.club.fr/ubuntu/xserver-xorg-air-core_1.0.99.902-0ubuntu1_i386.deb](http://gandalfn.club.fr/ubuntu/xserver-xorg-air-core_1.0.99.902-0ubuntu1_i386.deb)

Make sure your system is up to date, remove the old compiz packages, then install the vanilla version along with the new Xorg-air package:

```

sudo apt-get remove compiz*
sudo apt-get install compiz-vanilla compiz-vanilla-aiglx compiz-vanilla-gnome gset-compiz
sudo dpkg -i xserver-xorg-air-core_1.0.99.902-0ubuntu1_i386.deb
```

Restart X and it should work.. enjoy :)

---

### Post by foxy123 on 2006-05-02
[QUOTE=psyke83]Just to let everyone know, it seems that the latest compiz-vanilla works well with Xorg-air :).

First of all you need to download the newest Xorg-air package here (it's not in the repo yet):
[http://gandalfn.club.fr/ubuntu/xserver-xorg-air-core_1.0.99.902-0ubuntu1_i386.deb](http://gandalfn.club.fr/ubuntu/xserver-xorg-air-core_1.0.99.902-0ubuntu1_i386.deb)

Make sure your system is up to date, remove the old compiz packages, then install the vanilla version along with the new Xorg-air package:

```

sudo apt-get remove compiz*
sudo apt-get install compiz-vanilla compiz-vanilla-aiglx compiz-vanilla-gnome gset-compiz
sudo dpkg -i xserver-xorg-air-core_1.0.99.902-0ubuntu1_i386.deb
```

Restart X and it should work.. enjoy :)[/QUOTE]

does it support 24 colour depth and this nice 'peeping beind windows' feature?

---

### Post by psyke83 on 2006-05-02
[QUOTE=foxy123]does it support 24 colour depth and this nice 'peeping beind windows' feature?[/QUOTE]
Unfortunately 24 bit colour still doesn't work, but I think that's a problem with the new driver or Mesa. Even with compiz disabled, running ppracer (for example) in 24 bit doesn't work well at all, there's a terrible black flickering across the entire screen that makes it very difficult to see, but 16 bit is fine. Actually, the new drivers and/or Mesa seems to have messed up some of the colours, I hope that gets fixed - but I've had this problem a while, it's not due to these recent updates.

As for the peeping behind windows, yep it seems to work :). Although if I bend the window too far it snaps back and unmaximizes, I'm not sure if that's supposed to happen. The new tray icon is very well laid out and presents all the gconf options in a handy form, and performance seems to have improved considerably - the only slowdown I can recognise is scrolling within applications, every other operation is really smooth (not counting the lack of apparent vsync).

Another great change I've noticed is that flicker from running opengl applications has significantly minimized, so running ppracer fullscreen is perfect, and it's now possible to play movies in totem (xine) without flicker using the opengl renderer:

gedit ~/.gnome2/totem_config
```
 
video.driver:opengl

```

---

### Post by jstueve on 2006-05-02
trying to remove compiz-aiglx-gnome results in this message:
```

Uninstalling gconf schemas...
Resolved address "xml:merged:/etc/gconf/gconf.xml.defaults" to a writable configuration source at position 0
I/O warning : failed to load external entity "/usr/share/gconf/schemas/compiz.schemas"
Failed to open `/usr/share/gconf/schemas/compiz.schemas': No such file or directory
dpkg: error processing compiz-aiglx-gnome (--remove):
 subprocess post-removal script returned error exit status 1
Removing compiz-aiglx ...
Errors were encountered while processing:
 compiz-aiglx-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

any hints?

---

### Post by no1wantdthisname on 2006-05-02
[QUOTE=jstueve]trying to remove compiz-aiglx-gnome results in this message:
```

Uninstalling gconf schemas...
Resolved address "xml:merged:/etc/gconf/gconf.xml.defaults" to a writable configuration source at position 0
I/O warning : failed to load external entity "/usr/share/gconf/schemas/compiz.schemas"
Failed to open `/usr/share/gconf/schemas/compiz.schemas': No such file or directory
dpkg: error processing compiz-aiglx-gnome (--remove):
 subprocess post-removal script returned error exit status 1
Removing compiz-aiglx ...
Errors were encountered while processing:
 compiz-aiglx-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

any hints?[/QUOTE]

I had the same problem.
```
file-roller /var/cache/apt/archives/compiz-aiglx-gnome*deb
```
open data.tar.gz and navigate to /usr/share/gconf/schemas/.
Extract compiz.schemas and move to /usr/share/gconf/schemas/.
It should uninstall now.

I have vanilla compiz working here.  However, gset doesn't work when changing plugin settings.  Any ideas?

---

### Post by foxy123 on 2006-05-02
[QUOTE=jstueve]trying to remove compiz-aiglx-gnome results in this message:
```

Uninstalling gconf schemas...
Resolved address "xml:merged:/etc/gconf/gconf.xml.defaults" to a writable configuration source at position 0
I/O warning : failed to load external entity "/usr/share/gconf/schemas/compiz.schemas"
Failed to open `/usr/share/gconf/schemas/compiz.schemas': No such file or directory
dpkg: error processing compiz-aiglx-gnome (--remove):
 subprocess post-removal script returned error exit status 1
Removing compiz-aiglx ...
Errors were encountered while processing:
 compiz-aiglx-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

any hints?[/QUOTE]
I had a similar problem. I found a solution on the Internet, but I do not remember it exactly. It involves a certain command with /var directory. I guess if you try to google
```
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
you will find it...

---

### Post by psyke83 on 2006-05-02
Here it is:

get a copy of the deb you tried to uninstall, on my system I think it was compiz-aiglx-gnome_0.0.9-0ubuntu3_i386.deb -

```

dpkg-deb -x compiz-aiglx-gnome_0.0.9-0ubuntu3_i386.deb compiz-gnome
sudo cp compiz-gnome/usr/share/gconf/schemas/compiz.schemas /usr/share/gconf/schemas/
sudo apt-get -f install

```

This solution worked for me, but only if I followed those steps *exactly*; "apt-get remove compiz-aiglx-gnome" caused the same problem. It seems the script deletes compiz.schemas when it's not supposed to.

---

### Post by psyke83 on 2006-05-02
[QUOTE=no1wantdthisname]I have vanilla compiz working here.  However, gset doesn't work when changing plugin settings.  Any ideas?[/QUOTE]

It does work, you need to choose "Restart compiz" in the drop-down menu for changes to take effect.

---

### Post by dabear on 2006-05-02
Gandalf, wanna update your guide (and packages) to the newest versions of compiz etc? Highly appriciated

---

### Post by no1wantdthisname on 2006-05-02
[QUOTE=psyke83]It does work, you need to choose "Restart compiz" in the drop-down menu for changes to take effect.[/QUOTE]

Still not working.  Here's what I do:
1. Right click gset tray icon and preferences.
2. Click Plugins.
3. In this example on cube tab, check in the cube.
4. Apply and close.
5. Apply and close.
6. Restart compiz.

When I rotate, it's still outside the cube.
Restarting compiz at this point doesn't make a difference.

If before step 1 I switch to metacity, then doing same as above and restarting compiz makes no difference.
At step 4, only applying without closing and then restarting compiz makes no difference.
Any change I make to any plugin disappears when I go back to preferences.

---

### Post by psyke83 on 2006-05-02
[QUOTE=no1wantdthisname]Still not working.  Here's what I do:
1. Right click gset tray icon and preferences.
2. Click Plugins.
3. In this example on cube tab, check in the cube.
4. Apply and close.
5. Apply and close.
6. Restart compiz.

When I rotate, it's still outside the cube.
Restarting compiz at this point doesn't make a difference.

If before step 1 I switch to metacity, then doing same as above and restarting compiz makes no difference.
At step 4, only applying without closing and then restarting compiz makes no difference.
Any change I make to any plugin disappears when I go back to preferences.[/QUOTE]

I just tried following your instructions, and it worked for me, sorry. I'm not sure what's wrong with your system. In fact, I only needed to click the first apply (your step 4), and dragging the cube showed that it worked immediately. It seems restarting compiz is only necessary to disable or enable plugins, the plugin-specific settings take effect immediately without needing a restart.

Can someone else try this out to help figure out no1wantdthisname's problem?

Edit: in case it helps, I have all plugins except gconf-dump activated. Perhaps your gconf settings were corrupted somehow, making it impossible for the changes to take effect? Try changing your prefs with gconf-editor as a troubleshooting measure.

---

### Post by no1wantdthisname on 2006-05-02
Finally got it working.  I had to unset all compiz keys.
Here's the command for whoever has the same problem.  Note: you lose all current settings.
```
gconftool-2 --recursive-unset /apps/compiz
```

---

### Post by magicrobotmonkey on 2006-05-02
I keep getting:

E: Couldn't find package compiz-vanilla-aiglx

when trying to install the vanilla compiz. All the other packages go fine. Am I missing something?

---

### Post by psyke83 on 2006-05-02
[QUOTE=magicrobotmonkey]I keep getting:

E: Couldn't find package compiz-vanilla-aiglx

when trying to install the vanilla compiz. All the other packages go fine. Am I missing something?[/QUOTE]

Yep, you musn't have added the aiglx repo to your sources.list:

```
# Xgl CVS
deb http://xgl.compiz.info/ dapper main [COLOR="Red"]aiglx[/COLOR]
deb-src http://xgl.compiz.info/ dapper main [COLOR="Red"]aiglx[/COLOR]
```

Hmm, the first page is in need of a rewrite methinks.. :)

---

### Post by magicrobotmonkey on 2006-05-02
ahh, nice, thanks for the heads up. now, whats this peeping behind windows thing, and how do I use it?

---

### Post by foxy123 on 2006-05-02
[QUOTE=magicrobotmonkey]ahh, nice, thanks for the heads up. now, whats this peeping behind windows thing, and how do I use it?[/QUOTE]
see [here]("http://ubuntuforums.org/showpost.php?p=976092&postcount=1")

---

### Post by arunsub on 2006-05-02
I wanted to go through this forum to find out, but it's running into 55th page. I don't think I have time to read through 55 pages. I have Acer Travelmate 8204 core duo laptop with ATI X1600 video card. Do you think if i follow the instructions on the 1st page (including x-server installation) will work on my system? I have the latest ATI driver installed (released few weeks back). Old ATI drivers don't work for my card.

---

### Post by gandalfn on 2006-05-02
Hi,

First page updated !

Now all packages are on xgl.compiz.net main and aiglx repos. Compiz aiglx patch are now partially official, compiz-vanilla work on xorg-aiglx and you can start it like this :
```

LIGL_ALWAYS_INDIRECT=TRUE compiz --strict-binding --indirect-rendering --replace gconf

```
compiz-aiglx packages are now deprecated and a new meta package compiz-vanilla-aiglx replace them. This integrate a new compiz-start python script which you can start gset-compiz to configure compiz, restart compiz and switch to metacity.

---

### Post by t3rror on 2006-05-02
i can try to start compiz by itself, but then I lose my window borders again.  I followed the new updated front page How-To exactly, but I am still getting the same problems.

---

### Post by jstueve on 2006-05-02
download and install the new xserver-xorg-air-core deb on one of these pages...  then restart x

---

### Post by jstueve on 2006-05-02
What is the new order of plugins for dock and bs?

also the top_images and bottom_images do nothing for me... (I can load an image using the images array, but not top and bottom arrays...)

---

### Post by ruffneck on 2006-05-02
Thanks for the update Gandalfn

---

### Post by psyke83 on 2006-05-02
[QUOTE=gandalfn]Hi,

First page updated !
[/QUOTE]Just a suggestion, but you may want to include the source repo to keep things consistent:
```
# Xgl CVS
deb http://xgl.compiz.info/ dapper main aiglx
deb-src http://xgl.compiz.info/ dapper main aiglx
```Additionally, I've noticed that this update drastically reduces flicker, making opengl applications (and video playback) much better (but it still doesn't follow compiz effects, and flicker occurs only when a window underneath is updating). Since xshm output looks so bad, perhaps include the option to use opengl in totem xine:

~/.gnome2/totem_config:```
video.driver:opengl
```

---

### Post by Kannisto on 2006-05-02
[QUOTE=t3rror]i can try to start compiz by itself, but then I lose my window borders again.  I followed the new updated front page How-To exactly, but I am still getting the same problems.[/QUOTE]
Same here, got this error: ```
The program 'gnome-window-decorator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 604 error_code 8 request_code 152 minor_code 8)

``` I got it after I started gnome-window-decorator manually in terminal.

---

### Post by galo on 2006-05-02
Can someone tell me, why after this upgrade, my right mouse button and my scroll wheel zoom in and out ?

It's kind of annoying..

---

### Post by dabear on 2006-05-02
I am not able to remove compiz-aiglx, how do I solve this issue?
> 
bjorninge@LappyDapper:~$ sudo aptitude purge compiz-aiglx compiz-aiglx-gnome compiz-aiglx-kde
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  cupsys-driver-gutenprint debconf debconf-i18n debconf-utils foomatic-db-gutenprint gdm gimp-print gnome-panel gnome-panel-data
  gnome-power-manager ijsgutenprint kdelibs-bin kdelibs-data kdelibs4c2a konq-plugins kubuntu-artwork-usplash kubuntu-default-settings
  language-selector language-selector-common language-selector-qt libasound2 libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common
  libgnomevfs2-dev libgnomevfs2-extra libgphoto2-2 libgphoto2-port0 libgutenprint2 libgutenprintui2-1 libnautilus-extension1 libogg0
  libpanel-applet2-0 libpanel-applet2-dev libpowersave10 libscim8c2a libvorbis0a libvorbisenc2 libvorbisfile3 nautilus nautilus-data
  powersaved python2.4-psyco scim scim-gtk2-immodule scim-modules-socket ubuntu-docs update-manager
The following packages will be REMOVED:
  compiz-aiglx-gnome{p}
0 packages upgraded, 0 newly installed, 1 to remove and 48 not upgraded.
Need to get 0B of archives. After unpacking 217kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 166899 files and directories currently installed.)
Removing compiz-aiglx-gnome ...
Uninstalling gconf schemas...
Resolved address "xml:merged:/etc/gconf/gconf.xml.defaults" to a writable configuration source at position 0
I/O warning : failed to load external entity "/usr/share/gconf/schemas/compiz.schemas"
Failed to open `/usr/share/gconf/schemas/compiz.schemas': No such file or directory
dpkg: error processing compiz-aiglx-gnome (--purge):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 compiz-aiglx-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
bjorninge@LappyDapper:~$   


---

### Post by jstueve on 2006-05-02
[http://ubuntuforums.org/showpost.php?p=976716&postcount=533](http://ubuntuforums.org/showpost.php?p=976716&postcount=533)

---

### Post by t3rror on 2006-05-02
[QUOTE=Kannisto]Same here, got this error: ```
The program 'gnome-window-decorator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 604 error_code 8 request_code 152 minor_code 8)

``` I got it after I started gnome-window-decorator manually in terminal.[/QUOTE]

I can't even get gnome-window-decorator to start manually on my machine.```
harrison@ssc-harrisontux2:~$ sudo gnome-window-decorator
Password:
sudo: gnome-window-decorator: command not found

```

---

### Post by dabear on 2006-05-02
[QUOTE=jstueve][http://ubuntuforums.org/showpost.php?p=976716&postcount=533](http://ubuntuforums.org/showpost.php?p=976716&postcount=533)[/QUOTE]
Right, thanks. 
> 
get a copy of the deb you tried to uninstall,

Where do I get  compiz-aiglx-gnome_0.0.9-0ubuntu3_i386.deb from again? Tried googling it, but only gave search results for this and a french howto

**edit:**never mind, the french howto pointed me to [http://gandalfn.club.fr/ubuntu/compiz-aiglx-gnome_0.0.9-0ubuntu3_i386.deb](http://gandalfn.club.fr/ubuntu/compiz-aiglx-gnome_0.0.9-0ubuntu3_i386.deb)

---

### Post by dentaku65 on 2006-05-02
I did the update to vanilla ...but where is transset plugin??

---

### Post by dabear on 2006-05-02
OK, gnome-window-decorator is not installed apparently, what package provides that command?
> 
bjorninge@LappyDapper:~$ compiz-start
gnome-window-decorator: no process killed
Traceback (most recent call last):
  File "/usr/bin/compiz-start", line 83, in ?
    start_compiz()
  File "/usr/bin/compiz-start", line 13, in start_compiz
    flags=gobject.SPAWN_SEARCH_PATH)
gobject.GError: Feil under kjøring av underprosess «gnome-window-decorator» (No such file or directory)
bjorninge@LappyDapper:~$


---

### Post by dentaku65 on 2006-05-02
[QUOTE=dabear]Right, thanks. 

Where do I get  compiz-aiglx-gnome_0.0.9-0ubuntu3_i386.deb from again? Tried googling it, but only gave search results for this and a french howto

**edit:**never mind, the french howto pointed me to [http://gandalfn.club.fr/ubuntu/compiz-aiglx-gnome_0.0.9-0ubuntu3_i386.deb](http://gandalfn.club.fr/ubuntu/compiz-aiglx-gnome_0.0.9-0ubuntu3_i386.deb)[/QUOTE]


try 
> sudo apt-get install --reinstall compiz-vanilla compiz-vanilla-aiglx compiz-vanilla-gnome gset-compiz

;)

---

### Post by MOGua on 2006-05-02
> OK, gnome-window-decorator is not installed apparently, what package provides that command?

I had the same problem. Try downloading this and install it; that fixed it for me.
> [http://gandalfn.club.fr/ubuntu/xserver-xorg-air-core_1.0.99.902-0ubuntu1_i386.deb](http://gandalfn.club.fr/ubuntu/xserver-xorg-air-core_1.0.99.902-0ubuntu1_i386.deb)

---

### Post by psyke83 on 2006-05-02
[QUOTE=dabear]OK, gnome-window-decorator is not installed apparently, what package provides that command?[/QUOTE]

It's a part of gnome-vanilla-gnome. Make sure you follow the instructions on the first page to the letter; judging from your apt-get output you haven't upgraded some packages. It's vital you do that (and you have holds, so use dist-upgrade).

---

### Post by dentaku65 on 2006-05-02
another not nice features of vanilla compiz:

- no transset plugin (already reported)
- the mouse cannot rotate the desktops (except dragging a window)
- the swithcer cannot switch windows on different desktop (the flag to set this is not working)

...hope no more to come :-?

---

### Post by Jeff250 on 2006-05-02
[QUOTE=Kannisto]Same here, got this error: ```
The program 'gnome-window-decorator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 604 error_code 8 request_code 152 minor_code 8)

``` I got it after I started gnome-window-decorator manually in terminal.[/QUOTE]

sudo gedit /etc/environment
Add this to the bottom:
```
XLIB_SKIP_ARGB_VISUALS=1
```
Save, reboot.  Solved the problem for me.

Alternatively, you can try typing:
```
XLIB_SKIP_ARGB_VISUALS=1 gnome-window-decorator
```
every time you want to run the gnome window decorator.

---

### Post by ruffneck on 2006-05-02
[QUOTE=dentaku65]another not nice features of vanilla compiz:
- no transset plugin (already reported)
- the mouse cannot rotate the desktops (except dragging a window)
- the swithcer cannot switch windows on different desktop (the flag to set this is not working)

...hope no more to come :-?[/QUOTE]

Yeah I've resorted to just opening up a terminal and using Ctrl+mouse wheel to change the opacity everytime. 

Also, the minimize plugin will not accept changes to the "zoom created windows from mouse/center."

---

### Post by alimh on 2006-05-03
Still no window borders for me.
When doing gnome-window-decorator:
```

The program 'gnome-window-decorator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 606 error_code 8 request_code 153 minor_code 8)

```
Notice this is serial 606 not 604 and 153 not 152

If I do  XLIB_SKIP_ARGB_VISUALS=1 gnome-window-decorator
I get no errors but I still have no window borders.

Somebody please help!

---

### Post by dentaku65 on 2006-05-03
[QUOTE=alimh]Still no window borders for me.
When doing gnome-window-decorator:
```

The program 'gnome-window-decorator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 606 error_code 8 request_code 153 minor_code 8)

```
Notice this is serial 606 not 604 and 153 not 152

If I do  XLIB_SKIP_ARGB_VISUALS=1 gnome-window-decorator
I get no errors but I still have no window borders.

Somebody please help![/QUOTE]

see
[http://www.ubuntuforums.org/showpost.php?p=978047&postcount=558](http://www.ubuntuforums.org/showpost.php?p=978047&postcount=558)

then:

> sudo rm /etcxdm/autostart/compiz*

and put in your session compiz-start

---

### Post by Balachmar on 2006-05-03
When I try to update my compiz to vanilla, I follow the howto on page 1.
But when I try to purge the old compiz packages I get the following error:
> 
E: compiz-aiglx-gnome: subprocess post-removal script returned error exit status 1

And then I cannot install the new vanilla compiz because of the same error.
So how can I remove it?
OK sorry found the solution. Unfortunately I removed the debs, already. Luckily Google had a cached page...

But...
Now I have it installed, I get a white box... The most feared white box....
At the moment I have removed all compiz libraries, so that I can work on my laptop...
I will try it later, but now I'm going home... :)

---

### Post by alimh on 2006-05-03
[QUOTE=dentaku65]and put in your session compiz-start[/QUOTE]

I tried this but I get that error along with:

```
compiz.real: No available stencil buffer
```

Did anyone else have AIGLX/compiz working from before and then try to update from this thread successfully?

---

### Post by Milamber_Cubed on 2006-05-03
Okay - got the new packages installed by following the instructions on page one but have/had some problems...

1. The uninstall process required compiz-kde to be removed as well - I think this should be added to the guide on Page 1.

2. Had the problem of not being able to remove compiz-aiglx because of missing file. Fixed as per a post a few pages back.

3. Textures are inverted for all windows and icons etc - see screen shot attached.

4. As well as being all inverted, the windows have no decorations.

Any help with 3 and 4 would be greatly appreciated or even some pointers as to where to dig for clues.

I am using a laptop with an i915 chipset, which is the same as gandalfn, so I am under the impression that this SHOULD work on my system. Indeed, until this latest update, everything has been working fine,

Any ideas?

Cheers,

Milamber

---

### Post by nik on 2006-05-03
> 
4. As well as being all inverted, the windows have no decorations.

You *sure* you're running in 16bit mode? I got this when trying 24bit.

But after todays updates of xorg and compiz-vanilla it doesn't work at all for me, just getting a white screen... anyone else have this?

---

### Post by Kannisto on 2006-05-03
All white here too, compiz says this
```
compiz.real: pixmap 0x260007b can't be bound to texture
compiz.real: Couldn't bind redirected window 0xe0001b to texture

``` (repeat change values) when launched from terminal.

---

### Post by jstueve on 2006-05-03
ditto...

---

### Post by magicrobotmonkey on 2006-05-03
me too, i just update my compiz-vanilla and a bunch of stuff to whatever was available since i updated this morning, and now when i log in, everything goes normally, i get a glimpse of my desktop, and suddenly it all goes white. All I've got is a white cube, which I can still flip and stuff. 

In my Xorg.0.log, I've got a bunch of AIGLX: 3D driver claims not to support visual 0x.. messaged. I'm not sure if those were there before or not, but I used to get a similar one when playing around with glxgears too much under compiz

---

### Post by dentaku65 on 2006-05-03
[QUOTE=magicrobotmonkey]me too, i just update my compiz-vanilla and a bunch of stuff to whatever was available since i updated this morning, and now when i log in, everything goes normally, i get a glimpse of my desktop, and suddenly it all goes white. All I've got is a white cube, which I can still flip and stuff. 

In my Xorg.0.log, I've got a bunch of AIGLX: 3D driver claims not to support visual 0x.. messaged. I'm not sure if those were there before or not, but I used to get a similar one when playing around with glxgears too much under compiz[/QUOTE]

Same here all white; the AIGLX 3d claims not to support visial etc was also before.... as far as I know should be a compiz.real problem :-k

---

### Post by t3rror on 2006-05-03
I have done everything on the front page to the letter.  I am still not able to get this to work.  It is still complaining about there not being a gnome-window-decorator.
```

harrison@ssc-harrisontux2:~/Desktop$ sudo compiz-start
Password:
gnome-window-decorator: no process killed
Traceback (most recent call last):
  File "/usr/bin/compiz-start", line 83, in ?
    start_compiz()
  File "/usr/bin/compiz-start", line 13, in start_compiz
    flags=gobject.SPAWN_SEARCH_PATH)
gobject.GError: Failed to execute child process "gnome-window-decorator" (No such file or directory)

```

---

### Post by no1wantdthisname on 2006-05-03
Yeah white screen here too.  Newer packages broke aiglx.  I had to downgrade to get it working again.  Here's my last known working config for whoever needs it.  Look in /var/cache/apt/archives/ for the .debs.  Might have to redo the make on the dri drivers after downgrading the libraries.

compiz-vanilla   0.0.10-0ubuntu5
compiz-vanilla-gnome   0.0.10-0ubuntu5
libgl1-mesa  6.5.1-0ubuntu4  
libgl1-mesa-dri 6.5.1-0ubuntu4  
libglu1-mesa 6.5.1-0ubuntu4  
xserver-xorg-air-core 1.0.99.902-ubuntu1 (not in repo)
[http://gandalfn.club.fr/ubuntu/xserver-xorg-air-core_1.0.99.902-0ubuntu1_i386.deb]("http://gandalfn.club.fr/ubuntu/xserver-xorg-air-core_1.0.99.902-0ubuntu1_i386.deb")

---

### Post by Kannisto on 2006-05-03
[QUOTE=t3rror]I have done everything on the front page to the letter.  I am still not able to get this to work.  It is still complaining about there not being a gnome-window-decorator.
[/QUOTE]
I think that package compiz-vanilla-gnome should also be installed.

---

### Post by ruffneck on 2006-05-03
Yeah white screen for me as well after the latest updates. I reverted back to metacity to get on here.

---

### Post by wiebel on 2006-05-03
[QUOTE=ruffneck]Yeah white screen for me as well after the latest updates. I reverted back to metacity to get on here.[/QUOTE]

Likewise :)

---

### Post by Milamber_Cubed on 2006-05-03
[QUOTE=Kannisto]I think that package compiz-vanilla-gnome should also be installed.[/QUOTE]

This is what I missed... I figured that something wasn't right when gnome-window-decorator wasn't found. Only thing was, I installed compiz-gnome and just answered yes to all the questions. This had the effect of removing compiz-vanilla and leaving me with plain old compiz. This is probably why I was getting the inverted textures problem.

Now I have "upgraded" to compiz-vanilla and compiz-vanilla-gnome I am at the same point as everyone else seems to be - white screen that lets me rotate cube and see the Novell logo on top but that's all. Not cool.

I miss the compiz magic already - metacity just doesn't seem good enough anymore.

Anyone actually got this working and if so what hardware are you using?

---

### Post by gandalfn on 2006-05-03
first page updated !

xserver-xorg-air debs updated which work with latest compiz-vanilla, and it's rework in 24 depth mode ;)

sorry ! but yesterday it's seem the xgl.compiz.net aiglx repos was really not sync, now it's OK

have fun !

---

### Post by ZoZo on 2006-05-03
Merci gandalfn :)

I'll try this right away.

---

### Post by t3rror on 2006-05-03
Thanks to everyone for their help.  I have now managed to get to where everyone else is.  I have the white screen.  Looking forward to a fix so I can actually start using this.

---

### Post by ZoZo on 2006-05-03
I had the white screen, but then I updated to xserver-xorg-air-core_1.0.99.902-0ubuntu1, set DefaultDepth in xorg.conf to 24 and it works fine :D

Edit: Scratch that... 24 bit depth still doesn't work with gnome-window-decorator, no title bars :(
But no more white screen with the new xorg-air

---

### Post by magicrobotmonkey on 2006-05-03
gandalfn, you're a god in this modern world. It was a rough coulple of eye-candy-less hours there, but now i got it running again and with 24-bit to boot!

---

### Post by Milamber_Cubed on 2006-05-03
[QUOTE=ZoZo]I had the white screen, but then I updated to xserver-xorg-air-core_1.0.99.902-0ubuntu1, set DefaultDepth in xorg.conf to 24 and it works fine :D

Edit: Scratch that... 24 bit depth still doesn't work with gnome-window-decorator, no title bars :(
But no more white screen with the new xorg-air[/QUOTE]


woo hoo!!! working again!

After noticing the new xorg package I ran through the entire guide from the begninning again step by step and ended up with a bunch of windows without title bars.

To get things working again, I removed all of my compiz settings:

```

gconftool-2 --recursive-unset /apps/compiz

```

and then clicked the compiz icon in the system tray (forgive the windows terminology) and chose "restart" compiz.

That was it. I will now try and tweak things back to the way I like them - is the best way to do this using the system tray thingy or gconf-editor? Is there any reason not to use one?

Thanks for all your hard work gandalfn - I really appreciate it as I am sure many others do.

---

### Post by ruffneck on 2006-05-03
Yeah white screen is gone after the latest updates awhile ago. Good stuff! Thanks Gandalfn!!

---

### Post by t3rror on 2006-05-03
After a reboot, everything is working now.  Thanks.  What is the water plugin?

---

### Post by Milamber_Cubed on 2006-05-03
Okay... so all seems to be well - I am not stuck on a white screen at least.

I am experiencing some problems with the configuration tool. It seems to only apply some settings and not others.

Example:

In the options for the cube plugin try setting the "in the cube" and clicking apply - the setting takes effect immediately.

Now try changing the settings for  "zoom created windows" in the minimize plugin options and click apply - nothing changes!

Is this just me or is anyone else getting this?

---

### Post by ruffneck on 2006-05-03
[QUOTE=Milamber_Cubed]Okay... so all seems to be well - I am not stuck on a white screen at least.

I am experiencing some problems with the configuration tool. It seems to only apply some settings and not others.

Example:

In the options for the cube plugin try setting the "in the cube" and clicking apply - the setting takes effect immediately.

Now try changing the settings for  "zoom created windows" in the minimize plugin options and click apply - nothing changes!

Is this just me or is anyone else getting this?[/QUOTE]

No. It happens to me as well. I've been trying to get this to work since I've switched to compiz-vanilla-aiglx. I have posted several times about it both here - in this thread - and over at [http://compiz.net/index.php](http://compiz.net/index.php) under bugs.

---

### Post by Milamber_Cubed on 2006-05-03
[QUOTE=ruffneck]No. It happens to me as well. I've been trying to get this to work since I've switched to compiz-vanilla-aiglx. I have posted several times about it both here - in this thread - and over at [http://compiz.net/index.php](http://compiz.net/index.php) under bugs.[/QUOTE]

Nice to know I am not the only one... It wouldn't be so bad if I could just revert to using gconf-editor, but doing the recursive unset has removed a lot of values that appear to have no defaults with compiz-vanilla :(

Don't suppose you know a place that lists all of these?

---

### Post by ruffneck on 2006-05-03
[QUOTE=Milamber_Cubed]Nice to know I am not the only one... It wouldn't be so bad if I could just revert to using gconf-editor, but doing the recursive unset has removed a lot of values that appear to have no defaults with compiz-vanilla :(

Don't suppose you know a place that lists all of these?[/QUOTE]

No not really. Try asking on the Compiz Forums. 

I've also noticed that the transset plugin doesn't seem to function anymore under compiz-vanilla-aiglx. Along with the problem with the minimize plugin settings these are the main issues that I haven't been able to solve.

---

### Post by eshehi on 2006-05-03
I still don't have windows borders, and I followed all the steps in the first post. How did people manage to get the borders back?

---

### Post by t3rror on 2006-05-03
Try this:
```

sudo apt-get update

sudo apt-get upgrade

```

That worked for me.  You should be prompted to download a new version of xserver-xorg-air-core

---

### Post by eshehi on 2006-05-03
I have the new xorg, and of course I have updated. Any help?

---

### Post by wiebel on 2006-05-03
Hi,

compiz-vanilla-aiglx is working like a charm now but I have a few issues:

1: custom hotkeys won't work
2: transset application settings don't work anymore. ( I'm missing the whole plugin actualy)
3: miniwin plugin seems gnone as well
3: when changing 
4: the water plugin isn't working (but it never has before :))

Are there more people seeing this issues?

Cheers,
Joris

---

### Post by t3rror on 2006-05-03
[QUOTE=eshehi]I have the new xorg, and of course I have updated. Any help?[/QUOTE]

[QUOTE=Kannisto]Same here, got this error: ```
The program 'gnome-window-decorator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 604 error_code 8 request_code 152 minor_code 8)

``` I got it after I started gnome-window-decorator manually in terminal.[/QUOTE]

Have you tried rebooting?

---

### Post by LordRaiden on 2006-05-03
Trying to install compiz-vanilla-aiglx... There seem to be a whole lot of gnom-related packages in the mix. What should a KDE user install? (xserver-xorg-air + compiz)?

---

### Post by Kannisto on 2006-05-03
[QUOTE=t3rror]Have you tried rebooting?[/QUOTE]
Everything working fine now with the updated xserver.

---

### Post by iXce on 2006-05-03
[QUOTE=wiebel]Hi,

compiz-vanilla-aiglx is working like a charm now but I have a few issues:

1: custom hotkeys won't work
2: transset application settings don't work anymore. ( I'm missing the whole plugin actualy)
3: miniwin plugin seems gnone as well
3: when changing 
4: the water plugin isn't working (but it never has before :))

Are there more people seeing this issues?

Cheers,
Joris[/QUOTE]

These are normal : water won't work with i915, and other problems are due to the fact that you're using compiz-vanilla, which does not include Quinnstorm's improvements and plugins : it's just compiz official cvs (with a little patch for --strict-binding to make wobbly faster on aiglx)

---

### Post by ruffneck on 2006-05-03
[QUOTE=iXce]These are normal : water won't work with i915, and other problems are due to the fact that you're using compiz-vanilla, which does not include Quinnstorm's improvements and plugins : it's just compiz official cvs (with a little patch for --strict-binding to make wobbly faster on aiglx)[/QUOTE]\\

Thanks for enlightening us on this iXce. I guess it's the same for the minimize plugin not having an effect anymore.

---

### Post by conmiweb on 2006-05-03
Vith vanille can I put 24 depth color and works fine?Please help i'm scared!

---

### Post by dabear on 2006-05-03
[QUOTE=conmiweb]Vith vanille can I put 24 depth color and works fine?Please help i'm scared![/QUOTE]
Yup, doing that here.

--
Could anyone tell me why I have lost the ability to use opacity? I can change the opacity etc in the move pluginmaking it work while moving windows, but nothing more.

---

### Post by jstueve on 2006-05-03
I have a strange problem...

When I bootup and login no window borders in compiz.  Then I suspend, and resume, viola window boarders with compiz.  Try to suspend again, nothing.  Then reboot, back to the beginning...

Not even sure where to start troubleshooting...

---

### Post by no1wantdthisname on 2006-05-04
Still no window borders on latest upgrades.  Running gnome-window-decorator in console doesn't show anything.  Any ideas?

I have already restarted/reinstalled several times, unset compiz keys, changed depth, etc.

---

### Post by wiebel on 2006-05-04
[QUOTE=iXce]These are normal : water won't work with i915, and other problems are due to the fact that you're using compiz-vanilla, which does not include Quinnstorm's improvements and plugins : it's just compiz official cvs (with a little patch for --strict-binding to make wobbly faster on aiglx)[/QUOTE]

Ok, thanks.

There is another issue though. Although i've setup compiz in a way it should show minimized windows and windows on other workspaces in the switcher, it doesn't. 

Cheers,
Joris

---

### Post by DreamThief on 2006-05-04
[QUOTE=no1wantdthisname]Still no window borders on latest upgrades.  Running gnome-window-decorator in console doesn't show anything.  Any ideas?

I have already restarted/reinstalled several times, unset compiz keys, changed depth, etc.[/QUOTE]


Ok guys - I think I got an solution for all of you who have problems with compiz after the lastest updates.
I got those problems, too, which resultet in an unusable desktop because compiz dint't show up correctly and no window had a border...

I've run the compiz-start script form inside a  terminal and realized that the two plugins gconf and gconf-dump have a conflict and therefor they can't be run together.

Please check if those two plugins are enabled and if yes DISABLE gconf-dump. Don't forget to apply the new settings! After this little intervention try starting compiz-start or restart gdm ...

I believe this should be helpfull for some of you ...

Greetings form Germany,

Mathias

---

### Post by bhaagensen on 2006-05-04
Hi, is anyone else having problems with deskbar-applet in combination with aiglx/compiz ? Basically deskbar-applet won't start for me when using compiz.

I vaguely remember having come accross this problem earlier, but can not at all remember how/where/when/why. 

Thanks, Bjorn

---

### Post by Ago12 on 2006-05-04
And how can I do that? It's maybe my problem.

Actually, my gnome session starts and crashes when the scipt is launched :/

---

### Post by jstueve on 2006-05-04
[QUOTE=jstueve]Not even sure where to start troubleshooting...[/QUOTE]

I was finally able to get an error message from gnome-window-decorator:

> (gnome-window-decorator:8267): Gdk-CRITICAL **: gdk_cairo_create: assertion `GDK_IS_DRAWABLE (drawable)' failed


Running compiz-vanilla aiglx on a intel 855GM.

anyone have a suggestion?

---

### Post by Permafrost91 on 2006-05-04
well, I have finally upgraded everything ... compiz works with the exception of gnome-window-decorator ... but compiz seems faster, smoother, and more responsive which is good news of course ... I also like the new config app a lot ... so here are my questions

(1) what needs to be done to get the window dec to work again? (another win deco maybe? Red Hat claims AIGLX works with metacity)

(2) can unmaximized windows be bend?

(3) does the water plugin work? I'd really like to see this effect

---

### Post by max-fx on 2006-05-04
Hi everybody

Sorry for my english, I'm french.

I have a big problem with compiz' removing :

```
max-fx@max-fx:~/Desktop$ sudo aptitude purge compiz-aiglx compiz-aiglx-gnome
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances... Fait
Lecture de l'information d'état étendu
Initialisation de l'état des paquets... Fait
Construction de la base de données des étiquettes... Fait
Les paquets suivants seront ENLEVÉS :
  compiz-aiglx{p} compiz-aiglx-gnome{p}
0 paquets mis à jour, 0 nouvellement installés, 2 à enlever et 0 non mis à jour.
Il est nécessaire de télécharger 0o d'archives. Après dépaquetage, 665ko seront libérés.
Voulez-vous continuer ? [Y/n/?] y
Écriture de l'information d'état étendu... Fait
(Lecture de la base de données... 91237 fichiers et répertoires déjà installés.)
Suppression de compiz-aiglx-gnome ...
Uninstalling gconf schemas...
Adresse « xml:merged:/etc/gconf/gconf.xml.defaults » résolue vers une source de configuration accessible en écriture à la position 0
I/O warning : failed to load external entity "/usr/share/gconf/schemas/compiz.schemas"
L'ouverture de « /usr/share/gconf/schemas/compiz.schemas » a échoué : Aucun fichier ou répertoire de ce type
dpkg : erreur de traitement de compiz-aiglx-gnome (--purge) :
 le sous-processus post-removal script a retourné une erreur de sortie d'état 1
Suppression de compiz-aiglx ...
Purge des fichiers de configuration de compiz-aiglx ...
Des erreurs ont été rencontrées pendant l'exécution :
 compiz-aiglx-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)
Échec de l'installation d'un paquet. Tentative de réparation :
max-fx@max-fx:~/Desktop$
```

In advance, thank you very much

---

### Post by jstueve on 2006-05-04
[http://ubuntuforums.org/showpost.php?p=976716&postcount=533](http://ubuntuforums.org/showpost.php?p=976716&postcount=533)

---

### Post by max-fx on 2006-05-04
thank you but it doesn't work for me :

```
max-fx@max-fx:~/Desktop$ sudo apt-get -f install
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances... Fait
Correction des dépendances... Fait
Les paquets supplémentaires suivants seront installés :
  compiz
Paquets recommandés :
  compiz-kde
Les NOUVEAUX paquets suivants seront installés :
  compiz
0 mis à jour, 1 nouvellement installés, 0 à enlever et 1 non mis à jour.
2 partiellement installés ou enlevés.
Il est nécessaire de prendre 0o/129ko dans les archives.
Après dépaquetage, 434ko d'espace disque supplémentaires seront utilisés.
Souhaitez-vous continuer [O/n] ? o
(Lecture de la base de données... 91261 fichiers et répertoires déjà installés.)Dépaquetage de compiz (à partir de .../compiz_0.0.2-4ubuntu2_i386.deb) ...
dpkg : erreur de traitement de /var/cache/apt/archives/compiz_0.0.2-4ubuntu2_i386.deb (--unpack) :
 tentative de remplacement de « /usr/share/gnome/wm-properties/compiz.desktop », qui appartient aussi au paquet compiz-aiglx-gnome
Des erreurs ont été rencontrées pendant l'exécution :
 /var/cache/apt/archives/compiz_0.0.2-4ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
max-fx@max-fx:~/Desktop$

```

---

### Post by alimh on 2006-05-04
I'm confused on the difference between Quinnstorm's compiz and compiz-vanilla. Can somebody point me to a thread or something where the differences are explained. From what I gathered, Quinnstorm patches "official" compiz-vanilla. It seems that Quinnstorm's have more features/plugins. Is it safe to use Quinnstorm's compiz with the other compiz-vanilla packages like compiz-vanilla-aiglx and compiz-vanilla-gnome? And if so, how do I do that?

Any help would be appreciated.

---

### Post by roax on 2006-05-04
dpkg -i --force-overwrite /var/cache/apt/archives/compiz_0.0.2-4ubuntu2_i386.deb
apt-get install -f

---

### Post by roax on 2006-05-04
Sorry, commands above are for max-fx

---

### Post by max-fx on 2006-05-04
[QUOTE=roax]Sorry, commands above are for max-fx[/QUOTE]

thank you very very much :D :D, all it's ok

---

### Post by Ago12 on 2006-05-05
No idea? :(

---

### Post by Ventajou on 2006-05-05
Hi,

I'm trying to run aiglx + compiz on my Dell Latitude D505 (i855GM) without success...

I reinstalled the latest Dapper last night, ran through the updates and finally went through the instructions on this thread. The first problem I encounter is that when I install the xserver-xorg-driver-i810 package from the compiz.info repository and restart the X server, it now will only run at 640x480 with a black band at the top of the screen. The normal display is basically shifted 2cm downwards making it impossible to see the bottom of the screen. Also, I do not see the mouse pointer anymore.

If I add the screen refresh rates in xorg.conf, even though it's a laptop screen, it at least lets me switch back to 1024x768, but the black band is still there and the mouse is still invisible.

Then if I try to run compiz-start, it'll just come up with some error message about not being able to run gnome-window-decorator...

I've spent hours trying to figure this out! Any help will be appreciated...


Thanks!

---

### Post by jstueve on 2006-05-05
have you installed and configured i915resolution?

---

### Post by Ago12 on 2006-05-05
Hello. I try again, with some more informations, after the new update:

- when I launch compiz-start, Gnome crashes and restarts again and again...

- when I lauch it from a tty:
> 
File "/usr/bin/compiz-start", line 7, in ?
Import GTK, Gobject

File "/usr/lib/python2.4/site-packages/gtk-2.0/gtk/__init_.py", line 45, in ?
From _gtk import *

---

### Post by no1wantdthisname on 2006-05-05
Dri is broken now.  Well, at least opengl games are freezing.
Any ideas?

Getting this from glxinfo:
```
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32

direct rendering: Yes
```
Already tried upgrading from cvs and reinstalling all packages..

---

### Post by ZoZo on 2006-05-05
With the latest xserver-xorg-air-core_1.0.99.902-0ubuntu2 24bit depth works but I have the same problem as no1wantdthisname.

---

### Post by echo on 2006-05-06
I'm looking for the patched xserver-xorg-driver-ati that fixes the double buffering error, as I'm still getting this with the latest packages, which means I don't have window borders. 

I'm using an ATI Radeon 7500, and I feel so close to making this work that I can almost taste it.

Several folks mentioned the patched ati driver being on page 1, but I can't find it. Anyone got the link?

---

### Post by JLu on 2006-05-06
[QUOTE=echo]I'm looking for the patched xserver-xorg-driver-ati that fixes the double buffering error, as I'm still getting this with the latest packages, which means I don't have window borders. 

I'm using an ATI Radeon 7500, and I feel so close to making this work that I can almost taste it.

Several folks mentioned the patched ati driver being on page 1, but I can't find it. Anyone got the link?[/QUOTE]
[Here]("http://gandalfn.club.fr/ubuntu/xserver-xorg-driver-ati_6.5.7.3-0ubuntu5_i386.deb") you go.  Works with my ATI Radeon Mobility M6.

---

### Post by no1wantdthisname on 2006-05-06
Well dri still not working, but the regular compiz package now works for aiglx. 
```
sudo apt-get install compiz compiz-gnome
```
Has the extra trailfocus, dock, miniwin, state, and bs plugins.  Also has the colored shadows.

Bs and miniwin have a lot of problems though.  Everything else seems to work okay.

EDIT: scratch that, somehow dri started working again.  Maybe when I switched to regular compiz.

---

### Post by psyke83 on 2006-05-06
[QUOTE=no1wantdthisname]Well dri still not working, but the regular compiz package now works for aiglx.[/QUOTE]They work, but not very well - at least not on my system. Have you tried quitting X or switching to a console? It crashes my machine (even with the troublesome plugins disabled).

---

### Post by Grey on 2006-05-06
Is anyone else having severe problems with menus and context menus?  For me, they don't display half the time... and it's really hard to get around my laptop without menus or right clicking.

---

### Post by Tab on 2006-05-06
[QUOTE=echo]I'm looking for the patched xserver-xorg-driver-ati that fixes the double buffering error, as I'm still getting this with the latest packages, which means I don't have window borders. 

I'm using an ATI Radeon 7500, and I feel so close to making this work that I can almost taste it.

Several folks mentioned the patched ati driver being on page 1, but I can't find it. Anyone got the link?[/QUOTE]
Mobility 7500, or the 7500 desktop card? I have the rv200/r100-based desktop card, and I've had nothing but trouble trying to get aiglx working.

---

### Post by foxy123 on 2006-05-07
I guess I stay away from compiz for a while. The last updates broke it again and now I had a black screen when I start compiz, though a mouse pointer is visible and moveable. Again it is some conflict between libgconf2 and compiz-start so that those both processes consume 100% of CPU.

---

### Post by enjoy_linux on 2006-05-07
[QUOTE=Grey]Is anyone else having severe problems with menus and context menus?  For me, they don't display half the time... and it's really hard to get around my laptop without menus or right clicking.[/QUOTE]


i have the same problem! any idea how to solve it?

---

### Post by ruffneck on 2006-05-07
[QUOTE=Grey]Is anyone else having severe problems with menus and context menus?  For me, they don't display half the time... and it's really hard to get around my laptop without menus or right clicking.[/QUOTE]

Yeah. This is a known bug. It's already reported on the [http://compiz.net/index.php](http://compiz.net/index.php) forums.

---

### Post by netspirit on 2006-05-07
> The last updates broke it again and now I had a black screen when I start compiz, though a mouse pointer is visible and moveable.
Same thing for me on an ASUS W5 laptop with Intel i915GM video card...

---

### Post by Grey on 2006-05-08
[QUOTE=enjoy_linux]i have the same problem! any idea how to solve it?[/QUOTE]

I solved it (temporarily), by disabling the fade plugin.  I am just going to wait until that's fixed.

EDIT:  Update killed compiz for me as well.  Just updated, and when I log in, it crashes X, and sends me back to GDM.

---

### Post by Balachmar on 2006-05-08
Yeah, I have the same problem!

OK I have "solved" the problem.
I have downgraded the compiz packages and then I use the older kernel and now it works.

I'm now installing the updates of compiz and trying to find out that it is only the kernel. Yes it is only the kernel... :)
But now I am thinking about it, we changed the kernel in this howto, didn't we?
So we should build the kernel again...
I cannot build the kernel again, because it is lacking a configuration file for the new kernel.

---

### Post by macmils on 2006-05-08
Couple of things to note:

With the latest updates and doing a dist-upgrade installs a new kernel, this mean you need to recompile and copy the drm modules as detailed on the first page.

If you get a white or a black screen when logging in, press <ALT> <CTRL> F1 and login to the console and killall compiz. <ALT><CTRL>F7 gets you back to your desktop and you can then try switching to metacity via the applet.

Lastly, if restarting metacity from the command line, don't use sudo as that will try and run it as root and not your login.

Meanwhile myself, I don't get the window decorator borders and get this in my .xsession-errors log

compiz.real: No stencil buffer. Clipping of transformed windows is not going to
be correct when screen is transformed.

I'm guessing this is to do with the Mesa GL libraries.


Hope the above can be of help.

---

### Post by Grey on 2006-05-08
Yeah, I am a bloody idiot.  That's what this has told me.  =P  I remember when I compiled the drm modules that I thought I would remember if the kernel was ever updated again.  Thanks for the reminder guys.

You know I even completely erased my compiz gconf entries?

---

### Post by Balachmar on 2006-05-08
But are you guys able to compile the new kernel with DRI?
Because mine failed...

---

### Post by max-fx on 2006-05-08
I have the same problem :

Gnome-Message: gnome_execute_async_with_env_fds: returning -1
gnome-window-decorator: aucun processus tué
compiz.real: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
Can't use gconf-dump plugin with gconf plugin
--replace: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
Can't use gconf-dump plugin with gconf plugin

---

### Post by Milamber_Cubed on 2006-05-08
Okay...

I just updated my kernel to the latest in the repos and have started having problems. After the new kernel was installed i could no longer log in - it would just crash and put me back at the login screen. Okay - drm modules must be it, right?

Installed kernel headers by logging into failsafe terminal session and re-downloaded and compiled the drm modules and copied them into place. Still no joy :( 

Tried a reboot and it finally let me log in. Now, there are still problems though. The menu popups (Applications, Places, System) appear BEHIND any open windows - which is not very useful - and after a short while (within a minute or two) the whole thing locks up and stops responding to keyboard/mouse input. The system is still running - the mouse cursor moves about and the animation for my CPU usage monitor is still moving along. I have to do a hard shut-down by holding in the power button. 

Rebooted with previous kernel (even though drm modules are compiled against newer one) and everything is working fine.

Any ideas/similar problems?

EDIT/UPDATE:

Played around a bit and found that it was something to do with sessions. hopefully that is the last of the problems

---

### Post by linuxmad on 2006-05-08
I have made the last updates and having the "old" problem logging out.. Is anyone else having this?

---

### Post by Grey on 2006-05-08
Well, since I erased all my compiz configurations... things seem to be working a lot better (and significantly faster) for me (vlc appears behind my panels now too!).  Although all my customizations are gone.  Perhaps it wasn't such a bad thing that I did that?  Maybe it would help your problem with the menus appearing behind windows.

EDIT:  And yes, attempting to log out locks up X.  Bummer.  Ah well, I suppose "sudo reboot" or "sudo halt" works just as well.

---

### Post by linuxmad on 2006-05-08
Does anyone have the old gnome-session packages provided by gandalf?

---

### Post by roax on 2006-05-08
All packages are in first page

---

### Post by linuxmad on 2006-05-08
> All packages are in first page
They used to be... but not now;)

---

### Post by foxy123 on 2006-05-08
[QUOTE=linuxmad]They used to be... but not now;)[/QUOTE]
I guess you can just force the appropriate version if you have compiz repositories enabled.

---

### Post by givré on 2006-05-08
Look there:
[http://xgl.compiz.info/dists/dapper/aiglx/binary-i386/](http://xgl.compiz.info/dists/dapper/aiglx/binary-i386/) ;)

---

### Post by roax on 2006-05-08
It's true linuxmad, sorry.

---

### Post by linuxmad on 2006-05-08
> Look there:
[http://xgl.compiz.info/dists/dapper/aiglx/binary-i386/](http://xgl.compiz.info/dists/dapper/aiglx/binary-i386/) 
That did it .. thanks:p 

> It's true linuxmad, sorry.

No hard feelings...:D

---

### Post by mnshsl on 2006-05-08
My gdm just hangs when I follow the complete process to install compiz ????

---

### Post by tonyo46 on 2006-05-08
[QUOTE=linuxmad]I have made the last updates and having the "old" problem logging out.. Is anyone else having this?[/QUOTE]

yes :( 

Did you solve it ?

---

### Post by Balachmar on 2006-05-08
Is it impossible to freely rotate the cube with this new vanilla compiz?
Or is it just because I still have some old setting in gconf?
And I hear people about removing all the settings, but how do I put the new vanilla settings in place then? Or does it default to some values, if they aren't set in gconf?

I, by the way, still can't get it to work with kernel: 2.6.15.22
Did the drm kernel fix, but gdm still crashes...

---

### Post by linuxmad on 2006-05-08
Yes... install the package listed by grivé:
[http://xgl.compiz.info/dists/dapper/aiglx/binary-i386/](http://xgl.compiz.info/dists/dapper/aiglx/binary-i386/)

---

### Post by tonyo46 on 2006-05-08
Thank you linuxmad !
it seems to work :)

---

### Post by Milamber_Cubed on 2006-05-08
[QUOTE=tonyo46]Thank you linuxmad !
it seems to work :)[/QUOTE]

There is a new gnome-session package in the repo now that means you won't be nagged about 1 update being available. :)

Awesome.

You will know it's the right one because it will say that the package is not authenticated if you use synaptic to upgrade it :)

---

### Post by domino on 2006-05-08
Does this how-to work with the current ATI proprietory driver and 9800 pro?

---

### Post by WiLLiE on 2006-05-08
I only get a black screen here, or the "No GLXFBConfig for default depth" error, and I followed the guide to the letter.
Should I download and install all packages [here]("http://gandalfn.club.fr/ubuntu/index.php") manually?

i915gm btw.

---

### Post by Permafrost91 on 2006-05-08
what's the word on the latest packages not providing a working gnome-window-decorator with mesa 6.5.1? (still not working for me). Where can I start trouble shooting this? I can't downgrade to 6.4 version of mesa. What logs should I consult? Has anyone gotten this to works since it broke?

---

### Post by WiLLiE on 2006-05-08
Yeah, no gnome-window-decorator here either.

---

### Post by magicrobotmonkey on 2006-05-08
[QUOTE=WiLLiE]Yeah, no gnome-window-decorator here either.[/QUOTE]


what hardware are you guys using? Also, did you upgrade to the new kernel? I'm scared to update!

---

### Post by Permafrost91 on 2006-05-08
IBM X30 with i810 on 2.6.15-22-686 kernel ... this worked with compiz 0.0.8 but 0.0.10 is broken

---

### Post by magicrobotmonkey on 2006-05-08
[QUOTE=Permafrost91]IBM X30 with i810 on 2.6.15-22-686 kernel ... this worked with compiz 0.0.8 but 0.0.10 is broken[/QUOTE]
so i guess I shouldn't update then, huh?

---

### Post by Permafrost91 on 2006-05-08
I'd recommend holding off on updating ... some people seem to have gotten it to work but I haven't been able to find the source of my problem yet so from a personal standpoint I'd say wait ... I also don't think 0.0.10 is a major update, mostly under-the-hood from what I've seen (well, with the exception of a new graphical configuration tool and compiz feeling more responsive)

---

### Post by magicrobotmonkey on 2006-05-08
[QUOTE=Permafrost91]I'd recommend holding off on updating ... some people seem to have gotten it to work but I haven't been able to find the source of my problem yet so from a personal standpoint I'd say wait ... I also don't think 0.0.10 is a major update, mostly under-the-hood from what I've seen (well, with the exception of a new graphical configuration tool and compiz feeling more responsive)[/QUOTE]
yea, if it doesnt have any of quinns plugins in it, i guess I won't them, I know they've been talking about figuring out the best way to get the two versions together. I think I'll wait until they get all that straightened out since I'm using this machine for work and I dont think i can work without compiz. using my window machine (for testing!) is painful

---

### Post by jstueve on 2006-05-08
I'm running the latest compiz (Quinn's) and compiz-gnome with the latest kernel, the only thing I had to do was compile the drm modules as documented on the main page, after I upgraded to the .22 kernel.  (Also upgrading from both beerorkid and the compiz repositories)

Running fine on a Dell 700m (intel 855GM).

---

### Post by Permafrost91 on 2006-05-08
recompiling the drm module did not do the trick for me, g-w-d still does not work

EDIT: 16bit/24bit both show same results

---

### Post by ZoZo on 2006-05-08
In 24-bit mode, display is slow. For example when I do System->Log out, the fading is very very slow and eats up 100% CPU. When I'm in 16-bit mode, everything seems to be at normal speed.

---

### Post by Grey on 2006-05-09
Yup.  Same here.  I think we have UMA (Unified Memory Architecture) to blame for that.  Since you use 50% more bandwidth, things should run at 66% as fast.  Just my personal theory... but it makes sense.

---

### Post by ruffneck on 2006-05-09
[QUOTE=jstueve]I'm running the latest compiz (Quinn's) and compiz-gnome with the latest kernel, the only thing I had to do was compile the drm modules as documented on the main page, after I upgraded to the .22 kernel.  (Also upgrading from both beerorkid and the compiz repositories)

Running fine on a Dell 700m (intel 855GM).[/QUOTE]

Thanks for this! I have 700m and have always ran compiz-aiglx and now the newer compiz-vanilla-aiglx and compiz-vanilla packages, which are strictly cvs (no quinn patches).

I have to try the latest compiz from Quinn now cause I didn't know it would work.

EDIT: Quinn's Compiz works a charm!

---

### Post by ruffneck on 2006-05-09
[QUOTE=ZoZo]In 24-bit mode, display is slow. For example when I do System->Log out, the fading is very very slow and eats up 100% CPU. When I'm in 16-bit mode, everything seems to be at normal speed.[/QUOTE]

yeah 24-bit mode is slow when scrolling down webpages as well and this is too annoying so i'll stick with 16-bit. Although I'm running at 60 refresh rate. Maybe going up to 75 would help but not sure how to do so yet.

---

### Post by Balachmar on 2006-05-09
So quinn's compiz is the vanilla compiz with some patches right?
And this how-to describes how to install the vanilla packages.
And the people behind compiz are now trying to merge these two compiz streams into one? Am I right?
Also the vanilla packages won't run with the new kernel, not even after doing the drm stuff with the new kernel. So at this moment I will stick with the older kernel.

---

### Post by Grey on 2006-05-09
You know, before I upgraded to the new kernel, I was having lots and lots of problems... including:

- sluggishness of compiz in general
- missing menus
- slow scrolling in firefox
- vlc appearing behind panels

I upgraded to the new kernel, and all these things *disappeared*.  I think it might be because I removed all my compiz customizations, and reinstalled all the compiz packages...  Can someone who's having troubles with the new kernel test something for me?  Just try erasing your compiz gconf entries, if you haven't extensively customized them.

Just try this command:

```
gconftool-2 --recursive-unset /apps/compiz
```

---

### Post by Balachmar on 2006-05-09
I did try that.
I took the new kernel, went in a terminal, because GDM wouldn't launch.
Created the new kernel stuff, copied it.
Then I threw away the setting, like you did.
(I only didn't reinstall all the compiz packages)
And it still crashed (at least I thought so...)
But I just updated (because there were 33 packages) and now it works fine...
So back to the latest kernel :)

I even (kind of) start to enjoy this... Living on the edge... :P

---

### Post by Grey on 2006-05-09
:)  Glad it's working for you now, regardless of the cause.

And yeah, I love beta software for precisely this reason.  It changes every day, and there's always a new feature or a bug to look forward to finding a fix for.  I'll admit that I'm exceptionally lazy regarding bug reporting (someone want to report the buggy pacman screensaver that blacks the levels every now and then for me?  :P)... but I'm here mostly for the experience.  Living with the uncertainty of whether or not my computers are still going to work or not tomorrow is just half the fun.

---

### Post by magicrobotmonkey on 2006-05-09
yea this mornings update fixed vanilla for me too. I still haven't gotten Quinns to run on this. I want more cutting edge!

---

### Post by Milamber_Cubed on 2006-05-09
Just thought I would point something out to all the people who are having problems:

I had a lot of issues after upgrading to the latest kernel so I assumed that compiz/kernel/drm was broken. As a last attempt to make some sense out of what was going on, I added a temporary user to the system and logged in as them. Everything worked!

For me, it turned out to be some weird issue with sessions (NOT the logout bug) and I managed to clear it up without haveing to unset all the compiz gconf keys. Try it out if you are having problems :)

---

### Post by t3rror on 2006-05-09
So is everyone running the latest kernel 2.6.15-22 with things still working?  I have everything up to date excpet the kernel.  I am going to upgrade it in a couple of minutes anyway, I just wondered if everyone had it running alright.

EDIT: I was not able to recompile the dri modules after upgrading to the above kernel.  My gdm session would die after about 10 secs also.  I am now reverting back to using the 2.6.15-21 kernel until i figure something else out.

---

### Post by lamarmotte on 2006-05-09
Hello everybody!
First of all, my apologies for my bad english, this is not my mother tongue. I hope I will be understable.
I followed the howto and after a reboot, absolutly nothing happend.
How can I check that everithing is ok (how to check that aiglx is running for instance)

Thanks a lot for this amazing job!

---

### Post by awakatanka on 2006-05-09
Any howto for kubuntu and kdm? And a sis vga card.

Great work btw. thxs

---

### Post by rendered_one on 2006-05-09
I have radeon 8500 aiw,

Tried from the 1st post yesterday, everything seems to install fine.. followed the instructions.. but when I go to do compiz --replace i get this!

$ compiz --replace
$ compiz.real: Root visual is not a double buffered GL visual
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

:S I tried to install the 'patched' ati driver but it says I already have a newer verions installed... Also is the ACTUAL "ati" driver or is it the "radeon" driver I need to be using?

Here is my xorg.conf

---

### Post by NMUrugbysteve on 2006-05-09
Anyone managed to make this work with xubuntu?

---

### Post by no1wantdthisname on 2006-05-09
[QUOTE=NMUrugbysteve]Anyone managed to make this work with xubuntu?[/QUOTE]

```
sudo gedit /usr/bin/compiz-start
```
Under 
```
def start_compiz()
```
add this
```
os.system("killall xfwm4")
```
Should work.

---

### Post by Kannisto on 2006-05-09
[QUOTE=NMUrugbysteve]Anyone managed to make this work with xubuntu?[/QUOTE]
Yep, just killall xfwm4 and then run compiz-start and save the session & logout.

---

### Post by NMUrugbysteve on 2006-05-09
Neither of those worked, 

stephen@ubuntu-laptop:~$ compiz-start
xfwm4: no process killed
gnome-window-decorator: no process killed
Traceback (most recent call last):
  File "/usr/bin/compiz-start", line 84, in ?
    start_compiz()
  File "/usr/bin/compiz-start", line 14, in start_compiz
    flags=gobject.SPAWN_SEARCH_PATH)
gobject.GError: Failed to execute child process "gnome-window-decorator" (No such file or directory)

---

### Post by foxy123 on 2006-05-09
[QUOTE=NMUrugbysteve]Neither of those worked, 

stephen@ubuntu-laptop:~$ compiz-start
xfwm4: no process killed
gnome-window-decorator: no process killed
Traceback (most recent call last):
  File "/usr/bin/compiz-start", line 84, in ?
    start_compiz()
  File "/usr/bin/compiz-start", line 14, in start_compiz
    flags=gobject.SPAWN_SEARCH_PATH)
gobject.GError: Failed to execute child process "gnome-window-decorator" (No such file or directory)[/QUOTE]
i've got the same problem... anyone?

---

### Post by no1wantdthisname on 2006-05-09
Er, do you have compiz-gnome or compiz-vanilla-gnome installed?

---

### Post by foxy123 on 2006-05-09
[QUOTE=no1wantdthisname]Er, do you have compiz-gnome or compiz-vanilla-gnome installed?[/QUOTE]
no, strangely enough but 
```
sudo apt-get install compiz-vanilla-aiglx
```
installs compiz and gset-compiz only. Installing compiz-vanilla-gnome removes compiz and installs compiz-vanilla.

I will try to do it as soon as the repository is up (it seems down at the moment).

---

### Post by echo on 2006-05-09
Whew! I finally got this to work on my ATI Radeon 7500.  

Hints to making it work:

1. Use compiz-vanilla-gnome, not compiz-gnome
2. Manually patch the ati driver.
3. Run in 16-bit

Now, the running in 16-bit is interesting.. Apparently the patch to fix the root visual to be double buffered works in 16-bit, but fails in 24-bit mode, as I get the same error. This is why I was thinking the patch didn't work. So someone is going to have to figure out how to patch the driver for 24-bit as well.

---

### Post by psyke83 on 2006-05-09
To anyone wanting to run in 24bit with a Radeon, I've modified the patch and built against the current source - attached to this post is both the driver and patch. If it works, consider the driver temporary; then the patch can be incorporated into the repos in order to stay up to date.

DISCLAIMER: I took a quick look at the source and modified the original patch, I don't have a Radeon card so I can't test it myself.

---

### Post by echo on 2006-05-10
This works in 24-bit mode now, however, it's super sluggishly slow compared to 16-bit mode.

In particular, it's not the 3d stuff that is slow, it's the 2d stuff. like scrolling in firefox. Or like, when you move a window, there's like a jerkiness as the window comes to a stop, where it like pauses and stuff.

---

### Post by ruffneck on 2006-05-10
[QUOTE=echo]This works in 24-bit mode now, however, it's super sluggishly slow compared to 16-bit mode.

In particular, it's not the 3d stuff that is slow, it's the 2d stuff. like scrolling in firefox. Or like, when you move a window, there's like a jerkiness as the window comes to a stop, where it like pauses and stuff.[/QUOTE]

It is this that kills me. I cannot take the slow scroll in firefox. bah!

---

### Post by benwillcox on 2006-05-10
Well I don't know what I'm doing wrong here, but all I get is a black screen with a mouse pointer when I run compiz-start. And I have to restart GDM to get things back,

I followed the instructions on the first post to the letter. I'm running kernel 2.6.15-22-386 on a Dell D620 with an Intel GMA950.


Thanks,
Ben

---

### Post by kronepils on 2006-05-10
[QUOTE=psyke83]To anyone wanting to run in 24bit with a Radeon, I've modified the patch and built against the current source - attached to this post is both the driver and patch. If it works, consider the driver temporary; then the patch can be incorporated into the repos in order to stay up to date.

DISCLAIMER: I took a quick look at the source and modified the original patch, I don't have a Radeon card so I can't test it myself.[/QUOTE]

Great! That makes it work in 24 bit mode. Nice one, thanks!

I still can't use it, however... When I run compiz-start, compiz starts and it works. But, everything is blinking and windows are drawing trails on the desktop.
I seem to remember to have seen this before, but I don't remember who, how or where.
I have unset all my compiz values in gconf, and tried to disable all plugins. Same same.


Any clues???



Thanks

---

### Post by t3rror on 2006-05-10
[QUOTE=benwillcox]Well I don't know what I'm doing wrong here, but all I get is a black screen with a mouse pointer when I run compiz-start. And I have to restart GDM to get things back,

I followed the instructions on the first post to the letter. I'm running kernel 2.6.15-22-386 on a Dell D620 with an Intel GMA950.


Thanks,
Ben[/QUOTE]

Try reverting back to 2.6.15-21 and see what happens.  I have not been successful in getting this to run under 2.6.15-22.

---

### Post by Milamber_Cubed on 2006-05-10
After the kernel upgrade you need to make sure you reboot so that you are using it  and install the new kernel headers before you try and compile the drm modules. Did you do this?

---

### Post by rendered_one on 2006-05-10
hey that patched driver works for me!!! but I don't get any borders :| I don't think I can find gnome-window-decorator.. or w/e it;s called.. had it been removed/depreciated???

---

### Post by rendered_one on 2006-05-10
Never mind I think I go tgnome-window-decorator back.. but now I'm getting THIS lovly error

compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

and still no window border.. do I need to redo my dri or something? I read somewhere in this thread something about the drivers needing to support that extension...

---

### Post by Permafrost91 on 2006-05-10
rendered_one ... are you using AIGLX or XGL? I don't have any g-w-d borders either since upgrading to 0.0.10. So far no one has been able to help me. If you get end up getting yours to work, please share your solution.

EDIT: Are you using compiz or compiz-vanilla packages?

I have compiz-vanilla on AIGLX, btw.

---

### Post by rendered_one on 2006-05-10
Hey perma,

this is the command I did to install.. 

sudo apt-get install --reinstall compiz-vanilla compiz-vanilla-aiglx compiz-vanilla-gnome gset-compiz

I removed my fglrx drivers (did a COMPLETE removal via synaptic before I issued above cmd)

and after I removed the fglrx driver compiz is definatly working.. but still no window borders :(

I'm going to try a reboot and some other stuff and I will keep you posted.. I am getting wobbly menus and fades right now.. which is a great sign for me! :D

---

### Post by benwillcox on 2006-05-10
[QUOTE=t3rror]Try reverting back to 2.6.15-21 and see what happens.  I have not been successful in getting this to run under 2.6.15-22.[/QUOTE]

I had originally tried it with 2.6.15-21 and it didn't work then either. I just tried reverting back to that again, but still no joy.
Maybe it's the GMA950 graphics thats the problem - anyone else got it working on this card?

Thanks,
Ben.

---

### Post by rendered_one on 2006-05-10
Hey,

Here is the latest error, (still no window borders :(.. BUT I can switch windows by clicking on them which I was unable to do before..) I'm going to try a total reinstall again, and if that doesn't work, I think I'll try a downgrade to see if I can get window-borders..

gnome-window-decorator: no process killed
compiz.real: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
compiz.real: water: GL_ARB_fragment_program is missing

(gnome-window-decorator:6052): Pango-CRITICAL **: pango_color_parse: assertion `spec != NULL' failed

---

### Post by rendered_one on 2006-05-10
Here is another error when I try to load the dock,

CreateDock event received!
Event added!
Processing the next event...
CreateDock event received!
Xlib: connection to ":0.0" refused by server
Xlib: Maximum number of clients reached

This disables compiz and I can only run it when I don't have the dock plugin enabled. Just some more bugs, yay bug hunting.. now.. where is my WINDOW DECORATIONS!!! :P

---

### Post by awakatanka on 2006-05-10
Are the aiglx packages gone from the repo ( xgl.compiz.info)?

---

### Post by jstueve on 2006-05-10
compiz-aiglx and compiz-aiglx-gnome have been depreciated, since the latest versions of compiz and compiz-gnome work with the latest version of xerver-xorg-air-core, and the associated mesa libs in the xgl.compiz.info repo.

There is a meta-package compiz-vanilla-aiglx (that works with quinn's and vanilla) that has the startup programs and settings to make compiz work under an aiglx xserver.

HTH.

---

### Post by rendered_one on 2006-05-10
Has anyone gotten the window decorations working yet? Is this a bug to be fixed in the next release?

---

### Post by dantrevino on 2006-05-10
where is this mythical compiz-vanilla-aiglx metapackage?  I've updated my repos with:
[INDENT][COLOR="RoyalBlue"]#aiglx
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main aiglx
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main aiglx
[/COLOR][/INDENT]

and still get:
[INDENT][COLOR="RoyalBlue"]Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package compiz-vanilla-aiglx
[/COLOR][/INDENT]

---

### Post by jstueve on 2006-05-10
I'm guessing, but it appears that there are some changes to the way the repos (Quinn's and Reggaemanu's) are being hosted... so stand by...

---

### Post by echo on 2006-05-10
[QUOTE=kronepils]Great! That makes it work in 24 bit mode. Nice one, thanks!

I still can't use it, however... When I run compiz-start, compiz starts and it works. But, everything is blinking and windows are drawing trails on the desktop.
I seem to remember to have seen this before, but I don't remember who, how or where.
I have unset all my compiz values in gconf, and tried to disable all plugins. Same same.


Any clues???



Thanks[/QUOTE]

Mine was doing this when I had

Option "EnablePageFlip" "true"

in my xorg.conf  I removed this and it went away.

---

### Post by ZoZo on 2006-05-10
[quote=jstueve]There is a meta-package compiz-vanilla-aiglx (that works with quinn's and vanilla) [/quote]

It doesn't work with quinn's packages because it asks for them to be removed and for the vanilla to be installed instead.

---

### Post by jstueve on 2006-05-10
What I did, was install vanilla and then after compiz-vanilla-aiglx was installed, apt-get install compiz compiz-gnome and it replaced compiz-vanilla and compiz-vanilla-gnome.

---

### Post by ZoZo on 2006-05-10
It doesn't matter, now there is a compiz-quinn-aiglx package :)

---

### Post by ruffneck on 2006-05-10
[QUOTE=ZoZo]It doesn't matter, now there is a compiz-quinn-aiglx package :)[/QUOTE]

yup i saw this today! great stuff!

---

### Post by Permafrost91 on 2006-05-10
what does compiz-quinn-aiglx provide? I still don't have any g-w-d window borders ](*,)

---

### Post by magicrobotmonkey on 2006-05-10
[QUOTE=Permafrost91]what does compiz-quinn-aiglx provide? I still don't have any g-w-d window borders ](*,)[/QUOTE]
Dude, i was missing window borders when I fiirst tried compiz-quinn-aiglx too, heres what I did:```

sudo apt-get remove compiz*
sudo apt-get install compiz-quinn-aiglx compiz-gnome

```

I first did it w/o compiz-gnome and thats when I was missing window borders. Once i installed compiz-gnome, i was good to go

---

### Post by Permafrost91 on 2006-05-10
Hey magicrobotmonkey,

the compiz packages don't work for me. I use the vanilla packages and have compiz-vanilla-gnome installed, but g-w-d is not working.

After starting X manually from a terminal I got [this Xorg.0.log file]("http://umsis.miami.edu/~fboecker/xlog").

Do any of these excerpts perhaps hold a clue as to why I don't have any window borders?

```
Backtrace:
0: /usr/bin/X11/X(xf86SigHandler+0x86) [0x80b4a56]
1: [0xffffe420]
2: /usr/lib/xorg/modules/extensions/libGLcore.so(__MESA_destroyBuffer+0x34) [0xb7b23871]
3: /usr/lib/xorg/modules/extensions/libglx.so(__glXDestroyDrawablePrivate+0x48) [0xb7c00612]
4: /usr/lib/xorg/modules/extensions/libglx.so(__glXUnrefDrawablePrivate+0x30) [0xb7c0067c]
5: /usr/lib/xorg/modules/extensions/libglx.so [0xb7bffdc7]
6: /usr/bin/X11/X(FreeClientResources+0xa1) [0x806fde5]
7: /usr/bin/X11/X(FreeAllResources+0x6a) [0x806fefa]
8: /usr/bin/X11/X(main+0x4a9) [0x806e0d5]
9: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7d20ea2]
10: /usr/bin/X11/X(FontFileCompleteXLFD+0x81) [0x806d611]
```

```
(II) I810(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    8x8 mono pattern filled rectangles
    Indirect CPU to Screen color expansion
    Solid Horizontal and Vertical Lines
    Setting up tile and stipple cache:
        16 128x128 slots
        4 256x256 slots
(==) I810(0): Backing store disabled
(==) I810(0): Silken mouse enabled
(II) I810(0): Initializing HW Cursor
(**) Option "dpms"
(**) I810(0): DPMS enabled
(II) I810(0): X context handle = 0x1
(II) I810(0): [drm] installed DRM signal handler
(II) I810(0): [DRI] installation complete
(II) I810(0): direct rendering: Enabled
(II) I810(0): libshadow is version 1.0.0, required 1.1.0 or greater for rotation.
```

---

### Post by kwicky21 on 2006-05-11
Hey guys,

I followed everything in the first page of this thread, and everything seemed to worked fine for me (no errors whatsoever). However, when I restarted gdm, nothing changed. I also tried restarting the PC, and still nothing has changed.

At least nothing really got screwed up, but the irritating thing is that nothing really happened.

Is there something that I need to run so that xorg-aiglx will run with all the effects?

Thanks,
Cricket La Chica

PS:
I have this file in /etc/xdg/autostart

compiz.desktop
--------------------
```
[Desktop Entry]
Name=compiz
Encoding=UTF-8
Version=1.0
Exec=/usr/bin/compiz-start
X-GNOME-Autostart-enabled=true

```

But I don't think it's running?

---

### Post by rendered_one on 2006-05-11
[QUOTE=Permafrost91]Hey magicrobotmonkey,

the compiz packages don't work for me. I use the vanilla packages and have compiz-vanilla-gnome installed, but g-w-d is not working.

After starting X manually from a terminal I got [this Xorg.0.log file]("http://umsis.miami.edu/~fboecker/xlog").

Do any of these excerpts perhaps hold a clue as to why I don't have any window borders?

```
Backtrace:
0: /usr/bin/X11/X(xf86SigHandler+0x86) [0x80b4a56]
1: [0xffffe420]
2: /usr/lib/xorg/modules/extensions/libGLcore.so(__MESA_destroyBuffer+0x34) [0xb7b23871]
3: /usr/lib/xorg/modules/extensions/libglx.so(__glXDestroyDrawablePrivate+0x48) [0xb7c00612]
4: /usr/lib/xorg/modules/extensions/libglx.so(__glXUnrefDrawablePrivate+0x30) [0xb7c0067c]
5: /usr/lib/xorg/modules/extensions/libglx.so [0xb7bffdc7]
6: /usr/bin/X11/X(FreeClientResources+0xa1) [0x806fde5]
7: /usr/bin/X11/X(FreeAllResources+0x6a) [0x806fefa]
8: /usr/bin/X11/X(main+0x4a9) [0x806e0d5]
9: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7d20ea2]
10: /usr/bin/X11/X(FontFileCompleteXLFD+0x81) [0x806d611]
```

```
(II) I810(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    8x8 mono pattern filled rectangles
    Indirect CPU to Screen color expansion
    Solid Horizontal and Vertical Lines
    Setting up tile and stipple cache:
        16 128x128 slots
        4 256x256 slots
(==) I810(0): Backing store disabled
(==) I810(0): Silken mouse enabled
(II) I810(0): Initializing HW Cursor
(**) Option "dpms"
(**) I810(0): DPMS enabled
(II) I810(0): X context handle = 0x1
(II) I810(0): [drm] installed DRM signal handler
(II) I810(0): [DRI] installation complete
(II) I810(0): direct rendering: Enabled
(II) I810(0): libshadow is version 1.0.0, required 1.1.0 or greater for rotation.
```[/QUOTE]


Perma,
Looks like you and I both have the same problem, yet we are both using COMPLETELY different drivers. So I think we can rule out a driver problem, is there a mismatch problem? My dri is working, my compiz is working, but no window decorations.. have you tried a fresh install and then the howto? I would if I could, but I have a very slow internet connection and to d/l all of those packages again would be.. well, not good. I'm going to try and make sure I don't have any XGL stuff left over.. did u try XGL before this? or might you have some XGL stuff installed? I'm going rooting thru my stsem later on, for now I am off to bed.

Good luck, I'll keep posting until this works!

---

### Post by Balachmar on 2006-05-11
OK, now I'm really curious...
What are the differences between these two compiz packages?
Quinn and Vanilla?
Were the packages before vanilla (that were stated here in the first post then) from Quinn? Because in my opinion the non vanilla packages were better...

---

### Post by Balachmar on 2006-05-11
OK, last updates broke compiz a little bit.
Now the menu's are drawn behind the windows...
Does anybody know how to get this right?
OK, I had quit taht system tray program, that was creating the problem.
Relogin and everything was fixed.

---

### Post by kwicky21 on 2006-05-11
I don't seem to have this command: gnome-window-decorator

How do I fix this?

Thanks,
Cricket La Chica

---

### Post by Balachmar on 2006-05-11
@kwicky21
Do you have compiz-vanilla-gnome (assuming vanilla compiz) or compiz-gnome (assuming that other one...) packages isntalled?

---

### Post by kwicky21 on 2006-05-11
[QUOTE=Balachmar]@kwicky21
Do you have compiz-vanilla-gnome (assuming vanilla compiz) or compiz-gnome (assuming that other one...) packages isntalled?[/QUOTE]

No, but I followed the instructions from page 1 of this thread, which said to install compiz-vanilla-aiglx..

Should I install compiz-vanilla-gnome ?

---

### Post by kwicky21 on 2006-05-11
Okay, I installed compiz-vanilla-gnome and it worked! Well, not really. Because my entire desktop froze to place, although I could still use it. And all the window borders disappeared.. any idea why?

---

### Post by Balachmar on 2006-05-11
did you restart gdm?
or could you start it again from terminal, so that we might get some error messages?

---

### Post by kwicky21 on 2006-05-11
It gave me this:

```

(compiz-start:15843): Gdk-WARNING **: locale not supported by Xlib

(compiz-start:15843): Gdk-WARNING **: cannot set locale modifiers
gnome-window-decorator: no process killed

(gnome-window-decorator:15848): Gdk-WARNING **: locale not supported by Xlib

(gnome-window-decorator:15848): Gdk-WARNING **: cannot set locale modifiers
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32
compiz.real: Root visual is not a double buffered GL visual
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

(gnome-window-decorator:15848): Pango-CRITICAL **: pango_color_parse: assertion `spec != NULL' failed

```

Although I think these three lines need to be re-displayed, to emphasize it:

```
compiz.real: Root visual is not a double buffered GL visual
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
```

Any idea what's wrong?

Thanks, by the way. :)

---

### Post by Balachmar on 2006-05-11
what kind of videocard do you have? ATI? Then you might need a new patched driver.
Is not, then did you set your default display depth at 16?

---

### Post by daverd on 2006-05-11
I spent like an hour last night going through a lot of this thread looking for a solution to the "white cube" problem, tried a bunch of different things and nothing worked. The latest compiz-quinn-aiglx package doesn't help either. Did anyone ever figure out what's causing this?

---

### Post by Balachmar on 2006-05-11
[QUOTE=daverd]I spent like an hour last night going through a lot of this thread looking for a solution to the "white cube" problem, tried a bunch of different things and nothing worked. The latest compiz-quinn-aiglx package doesn't help either. Did anyone ever figure out what's causing this?[/QUOTE]
I have had a white cube as well. But now with everything updated and running the vanilla compiz everything works fine.
Maybe just follow the entire first post again, might help...

---

### Post by Permafrost91 on 2006-05-11
[QUOTE=rendered_one]Perma,
Looks like you and I both have the same problem, yet we are both using COMPLETELY different drivers. So I think we can rule out a driver problem, is there a mismatch problem? My dri is working, my compiz is working, but no window decorations.. have you tried a fresh install and then the howto? I would if I could, but I have a very slow internet connection and to d/l all of those packages again would be.. well, not good. I'm going to try and make sure I don't have any XGL stuff left over.. did u try XGL before this? or might you have some XGL stuff installed? I'm going rooting thru my stsem later on, for now I am off to bed.

Good luck, I'll keep posting until this works![/QUOTE]

Hey rendered_one ... I did try XGL at one point but it was sluggish for me. I then found this thread, deleted all XGL stuff, and followed the instructions to install AIGLX + Compiz (starting at version 0.0.8 I believe, I can't remember, may have been 0.0.9). That worked great for me! ... Until I updated to 0.0.10 at which point I lost g-w-d borders. I updated the DRM module with each kernel upgrade. I don't have the time and patience to reinstall everything. Plus I don't have a CD burner so getting dapper involves going through my breezy CDs first, which sucks (this is a laptop with only a wireless connection through an ndiswrapper driver :( ).

And yes, compiz works great with the exception of the window borders. My windows wobble, I can do the cube, I can bend windows ... water doesn't work but I don't think it works for anyone and I haven't played with the dock plugin yet. In fact, wobbly windows seem a lot more responsive with 0.0.10 but at this point I can't say whether they are because of the new version or because I don't have any window borders. Thanks for your companionship in these difficult times :-D I'm gonna swing over to compiz.net again and see if I can dig something up there.

---

### Post by Grey on 2006-05-11
Permafrost, One of my upgrades in the last few days resulted in the same problems.  Everything worked good, except the window borders didn't work.  My solution to the problem was to unset all my compiz gconf entries, and reinstall all the packages.  A reboot later, and everything was working fine.

---

### Post by kwicky21 on 2006-05-11
[QUOTE=Balachmar]what kind of videocard do you have? ATI? Then you might need a new patched driver.
Is not, then did you set your default display depth at 16?[/QUOTE]

Yes, I do have ATI. ATI Mobility Radeon 9100 IGP. How do I install a new patched driver?

---

### Post by benwillcox on 2006-05-11
Hi Folks,

Well it seems my blank screen problems are no more, with the updates that came through last night.
I installed compiz-quinn-aiglx, and now when I startup I get my desktop, however there are no title bars on the windows or borders (are these the window decorations?), and none of the shortcut key commands work so I can't see that compiz is actually doing anything.
I cleared out the gconf entries (just unticking all the plugin boxes, is that enough?) and rebooted and readded, but nothing changes.

Cheers,
Ben

---

### Post by rendered_one on 2006-05-11
[QUOTE=Permafrost91]Hey rendered_one ... I did try XGL at one point but it was sluggish for me. I then found this thread, deleted all XGL stuff, and followed the instructions to install AIGLX + Compiz (starting at version 0.0.8 I believe, I can't remember, may have been 0.0.9). That worked great for me! ... Until I updated to 0.0.10 at which point I lost g-w-d borders. I updated the DRM module with each kernel upgrade. I don't have the time and patience to reinstall everything. Plus I don't have a CD burner so getting dapper involves going through my breezy CDs first, which sucks (this is a laptop with only a wireless connection through an ndiswrapper driver :( ).

And yes, compiz works great with the exception of the window borders. My windows wobble, I can do the cube, I can bend windows ... water doesn't work but I don't think it works for anyone and I haven't played with the dock plugin yet. In fact, wobbly windows seem a lot more responsive with 0.0.10 but at this point I can't say whether they are because of the new version or because I don't have any window borders. Thanks for your companionship in these difficult times :-D I'm gonna swing over to compiz.net again and see if I can dig something up there.[/QUOTE]


Ok,

So it looks like we have the exact same problem, I've tried removing the files (all compiz) removing ALL the configs related to compiz, and re-did everything.. to no avail... so now I'm going last resort.. my system is right now up-to-date so to speak, so I'm going to back up my entire install, and reinstall...then update and follow the instructions on a clean system.. i'll then try to compare the two, it seems like a lot of work to get eye-candy, but hey.. I'm just that obsessive-compulsive.. :P I'll keep you updated and let you know if this helps AT all... if not, then I think we just need to wait it out for the devs to fix it.

God bless

---

### Post by cuban on 2006-05-11
Thanks, worked great on my Toshiba A10 with intel 855 Extreme gfx, also is alot faster than xgl when i tried that.

---

### Post by Ventajou on 2006-05-11
Hi,

I'm still having the same problem I was having earlier. That is the whole display is shifted down, leaving a band at the top of the screen. Also the mouse pointer is gone.

It basically looks as if the viewport (or whatever it is called in X drivers lingo) has been set a few lines too early. I have tried many combinations of switching drm drivers and xorg i810 (I have an i855gm) drivers between the dapper repository and the ones from the first post. In the end the problem only shows when using the newer xorg drivers from compiz.info.

Is there a newer xorg driver available? Or does anyone know of a fix for the problem? Compiz is not as hot with that band and no pointer!

---

### Post by ErezNoodle on 2006-05-11
This worked great for me for about a week, 
yesterday after apt-get update i got this message:
```
W: GPG error: http://xgl.compiz.info dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
``` 
how can i fix it?

---

### Post by ruffneck on 2006-05-11
@Ventajou

I also have i855gm and I currently have the xorgi810 version "1.6.0-0ubuntu1" installed from the dapper repos. I use the following:

compiz
compiz-gnome
compiz-quinn-aiglx
gset-compiz

All the latest from Quinn's Repo. I also have Raggaemanu's repo enabled as well. So far everthing works fine.

---

### Post by jstueve on 2006-05-11
FYI: Quinn's repo and Reggaemanu's repos are now mirrors, so you should have at MOST one selected...

see: [http://compiz.net/viewtopic.php?id=769](http://compiz.net/viewtopic.php?id=769)

---

### Post by ruffneck on 2006-05-11
[QUOTE=ErezNoodle]This worked great for me for about a week, 
yesterday after apt-get update i got this message:
```
W: GPG error: http://xgl.compiz.info dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
``` 
how can i fix it?[/QUOTE]

hmm.. try:

```
wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
```

---

### Post by ruffneck on 2006-05-11
[QUOTE=jstueve]FYI: Quinn's repo and Reggaemanu's repos are now mirrors, so you should have at MOST one selected...

see: [http://compiz.net/viewtopic.php?id=769](http://compiz.net/viewtopic.php?id=769)[/QUOTE]

Thanks for the headsup.

---

### Post by ErezNoodle on 2006-05-11
thanks, it fixed it.

---

### Post by Permafrost91 on 2006-05-11
[QUOTE=ErezNoodle]This worked great for me for about a week, 
yesterday after apt-get update i got this message:
```
W: GPG error: http://xgl.compiz.info dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
``` 
how can i fix it?[/QUOTE]

I fixed this by commenting out the repo in /etc/apt/sources.list, running apt-get update, then uncommenting the repo and running apt-get update again. Hope this helps.

EDIT: Nevermind, I didn't see the earlier post that the two repos are now mirros.

---

### Post by Permafrost91 on 2006-05-11
[QUOTE=rendered_one]Ok,

So it looks like we have the exact same problem, I've tried removing the files (all compiz) removing ALL the configs related to compiz, and re-did everything.. to no avail... so now I'm going last resort.. my system is right now up-to-date so to speak, so I'm going to back up my entire install, and reinstall...then update and follow the instructions on a clean system.. i'll then try to compare the two, it seems like a lot of work to get eye-candy, but hey.. I'm just that obsessive-compulsive.. :P I'll keep you updated and let you know if this helps AT all... if not, then I think we just need to wait it out for the devs to fix it.

God bless[/QUOTE]

Thanks!

---

### Post by linuxmad on 2006-05-11
Hi...
I am playing with quins debs and cannot find how to put water plugin to work... Has anybody managed to put it to work??](*,)

---

### Post by jstueve on 2006-05-11
water plugin doesn't work on intel cards...

---

### Post by linuxmad on 2006-05-11
:( too bad.....:( :(

---

### Post by Ventajou on 2006-05-11
It's working!!

After many hours spent trying to figure out what was wrong, I finally got my mouse pointer back!

In case someone experiences the same problem (black band at top of screen and mouse pointer gone), here is what I had to do:
- Follow the instructions from the first post
- get the intel drivers for xorg:
 [http://dri.freedesktop.org/snapshots/archive/i915-20060117-linux.i386.tar.bz2](http://dri.freedesktop.org/snapshots/archive/i915-20060117-linux.i386.tar.bz2)
these are the january snapshots. Anything newer than that is broken for me...
All I did was copy the two drivers from the i915 directory in that archive to the appropriate location on my system (/usr/lib/dri and /usr/lib/xorg/modules/drivers IIRC)

Now I am enjoying Quinn compiz in 24bpp with pretty much everything running smooth as something really smooth.

Just in case it's of any use to someone, here are my system's specs:
- Dell Latitude D505 laptop
- Bios rev A10
- Intel 852GM/855GM adapter
- Latest Ubuntu Dapper beta with everything up to date

---

### Post by daverd on 2006-05-11
I fixed my white cube problem, turns out I had to:

apt-get remove compiz*
apt-get install compiz-vanilla-aiglx
apt-get remove _--purge_ compiz-vanilla-aiglx
apt-get install compiz-quinn-aiglx compiz-gnome

Now everything is up and running.

---

### Post by daverd on 2006-05-11
[QUOTE=benwillcox]Hi Folks,

Well it seems my blank screen problems are no more, with the updates that came through last night.
I installed compiz-quinn-aiglx, and now when I startup I get my desktop, however there are no title bars on the windows or borders (are these the window decorations?), and none of the shortcut key commands work so I can't see that compiz is actually doing anything.
I cleared out the gconf entries (just unticking all the plugin boxes, is that enough?) and rebooted and readded, but nothing changes.

Cheers,
Ben[/QUOTE]

I am currently having this same issue. Oddly, the gconf configuration window does have a title bar, but nothing else I run does.

Also, is there a way to turn down the wobbliness? Or configure the other plugins for that matter.

---

### Post by kwicky21 on 2006-05-11
[QUOTE=Balachmar]what kind of videocard do you have? ATI? Then you might need a new patched driver.
Is not, then did you set your default display depth at 16?[/QUOTE]

I tried setting the default display depth to 16, but that didn't work as well. I'm still getting no borders..

And yes, I do have ATI. ATI Mobility Radeon 9100 IGP on my ASUS L4R Laptop. How do I install a new patched driver?

---

### Post by RobNyc on 2006-05-11
Anyone with a x1600 or x1600 pro ?

---

### Post by Balachmar on 2006-05-12
[QUOTE=kwicky21]I tried setting the default display depth to 16, but that didn't work as well. I'm still getting no borders..

And yes, I do have ATI. ATI Mobility Radeon 9100 IGP on my ASUS L4R Laptop. How do I install a new patched driver?[/QUOTE]

A patched radeon driver was discussed in this post, this was for 24 depth.
[http://www.ubuntuforums.org/showpost.php?p=1000050&postcount=689](http://www.ubuntuforums.org/showpost.php?p=1000050&postcount=689)

But my question has not been answered yet, is there any difference between vanilla and Quinn's?
Because I kind of miss my manually rotating cube... And the fact that I can't reset the short-cuts... (I'm using vanilla ATM)

---

### Post by kwicky21 on 2006-05-12
I was finally able to get compiz-vanilal-aiglx to work, but the problem is, everything became slower. As in EVERYTHING. even typing this message is lagging.

Any ideas as to why?

Thanks,
Cricket La Chica

---

### Post by Balachmar on 2006-05-12
[QUOTE=kwicky21]I was finally able to get compiz-vanilal-aiglx to work, but the problem is, everything became slower. As in EVERYTHING. even typing this message is lagging.

Any ideas as to why?

Thanks,
Cricket La Chica[/QUOTE]
yes, turn off the 24 depth! :P
Try 16 now. 24 is reported to be slow quite a few times :)

---

### Post by kwicky21 on 2006-05-12
[QUOTE=Balachmar]yes, turn off the 24 depth! :P
Try 16 now. 24 is reported to be slow quite a few times :)[/QUOTE]

Haha, it works perfectly now, thanks! :) Although I wish I could use 24 depth, hehe.

---

### Post by foxy123 on 2006-05-12
I rebuilt dri modules and install I guess compiz-quinn, compiz-gnome (Iam not at my laptop at the moment). I also reset my compiz configuration as it was advised in this topic. After I enabled Decoration plugin, everything worked again!

However, the wobble plugin is too wobbly for me :) I tried decrease some values using gconf-editor and change shiver to none, but still it's a bit too much.

I wonder what 'bs' plugin does?

---

### Post by togume on 2006-05-12
So, after much time spent searching for this answer I feel utterly stupid. I followed the tutorial to the line and compiz won&#8217;t turn on. It leads me to believe that there might have been some assumed command that I did not enter at the appropriate time which was left out of the tutorial because it is assumed knowledge. 

All the installation procedures completed successfully, all of my conf files are the same as the ones in the tutorial. However, after restarting gdm, nothing happened. I have another dev laptop with an nvidia card which gave me no trouble on the install and is now sporting complete compiz. The current machine I am trying to get this to work in is an HP dv1000. 
When I type compiz-start it gives me the following error: 

... Failed to execute child process "gnome-window-decorator" (No such file or directory)

Any ideas/comments would be greatly appreciated. 

Best, 

Tomás

---

### Post by Permafrost91 on 2006-05-12
[QUOTE=togume]So, after much time spent searching for this answer I feel utterly stupid. I followed the tutorial to the line and compiz won’t turn on. It leads me to believe that there might have been some assumed command that I did not enter at the appropriate time which was left out of the tutorial because it is assumed knowledge. 

All the installation procedures completed successfully, all of my conf files are the same as the ones in the tutorial. However, after restarting gdm, nothing happened. I have another dev laptop with an nvidia card which gave me no trouble on the install and is now sporting complete compiz. The current machine I am trying to get this to work in is an HP dv1000. 
When I type compiz-start it gives me the following error: 

... Failed to execute child process "gnome-window-decorator" (No such file or directory)

Any ideas/comments would be greatly appreciated. 

Best, 

Tomás[/QUOTE]

g-w-d is in compiz-vanilla-gnome or compiz-gnome. Let us know if your windows have borders! (mine still don't) ... are you using AIGLX or XGL?

---

### Post by psyke83 on 2006-05-12
[QUOTE=togume]
When I type compiz-start it gives me the following error: 

... Failed to execute child process "gnome-window-decorator" (No such file or directory)[/QUOTE]if you've installed compiz-quinn, "sudo apt-get install compiz-gnome", or if you've installed compiz-vanilla, "sudo apt-get install compiz-vanilla-gnome".

---

### Post by psyke83 on 2006-05-12
Can anyone with an Intel card tell me what fps you're getting with glxgears? For me at 1024x768, 24bit it's around 800-900 fps, but it sometimes reduces to 600 fps, and in 16bit, 1000-1300 fps. I have an 82865G and I notice slowdown when scrolling in apps such as firefox with compiz (versus perfectly smooth scrolling without); I asked a friend but he noticed no slowdown.. what about everyone else?

I saw this: [https://bugs.freedesktop.org/show_bug.cgi?id=6814](https://bugs.freedesktop.org/show_bug.cgi?id=6814) - but that bug should be fixed by now.

---

### Post by togume on 2006-05-12
Guys, 

Thank you for your help. I knew it would be this dumb little command. After installing the g-d-m using the command given, and restarting, I was using compiz. It worked beautifully for a while and then I lost menus...

To answer your question about borders, they worked perfectly well under gnome. After I went to kde and started compiz I lost borders. 

Thanks again for your help. People like you are making linux go forward (helping others). 

I currently have:
HP DV1000, Centrino 2.0GHz, 512, 80gb, intel 915. 
Running Dapper, AIGLX+compiz

Be well, 

Tomás

---

### Post by foxy123 on 2006-05-12
after today's upgrade I have a problem with compiz and xfce4-panel. It is not on the top of the screen anymore (see the screenshot). I have no idea whether it is compiz or xfce4-panel problem as both were updated today. The panel is fine with xfwm4 and compiz works ok in Gnome.

---

### Post by togume on 2006-05-12
Update:

Everything is working now, for a little while at least. One of the things that was not explicitly stated in this thread was the use of gconf-editor. I know it was nub of me not to go there first, but for a while I was looking for the appropriate file to modify to add the plugins. 

For the newbies out there (like me).
To add/subtract plugins from compiz:
-open a terminal
-type gconf-editor
-navigate to apps>compiz>general>allscreens>options
-change plugins and any other settings

KDE is still problematic, but GNOME is mostly running well. The bug that is giving me most grief in GNOME is that after a little while of using the menus, like "Applications Places System", they go away. Not necessarily go away, but it is as if they were rendering behind the desktop... Quite interesting. I found out that I could still select items from the menu by using the arrow keys, but talk about navigating blindly.

---

### Post by Permafrost91 on 2006-05-12
Well, I still don't have any window borders ... :evil: 

But I have a few questions:

(1) when browsing to /apps/compiz/plugins with gconf-editor only the fade plugin shows up ... could that be the problem for me not having window borders? How can I get the other plugins to show up in gconf again?

(2) would this maybe also explain why I can't save any plugin settings using gset-compiz?

(3) How do I use the zoom plugin? What's the shortcut?

---

### Post by dentaku65 on 2006-05-13
Hi all,
there is someone that wants to explain the difference between 
compiz-vanilla-aiglx and compiz-quinn-aiglx?
I'm using compiz-vanilla-aiglx and is pretty good, except for transset plugin that there is no way to manage it.

TIA
Den

---

### Post by daverd on 2006-05-13
To anyone who is having the problem with no window borders, I don't know if you were having the same problem as me, but it turns out all the windows were just being opened up in the top left corner such that the title bar was hidden under the taskbar at the top... if you alt+left-click to grab the window and move it down, then you get the title bar back. Not sure why the windows are defaulting to that position but it's annoying.

---

### Post by jstueve on 2006-05-13
[QUOTE=dentaku65]Hi all,
there is someone that wants to explain the difference between 
compiz-vanilla-aiglx and compiz-quinn-aiglx?
I'm using compiz-vanilla-aiglx and is pretty good, except for transset plugin that there is no way to manage it.

TIA
Den[/QUOTE]
compiz-vanilla-aiglx uses compiz-vanilla which uses the default CVS as its source.
compiz-quinn-aiglx using compiz which uses Quinn's CVS tree with more patches and plugins.

transset was depreciated (if I recall correctly) and now the state plugin does the same functionality, though with a different syntax.

w:Unkown:80 - see [here]("http://compiz.net/viewtopic.php?id=787") for more info.

---

### Post by Permafrost91 on 2006-05-13
[QUOTE=daverd]To anyone who is having the problem with no window borders, I don't know if you were having the same problem as me, but it turns out all the windows were just being opened up in the top left corner such that the title bar was hidden under the taskbar at the top... if you alt+left-click to grab the window and move it down, then you get the title bar back. Not sure why the windows are defaulting to that position but it's annoying.[/QUOTE]

yes, windows do open in the top left but I can move them anywhere on the screen ... the missing borders are not hidden by the top panel.

---

### Post by dentaku65 on 2006-05-13
[QUOTE=jstueve]compiz-vanilla-aiglx uses compiz-vanilla which uses the default CVS as its source.
compiz-quinn-aiglx using compiz which uses Quinn's CVS tree with more patches and plugins.

transset was depreciated (if I recall correctly) and now the state plugin does the same functionality, though with a different syntax.

w:Unkown:80 - see [here]("http://compiz.net/viewtopic.php?id=787") for more info.[/QUOTE]

Thanks for the explanation....
I have state plugin but is grayed out in the gset-compiz and I'm not able to set tha transparency stuff... it seems that even state plugin has been removed.. :-?

---

### Post by jstueve on 2006-05-13
It seems that gset-compiz isn't upto date with the changes to compiz and compiz-vanilla.

Especially with the state plugin (the order where it loads has changed, and loading it too early (as gset-compiz does) will make it fail.  Add state in gconf-editor in apps>compiz>general>allscreens>options>active_plugins and then make changes in gconf-editor.

---

### Post by dentaku65 on 2006-05-13
[QUOTE=jstueve]It seems that gset-compiz isn't upto date with the changes to compiz and compiz-vanilla.

Especially with the state plugin (the order where it loads has changed, and loading it too early (as gset-compiz does) will make it fail.  Add state in gconf-editor in apps>compiz>general>allscreens>options>active_plugins and then make changes in gconf-editor.[/QUOTE]

In gconf-editor after I inserted the state plugin in active_plugins does not keep the entry... actually I don't have state plugin under the tree of plugins in the gconf-editor :confused:

---

### Post by jstueve on 2006-05-13
is libstate.so in /usr/lib/compiz ?

what does located libstate.so generate?

---

### Post by remusus on 2006-05-13
Any idea when this will be compatible with fglrx drivers?  My card doesn't do well with the radeon one...

It seems like it should work, but for some reason when I have aiglx selected it tried to load "libfglrxdrm.a" instead of the newer, 7.0.0 compatible "libfglrxdrm.so".  Any ideas on that?  Could I fix it by doing a custom build of aiglx, or is it a problem in the fglrx driver?

---

### Post by dentaku65 on 2006-05-14
[QUOTE=jstueve]is libstate.so in /usr/lib/compiz ?

what does located libstate.so generate?[/QUOTE]

uh, I don't have libstate.so 
Could be that in vanilla state plugin is still not available?

---

### Post by Permafrost91 on 2006-05-14
jasquigle solved the no g-w-d window border problem over on compiz.net.

Make sure XLIB_SKIP_ARGB_VISUALS does not get set!

```
$ echo $XLIB_SKIP_ARGB_VISUALS
1
$ unset XLIB_SKIP_ARGB_VISUALS
```

If it's set to 1 (as above) unset it and run compiz-start (or however you start compiz). This should give you window borders back!

I had set /etc/environment at one point after recommendation in some forum to set XLIB_SkIP_ARGB_VISUALS to 1. If you have done the same, make sure to take this out!

---

### Post by simplyw00x on 2006-05-14
Without XLIB_SKIP_ARGB_VISUALS, several apps (loki installers, audacity etc.) will appear semitransparent to the point of being unreadable and unusable and firefox will crash when you view flash movies. There has to be a better solution.

---

### Post by psyke83 on 2006-05-14
[QUOTE=simplyw00x]Without XLIB_SKIP_ARGB_VISUALS, several apps (loki installers, audacity etc.) will appear semitransparent to the point of being unreadable and unusable and firefox will crash when you view flash movies. There has to be a better solution.[/QUOTE]

How about setting XLIB_SKIP_ARGB_VISUALS=1 in /etc/environment & starting compiz like this: "XLIB_SKIP_ARGB_VISUALS=0 compiz-start"?

Or alternatively, edit /usr/bin/firefox and insert the variable there, as well as doing the same for problematic apps?

I only had trouble with Firefox so I use the latter method. I'll give my first idea a shot, tho.

EDIT: The first idea didn't work. See the HOWTO on page 1 to get Firefox and Flash working, and do the same for other apps you've trouble with.

EDIT2: It will work, start compiz like this: "unset XLIB_SKIP_ARGB_VISUALS & compiz-start" (I thought that setting the variable to 0/false was enough, but it needs to be unset as another person found out).

---

### Post by kronepils on 2006-05-14
[QUOTE=remusus]Any idea when this will be compatible with fglrx drivers?  My card doesn't do well with the radeon one...

It seems like it should work, but for some reason when I have aiglx selected it tried to load "libfglrxdrm.a" instead of the newer, 7.0.0 compatible "libfglrxdrm.so".  Any ideas on that?  Could I fix it by doing a custom build of aiglx, or is it a problem in the fglrx driver?[/QUOTE]


AIGLX doesn't work with fglrx, only radeon (and intel and so on).
Try XGL instead. You can't miss it in the forum...

The compiz is the same, so you SHOULD get very similar results.

---

### Post by Permafrost91 on 2006-05-14
[QUOTE=simplyw00x]Without XLIB_SKIP_ARGB_VISUALS, several apps (loki installers, audacity etc.) will appear semitransparent to the point of being unreadable and unusable and firefox will crash when you view flash movies. There has to be a better solution.[/QUOTE]

Well, I thought so too ... but I have been able to watch flash movies in Firefox without any problems so far. Maybe this only affects newer versions of flash? I have not checked what flash movies I can and cannot see since I don't visit all that many flash utilizing sites. What exactly does this variable control anyways? Is there a way to circumvent its usage altogether (even for Firefox) by hardcoding a better solution into Compiz or AIGLX or XGL?

---

### Post by remusus on 2006-05-14
Well, I tried XGL but it gave me weird slowdowns in a lot of apps that it probably shouldn't have been giving me slowdowns (or at least it wasn't reported by anyone else in the forums).

Oh well, I got the new fglrx drivers working on my video card (finally), so maybe it will work now...

---

### Post by Balachmar on 2006-05-15
Just wondering, with Quinn's I used to be able to rotate the cube, using the mouse. Is this still possible somehow?
Because I can't seem to get that to work. This means that I cannot use the top for displaying SVG's for a presentation...

---

### Post by setine on 2006-05-15
Hi!

Great howto! thnx

Just followed the described steps but there seems to have been an update to the packageing.

The following package had to be installed to get it to start automatically (see 4. in the howto):

compiz-vanilla-gnome

have fun, 
setine

---

### Post by jstueve on 2006-05-15
[QUOTE=Balachmar]Just wondering, with Quinn's I used to be able to rotate the cube, using the mouse. Is this still possible somehow?
Because I can't seem to get that to work. This means that I cannot use the top for displaying SVG's for a presentation...[/QUOTE]

Makes sure the keys: edge_flip_dnd, edge_flip_move, edge_flip_pointer are enabled in

apps/compiz/plugins/rotate/screen0/options

That will rotate the cube around the faces with desktops.  To move to the top and bottom of the cube, the keypress is Ctrl+Alt+Button1 then drag.  There is another key in Cube to lock on the top and bottom faces.

---

### Post by Permafrost91 on 2006-05-15
/apps/compiz/plugins only shows the fade plugin! How can I get gconf entries for all the other plugins back?

Also, gset-compiz does not save any of my preferences other than the plugins I want to load. What's the deal? (Version 0.3.2 by the way)

I'm using the latest dapper packages from the xgl.compiz.net repo

---

### Post by jstueve on 2006-05-15
there is a 0.3.3 for gset-compiz that works now with Quinn's compiz.  

you might recursive-unset /apps/compiz, then --reinstall the packages to see if the keys reinstall.  (recommend go back to metacity to do that)

---

### Post by remusus on 2006-05-17
I don't know where to make this recommendation, but perhaps someone could pass along the word that the compiz-start script should have a del os.environ['XLIB_SKIP_ARGB_VISUALS'] at the beginning of start_compiz(), so it's safe to put that variable in your /etc/environment without breaking everything.  Then Flash works in all browsers, not just Firefox... yay.

---

### Post by dengar on 2006-05-17
Someone should add something about gnome windows decorator to the howto, it doesn't come default with dapper (at least not after doing the dist-upgrade) and is required for compiz to work apparently, I had alot of trouble until I followed directions in the thread (although now I can't find which specific ones I did, so I won't confuse people by putting the wrong ones).

---

### Post by linuxmad on 2006-05-17
Gnome-session again.... ](*,) .. I did latest updates and I have the old "not able" to logout problem .. anyone else??

---

### Post by pau on 2006-05-17
Hi,

I followed the howto and everything went fine. I didn't get any error message. I have an intel 855gm just as jstueve has and the result is NOTHING

I have the feeling that it is a problem of the xorg.conf because when logging out and in strange things happens; for instance, a brown screen, or the task bar is missing, or it seems to be ok but not compiz effects

But I cannot see anything wrong. Do you?!?!?!


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
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
#	Load	"GLcore"
#	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
        Load    "dbe"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "DRI"
  Mode 0666
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
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
        Identifier "Intel Corporation Intel Default Card"
	Driver		"i810"
        Option "XAANoOffscreenPixmaps"
	BusID		"PCI:0:2:0"
#        Option "VideoOverlay" "on"
EndSection

Section "Monitor"
        Identifier   "Monitor genèric"
        VendorName   "Monitor Vendor"
        ModelName    "LCD Panel 1280x768"
        HorizSync    20 - 90
        VertRefresh  50 - 100
        DisplaySize 230 138
        ModeLine "1280x768" 81.59 1280 1280 1384 1688 768 769 774 791
EndSection

# 10 Abril 2006:

#Section "Monitor"
#        Identifier      "Monitor genèric"
#        Option  "DPMS"
#        HorizSync    28.0 - 96.0
#        VertRefresh  50.0 - 75.0
#        Modeline "1280x768" 80.14 1280 1344 1480 1680 768 769 772 795
#        Modeline "1024x768" 65.00 1024 1047 1183 1343 768 770 776 805
#EndSection


#Section "Monitor"
#	Identifier	"Monitor genèric"
#	Option		"DPMS"
#EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Monitor genèric"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x768"
	EndSubSection
 	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
        Option "AIGLX"  "true"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
        Mode	0666
EndSection

Section "Extensions"
  Option "Composite" "Enable"
EndSection
```


On the other hand,

> 4. Compiz-aiglx start script
the compiz-aiglx start script is now in package and automatically started on all gnome session startup. If you have some trouble with it you can remove compiz-aiglx.desktop file in /etc/xdg/autostart.

In /etc/xdg/autostart I just have a file called compiz.desktop :

```
[Desktop Entry]
Name=compiz
Encoding=UTF-8
Version=1.0
Exec=/usr/bin/compiz-start
X-GNOME-Autostart-enabled=true
```

Nothing regarding aiglx

What's wrong?!?!

I want compiiiiiiiiiiiiiiiz!!!!!](*,)

---

### Post by remusus on 2006-05-17
[QUOTE=dengar]Someone should add something about gnome windows decorator to the howto, it doesn't come default with dapper (at least not after doing the dist-upgrade) and is required for compiz to work apparently, I had alot of trouble until I followed directions in the thread (although now I can't find which specific ones I did, so I won't confuse people by putting the wrong ones).[/QUOTE]

The gnome-window-decorator program seems to be in compiz-gnome now, the howto should mention that this package is required now.

---

### Post by gandalfn on 2006-05-17
Hi all !

First page updated !

xorg-air 1.0.903: add copy-sub-buffer support, it needs a compiz update to benefit fully of this functionality, propably in next compiz-quinn and compiz-vanilla packages. Firefox hang is fixed in this release too.

new linux-dri-modules packages to prevent CVS compilation

new compiz-quinn-aiglx packages ;)

sorry for this late first page update

Have fun !

---

### Post by WiLLiE on 2006-05-17
I get the dreaded "No GLXFBConfig for default depth, this isn't going to work."
I've been trying for hours now to make it work to no avail.

More info in this thread:
[http://compiz.net/viewtopic.php?pid=6568](http://compiz.net/viewtopic.php?pid=6568)

If you can help, please do. thanks.

---

### Post by pau on 2006-05-18
Anybody please heeeeeelp meeeeeee

(see last post, one page ago)


:-& #-o

---

### Post by thasheep on 2006-05-18
[QUOTE=pau]Anybody please heeeeeelp meeeeeee

(see last post, one page ago)


:-& #-o[/QUOTE]
Do you have this in /etc/gdm/gdm.conf-custom?
```
[servers]
0=aiglx

[server-aiglx]
name=aiglx server
command=/usr/bin/Xorg-air :0
flexible=true
```
And by saying you get nothing, do you mean no special effects, no X session or something else?

---

### Post by pau on 2006-05-18
Yes, I have that... I followed in detail the first post of this thread and did it carefully

I mean that sometimes the screen is blue, sometimes ubuntu-brown (but whe I restart X I see durin one millisecond my original background popping up, as if it was hidden and covered by those colours), sometimes normal but with no compiz xgl effects at all!!

I have a fujitsu siemens lifebook P7010 and the embedded graphic card is Intel 855GME 

I believe it has something to do with the xorg.conf ... but I don't have any idea

---

### Post by Balachmar on 2006-05-18
[QUOTE=pau]Yes, I have that... I followed in detail the first post of this thread and did it carefully

I mean that sometimes the screen is blue, sometimes ubuntu-brown (but whe I restart X I see durin one millisecond my original background popping up, as if it was hidden and covered by those colours), sometimes normal but with no compiz xgl effects at all!!

I have a fujitsu siemens lifebook P7010 and the embedded graphic card is Intel 855GME 

I believe it has something to do with the xorg.conf ... but I don't have any idea[/QUOTE]
the only thing I have different with my 855GME
in the xorg.conf is the defaultdepth.
You should try and set this to 16, instead of 24.

---

### Post by foxy123 on 2006-05-18
[QUOTE=Balachmar]the only thing I have different with my 855GME
in the xorg.conf is the defaultdepth.
You should try and set this to 16, instead of 24.[/QUOTE]
I've got the same chip and it works fine with 24. The thing I learnt from experience with compiz is that you should follow the howto to the letter. If it does not work, uninstall everything and try again. It's quite frustrating sometimes but what you want from alpha software.

---

### Post by lipido on 2006-05-18
Have someone experimented a low performance resizing windows in KDE?? When I want to resize a window, I drag the mouse from one of the window's corners and, 2-5 seconds after!, I see the new size.

I see this behaviour mostly in konqueror.

The other effects (cube, wobbly, maximize, all...) run very smoothy.

My Config
- AIGLX/Compiz-vanilla
- ATI 9200, driver "radeon"

Other question:
Following this tutorial (at the first page), I can't see the packages compiz-aiglx-kde, does it exists? other similar for KDE?

---

### Post by murataht on 2006-05-18
[QUOTE=gandalfn]
new compiz-quinn-aiglx packages ;)
[/QUOTE]

sorry this may be a stupid question, but what does compiz-quinn-aiglx package do?
thanks

---

### Post by Balachmar on 2006-05-18
The Quinn package gives you the Quinn fork of compiz.
There are at this moment to my knowledge 2 types of compiz.
Quinn and Vanilla. Use the one you like best!

---

### Post by pau on 2006-05-18
Hey!

I did it!

I don't know why, but after repeating the steps and choosing

```
compiz-quinn-aiglx
```

instead of vanilla, it worked!

The only problem I have now is that the gset-compiz applet doesn't give me the option of switching back to metacity.

I have noticed that when creating a new user the applet is THERE per default and it gives you the possibility of switching between metacity and xgl

Any hint??

I am trying to record a movie of the desktop to upload it to google videos or youtube but instanbul is not launching...

---

### Post by stenka on 2006-05-18
[QUOTE=lipido]Have someone experimented a low performance resizing windows in KDE?? When I want to resize a window, I drag the mouse from one of the window's corners and, 2-5 seconds after!, I see the new size.

I see this behaviour mostly in konqueror.

The other effects (cube, wobbly, maximize, all...) run very smoothy.

My Config
- AIGLX/Compiz-vanilla
- ATI 9200, driver "radeon"
[/QUOTE]

I experiment the same with a i915GM card and Gnome.

Another thing, quite major, is that it goes messy after hibernation / suspend. It displays empty (no text) and weired colored rectangles instead of the windows and I have to [CTRL]-[ALT]-[BCKSP].

---

### Post by pau on 2006-05-20
It's the same for me... regarding sleep... I get weird colours after suspend-to-RAM (sleep)

I have to restart X again...

why is that?!

But resizing it's ok... it's a BIT slower but not that slower. Mine is an Intel 855GME

---

### Post by damagedspline on 2006-05-20
gandalfn, please add a link to the modified ati driver on the first page of the forum, plus, a minor note to oss radeon driver users might decrease the number of questions about the "xserver keep restarting" or "root visual not double bufferred"...

anyway, with quinz package everything (except hibernation) is working a-ok, well atleaset on my laptop's radeon igp340m (oss driver - 16 bit selected). the shadows look a bit greenish, and i disabled the dock plugin so mplayer will stop it's bad behavior on full screen.
thanks everyone for the hard work.

---

### Post by sorcererx84 on 2006-05-21
Followed the guide but I can't get compiz to work.
> $ libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x31
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

I have i915gm integrated graphics card. Glxinfo shows that direct rendering is enabled AND that I have the GLX_EXT_texture_from_pixmap extension.
I have updated libGL1-mesa and libGL1-mesa-dri to 6.5.1, still nothing.
I am out of ideas.

---

### Post by pau on 2006-05-21
Are there any problems with DRI?

Which kernel are you using?

The issue is usually that the 
DDX driver (server-side) and the 3D driver (client-side) don't agree on 
the same set of visuals.

What visual properties are you requesting ? Can you show us your code ?

If you don't have a single visuals that has alpha bits you can't 
request alpha bits or it will fail, so keep SDL_GL_ALPHA_SIZE at 0. 
These are the "visual attributes" : the number of r, g, b, 
alpha or whatever bits.
Having alpha in the framebuffer is seldom
needed. You can still do blending without it. The framebuffer alpha is
just 0 always. The usual blending operation is GL_SRC_ALPHA,
GL_ONE_MINUS_SRC_ALPHA, which uses only the fragment's alpha. Another
common one is GL_SRC_ALPHA, GL_ONE which is often used to avoid having
to sort objects back-to-front. It doesn't use the framebuffer alpha
either.

---

### Post by FISH on 2006-05-21
New toys yay! Problems I have. miniwin crashes the gnome session. Drop shadows aren't black they glow blue or red. Would be nice if I can speed up the animation somehow on the taskbars and opening maximizing windows. When Applications menu loads the animation doesnt happen, before it would wait then animate now it just does no render. Besides that im still impressed thanks Gandalf ;)

---

### Post by psyke83 on 2006-05-21
A tiny bit off-topic, but I made a minor discovery with Xgl and Intel integrated graphics. First of all, when I use Xorg in conjunction with the updated drm and Mesa drivers (leaving aside compiz), OpenGL performance is fairly bad (the speed is roughly halved compared to normal). With Xorg-air, OpenGL performance is fine.

I tried running Xgl with compiz-vanilla, and the speed was mediocre (unsurprisingly), but I noticed that Xgl relies on Xorg which is in fact a running process while Xgl is used. So I tried renaming Xorg-air to Xorg and moving the original Xorg out of the way, and restarted Xgl - it was quite a bit faster :). Not on par with AIGLX, but certainly getting there, and some operations seem a bit smoother than AIGLX (wobble).

---

### Post by WiLLiE on 2006-05-22
sorcererx84 seems to have the same problem as me.
I'm out of ideas too.

---

### Post by sorcererx84 on 2006-05-22
Nevermind, got it working. From a clean install I installed linux-image-2.6.15-23, linux-dri-modules-common, and linux-dri-modules-2.6.15-23. There is a bug with update-grub (User hook script /sbin/update-grub failed at /var/lib/dpkg/info/linux-image-2.6.15-23-686.postinst line 991.) so it doesn't update your menu.lst and you are still booting into your old kernel. So I copied the default kernel entry and replaced 2.6.15-20 with 2.6.15-23, rebooted and everything worked!

---

### Post by WiLLiE on 2006-05-22
[QUOTE=sorcererx84]Nevermind, got it working. From a clean install I installed linux-image-2.6.15-23, linux-dri-modules-common, and linux-dri-modules-2.6.15-23. There is a bug with update-grub (User hook script /sbin/update-grub failed at /var/lib/dpkg/info/linux-image-2.6.15-23-686.postinst line 991.) so it doesn't update your menu.lst and you are still booting into your old kernel. So I copied the default kernel entry and replaced 2.6.15-20 with 2.6.15-23, rebooted and everything worked![/QUOTE]

I didn't have linux-dri-modules-2.6.15-23-686 for some reason.
Installed, rebooted, still no joy.

I will do the guide one more time later today and see how it goes. ](*,)

---

### Post by sorcererx84 on 2006-05-22
Did you update grub's menu.lst?

---

### Post by WiLLiE on 2006-05-22
Didn't have to, it worked here. (grub)

willie@HP:~$ uname -r
2.6.15-23-686

---

### Post by FISH on 2006-05-22
Is anyone having problems with there gl screensavers and games? they flicker enough to make me have a seizure! Any fix?

---

### Post by damagedspline on 2006-05-23
quinz-compiz+aiglx users:
in case anyone came across shadow frames that stays after popups disapearance and stuff:
remove "Splash" from the window list in the plugin fade (and restart compiz).

in case you want black shadows but get blue/red shadows:
in the decoration plugin select black color (#000000) and change the opacity to your liking.

---

### Post by murataht on 2006-05-23
[QUOTE=damagedspline]
in case you want black shadows but get blue/red shadows:
in the decoration plugin select black color (#000000) and change the opacity to your liking.[/QUOTE]
thanks, it fixed my green-shadow problem.

---

### Post by psyke83 on 2006-05-23
[QUOTE=FISH]Is anyone having problems with there gl screensavers and games? they flicker enough to make me have a seizure! Any fix?[/QUOTE]Yes, I have this problem too. 

Until recently, some opengl applications flickered terribly, so much that it would give seizures (as you said) when running fullscreen, ppracer for example. However, in the past few weeks that problem disappeared, possibly due to updated Mesa libs, or Xorg-air+drivers.

There's another minor kind of flickering that occurs when active (moving) windows are underneath an opengl application, even when fullscreen. So try minimizing all other apps before launching a screensaver or opengl application and see if it helps.

---

### Post by linuxmad on 2006-05-23
did last update and ... it is broken.... nothing works... anyone else??

---

### Post by no1wantdthisname on 2006-05-23
Yeah, the latest updates don't work for me either.  The quinn versions seem to be broken.  I switched to vanilla, and it's working.

---

### Post by linuxmad on 2006-05-23
Yes it is only quins that don't work ... vanilla is working-....thank god8)

---

### Post by bhaagensen on 2006-05-23
Hi, 

I'm having a few minor issues which I'd like feedback on before considering filing in bugzilla. Using compiz-vanilla

1. Scale plugin. Do you get opacity in scale? For me the windows gets opacity while the scaling is done, but as soon as the scale finishes, i.e. all windows are downscaled and layed out, the opacity snaps to 100 for all windows. Perhaps only on aiglx?

2. Disabling visual_bell only lasts until compiz is restarted in which case it gets reenabled.

3. Dragging windows between viewports with the mouse causes alot of graphical errors. I.e. the windows does not properly wrap around the corners of the cube. Best seen with slow animations <Shift>F10. Again, perhaps only on aiglx?

Bjorn

---

### Post by bhaagensen on 2006-05-23
[QUOTE=bhaagensen]Hi, 

I'm having a few minor issues which I'd like feedback on before considering filing in bugzilla. Using compiz-vanilla

1. Scale plugin. Do you get opacity in scale? For me the windows gets opacity while the scaling is done, but as soon as the scale finishes, i.e. all windows are downscaled and layed out, the opacity snaps to 100 for all windows. Perhaps only on aiglx?

2. Disabling visual_bell only lasts until compiz is restarted in which case it gets reenabled.

3. Dragging windows between viewports with the mouse causes alot of graphical errors. I.e. the windows does not properly wrap around the corners of the cube. Best seen with slow animations <Shift>F10. Again, perhaps only on aiglx?

Bjorn[/QUOTE]

Oh, and thats visual_bell in the fade plugin.

---

### Post by ahawks on 2006-05-23
I seem to be having the same problems Render_One was having about a week ago. 

Sometimes:
compiz.real: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.

And I also saw:
"GLX_EXT_texture_from_pixmap is missing"

I basically have no window-manager functionality unless i use they tray applet to switch to metacity, or run metacity manually.

Help? :)

---

### Post by ahawks on 2006-05-23
I just wanted to mention that I just fixed my problem (not even 2 minutes after posting).

Removed all compiz-* packages I had, and installed the compiz-vanilla, -aiglx, -gnome ones.

---

### Post by SkratX on 2006-05-23
Is there a solution for xwinwrap?
I can't get it to work on aiglx... put screensaver and videos playing in the background. And what about the videos? Is there a fix for the blue screen when dragging videos or rotating de cube?

I tried to search for answers through this post, but couldn't find anything...

Hope you could answer me.

---

### Post by togume on 2006-05-23
So, everything is working well now. But looking at all the options, I notice that some of the plugins are not availbale, such as dock. I was wondering if anyone could point me in the right direction to either download and install the plugins or enable them. 

Thank you!

Tomas

---

### Post by psyke83 on 2006-05-23
[QUOTE=bhaagensen]3. Dragging windows between viewports with the mouse causes alot of graphical errors. I.e. the windows does not properly wrap around the corners of the cube. Best seen with slow animations <Shift>F10. Again, perhaps only on aiglx?[/QUOTE]I've noticed this problem too, and yes, it's only on AIGLX. Try installing xserver-xgl and running compiz. Speed is getting much better on Intel chipsets at least, but the reason I'm recommending you try it is so that you'll see the window "wrapping" correctly with the same version of compiz/compiz-vanilla (I've tested here).

---

### Post by ialiende on 2006-05-24
Hello all!! I finally did it!!! and it's amazing, even on a notebook i915GM card. I confess that i was not totally convinced but well, it's true. I've been reading web pages since saturday but all I got was setting opacity when changing focus (I use focus following mouse without raise windows, so I can write on terminal while I read kopete conversation only moving mouse a little). But last night I found the solution to the GLX_EXT_texture_from_pixmap problem. Maybe this solution is explained in this thread before but there are too many pages and I couldn't find it. Well I try to explain it easily but sorry if I speak english bad, because is not my native language :)

My computer is a Dell D410 notebook with an i915 running a Dapper Drake Ubuntu with a 2.6.15-23-686 kernel.

The first thing I did was to follow Gandalfn guide from 1st message of this thread. At this point I had opacity change on but all the rest was nothing :(

Last night I found this [http://www.linuxedge.org/?q=node/58#comment-226](http://www.linuxedge.org/?q=node/58#comment-226), and the solution in the first reply was clear for me: "There is no GLX_EXT_texture_from_pixmap in nvidia GL library now. To use it, you have to install cvs Mesa ([http://cvs.freedesktop.org/mesa/Mesa/](http://cvs.freedesktop.org/mesa/Mesa/)) to a separate directory (/usr/lib/mesa, for example) and run compiz with 'LD_LIBRARY_PATH=/usr/lib/mesa compiz [plugins]'.". Sure I had read this a lot of times the last days but was not so clear. Ok, I have no nvidia card but I read similar things and had to try it.

Then I did a checkout of the mesa code with

   ```
cvs -d :pserver:anoncvs@cvs.freedesktop.org:/cvs/mesa co Mesa
```

and compiled with

   ```
make linux-dri-x86
```

I chose linux-dri-x86 target reading the Makefile file and guessing a little :). The compilation was going well but I was tired and thinking to stop it until today morning when I saw libGL.so passing and I couldn't stop my fingers from pressing ctrl-c :P

Finally copied ./lib/libGL* to a new directory under my home and did

   ```
LD_LIBRARY_PATH=~/mesa compiz [here go the plugins you want to load]
```

and voila!! all started to happen (perhaps compiling all the stuff is better but I don't want to mess my dapper installation and this partial solution is all I need by now)

Now its time to investigate because I have some little problems but everything seems to go very well. The first problem I found was that under kde with kdm the compiz window manager was loaded but I couldn't use the keyboard. Finally this morning I tried gnome under gdm and that problem went away. But I found another problem :). I don't know why but even choosing gnome session under gdm, when the session is loading the window manager seems to stop and looking the processes list I found some kde stuff like kdeinit, kded, ... I have to investigate more but then I killed them and started compiz with

   ```
DISPLAY=:0.0 gnome-window-decorator &
```
   ```
DISPLAY=:0.0 compiz --replace gconf decoration state transset wobbly fade minimize cube rotate zoom scale move resize place switcher trailfocus water bs &
```

(Setting the display was necessary because I had to do the last things from text terminal, that is, ctrl-alt-F1 from X)

Finally the session started and now all is running nice :)

This page is good to start the fun: [http://en.opensuse.org/Compiz](http://en.opensuse.org/Compiz)

Well, I hope the explanation is so clear but feel free to ask and I'll try to answer :)

Good luck

---

### Post by GarethMB on 2006-05-24
Sweet. Worked on intel 852. :D video playback is choppy tho.

---

### Post by nik on 2006-05-24
[QUOTE=GarethMB]Sweet. Worked on intel 852. :D video playback is choppy tho.[/QUOTE]

Did you try MPlayer? Only one that works good in fullscreen for me...

---

### Post by GarethMB on 2006-05-24
[QUOTE=nik]Did you try MPlayer? Only one that works good in fullscreen for me...[/QUOTE]
I've just tried m player and whilst its better than VLC or totem. its still slightly choppy in FS. But i'll just use metacity to watch FS vids its no biggie.

On a side note anyone know how to make the keybindings actually work?

---

### Post by psyke83 on 2006-05-24
[QUOTE=GarethMB]Sweet. Worked on intel 852. :D video playback is choppy tho.[/QUOTE]
If you're running 24 bit, use totem-xine and Xv, it works fine with absolutely no slowdown. Works in windowed and fullscreen mode, except that it doesn't update with compiz effects, you need to wait for "wobble" to stop etc.

---

### Post by indridi on 2006-05-24
I just installed xorg-air using the instructions in this thread, and now, finally, I have got hardware acceleration working (for the most parts, at least) on my laptop. It is a:
ibm thinkpad R40 (type 2722) with a
Radeon Mobility M7 LW [Radeon Mobility 7500] graphics card

Thanks
Indriði

---

### Post by nik on 2006-05-24
Sorry for being extremely dense, but what does this (from first page) really say?

video.driver:mad:shm

---

### Post by simplyw00x on 2006-05-24
video.driver: xshm with no spaces

: x is the :x

---

### Post by jstueve on 2006-05-24
```
video.driver:xshm
```

the &91;code] tag folx.

---

### Post by jstueve on 2006-05-24
grrr.. then I hack up the ascii code...

---

### Post by meonline25 on 2006-05-24
Hi I installed aiglx on sunday (May 21) I ran some updates on my PC but now 

compiz is not working! (one of the updates changed my gdm.conf file).

Metacity is working but compiz is not...

---

### Post by meonline25 on 2006-05-24
Oops...looks like it worked after I rebooted using the 386 Kernel instead of the 686
kernel...:)

---

### Post by Sargonmetal on 2006-05-27
Hi,

I hope someone could help me. I got it all working except two things:

1) when I **glxinfo | grep direct** I get **direct rendering: No**
2) when I switch to a different tty I get my screen split into two, and I can't see almost anything.

BTW, I've never been able to active direct rendering, and I don't know what to do.
Here's some outputs that I get:

> lspci | grep Host
0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)


> dmesg | grep drm
[4294700.128000] [drm] Initialized drm 1.0.1 20051102
[4294700.142000] [drm] Initialized i915 1.4.0 20060119 on minor 0:
[4294700.142000] [drm] Used old pci detect: framebuffer loaded


> cat /var/log/Xorg.0.log | grep render
(II) I810(0): direct rendering: Enabled


I'm newbie on this, any help will be very appreciated! Ask if you need any other outputs.
Thanks and good job on this thread!

---

### Post by Beonix on 2006-05-27
Great! It works!

Tried it 2 times. First attempt gave me borderless windows. Second time I tried it on a fresh system. Followed the guide(using vanilla) and now everything works flawlessly.

Thanks a lot :D 

Dell Inspiron 1300(intel 915)

---

### Post by tigrux on 2006-05-29
As I have said before, after installing the intel 810 driver 1.6.0, the 3D performance is severily affected.

Is there a way to get back to the performance found in intel driver 1.4.0?

---

### Post by zAo on 2006-05-30
I installed and everything went fine, except for the borders. I searched the forums, but I cannot find the "gnome-window-decorator-aiglx" mentioned, gnome-window-decorator is started though.

Any ideas? Thanks in advance.

---

### Post by maxx_730 on 2006-05-30
I installed and followed the instructions on an ATI Radeon Mobility 9200, didn't work, i got weird screens when i logged in, without borders and fonts etc. So i remove all the packages i had installed and restored the configuration. Now, however i OpenGL programs like Xmoto dont work anymore! I get errors like these:
```
[fglrx] API ERROR: could not register entrypoint for IsFramebufferEXT
[fglrx] API ERROR: could not register entrypoint for BindFramebufferEXT
[fglrx] API ERROR: could not register entrypoint for DeleteFramebuffersEXT
[fglrx] API ERROR: could not register entrypoint for GenFramebuffersEXT
[fglrx] API ERROR: could not register entrypoint for CheckFramebufferStatusEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture1DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture2DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture3DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferRenderbufferEXT
[fglrx] API ERROR: could not register entrypoint for GetFramebufferAttachmentParameterivEXT
[fglrx] API ERROR: could not register entrypoint for GenerateMipmapEXT
```
Anyone got an idea on how to fix this? Thanks in advance.

---

### Post by siena on 2006-05-30
Please click one of the Quick Reply icons in the posts above to activate Quick Reply.

---

### Post by uzi09 on 2006-05-30
how difficult is it to remove aiglx if you don't want it anymore?

---

### Post by navil on 2006-05-31
I got my gnome-compiz/aigxl working fine on my intel 915. I did an upgrade last week and for some reason my "always on top" window setting seems to be disabled. Does any one know any way to get it back ?? :-k

---

### Post by dabear on 2006-05-31
[QUOTE=uzi09]how difficult is it to remove aiglx if you don't want it anymore?[/QUOTE]
just aptitude purge/remove the packages and remove/undo the customizations you did to your xorg.conf

---

### Post by Balachmar on 2006-06-01
I get the following error when trying to update repos:
W: GPG error: [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release: The following signatures couldn't be verified because the public key is not available:

How can I fix it?

---

### Post by tigrux on 2006-06-01
You need to import the keys.
There are instructions at [http://xgl.compiz.info](http://xgl.compiz.info)  and its mirrors.

---

### Post by t3rror on 2006-06-01
I don't know about you all, but the latest updates have really slowed down my machine.  It had been running very smooth for the past month.  It seems like something in the last set of compiz-vanilla updates for the dapper release has drastically slowed my machine down.  It is acceptable, but also noticeable.  How often do you think that we will see updated compiz packages now that dapper has been officially released?

---

### Post by tonyo46 on 2006-06-01
I had exactly the same problem as you t3rror.
I solved it installing compiz-quinn, and now it works quite well as before (when I had compiz-vanilla)...

---

### Post by t3rror on 2006-06-01
[QUOTE=tonyo46]I had exactly the same problem as you t3rror.
I solved it installing compiz-quinn, and now it works quite well as before (when I had compiz-vanilla)...[/QUOTE]


Whoa!!! Big difference.  Thanks for the heads up.  Things are working great again!:mrgreen:

---

### Post by BigErn on 2006-06-01
root window is not a double buffered visual  ](*,) 

That's what I always get when I try to start compiz.  That's what I've been getting for weeks.  I know my radeon (7500) is capable of aiglx/compiz, as I had it working a couple months back, but went back to normal X because of lack of 24-bit color support in the radeon driver.  I've tried everything it seems.  Here's my Xorg.conf, can anyone help me?  Please?

BTW, I have the latest aiglx stuff and the latest dri-modules-* and all that jazz.  The X server seems to start up fine.  Just no go on compiz.

```

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
#       Load    "GLcore" #--disabled for aiglx--
#       Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dbe"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility 9000 (M7 LW)"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
#       Option          "AGPMode"       "4"
#        Option          "AGPFastWrite"          "1"
#        Option          "HWCursor"              "true"
#       Option          "NoAccel"               "false"
#       Option          "AGPSize"               "32"
#        Option         "BufferSize"            "2"
#       Option          "ColorTiling"           "no"
#        Option                 "DisplayPriority"       "BIOS"
#       Option          "DynamicClocks"         "yes"
#        Option         "EnableDepthMoves"      "yes"
#       Option          "EnablePageFlip"        "yes"
#        Option         "RenderAccel"           "yes"
#        Option         "RingSize"              "8"
        Option          "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon Mobility 9000 (M7 LW)"
        Monitor         "Generic Monitor"
        DefaultDepth    24  #was 24, changed to 16 for aiglx
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Option "AIGLX" "true"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
    Option      "Composite"     "Enable"
EndSection


```

---

### Post by Melvil on 2006-06-01
I'm trying to run AIGLX on my 9700 radeon using the radeon driver. Xorg-air loads fine, the radeon driver has DRI enabled. But as soon as I login with GDM all I get is a cursor on a red screen - I can move the cursor though.
Any ideas why nothing is showing up? (gnome panels etc)

---

### Post by p1rate on 2006-06-02
Has anyone had any success getting this working on an i915GM card?

I've followed the instructions exactly as stated using both compiz-vanilla and compiz-quinn and each time the borders on my windows disappear. Not even opacity works for me, like it has for other peoples 915GM cards.

Do I need to install any additional Intel drivers? Or do I just use the ones that are automatically installed with Dapper?

Also does 'sudo /etc/init.d/gdm restart' differ from hitting control+alt+backspace, or do they both perform the same thing?

---

### Post by tigrux on 2006-06-02
Mine is an intel 950 gma which uses i915 for DRI and i810 for xorg.

I can tell you it works really nice in my Dell Inspiron E1505.

Just notice, if you play games like Unreal Tournament, then don't install compiz because it requires i810 driver 1.6 which is much slower than the 1.4 shipped with dapper.

---

### Post by Jingo on 2006-06-02
Just wondering where to get the latest radeon-driver capable of running aiglx?

Just adding the repositories didn't give me the posibility to update the driver!

---

### Post by e_liming on 2006-06-02
Can I use AIGLX in Xfce 4.4 Beta in Xubuntu?

---

### Post by damagedspline on 2006-06-03
[QUOTE=BigErn]root window is not a double buffered visual  ](*,) 

That's what I always get when I try to start compiz.  That's what I've been getting for weeks.  I know my radeon (7500) is capable of aiglx/compiz, as I had it working a couple months back, but went back to normal X because of lack of 24-bit color support in the radeon driver.  I've tried everything it seems.  Here's my Xorg.conf, can anyone help me?  Please?

BTW, I have the latest aiglx stuff and the latest dri-modules-* and all that jazz.  The X server seems to start up fine.  Just no go on compiz.
[/QUOTE]

[http://www.ubuntuforums.org/showpost.php?p=1000050&postcount=689](http://www.ubuntuforums.org/showpost.php?p=1000050&postcount=689)
try to install the patched radeon driver from the link above (and don't upgrade the ati-driver to newer versions - just keep the deb file in a known folder and if you mistakenly updated the driver reinstall it using 'dpkg -i ...' from the shell).
what taste of compiz do you use, vanilla or quinz?

jingo, thats for you 2... i've also searched if there's a repository which contain the patched driver and found non...

---

### Post by iXce on 2006-06-03
Just a quick note... The latest official compiz is broken due to a modification in switcher plugin that dramatically kills performances. I submitted a patch to the compiz mailing list (it's a conceptual problem)

---

### Post by foxy123 on 2006-06-03
the latest update of vanilla compiz made impossible to watch movies with mplayer and vlc (at least as I ahev not tried anything else). see the screenshot:

---

### Post by iXce on 2006-06-03
[QUOTE=foxy123]the latest update of vanilla compiz made impossible to watch movies with mplayer and vlc (at least as I ahev not tried anything else). see the screenshot:[/QUOTE]
That's the problem I was speaking of ;) I'll make sure that my patch is integrated in the next compiz-vanilla release

Edit : if someone can ensure me that the patched radeon driver posted above works well i can manage to get it inside the reggaemanu repos (with the author authorization)

---

### Post by Melvil on 2006-06-03
Neither radeon driver works for me, gnome-session won't load

---

### Post by bhaagensen on 2006-06-03
[QUOTE=iXce]Just a quick note... The latest official compiz is broken due to a modification in switcher plugin that dramatically kills performances. I submitted a patch to the compiz mailing list (it's a conceptual problem)[/QUOTE]


Quick, but very useful note. Compiz has been usless for me the last days, but the patch seems to have done the trick. Nice work !

Edit: I'm on intel.

---

### Post by damagedspline on 2006-06-03
[QUOTE=Melvil]Neither radeon driver works for me, gnome-session won't load[/QUOTE]

what's your xorg.conf configuration? compiz flavour? 
if your hardware is radeon 9700 i think you should use the xgl instead of aiglx...

---

### Post by yteh on 2006-06-03
Gandalfn... thanks! Worked like a charm for me.

---

### Post by Melvil on 2006-06-03
[QUOTE=damagedspline]what's your xorg.conf configuration? compiz flavour? 
if your hardware is radeon 9700 i think you should use the xgl instead of aiglx...[/QUOTE]

Yes, it's a 9700. XGL works fine with fglrx, but I wanted to give AIGLX a shot with the native radeon drivers since my fglrx is broken.

---

### Post by didobuntu on 2006-06-03
All freezes under ATI Mobility 7500

---

### Post by psyke83 on 2006-06-03
[QUOTE=iXce]Edit : if someone can ensure me that the patched radeon driver posted above works well i can manage to get it inside the reggaemanu repos (with the author authorization)[/QUOTE]

I'm not sure if you were referring to me as the "author" (re: the radeon patch), but just in case, you have my full permisssion to use my patch. In fact, it's only slightly modified from Kristian Høgsberg's original patch (I'd say he simply missed the second instance in which to enable a double buffered visual in the code).

Changing the subject, will the effect for moving window across the cube get fixed soon? It's still working with Xgl, but not AIGLX :(

---

### Post by didobuntu on 2006-06-03
Hi psyke,
I unfortunately installed you patch ... and all has freezed in my (not running yet)  aiglx-compiz environment ... how can I come back and reinstall the old one ?

---

### Post by psyke83 on 2006-06-03
[QUOTE=didobuntu]Hi psyke,
I unfortunately installed you patch ... and all has freezed in my (not running yet)  aiglx-compiz environment ... how can I come back and reinstall the old one ?[/QUOTE]

What ATI card have you got exactly? To restore your old driver, reboot (if grub doesn't display hit the escape key), then pick recovery mode. When it's finished booting, type "sudo apt-get install --reinstall xserver-xorg-driver-ati" and reboot once more.

(Or if you can Ctrl+Alt+F1 to a terminal, reinstall the driver without restarting, then restart gdm).

---

### Post by didobuntu on 2006-06-03
OK good , I did it ,

To me aiglx-compiz works halfly (or less LOL) ... I can fortunately switch from compiz metacity ... but in compiz there is no window borders, I cannot move them ... maybe I dont't know how to use compiz ... my dream of seeing the famous cube on my screen seems too far to reach .... ](*,) 

for example here what I get when I start compiz from a line command 

code:  compiz-start

gnome-window-decorator: aucun processus tué
compiz.real: Root visual is not a double buffered GL visual
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0


Is it possible that aiglx-compiz runs on an ATI Mobility 7500 card?

---

### Post by Belathor on 2006-06-04
I just followed the Howto and now have no window borders or panels. ](*,)  I followed the steps even though I found many of them to already have been implemented. I did, however, have to add the Section "Extensions" to my xorg.conf file. I must have missed something!?!

---

### Post by t3rror on 2006-06-04
For the border problems:

You all will need to purge the associated packages that you have installed now and reinstall them.  Do a search on this thread for the exact command.  I cannot remember it, sorry.

---

### Post by Belathor on 2006-06-04
[QUOTE=t3rror]For the border problems:

You all will need to purge the associated packages that you have installed now and reinstall them.  Do a search on this thread for the exact command.  I cannot remember it, sorry.[/QUOTE]

Thanks! Worked for me! 

Now I just have to see about those upside down and backwards icons in the dock! :D  Atleast its working! Now I can go Ubuntu evangelizing! Yay! :mrgreen:

---

### Post by Jingo on 2006-06-04
[QUOTE=iXce]That's the problem I was speaking of ;) I'll make sure that my patch is integrated in the next compiz-vanilla release

Edit : if someone can ensure me that the patched radeon driver posted above works well i can manage to get it inside the reggaemanu repos (with the author authorization)[/QUOTE]

The radeon driver works for me (on T42 with Radeon 7500).

BUT... 24bpp is awfully slow and xorg-air used 14%cpu at idle. At 16bpp it runs nicely.
An overall problem on radeon (7500 at least) is GPU utilization. My GPU runs hot after installing the new DRI thing, even without compiz started. With compiz started its even worse.
Guess the new DRI utilizes the GPU a lot more then before.
This is not good on a laptop!

But no problem with the driver so far!

---

### Post by sherlock-holmes on 2006-06-04
I always had this combination working.... following this how to ....

BUT...

WHn i try to open firefox it opens in stages.... means... i could see the border growing in stages despite i get all the animations such as wobbly, water effects.. 

this is not only observed for firefox but also for many other applications such as a nautilus browser, etc....

what could be the problem....i have ati 9600 radeon ..(IBM T42) 

thank you

---

### Post by v8YKxgHe on 2006-06-04
Hey,

I've been trying to get XGL working for the past 2-3 days with no luck. Do you think I should try AIGLX instead? My system is:

AMD x2 3800 ( Running 32bit Dapper ) 
ATI X800XT
DFI LanParty UT Ultra-D

Regards,

---

### Post by didobuntu on 2006-06-04
[QUOTE=Belathor]Thanks! Worked for me! 

Now I just have to see about those upside down and backwards icons in the dock! :D  Atleast its working! Now I can go Ubuntu evangelizing! Yay! :mrgreen:[/QUOTE]
Hi,
Where did you find the commands to purge and reinstall tha packages to resolve the border problem ?

---

### Post by Belathor on 2006-06-04
I just sudo apt-get remove compiz* and then reinstalled the stuff from the first page using quinns compiz.

---

### Post by FiveNines on 2006-06-04
[QUOTE=iXce] if someone can ensure me that the patched radeon driver posted above works well i can manage to get it inside the reggaemanu repos (with the author authorization)[/QUOTE]

I can confirm that this patch has done the trick for me.  With compiz-start in my session, I would get no borders etc.  If i took it out of my session and ran compiz-start at terminal I saw the error about double buffering or whatever.

Works like a charm in 16bpp with the patched driver! I have a Radeon Mobility 7500

Still experimenting with 24bpp, but thus far all it seems to do is completely lockup my laptop.

---

### Post by didobuntu on 2006-06-04
Hello,

Is there a way to know whether or not aiglx-compiz is well installed ? 
Some command has to be done to make the cube moves or the windows moving ?

---

### Post by Nonno Bassotto on 2006-06-04
I use Gnome and have a ATI Radeon 9200 card without proprietary driver (at least I think, is there a way I can check?), so I think this is the right HowTo I should follow to enable compositing (is this right?).
Now the real question is: what if something goes wrong? The following HowTo
[http://www.tectonic.co.za/view.php?id=916&page=1](http://www.tectonic.co.za/view.php?id=916&page=1)
(which does not apply to my case) shows how to install Compiz, but every system configuration is done in the file ~/.Xsession, so if something goes wrong one just has to login in failsafe mode and delete the file (or restore an old working one) to restore the original setting (I think the point is that in failsafe mode the Xsession file is ignored).
Is there a way to modify gandalfn's HowTo to be sure that it will be as easy to come back?

---

### Post by jhs_s on 2006-06-05
Hi!

I have installed everything according to this Howto! Anyway, I am getting the following when trying to start compiz.

> 
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0


Hardware is i915GM on a HP nx6110  laptop. The solution posted here for some nVidia cards don't work here and libGL.so.1.2 really contains GLX_EXT_texture_from_pixmap.

Thanks,
Johannes

---

### Post by Aldoo on 2006-06-05
Now that Xorg 7.1 is released, with all the AIGLX stuff in the official trunk, shouldn't it work with compiz ?

Or do we still need a patched "xorg-air" ?

With latest Xorg and compiz-quinnstorm-0.0.11.2 (and also with vanilla), I've got this error message :

LIBGL_ALWAYS_INDIRECT="TRUE" compiz --indirect-rendering --replace gconf
compiz: Another window manager is already running on screen: 0
compiz: No managable screens found on display :0

But I've got no window manager running (--replace kills it). Btw the error message is different when a window manager is actually running.

I modified compiz sources so that it skips that test. Then compiz would run, but the contents of the windows were black (or white), and the error log complains about not beeing able to bind windows to textures.

Am I the only one with those problems ?

---

### Post by sev(n) on 2006-06-05
Hey guys,
I had many problems when first using this howto, and I think I found the root of all of them.
```
[servers]
0=aiglx

[server-aiglx]
name=aiglx server
command=/usr/bin/Xorg-air:0
flexible=true

```

This was what the howto said to put into your gdm.conf-custom file, using this i was getting various "could not start x" errors. (Blue screen at startup, failed to manage screen)

Here's what fixed all my problems:
```
[servers]
0=aiglx

[server-aiglx]
name=aiglx server
command=/usr/bin/Xorg-air
flexible=true

```

Simply take the ":0" (colon zero) out of that line. Then sudo reboot, it worked for me the first time.

---

### Post by Glupak on 2006-06-05
Hey guys.

Just wanted to share with you two quick-and-dirty scripts I wrote to get suspend/resume to work for all users. You just need to put them in the indicated locations and make them executable; they'll be sourced automatically from sleep.sh.

```

#!/bin/bash
#/etc/acpi/suspend.d/25-compiz-stop.sh

COMPIZUSER=`ps -Ao user,comm | grep compiz.real | awk '{print $1}'`
killall gnome-window-decorator &
killall compiz.real &

```

and

```

#!/bin/bash
#/etc/acpi/resume.d/99-compiz-resume.sh

if test ! -z $COMPIZUSER;then
        export DISPLAY=:0.0
        sudo -H -b -u $COMPIZUSER /usr/bin/gnome-window-decorator
        sudo -H -b -u $COMPIZUSER /usr/bin/compiz --strict-binding --indirect-rendering --replace gconf
fi

```

This assumes your xserver runs on :0.0 .

Take care.
Glupak

---

### Post by jvdv360 on 2006-06-06
I have these problems (this is an extract for another post of me):
 
I first tried the method gandalfn posted, and used the compiz-vanilla package. No errors whatsoever but when I restart gdm, the taskbars, icons etc all disappear. I can only see the desktop background. However, things should work because I can open windows and when hovering over those windows (which I can't see), the mouse cursor changes...
Second try was with the compiz-quinn package: I can see the taskbars and icons now, but I can't click on them.
If I disable the "extensions" section in xorg.conf however, these two methods work fine, only I don't have the eyecandy.
Finally I tried with the compiz-aiglx and compiz-aiglx-gnome package and after restarting gdm I can see the taskbar and icons, they work, only there are no window borders drawn.
Again disabling the "extensions" section worked to restore to normal (without the eyecandy).

Can anybody help me out?

---

### Post by wushumofo on 2006-06-06
ok... I've done all this.. installed compiz-quinn packages... 

when I boot to gnome... it freezes.

I'm running kubuntu, with gdm, kde and gnome installed...

I'm trying to configure it to run compiz with gnome and aiglx.

video card: intel extreme 2 - 855GME chipset. (had it running on dapper... but sluggish)

heard this would work good for intel cards, but when it starts... it freezes :(

any tips? hints?

---

### Post by wushumofo on 2006-06-06
[QUOTE=sev(n)]Hey guys,
Simply take the ":0" (colon zero) out of that line. Then sudo reboot, it worked for me the first time.[/QUOTE]

tried that... no dice there either.

---

### Post by damagedspline on 2006-06-07
[QUOTE=Glupak]Hey guys.

Just wanted to share with you two quick-and-dirty scripts I wrote to get suspend/resume to work for all users. You just need to put them in the indicated locations and make them executable; they'll be sourced automatically from sleep.sh.
Glupak[/QUOTE]

tried what yu suggested, but it didn't work - i tried:
echo $COMPIZUSER

but it looked as if it wasn't initialised after i returned from hibernation...

---

### Post by GarethMB on 2006-06-07
Anyone else's PC playing up after todays updates to the quinnstorm packages

---

### Post by gandalfn on 2006-06-07
Well,

xgl.compiz.info updated with newest linux-dri-modules and xserver-xorg-drivers-ati, good news aiglx work now with radeon card

have fun !

---

### Post by BigErn on 2006-06-07
Gandalf, you are the man!  Everything is working beautifully on my radeon 7500 now.  Hats off to you! =D> =D> =D> =D> =D> =D> =D> =D>

---

### Post by damagedspline on 2006-06-08
no luck here with the new radeon drivers... i still came across the issue of a freezed system after ctrl-alt-f1 ctrl-alt-f7... gdm also restart itself unattended...

radeon igp340m - oss drivers

EDIT: gdm restarts solved by updates

---

### Post by Bionic_Beefpile on 2006-06-08
Awesome thread, this runs great, even on my integrated Intel graphics.  Hats off!!

---

### Post by homicidalmo0se on 2006-06-08
this tutorial worked great on a dell e510 with 945g onboard graphics using the i810 drivers. thank yoooooou! =D>

---

### Post by linuxmad on 2006-06-09
[QUOTE=Glupak]Hey guys.

Just wanted to share with you two quick-and-dirty scripts I wrote to get suspend/resume to work for all users. You just need to put them in the indicated locations and make them executable; they'll be sourced automatically from sleep.sh.

```

#!/bin/bash
#/etc/acpi/suspend.d/25-compiz-stop.sh

COMPIZUSER=`ps -Ao user,comm | grep compiz.real | awk '{print $1}'`
killall gnome-window-decorator &
killall compiz.real &

```

and

```

#!/bin/bash
#/etc/acpi/resume.d/99-compiz-resume.sh

if test ! -z $COMPIZUSER;then
        export DISPLAY=:0.0
        sudo -H -b -u $COMPIZUSER /usr/bin/gnome-window-decorator
        sudo -H -b -u $COMPIZUSER /usr/bin/compiz --strict-binding --indirect-rendering --replace gconf
fi

```

This assumes your xserver runs on :0.0 .

Take care.
Glupak[/QUOTE]

Glupak these scripts are very good, and I guess you should create a new post with them, so that people find them the easy way. 

Note: The scripts work very well however I found them NOT to work in a situation that  I will try to reproduce:
-log in
-sleep ot hibernate
-resume

It all works as it is supposed !!!

Now ...without logging off or rebooting or halting..
-sleep or hibernate
-it fails... you see the screensaver and you are prompted for password

So i guess it works well first time, and if you try a second time during the same session it does not work anymore.
If you can please try to take a look at this, as I think there are lots of people that will enjoy your script. A good idea is to move this to the how-to section=D> 
thanks
josé

---

### Post by killbill on 2006-06-09
Anyone get the recent aiglx running with intel video card?

And any update on this tutorial? 

And one more question , how to install aiglx+compiz all over again (freshly)?

---

### Post by Aldoo on 2006-06-09
[QUOTE=gandalfn]Well,

xgl.compiz.info updated with newest linux-dri-modules and xserver-xorg-drivers-ati, good news aiglx work now with radeon card

have fun ![/QUOTE]

Should I understand it was not working anymore with radeon cards ?
Is that the reason why it wouldn't work on my PC ? (see my post above)

---

### Post by hatatitla on 2006-06-09
I did it! :)

now everything works, only one problem was with gconf-custom item in compiz preferences, but now it seems that it works. I've used a custom pathce Ati driver from my friend, now will try the regular one. 

thanks for the howto :)

---

### Post by jx2150 on 2006-06-09
Hello people - gandalfn, thanks for the HowTo.

I setup compiz as per your directions yesterday and it went smoothly. However, afterwards, amarok failed to launch. The splash screen came up but it would either crash or freeze the system completely, needing a reboot.

So I compiled amarok from source after removing it completely, hoping that would do the trick, but I've got the same problem.

Any tips?

-Jack

---

### Post by psyke83 on 2006-06-09
[QUOTE=jx2150]I setup compiz as per your directions yesterday and it went smoothly. However, afterwards, amarok failed to launch. The splash screen came up but it would either crash or freeze the system completely, needing a reboot.[/QUOTE]First of all, try switching to metacity before launching amarok. If it works, troubleshoot the issue with compiz, by disabling plugins one by one (start with splash). If neither works, remove your custom compiled version, and reinstall the standard version from the official repos. If that works but you want the newest package, see this announcement:

[http://kubuntu.org/announcements/amarok-1.4.php](http://kubuntu.org/announcements/amarok-1.4.php)

---

### Post by damagedspline on 2006-06-09
[QUOTE=jx2150]

So I compiled amarok from source after removing it completely, hoping that would do the trick, but I've got the same problem.

-Jack[/QUOTE]
i came across the same problem,  i fixed it by erasing the local user amarok data dir: ~/.kde/share/apps/amarok
when i restarted amarok it started as it did in the first time i ran it, and then it worked(at least for me)... i never figure out why it worked, because it wasn't supposed to work.
EDIT: same goes for openoffice which on start looks stuck forever - remove the folder ~/.openoffice.org2
and still couldn't figure out y removing the user conf folders solve these issues... any1 have a clue?

---

### Post by drpolish on 2006-06-09
would this take up more battery juice?

---

### Post by jx2150 on 2006-06-09
[QUOTE=damagedspline]i came across the same problem,  i fixed it by erasing the local user amarok data dir: ~/.kde/share/apps/amarok
when i restarted amarok it started as it did in the first time i ran it, and then it worked(at least for me)... i never figure out why it worked, because it wasn't supposed to work.[/QUOTE]

Yep, that worked with metacity and now with compiz. Thanks a lot.

-Jack

---

### Post by wakady on 2006-06-09
Thanks gandalfn =D> =D> =D>
But u didn't explain any thing about working with ati....???:-k:-k
1- does it work with radeon 8500+ (Mine is 9600XT)...
2- if it does do i have to change to the "ati" driver in xorg or what shall i do#-o
3- will be great if u put a how to for ati users if it really work on ati 8500+
if any one got it work can u please post a little how to here or in a new thread..
thax alot guys\\:D/ \\:D/

---

### Post by Jeff250 on 2006-06-09
To any i915 AIGLX-compiz user: Are shadows working properly?  Mine are solid black.  I'm not using the repositories though--I'm compiling from source, but if they're working for you repo guys, I'd like to ultimately figure out why so I can fix it on my end, otherwise I won't bother. :cool:

---

### Post by damagedspline on 2006-06-09
have any1 beside me came across the following problem: everything is working fine and then allof a sudden gdm crash unattended, restart (gdm) and requesting a login - and now for the real suprise - after login all i get is the mouse curser and... nothing more. ctrl-alt-backspace has the same behavior. only after a full restart everything works fine.

btw, the new compiz update looks smoother then before but has some annoying new issues - but that's not for this forum.

EDIT: gdm sudden crashes solved by updates - however the "ctrl-alt-backspace" bug remains

---

### Post by killbill on 2006-06-09
How can I perform a fresh install of aiglx+compiz?

Please. 


I deleted the /etc/xdg/autostart/compiz.desktop.  and dunno how to resolve the problems.

---

### Post by Glupak on 2006-06-10
linuxmad,

I can't reproduce your problem here, for me it works. Could you check whether this is indeed a problem with the script, i.e. by manually killing compiz, suspend, resume, restart compiz?

Thanks,
Glupak

---

### Post by Slicedbread on 2006-06-10
I could not get it to work, I'm probably configuring something wrong but I followed the instructions correctly. Everytime I try to use the fglrx driver, Xserver fails to start. If someone can show me how to get the error output I will post it. When I use the ati driver option it boots up but obviously know effects.

I get "No servers found" when trying to restart the gdm with fglrx drivers, but if I restore /etc/gdm/gdm.conf-custom to its default settings, everything works.

---

### Post by linuxmad on 2006-06-11
To GLUPAK:

I tried manually killing compiz and gnome-window-decorator, then sleep and resume and worked as supposed. Then one second time "inside" the same session i tried again sleep, resume ... and it all worked. I am not saying that this is related with your scripts. It can be related with the general SLEEP and HIBERNATE / RESUME scripts.:confused:

---

### Post by psyke83 on 2006-06-11
[QUOTE=Slicedbread]I could not get it to work, I'm probably configuring something wrong but I followed the instructions correctly. Everytime I try to use the fglrx driver, Xserver fails to start. If someone can show me how to get the error output I will post it. When I use the ati driver option it boots up but obviously know effects.

I get "No servers found" when trying to restart the gdm with fglrx drivers, but if I restore /etc/gdm/gdm.conf-custom to its default settings, everything works.[/QUOTE]
You can't use the fglrx driver with AIGLX, you have to use the open source driver. If you insist on using fglrx, try Xgl instead.

---

### Post by Slicedbread on 2006-06-11
[QUOTE=psyke83]You can't use the fglrx driver with AIGLX, you have to use the open source driver. If you insist on using fglrx, try Xgl instead.[/QUOTE]

The free drivers are they the ones labled 'ati' in xserver? I did not insist on using fglrx, its  that there is no direct rendering with the default 'ati' drivers.

---

### Post by psyke83 on 2006-06-11
[QUOTE=Slicedbread]The free drivers are they the ones labled 'ati' in xserver? I did not insist on using fglrx, its  that there is no direct rendering with the default 'ati' drivers.[/QUOTE]
Yes, "ati" is a wrapper for r128, radeon, etc. If you can't get direct rendering working with the open source drivers, then try Xgl, it may work better for you.

---

### Post by Slicedbread on 2006-06-11
[QUOTE=psyke83]Yes, "ati" is a wrapper for r128, radeon, etc. If you can't get direct rendering working with the open source drivers, then try Xgl, it may work better for you.[/QUOTE]

Im going to have to because when I follow the guide, nothing loads at all, I just get a blank screen with my wallpaper. I heard that aiglx was better with low end graphics cards. I didnt have a problem with xgl except a longer load time and some scrolling issues in firefox.

---

### Post by linuxmad on 2006-06-12
I am using the latest debs from quins and I am having one strange problem with compiz. Everything is working fine, but after a few hours when I use the switcher plugin it drains all cpu to 100% and it gets TOOOO SLOW. If I restart compiz it all goes to normal. The thing is that this occurs randomly and I cannot say what triggers this. Is anyone else having this? :confused: :confused: 
Thanks

---

### Post by damagedspline on 2006-06-12
[QUOTE=linuxmad]I am using the latest debs from quins and I am having one strange problem with compiz. Everything is working fine, but after a few hours when I use the switcher plugin it drains all cpu to 100% and it gets TOOOO SLOW. If I restart compiz it all goes to normal. The thing is that this occurs randomly and I cannot say what triggers this. Is anyone else having this? :confused: :confused: 
Thanks[/QUOTE]

I've tried using the switcher to its max but didn't come  across the issue - but i've bumped to another issue whch might be linked:sometimes while rotating the cube the screen doesn't fit right and the screen splits into two parts which contain the same screen.
r u working in 24bpp mode or 16bpp? (i think it's related)
what plugins r enabled?

---

### Post by linuxmad on 2006-06-12
I am working on 24 bpp. I have everything execpt for water(which does not work with intel boards), dock and miniwin. I heard there was something wrong with swicther... It could be responsible for this:confused:

---

### Post by fluid_motion on 2006-06-12
Seems quite sluggish on my ATi X300, P4 3Ghz with 1GB RAM.  Is the slowness in speed due to the poor graphics card? How do I check where the bottleneck is?

And why are the plugins settings for state, trailfocus, dock, miniwin, bs greyed out?

---

### Post by damagedspline on 2006-06-13
[QUOTE=fluid_motion]Seems quite sluggish on my ATi X300, P4 3Ghz with 1GB RAM.  Is the slowness in speed due to the poor graphics card? How do I check where the bottleneck is?

And why are the plugins settings for state, trailfocus, dock, miniwin, bs greyed out?[/QUOTE]

there were several posts in the forum about sluggines by people which use the fglrx supported cards but use the oss ati driver... i guess the oss driver just doesn't fit well for cards that can use the "other" driver.
u'd better use fglrx+xgl (instead of oss ati+aiglx) for now.

---

### Post by Balachmar on 2006-06-15
Hi, I get the following error, if I want to change my theme now:
> 
The default theme schemas could not be found on your system.  This means that you probably don't have metacity installed, or that your gconf is configured incorrectly.

And I want to change the theme, into a SVG theme, so that the zooming should be able to scale the images as well. That should be possible, right?
So how can I fix this?

---

### Post by gemini91 on 2006-06-15
Hi, I installed AIXGL on my laptop, just to see if it worked. Install went just fine.
Hardware:
IBM A31 laptop, 1.60GHz cpu
768 MB memory
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]

Tried both quinn and vanilla versions. At 'Default Depth 24' resize does not work. Any window that you try to resize becomes smaller and you can never make it bigger. You can make it smaller but never get beyond a certian size going up.
Under 'Default Depth 16' resize works fine but Firefox will not run. I get :

don@don:~$ firefox %u
The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 120 error_code 8 request_code 145 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

GLXGEARS output:
Normal:
7886 frames in 5.0 seconds = 1577.120 FPS
Default Depth 16
5701 frames in 5.0 seconds = 1140.109 FPS
Default Depth 24
3431 frames in 5.0 seconds = 687.175 FPS

System seems responsive and all works well except firefox.

---

### Post by erdalronahi on 2006-06-15
Hi, 

I managed to install aiglx and compiz on a rather old machine (ati 9000 mobile, 512 MB RAM). The 3-D effetcs like "cube" and the 2-D effects like "wobbly" are really smooth and fast. 

Unfortunately a lot of things happening INSIDE the windows are really slow. Not only video replay, writing text also got remarkably slower, especially in Firefox. 

Do I have to shutdown some plugins to boost performance? Or is there another way? The reduced writing speed is annoying.

---

### Post by redline6561 on 2006-06-15
OK. I've been reading the forum over [here]("http://www.ubuntuforums.org/showthread.php?t=192909&page=4") and was wondering if I'm better off in the long run trying to upgrade to xorg 7.1 now and then setup my compositing manager or follow the instructions here to get up and running and worry about upgrading X and maybe breaking my config later.

I'm running a fresh install of Dapper 386 on an AMD64 box with a Radeon 9800XT. I still haven't installed ATI's binaries. Please advise.

---

### Post by mscman on 2006-06-15
[QUOTE=fluid_motion]Seems quite sluggish on my ATi X300, P4 3Ghz with 1GB RAM.  Is the slowness in speed due to the poor graphics card? How do I check where the bottleneck is?

And why are the plugins settings for state, trailfocus, dock, miniwin, bs greyed out?[/QUOTE]
The plugin settings are greyed out because you don't have the plugins enabled.  Once you enable them, the plugin settings become active (and configurable).

---

### Post by linuxmad on 2006-06-16
WARNING !!!!
LAtest gnome-session update ... seems to bring back the old log out troubles...
Anyone else...???

---

### Post by DerCorny on 2006-06-16
Yeah, I seem to encouter the same problem.

---

### Post by jdmpike on 2006-06-16
Is "the same problem" issues with logging out and logging back in? When I do this after an initial login, I get a brown screen with a thinking cursor that just hangs and hangs...

Also - I want to ask if people are once again experincing problems maximizing windows/viewing things fullscreen? It seems to work for a while, but then I'll maximize something and get nothing but a black screen in the window.

It is so fun to have things to tinker with again...

Peace, love, and Ubuntu!

jdmpike

---

### Post by foxy123 on 2006-06-16
I wonder if it is possible to add "Switch to xfwm4" to gset-compiz?

---

### Post by DerCorny on 2006-06-17
[QUOTE=jdmpike]Is "the same problem" issues with logging out and logging back in? When I do this after an initial login, I get a brown screen with a thinking cursor that just hangs and hangs...[/QUOTE]
yes, you describe exactly what I have here. No fullscreen problems so far, but I haven't run anything in fullscreen yet.

---

### Post by mitjab on 2006-06-17
maybe stupid question but i follow this howto and i install compiz but when i login into my account i can't see anything different, only compiz shortcut is in the top and programs are opening little strange, i can't see x for sthut it down.

what i must see when i install compiz?

---

### Post by Nekrataal on 2006-06-17
After the last security Update it got broken, all the effects are really slow, im uninstalling it until it get fixed

---

### Post by damagedspline on 2006-06-18
[QUOTE=mitjab]maybe stupid question but i follow this howto and i install compiz but when i login into my account i can't see anything different, only compiz shortcut is in the top and programs are opening little strange, i can't see x for sthut it down.

what i must see when i install compiz?[/QUOTE]

try pressing alt-ctrl-left arrow for instance

---

### Post by BeeRockxs on 2006-06-18
I just followed the HOWTO with my Radeon 8500, and it kinda works, except for one problem: Lots of times, windows don't show their content, just white, or just a few of the buttons, like in this screenshot: [IMG]http://www.deckmaker.mynetcologne.de/compiz-bug.png[/IMG]

Anyone have an idea?

---

### Post by damagedspline on 2006-06-18
[QUOTE=BeeRockxs]I just followed the HOWTO with my Radeon 8500, and it kinda works, except for one problem: Lots of times, windows don't show their content, just white, or just a few of the buttons, like in this screenshot: 
Anyone have an idea?[/QUOTE]

Please post your device section from /etc/xorg.conf and the list of the currently loaded plugins

---

### Post by BeeRockxs on 2006-06-18
[QUOTE=damagedspline]Please post your device section from /etc/xorg.conf and the list of the currently loaded plugins[/QUOTE]

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon R200 QL [Radeon 8500 LE]"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
        Option		"AGPMode" "4"
	Option		"MonitorLayout" "NONE, CRT"
	Option		"EnablePageflip" "true"
	Option		"RenderAccel" "false"
EndSection

Using the plugins gconf, decoration, wobbly, fade, minimize, cube, rotate, zoom, scale, move, resize, place, switcher, rain.

Also, some menus in the applications menu don't open correctly, I see the outline of the submenu, but not the contents of menu.

---

### Post by damagedspline on 2006-06-18
[QUOTE=BeeRockxs]Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon R200 QL [Radeon 8500 LE]"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
        Option		"AGPMode" "4"
	Option		"MonitorLayout" "NONE, CRT"
	[COLOR="Red"]#[/COLOR]Option		"EnablePageflip" "true"
	[COLOR="Red"]#[/COLOR]Option		"RenderAccel" "false"
EndSection
[/QUOTE]
1) add '#'

[QUOTE=BeeRockxs]
Using the plugins gconf, decoration, wobbly, fade, minimize, cube, rotate, zoom, scale, move, resize, place, switcher, rain.
[/QUOTE]
2) disable rain (&water) - it won't work anyway

[QUOTE=BeeRockxs]
Also, some menus in the applications menu don't open correctly, I see the outline of the submenu, but not the contents of menu.[/QUOTE]
3) in the fade plugin, remove the fade for "menu" & "splash" & "unknown" 
4) restart compiz

- those are my suggestions for now - just temp fixes till there'll be better radeon drivers are out there, it supposed to work...

---

### Post by BeeRockxs on 2006-06-18
[QUOTE=damagedspline]
- those are my suggestions for now - just temp fixes till there'll be better radeon drivers are out there, it supposed to work...[/QUOTE]


Those changes didn't change a thing, windows often still look like this:
[img]http://www.deckmaker.mynetcologne.de/compiz-bug2.png[/img]

---

### Post by andreag on 2006-06-18
Everything worked great for me with Ubuntu Dapper on a Toshiba laptop with Intel graphics card. Much better than xgl which somehow worked and somehow not.

Except: the "Quit" menu now no longer works, it executes logout instead of letting me chose to hibernate, suspend, logout or shutdown. I suspect there can be some problem with the hybernate script. I would not like to give up the possibility of hibernating the computer, somebody knows a solution?

---

### Post by damagedspline on 2006-06-19
[QUOTE=BeeRockxs]Those changes didn't change a thing[/QUOTE]

have you tried adding the line
```
Option          "XAANoOffscreenPixmaps"
```
to the device section in xorg.conf (it is in the howto)

---

### Post by Balachmar on 2006-06-19
[QUOTE=andreag]Everything worked great for me with Ubuntu Dapper on a Toshiba laptop with Intel graphics card. Much better than xgl which somehow worked and somehow not.

Except: the "Quit" menu now no longer works, it executes logout instead of letting me chose to hibernate, suspend, logout or shutdown. I suspect there can be some problem with the hybernate script. I would not like to give up the possibility of hibernating the computer, somebody knows a solution?[/QUOTE]
No this is the infamous log-out bug. Which has been re-introduced with the latest updates. Just have to wait for a fix I guess...
It is also the only problem I am experiencing by the way.

---

### Post by damagedspline on 2006-06-19
[QUOTE=Balachmar]No this is the infamous log-out bug. Which has been re-introduced with the latest updates. Just have to wait for a fix I guess...
It is also the only problem I am experiencing by the way.[/QUOTE]

i guess this bug only apply to intel chipsets - logout screen works fine on my radeon chip

---

### Post by Balachmar on 2006-06-20
mmm, I am unable to execute this command:
sudo /sbin/ldm-manager

I don't have ldm-manager. Which package do I need to get this?

Also:
sudo apt-get install linux-dri-modules-common linux-dri-modules-`uname -r`

Doesn't work on my computer.
I wanted to try these things to see wether or not I could fix the log-out problem.

---

### Post by Milamber_Cubed on 2006-06-20
[QUOTE=damagedspline]i guess this bug only apply to intel chipsets - logout screen works fine on my radeon chip[/QUOTE]

I updated yesterday after a few weeks of being away and I don't have the logout screen problem. This is on my integrated intel chip. I guess a newer package has been released in the past few days?

Anyone still having the problem??

---

### Post by bomanizer on 2006-06-20
[QUOTE=mscman]The plugin settings are greyed out because you don't have the plugins enabled.  Once you enable them, the plugin settings become active (and configurable).[/QUOTE]

How? I tried searching on this... :confused:

---

### Post by damagedspline on 2006-06-20
[QUOTE=bomanizer]How? I tried searching on this... :confused:[/QUOTE]

plugins that are not marked with V (as seen in the attachment) will be grayed out

---

### Post by siriusnova on 2006-06-20
Can someone guide me for my Thinkpad T30 and ATI Radeon 7500 with a simple current howto?

This thread is way too long for me to read the entire thing.

---

### Post by gookie on 2006-06-20
Thanks for the guide! 
Works flawlessly on my DELL Latitude D400 Intel 855GM Integrated Graphics.
No glitch and looks definitely faster than XGL.

:)

---

### Post by bomanizer on 2006-06-21
[QUOTE=damagedspline]plugins that are not marked with V (as seen in the attachment) will be grayed out[/QUOTE]

Silly me.. :D 

But apparently I don't have all the plugins installed. I installed according to the howto, did I miss something?

---

### Post by Dougan on 2006-06-21
Hi,

I am having a little trouble installing aiglx/compiz on kubuntu 6.06. I have managed to install it on ubuntu dapper and its work great, however upon trying to run it in kubuntu dapper i get the following compiz log error:
> libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32
/usr/bin/compiz.real: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real: Failed to manage screen: 0
/usr/bin/compiz.real: No managable screens found on display :0

Note I was unsure how to modify the KDM and so I just changed kdmrc to read:
> [X-:*-Core]
AllowNullPasswd=true
AllowShutdown=All
ServerArgsLocal=-nolisten tcp
ServerCmd=/usr/bin/Xorg-air :0

The rest of kdmrc is the same as default. Is this right?

The other thing I've tried was something suggest on the Compiz community forum. I put this into the terminal:
> compiz --indirect-rendering --strict-binding --replace gconf

and compiz started however I had no window boarders and compiz gave the same error as shown above except that the 3 bottom lines were replaced by:
> compiz.real: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.


Can anyone help?
Cheers

---

### Post by myha on 2006-06-21
Hi all,

I am finaly able to run xgl on my desktop with intel i915 card, with xgl I couldnt get dri to work... Well, not quite xgl but it doesnt matter... As long as it looks great and works well...:cool: 

I have one question though... When I try to configure plugins the last five of them are greyed out... What is the reason for that?

Also, can I install both quinn and vanilla packages and somehow switch between them or just select one of them?

regards

---

### Post by Sethiano on 2006-06-21
Hi all!

I'm trying the impossible (or at least it feels that way), to get AIGLX/Compiz to work on a Radeon 7500 Mobile (IMB Thinkpad T41).

Now here's the deal. The first thing that I did to try if Compiz works on my hardware was tho try out the Kororaa live-CD. It worked great with no problems at all. Now as I understand Radeon 7500 won't work with flgxr drivers so XGL is no option, but I hope AIGLX is :lol: 

The problem for me is that I get a classic white screen with a slightly darker border, where my Gnome panels normaly is located. The mouse is showing and working, but I can't do anything but move it around.

I have tried this without any result

* Followed the HOWTO step-by-step
* Changed screen deph to 16 
* Changed from compiz-quinn to compiz-vanilla
* Comment out all "DRI"-refrence
* Changed the driver in "xorg.conf" from the orginal "ati" to "radeon"

One thing is quite strange, If I boot into my dear white screen and then hit Alt+Ctlr+F1 and restart GDM and log in again, my icons shows for like 1/2 sec and now my wallpaper is visible, but nothing more than that.

So if anybody got an idea or have a Radeon 7500 and got any kind of tip how to get this to work, please answer! ]

Thanks in advanced!

P.S As I've browsed this thread for answers, I've seen many refrences to "pached ati drivers", but I can't find an accualy link to those. If anybody could post a link I would be happy ;)

---

### Post by Balachmar on 2006-06-22
A search on this thread on "patched ati" came up with this result...
[http://www.ubuntuforums.org/showpost.php?p=1000050&postcount=689](http://www.ubuntuforums.org/showpost.php?p=1000050&postcount=689)

---

### Post by lawngn0mex on 2006-06-22
I'm unable to get a screen running aiglx... I found out dri isn't working... any ideas?

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
	Load	"dbe"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Driver		"ati"
	Option		"XAANoOffscreenPixmaps"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Monitor		"Generic Monitor"
	DefaultDepth	16	
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Option "AIGLX"  "true"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection

```

```

$ glxinfo | grep "direct rendering"
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No

```

---

### Post by thomasbilgram on 2006-06-23
I followed exactly the Howto, but I cannot avoid the "white cube". When I try to log in, I can see my wallpaper and the bars for about 1 second. Then the whole display turns white. I can turn this white cube, but that's it. I tried with compiz-vanilla-aiglx and compiz-quinn-aiglx, nothing works :-/. I also tried to vary the DefaultDepth: 8 <-> 16 <-> 24, no effect.
Does anybody know a solution??
____________________________
Dapper Drake 6.06
ASUS S5200N, Intel GM855

---

### Post by Sethiano on 2006-06-23
**thomasbilgram:** I got the same exact problem as you, as your can see above. Witch graphic care are you using.

---

### Post by mmk on 2006-06-23
I have a Radeon 7500 (Mobility) video card. The last version of XGL (from the same repository), as AIGLX both work (Ubuntu Dapper).
Here is the thing though... I find XGL a little faster. The weird stuff is that direct rendering is enabled in AIGLX and not working in XGL.

So... with Xorg: Direct rendering - yes,  glxgears fps: ~1000
XGL: Direct rendering - no, glxgears: ~90 fps
AIGLX: Direct rendering - yes, glxgears: ~600fps

I have though some warnings like:
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d

I tried both vanilla and quinn, but ofcourse they have the same aiglx server.
So, even though aiglx has direct rendering (with the warnings) ... i find it slower ...

Just using gaim my CPU stays close to 90% .... (just like XGL :P)

Other than that, movies work fine (even in full screen) - i tried both xine and mplayer.

My question: is it normal to have the high CPU usage?
I have Pentim M Banias 1.4Ghz, 1MB L2cache, 512 ram and Radeon Mobility 7500 (rv200 chip, no proprietary driver).
Thank you.

---

### Post by Sethiano on 2006-06-23
[QUOTE=mmk]I have a Radeon 7500 (Mobility) video card. The last version of XGL (from the same repository), as AIGLX both work (Ubuntu Dapper).
Here is the thing though... I find XGL a little faster. The weird stuff is that direct rendering is enabled in AIGLX and not working in XGL.

So... with Xorg: Direct rendering - yes,  glxgears fps: ~1000
XGL: Direct rendering - no, glxgears: ~90 fps
AIGLX: Direct rendering - yes, glxgears: ~600fps

I have though some warnings like:
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d

I tried both vanilla and quinn, but ofcourse they have the same aiglx server.
So, even though aiglx has direct rendering (with the warnings) ... i find it slower ...

Just using gaim my CPU stays close to 90% .... (just like XGL :P)

Other than that, movies work fine (even in full screen) - i tried both xine and mplayer.

My question: is it normal to have the high CPU usage?
I have Pentim M Banias 1.4Ghz, 1MB L2cache, 512 ram and Radeon Mobility 7500 (rv200 chip, no proprietary driver).
Thank you.[/QUOTE]

I see that you have manage to get your 7500 M to work both in XGL and in AIGLX. I (and probaly more than me) can't get this work so it would be great if you had the time to answer some of thees questions!

How did you manage to get your 7500 M to work with XGL and AIGLX? (Did you use this HOWTO for AIGLX?) 
Witch drivers do you use? 
How does your xorg.conf look like?

Many thanks!

---

### Post by mmk on 2006-06-23
On a fresh dapper install, i got all the upgrades. Here is my sources.list:

```
deb http://www.beerorkid.com/compiz dapper main
deb http://www.beerorkid.com/compiz dapper aiglx

deb http://theli.free.fr/packages/dapper/ ./
deb http://mirror3.ubuntulinux.nl/ dapper-seveas freenx

deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe


```

For XGL, just "apt-get install xserver-xgl", and then "apt-get install compiz compiz-gnome gset-compiz"

For AIGLX, follow the guide from post #1. That is, install the appropiate compiz packages (they will also install xserver-xorg-air-core) and add the required lines in xorg.conf.

Here is my xorg.conf:
```

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dbe"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
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
        Identifier      "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
        Driver          "radeon"
        Option          "XAANoOffscreenPixmaps"                      # for AIGLX only!
        Option          "AGPMode"       "4"
        Option          "UseFBDev"      "false"
        Option          "AGPFastWrite"  "true"
        Option          "EnablePageFlip"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Option          "AIGLX"         "true"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"                                             # for AIGLX only!
        Option          "Composite"     "Enable"           # for AIGLX only!
EndSection                                                            # for AIGLX only!


```


And that's just about it.
But painfully slow :( I'll try 16bpp.
Anybody reported good performance with AIGLX on radeon ?

---

### Post by damagedspline on 2006-06-24
.... i've managed to run xgl on a oss driver radeon (IGP340M) by changing my xorg.conf - those work for me, are just suggestion, and if its working i ain't gona break it trying to investigate. :)
since it is not related to this forum, DO NOT post related questions here, i'll open a new forum if such doesn't exist - just wanted you to know that the possibility exist (for the new ppl):
i've installed xgl related packages + quinz compiz
```
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
        Driver          "ati"
        Option          "AccelMethod" "EXA"
        Option          "AGPMode" "4"
        Option          "AGPFastWrite" "true"
        #Option                 "EnablePageFlip" "true"
        Option          "DDCMode"
        Option          "RenderAccel" "true"
        Option          "SubPixelOrder" "NONE"
        Option          "ColorTiling" "false"
        BusID           "PCI:1:5:0"
EndSection
```
added to gdm.conf-custom
```
[servers]
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true
```
added to gnome-session
```
compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher 
```
but, it has to run at 24bpp, gset-compiz&gnome-window-decorator should be run manualy, direct rendering is out of the question so dont glxgears, displaying video on fullscreen is slow as :evil: ... (and finally, firefox doesn't crash due to flash as opposed to aiglx!!!)
beside the buts, works fine on a compaq evo n1020v equippt with radeon igp340m and a 2.4ghz cpu

---

### Post by Eversmann on 2006-06-24
Hi!

I've followed the first post, and tried with quinn and vanilla packages. It's a clean install and fglrx works ok (direct rendering, everything).

But if i make the changes on gdm.conf-custom and xorg.conf.

If i do, i can't get xserver to run, and it log, says something like R200Setup X Version mismatch. I have 7.1.0.0 version and something ask for 7.0.-1.0

Does anyone had this problem? on the forum i can't get any answer for it.

Thanks a lot.

---

### Post by mmk on 2006-06-24
I read that aiglx works with DRI drivers. Try with those, instead of the proprietary drivers ... 
Other than that ... ](*,)

---

### Post by mmk on 2006-06-25
UPDATE

New packages in the repository.... and now things get worse :(
No more direct rendering.... :(

---

### Post by H.E. Pennypacker on 2006-06-25
[QUOTE=Balachmar]mmm, I am unable to execute this command:
sudo /sbin/ldm-manager

I don't have ldm-manager. Which package do I need to get this?

Also:
sudo apt-get install linux-dri-modules-common linux-dri-modules-`uname -r`

Doesn't work on my computer.
I wanted to try these things to see wether or not I could fix the log-out problem.[/QUOTE]

I am having the EXACT same problem.

When I get to this line:

sudo apt-get install linux-dri-modules-common linux-dri-modules-`uname -r`

I get:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-dri-modules-common

Wen I try to do:

sudo /sbin/ldm-manager

I get:

pablo@Pablo:~$ sudo /sbin/ldm-manager
sudo: /sbin/ldm-manager: command not found

I went on Synaptic too look for something called LDM-Manager, but only found something called "ldm," and the description name is LTSP Display Manager.  Close enough, I thought, but it didn't solve this problem.

I am really hoping someone has a solution for these two issues, because I could probably not skip these two steps.

---

### Post by mettallicat on 2006-06-25
To me is everyting working ... but if i try to use Xchat this aplication will be so SLOW .. i need to wait til something apears.

Anyone having this kind of weirdo stuff ?

---

### Post by Donshyoku on 2006-06-26
With 51 pages, I didn't dig all through this thread, but...

When using Compiz, my windows do not have a border!  I can't drag them or move them nor close/minimize them.  They are basically stuck in the position they are in when they open.

Using the tray icon, switching to Metacity brings the borders back and all is well.  

Any thoughts?

EDIT:  By the way, I am using compiz-vanilla...

EDIT #2:  compiz-quinn fixed all of my problems!  Thanks!

---

### Post by damagedspline on 2006-06-26
[QUOTE=mmk]New packages in the repository.... and now things get worse :(
No more direct rendering.... :([/QUOTE]
yep, i've also noticed that too, but i've also noticed that only Xorg-air is running, as opposed to Xorg-air+Xorg

---

### Post by mmk on 2006-06-26
Haven't notice that before it was running Xorg + Xair :)
Anyhow, now if you just use Xorg, direct rendering is gone too :)

So I guess it's in the libMesa's ...

---

### Post by thomasbilgram on 2006-06-26
**Sethiano:** My graphic card is an Intel GM 855.

---

### Post by myha on 2006-06-26
[QUOTE=mmk]Haven't notice that before it was running Xorg + Xair :)
Anyhow, now if you just use Xorg, direct rendering is gone too :)[/QUOTE]
Same here..

---

### Post by n0yd on 2006-06-26
I have that direct rendering problem also.  Also I'm not sure what this line is supposed to look like for totem-xine, video.drivershm or video.driver:shm, I can't tell for sure because of the smiley face that got put in, but either one just makes totem open and then instantly close.  Video playback seems to work fine, but I've always had this problem where the videos appear to bright in certain parts where there is heavy lighting things appear white.  Any ideas/suggestions/fixes would be great, this happens in totem-xine, and mplayer.   
I have tried .wmv and .mpg and the same thing happens.  

This is on my i810 with 32mb shared laptop.

EDIT: Ok I fixed the video playback.  Still no fixes as of yet for direct rendering?  Also is there a way to get video to play properly while using the cube?  

Thanks, any help would be appreciated.

---

### Post by Donshyoku on 2006-06-26
Really dumb question... how do I rotate the cube? ](*,)

---

### Post by Hender on 2006-06-26
I've been trying to get AIGLX working with my Intel 82852/855GM Integrated Graphics card. I've used the walkthrough, and I've gone over it several times. I cannot fathom that I have done something wrong. And yet I don't understand how to fix it using the instructions earlier in the thread.

After using XLIB_SKIP_ARGB_VISUALS=1 gnome-window-decorator &
, I don't get an error when starting the window decorator anymore, but the I don't get a window decoration either. As far as I can tell, I've got AIGLX up and running, so starting Compiz really shouldn't be a problem. However, all I get are windows without borders, and without any window-managing functions available.

If someone knows how to fix this, please help. I don't really know what errors or messages to look up and paste here, but if you need more information before helping out, I'll be glad to provide it.

I'm running Dapper.

BTW, n0yd - nice avatar. ;)

Donshyoku - you press Ctrl + Shift and Drag with your left mouse button. Alternatively press Ctrl + Shift and a mouse button. At least I think so. It's been a while since I last tried Compiz.

---

### Post by Donshyoku on 2006-06-26
[QUOTE=Hender]
Donshyoku - you press Ctrl + Shift and Drag with your left mouse button. Alternatively press Ctrl + Shift and a mouse button. At least I think so. It's been a while since I last tried Compiz.[/QUOTE]

That is what I thought it was, but it is not working for me... :confused:

---

### Post by Hender on 2006-06-26
[QUOTE=Donshyoku]That is what I thought it was, but it is not working for me... :confused:[/QUOTE]
I meant "Alternatively press Ctrl + Shift and an arrow button".

:-#

Does that work? If it doesn't, you could always check out Gset-compiz ... I must admit, though, I'm way out of my league on this.

---

### Post by n0yd on 2006-06-26
[QUOTE=Hender]


BTW, n0yd - nice avatar. ;)

[/QUOTE]

Doh :p (Looks around for a new avatar :cool: )

Hender, It works fine here as the compiz-start script is now put right into the package so when I start gnome it just starts.  I didnt have to add it my sessions or anything like that.  Just change the gdm.conf to use Aiglx for the Xserver and off I went...:mrgreen:

---

### Post by fiddler59 on 2006-06-26
How do I configure Xorg ?? I am trying to do step 2 on the first (instalation) page ??? I am a total noob but computer savy. I got all the way to step 2 but at am a loss and know nothing about Xorg.
TIA
David

---

### Post by n0yd on 2006-06-26
[QUOTE=fiddler59]How do I configure Xorg ?? I am trying to do step 2 on the first (instalation) page ??? I am a total noob but computer savy. I got all the way to step 2 but at am a loss and know nothing about Xorg.
TIA
David[/QUOTE]

What exactly are you getting stuck on?  You need to edit your xorg.conf file according to the guide.  The file is in /etc/X11/xorg.conf

---

### Post by fiddler59 on 2006-06-27
Thnx,
 I got it working. Awesome !!!!
David B

---

### Post by Hender on 2006-06-27
Could someone post their xorg.conf, gdm.conf and gdm.conf-custom?

I have messed about with these before in failed attempts to install Xgl, and I fear this may be my problem.

---

### Post by Gibb on 2006-06-27
It's working, except for video on totem-gstreamer or VLC.
I have to switch back to mesa for watching video's.

Here's my xorg.conf and gdm.conf-custom.

---

### Post by Patrick-Ruff on 2006-06-28
I keep getting the infamous no window boarders/title bars etc. 


I'm on an ATI X300 mobility card.  I don't get errors anymore, just no title bars... no possibility of moving the windows in any way...

---

### Post by mmk on 2006-06-28
That means that compiz is not working ...
Have you put in your xorg the COMPOSITION stuff ?
Or have you enabled the **decoration** plugin ?
Do you have the little red box in your systray when booting? If yes, enable all pllugins (especially decoration) and try a reboot if the problem is not fixed right away...
Also, you might try in the borderless console:

gnome-window-decorator &
compiz --replace gconf decoration ...

Also, does ALT + mouse works to move the windows ? (**move** plugin)

---

### Post by Patrick-Ruff on 2006-06-28
ok I finally made compiz work, however its kinda weird... like for instance, if I open up a terminal, it shows like a black screen or something like it didn't render correctly, but when I resize the window it shows what it should look like, but it doesn't render what I type in untill I resize it again


quick fix?

---

### Post by Patrick-Ruff on 2006-06-28
also, it seems to apply to pretty much any window I open up. top menu's go fine, also I can move windows and all that and the animation is VERY VERY VERY smooth, switching between desktops in 3d mode is also smooth.

---

### Post by mmk on 2006-06-28
I had this error in AIGLX (black terminat) when I was not using the XAANoOffscreenPixmaps in my devide configuration in xorg.conf

are you sure you have it ? (in xgl worked fine without it ...)

```

        Option          "XAANoOffscreenPixmaps"
        Driver          "i810"

```

---

### Post by Patrick-Ruff on 2006-06-28
yes I have that on.

---

### Post by Patrick-Ruff on 2006-06-28
wtf, Xorg.conf seems to have a really ****** up consistancy with resetting alot of shit... excuse the language but this is VERY annoying..

---

### Post by Patrick-Ruff on 2006-06-28
ok, that fixed that particular problem, the selection rectangle for my desktop seems to be a little sluggish, any fix? (I'm not setting my colors down, looks way too crappy)

---

### Post by mmk on 2006-06-28
do yo use the DRI driver or the ATI proprietary driver ?
Cause it might be a bug of the DRI driver ....
And if you have X300, why don;t you use fglrx and XGL ?
I only use AIGLX cause it has better support for my radeon 7500 laptop/i810 desktop.
But on your card, XGL works better.
Just "apt-get remove xserver-xorg-airo" and install "xserver-xgl" ....
(also remove some options from xorg.conf, like composition stuff and XAA ...)

---

### Post by Patrick-Ruff on 2006-06-28
well, XGL never really worked for me, it was sad.... I got like a messed up welcome screen with a constant loading pointer, I WOULD REALLY Love to get XGL working, like SERIOUSLY, but I got an error and it also gave me the 'No Screens Found" crap. 


I would really appriciate it if you helped me.

---

### Post by mmk on 2006-06-28
Well ... if everything seems to work, except for the sluggish-iness .... wait for better drivers :)

It also works slow on my radeon 7500 (slower than on i810), and i find XGL quite working faster than AIGLX, except that glxgears show me 600-700 on AIGLX and 90 on XGL :) and also I **had** direct rendering with AIGLX (last version of the mesa libs) ... so AIGLX looks more promising than XGL for my hardware.

But I am still waiting for better support. For now, I am using AIGLX on my i810 and Xorg + metacity on my radeon :( When new drivers come out, I try AIGLX again ... maybe the speed is better. For now I keep it on my radeon just for "show off" :)
I hope there will be a time when it will be completely functional (and i still have my laptop - cause I plan a upgrade)....

So .... wait for upgrades :)

EDIT: meantime, you might give XGL another try ... with different drivers... what do the other X300 users say? I know i got it working really nice on Radeon 9700 ...

---

### Post by Patrick-Ruff on 2006-06-28
well, I've learned quite a bit more about the entire system just from my recent tweaking, perhaps I'll be able to troubleshoot XGL better now.

---

### Post by jonny on 2006-06-28
Works perfectly on intel 810 graphics on a 512MB 1.6GHz mobile Celeron.  All effects seem to work perfectly and performance is very acceptable.

---

### Post by americanLoki on 2006-06-28
I just got a new Inspiron B130 and this works better on this machine than my nVidia 6800+XGL machine. This is really cool, thanks gandalfn for the guide =D>

---

### Post by fiddler59 on 2006-06-28
I've got compiz-Quinn up and running using aiglx. When I go into gset-compiz and click on the plugin mngr dock and miniwin are are shown but not highlited (for lack of a better term). How do I enable these plugins so I can try them out ??
TIA,
David B.
HP Pavilion 4275
Intel 915GM Pent.M
2gigs Ram

---

### Post by Corvillus on 2006-06-28
New mesa just hit the repos, DRI is back. :D (using an i855gm)

---

### Post by Milamber_Cubed on 2006-06-28
All working well with the current packages with one exception - The SVG on the top/bottom of the cube is garbled. At some point, one of the package updates has changed this.. the only problem is that I can't figure out when, or how to fix it.

I will attach a screenshot of what things look like and the SVG file itself for people to try out.

Anyone else have these problems?

---

### Post by mmk on 2006-06-28
Right, DRI back. 865 here. I'll try tonite on radeon 7500.

---

### Post by myha on 2006-06-29
[QUOTE=mmk]Right, DRI back.[/QUOTE]
Yes, works now also with my i915! :)

br

---

### Post by mmk on 2006-06-29
Ok, on radeon 7500 ... works again, but still too slow to use :(
I don't get it how intel 865 is faster than radeon 7500 .... :(

How are other 7500 ?

---

### Post by damagedspline on 2006-06-29
[QUOTE=mmk]How are other 7500 ?[/QUOTE]

My radeon IGP340M (~7200 equiv) works fine, incl direct rendering, with new mesa patches, but only @16bpp. 24 bit is just too much i guess...

---

### Post by H.E. Pennypacker on 2006-06-29
How did you guys get past the errors described in this post:

[http://ubuntuforums.org/showpost.php?p=1180481&postcount=967](http://ubuntuforums.org/showpost.php?p=1180481&postcount=967)

I have no idea how to get past those two.

---

### Post by Cruzer on 2006-06-29
Hi People, 
I'm a newbie and was trying to get this thing working, however I don't know how to do the second step in the first post!

> 
". Configure Xorg

Good news you can rework in 24 depth mode
Edit your Screen section and modify your DefaultDepth
Quote:
DefaultDepth 24

Warning this options are necessary !

first activate dri,dbe, glx and all necessary modules like this..

How can I activate dri, dbe, glx and all those things?:-? 

Thanks

---

### Post by H.E. Pennypacker on 2006-06-29
[QUOTE=Cruzer]Hi People, 
I'm a newbie and was trying to get this thing working, however I don't know how to do the second step in the first post!



How can I activate dri, dbe, glx and all those things?:-? 

Thanks[/QUOTE]

I was wondering the same thing about DRI.  It probably involves messing with Xorg.

---

### Post by Corvillus on 2006-06-29
Those modules usually are enabled just by having their Load lines listed (for me they were there by default) and uncommented in the modules section of xorg.conf. As for DRI, that may or may not actually enable depennding on whether your driver supports it.

On another note, does anyone else have issues with Cream having horribly slow text render speed under Compiz (the vanilla gVim works fine though)?

---

### Post by damagedspline on 2006-06-29
[QUOTE=H.E. Pennypacker]How did you guys get past the errors described in this post:

[http://ubuntuforums.org/showpost.php?p=1180481&postcount=967](http://ubuntuforums.org/showpost.php?p=1180481&postcount=967)

I have no idea how to get past those two.[/QUOTE]

add to your /etc/sources.list instead of xgl.compiz.info:
```
deb http://www.beerorkid.com/compiz dapper main aiglx
```

then run from console:
```
wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
```
and then:
```
sudo apt-get update
```
and only then:
```
sudo apt-get install linux-dri-modules-common linux-dri-modules-`uname -r`
```
the thing with ldm-manager is for a different kind of problems...

---

### Post by myha on 2006-06-30
Hi,

I have one little problem.... I am connecting to some server through XDCMP. I start session from console, but when it tries to connect it completely freezes my system because I think it tries to load AIGLX...

So how could I start new session without xgl support? The same goes for my X server... Is it enough if I just start it with diffrent xorg.conf that doesn't have glx, composite, etc support?

regards,
Miha

---

### Post by mbeierl on 2006-06-30
Does anyone know if this will work with dual monitor support (ie: xinerama) on the i915?

---

### Post by t3rror on 2006-06-30
I am not really sure what happened, but I have had my laptop off for a couple of weeks, and recently installed some updates and everything went to shit.  I had been running this setup flawlessly for a couple of months.  I am on a Dell D600 laptop.  I have tried both vanilla and quinn packages.  The wierd thing is, I have a quinn package installed on a desktop that is version 13, and the one that is installing on the laptop is 11.  This makes me wonder if my sources.list is jacked.  When I do a apt-get update, I noticed that the aiglx repos are IGN.  This must be my problem.  If anyone can help, I would appreciate it.

****EDIT****
I have been able to get my desktop back, but there is no aiglx.  I am not really sure what the heck happened, but I am guessing it was something with the latest round of updates.  I still don't understand why I am getting IGN reports from the aiglx repos.  Maybe someone could shed a little light.

---

### Post by soulglo83 on 2006-07-02
[QUOTE=Eversmann]Hi!

I've followed the first post, and tried with quinn and vanilla packages. It's a clean install and fglrx works ok (direct rendering, everything).

But if i make the changes on gdm.conf-custom and xorg.conf.

If i do, i can't get xserver to run, and it log, says something like R200Setup X Version mismatch. I have 7.1.0.0 version and something ask for 7.0.-1.0

Does anyone had this problem? on the forum i can't get any answer for it.

Thanks a lot.[/QUOTE]

I too have this problem, apparently its just us two :(

i have the latest mesa and ati and the error i get is identical, even the R200Setup part!  i have an ati x1600 pci-e running on an athlon 64 w/ 1gig ram.  like you mentioned, i get this error when aiglx or air or whatever it is in the gdm.conf-custom, is loaded.  without my gdm.conf-custom my computer boots like normal and dri works!  obviously without the lines in gdm.conf-custom, no aiglx, means no compiz :(

the lines in my Xorg.0.log file show the error as follows:
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.99.8, module version = 8.25.18
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
[R200Setup] X version mismatch - detected X.org 7.1.0.0, required X.org 7.0.-1.8
(II) UnloadModule: "fglrx"
(II) Unloading /usr/lib/xorg-air/modules/drivers/fglrx_drv.so
(EE) Failed to load module "fglrx" (module requirement mismatch, 0)

---

### Post by steven83m on 2006-07-03
Hi. First thanks for the great tutorial.
With this i get the airxgl working on my ati7500mobile.
but i think there are some bugs that i cant fix without the help of the community.
if the airxgl runs with compiz some windows and menus are not drawed. for example i open the kde menu and i can only see the white background or the bordershadow. plz take a look to the pciture attachment.

the next problem since last update is that the cube ist only 1024x1024 but my resolution is 1024x1280. 

here are some environmentfacts:

- Dapper Drake
- AIR-XGL 7.1
- KDE 3.5
- compiz_0.0.13-0quinn7_i386
- 2.6.15-25-686
- xorg works with radeon driver (same problems with ati)
- default-depth is 16bit

it would be realy nice if someone can help me. 

thank you

---

### Post by naked on 2006-07-03
If I suspend with compiz-vanilla, when I attempt to resume I get a black screen.  I can move my mouse, but I can't access anything else.  My keyboard seems to be locked out.  I have to power off with the power button, any help for this issue?

I'm on a dell 700m w/ i810.

L

---

### Post by Corvillus on 2006-07-03
Compiz does not work at all with Suspend or Hibernate. It never resumes properly. What I usually do is just right click on the tray icon for Compiz and click "switch to metacity" before suspending. That usually works. Then when I resume I right click the icon and "restart compiz" to get compiz back. Alternatively, if you don't have that icon, just do ```
metacity --replace
``` to get Metacity before suspending, and ```
compiz --replace gconf
``` to go back to Compiz after resuming. If you dig around earlier in this thread there was some guide on how to script this to automatically happen on suspend/resume, but I haven't tried that yet.

---

### Post by MarkSheely on 2006-07-03
Awesome how-to, thanks very much!

I'm amazed that my cheap dell laptop (Dell B130) can do this!

--Mark

---

### Post by JeremyHarrison on 2006-07-04
Ok, I'm still fairly new to Linux. I've also run into problems with suspending and I love the idea of just switching to metacity first. Can someone help point me to the script that allows you to switch between the two?

EDIT: I found it. In case anyone else is having this problem here is a link to the thread that describes the script:

[http://ubuntuforums.org/showthread.php?t=150463&highlight=script+switch+metacity+compiz](http://ubuntuforums.org/showthread.php?t=150463&highlight=script+switch+metacity+compiz)

However, be warned, some users are saying that they have problems with it from time to time. I think that hitting Alt-F2 and than switching by typing "metacity --replace" before you sleep is probably the safest method.

---

### Post by llamakc on 2006-07-04
[quote=soulglo83]I too have this problem, apparently its just us two :(

i have the latest mesa and ati and the error i get is identical, even the R200Setup part!  i have an ati x1600 pci-e running on an athlon 64 w/ 1gig ram.  like you mentioned, i get this error when aiglx or air or whatever it is in the gdm.conf-custom, is loaded.  without my gdm.conf-custom my computer boots like normal and dri works!  obviously without the lines in gdm.conf-custom, no aiglx, means no compiz :(

the lines in my Xorg.0.log file show the error as follows:
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
    compiled for 6.8.99.8, module version = 8.25.18
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 0.7
[R200Setup] X version mismatch - detected X.org 7.1.0.0, required X.org 7.0.-1.8
(II) UnloadModule: "fglrx"
(II) Unloading /usr/lib/xorg-air/modules/drivers/fglrx_drv.so
(EE) Failed to load module "fglrx" (module requirement mismatch, 0)[/quote]

Same problem here.,
ATI X300 PCIE card,
AMD 64 3000+
a gig of RAM.

When I switch to the ati/radeon driver my resolution goes to 640x480 (but aiglx and compiz work). I did try running in 16-bit mode too.

---

### Post by Eversmann on 2006-07-04
Our problem is, i think, fglrx doesn't support xorg 7.1 yet, and aiglx uses it, more or less.

I switched to XGL and working great, except for the hardlocks after the login (when i use fglrx) :-(

---

### Post by Ubuntuud on 2006-07-05
Uhm, I'm having some trouble... I ran compiz fine for some months now, but today the cube gave up. The windows still move smoothly, but the cube is very slow and shocky. It might be because of the gcompizthemer update, I don't know? Any hints? Thanks in advance!

---

### Post by Ubuntuud on 2006-07-05
Hmm... I changed from Quinn to Vanilla, that solved the cube problem, bur Vanilla isn't themeable by gcompizthemer... Why?

---

### Post by OPTiCO on 2006-07-05
[QUOTE=Ubuntuud]Uhm, I'm having some trouble... I ran compiz fine for some months now, but today the cube gave up. The windows still move smoothly, but the cube is very slow and shocky. It might be because of the gcompizthemer update, I don't know? Any hints? Thanks in advance![/QUOTE]
Nearly the same thing has happened here. The cube is extremely choppy, and my windows aren't moving as smoothly as they used to do before the last few quinn-packages.

---

### Post by crazy___cow on 2006-07-05
Same problem after upgrade....

---

### Post by andreag on 2006-07-05
I have a different problem after the upgrade: suspend/hybernate worked perfectly for me on a Toshiba laptop with Intel card, aiglx, compiz (!!!) now it gives a blank screen when waking up. Everything works again if I switch to metacity, but yesterday it worked perfectly with compiz! How can I downgrade to previous versions of compiz etc?

---

### Post by andreag on 2006-07-05
[QUOTE=Corvillus]Compiz does not work at all with Suspend or Hibernate. It never resumes properly. What I usually do is just right click on the tray icon for Compiz and click "switch to metacity" before suspending. That usually works. Then when I resume I right click the icon and "restart compiz" to get compiz back. Alternatively, if you don't have that icon, just do ```
metacity --replace
``` to get Metacity before suspending, and ```
compiz --replace gconf
``` to go back to Compiz after resuming. If you dig around earlier in this thread there was some guide on how to script this to automatically happen on suspend/resume, but I haven't tried that yet.[/QUOTE]

It is not true! it worked perfectly for me on a Toshiba laptop with Intel card until this morning, when I did an upgrade and now I am compelled to switch to metacity... so things actually went worse, it was working until yesterday, how can I downgrade?

---

### Post by andreag on 2006-07-05
[QUOTE=Balachmar]No this is the infamous log-out bug. Which has been re-introduced with the latest updates. Just have to wait for a fix I guess...
It is also the only problem I am experiencing by the way.[/QUOTE]

I fixed that using the gTweakUI-Session GUI, and selecting "Show logout menu". Then everything was right.

---

### Post by andreag on 2006-07-05
[QUOTE=Corvillus]Compiz does not work at all with Suspend or Hibernate. It never resumes properly. What I usually do is just right click on the tray icon for Compiz and click "switch to metacity" before suspending. That usually works. Then when I resume I right click the icon and "restart compiz" to get compiz back. Alternatively, if you don't have that icon, just do ```
metacity --replace
``` to get Metacity before suspending, and ```
compiz --replace gconf
``` to go back to Compiz after resuming. If you dig around earlier in this thread there was some guide on how to script this to automatically happen on suspend/resume, but I haven't tried that yet.[/QUOTE]

When I switch from compiz to metacity all the windows from all the virtual desktops get messed up in the first virtual desktop! some hint?

---

### Post by andreag on 2006-07-05
[QUOTE=Corvillus]Compiz does not work at all with Suspend or Hibernate. It never resumes properly. What I usually do is just right click on the tray icon for Compiz and click "switch to metacity" before suspending. That usually works. Then when I resume I right click the icon and "restart compiz" to get compiz back. Alternatively, if you don't have that icon, just do ```
metacity --replace
``` to get Metacity before suspending, and ```
compiz --replace gconf
``` to go back to Compiz after resuming. If you dig around earlier in this thread there was some guide on how to script this to automatically happen on suspend/resume, but I haven't tried that yet.[/QUOTE]

When going instead from metacity to compiz windows are incorrectly positioned under the panel...

---

### Post by Corvillus on 2006-07-05
Yes, they are, but until the suspend issue gets fixed I'd rather have to move a couple windows than have to reboot the computer because compiz froze it on resume.

---

### Post by tonyo46 on 2006-07-06
> 
Nearly the same thing has happened here. The cube is extremely choppy, and my windows aren't moving as smoothly as they used to do before the last few quinn-packages.
same problem after upgrade :(

---

### Post by iphands on 2006-07-06
Hey guys and gals. I have been using the quinn packages for quite some time now. I have been hesitant to upgrade, but my right click window options were gone. So I uncommented the repos and upgraded to the latest quinn package (tried vanilla also) well either way aiglx is now goofed (see the attached pics). I was wondering if there is anything I can do.... My guess is that I'll be fine just waiting for the latest updates; either way it helps to show what bugs users have right?

I am running: xorg 7.0, quinn packages, ATI driver for a radeon 7500 mobility

And once again the setup was working perfectly (I had xorg7) all I updated were the compiz packages (compiz compiz-gnome and quinn-compiz-aiglx).

edit: the pic on the right (#2) is what the desktop looks like without aiglx (that may have been confusing).

Happy ubuntuing. -Ian

p.s. I cant seem to force version to the last set of quinn packages... anyone have backup files somewhere??

---

### Post by steven83m on 2006-07-06
hi iphands. i have the same problem and no solution :( .. hope someone can help.

---

### Post by Corvillus on 2006-07-06
Yeah, the quinn9 packages seem to be broken, I just reinstalled the quinn8 .debs from the apt-cache.
```
sudo dpkg -i /var/cache/apt/archives/compiz_0.0.13-0quinn8_i386.deb
sudo dpkg -i /var/cache/apt/archives/compiz-gnome_0.0.13-0quinn8_i386.deb

```
should bring you back to a working version.

---

### Post by iphands on 2006-07-06
Hey Corvillus i've tried reverting with the method you've described; however, I don't have those packages, so I grabbed them manually from the repository. But I still can't get aiglx working agian.

Ive reverted to:
compiz_0.0.13-0quinn8_i386.deb
compiz-gnome_0.0.13-0quinn8_i386.deb

Then I thought it may be my compiz-quinn-aiglx so I tried:
compiz-quinn-aiglx_0.0.13-0ubuntu1_i386.deb
compiz-quinn-aiglx_0.0.11-0ubuntu2_i386.deb
compiz-quinn-aiglx_0.0.11-0ubuntu1_i386.deb

All with no luck.... I think the error is between the chair and the keyboard but I just can't seem to figure it out.

I would like to have it fixed so I can convert a relative that may be coming visit soon so any help would be aprriciated...

Thanks agian. -Ian

---

### Post by H.E. Pennypacker on 2006-07-07
I have this weird problem with AIGLX/Compiz that results in not seeing anything after coming back from suspension.  After I return from suspended mode, the only thing I see on my screen is the mouse.  When I move the mouse around, I notice there's clearly a textbox in the middle of the window, eventhough I can't see it (the mouse changes when its on top of a textbox).  That's how I knew the password dialog was there, and I typed in my password.  It logged me in as it was supposed to have done, but I can't see anything except white.  So, it's black before logging in, but white after logging in.  The shadow traces of windows are clearly visible, although the windows are not visible themselves.

Anyone know what's going on here?

> **damagedspline said:**
> add to your /etc/sources.list instead of xgl.compiz.info:
```
deb http://www.beerorkid.com/compiz dapper main aiglx
```

then run from console:
```
wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
```
and then:
```
sudo apt-get update
```
and only then:
```
sudo apt-get install linux-dri-modules-common linux-dri-modules-`uname -r`
```
the thing with ldm-manager is for a different kind of problems...

damagedspline, I don't know how you knew the solution, but it worked!  Thank you so very much.

---

### Post by andreag on 2006-07-07
> **H.E. Pennypacker said:**
> I have this weird problem with AIGLX/Compiz that results in not seeing anything after coming back from suspension.  After I return from suspended mode, the only thing I see on my screen is the mouse.  When I move the mouse around, I notice there's clearly a textbox in the middle of the window, eventhough I can't see it (the mouse changes when its on top of a textbox).  That's how I knew the password dialog was there, and I typed in my password.  It logged me in as it was supposed to have done, but I can't see anything except white.  So, it's black before logging in, but white after logging in.  The shadow traces of windows are clearly visible, although the windows are not visible themselves.

Anyone know what's going on here?

damagedspline, I don't know how you knew the solution, but it worked!  Thank you so very much.


Helas it didn't work for me... by the way, I had the mouse on the black screen for a short time, now I have only the black screen and I can't even guess where the login window is, although I suspect it is there. 

Also the latest upgrade of compiz-vanilla didn't fix things.

The really weird thing is that there is no way to get out of the black screen: Ctrl-Alt-F1 does not work, and
neither /etc/init.d/gdm restart (you must get in from the network for that). You just have to reboot. But top shows that xorg-air is alive behind the black screen.

---

### Post by techrosis on 2006-07-07
man oh man....i finally found someone with the same problem i'm having!!! Iphands...that screenie of the right side of the screen boogered up and wallpaper shot etc.etc. is all i've managed to get AT ALL...of course i just started trying to get aiglx/compiz to work 2 days ago...i would love if someone had a quickie answer to this problem...i'm running an ATI Radeon Mobilty 32MB...any suggestions to make this bad boy work???

---

### Post by iphands on 2006-07-07
Hey techrosis, hold in there I had this setup working for a long while now and it only broke with the latest updates. Hopefully someone will come along who has a solution... I have tried a number of old versions and none seem to give me the aiglx support I had before... Is there any log that can show me what versions of packages I was running before the update?? and would the log be gone if i've since installed like 10 different versions?

---

### Post by t3rror on 2006-07-07
> **iphands said:**
> Hey techrosis, hold in there I had this setup working for a long while now and it only broke with the latest updates. Hopefully someone will come along who has a solution... I have tried a number of old versions and none seem to give me the aiglx support I had before... Is there any log that can show me what versions of packages I was running before the update?? and would the log be gone if i've since installed like 10 different versions?

I am in the same boat iphands.  Have had this setup working for quite some time and then it all broke about the same time as yours i believe.  The screenshots are dead on.  BTW nice desktop.  Currently, I have purged all compiz + aiglx packages from my system and am just trying every other day or so to install whats new.  I have a desktop setup that is still working with aiglx, but I can report the same cube slow-down that others have stated with the most recent quinn packages.

---

### Post by CarpmanVPTR on 2006-07-07
There are quinn10 packages on the repository this morning, but they don't seem to have an effect on the suspend/resume problem.

---

### Post by techrosis on 2006-07-07
okay...so...if i'm understanding correctly...it was just my bad timing and i decided to give it a try with (apparently) broken packages??? hehehe just my luck....i'm not giving up though...i think it's simply amazing what AIGLX is capable of on lowend graphic chips with open source drivers.....

---

### Post by CarpmanVPTR on 2006-07-07
> **CarpmanVPTR said:**
> There are quinn10 packages on the repository this morning, but they don't seem to have an effect on the suspend/resume problem.
quinn8 dosn't seem to fix the problem either. Weird. Although cube-spinning is smooth in 8 and 10.

---

### Post by fugit10 on 2006-07-07
Hi,
Just got ubuntu dapper and trying it out for the first time. I was going through the whole ubuntuguide and got eventually stuck on this one. What happens is that the window boarders/title bars get stuck on my screen and can't be adjusted (not even with alt) I'll post my xorg.conf file since i'm guessing its a compiz problem. If someone can please tell me what I did wrong it would help a lot. Thanks

I have only put up the changes

Section "Module"

	# Load "GLcore"
	Load "i2c"

	Load "bitmap"

	Load "ddc"

	Load "dbe"

	Load "dri"

	Load "extmod"

	Load "freetype"

	Load "glx"

	Load "int10"

	Load "type1"

	Load "vbe"

EndSection


Section "Device"

	Identifier "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"

	Driver "i810"

	Option "XAANoOffscreenPixmaps"

	BusID "PCI:0:2:0"

EndSection

Section "ServerLayout"

	Option "AIGLX" "true"

	Identifier "Default Layout"

	Screen "Default Screen"

	InputDevice "Generic Keyboard"

	InputDevice "Configured Mouse"

	InputDevice     "stylus" "SendCoreEvents"

	InputDevice     "cursor" "SendCoreEvents"

	InputDevice     "eraser" "SendCoreEvents"

	InputDevice "Synaptics Touchpad"

EndSection



Section "DRI"

	Mode 0666

EndSection



Section "Extensions"

	Option "Composite" "Enable"

EndSection

---

### Post by CarpmanVPTR on 2006-07-07
> **fugit10 said:**
> Hi,
Just got ubuntu dapper and trying it out for the first time. I was going through the whole ubuntuguide and got eventually stuck on this one. What happens is that the window boarders/title bars get stuck on my screen and can't be adjusted (not even with alt) I'll post my xorg.conf file since i'm guessing its a compiz problem. If someone can please tell me what I did wrong it would help a lot. Thanks

I have only put up the changes

Section "Module"

	# Load "GLcore"
	Load "i2c"

	Load "bitmap"

	Load "ddc"

	Load "dbe"

	Load "dri"

	Load "extmod"

	Load "freetype"

	Load "glx"

	Load "int10"

	Load "type1"

	Load "vbe"

EndSection


Section "Device"

	Identifier "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"

	Driver "i810"

	Option "XAANoOffscreenPixmaps"

	BusID "PCI:0:2:0"

EndSection

Section "ServerLayout"

	Option "AIGLX" "true"

	Identifier "Default Layout"

	Screen "Default Screen"

	InputDevice "Generic Keyboard"

	InputDevice "Configured Mouse"

	InputDevice     "stylus" "SendCoreEvents"

	InputDevice     "cursor" "SendCoreEvents"

	InputDevice     "eraser" "SendCoreEvents"

	InputDevice "Synaptics Touchpad"

EndSection



Section "DRI"

	Mode 0666

EndSection



Section "Extensions"

	Option "Composite" "Enable"

EndSection
Switch to another virtual terminal while X is running, run this...

```

export DISPLAY=:0.0
gset-compiz

```

switch back to X and in the list of modules, make sure that the move module has a check mark next to it.

---

### Post by fugit10 on 2006-07-07
Hi, thanks for the reply
When you say when X is running do you mean compiz? Sorry new to linux and don't know any of the lingo. 
Also I'm not sure what a virtual terminal is but I also noticed that when I load compiz my borders go away but also my ability to open any new programs including the terminal. I have to actually switch to metacity to make it work. I also tried your method by typing it into the terminal but I saw no difference and the move box was already checked.


Compiz seemed to autoload when I login and I tried starting it instead through the terminal. I noticed that there were a couple of errors but I have no idea how to decipher it. Could someone tell me what the errors mean?
Thanks


seung@seung-laptop:~$ compiz-start
gnome-window-decorator: no process killed
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
The program 'gnome-window-decorator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 652 error_code 8 request_code 153 minor_code 8)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
gnome-window-decorator: no process killed

---

### Post by CarpmanVPTR on 2006-07-07
> **fugit10 said:**
> Hi, thanks for the reply
When you say when X is running do you mean compiz? Sorry new to linux and don't know any of the lingo. 
Also I'm not sure what a virtual terminal is but I also noticed that when I load compiz my borders go away but also my ability to open any new programs including the terminal. I have to actually switch to metacity to make it work. I also tried your method by typing it into the terminal but I saw no difference and the move box was already checked.


Compiz seemed to autoload when I login and I tried starting it instead through the terminal. I noticed that there were a couple of errors but I have no idea how to decipher it. Could someone tell me what the errors mean?
Thanks


seung@seung-laptop:~$ compiz-start
gnome-window-decorator: no process killed
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
The program 'gnome-window-decorator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 652 error_code 8 request_code 153 minor_code 8)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
gnome-window-decorator: no process killed
Hmm... can you post the output of the glxinfo command?

---

### Post by fugit10 on 2006-07-07
here's the output for glxinfo

seung@seung-laptop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control,
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control,
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGI_video_sync, GLX_SGIS_multisample,
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20050225
OpenGL version string: 1.3 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging,
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters,
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle,
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object,
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_equation_separate,
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array,
    GL_EXT_convolution, GL_EXT_copy_texture, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_histogram, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_3DFX_texture_compression_FXT1, GL_APPLE_client_storage,
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate,
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat,
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture,
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent,
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program,
    GL_NV_vertex_program1_1, GL_OES_read_format, GL_SGI_color_matrix,
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture,
    GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x4b 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

---

### Post by CarpmanVPTR on 2006-07-07
Weird. Your OpenGL/DRI seems to be set up correctly, do you have the red box icon in your taskbar? If so click it and select restart compiz.

---

### Post by llamakc on 2006-07-07
Good news for me. I used the vanilla packages and followed the howto. All working. I got the error about fglrx so I switched to "ati". Next, my lcd monitor wouldn't use the rate that was being autoset, so I had to add a Mode line under the Display.

xorg.conf snip:
```

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes   "1280x1024"
        EndSubSection
EndSection

```

I'll go back to fglrx when that problem is fixed. 

Meanwhile, this is truly a beautiful piece of work. I just flattened my cube with ctrl-alt-downarrow on accident. Sweet.

---

### Post by H.E. Pennypacker on 2006-07-08
> **andreag said:**
> Helas it didn't work for me... by the way, I had the mouse on the black screen for a short time, now I have only the black screen and I can't even guess where the login window is, although I suspect it is there. 

Also the latest upgrade of compiz-vanilla didn't fix things.

The really weird thing is that there is no way to get out of the black screen: Ctrl-Alt-F1 does not work, and
neither /etc/init.d/gdm restart (you must get in from the network for that). You just have to reboot. But top shows that xorg-air is alive behind the black screen.

Andreag, you don't have to restart.  Just do CTRL-ALT-Backspace.  That restarts Gnome.  It's a lot faster than restarting.

To not have this problem occur in the first place, disable AIGLX/Compiz before you go into suspension/hibernation, and then restart AIGLX/Compiz when you're back.  Everything should work properly if you disable AIGLX/Compiz first.  Right click the red icon, and select "Switch to Metacity."

Still, we need a solution for this.

---

### Post by techrosis on 2006-07-08
Has anyone other than me and Iphands encountered this wierdo error...sorta like cutting off the right side of the screen and killing the wallpaper...i've tried vanilla and quin packages and both yield the same results.... here is a screenie

[IMG]http://www.shererdentallab.com/screenshot.png[/IMG]

---

### Post by llamakc on 2006-07-08
Oh it was running beautifully for me and I had to go and reboot.

Sigh.

---

### Post by damagedspline on 2006-07-08
> **techrosis said:**
> Has anyone other than me and Iphands encountered this wierdo error...sorta like cutting off the right side of the screen and killing the wallpaper...i've tried vanilla and quin packages and both yield the same results.... 

OK, for all of you ppl that has this issue:
I've came across this bug way,way back on my radeon chipset - I couldn't find a solution, however I found a quick way to make the black/doublescreen issue go away by simply spinning the cube really fast in several directions until it was gone (just press something like ctrl-alt-left-up for 30 sec without releasing the keys). It's not a compiz issue - it's because of a memory leak in mesa/dri - wait for those updates (it might take a while)...

And about the hibernation/suspend black screen:
It is a known issue that X is having trouble recovering when 3d stuff were present on screen. In this forum someone posted scripts that should go in /etc/acpi/suspend.d and /etc/acpi/resume.d that should solve this issue by automating the compiz kill prior the hibernation, and restarting it on resume. I say should because it didn't worked for me (a variable seems to disapear). Other then that, just wait for better foss drivers||better mesa/dri integration.

---

### Post by andreag on 2006-07-08
> **H.E. Pennypacker said:**
> Andreag, you don't have to restart.  Just do CTRL-ALT-Backspace.  That restarts Gnome.  It's a lot faster than restarting.

To not have this problem occur in the first place, disable AIGLX/Compiz before you go into suspension/hibernation, and then restart AIGLX/Compiz when you're back.  Everything should work properly if you disable AIGLX/Compiz first.  Right click the red icon, and select "Switch to Metacity."

Still, we need a solution for this.

CTRL-ALT-Backspace doesn't work, just as CTRL-ALT-F1. 
I know I can disable compiz. 
But why suspend/hybernate was working perfectly with compiz until a few days ago? that's quite annoying.

---

### Post by andreag on 2006-07-08
> **damagedspline said:**
> 
And about the hibernation/suspend black screen:
It is a known issue that X is having trouble recovering when 3d stuff were present on screen. In this forum someone posted scripts that should go in /etc/acpi/suspend.d and /etc/acpi/resume.d that should solve this issue by automating the compiz kill prior the hibernation, and restarting it on resume. I say should because it didn't worked for me (a variable seems to disapear). Other then that, just wait for better foss drivers||better mesa/dri integration.

What is really annoying is that suspend/hybernate was working perfectly with compiz-aiglx just a few days ago... so the solution was there and has been lost.

---

### Post by techrosis on 2006-07-08
> **damagedspline said:**
> OK, for all of you ppl that has this issue:
I've came across this bug way,way back on my radeon chipset - I couldn't find a solution, however I found a quick way to make the black/doublescreen issue go away by simply spinning the cube really fast in several directions until it was gone (just press something like ctrl-alt-left-up for 30 sec without releasing the keys). It's not a compiz issue - it's because of a memory leak in mesa/dri - wait for those updates (it might take a while)...

And about the hibernation/suspend black screen:
It is a known issue that X is having trouble recovering when 3d stuff were present on screen. In this forum someone posted scripts that should go in /etc/acpi/suspend.d and /etc/acpi/resume.d that should solve this issue by automating the compiz kill prior the hibernation, and restarting it on resume. I say should because it didn't worked for me (a variable seems to disapear). Other then that, just wait for better foss drivers||better mesa/dri integration.
hmm...wierd fix but i'll try anything once ;)....i'll let you know of my findings heheh

---

### Post by fugit10 on 2006-07-08
I actually tried disabling it and restarting but theres no difference. When I enable it again all my screens lock up like it was a wallpaper. any other ideas on how to fix it? thanks

---

### Post by techrosis on 2006-07-08
i tried the spinning thing...for like a minute and a half...no dice....i also just updated to todays quinn packages....no dice...even tried the spinning thing with todays packages....still didn't fix the issue....](*,) ...this is very disheartening....

---

### Post by iphands on 2006-07-08
> **techrosis said:**
> i tried the spinning thing...for like a minute and a half...no dice....i also just updated to todays quinn packages....no dice...even tried the spinning thing with todays packages....still didn't fix the issue....](*,) ...this is very disheartening....

I can confirm that in our situation the spinning trick dosen't work... I would love to find a repositoy that has all the versions of aiglx-compiz related packages.

Also just to clarify the symptoms are still the same as my original post... even with the vanilla packages.

Hope someone can figure it out... I have someone coming visit soon and I wanna convert them (most windows users like the ohh and ahh of compiz).

---

### Post by damagedspline on 2006-07-08
iphands & techrosis, please post your device section in xorg.conf, i think i've found the "missing link"...

---

### Post by techrosis on 2006-07-08
> **damagedspline said:**
> iphands & techrosis, please post your device section in xorg.conf, i think i've found the "missing link"...


Here ya go!
```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
	Driver		"radeon"
	Option		"backingstore"	"true"
	Option		"ColorTiling"	"on"
	Option		"EnablePageFlip"	"true"
	Option		"SubPixelOrder"		"none"
	Option		"AccelMethod"		"XAA"
	Option		"RenderAccel"		"true"
	Option		"AGPMode"	"4"
	Option		"DynamicClocks"	"on"
	Option		"mtrr"	"on"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	BusID		"PCI:1:0:0"
EndSection
```

---

### Post by iphands on 2006-07-08
> **damagedspline said:**
> iphands & techrosis, please post your device section in xorg.conf, i think i've found the "missing link"...

```

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
        Driver          "ati"
        Option          "XAANoOffscreenPixmaps"
        BusID           "PCI:1:0:0"
EndSection
```

Ive also tired the radeon driver as techrosis has.... wouldn't you need ati (because radeon has no DRI)?

---

### Post by techrosis on 2006-07-08
radeon does have DRI....i haven't tried ati however :-P

---

### Post by damagedspline on 2006-07-09
> **techrosis said:**
> radeon does have DRI....i haven't tried ati however :-P

the ati driver is actually a wrapper for radeon so you're actually both using the same driver.
that's funny how you both has completly different device section... :)

well anyway, my suggestion is a combo of both device sections with some slight changes - well, until someone will successfully make a deb file out of the 6.6.1 ati radeon driver [http://lists.freedesktop.org/archives/xorg-announce/2006-June/000099.html]("http://lists.freedesktop.org/archives/xorg-announce/2006-June/000099.html")
which fixes several things... i've tried compiling it by myself but i get this weird error:
```
/usr/include/sys/types.h:62: error: conflicting types for 'xf86dev_t'
/usr/include/xorg/xf86_libc.h:87: error: previous declaration of 'xf86dev_t' was here
``` but that's off topic...
so this is the device section i'm suggesting (again it might work and it might not work):

	```
Driver		"ati"
	Option		"ColorTiling"	"off"
	Option		"SubPixelOrder"		"none"
	Option          "XAANoOffscreenPixmaps"
	BusID		"PCI:1:0:0"
```
notice that color tiling should be off. please try this setting with 16bpp first - if it's working let it be, if not try with 24bpp
my Radeon IGP340M (which is equiv. to radeon 7200) uses to following:
```
	Driver		"ati"
	Option		"AGPFastWrite" "true"
	Option		"AGPMode"	"4"
	Option		"EnablePageFlip" "true"
	Option		"RenderAccel"	"true"
	#Option 		"LVDSProbePLL" 	"true"
	#Option 		"BIOSHotkeys" 	"true"
	#Option 		"IgnoreEDID" 	"true"
	Option 		"XAANoOffscreenPixmaps"
	BusID		"PCI:1:5:0" 
```
(i think you've probably tested something similar already and it didn;t worked for you - note: dont change your BusID)

---

### Post by BeatBoxRocker on 2006-07-09
I have followed the thread but i havent found a way to use aiglx+compiz with kde. Which are the packages to make it work under Kubuntu? are the same steps to install it in gnome & kde?

Thanks in advance.

---

### Post by techrosis on 2006-07-09
> **damagedspline said:**
> the ati driver is actually a wrapper for radeon so you're actually both using the same driver.
that's funny how you both has completly different device section... :)

well anyway, my suggestion is a combo of both device sections with some slight changes - well, until someone will successfully make a deb file out of the 6.6.1 ati radeon driver [http://lists.freedesktop.org/archives/xorg-announce/2006-June/000099.html]("http://lists.freedesktop.org/archives/xorg-announce/2006-June/000099.html")
which fixes several things... i've tried compiling it by myself but i get this weird error:
```
/usr/include/sys/types.h:62: error: conflicting types for 'xf86dev_t'
/usr/include/xorg/xf86_libc.h:87: error: previous declaration of 'xf86dev_t' was here
``` but that's off topic...
so this is the device section i'm suggesting (again it might work and it might not work):

	```
Driver		"ati"
	Option		"ColorTiling"	"off"
	Option		"SubPixelOrder"		"none"
	Option          "XAANoOffscreenPixmaps"
	BusID		"PCI:1:0:0"
```
notice that color tiling should be off. please try this setting with 16bpp first - if it's working let it be, if not try with 24bpp
my Radeon IGP340M (which is equiv. to radeon 7200) uses to following:
```
	Driver		"ati"
	Option		"AGPFastWrite" "true"
	Option		"AGPMode"	"4"
	Option		"EnablePageFlip" "true"
	Option		"RenderAccel"	"true"
	#Option 		"LVDSProbePLL" 	"true"
	#Option 		"BIOSHotkeys" 	"true"
	#Option 		"IgnoreEDID" 	"true"
	Option 		"XAANoOffscreenPixmaps"
	BusID		"PCI:1:5:0" 
```
(i think you've probably tested something similar already and it didn;t worked for you - note: dont change your BusID)
that didn't work either....i'm gonna look into that new driver...maybe i can get it to compile (not likely) but what the heck hehehhe

---

### Post by techrosis on 2006-07-10
just tried todays packages....it seems to run faster...but i still have the missing wallpaper/right side of the screen missing problem....

---

### Post by samoht on 2006-07-10
Amazing!

This runs smoothly with my cheap ATI Radeon 9200SE (opensource-drivers!, 128mb, 4x AGP). The performance is much better compared to XGL...

Thanks,
Thomas (squeezing windows for hours...)

---

### Post by iphands on 2006-07-10
> **techrosis said:**
> just tried todays packages....it seems to run faster...but i still have the missing wallpaper/right side of the screen missing problem....

Same thing here.... Looks just like the [screen shots]("http://ubuntuforums.org/showpost.php?p=1221196&postcount=1033s") still. I wonder which package acctually borked it up?? (it was working for months, and seems to still work on other cards. weird.)

---

### Post by auknoi on 2006-07-12
Hi! this is my first post. I recently installed ubuntu(my first) to check it out. I am unhappy with my screen resolution so I ended up here. I did all that is required from the very first post. But when I restart gdm.. i get a gray screen with an X in the middle. Nothing seems to happen. So i restart my laptop and ubuntu loads up and asks for login... i login.. and see nice graphics for about 7 seconds then my the gray screen appears and I am brought back to the original login screen! ](*,) It just keeps repeating this. 

I have a IBM t42 laptop. 
My video card: ATI Mobility 7500

pls help

---

### Post by iphands on 2006-07-12
> **auknoi said:**
> Hi! this is my first post. I recently installed ubuntu(my first) to check it out. I am unhappy with my screen resolution so I ended up here. I did all that is required from the very first post. But when I restart gdm.. i get a gray screen with an X in the middle. Nothing seems to happen. So i restart my laptop and ubuntu loads up and asks for login... i login.. and see nice graphics for about 7 seconds then my the gray screen appears and I am brought back to the original login screen! ](*,) It just keeps repeating this. 

I have a IBM t42 laptop. 
My video card: ATI Mobility 7500

pls help

If all you were trying to do is fix the screen resolution you've goofed up royally, but when you do get the res fixed you may see some nice effects for a first time linux user. If this is the case you should google XGL and AIGLX and see what you've just installed... Then take a look at you xorg.conf.

To fix the res I would bet that you need to set the horizSycn and VertRefresh to the correct values. The correct values can be had by googleing the make and model of your monitor...

The relevant section of my make.conf looks as follows
```

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
        HorizSync       30-86
        VertRefresh     50-160

EndSection

```

you need to change the Hsync and Vrefresh to your monitors specific values... hope this helps

BTW if I misunderstood you and you were actually trying to install Aiglx, please disregard this post

Also this will not help the grey sreen with just an X problem.. what I have described just fixes the resolution.. if you need to you can uninstall the ompiz-quinn-aiglx or compiz-vanilla-aiglx which stops compiz from loading on login. This should get rid of the grey screen with x problem.... but you won't have the fancy aiglx...

---

### Post by auknoi on 2006-07-12
I'm trying to install Aiglx. If I understand right, I would have to have the correct configuration for it to run correctly. My problem is that the graphics on the screen are crappy(or less vibrant) compared to Windows. So i'm guessing it's the standard drivers that arent up to it. For example, some buttons have red dots that disappear when I put my cursor over them. I was going to put fglrx but it doesn't support my video card, which is a ati r100 chipset. So i'm left with aiglx if I can get it to work. 

I could see the good crisp icons on my desktop for 10 seconds b4 i get booted up to login.

---

### Post by iphands on 2006-07-13
> **auknoi said:**
> So i'm left with aiglx if I can get it to work.

If I am understanding correctly you are still kinda mixed up. Aiglx is not a driver for a radeon card, and it is probably not what you are looking for. It sounds like ubuntu just didnt set up X properly out of the box, and thus you will have to correct it manually... Aiglx is a whole new ballpark that you should explore after you get more familair with linux and Xorg specifically.

I think you may be confused about what AIGLX is and should maybe do some reading on it...

As far as the ati drivers go there are many here that would be glad to help, but you may want to post some screenshots and start a new thread as it would kinda be hijacking this one if non aiglx/compiz discussion was posted here.

BTW when you get your problem sorted out then, yes you sould try AIGLX. It is a great way to have extremly functional eye candy, and it changes the desktop experience. It is not neccessary though and it will most likely cause some headaches here and there until the devs work all of the kinks out.

---

### Post by Milamber_Cubed on 2006-07-13
Latest update for the quinnstorm compiz has gone back to the choppy animations that one a short while ago had caused :(

Any way to revert to the previous version?

---

### Post by samoht on 2006-07-13
Same here Milamber_Cubed :(

---

### Post by tychocity on 2006-07-13
Excelente, anda perfecto en mi thinkcentre intel810 8 megas de video.


Gracias!!

---

### Post by MarkSheely on 2006-07-13
> **samoht said:**
> Same here Milamber_Cubed :(


I'm having the same problem.  Hope a fix comes out soon.  

--Mark

---

### Post by jstueve on 2006-07-13
to revert (given that the debs aren't auto-cleaned)

```
sudo dpkg -i /var/cache/apt/archives/compiz_0.0.13-0quinn12.deb /var/cache/apt/archives/compiz-gnome_0.0.13-0quinn12.deb

```

check the directory for the correct file names...

once done, go into synaptic and lock those versions, until another version comes out.

---

### Post by skattman83 on 2006-07-13
I got aiglx and compiz installed on my laptop with i810 video, and it works great except I can't seem to get the expose function to work.  I have tried pressing both f10 and f12 and nothing happens.  I checked and all of the options are checked in the gconf(?) applet.  Any ideas how to get this one working?  It was one of the reasons I wanted to get this set up, but I can't get it working, even though the cube switch and everything else works fine.

---

### Post by mmk on 2006-07-13
Use gset-compiz to enable the plugin... maybe it's not activated...

---

### Post by samoht on 2006-07-14
Okay, this speeded up things a litte bit for my ATI Radeon 9200SE even with the latest quinn-packages:

/etc/X11/xorg.conf:
```
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "radeon"
        BusID           "PCI:1:0:0"

        Option          "XAANoOffscreenPixmaps"
        Option          "backingstore"  "true"
        Option          "ColorTiling"   "on"
        Option          "EnablePageFlip"        "true"
        Option          "SubPixelOrder"         "none"
        #Option         "AccelMethod"           "XAA"
        Option          "RenderAccel"           "true"
        Option          "AGPMode"               "4"
        Option          "DynamicClocks"         "on"
        Option          "mtrr"                  "on"
        Option          "VideoOverlay"          "on"
        Option          "OpenGLOverlay"         "off"
EndSection
```

Greets,
Thomas

---

### Post by zneastman on 2006-07-14
Let me just say that AIGLX rocks.  Hard.  I've got a Dell B130, the budgetest of the budget laptops, and it's smooth and fast as a rocket-powered bowling ball.  Here's what worked best for me:

1]  Setting the DefaultDisplay to 16 instead of 24 made everything lightning fast.  The difference is unreal.  

2]  Using the Industrial theme instead of the default Ubuntu one made things a bit faster, especially scrolling through webpages and the like.

3]  Using Gconf's graphical manager to set things like opacity when they don't work in the applet

4]  Using the scripts earlier in this thread (like page 72) to make suspend and hibernate work right.

5]  Changing Totem's video driver to "xshm" in .gnome2/totem_config (you have to uncomment the line to get it to work).  Hello translucent, wobbly video.

Compared to SLED 10, with it's broken package management and beta-quality XGL... well, there's no comparson.

---

### Post by techrosis on 2006-07-14
wah! wah! i want mine to work ](*,) ](*,) ](*,)

---

### Post by Jeff250 on 2006-07-14
Keep in mind that xshm is unaccelerated, so playing high-quality video like full-screen DVD's will be choppy.  I find it better to have smooth video that doesn't wobble than choppy video that does. :)

---

### Post by skattman83 on 2006-07-14
> **mmk said:**
> Use gset-compiz to enable the plugin... maybe it's not activated...

Thanks for the reply, but it was already activated.  I checked and the key to activate it was alt tab, but that just gave me a fancy alt tab switch.  How do I get the OSX style expose functionality?

---

### Post by Jaidee on 2006-07-15
Hello all,

I'm working to get aiglx and compiz working on a friends Sony Vaio PCG-VX71P.

I've followed this HOWTO to the letter, and installed all of quinn's packages, the DRI stuff, configured my xorg,conf and gdm.com-custom.

AiGLX is working fine, grep shows it to be running, but when I try to run the compiz-start I get dumped back to terminal, X just crashes. I've had to remove the autostart entry just so it doesn't crash everytime.

Running compiz --replace gconf causes the exact same thing to happen, so it's definetely compiz, not the script or something.

Here's my xorg.conf:

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
# Load "GLcore"
Load "bitmap"
Load "ddc"
Load "dbe"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
Identifier "Intel Corporation Intel Default Card"
Driver "i810"
Option "XAANoOffscreenPixmaps"
BusID "PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Intel Default Card"
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
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
	Option "AIGLX" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection
```

And here's my gdm.conf-custom

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
# http://www.gnome.org/projects/gdm/
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

[servers]
0=aiglx

[server-aiglx]
name=aiglx server
command=/usr/bin/Xorg-air :0
flexible=true

```

Here's an attempt at writing what the error messages say in the terminal - I don't know how to copy paste from tty1 into graphical, sorry.

```
[17179776:068000] [drm:i810_wait_ring] *ERROR* lockup
[17179779:076000] [drm:i810_wait_ring] *ERROR* space: 65512 wanted 65528
```

These lines repeat a few times with slightly different numbers. I've no idea. 

This isn't my laptop, but I think it uses an Intel 815 graphics card - my xorg.conf is pointing to i810 drivers - is this a problem?

Thanks for reading, and I hope you can help!

---

### Post by Jaidee on 2006-07-15
Forgot to include my Xorg.0.log

Here it is, and also you can see that there is a problem loading DRI. Don't know what to do to fix this.

```

(II) I810(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) I810(0): Setting dot clock to 65.0 MHz [ 0x3f 0xa 0x30 ] [ 65 12 3 ]
(II) I810(0): chose watermark 0x22214000: (tab.freq 65.0)
(II) I810(0): xf86BindGARTMemory: bind key 0 at 0x00000000 (pgoffset 0)
(WW) I810(0): xf86AllocateGARTMemory: allocation of 1024 pages failed
	(Cannot allocate memory)
(II) I810(0): No physical memory available for 4194304 bytes of DCACHE
(II) I810(0): xf86BindGARTMemory: bind key 1 at 0x00800000 (pgoffset 2048)
(II) I810(0): Allocated of 4096 bytes for HW cursor
(II) I810(0): xf86BindGARTMemory: bind key 2 at 0x00801000 (pgoffset 2049)
(II) I810(0): Allocated of 16384 bytes for ARGB HW cursor
(II) I810(0): Adding 512 scanlines for pixmap caching
(II) I810(0): Allocated Scratch Memory
(**) I810(0): Option "XaaNoOffscreenPixmaps"
(II) I810(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Setting up tile and stipple cache:
		16 128x128 slots
		4 256x256 slots
(==) I810(0): Backing store disabled
(==) I810(0): Silken mouse enabled
(**) Option "dpms"
(**) I810(0): DPMS enabled
(WW) I810(0): Direct rendering disabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg-air/modules/extensions/libGLcore.so
dlopen: /usr/lib/xorg-air/modules/extensions/libGLcore.so: undefined symbol: _mesa_BindVertexArrayAPPLE
(EE) Failed to load /usr/lib/xorg-air/modules/extensions/libGLcore.so
(II) UnloadModule: "GLcore"
error opening security policy file /usr/lib/xserver/SecurityPolicy

```

---

### Post by Jaidee on 2006-07-16
I just changed Default Depth to 16 bit, and reinstalled libgl1-mesa, and it seems to have **resolved the DRI problem**. Hooray! Now I am getting a new error message:

```
libGL warning: 3D driver claims to not support visual 0x4blibGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
```
I'll have a look around for solutions to this, new problem.

Can't wait for some Compiz action.
[b]
UPDATE:[/b] 

Ok, it looks like the libGL warning are irrelevant, so it's the same old GLX_EXT_texture from pixmap error. glxinfo shows it to be running, so i think it's my libGL.

```

simon@simon-laptop:~$ glxinfo
name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe,
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control,
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control,
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Keith Whitwell
OpenGL renderer string: Mesa DRI i815 20050821
OpenGL version string: 1.2 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture,
    GL_ARB_texture_compression, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle,
    GL_ARB_transpose_matrix, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution,
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_histogram,
    GL_EXT_packed_pixels, GL_EXT_polygon_offset, GL_EXT_rescale_normal,
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture,
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle,
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_IBM_rasterpos_clip,
    GL_IBM_texture_mirrored_repeat, GL_MESA_ycbcr_texture, GL_MESA_window_pos,
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle,
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix,
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp,
    GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x24 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x25 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x26 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x27 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x28 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x29 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x2a 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x2b 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x2c 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x2d 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x2e 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x2f 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x30 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x31 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x32 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x4b 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

When I do locate mesa, I can only find it in /usr/share/doc - I'm used to NVidia but i'm sure it should be somewhere else.

```

simon@simon-laptop:~$ locate mesa /var/cache/apt/archives/libgl1-mesa-dri_6.5.1-cvs20060628_i386.deb
/var/cache/apt/archives/libgl1-mesa_6.5.1-cvs20060628_i386.deb
/var/cache/apt/archives/libglu1-mesa_6.5.1-cvs20060628_i386.deb
/var/cache/apt/archives/mesa-utils_6.5.1-0ubuntu16_i386.deb
/var/lib/dpkg/info/libgl1-mesa-dri.list
/var/lib/dpkg/info/libgl1-mesa-dri.md5sums
/var/lib/dpkg/info/libgl1-mesa.list
/var/lib/dpkg/info/libgl1-mesa.md5sums
/var/lib/dpkg/info/libgl1-mesa.postinst
/var/lib/dpkg/info/libgl1-mesa.postrm
/var/lib/dpkg/info/libgl1-mesa.shlibs
/var/lib/dpkg/info/libglu1-mesa.list
/var/lib/dpkg/info/libglu1-mesa.md5sums
/var/lib/dpkg/info/libglu1-mesa.postinst
/var/lib/dpkg/info/libglu1-mesa.postrm
/var/lib/dpkg/info/libglu1-mesa.shlibs
/var/lib/dpkg/info/mesa-utils.list
/var/lib/dpkg/info/mesa-utils.md5sums
/usr/share/doc/libgl1-mesa
/usr/share/doc/libgl1-mesa/changelog.Debian.gz
/usr/share/doc/libgl1-mesa/changelog.gz
/usr/share/doc/libgl1-mesa/copyright
/usr/share/doc/libgl1-mesa-dri
/usr/share/doc/libgl1-mesa-dri/changelog.Debian.gz
/usr/share/doc/libgl1-mesa-dri/changelog.gz
/usr/share/doc/libgl1-mesa-dri/copyright
/usr/share/doc/libglu1-mesa
/usr/share/doc/libglu1-mesa/changelog.Debian.gz
/usr/share/doc/libglu1-mesa/changelog.gz
/usr/share/doc/libglu1-mesa/copyright
/usr/share/doc/mesa-utils
/usr/share/doc/mesa-utils/changelog.Debian.gz
/usr/share/doc/mesa-utils/copyright

```

What should be the symlinking arrangement for i810 drivers? What are the symlinks for libGL.so and libgl.so.1 and stuff?

I currently have:

```

simon@simon-laptop:/usr/lib$ ls libGL.* -la
lrwxrwxrwx 1 root root     12 2006-07-16 11:42 libGL.so.1 -> libGL.so.1.2
-rw-r--r-- 1 root root 410880 2006-06-28 20:21 libGL.so.1.2

```

So many thanks for reading!

---

### Post by fakirhs on 2006-07-16
Jaidee I think I have the exact same problem, but using the ati driver (I have a ATI RADEON Mobility 7500 -- fglrx does not support it).

I have been reading hundreds of posts the last week and I haven't been able to find a solution, even though it seems that many people have/had the same problem. One interesting thing to note is that glxinfo shows that the notorious GLX_EXT_texture_from_pixmap is included in the server glx and client glx extensions, but not in the GLX and OpenGL extensions.

In the various posts that I read some people say that since GLX_EXT_texture_from_pixmap is in the server glx extensions then it should be enough. Some others say that it's a problem with the links of libGL.so (which I guess is true for those who use fglrx). A a couple of months ago somebody who was using a older version of compiz reported that the problem disappeared when he upgraded the compiz packages (!). Nothing worked for me so far and the trouble is that I don't even have a clear view of where the problem is located anyway. Is it Xorg-air that has trouble with GLX_EXT_texture_from_pixmap? Is it compiz that looks for libs at the wrong path? Is it the libGL.so itself? Is it the driver (ati) that I am using? Does it have to do with the extension libGLcore.so? ...

Anyway, here is (a lot of) information about my system.

Firs of all, of course, I get the same error when I try to start compiz:
```
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

```

Here's my glxinfo:
```
name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe,
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control,
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control,
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20060327 AGP 4x TCL
OpenGL version string: 1.3 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture,
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_window_pos,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_logic_op,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram,
    GL_EXT_packed_pixels, GL_EXT_polygon_offset, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias,
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object,
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels,
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once,
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat,
    GL_MESA_ycbcr_texture, GL_MESA_window_pos, GL_NV_blend_square,
    GL_NV_light_max_exponent, GL_NV_texture_rectangle,
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix,
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x24 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x25 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x26 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x27 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x28 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x29 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x2a 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x2b 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x2c 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x2d 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x2e 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x2f 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x30 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x31 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x32 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x4b 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

Here's some info about the location of files
```
$locate GL
/usr/share/perl/5.8.7/unicore/lib/lb/GL.pl
/usr/share/i18n/charmaps/ISO_8859-1,GL.gz
/usr/share/i18n/locales/kl_GL
/usr/share/cups/data/HPGLprolog
/usr/include/GL
/usr/include/GL/gl_mangle.h
/usr/include/GL/gl.h
/usr/include/GL/glext.h
/usr/include/GL/glx_mangle.h
/usr/include/GL/osmesa.h
/usr/include/GL/glx.h
/usr/include/GL/glxext.h
/usr/lib/python2.4/site-packages/PIL/ImageGL.py
/usr/lib/python2.4/site-packages/PIL/ImageGL.pyc
/usr/lib/python2.4/site-packages/PIL/ImageGL.pyo
/usr/lib/xorg/modules/extensions/libGLcore.so
/usr/lib/libGL.so.1
/usr/lib/libGLU.so.1
/usr/lib/libGL.so.1.2
/usr/lib/libGLEW.so.1.3.1
/usr/lib/libGLEW.so.1.3
/usr/lib/libGLU.so.1.3.060500
/usr/lib/xorg-air/modules/extensions/libGLcore.so
/usr/lib/libGL.so

```

By the way, glxinfo does not use libGLcore.so:
```
ldd /usr/bin/glxinfo
linux-gate.so.1 =>  (0xffffe000)
libGL.so.1 => /usr/lib/libGL.so.1 (0xb7ea6000)
libGLU.so.1 => /usr/lib/libGLU.so.1 (0xb7e30000)
libglut.so.3 => /usr/lib/libglut.so.3 (0xb7dfc000)
libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7dda000)
libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7cab000)
libX11.so.6 => /usr/lib/libX11.so.6 (0xb7bc5000)
libXext.so.6 => /usr/lib/libXext.so.6 (0xb7bb8000)
libXxf86vm.so.1 => /usr/lib/libXxf86vm.so.1 (0xb7bb3000)
libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7ba0000)
libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7b9d000)
libdrm.so.2 => /usr/lib/libdrm.so.2 (0xb7b96000)
libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7ac1000)
libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7ab7000)
/lib/ld-linux.so.2 (0xb7f1e000)
libXau.so.6 => /usr/lib/libXau.so.6 (0xb7ab3000)

```

Finally, here's my xorg.conf too.
```
Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
#       Load    "GLcore"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
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
        Identifier      "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
        Driver          "ati"
        Option          "XAANoOffscreenPixmaps"
        Option          "RenderAccel"           "true"
        Option          "AGPMode"               "4"
        Option          "AGPFastWrite"          "true"
        Option          "EnablePageFlip"        "True"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Option          "AIGLX"                 "true"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option  "Composite"     "Enable"
EndSection

```

Any ideas? Jaidee, did you make it work?

---

### Post by Jaidee on 2006-07-16
No luck here as yet, but I am unsure at to where my libGL.so are located.

I have this all working with XGL on an NVidia card, and I overcame the GLX_EXT error but symlinking the libGL.so files correctly - I don't understand exactly how they work but on my NVidia system my libgl.so > libgl.so.1 and libgl.so.1 > libgl.so.1.2.8756 I think.

Anyone know where libGL should be and how symlinking should look for intel and aiglx?

---

### Post by techrosis on 2006-07-17
I don't know about Iphands but as of the last two updates my Compiz is broken (not that it worked properly before mind you)....now by broken I mean that there are no window borders or effects now however the red cube is in the Gnome task bar....I can switch to Metacity and all is well...when I click on Restart Compiz...no windows again....sheesh.....but at least now the wallpaper doesn't disapper and there isn't a white bar on the right side of my screen heheheh....

---

### Post by iphands on 2006-07-17
> **techrosis said:**
> I don't know about Iphands but as of the last two updates my Compiz is broken (not that it worked properly before mind you)....now by broken I mean that there are no window borders or effects now however the red cube is in the Gnome task bar....I can switch to Metacity and all is well...when I click on Restart Compiz...no windows again....sheesh.....but at least now the wallpaper doesn't disapper and there isn't a white bar on the right side of my screen heheheh....

Weird... with the latest updates mine sill looks the same. I am missing the window borders though...

Its so odd a week or two ago aiglx was working perfectly for me, then a update just killed it. I wish I could figure out exactly which package did it and just revert... I'm starting to think its not the aiglx/compiz packages (i've tried them all), but something else.

---

### Post by findsun on 2006-07-17
After I upgrade to the latest packages, compiz became very unstable. Especially switcher and wobbly plugin, worked very badly.

Do you know how could I fix this problem?

---

### Post by t3rror on 2006-07-17
iphands, techrosis,

i am still in the same boat.  the exact same thing happened to me about 2 or 3 weeks ago.  aiglx had been running fine for more than a couple of months, and then poof, it didn't anymore.  i am still waiting for someone to definitively identify the problem.  it looks like it has something to do with the ati card since my desktop is still running great on an intel card.  i will just continue to wait patiently and hope one day i wake up to have all the aiglx goodness back on my laptop.

---

### Post by eradicator_006 on 2006-07-18
I'm attempting to install the 2.6.17 kernel on my Dapper install.  I have aiglx and compiz working great on my gma950.  Does anybody know how to compile the linux-dri-modules for the 2.6.17 kernel?

---

### Post by cywhale on 2006-07-19
Has anyone aiglx running with a radeon 9700 mobile? Read somwhere (compiz forum?) about gandalfn`s ati-driver supporting those cards...?:-k
Xgl working fine here but I just want to check out aiglx if possible. 

Following this howto aiglx seems to start, I can see the b/w background and a mouse cursor for 1 second, then I'm sent back to console.

Xorg.0.log says something about dri not working...:(

Weird: after removing all the new packages and re-editing xorg.conf and gdm.conf-custom I get back to Gnome/metacity but my wireless conecction was "not configured" ?!?

---

### Post by skattman83 on 2006-07-19
I fixed my issue with not being able to use the expose feature.  I had installed the vanilla packages and that feature is included in the quinn packages.  I switched over, and it works great now!

---

### Post by MattW on 2006-07-20
Mine broke yesterday... package came down that needed a reboot, and now /usr/bin/compiz-start doesn't actually exist. Not quite sure what's going on there.

Does anybody know which package provides compiz-start?

Edit: Further recollection suggests that the reboot was required for something like linux-image or linux-dri-something, possibly both.

Further experimentation reveals that starting compiz manually causes problems:

```

compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0
```

Yes it's the dreaded GLX_EXT_texture_from_pixmap thing again. Clearly something's gone barfy with a package update. I'm going to sit here and hope that a new compiz package maybe sorts things out.

---

### Post by Wazo-Wazo! on 2006-07-20
I can confirm everything works great and fast with an ATI Radeon 7500 (non-mobility) using the "radeon" driver and gandalfn's instructions on post number 1. 

It is also quite fast, no visible delays on windows or desktop tasks except for mouse scrolling wich is somewhat slow.

---

### Post by lomomo on 2006-07-21
i'm trying to install compiz but it seems i need gnome-session 2.14.1-0ubuntu12, and the one i have is 2.14.1-0ubuntu11.

My system is up to date and i don't know where to get this gnome-session version.

Same with libpango.

---

### Post by lomomo on 2006-07-21
> **lomomo said:**
> i'm trying to install compiz but it seems i need gnome-session 2.14.1-0ubuntu12, and the one i have is 2.14.1-0ubuntu11.

My system is up to date and i don't know where to get this gnome-session version.

Same with libpango.

It was a problem with old repository, now it is working fine.

---

### Post by Sethiano on 2006-07-21
Hi guys!

I've just got all things working on my freaking Radeon Mobility 7500 (@ IBM Thinkpad T41) and I would like to share my success story with you.

Here's what i did to make it work:

1. Did a fresh install of Ubtuntu Dapper Drake 6.06 and confirmed that
direct rendering was enabled with ```
$ glxinfo | grep direct 
direct rendering: Yes
```

2. Followed the first steps in this guide (at the first page) **except** installing dri modules packages (wich I suspected changed my direct rendering to "no")

3. Choosed the Quinn packages

4. Continue to follow every last step in the guide

5. SUCCESS!

I've hope this will help somebody!

P.S I use the deafult "ati" driver not the "radeon"

---

### Post by MattW on 2006-07-22
> **skattman83 said:**
> Thanks for the reply, but it was already activated.  I checked and the key to activate it was alt tab, but that just gave me a fancy alt tab switch.  How do I get the OSX style expose functionality?

The plugin's called Scale. When my compiz was working I had it set up to activate when I pressed Pause, and things worked nicely. Alt-Tab triggered the Nav plugin as per the default settings.

---

### Post by originof on 2006-07-22
hi to all, i'm italian....my english isn't very good.... ](*,) 

Tutorial say that i must modify the Device section

```
Section "Device"
Identifier "Intel Corporation Intel Default Card"
Driver "i810"
Option "XAANoOffscreenPixmaps"
BusID "PCI:0:2:0"
EndSection
```


but i have TWO device section :rolleyes: 

```
Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection
```

so, where i add the Option "XAANoOffscreenPixmaps" ??
thanks :D

---

### Post by originof on 2006-07-22
> **originof said:**
> hi to all, i'm italian....my english isn't very good.... ](*,) 

Tutorial say that i must modify the Device section

```
Section "Device"
Identifier "Intel Corporation Intel Default Card"
Driver "i810"
Option "XAANoOffscreenPixmaps"
BusID "PCI:0:2:0"
EndSection
```


but i have TWO device section :rolleyes: 

```
Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection
```

so, where i add the Option "XAANoOffscreenPixmaps" ??
thanks :D

i've tried to add the option to the all device section...but...seems doesn't work.....

---

### Post by bvc on 2006-07-23
instructions say > you should install latest dri modules packages :```
sudo apt-get install linux-dri-modules-common linux-dri-modules-`uname -r`
```
I'm Ubuntu 6.06 dapper and if I try to install those, apt wants to remove all compiz-quinn-aiglx and related packages.
I have kernel 2.6.15-23-k7. Can you not have a k7 kernel? What's up?

---

### Post by JoWilly on 2006-07-23
> **originof said:**
> i've tried to add the option to the all device section...but...seems doesn't work.....

There are no commercial ati/nvidia drivers for aiglx yet. So, it will not work with your ati 9600 (only works with cards that have working opensource 3d drivers like the ati 9250 and some intel cards).

Use xgl with your card.

---

### Post by bvc on 2006-07-23
great....so basically if you are nvidia forget aiglx for now :rolleyes: That contradicts everything I've read the past few days, but I believe you because it ain't working ](*,)

---

### Post by JoWilly on 2006-07-23
> **bvc said:**
> great....so basically if you are nvidia forget aiglx for now :rolleyes: That contradicts everything I've read the past few days, but I believe you because it ain't working ](*,)


Yes you can believe me. I know that there are many armchair gurus :) 

See here for what works and why :

[http://fedoraproject.org/wiki/RenderingProject/aiglx]("http://fedoraproject.org/wiki/RenderingProject/aiglx")

---

### Post by royskie on 2006-07-23
hello,

I kind of accidentally removed the compiz icon on my panel ....how do i get it back?

Thanks!

---

### Post by Uncle Spellbinder on 2006-07-24
OK, this may be the stupidest question to appear on this thread:

From the first post in this thread:
1.) Download packages
2.) Configure Xorg

Obviously, an xorg-aiglx + compiz noob here (and a Linux/Ubuntu novice). #1 is self explanatory to me. #2 is clearly marked with everything to configure. I just don't know what step to take to *configure*. What do I initiate to *configure* Xorg?

---

### Post by PeteD on 2006-07-24
I've just been fiddling with getting aiglx working with KDE on my new laptop (with i915gm).  It wasn't working so rather than spend more time on it today I decided to revert everything.  I'd backed up xorg.conf and any other files I'd edited (kdmrc etc) but now I can't get into KDE.  I get the kdm login screen but after login the Gnome splash screen appears, displays the first icon then just stops.   If anyone can help I'd really appreciate it as other than finishing getting aiglx working I'd just got this machine set up how I wanted it and don't really want to do a clean install :(

thx

*EDIT*  doh! lack of sleep, fixed it by changing session type to KDE on the login screen.

---

### Post by jordanmthomas on 2006-07-24
To configure X, just edit /etc/X11/xorg.conf in your favorite editor.
You'll need to be running the editor as root, so something like this:

sudo gedit /etc/X11/xorg.conf

---

### Post by thelost on 2006-07-24
](*,) 

I am experiencing some problems installing aiglx+compiz. I did all necessary, and have double-double checked everything was correct in xorg.conf & gdm.conf-custom. 

When I boot from the Gnome Login Manager it boots into Gnome ok for a few seconds, the menu item for Metacity/Compiz is there, but then it hangs and kicks me to a command prompt.

Where do I go from in analysing this problem and fixing it? I kept a normal copy of xorg.conf and when I use that everything boots up fine. Any ideas welcome!

---

### Post by JoWilly on 2006-07-24
> **thelost said:**
> ](*,) 

I am experiencing some problems installing aiglx+compiz. I did all necessary, and have double-double checked everything was correct in xorg.conf & gdm.conf-custom. 

When I boot from the Gnome Login Manager it boots into Gnome ok for a few seconds, the menu item for Metacity/Compiz is there, but then it hangs and kicks me to a command prompt.

Where do I go from in analysing this problem and fixing it? I kept a normal copy of xorg.conf and when I use that everything boots up fine. Any ideas welcome!

What is your card ?

If you are using a card with commercial binary drivers (nvidia, ati,...) it will not work as drivers are no available for this (comming soon).

---

### Post by thelost on 2006-07-24
> **JoWilly said:**
> What is your card ?

If you are using a card with commercial binary drivers (nvidia, ati,...) it will not work as drivers are no available for this (comming soon).

aaah. nvidia GeForce FX Go5700. I guess the drivers must be the problem. ah well. i will wait with baited breath. thanks for the quick reply.

---

### Post by techrosis on 2006-07-24
YO Iphands....i got mine working....it has something to do with the resolution...it is working flawlessly in 1024x768 mode...anything higher and i get the dreaded bar on the side.....there has to be a fix....i'm so excited i'm giddy....(well maybe not THAT excited heheh) anyone have any input on this...i seem to remember a similar problem on XGL when it first came out...but i don't recall what the fix was....

---

### Post by iphands on 2006-07-24
OMFG Yo Tech and T3rror I fixed it.... check the last option ive added in my "Device" section...

```
        
        Option "AGPMode" "4"
        Option "AGPFastWrite" "true"
        Option "EnablePageFlip" "true"
        Option "AGPSize"       "32"

```

I think the last line is the only critcal one, but all four are new lines for me...... It's fixed finally.

Of course  make sure the agp size is the correct size for you model...

It must have been a change in the xorg-ati driver that defaulted the mem size too low for xgl... Thanks tech you tipped me off.

Someone should update the first page as this will destroy the aiglx experience for all(?) of the mobility 7500 users. (this simple thing did me in for weeks)

p.s. Oh yeah thanks goes to gentoo my gentoo boxes... noticed the option there. ;)

---

### Post by Uncle Spellbinder on 2006-07-25
> **jordanmthomas said:**
> To configure X, just edit /etc/X11/xorg.conf in your favorite editor.
You'll need to be running the editor as root, so something like this:

sudo gedit /etc/X11/xorg.conf

Appreciate it.

---

### Post by Uncle Spellbinder on 2006-07-25
Yep, a bit confused from the start. I'm not sure what *exactly* I'm suppose to add to the repositories - 

> **gandalfn said:**
> 
1. Download packages

aiglx :
First you should add [reggaemenu compiz repository ]("http://compiz.ed3n.com/viewtopic.php?id=74") in you source.list
```

deb http://xgl.compiz.info/ dapper aiglx
deb http://xgl.compiz.info/ dapper main

```

***Which do I add? The codes from the link, or the codes below the link.*** 

The codes from the link above are:
```
deb http://xgl.compiz.info/ dapper main aiglx
deb-src http://xgl.compiz.info/ dapper main aiglx
```

which lead to this:

> Insert one of these lines (each are various mirrors, and you can get deb-src from them too if you wish.)
```
deb http://www.beerorkid.com/compiz dapper main
deb http://ubuntu.compiz.net/ dapper main
```
If you use aiglx, add ' aiglx' to the end of the line (so it reads 'main aiglx')

Then, save and exit the editor and run one of these commands (again, various mirrors) to add my key.
```
wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
wget http://ubuntu.compiz.net/quinn.key.asc -O - | sudo apt-key add -

```
Then, use the repository as usual. The useful packages are compiz, compiz-gnome, and compiz-kde.

---

### Post by techrosis on 2006-07-25
HALLELUJAH! HALLELUJAH! hehehehheh dude...i can confirm the fix on this end...i saw that Device Options all over the place and just didn't think to try that particular one figuring that X knew that much already hehehhe...dang man....this is why i love the Linux community but most of all why i love Ubuntu....nice forum peeps ACTUALLY working together heheh...peace out all....

---

### Post by t3rror on 2006-07-25
Iphands & Techrosis >

I will check this out over lunch today.  Good find to both of you.  I have been too busy to look into it too far, and had just purged my quinn packages and running without all the eye-candy.  Going to be good to get back to it now.  Thanks again guys.

---

### Post by techrosis on 2006-07-25
New problem....may be no fix....i use my laptop at work and when i leave my desk (which is quite often) i lock the desktop...after about 2 or 3 times of this it fails to go to screensaver and psudo-locks....by that i mean the cursor moves around but it doesn't go to the password screen...and i can't control-alt F2 or F3 to try and kill a rogue process or anything...btw it is a GL screensaver...i'm gonna try it with a few 2D ones and see if may the GL is causing the problem...

---

### Post by no1wantdthisname on 2006-07-25
Anyone else having a problem with Opengl games crashing X?
I used to be able to play opengl games a couple of versions back, but it doesn't seem to work anymore.  
I'm also confused as to why dmesg says that i915 is only version 1.5.0 20060119 when the deb package suggests that i915 should be at version 1.6.0.

---

### Post by techrosis on 2006-07-25
so far i've only tried foobillard and scorch3d...but those two seem to work just fine

---

### Post by damagedspline on 2006-07-25
> **techrosis said:**
> New problem....may be no fix....i use my laptop at work and when i leave my desk (which is quite often) i lock the desktop...after about 2 or 3 times of this it fails to go to screensaver and psudo-locks....by that i mean the cursor moves around but it doesn't go to the password screen...and i can't control-alt F2 or F3 to try and kill a rogue process or anything...btw it is a GL screensaver...i'm gonna try it with a few 2D ones and see if may the GL is causing the problem...

try closing the laptop screenpanel (or manually press the lid button) for 5 sec and open it again - try this for 2-3 times... works for me anyhow...

---

### Post by mmk on 2006-07-25
techrosis: i have this too, but only from the new update :)

Thanks for the AGPSize stuff. I was using 1024x768 and did not have problems, but with this settings maybe things will work faster ;)

---

### Post by techrosis on 2006-07-25
damagedspline: hehe i can't...my laptops lid switch is broken heheh...it's ghetto...

mmk:  for now i just have mine set to blank screen...seems to be fine...i'll try again after a few updates and report back...

lovin' my compiz/aiglx...woot!!!

---

### Post by Hollowman on 2006-07-26
It works. I don't know how or why it finally works, I don't care.  I am in love with compiz.  I followed the instructions and when I restarted x it died on me, I reverted to the backup of xorg.conf, and up pops my gdm but with a strange red icon in the top panel.  I then notice my windows had wobble and all the compiz goodness was there.  I checked my xorg.conf file and it, for some strange reason, did not convert back to the original.  I don't care how it happened, maybe divine intervention.  All is well,



The very happy Hollowman:D

---

### Post by Paerez on 2006-07-27
When I try to run compiz I get the following error:
compiz.real: GLX_EXT_texture_from_pixmap is missing

which I googled and apparently it means "you have an old version of mesa that doesn't have this function". The weird part is, I am running libgl1-mesa version 6.5.1-cvs20060628, which should have that ability.

I am currently getting:
$ glxinfo | grep rendering
direct rendering: Yes

Also, I have previously had XGL/Compiz working, but at only 1024x768, which is too low for me, so I thought I'd try Xorg-Air.

I'm stumped, anyone have any idea?

---

### Post by Hollowman on 2006-07-27
I have all compiz working in all its glory, but I can't figure out how to get printing to work.  I put in the two lines to gconf-editor and that didn't do anything.  Any ideas would be great.

HOllowman

---

### Post by atoni on 2006-07-27
Hiya!

I've got it working but only in 1024x768 resolution. If I go higher, there's this weird blank area on the left side of screen. Height works correctly and performance is great, but the desktop doesn't expand correct horizontally. I can put a windows over the blank area.

Any suggestions...?

EDIT: Oh I got it working with adding these line to xorg.conf, which were spoken in earlier post. Thanks! :cool: 

```
       
Option "AGPMode" "4"
Option "AGPFastWrite" "true"
Option "EnablePageFlip" "true"
Option "AGPSize"       "32"

```

---

### Post by mailmaldi on 2006-07-27
i am a newbie here....& i dunno what to do for xgl...
i ve a intel 915GAV motherboard with onboard GMA 900 graphic card

i had a fully functional dapper system with DIrect Rendering : YES

then i followed the CompositeManager/XGL tutorial here using method A to start XGL....

but after logging out & choosing XGL as new session to login i got some error so i rebooted & tried again....
this time i was able to login to XGL session but now my Direct Rendering has been switched off...it shows NO now...

please help me to setup Direct Rendering again...
or remove CompositeManager/XGL & install this one...whichever is better...
i am getting 150fps from glxgears now...:-(

---

### Post by mailmaldi on 2006-07-28
i ve just the standard onboard graphics on the intel 915 gav motherboard....

anyway i removed xgl & installed aiglx instead....works like a charm....

---

### Post by mailmaldi on 2006-07-28
hi i installed aiglx + compiz on ubuntu dapper...

after that i fiddled around with preferences & plugins & now i am finding it very weird indeed to use...

i ve messed up preferences quite a lot & want to Revert/ Reset Preferences to defaults....

how do i do it....

---

### Post by ricesteam on 2006-07-28
Just installed Ubuntu DD today, and so far so good!

My ATI drivers still needs tweaking, but with this guide I got compiz to work!

Thank OP for this guide!  (Not sure if I'm currently using Xorg 7.0 or 7.1)

...now how do I get dual display working...

---

### Post by Uncle Spellbinder on 2006-07-30
Just got through the final steps of installing **xorg-aiglx + compiz**. All I can say is WOW! Now to play around and get use to this. Impressed. Thoroughly impressed!

---

### Post by ayoli on 2006-07-30
> **Uncle Spellbinder said:**
> Just got through the final steps of installing **xorg-aiglx + compiz**. All I can say is WOW! Now to play around and get use to this. Impressed. Thoroughly impressed!

I can't say more, :D really impressive, quite easy to install, thx gandalfn for this good guide !
regards.

---

### Post by Uncle Spellbinder on 2006-07-30
first question/problem:

Now that I'm up and running, How are themes added/activated?  When I click the Compiz cube in the System tray, then "themes", there is a list of more than 30 themes. How can any of these be activated as I see only "refresh", "delete", "import",  "quit" and "edit"? None of which seem to do anything as far as activating themes.

I thought I read somewhere it has to do with CGWD and/or Gcompizthemer. Being so new to this, I'm not sure where to start or what to edit (if anything). :-k

---

### Post by ayoli on 2006-07-30
> **Uncle Spellbinder said:**
> first question/problem:

Now that I'm up and running, How are themes added/activated?  When I click the Compiz cube in the System tray, then "themes", there is a list of more than 30 themes. How can any of these be activated as I see only "refresh", "delete", "import",  "quit" and "edit"? None of which seem to do anything as far as activating themes.

I thought I read somewhere it has to do with CGWD and/or Gcompizthemer. Being so new to this, I'm not sure where to start or what to edit (if anything). :-k

i've edited /usr/bin/compiz-start and replace gnome-window-decorator with cgwd (2 occurences) in start_compiz() function (at the top of the script), then i had to restart X.
regards.

---

### Post by RajivNair on 2006-07-30
can anyone tell me how can i achieve the effect in the attached pic.?

and also is the water n rain effect possible yet on aiglx?

thnx in advance,
rajiv.

---

### Post by ayoli on 2006-07-30
> **RajivNair said:**
> can anyone tell me how can i achieve the effect in the attached pic.?

and also is the water n rain effect possible yet on aiglx?

thnx in advance,
rajiv.

hold ctrl+alt+left-clik and move the cube manually
it seems that water and rain fx don't work with aiglx.
regards.

---

### Post by RajivNair on 2006-07-30
thnx mate,ayoli

---

### Post by sorcererx84 on 2006-07-30
> **ayoli said:**
> i've edited /usr/bin/compiz-start and replace gnome-window-decorator with cgwd (2 occurences) in start_compiz() function (at the top of the script), then i had to restart X.
regards.

Actually there's a third occurence in metacity_menu_activate. You should replace that also because otherwise cgwd stays in memory after you switch to metacity.

---

### Post by Uncle Spellbinder on 2006-07-30
> **sorcererx84 said:**
> Actually there's a third occurence in metacity_menu_activate. You should replace that also because otherwise cgwd stays in memory after you switch to metacity.


**SOLVED**

I replaced my *#! /usr/bin/python* with the compiz-start.py from *WiLLiE's* post [here](http://www.compiz.net/viewtopic.php?pid=15059#p15059). Changing and adding themes with no problem now. All effects are available.

---

### Post by mscman on 2006-07-30
> **ayoli said:**
> it seems that water and rain fx don't work with aiglx.
regards.
Interesting... I'm able to use the rain effect with no problem at all with the shortcut SHIFT+F9, just like on my computer using XGL. There's no lag whatsoever. (It actually performs better than on my nVidia card...)

Also a big thanks to gandalfn for the HowTo and everyone on the Compiz team!  You guys are awesome!!! :D  I brag about Compiz to anyone that thinks Vista is gonna kick @$$ simply because of the eyecandy; Linux does it better and with less resources!

---

### Post by NMUrugbysteve on 2006-07-30
So I just installed on a i855 and when i log in the gnome splash shows and then it throws me to a terminal and restarts GDM. Anyone know what's going on?

---

### Post by zootreeves on 2006-07-31
Aiglx + Compiz = kickass :)

Spent ages trying to get xgl to work, followed this guide worked first time :cool: Better than anything vista can offer..

---

### Post by routerstu on 2006-08-02
i followed the instructions as well and rebooted to gdm, entered login info and started process but gdm keeps looping.  any ideas?

---

### Post by facejeans on 2006-08-02
Hey all,

I'm running a dell 700m with an i855gm gfx...aiglx works, but its all slow...Did any of the other i855gm users update something that was not on the how-to?  I have the drivers from the 915resolutionfix...are there better ones out there?  Please help, all these people love the aiglx on i855gm...i want to be one too!

EDIT: when i mean running slow, i am specifically noticing wobbly to run slow if the screen is somewhat large.  ALSO, my glxgears is pulling in only about 432 FPS, when others have reported 700's...please help if you know why!:confused:

---

### Post by drpolish on 2006-08-02
ever since i updated compiz, it seemed to have ruined  my aiglx compiz experience. I've been able to manage some bearable speed with the plugins by lowering the numbers and figuring with stuff, but i cant get the cube to spin right. the cube starts turning, then it just shows the full desktop. another thing is that when i try to get to my menu (which is in the upper left corner, all the windows just organize (like F12) and therefore i cant click on the menu. i've been using aiglx and compiz for about a year on my laptop, and nothing was this bad!

---

### Post by dengar on 2006-08-02
I was wondering whether there is a way to restore the default options in gconf-editor. When I installed the latest version of quinn's version of compiz aiglx it made things hairy, so I tried to mess with the options and fi x it without luck. Is there a way I can completely remove the keys from gconf-editor so that when I reinstall it'll give me the default options?

---

### Post by jstueve on 2006-08-02
gconftool-2 --recursive-unset /apps/compiz

---

### Post by damagedspline on 2006-08-02
> **routerstu said:**
> i followed the instructions as well and rebooted to gdm, entered login info and started process but gdm keeps looping.  any ideas?

you might be using bad xorg.conf configuration or fglrx/nv driver

facejeans:
try setting your screen to 16 bpp instead of 24 in xorg.conf.
slowness is most likely to occur when running firefox with flash/resizing windows, etc...

---

### Post by facejeans on 2006-08-02
Damagedspline:

You are an effing God.  Thank you.  This is Too sexy.

---

### Post by Uncle Spellbinder on 2006-08-02
OK. Just had an update nitification. One of the updates was Compiz. "Removing Gcompiz themer and updating cgwd". Rebooted and now there's no cube in the system tray and I can't find a way to get it back. No way to modify or add themes. Ideas??

---

### Post by Uncle Spellbinder on 2006-08-03
:? :-k

Just checked in *Synaptic* and noticed this in *Not Installed (Residual Config)* :
[[img]http://img220.imageshack.us/img220/9444/compizreinstall1fu6.th.png[/img]](http://img220.imageshack.us/my.php?image=compizreinstall1fu6.png)

Tried to (re) install, and got this:
[[img]http://img164.imageshack.us/img164/7193/compizreinstall2na5.th.png[/img]](http://img164.imageshack.us/my.php?image=compizreinstall2na5.png)

---

### Post by TheMono on 2006-08-03
The new CGWD - Generic Custom Window Decorator - included GCompizThemer, so that package gets uninstalled. However, compiz-quinn-aiglx still depends on that specific package, therefore it will not install.

Has been fixed now though I believe.

---

### Post by facejeans on 2006-08-03
Hey guys,

Thanks again for the help...changing the depth to 16 really made a difference, it runs exceptional. 

I do have a new problem, however.  When i use firefox to login to gmail, or to just get to the yahoo homepeage, firefox crashes.  No other site i've found does this except these two, and it was working fine after the compiz install.  Has anyone experienced this before?  and how do i fix it?

---

### Post by mercurysquad on 2006-08-03
> **routerstu said:**
> i followed the instructions as well and rebooted to gdm, entered login info and started process but gdm keeps looping.  any ideas?

For anyone having this problem, the solution is to do this right after installing and setting everything up -

sudo apt-get install xserver-xorg-driver-i810

It took me 3 days to figure this simple fact that for whatever reason (maybe because of not doing a full dist-upgrade), the latest i810 driver (v1.6 I think) were not installed with compiz or xorg-air... the one that comes with ubuntu is 1.4.1.

If you have already messed up and gdm keeps restarting, just restart in recovery mode, then

apt-get remove compiz-quinn-aiglx compiz compiz-gnome
apt-get remove xserver-xorg-air-core
apt-get install xserver-xorg-air-core
apt-get install --reinstall xserver-xorg-driver-i810

Then restart (type reboot instead of doing gdm restart). It should come up because compiz is no longer there. Then type -

glxinfo|grep direct

in a terminal. It should say yes, which means the i810 driver v1.6 is up and running. Finally reinstall compiz -

sudo apt-get install install compiz-quinn-aiglx compiz-gnome

and restart X (ctrl+alt+backspace).

Hope it helps!

BTW, anyone know why i810 driver v1.6 is giving me worse performance than 1.4.1? I used to get around 1080 fps in glxgears but now I get only around 750-800 fps (with or without compiz running). Any pointers?

---

### Post by bwayman on 2006-08-04
I wish there would be a package that does all that work for you. Just download and it will install.. I am not that much of a geek.

---

### Post by damagedspline on 2006-08-04
> **facejeans said:**
> Hey guys,

Thanks again for the help...changing the depth to 16 really made a difference, it runs exceptional. 

I do have a new problem, however.  When i use firefox to login to gmail, or to just get to the yahoo homepeage, firefox crashes.  No other site i've found does this except these two, and it was working fine after the compiz install.  Has anyone experienced this before?  and how do i fix it?

you need to edit the file /usr/bin/firefox:
search for the section that says
```
##
## Variables
##
```

and add a line after it:
```
export XLIB_SKIP_ARGB_VISUALS=1
```

so it will look like this:
```
##
## Variables
##
export XLIB_SKIP_ARGB_VISUALS=1
MOZ_DIST_BIN="/usr/lib/firefox"
MOZ_PROGRAM="${MOZ_DIST_BIN}/firefox-bin"
```

this is need to be done after every firefox update until further notice

---

### Post by facejeans on 2006-08-04
I'm sorry, i feel like i'm the one that just has issue after issue.  

Once again, damagedspline, you are my savior.  Thanks.

So here's my latest issue:

I get this error when I'm updating apt: 

W: GPG error: [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
W: You may want to run apt-get update to correct these problems

Now i think i have done this whole key import thing for automatix without knowing it, but how do i fix this error, because simply re running apt-get update doesn't fix it.  Where can i get this key, or how do i put it in?

---

### Post by Aldoo on 2006-08-04
Hey, I am running AIGLX+Compiz on my Intel i915. Almost everything is working fine, excepted that the saturation setting does not really work : either the window has 100% saturation and is fully colored, either it is less than 100% and the window is gray scales only, even if the saturation is strictly more than 0%.

Do you have the same bug ?

---

### Post by damagedspline on 2006-08-05
> **bwayman said:**
> I wish there would be a package that does all that work for you. Just download and it will install.. I am not that much of a geek.

such package cannot exist yet since it is still in experimental stages and need to be tweaked differently on different computers, taking in factor: the video card, cpu speed etc...

besides, it not that bad, just edit a couple of files and you get your aiglx+compiz up and running (in most cases).

> **facejeans said:**
> I'm sorry, i feel like i'm the one that just has issue after issue.  

Once again, damagedspline, you are my savior.  Thanks.

So here's my latest issue:

I get this error when I'm updating apt: 

W: GPG error: [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
W: You may want to run apt-get update to correct these problems

Now i think i have done this whole key import thing for automatix without knowing it, but how do i fix this error, because simply re running apt-get update doesn't fix it.  Where can i get this key, or how do i put it in?

please search the thread before posting a question, i posted an answer a while back
[http://www.ubuntuforums.org/showpost.php?p=1197416&postcount=1010](http://www.ubuntuforums.org/showpost.php?p=1197416&postcount=1010)

---

### Post by Milamber_Cubed on 2006-08-05
> **Aldoo said:**
> Hey, I am running AIGLX+Compiz on my Intel i915. Almost everything is working fine, excepted that the saturation setting does not really work : either the window has 100% saturation and is fully colored, either it is less than 100% and the window is gray scales only, even if the saturation is strictly more than 0%.

Do you have the same bug ?

I have this problem as well... I just set all windows to be 100% and I can live without the fanciness. 

One thing that I haven't been able to get a solution for is that with the newer versions of compiz everything is kind of slow and jerky. If I revert back to compiz_0.0.13-0quinn12_i386, everything is nice and smooth again. Anyone have any ideas what could be causing this and maybe even a fix?

I can live with the older version of compiz, but knowing that I might be missing out on a fancy new feature is a bit upsetting :rolleyes:

---

### Post by Razer(x) on 2006-08-06
i have just installed aiglx,but how can i change the theme???using cgwd themer ora what?i want to install [this]("http://www.compiz.net/viewtopic.php?id=2634") theme is it possible? ](*,) ](*,)

---

### Post by foxy123 on 2006-08-06
> **Razer(x) said:**
> i have just installed aiglx,but how can i change the theme???using cgwd themer ora what?i want to install [this]("http://www.compiz.net/viewtopic.php?id=2634") theme is it possible? ](*,) ](*,)

if you have gset-compiz icon, then click it and click 'Use cgwd' then 'Themes' and choose your favourite theme...

---

### Post by Razer(x) on 2006-08-06
i THINK that i don't have it...but i THINK...

---

### Post by foxy123 on 2006-08-06
> **Razer(x) said:**
> i THINK that i don't have it...but i THINK...

then in Settings you should have CGWD Themer, use it, but make sure that you use cgwd not gnome-window-decorator (or sort of)

---

### Post by Razer(x) on 2006-08-06
yes,there is the cgwd themer...how can i use the cgwd and not the gnome-window-decorator?..sorry..but i'm not an expert :(..i think that i am using is but if i select a theme in the cgwd themer the theme does'nt change

---

### Post by foxy123 on 2006-08-06
> **Razer(x) said:**
> yes,there is the cgwd themer...how can i use the cgwd and not the gnome-window-decorator?..sorry..but i'm not an expert :(

basically you should kill gnome-window-decorator and launch cgwd. You may try 
```
killall gnome-window-decorator &
cgwd &
exit
```
and then make sure that cgwd is launched in gnome-session instead of gnome-window-decorator. I do not use gnome so I do not remember correctly how to do it, but you may use Preferences/Sessions for that.

---

### Post by Razer(x) on 2006-08-06
i'm not gay...but i love you!!!!!!..thanx...

---

### Post by foxy123 on 2006-08-06
> **Razer(x) said:**
> i'm not gay...but i love you!!!!!!..thanx...

I'm glad if it helped :)

---

### Post by Razer(x) on 2006-08-06
> **foxy123 said:**
>  I do not use gnome so I do not remember correctly how to do it, but you may use Preferences/Sessions for that.
somebody know how can i do this?(sorry,but my english isn't so good)

---

### Post by Razer(x) on 2006-08-06
nobody??please help me

---

### Post by Dunska on 2006-08-06
> **ayoli said:**
> i've edited /usr/bin/compiz-start and replace gnome-window-decorator with cgwd (2 occurences) in start_compiz() function (at the top of the script), then i had to restart X.
regards.

This is what I did and it worked fine.

---

### Post by Dunska on 2006-08-06
OK, I just relooked at my /usr/bin/compiz-start script and it has been updated recently.  The above editing is not required.
The script now has a get_wnd() function that checks for the existence of a .cgwd-start file in your home directory.  If it is there it will start cgwd.

I assume this .cgwd-start file is created when you choose "use cgwd" from the  gset-compiz menu (this is using quinn's packages).

---

### Post by cogsprocket on 2006-08-06
gandalfn

Thanks a lot!  It took a little bit of doing.  I had to do a little more legwork to get compiz running, but the payoff was well worth it.

---

### Post by Razer(x) on 2006-08-07
> i've edited /usr/bin/compiz-start and replace gnome-window-decorator with cgwd (2 occurences) in start_compiz() function (at the top of the script), then i had to restart X.
regards.

somebody can change it for me??please

---

### Post by Razer(x) on 2006-08-07
please i need help!

---

### Post by foxy123 on 2006-08-07
> **Dunska said:**
> OK, I just relooked at my /usr/bin/compiz-start script and it has been updated recently.  The above editing is not required.
The script now has a get_wnd() function that checks for the existence of a .cgwd-start file in your home directory.  If it is there it will start cgwd.

I assume this .cgwd-start file is created when you choose "use cgwd" from the  gset-compiz menu (this is using quinn's packages).

> please i need help!
you do not need to edit it as to the post above. Just create .cgwd-start file in your home directory.

---

### Post by techrosis on 2006-08-07
I know this has been asked before...but my situation is a bit different...themes are broken....cgwd is running but clicking on a theme does nothing...i've manually killed and --replaced cgwd and that didn't help either...i'm wondering if there may be some "leftover" config files somewhere screwing with it...any ideas???

---

### Post by foxy123 on 2006-08-07
> **techrosis said:**
> I know this has been asked before...but my situation is a bit different...themes are broken....cgwd is running but clicking on a theme does nothing...i've manually killed and --replaced cgwd and that didn't help either...i'm wondering if there may be some "leftover" config files somewhere screwing with it...any ideas???

remove .cgwd from you home dir it should fix it...

---

### Post by techrosis on 2006-08-07
heheh thanks...i just finished doing that and it worked and was on my way back to report it hehehe...many thanks...

---

### Post by Razer(x) on 2006-08-07
create a cgwd start file???and what i have to write into this?can you do it for me?please

---

### Post by foxy123 on 2006-08-07
just make it empty

---

### Post by Razer(x) on 2006-08-07
but i don't have to kill the gnome-window-decorator?

---

### Post by techrosis on 2006-08-07
didn't know where to post this...since this has been my regular thread as of late i'll post here :) ...has anyone else experienced the HIGH cpu usage when amarok is onscreen as of like 3 or 4 updates ago....works fine...was just concerned what may be making it slam the cpu like that when it's onscreen...if i minimize it to system tray it drops back down to normal levels....wierd huh....

---

### Post by Razer(x) on 2006-08-07
so..i have to create a text and his name must be cgwd-start?

---

### Post by techrosis on 2006-08-07
open up your terminal app and type the following:

touch .cgwd-start

that will create an empty file named as it needs to be....

---

### Post by Razer(x) on 2006-08-07
it didn't work

---

### Post by Dunska on 2006-08-07
Razer(x) - are you using quinn's packages?

That is, did you install this:
```
sudo apt-get install compiz-quinn-aiglx compiz compiz-gnome
```

If you follow this guide and install quinn's packages (rather than the vanilla ones), the you should have a red gset-compiz icon in your tray that you can click on and select "Use cgwd" from the menu.  You will (or may) need to install the cgwd-themes package also:
```
sudo apt-get install cgwd-themes
```

---

### Post by blackphiber on 2006-08-08
*EDIT
Ok, so I decided to be a bit daring and followed the instructions on the first page word for word and went with compiz-vanilla packages.  I read a few pages in and a bunch of people were getting lots of white (no wall paper, i cannot access anything in my menus, no applications, no clock etc).  I found one post which looks like it would solve my problem, but it is very old and I have no idea where the script for starting compiz is
[here is the post]("http://www.ubuntuforums.org/showpost.php?p=833855&postcount=129").  Any ideas/suggestions?  appreciated.  Thank you.

*Ok, nevermind, seems like many people have this problem (the missing wallpaper/right side of the screen missing problem....) so, sorry to bother

---

### Post by Meck1982 on 2006-08-08
Hello everybody!

This is no answer to the previous posts. I just wanted to say that I got Compiz/AIGLX working on my Acer Travelmate 800 with radeon mobility 9000 (64MB) by following this HOWTO. I am using the compiz-quinn packages never tried vanilla.
I am very satisfied with the speed in 16 bpp mode, scrolling is smooth and glxgears shows me over 2000 FPS. \\:D/ 
When I switch to 24 bpp the speed is still impressing concerning the compiz effects. BUT the scrolling in Konqueror is quite slow and CPU-consuming so that I stick to 16 bpp for now. :???: 

By the way I am using KDE and this is my Device Section in xorg.conf:

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
        Option          "AGPMode" "8"
        Option          "AGPFastWrite" "yes"
        Option          "ColorTiling" "on"
        Option          "EnablePageFlip" "on"
#       Option          "AccelMethod" "EXA"
#       Option          "FBTexPercent" "10"
EndSection

So my question is: Is there a way to have both smooth scrolling and 24 bpp mode?

---

### Post by techrosis on 2006-08-08
```

```> **blackphiber said:**
> *EDIT
Ok, so I decided to be a bit daring and followed the instructions on the first page word for word and went with compiz-vanilla packages.  I read a few pages in and a bunch of people were getting lots of white (no wall paper, i cannot access anything in my menus, no applications, no clock etc).  I found one post which looks like it would solve my problem, but it is very old and I have no idea where the script for starting compiz is
[here is the post]("http://www.ubuntuforums.org/showpost.php?p=833855&postcount=129").  Any ideas/suggestions?  appreciated.  Thank you.

*Ok, nevermind, seems like many people have this problem (the missing wallpaper/right side of the screen missing problem....) so, sorry to bother
don't know how far into the thread you've read or if you've tried this yet...but when i was getting the "white/no wallpaper" problem this is what fixed me...make sure you have the following in your xorg.conf under the device section:```
Option "AGPSize"     "32"
```

Of course you'd want to change the 32 to whatever amount of video memory you have...this fixed my issues...

---

### Post by zachstruck on 2006-08-08
I'm running kernel 2.6.17-5-686 with i915 graphics.  glxinfo says that direct rendering is enabled.  However, X is giving me errors when I restart gdm.  It says that "Module ABI version (1) doesn't match the server's version (0)"  and then fails to load the module i810 because of a module mismatch.  Any suggestions as to how to fix this problem?

---

### Post by blackphiber on 2006-08-08
Thanks tech, that tip, plus your previous tip of changing resolution worked.  I have a 9200 mobility.  my screen supports 1400x1050 but aiglx only works at 1024x768 for now, kind of a shame.  Either it is a bug, or my card just cannot handle it at the higher resolution.

---

### Post by Razer(x) on 2006-08-08
no,i am using the package vanilla...and i've installed cgwd theme

---

### Post by techrosis on 2006-08-08
> **blackphiber said:**
> Thanks tech, that tip, plus your previous tip of changing resolution worked.  I have a 9200 mobility.  my screen supports 1400x1050 but aiglx only works at 1024x768 for now, kind of a shame.  Either it is a bug, or my card just cannot handle it at the higher resolution.
how much video memory does it have...i have the mobility 9000 same resolution as you with 32MB video mem...i couldn't go about 1024x768 until i added the Option "AGPSize" line...after i did that all resolutions worked....good luck...if that doesn't do it post back and i'll post entire Device section from Xorg for ya :)

---

### Post by techrosis on 2006-08-08
> **Razer(x) said:**
> no,i am using the package vanilla...and i've installed cgwd theme
if i'm not mistaken that is your problem...to my knowledge cgwd doesn't work with vanilla....

---

### Post by Razer(x) on 2006-08-08
i don't know..but i've installed cgwd themer using synaptic and when i do,-killall gnome-window-decorator &
-cgwd &
-exit
it works

---

### Post by blackphiber on 2006-08-08
> **techrosis said:**
> how much video memory does it have...i have the mobility 9000 same resolution as you with 32MB video mem...i couldn't go about 1024x768 until i added the Option "AGPSize" line...after i did that all resolutions worked....good luck...if that doesn't do it post back and i'll post entire Device section from Xorg for ya :)

Heh, turns out I have the exact same configuration as you, I was wrong, I have the [mobility 9000 too]("http://www.thinkwiki.org/wiki/Category:T41")

my entire device section
```

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
        Option          "backingstore"  "true"
        Option          "ColorTiling"   "on"
        Option          "EnablePageFlip"        "true"
        Option          "SubPixelOrder"         "none"
        Option          "RenderAccel"           "true"
        Option          "AGPMode"               "4"
        Option          "DynamicClocks"         "on"
        Option          "mtrr"                  "on"
        Option          "VideoOverlay"          "on"
        Option          "OpenGLOverlay"         "off"
        Option          "AGPSize"               "32"
EndSection

```

if you could post it that would be great.  Thanks again.
oh and it looks like there is a [bug out for it]("https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/42527")
*edit2
I was able to kick it up to 1280x1024 instead of 1024x768, so much better, although I wish it would work at 1400x1050.  Well, I did get it to work (magically started working, idk why) but at 1400x1050 it is so slow it is not worth it, at 1280x1024 it is enough and fast enough.  thanks for the help. *edit3: setting the default depth down to 16 allows me to run at 1400x1050 and no real noticable difference to me.

---

### Post by FuriousChipmunk on 2006-08-10
I'm trying to get aiglx and compiz to work together on my laptop. The problem is that I have a SiS 760 graphics chips which sucks. Months ago when xgl first came out, I tried to compile the source myself and almost got it running (had wobbly windows but were all black). Now I am trying to get aiglx to work since I think it will be a better choice. I followed the guide that is on the first post and I can boot up using the aiglx xserver, but when I try to run compiz, glxinfo, glxgears, etc. the gdm crashes me back out into the login prompt. I have read other people that have had this problem too, but it has gone away for others. Can someone give me an idea what is going on, besides have a **POS** SiS chip?

Also, if no one knows how to resolve this, is there a guide or something that I can use to get aiglx compiled *correctly* from source. Thanks...

---

### Post by seshomaru samma on 2006-08-11
Hi ,just followed the first post and I get this error:
```
sesho@ubuntu:~$ compiz-start
GTK Accessibility Module initialized
gnome-window-decorator: no process killed
GTK Accessibility Module initialized
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32
compiz.real: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
compiz.real: water: GL_ARB_fragment_program is missing
Can't use gconf-dump plugin with gconf plugin
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32
--replace: GLX_EXT_texture_from_pixmap is missing
--replace: Failed to manage screen: 0
--replace: No managable screens found on display :0.0
GTK Accessibility Module initialized
GTK Accessibility Module initialized
GTK Accessibility Module initialized
Bonobo accessibility support initialized
application finalize called
```

my card is :```
0000:00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
```

(I just bought an nVidia card but my machine doesn't seem to have a slot for it)

I tried starting Compiz with other commands I found on this thread but mots of them return 'command not found'

I get a Gset Compiz item on my menu but most of it is empty (see attached)

---

### Post by Andrew67 on 2006-08-11
Hi, I decided to try out aiglx today, and I'm running into a bit of trouble when attempting to install the vanilla or quinn packages for compiz, which seems to be a broken dependency for package 'gset-compiz'. Here's the output of the apt-get command:

```
$ sudo apt-get install compiz-vanilla-aiglx compiz-vanilla compiz-vanilla-gnome
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz-vanilla-aiglx: Depends: gset-compiz but it is not installable
E: Broken packages
```

Trying the quinn packages gives the same error as well (same package missing).
Any help is appreciated.

---

### Post by royskie on 2006-08-11
I'm also getting that broken packages error when trying to install.  I tried both quinn and vanilla.

---

### Post by skroll on 2006-08-12
Well, I just finished doing this with a Inspiron 6000 with an i915gm graphics adapter.  Everything worked 100% fine, execpt if I disable the cube plugin (or even rotate) I am unable to switch to different virtual desktops.  However, everything seems to run better with aiglx then just the plain jane Ubuntu install.

Awesome guide!

---

### Post by royskie on 2006-08-12
I've used this guide before and it worked.  However, I rebuilt dapper (installed from scratch).  Now I'm getting the error of broken packages after running "sudo apt-get install compiz-quinn-aiglx compiz compiz-gnome".  


**************************************************************************
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
root@StarterTux:/home/roy# sudo apt-get install compiz-quinn-aiglx compiz compiz-gnome
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz-quinn-aiglx: Depends: gset-compiz but it is not installable
E: Broken packages
*************************************************************************


I was also was able to stumble upon an error that says:

"compiz-quinn-aiglx:
 Depends: gset-compiz  but it is not installable"

any ideas?

thanks!

---

### Post by phetre on 2006-08-12
Hi Royskie,

I had the same problem last night.  It seems gset-compiz is no longer in the repositories.  Fortunately, you can still download a .deb file for gset-compiz, which you can install using GDebi (just double-click on the .deb file if you're using Dapper).  There's a copy available here:  [http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/]("http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/").  And in case that goes down, I&#8217;ll host it on my space for a while: [http://home.uchicago.edu/~pashultz/gset-compiz_0.3.4-3v1ubuntu3_i386.deb]("http://home.uchicago.edu/~pashultz/gset-compiz_0.3.4-3v1ubuntu3_i386.deb")
Hope this helps!

---

### Post by feniix on 2006-08-14
It gives me this error, what can i do to fix it?

```

root@otaegui:~# apt-get install compiz-quinn-aiglx compiz compiz-gnome
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
No se pudieron instalar algunos paquetes. Esto puede significar que
usted pidió una situación imposible o, si está usando la distribución
inestable, que algunos paquetes necesarios no han sido creados o han
sido movidos fuera de Incoming.
La siguiente información puede ayudar a resolver la situación:

Los siguientes paquetes tienen dependencias incumplidas:
  compiz: Depende: libpango1.0-0 (>= 1.12.3) pero 1.12.2-0ubuntu3 va a ser instalado
  compiz-gnome: Depende: libpango1.0-0 (>= 1.12.3) pero 1.12.2-0ubuntu3 va a ser instalado
  compiz-quinn-aiglx: Depende: gnome-session (>= 2.14.1-0ubuntu12) pero 2.14.1-0ubuntu11 va a ser instalado
                      Depende: gset-compiz pero no es instalable
                      Depende: cgwd pero no va a instalarse
E: Paquetes rotos

```

---

### Post by facejeans on 2006-08-14
> **feniix said:**
> It gives me this error, what can i do to fix it?

```

root@otaegui:~# apt-get install compiz-quinn-aiglx compiz compiz-gnome
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
No se pudieron instalar algunos paquetes. Esto puede significar que
usted pidió una situación imposible o, si está usando la distribución
inestable, que algunos paquetes necesarios no han sido creados o han
sido movidos fuera de Incoming.
La siguiente información puede ayudar a resolver la situación:

Los siguientes paquetes tienen dependencias incumplidas:
  compiz: Depende: libpango1.0-0 (>= 1.12.3) pero 1.12.2-0ubuntu3 va a ser instalado
  compiz-gnome: Depende: libpango1.0-0 (>= 1.12.3) pero 1.12.2-0ubuntu3 va a ser instalado
  compiz-quinn-aiglx: Depende: gnome-session (>= 2.14.1-0ubuntu12) pero 2.14.1-0ubuntu11 va a ser instalado
                      Depende: gset-compiz pero no es instalable
                      Depende: cgwd pero no va a instalarse
E: Paquetes rotos

```
Read above, it tells you exactly how to get gset to work again

---

### Post by facejeans on 2006-08-14
> **seshomaru samma said:**
> Hi ,just followed the first post and I get this error:
```
sesho@ubuntu:~$ compiz-start
GTK Accessibility Module initialized
gnome-window-decorator: no process killed
GTK Accessibility Module initialized
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32
compiz.real: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
compiz.real: water: GL_ARB_fragment_program is missing
Can't use gconf-dump plugin with gconf plugin
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32
--replace: GLX_EXT_texture_from_pixmap is missing
--replace: Failed to manage screen: 0
--replace: No managable screens found on display :0.0
GTK Accessibility Module initialized
GTK Accessibility Module initialized
GTK Accessibility Module initialized
Bonobo accessibility support initialized
application finalize called
```

my card is :```
0000:00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
```

(I just bought an nVidia card but my machine doesn't seem to have a slot for it)

I tried starting Compiz with other commands I found on this thread but mots of them return 'command not found'

I get a Gset Compiz item on my menu but most of it is empty (see attached)

I have the same problem, Mine looks like this:

libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32
compiz.real: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
compiz.real: water: GL_ARB_fragment_program is missing


Does anyone know how to correct this?  Damaged Spline, maybe you do? :)  Also, that's the reason why the water plugin seems to not be working for me, and probably for most, how do you fix that?

---

### Post by smileyjon on 2006-08-15
Hello,

Having a few problems getting aiglx+compiz working and would appreciate any help.

I followed the guide on the first page of this thread to the letter, and can actually start compiz, but everything "compiz-like" (effects, etc) happens incredibly slowly. This, combined with the massive spike in CPU usage whenever I open, move, minimize, etc a window or menu makes me believe that no work is being done by my graphics card and instead everything is being done by the CPU.

My system: a HP/Compaq nx6110 laptop with an Intel 915GM/GMS/910GML graphics chip, running a fresh install of Xubuntu 6.06.1. I *am* killing xfwm4 before launching compiz.

Attached are the output of lspci, xorg.conf, the output of glxinfo, and the latest Xorg.0.log (gzipped).

Other things I've come across while trying to solve this that may or may not be relevant: 

[LIST]
[*]When I run e.g. glxinfo I get the same libGL warnings shown in the posts above this one.
[*]/var/log/gdm/:0.log contains the line *Exceeded maximum nr indirect texture lookups*
[*]The gdm log has also previously contained the lines *DRM_I830_CMDBUFFER: -22* and *(EE) I810(0): I830 Vblank Pipe Setup Failed*
[*]/var/log/syslog repeatedly contains the line *localhost kernel: [17179924.076000] [drm:i915_cmdbuffer] *ERROR* i915_dispatch_cmdbuffer failed*
[/LIST]

Any and all help is gratefully appreciated!

j.

---

### Post by gruffy-06 on 2006-08-15
Why do my windows under Compiz resize *very* slowly? I love my performace after all.

--Gruffy--

*Life is one's dream. Nothing more, nothing less.*

---

### Post by smileyjon on 2006-08-15
Ah. After a bit more playing around it seems that one or more of the plugins causing the problems.

I'll try and narrow it down.

---

### Post by drpolish on 2006-08-15
suddenly, quinn's aiglx packages havent been working so smoothly with aiglx. its still smooth, but not as before- 
and does anyone know how to make the cube not zoom out before switching desktops?

---

### Post by facejeans on 2006-08-15
drpolish,

the maximize/minimize and cube zoom thing were pretty bad That's why i removed quinn and installed vanilla...i have an 855 and it was running like a$$...but vanilla runs perfect, and you can still use cgwd themes by running this at terminal:

$sudo killall gnome-window-decorator & cgwd & exit

works for me like a charm, i just don't know how to make it work as a startup command(if anyone knows, please let me know)

gruffy, smileyjohn:

Try a couple of these things to see if it moves a little better: (if you have quinn installed, this is probably not going to do much)

in Gconf-editor: 

apps>panel>global and disable animations
Gnome>desktop>interface and disable animations
Apps>metacity>general or global or something, and enable reduced resources.

Also, another thing that i changed is to edit your xorg.conf file, and wherever you see the defaultdepth line ( i think its under the screen section) set it at 16 instead of 24.  

I hope this helps!

---

### Post by facejeans on 2006-08-15
Smileyjon (sorry i spelled it wrong before):

Did you install the 915resolution package?  that is a package that patches ubuntu and installs the proper drivers.  That might be why you're having an issue too?  if not, just have your universe repos open (and multiverse just in case) and update and install 915resolution.

---

### Post by bdonkey on 2006-08-15
I am having the same performance problems as drpolish and facejeans: quinn packages performance are down the drain, but vanilla runs smooth as butter.

Oddly, I think it has more to do with the quinn-aiglx component than the others; while I was mucking around with synaptic, I got the quinn packages running super smoothly for just one session. When I rebooted, it was gone :(

Anybody have an idea what's going on? Just seems odd that the two would differ so much.

---

### Post by smileyjon on 2006-08-16
Hi Facejeans,

Thanks for the advice. I do have quinn installed - may try vanilla later - but am using Xubuntu, so changing gnome settings isn't going to do a great deal! 

Actually, I've tracked the problem down to a couple of the plugins - blur & reflection I think but will experiment when I have a bit more time.

Thanks again,

j.

---

### Post by findsun on 2006-08-16
guys, seems that chmod +s /usr/bin/compiz* could help to improve the performance. Seems that in normal user mode, libGL can not open DRM kernel module.

---

### Post by MattW on 2006-08-16
Blur I gather is rather slow at times... perhaps not utilising all the hardware tricks it could be using (and that perhaps Vista's blur is taking advantage of - there's a reason they're so keen on DX9-capable cards).

Anyway, I finally got my compiz+AIGLX working again. compiz-start, it turns out, is provided by the compiz-aiglx package, which had disappeared from somewhere, or was possibly new and the result of a repackaging. Whatever it was, things are working now, and I've even got it to do a cute little wobble when a window gains focus.

Shame the shortcut keys appear to be working highly abnormally, but I'll figure that out.

---

### Post by MattW on 2006-08-16
> **findsun said:**
> guys, seems that chmod +s /usr/bin/compiz* could help to improve the performance. Seems that in normal user mode, libGL can not open DRM kernel module.

Is your Xorg set up to allow normal users to access DRI? In /etc/X11/xorg.conf:

```

Section "DRI"
        Mode    0666
EndSection

```

That'll allow any user to run programs that use hardware OpenGL if it's available. Well, it should anyway.

---

### Post by b3h0ld3r on 2006-08-16
Hi!

I installed aiglx+compiz and it worked fine. But after the first reboot somehow I'd lost direct rendering. (I am sure it was working after the completion of steps in the how-to.) That is the same symptom I experienced after installing xgl+compiz. That's why I tried aiglx.

I have a Compaq Evo n1020v with ATI Radeon IGP 340M.

Do you have any ideas?

Thx in advance

---

### Post by findsun on 2006-08-16
Oh, ft, the section in my xorg.conf was commented, maybe by upgrade process.
Thank you very much! :)

---

### Post by b3h0ld3r on 2006-08-16
> **b3h0ld3r said:**
> Hi!

I installed aiglx+compiz and it worked fine. But after the first reboot somehow I'd lost direct rendering. (I am sure it was working after the completion of steps in the how-to.) That is the same symptom I experienced after installing xgl+compiz. That's why I tried aiglx.

I have a Compaq Evo n1020v with ATI Radeon IGP 340M.

Do you have any ideas?

Thx in advance

Hi!

After googling, I found out that as root I get direct rendering but as normal user, nothing. The DRI section is OK in xorg.conf but does not help.

Still trying...

---

### Post by skroll on 2006-08-16
Well, with an i915GM, I've noticed that alot of things run faster with compiz and aiglx, but, resizing and scrolling are alot slower.  It's almost a toss up and what I want.  I would love to get the best of both worlds, however.

Has anyone that uses an i915GM graphics card managed to overcome the slow text scrolling?  Particularly it happens in Firefox and OpenOffice.  Also, OpenOffice redraws all it's buttons noticably slower.

---

### Post by damagedspline on 2006-08-17
> **b3h0ld3r said:**
> Hi!

After googling, I found out that as root I get direct rendering but as normal user, nothing. The DRI section is OK in xorg.conf but does not help.

Still trying...

i have the same "comcrap" laptop - it worked ok for me. may there's something bad in another place in the xorg file:

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
	Load	"dri"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
	Driver		"ati"
	Option		"XAANoOffscreenPixmaps"
	Option          "AGPSize"               "32"
	Option  "TVOutput" "PAL"
        Option  "IgnoreEDID" "true"
	Option	"DRI"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Device"
        Identifier      "RADEON-TVOut"
        Driver  "ati"
        Option  "AGPMode" "4"
        Option  "AGPFastWrite" "yes"
        Option  "TVOutput" "PAL"
        Option  "IgnoreEDID" "true"
        Option "MonitorLayout" "NONE, CRT"   #here
 EndSection

 Section "Monitor"
        Identifier      "TV Monitor"
        HorizSync    30.0 - 40.0
        VertRefresh  60
        Modeline "800x600" 40.00 800 840 968 1056 600 601 605 628
 EndSection

 Section "Screen"
        Identifier      "TV Screen"
        Device          "RADEON-TVOut"
        Monitor         "TV Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           16
                Modes           "800x600"
        EndSubSection
 EndSection

Section "ServerLayout"
	Option		"AIGLX"	"Enable"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection
```

---

### Post by myha on 2006-08-17
Hi,

in todays upgrade I have noticed the change od font sizes, everything is a lot bigger than before... Has anyone else noticed that?

Also, the gnome-terminal has now real transparent background...  :)

---

### Post by b3h0ld3r on 2006-08-17
Thx for the idea. I copied your xorg.conf to my /etc/X11, restarted X but it is all the same.

Again, after some hours I found an interesting thing: As root DRI works, glxgears works fine too but only if I start a login shell with "su -". With the pure "su" root user gets no DRI, exactly like a normal user.

Which environment variables may play here important role?

Xorg-air runs with root privileges, Xgl with normal user privileges.
"lsof | grep dri" says:

```
Xorg-air  8535       root  mem       CHR      226,0               11087 /dev/dri/card0
Xorg-air  8535       root  mem       REG        3,6  2155504      67004 /usr/lib/dri/radeon_dri.so
Xorg-air  8535       root  mem       REG        3,6   312152     261812 /usr/lib/xorg/modules/drivers/radeon_drv.so
Xorg-air  8535       root  mem       REG        3,6    52344     263480 /usr/lib/xorg/modules/drivers/ati_drv.so
Xorg-air  8535       root  mem       REG        3,6    34210     520921 /usr/lib/xorg-air/modules/extensions/libdri.so
Xorg-air  8535       root    8u      CHR      226,0               11087 /dev/dri/card0
Xorg-air  8535       root    9u      CHR      226,0               11087 /dev/dri/card0
Xgl       8604       root  mem       CHR      226,0               11087 /dev/dri/card0
Xgl       8604       root  mem       REG        3,6  2155504      67004 /usr/lib/dri/radeon_dri.so
Xgl       8604       root    1u      CHR      226,0               11087 /dev/dri/card0

```

Slowly getting crazy...

---

### Post by b3h0ld3r on 2006-08-17
Sorry, in the code in the post above I changed Xgl attributes (setuid root) but nothing has changed...

---

### Post by WishMaster on 2006-08-17
So I need DRI-modules for xgl...
I also need kernel > 2.6.16 for my intel855GM card.

So I compiled 2.6.17.7.
According to [http://dri.sourceforge.net/doc/DRIcompile.html](http://dri.sourceforge.net/doc/DRIcompile.html) I need to enable some things in "make menuconfig"

> Configure your kernel. You might, for example, use make menuconfig and do the following:  [LIST]
[*]Go to *Code maturity level options*
[*]Enable *Prompt for development and/or incomplete code/drivers*
[*]hit ESC to return to the top-level menu
[*]Go to *Processor type and features*
[*]Select your processor type from *Processor Family*
[*]hit ESC to return to the top-level menu
[*]Go to *Character devices*
[*]Disable *Direct Rendering Manager (XFree86 DRI support)* since we'll use the DRI code from the XFree86/DRI tree and will compile it there.
[*]Go to */dev/agpgart (AGP Support) (EXPERIMENTAL) (NEW)*
[*]Hit SPACE twice to build AGP support into the kernel
[*]Enable all chipsets' support for AGP
[*]It's recommended that you turn on MTRRs under *Processor type and Features*, but not required.[/LIST] 
Configure the rest of the kernel as required for your system (i.e. Ethernet, SCSI, etc)
Did all of that. No dri-modules.... only the dri-modules from the standard Ubuntu kernel (2.6.15)

---

### Post by Milamber_Cubed on 2006-08-17
> **skroll said:**
> Well, with an i915GM, I've noticed that alot of things run faster with compiz and aiglx, but, resizing and scrolling are alot slower.  It's almost a toss up and what I want.  I would love to get the best of both worlds, however.

Has anyone that uses an i915GM graphics card managed to overcome the slow text scrolling?  Particularly it happens in Firefox and OpenOffice.  Also, OpenOffice redraws all it's buttons noticably slower.

I have the same problem with open office but scrolling seems to be okay for me. I did notice that after a certain point in time compiz got a great deal slower and managed to revert to a fast version of compiz and cgwd. I can post them somewhere if you want to try them. I have locked my versions in Synaptic and can live quite happily without the latest developments so long as things run smoothly.

---

### Post by skroll on 2006-08-17
> **Milamber_Cubed said:**
> I have the same problem with open office but scrolling seems to be okay for me. I did notice that after a certain point in time compiz got a great deal slower and managed to revert to a fast version of compiz and cgwd. I can post them somewhere if you want to try them. I have locked my versions in Synaptic and can live quite happily without the latest developments so long as things run smoothly.

Interesting.  Was your scrolling ever slow, or was it always quick for you?  What version of compiz in particular did you use?

---

### Post by Hotaru on 2006-08-17
I am using compiz and aiglx @ i915GM and everything's just fine. I have no problems scrolling both in Firefox and OpenOffice. I never had.
And after recent updates I have transparent terminal window and fonts seem to be smoother than I remember them :).

---

### Post by skroll on 2006-08-17
> **Hotaru said:**
> I am using compiz and aiglx @ i915GM and everything's just fine. I have no problems scrolling both in Firefox and OpenOffice. I never had.
And after recent updates I have transparent terminal window and fonts seem to be smoother than I remember them :).

What are the specs of your machine?  I'm running on a Dell Inspiron 6000, with a 1.6Ghz Pentium M and 512mb RAM.  Just curious on what you have going.  I really want to have the benefits of aiglx+compiz (I love how smooth the windows move, and the window organizer is awesome), but the text scrolling was sluggish.

---

### Post by Milamber_Cubed on 2006-08-18
> **skroll said:**
> Interesting.  Was your scrolling ever slow, or was it always quick for you?  What version of compiz in particular did you use?

I think that the scrolling was slow for me at some point but now is acceptable. Just to clarify, scrolling is not the problem in OpenOffice but rather the amount of time it takes to redraw a window. 

Here is a list of packages I have locked versions of:

cgwd_0.48_i386.deb       compiz_0.0.13-0quinn12_i386.deb
cgwd-themes_0.9_all.deb  compiz-gnome_0.0.13-0quinn12_i386.deb


This leaves me with only the OpenOffice problem.

For the sake of completeness, I have a Dell Lattitude 110L with a Pentium M 1.7GHz processor and 512MB of RAM the following integrated graphics card:

VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

Actually, it just occured to me that the graphics card might be stealing it's RAM from the main memory. I am going to go into the BIOS and check it out now. Maybe increasing how much is given over the the graphics card will help compiz run more smoothly? Will report back soon!

---

### Post by Hotaru on 2006-08-18
> **skroll said:**
> What are the specs of your machine?  I'm running on a Dell Inspiron 6000, with a 1.6Ghz Pentium M and 512mb RAM.  Just curious on what you have going.  I really want to have the benefits of aiglx+compiz (I love how smooth the windows move, and the window organizer is awesome), but the text scrolling was sluggish.

HP Pavilion dv4152ea: Centrino, CPU 1.7 GHz, 1024 MB RAM.
Not that different really...

---

### Post by skroll on 2006-08-18
> **Hotaru said:**
> HP Pavilion dv4152ea: Centrino, CPU 1.7 GHz, 1024 MB RAM.
Not that different really...

Yes, doesn't really make sense.  Last question then, did you install the vanilla or quinn packages?  I installed the vanilla ones, not sure if this should have an effect or not.

---

### Post by Milamber_Cubed on 2006-08-18
> **skroll said:**
> Yes, doesn't really make sense.  Last question then, did you install the vanilla or quinn packages?  I installed the vanilla ones, not sure if this should have an effect or not.

I think that the 1GB of RAM might make all the difference. I read a page on the Dell site that talks about the intel graphics controllers having a maximum shared memory size - allocated dynamically by the way - dependant on the total memory installed. With 512MB of ram the max share size is 64MB and with 1GB the maximum is 128MB. Maybe us poor 512-ers are just running out of texture memory?

---

### Post by RajivNair on 2006-08-19
Hello everyone,
 My sys specs are :-
     P IV 1.7 Ghz,512mb DDR,Intel 845GL(uses i810 driver) and 64 mb shared memory for graphics,i want to know as to which package to install,quinn or vanilla.

Thanks in Advance,
Rajiv Nair

---

### Post by Hotaru on 2006-08-19
I used vanilla packages as well... just like the name better :).
I remeber hearing about the amount of video memory assigned dependant on total size of RAM. That mihgt be the case, actually... let me have a look.

...

According to this document: [http://download.intel.com/design/chipsets/applnots/30262305.pdf](http://download.intel.com/design/chipsets/applnots/30262305.pdf)
128MB can be assigned when having 512 MB of RAM... hmm....

---

### Post by BCCZeus on 2006-08-19
Hey there.  I'm relatively new to Ubuntu and I've played around with Linux some in the past.  I've installed the Compiz+AIGLX packages on 6.06 and have got it working - sort of.

All my wobbly, cube and everything works, but I have to start compiz manually - which I don't mind.

The thing is I don't have a compiz-aiglx start file.  All I have is compiz-start script in my /usr/bin/

I'm assuming that I'm not running compiz-aiglx if I don't have that compiz-aiglx-start script?  Is this true or am I not running aiglx at all?

Any help would be appreciated - I'm running an Aspire TravelMate 2428AWXMi with Intel i915 graphics with a Pentium M 745 processor and 1GB of DDR2.

Thanks in advance.

---

### Post by ButteBlues on 2006-08-19
I followed the instructions, but whenever I try to sign into a Gnome Session, Nautilus loads and X crashes.

I installed Compiz-vanilla and am using the default xorg ati drivers.

Running on a Compaq 1525 US with I think a Radeon Mobility M7 7500 (possibly 9000)?

---

### Post by skroll on 2006-08-19
> **Hotaru said:**
> I used vanilla packages as well... just like the name better :).
I remeber hearing about the amount of video memory assigned dependant on total size of RAM. That mihgt be the case, actually... let me have a look.

...

According to this document: [http://download.intel.com/design/chipsets/applnots/30262305.pdf](http://download.intel.com/design/chipsets/applnots/30262305.pdf)
128MB can be assigned when having 512 MB of RAM... hmm....

Well, I know it's not the prettiest (it's actually only a minor difference) but setting the X server to 16bit color increases performance **significantly**.

I really only want the really slick window arranger for the most part, but it works GREAT.  Also, desktop switching is way faster this way.

---

### Post by Hotaru on 2006-08-19
That would mean that memory really was a problem in your case. 
Can someone calculate the difference in memory needed in 16 vs 32 bit 3D desktop?

---

### Post by harissza on 2006-08-19
I just installed aiglx&compiz. Few notes: Allocated RAM didn't make any difference nor the colour depth change. The "quinn" version is absolutely useless on Inspiron 6000, opening a gnome-terminal took over a minute, couldn't move any window,cpu was hammered,shocking... Vanilla works like charm! I suggest to everybody who's having speed issues to try vanilla first. One thing I noticed that changing to any text console is ok but as soon as I try to change back to GUI the laptop freezes completely. It's fine, we can change back to metacity in no time and do these if necessary.

---

### Post by PathSpace on 2006-08-19
I have 2 quick questions about AIGLX/Compiz.

1.  What is the difference between vanilla and regular?  I tried the regular packages and they were WAY too slow; I am thinking about trying the vanilla to see if there is an improvement.

2.  Do I still need to install gset-compiz to install the vanilla set of packages?

UPDATE:  Omg; I just installed the vanilla set of packages, and performance is GREATLY improved!  :D

---

### Post by Hotaru on 2006-08-20
I was very lucky then to choose vanilla as my first option... I thought there was really no difference (performance-wise) between the two. Apparently, there is!

---

### Post by bflat on 2006-08-20
I hope not to be out of theme in this thread,

I managed to have compiz-vanilla, CGWD, with Dapper and an ati radeon 7000/ve, and following step by step some software-upgrades correcting bugs,
by the way compiz is not just a candy IMHO ...

recently I had some problem whith the djvulibre standalone app, DJvulibre 3.5.16) does not integrate well whith my compiz install, and need to switch to metacity, with compiz the window is completely translucent (ink is orange over one of the circulating orange wallpapers)

(I installed the whole set of packages not only the reader), see at:
[http://packages.ubuntulinux.org/dapper/source/djvulibre](http://packages.ubuntulinux.org/dapper/source/djvulibre)

plus (but this may be a totally different issue) I can't make the plugin being recognized from Firefox 1.5

minor issues, maybe interesting anyway since I don't see some of the kind being posted before,

someone maybe knows if the problems could be solved trying to install the packages for Edgy? (last version 3.5.17) 
or just sit down and wait a minute?

thank you

---

### Post by PathSpace on 2006-08-20
I don't know the answer to your questions, bflat, but would like to ask you one:  how did you install CGWD along with compiz-vanilla?  I thought vanilla did not support CGWD...

---

### Post by Uncle Spellbinder on 2006-08-20
If it's not been mentioned yet, Use: 

*deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx*
or
*deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main aiglx*
Or both.


DO NOT....I repeat... [color=#CC0000]**DO NOT**[/color] add **ubuntu.compiz.net** or **xgl.compiz.info** to your sources list. 

Or at least comment them out if you insist on adding them.


See here:  [**_Community Compiz+etc. Packages_**](http://www.beerorkid.com/compiz/)

---

### Post by PathSpace on 2006-08-20
Thanks for that, Uncle Spellbinder.  :) 

Will using those repositories allow me to use cgwd with vanilla?  EDIT:  No, it does not.  I still don't understand how bflat managed to install cgwd along with vanilla...

---

### Post by facejeans on 2006-08-20
Pathspace,  

I happened to have it installed because i used quinn's packages initially, only to realize the drastic change in performance...when i uninstalled quinn and changed to vanilla, i kept gset and cgwd.  THe thing is, CGWD is not "technically supported" by vanilla, but a quick command at the terminal allows you to use it: killall gnome-window-decorator & cgwd & exit.

As far as installing, i'm sure if you have the repos in your list, just hit sudo apt-get install cgwd and you should be all good...

---

### Post by PathSpace on 2006-08-20
Thanks a ton, facejeans.  :D

---

### Post by Hotaru on 2006-08-20
> **Uncle Spellbinder said:**
> If it's not been mentioned yet, Use: 

*deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx*
or
*deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main aiglx*
Or both.


DO NOT....I repeat... [color=#CC0000]**DO NOT**[/color] add **ubuntu.compiz.net** or **xgl.compiz.info** to your sources list. 

Or at least comment them out if you insist on adding them.


See here:  [**_Community Compiz+etc. Packages_**](http://www.beerorkid.com/compiz/)

Thanks! I got my window borders back. Worked fine for me... I guess that AIGLX still rulez ;P.

---

### Post by Uncle Spellbinder on 2006-08-21
***Repo update:***

It seems as the repos are back and "good to go"

See here: 
[_**xgl.compiz.info/ubuntu.compiz.net repos are back up**_](http://www.compiz.net/viewtopic.php?pid=27483#p27483) 
and 
[_**Community Compiz+etc. Packages**_](http://www.beerorkid.com/compiz/)

---

### Post by bflat on 2006-08-21
pathspace,facejeans
I installed compiz vanilla and vanilla-gnome packages, and afterwards CGWD, it worked ever since just starting CGWD from the command line

but why my gset-compiz menu-view reads (and checks): 
quinnstorm package?

---

### Post by myha on 2006-08-22
Hi,

today I tried to replace quinn with vanilla and now I can't get the window manager to work, when I try tu upgrade I get the following error:
```
root@laptop:mihap# apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  cgwd: Depends: compiz (>= 0.0.13-0quinn33) but it is not installed or
                 compiz-vanilla but it is not installed
  compiz-vanilla-aiglx: Depends: compiz-vanilla (>= 0.0.12) but it is not installed
                        Depends: compiz-vanilla-gnome (>= 0.0.12) but it is not installed
  gset-compiz: Depends: compiz but it is not installed or
                        compiz-vanilla but it is not installed or
                        compiz-aiglx (>= 0.0.8) but it is not installable
E: Unmet dependencies. Try using -f.
root@laptop:mihap# apt-get -f upgrade
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following NEW packages will be installed:
  compiz-vanilla compiz-vanilla-gnome
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/411kB of archives.
After unpacking 2314kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 115349 files and directories currently installed.)
Unpacking compiz-vanilla (from .../compiz-vanilla_0.0.13+cvs20060820_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-vanilla_0.0.13+cvs20060820_i386.deb (--unpack):
 trying to overwrite `/usr/bin/compiz', which is also in package compiz-core
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking compiz-vanilla-gnome (from .../compiz-vanilla-gnome_0.0.13+cvs20060820_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-vanilla-gnome_0.0.13+cvs20060820_i386.deb (--unpack):
 trying to overwrite `/usr/share/gconf/schemas/compiz.schemas', which is also in package compiz-plugins
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-vanilla_0.0.13+cvs20060820_i386.deb
 /var/cache/apt/archives/compiz-vanilla-gnome_0.0.13+cvs20060820_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@laptop:mihap#
```

Any ideas?

regards

---

### Post by myha on 2006-08-22
Hi,

it looks like the problem was that cgwd works only with quins packages...

So I somehow managed to remove vanilla packages, but now I cannot get the quins packages, have problem with compiz-quinn-aiglx:
```

root@laptop:mihap# apt-get install compiz-quinn-aiglx compiz compiz-gnome
Reading package lists... Done
Building dependency tree... Done
Package compiz-quinn-aiglx is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package compiz-quinn-aiglx has no installation candidate
root@laptop:mihap#
```

?

EDIT: Ok, I managed to get it working now - I changed repositories to:
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main aiglx
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main aiglx

And it works ok now.

Why use repositories described in the beginning then?

---

### Post by one_stinky_bum on 2006-08-22
Is the howto broken?
```
compiz:
 Depends: compiz but it is not going to be installed
  Depends: compiz-plugins (>=0.2) but 0.1-0ubuntu1 is to be installed or
 	compiz-plugins-quinn  but it is not installable

compiz-vanilla-aiglx:
 Depends: gset-compiz  but it is not installable

gcompizthemer-themes:
 Depends: gcompizthemer (>= 0.1 8 )

```
And during the install, I get:
```
E: /var/cache/apt/archives/compiz-vanilla_0.0.13+cvs20060822_i386.deb: trying to overwrite `/usr/bin/compiz', which is also in package compiz-core

```

---

### Post by gottferdamnt on 2006-08-22
SAME PROBLEME ! I really need some helps ! I can't install compiz packages...

---

### Post by spockrock on 2006-08-22
try
```
sudo apt-get install -f
```

---

### Post by PathSpace on 2006-08-22
You guys can get the gset-compiz package from here:

[http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/](http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/)

That will resolve at least one dependency.  :)

---

### Post by spockrock on 2006-08-22
ok if you guys are experiencing the same thing I am right now with the broken dependenicies, and compiz-plugins 0.2 being missing then this will restore you back to an earlier version, just wait for the fix.

```
sudo dpkg -i /var/cache/apt/archives/compiz-core_0.0.13.35-0ubuntu1_i386.deb 
sudo dpkg -i /var/cache/apt/archives/compiz_0.0.13.35-0ubuntu1_i386.deb
sudo dpkg -i /var/cache/apt/archives/compiz-plugins_0.1-0ubuntu1_i386.deb
sudo dpkg -i /var/cache/apt/archives/compiz-gnome_0.0.13.35-0ubuntu1_i386.deb
sudo dpkg -i /var/cache/apt/archives/cgwd_0.59_i386.deb
sudo dpkg -i /var/cache/apt/archives/cgwd-themes_0.11_all.deb
```

---

### Post by T8y8 on 2006-08-23
I got the same error, so I uninstalled all compiz packages and am waiting for the fix.

---

### Post by myha on 2006-08-23
> **PathSpace said:**
> You guys can get the gset-compiz package from here:
[http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/](http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/)
That will resolve at least one dependency.  :)
This helped me for gset-compiz, but compiz-quinn-aiglx was available only through diffrent repositories - read above.

Works fine now - exept I lost the use CGWD....  :(

Regards

---

### Post by routerstu on 2006-08-23
id really like to try this but it looks like the howto is outdated?  can someone please update this, please please please :)

---

### Post by myha on 2006-08-23
Howto is fine, I think that only the repos are not ok... You can try using the repos that are described in how-to and add the ones that I mentioned one page back...
Also, if you plan to use CGWD themer you have to use quinns packages because it doesnt work with vanilla.

regards,

---

### Post by BungaMan on 2006-08-23
What is going on with the latest updates?  I tried installing cgwd and it depends on compiz-vanilla but from the package you can read that cgwd should not be used with vanilla.

and the update broke my compiz too ([http://www.ubuntuforums.org/showthread.php?t=241998](http://www.ubuntuforums.org/showthread.php?t=241998))

---

### Post by foxy123 on 2006-08-23
I've just opened synaptic, did reinstall of 3 broken packages, got another error, click Apply again and got everything installed fine. Though I can not confirm it as I rushed out for work straight after that.

---

### Post by neok on 2006-08-23
Hi!

I have a problem with DRI modules for my ATi Radeon 9200 AGP.

My monitor goes to standby randomly and when it happens I can't do anything more than reboot, the XServe is blocked.

After that I look my X.org.log and it has this:

> (EE) RADEON(0): RADEONWaitForIdleCP: CP idle -1022
(EE) RADEON(0): Idle timed out, resetting engine...
(**) RADEON(0): EngineRestore (32/32) 

These three lines a lot of time.

Can somebody helps me? Now I have to switch to ATi propietary drivers.

Thanks!

---

### Post by one_stinky_bum on 2006-08-23
Everything works now - compiz is better than ever!

---

### Post by PathSpace on 2006-08-23
> **myha said:**
> 
Also, if you plan to use CGWD themer you have to use quinns packages because it doesnt work with vanilla.


That's not really true.  You can always install cgwd and cgwd-themes with your vanilla packages, and do the following at the beginning of each session:

Run (Alt+F2 if you use GNOME) the command:

killall gnome-window-decorator && cgwd

Then you will have cgwd in vanilla.  :grin:

---

### Post by StayPuft on 2006-08-23
So I've tried all of the following repositories:

deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper aiglx
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main aiglx
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main aiglx

and NONE of them work (EDIT: beerorkid works). When I run a sudo apt-get update they error out. Error message = ```
Err http://media.blutkind.org dapper Release.gpg
  Temporary failure resolving 'media.blutkind.org'
Err http://ubuntu.compiz.net dapper Release.gpg
  Could not connect to ubuntu.compiz.net:80 (195.14.0.203), connection timed out

```
and so forth for each repo.

Does anyone know of a reliable repo? The XGL repos always worked fine for me, why aren't the AIGLX repos as reliable? Thanks.

---

### Post by Uncle Spellbinder on 2006-08-23
Anyone had any luck getting to the Compiz Forums. Not only has it been impossible to access, It's no longer showing up in Google searches. Strange.

---

### Post by Uncle Spellbinder on 2006-08-23
Compiz Forums are back.

---

### Post by facejeans on 2006-08-24
I have seen more than a few people get cgwd to work with vanilla...look on previous posts...there's one command you need to do when you want to use cgwd, and it works with vanilla.  Really, just try it out (when the repos get fixed, :))

---

### Post by ayoli on 2006-08-24
wow, i had to do some work to make my compiz-quinn and cgwd working nice after last updates:
 - running twice apt-get install -f
 - removing ~/.cgwd to be able to apply themes
 - using a gset-compiz package from [http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/]("http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/") since it has been delete from other repos
 - modify my own theme since themer has change a bit
btw, it's quite normal pb that's unstable since compiz is still in early stages and packages are from community.
continue enjoy compiz, it's a great WM.
regards.

---

### Post by myha on 2006-08-24
Hi,

how did you apply themes? I don't have the use CGWD under right-click in the AIGLX icon anymore...

---

### Post by ayoli on 2006-08-24
i didn't lost it, but reffering to previous posts you might create a file named cgwd-start under your home dir to make it work.
regards.

---

### Post by myha on 2006-08-24
mihap@laptop ~ $ ll .cgwd-start
-rw-r--r-- 1 mihap root 0 2006-08-22 09:14 .cgwd-start

I have it already but it doesn't help.... It is an empty file....?
Can you post yours?

---

### Post by ayoli on 2006-08-24
it suposed to be an empty file, actually i don't have it, i've only got a ~/.cgwd dir.
since the start script search for .cgwd in home dir i suppose it can work with this dir, if you dont have it, create it:
```
mkdir ~/.cgwd
```
regards.

---

### Post by Jingo on 2006-08-24
I have been following the guide to install aiglx on my ibm t42 with radeon 7500.
I have the problems with the repos, and can't install the compiz-quinn-aiglx, and went for compiz-vanilla-aiglx. After installing gset-compiz from above post, and succesed.. so I thought!!

My Desktop doesn't render right, look at the screenshot attached!
What is wrong, what can I do?
Looks like it's only 1024 pixels width!?
What about my background image?

Any help appreciated.

---

### Post by myha on 2006-08-24
> **ayoli said:**
> it suposed to be an empty file, actually i don't have it, i've only got a ~/.cgwd dir.
since the start script search for .cgwd in home dir i suppose it can work with this dir, if you dont have it, create it:
```
mkdir ~/.cgwd
```
regards.

I have this file...

root@laptop:mihap# ls -la .cgwd
total 20
drwxr-xr-x  4 mihap root 4096 2006-08-24 17:36 .
drwxr-xr-x 83 mihap root 4096 2006-08-24 19:15 ..
-rw-r--r--  1 mihap root  257 2006-08-24 17:36 settings.ini
drwxr-xr-x  2 mihap root 4096 2006-08-24 17:36 theme
drwxr-xr-x  2 mihap root 4096 2006-08-24 15:37 themes
root@laptop:mihap#

but I still cannot use CGWD... I have the CGWD themer, I see all the themes but I cannot start it...  :(

I tried also cgwd --replace and it doesn't work also...

---

### Post by ayoli on 2006-08-24
> **myha said:**
> I have this file...

root@laptop:mihap# ls -la .cgwd
total 20
drwxr-xr-x  4 mihap root 4096 2006-08-24 17:36 .
drwxr-xr-x 83 mihap root 4096 2006-08-24 19:15 ..
-rw-r--r--  1 mihap root  257 2006-08-24 17:36 settings.ini
drwxr-xr-x  2 mihap root 4096 2006-08-24 17:36 theme
drwxr-xr-x  2 mihap root 4096 2006-08-24 15:37 themes
root@laptop:mihap#

but I still cannot use CGWD... I have the CGWD themer, I see all the themes but I cannot start it...  :(

I tried also cgwd --replace and it doesn't work also...
Is cgwd running ? (ps -A | grep cgwd). if yes look in your home dir if you got a .cgwd **_file_**, remove it then apply any theme you want. worked for me.
regards.

---

### Post by myha on 2006-08-24
No, it isn't running....
When I try to start it manually I get the following error:

```

root@laptop:mihap# free
             total       used       free     shared    buffers     cached
Mem:       1026400     603384     423016          0      16040     232704
-/+ buffers/cache:     354640     671760
Swap:       522068          0     522068
root@laptop:mihap# cgwd --replace
cgwd: Connection Error (No reply within specified time)
6079: arguments to dbus_connection_get_data() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 4628.
This is normally a bug in some application using the D-BUS library.
6079: arguments to dbus_connection_set_data() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 4592.
This is normally a bug in some application using the D-BUS library.

** ERROR **: Not enough memory to set up DBusConnection for use with GLib
aborting...
Aborted
root@laptop:mihap#

```

---

### Post by ayoli on 2006-08-24
first, why run cgwd as root ? second you may kill gnome-window-decorator before, ie: as user type :
killall gnome-window-decorator && cgwd
regards.

---

### Post by myha on 2006-08-25
> **ayoli said:**
> first, why run cgwd as root ? second you may kill gnome-window-decorator before, ie: as user type :
killall gnome-window-decorator && cgwd
regards.

God damn!!! ](*,) ](*,) 
Yes, you were right, had to run it as user which is ofcource logical since I am running display as user not root.....  :evil: 

Thank you very much!

Regards

---

### Post by Jingo on 2006-08-25
Anyone running aiglx on a radeon with a resolution > 1024 ?
Anyone having success on radeon 7500 or the like?

I am having problems, se my above post with screenshots.

---

### Post by Dunska on 2006-08-25
I just did a dist-upgrade and got some new compiz files and now the thing flies!  Cube rotation has lost all it's jerkyness and all animations are fast.  8)  I am using AIGLX with Quinn's Compiz and integrated i915 (i810) gfx.

---

### Post by myha on 2006-08-25
> **Dunska said:**
> I just did a dist-upgrade and got some new compiz files and now the thing flies!  Cube rotation has lost all it's jerkyness and all animations are fast.  8)  I am using AIGLX with Quinn's Compiz and integrated i915 (i810) gfx.
Hi, sam here - works perfectly now! :)  
i915 + quinn + aigl

Can someone tell me which plugin is the one that hides all the windows if you move your mouse to bottom-right?

Also, when I switch desktops it first zooms them out, then switches and then zooms back in... How could I disable that?

And few updates back the menu-opening was done from zooming from mouse cursor and back, and now it just "wobbles - jumps" in. I think that this is dine via the minimize plugin and "zoom created windows" should do what I want but it doesn't...

regards

---

### Post by mdwuznik on 2006-08-25
The plugin is showdesktop, set the active edge to BottomRight (or whatever else of preference.

---

### Post by myha on 2006-08-25
ok, thanks, found it. I don't have it under plugins, but I see it in the gconf-editor...

What about the dock plugin? Does that work for anyone?

---

### Post by ayoli on 2006-08-25
dunno about dock plugin, i use kxdocker (apt-get able from the quinnstorm repo : [http://www.beerorkid.com/compiz/pool/main/k/kxdocker/kxdocker_1.1.4a-0quinn1_i386.deb](http://www.beerorkid.com/compiz/pool/main/k/kxdocker/kxdocker_1.1.4a-0quinn1_i386.deb)) with is a great OSX like docker.
regards.

---

### Post by myha on 2006-08-25
It looks ok, but it is for KDE and it wants to install lots of KDE dependancies - which I don't like...

Is anything like this available for Gnome natively?

---

### Post by logus on 2006-08-25
Does anybody run into problem described [here]("http://ubuntuforums.org/showthread.php?p=1420566")? (latest mesa + aiglx + i915)

Problem seems to appear after dist-upgrading to mesa cvs20060824 yesterday: random x-server freezes, screensaver freezes, glxgears lead to error:
```
glxgears: intel_ioctl.c:62: intelEmitIrqLocked: Assertion `((*(int*)intel->driHwLock) & ~0x40000000U) == (0x80000000U|intel->hHWContext)' failed.
Aborted
```

I've got compiz-quinn-aiglx installed; graphics - i915.

---

### Post by ayoli on 2006-08-25
> **myha said:**
> It looks ok, but it is for KDE and it wants to install lots of KDE dependancies - which I don't like...

Is anything like this available for Gnome natively?

there is [cairo-dock (aka gnome-dock)]("http://macslow.thepimp.net/?p=61") but it is alpha and really experimental, i heard it sucks a lot of processor and/or memory and havan't all functions you could find in kxdocker.
regards.

---

### Post by foxy123 on 2006-08-25
I've got Xorg randomly crashing after a recent update so I had to switch to xfwm4. This is being discussed on the compiz forum and one of the explanation is that 810i driver and aiglx need to be upgraded after a recent mesa upgrade. So I am waiting...

---

### Post by StayPuft on 2006-08-25
oops, dual post, read below ;)

---

### Post by StayPuft on 2006-08-25
This is an FYI for users installing AIGLX.

**FLASH CAUSES FIREFOX TO TERMINATE**
If you are experiencing this, follow these steps:

In terminal type:
```
sudo gedit /usr/bin/firefox
```

A text editor will open.

after the lines that read:

```
#
# Contributor(s): 
#

```

insert these 2 lines:
```

XLIB_SKIP_ARGB_VISUALS=1 
export XLIB_SKIP_ARGB_VISUALS
```

And you now have Flash!

Thanks to _profox for the code!

---

### Post by mahalram on 2006-08-25
I had sleep working very well before I installed aiglx...
(Sony Vaio TR series, intel 810, 1280x768)
Now the laptop does not wake up UNLESS I switch to metacity.

This is not a big issue...All I have to do is right click on the gset-compiz icon on my panel and choose switch to metacity...but it would be nice if I dont have to do this....

Any ideas???

aiglx is cool. One feature I especially like is that when I move the mouse over to the right-top corner it shows all windows (in the desktop) - automatically scaled down in size to ensure that all windows can be seen. The nice thing is that I can start a presentation in full screen mode and still access other windows without leaving full screen mode.

Does anyone know which plugin is responsible for this behavior, and how I can control it (for example if I want this to happen if I take to mouse to any corner)?

---

### Post by myha on 2006-08-25
Hi,

I believe that the plugin you are talking about is scale.... expose like in xgl...

You should have the settings in the system - preferences - gset-compiz, then click plugins and select scale and modify it.

You can also access it through gconf-manager...  apps - compiz - plugins.

You can find all the plugins described more detailed here:
[https://help.ubuntu.com/community/CompositeManager/ConfiguringCompiz](https://help.ubuntu.com/community/CompositeManager/ConfiguringCompiz)

regards

---

### Post by myha on 2006-08-25
> Also, when I switch desktops it first zooms them out, then switches and then zooms back in... How could I disable that?

And few updates back the menu-opening was done from zooming from mouse cursor and back, and now it just "wobbles - jumps" in. I think that this is dine via the minimize plugin and "zoom created windows" should do what I want but it doesn't...
regards
Hi, managed to resolve the second issue - under minimize plugin the unknown window type has to be checked...

Anyone knows about the first one? And howto make ctrl+alt+down to display all the desktops lined-up?

---

### Post by facejeans on 2006-08-26
Hey all,

I'm wondering if anyone else has been having this problem...

I've had to reinstall my ubuntu, and thus am trying to reinstall aiglx/compiz.

I followed everything to the T (according to the howto on page 1) and installed vanilla using the beerorkid repos, and the one repo to get gset.

However, when i restart to get it to work, my Xserver fails totally, and i can't even get any kind of interface, it just lets me know that it will disable gdm, and then i'm stuck with a prompt.  Has anyone else had this problem, and if so, what's the deal?  Maybe the packages are screwed up for vanilla now too?

---

### Post by centraspike on 2006-08-26
> **facejeans said:**
> Hey all,

I'm wondering if anyone else has been having this problem...

I've had to reinstall my ubuntu, and thus am trying to reinstall aiglx/compiz.

I followed everything to the T (according to the howto on page 1) and installed vanilla using the beerorkid repos, and the one repo to get gset.

However, when i restart to get it to work, my Xserver fails totally, and i can't even get any kind of interface, it just lets me know that it will disable gdm, and then i'm stuck with a prompt.  Has anyone else had this problem, and if so, what's the deal?  Maybe the packages are screwed up for vanilla now too?

I've just tried this for the first time and have had the same problem. After checking the Xorg logs it looked like none of the drivers specified in xorg.conf could be loaded.
Thus, i checked the /usr/lib/xorg-air/modules/drivers and /usr/lib/xorg-air/modules/input from where the drivers would be loaded only to find that they didn't exist.
As a fix i tried creating soft links to the drivers and input directories in /usr/lib/xorg/modules.

```
$ sudo ln -s /usr/lib/xorg/modules/drivers /usr/lib/xorg-air/modules/drivers
$ sudo ln -s /usr/lib/xorg/modules/input /usr/lib/xorg-air/modules/input
```

This now allows gdm to start, but all is not quite right. I have no window decoration when using compiz and have to switch back to metacity to get them back.
Not sure what to do now.

---

### Post by yaddoshi on 2006-08-26
> **centraspike said:**
> This now allows gdm to start, but all is not quite right. I have no window decoration when using compiz and have to switch back to metacity to get them back.
Not sure what to do now.

[CENTER]:confused: :frown: :( [/CENTER]

I just updated linux-dri-modules-common and linux-dri-modules-2.6.15-26-686, and also xserver-xorg-air-core, and something else aiglx & compiz related (can't remember now) with Synaptic, and now I have the same problem.  Gonna try dropping the linux-dri-modules* back to their previous version and see if that helps anything.

It was working fine yesterday (although not entirely stable).

EDIT: dropping to an earlier of linux-dri-modules* depends on an earlier kernel, not recommended.

---

### Post by skroll on 2006-08-26
Well folks, this guide is now outdated and doesn't work.  There is a new method, and I'll post a quick (albeit dirty) rundown.  This method works for me, and it no longer depends on gset-compiz.

1. You need to install: cgwd, compiz, compiz-core, compiz-gnome, xserver-xorg-air-core, so:
```

sudo apt-get install cgwd compiz compiz-core compiz-gnome xserver-xorg-air-core

```

Now, however, your modules will not be set up right, so you need to fix this.  When I first restarted, I found out that it couldn't load any modules, and I had the same idea **centraspike** did, and tried to:

```

$ sudo ln -s /usr/lib/xorg/modules/drivers /usr/lib/xorg-air/modules/drivers
$ sudo ln -s /usr/lib/xorg/modules/input /usr/lib/xorg-air/modules/input

```

But this didn't work (error reported it was too many levels linking), so I just copied all the modules from xorg to xorg-air.

Everything else about setting up gdm and the xorg.conf is the exact same though.

An important note: gset-compiz is **GONE** so don't bother installing it, because its discontinued.  You now use gconf-editor to do this, browse to apps/compiz/plugins in gconf-editor to change your settings.

I found that this new install was by far the fastest and most stable for me, and I run on a i915GM video card.  I guess I can work on a proper new HOWTO and post it in a bit.

---

### Post by 4eVaH on 2006-08-26
> **skroll said:**
> 
An important note: gset-compiz is **GONE** so don't bother installing it, because its discontinued.  You now use gconf-editor to do this, browse to apps/compiz/plugins in gconf-editor to change your settings.
.

This is not true, gset-compiz have been replaced by gnome-compiz-manager

```
sudo apt-get install gnome-compiz-manager
```

---

### Post by kdexglpsycho on 2006-08-26
does anyone else find it strange that this topic has not been made sticky thus allowing users with all flavors/hardware to find a solution in the same place?

---

### Post by skroll on 2006-08-26
> **4eVaH said:**
> This is not true, gset-compiz have been replaced by gnome-compiz-manager

```
sudo apt-get install gnome-compiz-manager
```

But you still need to use gconf-editor to fine tune your settings.

---

### Post by yaddoshi on 2006-08-26
> An important note: gset-compiz is **GONE** so don't bother installing it, because its discontinued.  You now use gconf-editor to do this, browse to apps/compiz/plugins in gconf-editor to change your settings.

I did a sudo aptitude remove gset-compiz, which also removed compiz-vanilla.  Then I did a search for compiz in Synaptic to see what was installed.  Apparently cgwd, compiz and compiz-core were no longer installed for some reason.  I tried to reinstall compiz-vanilla-aiglx but it told me it depended upon gset-compiz, which as was pointed out, is no longer available.  Also, compiz-quinn-aiglx was listed, but not compiz-quinn-gnome, so that was not an option.  I did go ahead and install cgwd, compiz, compiz-core and compiz-gnome, in addition to gnome-compiz-manager (which then magically updated from 0.2.0 to 0.2.1 within a minute of my installing it).  

On restart, I have compiz with windows borders once more.  Unfortunately I can't seem to get the water effects to work, and I haven't tested everything else out yet.  I need some clearer documentation on using gconf-editor, because it's not exactly 100% intuitive.  I also removed the compiz-start listing from my Sessions, as it seems to no longer be useful.

What does look neat and also is provoking me to research more is the optional customized window manager feature that pops up in gnome-compiz-manager's Preferences window.

:biggrin:

---

### Post by lozenge on 2006-08-26
```
james@monkey:~$ sudo apt-get install compiz-vanilla-aiglx compiz-vanilla compiz-vanilla-gnome
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz-vanilla-aiglx: Depends: gset-compiz but it is not installable
E: Broken packages
```

gset-compiz won't install no matter what I do. Any ideas?

---

### Post by yaddoshi on 2006-08-26
> **lozenge said:**
> gset-compiz won't install no matter what I do. Any ideas?

gset-compiz is gone (but not forgotten).  As skroll says, you are now relegated to using gconf-editor instead (you can add it to your menu by right-clicking on Applications, select "Edit Menus" which will open Alacarte Menu Editor, then click on System Tools and put a check mark next to Configuration Editor"), and while in gconf-editor select Applications>Compiz>Plugins to make configuration changes.

To install compiz today, you will have to do the following:
```
sudo apt-get install cgwd compiz compiz-core compiz-gnome xserver-xorg-air-core gnome-compiz-manager
```

Unfortunately until things get updated compiz-vanilla-aiglx is just unavailable for the time being.  The gnome-compiz-manager will show up as an icon on your taskbar, you can right-click on it and select Preferences for some configuration options also.

Good luck!

---

### Post by lozenge on 2006-08-26
Thanks for that... I've installed everything you said, however when I right click the tray icon and click preferences, nothing comes up.

Any idea about that?

Thanks.

Edit: got it working but I've no idea how to apply themes, half the time when I turn on the "GL Desktop" it just craps itself and all titlebars disappear and such.

---

### Post by suoko on 2006-08-27
Hi,

I'm trying to have aiglx working with my ati 9250 following this thread instrauctions but I can't run aiglx.

Normal Xorg works correctly with DRI enabled while modified gdm (with aiglx enabled) crashes at start.

I'm attaching both the xorg config file and the log.

Has anybody a clue of this problem?

thanks

---

### Post by Meck1982 on 2006-08-27
Hi, as described earlier in this thread aiglx works well on my Acer Travelmate 800 (Radeon Mobility 9000, 64MB) with the radeon driver and 16 bpp mode at 1280x1024.

I am now using the vanilla packages and the following repositories:

deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main aiglx
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main aiglx

# for the missing gset-compiz
deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper 3v1n0
deb-src [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper 3v1n0

My card has 64 MB vram and my device section in xorg.conf looks like:

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        Option          "AGPMode" "8"
        Option          "AGPFastWrite" "on"
        Option          "XAANoOffscreenPixmaps" "on"
        Option          "ColorTiling"   "off"
        #Option         "AccelMethod" "EXA"
EndSection

My problem is when working in 24 bpp mode. Then KDE starts fine but alle windows have only white content. And everything except the window borders/titlebar and kmenu borders are white.

Any suggestions for this problem? With previous xorg versions I have been able to use compiz in 24 bpp mode, even if it was remarkably slower in scrolling than 16 bpp mode.

---

### Post by skroll on 2006-08-27
Like I mentioned before, gset-compiz and compiz-vanilla have gone the way of the dodo, look at my previous post here, it has instructions for this.

---

### Post by Corona on 2006-08-27
> **skroll said:**
> Well folks, this guide is now outdated and doesn't work.  There is a new method, and I'll post a quick (albeit dirty) rundown.  This method works for me, and it no longer depends on gset-compiz.

1. You need to install: cgwd, compiz, compiz-core, compiz-gnome, xserver-xorg-air-core, so:
```

sudo apt-get install cgwd compiz compiz-core compiz-gnome xserver-xorg-air-core

```

Now, however, your modules will not be set up right, so you need to fix this.  When I first restarted, I found out that it couldn't load any modules, and I had the same idea **centraspike** did, and tried to:

```

$ sudo ln -s /usr/lib/xorg/modules/drivers /usr/lib/xorg-air/modules/drivers
$ sudo ln -s /usr/lib/xorg/modules/input /usr/lib/xorg-air/modules/input

```

But this didn't work (error reported it was too many levels linking), so I just copied all the modules from xorg to xorg-air.

Everything else about setting up gdm and the xorg.conf is the exact same though.

An important note: gset-compiz is **GONE** so don't bother installing it, because its discontinued.  You now use gconf-editor to do this, browse to apps/compiz/plugins in gconf-editor to change your settings.

I found that this new install was by far the fastest and most stable for me, and I run on a i915GM video card.  I guess I can work on a proper new HOWTO and post it in a bit.

Could you explain how you copied the modules from xorg to xorg-air?

---

### Post by ouroboros1827 on 2006-08-27
I'm installing on a 945 chipset...

I ran all this:
sudo apt-get install cgwd compiz compiz-core compiz-gnome xserver-xorg-air-core
sudo mkdir /usr/lib/xorg-air/modules/drivers
sudo mkdir /usr/lib/xorg-air/modules/input
sudo cp /usr/lib/xorg/modules/drivers/* /usr/lib/xorg-air/modules/drivers/
sudo cp /usr/lib/xorg/modules/input/* /usr/lib/xorg-air/modules/input/
sudo shutdown -r now

And gdm starts up no problem, logs into gnome fine...but no compiz. Probably a easy fix but I've had so much trouble with xgl (runs fine on kororaa livecd but nowhere else...) that I decided to try aiglx an hour ago...lol

I'll post back if I sort this out myself..
*looking into it*

---

### Post by skroll on 2006-08-27
> **ouroboros1827 said:**
> I'm installing on a 945 chipset...

I ran all this:
sudo apt-get install cgwd compiz compiz-core compiz-gnome xserver-xorg-air-core
sudo mkdir /usr/lib/xorg-air/modules/drivers
sudo mkdir /usr/lib/xorg-air/modules/input
sudo cp /usr/lib/xorg/modules/drivers/* /usr/lib/xorg-air/modules/drivers/
sudo cp /usr/lib/xorg/modules/input/* /usr/lib/xorg-air/modules/input/
sudo shutdown -r now

And gdm starts up no problem, logs into gnome fine...but no compiz. Probably a easy fix but I've had so much trouble with xgl (runs fine on kororaa livecd but nowhere else...) that I decided to try aiglx an hour ago...lol

I'll post back if I sort this out myself..
*looking into it*

Do you at least get the tray icon in the upper right?

---

### Post by skroll on 2006-08-27
> **Corona said:**
> Could you explain how you copied the modules from xorg to xorg-air?

sudo mkdir /usr/lib/xorg-air/modules/drivers
sudo mkdir /usr/lib/xorg-air/modules/input
sudo cp /usr/lib/xorg/modules/drivers/* /usr/lib/xorg-air/modules/drivers/
sudo cp /usr/lib/xorg/modules/input/* /usr/lib/xorg-air/modules/input/

---

### Post by ButteBlues on 2006-08-27
skroll - Those last instructions have made my DAY!

For the first time in 3-4 Dapper installs and many attempts with Compiz, it runs on my laptop!

Thank you so much!


My only issue is, I could never get my resolution below 1400x1050, so my desktop is currently whited out. But really, I'd rather get that working than lose compiz again.

Thank you! ^_^

---

### Post by jcrnan on 2006-08-27
soo.. I tried the apt-get update and it gives me this:

W: GPG error: [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
W: You may want to run apt-get update to correct these problems


btw: yes, Im rather new to both the forum and linux ;)

---

### Post by ButteBlues on 2006-08-28
JC - Run this:

$ wget [http://xgl.compiz.info/quinn.key.asc](http://xgl.compiz.info/quinn.key.asc) -O - | sudo apt-key add -

That should hopefully resolve it.


---=====----

IMPORTANT FIX FOR ATI USERS WANTING TO RUN COMPIZ IN >1024 resolution!

```
sudo gedit /etc/drirc
```

Paste into the file:

> <driconf>
    <device screen="0" driver="radeon">
        <application name="all">
            <option name="allow_large_textures" value="2" />
        </application>
    </device>
</driconf>

Replace "radeon" with the name of your respective driver.

This allows me to run AIGLX+Compiz smoothly on 1400x1050. :)

---

### Post by raggit on 2006-08-28
Trying to run 
```
mark@mark-laptop:~$ sudo apt-get install compiz-quinn-aiglx compiz compiz-gnome

```

and im greeted with 
```
Reading package lists... Done
Building dependency tree... Done
Package compiz-quinn-aiglx is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package compiz-quinn-aiglx has no installation candidate

```

What am i mising here?  I would prefer to use the quinn packages.

---

### Post by ButteBlues on 2006-08-28
> **raggit said:**
> Trying to run 
```
mark@mark-laptop:~$ sudo apt-get install compiz-quinn-aiglx compiz compiz-gnome

```

and im greeted with 
```
Reading package lists... Done
Building dependency tree... Done
Package compiz-quinn-aiglx is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package compiz-quinn-aiglx has no installation candidate

```

What am i mising here?  I would prefer to use the quinn packages.
Read this post: [http://ubuntuforums.org/showpost.php?p=1425898&postcount=1311](http://ubuntuforums.org/showpost.php?p=1425898&postcount=1311)

They ARE the quinn packages, IIRC. Same repo. New name.

---

### Post by gandalfn on 2006-08-28
hi,

first page updated !

- compiz-quinn-aiglx and compiz-vanilla-aiglx are now deprecated, [Gnome compiz manager]("http://gandalfn.wordpress.com/gnome-compiz-manager/") replace them !
- a new howto is added, compiz aiglx on edgy :)

have fun !

---

### Post by Uncle Spellbinder on 2006-08-28
*compiz-quinn-aiglx* is no longer available.  I've saved the .deb. Download it here if you'd like:

[*_compiz-quinn-aiglx_0.0.13-0ubuntu5_i386.deb_*](http://www.box.net/public/qrbndb80qn)

---

### Post by raggit on 2006-08-28
*update for me

I've gone through the steps, and now currently see a red box with a white x and - on it.  If i right click on it, i can see where it says gl desktop.  Is that how I turn on COMPIZ>??  Or should compiz allready be running after that setup?

I know the last time i clicked on that GL Desktop....My machine would never start X so im a tad hesitant to do that before some guidance.  Also the lsat time i had compiz running i had an option metacity, where now i do not.

Thanks guys

---

### Post by jtsai256 on 2006-08-28
Thanks for the update! Everything works smoothly for me.

To the poster above, you activate it by clicking on the GL Desktop checkbox.

---

### Post by raggit on 2006-08-28
Unfortunately,  I clicked on the GL Desktop and now my xserver continually reboots.  Example:  When i log in, I can see the desktop and everything for about 1 second "if that" then it sends me back to the login screen wanting username. And that goes on as many times as I log in. so now how do i tell it to not use the GL Desktop so I can atleast use that machine?
Any ideas?


SOLVED ! ! 

Problem was that in my gdm.conf i had commented out the SERVERS info and went back to standard.  I had neglected to put in the aiglx server info prior to clicking the GL DESKTOP

---

### Post by facejeans on 2006-08-28
I installed the "quinn version" according to the blog for intalling aiglx that was linked on page 1.  but after restarting i get a failure to launch because i'm missing xorg-air?  it said the command wasn't found, and then disabled X.  How do i get that? is it not included in the packages that install with gnome-compiz-manager or whatever?

---

### Post by Uncle Spellbinder on 2006-08-28
> **facejeans said:**
> I installed the "quinn version" according to the blog for intalling aiglx that was linked on page 1.  but after restarting i get a failure to launch because i'm missing xorg-air?  it said the command wasn't found, and then disabled X.  How do i get that? is it not included in the packages that install with gnome-compiz-manager or whatever?


 xorg-air is in the repos for me.

> 
DESCRIPTION:
**X server with accelerated indirect 3D support**
The X.Org X server is an X server for several architectures and operating
systems, which is derived from the XFree86 4.x series of X servers. This
package contains support for accelerated indirect 3D, allowing clients
that cannot directly access the hardware (such as those running on remote
machines, or rendering through compositing managers) to take advantage of
hardware acceleration.

The X.Org server supports most modern graphics hardware from most vendors,
and supersedes all XFree86 X servers.

More information about X.Org can be found at:
<URL:http://xorg.freedesktop.org>
<URL:http://lists.freedesktop.org/mailman/listinfo/xorg>


---

### Post by mardukdennis on 2006-08-28
I have just installed the new Packages and now the Windowborders dont work.
Before that, everything went fine. I have used the vanilla Packages. When i start compiz in the terminal i get this error:

> compiz --replace
libGL warning: 3D driver claims to not support visual 0x5b
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No manageable screens found on display :0.0

I have an intel card:

> Section "Device"
        Identifier      "Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
        Driver          "i810"
        Option          "XAANoOffscreenPixmaps"
        BusID           "PCI:0:2:0"


---

### Post by ButteBlues on 2006-08-28
Did you also run gnome-window-decorator?

Have you tried using cgwd?

---

### Post by mardukdennis on 2006-08-28
cgwd was not installed, just installed it and now it works again, but the effects are slower now :(

---

### Post by jcrnan on 2006-08-28
okey.. Im somewhat confused.. Ive been reading around about compiz and xgl and its still rather confusing.. I got the compiz manager installed.. What exactly do I have to do to get it up and running properly? (I have a Intel 915 with 815 drivers)

I also got this message wich confused me a bit:

nan@THE-HOLY-LAPTOP:~$ glxinfo | grep rendering
i915 DRI driver expected DDX version 1-1.5.x but got version 1.4.1
libGL warning: 3D driver returned no fbconfigs.
libGL error: InitDriver failed
libGL error: reverting to (slow) indirect rendering
direct rendering: No
nan@THE-HOLY-LAPTOP:~$

---

### Post by Jingo on 2006-08-28
> **a simple façade said:**
> 
---=====----

IMPORTANT FIX FOR ATI USERS WANTING TO RUN COMPIZ IN >1024 resolution!



Thank you... solved it for me.
I already had it in ~/.drirc, but copying it to /etc/drirc solved it!

Finally aiglx on my Radeon 7500 ! At both 1280x1024 and 1440x1050 ;)

---

### Post by sierranovember on 2006-08-28
**Corona**'s post (see below) is a much better description of what was happening to me, except when I restarted the X server, there were no titlebars and *cgwd --replace* hung in the terminal.

---

### Post by StayPuft on 2006-08-28
Random question, I have noticed that since I have installed AIGLX on my Gnome system I can no longer run KDE apps. (I really like using Katapult). Is there a way to restore KDE apps functionality while in Gnome AIGLX? Or possibly just a Gnome substitute for Katapult? Thanks.

---

### Post by ButteBlues on 2006-08-28
This sounds like a corrupted lib to me.

Amarok, Kopete, et al run seemlessly inside my Compiz-Gnome.

---

### Post by Corona on 2006-08-28
> **gandalfn said:**
> hi,

first page updated !

- compiz-quinn-aiglx and compiz-vanilla-aiglx are now deprecated, [Gnome compiz manager]("http://gandalfn.wordpress.com/gnome-compiz-manager/") replace them !
- a new howto is added, compiz aiglx on edgy :)

have fun !

I have followed your guide to the 't' on a fresh install. I get the following error on boot 'xserver cannot start' or something to that effect. Then I get this error: Please install the xserver or reconfigure your gdm. I can then edit the gdm.conf-custom file and then I can boot normally. Any ideas??

---

### Post by zephyros on 2006-08-29
I'm experiencing the same problem as Corona. For some reason, xserver-xorg-air-core was not pulled in as a dependency when updating from the compiz repository. 

I installed this package, but whenever I try to start a gdm or x-session, I receive errors complaining about missing modules and drivers. ](*,)

---

### Post by 4eVaH on 2006-08-29
I have this graphics problem while running glxgears and another 3d apps

It's like aiglx doesn't work with 3d apps or something like that because it draw 3d gears with a lot of graphical errors

I'll hope you can understand my problem with this screenshot and tell my what is this problem, why i have that and how to solve it.[[img]http://img245.imageshack.us/img245/7659/pantallazopf7.th.png[/img]](http://img245.imageshack.us/my.php?image=pantallazopf7.png)
thanks everybody.

Sorry about my bad english.

---

### Post by Corona on 2006-08-29
UPDATE

I finally got it going and this is what I did:

1. I followed this guide - 

[http://www.ubuntuforums.org/showthread.php?t=244559&highlight=aiglx+modules]("http://www.ubuntuforums.org/showthread.php?t=244559&highlight=aiglx+modules")

2. I added this at the end -

sudo mkdir /usr/lib/xorg-air/modules/drivers
sudo mkdir /usr/lib/xorg-air/modules/input
sudo cp /usr/lib/xorg/modules/drivers/* /usr/lib/xorg-air/modules/drivers/
sudo cp /usr/lib/xorg/modules/input/* /usr/lib/xorg-air/modules/input/

Thank You - Skroll.

---

### Post by jcrnan on 2006-08-29
I got it all working last night :D Im so happy ^^

It was a bit buggy at first but after a restart and some small meddling it seems to work fine. :)

---

### Post by Rmorris84 on 2006-08-29
How current is this guide? Can someone give me a little insight on the steps I should be taking on a Intel i810. Ive read that Intel has better support with aiglx and compiz... Ive fiddled with this a little bit and like a few other people i end up with windows with no sourrounds (topbar, min, max, close) and I kinda just reverted everything until I could find a guide that I knew was up to date, or if someone has had some experience with Intel on the i810 driver then shoot me some help my way... :-D Id love to get this working. 

RMorris

---

### Post by myha on 2006-08-29
Does anyone have the gset-compiz deb? I like it more than gnome-compiz... Where could I find it? Any ideas...  ?

---

### Post by jcrnan on 2006-08-29
Rmorris: Have you gotten compiz manager installed? After that you have to edit the xorg.config and gdm.config-custom properly to make it work. You just have to edit it very carefully and be sure to make backups of both those files first. If you edit any of them wrong your gnome wont work properly or in worst case (and rather likley) not even start.


Rember to get the compiz manager running before editing ANY files. If you get it installed you can also restart your pc to be sure it gets up and running properly before you start editing files.



In the terminal you write you need to do this:

sudo gedit /etc/X11/xorg.conf

This will open your xorg.conf file. First you find the Section "module" area.

That paragraph have to look EXACTLY like this:

Section	 "Module" 
	# Load	"GLcore" 
	Load	"bitmap" 
	Load	"ddc" 
	Load	"dbe" 
	Load	"dri" 
	Load	"extmod" 
	Load	"freetype" 
	Load	"glx" 
	Load	"int10" 
	Load	"type1" 
	Load	"vbe" 
EndSection

And I mean EXCACTLY! Very very important that there isnt a slightest difference. And be careful to not edit anything else.

Then you find the Section "Device" Area and make sure it looks like this: 

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Then you find the DeafultDepth setting and set it to 16 as that is more stable with this driver.


Then you scroll a bit down and find the section "ServerLayout". That have to look like this:

Section "ServerLayout"
	Identifier	"Default Layout"
	Option		"AIGLX" "true"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Remember to do it properly.

And the end of file it should look like this:

Section "DRI"
	Mode	0666
EndSection

Section "Extensions" 
Option "Composite" "Enable" 
EndSection

Then you save it and close it.

Then you go back to terminal. Write: sudo gedit /etc/gdm/gdm.conf-custom

A window opens and you scroll down to the bottom setting. it should look like this:

[servers] 
0=aiglx 
 
[server-aiglx] 
name=aiglx server 
command=/usr/bin/Xorg-air :0 
flexible=true


Now save and close.

Now you restart your pc and hope for the best. When it starts if everything is well you log into gnome and you should see a red box in system tray. Right click it and check of GL Desktop. Now it "should" be working :)

---

### Post by devilsadvocate1987 on 2006-08-29
I did that (from the previous post) and whenever I turn on the GL Desktop my windows dont move at all andmore, and the close and resize buttons are gone. 

I'm using the i915 chipset though ... do i have to change anything for that?

gdm looks the same as usual

---

### Post by jonibo on 2006-08-29
I get "module does not exist" when I try to start Xorg-air with xorg configured to use the "radeon" driver.  Any ideas?

I ran ldm-setup, but modprobe -l does not show any of the dri modules... not sure if it should.

---

### Post by Milamber_Cubed on 2006-08-29
> **devilsadvocate1987 said:**
> I did that (from the previous post) and whenever I turn on the GL Desktop my windows dont move at all andmore, and the close and resize buttons are gone. 

I'm using the i915 chipset though ... do i have to change anything for that?

gdm looks the same as usual

I am using the i915 chipset as well and all is working fine for me. It's possible that the problems you are having are with cgwd only. Try holding Alt and then clicking on a window - you should be able to move it around and if compiz is doing its thing, the window should be wobbly.

---

### Post by ayoli on 2006-08-29
> **jonibo said:**
> I get "module does not exist" when I try to start Xorg-air with xorg configured to use the "radeon" driver.  Any ideas?

I ran ldm-setup, but modprobe -l does not show any of the dri modules... not sure if it should.
have you install the dri modules with this code (from original [howto]("http://gandalfn.wordpress.com/howto-compiz-aiglx-on-dapper/")):
```
sudo apt-get install linux-dri-modules-common linux-dri-modules-`uname -r`
```
do you have the xserver-xorg-driver-ati (1:6.6.0-0ubuntu1) installed also ?
regards.

---

### Post by ayoli on 2006-08-29
> **devilsadvocate1987 said:**
> I did that (from the previous post) and whenever I turn on the GL Desktop my windows dont move at all andmore, and the close and resize buttons are gone. 

I'm using the i915 chipset though ... do i have to change anything for that?

gdm looks the same as usual

do you have cgwd installed?
```
dpkg-query --list |grep cgwd
```
and, if yes, is it running ?
```
ps -A |grep cgwd
```
regards.

---

### Post by ayoli on 2006-08-29
> **myha said:**
> Does anyone have the gset-compiz deb? I like it more than gnome-compiz... Where could I find it? Any ideas...  ?

gset-compiz package is deprecated like compiz-quinn-aiglx and compiz-vanilla-aiglx Gnome Compiz Manager replace them according to the first post of this thread that has been updated, so fellow instructions from this [post]("http://www.ubuntuforums.org/showpost.php?p=828007&postcount=1")
to remove old compiz-*-aiglx and install Gnome Compiz Manager.
regards.

---

### Post by Uncle Spellbinder on 2006-08-29
> **ayoli said:**
> gset-compiz package is deprecated like compiz-quinn-aiglx and compiz-vanilla-aiglx Gnome Compiz Manager replace them according to the first post of this thread that has been updated, so fellow instructions from this [post]("http://www.ubuntuforums.org/showpost.php?p=828007&postcount=1")
to remove old compiz-*-aiglx and install Gnome Compiz Manager.
regards.

Yep. I did that and all is working well. This is  what is installed on my computer after updating and installing *Gnome Compiz Manager*:

cgwd 0.65-0ubuntu1
cgwd-themes 0.15-0ubuntu1
compiz-core 0.0.13.41-0ubuntu1
compiz-plugins 0.7-0ubuntu1
gnome-compiz-manager 0.3.0-0gandalfn1
libcm7 0.0.16-0ubuntu2
libcm7-dev 0.0.16-0ubuntu2

---

### Post by vrode on 2006-08-29
I've followed this[0] howto down to the T [0]http://gandalfn.wordpress.com/howto-compiz-aiglx-on-dapper/

and now my ubuntu 6.06.1 is unable to boot into GUI and drops into console login stating "failed to start the X server...."

I'm using Thinkpad R52 w/ Intel graphic chipset,

"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
Driver "i810"
BusID "PCI:0:2:0"

Looking at my /var/log/gdm/:0.log, it shows the following,

(EE) Failed to load module "i810" (module does not exist, 0)
(EE) Failed to load module "kbd" (module does not exist, 0)
(EE) Failed to load module "mouse" (module does not exist, 0)
(EE) Failed to load module "wacom" (module does not exist, 0)
(EE) Failed to load module "synaptics" (module does not exist, 0)
(EE) No drivers available

Fatal server error:
no screens found

According to gandalfn how-to,

# sudo apt-get install gnome-compiz-manager compiz-vanilla \
compiz-vanilla-gnome

I don't remember below packages being installed. In fact, I had to manually install xserver-xorg-air-core.


cgwd 0.65-0ubuntu1
cgwd-themes 0.15-0ubuntu1
compiz-core 0.0.13.41-0ubuntu1
compiz-plugins 0.7-0ubuntu1
libcm7 0.0.16-0ubuntu2
libcm7-dev 0.0.16-0ubuntu2


Did I miss something?

Please advice.


regards,
/virendra

---

### Post by jcrnan on 2006-08-29
Anyone that followed the instructions I put up there and it didnt work I think I have a solution.. or rather, a simple facade has the solution, I just have to get a hold of him, I prolly will in the next few hours or so when he logs on. 

There is a file you create that should resolve that last little problem to get it working. Just be patient a bit longer ;)

---

### Post by vrode on 2006-08-29
That would be nice. 

Appreciate your help.


regards,
/virendra

---

### Post by ayoli on 2006-08-29
> **vrode said:**
> 

(EE) Failed to load module "i810" (module does not exist, 0)
(EE) Failed to load module "kbd" (module does not exist, 0)
(EE) Failed to load module "mouse" (module does not exist, 0)
(EE) Failed to load module "wacom" (module does not exist, 0)
(EE) Failed to load module "synaptics" (module does not exist, 0)
(EE) No drivers available



this suppose some drivers are missing. you also told you had to anually install xserver-xorg-air-core, did you also install xserver-xorg-driver-i810 ?
regards.

---

### Post by vrode on 2006-08-29
No I didn't? Do I?

I was going by the URL :(


regards,
/virendra

---

### Post by kraft2000 on 2006-08-29
has anyone managed to install AIGLX on a ATI mobility 9700  ???
and on the systems compatible both XGL and AIGLX, which one has better performances ??

---

### Post by vrode on 2006-08-29
It appears that my system already has the newest version of xserver-xorg-driver-i810.

Is there anything else I can look for?



regards,
/virendra

---

### Post by pepitogrillo37 on 2006-08-29
Does anybody know why the borders dissapear with the compiz-vanilla & compiz-vanilla-gnome? Is my favorite compiz option with my i915... 

Ah! By the moment you can use the compiz-quinn and works better than last release (at last for me) but stills slower than compiz-vanilla. 
For installing it: sudo apt-get install cgwd compiz compiz-core compiz-gnome

if you cannot install it 'cause you were using compiz-vanilla first execute sudo aptitude purge compiz-core compiz-plugins

If you are installing aiglx for the first time aiglx see [http://www.ubuntuforums.org/showthread.php?t=244559&highlight=aiglx+modules](http://www.ubuntuforums.org/showthread.php?t=244559&highlight=aiglx+modules).

This is my first post so I want to give thanks to gandalfn for all the post and his blog page. Many times I found the way to install aiglx in this thread! Thanks!

---

### Post by pepitogrillo37 on 2006-08-29
> **kraft2000 said:**
> has anyone managed to install AIGLX on a ATI mobility 9700  ???
and on the systems compatible both XGL and AIGLX, which one has better performances ??

Aiglx is better for this graphic card. I have tested with xgl and it was worse than aiglx. In general I recommend aiglx for ati and intels cards. Xgl works great with nvidia!

---

### Post by vrode on 2006-08-29
Yeah after searching through the forum for error messages (not being able to load the drivers), I came across the this site[0] and it appears to have fixed my problem. I'm now able to load my X w/ GL.

Doing so, now my borders have dissapeared? When I disable my GL Desktop the borders are restored?

Does anyone have any insight into this?

[0]http://www.ubuntuforums.org/showthread.php?t=244559&highlight=aiglx+modules

regards,
/virendra

---

### Post by ButteBlues on 2006-08-29
Virenda -

```
sudo aptitude install gnome-compiz-manager compiz compiz-core compiz-gnome compiz-plugins cgwd cgwd-themes
```

Then

```
sudo mkdir /usr/lib/xorg-air/modules/drivers
sudo mkdir /usr/lib/xorg-air/modules/input
sudo cp /usr/lib/xorg/modules/drivers/* /usr/lib/xorg-air/modules/drivers/
sudo cp /usr/lib/xorg/modules/input/* /usr/lib/xorg-air/modules/input/
```

Next

```
sudo gedit /etc/X11/xorg.conf
```

I have noticed that the XAANoPixMaps option will kill my gdm repetitively. Removing it solved this problem. If, in your devices section, you have this option, REMOVE IT! Make sure all else checks out, and save.

```
sudo gedit /etc/drirc
```

Paste in the following substituting the driver with your own driver:

> <driconf>
    <device screen="0" driver="radeon">
        <application name="all">
            <option name="allow_large_textures" value="2" />
        </application>
    </device>
</driconf>


That nifty fix will let you run Compiz on any resolution higher than 1024, afaik.

Then follow the edit of /etc/gdm/gdm.conf-custom as noted in the first post (or rather, as linked to in the first post).

Hopefully all of that OUGHT to help.

---

### Post by vrode on 2006-08-29
Thanks for the post. Couple quick questions.

sudo cp /usr/lib/xorg/modules/drivers/* /usr/lib/xorg-air/modules/drivers/
sudo cp /usr/lib/xorg/modules/input/* /usr/lib/xorg-air/modules/input/

Did fix my problem. See my previous post. Appreciate the pointer.


BTW, I currently have following packages loaded:

-> gnome-compiz-manager 
-> compiz-vanilla 
-> compiz-vanilla-gnome
-> linux-dri-modules-common
-> linux-dri-modules-2.6.15-26-386
-> xserver-xorg-air-core

But somehow skipped compiz-plugins, cgwd & cgwd-themes packages :(

Is is ok to load them even though my GL desktop is operational? Will it break anything?

Also I'm using Intel chipset so I don't think /etc/drirc entries would apply to me?

Do you know why would my borders dissapear when I enable GL Desktop? When disabled the borders are restored and I'm able to minimize and maximize my windows?


regards,
/virendra

---

### Post by ayoli on 2006-08-30
> **vrode said:**
> Thanks for the post. Couple quick questions.

Do you know why would my borders dissapear when I enable GL Desktop? When disabled the borders are restored and I'm able to minimize and maximize my windows?


because you don't have cgwd, install it (and two other missing packages) and run again your GL Desktop, it should work after that.
regards.

---

### Post by ButteBlues on 2006-08-30
> **vrode said:**
> Also I'm using Intel chipset so I don't think /etc/drirc entries would apply to me?

That drirc fix is for Intel and ATI users who want to use Compiz in a resolution higher than 1024x768,

---

### Post by Yerakon on 2006-08-30
> **vrode said:**
> (...) Do you know why would my borders dissapear when I enable GL Desktop? (...)
I have the same problem! also with cgwd installed...:???: 

I have tried with "DefaultDepth 16" in xorg.conf and seems better! borders NOT dissapear ;) 

Regards.;)

---

### Post by Balachmar on 2006-08-30
Hey, I just visited this thread again, and found out about the depricated quinn package. So I updated to the new stuff. But now I cannot find many of the settings. For instance I want less delay between the switching of the desktops... I mean the zooming out before the rotating takes too long for me.
Where can I find these settings now?

---

### Post by vrode on 2006-08-30
> **ayoli said:**
> because you don't have cgwd, install it (and two other missing packages) and run again your GL Desktop, it should work after that.
regards.


Hmmm...this is what I'm getting. Did I miss something?

vrode@promiscious:~$ sudo apt-get install compiz-plugins cgwd-themes

Reading package lists... Done
Building dependency tree... Done
cgwd-themes is already the newest version.
The following extra packages will be installed:
  compiz-core
The following NEW packages will be installed:
  compiz-core compiz-plugins
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/627kB of archives.
After unpacking 2936kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 76697 files and directories currently installed.)
Unpacking compiz-core (from .../compiz-core_0.0.13.41-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-core_0.0.13.41-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/bin/compiz.real', which is also in package compiz-vanilla
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking compiz-plugins (from .../compiz-plugins_0.7-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-plugins_0.7-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libresize.so', which is also in package compiz-vanilla
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-core_0.0.13.41-0ubuntu1_i386.deb
 /var/cache/apt/archives/compiz-plugins_0.7-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



regards,
/virendra

---

### Post by vrode on 2006-08-30
> **Yerakon said:**
> I have the same problem! also with cgwd installed...:???: 

I have tried with "DefaultDepth 16" in xorg.conf and seems better! borders NOT dissapear ;) 

Regards.;)


Yes this indeed fixed the problem but screen display is not that great :(


regards,
/virendra

---

### Post by pepitogrillo37 on 2006-08-30
> **Yerakon said:**
> I have the same problem! also with cgwd installed...:???: 

I have tried with "DefaultDepth 16" in xorg.conf and seems better! borders NOT dissapear ;) 

Regards.;)

WINDOWS-BORDER APPEARED!!

THANKS! It works again. There´s must be a bug but by the moment is a good solution.

:-D :-D :-D

---

### Post by ayoli on 2006-08-30
it works for me with DefaultDepth 24, howto also tells that it is supposed to work with this depth.

---

### Post by vrode on 2006-08-30
> **ayoli said:**
> it works for me with DefaultDepth 24, howto also tells that it is supposed to work with this depth.

which howto did you reference to?

may I need to uninstall and reinstall back.


regards,
/virendra

---

### Post by vrode on 2006-08-30
> **pepitogrillo37 said:**
> WINDOWS-BORDER APPEARED!!

THANKS! It works again. There´s must be a bug but by the moment is a good solution.

:-D :-D :-D

I'm sure it helps but my in my case going to certain websites automatically shuts my browser maybe because defaultdepth 16 is unable to handle the highres page.



regards,
/virendra

---

### Post by vrode on 2006-08-30
I uninstalled and reinstalled compiz and it works like a charm w/ 
DefaultDepth of 24.

I will try and put toghter what I did so that hopefully people could benefit.



regards,
/virendra

---

### Post by blackphiber on 2006-08-31
Anyone else having it lock up on them now and then?  Like I can move the mouse but it is totally locked up.  ctrl+alt+backspace does nothing and I cannot get to a terminal with ctrl+alt+f2
cat'ed thru various /var/log stuff and found nothing relevant.  I have to do a hard reset, really annoying..

---

### Post by ayoli on 2006-08-31
> **vrode said:**
> which howto did you reference to?



lol ! i use [gandalfn's howto]("http://gandalfn.wordpress.com/howto-compiz-aiglx-on-dapper/")

> **vrode said:**
> I uninstalled and reinstalled compiz and it works like a charm w/
DefaultDepth of 24.
cool :)

---

### Post by Yerakon on 2006-08-31
> **vrode said:**
> (...)I will try and put toghter what I did so that hopefully people could benefit.

Good idea! Thanks!:) 

(i have reinstalled but with "defaultdepth 24" i have still "no border":( )

Ciao.
Roberto

---

### Post by obi-nine on 2006-08-31
Hi folks,

I made the first cut at a updated guide for installing Compiz/Aiglx with Intel i915 chipsets.

If that's you, check it out...

[http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card](http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card)

---

### Post by Yerakon on 2006-08-31
> **obi-nine said:**
> Hi folks,(...)[http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card](http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card)

It works!  With gconf-editor and with some patience:rolleyes:  it is possible to obtain very good settings.  
Thanks. :D 

Regards.
Ciao
Roberto.

---

### Post by peterl on 2006-08-31
Hello!

I just managed to get xgl+compiz working on dapper amd64 with an nvidia 7600gs... words fail me when it comes to how good this looks.

but there's a problem. having followed [this]("http://ubuntuforums.org/showthread.php?t=133427") guide, my MS natural ergonomic 4000 usb keyboard has stopped working (in some respects). Namely, I can't use the numeric keypad. And yes, I've tried switching numlock off/on a few times. Also, caps lock doesn't work any more...

I don't know much about this kind of thing, but i've checked my xorg.conf and it's the same as before (when everything worked).

is annoying. help appreciated :)

thanks,
peter.

---

### Post by bdonkey on 2006-08-31
Upgrading to compiz-core, etc from compiz-quinn-aiglx, etc. broke all of compiz (no borders when switching to GL Desktop, no wobbly, nothing). No matter what I installed, I couldn't seem to get it working. Tweaks like Default Depth, strict binding, and other ones that I could find didn't work either.

After a fresh reinstall of Ubuntu, compiz-core works on the first try. There must be something left over from the old compiz packages that conflicts with the new ones...

---

### Post by peterl on 2006-08-31
> **peterl said:**
> Hello!

I just managed to get xgl+compiz working on dapper amd64 with an nvidia 7600gs... words fail me when it comes to how good this looks.

but there's a problem. having followed [this]("http://ubuntuforums.org/showthread.php?t=133427") guide, my MS natural ergonomic 4000 usb keyboard has stopped working (in some respects). Namely, I can't use the numeric keypad. And yes, I've tried switching numlock off/on a few times. Also, caps lock doesn't work any more...

I don't know much about this kind of thing, but i've checked my xorg.conf and it's the same as before (when everything worked).

is annoying. help appreciated :)

thanks,
peter.

ok. to answer my own question, i changed /etc/gdm/gdm.conf-custom to comment out the -kb at the end of the 'command' line, and that solved the problem.

---

### Post by pepitogrillo37 on 2006-08-31
> **vrode said:**
> I'm sure it helps but my in my case going to certain websites automatically shuts my browser maybe because defaultdepth 16 is unable to handle the highres page.



regards,
/virendra

There's no sense between your color path and the browser. There must be another reason. Anyway a 16 bit color range is not so bad. 2^16 is more than 64 thousends different colors. Much better are the 24 bits but I prefer to have my compiz-vanilla with borders. Anyway, a browser or any page would make a significally difference between the 16 and 24 bits.=;

---

### Post by pepitogrillo37 on 2006-08-31
> **ayoli said:**
> it works for me with DefaultDepth 24, howto also tells that it is supposed to work with this depth.

Hi! Please tell us how did you configure your compiz-vanilla? Are you using the new gnome-compiz-manager package? It should works for a 24 colorDepth but it doesn't by the moment. At least for me with my intel's 915 chipset and the last packages. Before upgrading all was ok (I mean I had the 24 bit). Although this continues being an inestable development and works really good!

Anyway as I said before a 16 bit range is no so bad.

---

### Post by ayoli on 2006-09-01
> **pepitogrillo37 said:**
> Hi! Please tell us how did you configure your compiz-vanilla? Are you using the new gnome-compiz-manager package? It should works for a 24 colorDepth but it doesn't by the moment. At least for me with my intel's 915 chipset and the last packages. Before upgrading all was ok (I mean I had the 24 bit). Although this continues being an inestable development and works really good!

Anyway as I said before a 16 bit range is no so bad.

i use the new gnome-compiz-manager, fellowing gandalfn howto and it works perfectly with DefaultDepth set to 24, no magical tweaks.
what's your version of xserver-xorg-air-core ? mine is:
```
[10:04:57@ayoli.zone]:~ >$ dpkg-query --list |grep xserver-xorg-air-core
ii  xserver-xorg-air-core                  1.1.1-0ubuntu2                          X server with accelerated indirect 3D support
```
from xgl.compiz.info repos.
regards.

---

### Post by pepitogrillo37 on 2006-09-01
> **ayoli said:**
> i use the new gnome-compiz-manager, fellowing gandalfn howto and it works perfectly with DefaultDepth set to 24, no magical tweaks.
what's your version of xserver-xorg-air-core ? mine is:
```
[10:04:57@ayoli.zone]:~ >$ dpkg-query --list |grep xserver-xorg-air-core
ii  xserver-xorg-air-core                  1.1.1-0ubuntu2                          X server with accelerated indirect 3D support
```
from xgl.compiz.info repos.
regards.

It's the same version. Are you using the compiz-vanilla or the compiz-quinn? With the second one all's ok, but the effects are slower in my i915! 

Thanks for the try.

---

### Post by ayoli on 2006-09-02
> **pepitogrillo37 said:**
> It's the same version. Are you using the compiz-vanilla or the compiz-quinn? With the second one all's ok, but the effects are slower in my i915! 

Thanks for the try.

compiz-quinn-aiglx and compiz-vanilla-aiglx are now deprecated, you have to use Gnome Compiz Manager instead.
first remove the one you use with 
```
sudo aptitude purge compiz-quinn-aiglx
```
then install new package:
```
sudo apt-get install gnome-compiz-manager
```
all this is explained in the first pot of this thread that was updated recently by gandalfn.
regaards.

---

### Post by banjobacon on 2006-09-02
So, I followed the guide and got compiz working, but after a day or two, the window decorations disappeared, though decorations are enabled. Other plugins, such as wobble and scale, work fine.

Any idea how I can fix this?

EDIT: Switching from vanilla to quinn seems to have fixed it.

---

### Post by Webspot on 2006-09-02
I followed the tutorial on the blog site. But now X doesn't start and it says Xorg-air doesn't exist!

I have a Radeon 9600 running on fglrx drivers so that I get dri.
Using Ubuntu Dapper

Please Help!

---

### Post by pepitogrillo37 on 2006-09-03
> **ayoli said:**
> compiz-quinn-aiglx and compiz-vanilla-aiglx are now deprecated, you have to use Gnome Compiz Manager instead.
first remove the one you use with 
```
sudo aptitude purge compiz-quinn-aiglx
```
then install new package:
```
sudo apt-get install gnome-compiz-manager
```
all this is explained in the first pot of this thread that was updated recently by gandalfn.
regaards.

Is truth the compiz-vanilla-"aixgl" is deprecated; but not the compiz-vanilla  and compiz-vanilla-gnome (both packages uses the gnome-compiz-manager). Don't confuse the old package with this two ones! :-\" You can find this information in the new gandalfn blog [http://gandalfn.wordpress.com/howto-compiz-aiglx-on-dapper/](http://gandalfn.wordpress.com/howto-compiz-aiglx-on-dapper/)

---

### Post by pepitogrillo37 on 2006-09-03
> **Webspot said:**
> I followed the tutorial on the blog site. But now X doesn't start and it says Xorg-air doesn't exist!

I have a Radeon 9600 running on fglrx drivers so that I get dri.
Using Ubuntu Dapper

Please Help!

I supposed you have install the xorg-air-core but when you install xorg-air-core, it doesn't seem to copy over your modules from xorg, so you need to do this (as root or starting each sentence with sudo).

mk /usr/lib/xorg-air/modules/drivers
mk /usr/lib/xorg-air/modules/input
cp /usr/lib/xorg/modules/drivers/* /usr/lib/xorg-air/modules/drivers cp /usr/lib/xorg/modules/input/* /usr/lib/xorg-air/modules/input

Restart x session or reboot and tell me later what happened!

---

### Post by ayoli on 2006-09-03
> **pepitogrillo37 said:**
> Is truth the compiz-vanilla-"aixgl" is deprecated; but not the compiz-vanilla  and compiz-vanilla-gnome (both packages uses the gnome-compiz-manager). Don't confuse the old package with this two ones! :-\" You can find this information in the new gandalfn blog [http://gandalfn.wordpress.com/howto-compiz-aiglx-on-dapper/](http://gandalfn.wordpress.com/howto-compiz-aiglx-on-dapper/)

oh , my bad, i know gandalf's pages, i ve just misunderstood you previous question.
to answer now i'm not using the vanilla one.

---

### Post by Webspot on 2006-09-03
> **pepitogrillo37 said:**
> I supposed you have install the xorg-air-core but when you install xorg-air-core, it doesn't seem to copy over your modules from xorg, so you need to do this (as root or starting each sentence with sudo).

mk /usr/lib/xorg-air/modules/drivers
mk /usr/lib/xorg-air/modules/input
cp /usr/lib/xorg/modules/drivers/* /usr/lib/xorg-air/modules/drivers cp /usr/lib/xorg/modules/input/* /usr/lib/xorg-air/modules/input

Restart x session or reboot and tell me later what happened!

I did this and recieved these errors in my Xlog:

```

(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg-air/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.99.8, module version = 8.28.8
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
[R200Setup] X version mismatch - detected X.org 7.1.1.0, required X.org 7.0.-1.8
(II) UnloadModule: "fglrx"
(II) Unloading /usr/lib/xorg-air/modules/drivers/fglrx_drv.so
(EE) Failed to load module "fglrx" (module requirement mismatch, 0)

```

---

### Post by pepitogrillo37 on 2006-09-04
> **Webspot said:**
> I did this and recieved these errors in my Xlog:

```

(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg-air/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.99.8, module version = 8.28.8
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
[R200Setup] X version mismatch - detected X.org 7.1.1.0, required X.org 7.0.-1.8
(II) UnloadModule: "fglrx"
(II) Unloading /usr/lib/xorg-air/modules/drivers/fglrx_drv.so
(EE) Failed to load module "fglrx" (module requirement mismatch, 0)

```

Hi, the problem is another one. The xorg unloads the fglrx module (the driver). Try this, in a normal gnome session (or kde, etc.) write in any console this command "glxinfo" and see, First is the fglrx is loaded and second is the line "direct rendering" equals "yes". If you find an error or a "no direct rendering" the module is not working. If this is the case, you should try to reinstall the packages. If you have a r100 or r200 you cant install the openfree ati's drivers (which works better than the propietary ones!) in this page: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver). If not you'll have to install the propietary's driver (search in google for "howto ubuntu dapper fglrx"). I would like to know with graphic card do you have (maybe ati 9200?).  

Good luck!

---

### Post by pepitogrillo37 on 2006-09-04
> **vrode said:**
> I'm sure it helps but my in my case going to certain websites automatically shuts my browser maybe because defaultdepth 16 is unable to handle the highres page.



regards,
/virendra


Surfing in the web I found the solution. Its a problem that many people have using aiglx with firefox!

**FLASH CAUSES FIREFOX TO TERMINATE**
If you are experiencing this, follow these steps:

In terminal type:
sudo gedit /usr/bin/firefox

A text editor will open.

after the lines that read:

#
# Contributor(s):
#


insert these 2 lines:

XLIB_SKIP_ARGB_VISUALS=1
export XLIB_SKIP_ARGB_VISUALS

And you now have Flash!

---

### Post by shof2k on 2006-09-04
Finally got this working on an Intel 82845G.  The Quinn repros worked, even though the gentoo wiki said my card would segfault.

Woo hoo wobbly windows!

---

### Post by yaddoshi on 2006-09-05
Why is it that I have to let Synaptic update my compiz right before I go to bed, breaking it and taunting me with the fact that my compiz no longer works and there's nothing I can do to fix it (at least right now)?

](*,) 

Alright, goin to bed now.  Hopefully someone fixes it by the time I get up.

---

### Post by yaddoshi on 2006-09-05
Sorry about the double-post, my session kept timing out last night.

Yes, my borders vanished too, and also the cube, etc...

Looks like there are already suggestions on how to fix it.

---

### Post by myha on 2006-09-05
Hi,

since yesterday's update I no longer have the window borders and no other plugin works...  :/... Anyone else with the same problem? How to repair it?

regards

---

### Post by Damwid on 2006-09-05
me too, window borders disappear after update

---

### Post by danhm on 2006-09-05
Some people got their compz working again after following the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=250489"), but mine is still broken too.

---

### Post by ayoli on 2006-09-05
seems that now compiz dont use gconf anymore, it uses csm instead.
so to start compiz:
```
compiz-start
```
then:
```
chmod -R 0755 ~/.compiz
```
then run csm, turn to your prefered settings:
```
csm
```,
then in Menu System > Preferences > Sessions, pick start up tab and add 
```
/usr/bin/compiz-start
```

---

### Post by frup on 2006-09-05
mine too :(

---

### Post by ayoli on 2006-09-05
the post i've made above fix the problem for me.

---

### Post by Webspot on 2006-09-05
> **pepitogrillo37 said:**
> Hi, the problem is another one. The xorg unloads the fglrx module (the driver). Try this, in a normal gnome session (or kde, etc.) write in any console this command "glxinfo" and see, First is the fglrx is loaded and second is the line "direct rendering" equals "yes". If you find an error or a "no direct rendering" the module is not working. If this is the case, you should try to reinstall the packages. If you have a r100 or r200 you cant install the openfree ati's drivers (which works better than the propietary ones!) in this page: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver). If not you'll have to install the propietary's driver (search in google for "howto ubuntu dapper fglrx"). I would like to know with graphic card do you have (maybe ati 9200?).  

Good luck!

I already have the propietary fglrx driver installed. I have a radeon 9600. direct rendering is working

please help!

---

### Post by myha on 2006-09-05
> **ayoli said:**
> the post i've made above fix the problem for me.
Hi,

if I do it according to your fix all works veeeeeeeeeeeeeeeeeeeeeery slow, sometimes it doesnt't even draw the windows....  :/

---

### Post by Yerakon on 2006-09-05
> **myha said:**
> Hi,
if I do it according to your fix all works veeeeeeeeeeeeeeeeeeeeeery slow, sometimes it doesnt't even draw the windows....  :/

*" If you find it too slow (I did!) then open up gconf-editor and remove the blur effect -- as of this writing (Sept. 2006) it REALLY slows things down. "*

From :[http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card]("http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card") :-|

---

### Post by Milamber_Cubed on 2006-09-05
Well I lost window decorations after updating last night and i found out why.

gconf is no longer used for compiz settings so the gnome-compiz-manageer (OR gset-compiz, if you are still using it) should be removed - they only get in the way of things. I removed them and things started working again, but all of my settings had been reset back to the defaults. To change the settings you now use "csm" instead of gconf-editor or gset-compiz/ gnome-compiz-manage - the most important thing for me was to disable the blur plugin. It is faster than before but still slow for me to use. Now everything is as it was before and I am a happy bunny ;)

Hope this helps some people. :)

---

### Post by ayoli on 2006-09-05
> **myha said:**
> Hi,

if I do it according to your fix all works veeeeeeeeeeeeeeeeeeeeeery slow, sometimes it doesnt't even draw the windows....  :/

run csm and disable blur plugin, it sucks a lot of ressources.

---

### Post by myha on 2006-09-05
Hi,

thanks, disabling blur did the trick, it works fine again!

regards

---

### Post by yaddoshi on 2006-09-05
Thanks for the heads-up Ryo...

I ended up disabling compiz-tray-icon from Startup Programs under Sessions after I ran gnome-compiz-manager in terminal and it started spitting out errors (I also went a step further and aptitude remove'd gnome-compiz-manager).  I added compiz-start to the list, and ran CSM, disabled the blur feature.  My top and bottom images are now missing (no big deal, I'm sure I can fix that).

However, I have rain drops once more, which were not present after I had to switch from compiz-vanilla-aiglx to compiz-gnome.

Lose some, win some I guess.

---

### Post by drpolish on 2006-09-06
i've had compiz-quinn-aiglx installed on my aiglx/i915/compiz laptop, but now compiz-gnome/compiz-core wants to install but its saying it cant overwrite compiz-start because its owned by compiz-quinn-aiglx. i can't remove compiz-quinn-aiglx because apt-get says there are unmet dependencies and i have to do apt-get install -f. however none of this works and im greeted with metacity when i boot. is there anyway to remove compiz-quinn-aiglx forcefully? i tried it with synaptic and that didnt work also

thanks,
drp

---

### Post by PathSpace on 2006-09-06
Man, somebody **really** needs to change the instructions at the beginning of the thread...they are so out of date that they talk about vanilla vs. quinn packages!  :-|

---

### Post by drpolish on 2006-09-06
figured it out - i just had to use dpkg to remove quinn packages.

and pointing to the thread above me, you can just go to gandalfn's blog
(gandalfn.wordpress.com)

---

### Post by Uncle Spellbinder on 2006-09-06
> **PathSpace said:**
> Man, somebody **really** needs to change the instructions at the beginning of the thread...|

Yeah, and Gnome Compiz Manager is not compatible with the new CSM.

---

### Post by PathSpace on 2006-09-06
> **drpolish said:**
> figured it out - i just had to use dpkg to remove quinn packages.

and pointing to the thread above me, you can just go to gandalfn's blog
(gandalfn.wordpress.com)

The instructions I found there seemed just as out-of-date and also spoke of seperate vanilla/quinn packages...

---

### Post by ayoli on 2006-09-06
> **Uncle Spellbinder said:**
> Yeah, and Gnome Compiz Manager is not compatible with the new CSM.
actually waht is Gnome Compiz Manager ? compiz-tray-icon and gui for prefrences settings only ?

edit: oh yes, it seems :)
do you think we can safely remove it and remove deprecated gconf keys ?

---

### Post by Uncle Spellbinder on 2006-09-06
> **ayoli said:**
> actually waht is Gnome Compiz Manager ? compiz-tray-icon and gui for prefrences settings only ?

edit: oh yes, it seems :)
do you think we can safely remove it and remove deprecated gconf keys ?

I've completely removed Gnome Compiz Manager from my system with no ill effects. And I assume you can do whatever you want with Gconf regarding Compiz, as Compiz no longer uses/points to Gconf at all. Compiz now uses CSM exclusively.

---

### Post by ayoli on 2006-09-06
thx, I thought of encountering dependancies problems, so i didnt try.

---

### Post by ronmarley1 on 2006-09-06
> **Uncle Spellbinder said:**
> I've completely removed Gnome Compiz Manager from my system with no ill effects. And I assume you can do whatever you want with Gconf regarding Compiz, as Compiz no longer uses/points to Gconf at all. Compiz now uses CSM exclusively.
Ditto here.

EDIT: After removing gnome-compix-manager, everything worked fine on reboot, until I tried to shut down.  Then the PC locked-up.  I reloaded it, and everything is fine.

---

### Post by Balachmar on 2006-09-07
So is there an easy way to switch compiz off?
I have removed the manager as well, since it caused some dependancy problems today. But now I don't know how to switch back to gnome without compiz...

---

### Post by ayoli on 2006-09-07
> **Balachmar said:**
> So is there an easy way to switch compiz off?
I have removed the manager as well, since it caused some dependancy problems today. But now I don't know how to switch back to gnome without compiz...
try in CLI or in a script:
```
killall `pidof compiz` && killall `pidof cgwd`
metacity --replace
```

---

### Post by gandalfn on 2006-09-07
hi,

first, i am really sorry of my episodically answers, my time and my bad english not allowing me most of the time to answer. 

well, i stop to support compiz quinn package, many personal reason with that, gnome-compiz-manager isn't supported by quinn and i think compiz-quinn modifying the original compiz so much. 

I still think compiz-quinn is excellent and great project but which leaves in a bad way :( . _it's only my personnal opinion_

well, i'll made from compiz-vanilla and newest Kristian Hoesberg patches, newest compiz-aiglx packages. it's only official compiz with aiglx support and iXce xinerama support patch, _no cgwd and none compiz-quinn plugins_.

i'll made a little edgy repository for now, a dapper repository comming soon, to install it follow [Howto compiz + aiglx on edgy]("http://gandalfn.wordpress.com/howto-compiz-aiglx-on-edgy/")

thank you for all the encouragements and supports that you gave me.

have fun

---

### Post by Uncle Spellbinder on 2006-09-08
Compiz Tray Icon Is Back!!!

See [***_HERE_***](http://www.compiz.net/viewtopic.php?pid=34728#p34728)

---

### Post by ayoli on 2006-09-08
oh yeah, and it works :)

---

### Post by ayoli on 2006-09-08
after this morning upgrade (spet 9th, compiz .48; plugins .20; csm 0.8) still have problem with Quit choices window which is here but not visible.
not a big problem, but a bit annoying.

---

### Post by nikosaei on 2006-09-08
hi i am from greece and i am fanatic of ubuntu and compiz!!!!
My problem is tha after new installation of compiz i can not find inside csm where to configure to maximize windows with double click on the windows title

I hope you understand my question...sorry for my english!

---

### Post by kaiowa on 2006-09-11
i have run script without errors, but when gdm start, all is very slow and finally system stop. How could i remove changes of script?


Thanks

---

### Post by ghotra on 2006-09-11
Hi guys, I'm having trouble getting the transset plugin to work.
[http://www.ubuntuforums.org/showthread.php?p=1488408](http://www.ubuntuforums.org/showthread.php?p=1488408)

The above link is my original post (with no response).
---


I have a working aiglx install and I am trying to get the transset plugin working in compiz. I've downloaded libtransset.so from:

[http://www.ubuntuforums.org/showpost...&postcount=629](http://www.ubuntuforums.org/showpost...&postcount=629)

and did:

$ sudo cp libtransset.so /usr/lib/compiz/

With gconf-editor, I edited the active_plugins key in /apps/compiz/general/allscreens/options

In that key, I placed 'transset' after 'decoration' and before 'wobble'.

As far as I know, that is all I need to do to get compiz to use the plugin. Is that correct?

I know I need to add a key named 'apps' with value 'Gnome-terminal 85'...but I don't know where or how I need to add it. Can someone help me? Also, is the key supposed to be a list or a string?

Basically, I'm looking to get the transset plugin working.

---

### Post by EnderTheThird on 2006-09-11
I've scoured the Internet(s) but I'm having trouble finding this out.  Will AIGLX work with a Radeon 9800 AIW Pro with the latest ATI drivers, 8.28.8?  I'm running XGL/Compiz right now, and it's running great, but there are some refresh problems in that it doesn't show all elements of a window unless I select it (like it will just show the desktop background until I give the window focus and then the file menu and all other elements will pop in).  It didn't do this until the latest Compiz updates about a week ago.  Now I know AIGLX probably won't fix this, but I figure I might try to give it a whirl just for kicks anyway, if it will work with my Radeon.  I know AIGLX needs specific driver support, but that some ATI users have had it working; I'm just not sure if it will work with my card.  Please let me know if it will work and how I should go about setting it up.  I hate how all the HOWTO's are months old now and you can never be sure if the author updated them after the most recent updates and whatnot.  Thanks!

---

### Post by kendals on 2006-09-12
I just went to copy the input files from /usr/lib/xorg/modules/input/ to /usr/lib/xorg-air/modules/input/ or whatever, and for some reason it deleted all those .so files that were in both folders (namely xorg's!) and now I cannot get back into Ubuntu- it tells me X Server failed to start, and says:

```
(EE) failed to load module "kbd"
```

But with all of my stuff basically (i.e. touchpad, mouse etc.). Could someone please let me know how to get it back, without the internet (can't access it on my laptop without being in Ubuntu...) :(

---

### Post by iam_foo on 2006-09-12
i switched off my cube in the compiz settings.
then i switched it back on.
it doesnt work now.
ive tried reloading the win manager..no good.
rebooting as well.
also sometimes my png on the top/bottom appears.. sometimes not.

anyhelp is appreciated..
or if you need more info let me know..

many thanks..

:twisted:

---

### Post by iam_foo on 2006-09-13
i have the cube working again.
but images arent displayed.
in the settings there are paths set.
any help?

:twisted:

---

### Post by brendo on 2006-09-13
I have installed all of the compiz packages and have glx running on my computer correctly. However, when I try to start compiz with

```
compiz-start
```

I read the following from nohup.out:

```
The application 'cgwd' lost its connection to the display :1.0;
most likely the X server was shut down or you killed/destroyed
the application.

```

and if I start the compiz-manager, I can try to select compiz as the window manager, but when I select it the windows dissapear and reappear, but metacity is still selected and running.

How can I fix this? I have been combing through the forums for hours and I can't find the answer...](*,)

---

### Post by rafadev on 2006-09-13
Hello. 
I've followed your instructions and it has worked almost wonderfully great. 
I have an Ati Radeon 7500 (r200 chip) using the "ati" driver, so it should actually work.

The thing is, all the visual effects (transparency, cube, desktop switching, minimizing and maximizing, etc..) work perfectly well, but when I open an application the window displays wrongly, generally only shows a little part, or a remainder of the bitmap that was in the section of the screen where the new window appeared, but, when I resize it, it displays correctly. Similar things happen with nautilus, the panels and everything else.

The really funny thing is, I wanted to take a screenshot so I could show you the problem, but the program in the screenshot showed perfectly well :confused:. 

glxinfo seems perfectly fine, except for this, that I have no idea if it's actually a real issue. 
This output goes to stderr, this means that if I do:

```
$ glxinfo > /dev/null
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32

```

It echoes it anyway.

The rest seems fine, DRI is available
```

$ glxinfo | grep direc
direct rendering: Yes
```

Well, I would really thank any help. If you need any aditional info please ask me.

Thanks,
         Rafael.

---

### Post by jcrnan on 2006-09-14
brendo: try using synaptics and find all the compiz files, cwgd and csm files and reinstall them there. then restart pc. 

I cant guarantee it works but it has worked for me when compiz got a bit ****** up :)

---

### Post by S1NGH on 2006-09-16
i followed the guide exactly but when i get to the point to
sudo update-alternatives &#8211;config Xorg
where i could not get any alternates.
i thought of giveing it a try and rebooted, x gets disabled and i am stuck, i dont know how to fix this.

here is the important part of the log.
(==) using config file:"/etc/x11/Xorg.config
parsew error on line 151 of section DRI in file /etc/x11/Xorg.config.
the section requires 1 or 2 quoted string to follow it.
(EE) problem parsing the config file
(EE) error parsing the config file.
fatal server error
no screens found
(WW) xf86CloseConsole: KDSETMODE failed: Bad file description.
"                                 "  VT_GETMODE "                                 "

please, i am in need to get aiglx running and fixing this error, please provide any feedback.

---

### Post by Jingo on 2006-09-16
I am having troubles getting the dri to work..
I've had it working for a long time. I have 7500.

I think its due to the recent kernel upgrade, but don't know for sure.
Anyway the radeon module won't load.

dmesg reports somthing like this:
```
...
[17179672.664000] radeon: Unknown symbol drm_core_reclaim_buffers
[17179672.664000] radeon: disagrees about version of symbol drm_release
[17179672.664000] radeon: Unknown symbol drm_release

```

I reinstalled the dri-modules from beerorkid, but it didn't solve it...

Any clues? Anyone else having this problem?

---

### Post by dengar on 2006-09-17
I just did the latest update from the Gandalfn sources. It works mostly except for the fact that some apps screw up, particularly gedit (but only when opened from the desktop) which doesn't really work until I resize it, at which point it starts working normally and terminal which when opened has a black window in which I can't type until I resize the terminal window. Also sometimes the box requesting my password when I try to open synaptics won't display the text I type into it.

Sorry if that's unclear. Has anyone had similar issues?

---

### Post by d3v1ant_0n3 on 2006-09-17
Many thanks for this guide! It's the only guide I found that actually worked first time for me:D :D :D Me loves teh eyecandy!!:D  Still having a couple of problems, but nothing major, and I shall fix them in time!

---

### Post by blackphiber on 2006-09-18
Just wondering.  Lets say I were to upgrade to 6.10 and I followed this guide, would I have to change anything?  6.10 will have Xorg 7.1 with AIGLX right?  How can I get rid of this special Xorg currently installed for an upgrade to 6.10 (planning on upgrading once the beta is released).  Thanks.

---

### Post by ayoli on 2006-09-18
> **blackphiber said:**
> Just wondering.  Lets say I were to upgrade to 6.10 and I followed this guide, would I have to change anything?  6.10 will have Xorg 7.1 with AIGLX right?  How can I get rid of this special Xorg currently installed for an upgrade to 6.10 (planning on upgrading once the beta is released).  Thanks.
use gandalfn guide and packages:
[http://gandalfn.wordpress.com/howto-compiz-aiglx-on-edgy/](http://gandalfn.wordpress.com/howto-compiz-aiglx-on-edgy/)

---

### Post by kgee on 2006-09-18
hmm, still having issues installing this. Following the structions i get as far as acually installing the packages ( sudo apt-get install compiz-quinn-aiglx compiz compiz-gnome)

then it tells me that it cant find the package:

Reading package lists... Done
Building dependency tree... Done
Package compiz-quinn-aiglx is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package compiz-quinn-aiglx has no installation candidate

Ived added some repositories, and I think i have more than i should need (after some frustration i tried putting more in hoping it would solve my problem)

deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper aiglx 
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main aiglx

deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main
deb-src [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main

deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper aiglx
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

anyone know what im missing to get this working?

---

### Post by ayoli on 2006-09-18
> **kgee said:**
> hmm, still having issues installing this. Following the structions i get as far as acually installing the packages ( sudo apt-get install compiz-quinn-aiglx compiz compiz-gnome)

then it tells me that it cant find the package:

Reading package lists... Done
Building dependency tree... Done
Package compiz-quinn-aiglx is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package compiz-quinn-aiglx has no installation candidate

Ived added some repositories, and I think i have more than i should need (after some frustration i tried putting more in hoping it would solve my problem)

deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper aiglx 
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main aiglx

deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main
deb-src [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main

deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper aiglx
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

anyone know what im missing to get this working?
try this:
```
sudo apt-get install compiz compiz-core compiz-plugins compiz-gnome compiz-manager cgwd cgwd-themes csm
```

---

### Post by Yerakon on 2006-09-18
I have used these instructions: 

[http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card]("http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card")

and all it works to duty!=D> 
  
Only one problem: the pop-up with the closing options does not appear when I press the key "off" of the panel...:eek: 

Thankyou...

---

### Post by ayoli on 2006-09-18
> **Yerakon said:**
> I have used these instructions: 

[http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card]("http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card")

and all it works to duty!=D> 
  
Only one problem: the pop-up with the closing options does not appear when I press the key "off" of the panel...:eek: 

Thankyou...

this is a known issue, will be fixed soon. a discuss about this here:
[http://www.compiz.net/topic-3888-can-longer-shut-dow-computer-after-update](http://www.compiz.net/topic-3888-can-longer-shut-dow-computer-after-update)
and a temporary solution here:
[http://www.compiz.net/topic-3888-can-longer-shut-dow-computer-after-update](http://www.compiz.net/topic-3888-can-longer-shut-dow-computer-after-update)

---

### Post by Yerakon on 2006-09-19
> **ayoli said:**
> this is a known issue, will be fixed soon. a discuss about this here:
[http://www.compiz.net/topic-3888-can-longer-shut-dow-computer-after-update](http://www.compiz.net/topic-3888-can-longer-shut-dow-computer-after-update)
and a temporary solution here:
[http://www.compiz.net/topic-3888-can-longer-shut-dow-computer-after-update](http://www.compiz.net/topic-3888-can-longer-shut-dow-computer-after-update)

Many Thanks Ayoli;) 

I have... had a moment of confusion:confused:  between the several Posts!:D

---

### Post by ThomHolwerda on 2006-09-19
> **Jingo said:**
> I am having troubles getting the dri to work..
I've had it working for a long time. I have 7500.

I think its due to the recent kernel upgrade, but don't know for sure.
Anyway the radeon module won't load.

dmesg reports somthing like this:
```
...
[17179672.664000] radeon: Unknown symbol drm_core_reclaim_buffers
[17179672.664000] radeon: disagrees about version of symbol drm_release
[17179672.664000] radeon: Unknown symbol drm_release

```

I reinstalled the dri-modules from beerorkid, but it didn't solve it...

Any clues? Anyone else having this problem?

I seem to be having the same problem with my Ati Radeo 9000. The package which provides the ati and radeon driver modules is installed fine, but still Xorg-air won't come up, saying the modules do not exist.

Any clues anyone?

---

### Post by Uncle Spellbinder on 2006-09-19
> **blackphiber said:**
> Just wondering.  Lets say I were to upgrade to 6.10 and I followed this guide, would I have to change anything?  6.10 will have Xorg 7.1 with AIGLX right?  How can I get rid of this special Xorg currently installed for an upgrade to 6.10 (planning on upgrading once the beta is released).  Thanks.

[***_How I got AIGLX-Compiz working on Edgy_***](http://www.ubuntuforums.org/showthread.php?p=1514105#post1514105)

---

### Post by sinaen on 2006-09-26
> **jamesshuang said:**
> Ok, so what am I doing wrong...

I followed the instructions on the front page perfectly. Xorg-air is running right now.

However, any attempts to run compiz-aiglx crashes out the Xserver, and just restarts GDM for me. I don't even get any debug messages. Any ideas?

Yeah I got this problem to. but i didnt find the solution when i looked. whats the sollution on this?

---

### Post by sinaen on 2006-09-26
> **damagedspline said:**
> have any1 beside me came across the following problem: everything is working fine and then allof a sudden gdm crash unattended, restart (gdm) and requesting a login - and now for the real suprise - after login all i get is the mouse curser and... nothing more. ctrl-alt-backspace has the same behavior. only after a full restart everything works fine.

btw, the new compiz update looks smoother then before but has some annoying new issues - but that's not for this forum.

EDIT: gdm sudden crashes solved by updates - however the "ctrl-alt-backspace" bug remains

I get this to, not the mouse, but sometimes i cannot click on the menus. and then i have to reset to the login-screen by my self. and it doesnt got solved by a update :( tried different settings in the settings editor the problems remain.

---

### Post by foureight84 on 2006-09-27
i installed xorg-aiglx and compiz from the gandolf tutorial. it's working fine, but i was wondering how i can assign f10 and f11 to do the focus and viewport?

---

### Post by StayPuft on 2006-10-02
So I have AIGLX working great on my integrated Intel card, but I am not pleased with the metacity themes. I was wondering if anyone had successfully installed cgwd to use the compiz themes. Are there any special instructions I need to know? Thanks.

EDIT: So when I went to attempt the cgwd install, it came up with "Unable to Find Package" but recommended that I install emerald themer instead. So I went another step and it installed a lot of beryl apps and packages, and then told me I need to update a bunch of libmesa packages. This is where I stopped in fear of compromising my current AIGLX install. Any help?

---

### Post by ronmarley1 on 2006-10-02
> **StayPuft said:**
> So I have AIGLX working great on my integrated Intel card, but I am not pleased with the metacity themes. I was wondering if anyone had successfully installed cgwd to use the compiz themes. Are there any special instructions I need to know? Thanks.

EDIT: So when I went to attempt the cgwd install, it came up with "Unable to Find Package" but recommended that I install emerald themer instead. So I went another step and it installed a lot of beryl apps and packages, and then told me I need to update a bunch of libmesa packages. This is where I stopped in fear of compromising my current AIGLX install. Any help?

I used this How-To from the Beryl wiki and everything works great!  You'll lose a few settings, but it's worth it!  I am running AIGLX on Intel integrated video also.  Here's the link: [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX)

---

### Post by Buffalo Soldier on 2006-10-04
Gandalfn,

Thank you for the how-to. On my Intel 855GM, official compiz is much more stable than Beryl. Plus I like the "minimalistic" approach.

---

### Post by Jaidee on 2006-10-08
With this tutorial I have succesfully, and for the first time after much trying, got compiz working on my old Intel 82815 chipset. Many thanks.

It performs very poorly however, with the cursor and surrounding pixels blinking and not updating in time with the rest of the screen. Any ideas?

Also, is there a way of installing the official Compiz (ie: not Beryl) without using the freedesktop repos?

---

### Post by ribamar on 2006-10-08
Hello guys.
I've just installed for the first time Ubuntu 4 days ago, and i was (still am, sort of) windows xp user, so i had to do a few research in forums and websites to configure right Ubuntu (using the terminal, synaptic package manager, installing last alsa release so my soundcard could work).
And i was in youtube and i saw a movie about Ubuntu aiglx. I had no idea that such thing like this existed :eek: 

So i'm willing to get my Ubuntu working like that, so should i read the first post in this thread, and if i do exactly as it documents here, i will get my Ubuntu work like i saw in the youtube movie? This thread is the most complete bout this subject? No new updates in the software, etc?

Sorry my bad english, i'm Portuguese.

Regards to everyone ;)

---

### Post by Buffalo Soldier on 2006-10-09
> **ribamar said:**
> Hello guys.
I've just installed for the first time Ubuntu 4 days ago, and i was (still am, sort of) windows xp user, so i had to do a few research in forums and websites to configure right Ubuntu (using the terminal, synaptic package manager, installing last alsa release so my soundcard could work).
And i was in youtube and i saw a movie about Ubuntu aiglx. I had no idea that such thing like this existed :eek: 

So i'm willing to get my Ubuntu working like that, so should i read the first post in this thread, and if i do exactly as it documents here, i will get my Ubuntu work like i saw in the youtube movie? This thread is the most complete bout this subject? No new updates in the software, etc?

Sorry my bad english, i'm Portuguese.

Regards to everyone ;)
It depends mostly on your hardware specifications. What kind of hardware do you have there?

---

### Post by Gannin on 2006-10-28
What happened to the Compiz + AIGLX on Dapper link?  It doesn't appear to be working, and some of us that are staying with Dapper for now would like to get AIGLX working with the new beta nVidia drivers.

---

### Post by flapane on 2006-10-28
composite works like a sharm here on edgy
[[IMG]http://img80.imageshack.us/img80/1838/sk10sn9.th.jpg[/IMG]](http://img80.imageshack.us/img80/1838/sk10sn9.jpg)

some one can tell me if beryl is stable and what does it do?

---

### Post by Gannin on 2006-10-28
Beryl is just a fork of Compiz, with more features and effects.

---

### Post by StayPuft on 2006-10-30
My install of AIGLX on Edgy worked great. Absolutely seamless except for one small issue. But first, Hats off to Gandalfn!

My issue is this: when I start applications (terminal, firefox, etc) they start up above where I can see them. They are about 25 pixels too high, so I cannot access the menubar. I have to right click on my windowlist and "Maximize". If I right click on the window list and hit "Move" it does not work. Has anyone encountered this? Is there a fix for this? Thanks.

---

### Post by StayPuft on 2006-10-30
Quick question because I cannot find the answer when searching:

what is the command that I add to my session startup items (in Edgy) to lauch AIGLX automatically at startup? Thanks.

---

### Post by Gannin on 2006-10-30
StayPuft, that depends upon what compositing manager you're using (Compiz, Beryl etc.)

---

### Post by Milamber_Cubed on 2006-10-31
> **StayPuft said:**
> My install of AIGLX on Edgy worked great. Absolutely seamless except for one small issue. But first, Hats off to Gandalfn!

My issue is this: when I start applications (terminal, firefox, etc) they start up above where I can see them. They are about 25 pixels too high, so I cannot access the menubar. I have to right click on my windowlist and "Maximize". If I right click on the window list and hit "Move" it does not work. Has anyone encountered this? Is there a fix for this? Thanks.

This is not a solution, but I have a workaround that doesn't involve maximising. You can move windows if you hold down Alt then click on them.

I have this problem too, but only with windows that were created before beryl was started.

---

### Post by iceseyes on 2006-10-31
Hi, I've got two little problems with compiz.

The first one is about start my gnome-session with compiz. I've tried more and more times to add /usr/bin/compiz-tray-icon with gnome-session-manager, but everytime it disappear! Does anyone know why, or how can I resolv this problem?

the second is about compiz 0.3.3! I've tried to install it but compiz-gnome-manager it say that my video card is not right configured! I use AixGL. My Video Card is ATI Radeon Mobility (IGP330/340/350 (RS200)). Is there an howto to setting my video card right?

---

### Post by StayPuft on 2006-10-31
Well thats another problem I guess I should have mentioned. I know about holding down Alt, but that doesnt work either. In fact, for the very few windows that do open up in the correct area, I can't move them at all. Even if I can grab the top title bar of the app I am completely unable to move it.

I am using Compiz, following Gandalf's tutorial (not Beryl). The preferences windows for this Edgy version are missing options I had in the Dapper version. I used to have an option for which button I wanted to hold to move windows (Ctrl, Alt, or Super) and I used to have a checkbox for the wobbly effect. Now I do not have those and I cannot move windows. Thanks for any help. I hope Gandalf gets a look at this. ;)

---

### Post by StayPuft on 2006-10-31
So I guess my main problem is just finding a way to move a window. The windows are actually starting up at the very top of the screen, this is a problem because I have a menubar up there, and the windows hide behind the menubar. If I could move the windows I could put up with them opening up on top. Oh, and getting the wobbly effect back would be cool too. ;) Thanks guys.

---

### Post by StayPuft on 2006-11-01
Well, when I got inot work this morning there was an update from gandalf and now all issues are fixed! Thanks gandalf!

The missing options have returned in the preferences, the startup command now stays in the session manager, the wobbly effect works again, the windows don't start too high, and the windows are movable. Thanks again!

---

### Post by Gannin on 2006-11-01
I'm glad to hear your issues have been resolved :).

---

### Post by dbbolton on 2006-11-01
```
sudo apt-get install gnome-compiz-manager
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gnome-compiz-manager

```

wtf?

---

### Post by StayPuft on 2006-11-02
did you add gandlaf's repos to your sources?

Dapper:
deb [http://gandalfn.club.fr/ubuntu](http://gandalfn.club.fr/ubuntu) dapper .

Edgy:
deb [http://gandalfn.club.fr/ubuntu](http://gandalfn.club.fr/ubuntu) edgy .

---

### Post by todayalemon on 2006-11-03
Hey there
recently i installed the gnome-compiz-manager and its dependencies, edited my xorg.conf file and now have access to the control panel  of "GL Dekstop" (I followd the instruction of this guy named gandalf). There i find a check box to "Enable GL Dektop". When I hit it, my complete system will freeze and reset is the only way to get out of there. after the reboot, my gnome desktop is available as before and nothing has changed. no matter which settings i choose within the control panel of gl desktop it wont cjage anything.
I use ubuntu edgy eft, gnome and I have an ATI RV350 AS Radeon 9600 graphic card. the driver ("ati") came along with edgy eft. i am just sad not to have great effects like the mac computers have. nothing really serious, just wondering if it is possible...

I suppose this problem has been reported, but I really cant find information that would help me...:-k

---

### Post by mannheim on 2006-11-03
I have compiz working happily from gandalfn's repositories. The one problem is that the gui becomes very unresponsive when the CPU is busy with other work. Is this just me, or a general problem with compiz? For example, try:
[LIST=1]
[*]Open up a terminal window and type ```
yes | gzip > /dev/null
``` to keep your cpu busy.
[*]If you have more than one core, or more than one cpu, or more than one virtual cpu (hyperthreading), then open up a corresponding number of terminals, as in step 1, so that all cpu cores are busy with gzip.
[*]Now try just moving the mouse around, dragging windows etcetera
[/LIST]

On my machine, even mouse pointer movement is very jerky in step 3. This does not happen with other composite managers such as xcompmgr or kompmgr. My setup is a 3 GHz P4 machine, with an nvidia geforce 6200, and the nvidia 9625 drivers. Anyone else experience this?

---

### Post by Gannin on 2006-11-03
Do you have the proper repositories enabled?

---

### Post by StayPuft on 2006-11-03
todayalemon,

Search around for tutorials to get this working for an ATI card. Gandalfs tutorials are designed for intel on-board graphics cards. I believe Beryl for ATI should work for you...

---

### Post by shywolf9982 on 2006-11-03
> On my machine, even mouse pointer movement is very jerky in step 3. This does not happen with other composite managers such as xcompmgr or kompmgr. My setup is a 3 GHz P4 machine, with an nvidia geforce 6200, and the nvidia 9625 drivers. Anyone else experience this?

Yes I did aswell. I have an ATI X700, and things aren't too bad usually... just, the cube flipping gets really slow, and sometimes "hangs up" in the middle.
I noticed it first when using firefox: if firefox was unfocused everything went fine, if it was the cube flipping wasn't smooth. Then noticed it happened with banshee too (another cpu-intensive app).
What I can't really get is why this happens, since it doesn't seem to me there are many cpu requests made when flipping the cube alone, but I might be in error.

---

### Post by mannheim on 2006-11-06
> **mannheim said:**
> 
On my machine, even mouse pointer movement is very jerky in step 3. This does not happen with other composite managers such as xcompmgr or kompmgr. My setup is a 3 GHz P4 machine, with an nvidia geforce 6200, and the nvidia 9625 drivers. Anyone else experience this?

As a follow-up to my earlier post, I gave beryl a try in place of compiz, and this problem does not occur with beryl. I can open up four terminals, get the CPU busy chewing on random stuff, and the gui with beryl remains responsive, and pretty smooth.

---

### Post by maxopotamus on 2007-01-04
I tried this and all went well until the last step where I got 

> E: Couldn't find package linux-dri-modules-common


---

### Post by sonyboy on 2007-01-07
> **gandalfn said:**
> Howto Install xorg-aiglx + compiz (packages)

To install compiz on aiglx in dapper :

[Howto compiz + aiglx on dapper]("http://gandalfn.wordpress.com/howto-compiz-aiglx-on-dapper/")

to install compiz on aiglx in edgy :

[Howto compiz + aiglx on edgy]("http://gandalfn.wordpress.com/howto-compiz-aiglx-on-edgy/")

[COLOR="Red"]Warning !! compiz-quinn-aiglx and compiz-vanilla-aiglx are now deprecated ! 
[Gnome Compiz Manager]("http://gandalfn.wordpress.com/gnome-compiz-manager/") replace them ![/COLOR]

to migrate on it, you may remove first compiz-quinn-aiglx :



or compiz-vanilla-aiglx:



and install gnome-compiz-manager :



Have fun

EDIT: 06/03/2006 
- add Composite options in xorg.conf configuration (thanks jstueve)

update compiz-aiglx 0.0.6-ubuntu2 packages
- resync with new compiz debs from ubuntu forums (compiz-0.0.6-0ubuntu7) 
- add opacity plugins in package
- add compiz-aiglx-kde package

EDIT 16/03/2006
update xserver-xorg-air_0.99-ubuntu3
- suppress buggy libmesa-aiglx packages and dependencies don't need (thanks Jeff250)
- modify xorg config to break dri 
- add patched xserver-xorg-driver-ati

EDIT 16/03/2006
- add forgot module listin xorg configuration

EDIT 20/03/2006
update compiz-aiglx 0.0.7 ubuntu1
- resync with new compiz debs from ubuntu forums (compiz-0.0.7-0ubuntu1)
- add LIBGL_ALWAYS_INDIRECT=TRUE in start aiglx (thanks Jeff250)
- replace vi by gedit (old user practice ;) )

EDIT 25/03/2006
update xorg-air 0.99.1
- resync xorg-air with lasted cvs snapshot which include some bug fixes, optimisation and security fix 
- mesa-aiglx-sources depends is removed this package is now obsolote
- to rebuild xorg-air from source you need this packages 
[x11proto-gl-dev_1.4.6-0ubuntu1_all.deb]("http://gandalfn.club.fr/ubuntu/x11proto-gl-dev_1.4.6-0ubuntu1_all.deb")
[x11proto-composite-dev_0.3-0ubuntu1_all.deb]("http://gandalfn.club.fr/ubuntu/x11proto-composite-dev_0.3-0ubuntu1_all.deb")
[x11proto-fixes-dev_4.0-0ubuntu1_all.deb]("http://gandalfn.club.fr/ubuntu/x11proto-fixes-dev_4.0-0ubuntu1_all.deb")
update compiz-aiglx 0.0.7 ubuntu2
- resync with the fantastic quinn compiz packages ;)
- compiz-aiglx-start script is now in package it's automatically started in gnome startup session to disabled it remove /etc/xdg/autostart/compiz-aiglx.desktop file
- patched gnome-session is now needed by compiz-aiglx-gnome
update xserver-xorg-driver-ati 
- rebuild with aiglx dri init patch

EDIT 25/03/2006
update compiz-aiglx 0.0.7 ubuntu3
- add a sleep 2 to make sure gnome-window-decoration-aiglx is started before compiz-aiglx

EDIT 28/03/2006
update compiz-aiglx 0.0.7 ubuntu4
- resynchronise with quinn compiz 0.0.7 ubuntu11 package
- improved compiz-aiglx-start script with notification area configuration tool to activate plugins (screenshots attached)

EDIT 31/03/2006
update compiz-aiglx 0.0.7 ubuntu6
- resynchronise with quinn compiz 0.0.7 ubuntu13 package
- water plugin is desactivated for now, not work with aiglx :(
update xorg-air 0.99.1 ubuntu2
- sync CVS HEAD
- comment GLcore module, it can crash X if not have latest DRI driver

EDIT 08/04/2006
update xorg-air 0.99.1 ubuntu3
- fixes some bugs and memory leaks
WARNING !! use only official libgl1 debs with it
update gnome-session 2.14.0 ubuntu3
- rebuild latest gnome-session deb with logout_no_grab patch to prevent hang   in logout
update xserver-xorg-driver-ati_6.5.7.3 0ubuntu5
- build latest package with radeon-prefer-db-visuals patch
update compiz-aiglx 0.0.9 ubuntu1
- resync with latest official compiz
- rework of compiz-aiglx-change patch now compiz-aiglx use copySubBuffer to refresh region (minor performance improvenement)
- remove of quinn patch for now
EDIT 08/04/2006
update compiz-aiglx 0.0.9 ubuntu2
- resync with quinn package (thanks very much iXce)
EDIT 18/04/2006
update xorg-air 1.0.99.2 ubuntu2
- resync with xorg server-1.1 branch
- mesa 6.5 is now needed to work
- cvs mesa kernel module are needed too
add xserver-driver-i810 1.6.0 ubuntu1
- needed to work with latest compiz-aiglx
update compiz-aiglx 0.0.9 ubuntu3
- resync with quinn package
- rework of compiz-aiglx to work with latest compiz
- add accelerated-indirect-rendering option 
update gnome-session 2.4.1 ubuntu3
- resync with latest ubuntu package

EDIT 02/05/2006
All compiz-aiglx are now deprecated, meta package compiz-vanilla-aiglx replace them. it's integrate a new compiz-start script (screenshots attached).
Add firefox hang tip (thanks Permafrost91)

EDIT 03/05/2006
xgl.compiz.net repos really updated with xorg-air 1.0.99.902 ubuntu02
- rework of aiglx-compiz patch to conform latest tfp spec
- 24 depth rework now with compiz-vanilla

EDIT 17/05/2006
xorg-air 1.0.99.903
- copy sub buffer support added
- firefox hang resolved
linux-dri-modules 
- new dri modules packages
- suppress dri modules compilation howto
compiz
- add compiz-quinn-aiglx install
- suppress firefox howto

EDIT 08/06/2006
linux-dri-modules 20060606:
xserver-xorg-drivers-ati 6.6.0:
good news aiglx compiz work now on ati radeon graphic card !

EDIT 28/08/2006
redirected on my blog howto.
add edgy howto
compiz-quinn-aiglx and compiz-vanilla-aiglx deprecated, gnome-compiz-manager replace it !


Howto compiz + aiglx on edgy 

that link doesn't work for me...it tells me error 404- not found 

:((please someone help me!!!

---

### Post by breakman on 2007-01-07
The link should be [http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy](http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy)

---

### Post by Refined Power on 2007-01-07
Hi I have successfully gotten to step 2. Configure Xorg, but I do not know what he means by “Edit your Screen section and modify your DefaultDepth” does anyone know how to do that?
thanks

---

### Post by deadwalkin on 2007-04-23
ok i have been trying to get this to install on a samsung laptop with ubuntu.

but copy all the links for compiz also xgl half the links dont work.
is it me or s there other ways to install this i see ubuntu has got cube working on its upgrade but does not work as multi screen. you can drag your items accross onto the other screen but thats it you cant have it running like a cube.

can some one help i have been trying to get this working all weekend 
and yes i am a noob lol!!!

just need the links for the working ones
THANK YOU guys and girls

---

### Post by toga34 on 2007-09-21
would this work for ubuntu 7.04 ... I realise that this is not edgy or dapper but will this also work for me?

---

### Post by pigbig842001 on 2007-11-03
> **vendetta red said:**
> What I am getting from this is that with AIGLX I wouldn't be able to watch a movie and wobble the window around with it still playing perfectly, is that correct? I sure hope not, I like having fully accelerated video.
Actually, I have G965 chipset (GMA X3000, open source drivers).

In the default ubuntu installation, it was difficult to run water effect and videos would not play. Then I did **sudo apt-get install xserver-xgl** and now everything runs on it. I like to run everything together like water effect, rotate cube, glass windows, transparent cube (glxgears inside it), play video. All of them run without a glitch.

I think, Xgl is good. I will try when AIGLX is added to repositories.

---

### Post by rhc on 2008-01-20
> **pigbig842001 said:**
> Actually, I have G965 chipset (GMA X3000, open source drivers).

In the default ubuntu installation, it was difficult to run water effect and videos would not play. Then I did **sudo apt-get install xserver-xgl** and now everything runs on it. I like to run everything together like water effect, rotate cube, glass windows, transparent cube (glxgears inside it), play video. All of them run without a glitch.

I think, Xgl is good. I will try when AIGLX is added to repositories.

But you can't play games with it.

---

