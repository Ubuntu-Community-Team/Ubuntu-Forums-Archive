---
title: "Howto setup a customized startup link ?"
date: 2008-01-10
forum: Desktop Environments
---

### Post by tadeusz666 on 2008-01-10
Hey

Im using blender and to have my sound working (in blender) I need to go to 
my blender folder, which is in: 

** /home/user/.blender** and type **export SDL_AUDIODRIVER=alsa &&**

and start blender to make the sound work. 

Now my question is how do i make this happen when i click the blender link from my 
desktop ?

I already tried rightclicking on the blender link and putting in the command in the 
launcher flag --> command line but i get an error from blender, that says that it 
couldnt load SDL_AUDIODRIVER

Im running Gutsy AMD64 and Gnome 2.20.1

Tadeusz

---

### Post by Coreigh on 2008-01-10
Do you need this driver only sometimes? Why not configure it to load at login or startup?

---

