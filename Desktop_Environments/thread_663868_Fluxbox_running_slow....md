---
title: "Fluxbox running slow..."
date: 2008-01-10
forum: Desktop Environments
---

### Post by mister_pink on 2008-01-10
But not in the normal way. Boot time is fine, programs even start relatively quickly. The problem is that whenever I type anything it takes an absolute age for anything to come up. I'm back in gnome because when I tried to type this in fluxbox it was just silly. I press all the keys and the letters appear, one by one, over the next minute or so for a few words. 

It's probably very relevant that this isn't the first time I've seen this - I got the same result when I wanted to try out KDE a while ago. That time typing was slow as was the drawing of the menus (first you'd get an outline, followed by the menu items appearing one by one).

I hope someone can help me! It's not really the end of the world, gnome works just fine, but it is a bit annoying! 

Cheers

---

### Post by Nomen Luni on 2008-01-10
Are you running gnome settings daemon in fluxbox at start? Check the Apps text file in the .fluxbox folder. I had a similar problem once and it stopped when I added the following line in Apps

[startup]    {gnome-settings-daemon}

You can add gnome volume manager with this:

[startup]    {gnome-volume-manager}

Might help, but maybe not. Sounds like its a problem with X. Or the font server being flooded with queries

---

### Post by mister_pink on 2008-01-10
That didn't seem to fix it but it's given another clue - things are fine when I type in xterm, so your font suggestion seems to be a pretty good call. I'll try and do some more investigation tomorrow. I'll see if I can get a script to log cpu usage.

---

### Post by TeaSwigger on 2008-01-10
Both Fluxbox and KDE are lightening fast for me in those respects, and I have no idea why those would have problems while Gnome would work fine. Doesn't help I don't use Gnome...

Are you confident of the graphics (driver etc)? If you type glxgears in a terminal, does the resulting gear graphics move smoothly? I don't suppose there is a proprietary graphics driver being used in Gnome but somehow not in other environments? If not, that's a puzzle to me too. Good luck.

---

### Post by cknight on 2008-01-11
Perhaps try commenting out anything you've added to your ~/.fluxbox/startup file?  Obviously, don't comment out the fluxbox executable!  My guess is that fluxbox is starting something on startup which is causing this problem.  The only other guess I have is to check your keys file?  Perhaps you have some strange key bindings which are launching background processes as you type?  Good luck!

---

### Post by Nomen Luni on 2008-01-11
> **mister_pink said:**
> That didn't seem to fix it but it's given another clue - things are fine when I type in xterm, so your font suggestion seems to be a pretty good call. I'll try and do some more investigation tomorrow. I'll see if I can get a script to log cpu usage.

cool. My bet is font server problem. If I get some time, I'll look into it more - I fixed it last time I just can't remember how I did it :)

---

