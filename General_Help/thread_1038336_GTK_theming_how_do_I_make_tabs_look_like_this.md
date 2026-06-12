---
title: "GTK theming: how do I make tabs look like this?"
date: 2009-01-12
forum: General Help
---

### Post by ChrisBookwood on 2009-01-12
Hi,

I'm customizing the Human theme for my likes, and I only have one thing left to fix before throwing the theme up on gnome-look.org, but I just can't figure out how to do it.

As far as I know, a frame with tabs in gtk is the GtkNotebook widget, and I want to change the look of its tabs, so it gets a line beneath the tabs on top of the content as showed on the mockup below.

[IMG]http://dl.getdropbox.com/u/168187/gtktm.jpg[/IMG]


I hope one of you out there can help me with this, cause I have been wondering around the gtkrc file and library.gnome.org's gtk theme reference to find out how to make it, but I haven't figured anything out, so please help me with this.

---

### Post by ChrisBookwood on 2009-01-13
Nobody knows? Come on...

---

### Post by Ivo Moelans on 2009-01-14
I think it is not very simple.

Maybe the solution lies not in how the *tabs* are rendered, but in how the *box* under the tab is rendered. If I understand correctly, what you want to achieve in a notebook with tabs at the top is something like this: the box has no space on the left, right & bottom and a space of a few pixels at the top.

If you compare notebook view in Nautilus, Text Editor (gedit) and Appearance Manager it seems to me that maybe the programs themselves manage how the box of a notebook view is rendered. On the other hand, maybe it is possible to make gtk override this.

You could look in the gtkrc of _[Ice]("http://www.gnome-look.org/content/show.php/Ice?content=88630")_. Take a look at the notebook style: it should give you some pointers. Only, here this is achieved with pixmaps. So, basically you're back at the same problem you had with the toolbar: how to make gtk draw that...

BTW: did you ever find out how to do that?

Sorry that I can't be of more help, but I am interested in the solution, if any.

---

### Post by ChrisBookwood on 2009-01-15
I've found out, that by inserting the following code, it will create a somehow alike of the mockup. There's still a lot of things to be fixed, though.
```

ythickness = 3
```With that in the notebook-style, it makes a 3 pixel high gab ( including the border above ) underneath the tabs, but it also does it on the bottom of the notebook, so I need to find a way to only make it show on the top, not the bottom. I also need to find a way to make the last 1px border underneath the 3pixels created by *ythickness*. 
This is how it looks now...
[IMG]http://dl.getdropbox.com/u/168187/gtktm2.jpg[/IMG]

---

### Post by spupy on 2009-01-16
Is the "mockup" a screenshot of a real theme? I'd say that the way the tabs look is not so much due to the gtkrc file, but to the rendering engine of the theme.

P.S.: Can you tell me what theme this is?

---

### Post by ChrisBookwood on 2009-01-16
> **spupy said:**
> Is the "mockup" a screenshot of a real theme? I'd say that the way the tabs look is not so much due to the gtkrc file, but to the rendering engine of the theme.

P.S.: Can you tell me what theme this is?

yeah, the mockup is a graphically manipulated version of my [Umano theme]("http://gnome-look.org/content/show.php/Umano?content=97370").

---

### Post by ChrisBookwood on 2009-01-19
Anyone?

---

