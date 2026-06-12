---
title: "Solution for Gutsy with Xgl/Compiz &amp; fglrx/games/videos simultaneously"
date: 2007-10-22
forum: Desktop Environments
---

### Post by kst- on 2007-10-22
Hello everyone,

I'm trying to get both Compiz and Games running on Gutsy at the same time with decent performance on an ATI Radeon Mobility x700 with proprietary fglrx drivers, without having to restart/re-login/shutdown anything. This solution could be interesting for other purposes/systems aswell tho.
Basically I got like 2 ideas how to do this:

**Solution 1:** 
- Define gfx card/monitor _twice_ in xorg.conf and create _2_ layouts
- Start 1 gnome session with serverlayout0 and 1 gnome session with serverlayout1 on a _different_ virtual X..

(forgive my bad use of terms, I only started to use linux like 1 month ago).. so I can switch with ctrl-alt-f7/f8/f9 through the sessions without closing and losing any open apps. But I don't know whether this is even possible, can anyone give some input on this? How do I put one layout on tty7 and the other on tty8/9?


**Solution 2:** 
- Use **gdmflexiserver** to start a 2nd session without Xgl when needed (I don't game every time I boot my notebook, and not all day long)
- Make it use _metacity_ and just use it without desktop effects

This already works with this dirty workaround (.config/../disable) to get rid of Xgl.. apparently there have been major changes to this since gutsy? Can someone explain how it works and how you can disable Xgl without using the file $HOME/.config/xserver-xgl/disable or removing the xserver-xgl package?

**So far I can do it like this:**
- Login to gnome session with Xgl installed/enabled
- Alt-F2 -> gdmflexiserver -l (doesnt lock current session) and select a new session in the popup
- Ctrl-Alt-F2 -> login -> create/rename file to $HOME/.config/xserver-xgl/disable to turn off Xgl
- Ctrl-Alt-F9 (thats where the new virtual session is) and login as usual with my normal username
- Use Ctrl-Alt-F7 and Ctrl-Alt-F9 to switch between Xgl/Compiz and Xorg/Games session

This seems to do the trick, I haven't tested performance/abilities much but I guess it will be fine with something like this.. but: How do I automate this (always create both sessions automatically with their window managers/decorators), and what about the disabling of Xgl? The way I do it right now, I'll have to remove the xserver-xgl/disable file again to get a new Xgl/Compiz session (e.g. when I reboot)..?

Help would be much appreciated :) or are there already some good solutions to this? All I need is Compiz and at the same time decent performance by fglrx for games (Xgl can't do that) without losing apps to a reboot/logout! :)

---

### Post by Jadd on 2008-01-08
Thanks for sharing.

---

### Post by Jouke74 on 2008-01-08
You can start a second X-server for the game only, similar to your option 1. It is posted some time ago on this forum, but with search it takes forever to find. Unfortunately I have saved this text only as a PDF document and for some peculiar reason I cannot copy & paste the text from here. It's shows gibberish. For now I made a screen image (JPG) of this PDF file.

See: [[img=http://img156.imageshack.us/img156/7932/2ndxserverpf7.th.jpg]](http://img156.imageshack.us/my.php?image=2ndxserverpf7.jpg)

Hope it works, I have not tried this, also because of lack of time... (I am a busy guy :lolflag:)

---

