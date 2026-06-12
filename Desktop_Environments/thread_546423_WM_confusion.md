---
title: "WM confusion?"
date: 2007-09-08
forum: Desktop Environments
---

### Post by gloomer on 2007-09-08
If Gnome and Beryl can exist together, then how come Fluxbox and Beryl cannot exist together?

Gnome is a windows manager, and so is Beryl. 

They seem to get along fine in Fiest,. so how come Fluxbox and Beryl can't get along?

---

### Post by mcduck on 2007-09-08
The thing is that Fluxbox and Beryl are both window managers, while Gnome is a desktop environment. The window manager used in Gnome is Metacity.

---

### Post by gloomer on 2007-09-08
Then what's the desktop manager in Fluxbox?

What's the difference between a windows manager and a desktop environment?

So Beryl is used instead of Metacity for Fiesty?

---

### Post by ppietryga on 2007-09-08
Think of it as of layers.
There are these layers when talking about windowing system in linux (and not only linux):
1. x server - it is responsible for knowing what it want to draw
2. windows manager - it is responsible for knowing how to draw the windows and their decorations (border, close button, etc.)
3. desktop environment - it is responsible for provideing the user with the feeling of completeness of the graphical inteface.

In default ubuntu install these layers are:
 - xorg
 - metacity
 - gnome
If you have desktop special effect like wobbly windows enabled these layers are:
 - xorg
 - beryl
 - gnome.
But if you use fluxbox as a window manager, there is no desktop environment on top of it:
 - xorg
 - fluxbox.
That's how it worked years ago, when nobody thought of Gnome, KDE or XFCE :)

---

### Post by RedSquirrel on 2007-09-09
> **gloomer said:**
> Then what's the desktop manager in Fluxbox?

The idea with Fluxbox is that if you want a lot of *desktop-like* functionality you generally have to use separate programs to achieve it.

For example, with Fluxbox alone you can't have desktop icons, but you can use rox-filer, fbdesk, idesk etc. for that.

Some more examples of separate programs that people like to use:

- fbpanel
- fbpager
- conky, gkrellm
- adesklets

One way to find out about interesting programs is to look at screenshots and ask their creators what programs they use (e.g., what the *heck* is that thing in the top-right corner?...:)).

This thread often has some nice screenshots:

[http://ubuntuforums.org/showthread.php?t=539991](http://ubuntuforums.org/showthread.php?t=539991)

---

