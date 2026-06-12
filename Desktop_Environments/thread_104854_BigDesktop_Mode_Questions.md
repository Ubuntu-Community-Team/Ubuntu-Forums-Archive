---
title: "BigDesktop Mode Questions"
date: 2005-12-17
forum: Desktop Environments
---

### Post by dk_pa on 2005-12-17
I am using the ATI Drivers and "BigDesktop" mode with my dual monitors.  I have two questions to ask about it...

First...I can't set a background on each of them.  I would imagine this is because it is, in fact, "one big desktop" but was wondering if there is anyone around this --- Other than putting two images together that work out to be 2560x1024 or whatever it is.

Also,  games that try to go full screen can't.  They will push fullscreen to the middle of both displays (I would imagine interpreting that as the middle of "THE" display) and then just sit there.  I could get some games working that would let me use a switch for window mode but others I'm not sure if I can.  

I would imagine there is a way to force a program to run in windowed mode but is there a way to force an application to full screen to one side or the other.  Kinda like how one might pull FireFox to the right side and go full screen with it now being on the right monitor.  

I would like to try some full blow Linux gaming down the road (like UT etc) but I figured I should get things out of the way / worked around first.  Thanks for any help.

---

### Post by dk_pa on 2005-12-18
Hate to do it but...bumpity bump =)

---

### Post by SculptusPoe on 2007-07-01
I have the exact same problem. Here are my posts from the BigDesktop thread. Hopefully there is a better answer than the one I found, which requires using an alias shortcut to use aticonfig to change --desktopsetup to single mode without making a backup and then {ctrl alt <--}. 

[http://ubuntuforums.org/showthread.php?t=301941]("http://ubuntuforums.org/showthread.php?t=301941")


> **SculptusPoe said:**
> Your walk-through for the ATI Big-Desktop worked first try with only one major problem so far.

I am running dual CRTs with a Radeon X1050

Everything works fine until I try to run a program like Neverball , then the display runs out of the program window. This seems to happen with any 3D game. If I switch back to clone the display works again. 

I wouldn't mind so much except that there is no fast way to turn on/off the display option. I can disable a single monitor and turn it back on. But that doesn't fix the problem.

Is there any way to get the DesktopSetup to switch between horizontal and clone on the fly? It doesn't appear so.

[EXAMPLE_PIC]("http://server6.theimagehosting.com/image.php?img=Screenshot-Neverball.png")







Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "on"
	Option	    "DesktopSetup" "horizontal,reverse"
	Option	    "Capabilities" "0x00000800"
	Option	    "PairModes" "0x0+0x0"
	Option	    "EnableMonitor" "crt1,crt2"
	Option	    "ForceMonitors" "crt1,crt2"
EndSection

> **SculptusPoe said:**
> I stuck 
```

alias DSoff='sudo aticonfig --desktop-setup=single --nobackup'
alias DSon='sudo aticonfig --desktop-setup=horizontal,reverse --nobackup'

```
in .bashrc and that works quickly enough for now after a {ctrl alt <--}

---

