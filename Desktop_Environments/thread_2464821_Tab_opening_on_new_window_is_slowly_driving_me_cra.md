---
title: "Tab opening on new window is slowly driving me crazy..."
date: 2021-07-13
forum: Desktop Environments
---

### Post by dbee on 2021-07-13
This must happen to me at least 13 times a day.

I click on a tab in chrome and the tab opens in a new window. Then I have to click on the tab again and put it back in it's original window.

And on and on and on...

Pls tell me there is some sort of chrome hack to stop this happening in the future....

thanks,

---

### Post by monkeybrain20122 on 2021-07-13
Tabs don't open in new window unless you choose to. You must have set some kind of preferences or maybe an extension is acting up.

---

### Post by cmcanulty on 2021-07-14
Happens to me in Firefox a lot also. I have never been able to figure out why. I am running Xubuntu 20.04. I think it may be a mouse thing but what I don't know.

---

### Post by Holger_Gehrke on 2021-07-14
If this happens with a touchpad, I'd try unsetting 'Tapping Drag Enabled' using xinput ('xinput set-prop *devicename* "libinput Tapping Drag Enable" 0'). If it's a mouse than you might try setting the distance the mouse can be moved with a button pressed before it gets recognized as a 'drag' higher (in XUbuntu that's available in the mouse settings applet, don't know about other flavours ...).

Holger

---

### Post by dbee on 2021-07-19
I get this error message when i try your solution Holger.

Wasn't there supposed to be a config file in /etc that I could use to adjust the touchpad? Or is that gone now?

> dara@laptop-20-04:~$ xinput set-prop 'SynPS/2 Synaptics TouchPad' "libinput Tapping Drag Enable" 0
property 'libinput Tapping Drag Enable' doesn't exist, you need to specify its type and format
dara@laptop-20-

---

### Post by Holger_Gehrke on 2021-07-19
Check what properties do exist for your touchpad with "xinput list-props 'SynPS/2 Synaptics TouchPad"; the names are mostly quite self-explanatory. And yes, you could set up a configuration file for the touchpad in /etc/X11/xorg.conf.d/, (assuming that you're using X and not Wayland ...). But X on Ubuntu is mostly self-configuring - so there are no config files by default - and a bad enough mistake in a configuration file might break X to the point where you have to go to a virtual terminal to fix things, so I usually avoid going that route.

Holger

---

### Post by dbee on 2021-08-12
@Holger_Gehrke

> 
dara@laptop-20-04:~$ xinput list-props "SynPS/2 Synaptics TouchPad"
WARNING: running xinput against an Xwayland server. See the xinput man page for details.
unable to find device SynPS/2 Synaptics TouchPad


> 
dara@laptop-20-04:~$ cat /proc/bus/input/devices | grep -i 'touchpad'
N: Name="SynPS/2 Synaptics TouchPad"


man XWaypoint isn't very useful. Still having the same issue.

Tried Settings->Touchpad but that doesn't seem to help...

---

### Post by Holger_Gehrke on 2021-08-13
If you're using Wayland, configuring the touchpad through **x**input is not going to be very useful because you're only configuring the X11 emulation layer of Wayland and programs that talk to Wayland directly will not be influenced by your configuration. With Wayland it's mostly graphical configuration or nothing. If the graphical tools don't offer a way to do something, then you're out of luck on Wayland.

You might try to find out the right name to use for your touchpad in xinput with 'xinput list --name-only'. The right name for your touchpad should be obvious on that list. There's also 'libinput list-devices' which should work with Wayland correctly. The 'libinput' executable will allow you to see settings for all devices controlled through libinput but sadly has no way to change those settings.

Holger

---

### Post by dbee on 2021-08-20
thanks @Holger_Gehrke

```

Device:           SynPS/2 Synaptics TouchPad
Kernel:           /dev/input/event4
Group:            7
Seat:             seat0, default
Size:             119x62mm
Capabilities:     pointer gesture
Tap-to-click:     disabled
Tap-and-drag:     enabled
Tap drag lock:    disabled
Left-handed:      disabled
Nat.scrolling:    disabled
Middle emulation: disabled
Calibration:      n/a
Scroll methods:   *two-finger edge 
Click methods:    *button-areas clickfinger 
Disable-w-typing: enabled
Accel profiles:   flat *adaptive
Rotation:         n/a

```

so you're saying i can see the value is enabled in Wayland. But i can't disable it? :-(

---

### Post by Holger_Gehrke on 2021-08-20
> **dbee said:**
> So you're saying i can see the value is enabled in Wayland. But i can't disable it? :-(

That's my understanding of the situation, yes. It might be possible to make some settings through 'gsettings set org.gnome.desktop.peripherals.touchpad *settingname* *settingvalue*', but since I don't use Gnome (or Wayland for that matter; I'm using XUbuntu and XFCE isn't compatible with Wayland ... yet ...) I can't test this.

I find it strange that you have tap-to-click deactivated and tap-and-drag active. From my reading of the libinput documentation tap-and-drag only works if tap-to-click is active.

Holger

---

### Post by dbee on 2021-08-20
Thanks Holger,

I'm not sure it is possible. When i do a ...
```

dara@laptop-20-04:~$ gsettings set org.gnome.desktop.peripherals.touchpad tap-and-drag false

dara@laptop-20-04:~$ gsettings get org.gnome.desktop.peripherals.touchpad tap-and-drag
false

```
which seems to be fine. Then i restart X...
```

dara@laptop-20-04:~$ sudo systemctl restart gdm

```
and then check the libinput...
```

Device:           SynPS/2 Synaptics TouchPad
Kernel:           /dev/input/event4
Group:            7
Seat:             seat0, default
Size:             119x62mm
Capabilities:     pointer gesture
Tap-to-click:     disabled
Tap-and-drag:     enabled
Tap drag lock:    disabled
Left-handed:      disabled
Nat.scrolling:    disabled
Middle emulation: disabled
Calibration:      n/a
Scroll methods:   *two-finger edge 
Click methods:    *button-areas clickfinger 
Disable-w-typing: enabled
Accel profiles:   flat *adaptive
Rotation:         n/a

```

```

dara@laptop-20-04:~$ gsettings list-recursively org.gnome.desktop.peripherals.touchpad
org.gnome.desktop.peripherals.touchpad tap-button-map 'default'
org.gnome.desktop.peripherals.touchpad click-method 'fingers'
org.gnome.desktop.peripherals.touchpad edge-scrolling-enabled false
org.gnome.desktop.peripherals.touchpad disable-while-typing true
org.gnome.desktop.peripherals.touchpad two-finger-scrolling-enabled true
org.gnome.desktop.peripherals.touchpad send-events 'enabled'
org.gnome.desktop.peripherals.touchpad speed 0.0
org.gnome.desktop.peripherals.touchpad scroll-method 'two-finger-scrolling'
org.gnome.desktop.peripherals.touchpad natural-scroll true
org.gnome.desktop.peripherals.touchpad middle-click-emulation false
org.gnome.desktop.peripherals.touchpad left-handed 'mouse'
org.gnome.desktop.peripherals.touchpad tap-to-click true
org.gnome.desktop.peripherals.touchpad tap-and-drag-lock false
org.gnome.desktop.peripherals.touchpad tap-and-drag false

```

The setting seems to have been changed. But isn't. I can still tap-and-drag on gnome...? I've read the gsettings man page. But i'm still none the wiser.

---

### Post by T6&amp;sfpER35% on 2021-08-21
have you seen [this](https://kingpinbrowser.com/blog/chrome-tabs-issue/) ?
might help

---

