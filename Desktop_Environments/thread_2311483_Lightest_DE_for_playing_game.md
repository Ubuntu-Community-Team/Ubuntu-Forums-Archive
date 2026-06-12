---
title: "Lightest DE for playing game?"
date: 2016-01-27
forum: Desktop Environments
---

### Post by TBK on 2016-01-27
I'm using Ub&#7909;ntu 15.10 and I have 1 GB ram, so I need a lightest DE for playing games (not xfce, mate, lxde,...), I see that seem openbox is popular, should I use it?
Give me some advices!

---

### Post by Dreamer Fithp Apprentice on 2016-01-27
The lightest DE is no DE, no window manager even, just plain X. AFAIK, and I'd welcome alternative views because I've only gotten interested in this recently myself, not for games but for purposes very similar where I want to run a gui application with the least possible demand on system resources, the best way is to create an additional user account dedicated to whatever the game (or other gui program) you want to run that way.

Then you get another tty with cntrl-alt-F3 (or whatever number is free, probably anything from 2 to 6 will do) and log in as the new user. Then type this:```
echo "exec command-to-start-program" > ~/.xinitrc
``` and press enter. Now type```
startx
``` and click enter. Your program should start.

That's as far as I've gone with this so far (like I said - this is a subject of recent interest to me & I'm still working on it) but I think you could switch back to the "regular" DE with cntrl-alt-F7 and log out there to reduce resource usage. I haven't tried killing x there yet, but there probably is a way to do it without killing x in the other user's environment, since it is a separate x. Better still you could uninstall the "display manager" (lightdm in my case) and start your graphical environment for either your regular user or your game user with "startx" after logging in with either.

That would be the lowest load setup I know of. There is one drawback to that. Xscreensaver can be set up to lock the screen very securely if you use a display manager but not if you start x with startx. There is probably a way around this, but I haven't looked for it yet.

I'd be very interested to know how this works out for you, as I am working on something similar.

======================
But I should answer your question literally as asked, also:

The lightest DE amoung the standard 'buntus is Lubuntu

Lighter still is plain Openbox. Not just as a window manager. As the DE as well, unless you want to get pedantic about whether it can be called a DE.  That's what I use for my "regular" system.

There are WMs lighter still:
[ATTACH=CONFIG]266990[/ATTACH]
Most, maybe all, of these are in the repo. If you go that route, you can select alternative "session types" with the graphical screen where you login with the display manager if you elect to keep it. And if you do, I'd be interested in your experiences with that also. I've played around with some of those and intend to do so more in the future.

There is probably some way to make the display manager optional after starting the system, but I haven't pursued that yet.

P.S. You can still lock the screen with xscreensaver without a DM, it is just that without a DM you can't stop someone from getting another tty with cntrl-alt-Fn, n being an integer, 1-6. If they find you are logged in on another tty, they could then kill xscreensaver and get around your screenlock. My CAT, yes, I mean the furry kind, felis domesticus I believe they are called, switched my computer to another tty this morning, I shine you not. Fortunately he didn't know how to log in. If you are careful to only leave the machine logged in on one tty at a time, I THINK this is not a security problem unless you use very short login name and password that a cat could type or a bad guy could brute force. But I haven't really studied the issue yet. As before, knowledgeable comments re this would be appreciated.

---

