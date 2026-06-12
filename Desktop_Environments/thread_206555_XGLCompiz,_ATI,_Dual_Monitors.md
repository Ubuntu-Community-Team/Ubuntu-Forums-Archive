---
title: "XGL/Compiz, ATI, Dual Monitors?"
date: 2006-06-30
forum: Desktop Environments
---

### Post by zodwallop on 2006-06-30
Perhaps what I'm trying to do just isn't possible.  I apologize if this has already been posted, but I couldn't find any info related to my specific issue via the search option or through Google.

I'd like to have XGL/Compiz installed on my computer, but it's proving to be quite a headache.  

I've got an ATI Radeon 9800Pro installed with the latest drivers (8.25.18).  That doesn't seem to be what's causing me problems, though.  It's the fact that I have a dual monitor setup that's giving me gray hairs.  I have one desktop spanned across 2 monitors at 2560 X 1024 and Compiz just doesn't want to play nice with it.  

After much fiddling, I think I've gotten XGL running properly using the tutorial found here ([https://help.ubuntu.com/community/CompositeManager/Xgl)](https://help.ubuntu.com/community/CompositeManager/Xgl)).  I set it up so from the login screen I can choose to log into a Gnome session or an XGL session.  When I log into an XGL session and type "compiz --replace gconf" I get "compiz.real: No composite extension".

Any ideas on whats going wrong and what I can do to make it work?  Has anyone with dual monitors and an ATI card been successful in getting XGL/Compiz to run properly?

---

### Post by zodwallop on 2006-07-01
Ba-dum-bump!  Any XGL/Compiz pros out there?

---

### Post by jgcamp99 on 2006-07-01
"When I log into an XGL session and type "compiz --replace gconf" I get "compiz.real: No composite extension"."

I'm taking baby steps myself with this and following the same instructionals you've found.

I reenabled root and did my install that way. I was getting a worse message than yours, As root, the XGL session worked fine. Everytime I went to go in as the Ubuntu user, it wouldn't let me log in under the XGL session, that is, until I did this as the Ubuntu user.

You can then start compiz at the beginning of each Xgl server session by placing two commands in your session file. Navigate to "System > Preference > Sessions". Click on the right-most tab, "Startup Programs".

Create a new entry for the window-decorator:

gnome-window-decorator

Now create a new entry for compiz:

compiz --replace gconf

Close the Session Preference Panel. Now compiz should start every time you log into your Xgl-Gnome session.

---

### Post by jgcamp99 on 2006-07-02
zodwallop, this iteration of xGL/Compiz seems limited, not to mention buggy. I get messages to restart things that crashed from time to time. I can't seem to get the cube effect that are screenshots found on the internet. All I get is a ghost effect to open windows/apps. Some of the shortcut key sequences work. This Compiz thing is a Novell production and those cube screenshots are probably done on their version of Linux. I found another 3d desktop for Linux, it's Sun's production and it's called Project Looking Glass. But darned if it's not a 130+ MB download and it's what I'll call a beta for it.

With Compiz, I find that often times a reboot allows you to go into the xGL session. Otherwise, I try, the system tries to go in and I get this message that the session lasted less than 10 seconds, without actually logging in. I'm glad this is one of those things where it's not the default session. Maybe it's my 9600 XT being long in the tooth as far as video cards go ? I have a gut feeling these perform as billed when running a $ 500 state of the art video card ?

---

### Post by zodwallop on 2006-07-06
jgcamp,  thanks for the info - I'll fiddle around with it some more.  

As a side note, I have a separate computer running Ubuntu with a 9600XT and XGL/Compiz runs great on it, cube effects and all.  I even got the water effects running, but disabled them as my poor Athlon XP 2200+ maxed out with it going.  That computer only has one monitor though, which I think makes all of the difference.

---

### Post by thegnark on 2006-07-08
just wanted to add a "metoo" to this thread

