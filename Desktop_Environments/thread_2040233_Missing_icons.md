---
title: "Missing icons"
date: 2012-08-10
forum: Desktop Environments
---

### Post by michaeljmcd on 2012-08-10
When I am using XFCE, I notice that some icons are missing. Firefox, for example, shows up properly in the window button list, but when I alt-tab through the active windows, its icon is missing. Moreover, xterm is missing its icon in both the window button list and the alt-tab list.

How do I go about setting the icons so that they show up properly in both the window button list and the alt-tab list?

---

### Post by Toz on 2012-08-10
What icon theme are you using? (Settings Manager -> Appearance -> Icons tab). Maybe try changing the icon theme.

---

### Post by itcotbtoemik on 2012-08-10
> **michaeljmcd said:**
> When I am using XFCE, I notice that some icons are missing. Firefox, for example, shows up properly in the window button list, but when I alt-tab through the active windows, its icon is missing. Moreover, xterm is missing its icon in both the window button list and the alt-tab list.

How do I go about setting the icons so that they show up properly in both the window button list and the alt-tab list?

See [https://bugs.launchpad.net/ubuntu/+source/xterm/+bug/129041](https://bugs.launchpad.net/ubuntu/+source/xterm/+bug/129041)

---

### Post by michaeljmcd on 2012-08-10
> **Toz said:**
> What icon theme are you using? (Settings Manager -> Appearance -> Icons tab). Maybe try changing the icon theme.

"Icons" is currently set to "elementary Xfce dark". I tried each one, to no effect.

---

### Post by Toz on 2012-08-10
Can you list off the icon themes that you do have installed? I'm wondering if you're missing one.

---

### Post by michaeljmcd on 2012-08-11
> **Toz said:**
> Can you list off the icon themes that you do have installed? I'm wondering if you're missing one.

elementary Xfce
elementary Xfce dark
elementary Xubuntu dark
GNOME
High contrast
Hight contrast inverse
humanity
humanity-dark
login icons
lowcontrast
oxygen
oxygen
ubuntu-mono-dark
ubuntu-mono-light
unity-icon-theme

---

### Post by michaeljmcd on 2012-08-11
> **itcotbtoemik said:**
> See [https://bugs.launchpad.net/ubuntu/+source/xterm/+bug/129041](https://bugs.launchpad.net/ubuntu/+source/xterm/+bug/129041)

But I can get icons for xterm when I use KDE or Unity. Do I need to create something XFCE specific? When I look for relevant .desktop files, this is what I find:

```

% locate xterm.desktop 
/home/myser/.local/share/applications/debian-xterm.desktop
/usr/share/app-install/desktop/roxterm:roxterm.desktop
/usr/share/app-install/desktop/xterm:debian-xterm.desktop
/usr/share/app-install/desktop/xxxterm:xxxterm.desktop 
/usr/share/applications/debian-uxterm.desktop
/usr/share/applications/debian-xterm.desktop
/usr/share/applications/xterm.desktop
/usr/share/xfce4/helpers/nxterm.desktop 
/usr/share/xfce4/helpers/xterm.desktop
/usr/share/xubuntu/applications/debian-uxterm.desktop 
/usr/share/xubuntu/applications/debian-xterm.desktop

```

---

### Post by Toz on 2012-08-11
> **michaeljmcd said:**
> elementary Xfce
elementary Xfce dark
elementary Xubuntu dark
GNOME
High contrast
Hight contrast inverse
humanity
humanity-dark
login icons
lowcontrast
oxygen
oxygen
ubuntu-mono-dark
ubuntu-mono-light
unity-icon-theme

I also have the Tango icon theme, that you seem to be missing. Try adding **tango-icon-theme** and **tango-icon-theme-common**.

Do you have an ~/.gtkrc-2.0 file? If so, what are the contents of that file?

---

### Post by michaeljmcd on 2012-08-11
> **Toz said:**
> I also have the Tango icon theme, that you seem to be missing. Try adding **tango-icon-theme** and **tango-icon-theme-common**.

Do you have an ~/.gtkrc-2.0 file? If so, what are the contents of that file?

I added tango and Firefox shows an icon in the alt-tab window now, but xterm is still without an icon.

The file looks like:

```

# -- THEME AUTO-WRITTEN BY gtk-theme-switch2 DO NOT EDIT
include "/usr/share/themes/Clearlooks/gtk-2.0/gtkrc"

include "/home/michael/.gtkrc-2.0.mine"

# -- THEME AUTO-WRITTEN BY gtk-theme-switch2 DO NOT EDIT

```

the file in the 4th line does not exist on my system.

---

### Post by Toz on 2012-08-11
Out of curiosity, why are you using xterm? xfce4-terminal is the Xfce default terminal application and it integrates better in the environment. 

Now that I start up xterm, I have the same issue with the icon in the tab field.

---

### Post by michaeljmcd on 2012-08-11
> **Toz said:**
> Out of curiosity, why are you using xterm? xfce4-terminal is the Xfce default terminal application and it integrates better in the environment. 

Now that I start up xterm, I have the same issue with the icon in the tab field.

I tend to tinker with my desktop environment a lot (awesome wm being one of the ones I keep going back to, when I don't care about glitz or glitter) and xterm normally transfers well. It's fast, it's light, and the fonts look good after a couple of quick configuration changes.

But if XFCE handles it that poorly, I might just have to use xfce4-terminal in the meanwhile.

---

### Post by Toz on 2012-08-11
So I did some digging and found this link: [http://forum.xfce.org/viewtopic.php?id=6779]("http://forum.xfce.org/viewtopic.php?id=6779"). Too funny - no wonder I thought this question was familiar.

Anyways, you need the imagemagick program installed to access the convert command. Then, find an icon that you like and convert it to an xbm file:
```
convert /path/to/icon/file /path/to/xterm.xbm
```

Create an ~/.Xresources file with the following content:
```
xterm*iconPixmap:	/path/to/xterm.xbm
```

Then merge in the ~/Xresources file:
```
xrdb -merge ~/.Xresources
```

---

