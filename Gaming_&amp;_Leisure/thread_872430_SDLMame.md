---
title: "SDLMame"
date: 2008-07-28
forum: Gaming &amp; Leisure
---

### Post by arfink on 2008-07-28
I am having trouble with SDLMame. I am using OpenGL and have recently installed working GL drivers for my ATI Radeon 300m. I know they work because other 3d games work great (Nexuiz, etc.) 

I am having strange problems with SDLMame though, it kicks me out with a cryptic "segmentation fault" and nothing else, no error messages or anything. When I run SDLMame in software rendering mode the games work, but are painfully slow, as you'd probably expect.

Anyone have any ideas or can help me out?

---

### Post by BigSilly on 2008-07-28
Have you edited your mame.ini to use opengl? 

```
sudo gedit /etc/sdlmame/mame.ini

```

Scroll down to VIDEO OPTIONS, and right underneath where it says 'video' type opengl on the right replacing whatever it was that was there.

It might be this. Sometimes people forget to do it.

EDIT: Sorry, you've obviously done this.

---

