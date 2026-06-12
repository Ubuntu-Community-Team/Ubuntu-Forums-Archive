---
title: "Ubuntu 9.10 Desktop All Black at 1280x1024"
date: 2009-10-31
forum: Desktop Environments
---

### Post by umaxtu on 2009-10-31
Ok I have a weird problem. On a fresh install of Ubuntu 9.10 I started it up to find a blank desktop no background, no icons and newly created files and folders don't show either but the rest of the ui was their and the graphics effects worked. After further experimentation I found that the desktop worked at lower resolutions at 75hz.

The graphics card is some Radeon 7000 i found lying around in my basement and It handles 1280x1024 fine on Windows.

Any Idea?

---

### Post by mugwump40 on 2009-10-31
Hi....I have a similar problem.  On a fresh install, I get as far as entering my user name and password and then get a message that the screen resolution must be 1280 X 1024.  It then locks up and I have to power off to clear.  BTW, the screen res already is 1280 X 1024.  AMD 64 X2 5200 processor, GeForce 6150SE video card, 4096 MB system memory.  From what I've observed so far, there are some real speed bumps in 9.10

---

### Post by Rubicon421 on 2009-11-01
umaxtu, I'm having the same issue. Mugwump40, your issue sounds like something else and may not be the same solution. 

I also have a Radeon card, it's the 9200. I have a 22" wide screen. The Ubuntu display manager senses the monitor and sets the display to 1680 X 1050 (16:10) by default. That is when I have the issue. If I change to any other available resolution (which are all lower and in 4:3 aspect) then it works fine. 

I noticed that I can still see a tiny part of my background through the transparent panel I have at the bottom. I can tell when I change backgrounds. Other than that little part, the background is all black when I have the display set to 1680 X 1050. This is the only available resolution that 'fills the screen' on my wide screen. The other ones look like crap and I'd really like to get it working on the right setting for my monitor. 

Sorry I don't have a solution to offer but I thought the extra details might help one of the guru's on here figure it out for us :)

---

### Post by KernelKen on 2009-11-01
Well I have the same problem however I did an upgrade from 9.04 to 9.10 and now have the same black screen.  I also have one other problem I didn't see mentioned and that is I can't see any window when it is full screen, i.e. firefox when shrunk to about two-thirds the size of the screen I can see it.  Stretch it bigger and it is black.

---

### Post by beesblaas on 2009-11-02
I have the same problem after upgrading to 9.10, black screen,
i.e. I can see the toolbar menu at the top, but where my icons usually are, there are none.
(they are actually there, but you cant see them, since when I try to create another shortcut
it says that it already exist)
Opening applications like Firefox in the black desktop area- the firefox window itself is fine.

Interestingly, if I log in as another user, the desktop is fine in all aspects!
The bad desktop is the user from which I upgraded.

Both users has the same video settings, i.e. 1920 x 1080.

So it is not this video setting, it is something else.

OK, SOLUTION: (from another mail in the forum)
=================================
Turn visual effects off, it works immediately.
right-Click on any area on your desktop, get pop-up window, select "change desktop background",
select "Visual Effects", select "None",
fixes it!

---

### Post by tormod on 2009-11-02
Make sure you report your issues in the bug tracker. If you have a Radeon card, "**ubuntu-bug xserver-xorg-video-ati**" is the best way to start filing a bug. Please also report how much video memory you have on your card.

First, check which acceleration you are using:
 **grep XAA /var/log/Xorg.0.log**
 **grep EXA /var/log/Xorg.0.log**
EXA has now replaced XAA as the default, except for cards with little memory. However there are some issues with XAA, so there are two things to try if your card runs XAA:

A. Disable RenderAccel, by creating an /etc/X11/xorg.conf with this:

```
Section "Device"
 Identifier "my-radeon"
 Driver "ati"
 Option "RenderAccel" "off"
EndSection
```

B. Force the use of EXA instead:

```
Section "Device"
 Identifier "my-radeon"
 Driver "ati"
 Option "AccelMethod" "EXA"
EndSection
```

One other thing to try for low-memory cards is to reduce the virtual screen size to what you are actually using:
```
Section "Device"
       Identifier "my-radeon"
       Driver "ati"
EndSection

Section "Screen"
       Identifier "my-screen"
       Device "my-radeon"
       # DefaultColorDepth 16
       SubSection "Display"
               Virtual 1024 768
       EndSubSection
EndSection
```

Change the Virtual parameters to your screen resolution, of course. Note that by further uncommenting the DefaultColorDepth line you will get fewer colors but even less memory is needed (depth 24 is default).

