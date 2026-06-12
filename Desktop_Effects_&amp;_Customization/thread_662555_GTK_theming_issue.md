---
title: "GTK theming issue"
date: 2008-01-09
forum: Desktop Effects &amp; Customization
---

### Post by daspooky on 2008-01-09
Hello mighty Ubuntu users,

I'm having an issue in modifying an existing GTK theme for my own use. 

I gave the gtk notebook controls dark tab background for active state, and a light background for inactive state. The text for active state should be white, and should be dark for inactive state. I did as follows in the gtkrc file and works very well for the tabs:

-----------------------------------------------------------------
style "tabs"
{
  fg[SELECTED] = "#505050"
  text[SELECTED] = "#505050"
  fg[ACTIVE] = "#505050"
  text[ACTIVE] = "#505050"
  fg[NORMAL] = "#ffffff"
  text[NORMAL] = "#ffffff"
	xthickness  = 2
  	ythickness  = 2
}

class "GtkNotebook"      style "tabs"
widget_class "*GtkNotebook*GtkLabel"	style "tabs"
-----------------------------------------------------------------

THE PROBLEM:

The line **widget_class "*GtkNotebook*GtkLabel"	style "tabs"** makes all the labels in a tab-sheet also white :( Like unchecked checkboxes and radio buttons, group box titles,...

How can I prevent this side-effect?

Thanks a lot.

Kind regards,

daspooky

---

