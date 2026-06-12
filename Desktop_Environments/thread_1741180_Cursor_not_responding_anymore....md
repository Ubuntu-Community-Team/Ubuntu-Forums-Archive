---
title: "Cursor not responding anymore..."
date: 2011-04-27
forum: Desktop Environments
---

### Post by onimal on 2011-04-27
The way it happened is: I have dual monitors, and I was running Minecraft in a window on the external screen and I accidentally pressed F11, which made the game appear on both screens at once (I have dual monitors), one with the mouse and one without, when I pressed F11 again both screens flickered but nothing changed. I could move the mouse to close the window but it didn't respond, so I restarted, and now the cursor is stuck against the left side of the screen and doesn't respond to the touchpad (unfortunately I don't have a USB mouse to try out)

It's a Samsung R580 laptop running Ubuntu 10.10, with an ATI HD545V graphics card.

Any help at all would be much appreciated, just recently installed Ubuntu for the first time and would really like to get to back to using it. Feel free to patronize me, I won't get offended. ;)

---

### Post by onimal on 2011-04-28
No worries, I googled around a bit more (as I probably should have done before panicking and running for help, apologies) and I found I could get into the terminal from the keyboard and run this command 

gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true

Which worked like a dream.

---

