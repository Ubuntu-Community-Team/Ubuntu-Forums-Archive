---
title: "Teamspeak 2 - does it ever work under Linux?"
date: 2009-12-28
forum: Gaming &amp; Leisure
---

### Post by Objekt on 2009-12-28
Has anyone ever gotten Teamspeak 2 to work correctly in any version of Kubuntu or Ubuntu?  I've been banging my head against the wall for the last week, trying to get TS2 to work in both Kubuntu 9.04 and Ubuntu 9.10, to no avail.

The problem is that while everyone else sounds fine to me, they report that I have a weird echo/breaking up sort of thing going on.  I've heard it myself by having 2 computers hooked up at once, talking through one while listening through the other.

All I can do is mute myself or turn myself up even louder.  Nothing fixes the quality issue.

TS2 works fine under Windows XP, so it's not a hardware issue.

I've tried the Teamspeak 3 beta client with the same people, and they say I sound fine through it.  So maybe the Linux TS2 client is simply crap.  What has been your experience?

---

### Post by Vadi on 2009-12-29
Yeah it was crap for me, I gave up on it and went to Mumble. TS3 unfortunately isn't faring much better atm.

---

### Post by Objekt on 2009-12-29
I'm having an extremely weird problem with TS3: it simply WILL NOT start from anywhere but the console.  

I can't make an icon for it, I can't click or double-click on the executable in a file browser.

Same problem in both Kubuntu 9.04 and Ubuntu 9.10

---

### Post by hikaricore on 2009-12-29
I never had any problems with TS, this could be a pulseaudio related issue.

---

### Post by Bölvaður on 2009-12-29
> **hikaricore said:**
> I never had any problems with TS, this could be a pulseaudio related issue.

sounds like it is a problem with config in ts.
try to increase the sound buffer and have more quality instead of performance on the outgoing sounds.

it can only be pulse problem if the same sound comes when you record with Applications &#8594; Sound & Video &#8594; Sound Recorder

---

### Post by FootySr on 2009-12-29
> **Objekt said:**
> So maybe the Linux TS2 client is simply crap.  What has been your experience?

For me the fix for TS2 is to do this... Under Settings --> Sound Devices --> Sound Driver... Click the "Other" radio button and type in /dev/dsp1

Hope that helps. Forget where I found that fix.

I've yet to try TS3 because I'm not sure how to deal with the .run thingy. :)

Jake

---

