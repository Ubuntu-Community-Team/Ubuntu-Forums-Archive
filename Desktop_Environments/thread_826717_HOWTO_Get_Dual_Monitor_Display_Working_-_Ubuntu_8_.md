---
title: "HOWTO: Get Dual Monitor Display Working - Ubuntu 8 / Hardy Heron"
date: 2008-06-12
forum: Desktop Environments
---

### Post by mhenwood on 2008-06-12
I had come hardships getting dual display working between by laptop (Dell Vostro 1700) running Hardy Heron, and an extra LCD panel display.

I noticed in these forums that others had similar problems, so here are my successful steps for those in similar pain.

FIRSTLY, read this: [http://www.intellinuxgraphics.org/dualhead.html](http://www.intellinuxgraphics.org/dualhead.html)
It really will help.

If you come this far without reading the above link, you'll probably get it wrong.

Next MAKE SURE YOU BACKUP YOUR EXISTING xorg.conf!
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

These instructions assume you have a laptop to the left of your larger LCD panel, and that you want the LCD panel to be the main screen. If this isn't true, you need to pay attention to the "LeftOf" / "RightOf" options in step 3 below, also in step 4 and during the rejigging of the layout using xrandr (more on this below).

Before you start, you will need the ID of your displays from xrandr.  Do:
sudo xrandr -q

In my case, the displays are called "VGA" and "LVDS". You will need these values when doing step 1 below.

Edit your xorg.conf (from the out-the-box Heron dist version) and make the following changes:
1. In 'Section "Device"', add the 2 lines highlighted in red so the section reads like this:
Section "Device"
        Identifier      "Configured Video Device"
        [COLOR="Red"]Option          "monitor-VGA" "lcddisp"
        Option          "monitor-LVDS" "laptop"[/COLOR]
EndSection

Note that the "Option" keys are the 2 values you got in 'sudo xrandr -q' earlier, prefixed bu the string "monitor-". **THIS IS IMPORTANT!**

2. Change the identifier in 'Section "Monitor"' as shown in red, so it reads like this:
Section "Monitor"
        Identifier      "[COLOR="Red"]lcddisp[/COLOR]"
EndSection

3. Immediately below the existing 'Section "Monitor"' add a new 'Section "Monitor"' which looks like this:
[COLOR="Red"]Section "Monitor"
        Identifier      "laptop"
        Option  "LeftOf"        "lcddisp"
EndSection[/COLOR]

**N.B.**  This assumes your laptop is to the left of your lcd display. If not, change "LeftOf" to "RightOf".

4. In 'Section "Screen"', edit the Monitor to be the one you want as your main screen (in my case 'lcddisp' but you may want 'laptop'):
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "[COLOR="Red"]lcddisp[/COLOR]"
        Device          "Configured Video Device"
EndSection

5. Also in the same 'Section "Screen"' add a SubSection as follows:
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "lcddisp"
        Device          "Configured Video Device"
        [COLOR="Red"]SubSection "Display"
                Depth   24
                Modes "1680x1050" "1440x900"
                Virtual 3120 1050
        EndSubSection[/COLOR]
EndSection
Note: The Modes options should reflect the 2 modes of your laptop and LCD panel (or just one mode if they are the same resolution.)
Also Note: **Virtual setting**. You should calculate this such that the first figure is the TOTAL width of both displays added together, and the second figger is the larger of the 2 display heights. If you don't know the resolutions you can get them by:
sudo xrandr -q

In short, the Virtual section creates a giant virtual screen which must be big enough to hold the 2 screens we are physically using.

OK that's the xorg.conf edited, so....

6. Restart X (CTRL-ALT-BACKSPACE)

Nothing amazing will have happened yet; you now need to use xrandr to move the displays around in the giant virtual screen we just made:

7. sudo xrandr -q to get the system names of the 2 displays. Im my case these are VGA (the LCD panel) and LVDS (the laptop)

8. Whichever display you opted for on the right, now use xrandr to reposition it. In my case:
xrandr --output VGA --pos 1440x0

This moved my VGA (lcd) display to position 1440, which is exactly at the right hand edge of my laptop display (within the giant virtual screen.)

This should have done the trick.

Again, this document is very helpful:
[http://www.intellinuxgraphics.org/dualhead.html](http://www.intellinuxgraphics.org/dualhead.html)

Good Luck!

---

### Post by shr2004 on 2008-06-12
First, thanks a lot your post. It is a good tutorial for dual screen. I am new in Ubuntu. In Hardy Heron, I found that in the System>Preferences there is an option for changing resolution which can be used to configure dual monitor. For my case it can detect my extra LCD along with laptop and I can fix its resolution. But to use both laptop and LCD monitor together, the active resolution becomes the LCD's resolution which is larger than laptop's, as a result the bottom pan is not visible in laptop screen. As I occasionally use extra LCD, I turn-off laptop display and use extra LCD. That works fine for me. Is your method works dynamically, ie, you can add or remove extra display without running any configuration, then I will try that. 
Thanks

---

### Post by mhenwood on 2008-06-13
Yeh, sorry I wasn't that clear about how to source the monitor names, so maybe it wasn't too clear.

Please re-read the above post - point(1) and the paragraph above.

Basically it's not dynamic but it does allow you to address both screens seaprately (so you don't have the problem with 2 displays with the same resolution setting, when one screen is physically smaller)

---

### Post by SteveG on 2008-06-23
mhenwood,

**Thank You** for a great HowTo. I was working with dual monitors in ver 7.04. I decided to upgrade to 8.04 ubuntustudio (new install - no change in hardware) & just couldn't get the same dual working. All the how-to's just were not addressing the problems. I even tried the ATI catalyst drivers . no go.

I actually went out and bought a nvidia to replace the ati, till I decided to check the help one last time. 
I now have dual display with a big desktop- as per your instructions.:) Though the size might need to be adjusted, i think. The background image of the mixer - gained in size. 


