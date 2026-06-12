---
title: "Compiz with 2 x-screen sessions"
date: 2009-10-24
forum: Desktop Environments
---

### Post by lordofduct on 2009-10-24
first off I'm not 100% sure this is the sub-forum this should be in. But because compiz is about the desktop and the sort... I figured this was the closest.

Please move if I was wrong.


So I have been using 2 monitors for some time. I prefer setting it as 2 separate x-screens. No Twinview, No Xinerama... just two unique x-screens that can't have windows swapped back and forth. I just prefer the functionality (I can swap virtual desktops individually on each).

Now I've only recently started using Compiz-Fusion for advanced stuff. Most specifically, the rotating cube thing. But when I use these advanced features of compiz my second monitor freezes up. Sometimes it goes blank, sometimes it shows what's there but the screen doesn't update... nothing. Stuff is still going on, if I click and drag stuff and then turn off compiz you'll see that things have moved and words were typed... just while it's running screen 2 doesn't update the display.


Now what I want to do is set compiz to ONLY run on display 1 (DISPLAY=:0.0) and no special effects on display 2. Display 2 merely exists as a place where I leave Pidgin, skype, Email, and Rhythmbox so I can get to it easily and see updates in the corner of my eye. I can continue working and chat at the same time. So I don't need the special effects over on that screen.

So if anyone can point me in the right direction for turning compiz on for 1 screen only, please do. The only results google has given me is adding some line to /usr/bin/compiz at the end which basically says to change the last line to set display to only current display. But that's kind of arbitrary and depends on the screen I'm on (if I understand it right)... isn't there a way to say it but designate a specific display? Furthermore it didn't work for me.

---

