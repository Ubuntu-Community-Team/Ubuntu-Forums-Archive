---
title: "[ubuntu_studio] 13.04 messed up ARANDR"
date: 2013-12-27
forum: Desktop Environments
---

### Post by chkneater on 2013-12-27
Hey guyz, I was trying to set the resolutions on a dual screen setup, I had both screens cloned with the same display.  

Anyways, I accidentally turned the DVI and VGA outputs off so I have no display after bootup.  I've tried opening a terminal from memory and changing arandr back but couldn't do it.

How do I arandr to turn the displays back on?  I can do most stuff from terminal without having to see it, so if anyone knows any tricks, lemme know!

This is a new install pretty much, some upgrades, I may just dump this install and reinstall IIIFFFFF noone has a solution...  I also have a LiveDVD with 13.04, so thanx for the help in advance!!

BTW, I was using ARANDR when I turned the ouputs off accidentally

I'm using UbuStud 13.04 and I was changing resolutions on a dual screen/single card setup and accidentally turned both outputs (vga and hdmi, only ones available for me) off under the devices menu in ARANDR.  Obviously I can't see anything happening now.  I've tried a couple times to memorize the commands by keyboard and execute it at startup but haven't had any luck yet.

Is there any way to use a LiveDVD to alter the default screenlayout or turn the outputs back on??

BTW, I have tried enabling the onboard video in the BIOS and had no luck either...

BumP?!?  Seriously???

Hello?? BUmP???!!??

---

### Post by steeldriver on 2013-12-29
:confused: afaik xrandr / arandr changes should not be persistent unless you save a script file and execute that as a startup application, if so you should be able to remove the script or the .desktop file

OTOH if you used Settings --> Displays then by default your changes get saved in ~/.config/monitors.xml so you could remove / rename that

Alternatively, if you can remember the name of the output device (e.g. LVDS-0, DVI-0 etc.) then it may be easier to type the xrandr commands 'blind' rather than trying to use arandr e.g. use the Ctrl-Alt-t key combo to open a terminal, then something like

```
xrandr --output LVDS-0 --auto
```

---

### Post by Iowan on 2013-12-29
Threads merged.
From the [Posting Guidelines]("http://ubuntuforums.org/showthread.php?t=2158945"):
Do not cross post, or post the same thing in multiple locations.

---

### Post by chkneater on 2013-12-29
BTW, steeldriver, I was using the graphical ARANDR when I made the changes, not the display.

---

### Post by steeldriver on 2013-12-29
As far as I know, arandr is just a graphical front end for xrandr - so any changes you made via one should be reversible by the other, it's likely just easier to type a command 'blind' than to navigate a GUI

BTW I was the person who asked for your threads to be merged

---

### Post by chkneater on 2013-12-30
Ok steeldriver, I duly apologize to Iowan for being a jerk.  I wasn't getting any views under one topic so I thot general help would get more views than desktop environs.  

Anyways Iowan sorry, also I didn't triple post, only twice.  

I attempted the commands and had no luck, also I think I posted I was using 13.04 but its 13.10 if it makes a diff.  Since you're the only one that evidently can see my posts for some mysterious reason, I just have to reinstall at this point, which just thrills me to death.  I think that something else happened beside the changes to ARANDR since I've tried a few times with both X and Arandr with no luck...  Anyways thanks for trying, much appreciation.

again sorry Iowan.

---

### Post by Iowan on 2013-12-30
> **chkneater said:**
>   I thot general help would get more views than desktop environs. I can move it there, if you'd like.

> **chkneater said:**
> ...also I didn't triple post, only twice. Never accused you of triple posting... but twice is once too often. 

> **chkneater said:**
>   Since you're the only one that evidently can see my posts for some mysterious reason...
I can see 'em ;)

As you've already pointed out, I probably can't solve the problem, but...
How far into the boot process does the machine get before you lose the video?
(Do you have the opportunity to reach rescue mode?)
I'm on 12.04, so I'm not sure what/if has changed in the past few versions.