My video is a ATI x300 pcie
Dual LG L194WTX at 1440x900   Virtual at 2880x900

Super Thanks
SteveG

---

### Post by RAOF on 2008-06-24
It might be worth noting that the Virtual line here:

> **mhenwood said:**
> ...
5. Also in the same 'Section "Screen"' add a SubSection as follows:
```

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "lcddisp"
        Device          "Configured Video Device"
        DefaultDepth    24
        [COLOR="Red"]SubSection "Display"
                Virtual 3120 1050
        EndSubSection[/COLOR]
EndSection

```
...

is really the only necessary part of these modifications.  The virtual line specifies the maximum combined resolution available across all of your screens, and it *defaults* to the resolution of the highest resolution device you have plugged in when X starts.  This means that by default you can't do non-clone dual-head.

However, once you have a specified a (sufficiently large) Virtual size, you can use System->Preferences->Screen Resolution to dynamically handle dual-head.  It will also restore your dual-head settings when you log in.  That's the way I have my dual-head set up on my laptop, since I tend to swap things around a lot.

---

### Post by sharifi14 on 2008-06-24
Hey guys,

I'm a newbie to Linux so a lot of this sounds pretty alien to me. Basically, I want to clone the picture on my primary display (15 inch 16:9) onto a secondary display (7 inch 16:9). Here's a bit of background information...

To set up my dual display, I've been using the nvidia-settings GUI, as opposed to editing X Server in Terminal which many tutorials seem to use.

So far, I've managed to clone the picture of the primary display onto the secondary display. However it is not scaled correctly, i.e. only a quarter (if that) of the desktop is showing.

Would anybody be able to offer any thoughts on (preferably using nvidia-settings) how to change the resolution of the secondary display to show all of the contents?

I apologise in advance for any ignorance that this post may exude, but I look forward to hearing back from someone!

Alex

