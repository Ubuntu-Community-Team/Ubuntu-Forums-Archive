---
title: "How to detect current theme from terminal?"
date: 2013-01-02
forum: Desktop Environments
---

### Post by leon.vitanos on 2013-01-02
First thing is always searching google.
i found this:
[http://ubuntuforums.org/showpost.php?p=4769893&postcount=2](http://ubuntuforums.org/showpost.php?p=4769893&postcount=2)

the commands always outputs
Ambience
ubuntu-mono-dark
Ambience

whatever the current theme is. But is from 2008 so its reasonable somethings to have changed. Any ideas on how can i do it now? ):P

---

### Post by Frogs Hair on 2013-01-02
Ubuntu has used the dconf editor on Gnome 3.xx since 11.10 and in 2008 the Gnome 2 was still in use . I don't how commands might have changed though.

My output displays a theme I tried and completely removed two days ago. :confused:

---

### Post by kansasnoob on 2013-01-02
You don't mention what version of Ubuntu you're using but I figured this out for 12.04 with the Unity-2D and classic (no effects) sessions:

```
gconftool-2 -g /apps/metacity/general/theme
```

```
gsettings get org.gnome.desktop.interface gtk-theme

```
```
gsettings get org.gnome.desktop.interface icon-theme
```

```
gsettings get org.gnome.desktop.interface cursor-theme
```

I'd think the latter three would be the same with Compiz but the first one may be different. You may find some other useful stuff here:

[http://ubuntuforums.org/showpost.php?p=11993655&postcount=70](http://ubuntuforums.org/showpost.php?p=11993655&postcount=70)

---

### Post by stinkeye on 2013-01-02
[COLOR="Red"]Edit[/COLOR]...Too slow :)

Use gsettings to get dconf values.
The last one is your window or titlebar theme.
```
gsettings get org.gnome.desktop.interface gtk-theme
gsettings get org.gnome.desktop.interface icon-theme
gsettings get org.gnome.desktop.interface cursor-theme
gsettings get org.gnome.desktop.wm.preferences theme
```

---

### Post by vasa1 on 2013-01-02
> **stinkeye said:**
> [COLOR="Red"]Edit[/COLOR]...Too slow :)

Use gsettings to get dconf values.
The last one is your window or titlebar theme.
```
gsettings get org.gnome.desktop.interface gtk-theme
gsettings get org.gnome.desktop.interface icon-theme
gsettings get org.gnome.desktop.interface cursor-theme
gsettings get org.gnome.desktop.wm.preferences theme
```

Doesn't work for a pure Lubuntu 12.10. I see:```
[07:40 AM] ~ $ gsettings get org.gnome.desktop.interface gtk-theme
'Adwaita'
[07:41 AM] ~ $ gsettings get org.gnome.desktop.interface icon-theme
'gnome'
[07:41 AM] ~ $ gsettings get org.gnome.desktop.interface cursor-theme
'Adwaita'
[07:41 AM] ~ $ gsettings get org.gnome.desktop.wm.preferences theme
'Adwaita'
[07:41 AM] ~ $ 

```Any ideas what will work for Lubuntu?

---

