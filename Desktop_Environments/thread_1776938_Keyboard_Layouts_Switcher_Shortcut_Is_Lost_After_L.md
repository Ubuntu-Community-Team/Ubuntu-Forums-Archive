---
title: "Keyboard Layouts Switcher Shortcut Is Lost After Logging Out"
date: 2011-06-07
forum: Desktop Environments
---

### Post by vvd416 on 2011-06-07
I have two keyboard layouts with the Left Win key set as a shortcut to switch between them. After I log off and on, the shortcut becomes disabled, and I have to go to Keyboard Layouts Plugin again. 

If I right click the plugin icon, I see that the layout option is correct - it's Left Win. After I click Close the shortcut is enabled until the next logon.

The system is Xubuntu 10.04, upgraded from 9.10.

I found a relevant bug record here
[https://bugs.launchpad.net/ubuntu/+source/xfce4-xkb-plugin/+bug/548631](https://bugs.launchpad.net/ubuntu/+source/xfce4-xkb-plugin/+bug/548631)
It seems that I hit the similar problem, but in the history I see neither real workarounds, nor resolution.

Here is my ~/.config/xfce4/panel/xkb-plugin-12419716390.rc file

display_type=0
group_policy=2
default_group=0
never_modify_config=false
model=pc105
layouts=us,ru
variants=,
toggle_option=grp:lwin_toggle
compose_key_position=

---

