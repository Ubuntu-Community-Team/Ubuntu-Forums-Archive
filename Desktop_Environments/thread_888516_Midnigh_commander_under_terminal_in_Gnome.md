---
title: "Midnigh commander under terminal in Gnome"
date: 2008-08-13
forum: Desktop Environments
---

### Post by lormitto on 2008-08-13
Hi

I am glad that forum like this exists couse it helped my few times in the past.

However I could not find solution for my new problem.

Let's say that i've got two terminals opened. Each of them has Midnight Commander running. I try to edit files. I would like to copy from one window to another but it's impossible. Ctrl+c, Ctrl+v don't work. It would increase speed of my work but still got no idea what to do.

Could you help?

---

### Post by Tim Sharitt on 2008-08-13
I don't know about midnight commander specifically, but in gnome-terminal the copy and paste keyboard shortcuts are Shift+Ctrl+C and Shift+Ctrl+V.

---

### Post by lormitto on 2008-08-13
in fact I am considering moving one part of  text from one window from mcedit to another.

---

### Post by mcduck on 2008-08-14
like said, use shift-ctr-c and shift-ctrl-v, or even better, the linux-style coypaste: just highlight the text you wish to copy and then middle-click to paste it.

---

### Post by lormitto on 2008-08-14
but what to do if I could edit file using mcedit. Copy paste like you wrote works perfectly but i can not use it in mcedit.

---

### Post by Taras Novokhatko on 2008-12-10
try to use "Copy to file(C+f)/Insert file(F15)" - It's a feature of mcedit

---

### Post by Dimath on 2010-11-09
Let me revive this, please, cause nothing really changed since then.

MCEdit from Midnight Commander uses Ctrl+Ins/Shift+Ins to Copy/Past parts of text. For a reason unknown to me, gnome-terminal does not pass these key combinations, as can be seen with ```
showkey -a
```

Since, as I understand, it can not be fixed, may be someone at least knows the reason for that? 

PS: Gnome-terminal shortcuts, like Ctrl+Shift+C, does not work in that case either. Others sometimes suggested ways, like copying with mouse, are not convenient at all. 
This also works fine with other console applications, for example 'konsole'.

---

