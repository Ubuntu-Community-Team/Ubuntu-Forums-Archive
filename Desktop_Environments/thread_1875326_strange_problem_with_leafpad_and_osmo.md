---
title: "strange problem with leafpad and osmo"
date: 2011-11-04
forum: Desktop Environments
---

### Post by stavrosLinux on 2011-11-04
Tried to import a google csv contacts file (greek language). Osmo displays garbage. Then tried to open it with leafpad, the same. Gedit displays it ok.

[http://imagebin.ubuntu-gr.org/1320437629.png]("http://imagebin.ubuntu-gr.org/1320437629.png")

---

### Post by stavrosLinux on 2011-11-05
screenshot

---

### Post by gsmanners on 2011-11-05
In the English version of Leafpad's Open dialog, you would look for a control called Character Coding. You probably need to change that to something (since I'm getting the impression that there's an encoding mismatch there or maybe there's some [weird mark]("http://en.wikipedia.org/wiki/Byte_order_mark") characters are showing up there)

---

### Post by amjjawad on 2011-11-05
> **stavrosLinux said:**
> Tried to import a google csv contacts file (greek language). Osmo displays garbage. Then tried to open it with leafpad, the same. Gedit displays it ok.

[http://imagebin.ubuntu-gr.org/1320437629.png](http://imagebin.ubuntu-gr.org/1320437629.png)

Hi,

I'll ask my Greek Friend to have a look at this. However, please check the other suggestion made earlier :)

Thanks!

P.S.
Check my signature - Lubuntu One Stop Thread. It's very helpful :)

---

### Post by TeoBigusGeekus on 2011-11-05
You could try opening it with geany and go to Document>Set Encoding.
Experiment a bit with different encodings and see what osmo accepts.

---

### Post by amjjawad on 2011-11-05
> **TeoBigusGeekus said:**
> You could try opening it with geany and go to Document>Set Encoding.
Experiment a bit with different encodings and see what osmo accepts.

Thanks my friend :)

---

### Post by TeoBigusGeekus on 2011-11-05
> **amjjawad said:**
> Thanks my friend :)

Anytime mate.

---

### Post by stavrosLinux on 2011-11-06
> **gsmanners said:**
> In the English version of Leafpad's Open dialog, you would look for a control called Character Coding. You probably need to change that to something (since I'm getting the impression that there's an encoding mismatch there or maybe there's some [weird mark]("http://en.wikipedia.org/wiki/Byte_order_mark") characters are showing up there)

So, google exports contacts into google.csv, in UTF-16 little indian.

Osmo and leafpad don't "get it". Tried to change the encoding in leafpad but the result is the same.

I am covering all angles when I move to Lubuntu (from Ubuntu).
Since gedit works, and I dont use osmo, I am ok.

---

### Post by amjjawad on 2011-11-06
> **stavrosLinux said:**
> Since gedit works, and I dont use osmo, I am ok.

You can install "gedit" into Lubuntu :)

It's a pain in the neck. Sometimes, I do have problem with encoding too and stuff.

---

### Post by vasa1 on 2011-11-06
I had a similar problem with leafpad in regular Ubuntu as well. I posted that [here]("http://ubuntuforums.org/showthread.php?t=1841762"). I've stayed with gedit after that.

---