On the other hand, for AGP cards with decent amounts of video RAM, increasing the AGPSize might help. Run **grep "GART aperture" /var/log/Xorg.0.log** to see the default value.
```
Section "Device"
 Identifier "my-radeon"
 Driver "ati"
 Option "AGPSize" "128"
EndSection
```
The number "128" has to be tuned for your hardware, try 16, 32, 64, 128 up to the amount of video RAM that you have. Higher numbers will reserve more system memory, so just set it as high as you need.

Finally, one can try KMS (Kernel mode-setting) which enables a video memory manager and DRI2 (for 3D rendering). This will be default in future releases, so this is where most development is focused. See [https://wiki.ubuntu.com/X/RadeonKMS](https://wiki.ubuntu.com/X/RadeonKMS) for how to try it.

---

### Post by philferrar on 2009-11-02
Brilliant solution - works a treat. Many Thanks.

---

### Post by Rubicon421 on 2009-11-02
tormod, could you explain how to use the code you provided? I'm new to Linux. I know how to use the terminal but I think you're talking about something else and I don't know how/where to use it.

Thanks

---

### Post by philferrar on 2009-11-02
> **Kill Vista said:**
> tormod, could you explain how to use the code you provided? I'm new to Linux. I know how to use the terminal but I think you're talking about something else and I don't know how/where to use it.

Thanks

The solution is easy - don't need to use terminal.

Turn visual effects off, it works immediately.
right-Click on any area on your desktop, get pop-up window, select "change desktop background",
select "Visual Effects", select "None",
fixes it!

---

### Post by Rubicon421 on 2009-11-02
> **philferrar said:**
> The solution is easy - don't need to use terminal.

Turn visual effects off, it works immediately.
right-Click on any area on your desktop, get pop-up window, select "change desktop background",
select "Visual Effects", select "None",
fixes it!


yes, but I want to keep visual effects enabled. I don't want the problem to go away because I turned off the feature that's not working. I want to fix that feature and keep using it.

---

### Post by philferrar on 2009-11-02
> **Kill Vista said:**
> yes, but I want to keep visual effects enabled. I don't want the problem to go away because I turned off the feature that's not working. I want to fix that feature and keep using it.

Sorry - didn't realise you needed to keep effects - perhaps someone else will provide a full solution soon.

---

### Post by dwasifar on 2009-11-02
[11/06/2009 - Editing to add newer options.]

> **Kill Vista said:**
> yes, but I want to keep visual effects enabled. I don't want the problem to go away because I turned off the feature that's not working. I want to fix that feature and keep using it.

I agree with you.  "Stop using it" is not a fix.  :)

I'm having the same issue on an old Dell laptop with an ATI Radeon RV250 (Mobility FireGL 9000) running a 1400x1050 panel.  When I moved this machine to Karmic, my desktop was black, with no desktop items appearing on it; but you could see the desktop wallpaper beneath the semi-transparent top panel.

In my case, the fix was exactly the opposite of what tormod described.  Here's how to do it, step by step.

In terminal, run these two commands:

```
grep XAA /var/log/Xorg.0.log
grep EXA /var/log/Xorg.0.log
```

One of them will return nothing; the other will return something like this:

```
(**) RADEON(0): Option "AccelMethod" "XAA"
(**) RADEON(0): Using XAA acceleration architecture
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
```

This tells you which method is currently in use on your system.  Whichever one it is, try the other.  For me it was EXA, and switching to XAA solved the problem.  Here is what to do.

**If it reported XAA:**

In terminal, do this:

```
sudo gedit /etc/X11/xorg.conf
```

This will give you a text editor window.  Paste this into the text editor:

```
Section "Device"
 Identifier "my-radeon"
 Driver "ati"
 Option "AccelMethod" "EXA"
EndSection
```

Save, and reboot, and see if the problem is solved.


**If it reported EXA:**

In terminal, do this:

```
sudo gedit /etc/X11/xorg.conf
```

This will give you a text editor window.  Paste this into the text editor:

```
Section "Device"
 Identifier "my-radeon"
 Driver "ati"
 Option "AGPSize" "128"
EndSection
```

Then save the file and exit the editor, and reboot.

If the problem still isn't solved when you have rebooted, open the file in text editor again, and change it to look like this:

```
Section "Device"
 Identifier "my-radeon"
 Driver "ati"
 Option "AccelMethod" "XAA"
EndSection
```

Then save the file and exit the editor, and reboot.

Both of these solved the problem for me.  The first one (with the AGPSize option) is the preferred choice and will result in better performance.

