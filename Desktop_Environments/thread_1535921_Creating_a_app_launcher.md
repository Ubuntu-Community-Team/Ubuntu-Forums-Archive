---
title: "Creating a app launcher"
date: 2010-07-21
forum: Desktop Environments
---

### Post by sarcasmrules on 2010-07-21
I am trying to make an app launcher for Ubuntu which replaces the top bar (default) in gnome. It will be a menu system in the middle of the screen which you would click on parts to bring up lists of apps and locations. What would be the easiest way to do this, and in which code? Thanks!

---

### Post by cliffdodger on 2010-07-21
Well "the panel" essentially is an app laucnher already and a very customizable one at that. It's unlikely you should need to code any special panel yourself and unless you're experience with Linux dev and have a lot of time I wouldn't (but if you had to - use QT or GTK+ or GLADE for your GUI toolkit and do the underlying code in C++ via g++)

I believe you can simply right click on the existing panel and begin to customize it or 'create a new panel' and pick exactly what goes on it and where it goes on the screen. You can move and probably disable (at your own peril) the existing panel if you choose.

---

### Post by sarcasmrules on 2010-07-26
Thanks a lot I will post what the finished app launcher looks like.

---

