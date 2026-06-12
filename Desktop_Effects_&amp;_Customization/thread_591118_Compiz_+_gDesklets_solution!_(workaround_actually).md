---
title: "Compiz + gDesklets solution! (workaround actually)"
date: 2007-10-25
forum: Desktop Effects &amp; Customization
---

### Post by szulat on 2007-10-25
i had problem with gdesklets disappearing on "show desktop" (by keyboard shortcut or the "desktop" icon). this is serious bug, as it effectively destroys the whole purpose of using desklets.
there are many threads on the forum with people complaining on the same problem and it seems there was no solution.

but after doing some research i found pretty good workaround:

1."advanced desktop effects settings" -> "window rules" -> enter "class=Gdesklets" in "Skip taskbar" and enable the "window rules" plugin
2. "advanced desktop effects settings" -> "general options" -> disable "Hide Skip Taskbar Windows"

the side effect is that the gDesklets Shell window is also excluded from the taskbar and is not minimized on "show desktop". but that's not a big issue as you don't see this window at all during normal work.

---

### Post by NawaMan on 2007-10-25
Thanks a lot for the trick, I was just about being MAD with this problem :D

---

### Post by rogerdean on 2007-10-28
Where would I find "advanced desktop effects settings"?
Sorry for being thick...
R

---

### Post by rogerdean on 2007-10-28
ah ok, i needed to install compiz config packages from synaptic...

---

### Post by hamster_billy on 2007-10-28
Great. Thanks. I couldn't find out what class of window gDesklets were - I never thought of trying Gdesklet. You've just made them infinitely better.

---

### Post by Anovadea on 2007-10-31
> **szulat said:**
> 
1."advanced desktop effects settings" -> "window rules" -> enter "class=Gdesklets" in "Skip taskbar" and enable the "window rules" plugin
2. "advanced desktop effects settings" -> "general options" -> disable "Hide Skip Taskbar Windows"


Hey, thanks for that!

Although, I found it didn't work at first. :(

I do have a solution though - on top of all of the above, I used this extra step:

3."advanced desktop effects settings" -> "window rules" -> enter "class=Gdesklets" in "Non minimizable windows" 

Having googled around, this doesn't seem to be necessary for a lot of people, but it seems I have to do it, so I just thought I'd share in case anyone else has my problem. :)

Regards,
Aoife

---

### Post by S1acker on 2008-01-19
thank you, very much infact

---

