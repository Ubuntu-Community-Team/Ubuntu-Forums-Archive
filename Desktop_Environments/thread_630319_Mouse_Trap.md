---
title: "Mouse Trap"
date: 2007-12-03
forum: Desktop Environments
---

### Post by r.pupkin on 2007-12-03
My fellow Ubuntuans,

Thanks to this forum I have configured my laptop and desktop with Gutsy in a symbiotic mouse-keyboard relationship using SSH and X2X. I installed KVM on the client and loaded XP into it which, now runs without any problems. 

Previously, I did have a problem whereby my shared mouse would not work in KVM. This, however, was fixed with the command:
[INDENT] [COLOR="DarkRed"]export[/COLOR] [COLOR="Teal"]SDL_VIDEO_X11_DGAMOUSE=[/COLOR]0. [/INDENT]
Now my shared mouse works.

Given my success with KVM I decided to try  [COLOR="DarkRed"]export[/COLOR] [COLOR="Teal"]SDL_VIDEO_X11_DGAMOUSE=[/COLOR]0 on ut2004 and it worked! My shared mouse is usable in ut2004! There is only one small problem: When playing the game my mouse can cross over to my laptops' screen which results in my death. :rolleyes:

Does anyone know how I can trap the mouse on the second screen when playing ut2004?
Thanks!

---

