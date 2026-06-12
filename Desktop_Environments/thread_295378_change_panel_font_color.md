---
title: "change panel font color"
date: 2006-11-08
forum: Desktop Environments
---

### Post by u534_n4m3 on 2006-11-08
how do you change the panel's font color?

thanks

---

### Post by Synikk on 2006-11-08
> **u534_n4m3 said:**
> how do you change the panel's font color?

thanks

[This]("http://brentroos.com/2006/07/07/change-gnome-panel-text-color/") might help.

---

### Post by u534_n4m3 on 2006-11-08
> **Synikk said:**
> [This]("http://brentroos.com/2006/07/07/change-gnome-panel-text-color/") might help.


it doesn't work for me

first of all, i don't have a .gtkrc-2.0 file.  i have a .gtkrc-1.2-gnome file.  i tried editing that, nothing happened.  i tried creating a .gtkrc-20 file, also nothing

---

### Post by Charvell on 2006-11-10
I have the same problem. The file created doesn't work.

When I click on the places bar and then click on home the window opens and there is the file. Directions say to place it in the home folder, although this folder does not exist, I assume it to be my personal user folder?

---

### Post by Charvell on 2006-11-10
Unable to save anything in the home folder. These permissions are a real pain in the but. I would like to be able to make mistakes. I don't need a baby sitter.

---

### Post by togume on 2006-12-02
Easy Charvell. The permissions are acutally a nice feature which adds an extra level of security.

In order to execute commands as root, simply append a <sudo> at the beginning of the command: i.e. sudo mkdir yourdir.

if you don't have the .gtkrc-2.0, make one, and add the following:

```
style "panel"
{
fg[NORMAL]               = "#ffffff"
#  fg[PRELIGHT]            = "#000000"
#  fg[ACTIVE]               = "#ffffff"
#  fg[SELECTED]            = "#000000"
#  fg[INSENSITIVE]            = "#8A857C"

#  bg[NORMAL]               = "#000000"
#  bg[PRELIGHT]            = "#dfdfdf"
#  bg[ACTIVE]               = "#D0D0D0"
#  bg[SELECTED]            = "#D8BB75"
#  bg[INSENSITIVE]            = "#EFEFEF"

# base[NORMAL]            = "#ffffff"
#  base[PRELIGHT]            = "#EFEFEF"
#  base[ACTIVE]            = "#D0D0D0"
#  base[SELECTED]            = "#DAB566"
#  base[INSENSITIVE]         = "#E8E8E8"

#  text[NORMAL]            = "#161616"
#  text[PRELIGHT]            = "#000000"
#  text[ACTIVE]               = "#000000"
#  text[SELECTED]            = "#ffffff"
#  text[INSENSITIVE]            = "#8A857C"
}
widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
class "*Panel*" style "panel"
widget_class "*Mail*" style "panel"
class "*notif*" style "panel"
class "*Notif*" style "panel"
class "*Tray*" style "panel"
class "*tray*" style "panel"
```

That's it. Restart x by rebooting, logging out and logging back in, or pressing <ctrl><alt><bkspace> at the same time.

---

### Post by brentroos on 2007-01-19
1[URL="http://brentroos.com/files/2007/01/gtkrc-20.txt"]
[/URL]

---

### Post by SqdnGuns on 2007-01-20
> **brentroos said:**
> [http://brentroos.com/files/2007/01/gtkrc-20.txt](http://brentroos.com/files/2007/01/gtkrc-20.txt)

Getting a 404 error for your site................

---

### Post by brentroos on 2007-01-23
> **SqdnGuns said:**
> Getting a 404 error for your site................

It's up and running now. I had some hacker try to ruin my reputation. 

Anyway, [I'm back on]("http://brentroos.com").

---

### Post by joskov on 2007-02-11
I had the same question as u534_n4m3 and was having the same problem: i would reset X and nothing would be changed (I would even restart just to make sure).  I found that (after playing around with the file .gtkrc-2.0) if you uncomment both the ```
fg[NORMAL] = "#ffffff"
``` and the ```
text[NORMAL] = "#ffffff"
``` the font color changes.

I am not sure if I did it the correct way or not, so please let me know if there is a problem in this method.

---

### Post by ardchoille42 on 2007-02-11
Does this help:

[http://www.gnomehelp.org/pmwiki/pmwiki.php?n=Gnome212.GnomePanelColour](http://www.gnomehelp.org/pmwiki/pmwiki.php?n=Gnome212.GnomePanelColour)

---

### Post by raul_ on 2007-02-13
Bret's script doesn't work for me. It has something to do with the "widget blablabla" parts, because the gnomehelp.org one does. The only problem is that it also changes the buttons colors, and that sucks.

For example, when i press Alt+f2 to run an application, the text is white, so i can't see anything. This happened because i added the selected,prelight, etc etc, lines because i don't like the text color to change when my mouse hovers it, or when i click it.

Is there anyway to override this?

Ok, i think i got it. this is a mix of those scripts:

```

include "/home/autocrosser/.gnome2/panel-fontrc" style "desktop-icon"

{
NautilusIconContainer::frame_text = 1
text[NORMAL] = "#000000"
NautilusIconContainer::normal_alpha = 70
}

class "GtkWidget" style "desktop-icon"

#NautilusIconContainer::dark_info_color="#888888"
#NautilusIconContainer::light_info_color="#bbbbbb"
#NautilusIconContainer::highlight_alpha=200

style "my_color"
{
fg[NORMAL] = "#ffffff"
fg[PRELIGHT]            = "#DBC8C8"
fg[ACTIVE]               = "#DBC8C8"
fg[SELECTED]            = "#DBC8C8"
fg[INSENSITIVE]            = "#ffffff"
}
widget "*PanelWidget*" style "my_color"
widget "*PanelApplet*" style "my_color"
widget_class "*MenuItem*" style "my_color"
widget_class "*ToolItem*" style "my_color"
widget_class "*SeparatorMenuitem*" style "my_color"
widget_class "*SeparatorToolitem*" style "my_color"
widget_class "*ImageMenuitem*" style "my_color"
widget_class "*RadioMenuitem*" style "my_color"
widget_class "*CheckMenuitem*" style "my_color"
widget_class "*TearoffMenuitem*" style "my_color"

```

Double EDIT:

Ok i THOUGHT i got it. Here's a screenshot. See how the menu in Gimp is unreadable?

Plus, the icon containers are horrible, and now that i logged out ALL the menus are unreadable. This is getting tough :cool:

---

### Post by raul_ on 2007-02-13
Ok, NOW it's done. I had to remove the first blocks, and some of the last lines. Here is the script and a screenie.

```
style "my_color"
{
fg[NORMAL] = "#ffffff"
fg[PRELIGHT]            = "#DBC8C8"
fg[ACTIVE]               = "#DBC8C8"
fg[SELECTED]            = "#DBC8C8"
fg[INSENSITIVE]            = "#ffffff"
}
widget "*PanelWidget*" style "my_color"
widget "*PanelApplet*" style "my_color"
```

---

