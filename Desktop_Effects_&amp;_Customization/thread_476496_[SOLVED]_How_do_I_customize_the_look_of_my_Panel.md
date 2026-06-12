---
title: "[SOLVED] How do I customize the look of my Panel?"
date: 2007-06-17
forum: Desktop Effects &amp; Customization
---

### Post by waggygee on 2007-06-17
I've been "pimpin'" my Ubuntu7.04, I'm using Beryl with Emerald and I wanted to customize the look of my panel.... surprisingly I found that I lacked the knowledge on the 'HowTo'.... I wanted to add a cool look other than just making it transparent.... anyone know how and feel like sharing?

---

### Post by diskotek on 2007-06-17
i think you can use some of your magination & cool icons for your panels. you can make a narrow - auto hide, transparent bottom (or top) panel for startters with cool icons of your taste. that's my formula. but there are few nice programmes (too complicated for me) check it out.
[http://lifehacker.com/software/featured-linux-download/awn-linux-application-dock-264328.php](http://lifehacker.com/software/featured-linux-download/awn-linux-application-dock-264328.php)

---

### Post by arist0tle on 2007-06-17
It's pretty easy actually depending on what you want to do. If you want to add a glassy look to you menu bar use gimp (there are tons of tutorials on this.... make sure you pay attention to the pixel height. Mine is 25(height) x 7 (width) ... it gets tiled across).If you want to add a custom menu button (similar to the start button in windowz), open the configuration editor in System tools and go to apps->panel->objects->object_?(mine is 0) and select the use_custom_icon checkbox them select the key for custom icon and choose the path of your custom icon. if you want to change the font color of your panel you have to create a file called  .gtkrc-2.0 (notice the period at the beginning...hidden file) and paste this into it:

style "panel"
{
# fg[NORMAL]               = "#ffffff"
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
 	 	

the first line is the font color for the panel. Uncomment it (remove the pound sign) and replace #ffffff with whatever color you want the text to be. Put that file into your home directory, log out and then back in and the changes will have taken effect. That is really all that i do.

---

### Post by waggygee on 2007-06-17
> **diskotek said:**
> i think you can use some of your magination & cool icons for your panels. you can make a narrow - auto hide, transparent bottom (or top) panel for startters with cool icons of your taste. that's my formula. but there are few nice programmes (too complicated for me) check it out.
[http://lifehacker.com/software/featured-linux-download/awn-linux-application-dock-264328.php](http://lifehacker.com/software/featured-linux-download/awn-linux-application-dock-264328.php)

I was searching that site. There a simple HowTo. Im installing it now...... [http://awn.wetpaint.com/page/UbuntuFeistyHowTo](http://awn.wetpaint.com/page/UbuntuFeistyHowTo)

---

### Post by waggygee on 2007-06-17
> **arist0tle said:**
> It's pretty easy actually depending on what you want to do. If you want to add a glassy look to you menu bar use gimp (there are tons of tutorials on this.... make sure you pay attention to the pixel height. Mine is 25(height) x 7 (width) ... it gets tiled across).If you want to add a custom menu button (similar to the start button in windowz), open the configuration editor in System tools and go to apps->panel->objects->object_?(mine is 0) and select the use_custom_icon checkbox them select the key for custom icon and choose the path of your custom icon. if you want to change the font color of your panel you have to create a file called  .gtkrc-2.0 (notice the period at the beginning...hidden file) and paste this into it:

style "panel"
{
# fg[NORMAL]               = "#ffffff"
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
 	 	

the first line is the font color for the panel. Uncomment it (remove the pound sign) and replace #ffffff with whatever color you want the text to be. Put that file into your home directory, log out and then back in and the changes will have taken effect. That is really all that i do.

You lost me after I clicked the custom_icon checkbox......... Where can I get those custom icons? Is there an easier way? Like some software or something.

---

### Post by waggygee on 2007-08-02
I found it's much easier to get an image of a panel/bar and then set the panel to show a background image (setting the image as the desired look/task bar or what ever design)

---

