---
title: "Lag in all games while on ubuntu"
date: 2007-12-30
forum: Gaming &amp; Leisure
---

### Post by flippykid on 2007-12-30
Well I have no idea why this happens, but even on games like Woflenstein enemy territory I seem to lag whenever I look somewhere on the map with loads more rooms and other things then other locations. I find it funny, because if I am playing a game and say I am on one side of the map, and the enemy spawn is at the other, every time I look in the direction regarless if something is blocking my view I still get so much lag to the point where I get about 1 fps every 3 - 4 seconds, It makes no sense, I mean it's as if it's showing everything all at once even though I can't see it, like even if there is a wall there making a boxed room, if I look in the direction where there are more models on the map ( like rooms, players etc) I still lag a lot. And once again this happens with all my games, including the ones that need wine, and even the ones that run right on linux. Can someone tell me if I can fix this, or if there is something I am doing wrong, oh and I am running a radeon 9000 pro on the built in drivers since aparently ubuntu already has one.

---

### Post by foolsh on 2007-12-31
you could try the closed source drivers and see if that clears up the trouble your having

---

### Post by flippykid on 2007-12-31
How do I install them? Is there some special way that I have to do it?

---

### Post by acoustibop on 2007-12-31
No, the fglrx drivers won't work with a Radeon 9000 unless you go back to the 8.28.8 one, which is quite old - came out for Edgy, I think.

@flippykid: open the Restricted Drivers Manager (System -> Administration -> Restricted Drivers Manager) and see if it offers to install a driver for your card.  If it does, go for it - the driver it installs will be the 8.28.8 one.  If there isn't a driver offered, I'd be inclined to forget it: the 8.28.8 driver is meant for a much older version of Ubuntu and may not work properly in newer versions - anyone using it who can comment on this?

The free driver you're using ATM (probably the 'ati' one) should be fine anyway.  Are these games you're getting problems with online games?  If they are, your internet connection should be the first thing you should look at.

---

### Post by dburnett77 on 2007-12-31
As far as I know, you can, if you own a legit copy, decode it.

Run it through a decompiler, and then integrate it into the Xserver, somewhat difficult, though.

Many do...

---

### Post by flippykid on 2007-12-31
> **acoustibop said:**
> No, the fglrx drivers won't work with a Radeon 9000 unless you go back to the 8.28.8 one, which is quite old - came out for Edgy, I think.

@flippykid: open the Restricted Drivers Manager (System -> Administration -> Restricted Drivers Manager) and see if it offers to install a driver for your card.  If it does, go for it - the driver it installs will be the 8.28.8 one.  If there isn't a driver offered, I'd be inclined to forget it: the 8.28.8 driver is meant for a much older version of Ubuntu and may not work properly in newer versions - anyone using it who can comment on this?

The free driver you're using ATM (probably the 'ati' one) should be fine anyway.  Are these games you're getting problems with online games?  If they are, your internet connection should be the first thing you should look at.

Well I looked in restricted drivers thing and all I saw was firmware for broadcom, I think that may be my wireless internet thing that's connected but not using. And I have no trouble with internet or anything, even when I play singleplayer whenever I look somewhere with lots of rooms or models or whatever even if my view is blocked I lag alot, so yeah.

---

