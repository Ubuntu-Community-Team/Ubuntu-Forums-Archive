---
title: "Wanting to try KDE"
date: 2006-01-07
forum: General Help
---

### Post by Jedeye on 2006-01-07
Hi all! I am using ubuntu right now with gnome, but was wanting to try KDE. I know that I could download the iso for kubuntu, but since I allready have a ubuntu base it seems like I should be able to just get the package. 

While I think this can be done, my other question is how to define which desktop is default? and is there a easy way to swith the two.

Thanks!

---

### Post by aysiu on 2006-01-07
Open a terminal and type ```
sudo apt-get update
sudo apt-get install kubuntu-desktop
``` Before saying yes, highlight all the packages to be installed and copy them to a text file--save that text file! Then, say yes. Log out. Click "session." Select KDE. Log in.

If you make KDE in charge of the login manager (KDM), you won't be able to shut down from Gnome. If you make Gnome in charge of your login manager (GDM), you won't be able to shut down from KDE. Either way, you can use KDE or Gnome. GDM will ask if you want to make the selected session the default or not. KDM will just use the last session you used before.

If you decide you don't like KDE, open a terminal and type ```
sudo apt-get remove
``` paste in the copied and pasted text file in and then hit Enter.

You **cannot** simply type ```
sudo apt-get remove kubuntu-desktop
``` This command will do virtually **nothing**.

---

### Post by kingsidy on 2006-01-07
it is pretty easy. after you install kde, when you get to the login screen there, you'll see sessions, you can then select KDE, a window will pop up asking you whether you want to make your default session, then click yes. if you want to change back to gnome, you can do the same thing and just select gnome and make it default. you can either make it default or use it once, your choice

---

### Post by Jedeye on 2006-01-07
Thanks for the tips! looking forward to trying KDE!

---

### Post by lotusleaf on 2006-01-07
If a person using Ubuntu Breezy wants the latest KDE, shouldn't they add the sources from the Kubuntu site?

---

### Post by shroom on 2006-01-07
Hi guys,

I just made a fresh install of Ubuntu and installed Kubuntu on top of it with *apt get install kubuntu-desktop*. I think it's great! I love the theme and all the visual effects. I think it's much prettier than Gnome!

Anybody disagree? Maybe it's possible to make Gnome the same pretty as KDE? I dunno.

---

### Post by gnutux on 2006-01-07
although I love KDE, there are ways to make GNOME "prettier"

gnutux

---