Post back and let us know if it fixes it for you.

---

### Post by tormod on 2009-11-02
I would not qualify disabling desktop effects as a fix, that's a workaround like wiping something under the carpet. These things are supposed to work on all Radeon cards.

The code I posted is supposed to go into a /etc/X11/xorg.conf file that you create. I am sure you can search and find some guides on how to create and edit text files.

EDIT: Oops, I did not see the last posts. Thanks for explaining.

---

### Post by mugwump40 on 2009-11-02
All the "Fixes" may work for someone that can even get the system to boot, but there is something in the latest Debian core that absolutely will not work on my desktop.  I even downloaded Debian and tried to install it and it died at the exact same spot as UBUNTU.  I get the message that my display MUST be set to 1280 X 1024 and then it locks up.  BTW, the display IS set to 1280 X 1024.  My setup:  HP Pavilion Slimline s3521p, AMD 64 X2 5200 processor, GeForce 6150SE graphics, 4096 Mb system memory, HP DVD RW, 500 Gb HD.  The install wiped out my UBUNTU 9.04, so I guess my best bet is just to reload that and wait for this to get fixed.  Thankfully, I'm running dual boot with Win XP, so I can still get into that.

---

### Post by AvgOrdinaryGuy on 2009-11-02
Just want to say thanks to dwasifar for posting that how-to above.  I just installed 9.10 this afternoon, and could not figure out why I only had a black background and could not change it to any thing else.  Turning off desktop effects fixed that, but changing to XAA fixed the problem on my A31P Thinkpad with 64MB Radeon graphics.

---

### Post by non-prophet on 2009-11-02
> **beesblaas said:**
>  ...........

OK, SOLUTION: (from another mail in the forum)
=================================
Turn visual effects off, it works immediately.
right-Click on any area on your desktop, get pop-up window, select "change desktop background",
select "Visual Effects", select "None",
fixes it!

The "Visual effects - none" temporary fix **worked well for me**. 

(Reduction from 1680 x 1050 down to 1440 x 900 also worked but I prefer the resolution over the visual effects.) 

Thanx guys.

---

### Post by dwasifar on 2009-11-03
> **mugwump40 said:**
> All the "Fixes" may work for someone that can even get the system to boot...

If you're not even booting, then this is not the same problem.

---

### Post by dwasifar on 2009-11-03
> **AvgOrdinaryGuy said:**
> Just want to say thanks to dwasifar for posting that how-to above.  I just installed 9.10 this afternoon, and could not figure out why I only had a black background and could not change it to any thing else.  Turning off desktop effects fixed that, but changing to XAA fixed the problem on my A31P Thinkpad with 64MB Radeon graphics.

You're welcome, but tormod deserves the thanks more than I do.  He solved the problem, not me; I just explained his technique in more detail.

---

### Post by emptybox on 2009-11-03
> **dwasifar said:**
> You're welcome, but tormod deserves the thanks more than I do.  He solved the problem, not me; I just explained his technique in more detail.

Well the technique worked for me as well. :D

I changed from EXA to XAA, and I can now enable the 3D effects using my Radeon 9200SE with 128MB **and** keep my desktop.

I think rotating the cube might be slightly less smooth than with 9.04?
But wobbly windows etc now work fine.

