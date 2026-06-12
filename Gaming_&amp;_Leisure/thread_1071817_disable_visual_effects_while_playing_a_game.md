---
title: "disable visual effects while playing a game"
date: 2009-02-16
forum: Gaming &amp; Leisure
---

### Post by sinukas on 2009-02-16
Hi, I have shell script I am using to start Enemy Territory on my Ubuntu 8.10 x64 box. However if I have the compiz functionality enabled my ET is very slow and laggy, but if I have it turned off it works really well. Is there a way for me to temporarily disable compiz in a shell script so that I can play ET and not have it lag, but enjoy compiz when not gaming?

If someone could help point me in the right direction I would really appreciate it. Thank you in advance.

---

### Post by Dizzle7677 on 2009-02-16
You could install Fusion-icon for easy switching from Compiz<->Metacity(no glx effects desktop). It's in synaptic. Make sure to run it as a Session startup also.

---

### Post by sinukas on 2009-02-16
Thanks, that was exactly what I was looking for!

---

### Post by grossaffe on 2009-02-16
can't you just make a line in your shell script to disable compiz?
```

metacity --replace

```

---

### Post by crazyfuturamanoob on 2009-02-17
How about compiz-switch?

Or maybe make a hotkey for it or remap a useless extra button from your keyboard to do it?

---

### Post by Polygon on 2009-02-17
compiz just really needs smart handling of this. Vista has this down really well. whenever you play a game, it turns off aero (all the transparancy goes to a single color) while your playing the game, and when the program exits it just turns it back on again. And yes, you heard right. microsoft had a great idea.

---

