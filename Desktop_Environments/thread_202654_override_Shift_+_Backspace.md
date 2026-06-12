---
title: "override Shift + Backspace"
date: 2006-06-23
forum: Desktop Environments
---

### Post by arthur_kalm on 2006-06-23
Hi everyone,

I am using Kubuntu and it seems that there is no way to override the Shift+Backspace keyboard shortcut which _kills X_. In GNOME I was able to override it but in KDE I cannot. This seems to be a shortcut associated with X rather then any of the desktop environments but I need to remove it. I press this keyboard combination all the time when I type (accidentally) and ](*,) 

I'm not entirely sure what the logic of making a keyboard shortcut that actually _kills X_ a 2 key shortcut, and what the hell was wrong with Ctrl + Alt + Backspace? Why do you need two shortcuts to kill X?

Hmm, well any help would be greatly appreciated. I tried looking around but haven't found anything yet.

---

### Post by matgates on 2006-06-24
It should be control-alt-backspace, not just shift-backspace.  It could be that you have some accessibility feature enabled which makes control a sticky key or something like that which is making it seem like a two key combo (check settings in: KDE system settings -> Personal -> Regional & Accessibility -> Accessibility (icon) -> Modifier Keys (tab).

In any case you can disable it by adding the following to the end of your /etc/X11/xorg.conf file:

```

Section "ServerFlags"
        Option "DontZap"
EndSection

```

If your xorg.conf file already includes a ServerFlags section, just add the *Option "DontZap"* line to the existing section.

---

### Post by arthur_kalm on 2006-06-25
It seems to have disabled the Ctrl+Alt+Backspace command but Shift+Backspace still seems to kill X. A friend has told me that Shift+Backspace does not kill his X in Ubuntu 6.06.

Furthermore, I do not have sticky key or anything else out of the ordinary enabled. But this does not seem to be a KDE issue as it kills X in GNOME and in the login screen. I'm not really sure what else can be done.. perhaps a reinstall? Maybe there was a problem during installation?

---

### Post by porchcth on 2006-06-25
Hi arthur,

do you have XGL installed? 
If so, you can turn off the annoying shift-backspace combination with
```
xmodmap /usr/share/xmodmap/xmodmap.de &
```

You can add it to startcompiz.sh or whatever file you start compiz with.

Regards,

porch.

---

### Post by arthur_kalm on 2006-06-25
porch, thank you so much that worked! Perhaps I should have mentioned that I had XGL installed...

Now, I can't really use xmodmap.de as I do need an English layout. I tried xmodmap.us but all of the XGL shortcuts didn't work. xmodmap.us-101 seems to work well in GNOME but in KDE the super-key is on by default and so trying to scroll with the mouse zooms in and zooms out...

---

### Post by evil_elman on 2006-06-25
I had the exact same problem and I used the following without any adverse effects:

xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"

---

### Post by arthur_kalm on 2006-06-25
Thank you so much evil_elman! Works like a charm!

---

### Post by evil_elman on 2006-06-25
Compiz.net forum is your friend... ;-) At least mine...

---

### Post by arthur_kalm on 2006-06-25
Hehe yeah, I should have realized that this was a problem with XGL rather than just an ubuntu problem (especially after my friend who doesn't have XGL said that shift+backspace did nothing on his computer)... but thank you.

---

### Post by bimargulies on 2008-04-29
As of 8.04, suddenly, shift-backspace went live for me (to my distress) with xubuntu. The recipe above fixed it.

---

### Post by molotov00 on 2008-06-12
I searched and this worked... only after I realized they were double quotes and not apostrophes.

```
xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"
```

But, this does not work. The directory doesn't exist. 
```
xmodmap /usr/share/xmodmap/xmodmap.de &
```
This isn't really for me because I got it fixed but I think this it's important that others can easily figure out how to stop this 'feature'.

I'm running Xubuntu 8.04 with Compiz and Emerald.

---

