---
title: "Changing KDE Themes"
date: 2006-02-26
forum: Desktop Environments
---

### Post by thrakirr on 2006-02-26
Is there a command to change theme/style from the console? I did something to the theme that somehow broke the System Settings panel, and there are no icons on it. ... soo, Any non-GUI way to change my theme, or reset to defaults, would be awesome.

Thanks.

---

### Post by aysiu on 2006-02-26
You could try ```
nano ~/.kde/share/config/kwinrc
``` I don't know how you would edit it, though. I use the Plastik theme, and mine looks like this: ```
[[$Version]
update_info=kwin.upd:kde3.0r1,kwin.upd:kde3.2Xinerama,kwin3_plugin.upd:kde3.2,k$

[Desktops]
Name_1=
Name_2=
Name_3=
Name_4=
Number=4

[MouseBindings]
CommandActiveTitlebar2=Lower
CommandActiveTitlebar3=Operations menu

[Style]
BorderSize=1
ButtonsOnLeft=
ButtonsOnRight=IAX
PluginLib=kwin3_plastik
ShowToolTips=true

[Windows]
AltTabStyle=KDE
AnimateMinimize=false
AnimateShade=false
FocusPolicy=ClickToFocus
IgnoreFocusStealingClasses=kio_uiserver
MoveMode=Transparent
MoveResizeMaximizedWindows=false
ResizeMode=Transparent
ShadeHover=false
TitlebarDoubleClickCommand=Shade
``` It seems easily editable, but I'd have had to know my theme was actually called *kwin3_plastik* and not just *plastik*.

Have you tried using ```
kcontrol
``` instead of ```
systemsettings
```?

---

### Post by awakatanka on 2006-02-26
Only way i know is gui way , but maybe you can remove the .kde map in youre home dir to correct all.

Else try kcontrol its the real kde systemsettings gui.

---

### Post by fdoving on 2006-02-26
[QUOTE=thrakirr]Is there a command to change theme/style from the console? I did something to the theme that somehow broke the System Settings panel, and there are no icons on it. ... soo, Any non-GUI way to change my theme, or reset to defaults, would be awesome.

Thanks.[/QUOTE]

If you want to change the style you can edit ~/.kde/share/config/kcmthememanagerrc

Example kcmthememangerrc contains theese two lines:

[I]
[General]
CurrentTheme=lipstik_std_kubuntu
[/I]


- Frode

---

### Post by thrakirr on 2006-02-26
nano ~/.kde/share/config/kwinrc
worked.

Thanks. :)

---

