---
title: "Desktop Font Color"
date: 2007-03-31
forum: Desktop Effects &amp; Customization
---

### Post by c-breakdown on 2007-03-31
I really like to use the transparent panels and I'd really like to try out some dark backgrounds.  However, if I do that I can no longer view the time, temperature, et cetera.  

Is there somewhere that I can change the font color in my panels to white?

[Click Here For Screenshot]("http://i17.photobucket.com/albums/b66/hoo1igan/Screenshot-3.png")

---

### Post by Techman010 on 2007-03-31
Yeah.  I have been trying to figure that out also...  It would be really helpful.

---

### Post by notwen on 2007-04-01
You can do this by following the how-to [here]("http://ubuntuforums.org/showthread.php?t=334570"), but once I did this, I had white text on top of all my light colored menus(other than my main gnome panel which is transparent w/ a dark BG).  If you figure out a way to change the menu background color as well, please toss some info back.  Hope this helps. =]

---

### Post by c-breakdown on 2007-04-01
Ahhh, I don't think I'll change it until I figure out the menu thing.  Thanks for the info and the heads up. :D

---

### Post by Hank_61 on 2007-04-01
Well, if you want to change the font color of the top and bottom gnome panels **WITHOUT** changing your menu text color, just do this instead of the one that's linked in the post above.


Open the terminal and type in gedit .gtkrc-2.0

Then hit enter of course.

Paste this into the text document that opens:

>  include "/home/autocrosser/.gnome2/panel-fontrc"style "desktop-icon"

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
fg[NORMAL] = "[COLOR="Red"]#ffffff[/COLOR]"
}
widget "*PanelWidget*" style "my_color"
widget "*PanelApplet*" style "my_color"
widget_class "*MenuItem*" style "000000"
widget_class "*ToolItem*" style "000000"
widget_class "*SeparatorMenuitem*" style "000000"
widget_class "*SeparatorToolitem*" style "000000"
widget_class "*ImageMenuitem*" style "000000"
widget_class "*RadioMenuitem*" style "000000"
widget_class "*CheckMenuitem*" style "000000"
widget_class "*TearoffMenuitem*" style "000000"


Change the red text above to whatever color you like.

The difference between this one and the one in the link above is that, if you look at bottom half of the text you'll see, only *widget "*PanelWidget*"* and *widget "*PanelApplet*"* are changed to "my_color". This leaves the rest of the colors black.

And make sure you SAVE before closing the text doc. Also, if it looks like the color hasn't been changed, that's because you have to log out of your user account and then log back in to see the changes to the panels.

That's what worked for me anyway. Hope it works for others as well.

---

### Post by notwen on 2007-04-01
Sweet, I'll be sure to try this when I get home.  Thanks for the info.  Any idea if it is possible to change your menu backgrounds as well?  I'd be happy w/ making them transparent, as long as I can specify my font color to not blend in w/ my current desktop background.  I'll post back and letcha know if it works for me.

---

### Post by c-breakdown on 2007-04-01
Worked perfectly, thanks!

---

### Post by notwen on 2007-04-03
This worked great.  Anyone know if making gnome menus from the main panel transparent is even possible?

---

### Post by tbuss on 2007-04-04
**I tried **
```

include "/home/autocrosser/.gnome2/panel-fontrc"style "desktop-icon"

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
[COLOR="Red"]{
fg[NORMAL] = "#FBEF55"[/COLOR]
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

The only changes that took place are on the menu bar on **gedit for .gtkrc-2.0**? Nothing else is affected. If I close out gedit and open another file, the menu bar at top has black text and the context menu is also black. If I open .gtkrc-2.0 in gedit then the menu bar for gedit has yellow text and yellow context menu text. I though this was for changing the gnome panel font color? **The only time the changes take place is when I actually open the script in gedit, and gedit is the only thing affected.**

Anyone have any ideas?

---

### Post by tbuss on 2007-04-04
Also, I tried using the script offered in this thread.
When I save the file and try to open it again I get this:

```
tbuss@tbuss-desktop:~$ gedit .gtkrc-2.0
/home/tbuss/.gtkrc-2.0:20: error: invalid string constant "000000", expected valid string constant

```

---

### Post by autocrosser on 2007-04-05
Wow--I wrote that script quite a while ago (I'm autocrosser)--see the gnome color scheme post for more info & I'll post some info tonight (I'm at work right now).
 
Take a look at this thread: [http://ubuntuforums.org/showthread.php?t=289426](http://ubuntuforums.org/showthread.php?t=289426) You can modify Blue Test Alpha to death if you want
(it turns EVERYTHING blue ;) )

---

### Post by autocrosser on 2007-04-05
OK for more information about theme work:  [http://developer.gnome.org/doc/API/2.0/gtk/index.html](http://developer.gnome.org/doc/API/2.0/gtk/index.html)

For "practical" use:  [http://live.gnome.org/GnomeArt/Tutorials](http://live.gnome.org/GnomeArt/Tutorials)

& ask if you need more info!!!

---

### Post by notwen on 2007-04-06
I'll read up on this and letcha know if I have any questions. Thanks for the reference. =]

---

### Post by Jhongy on 2007-04-18
Just out of interest, where are people getting these nice background images for their Gnome panels? I don't want to download a whole theme, I just want an image or two to play with.

---

### Post by notwen on 2007-04-20
Since using Hank's posted gtkrc-2.0 setup, my icons text is now black surrounded by a white background. Is there anyway to keep my white menus in gnome-panel, but keeping my icons text background transparent?

---

### Post by IsKall on 2007-07-18
how did you do that? Getting black text color on white background?

---

### Post by notwen on 2007-07-18
Found a solution in this [thread]("http://ubuntuforums.org/showthread.php?t=89197").  It will eliminate the black text w/ white background for your desktop icons.

---

