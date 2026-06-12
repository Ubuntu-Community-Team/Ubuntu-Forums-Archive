---
title: "Xlib:  extension &quot;XFree86-DRI&quot; missing on display"
date: 2006-06-19
forum: Desktop Environments
---

### Post by dcherryholmes on 2006-06-19
Somehow I've lost 3D accel on my Thinkpad R52 running the x300 ATI Mobility.

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X300 Generic
OpenGL version string: 2.0.5814 (8.25.18)

root@morgulis:~# glxinfo
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No

I've reinstalled the latest fglrx drivers, ensured my restricted modules match my running kernel (haven't tried uninstalling the older restricted ones though), and symlinked some /lib/dri directories (picked up from another thread, but didn't work for me).

Any suggestions?

---

### Post by alejandrops on 2006-06-19
same problem here. but 3d seems to work OK. did you find anything?

---

### Post by dcherryholmes on 2006-06-21
[QUOTE=alejandrops]same problem here. but 3d seems to work OK. did you find anything?[/QUOTE]

Nope.  And I wouldn't say 3d is working OK for me.  Rendering is very choppy, fglx_gears and glxgears fails.  My desktop is horribly borked, and I can't seem to find the cause.  I don't know if this is ati's fault, the package maintainers, or just my own for trying to run Xgl.  All I know is that my Ubuntu system *was* sweet, and now it sucks.

---

### Post by dcherryholmes on 2006-06-22
I'm surprised that either:
A) nobody else is getting screwed by this --or--
B) nobody has the answer

In case anyone else is looking for some answers, I'll relate my experiences so far:

