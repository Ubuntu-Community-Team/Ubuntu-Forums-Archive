---
title: "[ubuntu tweak] &quot;Fix the appearance of themes when granted root privileges&quot; failure"
date: 2012-07-17
forum: Desktop Environments
---

### Post by blinksilver on 2012-07-17
So I did some mild theming to my desktop and thought I could use the above ubuntu-tweak setting as a shortcut to apply my theme system wide. 

Turns out there is a bug in that setting:  [https://bugs.launchpad.net/ubuntu-tweak/+bug/1016116](https://bugs.launchpad.net/ubuntu-tweak/+bug/1016116)

That stops it from completing. This left my system in a rather strange quasi themed state. I went about wiping all my user settings, all the setting in the lightdm user, and all the settings in the root user account, in an effort to revert the the half enabled effects. I think I've got everything back to normal. Expect for one edge case. When I autologin my user account(Plymouth directly to unity, not regularly logging in with my password for lightDM) the theming in all my apps are borked. Appmenu shows in the app window itself and in the unity menu, all the menus have icons, firefox/thunderbird is not themed and a few others.

Where does the autologin process take place how to I revert all its settings to default?

---

