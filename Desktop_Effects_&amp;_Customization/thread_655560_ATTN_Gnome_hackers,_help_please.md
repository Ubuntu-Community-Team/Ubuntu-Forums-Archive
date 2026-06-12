---
title: "ATTN: Gnome hackers, help please"
date: 2008-01-01
forum: Desktop Effects &amp; Customization
---

### Post by bwhite82 on 2008-01-01
Few things I'm hoping someone can help me out with:

1) How to remove the intrusive arrow on my custom start button (screenshot attached, kinda hard to see, it's above the right horn.)

2) How to add a custom banner to the start menu

3) And how do I create a launcher to the trash, what is the command?

Thanks.

---

### Post by steveneddy on 2008-01-01
It looks like KDE. Why not just install KDE if you want that look?

On the arrow, where is the image of the start button stored?

Maybe you need to edit that image. Is it there all of the time or only on mouse over?

Did you paste one image on top of another image?

---

### Post by bwhite82 on 2008-01-01
> It looks like KDE. Why not just install KDE if you want that look?

I can't stand KDE.

> On the arrow, where is the image of the start button stored?

It is stored in my home folder, the value set in gconf-editor.

> Maybe you need to edit that image. Is it there all of the time or only on mouse over?

It is there all of the time, I created the image, it has no arrow on it. Gnome adds it automatically, if I place this start button on a Top panel, the arrow points downward.

> Did you paste one image on top of another image?

No.

---

### Post by Espreon on 2008-01-01
> **steveneddy said:**
> It looks like KDE. Why not just install KDE if you want that look?

You shouldn't use a DE just for its default look...

[B]To the OP:
[/B]
How did you change the default icon of the start button?

BTW, very nice desktop and what icon set are you using?

---

### Post by bwhite82 on 2008-01-01
> **Espreon said:**
> You shouldn't use a DE just for its default look...

[B]To the OP:
[/B]
How did you change the default icon of the start button?

BTW, very nice desktop and what icon set are you using?

To make a custom menu button: make sure you have the "Main Menu" applet added to your panel and not the "Menu Bar" - Then (if installed) open "gconf-editor" from the CLI and navigate to:

apps>panel>objects

You should see a list of objects (object_1, object_2, etc) find the one where on the right side the "object type" value is "menu object".

Check "use_custom_icon".

Change value of "custom_icon" to the path of your button.

The iconset is OSX>gnome-look.org

---

### Post by steveneddy on 2008-01-01
For number 1, I think it is

apps --> panel --> toplevels --> bottom_panel_screen0

uncheck "enable arrows"

---

### Post by bwhite82 on 2008-01-01
> **steveneddy said:**
> For number 1, I think it is

apps --> panel --> toplevels --> bottom_panel_screen0

uncheck "enable arrows"

I've tried that option, doesn't work for me. Although, I don't know what else it could mean.

---

### Post by steveneddy on 2008-01-01
Did you move the top bar to the bottom?

Maybe you need to try

apps --> panel --> toplevels --> top_panel_screen0

Just a thought.

---

### Post by bwhite82 on 2008-01-01
> **steveneddy said:**
> Did you move the top bar to the bottom?

Maybe you need to try

apps --> panel --> toplevels --> top_panel_screen0

Just a thought.

Nope. Don't have a top panel, hence no entry for that. Just found the description of the option in GCONF, so its not the one:

"Enable arrows on hide buttons"

---

### Post by andrewsomething on 2008-01-01
> 3) And how do I create a launcher to the trash, what is the command?

Navigate to apps>nautilus>desktop in gconf and select "trash icon visible."

---

### Post by ~LoKe on 2008-01-02
Sorry to bother you with a post that doesn't help you, but could I possibly get that wallpaper?

---

### Post by bwhite82 on 2008-01-02
> **andrewsomething said:**
> Navigate to apps>nautilus>desktop in gconf and select "trash icon visible."

Thanks!

> Sorry to bother you with a post that doesn't help you, but could I possibly get that wallpaper?

Went to gnome-look.org and search for "freebsd".

---

