---
title: "Eclipse tab bar bigger on ubuntu"
date: 2010-04-29
forum: Desktop Environments
---

### Post by bond17_007 on 2010-04-29
Hi, 
   This issue has been there for a long time and finally thought of posting it. I use Eclipse IDE for development. The IDE looks nice and pretty on Windows and Mac but for some reason ubuntu it looks HUGE. Pics attached.
First I thought may be its the theme. So, I played with gtkrc file of the themes I use but no luck. I am wondering what enforces the tab view? for some reason looks like all menu items are being padded. 
  I was able to turn down the tree view etc so it looks normal but I am still stuck with large tab and file bar.

[IMG]http://lh3.ggpht.com/_IBeiGZb2P1E/S9oFh1qZMkI/AAAAAAAAEFo/ulL3giDZN0A/eclipseOnUbuntu10.png[/IMG]

[IMG]http://lh5.ggpht.com/_IBeiGZb2P1E/S9oFhwUHWvI/AAAAAAAAEFs/kDJl-crPE2M/eclipseOnWin7.png[/IMG]

---

### Post by marbot on 2010-05-01
Hi James

I had the same problem with the new Ubuntu Lucid... Here's what helped:

- open a terminal and create a new file in your home directory called .gtkrc-2.0:

```
gedit ~/.gtkrc-2.0
```

- paste the following inside the file:

```
style "gtkcompact" {
GtkButton::default_border={0,0,0,0}
GtkButton::default_outside_border={0,0,0,0}
GtkButtonBox::child_min_width=0
GtkButtonBox::child_min_heigth=0
GtkButtonBox::child_internal_pad_x=0
GtkButtonBox::child_internal_pad_y=0
GtkMenu::vertical-padding=1
GtkMenuBar::internal_padding=0
GtkMenuItem::horizontal_padding=4
GtkToolbar::internal-padding=0
GtkToolbar::space-size=0
GtkOptionMenu::indicator_size=0
GtkOptionMenu::indicator_spacing=0
GtkPaned::handle_size=4
GtkRange::trough_border=0
GtkRange::stepper_spacing=0
GtkScale::value_spacing=0
GtkScrolledWindow::scrollbar_spacing=0
GtkTreeView::vertical-separator=0
GtkTreeView::horizontal-separator=0
GtkTreeView::fixed-height-mode=TRUE
GtkWidget::focus_padding=0
}
class "GtkWidget" style "gtkcompact"

```

- restart Eclipse, everything should look small and nice again.

cheers
marbot

---

### Post by bond17_007 on 2010-05-02
Awesome!!
Thanks a lot for the reply this worked like a charm.
Now eclipse looks "Normal" and I got the realstate back.

---

### Post by wezside on 2010-05-09
Awesomeness! Works for me.

---

### Post by nZain on 2010-07-15
Thank you so much - no need for a individual icon theme :) This is especially usefull on laptops with a small screen height.

---

### Post by yvsong on 2010-07-30
The status bar seems unnecessarily tall, too. Is there a solution?

---

### Post by xmas_spirit on 2010-08-13
unfortunately this does not work in kubuntu

---

### Post by Azuma59 on 2010-10-08
Hi, much easily place this in the .gtkrc-2.0 file

```

style "compact-toolbar"
{
	GtkToolbar::internal-padding = 0
	xthickness = 1
	ythickness = 1
}

style "compact-button"
{
	xthickness = 0
	ythickness = 0
}

class "GtkToolbar"   				style "compact-toolbar" 
widget_class "*<GtkToolbar>*<GtkButton>"	style "compact-button"

```

Tabs will be smaller.

---

### Post by kilaka on 2011-02-28
> **yvsong said:**
> The status bar seems unnecessarily tall, too. Is there a solution?

I found something here:
[http://ubuntuforums.org/showthread.php?t=1007562](http://ubuntuforums.org/showthread.php?t=1007562)

But it didn't work.
Perhaps Java doesn't use gnome's settings?

---

