---
title: "[lubuntu] How to Configure Desktop Notifications"
date: 2014-10-25
forum: Desktop Environments
---

### Post by Dennis N on 2014-10-25
How do I configure Desktop notifications in Lubuntu? I can find no preferences or settings anywhere for this. In the screenshot, the default settings encroach on the window title bar and controls and this needs to be moved elsewhere. Also, there should be other styles. This is Lubuntu 14.04. Thanks.

EDIT:

OK, I found the solution to access a dialog using the command line. In case anyone needs this information:
Using this command will bring up a small dialog controlling the position and style.

```
dmn@Sydney:~$ xfce4-notifyd-config
```

EDIT #2:

See Post #5 for how to get an entry for **Notifications** in Lubuntu's menu under **Preferences**.

---

### Post by JKyleOKC on 2014-10-26
Works under Xubuntu also. Thanks!

---

### Post by vasa1 on 2014-10-26
> **Dennis N said:**
> ...
OK, I found the solution to access a dialog using the command line. In case anyone needs this information:
Using this command will bring up a small dialog controlling the position and style.

```
dmn@Sydney:~$ xfce4-notifyd-config
```
The corresponding .desktop file is here: /usr/share/applications/xfce4-notifyd-config.desktop and the notifications can be themed, to some extent, by editing /usr/share/themes/*theme_name*/xfce-notify-4.0/gtkrc.

---

### Post by Dennis N on 2014-10-26
> **vasa1 said:**
> The corresponding .desktop file is here: /usr/share/applications/xfce4-notifyd-config.desktop and the notifications can be themed, to some extent, by editing /usr/share/themes/*theme_name*/xfce-notify-4.0/gtkrc.

I am using the Lubuntu dark panel theme, but I don't see any **xfce-notify-4.0** folder in **/usr/share/themes/Lubuntu-dark-panel/** or in the Lubuntu-Default theme. What theme are you using?

In Lubuntu 14.10, the appearance of the notifications are not right and need to be fixed. Maybe it is possible with that file. They are fine in Lubuntu 14.04

---

### Post by Dennis N on 2014-10-26
vasa1's mentioning the .desktop file got me to thinking that it might be preventing the dialog from appearing in Lubuntu's "Preferences" menu.

Sure enough, if you examine **[FONT=Courier New]/usr/share/applications/xfce4-notifyd-config.desktop[/FONT]** you will find a line **OnlyShowIn=XFCE;**

If you comment out this line (change it to **#OnlyShowIn=XFCE;**) you will then get a menu entry as **Preferences > Notifications** that brings up the same dialog. I also cleaned up the Categories line to just **Categories=GTK;Settings;**

---

### Post by vasa1 on 2014-10-26
> **Dennis N said:**
> vasa1's mentioning the .desktop file got me to thinking that it might be preventing the dialog from appearing in Lubuntu's "Preferences" menu.

Sure enough, if you examine **[FONT=Courier New]/usr/share/applications/xfce4-notifyd-config.desktop[/FONT]** you will find a line **OnlyShowIn=XFCE;**

If you comment out this line (change it to **#OnlyShowIn=XFCE;**) you will then get a menu entry as **Preferences > Notifications** that brings up the same dialog. I also cleaned up the Categories line to just **Categories=GTK;Settings;**
My bad!

That's one of some .desktop files I've copied over to ~/.local/share/applications and then "cleaned up": the local .desktop file looks like this:```
[Desktop Entry]
Version=1.0
Name=Notifications
Comment=Customize how notifications appear on your screen
Exec=xfce4-notifyd-config
Icon=xfce4-notifyd
Terminal=false
StartupNotify=true
Type=Application
Categories=XFCE;GTK;Settings;DesktopSettings;X-XFCE-SettingsDialog;X-XFCE-PersonalSettings;
X-XfcePluggable=true
```

---

### Post by Dennis N on 2014-10-28
The **gtk-2.0/gtkrc** file in the theme folders has **include "assets/xfce4-notifyd.rc"** so looking there, that file appears to define the colors of the background, button, etc. and it is a color match for Smoke (default) but not for ZOMG-PONIES!. Also, it defines a white border, and none have that. There should be additional configuration elsewhere for the style.

---

### Post by vasa1 on 2014-11-03
> **Dennis N said:**
> The **gtk-2.0/gtkrc** file in the theme folders has **include "assets/xfce4-notifyd.rc"** so looking there, that file appears to define the colors of the background, button, etc. and it is a color match for Smoke (default) but not for ZOMG-PONIES!. Also, it defines a white border, and none have that. There should be additional configuration elsewhere for the style.

Sorry for the delay ... but I use the **Greybird theme** (part of shimmer-themes in the Software Center). I understand it's the default theme for Xubuntu. */usr/share/themes/Greybird/xfce-notify-4.0/gtkrc* has this:```
style "notify-window"
{
    XfceNotifyWindow::summary-bold = 1
    XfceNotifyWindow::border-color = "#ffffff"
    XfceNotifyWindow::border-color-hover = "#ffffff"
    XfceNotifyWindow::border-radius = 10.0
    XfceNotifyWindow::border-width = 0.1
    XfceNotifyWindow::border-width-hover = 0.1
    bg[NORMAL] = "#111"
}

style "notify-button"
{
    bg[NORMAL] = "#202020"
    bg[PRELIGHT] = "#303030"
    bg[ACTIVE] = "#222222"
    fg[NORMAL] = "#ffffff"
    fg[PRELIGHT] = "#ffffff"
    engine "murrine" {
	border_shades = { 2.9, 2.6 }
	shadow_shades = {2.4,2.4}
        roundness = 4
    }
}

style "notify-text"
{
    fg[NORMAL] = "#ffffff"
    fg[PRELIGHT] = "#ffffff"
    GtkWidget::link-color = "#a7a7a7"
}

style "notify-summary"
{
    font_name = "Bold"
}

style "notify-progressbar"
{
    GtkProgressBar::min-horizontal-bar-height = 4
    xthickness   = 0
    ythickness   = 0

    fg[PRELIGHT] = "#000000"
    bg[NORMAL]   = "#fefefe"
    bg[SELECTED] = "#fefefe"
    bg[ACTIVE]   = "#696969"

    engine "murrine" {
        gradient_shades = { 1.0, 1.0, 1.0, 1.0 }
        contrast	= 0.5
        border_shades	= { 0.9, 0.9 }
        progressbarstyle    = 0
    }
}

class "XfceNotifyWindow" style "notify-window"
widget "XfceNotifyWindow.*.summary" style "notify-summary"
widget_class "XfceNotifyWindow.*<GtkButton>" style "notify-button"
widget_class "XfceNotifyWindow.*.<GtkLabel>" style "notify-text"
widget_class "XfceNotifyWindow.*.<GtkProgress>" style "notify-progressbar"
widget_class "XfceNotifyWindow.*.<GtkProgressBar>" style "notify-progressbar"
```

I won't pretend that I understand all of that but I changed some things (not shown above) about so that I get notifications I don't mind seeing.

---

