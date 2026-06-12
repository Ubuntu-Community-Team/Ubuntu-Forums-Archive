---
title: "Changing Text Color in Panels"
date: 2008-06-25
forum: Desktop Environments
---

### Post by CharmCityCrab on 2008-06-25
I've changed my panel color to blue.  Unfortunately, the black text of the aps menu and so forth doesn't show up well against a fairly dark blue panel.  Is there a way I can change the text color in the panels to white?  I think that would look really nice and show up better.

---

### Post by CharmCityCrab on 2008-06-26
Anyone want to take a guess?

---

### Post by cdtech on 2008-06-26
Could you elaborate on the "Panels"? Do you mean terminal, Nautilus?

You can change Nautilus within the System > Preferences > Appearance
And the terminal just right click within the terminal to alter the appearance.

Hope this helps......

---

### Post by Xgen on 2008-06-26
You can change panel attributes with the Gnome Color Chooser (Synaptic--->gnome-color-chooser) OR...add:

style "panel color"
{
fg[NORMAL] = "#(color number)" 
}
widget "*PanelWidget*" style "panel color"
widget "*PanelApplet*" style "panel color"

...to your ~/.gtkrc-2.0 file...of course, substituting (color number) for the preferred one (white is ffffff). Restart the X session.

---

