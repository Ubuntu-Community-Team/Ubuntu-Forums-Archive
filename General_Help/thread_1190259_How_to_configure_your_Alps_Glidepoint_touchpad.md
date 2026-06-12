---
title: "How to configure your Alps Glidepoint touchpad"
date: 2009-06-17
forum: General Help
---

### Post by cknight on 2009-06-17
UPDATE (28/08/2010): The original post dealt with creating a HAL configuration file to configure your Alps touchpad.  HAL stands for Hardware Abstraction Layer and was responsible for configuring some (all?) of your hardware on startup.  In Lucid (10.4), HAL has been ditched and the original instructions (for creating an fdi file) will no longer work in Lucid Lynx or beyond.  New instructions for Lucid are as follows (see further below for original instructions):

[COLOR="Red"][SIZE="6"]**Lucid-Lynx (Ubuntu 10.4):**[/SIZE][/COLOR]
There are still several ways to configure your touchpad.  In order of ease:
**1) Change XORG configuration files**
**[COLOR="Red"]Caution:[/COLOR]**  This method worked for me.  It may not work for you and making changes to xorg configuration files can cause serious (but reversible) issues with keyboard input, mouse input or monitor.  Before proceeding I suggest making backups of any file you will be changing and have a live CD on hand to back out any changes you made which broke something.

To start, go to xorg's configuration folder
```
cd /usr/lib/X11/xorg.conf.d
```
Edit the synaptics specific configuration:
```
sudo gedit 10-synaptics.conf
```
Under the section with identifier 'Identifier "touchpad catchall"', add your touchpad specific options under the device label.  Specifically, using the setup described in the original posting, here is how mine ended up (all changes consist of adding the various 'Option's):
```
Section "InputClass"
	Identifier "touchpad catchall"
	MatchIsTouchpad "on"
	MatchDevicePath "/dev/input/event*"
	Driver "synaptics"
	Option "SHMConfig" "True"
	Option "LeftEdge" "0"
	Option "RightEdge" "850"
	Option "TopEdge" "300"
	Option "BottomEdge" "550"
	Option "EmulateTwoFingerMinZ" "100"
	Option "EmulateTwoFingerMinW" "0"
	Option "VertScrollDelta" "7"
	Option "HorizScrollDelta" "7"
	Option "HorizEdgeScroll" "True"
	Option "VertTwoFingerScroll" "1"
	Option "MaxSpeed" "1"
	Option "RTCornerButton" "2"
	Option "RBCornerButton" "3"
	Option "TapButton2" "0"
	Option "TapButton3" "0"
EndSection

```
A few notes:
1) Once changes are made, a restart of the x-server is required.
2) Use synclient -l to verify that all changes have been activated.  Some programmes will override these values.  I don't know exactly which ones those are but one remedy is to turn off 'TouchPad' in startup programmes (System->Preferences->StartUp Applications') and untick 'Touchpad'.

