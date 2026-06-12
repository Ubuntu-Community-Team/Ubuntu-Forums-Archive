---
title: "How to make xine pop up for DVDs, instead totem?"
date: 2005-12-10
forum: General Help
---

### Post by ultranet on 2005-12-10
I've seen some mime config files, but don't quite see how they are used.

Thanks.

---

### Post by aysiu on 2005-12-10
System > Preferences > Removable Drives and Media > Multimedia > Video DVD Discs > Command: ```
xine
```

---

### Post by dcstar on 2005-12-11
[QUOTE=aysiu]System > Preferences > Removable Drives and Media > Multimedia > Video DVD Discs > Command: ```
xine
```[/QUOTE]
Should it be "xine %U"??

---

### Post by aysiu on 2005-12-11
[QUOTE=dcstar]Should it be "xine %U"??[/QUOTE] I don't know.

---

### Post by taurus on 2005-12-11
I thought it's

xine %d

---

### Post by doitashimashite on 2005-12-11
or was it:

xine dvd:/

---

### Post by lysis on 2005-12-11
[QUOTE=taurus]I thought it's

xine %d[/QUOTE]
this is the correct method.

---

### Post by doitashimashite on 2005-12-11
[QUOTE=lysis]this is the correct method.[/QUOTE]

It is indeed, for xine it is.

For those using gxine (like me), "gxine dvd:/" is the method.

---

### Post by taurus on 2005-12-11
[QUOTE=lysis]this is the correct method.[/QUOTE]
Thank you.  :)

---

### Post by ultranet on 2005-12-11
I'm using 
xine -u 0 dvd:/

Let's me not have to choose en subtitles all the time. But i wonder if xine can handle en instead of 0. I know mplayer can, but mplayer doesn't have DVD menus...

---

### Post by ultranet on 2005-12-11
[QUOTE=ultranet]I'm using 
xine -u 0 dvd:/

Let's me not have to choose en subtitles all the time. But i wonder if xine can handle en instead of 0. I know mplayer can, but mplayer doesn't have DVD menus...[/QUOTE]
I don't think xine can handle en for subtitles...

---

