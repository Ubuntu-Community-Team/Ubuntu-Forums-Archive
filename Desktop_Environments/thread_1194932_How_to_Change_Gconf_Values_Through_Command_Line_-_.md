---
title: "How to Change Gconf Values Through Command Line - Dissabling Touchpad Example"
date: 2009-06-23
forum: Desktop Environments
---

### Post by hamidaddin on 2009-06-23
This is how to toggle gconf keys through a shell script (or command line):

You can get the key address of the item you want to change by running gconf from the terminal or ALT+F2

In my case, I want to toggle the touchpad on and off when I am typing. I searched in gconf for "touchpad" and found the "touchpad_enabled" key. When the key is highlighted, a Key Documentation appears in the lower panel. Under Key name I found and copied the full address of the key that I can access through the terminal using the gconftool (In this case the full name is: /desktop/gnome/peripherals/mouse/touchpad_enabled).

In the terminal:
Getting the current key value: 
gconftool --get /desktop/gnome/peripherals/mouse/touchpad_enabled

Assigning a new value (you have to put the type. In this case Boolean):
gconftool --type Boolean --set /desktop/gnome/peripherals/mouse/touchpad_enabled true

A simple shell script to toggle touchpad on and off would look like this:
```
#!/bin/bash
key_value=$(gconftool --get /desktop/gnome/peripherals/mouse/touchpad_enabled)
echo $key_value | grep "false"
if [[ $? -eq 0 ]] ; then
	gconftool --type Boolean --set /desktop/gnome/peripherals/mouse/touchpad_enabled true
else
	gconftool --type Boolean --set /desktop/gnome/peripherals/mouse/touchpad_enabled false
fi
```

You can then assign this to a keyboard shortcut for quick toggling.

Hope someone find this useful.

---

### Post by Mr. Picklesworth on 2009-08-17
Thanks for this. I just used this to throw together a button on my panel which toggles Metacity's compositor on and off.

Changed it just a tiny little bit to use /bin/sh, which if I understand properly makes this more portable.

```
#!/bin/sh
key_value=$(gconftool --get /apps/metacity/general/compositing_manager)
echo $key_value | grep "false"
if [ $? -eq 0 ] ; then
	gconftool --type Boolean --set /apps/metacity/general/compositing_manager true
else
	gconftool --type Boolean --set /apps/metacity/general/compositing_manager false
fi
```

Just dump it in your home folder, add a custom application launcher to your panel, drag a pretty icon to it (eg: /usr/share/icons/Tangerine/32x32/apps/desktop-effects.png) and you're all set.

---