Do we know why this happened, and why for this specific card?
Did the developers drop support for it from the default driver, or is it some other issue?
I suppose it **is** an old card, but it had always been my most trouble free with Linux, up to now. :(

---

### Post by Rubicon421 on 2009-11-03
Thanks [dwasifar]("http://ubuntuforums.org/member.php?u=59966"), this worked perfectly! I did notice that my graphics are a bit choppy when using the desktop effects now though. They were very smooth when using the desktop cube and minimize effect etc... before when I was using 9.04. Any ideas on how to fix that?

---

### Post by Rubicon421 on 2009-11-03
> **emptybox said:**
> Well the technique worked for me as well. :D

I changed from EXA to XAA, and I can now enable the 3D effects using my Radeon 9200SE with 128MB **and** keep my desktop.

I think rotating the cube might be slightly less smooth than with 9.04?
But wobbly windows etc now work fine.

Do we know why this happened, and why for this specific card?
Did the developers drop support for it from the default driver, or is it some other issue?
I suppose it **is** an old card, but it had always been my most trouble free with Linux, up to now. :(


Worked for me too but then I also noticed the effects were less smooth. Let me know if you find a fix for that. I thought about using the Envy program to install a different driver or just using synaptic to install anything ATI related that I don't already have.

---

### Post by tormod on 2009-11-03
EXA should work fine with 128MB of video memory, and is generally faster than XAA. The developers are also focusing on EXA and will not have time to improve the XAA stuff. It is therefore useful to try diagnose this EXA issue further, so that you can use EXA in a later release or update.

"man exa" lists four options that you can try. For MigrationHeuristic the "greedy" value has solved some issues, but I don't know if will help here. Once you have tried this out, it is time to file a bug report.

---

### Post by dee02 on 2009-11-03
:popcorn:> **dwasifar said:**
> I agree with you.  "Stop using it" is not a fix.  :)

I'm having the same issue on an old Dell laptop with an ATI Radeon RV250 (Mobility FireGL 9000) running a 1400x1050 panel.  When I moved this machine to Karmic, my desktop was black, with no desktop items appearing on it; but you could see the desktop wallpaper beneath the semi-transparent top panel.

In my case, the fix was exactly the opposite of what tormod described.  Here's how to do it, step by step.

In terminal, run these two commands:

```
grep XAA /var/log/Xorg.0.log
grep EXA /var/log/Xorg.0.log
```

One of them will return nothing; the other will return something like this:

```
(**) RADEON(0): Option "AccelMethod" "XAA"
(**) RADEON(0): Using XAA acceleration architecture
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
```

This tells you which method is currently in use on your system.  Whichever one it is, try the other.  For me it was EXA, and switching to XAA solved the problem.  Here is what to do.

In terminal, do this:

```
sudo gedit /etc/X11/xorg.conf
```

This will give you a text editor window.  If the first step reported that you were using XAA, paste this into the text editor:

```
Section "Device"
 Identifier "my-radeon"
 Driver "ati"
 Option "AccelMethod" "EXA"
EndSection
```

If the first step reported that you were using EXA, paste this into the text editor instead:

```
Section "Device"
 Identifier "my-radeon"
 Driver "ati"
 Option "AccelMethod" "XAA"
EndSection
```

Then save the file and exit the editor, and reboot.

This solved it for me.  Post back and let us know if it fixes it for you.

OMG IT WORKED THANK YOU ...........WOOOOOOOOW U the MAN!!!

---

### Post by KingStill on 2009-11-03
Switching to XAA correctly enables all effects on my radeon 9200, but it's too slow. EXA effects are higher performance but past certain screen resolution/window size, it blacks out. It's either bugs and/or my hardware is just ancient. Thanks for helping.

---

### Post by Luis-for-um33 on 2009-11-04
My Gnome desktop background image has disappeared

Yesterday, under Jaunty Jackalope, the background image was just fine. Today (11-2-09) I upgraded to Ubuntu 9.10 (Karmic Koala) and I noticed that the image I had as background had been replaced by a black screen. Now I cannot display any of my background images. The "Appearance Preferences" app doesn't seem to be working. Does anybody have a clue as to how to make it work?

PS: I followed the instructions somebody in the Forum gave, but they didn't work for me: 
[Press <ALT>F2 and type gconf-editor. In the left hand pane click desktop, then gnome, then background. Click draw_background and the wallpaper should return.]

PS: I realized this morning (11-3-09) that the background image is indeed on the desktop; but it just cannot be seen.

If I move the mouse over the desktop and click the right button in the area where the image should be, the drop down menu tells me that there is an image there because I can open it in the image viewer.

Also, if I move the mouse over to the top left of the screen and press the right button, I get evidence that the two pdf files I had on the desktop before I made the upgrade to Ubuntu 9.10 are still there; just invisible.

PS: I just discovered something else: after the background images disappeared (as explained above), but the top menu panel and the bottom panel are still visible; but if I press F11 (Full Screen) while in Firefox, the browser itself becomes invisible and the entire screen goes blank (well, actually, it goes black).  (11-3-09 @ 2251)

Just what could be causing all this?

If I cannot fix this problem, how can I reverse the upgrade? Can I go back to Ubuntu 9.04?

I use an ATI Radeon 9200 AGP 8X video card, inside an MSI KT3 Ultra mobo, with an AMD Athlon XP 1700 CPU, with 2GB RAM.

Thanks for any help anybody can provide.

Luis

---

### Post by Luis-for-um33 on 2009-11-04
Well, people, I got my desktop back!

I'm not sure what I did to repair it. I simply re-started the computer, went into the BIOS' Advanced Chipset Features, re-apportioned the RAM for the "AGP Aperture Size" from 128 MB to 4MB and enabled the AGP's Write, Read & Synchronization from Disabled to Enabled. 

I cannot believe this did the trick. I probably just got lucky and Ubuntu was in a good mood this time. I hope it holds.

By the way, I said earlier that the RAM was 2GB; but the POST reports only 1GB. So, maybe Ubuntu was thirsty for more. 

Thanks for listening!

Luis

---

### Post by thedogisdead on 2009-11-04
I'm having the same problem, too!  I've got a very similar set-up to Luis... same graphics card and such.

Thanks for the (initial) fix, though!  I tried it and it worked a treat, apart from the poor performance as described above.

I've gone back to 'no effects' for now, though!

I know none of you are mind readers, but in your experience, is this something that is likely to be fixed?  Are bug fixes rolled out with the rest of the updates?

I can't pretend to be as down on Karmic as lots of others, but this bug has kinda spoiled my transition to an Ubuntu only machine.  D'oh!  Never mind, I'm sure it'll be worked out!

---

### Post by andey on 2009-11-04
> **philferrar said:**
> The solution is easy - don't need to use terminal.

Turn visual effects off, it works immediately.
right-Click on any area on your desktop, get pop-up window, select &quot;change desktop background&quot;,
select &quot;Visual Effects&quot;, select &quot;None&quot;,
fixes it!

  thanks but, it was working in 9.04, but not in 9.10 for some reason. Whatever I can live with it.

---

### Post by tormod on 2009-11-05
Everybody, please read my comment 22. This issue can not be fixed without your input.

---

### Post by thedogisdead on 2009-11-05
Tormod - thanks for your responses.  Any chance you could give a bit more detailed instruction on how to try those four different options you mentioned?

Thanks very much!

---

### Post by tormod on 2009-11-05
> **thedogisdead said:**
> Tormod - thanks for your responses.  Any chance you could give a bit more detailed instruction on how to try those four different options you mentioned?

Thanks very much!

Now, first read the "man exa" text, I am not going to repeat it here. You just stuff one of this options into the Device section, like for example:
```
Section "Device"
 Identifier "my-radeon"
 Driver "ati"
 Option "AccelMethod" "EXA"
 Option "MigrationHeuristic" "greedy"
EndSection
```
For the other options, "boolean" means on or off, and default is off, so try "on".

---

### Post by KingStill on 2009-11-05
Actually, I have found solution that doesn't involve switching KMS on (radeon.modeset = 1) which introduces tearing/corruption, or switching to XAA which reduces performance. I added Option "AGPSize" "128" to xorg.conf under device section and now I'm running full effects at 1680 x 1050.

---

### Post by tormod on 2009-11-06
> **KingStill said:**
> Actually, I have found solution that doesn't involve switching KMS on (radeon.modeset = 1) which introduces tearing/corruption, or switching to XAA which reduces performance. I added Option "AGPSize" "128" to xorg.conf under device section and now I'm running full effects at 1680 x 1050.

Interesting. What were your symptoms, and what is exactly your card:
```
lspci -nn | grep VGA
```
How much memory does it have?

---

### Post by KingStill on 2009-11-06
My symptoms were that if I had my display resolution past x:y (don't remember exactly which one, but lets assume 1280x1024 for argument's sake), the desktop area would be black and all icons were gone. If I blindly clicked where I knew the icons should be, I could open the app so everything was there, just not visible. The taskbars at the top and bottom of the screen were visible. Also, any window that was resized past certain size, would have all contents replaced with just a blank screen - just like the desktop. My card is ati mobility radeon 9200 with 128MB of ram. Here's the output of the command:
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] [1002:4c66] (rev 01)

