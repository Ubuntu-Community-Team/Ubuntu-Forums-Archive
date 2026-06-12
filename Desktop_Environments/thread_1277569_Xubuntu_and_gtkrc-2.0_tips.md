---
title: "Xubuntu and gtkrc-2.0 tips?"
date: 2009-09-28
forum: Desktop Environments
---

### Post by frankwakeman on 2009-09-28
I've been experimenting with and to an extent researching gtkrc-2.0, first in Gnome Ubuntu and now in Xubuntu.  This has been mostly to advance the panel design (in both versions I delete the bottom panel and put the top one there) beyond the grey Windows 95 look.  I'm pleased with my Ubuntu desktop, which is practically indistinguishable from KDE now, but I'm still a bit stumped with Xubuntu.  There are 3 gtkrc-2.0 files below, numbered.  The first is my current Xubuntu one, and so far just gets rid of that unsubtle desktop icon background.  The second is my Gnome Ubuntu gtkrc-2.0 file, which gives me white text on my darker panel background (without mucking up the rest of the gtk theme), which at the moment is a Kubuntu-like semi-transparent one.  The third is one I found online which enables a flawed panel background in Xubuntu - flawed because panel icons aren't in sync.  I've as a compromise used a version of this, replacing mention of the pixmap with a grey colour I like, #353535, with which white text sits well.  I imagine some hybrid of all three will give me what I want, where the applications & places menus when selected don't leave a merely grey selection colour when they're clicked on.  In 2. I managed to achieve this, but at first I just pasted the relevant detail from 2. (from 'widget' onwards) into 1., which proved unsuitable - obviously XFCE requires a slightly different format somehow.  I've seen a few gtkrc-2.0 boffins gives replies here, that'd be appreciated.




1.

style "xfdesktop-icon-view" {
    XfdesktopIconView::label-alpha = 0

    base[NORMAL] = "#ffffff"
    base[SELECTED] = "#ffffff"
    base[ACTIVE] = "#ffffff"

    fg[NORMAL] = "#ffffff"
    fg[SELECTED] = "#ffffff"
    fg[ACTIVE] = "#ffffff"
}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"


2.

bg[NORMAL] = "#353535"
bg[PRELIGHT] = "#353535"
bg[ACTIVE] = "#353535"
bg[SELECTED] = "#353535"
bg[INSENSITIVE] = "#FFFFFF"

base[NORMAL] = "#FFFFFF"
base[PRELIGHT] = "#FFFFFF"
base[ACTIVE] = "#FFFFFF"
base[SELECTED] = "#FFFFFF"
base[INSENSITIVE] = "#FFFFFF"

text[NORMAL] = "#FFFFFF"
text[PRELIGHT] = "#FFFFFF"
text[ACTIVE] = "#FFFFFF"
text[SELECTED] = "#FFFFFF"
text[INSENSITIVE] = "#FFFFFF"
}
widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
class "*Panel*" style "panel"
widget_class "*Mail*" style "panel"
class "*notif*" style "panel"
class "*Notif*" style "panel"
class "*Tray*" style "panel"
class "*tray*" style "panel"


3.
&#65279;
style "panel"
{
bg_pixmap[NORMAL] = ".panelbackground.png"
fg[NORMAL] = "white"
}
widget_class "*Panel*" style "panel"
widget "*Panel*" style "panel"
class "*Panel*" style "panel"

---

### Post by frankwakeman on 2009-10-04
With a bit of fiddling I've solved this for myself.  This is my gtkrc-2.0 file now, (and my panel background is attached)...

style "xfdesktop-icon-view" {
    XfdesktopIconView::label-alpha = 0

    base[NORMAL] = "#ffffff"
    base[SELECTED] = "#ffffff"
    base[ACTIVE] = "#ffffff"

    fg[NORMAL] = "#ffffff"
    fg[SELECTED] = "#ffffff"
    fg[ACTIVE] = "#ffffff"
}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"

# ~/.gtkrc-2.0
style "panel-background" {
  bg_pixmap[NORMAL]        = "pb.png"
  bg_pixmap[PRELIGHT]      = "pb.png"
  bg_pixmap[ACTIVE]        = "pb.png"
  bg_pixmap[SELECTED]      = "pb.png"
  bg_pixmap[INSENSITIVE]   = "pb.png"
}
style "panel-color" {
  fg[NORMAL]               = "#ffffff"
  fg[ACTIVE]               = "#ffffff"
  fg[PRELIGHT]		="#ffffff"
  bg[NORMAL]               = "#353535"
  bg[PRELIGHT]             = "#353535"
  bg[ACTIVE]               = "#353535"
}
widget_class "*Panel*" style "panel-background"
#change the above line so it ends "panel-color" if you don't want a pb.png
widget "*PanelWidget*" style "panel-color"
widget "*PanelApplet*" style "panel-color"
widget "*Panel*" style "panel-color"
widget_class "*Panel*" style "panel-color"
class "*Panel*" style "panel-color"
class "*Tray*" style "panel-color"
class "*tray*" style "panel-color"

---

### Post by coolbrook on 2009-10-25
This is awesome and would be a great sticky if there was Xubuntu/XFCE subforum.  I didn't think to reboot for changes to take effect when I tried other code, but did after yours and my desktop looks great with the white on black panel. Now if I can just get the new network manager icon to brighten up a bit, then that would be perfect.

:KS:KS:KS:KS:KS

---

### Post by frankwakeman on 2009-10-26
You could find the icon, log into the filesystem as root and alter it with Gimp couldn't you?

---

