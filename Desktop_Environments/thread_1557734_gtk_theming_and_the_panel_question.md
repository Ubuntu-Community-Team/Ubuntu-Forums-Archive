---
title: "gtk theming and the panel question"
date: 2010-08-21
forum: Desktop Environments
---

### Post by tpprynn on 2010-08-21
I have a theme made of the New Wave border, the Nodoka gtk engine (Nodoka-Squared specifically), a medium grey colour in general and a panel background made from editing a screenshot of the New Wave border.  I've got a gtkrc-2.0 file in /home to make the panel's text white and boxes round the menu titles almost the panel background colour.  When the Evolution or volume control icons are clicked on they use the 'selected' background colour from the main theme.  I imagine that my gtkrc-2.0 file doesn't cover what these two are in its closing lines or something about those applets overrides my file:


style "panel"
{
fg[NORMAL] = "#FFFFFF"
fg[PRELIGHT] = "#FFFFFF"
fg[ACTIVE] = "#FFFFFF"
fg[SELECTED] = "#616161"
fg[INSENSITIVE] = "#FFFFFF"

bg[NORMAL] = "#616161"
bg[PRELIGHT] = "#616161"
bg[ACTIVE] = "#616161"
bg[SELECTED] = "#616161"
bg[INSENSITIVE] = "#FFFFFF"

base[NORMAL] = "#FFFFFF"
base[PRELIGHT] = "#FFFFFF"
base[ACTIVE] = "#FFFFFF"
base[SELECTED] = "#FFFFFF"
base[INSENSITIVE] = "#FFFFFF"

text[NORMAL] = "#FFFFFF"
text[PRELIGHT] = "#FFFFFF"
text[ACTIVE] = "#FFFFFF"
text[SELECTED] = "#FFFFFF"
text[INSENSITIVE] = "#FFFFFF"
}
widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
class "*Panel*" style "panel"
widget_class "*Mail*" style "panel"
class "*notif*" style "panel"
class "*Notif*" style "panel"
class "*Tray*" style "panel"
class "*tray*" style "panel"


Would I also be right to say that pixmaps on a panel, i.e. like those used as boxes of running program names, can't be transparent, or aren't used transparently if they have been made as transparent?  I did have a glassy desktop for a while but it looked a bit botched in this way.  Ideally running programs would have no box around on the panel, it'd just be the program name, just like if you have two or three programs running the not currently selected ones aren't boxed in the panel (like the Calculator panel box in my attached png file as opposed to the boxed Firefox).  This must be easy to do but I don't want to study gtk in any scholarly depth.

Thanks for any help.

---

