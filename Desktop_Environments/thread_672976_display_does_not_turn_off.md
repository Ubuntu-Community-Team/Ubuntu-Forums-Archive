---
title: "display does not turn off"
date: 2008-01-20
forum: Desktop Environments
---

### Post by prkfriryce on 2008-01-20
In the system->preferences->screensaver-> "power management":

"put display inactive for 15 min"  

but the display turns to blank screen and the lcd backlight is still on and the power light is green.

I tried to manually set the settings in xorg.conf:

```
Section "Monitor"
        Identifier      "DELL 1905FP"
        Option          "DPMS"
EndSection


Section "ServerFlags"
Option "BlankTime" "10"
#Option "StandbyTime" "0"
#Option "SuspendTime" "0"
Option "OffTime" "12"
EndSection
```

but `xet q` displays:

```
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On
```

yet the xorg.log displays:

```
(**) Option "BlankTime" "10"
(**) Option "OffTime" "12"

```

I am able to force it to turn offusing `xset dpms force off` so I know the hardware is supported.

Any ideas why my monitor does not turn off using the gnome settings or xorg.conf?

---

### Post by rosegarden78 on 2008-01-20
I am NOT aware of the feature you requested ever having been available under Windows at any time nor in Ubuntu.  In fact, I've never experienced a screen saver shutting off the back-light - they only turn off the colors.  Make sure that Windows doesn't share the same problem.

---

### Post by prkfriryce on 2008-01-20
> **rosegarden78 said:**
> I am NOT aware of the feature you requested ever having been available under Windows at any time nor in Ubuntu.  In fact, I've never experienced a screen saver shutting off the back-light - they only turn off the colors.  Make sure that Windows doesn't share the same problem.

my definition of 'off' is the lcd power bu when i notcied tton is yellow, but video feed to the inputs is interrupted so the pixels are black.

This option works in windows and I know it works in ubuntu as well.  I recently ran a fresh install with the latest updates when i noticed the dispaly does not turn off.

---

### Post by glennph93 on 2008-01-22
I have the same problem, but if I restart the display goes to sleep(power saver) correctly. After awhile it stops working and stays on. Other post say the dpms setting are overwritten(every hour our so) with zeros.  I 'am very interested in a solution also.

---

### Post by schmolch on 2008-01-23
I have the same problem on both of my computers and i remember having this problem since FOREVER.

The dpms settings work once and then the screens never get turned off again.

Doesnt matter if i set them with gnome or kill gnome-screensaver and gnome-power-manager and use xset dpms myself.

---

### Post by prkfriryce on 2008-01-23
so I was reading the xorg.conf and decided to revert by running:

```
 sudo dpkg-reconfigure -phigh xserver-xorg
``` then ctrl+alt+backspace to restart Xorg.

I log in and realize that Xgl is now running instead of Xorg, but running `xset q` shows 
```
DPMS (Energy Star):
  Display is not capable of DPMS

```
and the display's backlight now does turn off after 10 min or so.  I'm not sure where this setting is enabled and still does not solve the original issue.

---

### Post by airbornespent on 2008-02-25
On my system I have the same problem where the display does not go to sleep, it blanks out, but the backlight does not turn off.

I've found that ```
xset dpms force off
``` does not work, neither does replacing off with suspend of standby.

However I've found using vbetool does work. Issuing ```
sudo vbetool dpms off
``` turns off the display and the backlight, however the session is not locked and the ONLY way to get the display back on is pressing up, hitting backspace twice and pressing n to change off to on. Or you could ssh into your box and issue the on command. Keyboard or mouse movement will not wake it up, only using dpms on with vbetool.

I wrote a script to turn the display on and off with vbetool, but it has to be run with sudo so assigning it a keyboard shortcut would be difficult or impossible. Also, it does not lock your screen, so anything you type on the keyboard or click on while the display is off will take place.

```

#Checks if file exists, if so turns display on, otherwise turns off display
if [ -f .dpmsoff ]
        then
        rm .dpmsoff
        vbetool dpms on
        else
        echo > .dpmsoff
        vbetool dpms off
fi

```

Ideally I'd like to change whatever script/program that issues the display timeout sleep command to use vbetool instead.

---

### Post by leehach on 2008-02-26
Well, I can't say much except that I'm facing the same problem as airbornespent.```
xset spms force [standby|suspend|off]
``` does nothing (all three options tried), but ```
sudo vbetool dpms [standby|suspend|off]
``` does turn off the monitor (all three options tried), but the monitor doesn't wake up if I move the mouse or hit the keyboard.

Anything I can try here?

---

### Post by agibby5 on 2008-03-05
Why isn't there an option for this in Power Management?  I see an option for "Put the display to sleep when inactive for:" but setting this option only makes the monitor go into it's screen saver (almost like when it's not plugged into the computer) and the monitor power light is still green...  I'd like it to turn the monitor off (light orange)

---

### Post by i_m_bobo on 2008-03-14
A little bump for this, see if it will attract the attention of someone who might have a clue what the problem is. I have the 2nd flavor of this problem, like airbornespent and leehach, in that *xset dpms force off* doesn't do anything. I've been all over google looking for clues - nothing! In particular, I couldn't find a clear explanation of how HAL and X are related.

I do notice one thing that might be important. xorg.conf shows that my monitor was automatically detected by X. But there's no mention of the monitor in the HAL-based "Device Manager" (listed under System / Preferences as "Hardware Information", but I've installed and removed so many flavors of device manager that I have no idea if this is a standard component of the distribution). I wonder if this means HAL doesn't recognize the monitor?

---

### Post by i_m_bobo on 2008-03-15
Orange light joy!

My problem (ymmv) turned out to be the display driver. When I installed the system, it opted to assign *"vesa"* as the video driver - a generic driver for a generic video card. Speculating here, but I'd wager this driver just doesn't support dpms.

My video "card" is ATI Radeon X1250, built in to the AMD690G Northbridge chip. After a couple of minor calamities caused by manually selecting *"ati"* and *"radeon"* drivers in xorg.conf, I installed the proper driver for my card using instructions I found [COLOR="Blue"][here]("https://help.ubuntu.com/community/BinaryDriverHowto")[/COLOR]. In my case it's the *"fglrx"* driver provided by AMD/ATI.

What changed for me: Some hidden magic automatically updated my xorg.conf file to
```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:5:0"
EndSection

```
*"xset dpms force off"* now forces the display off. A flick of the mouse turns it back on.

The Gnome screensaver and power manager settings control the display. The screensaver always worked, but the best the power manager could do for *off* was backlit black pixels. Now it really turns it off!

What didn't change:
xorg.conf still has this:
```
Section "ServerFlags"
	Option		"BlankTime"	"10"
	Option		"StandbyTime"	"0"
	Option		"SuspendTime"	"0"
	Option		"OffTime"	"15"
EndSection

```
but xset q still reports this:
```
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On

```

Hope this helps somebody!

---

