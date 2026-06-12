---
title: "mathematica problem with XGL"
date: 2006-09-27
forum: Education &amp; Science
---

### Post by interskh on 2006-09-27
when i lauched the mathematica in XGL, it did not work, and X broke with it. i had to restart X.

i have tried without XGL, it is ok.

so, what's the problem? what should i do?

thx for your suggestion.

my system: ubuntu6.06lts

---

### Post by Rui Pais on 2006-09-27
hi,

some people seems to find a solution by exporting first:
```
export XLIB_SKIP_ARGB_VISUALS=1
```
before running Mathematica.

Hope it works with you.

---

### Post by interskh on 2006-09-27
thx:)
i've done this before, but it does not work either:(

---

### Post by Rui Pais on 2006-09-27
uhmm, sorry to ear it.

it didn't work with me too, but since i readed lot of people reporting success with that and you haven't mention it in your 1st post so i suggested... 

Another one. 
Do you really need XGL? Or maybe don't work with xgl on Mathematica sessions...
Before i give up on Xgl, i've made 2 X servers, 0=Standard and 1=Xgl (on  /etc/X11/gdm/gdm.conf-custom) so when i needed to use Mathematica (totem have the same problem) i simply press Ctrl+F7 and login there. 
Or lightly you can do the same using a nested login window (usually on gnome is on System menu) with a Standard server.

Sorry, not solutions, only workarounds :(

---

### Post by interskh on 2006-09-27
emm, it seems a nice idea
though it's better to do these all in one x server.
anyway, thank u:)

sry for my poor english.

---

### Post by SuperSack56 on 2006-10-22
i was having some issues running mathematica in Edgy, but 

export XLIB_SKIP_ARGB_VISUALS=1

worked great for me. thanks!

---

