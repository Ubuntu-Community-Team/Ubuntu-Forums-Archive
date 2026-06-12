---
title: "compiz-vanilla scale hotkeys broken"
date: 2006-07-18
forum: Desktop Environments
---

### Post by jakemikey on 2006-07-18
Hi all,

I've scoured around for a solution to this problem, but I can't find one.  I've been going back and forth between the quinn and vanilla versions of compiz.  I've settled on vanilla because I like the more conservative default settings and it seems less prone to weird errors.  However, I can't activate the scale plugin via the typical F10, F11 shortcuts.  I've set F10 as the activate/deactivate button in gconf-editor, but it reports that "no schema exists for this key" -- not sure what that means.  The plugin itself is functional, as the hot mouse corners activate it, but I can't seem to assign a shortcut key.  All this works fine in the quinn debs.

Does anyone know how I can fix this?

Thanks in advance.

PS - I'm running compiz-vanilla and compiz-vanilla-gnome 0.0.13+cvs20060713

---

### Post by shrift on 2006-07-18
Try setting the shortcut with the "gset-compiz" package. It makes all that stuff much easier.

---

### Post by jakemikey on 2006-07-18
> **shrift said:**
> Try setting the shortcut with the "gset-compiz" package. It makes all that stuff much easier.

Actually, that's another thing I've tried.  Activate and deactivate are set to F10 both in gset-compiz and gconf-editor. Still no dice.

---

### Post by shrift on 2006-07-18
Huh. But it works fine when you have the quinndebs installed?

Is your keyboard layout properly set? 

try using the xmodmap and xkb commands to set your keyboard layout properly:

```
xmodmap /usr/share/xmodmap/xmodmap.us
setxkbmap us
```

that is of course assuming your keyboard layout is US. If not then us whatever it is.

---

### Post by jakemikey on 2006-07-18
> **shrift said:**
> Huh. But it works fine when you have the quinndebs installed?

Is your keyboard layout properly set? 

try using the xmodmap and xkb commands to set your keyboard layout properly:

```
xmodmap /usr/share/xmodmap/xmodmap.us
setxkbmap us
```

that is of course assuming your keyboard layout is US. If not then us whatever it is.

Yes, the scale plugin works as expected under the quinn debs. I'm fairly certain my kb layout is properly set - not sure why it would change by installing the compiz-vanilla packages.  I've gone back and forth several times today between quinn and vanilla and quinn works each time, while vanilla does not.

Anyway, I ran your commands just to be safe and here's what I got:

jake@ubuntu:~$ xmodmap /usr/share/xmodmap/xmodmap.us
jake@ubuntu:~$ setxkbmap us
Couldn't interpret _XKB_RULES_NAMES property
Use defaults: rules - 'xorg' model - 'pc101' layout - 'us'

---

### Post by deeek on 2006-07-18
> **jakemikey said:**
> Hi all,
...

Does anyone know how I can fix this?

Thanks in advance.

PS - I'm running compiz-vanilla and compiz-vanilla-gnome 0.0.13+cvs20060713


I had this same problem (and a few others with keybindings) with the quinndeb version and it seems to be fixed with the version released today: 0.0.13-0quinn18.  So, you might want to get an updated vanilla or use quinn's.

---

