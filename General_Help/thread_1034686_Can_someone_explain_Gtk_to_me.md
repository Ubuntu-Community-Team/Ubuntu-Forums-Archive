---
title: "Can someone explain Gtk to me??"
date: 2009-01-08
forum: General Help
---

### Post by 3pinner on 2009-01-08
I started poking around for new desktop themes (gnome) and downloaded a couple that need a Gtk engine (?)
Entering Gtk in synaptic returns what looks like several kinds.
So what is Gtk exactly, and which should I choose for my intrepid desktop?
Thanks!

---

### Post by mssever on 2009-01-08
> **3pinner said:**
> I started poking around for new desktop themes (gnome) and downloaded a couple that need a Gtk engine (?)
Entering Gtk in synaptic returns what looks like several kinds.
So what is Gtk exactly, and which should I choose for my intrepid desktop?
Thanks!
Gtk is what draws the various GUI elements on your windows (actually, it's a GUI toolkit, and there are several others in use, most notably Qt for KDE). Some examples of things Gtk draws are buttons, text entry boxes, and even blank space where there's nothing else.

Gtk is themable. All Gtk themes make use of some theme engine. For the themes you downloaded, you'll need to make sure that you've installed the proper theme engine. Try installing and selecting the theme. If it works, you have the necessary theme engine. If not, you'll have to find and install the engine. Simply search for the theme engine's name. It's possible that some theme engines might not be in the repositories. In that case, you'll have to manually find and install it.

---

### Post by hivelocitydd on 2009-01-09
Gtk: At one point, before KDE was substantially complete, Qt antagonists reasoned that since there were more lines of Qt code than of KDE code, it would be better to develop a widget library from scratch--but that is an aside. The Gtk widget library was written especially for gimp (GNU Image Manipulation Program), is GPL'd and written entirely in C in low-level X calls (i.e., without the X Toolkit), object oriented, fast, clean, extensible and having a staggering array of features. It comprises Glib, a library meant to extend standard C, providing higher-level functions usually akin only to scripting languages, like hash tables and lists; Gdk, a wrapper around raw X Library to give GNU naming conventions to X, and to give a slightly higher level interface to X; and the Gtk library itself. Using Gtk, the Gnome project began, analogous to KDE, but written entirely in C. From Rute-Users-Guide

---

