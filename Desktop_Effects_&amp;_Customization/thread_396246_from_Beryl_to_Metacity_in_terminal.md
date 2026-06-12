---
title: "from Beryl to Metacity in terminal?"
date: 2007-03-29
forum: Desktop Effects &amp; Customization
---

### Post by sveard on 2007-03-29
Hi all,

Is there a way to switch from beryl to metacity or from metacity to beryl in the terminal, so that I won't have to right-click the beryl-manager icon > Select Window Manager?

I've searched the beryl forums but I can't seem to find it. I hope there's such an option though.

---

### Post by 23meg on 2007-03-29
```
metacity --replace
```will give you Metacity. I don't know if Beryl has the same option but give it a try.

---

### Post by NikoC on 2007-03-29
Beryl also has that option.

---

### Post by 23meg on 2007-03-29
Good, so you can also write a script that detects which one is running, and switches between them. Take a look at [this]("http://www.ubuntuforums.org/showthread.php?t=57259") for a start; if you're interested and can't figure out how, let me know.

---

