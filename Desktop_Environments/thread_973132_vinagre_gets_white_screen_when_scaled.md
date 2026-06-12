---
title: "vinagre gets white screen when scaled"
date: 2008-11-06
forum: Desktop Environments
---

### Post by SalsaDoom on 2008-11-06
Hi fellas.

I'm having a weird little problem here, when I activate scaling in vinagre, I just get a white blank screen. If I switch off scaling, the remote desktop appears normally. This is a bit of a tricky one, since I can easily replicate the problem on my eee 901, but it doesn't happen on my desktop machine. Course, its the 901 where the scaling is really useful! 

Now, since the eee's have a bit of an unusual screen resolution, could this be why it works on my desktop but not on the laptop? What do you guys think? Anyone else noticed this problem?

btw, Compiz and all that is disabled across the board on all machines, my desktop and my laptop run 8.10, another machine I vnc to runs 8.04. The white screen issue happens when connecting to the 8.10 and 8.04 machine.

---

### Post by SalsaDoom on 2008-11-06
Ok. Changing the resolution down doesn't fix anything. I really have no idea why it does this. Not sure how to debug this further, right now I don't seem to have enough to generate any sort of meaningful bug report. Especially since a look on google, the forums and launchpad doesn't seem to have anyone else who has this problem.

---

### Post by SalsaDoom on 2008-11-06
More data. Think I might submit a proper bug report on this one. From my testing between 3 computers and two laptops, it looks like the number of monitors is the key. 

It looks like a computer with a single monitor can scale another computer with a single monitor, but not a computer with two screens. But a computer with two screens can scale another computer with two screens. Interesting bug.

And, unfortunately, completely ruining the point of scaling in many cases.

---

### Post by DavHod on 2008-11-17
Have a similar problem under 8.10 but with a single monitor to single monitor on MS XP. I inadvertently pressed Control "Q" during a session and killed the session. Each time I fire up vinagre from the Applications/Internet menu all I get now is a white screen and cannot switch off full screen mode. Locked out! Reinstalling vinagre did not help. Created a new user and can run ok under the new user. Seems user related within Gnome but I haven't a clue where to look.

Update - Thanks to bobbob1016 - typing "vinagre reset" in terminal forced an error message in normal screen mode and restored normal working. Sorry for the noise - missed his post earlier.

---

### Post by Ghosty.be on 2008-12-13
Thx a lot the "vinagre reset" in console did the trick for me too!

---

### Post by gcastell on 2009-04-21
> **Ghosty.be said:**
> Thx a lot the "vinagre reset" in console did the trick for me too!

I just want to mention that I had to do a "sudo vinagre reset" for me to work.

---

