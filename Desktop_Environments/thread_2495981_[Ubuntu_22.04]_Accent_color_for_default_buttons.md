---
title: "[Ubuntu 22.04] Accent color for default buttons"
date: 2024-03-10
forum: Desktop Environments
---

### Post by popov895 on 2024-03-10
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293477&stc=1[/IMG]

Ubuntu 22.04 is quite old now, but I'm sure there are a lot of people who are still using it. It has some support for accent colors, but for some reason the developers decided that the default buttons should always be green. And it really annoys me! To fix this mess, just create a file **~/.config/gtk-3.0/gtk.css** with the following contents:

```

.suggested-action {
    background: @theme_selected_bg_color;
}
.suggested-action:hover, .suggested-action:focus { 
    background: shade(@theme_selected_bg_color, 1.05);
}
.suggested-action:active {
    background: shade(@theme_selected_bg_color, .93);
}
.suggested-action:insensitive {
    background: alpha(@theme_selected_bg_color, .5);
}

```

---

### Post by MAFoElffen on 2024-03-10
I might be confused...

Are you just stating a fact (as I see that)? Or did you have a further question?

You seem to have answered that, right?

Yes. The upstream Gnome DEV's made a decision to streamline their own code, by using the default themes for the Desktop, and inheriting thaqt theme for their applications. Many of the tweaks we had for theming before disappeared with that change in how that is done now. 

Now we edit the CSS files. Not elegant. Not easy. But sill do-able & possible. Ugh.

---

### Post by ajgreeny on 2024-03-11
There are many other changes that can be made to the general look of windows such as adding "propper" scrollbars of a sensible size by other additions to the gtk.css file.

Caveat!
I don't use gnome and have no idea what gnome uses for scrollbars but I'm aware that it did at one point use the dreadful overlay scrollbars; perhaps it no longer uses them?

---

### Post by MAFoElffen on 2024-03-11
> **ajgreeny said:**
> There are many other changes that can be made to the general look of windows such as adding "propper" scrollbars of a sensible size by other additions to the gtk.css file.

Caveat!
I don't use gnome and have no idea what gnome uses for scrollbars but I'm aware that it did at one point use the dreadful overlay scrollbars; perhaps it no longer uses them?

Gnome uses scrollbars, but the default width of them is very miniscule (thin)... making them hard for us older folk to see and use. LOL If you are not hovered over them, it's default behavior is to hide it's very thin scrollbars until then. When you hover over them, it reappears, and the background of them changes making them easier to see. Lot's of things happen at the same time of that action. I think it was a GUI visual appearance decision that they thought was more appealing. I have to wonder about the "why" of some of those decisions made, but they did change.

Yes. Xubuntu has less changes that happen over time to the UI.

---

### Post by ajgreeny on 2024-03-11
If you want to try it out here's my version of ~/.config/gtk-3.0 with all the required changes I like for scrollbars and a few other changes for the GUI.
Backup what you have at the moment and try mine in place of your version, logout and back in again and the differences should show in most applications but possibly not in firefox if you use that; firefox has its own configuration settings for that in **about:config**.
```
# gtk.css file created to enable steppers on scrollbars of gtk3 applications.
#
/* Scrollbar width fixes */
scrollbar.vertical slider,
scrollbar.slider.vertical
{
    min-width: 1em;
}
scrollbar.horizontal slider,
scrollbar.slider.horizontal
{
    min-height: 1em;
}

/* Steppers */
* {
    -GtkScrollbar-has-backward-stepper: 1;
    -GtkScrollbar-has-forward-stepper: 1;
}

scrollbar button {
    min-width: 1em;
    min-height: 1em;
}

scrollbar.vertical button.down {
    -gtk-icon-source: -gtk-icontheme("pan-down-symbolic");
}

scrollbar.vertical button.up {
    -gtk-icon-source: -gtk-icontheme("pan-up-symbolic");
}

scrollbar.horizontal button.down {
    -gtk-icon-source: -gtk-icontheme("pan-end-symbolic");
}

scrollbar.horizontal button.up {
    -gtk-icon-source: -gtk-icontheme("pan-start-symbolic");
}

/* Set thickness of scrollbars */
.scrollbar.vertical slider,
scrollbar.vertical slider {
    min-width: 12px;
    background-color: #7F7A7A;
}

.scrollbar.horizontal.slider,
scrollbar.horizontal slider {
    min-height: 12px;
    background-color: #7F7A7A;
}

.scrollbar.vertical.slider:hover,
scrollbar.vertical:hover slider {
    min-width: 12px;
}

.scrollbar.horizontal.slider:hover,
scrollbar.horizontal:hover slider {
    min-height: 12px;
}

/* Include scrollbar steppers */
.scrollbar,
scrollbar {
    -GtkScrollbar-has-backward-stepper: 1;
    -GtkScrollbar-has-forward-stepper: 1;
}

scrollbar button {
min-width: 20px;
min-height: 20px;
}

.xfce4-panel {
  -XfcePanelWindow-popup-delay: 10;
  -XfcePanelWindow-popdown-delay: 5;
}

```

---

