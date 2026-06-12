---
title: "Compiz and Scroll Wheel .... help?"
date: 2009-10-28
forum: Desktop Environments
---

### Post by aristotlewilde on 2009-10-28
Good morning.  I am running 9.10 Beta now and am missing a feature that was always default in Compiz for me before.  

When hovering over the desktop, I used to be able to spin the scroll wheel and switch between desktops.  This was disabled by default in my install for some reason.  I tried adding Buttons 4 and 5 in Desktop Wall to make this work and it does.  BUT it overrides the scroll wheel while in a window, so if I am scrolling through say... Ubuntu Forums, and want to read further down a page, I accidentally switch desktops.  

Can anyone give me some direction here?

---

### Post by anagor on 2009-10-28
I just tried it for myself,
and the conclusion is.... :)
instead of "Desktop Wall" where it should remain disabled since it applies globally, you should enable it in "Viewport Switcher"
in "Desktop-based Viewport Switching" tab, where it will get you the desired effect.

cheers;

---

### Post by aristotlewilde on 2009-10-28
Thanks.  I just enabled Viewport Switching and tried this.  Spinning the scroll wheel is giving me no results,

---

### Post by anagor on 2009-10-28
this is strange, cause before replying to you, I tried it on my laptop and got the result.
There are "left", "right", "up", "down" and "next", "prev"
have you tried the "next", "prev" ones?

---

### Post by anagor on 2009-10-28
what is written in your "plugin initiate action" and "action name for initiate" fields?
Mine says, "rotate" and "initiate_button" respectively.

---

### Post by aristotlewilde on 2009-10-28
> **anagor said:**
> this is strange, cause before replying to you, I tried it on my laptop and got the result.
There are "left", "right", "up", "down" and "next", "prev"
have you tried the "next", "prev" ones?

When I set it to next or previous, it is still overriding scrolling within window...?

> what is written in your "plugin initiate action" and "action name for initiate" fields?
Mine says, "rotate" and "initiate_button" respectively. 

Mine say the same.  Wondering if maybe I have my mouse settings incorrect.

---

### Post by anagor on 2009-10-29
Have you disabled it in the "Desktop wall" section?
I don't think any mouse setting can be that wrong :)
It's looks like a compiz issue.
Maybe you should file a bug for that, since on my system it works as expected.

---

### Post by spongypants23 on 2009-10-29
I fixed this by setting the Next to Button4 and Prev to Button5 in Viewport Switcher.

---

### Post by aristotlewilde on 2009-10-29
uh....  how about just setting Visual Effects to EXTRA???  it worked :)

---

### Post by anagor on 2009-10-29
I have it on manual for a long time, so didn't even thought about it :)

---

### Post by TalioGladius on 2009-11-02
I set Move Next to Button5 and Move Prev to Button4 in the Viewport Switcher and have the same functionality as before 9.10.

---

### Post by dogooder on 2009-11-05
> **TalioGladius said:**
> I set Move Next to Button5 and Move Prev to Button4 in the Viewport Switcher and have the same functionality as before 9.10.
This worked for me. Thanks.

---

### Post by aristotlewilde on 2010-05-26
Special thanks to myself for remembering I posted this before asking the question again...

---

