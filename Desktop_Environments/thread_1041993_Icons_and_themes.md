---
title: "Icons and themes"
date: 2009-01-17
forum: Desktop Environments
---

### Post by guenwhyever on 2009-01-17
Just a couple questions.. I've been googling for the last couple days and I've yet to come up with anything!

How can I change the icons in thos notification area? (As in, use my own icons)
I'd also like to be able to change the icon that shows for an application in the task bar.

Can I make certain applications use a different theme than my dekstop (and everything else for that amtter)? I am currently using a dark theme and it really screws with forms in firefox and my openoffice applications.
Another solution would be to use clearlooks as my default them but have a dark theme for my gnome panel.

How can I make my own themes? Is there some easy-to-use program that I can do it with?


Sorry if I've misplaced this at all and thanks for your time =]

---

### Post by ayoli on 2009-01-17
> **guenwhyever said:**
> Just a couple questions.. I've been googling for the last couple days and I've yet to come up with anything!

How can I change the icons in thos notification area? (As in, use my own icons)
I'd also like to be able to change the icon that shows for an application in the task bar.

Can I make certain applications use a different theme than my dekstop (and everything else for that amtter)? I am currently using a dark theme and it really screws with forms in firefox and my openoffice applications.
Another solution would be to use clearlooks as my default them but have a dark theme for my gnome panel.

How can I make my own themes? Is there some easy-to-use program that I can do it with?


Sorry if I've misplaced this at all and thanks for your time =]

If you want to change notification icons you have to change them in the icon theme you use either in /usr/share/icons (need root privilege here) or ~/.icons

To launch an app with a different gtk theme something like :
```
export GTK2_RC_FILES=/usr/share/themes/Human/gtk-2.0/gtkrc && firefox
```
should do the trick.
Btw, there are many fixes for firefox pb with dark themes. Look for stylish extension for FF and find styles on userstyles.org that fix this issue.

Now, to make gtk theme, there is no easy-prog-t-to-use, it is a text file (and sometimes pixmap if you want to use pixbuf engine).
The best is to start from a theme and start tweaking it.
You'll find some useful links here : [http://gnome-look.org/groups/?id=65](http://gnome-look.org/groups/?id=65) and may also be interested to install [the widget factory]("http://gnome-look.org/content/show.php/The+Unofficial+Widget+Factory+(DEB)?content=84209") (for testing themes).

---

