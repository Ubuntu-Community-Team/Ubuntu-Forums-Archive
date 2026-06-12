---
title: "Strange WoW / Keyboard problem"
date: 2006-07-10
forum: Gaming &amp; Leisure
---

### Post by craigi on 2006-07-10
Hey everyone,

I have WoW running pretty good with Cedega, but I am having one minor issue.  

When I tab out of the game, or I bring a different window into focus, I sometimes lose keyboard functionality in WoW.  Nothing I type shows up in the screen except special characters ; any letter I type does not work.  If I quit the game and relaunch it, everything is fine until I bring up another window.

It doesn't happen all the time, but enough to be annoying.  I have the desktop setting in Cedega set to 1280x1024 (as well as in game) and I have DXGrab unselected so that I can move my mouse outside of the game window.  

Has anyone else had this problem or may know how to fix it?  Using the latest version of everything.  If I can provide attional details, please let me know.

Ubuntu 6.06.  Wow 1.11.  Cedega 5.21.  Microsoft Natural keyboard.  nVidia 6800.

EDITED TO ADD:  One thing I just noticed.   I just had the problem while I was typing this forum post.  I went back into the game and I can't type anything.  However, I can still use the number keys to select spells.  The weird thing is that everything has been shifted up one.  Meaning, if I press '1", it's casing the spell on my second row of buttons, not the first row.  Same thing happens for all other numbers.  

Another weird thing is that I can bring another window into focus a few times and the problem seems to correct itself.

---

### Post by Rhose on 2006-07-10
Any chance this is the same issue discussed in the "WORKSPACE SWITCHING" section of the [World of Warcraft with Wine]("http://www.ubuntuforums.org/showthread.php?t=120615") thread?

> WORKSPACE SWITCHING

Ok, I like to use the workspace switching feature in Gnome (also found in every other window manager I am aware of) when playing WoW, to check Thottbot, reply to a IM, particularly on those long griffon/bat flights. I have set shortcut keys to switch to each workspace under System > Preferences > Keyboard Shortcuts, mine are set to CTRL-F1 through F4. If you do this after starting WoW from wine in a terminal, it will switch out, but when you switch back, keyboard input is routed to the terminal instead of the game, so you can no longer use the ingame chat among other things. To fix this, I use a custom panel button to start the game instead. To make this panel button:

1. Right click on the panel you want to add it to (such as the one containing the Applications drop down) and select "Add to Panel..."
2. Highlight "Custom Application Launcher" and click "Add"
3. Give it a "Name" (such as "WoW Wine")
4. Under "Command" type "wine /path/to/World of Warcraft/WoW.exe -opengl"
5. Do not select "Run in terminal"

---

### Post by craigi on 2006-07-10
Wow, I can't believe that was sitting there right under my nose.   Thanks for pointing that out and sorry for this post. :(

Although I am not using Wine, but I'll see if this helps.

---