**2) Write a script which executes xinput commands**
This method can have the advantage of running after all the mouse settings have been loaded so you can be reasonably sure of these settings not being overridden.  Here's a sample script which might do the trick:
```

#!/bin/bash
#use 'man synaptics' to see the full list of available commands
sleep 7
xinput set-int-prop "AlpsPS/2 ALPS GlidePoint" "Synaptics Edge Scrolling" 8 1 0 0
#etc...
```
**3) Write custom UDev rules**
This is more serious hard-core programmer stuff, but might do the trick in a pinch.  Be forewarned that I've not heard many people  having success with this route.  Rather than spell this out here, I'll pass you along to these sites:
1) [http://www.bhagwad.com/blog/2010/technology/alps-synaptics-touchpad-configuration-in-lucid-lynx-ubuntu-10-04.html]("http://www.bhagwad.com/blog/2010/technology/alps-synaptics-touchpad-configuration-in-lucid-lynx-ubuntu-10-04.html")
2) [https://wiki.ubuntu.com/X/Config/Input#Input%20Configuration%20with%20udev%20%28Ubuntu%2010.04%29]("https://wiki.ubuntu.com/X/Config/Input#Input%20Configuration%20with%20udev%20%28Ubuntu%2010.04%29")

[COLOR="Red"][SIZE="6"]**Pre Lucid-Lynx (e.g. Karmic (9.10), Jaunty(9.4), etc.):**[/SIZE][/COLOR]
I recently purchased a Dell Studio 17 which came with an AlpsPS/2 ALPS GlidePoint touchpad.  Though this guide is specific to my Glidepoint, it may prove useful to other Alps touchpads.

To my knowledge, Alps and Synaptic are the two main supliers of touchpads to laptops.  While the Alps touchpads use the synaptics drivers to work in Ubuntu, it does not provide all the same functionality.  The main difference between the two is that most (?) synaptic touchpads are multi-touch.  This means that the pad can register two or more pressure points on it at once.  The Alps range can only register one no matter how many fingers you press with or how hard.  

But do not dispair! My Alps actually has a superior feel to it than my previous Synaptic and can be configured to use simulate the use of two fingers for vertical scrolling.  

How to check your touchpad type?  There are probably lots of ways, but I used: 
```
xinput -list
```
This lists all devices Hal knows how to configure on your computer.  Look for Synaptic or Alps under [XExtensionPointer] devices.

So, here's how to match my setup (with an explanation of what it is):

Firstly, input devices are no longer defined in xorg.conf.  This is great, becuase mistakes in configuration won't screw up your display.  Configuration and detection is now taken care of by hal (hardware abstraction layer) which supports hot-plugging (as of Jaunty) of input devices.

To start with, we need to provide hal the configuration file for the Alps touchpad.  Configuration is done via fdi files, so let's create one:
```
gksudo gedit /etc/hal/fdi/policy/shmconfig.fdi
```


I think you can probably name it whatever you like and hal simply reads all fdi files in this directory.

Here's what my file looks like (your milage with this may vary, but should provide a good starting point):
```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" string="synaptics">
      <merge key="input.x11_options.SHMConfig" type="string">True</merge>
      <merge key="input.x11_options.LeftEdge" type="string">0</merge>
      <merge key="input.x11_options.RightEdge" type="string">850</merge>
      <merge key="input.x11_options.TopEdge" type="string">300</merge>
      <merge key="input.x11_options.BottomEdge" type="string">550</merge>
      <merge key="input.x11_options.EmulateTwoFingerMinZ" type="string">100</merge>
      <merge key="input.x11_options.VertScrollDelta" type="string">7</merge>
      <merge key="input.x11_options.HorizScrollDelta" type="string">7</merge>
      <merge key="input.x11_options.HorizEdgeScroll" type="string">True</merge>
      <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
      <merge key="input.x11_options.MaxSpeed" type="string">1</merge>
      <merge key="input.x11_options.RTCornerButton" type="string">2</merge>
      <merge key="input.x11_options.RBCornerButton" type="string">3</merge>
      <merge key="input.x11_options.TapButton2" type="string">0</merge>
      <merge key="input.x11_options.TapButton3" type="string">0</merge>
    </match>
  </device>
</deviceinfo>
```

Let's walk through this.
Hal will read this file and when it finds the <match> element it will merge all the specified <merge> elements under the <match> into the matched default configuration it has (for the synaptics driver in this case).

All of the <merge> elements are our overrides of the default options.

The first is SHMConfig, which allows you to dynamically play around with the options on the fly, rather than changing this file and rebooting.  SHMConfig does present a security risk in shared computing environments so fiddler-beware.  SHMConfig allows you to use such programs as synclient, the best way to configure your touchpad to your exact requirements.

A few tips:
```
synclient -l
```
will list all of your current touchpad settings. And 
```
synclient LeftEdge=10
``` will let you set the left edge of the touchpad to 10.  Changes keep until next reboot (or restart of hal)
```
man synaptics
``` to see an explanation of all the options.

Now, back to my configuration.  The left, top, right and bottom edge allow you to define special regions of your touch pad.  For example, reducing the number of the right edge will increase the scrollable area of your one-finger vertical scroll.  I've made my scrollable area much bigger since it was so fiddly before.

I've set left to 0 since I don't have a special left area.  Top, Bottom and Right have all been modified to create 3 special regions:  The right scroll area, the top right corner and bottom right corner.  E.g. TopEdge of 100 and RightEdge of (maxValue-100) creates a 100x100 special area in the top right corner which, when tapped, can activate the left, middle or right button.  My top right corner (RTCornerButton) is set to middle-click (2) and bottom-right corner (RBCornerButton) is right click (3).  Again, my RTCorner and RBCorner are big so I can be lazy with my aim.  The original default for these corners is way to small in my opinion.

EmulateTwoFingerMinZ is how to enable the use of two fingers on a touchpad without multi-touch.  The value (100 in this case) is the touchpad pressure at which it will consider you using two fingers.  E.g. if the pressure rises above 100 it will count it as two fingers.  Play around with:
```
synclient -m 100
```
to see what works best for you pressure wise.  X,Y are the x,y coordinates of your press.  Z is the pressure.  F is the number of fingers (should always be 1 if you don't have multi-touch). See the man page for a more complete explanation.

Once EmulateTwoFingerMinZ is set, you can then turn VertTwoFingerScroll and HorizTwoFingerScroll on (1).  However, I've discovered with my Alps that the 2 finger tap (e.g. to middle-click) doesn't work very well.  Tapping alone even with 5 fingers wouldn't produce a pressure greater than about 40.  It's not until you move your multiple fingers along the touchpad that it registers a much greater pressure.  Hence, I've turned TapButton2 and TapButton3 off to prevent accidental usage. Play around with synclient -m and watch the Z value to see what I mean.

That's pretty much it.  The MaxSpeed and Delta entries determine the sensitivity of the touchpad.  Be forewarned that my settings above are rather on the sensitive side.  Also, there are lots of other options I've not used.  See the synaptics man page for more info.

Once you're done setting up your fdi file, rebooting is the easiest way to get hal to register your changes.  Happy touchpadding!

---

### Post by phorque on 2009-08-21
thanks, this worked perfectly for my Inspiron 1525 :)

i just disabled all the edge/corner stuff as all i wanted to was two-finger scrolling in both directions. epic win.

---

### Post by cknight on 2009-11-10
I've just upgraded to Karmic/9.10 and it broke my vertical two finger scrolling.  However, thanks to Raphael Mattos for this update from [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/463735/comments/3]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/463735/comments/3"):
> If you have an ALPS or other touchpad that isn't hardware multitouch capable, there is a problem with a default setting in hal. That's the minimum two finger width, but ALPS touchpads don't detect width. I have an HP dv4 notebook and solved this after creating the 11-x11-synaptics.fdi file in /etc/hal/fdi/policy and adding the "input.x11_options.EmulateTwoFingerMinW" option setting it to zero. The default is 7.

So, simply add this to make your two finger vertical scrolling work:
```
      <merge key="input.x11_options.EmulateTwoFingerMinW" type="string">0</merge>

```

---

### Post by rockdj on 2009-11-23
> **cknight said:**
> 
So, simply add this to make your two finger vertical scrolling work:
```
      <merge key="input.x11_options.EmulateTwoFingerMinW" type="string">0</merge>

```

Thank you!  That made everything happy. :D  The only extra thing I had to do in Karmic once I had this was to go and enable "Two finger scrolling" in the Mouse Preferences panel.

---

### Post by Otto Nascarella on 2009-12-07
Mate. FINALLY I've found a GOOD POST on the subject.

I've been trying this for AGES and now I got it!

My mistake was that I didn't which touchpad model I had, so I was always following SYNAPTICS tutorial (I bet loads of people are doing the same!)

In theory, if you have the latter, you don't need any other configuration if you already have Karmic Koala, right?

Well, I just wanna say a big thanks the ubuntu community, specially to cknight who wrote these brilliant instructions!



ciao for now!

---

### Post by edm1 on 2010-11-08
Would is it possible for someone to update this for Ubuntu 10.10. I think the config files have changed and I don't want to risk breaking something because i'm not really sure what i'm doing.

---