---

### Post by dwasifar on 2009-11-06
> **KingStill said:**
> Actually, I have found solution that doesn't involve switching KMS on (radeon.modeset = 1) which introduces tearing/corruption, or switching to XAA which reduces performance. I added Option "AGPSize" "128" to xorg.conf under device section and now I'm running full effects at 1680 x 1050.

Confirmed.  I added this option to xorg.conf device section (and commented out the XAA line), and my system is now also using EXA with full effects and increased performance.  Thank you.  :)

I have the same hardware as you, BTW.

---

### Post by Tholley on 2009-11-06
YAAAAYYYYY!

It worked for me!
I showed to be using EXA and copied and pasted the new code for XAA, rebooted and I now see the cherries I had selected earlier!

All is good with 9.10 now 

Got sound, and now my desktop!

Woo Hoo!!

---

### Post by tormod on 2009-11-07
Everybody who has 128MB or more of video memory should try Option "AGPSize" "128" instead of downgrading to XAA.

Upping the AGPSize reserves more system memory so it should not be abused though. On the other hand, those with 128MB video ram often have plenty of system RAM as well.

For reference there is a similar bug report at [https://bugs.launchpad.net/bugs/197651](https://bugs.launchpad.net/bugs/197651) but please file new bugs instead of commenting on that one.

---

### Post by bagl0312 on 2009-11-07
I have an old radeon 9200 pro card:

> lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV280 [Radeon 9200 PRO] [1002:5960] (rev 01)

attached to a monitor with resolution 1680x1050.
Desktop effects worded well in Jaunty, in Karmic they are back using the following /etc/X11/xorg.conf

```

Section "Device"
        Driver "ati"
        Identifier "Radeon 9200"
        Option "BusType" "PCI"
        Option "AccelMethod" "EXA"
        Option "MigrationHeuristic" "greedy"
        Option "AGPSize" "64"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device "Radeon 9200"
EndSection


```The system was unstable (kernel panic few minutes after logon) until I  added the options:
```

Option "AccelMethod" "EXA"
Option "MigrationHeuristic" "greedy"

```also the option "BusType" "PCI" is needed to enable desktop effects

---

### Post by jacopoL on 2009-11-07
[reverting libgl1-mesa-dri to version 7.5.1-1]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/444139/comments/37") seems to be a good workaround.

---

### Post by bagl0312 on 2009-11-07
Hi JacopoL,
I tried also downgrading libgl1-mesa-dri but it did not work wih my graphic card.
Instead modifying xorg.conf as described in my previous post works very well and no downgrading of libraries is needed (at least with my card)

---

### Post by Tholley on 2009-11-07
This is what worked for me yesterday.

> I'm having the same issue on an old Dell laptop with an ATI Radeon RV250 (Mobility FireGL 9000) running a 1400x1050 panel. When I moved this machine to Karmic, my desktop was black, with no desktop items appearing on it; but you could see the desktop wallpaper beneath the semi-transparent top panel.

In my case, the fix was exactly the opposite of what tormod described.  Here's how to do it, step by step.

In terminal, run these two commands:

 	Code:
 	grep XAA /var/log/Xorg.0.log
grep EXA /var/log/Xorg.0.log 
One of them will return nothing; the other will return something like this:

 	Code:
 	(**) RADEON(0): Option "AccelMethod" "XAA"
(**) RADEON(0): Using XAA acceleration architecture
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA) 
This tells you which method is currently in use on your system. Whichever one it is, try the other. For me it was EXA, and switching to XAA solved the problem. Here is what to do.

