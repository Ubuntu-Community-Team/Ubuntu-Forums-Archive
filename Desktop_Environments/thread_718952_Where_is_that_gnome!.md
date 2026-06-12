---
title: "Where is that gnome?!"
date: 2008-03-08
forum: Desktop Environments
---

### Post by Aaron_Griffiths_92 on 2008-03-08
Hi, I recently installed linux and i want to install themes, i have seen guides for gnome, but nether do i know how to find it or even install it, i downloaded beryl... couldnt install it i dont know how, so basically i need to know where to find gnome and exactly how I install it... thanks

---

### Post by jose158 on 2008-03-08
I don't think you quite understand. Gnome is not like beryl. Taken from the gnome website: "GNOME is [Free Software]("http://www.gnu.org/philosophy/free-sw.html") and part of the GNU project, dedicated to giving users and developers the ultimate level of control over their desktops, their software, and their data. Find out more about the GNU project and Free Software at [gnu.org]("http://www.gnu.org/")."
 It is not something you install...

---

### Post by jken146 on 2008-03-08
If you have installed Ubuntu (not Kubuntu or Xubuntu) then you are already using GNOME.  [http://en.wikipedia.org/wiki/GNOME](http://en.wikipedia.org/wiki/GNOME) explains what GNOME is.

If you want to theme GNOME, visit [http://gnome-look.org](http://gnome-look.org) and download some themes.  Then open up System -> Preferences -> Appearance and click on the themes tab.  Drag the files you downloaded into that window (no need to extract them first).


As for beryl, that has merged with compiz and is now known as compiz-fusion, which is already enabled in Ubuntu 7.10.  To get the extra features (the rotating cube, fire on the screen, etc.) you need to install the package **compizconfig-settings-manager** -- this can be done in Applications -> Add/Remove, in System -> Preferences -> Synaptic or by typing in a terminal ```
sudo aptitude install compizconfig-settings-manager
```
Then go to System -> Preferences -> Advanced Desktop Effects and enable the features you want.

---

### Post by Aaron_Griffiths_92 on 2008-03-08
tried it.... says wrong filetype

---

### Post by jken146 on 2008-03-08
What did you download?  Can you post a link?

---

### Post by Aaron_Griffiths_92 on 2008-03-08
yeh let me find link, basically the file was a .emerald and if i tried to drag it to where you said or double click it it would give me a message saying the filetype is wrong, also could you send me  a link to one which should work?

---

### Post by Aaron_Griffiths_92 on 2008-03-08
[http://gnome-look.org/content/show.php/Gray+Dark+Ice+Emerald+Theme?content=73173](http://gnome-look.org/content/show.php/Gray+Dark+Ice+Emerald+Theme?content=73173)

---

### Post by jken146 on 2008-03-08
Ah, OK, .emerald themes are themes for Emerald, which is a window decorator and does more things than the standard GNOME window decorator (metacity).  You'll have to install Emerald first.  ```
sudo aptitude install emerald
```
Then ```
emerald --replace
```
Then go to System -> Preferences -> Emerald and add the theme using that program.

The instructions I gave you earlier work for gtk themes.

---

### Post by Aaron_Griffiths_92 on 2008-03-08
Thank you very much, this is a very helpful community, hey with ubuntu who needs windows and gates
:guitar:

---

