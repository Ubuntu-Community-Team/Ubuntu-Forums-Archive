---
title: "Xorg.conf won't recognize touchpad"
date: 2009-06-07
forum: General Help
---

### Post by cknight on 2009-06-07
I've got a synaptics touchpad on my new laptop.  It works and I'm relativly happy, but I want to tweak it to take advantage of some of the additional functionality I'm sure exists (primarily 2-finger tap for middle click and 3-finger tap for right click).  My problem is that my changes to xorg.conf either aren't being recognized or don't work as nothing changes (with respect to the touchpad) after rebooting.  When I first edited the xorg.conf file there wasn't an InputDevice section, so I created it from scratch. Here is the current state of my xorg.conf:

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "InputDevice"
	Identifier "Synaptics Touchpad"
	Driver "synaptics"
	Option "CorePointer"
	Option "SendCoreEvents" "true"
	Option "Device" "AlpsPS/2 ALPS GlidePoint"
	Option "Protocol" "auto-dev"
#	Option "Device" "/dev/input/event12"
#	Option "Protocol" "event"
	Option "VertTwoFingerScroll" "true"
	Option "TapButton1" "1"
	Option "TapButton2" "2"
	Option "TapButton3" "3"
EndSection

Section "ServerFlags"
	Option "DontZap" "False"
EndSection

```

Here's the output of xinput list "AlpsPS/2 ALPS GlidePoint":
```
cknight@cknight-laptop:~$ xinput list "AlpsPS/2 ALPS GlidePoint"
"AlpsPS/2 ALPS GlidePoint"	id=5	[XExtensionPointer]
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
	Axis 1 :
		Min_value is 0
		Max_value is 767
		Resolution is 1

```

And finally, here's the listing of "cat /proc/bus/input/devices"
```
I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input13
U: Uniq=
H: Handlers=mouse2 event12 
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003

```

Any help is most appreciated!

---

### Post by Yellow Pasque on 2009-06-07
Are you using Ubuntu Jaunty? If so, you'll have to turn off input hotplugging if you want to configure input devices through xorg.conf: [http://wiki.archlinux.org/index.php/Xorg_input_hotplugging#I_don.27t_want_this_crap.2C_how_do_I_turn_it_off.3F](http://wiki.archlinux.org/index.php/Xorg_input_hotplugging#I_don.27t_want_this_crap.2C_how_do_I_turn_it_off.3F)

---

### Post by cknight on 2009-06-07
> **Temüjin said:**
> Are you using Ubuntu Jaunty? If so, you'll have to turn off input hotplugging if you want to configure input devices through xorg.conf: [http://wiki.archlinux.org/index.php/Xorg_input_hotplugging#I_don.27t_want_this_crap.2C_how_do_I_turn_it_off.3F](http://wiki.archlinux.org/index.php/Xorg_input_hotplugging#I_don.27t_want_this_crap.2C_how_do_I_turn_it_off.3F)

Ah, now this sounds promising.  Yes, I'm using Jaunty.  I'm confused though.  Is the situation that basically you get either configurability (via xorg.conf) OR hotplugging?  And is this just input device hotplugging (e.g. mouse/keyboard) or does this extend to other things such as external monitors or USB speakers for example?

---

### Post by cknight on 2009-06-07
Well, not sure how much further I am, but it appears that with hotplugging, hal and not xorg is responsible for the configuration of your input devices.  On the plus side, it appears that it is possible to configure the way Hal loads your devices via fdi files.  This post was quite helpful in understanding how it might work:

[http://www.linux.com/community/blogs/X-Server-Xorg-1.6-and-Input-Hotplug.html]("http://www.linux.com/community/blogs/X-Server-Xorg-1.6-and-Input-Hotplug.html")

Unfortunately, using the fdi file attached to the post (in the above URL) and even my own very stripped down version, I still can't enact any changes whatsoever.  Here's what my latest version looks like on the off chance some fdi expert is out there!

```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
 <device>
   <match key="info.capabilities" contains="input.touchpad">
     <match key="info.product" contains="Synaptics TouchPad">
       <merge key="input.x11_driver" type="string">synaptics</merge>
       <merge key="input.x11_options.SHMConfig" type="string">true</merge>
       <merge key="input.x11_options.Protocol" type="string">auto-dev</merge>
       <merge key="input.x11_options.LeftEdge" type="string">1700</merge>
       <merge key="input.x11_options.RightEdge" type="string">5300</merge>
       <merge key="input.x11_options.TopEdge" type="string">1700</merge>
       <merge key="input.x11_options.BottomEdge" type="string">4000</merge>
       <merge key="input.x11_options.HorizEdgeScroll" type="string">1</merge>
       <merge key="input.x11_options.VertEdgeScroll" type="string">1</merge>
       <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
       <merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>
       <merge key="input.x11_options.HorizScrollDelta" type="string">100</merge>
       <merge key="input.x11_options.VertScrollDelta" type="string">100</merge>
       <merge key="input.x11_options.FingerLow" type="string">25</merge>
       <merge key="input.x11_options.FingerHigh" type="string">30</merge>
       <merge key="input.x11_options.MinSpeed" type="string">0.25</merge>
       <merge key="input.x11_options.MaxSpeed" type="string">0.35</merge>
       <merge key="input.x11_options.AccelFactor" type="string">0.060</merge>
       <merge key="input.x11_options.MaxTapMove" type="string">220</merge>
       <merge key="input.x11_options.MaxTapTime" type="string">180</merge>
       <merge key="input.x11_options.MaxDoubleTapTime" type="string">200</merge>
       <merge key="input.x11_options.TapButton1" type="string">1</merge>
       <merge key="input.x11_options.TapButton2" type="string">2</merge>
       <merge key="input.x11_options.RTCornerButton" type="string">0</merge>
       <merge key="input.x11_options.RBCornerButton" type="string">0</merge>
       <merge key="input.x11_options.LTCornerButton" type="string">0</merge>
       <merge key="input.x11_options.LBCornerButton" type="string">0</merge>
     </match>
     <match key="info.product" contains="AlpsPS/2 ALPS">
       <merge key="input.x11_driver" type="string">synaptics</merge>
     </match>
     <match key="info.product" contains="appletouch">
       <merge key="input.x11_driver" type="string">synaptics</merge>
     </match>
     <match key="info.product" contains="bcm5974">
       <merge key="input.x11_driver" type="string">synaptics</merge>
     </match>
   </match>
 </device>
