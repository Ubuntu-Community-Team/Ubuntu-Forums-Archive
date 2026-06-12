---
title: "Is it possible to modify Control Panel settings via a script?"
date: 2005-08-12
forum: Desktop Environments
---

### Post by bsoric on 2005-08-12
Hello
I'm trying to write a script that can edit my control center settings for me automatically, however I'm not sure what the command to do so is, or even if its possible.
I want to be able to edit the background picture of the panel, and toggle the panel's transparency setting.

Any help would be greatly appreciated.

Brett

---

### Post by daller on 2005-09-04
Kcontrol is just editing some config-files on your system...

...a lot of them are placed i $HOME/.kde/share/

About the panel:

$HOME/.kde/share/config/kickerrc

---

### Post by daller on 2005-09-04
in kickerrc, simply find this passage - the rest is quite self-explanatory:

[General]
Alignment=1
Applets2=KMenuButton_1,ExtensionButton_1,ServiceButton_2,ServiceButton_3,ServiceMenuButton_1,ExtensionButton_2,Applet_1,Applet_2,Applet_6,Applet_7,Applet_3,Applet_4,Applet_5
AutoHideDelay=3
AutoHidePanel=false
AutoHideSwitch=false
BackgroundHide=false
BackgroundTheme=/usr/share/apps/kicker/wallpapers/default.png
ColorizeBackground=false
CustomSize=38
ExpandSize=true
FadeOutAppletHandles=true
HideAnimation=true
HideAnimationSpeed=40
HideAppletHandles=false
HideButtonSize=14
Position=3
ShowLeftHideButton=false
ShowRightHideButton=false
ShowToolTips=false
Size=4
SizePercentage=100
TintColor=199,199,199
TintValue=0
Transparent=false
UnhideLocation=6
UseBackgroundTheme=true
XineramaScreen=0

The easiest way to edit it with at script, will be to overwrite the whole file.

something like:

cat modified.file > original.file

---

