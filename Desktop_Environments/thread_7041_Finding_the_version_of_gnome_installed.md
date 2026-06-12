---
title: "Finding the version of gnome installed"
date: 2004-12-03
forum: Desktop Environments
---

### Post by 2fargon on 2004-12-03
1. How do I find out what version of gnome is installed on my computer?

2. I tried searching for gnome in synaptic, and though there are a lot of results, there seems to be no basic "gnome" entry. In other words there is gnome-foo and gnome-bar but no gnome. Why is this so?

3. What is the difference between gnome and gnome2 (I find these often when I search for gnome related stuff) ?

4. I find it irritating that I cannot make the "Applications Computer" menu in the panel transparent. Can someone please point me out to a resource which explains how gnome generates the menus, and how I can create a custom "Menu Bar" (I beleive that is the term for the "Applications Computer" thingy on the panel) ?

Yes, if someone can point me to a resource that tells me how gnome goes about it's business, building the bar etc, that would be just great.

---

### Post by astoltz on 2004-12-03
[QUOTE=2fargon]1. How do I find out what version of gnome is installed on my computer?[/QUOTE]

Right-click on a gnome panel and pick "About gnome".

[QUOTE=2fargon]4. I find it irritating that I cannot make the "Applications Computer" menu in the panel transparent. Can someone please point me out to a resource which explains how gnome generates the menus, and how I can create a custom "Menu Bar" (I beleive that is the term for the "Applications Computer" thingy on the panel) ?[/QUOTE]

Yeah, I'm bugged by this too and I haven't found a way to do it.  But if you get rid of that panel item and replace it with the Main Menu, it has a transparent background.  There are some things that are on the "Applications Computer" menu that aren't on the Main Menu so you might have to do a little more customization, but you should be able to get a *mostly* transparent panel.

---

### Post by 2fargon on 2004-12-03
[QUOTE=astoltz]Right-click on a gnome panel and pick "About gnome".
[/QUOTE]
That was counter-intuitive, for me. I clicked on the Applications menu, and got an "About Ubuntu" the first time around. Thanks a lot for the info :)
[QUOTE=astoltz]
Yeah, I'm bugged by this too and I haven't found a way to do it.  But if you get rid of that panel item and replace it with the Main Menu, it has a transparent background.  There are some things that are on the "Applications Computer" menu that aren't on the Main Menu so you might have to do a little more customization, but you should be able to get a *mostly* transparent panel.[/QUOTE]

That is the other thing -- I cannot right-click on any of the items in the Computer Menu to see what their properties are, so I can mimic them. 

I would be willing to spend some time trying to replicate the Menu Bar, this time, with a transparent background, or edit the Main Menu to replicate the Menu Bar, if only I knew how Gnome works, if you see what I mean.

Any answers to the other two questions will be appreciated :)

Thanks a lot, at least I know the version now.

---

### Post by astoltz on 2004-12-03
[QUOTE=2fargon]
That is the other thing -- I cannot right-click on any of the items in the Computer Menu to see what their properties are, so I can mimic them. [/QUOTE]

Get set for some more counter-intuitive-ness.  The right-click thing only works on menu items that don't have any lower-level "children".  If you drill down 'till you get to an entry like that, the right-click menu has some useful stuff.  Including a "properties" dialog and an entry for "entire menu" that has some more useful things.  It takes some playing.

One other thing.  If you open a nautilus window and type "applications:///" in the location bar, you'll get to gnome's menu structure (for the current user).  I've not played around with this at all so I can't say what happens when you move stuff around using this interface.  Good luck...

---

### Post by 2fargon on 2004-12-03
I guess there is no way I can have a transparent panel, leave alone a transparent background for the Menu Bar!

Gnome is a little painful, for all it's simplicity. This is not a brickbat, just an observation. This is my second attempt at using gnome, and trying to get it to work the way I want, which doesn't seem to be easy, as of now.

---

### Post by calamari on 2004-12-04
In case you still wanted to construct that new applications menu, check out the directory (and subdirectories!) /usr/share/applications in Nautilus.  It has almost everything on the computer menu.  There are a few things it doesn't have, but they are mostly easy to recreate like computer:/// and network:///. 

Jeff

---