[EDIT: I've worked out how to change the brightness - it was the display afterall...]

---

### Post by Motorhead Kaze on 2008-06-26
Thanks for this post, I just bought my new monitor yesterday, and am excited to get the split screen/extended desktop going. I am running an ATI Radeon dual-head graphics card on Hardy, with 2, 19in. monitors (off my desktop).Before I follow the above instructions, I have questions.  Here they are:

```
  Section "Screen"
Identifier "Default Screen"
Monitor "lcddisp"
Device "Configured Video Device"
SubSection "Display"
Depth 24
[COLOR="Red"]Modes "1680x1050" "1440x900"
Virtual 3120 1050[/COLOR]
EndSubSection
EndSection

```

Are these numbers, which I have in red, good for everyone or do I need to use a specific pair for my machine?  

Next, to **RAOF**, 'SubSection "Display" Virtual 3120 1050 EndSubSection... is really the only necessary part of these modifications.' does this mean that this is the only part of xorg.conf I need to change to get one elongated desktop/split screens?  Not sure if that is what you meant.

Also, since I am running two similar monitors (VGA-0 and DVI-0) off a desktop, I want to know if in this section:
```
Option "monitor-VGA" "lcddisp"
Option "monitor-LVDS" "laptop"
```
should I be writing this instead?
```
Option "monitor-VGA" "lcddisp"
Option "monitor-DVI" "lcddisp"
```

Thank you for taking time to deal with my lack of understanding. I just want to make sure I get all the parts correct before I do it.

Peace

---

### Post by RAOF on 2008-06-26
> **Motorhead Kaze said:**
> Thanks for this post, I just bought my new monitor yesterday, and am excited to get the split screen/extended desktop going. I am running an ATI Radeon dual-head graphics card on Hardy, with 2, 19in. monitors (off my desktop).Before I follow the above instructions, I have questions.  Here they are:

```
  Section "Screen"
Identifier "Default Screen"
Monitor "lcddisp"
Device "Configured Video Device"
SubSection "Display"
Depth 24
[COLOR="Red"]Modes "1680x1050" "1440x900"
Virtual 3120 1050[/COLOR]
EndSubSection
EndSection

```

Are these numbers, which I have in red, good for everyone or do I need to use a specific pair for my machine?  

You want the numbers in red to be greater than or equal to the combined maximum resolution of all monitors you intend to plug in.  So, I've got a 1680x1050 laptop and a 1280x1024 LCD screen; I'd want the Virtual line to be greater than or equal to 2960 1050 (= 1680+1280 1050) in order to have the two screens side-by side, or >= 1680 2074 (= 1680 1050+1024) to have one on top of the other.  Setting a Virtual size larger than you need will consume a little more VRAM than strictly necessary.  Note that some cards (some Intel cards, I believe) will lose 3D acceleration with a Virtual size too high - this threshold seems to be when either of the dimensions exceed 2048.

> **Motorhead Kaze said:**
> 
Next, to **RAOF**, 'SubSection "Display" Virtual 3120 1050 EndSubSection... is really the only necessary part of these modifications.' does this mean that this is the only part of xorg.conf I need to change to get one elongated desktop/split screens?  Not sure if that is what you meant.
...

Exactly.  Once you've set the Virtual size, you can use System->Preferences->Screen Resolution to manage your multiple monitors - cloning, above, below, beside, etc.  You don't need to hardcode the layout in the xorg.conf.

---

### Post by Motorhead Kaze on 2008-06-26
Thanks for replying!

Just another question. My xorg.conf looks like this:
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Modes		"800x600"
	EndSubSection
	Defaultdepth	24
EndSection

```
and I am now wondering if (under "Monitor") I need to change the words "**Configured Monitor**" to "**lcddisp**" ? Or is it ok like it is?

I tried this:  
```
Modes "1280x1024" "1280x1024"
Virtual 2560 1024

```
My current resolution on either screen is 1280x1024.  But after saving xorg.conf I went up to System->Preferences->Screen Resolution and tried changing from cloned output, but after ticking off that box and playing with left/right, not only did that not work (cloned output came back on), when I restarted X, I got a Gnome settings daemon error, and Gnome was all wacked out. The desktop image is about 2 inches lower than usual, my keyboard keys are all set back to American standard (I usually have it set on Japanese keyboard) and etc. I changed back to my original settings on xorg.conf, but Gnome is still messed.  What did I do wrong?

...what?  Ok, 5 seconds after I pressed "Save" on this post, Gnome came back.

As for the xorg.conf, was I mistaken to type in the above ratios?  Should I have typed 800x600 twice, then under virtual something like 1600 600?  Or is my problem that my numbers are identical? (you guys are using external screens that are different in size from your laptops) I am a bit confused.

---

### Post by Motorhead Kaze on 2008-06-26
Howdy again.

Well, after following the way I mentioned above, and nothing good happened, I re-read the full tutorial above, and read the Intel tutorial 2 more times. This is what I did in my xorg.conf, and nothing happened. I even tried going back into the screen resolution menu to try to arrange things, but after messing with that, I reopened it just to check, and the clone box is checked again. Here is my xorg.conf:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
	Option "monitor-VGA" "lcddisp"
	Option "monitor-DVI" "Configured Monitor"
EndSection

Section "Monitor"
	Identifier	"lcddisp"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
Option "LeftOf" "lcddisp"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Modes	"1280x1024"
	Virtual 2560 1024
	EndSubSection
	Defaultdepth	24
EndSection
```

After restarting X I put this in a terminal
```
 xrandr --output VGA --pos 1280x0

```
This should be right now, correct? But I still have two of the same screen going on here. So what is not working? 

Your help would really be appreciated.

PS  Are the names "lcddisp" and "Configured Monitor" not ok?  "lcddisp" I copied from the text above. If this monitor actually has a proper name, how do I find it?  Should I not be using the name "Configured Monitor" anymore?

Help.

---

### Post by Motorhead Kaze on 2008-06-26
Hello?  This tutorial didn't work for me, perhaps I misunderstood a part? I could really use some help to get these monitors working. 

come baaaaaccckk...

---

### Post by RAOF on 2008-06-26
> **Motorhead Kaze said:**
> Thanks for replying!

Just another question. My xorg.conf looks like this:
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Modes		"800x600"
	EndSubSection
	Defaultdepth	24
EndSection

```
...

Sorry, I should have mentioned.  This guide will work only for reasonably recent (Hardy is OK, Gutsy should be OK, too) open-source drivers which implement the XRandR 1.2 extension.  The "intel", "ati" and (if you have a Geforce >= 8xxx) "nv" drivers implement XRandR 1.2.

There's no technical reason I can think of why the proprietary drivers cannot implement this, but as far as I'm aware, none of them have.  This is one of the reasons that proprietary drivers suck :).

Since you are using the fglrx proprietary ATI driver, this howto doesn't apply to you.  I don't have experience with ATI cards under linux, but you'll probably be able to set up dual-screen using the ATI control centre thingy.

---

### Post by Brandon Jenko on 2008-06-26
hi my name is Brandon Jenko, dual monitors require the computer to support a dual monitor option however there is software to help with this. make life easier and install a video card that supports that.

Brandon Jenko

---

### Post by Motorhead Kaze on 2008-06-27
Howdy again.  I FINALLY got this all working. I tried 3 tutorials, and what ended up working was just this:

```

Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        DefaultDepth    24
       [COLOR="Red"][B] SubSection "Display"
            Depth           24
            Virtual         2560 1024
        EndSubSection[/B][/COLOR]
EndSection
```
RAOF? Isn't this precisely what you said yesterday? Somehow, when I did this yesterday, my changes in screen resolution would not do a thing. I think that somehow the changes I made from other tutorials did something weird to my PC that I didn't mean to do. The weirdest crap happened. My monitors remained cloned, but Gnome freaked out and wouldn't come on all the way, THEN Compiz somehow got turned on (I don't even use Compiz!) and gave me a white screen...and all these horrible issues. I ended up in failsafe Gnome and a terminal for half the day. I was able to get rid of that white screen by uninstalling compiz in a terminal, reverted to my backup of xorg.conf, and added these little changes, and suddenly my screen resolution changes took, and I have dual monitors.  Can messing with xorg.conf turn Compiz on? Can it shut down parts of Gnome?  Apparently. How wacked out is that?

Anyway, thanks for your help. Simple is just what I was looking for.

Brandon, the vid card and computer clearly do support dual monitors, the lengthy and unnecessary additions to xorg.conf in tutorials I found in the forum were the major problem. (Most are outdated as well). No additional software was required.

---

### Post by shr2004 on 2008-06-27
Although not able to do what I am for, comments in this thread helps to understand the display settings. My laptop has intel video card, so it is retricted to 2048x2048.  I am trying to use external LCD above laptop. I just changed the virtual size to fit my need in xorg, then configure using menus. The only problem is after configuring the screen just scattered. If I restart X then it works. Restarting always is not a good option I think, it is probably the problem with my Intel driver.
A small query: the ubuntu menus are in the external VGA screen, not in my laptop screen. Is there any way that menus will be in laptop screen and VGA will be the extended?
Thanks

---

### Post by sistoviejo on 2008-06-28
I successfully set up dual screen with the nvidia driver.
The only problems I have right now are:
1) My gnome-panels don't appear on my secondary display. Is it possible to have the panels duplicated on the second screen?
2) The desktop icons only appear on the second screen. Can I make them appear on the first screen also?
Thanks,
Silvio :)

---

### Post by Motorhead Kaze on 2008-06-30
That is a good question. It is pretty clear that panels and icons on one monitor only is default, that is what I got too.  

"Bump" on that one.

Also, for RAOF or anyone else who knows, I was trying to get the dual monitors set up on GUTSY too, but the xorg.conf setup is different. I am seeing a LOT more text there for both monitors, with some text for VIRTUAL already there.  I tried replacing the virtual section, by using the same text I put in my Hardy xorg.conf, but when I restarted X and went to the Admin/Screen...area, I couldn't do a thing with the second screen. One screen was default, and there is no CLONE box to uncheck as in Hardy.

What is the process for Gutsy then?

---

### Post by Motorhead Kaze on 2008-07-01
Update: Hardy could not detect my second monitor because the **propriety driver for my ATI graphics card was ON**. (not so last week when I had the dual monitors running great) Once I switched that driver off, Hardy was able to see that I had 2 monitors, I went back to xorg.conf and added the Screen subsection and virtual text again, then arranged the screens in Screen Resolution prefs. I am back to dual monitor happiness again.

These links were also very helpful:

[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)
[https://help.ubuntu.com/community/XORGHardy](https://help.ubuntu.com/community/XORGHardy)
And about the propriety drivers, etc. [http://ubuntuforums.org/showthread.p...tection&page=2](http://ubuntuforums.org/showthread.p...tection&page=2)

To RAOF "Propriety drivers DO suck", and now you know how to setup dual monitors on a ATI graphics card! JOY! (that and a 3 year old graphics card at that!)

---

### Post by RAOF on 2008-07-01
> **Motorhead Kaze said:**
> That is a good question. It is pretty clear that panels and icons on one monitor only is default, that is what I got too.  

"Bump" on that one.


You can add more panels to your second monitor.  I don't think there's a way to make a single panel span both screens, although I also can't think of any reason you'd want that either ;).

> **Motorhead Kaze said:**
> 
...I tried replacing the virtual section, by using the same text I put in my Hardy xorg.conf, but when I restarted X and went to the Admin/Screen...area, I couldn't do a thing with the second screen. One screen was default, and there is no CLONE box to uncheck as in Hardy.

What is the process for Gutsy then?

I'm not sure.  The dual-head-aware System->Preferences->Screen Resolution applet is new in Hardy, though.  You could probably add the rest of the xorg.conf stuff from the first post to make it work, though (if you're using a suitable free driver, of course).  I *think* that Gutsy's Xorg had the XRandR 1.2 stuff.

---

### Post by sistoviejo on 2008-07-01
I've made a little script to replace my xorg.conf file with my dual monitor configuration... it does just this:
cp /etc/X11/xorg.conf.2monitors /etc/X11/xorg.conf
And then another one to turn it back to normal:
cp /etc/X11/xorg.conf.1monitor /etc/X11/xorg.conf
I run them and then manually restart X.
I've also added a panel to my second monitor only with the window list and the gnome menu. Is there a way to make that script add and remove the panel when I switch configurations?

---

### Post by Buddy Gurt on 2008-08-14
Excellent! Thanks for the very helpful post. I have a HP laptop with 1680x1050 resolution with an external 1280x1024 LCD monitor. Adjusting the xorg.conf as you suggested indeed resulted in a dual (extended) screen. Some remarks though:

1. After every boot the laptop screen was set to 1280x1024. I could adjust that manually with System - Preferences - Screen resolution, but it's annoying, obviously. However, I found out that a minor change in xorg.conf did the trick:
```
Section "Screen"
	Identifier	"Default Screen"
	# Monitor	"Configured Monitor"
	Monitor		"lcddisp"
	Device		"Configured Video Device"
	Option		"metamodes"	"VGA: 1280x1024 +0+0, LVDS: 1680x1050 +1280+0"
	SubSection "Display"
		Depth	24
		Modes	"1680x1050"
 		Virtual	2960 1050
 	EndSubSection
EndSection
```
This completely solves my problem! Now the laptop screen is set to 1680x1050 after every boot. (Note that my laptop is RightOf the LCD screen).
By the way, booting without the LCD screen still works fine (as it is supposed to).

2. I've read before that dual screen and Compiz can't work together for Intel videocards. The nice thing is that when I work with dual screens Compix is automatically switched off. Restarting with one screen turns Compiz back on. Nice! Although dual + Compiz would be nicer of course...

3. One thing I still can't fix is the fact that my Gnome panel is always on the LCD screen, while I would like to have it on my laptop screen. No matter what I try in xorg.conf or XRandR, it's always on the LCD screen. I expect that this is not an xorg problem, but a Gnome thing. Anyone any suggestions to change this?

---

### Post by Buddy Gurt on 2008-08-14
Before I forget (this might be helpful for some people): I first had to remove the package **xserver-xgl** before the above procedure worked.

---

### Post by Toshibawarrior on 2008-09-01
Ok, I have an Intel 945GM chipset...i followed this tutorial entirely from beginning to end...And this crap still doesn't work!

After changing the xorg.conf and restarting X, I just get a huge desktop between both screens (15.4 laptop LCD and a 27" Panasonic TV, plugged via S-Video) with the gnome panel on the TV (not the default screen) and the desktop icons scattered through both screens. Even worse, when i restart my PC, the laptop's screen goes blank and turns off...just the TV is available.

I really dont know what the heck is wrong with this thing! I'm beginning to hate this whole "two-head-laptop" thing...

And besides I set the "modes" with the correct resolutions and when i restart (if both monitors turn on) the resolutions stays at 1024x768 on both monitors, completely and utterly ignoring (and giving a damn) about what i specified in the xorg.conf.

Looks like this stupid computer wants to give me a headache...I've been fighting with this for weeks now...

Can anyone please help me?!...

Here's my xorg.conf:
```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option "monitor-TV" "lcddisp"
	Option "monitor-LVDS" "laptop"
EndSection

Section "Monitor"
	Identifier	"lcddisp"
EndSection

Section "Monitor"
	Identifier "laptop"
	Option "RightOf" "lcddisp"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"laptop"
	Device		"Configured Video Device"	
	SubSection "Display"
		Depth   24
		Modes  "1280x800" "640x480"
		Virtual 1920 1280
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```

I'm getting extremely annoyed with the whole "laptop screen won't turn on".

PLEASE PLEASE HELP ME! Any help will be greatly appreciated!!!

---

### Post by svamppi on 2008-09-02
I bought a second monitor today and have been struggling to get an "extended desktop" going. With the Gnome panel on one monitor and with ability to move applications over to the other monitor. I was using the proprietary driver first and was only able to get two xservers running or something at first by manually messing with the xorg.conf. After I switched the driver in xorg.conf back to radeon everything started working better. But don't you need the proprietary drivers to get the hardware acceleration to work? And even though the setup I have now functionally is like I want it, the mouse cursor flickers when it hovers over certain spots on the screen.

---

### Post by utnubuuser on 2008-11-02
Hi -- Ditto - tried the tutorial without much luck, but checked the xorg.conf file in Ubuntu 8.10 after going through the System>>Preferences,(in 8.10 dual monitors works flawlessly and automatically through the System>>Preferences>>Screen Resolution), and noticed that xorg had symply added the Virtual 2048 768 to my "Screen" section, tried adding it to the corresponding lines in 8.04 xorg.conf and got automatic dual screens.

---

### Post by Zezu on 2008-11-07
I tried this way, No Luck. came across the following bit of code while researching Dual monitors, But only works for Nvidia:

> nvidia-xconfig --twinview --enable-all-gpus

To use this code:
1.Restart your computer in recovery mode
2. When the bule screen gives you 4 choices, drop into root.
3. use above code
4.ctrl+d to get back to blue screen
5. continue on.

Enjoy!

---

### Post by dremanu on 2008-11-12
This worked for me perfectly! Thank you for sharing.

---

### Post by alingham on 2008-12-14
Hey - I'm in KDE 4.1, and can only get dual monitors working this way and it works totally fine.
However, it seems to remove the window decoration that kwin provides and instead resorts to some default white oxygen theme, but the buttons are on the wrong side.
This doesn't happen when I have the default xorg.conf file, but then the dual monitors can only be clone.

Sidenote:
KDE 4.1's Display configuration puts both dual monitors ontop of each other, and they can't be moved outside of their own boundaries. Big bug! If anyone has a solution I suspect I won't need the xorg.conf modifications...

---

### Post by sbuhlig on 2008-12-17
mhenwood

You are the man.

After reading the link and your post. Worked great. 


Big Thanks!!!

---

### Post by CHaoSlayeR on 2009-01-10
Hi guys,

I'm trying to get a dual head setup with my old nVidia Geforce FX 5200 Go 64M using the nv driver with no success until now. The external display of this Dell Inspiron 8600 just don't get any signal.

I tried the how-to here as it is basically the same as the intel one that works great for ati and radeon driver but not for the nv I'm using.

I previously used the nvidia proprietary driver with the success that I got dual head but I want to use KDE4 at usable speeds and on the notebook display the nv driver performs very well (although without 3D hardware acceleration and so without effects). But I can't get a dual head configuration.

My external monitor is a NEC MultiSync FE1250+ (21" CRT with Sony Trinitron flat) connected to the Sub-D.

Xrandr doesn't recognize the second output:

```

Screen 0: minimum 640 x 480, current 1280 x 800, maximum 1280 x 800
default connected 1280x800+0+0 0mm x 0mm
   1280x800       60.0*
   1024x768       60.0
   800x600        60.0
   640x480        60.0

```

The ddcprobe only gets information from the external display:
```

vbe: VESA 3.0 detected.                                            
oem: NVIDIA
vendor: NVIDIA Corporation
product: NV34 Board - p136nz Chip Rev
memory: 65536kb
mode: 640x400x256
mode: 640x480x256
mode: 800x600x16
mode: 800x600x256
mode: 1024x768x16
mode: 1024x768x256
mode: 320x200x64k
mode: 320x200x16m
mode: 640x480x64k
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 1024x768x64k
mode: 1024x768x16m
edid:
edid: 1 3
id: 61b6
eisa: NEC61b6
serial: 0000304f
manufacture: 40 2001
input: composite sync, sync on green, analog signal.
screensize: 40 30
gamma: 2.200000
dpms: RGB, active off, suspend, standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 720x400@88 Hz (XGA2)
timing: 640x480@60 Hz (VGA)
timing: 640x480@67 Hz (Mac II, Apple)
timing: 640x480@72 Hz (VESA)
timing: 640x480@75 Hz (VESA)
timing: 800x600@56 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 800x600@72 Hz (VESA)
timing: 800x600@75 Hz (VESA)
timing: 832x624@75 Hz (Mac II)
timing: 1024x768@87 Hz Interlaced (8514A)
timing: 1024x768@60 Hz (VESA)
timing: 1024x768@70 Hz (VESA)
timing: 1024x768@75 Hz (VESA)
timing: 1280x1024@75 (VESA)
ctiming: 800x600@85
ctiming: 1024x768@85
ctiming: 1152x864@75
ctiming: 1280x960@85
ctiming: 1280x1024@85
ctiming: 1600x1200@75
ctiming: 1792x1344@75
ctiming: 1920x1440@72
dtiming: 1600x1200@111
monitorrange: 30-110, 50-160
monitorname: NEC FE1250+
monitorserial: 110112367

```

The Xorg.0.log with the nv driver also only gets EDID information from the external display but initializes only the internal one. That confuses me a lot as I think when the driver detects a display it must be able to use it.

I slowly come to the conclusion that the nv driver doesn't support dual head modes at all although there is a "DualHead" option for the device section available. But trying to use it just doubles the virtual size, nothing more.

Please help me with that!

C]-[aoZ

---

### Post by CHaoSlayeR on 2009-01-10
...hm... double post. strange...

---

### Post by SlickRick on 2011-01-11
thank you, exactly what I was looking for
used the xrandr method

---

