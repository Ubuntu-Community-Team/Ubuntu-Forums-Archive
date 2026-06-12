---
title: "Simple one, changing font color on panels..."
date: 2006-07-19
forum: Desktop Environments
---

### Post by BayGuy27 on 2006-07-19
Hello, I cannot figure out how to change the font color on such things as the clock and weather report. Very hard to see black text over a blue panel. But I do have the Window List over a white background and would not want the font color of open programs to change to white. Is this possible? Thanks in advance,

Dave

---

### Post by spiral777 on 2006-08-08
Ok, this is blatantly stolen from a blog I frequent, so I'll link back there.

[Brent Roos: The Power of Truth]("http://brentroos.com/2006/07/07/change-gnome-panel-text-color/")

Open the terminal and type:

```
gedit .gtkrc-2.0
```

Insert the following into this file:

```
style "panel"
{
# fg[NORMAL] = "#ffffff"
# fg[PRELIGHT] = "#000000"
# fg[ACTIVE] = "#ffffff"
# fg[SELECTED] = "#000000"
# fg[INSENSITIVE] = "#8A857C"
# bg[NORMAL] = "#000000"
# bg[PRELIGHT] = "#dfdfdf"
# bg[ACTIVE] = "#D0D0D0"
# bg[SELECTED] = "#D8BB75"
# bg[INSENSITIVE] = "#EFEFEF"
# base[NORMAL] = "#ffffff"
# base[PRELIGHT] = "#EFEFEF"
# base[ACTIVE] = "#D0D0D0"
# base[SELECTED] = "#DAB566"
# base[INSENSITIVE] = "#E8E8E8"
# text[NORMAL] = "#161616"
# text[PRELIGHT] = "#000000"
# text[ACTIVE] = "#000000"
# text[SELECTED] = "#ffffff"
# text[INSENSITIVE] = "#8A857C"
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

Next, uncomment the part that says:

```
# fg[NORMAL] = "#ffffff"
```

So it looks like:

```
fg[NORMAL] = "#ffffff"
```

Save this file. It will be saved as .gtkrc-2.0 in your home directory. You do not need to do save as, unless your terminal is opened in another directory besides your home directory.

Note: you will not see this file in normal view. The “.” in front of the filename makes the file hidden. You can see all of your hidden files in Nautilus by selecting view -> show hidden files.

To explain, the #ffffff represents the color white. You can change this:

```
fg[NORMAL] = "#ffffff"
```

to allow our Gnome panel to have a different text color besides black (#000000), which is the default. The rest of the lines in this are out of the scope of this solution. However, they are useful for other things which will not be discussed for this post.

The last step is to refresh the Gnome panel:


```
killall gnome-panel
```

---

### Post by PartisanEntity on 2006-11-27
Hello everyone, sorry for bringing back an old thread, but I don't seem to have a **.gtkrc-2.0** file in 'home'?

I am using Dapper.

Thank you in advance.

---

### Post by macewan on 2006-11-27
If you do not have the .gtkrc-2.0 file then create one with gedit

---

### Post by mack1082 on 2007-07-14
This is just what I was looking for, thanks!

---

