---
title: "How to add programs to Applications?"
date: 2010-06-07
forum: Desktop Environments
---

### Post by fopetesl on 2010-06-07
I have recently installed (& updated) Lucid.
I have also downloaded & installed GNUstep and Beagle.
How do I add these launchers to Applications->Programming, etc?

I know the launchers are all in /usr/share/applications but there must be an easier way than editing a new .desktop file by hand?

Have RTFM and Googled but nothing indicates how to do this.:(

---

### Post by Breambutt on 2010-06-07
System > Pref > Main Menu

---

### Post by an0dos on 2010-06-07
right-click on the ubuntu icon and click on "Edit Menus"?

---

### Post by fopetesl on 2010-06-07
Ah! Thanks, guys.
Just about what I wanted but not quite.
Bad syntax on my part. :(
What I meant was if, say, using Synaptic to install a program is there an automagic way of getting its launcher added to Applications?

For example I downloaded Beagle but it's not clear which of the beagle-* apps to run. 
OK. OK. I give in - I'll RTFM :)

---

### Post by Breambutt on 2010-06-07
I wouldn't necessarily recommend installing complete software bundles from Synaptic, it's handier with individual packages and the like. You might even get more lucky menu item -wise by installing from the terminal / software center.

I'm guessing the problem is that the program class isn't pre-defined when it comes to less popular software.

---

### Post by fopetesl on 2010-06-07
Edit: GNUstep **is** there but it's named "ProjectCenter". Yay! :)
Learning something everyday :P

However Beagle isn't.  It **is** in [COLOR="Blue"]/usr/share/applications[/COLOR] as [COLOR="Blue"]beagle-search.desktop[/COLOR] but it doesn't show up in Applications.

I looked at the syntax in [COLOR="Blue"]beagle-search.desktop[/COLOR] and it compares well with [COLOR="Blue"]blender-fullscreen.desktop[/COLOR], i.e. I couldn't see any obvious syntax error(s).

Do I have to initialise something first?

---

