---
title: "gaming mouse way too sensitive (too fast!)"
date: 2009-12-02
forum: Desktop Environments
---

### Post by fuzzybyte on 2009-12-02
I have a SteelSeries Ikari laser mouse which is rated for 3200cpi and so is very sensitive. I have tried to set mouse sensitivity and acceleration in gnome mouse panel to zero without any affect, it still goes way too fast for any normal desktop usage.

How can I slow down my mouse?

(I know, I could just turn down the sensitivity in the mouse itself, but I was able turn down the sensitivity down in Windows, so I want to do the same in Linux.)

---

### Post by taurolyon on 2010-02-21
If you're dual-booted to windows, log into windows, load up the mouse's software, and turn down the DPI.

I had a similar problem with my Steelseries Warcraft mouse running at 3200dpi (way to "touchy."), I turned it down to 1800 and it's alot better in gnome.


EDIT: Ack, sorry for rezzing an old post.. didn't see the date... (Was trying to find some support for my mouse....)

---

### Post by Tamale on 2010-09-29
use this:

[http://patrickmylund.com/blog/lowering-gaming-mouse-sensitivity-in-ubuntu-9-10/](http://patrickmylund.com/blog/lowering-gaming-mouse-sensitivity-in-ubuntu-9-10/)

Open a terminal
Run the command: xinput --list --short
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Razer USA, Ltd DeathAdder Mouse         	id=6	[slave  pointer  (2)]
&#9116;   &#8627; Razer USA, Ltd DeathAdder Mouse         	id=7	[slave  pointer  (2)]
&#9116;   &#8627; Razer DeathAdder                        	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Power Button                            	id=9	[slave  keyboard (3)]
    &#8627; Dell Dell USB Keyboard                  	id=10	[slave  keyboard (3)]
Note the name of your device. In my case, manipulating &#8216;Razer DeathAdder&#8217; worked.
Set the constant deceleration for the device:
xinput --set-prop "Razer DeathAdder" "Device Accel Constant Deceleration" 5
That&#8217;s it. You might have to play around with the value, but 5 slowed down my mouse sufficiently.

To see the current settings for the device:
xinput --list-props "Razer DeathAdder"
To turn off mouse acceleration:
xinput --set-prop "Razer DeathAdder" "Device Accel Velocity Scaling" 1
To perform the tuning automatically, I simply created a file containing the script below, ran chmod +x on it and added it to System -> Preferences -> Startup Applications in GNOME:

#!/bin/sh
xinput --set-prop "Razer DeathAdder" "Device Accel Constant Deceleration" 5
xinput --set-prop "Razer DeathAdder" "Device Accel Velocity Scaling" 1

---

### Post by cosmic_cow on 2012-11-19
You can script this and make it automagically grab the device id, too:

```

#!/bin/sh

mouse=` xinput | grep DeathAdder | awk '{print $6}' | awk 'BEGIN {FS="=";} {print $2}'`
xinput --set-prop $mouse "Device Accel Constant Deceleration" 5
xinput --set-prop $mouse "Device Accel Velocity Scaling" 1

```

Just save that into an executable bash script.

---

### Post by oldos2er on 2012-11-19
Old thread closed, please don't bump old threads.

---

