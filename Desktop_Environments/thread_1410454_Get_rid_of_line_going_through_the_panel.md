---
title: "Get rid of line going through the panel"
date: 2010-02-18
forum: Desktop Environments
---

### Post by cjnkns on 2010-02-18
I just downloaded/installed the Elementary theme via ppa.

My panel size is set to 48 which is a bit larger than normal.
Now there is a line running through the middle of the panel(s).

Is there a way to keep my panel size but get rid of the line? (see attachment)

---

### Post by Hero of Time on 2010-02-19
You have to check the theme itself and see if there is anything like that for panel background image or if the colours are noted like that. When you find the image or noted colours, change them to not show that line. It's the top of the panel that's repeated.
Or, but I'm not sure about this, it's set to tile the image vertically and you need to set it to scale instead. Might end up looking ugly though.

---

### Post by jquerygeek on 2010-02-19
I have some sort of similar problem. :o

---

### Post by cjnkns on 2010-03-11
> You have to check the theme itself and see if there is anything like that for panel background image or if the colours are noted like that. When you find the image or noted colours, change them to not show that line. It's the top of the panel that's repeated.
Or, but I'm not sure about this, it's set to tile the image vertically and you need to set it to scale instead. Might end up looking ugly though.

I downloaded a transparent image in order to apply that as the background for my panel. But, for some reason the panel is only transparent in certain areas. Otherwise, it looks like it retains the theme coloring? What's going on here? You would think getting rid of the damn line when you increase the panel size would be easier!

---

### Post by mcduck on 2010-03-12
The thing here is that any theming for the panel in your GTK theme will override whatever you try to do to the panel yourself.

So, if the GTK theme has set a background to panel applets, then that's what they'll use, no matter what background you set to the panel itself.

And another thing is that while Gnome-panel *is* able to scale panel backgrounds to fit your panel size, and rotate the background for vertical panels, neither one of these features works for panel backgrounds set by your GTK theme.

So, the solution is simple:
1. Remove all panel-related stuff from the GK teme you are using (many themes have a specific panel.rc, in that case simply renaming tat file would do the trick).

2. Set the panel background image yourself directly from the panel's options. 

3. Open gconf-editor, browse to apps/panel/toplevels/*name_of_your_panel*/background and enable any/all of the **fit**, **scale** and **rotate** options depending on what you need.

---

