---
title: "Changing window button icon size on xfce4-panel"
date: 2012-08-11
forum: Desktop Environments
---

### Post by [o_0] Rob on 2012-08-11
I'm trying to increase the size of Window Button icons in xfce 4.8's panel.

I tried adding the following to ~/.gtkrc-2.0:

```

style "xfce-tasklist-style"
{
XfceTasklist::max-button-size = 70
}
class "XfceTasklist" style "xfce-tasklist-style"

```

This only seems to work when "Show Button Labels" setting is not selected. When the window buttons have text, the icons go back to being small. Is there a way increase the icon size when the window buttons have text labels?

---

### Post by black veils on 2012-08-11
they adjust when you adjust the panel size:

right-click the panel >> **panel** >> **panel preferences** >> the **size** is somewhere on one of those tabs

---

### Post by [o_0] Rob on 2012-08-14
Thanks black veils. That doesn't seem to change the size of the icons though.

This is what I'm trying to do:

[IMG]http://i.imgur.com/Le5qm.png[/IMG]

---

### Post by nickless on 2012-12-26
I'm trying to do this as well. Furthest I came was this ominous line in the xfce documentation:
> You can set a custom icon size in gtk-icon-sizes with the name panel-tasklist-menu. The default icon size is 16px. 
[http://docs.xfce.org/xfce/xfce4-panel/tasklist](http://docs.xfce.org/xfce/xfce4-panel/tasklist)

I tried to do this by changing

```
<property name="IconSizes" type="empty" />
```
to
```
<property name="IconSizes" type="string" value="gtk-menu=32,32:gtk-button=32,32:panel-applications-menu=32,32:panel-directory-menu=32,32:panel-tasklist-menu=32,32"/>
```

in

 ~/.config/xfce4/xfconf/xfce-perchannel-xml/xsettings.xml 

Effectively changing the size of most of the icons except those in my panel... :(

---

### Post by SantaFe on 2012-12-26
Hope you find out how to do this,not only for your sake, but  it bugs me also.  Even tried editing my themes gtkrc file.

gtk-icon-sizes	= "gtk-large-toolbar=16,16: gtk-small-toolbar=16,16: panel-menu=16,16: gtk-button=16,16" # This enables "compact-mode".

Tried changing the first numbers from 16,16 to 32,32.  Saved the file & rebooted,  Same thing, tiny icons still.  Even commented the line out.  Same thing!  Durn it. ;)

---

### Post by nickless on 2012-12-27
I didn't try the gtkrc in my theme until now. If something should work, I figure it would be:
```
gtk-icon-sizes = "panel-tasklist-menu=32,32"
```
But of course this didn't work as well. I also tried to add this to ~/gtkrc-2.0 with no success. I believe this could be a bug. 
I opened a [questing on askubuntu]("http://askubuntu.com/questions/233200/how-to-increase-icon-size-of-xfce4-panel-window-buttons-panel-tasklist-menu") and will wait if someone there can help. If this fails as well I will contact the author of the tasklist-widget. :I

---

