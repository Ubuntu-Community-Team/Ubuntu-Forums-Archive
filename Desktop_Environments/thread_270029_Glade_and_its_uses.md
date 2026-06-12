---
title: "Glade and its uses"
date: 2006-10-02
forum: Desktop Environments
---

### Post by elpuerco on 2006-10-02
Bouncing about the web etc etc and have now come across Glade and tried a tutorial but came up against a few problems and hope someone can explain please?

I am running Kubuntu so will Glade applications I write work for me?

I followed this tutorial which I think is very good:

[http://www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/](http://www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/)

The application ran OK, but only while Glade was running?

When I typed ./pyHelloWorld.py nothing happened and the prompt returned?

Does this mean Glade has to be running for these application to run?

Thnx

---

### Post by ardchoille on 2006-10-02
Going from memory on this and it's been a while since I did it, so keep that in mind.

Glade is used for creating the gui for gnome/GTK apps, the code can be written in a number of languages including python, ruby, C, C++ etc. The KDE side uses qt/tkinter, not sure what the code is written in. If you want to develop KDE apps, have a look at kdevelop or qt.

I use Anjuta as my IDE when writing gnome/GTK apps. Anjuta integrates gnome-iconedit and glade all from the Anjuta IDE.

If you write gnome/GTK apps, they should work fine in KDE and apps designed in qt or kdevelop should run fine in gnome, so your apps should work fine regardless of your choice of desktop.

---