</deviceinfo>
```

As an aside, anyone know where Hal logs to?

---

### Post by Yellow Pasque on 2009-06-07
> Is the situation that basically you get either configurability (via xorg.conf) OR hotplugging?
Yes. Your other option is to edit the HAL policy file and then you can still keep the hotplugging ability. You would edit /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi and then copy that file to /etc/hal/fdi/policy/

EDIT: I see you beat me to it :P

---

### Post by Yellow Pasque on 2009-06-07
> **cknight said:**
> As an aside, anyone know where Hal logs to?
[https://wiki.ubuntu.com/DebuggingRemovableDevices](https://wiki.ubuntu.com/DebuggingRemovableDevices)

---

### Post by cknight on 2009-06-08
Well, its been a long journey, but I think I have finally figured out the problem(s).  After many attempts, I finally was able to get an fdi file to work for hal recognition.  Actually, I probably had it working for some time without realizing it.  You see, what I've been trying to accomplish for some time is to get my touchpad to do two-finger scrolling and two/three finger taps to emulate middle/right clicking.

So what was the issue?  Alps touchpads don't support multi-finger touch!  Damn.  Figures.  I upgrade my laptop after many years and get a touchpad with less functionality!  Oh well.

For the record, here's how I finally got SHMConfig to work. 
```
gksudo gedit /etc/hal/fdi/policy/shmconfig.fdi
```

In it, put the following:
```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" string="synaptics">
      <merge key="input.x11_options.SHMConfig" type="string">True</merge>
    </match>
  </device>
</deviceinfo>

```

Note, using SHMConfig is considered a security risk since other users can access the shared memory of the touchpad.  However, it makes on-the-fly changes to your touchpad possible.

Anyhow, reboot and you should finally be able to use gsynaptics (GUI) or the command line synclient.  It was using synclient that I discovered that my Alps touchpad wouldn't recognize multi-finger touch via:
```
synclient -m 100
```
Which records button presses, finger pressure, number of fingers, etc.  Very useful in figuring out which values to use.

Right, now I'm off to figure out how to emulate a middle button click!  Many thanks to Temüjin for the above help.

Finally, anyone else looking for more resources to help with their touchpad should check out [https://help.ubuntu.com/community/SynapticsTouchpad]("https://help.ubuntu.com/community/SynapticsTouchpad") or [http://ubuntuforums.org/showthread.php?p=7474290#post7474290]("http://ubuntuforums.org/showthread.php?p=7474290#post7474290")

---

