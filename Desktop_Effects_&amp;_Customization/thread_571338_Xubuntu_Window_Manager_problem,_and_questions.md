---
title: "Xubuntu Window Manager problem, and questions"
date: 2007-10-09
forum: Desktop Effects &amp; Customization
---

### Post by cuervo_jones_85 on 2007-10-09
I've recently installed xubuntu-desktop in my ubuntu and intend to migrate. I do have some problems however:

1 - I can't select the window manager item in the Settings Manager it says "These settings cannot work with your current window manager". What do do here?

2- I've replacede gnome-system-tools for xubuntu-system-tools... what's the difference between them?

3- Can i completely remove gnome desktop and still run gnome apps?

---

### Post by Forlong on 2007-10-09
> **cuervo_jones_85 said:**
> 1 - I can't select the window manager item in the Settings Manager it says "These settings cannot work with your current window manager". What do do here?
If you want to use Compiz/Beryl, that's normal. If not, run
```
xfwm4 --replace
```
> **cuervo_jones_85 said:**
> 3- Can i completely remove gnome desktop and still run gnome apps?
Well, not completely obviously. GNOME apps need GNOME dependencies.
But if you are referring to GTK apps then the answer is yes.

---

### Post by PGScooter on 2008-03-02
[QUOTE=Forlong;3502252]If you want to use Compiz/Beryl, that's normal. If not, run
```
xfwm4 --replace
```

thanks Forlong! I had a very similar problem, and this simple code worked for me. I think it was from left-over compiz stuff.

---

