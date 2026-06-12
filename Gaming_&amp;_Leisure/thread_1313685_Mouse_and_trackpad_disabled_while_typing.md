---
title: "Mouse and trackpad disabled while typing"
date: 2009-11-03
forum: Gaming &amp; Leisure
---

### Post by adrn on 2009-11-03
This is the exact behaviour some people want, however...
  
I had World of Warcraft set up so that I had my left hand free for most keyboard commands, my left thumb on spacebar for moving my char, and my right hand on a trackball for steering, camera adjustment, and clicking on objects in the environment. 
Since upgrading to Karmic Koala, any keyboard key except for control keys FREEZES the mouse pointer, whether I am using the trackball or the touchpad (pad built into Adesso keyboard) for about a half second.  This makes holding spacebar down and using the trackball for steering impossible.

So far as I can tell, the synaptics driver is NOT loaded --at least, 
"lsmod |grep syn" returns nothing.  
The touchpad control panel fails to load (with the usual "SHMconfig" complaint); no touchpad control tab shows in the "Mouse" control panel.  
None of the fixes to get SHMconfig fixed (/etc/X11/xorg.conf, /etc/hal/..., /usr/share/hal...) made any difference. 

 *BTW, shouldn't a properly written install script for the touchpad control panel have at least made a commented-out entry in the correct file, and popped up some kind of readme about it?  What's the point of a new-user friendly GUI that forces manual research and editing of arcane config files?*

Run as root, "tpconfig" returns

Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
Sensor type: unknown (0).
Geometry: rectangular/landscape/up.
Packets: absolute, 80 packets per second.
Corner taps disabled;        no tap gestures.
Edge motion: none.
Z threshold: 6 of 7.
2 button mode; corner tap is right button click

BUT none of the commands to change the trackpad's behavior
do anything.

"touchfreeze" run as root from console displays:

root@duck:/home/adrn# touchfreeze
SynDaemon::SynDaemon 
set daemon true 
set pad true 
using typing delay of 500 ms 
"/usr/bin/synclient" 
initial state is TouchpadOff= 0 
start typing
Couldn't find synaptics properties. No synaptics driver loaded?

Here too, none of the controls actually change anything.

All the expected functions of the trackpad (touch drag, corner = right button, right side = mouse wheel) work, 
and have always worked, with no driver installation by me, on any system I plugged it into (Ubuntu Intrepid, Jaunty, Karmic; Win2k).

 World of Warcraft allows for both mouse buttons down at once for movement, 
but I have mild carpal tunnel which gets pushed from a nearly non-existent problem into a genuinely uncomfortable condition by prolonged, continuous usage of my right middle and index fingers.
Therefore, switching to the left thumb instead for continuous usage is essential.

Any ideas on what may have changed in "Karmic" to trigger this new behavior?
Did some "helpful" developer decide to hard-code 500 ms of mouse lockout after every keyboard press?  
Again, under Jaunty, I could hold the spacebar down without affecting the touchpad or trackball at all.
I should note that unplugging the trackpad cable (ps2 connector through a USB adapter) and rebooting does not change the behavior -- trackpad still locked out for 500 ms by keyboard press.

With all the other grief I'm reading about, we must have built up some really bad Karma.

---

### Post by frprovis on 2009-11-04
> **adrn said:**
> 
Did some "helpful" developer decide to hard-code 500 ms of mouse lockout after every keyboard press? 

Yep. See
[http://ubuntuforums.org/showthread.php?t=1309104](http://ubuntuforums.org/showthread.php?t=1309104)

You need to use System->Preferences->Mouse and uncheck the "disable touchpad while typing" option. If you are like me and want this feature, but with a longer timeout interval, then you'll need to start syndaemon yourself with the appropriate parameters, as described on the man page. 

You wouldn't happen to know how to report a bug to the developers? I'm new to linux so I don't know. I consider hardcoding the timeout interval rather than making it user-specifiable to be a bug. In fact, if they are going to use a GUI to start syndaemon, then they need to make all the syndaemon options available on the GUI. It is really half-assed to have configuration sometimes use a GUI and sometimes not. Furthermore, syndaemon should do like in windows, which disables the touchpad if another pointing device (mouse) is connected.

---

### Post by adrn on 2009-11-05
The touchpad tab never got added to my mouse control panel during the upgrade.
Syndaemon is not running; further, if I try to launch it manually, 
I get the error message:
"Unable to find a synaptics device."

A few kind souls on the IRC channel were willing to try holding a key down while trying to move mouse.   One had the mouse move freely, one's mouse continued to move after a brief pause, while yet others reported the same behavior I'm seeing.

I tried booting to a CD -- mouse moves while keyboard keys are held down there just fine.  I'm backing up folders I dont want to lose (mainly .wine with 27G of WoW installed) and may nuke this installation and do a clean install.  

Bugs get reported to launchpad, I think

---

### Post by Kerin on 2009-11-30
I have all these issues: SHMConfig is enabled in xorg AND hal, gsynaptic and synclient can't access shared memory, and syndaemon can neither detect a synaptics device nor access shared memory.

Curously, tpconfig detects the synaptics (actually an Elantech, but whatever) but won't configure it.

The only difference between my issues and the OP's is that my touchpad isn't disabled while typing and it's driving me crazy.  Running Karmic (9.10) on a Dell Mini 10.

---