i've checked all the forums and tutorials and they all say the same thing (for installing xgl as a session). the only difference is, i changed the screen to screen 0 instead of 1. when i use 1, my session loads and dies quickly, and i'm notified of it. when i change it to 0 (per fglrxinfo below), it loads fine

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9700 Generic
OpenGL version string: 2.0.5814 (8.25.18)
``` 

in any case, the session now loads fine, but i can't start compiz because of the aforementioned error

p.s. i too have dual monitors

---

### Post by Fudgie on 2006-07-26
I've read several places that the ATI driver doesn't support more than 2048x2048, so the best you can do until Xgl gets support for splitting the desktop into multiple chunks is 2048x768. As I refuse to lower my resolution (2560x1024 is small enough as it is), I'm stuck with regular X11 for now. ](*,)

---

### Post by blueturtl on 2006-07-26
> Any ideas on whats going wrong and what I can do to make it work? Has anyone with dual monitors and an ATI card been successful in getting XGL/Compiz to run properly?

Sorry to ruin your hopes, but XGL/Compiz in it's current state does not have dual-monitor support at all. It's broken. If you need dual-monitors, you should disable XGL for the time being.

---

### Post by leohart on 2006-07-26
Umm, I think you should rephrase that as: it currently does not support dual monitor natively. My nVidia card allow me to Twinview and have Compiz working just fine.

That rotating cube on 2 19" LCD really woo my future gf.

---

### Post by reuben on 2006-07-26
I have dual monitors using two x screens / two device entries, etc. Granted you lose the xinerama niceness, but xgl/compiz *does* fire up fine in this config. My xorg.conf is attached if you want to try to replicate my setup.

---

### Post by thegnark on 2006-07-26
it seems to be that the ati dual screen just isn't up to snuff. for the users reporting that it works, both have nvidia

---

### Post by pRedat0r on 2006-07-26
I have a 9800 Pro as well with Big Desktop (one desktop spanned over 2 monitors) and havent been able to make any progress getting XGL/Compiz working.  I have not yet tried to disable 1 of my monitors and see if I can get it working that way however.

I have tried the setup where you modify gdm.conf and make it ALWAYS run XGL -- no luck.  I also tried the more preferred (for me) method of having a separate session at login to select XGL, and that didnt work either.  In the past I got some error that rgb.txt or something like that didnt exist.  The next compiz build I installed, and the current one I tried last week both complain that there are no screens, and it dies seconds after I click login.  No clue why I get that.  I have also tried on the parameters to start XGL to set the Screen to 0 or 1, neither seem to help.

I too am wondering if anyone with an ATI card has gotten Big Desktop mode to work with XGL/Compiz.  I opened a thread in the hardware Video & Sound section a few days back and no one responded:  

[http://www.ubuntuforums.org/showthread.php?t=222039]("http://www.ubuntuforums.org/showthread.php?t=222039")

Hopefully someone can get this running eventually.  XGL/Compiz looks really nice, and Kororaa XGL was nice (albeit it ran in clone mode on my machine by default), but without dual monitor support, XGL/Compiz doesnt meet a lot of people's needs (web development on 1 monitor is painfully annoying).

Thanks.

---

### Post by bonustracks on 2006-09-13
I'm in the same ATI + Big Desktop boat.  A solution would be greatly appreciated.

---

### Post by TrinitronX on 2006-09-13
To begin, before you even start messing with dual head stuff, make sure compiz will start normally, and that fglrxinfo gives you something like:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.5946 (8.27.10)

```

The method I used to start compiz is the Xgl session method using the startxgl.sh script, and putting compiz-start in System->Preferences->Sessions->Startup Programs.
Make sure you have all dependencies, especially: ```
xserver-xgl
compiz
compiz-gnome (or compiz-kde if you're using kde)
compiz-core
compiz-plugins
csm
cgwd (required if you want to change the window decorations)

```

If you're getting an error when trying to start compiz, make sure your ATI drivers are installed correctly first, and that fglrxinfo does't mention mesa at all.