**If it reported XAA:**

In terminal, do this:

 	Code:
 	sudo gedit /etc/X11/xorg.conf 
This will give you a text editor window.  Paste this into the text editor:

 	Code:
 	Section "Device"
 Identifier "my-radeon"
 Driver "ati"
 Option "AccelMethod" "EXA"
EndSection 
Save, and reboot, and see if the problem is solved.


**If it reported EXA:**

In terminal, do this:

 	Code:
 	sudo gedit /etc/X11/xorg.conf 
This will give you a text editor window.  Paste this into the text editor:

 	Code:
 	Section "Device"
 Identifier "my-radeon"
 Driver "ati"
 Option "AGPSize" "128"
EndSection 
Then save the file and exit the editor, and reboot.

If the problem still isn't solved when you have rebooted, open the file in text editor again, and change it to look like this:

 	Code:
 	Section "Device"
 Identifier "my-radeon"
 Driver "ati"
 Option "AccelMethod" "XAA"
EndSection 
Then save the file and exit the editor, and reboot.

Both of these solved the problem for me. The first one (with the AGPSize option) is the preferred choice and will result in better performance.

Post back and let us know if it fixes it for you.


Mine was EXA also and switched to XAA and all is good in TUX land.

---

### Post by thedogisdead on 2009-11-08
I'm good too, now!  Went back and tried the first method again - everything is smashing now.  I'm able to enjoy Karmic much more now :-)

No more complaints from me! I'm a super happy customer now.  Thanks for the help everyone.

---

### Post by emptybox on 2009-11-10
Just to say that I switched back to EXA, but added in the line
Option "AGPSize" "128", and all seems well and the compiz effects are now running as smoothly as they did under 9.04. :)
And that's on a 1920 x 1200 display.

Does that mean that my graphics card is now using some of the system RAM as well as it's own dedicated memory?
I've only got 512MB system RAM, which is the maximum I can put on the old Dell motherboard in this computer.

I'm not technically knowledgable enough to file a bug report. I hadn't even heard of "EXA" or "XAA" before I had this problem. :D

---

