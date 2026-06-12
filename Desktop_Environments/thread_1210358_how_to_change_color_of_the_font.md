---
title: "how to change color of the font??"
date: 2009-07-11
forum: Desktop Environments
---

### Post by chinmaya_n on 2009-07-11
I would like to change the color of the font on the desktop.....!!

I could change the font style but i could not the color them....:p

Thanx

---

### Post by SonnHalter on 2009-07-11
the only way I know how is to actually go in and edit your current theme's settings. so if you had clearlooks, you'd have to go and edit the source code and change font color to #ffffff or #2b2b2b ect.

---

### Post by chinmaya_n on 2009-07-13
Is that the only way we can change the colors.

Does anyone tried to change the color? plz help me

---

### Post by chinmaya_n on 2009-09-10
i guess this may change color of text in all applications!! (i didnt tried)

Can we change only to the desktop text i.e only for icons!

---

### Post by TopEnder on 2009-09-10
chinmaya_n,  You could have a look at Gnome-Color Chooser, it maybe what you are looking for or you could install the package using: [COLOR="Blue"]sudo apt-get install gnome-color-chooser[/COLOR].  TopEnder

---

### Post by kerry_s on 2009-09-10
**sudo apt-get install gnome-color-chooser**

careful it's addicting, nerve recking, maddening. :lolflag:

oops, i'm slow.

---

### Post by mcduck on 2009-09-10
Changing the desktop font color is possible by using a .gtkrc-2.0 file in your home directory. But note that the change applies to icons in file manager windows as well, since Nautilus handles the desktop and doesn't make much of a difference between the desktop and other file manager windows.

Anyway, all you need to do is create a file called ".gtkrc-2.0" in your home directory, and then add the following piece of text into that file:

```

style "desktop-icon"
{
  text[NORMAL] = "#000000"
}
class "GtkWidget" style "desktop-icon"
```


Alternatively you can use the following piece of code, which would set the text color and also remove the shadow from the text:
```

style "desktop-icon"
{
  NautilusIconContainer::frame_text = 1
  text[NORMAL] = "#000000"
  NautilusIconContainer::normal_alpha = 0
  NautilusIconContainer::highlight_alpha = 255
  NautilusIconContainer::dark_info_color = "#222266"
  NautilusIconContainer::light_info_color = "#dddddd"
}
class "GtkWidget" style "desktop-icon"
```
(The info colors are used for additional information under the icons if you have any enabled at your default zoom level.)

When you are ready log out and back again to see the changes.

---

### Post by JackTheDipper on 2009-10-08
> **mcduck said:**
> Changing the desktop font color is possible by using a .gtkrc-2.0 file in your home directory. But note that the change applies to icons in file manager windows as well, since Nautilus handles the desktop

so far it's true ;-)

> **mcduck said:**
> and doesn't make much of a difference between the desktop and other file manager windows.


but this doesn't mean that the look of both cannot differ.
Just use the following matching instead of the class "GtkWidget" [..] line:
```

widget_class "*DesktopIcon*" style "desktop-icon"

```

or simply use GNOME Color Chooser which handles that for you. ;)

Best regards,
JackTheDipper

---

### Post by JackTheDipper on 2009-10-08
> **kerry_s said:**
> **sudo apt-get install gnome-color-chooser**

careful it's addicting, nerve recking, maddening. :lolflag:

oops, i'm slow.

Hey, kerry_s. I quoted you at [http://gnomecc.sourceforge.net](http://gnomecc.sourceforge.net) and I hope that this is ok for you..? Just love this sentence! ;)

---

### Post by chinmaya_n on 2009-10-31
> **kerry_s said:**
> **sudo apt-get install gnome-color-chooser**



I installed this but it don't 've an option to change the desktop text color! where as it can change the background color of the text !!

---

### Post by cmschoonbee on 2009-11-08
Install package gnome-color-chooser
Open the program: System > Preferences > Gnome Color Chooser (Can take a while to open up.)
Click on the Desktop tab.
Change the settings to look like the attached screenshot.
Note that to change the color, e.g. for Text, you have to check the check box and then double-click on the color box. This allows you to pick a color. I find using the eyedropper the most convenient way of picking a color.

The settings I have given will give a black text color with a transparent background for the desktop icon label.  When you hover over the icon with the mouse it will change to white text on a black backround.

This should be enough to get you started and making further changes e.g you can deactivate hover effects if you want.

---

### Post by chinmaya_n on 2009-11-09
I'm really thanx to all .........

and specially to _cmschoonbee_
After a long time i realised my dream ... thanx!

Ru good at CMS ? mr.cmschoonbee... i got this doubt b'se of ur name ! 
i would like to learn it, so asking....!

---

### Post by Gargoulf on 2011-11-10
Seems gnome color chooser has no effect on 11.10!! Anyone has found solution to this?

---

### Post by overdrank on 2011-11-10
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]

---

