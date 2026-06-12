---
title: "Theme problems"
date: 2008-03-13
forum: Desktop Effects &amp; Customization
---

### Post by chatman22222 on 2008-03-13
Hi, i've recently moved over to ubuntu from windows. I used to be able to modify my desktop pretty easily, and i figured i'd like to do it on linux too.

I've downloaded many different themes, trying to get them to work. In a certain way they do but not completely.

In the appearance manager, under the tab Controls, all is fine. However, under the window Border tab, i cannot select the them which i've installed, so the them ends up not looking quite right.

For example I installed this theme: [http://www.gnome-look.org/content/show.php/Murrina-CleanEyes?content=50057](http://www.gnome-look.org/content/show.php/Murrina-CleanEyes?content=50057)

and it came out like this for me: 

[[img]http://ix0.nl/mellow/th_theme_fail.png[/img]](http://ix0.nl/image/2984)

As you can see, it isn't the same.

Any help?

Thanks

---

### Post by rune0077 on 2008-03-13
That's because the theme you installed is actually not a whole theme, but only the GTK part (which is the controls).

For a quick introduction:

GTK themes are the controls, like the sliders, progressbar, radio-buttons, etc, etc.

Metacity is responsible for rendering your windowsborders and titlebars and such. 

So, since you only installed a GTK theme, all you get is the Controls. You can find metacity themes on Gnome-look as well.

---

### Post by Therion on 2008-03-13
> **rune0077 said:**
> ... GTK themes are the controls, like the sliders, progressbar, radio-buttons, etc, etc.

Metacity is responsible for rendering your windowsborders and titlebars and such. 

So, since you only installed a GTK theme, all you get is the Controls. You can find metacity themes on Gnome-look as well.
Not that I'm disagreeing with you, but this is an issue I've been dealing with recently myself, so this is pertinent to my interest's.  If GTK only modifies things like buttons and sliders, how is it some GTK themes [like this one](http://www.gnome-look.org/content/preview.php?preview=1&id=65533&file1=65533-1.jpg&file2=&file3=&name=Divinorum) very much change the Window decoration?

I just had a heck of a time getting Emerald to STOP decorating my Windows because I wanted a GTK theme (very similar to the one I linked above) and about went nutty until I was told how to stop Emerald from taking over Window Decoration when Compiz starts.

Just trying to understand all of this because it's confuses me (more than normal).

---

### Post by rune0077 on 2008-03-13
Sorry, I can't test the theme since the link seems brocken (not the one you gave me, but the download link from Gnome-look). I can't really say why that is, except that this particular example seems to be labeled as "Theme/style", while allmost everything else is labeled just "Theme", so maybe that has a say. Not sure what the different would be, though. I'll give the download another try tomorrow and see if the link is up again, let you know if (and how) it works on this end (I'm using Emerald to).

---

### Post by xl_cheese on 2008-03-13
> **Therion said:**
> Not that I'm disagreeing with you, but this is an issue I've been dealing with recently myself, so this is pertinent to my interest's.  If GTK only modifies things like buttons and sliders, how is it some GTK themes [like this one](http://www.gnome-look.org/content/preview.php?preview=1&id=65533&file1=65533-1.jpg&file2=&file3=&name=Divinorum) very much change the Window decoration?

I just had a heck of a time getting Emerald to STOP decorating my Windows because I wanted a GTK theme (very similar to the one I linked above) and about went nutty until I was told how to stop Emerald from taking over Window Decoration when Compiz starts.

Just trying to understand all of this because it's confuses me (more than normal).

That theme contains both the gtk2 and metacity files.  Some themes you get contain both, just the gtk2.0, or just the metacity.  You can mix and match gtk and metacity within the gnome appearance manager by hitting the customize option.  Some themes also allow for color customization.

Yes this is confusing.  Too many themeing items to keep track of.  GDM, GTK2, metacity, emerald, etc...

---

### Post by Therion on 2008-03-13
> **xl_cheese said:**
> That theme contains both the gtk2 and metacity files.  Some themes you get contain both, just the gtk2.0, or just the metacity.  You can mix and match gtk and metacity within the gnome appearance manager by hitting the customize option.  Some themes also allow for color customization.

Yes this is confusing.  Too many themeing items to keep track of.  GDM, GTK2, metacity, emerald, etc...
Damnit!!  Finally it all makes sense!  So then GTK "elements" are pieces of a complete theme that will be *managed* by Metacity!  These elements being things like the buttons and sliders.  The rest of the theme package would be things like window borders, which may or may not be included, but are also managed by Metacity when included, UNLESS Emerald has been chosen as the default Window Decorator... In which case the Emerald Window decorations will be used instead, over-riding the GTK elements of the installed theme!!  Yes! Good gawd I.. I think I've g...

<<head explodes>>

---

