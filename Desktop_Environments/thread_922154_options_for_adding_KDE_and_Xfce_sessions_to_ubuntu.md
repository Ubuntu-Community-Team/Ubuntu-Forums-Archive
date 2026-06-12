---
title: "options for adding KDE and Xfce sessions to ubuntu"
date: 2008-09-17
forum: Desktop Environments
---

### Post by pjizz on 2008-09-17
hi all,

i was wondering about switching to KDE or Xfce to see how they compared, but i ran into several ways to go about this.  basically, i've read that there are three commands.

1) apt-get install kubuntu-dekstop
2) apt-get isntall kde4-core
3) apt-get install kde

(i'm not sure about the 3rd one...I know I found a third option the other day but can't seem to find it anymore)

anyways, so is there any difference between these commands?  could someone explain the difference?

thanks,


pjizz

---

### Post by Bucky Ball on 2008-09-17
Option 1 is what you want. At login you should then be able to select kde in sessions. You will need to add 'sudo' to that command or find it in Synaptics from the desktop.

---

### Post by pjizz on 2008-09-17
okay...still, is there much of an effective difference here?  the curiousity is killing me inside...

---

### Post by SkonesMickLoud on 2008-09-17
> **pjizz said:**
> hi all,

i was wondering about switching to KDE or Xfce to see how they compared, but i ran into several ways to go about this.  basically, i've read that there are three commands.

1) apt-get install kubuntu-dekstop
2) apt-get isntall kde4-core
3) apt-get install kde

(i'm not sure about the 3rd one...I know I found a third option the other day but can't seem to find it anymore)

anyways, so is there any difference between these commands?  could someone explain the difference?

thanks,


pjizz

You don't need to "switch" to any of them.  You can have all 3 available in the same install.  You just have to select them through the login screen.

For KDE:

```
sudo aptitude install kubuntu-desktop
```

XFCE:

```
sudo aptitude install xubuntu-desktop
```

Aptitude is better for something like this as it makes it much easier to remove them if you don't like them.  Just replace "install" with "remove".

"kde4-core" will install KDE4, rather than KDE 3.5

---

### Post by pjizz on 2008-09-17
so... install kubuntu-desktop still points to 3.5, and you have to specify install kde4-core to get the newer version?

is anyone familiar with the third option...did i get that right?

---

### Post by Bucky Ball on 2008-09-17
> **pjizz said:**
> okay...still, is there much of an effective difference here?  the curiousity is killing me inside...

Why don't you go ahead and give it a go and find out??? ;)

I currently have Gnome, KDE4, IceWM, Xfce and Openbox available in my 'Sessions' menu at login.

apt-get what you want, logout then at login, go to sessions and whatever you have installed should be an option in there. 'Change session' (you can do this for 'this session' or 'permanently') and go for it!

Some are a bit different (Xubuntu and Ubuntu), some have a very different look (KDE and Gnome) and some are a radically different approach (IceWM and Openbox). Software packages can be different from one to the other, artwork and themes usually are (from not much to radically different again).

Enjoy! :)

---

