---
title: "Fast, easy, and fancy desktop setup recommendations ?"
date: 2008-12-25
forum: Desktop Environments
---

### Post by albinootje on 2008-12-25
I'm using FreeNX remote desktop server on a remote machine.

For the new users (some of them will be completely new to Linux!) on that FreeNX server, who will basically only be editing documents in a word-processor and moving or renaming files around, I'd like to have a fast, easy and still good looking desktop for those users which does the following :

1) Good and fast file-manager which supports drag and drop, and is preferably theme-able/skin-able.
2) Simple and fast window-manager which has menus which are working automatically when applications are added, or are easy to rebuild.
(From years ago I remember using Windowmaker myself, but the menu was a static one, and had much more links to applications than there were actually installed, not so handy in this case).
3) Desktop configuration files for new users must be coming from /etc/skel so that I don't have to edit those manually.
4) A panel which is very simple but at the same time good looking.
5) Support for easily changing the wallpaper for the users.
6) A session which can easily do without using HAL and dbus.
7) Preferably not a resource hungry setup, although I'd like to add more RAM as soon as I get the chance.
8) Good use of color brightness and contrast, because by default the color-depth of FreeNX is lower than the default.

What would you recommend ?
TIA!

---

### Post by jim_mule on 2008-12-25
1. pcmanfm or thunar, both gtk based. pcmanfm can draw your desktop too.

2. openbox.

3. im not sure.

4. pypanel, fbpanel, i tried a few and never really could settle on one, went back to xfpanel. 

5. pcmanfm keeps is it under edit > preferences > something from what i recall, its not tough and the project seemd to update frequently, so maybe they have it on desktop right-click by now.

6. i dont think pcmanfm requires hal/dbus i know it didnt automount like thunar does. besides that i am not sure if i understand what a session might require from hal/dbus.
s.

7. i set up pcmanfm + openbox + pypanel on a pII with 128mb ram, it was sufficiently quick, add a light browser, midori or kazakahzee [if forget its name]. should be ok.


8. choose a high contrast gtk theme, theres quite a few out there, look thru [http://xfce-look.org](http://xfce-look.org) to get an idea.

---

### Post by albinootje on 2008-12-25
Thanks a lot! :)

---

