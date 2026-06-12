---
title: "Reduce delay for re-clicking a .desktop entry in Unity launcher"
date: 2015-05-14
forum: Desktop Environments
---

### Post by vaselinessa on 2015-05-14
[COLOR=#111111][FONT=Ubuntu]I have a number of homemade desktop entries in my Unity launcher, and I perceive that after I click on any of them, the clicked item experiences a delay of 5 or 6 seconds before it will respond to another click. This is a problem because I have a number of accessibility-oriented entries which should be clickable with greater frequency. (1/10 of a second would be ideal.)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
Is there any way for me to obviate or reduce this delay? Or can anyone explain why this delay occurs?
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Here is an example of my .desktop files:
[/FONT][/COLOR]
```
[Desktop Entry]
Name=Increase Bright by 5
Exec=/usr/bin/env bright +5
Icon=/usr/share/icons/kid-icarus.png
Type=Application
Terminal=false
StartupNotify=true
Categories=GTK;GNOME;Utility;
```

---

### Post by mc4man on 2015-05-14
Get rid of the StartupNotify line, it isn't needed & may help out the time issue

---

### Post by vaselinessa on 2015-05-14
Yes, that doesn't need to be there. I've gotten rid of it, but it has no perceptible effect. A perusal of the documentation for desktop entries makes me think that this key is not related to my problem:

> [COLOR=#000000][FONT=monospace]StartupNotify[/FONT][/COLOR]

[COLOR=#000000][FONT=Times New Roman]If true, it is KNOWN that the application will send a "remove" message when started with the DESKTOP_STARTUP_ID environment variable set. If false, it is KNOWN that the application does not work with startup notification at all (does not shown any window, breaks even when using StartupWMClass, etc.). If absent, a reasonable handling is up to implementations (assuming false, using StartupWMClass, etc.). (See the [/FONT][/COLOR][Startup Notification Protocol Specification]("http://www.freedesktop.org/Standards/startup-notification-spec")[COLOR=#000000][FONT=Times New Roman] for more details).[/FONT][/COLOR]

source: [http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html)

Or do you think that after making the change I need to refresh my launcher somehow? Is the button in my launcher somehow ignoring the changes in the file? (It seems to ignore changes to the icon setting.) I wouldn't ask this without testing, but I'm at the office and away from the workstation on which I have my Ubuntu installation.

---

### Post by CantankRus on 2015-05-14
Use middle click is the only solution I know.
The delay must be there so you don't launch multiple instances of a slow loading application.

---

### Post by vaselinessa on 2015-05-14
> **CantankRus said:**
> Use middle click is the only solution I know.

Alas, I'm using a touchscreen, so a middle click is not an option.

---

### Post by mc4man on 2015-05-14
There are some commands that aren't 100% suited to running via a launcher icon  in the Unity launcher (though they will work.
Typically the icon will pulse during which the launcher cannot be used, you didn't mention (or see?) that..

In those cases nothing much to be done, if more immediate action on is needed then make the .desktop executable & place on your Desktop or find another way to launch it  or run the command like a key binding, ect.

I have one here that if added/used from the launcher can only be re-used after about 7 sec.'s while if the script is executed from other means than the Unity launcher it can be re-run immediately.  (though in this case no reason to re-run

ex. for any curious - script to toggle unity launcher exposed or hidden
```
#!/bin/bash
key_value=$(dconf read  /org/compiz/profiles/unity/plugins/unityshell/launcher-hide-mode)
echo $key_value | grep "0"
if [[ $? -eq 0 ]] ; then
dconf write  /org/compiz/profiles/unity/plugins/unityshell/launcher-hide-mode 1
else
dconf write  /org/compiz/profiles/unity/plugins/unityshell/launcher-hide-mode 0
fi
```

If that is run from a simple .desktop there is a delay if in the Unity launcher but not elsewhere, ect. - 
```
[Desktop Entry]
Version=1.0
Type=Application
Name=Toggle Launcher
Exec=toggle6 
Icon=dvdisaster.png
```

---

### Post by vaselinessa on 2015-05-14
> **mc4man said:**
> There are some commands that aren't 100% suited to running via a launcher icon  in the Unity launcher

Interesting. What distinguishes commands that are suited from those that aren't? Is there a list I can read?

(Yes, I noticed the pulsing of the icon on my machine.)

---

### Post by mc4man on 2015-05-15
A list? - no. I don't think t's that specific. It's probably related to how the the Unity dock works. Without knowing how it works internally would be hard to say what's happening..
Another example would be if one clicked on an icon that required authentication then dismissed the auth box instead of completing action. Seen by having a synaptic icon in the dock. Click on it, then close/cancel the policykit popup. The synaptic icon would then pulse for a bit, ect.

---

