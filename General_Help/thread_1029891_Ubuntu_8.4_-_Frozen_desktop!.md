---
title: "Ubuntu 8.4 - Frozen desktop!"
date: 2009-01-03
forum: General Help
---

### Post by cayenne on 2009-01-03
Hi!
I just upgraded to Ubuntu 8.4, and i had a problem with the sound with Flash (youtube.com etc.) because of this i tried the following commands:

1. sudo apt-get install alsa-oss
2. sudo gedit /firefox/firefoxrc.
3. Changed the line FIREFOX_DSP = "none" to "aoss"
4. put the line: ln -s /tmp/.esd-1000/tmp/.esd into System - Preferences - Sessions - Startup programs
5. then restart

But after restarting my PC, my desktop was frozen, the mouse and keyboard was working, but there was no response when i tried to press the firefox, terminal, pidging buttons etc.
I have tried this:
from terminal: Ctrl + Alt + F1, "killall gnome-panel", Ctrl + Alt + backspace. 
But no response, just the same when I am back to the desktop after rebooting.
Please help me!

ps! I got NVIDIA Go 7400 Graphics

---

### Post by Tim Sharitt on 2009-01-03
I suspect that the line you've added to Startup programs may be the problem. Look in ~/.config/autostart, there shold be a file there which lauches that command. It will be named whatever you named it when you created the launcher.

---

### Post by cayenne on 2009-01-04
Hi!
I have now located the "~/.config/autostart", but there is no such file in there, i remember i called the launcher "firefox-flash", but i cant find it nowhere. any other suggestions to this problem?

---