So... I've been looking for a solution to this ever since I started using compiz back when Dapper was still in development.  ATI really needs to get their drivers up to par, the only way I was able to get a form of dual screen working with my particular setup was with setting up a secondary graphics device in my xorg.conf that pointed to the same bus ID of my 9800pro.  Then, I linked my first monitor to the main device, and the second one to the secondary device.  This setup worked in dual screen mode with 2 different screen resolutions (I've got a widescreen LCD and a VGA monitor, needless to say that the LCD's native resolution is unsupported by the VGA monitor).

The problem: Each screen is a totally separate X session.  Also, when starting compiz, the primary screen will show things normally, and the secondary is just totally blank.  You can move the mouse to the other screen, but you can't do anything.  Not to mention that the window moving to that side of the cube adjacent to the secondary screen will not work.  Your cursor will just drop the window at the edge and continue onto the secondary monitor.  I'm not totally sure, but it may be necessary to start another Xgl session on the other display... however this may be problematic due to the DRI support already being used on the other display.

Another solution is to use Xinerama, which gives you the large desktop spanned across both monitors, allowing for window dragging between them.  However, there is a problem with this setup too.  Both monitors need to be the same resolution (won't work for me), and the secondary monitor does not get DRI!  That means compiz won't work on it at all while in xinerama mode.

Yet another solution involves using the open source 'radeon' drivers, and using MergedFB along with Xinerama to enable the DRI on both screens.... however, I think the problem with that is that the radeon driver does not support composite, which is required for compiz.

The last solution is the 'ATI BigDesktop', which is similar to nVidia's 'TwinView' mode.  As of version 8.27.10, this does not support screens of different resolutions.  That was my problem with it, so I was unable to test it with Xgl/compiz to begin with.  I'm not sure if it allows for DRI support on both monitors or not.

There is hope:
The new ATI driver version 8.28.8 which is not in the repo yet looks promising for using the big desktop with two screens of differing resolution, using what is called 'pairmode'.  I haven't tried this myself at all yet, but will definately do so when I have time to fool around with it.

Lastly, I've attached an awesome guide which I found somewhere online, but have been unable to locate it since.  This guide details the many different dual head setups that are possible (aside from BigDesktop) in a very straightforward way, explaining what each is and what it's limitations are.
When I first stumbled into the world of trying to get dual head working on my ATI card, I found all the crazy setups so confusing since I couldn't figure out what each one exactly was doing, or how each needed to be set up.  This guide helped clear the fog, so I'm just throwing it out there.

---

### Post by gubluntu on 2006-09-14
Im in the same boat: ati + compiz/xgl + dual monitors

BigDesktop works fine and i get the two screens going for a regular x session but when trying to get an Xgl session running i get "no screens found" and it backs out to the login screen. I have xgl/compiz running great on just one monitor (second monitor is "cloned" by default).

@TrinitronX : As per your last solution; both of my monitors are the same, does that mean i could get this set up with compiz/xgl but im missing something?

---

### Post by TrinitronX on 2006-09-15
> **gubluntu said:**
> Im in the same boat: ati + compiz/xgl + dual monitors

BigDesktop works fine and i get the two screens going for a regular x session but when trying to get an Xgl session running i get "no screens found" and it backs out to the login screen. I have xgl/compiz running great on just one monitor (second monitor is "cloned" by default).

@TrinitronX : As per your last solution; both of my monitors are the same, does that mean i could get this set up with compiz/xgl but im missing something?

It is possible in theory, however my last experiment while using pairmode and BigDesktop was unsuccessful.  While starting an XGL session from gdm, I got the 'session lasted less than 10 seconds' message.  I don't have the exact detailed error right now, as it's on my home PC in the ~/.xsession-errors file :P.

I finally got BigDesktop working in a normal gnome session using the new pairmode though.  I'm thinking that XGL just crashed horribly the way I was starting it, since a desktop session didn't even start.  Compiz never even got a chance to start.
I'm wondering if there's a special way to start XGL while using BigDesktop, assuming that the DRI extension works in this mode for the big framebuffer.  Perhaps my startxgl.sh script isn't starting it on the right display in this mode?  If DRI is the problem, then again the constraint is the video card drivers.  Hopefully now that ATI and AMD have merged, the Linux drivers will continue to get better.

---

### Post by Trista on 2006-10-21
> **TrinitronX said:**
> To begin, before you even start messing with dual head stuff, make sure compiz will start normally, and that fglrxinfo gives you something like:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.5946 (8.27.10)

```

The method I used to start compiz is the Xgl session method using the startxgl.sh script, and putting compiz-start in System->Preferences->Sessions->Startup Programs.
Make sure you have all dependencies, especially: ```
xserver-xgl
compiz
compiz-gnome (or compiz-kde if you're using kde)
compiz-core
compiz-plugins
csm
cgwd (required if you want to change the window decorations)

```

If you're getting an error when trying to start compiz, make sure your ATI drivers are installed correctly first, and that fglrxinfo does't mention mesa at all.

So... I've been looking for a solution to this ever since I started using compiz back when Dapper was still in development.  ATI really needs to get their drivers up to par, the only way I was able to get a form of dual screen working with my particular setup was with setting up a secondary graphics device in my xorg.conf that pointed to the same bus ID of my 9800pro.  Then, I linked my first monitor to the main device, and the second one to the secondary device.  This setup worked in dual screen mode with 2 different screen resolutions (I've got a widescreen LCD and a VGA monitor, needless to say that the LCD's native resolution is unsupported by the VGA monitor).

The problem: Each screen is a totally separate X session.  Also, when starting compiz, the primary screen will show things normally, and the secondary is just totally blank.  You can move the mouse to the other screen, but you can't do anything.  Not to mention that the window moving to that side of the cube adjacent to the secondary screen will not work.  Your cursor will just drop the window at the edge and continue onto the secondary monitor.  I'm not totally sure, but it may be necessary to start another Xgl session on the other display... however this may be problematic due to the DRI support already being used on the other display.

Another solution is to use Xinerama, which gives you the large desktop spanned across both monitors, allowing for window dragging between them.  However, there is a problem with this setup too.  Both monitors need to be the same resolution (won't work for me), and the secondary monitor does not get DRI!  That means compiz won't work on it at all while in xinerama mode.

Yet another solution involves using the open source 'radeon' drivers, and using MergedFB along with Xinerama to enable the DRI on both screens.... however, I think the problem with that is that the radeon driver does not support composite, which is required for compiz.

The last solution is the 'ATI BigDesktop', which is similar to nVidia's 'TwinView' mode.  As of version 8.27.10, this does not support screens of different resolutions.  That was my problem with it, so I was unable to test it with Xgl/compiz to begin with.  I'm not sure if it allows for DRI support on both monitors or not.

There is hope:
The new ATI driver version 8.28.8 which is not in the repo yet looks promising for using the big desktop with two screens of differing resolution, using what is called 'pairmode'.  I haven't tried this myself at all yet, but will definately do so when I have time to fool around with it.

Lastly, I've attached an awesome guide which I found somewhere online, but have been unable to locate it since.  This guide details the many different dual head setups that are possible (aside from BigDesktop) in a very straightforward way, explaining what each is and what it's limitations are.
When I first stumbled into the world of trying to get dual head working on my ATI card, I found all the crazy setups so confusing since I couldn't figure out what each one exactly was doing, or how each needed to be set up.  This guide helped clear the fog, so I'm just throwing it out there.
I get this in fglrxinfo:

```

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

I don't think I understand the XGL session stuff.  COMPLETE noob.  I am running Ubuntu 6.06, and ATI X700 video card.  I downloaded the latest drivers from ATI, and I do seem to have more speed, but I want my dual monitors to work.  I'm a studying software development and those dual screens are really nice.  But I'm refusing to go back to a windows environment!
Help?

---

