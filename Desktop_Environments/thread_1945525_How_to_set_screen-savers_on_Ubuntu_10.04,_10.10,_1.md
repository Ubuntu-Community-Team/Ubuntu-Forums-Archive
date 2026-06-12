---
title: "How to set screen-savers on Ubuntu 10.04, 10.10, 11.04 and 11.10"
date: 2012-03-23
forum: Desktop Environments
---

### Post by ankushub on 2012-03-23
Hi Friends,

Recently in my company a new project came which requires users to use Linux as a Desktop and Ubuntu has been preferred as some of the users where already using Ubuntu. 

Most of the things are set except we need to enable customized screen saver(yet to create a customized screen saver) on different Ubuntu versions.

Some of the users are using Unity (11.04,11.10) and some are using Gnome (2/3) and KDE.

We would like to push this screen saver in a script through Puppet(already running in the company).

So what is the correct way to configure screen saver with customized settings.

Searching on the Internet and Forums and I came across the below commands to activate the screen savers for the users. But when I run these commands the user settings for screen saver remains the same

gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.mandatory --type int  --set /apps/gnome-screensaver/idle_delay 4
 gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.mandatory --type boolean --set /apps/gnome-screensaver/lock_enabled true
 gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.mandatory --type boolean  --set /apps/gnome-screensaver/idle_activation_enabled true
 gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --set --type list --list-type=string /apps/gnome-screensaver/themes [blank-only]



Output of gconftool-2 -R /apps/gnome-screensaver


gconftool-2 -R /apps/gnome-screensaver
 lock_delay = 0
 themes = [screensavers-personal-slideshow,screensavers-hypertorus,screensavers-gltext,screensavers-glslideshow,screensavers-glschool,screensavers-glmatrix,screensavers-glcells,screensavers-glblur,screensavers-fuzzyflakes,screensavers-ubuntu_theme,screensavers-footlogo-floaters,screensavers-fiberlamp,screensavers-cosmos-slideshow,screensavers-antspotlight]
 logout_command = 
 theme = screensavers-ubuntu_theme
 power_management_delay = 30
 logout_enabled = false
 embedded_keyboard_enabled = true
 embedded_keyboard_command = /usr/bin/cellwriter --xid --keyboard-only
 logout_delay = 120
 idle_delay = 3
 user_switch_enabled = true
 lock_dialog_theme = default
 mode = random
 status_message_enabled = true
 cycle_delay = 10
 idle_activation_enabled = true
 lock_enabled = true

Whereas the User settings for ScreenSaver -> Regard the Computer as idle after 5 minutes and the Theme is "Random".

Please let me know what is the correct way to set the things so that those are persistent across reboots.


Regards

Ankush

---

