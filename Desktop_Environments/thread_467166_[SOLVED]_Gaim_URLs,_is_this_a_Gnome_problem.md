---
title: "[SOLVED] Gaim URLs, is this a Gnome problem?"
date: 2007-06-07
forum: Desktop Environments
---

### Post by bobpaul on 2007-06-07
From what I recall, GAIM has never opened URLs in my browser all the way back to Breezy. Now on Fiesty I just upgraded to PidginIM and the problem persists: nothing happens when I click a URL, nor if I chose "Open link in Browser." I'm forced to copy the link and past it in Firefox.

I've tried deleting the ~/.gaim folder and allowing gaim to create new preferences to no avail. Might there be something screwed up my my GNOME settings? Links from other programs, such as ThunderBird, but not from GAIM/Pidgin (or gnome-terminal, I just noticed.)

---

### Post by brt on 2007-06-29
This is how i was able to fix it:

[LIST][*]fire up (<alt><f2>) **gconf-editor**[/LIST]
[LIST][*]look for / Desktop / Gnome / url-handlers / http[/LIST]
[LIST][*]check if the key **command** represents the **correct path to your browser**[/LIST]

in my case it was */usr/bin/swiftfox "%s"*  i checked it by pasting it to a terminal and noticed that it was incorrect, after some struggling i found out that if i type in the terminal */usr/bin/swiftfox_start [http://ubuntu.com](http://ubuntu.com)* the browser starts, so i changed the value of command to */usr/bin/swiftfox_start "%s"* and voila it works :)

so you have just to put in the correct path to your browser, eg. if you are using firefox it may be **/usr/bin/firefox "%s"**. just test the command with a URL in a terminal to check if it starts your browser, and maybe this will help you out too...

---

