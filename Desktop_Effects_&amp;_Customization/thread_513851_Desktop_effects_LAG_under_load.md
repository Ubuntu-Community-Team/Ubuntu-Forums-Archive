---
title: "Desktop effects LAG under load"
date: 2007-07-31
forum: Desktop Effects &amp; Customization
---

### Post by screaminj3sus on 2007-07-31
This has been annoying me for a while, when using desktop effects when my pc is doing something like installing a program or even web browsing with firefox, basically anything using cpu greatly decreases compiz's performance. When I am not doing anything all effects are nice and silky smooth but then the PC is under load all of the animations get very slow and laggy.The minimize animation in particular is really bad. is there anyway to fix this? I went into gconf-editor and changed my refresh rate from 50 to the correct 75 and that helped a bit but animations still get laggy as hell.

Specs
p4 3.0 Ghz HT
Nvidia GeForce 7600GS 256MB
1GB RAM

Monitor is a 19 inch LCD @1440x900 75Hz

---

### Post by blueturtl on 2007-07-31
Seeing as the effects are still an experimental feature I don't think there's yet anything that can be done. Maybe someone will prove me wrong though...

---

### Post by screaminj3sus on 2007-07-31
Yes, but I am hoping there is some way to fix this. I mean compiz is touted as being so much faster than the likes of aero but it just runs so deadly slow on my computer for some reason. I have tried compiz, beryl, and even compiz fusion on sabayon and if anything fusion was WORSE. It is odd how cube and wobbly windows continue to run perfectly but the animations are so ridicuolously slow.

---

### Post by punx45 on 2007-07-31
this is going to sound like a stupid question, but, are you using the generic drivers for your video card?

---

### Post by screaminj3sus on 2007-08-01
> **punx45 said:**
> this is going to sound like a stupid question, but, are you using the generic drivers for your video card?

Nope I was using Nvidia's 9631 drivers installed via the restricted-manager. This has happened to me in many distro's with varying versions of compiz/beryl and nvidia drivers, even happend in sabayon using 100.xx drivers and compiz fusion. I installed gutsy yesterday though and for some reason it works perfectly in it without the problem I had in feisty and every other distro.

---

### Post by amccabe on 2007-08-03
I have the same problem with my 7600gs... I also can not get any open gl games to play at a decent framerate (like 1fps at 640x480)

And I also had the same problem with FC6... I was hoping to switch to Ubuntu and have it work.

---

### Post by screaminj3sus on 2007-08-07
for some reason Gutsy's compiz fusion is the only thing that runs really smoothly on my computer. If I install fusion on fiesty it is still sluggish with the minimize animations sometimes. Starting compiz fusion with --loose binding helps a little. I tried gutsy and it was smooth as hell. I'm not sure what they've in gutsy to make it run so smooth, I was very impressed. Now I just have to get it running smoothly in feisty :( Gutsy is the only time where I have gotten truly great performance, I have tried a lot of other distros like sabayon, PCLOS, SuSE, Fedora 7 ect...Right now I have at least acceptable performance in feisty. The lag usually only happens when I am using firefox. It gets really bad when I have a lot of tabs open or have been using it for a while.

---

### Post by screaminj3sus on 2007-08-07
Well I was messing around with my compiz fusion startup script some more and decided to add --indirect rendering and now it seems to run much faster and the animations are all smooth, any idea why this worked so well for me? I remember this being some kind of workaround for aTi cards and I have nvidia. Only problem now is I get some annoying line artifact like things when cropping images in GIMP.

---

### Post by Alexander2007 on 2007-08-07
I got it working on my box but the animations are slow as hell even "Cube". I'm also using the latest NVIDIA driver though "Envy".  Strange, seeing that I have an "NVIDIA 6200 (Turbo Cache)" that displayed graphics perfectly on Vista. :confused:
When I just installed Feisty with Compiz and NVIDIA drivers from the "Restricted Manager" everything was fast until  I received updates from Ubuntu.

---

### Post by mu:te on 2007-11-14
Same problem for me, when I have little programs such as Mono open, network manager, the computer goes really slow and I can barely do anything for a long time.

Developers, have you figured out whats wrong? Cause only writing this message, the computer stopped many many times..:(

---

