---
title: "Why does Feisty (aptitude) keep &quot;uninstalling&quot; Xubuntu??"
date: 2007-04-20
forum: Desktop Environments
---

### Post by wilberfan on 2007-04-20
This has happened to me a few times now:  About half-an-hour ago I wanted to try the[ improved font rendering]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_improve_sub-pixel_font_rendering_for_Feisty") for Feisty, and as soon as I did my "sudo aptitude install...", it told me that all my Xubuntu packages were "unused" and would be uninstalled...

Is there a way to prevent this from happening?   (It's pretty easy to re-install Xubuntu-desktop--but it's annoying to have to do that again and again...)

---

### Post by mcduck on 2007-04-21
Aptitude can act a bit strange sometimes. You could just use apt-get instead..

---

### Post by aysiu on 2007-04-21
Yes. If you're using Edgy or Feisty, *apt-get* is a better choice. *aptitude* can sometimes be a little overzealous--too "smart" for its own good.

---

### Post by wilberfan on 2007-04-21
Good to know--I appreciate that..  

Although wasn't it YOUR website that encouraged me to use "aptitude" in the first place, Aysiu?  ;)

---

### Post by aysiu on 2007-04-21
> **wilberfan said:**
> Good to know--I appreciate that..  

Although wasn't it YOUR website that encouraged me to use "aptitude" in the first place, Aysiu?  ;)
Yeah, but things have changed, and I've since updated that page.

With the advent of *autoremove* in *apt-get*, *aptitude* is a lot less appealing.

---

