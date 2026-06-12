---
title: "Side Panel - some items have background"
date: 2010-03-15
forum: Desktop Environments
---

### Post by kazakore on 2010-03-15
Now I know the background has been picked from the theme and is the same as the whole panel I have across the bottom of the screen but I have this one on the left and the gradients under certain items makes it look horrible. Is there anything that can be done about it?

[[IMG]http://i4.photobucket.com/albums/y144/kazakore/th_ScreenshotMenuBar.png[/IMG]](http://s4.photobucket.com/albums/y144/kazakore/?action=view&current=ScreenshotMenuBar.png)

---

### Post by n0dix on 2010-03-15
Change the theme.

---

### Post by kazakore on 2010-03-15
> **n0dix said:**
> Change the theme.

Really? :rolleyes:

Found it hard enough getting something vaguely pleasant to start with. Could do with a few more configurable colours and stuff. All I need to be able to do is remove the gradient but I can't see an option in Appearance Preferences, where you change all the other Theme stuff.

Also it does help the lower Pane stand out. Would be nice if I could have a horizontal gradient on the horizontal panes and vertical gradients on the vertical panes.

---

### Post by n0dix on 2010-03-15
Maybe this helps you ... more ;)
[http://www.youtube.com/watch?v=QITGJzwA-Sc]("http://www.youtube.com/watch?v=QITGJzwA-Sc")

---

### Post by mcduck on 2010-03-16
> **kazakore said:**
> Really? :rolleyes:

Found it hard enough getting something vaguely pleasant to start with. Could do with a few more configurable colours and stuff. All I need to be able to do is remove the gradient but I can't see an option in Appearance Preferences, where you change all the other Theme stuff.

Also it does help the lower Pane stand out. Would be nice if I could have a horizontal gradient on the horizontal panes and vertical gradients on the vertical panes.

You can't remove the panel background from any dialog. It's defined in your GTK theme and that definition will always override whatever you set elsewhere.

The best way to solve the problem is to edit the theme itself, and remove all panel theming from it. Then apply that panel background image manually from the panel's preferences, and now you can set the panel to rotate & scale the image correctly for your panel through gconf-editor.

(most themes have a separate panel.rc file, if there's one then simply renaming it will usually do the trick. If not you'll have to read through the main theme rc file and remove all panel-related stuff from it. And the gconf keys for scaling/rotating the panel background image can be found in apps/panel/toplevels/*nameofyourpanel*/background.)

---

### Post by kazakore on 2010-03-16
> **n0dix said:**
> Maybe this helps you ... more ;)
[http://www.youtube.com/watch?v=QITGJzwA-Sc]("http://www.youtube.com/watch?v=QITGJzwA-Sc")
~/.themes is empty


Had a look in gconf-editor at  apps/panel/toplevels/*nameofyourpanel*/background and it shows the panel as being black (#ffffff) and I do have it set t solid colour for both so that would make sense, although it's not how it displays.

More weirdly I see and entry for Top and Bottom Panels but I actually have a Bottom and Left panel, I removed the Top one. The Orientation also says Top/Bottom, not Left/Bottom and doesn't match with the settings so doesn't make much sense (I can only assume Bottom really is the bottom one,)

---

### Post by mcduck on 2010-03-16
> **kazakore said:**
> ~/.themes is empty


Had a look in gconf-editor at  apps/panel/toplevels/*nameofyourpanel*/background and it shows the panel as being black (#ffffff) and I do have it set t solid colour for both so that would make sense, although it's not how it displays.

More weirdly I see and entry for Top and Bottom Panels but I actually have a Bottom and Left panel, I removed the Top one. The Orientation also says Top/Bottom, not Left/Bottom and doesn't match with the settings so doesn't make much sense (I can only assume Bottom really is the bottom one,)

Like I said, you _must_ remove the panel theming from your GTK theme first. Background set in GTK theme will always override any panel configuration you try to do yourself.

(as you can see, I didn't even suggest trying to change the panel color in gconf. I only told you that *after* you have removed panel theming from the GTK theme and *set the background image manually* you can enable panel background *scaling* and *rotation* in gconf.)

Also the panel names in gconf are set when the panel is created, and don't change if you move the panel around or do anything. You could name your panels as "Mike" and "Steve" if you liked to, it's just a name to point to individual panels you have.

---

### Post by kazakore on 2010-03-16
> **mcduck said:**
> 

Also the panel names in gconf are set when the panel is created, and don't change if you move the panel around or do anything. You could name your panels as "Mike" and "Steve" if you liked to, it's just a name to point to individual panels you have.


Fair enough, but the Orientation entry should surely match where the panel actually is, no? Well it shows top and bottom when they are left and bottom.

Sorry I'm new to Ubuntu. Is the GTK Theme the theme I was editing with Appearance, Theme, Cutomise? As there doesn't seem to be many options there.

Editing backgrounds in Panel configs works apart from when there is text, when it puts the gradient underneath it.

---

### Post by matrix14 on 2010-03-16
Panel features, includes the fixed panel background (with image in this case) may also be controlled via gtkrc of current used themes. If so, you may need to look at such gtkrc and may need to edit by hand; the file is in /usr/share/themes/[theme name]/, not on your home dir.

---

### Post by kazakore on 2010-03-16
Nice one, have it sorted.

Although I edited the Theme and it was called Custom it didn't show up in the list. Saved it and it still didn't but did show in the ~/.themes but with nothing useful. Moved the panel image from the original Ubuntu Studio Theme into my Home for safe keeping (just in case) and it's all worked smoothly. Could do with choosing an image with a bit more texture for the panels now...

Should really edit the file though, stop errors.

EDIT: Also still swear the gconf isn't correct as it doesn't show either of the panels being autohide, when one of the is, as well as showing wrong orientation.

EDIT2: Don't much like the fact it means all application in the bar that aren't the currently focuses ones have no background now though. Any way to change that?

---

