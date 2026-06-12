---
title: "ubuntu and firefox.. with"
date: 2006-07-03
forum: Desktop Environments
---

### Post by frup on 2006-07-03
I just got a theme off gnome-look.org called meidarong 4... i like it. 
I'm having a few issues with text colors in programs though namely, firefox and gaim.

Firefox uses the mostly crystal theme and looks great with the new gnome theme except that the color of the texts on the tabs is black/dark gray and this is a dark theme (ubuntu) .. i cant read the titles... i tried changing some stuff in the miederong source but it doesnt appear to have changed anything... is this likely to be held in the firefox theme? how would i change the color of this text?

On gaim, i have searched through every single preference and cant change the color of the Aliases in a message.. right now theyre standard blue and red... which doesnt look good next to gray either.. where would i do this?


thank you

Ohh one more thing.. i like this theme but dont love it, but really like having the panels in the dark theme.. can i make it so that the panels are different colors to the windows?

The whole theme is controlled by a gtksrc file for "theme details" controls

---

### Post by mcduck on 2006-07-03
I think the problem with Firefox is that it doesn't actually use GTK but XUL instead, so all colors from GTK themes are not properly used. Not a serious problem unless you want to use a GTK theme with dark background color.. I haven't found any solution to this yet..

You could give Epiphany a try, It's a nice browser, and uses GTK :)

---

### Post by Matthew Bartram on 2006-07-03
To change a panel's colour, right-click on it, choose properties, then background.

---

