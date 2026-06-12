---
title: "Mate Panel Text Colour"
date: 2017-07-04
forum: Desktop Environments
---

### Post by Quarkrad on 2017-07-04
Running 16.04 Mate.  I've been playing around with configuring but so far have not been to find out how to change the colour of the text in the top panel. E.g. Date/Time, Applications, Places, System.  Any help appreciated.

---

### Post by Quarkrad on 2017-07-04
I can be a bit more specific - if you add to the (top) panel *menu bar* you get another instance of Applications, Places, System.  On my system/theme this new instance appears with black text.  I would like to, if possible, configure my system so the text appears white.

---

### Post by #&amp;thj^% on 2017-07-04
It has been a while since i did anything like this, have a look @ dconf-editor

Nagivate to org/gnome/libgnomekbd/indicator
You should see a few keys, one of them named "foreground-color" which is hex (set #FFFFFF - for white color), and defaults to #000000 (black color).
Not sure if there was anything seen for mate-panel in there.
EDIT: I forgot this (When mate-panel is built with GTK3 as on many distros using 1.16, no GTK2 setting has any effect. The GTK3 theme controls it, could be overrriden by code in ~/.config/gtk-3.0/gtk.css. The code below is taken from my UbuntuStudio_Legacy theme and should do it if saved to ~/.config/gtk-3.0/gtk.css

```
panel-toplevel.background.horizontal,
.mate-panel-menu-bar,
#clock-applet-button,
#clock-applet-button:hover  {
	color: white;
}

```
Anyway hope this proves useful.

---

### Post by Quarkrad on 2017-07-04
Thank you.  I had a look under org/gnome but I have no libgnomekbd.  I also created a css file and used your code but it has not made any difference.  (In ~/.config/gtk-3.0/ I have a file called settings.ini that contains the txt [Settings]
gtk-application-prefer-dark-theme=0).

---

### Post by #&amp;thj^% on 2017-07-04
hmmm? Have you tried right clicking in the panel...Top Tabs>>>.Background...Solid color?
You will also have transparency enabled also might be helpful.
Sorry to be Clear...Right Click the Panel>>>Properties...Tabs at the top choose Background...Tick the Solid Color option.
By Default it is set to use the system's Theme.

---

### Post by Dennis N on 2017-07-04
What theme do you use? Don't panel colors, including text color, change with the theme? On my 16.04 Mate, I used Greybird GTK Theme which gives white text on all the panel items, including menu bar. I have a custom Gnome Metatheme Greybird-Gray with this index.theme:
```
[Desktop Entry]
Type=X-GNOME-Metatheme
Name=Greybird-Grey
Encoding=UTF-8

[X-GNOME-Metatheme]
GtkTheme=Greybird
MetacityTheme=Zukitwo-Dark
IconTheme=Mint-X-Grey
CursorTheme=FlatbedCursors.White.Large

```
Mint-X-Grey is mostly for folders, so to get the application icons and correct Mate menu icon, I change its index.theme to contain the line **Inherits=mate**

---

### Post by #&amp;thj^% on 2017-07-04
> **Dennis N said:**
> What theme do you use? Don't panel colors, including text color, change with the theme? On my 16.04 Mate, I used Greybird GTK Theme which gives white text on all the panel items, including menu bar. I have a custom Gnome Metatheme Greybird-Gray with this index.theme:
```
[Desktop Entry]
Type=X-GNOME-Metatheme
Name=Greybird-Grey
Encoding=UTF-8

[X-GNOME-Metatheme]
GtkTheme=Greybird
MetacityTheme=Zukitwo-Dark
IconTheme=Mint-X-Grey
CursorTheme=FlatbedCursors.White.Large

```
Mint-X-Grey is mostly for folders, so to get the application icons and correct Mate menu icon, I change its index.theme to contain the line **Inherits=mate**
+1 Nice! :)
I'm betting OP is still on the default theme...use's Black Text in the Panels.

---

### Post by Quarkrad on 2017-07-04
At the moment I'm using the GreenLaguna theme and the standard Desktop picture - my panel is set to a solid colour but the transparency is very low.  I actually like this set up bit if the Applications, Places. System  (and date/time) text in the top panel were white is would really set it off.

---

### Post by Dennis N on 2017-07-04
I just decided to switch the Icon Theme to Paper to give things a more up-to-date look. All depends on what the user thinks looks good, of course. No problems noticed yet.

---

### Post by Dennis N on 2017-07-04
> **Quarkrad said:**
> At the moment I'm using the GreenLaguna theme and the standard Desktop picture - my panel is set to a solid colour but the transparency is very low.  I actually like this set up bit if the Applications, Places. System  (and date/time) text in the top panel were white is would really set it off.

Yes, white would be better. Some of the provided themes have white text. I have used Green Submarine or Blue Submarine - both have white text. These also have dark menu backgrounds that many people like.

---

### Post by oldos2er on 2017-07-04
Thread moved to *Desktop Environments*

---

### Post by Quarkrad on 2017-07-05
I notice, using the GeenLaguna theme that although Applications, Places and System are black in colour, when I click on any of them and get the drop down menu then they do turn white.  So my question is - is there are config file somewhere (I guess there must be) that dictates that before clicking on them their colour is black.

---

### Post by Quarkrad on 2017-07-05
Virtually there - although there might be some odd things I've yet to find.  I install Gnome-Color-Chooser and changed the colour as per *before.png*. You can see the difference in *after.png*.  Many thanks for your help on this one.  (This also change the text colour of the date/time which is super).

---

### Post by Dennis N on 2017-07-05
> **Quarkrad said:**
> Virtually there - although there might be some odd things I've yet to find.  I install Gnome-Color-Chooser and changed the colour as per *before.png*. You can see the difference in *after.png*.  Many thanks for your help on this one.  (This also change the text colour of the date/time which is super).

That's the tool that we used in the old gnome 2 desktop before Unity appeared. I remember trying it on the first ever Ubuntu MATE (14.10) and only certain changes worked correctly. There were a lot of changes you could make on the old systems. I would think it would not work once MATE went to gtk 3, but maybe that had not happened completely in 16.04 so you panels could be still built on gtk 2. Not sure of the change timeline on that. Anyway, glad to hear that worked out.

---

