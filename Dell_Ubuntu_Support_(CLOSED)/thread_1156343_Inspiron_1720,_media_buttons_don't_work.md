---
title: "Inspiron 1720, media buttons don't work"
date: 2009-05-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jda1701 on 2009-05-11
Greetings all,

I have a Dell Inspiron 1720 laptop.  I previously had Intrepid 64-bit installed and it worked great.  Jaunty fixed a few things (backlight dimming) but also broke a few things as well.

Particularly, the media buttons along the front bezel no longer control Rhythmbox or Totem like they did under Interpid.  Volume Up and Volume Down still work, but Mute does not.

I looked in System > Preference > Keyboard shortcuts and all the Sound shortcuts are correctly mapped.  Clicking on each XF86- mapped key binding will tell me to enter a new shortcut, at which point I press the corresponding button, and the mapping goes back to the same XF86- label it had before.

So, I don't think xorg is at fault, it correctly mapped the keyboard shortcuts.  But I'm at a loss as to how to check to make sure those keyboard events are getting to the proper applications (in most cases rhythmbox and totem for media controls, and gnome itself? for volume controls and mute).

Has anyone else had this issue with a similar Dell laptop or knows some further steps I can take to troubleshoot this issue?

I've not yet filed a bug in launchpad as I wanted to see if an easy fix presents itself.

Thanks

---

### Post by coffeeaddict22 on 2009-05-11
hi,
I'm not completely up to speed on this, but have found (the hard way) that things are in the process of being altered.  xorg.conf used to be the home for input settings; they've all moved now to HAL, and you're probably needing to make/change an fdi file.  Have a look at [https://wiki.ubuntu.com/X/Config/Input]("https://wiki.ubuntu.com/X/Config/Input")

---

### Post by jda1701 on 2009-05-11
Thanks coffeeaddict,

Unfortunately I can't really be certain whether or not, with the link you provided me, its an X.org issue.  I am able to manually set the keymappings using gnome-keybindings and it shows the correct keyboard code, XF86PlayPause, XF86FastForward, etc. So I believe X.org is properly detecting the keys, but somewhere between that and the applications the key presses are just "getting lost".  

I believe several models of Dell keyboards use the same keyboard and media buttons. I'm hoping others have either had this issue.

To give some more information, the keybindings worked in Intrepid, and worked after upgrading to Jaunty Alpha 4.  After I did a fresh install of Jaunty, the keybindings no longer worked.

---

### Post by jda1701 on 2009-05-27
Apparently enabling the "Show position of pointer when Control key is pressed" disabled my media keys, as well as disabling the ability to ctrl+mousewheel zoom in Firefox.  

This issue has been fixed.  Woot! :)

---

