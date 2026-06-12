---
title: "Can I Add New Desklets"
date: 2005-01-22
forum: Desktop Environments
---

### Post by Sapper2ID on 2005-01-22
Can these be added like new themes? I would like to put an active weather radar map on my desktop (just for the fun of it).

---

### Post by Dissonance on 2005-01-22
[QUOTE=Sapper2ID]Can these be added like new themes? I would like to put an active weather radar map on my desktop (just for the fun of it).[/QUOTE]
 I read a tutorial on how to do this a few days back.  I have a dock on mine.  (think OSX style.  :) )

---

### Post by tjz on 2005-01-23
Can you write how got that dock?

---

### Post by jensyt on 2005-01-23
[QUOTE=tjz]Can you write how got that dock?[/QUOTE]
If you're using gDesklets, you can just find and install the "StarterBar" desklet. Shouldn't be too hard to find on the [gDesklet website](http://gdesklets.gnomedesktop.org/).

EDIT: [Here's a direct link to that desklet, permitted that's what you're talking about.](http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=210)

---

### Post by scotty on 2005-01-23
Is this something that can be apt-get -ed or something that needs to be compiled?  Or is it an installer?

As of now my warty setup cannot compile anything as that part of the OS was never installed.

I altered my sources.list to do hoary's repositories and now when I synaptic for gdesklets a lot of stuff gets installed, removed, AND upgraded.  Some of it seems contradictory.  I am afraid that I am going to mess up my Gnome install.

Scott

---

### Post by jensyt on 2005-01-23
[QUOTE=scotty]Is this something that can be apt-get -ed or something that needs to be compiled?  Or is it an installer?

As of now my warty setup cannot compile anything as that part of the OS was never installed.

I altered my sources.list to do hoary's repositories and now when I synaptic for gdesklets a lot of stuff gets installed, removed, AND upgraded.  Some of it seems contradictory.  I am afraid that I am going to mess up my Gnome install.

Scott[/QUOTE]
You should be able to sudo apt-get install gdesklets gdesklets-data

But I'd ask someone else when it comes to dependency problems/conflicting software.

---

### Post by scotty on 2005-01-23
Done Done and Done...

It can't easily be done through synaptic.  I made sure that all of the things that apt-get was complaining about was in the initial apt-get install command.  Again, it wanted many many things, but it worked out in the end.  I think that a lot of things came from the hoary repositories.

Is there a CLI command that I can use to determine what version of Gnome I am running right now?  The menus have changed dramatically.

The gdesklets are sweet though.  Just like OS X.

Scott

---

### Post by Sapper2ID on 2005-01-24
This puts me on the right track, thanks

---

