---
title: "Customizing Gnome panel"
date: 2005-10-23
forum: Desktop Environments
---

### Post by mrmcctt on 2005-10-23
Is there a way to change just the font color in the Gnome panel?  

I am using the Clearlook theme with the Gnome panel set to transparent on a dark background.  As you can see in the attached screenshot, there are two windows in the window list that are open but minimized (you should be able to barely make out the icons).  The font is black and so is the font for the clock when I have it running.  I have tried a couple of dark Clearlooks themes that have a light font in the panel but then I can't read the bookmarks toolbar in firefox.

Just an inconvenience really but I'd like to change it if I can.  There may be a HOWTO for this but if there is I didn't see it.

---

### Post by agapito on 2005-11-15
See my solution here:
[http://ubuntuforums.org/showthread.php?t=47776](http://ubuntuforums.org/showthread.php?t=47776)

It really works! :smile:

---

### Post by mrmcctt on 2005-11-15
I thank you for that but I have a question.  I don't have the file ```
~/.gtkrc-2.0
```  I have the file ```
.gtkrc-1.2-gnome2
```.

Does this mean I have to upgrade irst and if yes, how?  What would I need to upgrade?  Gnome?

Again, Thanks for your reply.

---

### Post by SickTwist on 2005-11-15
Just create a new file. Be sure that it is named correctly or else it will not be read. Start Gedit (Applications --> Accessories --> Text Editor) and create the contents of the file. Then save it as ".gtkrc-2.0" (without quotes) in your home directory. Don't forget the period at the beginning of the filename.

---

### Post by agapito on 2005-11-15
Don't worry. Breezy uses Gnome 2.12, which relies on Gtk2. You don't have a local configuration file for Gtk2 simply because it was never needed. Just create one, like SickTwist said.

If you have any color problems, tell me about it and I'll see what I can do.

---

### Post by Tiede on 2005-11-17
[QUOTE=agapito]Don't worry. Breezy uses Gnome 2.12, which relies on Gtk2. You don't have a local configuration file for Gtk2 simply because it was never needed. Just create one, like SickTwist said.

If you have any color problems, tell me about it and I'll see what I can do.[/QUOTE]

Ok, I hope you can help me with this. I have downloaded the *chaotic* Gtk-2 Theme from gnome-look.org, and now in some apps, I cannot see the text, because some programs only ask the theme for font color, not background color. I have included a thumbnail to illustrate. Now, I'd like to know how to change the font color to something else, (maybe a lite green)... Or if possible, have a blue background under the text as it was intended to be.

Thunbnail:
[[img=http://img123.imageshack.us/img123/2531/capture7xa.th.png]](http://img123.imageshack.us/my.php?image=capture7xa.png)

---

### Post by mrmcctt on 2005-11-17
[QUOTE=agapito]Don't worry. Breezy uses Gnome 2.12, which relies on Gtk2. You don't have a local configuration file for Gtk2 simply because it was never needed. Just create one, like SickTwist said.

If you have any color problems, tell me about it and I'll see what I can do.[/QUOTE]

Ok.  Here's what I have done.

Created the ~/.gtkrc-2.0 file.  Here are the contents: ```
include "/home/rlodge/.gnome2/panel-fontrc"
```

Next I created the ~/.gnome2/panel-fontrc (panel-fontrc was not in the /.gnome2 folder).  Here's what's in the panel-fontrc file:  ```
style "my_color"
{
fg[NORMAL] = "#4353b6"
}
widget "*PanelWidget*" style "fefe00"
widget "*PanelApplet*" style "fefe00"
```

I have tried to add the colors as "yellow" "FEFE00" "fefe00" and no luck.  I have done a ```
sudo killall gnome-panel restart
``` as well as a log out and log back in.  I also did a chmod on the ~/.gtkrc-2.0 since it was only 644 (rw-r-r).  To ease things I made it 777.

Any ideas why the font colors still won't change?  I thought I followed your instructions but maybe I missed something.

Thanks

Note:  I still have the ~/.gtkrc-1.2-gnome2 file in my home folder.  It's contents are: ```
# Autowritten by gnome-settings-daemon. Do not edit

include "/home/rlodge/.gtkrc.mine"
``` Could this be a conflicting file?  I cannot find the /home/rlodge/.gtkrc.mine which confuses me, also.

---

### Post by kperkins on 2005-11-17
write them "#fefe00" not "fefe00"

---

### Post by mrmcctt on 2005-11-17
[QUOTE=kperkins]write them "#fefe00" not "fefe00"[/QUOTE]

I should have seen that after all the times it caused me problems writing web pages. :rolleyes: 

Still did not fix the problem of the font color not changing after a ```
sudo killall gnome-panel restart
```

Thanks, though.  This may be one step closer.

---

### Post by kperkins on 2005-11-19
Try changing: 
```

style "my_color"
{
fg[NORMAL] = "#4353b6"
}


```
to:
```

style "my_color"
{
fg[NORMAL] = "#fefe00"
}


```

and change 
```

widget "*PanelWidget*" style "fefe00"
widget "*PanelApplet*" style "fefe00"

```
to
```

widget "*PanelWidget*" style "my_color"
widget "*PanelApplet*" style "my_color"

```

---

### Post by mrmcctt on 2005-11-19
Thank you kperkins.  That was what the problem was.  Looking at it now it should have been obvious, but....

Anyway, thanks to everyone for their help.

I attached a screenshot to show how it looks now.

---

### Post by kperkins on 2005-11-19
[QUOTE=mrmcctt]Thank you kperkins.  That was what the problem was.  Looking at it now it should have been obvious, but....

Anyway, thanks to everyone for their help.

I attached a screenshot to show how it looks now.[/QUOTE]

It _should_ have been obvious, but I didn't see it either untilk I looked at the code a couple of times. :D ](*,)

---

### Post by ColdWind on 2005-11-20
Do someone know how to do the same thing with the Gnome Panel menu?

---

### Post by autocrosser on 2005-11-20
My .gtkrc-2.0 file looks like---

include "/home/autocrosser/.gnome2/panel-fontrc"style "desktop-icon"

{
 NautilusIconContainer::frame_text = 1
 text[NORMAL] = "#9203c1"
 NautilusIconContainer::normal_alpha = 70 
}
class "GtkWidget" style "desktop-icon" 

#NautilusIconContainer::dark_info_color="#888888"
#NautilusIconContainer::light_info_color="#bbbbbb"
#NautilusIconContainer::highlight_alpha=200

style "my_color"
{
fg[NORMAL] = "#9203c1"
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


The *Menuitem* line is what you are looking for--I'm still looking for the way to get the last of my fonts to change----Anyone else know??

---

### Post by ColdWind on 2005-11-21
Thanks! Now I only need make the menu transparent. Is it possible?

---

### Post by autocrosser on 2005-11-21
I'll be looking into that over the next couple of weeks--going thru GTK docs is like walking thru quicksand:???:--I've got some ideas--but none postable yet---There is another thread in the Customization forum that I'm posting in too--I think that these two should be combined--Sticky anyone????

---

### Post by autocrosser on 2005-11-22
Well-I modified one of my themes to come up with about 95% of the fonts changing to the color I want--not the clean, little gtkrc-2.0 file I wanted---but see for your self--http://www.ubuntuforums.org/showthread.php?t=89197&page=3

The color is purple--but I allow any & everyone to change/modify/cut&paste/otherwise change any part to whatever you want:smile:

---

### Post by 23meg on 2005-11-22
There's [a $50 bounty in Launchpad]("https://launchpad.net/bounties/gnome-panel-font-colour") on making the panel font color adjustable via panel properties. Still open.

---

