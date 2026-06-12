---
title: "Launcher only launches application once"
date: 2012-05-30
forum: Desktop Environments
---

### Post by pastim on 2012-05-30
I have a few applications on 12.04 which exhibit the following behaviour:

- they run from the Dash fine, every time
- they run from the Classic Menu fine, every time (I'm trying to wean myself off menus, but old habits are hard to break....)
- when I drag an icon from Dash into the launcher and then select one of these applications, it runs fine the first time, BUT only the first time - after that it never runs again from this launcher icon until I reboot, but continues to run OK using all other methods
- if I remove the icon from the launcher and re-create it as above, the application again runs once, and then not again
- if one of these applications has an (ineffective) icon on the launcher, and I reboot, the icon works just the one time again

All the applications which exhibit this behaviour have one other strange characteristic which I am guessing is related.  When running they do not show their own icon with the small 'running' arrows to left or right of the icon in the launcher, but they show another icon with a '?' in it plus the arrows.  So, if one of these applications has a new icon in the launcher, when I select the icon and the application starts, another ('?') icon appears on the launcher with the white arrow beside it.

The applications are as follows?  I have one called 'Squeezeplay' (for Logitech Media Server) which was built elsewhere and did not have a 'proper' installation package.  It had to be moved to /opt manually.  The others are a few Windows applications, installed and running under Wine 1.5, for which I have yet to find a good linux replacement (but I am looking hard).

My application .desktop files for these are much the same as .desktops for other applications which work fine.  The same .desktop files are used by the Dash and Classic menu without difficulty.

Any thoughts out there?  Is there some installation process which is incomplete?  What else can affect the behaviour of such applications on the launcher?

---

### Post by mc4man on 2012-05-30
It's possible that if you create a new .desktop for your wine prog's that they can run & be controlled thru their own unity launcher icon
To try post the current .desktop of one. Also include the actual path to the .exe inc. the exact name of that .exe (or .EXE

---

### Post by pastim on 2012-05-30
> **mc4man said:**
> It's possible that if you create a new .desktop for your wine prog's that they can run & be controlled thru their own unity launcher icon
To try post the current .desktop of one. Also include the actual path to the .exe inc. the exact name of that .exe (or .EXE
I'm not sure what you mean.  However, an example desktop is:

```

[Desktop Entry]
Comment=Play Music from Vortexbox
Exec=/opt/squeezeplay/bin/squeezeplay.sh
Icon=/usr/share/icons/squeezeplay.png
Icon[en_GB]=/usr/share/icons/squeezeplay.png
Name=Squeezeplay Beta
Name[en_GB]=Squeezeplay Beta
Type=Application
Version=1.0
Categories=AudioVideo;Audio;Player;
Terminal=false
Path=/opt/squeezeplay/bin

```

Or:

```

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_GB]=3C17_foobar2000.0
Name[en_GB]=foobar2000
Name=foobar2000
Icon=3C17_foobar2000.0
Exec=env WINEPREFIX="/home/crusty/.wine" wine C:\\\\windows\\\\command\\\\start.exe /Unix /home/crusty/.wine/dosdevices/c:/users/Public/Desktop/foobar2000.lnk
Categories=AudioVideo;Audio;Player;
StartupNotify=true
X-Desktop-File-Install-Version=0.20

```

---

### Post by mc4man on 2012-05-30
> **pastim said:**
> I'm not sure what you mean. 

What I wanted was if you were to browse in nautilus to the .exe the exact path. One reason is it's slightly different on 32 & 64 bit installs

So I'll show you how I'd do foobar2000 on both. 
For starters I'd put the .desktop in ~/.local/share/applications, then drag on to the unity launcher. it doesn't matter if you use your existing or create a new one

So  either move then edit or create a new one.
```
gedit ~/.local/share/applications/foobar2000.desktop
```

for 32 bit

```
[Desktop Entry]
Version=1.0
Type=Application
Name=foobar2000
Exec=wine C:\\\\Program\\ Files\\\\foobar2000\\\\foobar2000.exe
Categories=AudioVideo;Audio;Player;
Path=/home/crusty/.wine/dosdevices/c:/Program Files/foobar2000
Icon=3C17_foobar2000.0
```

For 64 bit install this instead

```
[Desktop Entry]
Version=1.0
Type=Application
Name=foobar2000
Exec=wine C:\\\\Program\\ Files\\ \\(x86\\)\\\\foobar2000\\\\foobar2000.exe
Categories=AudioVideo;Audio;Player;
Path=/home/crusty/.wine/dosdevices/c:/Program Files (x86)/foobar2000
Icon=3C17_foobar2000.0

```

After creating or editing the existing  then drag & drop on to launcher, if icon doesn't show then do a log out/in

It's also possible to to create a DnD launcher for foobar2000 & or right click option that opens a file directly in it. BUT it can't be used to start fooobar2000 due to the command needed. More useful as a r.click option because you really wouldn't want to inadvertantly try to start foobar with it.

screen shows foobar running in it's own icon which will persit

---

### Post by pastim on 2012-05-31
Thanks very much.  I don't quite understand why your version works and mine doesn't, but the volume of stuff I don't understand is never small!

> **mc4man said:**
> 
It's also possible to to create a DnD launcher for foobar2000 & or right click option that opens a file directly in it. BUT it can't be used to start fooobar2000 due to the command needed. More useful as a r.click option because you really wouldn't want to inadvertantly try to start foobar with it.
Apologies, but this is another example of something I don't understand.  What's a DnD - I've never seen that acronym before?  What right click option are you referring to?

---

### Post by pastim on 2012-05-31
Whilst your .desktop changes fix foobar, they don't fix my other program - squeezeplay.

This is run via a .sh file which sets various paths up before running the actual program, as follows:

```

#!/bin/sh

##
## This script is a basic startup script for the SqueezePlay binary (jive) that requires a few environment variables be set.
##

## Change these if you changed your install path
INSTALL_DIR=/opt/squeezeplay/
LIB_DIR=$INSTALL_DIR/lib
INC_DIR=$INSTALL_DIR/include

## Start up
export LD_LIBRARY_PATH=$LIB_DIR:$LD_LIBRARY_PATH
export LD_INCLUDE_PATH=$INC_DIR:$LD_INCLUDE_PATH
export PATH=$PATH:$INSTALL_DIR/bin

cd $INSTALL_DIR/bin
ALSA_CONFIG_PATH=/usr/share/alsa/alsa-nopulse.conf ./jive

```
Do you have any idea why your fix would not work for such a program?  The program does run quite happily, it just won't stick in the launcher and stay working from there.

---

### Post by mc4man on 2012-05-31
I've no idea ATM about squeezeplay, don't have it here, the solution I posted before was _for wine programs only_
 it's possible that this happens - 

The launcher calls a script, squeezeplay.sh, the script then opens the program separately so there is no association to the orig. launcher icon
Is squeezeplay available to look at here?

DnD means drag & drop

---

### Post by pastim on 2012-05-31
> **mc4man said:**
> I've no idea ATM about squeezeplay, don't have it here, the solution I posted before was _for wine programs only_
 it's possible that this happens - 

The launcher calls a script, squeezeplay.sh, the script then opens the program separately so there is no association to the orig. launcher icon
Is squeezeplay available to look at here?

DnD means drag & drop
Thanks.

What I'd like is to find some documentation somewhere about .desktop files, and the way applications that might be invoked, that would help me to solve this one myself.  squeezeplay is but one application that I might want to install one day, and I want to see if I can understand some basic principles.  

So in this case, can I in some way associate an application invoked from within a script with a launcher icon?

---

### Post by mc4man on 2012-05-31
If I find a link to .desktops will post - 
For sqeezebox try this - 
1st I'd remove the icon from from unity launcher if it's there & log out/in just to clean up 

Then i'd probably place the .desktop in ~/.local/share/applications/
After that open in a text editor & add this line to the bottom 

```
StartupWMClass=jive
```

Save, then drag the .desktop on to the unity launcher & try out

---

### Post by pastim on 2012-06-01
> **mc4man said:**
> If I find a link to .desktops will post - 
For sqeezebox try this - 
1st I'd remove the icon from from unity launcher if it's there & log out/in just to clean up 

Then i'd probably place the .desktop in ~/.local/share/applications/
After that open in a text editor & add this line to the bottom 

```
StartupWMClass=jive
```

Save, then drag the .desktop on to the unity launcher & try out
Thanks very much.  I thought I had already replied, but maybe I failed to complete the process.  

Your addition did part of the job, but I still got a second icon coming up, this time with the correct .png picture rather than a '?', with the white arrows.  The original icon still failed to work a second and subsequent times.

However, also adding:

```

StartupNotify=true

```

did the trick. The icon now sticks to the launcher, shows the appropriate arrows whilst the program runs, and works each time I press it.

I just wish I could find some information to help me work such things out rather than trying random changes (albeit well informed based on information form such as yourself).  Still, all's well that ends well :-)

---

### Post by mc4man on 2012-06-01
You can get some info here, maybe you can find additional
[http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html)

You can also open existing installed ones to get somen idea's ect.

I tend to work out just using some logical trial & error, don't think I've needed StartupNotify=true for StartupWMClass to be effective but generally that line isn't an issue


If you're going to spend much time with .desktops and or quicklists ect. you may want to set up a nautilus action or 2

I always put in 2 right away on a new install - 
Open desktop file
Open desktop file as Root

NA lets you set an action using basename so the above will only show in the context menu for .desktop's

---

### Post by pastim on 2012-06-01
> **mc4man said:**
> You can get some info here, maybe you can find additional
[http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html)

You can also open existing installed ones to get somen idea's ect.

I tend to work out just using some logical trial & error, don't think I've needed StartupNotify=true for StartupWMClass to be effective but generally that line isn't an issue


If you're going to spend much time with .desktops and or quicklists ect. you may want to set up a nautilus action or 2

I always put in 2 right away on a new install - 
Open desktop file
Open desktop file as Root

NA lets you set an action using basename so the above will only show in the context menu for .desktop's

There's a enormous information gap here, and I am not asking you to try & fill it.  I will, however, briefly show just how ignorant one can be and still get stuff to work.

The problem with the spec is that it means little to a user, rather than an expert.   I still have no understanding of what these 2 additions mean, even though I have read the words.  So, for instance, StartupWMClass still means nothing to me.  If it is needed and works, fine, but why a 'WM Class' has anything to do with the executable name is unfathomable.

In addition, I have absolutely no idea what Nautilus actions, or quicklists, are.  In fact I don't really know what Nautilus is.  It may surprise many linux people to know that it is quite possible to use a system without much understanding of what it elements are called or how it really works.  I cannot begin to explain just how much information I don't have!

I worked on my first IT system in 1971, but didn't touch linux until last year and still very much as a user, not as a programmer.  There is simply too much to learn.

Never mind, I now have something working.  Time to move on to the next problem!

---

### Post by pastim on 2012-06-04
> **mc4man said:**
> You can get some info here, maybe you can find additional
[http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html)

You can also open existing installed ones to get somen idea's ect.

I tend to work out just using some logical trial & error, don't think I've needed StartupNotify=true for StartupWMClass to be effective but generally that line isn't an issue


If you're going to spend much time with .desktops and or quicklists ect. you may want to set up a nautilus action or 2

I always put in 2 right away on a new install - 
Open desktop file
Open desktop file as Root

NA lets you set an action using basename so the above will only show in the context menu for .desktop's
Thanks.  I managed to work out what some of this means.  The NA had me fooled for ages (acronyms are like that), thinking it meant Not Applicable.

Having worked out that Nautilus Actions was something I needed to install I did so, and got the basic version working for me as a default user.  To be able to edit one belonging to root (in /usr/share/applications...) I finally worked out I needed to use gksudo (I have always used sudo in the past from a terminal).

However, whilst it does open the file (I'm using gedit) it also opens an extra untitled document. I have seen that you and others appear to have reported this as a fault in 12.04 (and some other versions).  Have you managed to find a work-around?

---