### Post by kwph on 2009-11-10
I am running 9.10, with a RV370 5B60 [Radeon X300 (PCIE)] video card. Monitor should be at 1280x1024, but instead was at 1152x864. Following the instructions here:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/444139/comments/37]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/444139/comments/37")

to downgrade the ATI drivers got everything working again, as it was in Ubuntu 9.04

---

### Post by ronnielsen1 on 2009-11-18
Thanks Tormod! Worked beautiful for me.

---

### Post by 0Hz on 2009-11-22
I had the same problem after updating to 9.10;
ATI Radeon 9250 feeding an HP w1707 monitor with a native resolution of 1440 x 900.  I doubt that many people are running this graphics card, but if anyone is this is what worked for me.  
Editing my xorg.conf file to this fixed the problem:


```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	1440 900
	EndSubSection
EndSection

Section "Device"
 	Identifier 	"my-radeon"
 	Driver 		"ati"
 	Option 		"AccelMethod" "EXA"
	Option		"AGPSize" "128"
EndSection
```

For those of you who are new to Linux, xorg.conf is a configuration file located at: /etc/X11/xorg.conf

You can just open the file by clicking through windows in the GUI, but this will give you read-only access to the file.  

To actually edit the file you need to open it as a "super user".

Open a terminal window (Applications->Accessories->Terminal)

at the command prompt type **exactly** the following:

```
sudo gedit /ect/X11/xorg.conf
```

What this does:

"sudo" - short for Super User DO
"gedit" - this is the text editor you want to open the file with
"/etc/X11/xorg.conf" - this is the path to the file you want to open

Hit enter.  When prompted for your admin password type it in and hit enter.  

Edit the file to look like the code above and save.  Then restart to see if it worked.

---

### Post by SeePU on 2009-11-27
> **0Hz said:**
> I had the same problem after updating to 9.10;
ATI Radeon 9250 feeding an HP w1707 monitor with a native resolution of 1440 x 900.  I doubt that many people are running this graphics card, but if anyone is this is what worked for me.  
Editing my xorg.conf file to this fixed the problem:

Edit the file to look like the code above and save.  Then restart to see if it worked.
I have that same resolution as yours but mine is a Radeon 900, RV250, mobility card in a Thinkpad laptop.  I think the card's specs might be similar enough to apply to your solution.  I hope so.  

I'm going to try your 'solution' and report my experience.  I'm not too optimistic, though.  I've tried a few 'solutions' from forum posts but nothing worked so far.

Thanks for posting 'your solution' though.  I hope it works while using a Live Cd, though.  I don't want to install if I cannot get 3D Desktop effects to work.

When you say, 'restart', do you also mean 'reboot' or to re-log in?  

If you need to reboot, that will be a tough decision for me.  Go to all the trouble to reinstall to see if IT MIGHT work?  Tough call.  :-/

---

### Post by tormod on 2009-11-27
> **SeePU said:**
> When you say, 'restart', do you also mean 'reboot' or to re-log in?
Logging out restarts X.

---

### Post by SeePU on 2009-11-27
> **tormod said:**
> Logging out restarts X.
That's good.  

So, I could try those steps on a Live CD ver. of Ubuntu 9.10, correct?   Since, I log out, that is.  

In theory, the response should be the same as if it was installed?

---

### Post by nomnex on 2009-11-27
> **dwasifar said:**
> [11/06/2009 - Editing to add newer options.]

I'm having the same issue on an old Dell laptop with an ATI Radeon RV250 (Mobility FireGL 9000) running a 1400x1050 panel.

```
Section "Device"
 Identifier "my-radeon"
 Driver "ati"
 Option "AGPSize" "128"
EndSection
```[...] The first one (with the AGPSize option) is the preferred choice and will result in better performance.

I am skeptical about this line on a laptop, since the connector for Mobility Radeon cards (not the Radeon cards for desktops) is PCI and not AGP. 

```
Option "AGPSize" "128"
```

And by the way Mobility Radeon and Firegl have the same chipset and are generally 64 MB DDR-SDRAM video memory (I have never seen one of 128 inside a notebook, even high end notebooks)

the post of tormod explains it well

> On the other hand, for AGP cards

---

### Post by chi2jjk on 2009-11-28
beesblaas,
Thanks for the solution!  Ever since 9.10, it's been driving me nuts.  Anyway, when I figure out how to report the bug (i.e. get the specifics, etc for the gurus), I will add my two-pence.

Thank you!

---

### Post by SeePU on 2009-11-29
Nah, no solution at all.  It doesn't work.  I have tried all these edits and all that results is a system lockup.  Latest one I tried locked everything up when I tried to log in again.  Ubuntu is pathetic.

