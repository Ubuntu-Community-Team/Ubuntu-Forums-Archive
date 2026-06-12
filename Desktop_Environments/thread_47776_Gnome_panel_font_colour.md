---
title: "Gnome panel font colour"
date: 2005-07-09
forum: Desktop Environments
---

### Post by TestDummy! on 2005-07-09
I really have no clue where to ask this...

But, does anybody know how to change the colour of the font on the main Gnome panel? (You know, the one with "Applications, Places, System", etc.) 

I want to change the text colour on the panel to white while still keeping it completely transparent. I know I could just make it opaque, but I think it looks weird that way. 

I've poked around but really have not a clue on how I'd change this. 

Any ideas?  :???:

---

### Post by TestDummy! on 2005-07-12
Is it possible to do this or not?

I'm not sure, but I've asked here, and on IRC and nobody seems to have any clue whatsoever if it can be done.

---

### Post by agapito on 2005-11-15
I have a way to do it. Try this:
In ~/.gtkrc-2.0 insert this line

include "/home/<user_name>/.gnome2/panel-fontrc"

then create the file panel-fontrc in .gnome2, which consists of the following lines:

style "my_color"
{
fg[NORMAL] = "#4353b6"
}
widget "*PanelWidget*" style "my_color"
widget "*PanelApplet*" style "my_color"

and that's it. All you have to do is choose the color and do a killall gnome-panel. The second "widget" line affects only the applets and the first one does the rest.
To chose the color you can use the color select dialog in GIMP or, even better, use this:
[http://gcolor2.sourceforge.net/](http://gcolor2.sourceforge.net/)
it allows you to pick colors from anywhare in the gnome desktop. It compiled smothly in Hoary.

Have fun! :smile:

---

### Post by yyagol on 2005-11-17
Hey thenks for that small but realy nice how to
but after i did that the clock did not want to
become transerant any more .
how can i fix that ?

---

### Post by kperkins on 2005-11-17
[QUOTE=agapito] use this:
[http://gcolor2.sourceforge.net/](http://gcolor2.sourceforge.net/)
it allows you to pick colors from anywhare in the gnome desktop. It compiled smothly in Hoary.

Have fun! :smile:[/QUOTE]
Thanks for that--I've used it to replace Kcoloredit/chooser--one more step to a KDE Free Desktop.
Now to find a replacement for K3B. :D

---

### Post by agapito on 2005-11-22
[QUOTE=kperkins]Thanks for that--I've used it to replace Kcoloredit/chooser--one more step to a KDE Free Desktop.
Now to find a replacement for K3B. :D[/QUOTE]

I've been using Graveman and Gnome Baker. Graveman has a really nice and simple user interface plus you can drag&drop items from the browser into a CD compilation. I think it's a pretty good replacement for K3B.

Try them out! :)

---

### Post by abh83 on 2007-02-24
> **agapito said:**
> I have a way to do it. Try this:
In ~/.gtkrc-2.0 insert this line

include "/home/<user_name>/.gnome2/panel-fontrc"

then create the file panel-fontrc in .gnome2, which consists of the following lines:

style "my_color"
{
fg[NORMAL] = "#4353b6"
}
widget "*PanelWidget*" style "my_color"
widget "*PanelApplet*" style "my_color"

and that's it. All you have to do is choose the color and do a killall gnome-panel. The second "widget" line affects only the applets and the first one does the rest.
To chose the color you can use the color select dialog in GIMP or, even better, use this:
[http://gcolor2.sourceforge.net/](http://gcolor2.sourceforge.net/)
it allows you to pick colors from anywhare in the gnome desktop. It compiled smothly in Hoary.

Have fun! :smile:

Just out of curiosity:

Since we are now in the year 2007... does ubuntu edgy 6.11 have this feature built in and with a nice gui? :D

ABH

---

### Post by rainai2k7 on 2008-01-08
Thanks for this!!!

One thing more, though.  Is it possible to also change the font color of that "User Switcher" panel applet (whatever you call it)?  How?  Its font color stays black on my panel.  (I'm very new to Ubuntu and Linux in general.)

---

### Post by mcduck on 2008-01-09
> **agapito said:**
> 
To chose the color you can use the color select dialog in GIMP or, even better, use this:
[http://gcolor2.sourceforge.net/](http://gcolor2.sourceforge.net/)
it allows you to pick colors from anywhare in the gnome desktop. It compiled smothly in Hoary.

Have fun! :smile:

By the way, gcolor2 is in Ubuntu repositories, so there's no need to compile it yourself ;)

---

### Post by LukeCarrier on 2008-02-12
To change the colour of the fast user switching applet, open the file to edit the colours using:
```

gedit .gtkrc-2.0

```Then add these lines into the file:
```

style "modpanel"
{
fg[NORMAL] = "#FFFFFF"
}
widget "*PanelWidget*" style "modpanel"
widget "*PanelApplet*" style "modpanel"
widget "*fast-user-switch-applet*" style "modpanel"

```Now run this code to reload the panels:
```

killall gnome-panel

```And you've got modded panels. Just replace the 3rd line with whatever colour you'd like the text to be.
Hope this helps!

---

### Post by restless on 2008-02-15
hey!!

an easy and very effective one!!! great..thank you!
Lorenzo

---

### Post by drzoo2 on 2008-03-08
> **LukeCarrier said:**
> To change the colour of the fast user switching applet, open the file to edit the colours using:
```

gedit .gtkrc-2.0

```Then add these lines into the file:
```

style "modpanel"
{
fg[NORMAL] = "#FFFFFF"
}
widget "*PanelWidget*" style "modpanel"
widget "*PanelApplet*" style "modpanel"
widget "*fast-user-switch-applet*" style "modpanel"

```Now run this code to reload the panels:
```

killall gnome-panel

```And you've got modded panels. Just replace the 3rd line with whatever colour you'd like the text to be.
Hope this helps!

Kudos. Worked great!
Thanks!
z

---

### Post by rugbeeprop on 2008-05-25
> **LukeCarrier said:**
> To change the colour of the fast user switching applet, open the file to edit the colours using:
```

gedit .gtkrc-2.0

```Then add these lines into the file:
```

style "modpanel"
{
fg[NORMAL] = "#FFFFFF"
}
widget "*PanelWidget*" style "modpanel"
widget "*PanelApplet*" style "modpanel"
widget "*fast-user-switch-applet*" style "modpanel"

```Now run this code to reload the panels:
```

killall gnome-panel

```And you've got modded panels. Just replace the 3rd line with whatever colour you'd like the text to be.
Hope this helps!


Thanks... works great :guitar:

---

### Post by didwah on 2008-06-11
Hi There

What change would I make to have the font heavier/stronger than shown in this thread?

---

