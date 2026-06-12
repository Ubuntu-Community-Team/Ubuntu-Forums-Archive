---
title: "n64 emulator"
date: 2008-07-29
forum: Gaming &amp; Leisure
---

### Post by jimi_hendrix on 2008-07-29
whats a good n64 emulator i can get and how would i install it (8.04 hardy)

---

### Post by RKCole on 2008-07-29
Hello, jimi_hendrix.

I use [Mupen64Plus]("http://getdeb.net/search.php?keywords=Mupen") which seems to work very well for me.  The link provided is from GetDeb; they have Ubuntu packages for this product there.

Hope this helps.

Take care.

---

### Post by jimi_hendrix on 2008-07-29
thanks

---

### Post by jdenicholls on 2008-07-29
Does Project 64 have a linux version? That was a good emulator I used to use.

---

### Post by jimi_hendrix on 2008-07-29
ive got it on my windows side but i cant find a starfox 64 file that it will run

---

### Post by grossaffe on 2008-07-29
> **jdenicholls said:**
> Does Project 64 have a linux version? That was a good emulator I used to use.

no, but i've heard it works perfectly in WINE.

---

### Post by geekygirl on 2008-07-29
Under Wine you say? Haven't tried it under Wine, and I much prefer Project64 over Mupen.


> **jimi_hendrix said:**
> ive got it on my windows side but i cant find a starfox 64 file that it will run

PM Sent ;)

---

### Post by Dark Aspect on 2008-07-30
Wait?? Whats the difference between [Mupen64]("http://mupen64.emulation64.com/") and [Mupen64Plus]("http://getdeb.net/app/Mupen64Plus")?I have Mupen64 0.5 installed on my computer now,is Mupen64Plus a newer version or something?

---

### Post by GSZX1337 on 2008-07-30
> **Dark Aspect said:**
> Wait?? Whats the difference between [Mupen64]("http://mupen64.emulation64.com/") and [Mupen64Plus]("http://getdeb.net/app/Mupen64Plus")?I have Mupen64 0.5 installed on my computer now,is Mupen64Plus a newer version or something?

[QUOTE="Wikipedia"]Mupen64Plus is a project which aims to improve the Mupen64 0.5 code. Originally it was developed to add a 64-bit recompilation core; however, it was decided soon after its creation that it would become a much larger project.[/QUOTE]

Thou shalt always search Wikipedia before posting on thy forums.

---

### Post by jimi_hendrix on 2008-07-30
when i try to get mupen64plus from getdeb i get "error wrong architecture i386"

---

### Post by Dark Aspect on 2008-07-30
> **GSZX1337 said:**
> Thou shalt always search Wikipedia before posting on thy forums.

:)


> **jimi_hendrix said:**
> when i try to get mupen64plus from getdeb i get "error wrong architecture i386"

Use [Getlibs]("http://ubuntuforums.org/showthread.php?t=474790").

After you install it your want to run:

```
sudo dpkg -i --force-all mupen64plus_1.4-0~getdeb1_i386.deb
```

---

