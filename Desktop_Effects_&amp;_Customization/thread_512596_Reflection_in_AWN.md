---
title: "Reflection in AWN"
date: 2007-07-29
forum: Desktop Effects &amp; Customization
---

### Post by What The Deuce on 2007-07-29
I am trying to get the reflection working in AWN, but I am completely unsuccessful at patching it.

I am working right now with SVN 240.  Maybe i am getting the wrong file to patch, or i am just an idiot.  I am using [this threads]("http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=463&page=1&isLive=true") instructions from over on the AWN forums and I get hunk errors and i am clueless.

Has anyone gotten this to work and maybe give me some ideas?

Also, where did you get the patch, i am using [this patch server]("http://patch-manager.dskw.de/") to get the patch (AWN new hover effects).

---

### Post by andrewsomething on 2007-07-29
The bad news is that the hover effects patch requires rev227. It's very experimental still and was basically just made to show some new ideas. 

The good news is that you don't need it to get reflection. Reflection has been committed to the core code. It's just not accessable through the GUI yet.

Follow the installation instructions here: [http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

After installing the deb or compiling from source, run AWN. Then open up gConfig. Go to apps>avant-window-navigator>bar. Change the settings for bar_angle to 45 and the setting for icon_offset to 15. Restart AWN. You should have the new look.

---

