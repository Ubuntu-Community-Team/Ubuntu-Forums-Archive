---
title: "why do the openoffice window looks all garbled up? (Screenshot inside)"
date: 2007-05-20
forum: Desktop Environments
---

### Post by dalert0140 on 2007-05-20
In Xubuntu when I open OpenOffice the window borders look all garbled. Like these:
[IMG]http://inlinethumb14.webshots.com/6221/2150038690101351064S600x600Q85.jpg[/IMG]

Anybody has the same problem or know how to fix it?

---

### Post by RedSquirrel on 2007-05-20
Try installing the openoffice.org-gtk package.

---

### Post by dalert0140 on 2007-05-20
it says its already installed. maybe its the drivers? I have an ati card

---

### Post by BertjeBebo on 2007-05-20
i have the same problem; i use xubuntu feisty on my laptop & installing the openoffice.org-gtk package  (it was already installed and i reinstalled it) does seems to help

---

### Post by RedSquirrel on 2007-05-20
I don't have this issue myself, so I'm not sure what it could be. I've done some research and so far I have not found any really useful suggestions. It might be a video driver issue (?). Which ATI driver are you using? I'm using "ati", but I have an old card.

Not sure if it would help, but maybe you could try running OO with the --widgets-set option:

```
 openoffice --widgets-set gtk
```Another possibility is to run the following command at startup, possibly by placing it in ~/.profile or having Xubuntu run it for you.

```
export OOO_FORCE_DESKTOP=gnome
```


EDIT:

Desktop effects might also cause problems.

---

### Post by BertjeBebo on 2007-05-21
unfortunately none of these solutions are working:(

what do u actually mean with desktop effects? how can i switch them off?

---

### Post by RedSquirrel on 2007-05-21
I haven't used Xubuntu in a while, so I thought maybe there were some new effects (transparency or even fancier things), but they're probably not worth worrying about too much. 

Have you looked at the forums for openoffice? Here's a thread which suggests installing openoffice.org-gtk (which didn't help you) and they also suggest near the bottom that you could change your bit depth from 24 to 16 and see if that helped....

["Garbage" display problems on Xubuntu]("http://www.oooforum.org/forum/viewtopic.phtml?t=55087&highlight=xubuntu")

```
gksudo mousepad /etc/X11/xorg.conf
```In the "Screen" section, there is a line:

```
       DefaultDepth    24
```change it to:

```
       DefaultDepth    16
```

Then logout. At the login screen, press Ctrl-Alt-Backspace, then login.

---

### Post by BertjeBebo on 2007-05-22
thank u very much!!!

---

