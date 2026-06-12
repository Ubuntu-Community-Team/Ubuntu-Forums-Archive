---
title: "Configuring laptop touchpad in GNOME"
date: 2011-04-20
forum: Desktop Environments
---

### Post by Eggbertx on 2011-04-20
I had this problem in Fedora too, so I know it isn't just Ubuntu. By default, for whatever reason, GNOME uses two finger scrolling, but to simulate a middle click, you need to tap three fingers, and to right click with the touchpad, you need to tap two fingers. I've tried creating a shell script that does 
```

synclient TapButton2=2 TapButton3=3

```
and having it run at startup, but as soon as I close the lid (I have it set to do nothing when the lid closes)
I also tried putting this in /usr/share/X11/xorg.conf.d/50-synaptics.conf to no avail:
```

Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
		Option "TapButton1" "1"
		Option "TapButton2" "2"
		Option "TapButton3" "3"

EndSection

```
That doesn't even do anything at all.

---

### Post by Eggbertx on 2011-04-21
...does anyone know udev?

---

### Post by Copper Bezel on 2011-04-21
If the scrolling part is a problem, that can be set through Gnome's Mouse settings.

It's very strange - I've never had Synclient settings unset themselves, like the Orientation value that my trackpad supports, but you're right that this one does on resuming from suspend. (I didn't get it on sleeping just the monitor; that's fairly strange, still.) If I wanted to reverse the settings on my machine, I'd have to add a script to my resume folder in ACPI. If it's really resetting even when the *monitor* sleeps, then we really need to find where the default settings are being stored and edit the settings *there*.

Edit: Do you have the screenlock turned on for when you close the lid?

---

### Post by Eggbertx on 2011-04-21
It's not the scrolling that's the issue, it's the actual tap, like for middle mouse button and right click emulation. And no, it doesn't lock the screen.
Actually, closing the lid doesn't reset it, but it did in Fedora. How would I have it run the synclient command at startup? I've tried
~/my_settings.sh
gnome-terminal -e ~/my_settings.sh
gnome-terminal ~/my_settings.sh
synclient TapButton2=2 TapButton3=3
and none of them seem to work. If I put it in ~/.bashrc [http://www.linuxquestions.org/questions/slackware-14/auto-execute-shell-script-on-startup-294891/would](http://www.linuxquestions.org/questions/slackware-14/auto-execute-shell-script-on-startup-294891/would) that work?

Edit: nevermind, that didn't work. I even tried /etc/rc.local, and that didn't work either. I know it is possible in linux, because I did it easily in KDE.

---

### Post by Copper Bezel on 2011-04-22
Got it. Run 

```
xmodmap -e "pointer = 1 2 3 4 5"
```

and it'll stick for the whole session, so you can just set it as a startup app. = )

(Note that this *will* affect *any* mouse attached, so it's not the perfect workaround.)

---

### Post by Eggbertx on 2011-04-23
But the synclient one should have worked at start up also. I'll try it anyway.

Update: It worked when I ran it in the terminal, but not at startup. :mad:

---

### Post by Copper Bezel on 2011-04-23
> But the synclient one should have worked at start up also. 

Yeah, except that it's being reset at the drop of a hat. = )

> Update: It worked when I ran it in the terminal, but not at startup.

It's working for me, but my startup apps are a sequenced script. Maybe it's being overridden by something else at boot, so like practically every other startup application, it needs a delay added before the command:

```
sleep 30s; xmodmap -e "pointer = 1 2 3 4 5"
```

---

### Post by Krytarik on 2011-04-23
I'm quite sure that it's gnome-settings-daemon. When I first set up a startup script to remap my CapsLock key, instead of just with ".Xmodmap" like I have it now, I had to delay the script, too. So, delaying the 'synclient' script should fix it imo.

---

### Post by Eggbertx on 2011-04-23
It still isn't working.

Edit: Oh I didn't see your post Krytarik, I'll mess around with the timing. I hate gnome-settings-daemon with a passion. It also makes it a pain to replace gnome-screensaver with Xscreensaver. At least in Fedora I could just uninstall it, and Xscreensaver would take over, but I have Ubuntu Studio, and Ubuntustudio-desktop and another Ubuntu studio package depend on it

Edit edit: I found it!! All I had to do was prevent gnome-settings-daemon from messing with the mouse settings! For anyone else who stumbles on this thread and has this issue, I went to /apps/gnome-settings-daemon/plugins/pointing-device and mouse and unchecked "active", though I'm not sure which one did it, but I don't really care.

---

