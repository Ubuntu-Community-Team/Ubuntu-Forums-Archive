---
title: "A couple Return to Castle Wolfenstein related questions"
date: 2005-07-18
forum: Gaming &amp; Leisure
---

### Post by deathfalls on 2005-07-18
Hey guys, I'm fairly new to Linux... trying to learn a bit. Just installed Hoary tonight and thought I'd try to get RtCW working. The first problem I encountered was it seemed to hang at a black screen, I could move the cursor and see some of the desktop. After doing some searching, it seemed that it could be a sound problem. I followed the instructions in [this](http://www.ubuntuforums.org/showthread.php?t=44753&highlight=happy+ALSA) thread, and I was able to get to the main menu in the game.

This is where another problem popped up, apparently the game was trying to write a config file, and it didn't have permission, so it wouldn't load a map. I was able to solve that by doing "sudo wolfsp".

So, here's my questions:

Is there a better way to solve the sound issue? So that I could hear system sounds, etc? I haven't tried using XMMS or anything else yet, so I don't know how what I did will affect that.

Also, is it normal that I would have to run the game with sudo? Just thought I would ask, as I never saw that mentioned anywhere when I was searching for information on installing the game.

---

### Post by mike998 on 2005-07-18
I usually make the .wolf directory in my home directory writable by my user to solve the running under root problem.

---

### Post by endy on 2005-07-18
Don't run RtCW (or any game) as root, it's dangerous!! You may have ran it as root and the ~/.wolf directory was created with root ownership. I would delete this folder (or chown it to your username and group), run the game as normal user and the files should be owned by the normal user.

Regarding the possible sound issue, try this taken from the id faq found [here](http://zerowing.idsoftware.com/linux/wolf/) :

```
The sound doesn't work / sound crashes

The first thing to check is that it is actually a sound related. 
Run the game with +set s_initsound 0 and see what happens.
```

If sound is the problem, try disabling ESD (System > Preferences > Sound) and try running wolf again.

HTH (But I've not installed wolf for a while so I'm rusty) :)

---

### Post by deathfalls on 2005-07-19
Well, I got the singleplayer to work fine, at least it seems to. I played a few minutes on the first level. I tried to load up the multiplayer, and when I'd go into the options menu, it looked like it had several of the menus layered over each other. I brought down the console, and noticed it had several messages that said "Couldn't write to Main". I did the chown thing, but I assume this is a problem related to permissions?

Edit: I uninstalled, and reinstalled. Played the game (version 1.4) with no problems, but once I patched it to 1.41 it had the problem with the menus, etc. Also, in the multiplayer server box, I couldn't scroll through the servers or click any buttons. I guess something with the patch is screwed up?

---

