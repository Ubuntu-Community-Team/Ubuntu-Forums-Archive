---
title: "[SOLVED] Fluxbox question - where is my terminal?"
date: 2007-12-07
forum: Desktop Environments
---

### Post by apothecaryaaron on 2007-12-07
I know that there are guides in this forum about getting a Fluxbox menu, but I seem to have a more pressing issue.  My Alt keys to get a terminal open seem to switch workspaces instead.  With no menu and no terminal I can't accomplish much.  I did enjoy a challenging game of "Spot the 5 differences" by switching workspaces over an hour's time.  Never found the 5th one though...:)

 I'm sure there's a key combination to open a teminal, but there are so many Ctrl, Alt, Super, Shift, FKey combos that I don't know where to start.  Any Ideas?

Thanks in advance for the help.

---

### Post by mali2297 on 2007-12-07
Try Ctrl-Alt-F1, that should get you to a virtual terminal. (Ctrl-Alt-F7 to get back to Fluxbox.)

---

### Post by apothecaryaaron on 2007-12-07
> **mali2297 said:**
> Try Ctrl-Alt-F1, that should get you to a virtual terminal. (Ctrl-Alt-F7 to get back to Fluxbox.)

Thanks for the fast response.  

When I use Ctrl-Alt-F1 (or F2 or F3 or F4) I get a black screen with a flashing cursor in the upper left corner.  Ctrl-Alt-F7 does get me back into Fluxbox.  

It is possible that I didn't install Fluxbox correctly.  I started with Ubuntu, did a search for Fluxbox in Synaptic, and installed anything that it recommended.  I'm changing sessions at the login screen to get to Fluxbox.  Is there maybe a package I should have gotten that wasn't automatically gotten in Synaptic?

---

### Post by mali2297 on 2007-12-07
> **apothecaryaaron said:**
> Thanks for the fast response.  

When I use Ctrl-Alt-F1 (or F2 or F3 or F4) I get a black screen with a flashing cursor in the upper left corner.  Ctrl-Alt-F7 does get me back into Fluxbox.  

See here:
[http://ubuntuforums.org/showthread.php?t=585454](http://ubuntuforums.org/showthread.php?t=585454)

> 
It is possible that I didn't install Fluxbox correctly.  I started with Ubuntu, did a search for Fluxbox in Synaptic, and installed anything that it recommended.  I'm changing sessions at the login screen to get to Fluxbox.  Is there maybe a package I should have gotten that wasn't automatically gotten in Synaptic?
I think it is installed correctly. Perhaps you should login to your regular desktop environment and configure the Fluxbox menu etc from there, then change sessions.

Personally, I quickly decided that Fluxbox needed too much work. I settled with Xfce instead.

---

### Post by RedSquirrel on 2007-12-07
> **apothecaryaaron said:**
> I'm sure there's a key combination to open a teminal, but there are so many Ctrl, Alt, Super, Shift, FKey combos that I don't know where to start.  Any Ideas?

There is no key combination to start a terminal by default. You can add one. The file is ~/.fluxbox/keys.

A line similar to the following will work, but you can adapt it to your needs:

```
Control Mod1 x :Exec xterm
```

Then you will just press Ctrl-Alt-x to start xterm.

See the link in my signature if you still don't have a menu.

If your virtual consoles are blank, that is very likely the framebuffer issue mentioned above.

---

### Post by apothecaryaaron on 2007-12-07
> **mali2297 said:**
> See here:
[http://ubuntuforums.org/showthread.php?t=585454](http://ubuntuforums.org/showthread.php?t=585454)

 Perhaps you should login to your regular desktop environment and configure the Fluxbox menu etc from there, then change sessions.

Personally, I quickly decided that Fluxbox needed too much work. I settled with Xfce instead.

Thanks, I will try that out as soon as I get a break at work.  I actually am trying Fluxbox specifically because of the work involved.  Seems like a good learning experience for a Linux n00b.  

> **RedSquirrel said:**
> There is no key combination to start a terminal by default. You can add one. The file is ~/.fluxbox/keys.

A line similar to the following will work, but you can adapt it to your needs:

```
Control Mod1 x :Exec xterm
```

Then you will just press Ctrl-Alt-x to start xterm.

See the link in my signature if you still don't have a menu.

If your virtual consoles are blank, that is very likely the framebuffer issue mentioned above.

Ahhh.  Thanks for the hint about the keys.  And the link in your signature would be the one I have seen around that I planned on finding.


Thanks to both of you for the quick and informative responses.  I do believe I have a starting point for playing with Fluxbox now.

---

