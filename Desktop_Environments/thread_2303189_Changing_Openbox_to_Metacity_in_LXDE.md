---
title: "Changing Openbox to Metacity in LXDE"
date: 2015-11-16
forum: Desktop Environments
---

### Post by c_xy on 2015-11-16
Hello,

We've recently upgraded Ubuntu 14.04 LTS with LXDE as the DE.

Openbox is the default window manager.

Everything works fine, but we are accustomed to the look of GNOME 2 with Ubuntu 10.04.

Would switching to metacity as the window manager in LXDE give a similar look of the window appearances/shape of GNOME 2?

If so, what are the steps to make this change.

I tried the following command:

I installed metacity

```
sudo apt-get install metacity
```

Then used the following command:

```
lxsession-edit
```


changed openbox to metacity in the advanced options.

However, I then logged out and logged in and the window appearances look weird. Nothing like the gnome-2 look of metacity.

Am I missing any steps? 

Any help/suggestions are appreciated.


Thanks.

c.

---

### Post by Sweet_Baby_Jamie on 2015-11-17
LXDE depends on Openbox and won't work as well with a different window manager.  If you like the look of Gnome 2, I suggest the MATE desktop!

---

### Post by NathanRodriguez on 2015-11-17
+1 for MATE as a Gnome2 replacement. You can also get a similar look and feel with Xfce.

---

### Post by grahammechanical on 2015-11-17
Metacity is a window manager but it will need a suitable (looking like Gnome 2 panel) user interface sitting on top of it. Personally, I would not mess with alternate desktops. It can get very messy with configuration files conflicting. I suggest installing the full distribution rather than install an alternate desktop on Ubuntu

If all we want is a Gnome 2 panel look-a-like on Ubuntu then we can install Gnome Flashback Session. That will give us 2 additional login sessions. Gnome Flashback (Metacity) & Gnome Flashback (Compiz). It is a long time since I used 14.04 but I think Gnome Flshback Session is available in Ubuntu from 14.04 onwards.

Regards.

---

### Post by mcduck on 2015-11-17
Or how about just checking if there might be Openbox theme that looks like you'd like it? No need to replace the whole window manager, let alone the desktop you are using, just to change how window borders look like ;)

Head to [box-look.org]("http://box-look.org") and check what's available under the Openbox themes section...

(And why just changing the window manager to Metacity didn't give you the look you were after? The thing is there isn't any specific "look of Gnome 2". Just like pretty much anything else, Metacity uses themes, and unless you are doing something to set it to the theme you want, it's going to be pretty ugly...)

---

### Post by c_xy on 2015-11-20
Thank you for the feedback everyone.

I'll look into mate and xfce.

mcduck, I have question about trying some of the temes from box-look.org.

I've installed some of the themes, and selected them in the Openbox-Configuration-Menu.

For example:

[http://box-look.org/content/show.php/Ambiance+Crunchy?content=136162](http://box-look.org/content/show.php/Ambiance+Crunchy?content=136162)

However, it only changes the outer borders of the window (such as a terminal window, gedit window, etc.). But the panel color and other color do not change. I can't get them to look like the screenshots.

If I try to change with another DE, such as Mate or the old Gnome 2, the theme change would also affect other colors of the desktop (panel, etc) not just terminal window borders.

Is this just a limitation of OpenBox or am I missing some additional steps?

Thanks,

c

---

### Post by mcduck on 2015-11-21
Openbox is just a window manager, so Openbox themes only affect the windows themselves. (Same actually applies in other desktops, changing a Metacity theme in Gnome would only change window borders, for example, but the default customization options often just show you "complete" themes these days, instead of letting you select your GTK, window manager, and icon themes separately.). The colors and the look of applications themselves comes from the GTK theme instead. There might be some around at box-look.org, but you'll find plenty more at [gnome-look.org]("http://gnome-look.org/").

I have only ever tested LXDE briefly, so I don't remember what panel application it uses, and if that will use GTK theme or if it has themes or settings of it's own.

---

### Post by kansasnoob on 2015-11-22
[Trusty Flashback w/Metacity]("http://ubuntuforums.org/showthread.php?t=2220264") uses the new 'gnome-panel' (aka; 'gnome-session-flashback').

---

### Post by c_xy on 2015-11-27
> **mcduck said:**
> Openbox is just a window manager, so Openbox themes only affect the windows themselves. (Same actually applies in other desktops, changing a Metacity theme in Gnome would only change window borders, for example, but the default customization options often just show you "complete" themes these days, instead of letting you select your GTK, window manager, and icon themes separately.). The colors and the look of applications themselves comes from the GTK theme instead. There might be some around at box-look.org, but you'll find plenty more at [gnome-look.org]("http://gnome-look.org/").

I have only ever tested LXDE briefly, so I don't remember what panel application it uses, and if that will use GTK theme or if it has themes or settings of it's own.

Mcduck, thanks again for the feedback.

The "Customize Look and Feel" option in LXDE settings changes the other parts of the theme I was looking for, aside from the terminal/gedit window borders. I'll do some more experimenting, but your feedback helps a great deal.

Thanks again.

c

---