---

### Post by chkneater on 2014-01-02
Yeah I think General help would get more responses...  If you could move it there I'd preciate it much...

I can see the BIOS splash screen on one display and some of the startup texts, but when it goes dark just before the desktop shows up all I see is a cursor on one display and nothing on the other, BUT they are getting signals, otherwise the displays themselves would say 'no signal', so I know SOMETHING is being transmitted to the display, just cant see or do anything 

and yes I can see the grub and get to rescue mode, just don't know what can be done from there?

Tired of running this Live DVD tho, no flash support and have to download the apps I like, but hopefully this can be fixed without reinstallation

---

### Post by steeldriver on 2014-01-02
From the live DVD did you check your home dir for a hidden ~/.config/monitors.xml or ~/.screenlayout file?

I'm starting to think this is nothing to do with arandr - if you'd set both displays to OFF then how would you have navigated the arandr menu to save the settings? If you didn't save the settings, they should not persist after rebooting afaik

---

### Post by chkneater on 2014-01-02
steeldriver

    Re: 13.04 messed up ARANDR
    From the live DVD did you check your home dir for a hidden ~/.config/monitors.xml or ~/.screenlayout file?

    I'm starting to think this is nothing to do with arandr - if you'd set both displays to OFF then how would you have navigated the arandr menu to save the settings? If you didn't save the settings, they should not persist after rebooting afaik 
---------------------------------------

That's exactly what I've been wondering... How would I have saved the settings without seeing them??  I did check screenlayout, this was the default.sh:

#!/bin/sh
xrandr --output VGA-0 --off --output DVI-0 --mode 1680x1050 --pos 0x0 --rotate normal --output HDMI-0 --off

I then changed it to this just to see:

#!/bin/sh
xrandr --output VGA-0 --on --output DVI-0 --mode 1680x1050 --pos 0x0 --rotate normal --output HDMI-0 --on

You can see I just changed the 'off's to 'on's.

This is 'layoutdefault.sh':

#!/bin/sh
xrandr --output VGA-0 --on --output DVI-0 --mode 1680x1050 --pos 0x0 --rotate normal --output HDMI-0 --on

It's the same as the default I modified.


This is the twinscreen format that worked fine before this mess (I haven't altered this one at all):

#!/bin/sh
xrandr --output VGA-0 --mode 1024x768 --pos 0x0 --rotate normal --output DVI-0 --mode 1024x768 --pos 1016x0 --rotate normal --output HDMI-0 --off

This is monitor.xml which I also haven't altered:

<monitors version="1">
  <configuration>
      <clone>no</clone>
      <output name="DFP1">
      </output>
      <output name="DFP2">
          <vendor>SQM</vendor>
          <product>0x058f</product>
          <serial>0x434d3232</serial>
          <width>1280</width>
          <height>1024</height>
          <rate>60</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
      <output name="CRT1">
      </output>
      <output name="CRT2">
          <vendor>@@@</vendor>
          <product>0x0000</product>
          <serial>0x00000000</serial>
          <width>1280</width>
          <height>1024</height>
          <rate>60</rate>
          <x>1280</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
  </configuration>
</monitors>

I know that's a lot to take in but do you see anything that sticks out?  I'm

---

### Post by steeldriver on 2014-01-02
... I suggest moving/renaming ALL of them until you get it working

FWIW I'm not sure that 'on' is a valid output option - you might want to try replacing 'off' with 'auto'

---

### Post by chkneater on 2014-01-02
Will try that...

Actually I just copied the old Arandr script from a previous install that hadn't been completely deleted and was able to access the desktop again.  Arandr still didn't work, it just showed one default monitor, but I noticed that a partial update updated some of the modules but not all of them, so I think that was the original problem.

I just completed a full update and am going to reboot, then I'll have to run aticonfig --initial again to get the amdccle and have full support. Hopefully.

---

