---
title: "Beryl keeps crashing, mega linux noob here"
date: 2007-05-21
forum: Desktop Effects &amp; Customization
---

### Post by moljac024 on 2007-05-21
Okay, i understand that this might be off-topic but i desperately need some questions answered.

I completely got rid of windows and installed Ubuntu 7.04. I wanted to try beryl so i installed that too with package manager and it, to my amazement, worked straight away (I have an ATI x550 graphic card). It seemed strange to me that i didn't have to install any ati drivers or fiddle with anything to get beryl working (many online guides relied on installing closed source ati drivers or modifying the existing open source ones).

So, beryl runs fine, everything works (i did fiddle a bit with video output in players to avoid the black screen) but i get random freezes and it won't revert back to metacity, i have to manually restart the computer. What could be causing that ? Please somebody help, i'm drowning here :-(

---

### Post by steevols on 2007-05-21
I have an NVidia card, so I may not be much help, but...

Define a random freeze. Does the whole PC lock up, or does the window-decorator/manager itself simply crash?

---

### Post by moljac024 on 2007-05-21
The PC locks up.

It locked up several times when i was just trying to maximize an app, it locked up once while my sister was chatting through skype and it also locked up while i was moving my mouse to the top right screen (to choose between all open windows)....

---

### Post by skyhopper88 on 2007-05-21
Make sure it's set to fallback to metacity when it crashes, I've never had it not do this.

---

### Post by moljac024 on 2007-05-22
It is set to fallback to metacity but still it locked up the PC.
Hasn't happened since then (i disabled water effects and under rendering platform picked Force AIGLX)

About the fallback - there are two options where it can be set, do they both have to be enabled ? Can they conflict ? There is an option when right clicking on the red diamond and an option in the settings manager under development tab - crash handler plugin - which need to be enabled ?

---

### Post by steevols on 2007-05-22
Ahh, problem solved: "...disabled water effects..."

Water fx need pixel shaders, and if you force them to enable when your PC doesn't fully support them, it will lock up.

---

### Post by moljac024 on 2007-05-22
Well everything runs fine now (must be water effects), but i was able to have rain drops on my desktop so the effects worked.....nah, don't need 'em anyway....

---

### Post by steevols on 2007-05-22
Okay... what version of Beryl are you running? Do you have the "unsupported" fx package off of synaptic?

---

### Post by moljac024 on 2007-05-22
well, i installed it using synaptic, but i don't know how to check which version it is....how do i do that ?

---

### Post by steevols on 2007-05-22
Well, my main question was about the unsupported thing. Easy way to check is to go into synaptic, search "beryl", and see the version number of each package that has a green checkbox. You've probably got 2.1 installed if you're having stability problems.

---

### Post by moljac024 on 2007-05-22
Yes, my beryl version is 0.2.1...what's the last stable one ? And what's new in 0.2.1 ?

---

### Post by steevols on 2007-05-22
2.0 (or is it 0.2.0...) should be the last stable version. I honestly have no idea what's new, but I've seen many people say that 2.1 tends to be more... crashy.

---

### Post by moljac024 on 2007-05-22
Thanks alot! What would be the easiest way to switch from v0.2.1 to 0.2.0 ?

---

### Post by steevols on 2007-05-23
I'd head to the Ubuntu packages repository and poke around; you should be able to find it easily enough.

---

