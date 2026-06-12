---
title: "[SOLVED] Compiz using Metacity Themes"
date: 2008-02-03
forum: Desktop Effects &amp; Customization
---

### Post by KnightOnline on 2008-02-03
Hi Everyone,

I've Been using Compiz fusion for a while and I love all the cool effects that it does. I tried to take it to the next level by installing emerald, but it sucks, no good themes for it at all. 

I want to go back to using the "Human" Metacity theme, but everytime i do "metacity --replace" it goes back to using metacity WITHOUT compiz's effects. And when i enable compiz's effects again, emerald gets loaded again. 

What's the easiest way to get compiz to go back to loading metacity as its windows border manager rather than emerald?

Thanks in advance.

---

### Post by spoilerhead on 2008-02-03
the secret word is

gtk-window-decorator --replace

---

### Post by KnightOnline on 2008-02-03
it worked! Thanks man, would have never figured it out myself :P

---

### Post by citizenc on 2008-03-12
It works, however the setting is not saved if I log out and in.

I tried putting it in .gnomerc but that just stopped Gnome from loading properly.

Ideas?

---

