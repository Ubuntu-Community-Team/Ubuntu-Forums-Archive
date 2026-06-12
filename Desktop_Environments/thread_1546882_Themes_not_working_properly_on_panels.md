---
title: "Themes not working properly on panels"
date: 2010-08-06
forum: Desktop Environments
---

### Post by kmkrebs on 2010-08-06
I have installed a few new themes via Synaptic recently, and now when I change themes, the panels do not get themed correctly for almost all themes.  I've tried removing and re-installing the themes but to no avail.  Here is an example of what it looks like when I switched to the 'ambience' theme:

[IMG]http://dl.dropbox.com/u/118844/Screenshot.png[/IMG]

  Any ideas?

---

### Post by mcduck on 2010-08-06
Actually the theme is working just like it was made to work, it's just that your panel is larger than what the theme was made for. :)

The actual problem lies in the fact that panel backgrounds coming from the GTK theme can't be scaled or rotated to fit the panel, even though the panel actually supports those features.

To solve that, you'll need to edit your GTK theme to remove any panel theming from it, and then set the background image directly from the panel's options. After that you can use gconf-editor to enable rotation and scaling for the image, depending on what you need.

If you are lucky, your GTK theme has a separate "panel.rc" file. In that case simply removing or renaming this file is enough to remove the panel theming from the theme. If it doesn't have such file, you'll just have to search through the main theme file to remove panel-related stuff manually.

One that's done you can just drag&drop the image you want  to use as panel background into the panel, or right-click on the panel to access it's settings and set the background there.

For the final step you need to run "gconf-editor", use it to browse to apps/panel/toplevels/*name_of_your_panel*/background, and enable the *stretch*, *fit* and *rotate* -options based on what you want.

---

