---
title: "Fluxbuntu: Setting up &quot;extra&quot; keys on keyboard"
date: 2008-06-12
forum: Desktop Environments
---

### Post by snowpine on 2008-06-12
Hi, I am using Fluxbuntu, but I would imagine any of you Fluxbox users might have an answer for me too. :)
My keyboard is working fine, however, there are a lot of other buttons on the keyboard (volume, mute, copy, paste, play, stop, etc) that worked in Windows but don't work in Flux. What is the best way to get these working? Thanks!

---

### Post by eriqjaffe on 2008-06-12
Depends on if they're even recognized...the "FN" key on my old laptop isn't, for example.

You can use "xev" (I think it's in the repos) to figure out the keycodes, but I'm not quite sure what to do beyond that.

---

### Post by Nythain on 2008-06-12
xev and xmodmap i believe will get the job done... redsquirrel has a great guide on this in the forums already, you could probably do a forum search for "fluxbox keys" and find it

---

### Post by snowpine on 2008-06-13
Thanks guys, I found the thread you mentioned and I think that will get me started. Yay fluxbox!

---

