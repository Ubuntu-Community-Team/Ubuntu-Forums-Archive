---
title: "compiz fusion, emerald theme manager......"
date: 2007-07-26
forum: Desktop Effects &amp; Customization
---

### Post by techno-mole on 2007-07-26
ok, ive installed compiz fusion, and ive also installed the emerald theme manager, now im having some trouble with a couple of things.
problem number one is, how do you set emerald to be the default window manager ? ive read various things and nothing seems to work.
the other things is, i can run emerald --replace from terminal or by doing alt + f2 and typing it, but nothing happens, but if i then do compiz --replace emerald starts working ?
i can do the compiz --replace -c emerald --replace code (you know the one im on about) and add it to sessions (to get it to run at start up) but it doesnt work, although im not bothered about running compiz at start up, i tend to leave it off as im quite likely to be playing a game and dont want it hogging cpu and graphics power.
i do however want the emerald themes to run at start, so how is the best way to do this ?
ive tried running emerald --replace at start up, but no dice.
i did try to change the window manager in gconf editor to emerald, that didnt go to well :)
cheers in advanced for any help.

---

### Post by llln30lll on 2007-07-26
*edit* i replied to the wrong topic lol

---

### Post by crimesaucer on 2007-07-26
> **techno-mole said:**
> ok, ive installed compiz fusion, and ive also installed the emerald theme manager, now im having some trouble with a couple of things.
problem number one is, how do you set emerald to be the default window manager ? ive read various things and nothing seems to work.
the other things is, i can run emerald --replace from terminal or by doing alt + f2 and typing it, but nothing happens, but if i then do compiz --replace emerald starts working ?
i can do the compiz --replace -c emerald --replace code (you know the one im on about) and add it to sessions (to get it to run at start up) but it doesnt work, although im not bothered about running compiz at start up, i tend to leave it off as im quite likely to be playing a game and dont want it hogging cpu and graphics power.
i do however want the emerald themes to run at start, so how is the best way to do this ?
ive tried running emerald --replace at start up, but no dice.
i did try to change the window manager in gconf editor to emerald, that didnt go to well :)
cheers in advanced for any help.

Emerald themes can only work if you have Compiz fusion or Beryl working...otherwise, you have to use your other window themes, for me on Xfce4 xubuntu, it's xfwm4.

Also, if you add:

```
compiz --replace
```

and

```
emerald --replace
```

...to your start up scripts, you will always have Emerald.


...but if you think it effects your games, then you should stick with your other window manager, and use "alt+f2" after start up with this command:

```
compiz --replace -c emerald &
```

---

### Post by atomkarinca on 2007-07-26
you can get compiz fusion icon. with the help of this icon you can easily change your window manager and window decorator.

---

### Post by techno-mole on 2007-07-27
cheers for the advice.
i did try adding the compiz --replace and emerald --replace codes to my start up sessions, but that didnt work, although im not sure why.
the only thing that seems to work is running the 2 codes in alt + f2 , (one after the other) or by doing - compiz --replace -c emerald &
like i said im not bothered about having compiz running from start up, i did hope i could get emerald to run with out compiz, but never mind, i tend to use compiz (as i used beryl) when im writing html or doing a load of things at once, using cube rotation and such is a very handy thing, havent used it with the ring switcher but, that my come in very handy aswell.
i didnt know there was an icon for fusion ? i did have a search for it, but couldnt find anything about it, so if some one could point me in the right direction i would appreciate it.
just out of interest, i read on the compiz website an faq about getting the cube rotation to work, and one way was to install gnome-compiz-manager which like i said was a way to get the cube working, but i noticed that it has a section for the window manager in it, maybe using this would get emerald running with out compiz ? 
cheers again.

*solved* found what i was looking for.

---

### Post by podfish on 2007-08-01
what did you find?

---

### Post by toddncl on 2007-08-02
same problem here, how did you solve this?

Thanks!

---

### Post by japglish on 2007-10-28
OK, I think i did the following: download the gnome-compiz-manger, download emerald and get the GPL themes by downloading them from [http://packages.ubuntu.com/feisty/x11/emerald-themes](http://packages.ubuntu.com/feisty/x11/emerald-themes) and install them - it's a one click install.  Open a terminal window and type emerald --replace & - select one of the emerald themes by opening emerald theme manager.  While the terminal is still open go to system > preferences > GL Desktop.  Click this and let it do whatever it does and you should now be able to close the terminal with the emerald theme remaining.

---

