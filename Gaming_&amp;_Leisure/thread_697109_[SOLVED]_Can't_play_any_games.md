---
title: "[SOLVED] Can't play any games"
date: 2008-02-14
forum: Gaming &amp; Leisure
---

### Post by BobLand on 2008-02-14
I've been playing sauerbraten for the past month.  Suddenly, the game play becomes jerky with small lockups.  This allows the monsters to beat the snot out of me while I'm frozen still.  I uninstalled/reinstalled, even added the patch.  Nothing changed.

Installed Tremulous.  Couldn't even get to the game.  The mouse would only move when it felt like it so I couldn't make any selections except to barely exit the game.

Next, Beyond the Red Line, which is a fantastic game.  I've played this a few times with the only problem being my inability to keep up with the game.  This time, I couldn't even start missions because the mouse would stall.

I don't have a problem with the mouse or lockups outside of the games.  Is it possible that during the past few days I downloaded something that overwrote an important lib or device common to all games?

Intel 4400 dual-core
2 G RAM
250 G SATA
GeForce 8400 GS
IBM kb (kind of old but it works)
Logitech MX510

All up-to-date drivers

I'm clueless...
bobland

---

### Post by xeth_delta on 2008-02-14
you could try checking if there is any program using the CPU in the background while you play.
Open a terminal and type "top". It will show a list with the most active programs/processes.

---

### Post by BobLand on 2008-02-14
One surprising thing this showed was I have 2 G RAM and 1 G is in constant use.  Why's that I wonder?

Is there a way to control this?

bobland

---

### Post by acoustibop on 2008-02-15
Do you have Compiz enabled, BobLand?

---

### Post by xeth_delta on 2008-02-15
> **BobLand said:**
> One surprising thing this showed was I have 2 G RAM and 1 G is in constant use.  Why's that I wonder?

Is there a way to control this?

bobland

Free memory is not wasted under Linux. The system uses it for buffers and cache to make the system faster, so that could very well be what you see. If programs need more memory, buffers and cache are displaced and memory freed.

You can check this with:
```
free -m
```
It will also tell you what amount is being used for cache and buffers, in MB.

---

### Post by BobLand on 2008-02-15
The diff between compiz and metacity is 23k.  Not much at all.

---

### Post by xeth_delta on 2008-02-15
> **BobLand said:**
> The diff between compiz and metacity is 23k.  Not much at all.

What acoustibop meant is that under compiz OpenGL applications seem to behave a bit strange, for instance there can be flickering. A work-around I know of in the meantime, is to switch to a regular window manager while playing games.

---

### Post by BobLand on 2008-02-15
I ran under metacity.  Before these troubles, I could run it under either.  

One thing I recall installing that may have effected this is sshserver.  I can't recall the syntax for this package so I haven't been able to remove as of yet.

On the other hand, I really don't want to remove it as it is such a valuable tool.

What mystifies me is why ALL the games are acting funny.  Is there a way to find out what libs games share in common?

bobland

---

### Post by xeth_delta on 2008-02-15
I guess you could try to run "strace program_name". It will let you know what functions are being called, but it is a huge amount of information output, and I am not sure it will be useful to you.

By the other hand it could be a problem witht the X11 server configuration. You can try to check if there is a back-up of "/etc/X11/xorg.conf" and when was the file changed.

Is the behaviour you describe intermittent, or is it continuous after it starts?

---

### Post by BobLand on 2008-02-15
I looked at the xorg logs but saw nothing out of the ordinary (as if I would know...).

The behaviour goes something like this.
I enter a game.  If there is an extensive menu like Beyond the Red Line, it make take a while to get anywhere.  When a briefing starts, the sound also goes on and off.  If I have to click on something, the cursor wont move.  I keep wiggling the mouse and eventually the cursor gets there.

Playing sauerbraten: enter the game and get the menu.  I want to select a player type and map.  The cursor doesn't move.  Wiggle it and eventually I can make the selection.  The game starts.  Monsters approach and fire at me.  I move left/right/jump.  Nothing.  They still approach - that's the weird part.  The game is not frozen.  I am!  Then they beat me to death and it starts again.  Heck, that aint no fun!

This pretty much happens in all my games.  I've reinstalled them but it didn't make a difference.

bobland

---

### Post by BobLand on 2008-02-16
Turns out the problem was either a funky keyboard connector - the connector is usb but I have an adaptor on it; or the port on the mo' board is defective.  After fiddling around a bit I was able to go back into sauer and play normally.

bobland

---

### Post by xeth_delta on 2008-02-16
> **BobLand said:**
> Turns out the problem was either a funky keyboard connector - the connector is usb but I have an adaptor on it; or the port on the mo' board is defective.  After fiddling around a bit I was able to go back into sauer and play normally.

bobland

Good to know the problem is gone! Comes to show us that sometimes the right answers are the obvious simple ones. :)

---

