---
title: "Ventrilo Problem : Please help me troubleshoot"
date: 2006-12-29
forum: Gaming &amp; Leisure
---

### Post by murraysw on 2006-12-29
Hi Guys:

Ventrilo runs just fine, I can hear just fine, but theres one slight problem:

After using my push-to-talk hotkey (or even just speaking once using the mic sensitivity method) I am not able to speak again unless I go into the settings and reset my push-to-talk or method of speaking....If I do it more than 3 or so times Ventrilo completely crashes.

Do you think this is an ALSA issue?  What could be the solution for this?  If I turn on the direct-input or whatever option, it centers my mouse in the screen and I cant change settings...

Ill describe the problem in more detail after im done this game of Starcraft with my roomate and WSGs with my guild...

Thanks

Scott

---

### Post by Sammi on 2006-12-30
Ventrilo behaves pretty similar to this on my machine. It's a laptop with a crappy onboard soundcard, which I think is the problem. Linux soundcard drivers just aren't good enough for onboard cards :mad:

I'm running Ventrilo under wine using aoss. How about you?

---

### Post by murraysw on 2006-12-31
Alright I solved the problem - 

If you are experiencing this issue, there are a couple settings you need to change:

Under ¨Output Device¨, make sure that Use Directsound is checked while under Input device it is NOT.  For the Output device use Default DirectSound Device and Input use Default Wavemapper....Mixer you should find the one that allows Mux to be rec and Line to be mic.  Make sure use DirectInput to detect hotkey is NOT checked and either is Discard Hotkey.  

It should work out.

---

### Post by Cappy on 2007-02-20
Awesome, thanks! Vent works perfectly now! My mic volume was low but the amplifiers fixed that =)

---

### Post by noenter1 on 2007-02-21
Nope didnt work, cant select mic for line, and also when i go into the setup it says: Unable to create Directimput object.

---

### Post by acattack12 on 2008-06-06
hey guys i had vent working the other day with all of my friends and stuff like 7 ppl but for some reason today when i try to log bak on to that server the panel just says msg:conatacting server and it has been like that for 30 min i need help ty if any1 ansewers this

---

