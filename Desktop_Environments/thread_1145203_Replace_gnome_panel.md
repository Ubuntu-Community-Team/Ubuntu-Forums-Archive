---
title: "Replace gnome panel"
date: 2009-05-01
forum: Desktop Environments
---

### Post by zhus on 2009-05-01
Hi all.
Forgive me my English.

I don`t like gnome panel, so I have installed xfce4-panel, configured it and added to to auto-started. But I do not want two panels, so I need to delete gnome panel. But option "delete" is grayed out even when I have deleted all applets from it. It is now empty but can not be deleted.

Can anybody suggest me something useful?

wbr, zhus.

---

### Post by andrea000 on 2009-05-01
to remove gnome desktop
open a terminal and type in

sudo apt-get remove ubuntu-desktop

There are some useful desktops kde 
and xfce are some.

A guide to remove and install desktops is [here]("http://ubuntuforums.org/showthread.php?t=205002")

best of luck

---

### Post by zhus on 2009-05-01
I like gnome, it is more powerful then xfce. Bit slower, but now I'm about other thing. I want to replace gnome-panel by xfce-panel only. Inside gnome. Do not installing xfce.

i.e. I want ubuntu-desktop with xfce-panel.

---

### Post by inobe on 2009-05-01
you can actually make the gnome panels appear like xfce panel by change the theme.

[http://www.techotopia.com/index.php/Customizing_the_Ubuntu_GNOME_Desktop_Panels](http://www.techotopia.com/index.php/Customizing_the_Ubuntu_GNOME_Desktop_Panels)

---

### Post by zhus on 2009-05-01
Ekhm...
Big thanks for suggestions.

There are lot of things that I am prefer in xfce-panel. For the first I can use xfce and gnome applets together. There are lot of xfce applets which much better then their gnome analogues. There are xfce applets which have no gnome analogues. Gnome panel does fake transparency, it uses desktop background instead of transparency. And so on. If somebody interesting, I can describe all I think about it, but, may be, in other thread...

Simply... How to disable starting of gnome-panel?

thanks, zhus.

---

### Post by PacSci on 2009-05-01
You can do this in a few steps:

[LIST=1]
[*]Open the Configuration Editor (gconf).
[*]Browse in the tree to /desktop/gnome/session/required_components.
[*]In the keys pane, right-click the "panel" key and select "Edit Key..." (the current key is "gnome-panel").
[*]Enter "xfce4-panel" and click OK.
[*]Close Configuration Editor and logout.
[/LIST]

That should work for you. If you want to change the WM or file manager, you can do that there as well - gnome-session gets all of its configuration from there.

Oh, and delete xfce4-panel from your auto-start, because this will auto-start it as well.

---

### Post by zhus on 2009-05-02
Great! BIG thanks!
It works and it is what I need.

wbr, zhus.

---

