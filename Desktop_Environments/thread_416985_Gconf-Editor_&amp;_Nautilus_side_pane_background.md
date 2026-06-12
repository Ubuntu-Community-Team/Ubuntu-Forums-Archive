---
title: "Gconf-Editor &amp; Nautilus side pane background"
date: 2007-04-21
forum: Desktop Environments
---

### Post by bryonak on 2007-04-21
Hi folks! Setting a background image/color for nautilus folders is simple enough (Edit->Backgrounds and Emblems->drag'n'drop), but I'd like sidepane to have the same color.
Drag'n'Drop doesn't work here, but there's an option in the Gconf-Editor:
apps->nautilus->preferences, there are 3 keys named **side_pane_background_set**, **side_pane_background_color** and **side_pane_background_filename**. Intuitively checking the **_set** key and assinging a color value to the **_color** key or a filepath to the **_filename** key should change the background of the sidepane, but I can't see any change even after rebooting. Any ideas here?

Another thing about the Gconf-Editor:
There's some keys labeled as "deprecated", for example apps->panel->global->**panel_show_delay**. Now changing this value has no effect, but some time ago I've been able to set the show delay of my panel to 10ms... in the Gonf-Editor on Edgy, though I'm not sure if it was exactly this key.
My panel still shows very quickly (just about 10ms ;)), but I can't find a way to affect this now (upgraded to Feisty, no fresh install) since it's labeled as deprecated. Does anyone know how to edit the delay time for the panel?

---

### Post by notarikon on 2007-04-21
Re: Side Pane

Well, actually it does work ... but only under "Information" in the side pane - all the other options have the standard background. What's worse is that the text for the Information bar has a ugly drop grey shadow that looks hideous on a dark background.

I'm still looking for a way to fix this (might have to write a Nautilus patch) but I also want to lose the header at the top of the side pane where you choose what you are showing, and relegate that option to the View menu - instead of a checkbox for Side Pane have a drop out menu with the options and None at the top :)

---

### Post by dustigroove on 2007-08-06
[FONT=Arial][SIZE=2][COLOR=Black]Also looking for a cure to this nautilus [/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]window background [/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]ailment... anybody have any suggestions?
[/COLOR][/SIZE][/FONT]

---

### Post by bluetec on 2007-11-09
I'm also looking for a solution or a trick to change the side pane color,

i thought it might has something to do with text label background color, i mean like the address bar color, maybe they are considered the same, but i don't know how to change the address bar color :S:S

any suggestions ?

---

### Post by AlexR1 on 2007-11-09
In your theme gtkrc add those lines 

GtkTreeView::odd_row_color = "#your color here"
 GtkTreeView::even_row_color = "#your color here"

 save & close  and then killall nautilus

---

