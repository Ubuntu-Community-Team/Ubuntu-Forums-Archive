---
title: "How can I get the new default Ubuntu theme on Fedora?"
date: 2010-06-19
forum: Desktop Environments
---

### Post by Max Destruction on 2010-06-19
I had a look around on gnome look (hopless searching skills?) but I couldn't find the ubuntu themes available for download. Anybody know where I can get them? I like the minimize maxamize buttons on the left ...

---

### Post by QIII on 2010-06-20
I don't know that you can find the Ubuntu themes exactly, but I suspect you can move the buttons since Fedora uses GNOME by default.

I'll fire up my machine and let you know what I find.

Edit:  OK.  Here it is.  Just use Ubuntu!

Alright.  Alright.

The following comes with no warranty for any particular use and cannot be guaranteed to work.

```
yum install gconf-editor
``````
gconf-editor
```Expand the apps tab, expand the metacity tab and highlight general.  Look at button_layout.

You will probably see something like "menu:minimize,maximize,close".

(PLEASE!  Don't fiddle around with the button positions this way on your Lucid machine.  This is NOT the preferred method.  There are things brewing at Canonical, and there are other ways to get your buttons moved around using current themes.)

The thing to remember here is that the colon represents center.  What is to the left will be displayed on the left of the window border.  What is to the right, to the right.

So you might want to experiment first with "close,maximize,minimize:menu".

AGAIN:  Don't do this in Lucid.  Things are afoot at Canonical and you don't want to mess things up when those come down.

Come hang out with us on the Debian side once in a while.  Install Ubuntu if you don't have it.

---

