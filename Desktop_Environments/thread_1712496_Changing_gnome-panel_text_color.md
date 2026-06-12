---
title: "Changing gnome-panel text color"
date: 2011-03-22
forum: Desktop Environments
---

### Post by Vostrocity on 2011-03-22
I have a theme that looks like this.
[IMG]http://i.imgur.com/8EEFr.png[/IMG]
Unfortunately, it makes the globalmenu and clock applets disappear on my gnome-panel. My panel is set to system theme, though when I choose a solid color I can get the hidden text to show up. I want to preserve the system color so I need to change the text color somehow. Also, I don't know why it uses that bluish color when clicked on since I never defined such a color in the appearance settings.

---

### Post by Frogs Hair on 2011-03-22
Some themes support color and text color change . Try Appearance  Preferences > Customize > Controls > Colors .

When you change a text color in on area it will affect other areas of the theme. I adjusted a themes text color on my first try and it worked great until I opened the software center and the application descriptions were invisible.

It takes some experimentation it will work with some themes. Have fun !

---

### Post by Vostrocity on 2011-03-22
But changing any of the text colors there doesn't have any effect on text in the panel.

---

### Post by Frogs Hair on 2011-03-22
> **Vostrocity said:**
> But changing any of the text colors there doesn't have any effect on text in the panel.

It does on some themes but not all . I found it to be hit and miss . Another  option would be to alter the theme file its self , but have not done that yet .  You would have to know what line/s to edit , but it is possible.

---

### Post by mcduck on 2011-03-23
You can define a custom text color for panel menus & applets by adding the following lines into ~/.gtkrc-2.0 (create the file first if you don't have it already):

```
style "custom-panel"
{
  fg[NORMAL] = "#000000"
}
widget "*PanelWidget*" style "custom-panel"
widget "*PanelApplet*" style "custom-panel"
widget "*fast-user-switch-applet*" style "custom-panel"

```

Change the #000000 to whatever color you want, of course. And you need to log out and back again for the changes to take effect. If something refuses to change color after that, then your GTK theme is specifically defining a color for that item and you need to edit the GTK theme itself.

---

### Post by Vostrocity on 2011-03-23
You were right that my GTK theme has a specific .rc file that defined the panel appearance. I don't have time to edit it so I just commented out that file and had the panel revert to the default Gnome settings.

---

