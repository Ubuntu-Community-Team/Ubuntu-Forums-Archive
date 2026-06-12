---
title: "Beryl starts but nothing happens."
date: 2007-03-15
forum: Desktop Effects &amp; Customization
---

### Post by ech on 2007-03-15
Okay..I have beryl installed I see the lil red emerald on the screen...I also have my drivers installed for my Nvidia 440go I thought I did it correctly but it seems I havent. Because when I run beryl nothing happens. Whats the problem?


I understand that this program is in still in the beta stages. So I want to ask another question....are there any other programs that are kinda similar to beryl that I can install and that is stable? This should keep me happy until a more stable version of it comes out.


My info:

Dell Inspiron 8200
Nvidia GeForce 44go

---

### Post by kevinf311 on 2007-03-16
Just a thought, but did you click on the Beryl icon and select Beryl as your window manager? It may default to the metacity/kwin window manager.

---

### Post by shanepardue on 2007-03-16
trying copying and pasting the following into a terminal...
```
glxinfo | less
```

Do you see "yes" next to direct rendering or a "no"?

I feel Beryl is very stable actually.

---

### Post by svenole on 2007-03-16
> **kevinf311 said:**
> Just a thought, but did you click on the Beryl icon and select Beryl as your window manager? It may default to the metacity/kwin window manager.

This icon has disappeared on my system and it's not in the add to panel menu. Any clues?

---

### Post by shanepardue on 2007-03-16
to run beryl-manager (the tray program), type alt-f2 to bring up the run dialog and type beryl-manager then enter.

You can make it autostart upon login by adding it to startup programs under system > preferences > sessions.

---

### Post by ech on 2007-03-17
> **shanepardue said:**
> trying copying and pasting the following into a terminal...
```
glxinfo | less
```

Do you see "yes" next to direct rendering or a "no"?

I feel Beryl is very stable actually.


Yes. It does say yes.

---

### Post by ech on 2007-03-17
> **kevinf311 said:**
> Just a thought, but did you click on the Beryl icon and select Beryl as your window manager? It may default to the metacity/kwin window manager.

Okay I did that..It was on metacity but when I choose beryl it tured my screen all messed up and green and purble. :( I had to restart.

---

