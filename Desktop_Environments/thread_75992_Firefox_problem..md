---
title: "Firefox problem."
date: 2005-10-14
forum: Desktop Environments
---

### Post by Kirky_D on 2005-10-14
I have had this problem since installing ubuntu. 

When i click my middle button (scroll wheel) i have it set to use autoscroll. when i click out of using auto scroll sometimes it says url could not be found sometimes it takes me to a completely random website and just now while typing this post it decided to paste some text that i had writeen in another thread a few minutes ago which i thought was a little bit weird.

Any body know if this a well known bug or knows where to find/change a setting to stop it that would be great.

Cheers

---

### Post by Dr. Nick on 2005-10-14
I used to have that problem of page cant be found if I recall. It has stoped now, not sure why/how. The problem is your scrool wheel can open links, If your clicking off scrool whie over a link it will open it up. No way to disable it that I know of

---

### Post by Kirky_D on 2005-10-14
It happens even when i am not over a link. My curser could be anywhere on the page and it would try to open a URL or send me to another page randomly. Very annoying.

Cheers for the info!

---

### Post by tjabri on 2005-10-14
[QUOTE=Kirky_D]It happens even when i am not over a link. My curser could be anywhere on the page and it would try to open a URL or send me to another page randomly. Very annoying.

Cheers for the info![/QUOTE]
I used to have the same problem in another distribution, I think it was Fedora Core 4. I never got that problem resolved software side, but the hardware problem was that my wheel would get stuck and click instead of roll. New mouse, no more problem!

---

### Post by Kirky_D on 2005-10-15
My wheel doesn't get stuck. The behaviour is similer to clicking a link, but with the mouse wheel and with no actual link there. as soon as i click out of autoscroll it tries to go to some URL which it either says it isn't a valid URL or takes me to a random web page.

---

### Post by liquidtenmillion on 2005-10-15
type in about:config and change middlemouse.contentLoadURL to false, and middlemouse.paste to false.

---

### Post by jdong on 2005-10-15
[QUOTE=liquidtenmillion]type in about:config and change middlemouse.contentLoadURL to false, and middlemouse.paste to false.[/QUOTE]

Just contentLoadURL needs to be false -- middlemouse.paste just disables mouse-paste in textboxes, which is a very powerful feature when mastered.

---

### Post by Kirky_D on 2005-10-15
Fantastic cheers!

---

