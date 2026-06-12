---
title: "Icon adjusting"
date: 2007-07-18
forum: Desktop Environments
---

### Post by Belgatom on 2007-07-18
[Desktop]("http://users.telenet.be/belgatom/ubuntu/desktopU.png")

If you have a look at my Desktop, you will see that I use icons for my most used applications that are quite self explanatory. But what I wanted was that the name of the shortcut doesn't appear under the icon. I have currently done this by removing the name of the launcher and replacing it with spaces. Unfortunately this didn't work with the VLC icon. I wouldn't accept spaces as a replacement. I replaced it with a full stop but that gives me one white pixel just under the Music Icon. 

Two questions:

1 Is there anywhere I can change the settings as to force the system to not show the name of the launcher under the icon? 

2 And while I am at it - can I also change the behaviour of a launcher so it reacts to a single click in stead of a double-click?

---

### Post by kyphi on 2007-07-18
For the labels:

Try System -> Preferences -> Menus and Toolbars -> Toolbar Button Labels.

For the Single or Double click:

Applications -> System Tools -> Configuration Editor -> Apps -> Nautilus -> Preferences, then scroll to click_policy.  Right click on that and edit the key.

---

### Post by Belgatom on 2007-07-19
> **kyphi said:**
> For the labels:

Try System -> Preferences -> Menus and Toolbars -> Toolbar Button Labels.

This ididn't do the trick. I think this is limited to the Toolbars and not the desktop. 

> **kyphi said:**
> 
For the Single or Double click:

Applications -> System Tools -> Configuration Editor -> Apps -> Nautilus -> Preferences, then scroll to click_policy.  Right click on that and edit the key.
This did work but it made the single click a system wide policy. 

Thanx for looking but I'm still looking for a solution.

---

### Post by kyphi on 2007-07-20
1.  Quite right, it only applies to the Toolbars.

When renaming an icon, using the spacebar has always done the trick and removed the text under the icon.
I have tried it with the VLC icon (the one that looks like a witch's hat) and it works.  You are using special icons so I cannot help you with those.

You mentioned that you had tried to replace the text with spaces.  I do it differently, when using 'Rename' the text becomes highlighted and I then press the spacebar once.  Is this technique different to what you have been doing?

2.  Changing double click to single click has s a system-wide effect indeed.  There is no way to make that policy specific to selected applications that I know of.

---

