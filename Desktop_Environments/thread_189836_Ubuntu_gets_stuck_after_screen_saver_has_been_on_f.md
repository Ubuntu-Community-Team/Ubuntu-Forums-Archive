---
title: "Ubuntu gets stuck after screen saver has been on for a long time"
date: 2006-06-05
forum: Desktop Environments
---

### Post by Wormsie on 2006-06-05
I got back from work today, and my Ubuntu desktop had become stuck again. It seems that if I leave my PC on for hours, the screensaver will lock up and although the PC is on, there's absolutely no way to wake it up again it seems. I've turned all "turn hard disk off" and "turn monitor off" and such options off. I only have the screensaver, which seems to cause the lockup.

The screensavers in Dapper Drake are pretty, so I'd like to keep them on, and I wouldn't want to shut down my PC when I go away for hours (because of my server, torrents, etc) so is there anything I could do?

---

### Post by shamrock_uk on 2006-06-05
You could try switching your screensaver and see if that eliminates the problem. 

sudo apt-get remove gnome-screensaver 
sudo apt-get install xscreensaver-gl

It may say that it wants to remove ubuntu-desktop, that's fine, it's not a real package. 


If you don't want to do that, then what about trying a console - 

see if you can do Ctrl+Alt+F1 when the computer appears to be frozen. If you still get nothing, then do Alt + SysReq + R and try it again. 

If you can get to a console then you can probably kill the offending screensaver from there. Have you tried checking the log files? (System -> Administration -> System Log)

One other thing to check - does it only happen when you've selected gl screensavers (ie the very pretty 3d accelerated ones)? That might indicate a graphics driver problem.

---

### Post by Hezekiah on 2006-06-05
The problem may also stem from buggy 3D drivers, if you're using any of the OpenGL screensavers available.  I have an NVIDIA on my desktop, and the drivers would cause crashes sometimes in similar situations to what you have described.

It may be worth fixing the screensaver on something which doesn't use OpenGL and leave it on for the day to see how it goes.

---

### Post by Wormsie on 2006-06-07
Seems to be working better now - and I got more functionality with that old screensaver dialog.

---

### Post by Hezekiah on 2006-06-07
If the xscreensaver version works for you where gnome-screensaver doesn't, please submit a bug!  The switch to gnome-screensaver was somewhat controversial from what I saw - as you pointed out the old version has many more options and works much better on some systems.

---

### Post by shamrock_uk on 2006-06-07
If you do bugreport though, it's important to test it with the exact same screensavers that were freezing the old one first to make sure it's not a problem with something else.

