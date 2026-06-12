---
title: "changing title bar size"
date: 2007-06-15
forum: Desktop Effects &amp; Customization
---

### Post by tezclo on 2007-06-15
I have Ubuntu 6.06LTS. I would like to customize the size of my title bar and the min/max icons but cannot find an option for it in System-Preferences-Theme. I can change the look of the window border (e.g., from Tango to Human) but not the size. Thanks for your help!

---

### Post by nereid on 2007-06-15
The size of the title bar is depended on the window theme. Some themes allow to change it, some not.

---

### Post by tezclo on 2007-06-15
I'm thinking there must be some config file that you can modify??

---

### Post by nereid on 2007-06-16
As I said, some themes allow to change this. As far as I know are metacity themes build by pictures, so your picture has a fixed height.

---

### Post by tezclo on 2007-06-18
I discovered the solution! Thanks for the hint about metacity rukh.de. 

The trick is you have to edit each individual metacity theme's XML file. Suppose you want to edit the LegacyHuman theme: 

```
sudo gedit /usr/share/themes/LegacyHuman/metacity-1/metacity-theme-1.xml

```

Then look for the block of code that matches this: 
 
```
<frame_geometry name="normal" rounded_top_left="false" rounded_top_right="false" rounded_bottom_left="false" rounded_bottom_right="false">
  <distance name="left_width" value="5"/>
  <distance name="right_width" value="5"/>
  <distance name="bottom_height" value="5"/>
  <distance name="left_titlebar_edge" value="4"/>
  <distance name="right_titlebar_edge" value="3"/>
  <aspect_ratio name="button" value="1"/>
  <distance name="title_vertical_pad" value="4"/>
  <border name="title_border" left="2" right="2" top="3" bottom="3"/>
  <border name="button_border" left="1" right="1" top="3" bottom="3"/>
</frame_geometry>

```

Under "title_border", increase the top="" and bottom="" values to something like 3 (as shown above). 

The next step involves refreshing the theme via System-Preferences-Theme (Ubuntu Dapper). Re-select the theme you just modified (e.g., Legacy Human), and volia! Check out my screenshot. 

Note: I found the info on [HTML]http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html[/HTML]

---

### Post by tezclo on 2007-06-18
To change the scroll bar size, you should modify the gtkrc file instead of metacity. For example, if you want to modify LegacyHuman:

```

sudo gedit /usr/share/themes/LegacyHuman/gtk-2.0/gtkrc

```

and find the section of code that looks like this:

```

  GtkRange::slider_width = 18
  GtkRange::stepper_size = 15
  GtkScrollbar::min_slider_length = 30
  GtkCheckButton::indicator_size = 12
  GtkMenuBar::internal-padding = 1

```

and change the slider_width value. For those of you who are willing to play around with these files, let me know if you find anything else to configure!

---

