---
title: "What the heck is this?"
date: 2009-05-20
forum: Desktop Environments
---

### Post by ecksit33 on 2009-05-20
It does this all the time. I don't know what to call it, so I just made a video --> [http://www.youtube.com/watch?v=3J8zgJin5PY](http://www.youtube.com/watch?v=3J8zgJin5PY)

The video descrip explains it so I don't have to type it all again.
> Been running Linux for about a month now. This is the only real problem I've ran into so far. Recently, at random moments, all open windows on screen will instantly be transported to an unreachable space. In this video, it was when I was uploading a video to my channel, and it threw firefox into some unknown space. While firefox was still open and running, the window was completely inaccessible. I tried minimizing, maximizing, throwing to another desktop, etc. The only way I can fix this problem is to close quit the process, or restart my computer. Any help, ideas, or even an explanation would mean the world to me.

---

### Post by khelben1979 on 2009-05-20
I haven't been able to watch the video, yet, but I have a question: does your problem occur with both Gnome and KDE?

---

### Post by ecksit33 on 2009-05-20
Like I said, I've only been running Linux for about a month, so I'm not sure what the difference is. Sorry. :(

---

### Post by zeex on 2009-05-20
> **ecksit33 said:**
> It does this all the time. I don't know what to call it, so I just made a video --> [http://www.youtube.com/watch?v=3J8zgJin5PY](http://www.youtube.com/watch?v=3J8zgJin5PY)

The video descrip explains it so I don't have to type it all again.
Any help, ideas, or even an explanation would mean the world to me.

Hi, 

Seems like some problem with Compiz. I had something similar problem once. i had no idea what to do so i removed compiz completely ( all the configuration ) and did a fresh compiz install. It worked. It's not a sure solution but you could try. I think it has something to do with plugin settings. seems like you 've messed up plugin settings somehow. It happens when compiz gives the warning of conflict in key bindings. 

May be removing and reinstalling solve the problem. Won't take long.

Good luck :)

---

### Post by khelben1979 on 2009-05-20
> **ecksit33 said:**
> Like I said, I've only been running Linux for about a month, so I'm not sure what the difference is. Sorry. :(

Okay, then check out this 2 wiki links: [Gnome]("http://en.wikipedia.org/wiki/Gnome") or [KDE]("http://en.wikipedia.org/wiki/Kde").

```
sudo apt-get install kde
```
installs the KDE enviroment if it isn't already installed.

---

### Post by coffeecat on 2009-05-20
I agree that this looks like a compiz problem. You've got a lot of effects there - perhaps a couple are conflicting. Before you uninstall and reinstall compiz, try this. Go to System > Preferences > Appearance > Visual Effects Tab. Tick the 'none' box to switch compiz off.

Are you now able to use the desktop normally? If so, tick the 'Normal' box to re-enable a minimal set of compiz effects. Are you still able to use the desktop? If so, now go into CompizConfig Settings Manager and enable the effects you want, but go cautiously. Don't do too many at once. :)

By the way, that's the gnome desktop you've got.

---

### Post by ckonestroh on 2009-05-20
Go into Preferneces > Compiz disable all the window management options...

Check this Youtube video out...

[http://www.youtube.com/watch?v=2xrF000XvFs&feature=channel]("http://www.youtube.com/watch?v=2xrF000XvFs&feature=channel")

Good Luck


Personally I would watch most of this users Gotbletu videos to get to now some of the linux programs and options in linux......

---

