---
title: "Gutsy+ Sdlmame+Loemu=Roms running Very slowly."
date: 2008-04-27
forum: Gaming &amp; Leisure
---

### Post by Kidis251 on 2008-04-27
I have gutsy installed and after getting both SDLmame and Loemu running I am very frustrated. I can get Loemu to find the roms, make the list, but when i start one of the games it runs very slowly. I tried Running WinUI32(the windows GUI mame) through wine, got it to work and see all of the roms, but the same thing happened. the sound sounds like a CD skipping and the graphics are choppy. Its unplayable. I am new to linux and ubuntu. It took a week for me to decide on ubuntu and get this far. Im just a little worn out. Please some one help!

---

### Post by Son of Silas on 2008-04-28
Find the line in your /etc/sdlmame/mame.ini/mame.ini that refers to your video settings and try changing OpenGL for 'soft'

That fixed it for me in Gutsy, however upgrading to Hardy has caused the problem to return!

---

### Post by Kidis251 on 2008-04-29
Would you be so kind as to walk me through that? I am brand new to linux and only half understand what you just told me.

---

