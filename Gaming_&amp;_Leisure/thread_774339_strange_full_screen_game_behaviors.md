---
title: "strange full screen game behaviors"
date: 2008-04-29
forum: Gaming &amp; Leisure
---

### Post by linuxlizard on 2008-04-29
I'm having some wierd game behavior under hardy.

I've got two user accounts.
Account #1 is the original and the screen resolution is 1024x768
Account #2 I created to play around with the desktop and the screen resolution is 1280x1024.
OK here's the wierd stuff-

If I'm logged into user account #1 
Legends won't open and just doesn't seem to respond

Open Arena is stuck in a window even though it's supposed to be full screen. It was working "properly" at the default (low) resolution of something like 640x400, but when I switched it to 1024x768 the full screen became a window and the mouse became non-responsive.

Flobo Puyo screen becomes white and everything "freezes up" until I hit ctrl-alt-bkspce.

Adonaxis is pretty much exactly like open arena

If I'm logged into user account #2

Everything seems to work properly. But 1280x1024 looks bad on my monitor for the desktop- hard to read, poor refresh rate, and something strange is going on with the video where I get rows of barely noticable "shadow" lines which while barely noticable are there and add to eye strain after a few minutes.

---------------
So, I figured it was the resolution, and I switched user account #1 to the same resolution as user account #2.

No change in the behavior of these games.

So, I figured maybe it was the user account and some crazy thing to do with that, so I logged into user account #2, and changed the resolution to match user account #1 originally (1024x768). Had the same problems as user account #1 now, except legends now started in a window and the mouse was unresponsive- same behavior as open arena, rather than the game not loading up and responding at all, like user account #1.

I do have compiz enabled, but when disabled it seems to make no difference to the behavior of these games.

I have an nvidia video card which has always worked fine prior to hardy.

Anyone know the source of my problem here?

edit: nearly forgot- some games are working fine in full screen mode in user account #1. Alien Arena for example has never looked so good or worked so well for me.

---

### Post by nutpants on 2008-04-29
i removed compiz completely after i noticed it was installed but not active (AFAIK) as i was not happy with just switching the screen resolution up and that seemed to fix it so far for me.

so far..

il keep you posted if it comes back.

btw the link to legends was all wrong when i installed it, i could not start it from the menu, i had to look for where it was installed and change the link.

nutz

---

### Post by linuxlizard on 2008-04-30
Hi Nuts,
Thanks for your response.
I got rid of compiz and that worked fine on my original install.

I didn't like that "broken" feeling that something was not right though, so I did a complete reinstall. Strangely, that seemed to fix the problem. I now have compiz working fine but I have to just turn it off in systems-preferences-appearance before I go into legends. No big deal there.

So, looks like it's working great now. Everything much faster than gutsy, and I'm getting better frame rates out of my video card in all games I've tried like legends, alien arena, etc.

---

### Post by stwert on 2008-08-18
I have a similar/same problem in that Open Arena switches to a window after a bit of playing and I can't control anything, quit, or switch applications, so essentially my computer is frozen up. I don't know how to quickly turn on/off compiz... I'd like to keep compiz, and I don't know how to keep my settings if I temporarily turn it off.
Thanks for any help.

---