xscreensaver is no longer being maintained by its developer (so I think it's in universe these days) . gnome-screensaver is the actively developed replacement, but it's still relatively young so I guess is more likely to have the occasional glitch. 

Glad it's fixed :-)

---

### Post by Peepsalot on 2006-06-07
I installed Ubuntu 6.06 with gnome, and then later decided to siwtch to xubuntu-desktop.  I also have this problem with screensavers crashing my computer.  I can't even find where the screensaver settings are for xfce.  I ran gnome-screensaver-preferences and I'm pretty sure I have disabled that completely.  

I almost tried the suggested sudo apt-get remove gnome-screensaver, but it says it would also remove ubuntu-desktop along with it.  I am afraif that would break things even more, so I chose not to do that.  Can anyone help me find the xfce screensaver settings?  I think it always crashes on a screen that shows chess pieces.

---

### Post by shamrock_uk on 2006-06-08
As I mentioned above, ubuntu-desktop isn't a real package. 

Uninstalling it won't harm your system in any way - it's what is called a meta-package: essentially a link to lots of other packages. It just means a user can install one package, ubuntu-desktop, without having to install all the packages individually. Removing it therefore will not remove any proper software. 

The chess screensaver is OpenGL, I suggest you try setting it to something very simple and non-3d accelerated.

---

### Post by bikeman on 2006-06-08
I was having a similar problem with the screensavers until I found [this]("http://ubuntuforums.org/showthread.php?t=119328&highlight=screensaver+lockup") thread.  The part that worked for my was:

"My solution was to add a line to the "Device" section of the xorg.conf file. The line I added is in bold (the entire Option line):
Code:
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9000 Pro (RV250 If)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	**Option "AGPMode" "4"**
EndSection

Of course, I happen to have a Radeon 9xxx series video card as well.  Thanks to PatrickMay16 for this most excellent and working (for me) fix.  I did not need to change my BIOS setting as noted in the thread.  Good luck!

---

### Post by Peepsalot on 2006-06-09
Well, i removed gnome-screensaver, but apparently xfce is running off something else, cause i still have a screensaver.
Can anyone just tell me how to pick what screensaver to show?  It is set to random right now.  I don't know where the list of screensavers is or if a configuration utility exists for xfce.

---

### Post by Peepsalot on 2006-06-10
Nevermind, I'm a dumbass.  The screensaver settings can be reached from the menu -> Settings -> Settings Manager.  For some reason I never clicked that setting manager before.  I guess I kinda thought that was the title of the submenu, especially since every other icon is in alphabetical order but that one.

I think the way that menu is layed out is very confusing.  Some of the settings are in both the settings manager, and in the menu, while others are only in one or the other.

---

### Post by Peepsalot on 2006-06-10
The following screensavers were locking up my system instantly(even in preview mode):
Antspotlight
Flipscreen3d
GFlux(grab)
Pulsar(textures)
even the act of unchecking these would lock up my system, since it would automatically preview them when you do that. I found that uncheking and quickly selecting another screensaver would let me change the setting without giving enough time for the preview to load and crash my computer.

Edit 6/12/2006: I also had to disable "atunnel" and "glknots".   My computer lasted through one day of me being at work(9hrs) so far. That's the most stable it's been with Ubuntu yet! :razz: 

I might try to install the remaining screensavers later, and test compatibility with those. For now I think I will test this configuration for stability and make sure this is good.  All the screensavers I have chosen now do not instantly lock up my computer, but who knows if they might over time.  Only one way to find out.

Where would the best place be to report my hardware compatibility issues?

---

### Post by Wormsie on 2006-06-10
I was wrong, today the screensavers managed to freeze my system again. So it's probably 3D related as speculated earlier.

---

### Post by tseliot on 2006-06-10
[QUOTE=Wormsie]I was wrong, today the screensavers managed to freeze my system again. So it's probably 3D related as speculated earlier.[/QUOTE]
Reinstall the drivers for your graphic card. That might solve your problem.

---

### Post by Wormsie on 2006-06-13
Turning off OpenGL screensavers helped. I have no idea how to reinstall a driver (since I didn't install it in the first place), but I'll try to find out how to do it. ;)

---

### Post by usererror on 2006-06-22
[QUOTE=bikeman]I was having a similar problem with the screensavers until I found [this]("http://ubuntuforums.org/showthread.php?t=119328&highlight=screensaver+lockup") thread.  The part that worked for my was:

"My solution was to add a line to the "Device" section of the xorg.conf file. The line I added is in bold (the entire Option line):
Code:
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9000 Pro (RV250 If)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	**Option "AGPMode" "4"**
EndSection

Of course, I happen to have a Radeon 9xxx series video card as well.  Thanks to PatrickMay16 for this most excellent and working (for me) fix.  I did not need to change my BIOS setting as noted in the thread.  Good luck![/QUOTE]

sadly that did line did not help me with my locking up screensaver (even in preview mode), no more GL screensaver usage. ](*,)

---

### Post by Peepsalot on 2006-06-22
I ended up completely disabling screensavers.  Even the most basic ones would eventually lock up my computer.  Not worth the effort going through countless freezes trying to find a stable one. :(

---

### Post by unclben on 2006-06-24
I, too, am having screensaver locks in Dapper. I've been previewing the different screensavers in alphabetical order; so far, colorfire and flux (Gflux works fine) lock me up. I can stilll move the mouse around, but the system is totally unresponsive. Not even ctrl-alt-bksp or ctrl-alt-del will do anything.

---

### Post by warjowuch on 2006-07-14
Hi there,
Just searching today for this problem and found this topic.
Too bad, has anyone filed a bug yet at launchpad?

This is quite a sucky problem, lost quite some information because of this...

Also on a Radeon 9200SE... others too?
Might it be related to de libGL.so.1.2 problem in the Ati-drivers, or is it also on Nvidea and other Ati-cards?

---

### Post by unclben on 2006-07-14
> **warjowuch said:**
> Also on a Radeon 9200SE... others too?
Might it be related to de libGL.so.1.2 problem in the Ati-drivers, or is it also on Nvidea and other Ati-cards? I'm using a Radeon 9800. I have not submitted a bug in Launchpad.

---