First, I decided to just start over from the beginning (although I'm on the verge of REINSTALLING Dapper..... how Windows-esque).  So I followed this guide:  [https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

That quite led me to the ATI Binary driver HOWTO:

[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

I went ahead and did: 

apt-get remove --purge linux-restricted-modules-$(uname -r)
apt-get remove --purge xorg-driver-fglrx

... just to be sure to start with a clean slate.  Or so I thought.  None of that touches your current xorg.conf, which would turn into a problem later.

So now I'm following the ATI driver guide.  I get to the part where it instructs you to run aticonfig --initial.  I run that, and it tells me that fglrx is already found.  I look at xorg.conf and see that it is, and figure maybe that makes sense.... maybe nuking xorg.conf from within a running X session is bad.  So, I do:

sudo dpkg-reconfigure xserver-xorg

and select my driver set to be "ati" (the free and open one, which I'm told won't support Xgl/compiz).  I run aticonfig --initial again, and it still tells me fglrx already found!  I 'grep fglrx /etc/X11/xorg.conf' and get nothing.  So I then make a folder called xorg.confs_old, and move every old backup xorg.conf file into it, leaving only the newly generated xorg.conf with the ati driver.  Now running aticonfig --initial does its stuff.  I think to myself that the ati guys write crap software, but I also think I may be making progress in getting my Desktop *back to the functionality it had weeks ago*.  You know, I know I'm probably coming off a little whiney, but honestly.... if this stuff just never worked (and with an ATI x300 card, for quite a while it didn't), then it wouldn't bother me.  But the fact that everything was working and, somehow, just by applying regular updates I've bought myself into.... what?  Days of beating on this thing.  Honestly..... I wasted less of my time running gentoo!

So I proceed with the guide, apply the 

sudo aticonfig --overlay-type=Xv

command, etc etc, reboot and cross my fingers.

Still the same crap.  Crap performance, and the usual "Xlib:  extension "XFree86-DRI" missing on display ":1.0"" message.

I've read every thread, followed every guide, and wasted an enormous amount of time on this.  I was quite the Ubuntu booster for a while, but "it just works" is starting to ring more and more hollow.  I suppose if anybody had the answer to my problem they would have already posted it by now, and complaining about it probably doesn't do any good, but I just feel really, really frustrated right now.  I thought linux was almost there, but going on my own personal experience I don't think I can tell my friends that anymore.

---

### Post by zerofx on 2006-06-22
I, too, have that error messege, and I followed the directions to the T on the aformentioned howto guide, and even edited the xorg.conf to add the line "Load  dri", but it was already there where it was specified to load it, and it's still getting this messege.

*shrug*

I'm runnin' an ATI Xpress 200M laptop.

---

### Post by dcherryholmes on 2006-06-26
New packages came out from the beerorkid, a new dsl package among them.  After I installed those my performance went back to normal, near as I can tell, but I still get the same error message out of fglrxinfo.  The error is not a huge concern of mine as long as performance is acceptable, which it seems to be.

---

### Post by carney1979 on 2006-11-09
This worked for me:

[http://www.ubuntuforums.org/showthread.php?t=292642&highlight=Xlib%3A+extension+XFree86-DRI%26quot%3B+missing+on+display+%26quot%3B%3A0.0.](http://www.ubuntuforums.org/showthread.php?t=292642&highlight=Xlib%3A+extension+XFree86-DRI%26quot%3B+missing+on+display+%26quot%3B%3A0.0.)

I did what [Eversmann]("http://www.ubuntuforums.org/member.php?u=42294") said and in my case I did not have to follow the link he provided for more help.

David

---

### Post by digitalghost1 on 2007-04-13
I have the same issue on my Compaq nw8440 using ATI FireGL V5200 256MB RAM.

Loaded ATI driver and Beryl works fine, just can't play games like this one:
[http://www.katanoon.nl/ubu-e/install.php](http://www.katanoon.nl/ubu-e/install.php)

Hoping to get this cleared up.

---

### Post by harvsman on 2007-05-23
I don't  know if you guys are having the same problem as me but the fact is:

You who the games isn't working after the xgl/beryl installation try to deactivate the xgl and then try to run your game, the beryl installation is not the problem but the xgl.

I'm looking for this solution a long time ago and I experienced this problem with an ATI 200M (compaq laptop) and a Geforce 4 series.

it doesn't matter what I do... always getting the same error after enabling xgl.

direct rendering: No
Xlib:  extension "XFree86-DRI" missing on display ":0.0".

---

### Post by strumluff on 2007-07-01
I have the same issure on an ATI X200M (X1100)

Anyone found a fix?

---

### Post by cberman on 2007-07-07
Pretty sure it's not possible to use openGL and sthe like with XGL using the ATI drivers. Everything I've found so far just says you need to switch between gnome for games and XGL to be able to run beryl and the like. Sad story but known issue. I should have gotten the nvidia card =(

And I should mention I only get that error when I'm running an XGL session =/

---

### Post by matrixbandit on 2007-07-15
> **cberman said:**
> Pretty sure it's not possible to use openGL and sthe like with XGL using the ATI drivers. Everything I've found so far just says you need to switch between gnome for games and XGL to be able to run beryl and the like. Sad story but known issue. I should have gotten the nvidia card =(

And I should mention I only get that error when I'm running an XGL session =/

I'm quickly coming to the same conclusion as well. It would seem to me to be an issue with XGL rather than the proprietary ati drivers, since as we've noted, DRI functions fine with gnome by itself, but as soon as you drop XGL on it, we lose DRI functionality. What really strikes me as ironic about the whole thing is that XGL runs its own features fully accelerated, just doesn't seem to pass on hardware accelerated functionality to its client processes.

I am curious about this because if my understanding is correct, the way it works is that basically, XGL runs on top of xorg. So maybe display 0 is xorg, and display 1 is XGL which is transparently managing display 0. So even though DRI may be available on display 0, and XGL may be using DRI to draw its own effects (window wobble, cube rotation, etc), if XGL isn't passing on DRI functionality to display 1, which all the programs we are running like glxinfo and glxgears are running on, we won't get the acceleration, and thus the 3d is done is software and sucks. Anyone have any thoughts on this?

---

### Post by hardKNOXbz on 2007-07-15
i too have the same problem..... 
come on there's gotta be a fix for this.....

here's a site i found.... i installed  but problem not fixed
[ftp://ftp.xfree86.org/pub/XFree86/4.1.0/binaries/Linux-ix86-glibc20/](ftp://ftp.xfree86.org/pub/XFree86/4.1.0/binaries/Linux-ix86-glibc20/)
[http://www.xfree86.org/4.1.0/Install3.html#3](http://www.xfree86.org/4.1.0/Install3.html#3)

---

### Post by Jukka-Pekka on 2007-08-14
Same here!

No-one knows how to get rid of this?

$ glxinfo
name of display: :1.0
_Xlib:  extension "XFree86-DRI" missing on display ":1.0"._
display: :1  screen: 0
_direct rendering: No_

It only seems to appear in GLX session with me also. Not in Gnome.

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.0.6747 (8.40.4)

On an ATI Mobility Radeon X1600 on a HP nc8430 laptop

---

### Post by djseeker2007 on 2007-08-16
> **matrixbandit said:**
> I'm quickly coming to the same conclusion as well. It would seem to me to be an issue with XGL rather than the proprietary ati drivers, since as we've noted, DRI functions fine with gnome by itself, but as soon as you drop XGL on it, we lose DRI functionality. What really strikes me as ironic about the whole thing is that XGL runs its own features fully accelerated, just doesn't seem to pass on hardware accelerated functionality to its client processes.

I am curious about this because if my understanding is correct, the way it works is that basically, XGL runs on top of xorg. So maybe display 0 is xorg, and display 1 is XGL which is transparently managing display 0. So even though DRI may be available on display 0, and XGL may be using DRI to draw its own effects (window wobble, cube rotation, etc), if XGL isn't passing on DRI functionality to display 1, which all the programs we are running like glxinfo and glxgears are running on, we won't get the acceleration, and thus the 3d is done is software and sucks. Anyone have any thoughts on this?

It really makes sense. Now the question is what we can do about it? How to fix this problem?? Any one has any idea??? Thanks a lot!

---

### Post by Rimers on 2007-08-19
It seems that XGL is stopping the system from being able to work with direct rendering (DRI)

This means my first post with a possible solution does not work.
So for me its back on the lookout for a soultion that will actualy work as intended 

/Rimers

---

### Post by glrossetti on 2007-08-23
Have you tried using:

DISPLAY=:0 glxinfo

XGL is similar to DWM in Vista and Quartz Compositor in OS X in that applications do not draw directly to screen, but instead draw to off-screen buffers that are then composited by the window manager and displayed on-screen.

I've found some compatibility issue using XGL, but all seems related to this layer between graphic driver and window manager. DISPLAY=:0 works even with aticonfig, and other related command line tools.

---

### Post by JBAlaska on 2007-08-31
Sweet! I was also bugged by the "Xlib: extension "XFree86-DRI" missing on display" when running a XGL session although Compiz-Fusion is working fine with my ATI 9600, that "no direct rendering" string was bugging me. However using glrossetti's suggestion "DISPLAY=:0 glxinfo" gives me:
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2

So since Compiz-Fusion is screaming along with my 9600 OC'd to Core=432.0 Mem=391.50 ( I can go higher, but I'm happy with the performance) I'm a happy camper! Thanks!

---

### Post by dawv on 2007-09-13
eact same error when trying to run UT2004

any ideas?

"[SIZE=3] Xlib:  extension "XFree86-DRI" missing on display ":1.0" "
[/SIZE]

---

### Post by evilbunnyfufu on 2007-09-15
> **glrossetti said:**
> Have you tried using:

DISPLAY=:0 glxinfo

XGL is similar to DWM in Vista and Quartz Compositor in OS X in that applications do not draw directly to screen, but instead draw to off-screen buffers that are then composited by the window manager and displayed on-screen.

I've found some compatibility issue using XGL, but all seems related to this layer between graphic driver and window manager. DISPLAY=:0 works even with aticonfig, and other related command line tools.

i can verify this is very true, 
mrradiks@MyOtherGF:~$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
mrradiks@MyOtherGF:~$ DISPLAY=:0 glxinfo | grep direct
direct rendering: Yes

running cedega using display :0 works.. OpenArena also does not work on my display :1 but works like a charm on :0
looking at a few applications :0 has my drivers and :1 does not..

---

### Post by jcrow on 2007-09-23
I came across this when the compiz fusion update started causing video to play choppy both in totem and Mplayer. I found that the CPU usage was very high. By running metacity videos played normal. I started to look into video driver problems or XGL problems and came across this thread. I do have direct rendering if I put in" DISPLAY=:0 glxinfo"  I think the solution should be coming soon with the new driver coming from ATI that supports aiglx. Then we won't have to use XGL, which is what seems to be slowing things down. I am running a Turion 64 dual core with 1 gig of ram and an ati xpress 1150 card and it seems slower compared to the desktop I have that is running beryl which is a pentium 4 1.6ghz with 512mb of ram and an nvidia card.

---

### Post by jcrow on 2007-09-24
I did a little more research on this and found that XGL does not use DRI. I also found that if you add "--indirect-rendering" to the command to start compiz, it really speeds things up. I have an AMD Turion 64X2 Laptop with an ATI Express 1150 integrated card. Making this change changed the FPS in GLXgears from around 600 to around 1500 to 1600. I hope this helps.

my fglrx info

jcrow@jcrow-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series
OpenGL version string: 2.0.6334 (8.34.8)

---

### Post by lordoflima on 2007-09-25
Maybe try this if you have installed xgl:

edit /usr/bin/startxgl.sh

set both :1 to :0 - log off and select xgl as session type.

Then you'll be fine (I was ;-) )

---

### Post by b3y0nd on 2007-12-05
> **harvsman said:**
> I don't  know if you guys are having the same problem as me but the fact is:

You who the games isn't working after the xgl/beryl installation try to deactivate the xgl and then try to run your game, the beryl installation is not the problem but the xgl.


I have an ATI X1300 card thats doing the same thing. I cant get games to expand to true fullscreen, performance SUCK when using metacity, but get this: With beryl and compiz performance is acceptable...except of course I can play games. I know, odd it should work the other way around, with metacity performing ok and compiz and beryl all geeked up. 

I have not found a way around this yet. Something that may help some of you is this thread :

[http://forumubuntusoftware.info/viewtopic.php?f=27&t=322&p=2363&sid=45a6bbbe378ad736222b230a223ed1cb#p2363](http://forumubuntusoftware.info/viewtopic.php?f=27&t=322&p=2363&sid=45a6bbbe378ad736222b230a223ed1cb#p2363)

Helped me to get beryl working on all desktops, but something is really goofed up with my ati driver and im really new to Ubuntu. 

Hope someone pins this one down... may just put in a nvida card hate to go from a 512MB to a 128 :(


beyond

---

### Post by tarekeldeeb on 2008-01-19
> **strumluff said:**
> I have the same issure on an ATI X200M (X1100)



same here . !

---

### Post by jay019 on 2008-04-07
Looks like im not alone

---

### Post by n8makar on 2008-06-26
i got this error in trying to install and run google earth. everything (meaning compiz and i also have awn) work fine before. i think im donw with ati for my next pc.

---

