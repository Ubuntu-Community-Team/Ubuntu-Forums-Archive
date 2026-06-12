---
title: "Icons without transparent background"
date: 2011-10-31
forum: Desktop Environments
---

### Post by woodyg on 2011-10-31
Since starting to use a background image for a panel background style on my Xubuntu 11.10, I have the problem with two icons not having transparent backgrounds. The icons are for the wastebasket and places. When using a specific colour as panel background, those icons behave as they should, i.e. their background take on the colour in question. When switching from solid colour to background image in the panel appearance it all goes wrong however. **Have a look at the screenshot** to see the problem...

The problem remain regardless of style or icons that I use for the desktop. Why is there no transparency for the background of those two icons? :confused:

---

### Post by mike555 on 2011-11-01
Not sure if this will work for your problem but to clear the background for icon text I did this;

 icon text transparency


To get icon transparency on the desktop, create (or add to if it already exists) the file ~/.gtkrc-2.0 (a hidden file in your home directory), the following content:
Code:

style "xfdesktop-icon-view" {
    XfdesktopIconView::label-alpha = 0

    base[NORMAL] = "#000000"
    base[SELECTED] = "#000000"
    base[ACTIVE] = "#000000"

    fg[NORMAL] = "#ffffff"
    fg[SELECTED] = "#ffffff"
    fg[ACTIVE] = "#ffffff"
}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"


Either log out and back in again or change the appearance theme to something else and back again for it to take effect.

---

### Post by woodyg on 2011-11-01
Thanks for the input, but it made no difference. The problem is still there.

---

### Post by Toz on 2011-11-01
Try adding this to your .gtkrc-2.0 file:
```
#fix panel transparency
style "default-style"
{
	GtkWindow::resize-grip-height = 8
	GtkWindow::resize-grip-width = 8
}
class "GtkWidget" style "default-style"

style "mypanel" 
{
      engine "pixmap"
        {
                image
                {
                        function                = BOX
                        recolorable             = TRUE
                        state                   = PRELIGHT
                        file                    = "panelbuttonhover.png"
                        border                  = { 1, 1, 0, 0 }
                        stretch                 = TRUE
                }
                image
                {
                        function                = BOX
                        recolorable             = TRUE
                        state                   = ACTIVE
                        file                    = "panelbuttonhover.png"
                        border                  = { 1, 1, 0, 0 }
                        stretch                 = TRUE
                }
        }
}

widget "*Xfce*Panel*"                style "mypanel"
class "*Xfce*Panel*"                style "mypanel"
widget "*PanelWidget*"              style "mypanel"
widget "*PanelApplet*"              style "mypanel"
widget "*fast-user-switch*"         style "mypanel"
widget "*CPUFreq*Applet*"           style "mypanel"
widget "*indicator-applet*"         style "mypanel"
class "PanelApp*"                   style "mypanel"
class "PanelToplevel*"              style "mypanel"
widget_class "*PanelToplevel*"      style "mypanel"
widget_class "*notif*"              style "mypanel"
widget_class "*Notif*"              style "mypanel"
widget_class "*Tray*"               style "mypanel"
widget_class "*tray*"               style "mypanel"
widget_class "*computertemp*"       style "mypanel"
widget_class "*Applet*Tomboy*"      style "mypanel"
widget_class "*Applet*Netstatus*"   style "mypanel"
```

And oh, you'll also need to add a file to your home directory. Save this image: [http://img99.imageshack.us/img99/6641/panelbuttonhover.png]("http://img99.imageshack.us/img99/6641/panelbuttonhover.png") in your home directory.

---

### Post by woodyg on 2011-11-01
The icons in question are still the same. Strange. Anyway... I noticed one can play around a bit with the code provided, and I was thinking... can one specify different styles for different panels (if one has more than one panel)? I mean, if I modify panelbuttonhover.png I can get all sorts of background color when hovering over the icon, which doesn't look bad. But it only looks good on the panel I use as a launcher (Unity lookalike), it doesn't look very good for the panel containing the usual system tray icons (wifi, sound etc). 

So can I use different styles for different panels? I've been searching for info on what "PanelToplevel*, *Xfce*Panel*, PanelApp* etc etc" refers to, but haven't found any useful documentation.

Where is a good place to find documentation on how to style the panels?

---