---

### Post by brookie on 2009-11-29
Try turning off Visual Effects in System>Preferences>Appearance and set it to 'None'.  It worked for me. Who needs desktop effects anyway? ;)

---

### Post by Rob-e on 2009-12-01
> **bagl0312 said:**
> I have an old radeon 9200 pro card:

> lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV280 [Radeon 9200 PRO] [1002:5960] (rev 01)

attached to a monitor with resolution 1680x1050.
Desktop effects worded well in Jaunty, in Karmic they are back using the following /etc/X11/xorg.conf

```

Section "Device"
        Driver "ati"
        Identifier "Radeon 9200"
        Option "BusType" "PCI"
        Option "AccelMethod" "EXA"
        Option "MigrationHeuristic" "greedy"
        Option "AGPSize" "64"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device "Radeon 9200"
EndSection


```The system was unstable (kernel panic few minutes after logon) until I  added the options:
```

Option "AccelMethod" "EXA"
Option "MigrationHeuristic" "greedy"

```also the option "BusType" "PCI" is needed to enable desktop effects

Hey thanks this worked for me!  I had to create the file though?  idk what happen there but it works and I can scroll in Firefox again at more that .5 FPS.

here is my lspci for anyone googleing:  VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)

---

### Post by torkiano on 2009-12-12
Solved here too:

I added Option "AGPSize" "128" to xorg.conf under device section and now I'm running full effects at 1600 x 1200.

lspci -nn | grep VGA:
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon R200 QH [Radeon 8500] [1002:5148] (rev 80)

I also added this info to this bug report: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/462436](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/462436)

Thank you tormod

---

### Post by tantares on 2009-12-22
**[COLOR="Sienna"]Thank you bagl0312! [/COLOR]**

Have the same graphic card and your hint worked well

---

### Post by gukid on 2010-01-05
Had the same problem on Linux Mint 8 with a Radeon 8500 64 mb card.  1280x1024 would not display desktop unless effects were disabled, but changing to XAA fixed it.

Thanks for the help!

---

### Post by NaveB on 2010-01-16
I'm also facing similar problem with my desktop.
I've P4 with 14" Monitor having PCI video card. I was having Ubuntu 9.04 earlier which I upgraded to 9.10 and not I'm not able to see the display. Best display for my monitor would be 1024x736 (1024x800).
Somehow I booted it successfully by getting into edit mode at boot menu. Then pressing Ctrl+X at line starting with "linux".

I'm not sure how to correct this problem. After reading this whole post, I didn't understand the solution for my problem. Please suggest what to do.

---

### Post by apheren on 2010-01-22
> **dwasifar said:**
> Confirmed.  I added this option to xorg.conf device section (and commented out the XAA line), and my system is now also using EXA with full effects and increased performance.  Thank you.  :)

I have the same hardware as you, BTW.

Very well indeed. For me, this is the perfect solution.

> **bagl0312 said:**
> I have an old radeon 9200 pro card:

> lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV280 [Radeon 9200 PRO] [1002:5960] (rev 01)

attached to a monitor with resolution 1680x1050.
Desktop effects worded well in Jaunty, in Karmic they are back using the following /etc/X11/xorg.conf

```

Section "Device"
        Driver "ati"
        Identifier "Radeon 9200"
        Option "BusType" "PCI"
        Option "AccelMethod" "EXA"
        Option "MigrationHeuristic" "greedy"
        Option "AGPSize" "64"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device "Radeon 9200"
EndSection


```The system was unstable (kernel panic few minutes after logon) until I  added the options:
```

Option "AccelMethod" "EXA"
Option "MigrationHeuristic" "greedy"

```also the option "BusType" "PCI" is needed to enable desktop effects


I only advise you to put this line **Option "AGPSize" "64" **under the options section. I "benchmarked" with glxgears and with the other lines it has a huge fps drop. Like without them I have 9000 fps and with them I have usually 2000. :D

Now, I can also say I'm a proud and happy Ubuntu 9.10 user! :D

---

### Post by h8uthemost on 2010-01-25
Thank you dwasifar. Your method fixed this.

---

### Post by engine on 2010-03-14
Thanks to everyone who mentioned turning off "effects"; just installed 9.10, and was immediately disappointed by immovably black background and s-l-o-o-o-w response to clicks on window controls.

If these "effects" screw up so many people's desktop, why are they selected by default when you install? "Ubuntu includes special visual effects which are intended to make your desktop more fun and easier to use ...", according to the helps <g>

---

