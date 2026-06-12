---
title: "Revert compiz to defaults?"
date: 2006-06-10
forum: Desktop Environments
---

### Post by ol1v3r on 2006-06-10
Hey everyone!

I've been messing with my Compiz settings and I got myself into a situation of windows bouncing everywhere and desktops spinning when they want to (lol) .. Is there any easy way to just revert everything back to default? Im getting dizzy from all of this OpenGL dancing action on my screen!

Thanks!
Oliver :]

---

### Post by angkor on 2006-06-10
I haven't heard of any 'revert to default' setting with xgl and compiz. But if you install 'gset-compiz' it's quite easy to remove plugins you don't want and change all other settings for that matter.

I myself removed the wobbly after 1 hour and set the cube speed so fast you don't notice it, so switching desktops is just as fast as in metacity. 

I like xgl and compiz for the increase in desktop speed (productivity) and remove all useless (to me) plugins. What's left is a very good looking, extremely fast desktop experience :)

---

### Post by roax on 2006-06-10
As your user do: gconftool-2 --recursive-unset /apps/compiz

---

### Post by ol1v3r on 2006-06-11
[QUOTE=angkor]I haven't heard of any 'revert to default' setting with xgl and compiz. But if you install 'gset-compiz' it's quite easy to remove plugins you don't want and change all other settings for that matter.

I myself removed the wobbly after 1 hour and set the cube speed so fast you don't notice it, so switching desktops is just as fast as in metacity. 

I like xgl and compiz for the increase in desktop speed (productivity) and remove all useless (to me) plugins. What's left is a very good looking, extremely fast desktop experience :)[/QUOTE]

Yeah i've found my productivity level has shot right up with XGL + Compiz .. Its just so good to look at and so useful! Its also a great party piece for all the Windows users who come over, haha! "HOWDUDOTHAT?"

I finally fixed my problem by tweaking everything with gset-compiz, its quite easy to use! Thanks for that angkor!

:mrgreen:

---

