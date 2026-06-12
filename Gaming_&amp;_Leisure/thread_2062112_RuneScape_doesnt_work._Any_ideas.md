---
title: "RuneScape doesnt work. Any ideas?"
date: 2012-09-24
forum: Gaming &amp; Leisure
---

### Post by Zilw3 on 2012-09-24
Hey there. Im very new to linux system and atm im having problem with launching online game RuneScape.  When i enter its website, everything is ok. But when i enter log in, i get black screen with "video loading" message and when this message dissapears, blackscreen still remains. I wonder if someone could help me with this problem?

---

### Post by vandorjw on 2012-09-24
I re-read your post, and java-plugins are not the problem. It might be a video driver issue.
Please open up a terminal and run

```

lspci | grep VGA

```

as well as
```

glxinfo | grep OpenGL

```

as well as
```

glxinfo | grep rendering

```

post your results below.

This is odd:
Runescape black-screens for myself as well, after loading the advertisement.

---

### Post by Zilw3 on 2012-09-24
> **cc7gir said:**
> I re-read your post, and java-plugins are not the problem. It might be a video driver issue.
Please open up a terminal and run

```

lspci | grep VGA

```as well as
```

glxinfo | grep OpenGL

```as well as
```

glxinfo | grep rendering

```post your results below.

This is odd:
Runescape black-screens for myself as well, after loading the advertisement.

this is what i get 
vartotojas@vartotojas-Aspire-5738:~$ lspci | grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV710 [Mobility Radeon HD 4500/5100 Series]
vartotojas@vartotojas-Aspire-5738:~$ glxinfo | grep OpenGL
OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD RV710
OpenGL version string: 2.1 Mesa 8.0.2
OpenGL shading language version string: 1.20
OpenGL extensions:
vartotojas@vartotojas-Aspire-5738:~$ glxinfo | grep rendering
direct rendering: Yes

---

