---
title: "Xfce 4 Rox ??"
date: 2005-06-12
forum: Desktop Environments
---

### Post by Digitallysick on 2005-06-12
Where do i find Rox for Xfce? I want to put icons on my desktop and turn my taskbar into just icons, also i have seen desktops with a transparent meter like this [Look at this desktop! i want mine like this!](http://photos14.flickr.com/18913585_a9a6575feb.jpg)

---

### Post by gil-galad on 2005-06-12
Well the repository has rox filer, but none of the other stuff.  Check on the site to see if you can figure out how to install it 
[http://rox.sourceforge.net/phpwiki/](http://rox.sourceforge.net/phpwiki/)  

I wish I used rox so I could help you out more ;)

---

### Post by jhk on 2005-06-12
Are you sure that you're looking at a ROX desktop?  That iconbar/taskbar seems like it's the enlightenment project's engage to me, or maybe a type of gdesklets or karamba display.

To get a transparent terminal, you can either try facy xorg extensions which would provide true transparency, or something like Eterm, which merely displays your background image, which is a kind of fake but much easier to use transparancy.   I use Eterm in such a way, and it's pretty nifty.  I can't tell what type of terminal they're running, but it well might be Eterm.

Hope this helps!

---

### Post by az on 2005-06-12
[QUOTE=Digitallysick]Where do i find Rox for Xfce? I want to put icons on my desktop and turn my taskbar into just icons, also i have seen desktops with a transparent meter like this [Look at this desktop! i want mine like this!](http://photos14.flickr.com/18913585_a9a6575feb.jpg)[/QUOTE]

[http://packages.ubuntu.com/hoary/x11/rox-filer](http://packages.ubuntu.com/hoary/x11/rox-filer)
It is in universe.


Start it with 
rox -p=1
to use the pinboard option.

---

### Post by bored2k on 2005-06-12
[QUOTE=azz][http://packages.ubuntu.com/hoary/x11/rox-filer](http://packages.ubuntu.com/hoary/x11/rox-filer)
It is in universe.


Start it with 
rox -p=1
to use the pinboard option.[/QUOTE]
 I have never understood this. What's the "pinboard option" ?

---

### Post by gil-galad on 2005-06-12
it allows you to put icons on the desktop.  Like nautilus.

---

### Post by bored2k on 2005-06-12
[QUOTE=gil-galad]it allows you to put icons on the desktop.  Like nautilus.[/QUOTE]
 Ok thanks. I thought I was missing this uber awsome feature ;) (I don't use the desktop, at all.).

---

### Post by az on 2005-06-12
The pinboard takes over your desktop background.  When you use Icewm or fluxbox, you need to enable the "send clicks to window manager".

Everything on the pinboard is a symbolic link.

---

