---
title: "checkboxes - how to make them bigger"
date: 2015-03-22
forum: Desktop Environments
---

### Post by Dreamer Fithp Apprentice on 2015-03-22
I want to make the checkboxes in gui programs bigger. As it is I can barely tell if they are checked without laying my eyeballs on the monitor.

I'm running Trusty with plain Openbox, so my setup is pretty similar to Lubuntu. I'm using a custom theme with folders for gtk-2.0, gtk-3.0, and openbox-3. The gtk-2.0 theme is a modified cleanice-marble. The other 2 are also modified versions of some standard theme, although I forget which.

I posted the same query about a year and a half ago and got no answer. I've been poking at it off and on in the meantime and I haven't made any progress.

Suggestions?

---

### Post by vasa1 on 2015-03-23
gtk2
```
	GtkCheckButton		::indicator-size       			= 15
```

gtk3
```
    -GtkCheckButton-indicator-size: 15;
```
Can you check these? The first is in gtkrc. The second is in gtk-widgets.css.

---

### Post by Dreamer Fithp Apprentice on 2015-03-24
Allright!!!!
Thanks a million, Vasa1! You're a champ.

gtk2:
It took me a few tries but I have the gtk2 working now. For the benefit anyone else with the same issue:
It seems to matter where in the file you put that statement. I put it in the wrong place first and it broke the theme. Then I put in another wrong place and it wasn't effective. It goes like this:
```
style "style_name_here"
{
    Statement goes somewhere in here. Look for similar statements and
    put it next to them, or if there is already one in the exact same form,
    just change the number. Stuff in here will probably be indented, which
    AFAIK is a stylistic thing to make it easier to understand, without
    functional importance. I took out the extra spaces and modified 
    Vasa1's line to look like this:
    GtkCheckButton::indicator-size = 30
}
```
  
gtk3:
Apparently I'd already fixed that. It had the suggested statement in it with a bigger number already. Probably, unlike my gtk2 gtkrc, it came with a statement already in it & I must have already found and edited it. I must have mostly gtk2 aps.

QT:
I've got QT set to follow gtk, so I'm good there. 

Other:
I've still got a few apps that ignore all my themes, maybe because they have hard coded themes, or because they have internal appearance settings I haven't found yet, or maybe they follow some other theme engine that I haven't discovered. A good example is xfontsel. Since there are only a handful of these, since they aren't programs I use every day, and since the problem with them is more general - it's not just check boxes, they don't seem themeable at all - it's really a different problem. If I try again on theming some of  those apps, and fail again, I'll start a new thread. So I consider this solved.

Thanks again. This makes a huge difference in usability. And if there are mistakes in my amplification above that could lead others astray, feel free to correct them.

---

### Post by Dreamer Fithp Apprentice on 2015-03-26
Lol, I needed this more than I thought. Looks like there are some Firefox checkboxes I didn't even know were there until I did this. A million thanks, Vasa1!

---

