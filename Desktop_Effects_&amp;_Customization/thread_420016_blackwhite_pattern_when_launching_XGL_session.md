---
title: "black/white pattern when launching XGL session"
date: 2007-04-23
forum: Desktop Effects &amp; Customization
---

### Post by randomstuff on 2007-04-23
I have a ATI mobile radeon X700 in my laptop, and installed XGL + beryl, using the fglrx driver from the restricted drivers tool. Everything is working fine as far as I can determine, however I do get this annoying black/white pattern after logging in, before the desktop shows. I have tried to search on google, but everyone asking the same question (in the midst of other threads) never received a reply, so I opted for a more direct approach here.

Can this pattern be disabled? Who's "fault" is it? Xgl?

Also, previous to the release of feisty, I heard rumors about the open source ati driver finally working with cards like mine. However, the install disk still did not work without safe mode, only gave a black screen after booting. Is the driver not working, or is it the bug where the output is routed to the (non-existent) secondary display?

I'll be most grateful for anybody who gives me an answer for either question.

---

### Post by aimran on 2007-04-23
I have the same problem. Also for me the beryl startup animation does not display instead the default ubuntu one does (with the black + white pattern in the BGround).

Not that it matters for me. I can live with that. That was in edgy btw. 

Specs: Compaq Laptop V5000 ATI 200M AMD 64 Sempron.

---

### Post by Sgozz on 2007-04-23
You just have to start Xgl with -br option, and you will have a black background.

Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer -br & sleep 2 && DISPLAY=:1 gnome-session

---

### Post by randomstuff on 2007-04-23
Thank you for your reply. Although I wish the transition could be made even smoother, at least it is no longer completely hideous. With regard to the driver issues, I suppose I'll check it out myself once I get access to a secondary display.

---

### Post by andrewsomething on 2007-06-15
I'm dropping a quick post to bump this back up. 

There has to be a way to make it look better than just a black screen or the ugly black and white pattern, but this is the only post I've been able to find that even asks the question.

Somebody out there knows. We're just waiting for you to stumble onto this post....

---

