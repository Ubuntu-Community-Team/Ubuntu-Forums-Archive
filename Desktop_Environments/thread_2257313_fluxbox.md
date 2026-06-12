---
title: "fluxbox"
date: 2014-12-18
forum: Desktop Environments
---

### Post by trav9595 on 2014-12-18
I tried fluxbox as an alternative faster desktop. It came as a black screen that you right clik on. There is no browser icon. It didnt seem much faster than xfce. Lulu didnt even work...there is no logout and that SUCKS....
how do you get black Fluxbox dressed up with some color and a Firefox???

---

### Post by vasa1 on 2014-12-18
> **trav9595 said:**
> I tried fluxbox as an alternative faster desktop. It came as a black screen that you right clik on. There is no browser icon. It didnt seem much faster than xfce. Lulu didnt even work...there is no logout and that SUCKS....
how do you get black Fluxbox dressed up with some color and a Firefox???
Even I thought that Openbox (close relative of Fluxbox) SUCKS but the real problem was MY inexperience and lack of knowledge. After about a year and a half of reading, experimenting and asking POLITELY, I'm happy.

So if you're still interested in using Fluxbox, please tell people what you started off with and what you did and where you got stuck.

---

### Post by trav9595 on 2014-12-19
dont have a year and a half..

---

### Post by andrew.46 on 2014-12-27
> **trav9595 said:**
> I tried fluxbox as an alternative faster desktop. It came as a black screen that you right clik on. There is no browser icon. It didnt seem much faster than xfce. Lulu didnt even work...there is no logout and that SUCKS.... how do you get black Fluxbox dressed up with some color and a Firefox???

Fluxbox is set from a series of text files in *$HOME/.fluxbox* and the settings there can be pretty minimal depending on how you have installed Fluxbox. A couple of tips:

[LIST=1]
[*]You will find the settings for the menu in *$HOME/.fluxbox/menu* and this is the menu that you see when you right click on the desktop. Edit this with leafpad, gedit, geany or whatever is your favoured text editor.
[*]You can set a background image for the desktop in  *$HOME/.fluxbox/overlay*. My own background image is set in this file as follows:
```

! The following line will prevent styles from setting the background.
! background: none
background: aspect
background.pixmap: /home/andrew/images/flux2.jpg
```
I believe there are several utilities to make this easier but this has always been easy enough for me!
[*]You will probably need a file manager if you do not already have one installed. Try Thunar which has worked for me while using Flux for many years. Maybe your installation already has one installed? It is easy enough to set some key bindings to start your file manager up, settings in *$HOME/.fluxbox/keys*.
[*]Be patient, getting Fluxbox set as you would like it takes some time...
[*]
[/LIST]

Well worth the time and effort to get everything set just right. I would be more than happy to answer further Flux questions, Fluxbox users are not that many and I would like to encourage a new one :)

---

