---
title: "Appearance of gtk applications in kde as root"
date: 2009-03-24
forum: Desktop Environments
---

### Post by Pafrapé on 2009-03-24
I am currently under kubuntu KDE 4.2.

For applications gtk such as firefox, I installed the package gtk-qt-engine with gtk2-engines-qtcurve. It is almost perfect.

But when I use a gtk application as administrator (synaptic), the appearance is ugly, it does not take into account the configuration with gtk-qt-engine and gtk2-engines-qtcurve or otherwise.
I thought if I opened "configuration system" as administrator of the system to adjust it would work, but it is not.

If someone would have the solution ?

---

### Post by Pafrapé on 2009-03-25
Someone ?

---

### Post by Pafrapé on 2009-03-29
Help !

---

### Post by transmition on 2009-03-29
Well, I do not know how to do this Kubuntu, but this is how you would do it under Gnome.

You would have to change the appearance settings for root. Normally, when you were changing your settings, you were doing so under *whatever your username is*. 

So, you must either run the program used to change your settings as root (sudo appearancesettingsprogram) or log in as root and change your settings as you normally would.

---

### Post by Khopstick on 2009-10-04
I'm using kubuntu (jaunty) and had the same problem, too. I found the following to solve the problem:

sudo cp ~/.gtkrc-2.0-kde4 /root/.gtkrc-2.0

That is, you copy your GTK-settings into the /root-directory. Note that the "-kde4" is missing in the root-folder.

Hope that helps,
 Chopstick

---

### Post by felipunk on 2010-04-28
Great that indeed worked as expected! you're great!

---

### Post by Atomic-Fanboy on 2011-10-09
I had exactly the same problem and this did, indeed work. :D

---

