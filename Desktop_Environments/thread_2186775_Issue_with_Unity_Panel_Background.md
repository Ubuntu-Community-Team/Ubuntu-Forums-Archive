---
title: "Issue with Unity Panel Background"
date: 2013-11-09
forum: Desktop Environments
---

### Post by dannymichel on 2013-11-09
Anyone a themes expert? I was finally able to use a background image for my panel by editing my theme files, but the panel background get's slightly darker when i hover over it. You really have to pay attention to the panel to see it [http://d.pr/v/bDag](http://d.pr/v/bDag)

---

### Post by Frogs Hair on 2013-11-09
What you are seeing happens with all themes when panel items are selected ,but not during hover . I have been using the application at the link, but still have a color change when selecting items. The application may allow you to set a panel color without the hover issue . 

  [http://www.webupd8.org/2012/09/customize-gtk3-gtk2-theme-colors-using.html](http://www.webupd8.org/2012/09/customize-gtk3-gtk2-theme-colors-using.html)

---

### Post by dannymichel on 2013-11-09
thanks. that application didnt help though.

---

### Post by mc4man on 2013-11-09
Does the 'color change' happen when you don't have a window whose decoration is slightly into the panel?
(from your video the change occurs when switching focus from window (no gradient or shadow) to the Desktop (gradient +shadow

---

### Post by dannymichel on 2013-11-09
No, it doesn't. I can make another video that shows it more clearly.

---

### Post by dannymichel on 2013-11-09
This video is a perfect example [http://d.pr/v/wctS](http://d.pr/v/wctS)

---

### Post by mc4man on 2013-11-09
> **dannymichel said:**
> This video is a perfect example 
That's much better to show issue.
I'd suggest to maybe get some help with whatever is gone wrong with your theme to post
What release of Ubuntu
What theme you're using
And if it didn't occur prior to your editing,  the changes made to that theme

(myself only use & slightly modify Ambiance so likely can be of no help other than what you have should not occur..

---

### Post by dannymichel on 2013-11-09
13.10.
This is a highly modified 'Numix'. 
I don't think 'getting help from the original maker of the theme', which is what i think you're saying would help.
I came here because I thought there might be some people on the boards who theme. If so, are there files that I can post here so someone can better assist?

---

### Post by dannymichel on 2013-11-09
I've tried everything icluding the mess you see here ```
UnityPanelWidget,
.unity-panel {
    /*border-width: 0 0 1px 0;
    border-style: solid;*/
    background-repeat:repeat-x;
    /*background-color: @panel_bg_color;*/
    background-image: url("panel_bg.png");
    /*background-image: none;*/
    color: @panel_fg_color;
}

.unity-panel.menubar, .unity-panel.menubar:hover,
.unity-panel .menubar {
    background-color: #527ead;
}

.unity-panel.menuitem,
.unity-panel .menuitem {
    border-width: 0 1px;
    color: @panel_fg_color;
}

.unity-panel.menubar.menuitem:hover,
.unity-panel.menubar .menuitem *:hover {
    border-color: mix(@panel_bg_color, @panel_fg_color, 0.23);
    /*background-color: mix(@panel_bg_color, @panel_fg_color, 0.21);
    background-image: none;*/
    color: #ffffff;
}
.unity-panel.menubar.menuitem:active,
.unity-panel.menubar .menuitem *:active,.unity-panel.menuitem:active,
.unity-panel.menuitem *:active,UnityPanelWidget:active,
UnityPanelWidget *:active,.unity-panel.menubar.menuitem:visited,
.unity-panel.menubar .menuitem *:visited,.unity-panel.menuitem:visited,
.unity-panel.menuitem *:visited,UnityPanelWidget:visited,
UnityPanelWidget *:visited {
    background-color: transparent;
    border-width:0;
    background-image: url("panel_bg.png");
}
```

---

### Post by stinkeye on 2013-11-09
Did the original theme change the panel color or did you write a panel color section?
Try using the original theme then use **GTK Theme Preferences** to change the panel color.

GTK Theme Preferences writes to "**/.config/gtk-3.0/gtk.css**" where you can see the code used to change panel color.

I don't see any color discrepancies when using a theme that changes the panel color or using GTK Theme Preferences to change panel color.

This is the relevant section of my "**/.config/gtk-3.0/gtk.css**" which is written when I choose a panel backgroud color 
of #CCCCCC with **GTK Theme Preferences**
```
@define-color panel_bg_color #cccccc;
@define-color panel_fg_color #333333;

PanelWidget,
PanelApplet,
PanelToplevel,
PanelSeparator,
PanelApplet > GtkMenuBar.menubar,
PanelApplet > GtkMenuBar.menubar.menuitem,
PanelMenuBar.menubar,
PanelMenuBar.menubar.menuitem,
PanelAppletFrame,
UnityPanelWidget,
.gnome-panel-menu-bar,
.unity-panel {
	background-image: -gtk-gradient(linear,left top,left bottom,from(shade(@panel_bg_color,1.2)),to(shade(@panel_bg_color,0.8)));
	color: @panel_fg_color;
}

.unity-panel.menuitem,
.unity-panel .menuitem {
	color: @panel_fg_color;
}

.unity-panel.menubar.menuitem:hover,
.unity-panel.menubar .menuitem *:hover {
	border-color: shade(@panel_bg_color, 0.7);
	border-image: none;
	background-image: -gtk-gradient(linear,left top,left bottom,from(shade(@panel_bg_color, 0.97)),to(shade(@panel_bg_color, 0.82)));
	color: @panel_fg_color;
}

PanelApplet .button {
	border-color: transparent;
	border-image: none;
	background-image: -gtk-gradient(linear,left top,left bottom,from(shade(@panel_bg_color,1.2)),to(shade(@panel_bg_color,0.8)));
	color: @panel_fg_color;
	box-shadow: none;
	text-shadow: none;
	-unico-inner-stroke-width: 0;
}

PanelApplet .button:active {
	border-color: shade(@panel_bg_color,0.8);
	border-image: none;
	background-image: -gtk-gradient(linear,left top,left bottom,from(shade(shade(@panel_bg_color,1.02),0.9)),to(shade(shade(@panel_bg_color,1.02),0.95)));
	color: @panel_fg_color;
	box-shadow: none;
	text-shadow: none;
	-unico-inner-stroke-width: 0;
}

PanelApplet .button:prelight {
	border-color: transparent;
	border-image: none;
	background-image: -gtk-gradient(linear,left top,left bottom,from(shade(@panel_bg_color,1.2)),to(shade(@panel_bg_color,1.0)));
	color: @panel_fg_color;
	box-shadow: none;
	text-shadow: none;
	-unico-inner-stroke-width: 0;
}

PanelApplet .button:active:prelight {
	border-color: shade(@panel_bg_color,0.8);
	border-image: none;
	background-image: -gtk-gradient(linear,left top,left bottom,from(shade(shade(@panel_bg_color,1.02),1.0)),to(shade(shade(@panel_bg_color,1.02),1.05)));
	color: @panel_fg_color;
	box-shadow: none;
	text-shadow: none;
	-unico-inner-stroke-width: 0;
}

WnckPager,
WnckTasklist {
	background-color: @panel_bg_color;
}
```

---

### Post by dannymichel on 2013-11-09
GTK Theme preferences only supports a solid color. This is a background image.

---

### Post by stinkeye on 2013-11-09
Oh, ok didn't notice because your panel in vid just looked like a gtk-gradient.

---

### Post by dannymichel on 2013-11-10
I went to gnome look to see if it was only my theme. it seems that any theme that uses opacity or a background image has the same problem.
[http://gnome-look.org/content/show.php/Mion?content=160939](http://gnome-look.org/content/show.php/Mion?content=160939)

---

