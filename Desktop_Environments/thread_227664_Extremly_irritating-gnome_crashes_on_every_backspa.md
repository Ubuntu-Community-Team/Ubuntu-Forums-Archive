---
title: "Extremly irritating-gnome crashes? on every backspace"
date: 2006-08-02
forum: Desktop Environments
---

### Post by nathandh on 2006-08-02
Since yesterday out of nowhere, if I use backspace in any program under gnome it seems to crash and in less then a second I'm back at the login screen. I think you can imagine how irritating that is for someone who types far from perfection (this is the 4rd time I'm rewriting this topic :)).

I've checked system->preferences->keyboard layout and no logout isn't bined to backspace.

Anyone got any idea? (or anyway u can check for sure it isn't bined to logout by anything else)

Nathan

---

### Post by Blairboy on 2006-08-02
Can you log in as another user and see if it happens then too?

---

### Post by nathandh on 2006-08-02
This doesn't happen with other users indeed. But i'm still clueless about what causes this and how to fix it cause it kinda drives you crazy getting logedout every few min.

---

### Post by Lord Illidan on 2006-08-02
Are you using XGL?

---

### Post by nathandh on 2006-08-02
Yes I'm infact, recently installed it. Right before the problem occured actually. Didn't think it would be related to xgl/compiz.

---

### Post by nathandh on 2006-08-02
So seems like its realated to compiz/xgl, anyone got an idea how to fix it then?

---

### Post by h00s on 2006-08-02
I have the same problem and this solved it:
Run this from terminal:

xmodmap /usr/share/xmodmap/xmodmap.[lang]

where [lang] is language.
Example:
xmodmap /usr/share/xmodmap/xmodmap.us

---

### Post by nathandh on 2006-08-02
Thanks alot, really really appriciated =)

---

### Post by h00s on 2006-08-02
I'm glad I could help :-D

---

