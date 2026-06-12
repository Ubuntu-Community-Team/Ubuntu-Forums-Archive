---
title: "Desktop background color and inverted font color"
date: 2007-12-30
forum: Desktop Effects &amp; Customization
---

### Post by timzak on 2007-12-30
Two questions on Gutsy (not Gusty!):

1) when logging in I always see that tan background color slightly before my wallpaper kicks in.  How do I change this color?  I already changed the color under Appearance Preferences->Background Tab->Colors and it doesn't keep the tan background from showing itself.

2) I am using a white-themed wallpaper and font text on the desktop icons is hard to read because it too is white with a black border.  I don't see any way to change this color in any of the sub menus of Appearance Preferences.

Any help on these two items is greatly appreciated.

---

### Post by hhhhhx on 2007-12-30
1: Adminastration > login window 
           just change the settings.

2: I dont know what you are taking about

---

### Post by Forlong on 2007-12-30
> **timzak said:**
> 1) when logging in I always see that tan background color slightly before my wallpaper kicks in.  How do I change this color?
```
sudo gedit /etc/gdm/PreSession/Default
```
look for
```
# Default value  
      if [ "x$BACKCOLOR" = "x" ]; then  
              BACKCOLOR="#dab082"  
      fi  
```
and change it to
```
# Default value  
      if [ "x$BACKCOLOR" = "x" ]; then  
              BACKCOLOR="x"  
      fi  
```
Afterwards you should be able to change the color in *System &#8594; Administration &#8594; Login Screen &#8594; Local*
> 2) I am using a white-themed wallpaper and font text on the desktop icons is hard to read because it too is white with a black border.
```
gedit .gtkrc-2.0
```
Put this in there:
```
style "desktop-font-color"
{
 NautilusIconContainer::frame_text = 1
 NautilusIconContainer::normal_alpha = 0
 text[NORMAL] = "#000000"
}
class "GtkWidget" style "desktop-font-color"
```
Then save.

This will make your desktop font solid black after you log in next time.

---

### Post by timzak on 2007-12-31
Forlong,

Wow!  That was exactly the help and info I needed.  Thank you SO MUCH! :guitar:

---

