---
title: "Make Ctrl-L in Nautilus permanent?"
date: 2010-06-07
forum: Desktop Environments
---

### Post by rizzeh on 2010-06-07
I came across very useful nautilus keyboard shortcut Ctrl-L - change view of location bar to display full folder address but can't find an option to make this changed view permanent. Any ideas where can i find it? i don't mind editing config files :)

---

### Post by Breambutt on 2010-06-07
Alt+F2

gconf-editor

/apps/nautilus/preferences/always_use_location_entry

Thanks. I mean it. I was wondering why it didn't stay that way in Lucid but didn't bother looking for the entry until now.

---

### Post by sanderd17 on 2010-06-07
is there a way to show the button again? The button to switch between buttons as a path and a textual path.

---

### Post by rizzeh on 2010-06-07
thank you, Breambutt!  and thanks for gconf-editor tip, didnt know it existed. long live teh forums!\\:D/

---

### Post by rizzeh on 2010-06-07
> **sanderd17 said:**
> is there a way to show the button again? The button to switch between buttons as a path and a textual path.

i'd take a guess you could just relogin to desktop or use handy gconf-editor tool. dunno the shortcut :D

---

### Post by Pawello on 2012-01-14
> **sanderd17 said:**
> is there a way to show the button again? The button to switch between buttons as a path and a textual path.
Hi, I know it's old thread, but I wonder is it possible to make such button? Did anyone do that?

---

### Post by matza55 on 2012-01-14
> **Breambutt said:**
> Alt+F2

gconf-editor

/apps/nautilus/preferences/always_use_location_entry

Thanks. I mean it. I was wondering why it didn't stay that way in Lucid but didn't bother looking for the entry until now.

Thanks!

---

### Post by El Potro on 2012-01-28
> is there a way to show the button again? The button to switch between buttons as a path and a textual path.
Hi, I know it's old thread, but I wonder is it possible to make such button? Did anyone do that? 

Hi, **Pawello**. There is a workaround, not exactly to put the button there again, but what I did was to add a button to the gnome-panel, that executes a simple script to toggle between on and off. You could also assign a keyboard shortcut to it.

This is the script 

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

Hope it helps!

Source: [http://ubuntuforums.org/showthread.php?t=1194932](http://ubuntuforums.org/showthread.php?t=1194932)

---

### Post by Pharnavaziani on 2012-01-28
Hey all,

I just tried to use gconf-editor to make the textual location permanent, but no such option was present!  Anyone else have this problem?

I'm using 11.10 64-bit.

---

### Post by Krytarik on 2012-01-28
> **Pharnavaziani said:**
> I just tried to use gconf-editor to make the textual location permanent, but no such option was present! ...
[..]
I'm using 11.10 64-bit.
[https://help.ubuntu.com/community/RestoreNautilusLocationBar](https://help.ubuntu.com/community/RestoreNautilusLocationBar):
> Note that as from **Ubuntu 11.10** the setting is no longer  in gconf but has moved to dconf.  It is necessary to install  dconf-tools then run dconf-editor and the setting will be found in org &#10140;  gnome &#10140; nautilus &#10140; preferences &#10140; always-use-location-entryOr via command line:
```
gsettings set org.gnome.nautilus.preferences always-use-location-entry true
```To disable that option again, just replace "true" with "false" in the command, obviously.

Regards.

---

### Post by Pharnavaziani on 2012-01-28
Thanks.  Shoulda looked around before posting.

---

### Post by Omar Othman on 2012-06-21
Press Escape while the cursor is in the location bar.

---

