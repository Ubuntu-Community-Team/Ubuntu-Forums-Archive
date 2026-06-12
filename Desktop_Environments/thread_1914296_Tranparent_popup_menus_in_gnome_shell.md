---
title: "Tranparent popup menus in gnome shell?"
date: 2012-01-24
forum: Desktop Environments
---

### Post by Sir Rodness on 2012-01-24
Hello, 

I've been trying to like unity, but its not working for me. I currently really like what gnome shell has to offer, however I wish my popup menus were transparent. With compiz in unity and previous versions of ubuntu it was easy, but gnome shell appears to be keeping this option a secret. Is there a way to give my popup menus some transparency? For me that the only thing left that I'm missing in gnome shell.

---

### Post by sanderd17 on 2012-01-24
What do you mean with popup-menus?

The menus you get when you click on elements in the top bar?

This is all themable. Just take a look at the bunch of themes on DevianArt: [http://gnome-shell.deviantart.com/](http://gnome-shell.deviantart.com/)

---

### Post by Sir Rodness on 2012-01-24
When you right click on the desktop, a file, titlebar. That menu that pops up. Currently there doesn't seem to be a way to add transparency to them. I've been looking, but I haven't seen a theme or procedure in gnome-shell that allows me to manipulate them.

---

### Post by Frogs Hair on 2012-01-24
There are transparent Gnome shell themes , but  they only  include the top panel and the over view . The context menu appearance is controlled by the GTK 3 Theme . The Gnome shell doesn't use Compiz and I don't know of anything comparable .

---

### Post by sanderd17 on 2012-01-24
gtk indeed does not support transparenty. There is a possibility to make entire windows transparent, but I don't know if it's possible to make context menus transparent (i don't know if the context menu is seen as a separate window, and if that is detectable).

Here is a video about such things, mabe, if you trace back the developer, he can help you.
[http://youtu.be/GYP1wMM2N3s](http://youtu.be/GYP1wMM2N3s)

---

### Post by andon21 on 2012-02-23
Requires the compiz opacity plugin and the window class to add is DropdownMenu,you can set the opacity however you like.

---

### Post by Bobhuber on 2012-02-23
You can indeed control windows opacity in gnome 3. Not for popups or menus but really functional in addition to the eye candy.

[http://www.webupd8.org/2011/10/gnome-shell-focus-effects-extension.html](http://www.webupd8.org/2011/10/gnome-shell-focus-effects-extension.html)

---

### Post by Copper Bezel on 2012-02-24
[QUOTE=sanderd17]gtk indeed does not support transparenty. There is a possibility to make entire windows transparent, but I don't know if it's possible to make context menus transparent (i don't know if the context menu is seen as a separate window, and if that is detectable).[/QUOTE]
Just for clarity, despite this being a dead thread: yes, Compiz can detect the difference, since context and drop-down menus constitute their own window class, and as the OP notes, Compiz can easily be set to make all menus transparent (and even blur the background behind them.) I was very disappointed early on that this couldn't be mimicked in Shell (I'd really got attached to the transparent menus!) in any apparent method, although it could probably be managed as an extension.

---

### Post by Sir Rodness on 2012-06-08
Appreciate all the feedback. Still using Gnome Shell since it is my favourite flavour of Ubuntu since it's interface evolution. They are definitely adding more cool extensions as time passes. We'll see what the future holds.

---

