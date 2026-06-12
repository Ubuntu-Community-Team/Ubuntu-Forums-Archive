---
title: "editing the .gtkrc-2.0 file"
date: 2008-12-20
forum: Desktop Environments
---

### Post by PatrickIIDX on 2008-12-20
ok here is what I have:

style "panel"
{
  fg[NORMAL] = "#ffffff"
# fg[PRELIGHT] = &#8220;#000000&#8243;
  fg[ACTIVE] = "#ffffff"
# fg[SELECTED] = &#8220;#000000&#8243;
  fg[INSENSITIVE] = "#8A857C"
  bg[NORMAL] = "#000000"
  bg[PRELIGHT] = "#5B9C79"
  bg[ACTIVE] = "#6C6A6A"
# bg[SELECTED] = &#8220;#D8BB75&#8243;
  bg[INSENSITIVE] = "#EFEFEF"
  base[NORMAL] = "#ffffff"
# base[PRELIGHT] = &#8220;#EFEFEF&#8221;
  base[ACTIVE] = "#D0D0D0"
# base[SELECTED] = &#8220;#DAB566&#8243;
# base[INSENSITIVE] = &#8220;#E8E8E8&#8243;
# text[NORMAL] = &#8220;#161616&#8243;
# text[PRELIGHT] = &#8220;#000000&#8243;
# text[ACTIVE] = &#8220;#000000&#8243;
# text[SELECTED] = &#8220;#ffffff&#8221;
# text[INSENSITIVE] = &#8220;#8A857C&#8221;
}
widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
class "*Panel*" style "panel"
widget_class "*Mail*" style "panel"
class "*notif*" style "panel"
class "*Notif*" style "panel"
class "*Tray*" style "panel"
class "*tray*" style "panel"

style "menubar"
{
  bg[NORMAL] = "#5A5A5A"
}

widget_class "*Menubar*"      style "menubar"
widget "*Menubar*"            style "menubar"
class "*Menubar*"             style "menubar"

this is what I get:
[IMG]http://i3.photobucket.com/albums/y62/PatrickDDRX/desktop-1.png[/IMG]

I can't seem to change the color of the drop down color of the menu. and the user part on the top panel seems to stay white. The drop down menus are still white with black text. I want to change the color of them.

another question: how do I change the border color of the items on the bottom panel. it is completely black, but I want to have a border color around them.

I am new to this, and I tried google but everything there confused me.

---

### Post by dabugas on 2008-12-21
I'd have to see and fiddle with the gtkrc to see what the problem is, which I don't have the time to do :)

Why don't you have a look at a hybrid theme such as Shiki-Colors and see what he does?
[http://gnome-look.org/content/show.php/Shiki-Colors?content=86717](http://gnome-look.org/content/show.php/Shiki-Colors?content=86717)

If you're not planning to release the theme and are just looking for a quick fix you can right click on the panel, click Properties, go to the Background tab, and manually enter the colour you want. I think that should work.

---

### Post by PatrickIIDX on 2008-12-22
the user part looks better now that it paints in black editing the preferences, but the only problem is it doesn't change the text of the user switch panel to white. Its really cool that you can use a background image and make it transparent like windows vista too!

I tried installing a new theme but that was too confusing. I just want to make my own personal theme. so what I need to do is change the color of the drop down menu.

Dark Color, with white text. I'm going to mess around with the gtkrc-2.0 file because there was one theme that had it, and it made it look cool. let me know if theres a certain script I should put in that could help to save me the hassle. thanks.

---

### Post by x1a4 on 2008-12-22
Hi,
Instead of editing .gtkrc-2.0 edit .gtkrc.mine.  Whenever you use a GUI to change the look (Gnome Control Centre, gtk-chtheme, etc) .gtkrc-2.0 will be overwritten.  Just make sure that you have 
```
include "/home/yourusername/.gtkrc.mine"
```
in .gtkrc-2.0.

---

### Post by PatrickIIDX on 2008-12-22
if possible I just want to add it manually. i'll probably try searching and downloading a theme that suits me. thx for the include part.

---

