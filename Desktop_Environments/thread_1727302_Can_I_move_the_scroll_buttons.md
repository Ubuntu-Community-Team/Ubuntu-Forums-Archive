---
title: "Can I move the scroll buttons?"
date: 2011-04-12
forum: Desktop Environments
---

### Post by ninja9578 on 2011-04-12
The scroll buttons are on the top and bottom of the scrollbar instead of together, which is really annoying to me.  Is there a way to put them together on the bottom of the scrollbar?

---

### Post by Frogs Hair on 2011-04-12
hi and Welcome

Need to know what version of Ubuntu you using and if you could post a screen shot it would help .

---

### Post by ninja9578 on 2011-04-12
I am using Ubuntu x86 10.10, and here is a screenshot of the strangeness.  I assume they did this to emulate windows, but for osx users, its really annoying.

[IMG]http://img849.imageshack.us/img849/70/screenshotubuntucanimov.png[/IMG]

this is where mac users expect the scroll buttons to be
[img]http://media.wiley.com/assets/204/71/0-7645-4168-4_0502.jpg[/img]

It makes it a lot easier to scroll if they are right next to each other.

---

### Post by Frogs Hair on 2011-04-12
It is most likely possible  , but you would need to know what to and how to change the gtk theme file . I have not done this , but there are others on the forum who have made gtk themes and may be able to help.

---

### Post by Paddy Landau on 2011-04-13
Seeing this post, it made me think. I'm sure I've come across the style you show somewhere; didn't Windows have it many, many years ago?

It's a good idea, actually. If you find out how to do it and it's easy, I might copy it.

---

### Post by Krytarik on 2011-04-13
For the Ambiance theme and any other theme based on the Murrine engine (as opposed to pixmaps) you can achieve that by adding/modifying a few entries in its "gtkrc" file, located at the toplevel of the theme's directory.

But the downside of this is that the sliders become squared, even if the endpoints of the scrollbars are rounded. This is the case with Ambiance, and you may or may not live with that.

- backup the original file:
```
sudo cp /usr/share/themes/Maverick/gtk-2.0/gtkrc /usr/share/themes/Maverick/gtk-2.0/gtkrc-original
```- open the file for editing:
```
gksu gedit /usr/share/themes/Maverick/gtk-2.0/gtkrc
```- add the [COLOR=Blue]blue[/COLOR] marked entries
- modify the [COLOR=Red]red[/COLOR] marked entry

/usr/share/themes/Ambiance/gtk-2.0/gtkrc:
```

    GtkScrollbar::activate-slider = 1
    GtkScrollbar::trough-border = 0
    GtkScrollbar::slider-width = 13
    GtkScrollbar::min-slider-length = 31
[COLOR=Blue][B]    GtkScrollbar::has-backward-stepper = 0
    GtkScrollbar::has-secondary-backward-stepper = 1[/B][/COLOR]
``````

    engine "murrine" {
        contrast = 0.6
        arrowstyle = 2
        reliefstyle = 3
        highlight_shade = 1.0
        glazestyle = 0
        default_button_color = shade (1.1, @selected_bg_color)
        gradient_shades = {1.1, 1.0, 1.0, 0.9}
        roundness = 4
        lightborder_shade = 1.26
        lightborderstyle = 1
        listviewstyle = 2
        progressbarstyle = 0
        colorize_scrollbar = FALSE
        menubaritemstyle = 1
        menubarstyle = 1
        menustyle = 2
        focusstyle = 3
        handlestyle = 1
        sliderstyle = 3
        scrollbarstyle = 2
[COLOR=Red][B]        stepperstyle = 0
[/B][/COLOR]#        rgba = TRUE
    }
```- save/quit
- re-apply the theme

Greetings.

---

### Post by Paddy Landau on 2011-04-13
@Krytaric: Thank you, this works well!

---

