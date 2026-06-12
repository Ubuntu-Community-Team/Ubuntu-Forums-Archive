---
title: "Can't change the size of certain icons in Human theme"
date: 2007-06-16
forum: Desktop Environments
---

### Post by Rahl on 2007-06-16
I have seen this being asked before, but I somehow can't find a working solution.

I am using Feisty with the default GNOME desktop and the default Human theme.

I want those icons in the main menu on the panel, those in the toolbars of various apps, those on the buttons in various dialogs, to get smaller, say 16x16. 

Apps which have their own means of customising this, such as Firefox, are okay. Non-GNOME apps, such as OpenOffice or Eclipse, allready have 16x16 icons in their toolbars, means they are also okay. 

But the regular GNOME apps such as Nautilus, gedit and the like, they stubbornly keep 24x24 icons in their toolbars and on the buttons of their dialogs no matter what I do.

Setting gtk-icon-sizes in ~/.gtkrc-2.0 did the trick in Edgy, but not in Feisty. While other things in ~/.gtkrc-2.0 seem to be respected, gtk-icons-sizes is being ignored.

Is there a way to make these icons smaller other than recreating the theme?

---

### Post by HeavyAl on 2007-06-18
"BUMP"

Yeah, I'm looking for this too .. I found this info in the gnome support forums:

----
In the begining of GTKRC include this:

gtk-icon-sizes = "panel-menu=24,24:gtk-menu=24,24:panel=24,24"
#Include next line end of the first line...
#:gtk-large-toolbar=XX,XX:gtk-small-toolbar=XX,XX"
XX= your choice...
----

But couldn't find an actual gtkrc only file - the one I found say .gtkrc1.2-gnome2 and uses an include that says to include ~/.gtkrc.mine so I created that file and inserted the above stuff (adding the 16x16 as the large/small toolbar stuff) with no noticeable changes in the toolbars. 

This is annoying because I use a laptop with only 1024x768 and the icons just take up way too much room when I'm working in gtk based editors.

Anyone know a fix for this?

---

### Post by lee_connell on 2007-06-21
I'm interested in this as well.

---

### Post by HeavyAl on 2007-06-22
As it turns out, .gtkrc and .gtkrc-2.0 do the trick - for me at least. I'm not sure why this doesn't work for Rahl. I guess it's one of those situations where the acronym YMMV actually applies! Anyway, to get to the point ..

It appears you only really need to make this modification in .gtkrc-2.0 in you home directory, but I've tried it on three different systems now and on two of them I also had to modify the .gtkrc file as well, so try it one way then the other and just see what works. Specifically you want to add this line:

```

gtk-icon-sizes="panel-menu=16,16:gtk-menu=16,16:panel=16,16:gtk-large-toolbar=16,16:gtk-small-toolbar=16,16"

```

Save that into your .gtkrc-2.0 file or .gtkrc file and restart X and you should see a noticeable difference. Of course as always, YMMV!

And hey, if one of the GNOME devs comes by and see's this could you PLEASE enlighten us as to WHY this is done in such a way? Why couldn't we just have an icon size selection tool? And WHY isn't it documented in other than the fall-asleep-as-you-try-and-trudge-through-it technical specs?

Griping aside, I hope that helps someone.

---

### Post by Rahl on 2007-06-22
I have a ~/.gtkrc-2.0 and it contains just one line, namely 

```

gtk-icon-sizes="gtk-large-toolbar=16,16:panel-menu=16,16:gtk-button=16,16:gtk-dialog=16,16:gtk-menu=16,16"

```This exactly the same file had the desired effect on Edgy, but on Feisty this particular setting is being ignored.

I have made a ~/.gtkrc with identical content, it had no effect. I also tried the exact line posted by Al, didn't work either. 

As I can see here [https://answers.launchpad.net/ubuntu/+question/7229](https://answers.launchpad.net/ubuntu/+question/7229) , there is at least one other person having the same symptoms. 

What could be the problem?

---

### Post by HeavyAl on 2007-06-22
Maybe I'm just being nit-picky, but I notice the line you just posted doesn't have this:

```

gtk-small-toolbar=16,16:

```

or this

```

panel=16,16

```

I noticed on my install that until I had all that junk in there nothing seemed to change.

---

### Post by Rahl on 2007-06-23
It doesn't matter, the rest wasn't working either. That gtk-icon-sizes setting doesn't have a definite number of entries. One can also put application-specific entries like "inkscape-decoration=32,32" or similar.

But now I found what was causnig me problems. The Human theme specifies gtk-icon-sizes in /usr/share/themes/Human/gtk-2.0/gtkrc and that entry is obviously preferred to what I have in my ~./gtkrc-2.0. Only after removing the theme's setting did my own become functional.

This means that an user who wishes to change this aspect of the UI must have administrative privileges because theme's global gtkrc must be modified. This also means manual tweaking if an update for the theme gets released.

---

### Post by HeavyAl on 2007-06-23
Well ouch, then! That's not the most user-friendly solution since it involves admin privileges, but on the upside you got it working! 

It occurs to me - I was working with a totally different theme when I was trying to get this to work - cant remember offhand which one and I'm not on that machine right now .. in any case, I wonder if it's something intrinsic to the Human theme.

---

### Post by jamesford on 2007-07-20
this works for me

gtk-icon-sizes = 
"panel-menu=20,20:
panel=22,22:
gtk-menu=16,16:
gtk-large-toolbar=20,20:
gtk-button=16,16:
gtk-small-toolbar=18,18"
gtk-toolbar-style = GTK_TOOLBAR_ICONS
gtk-toolbar-icon-size = GTK_ICON_SIZE_SMALL_TOOLBAR

---

### Post by caraboy on 2008-06-09
Not working anymore in Ubuntu 8.04. :( Any ideas?

---

