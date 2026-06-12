---
title: "Gnome Panel Font + other things"
date: 2011-04-25
forum: Desktop Environments
---

### Post by jesuisbenjamin on 2011-04-25
Hello there,

I found an [old thread from 2005]("http://ubuntuforums.org/showthread.php?t=47776") on how to change the font color on the gnome-panel.
It worked for all applets on the panel except for the notification area and me-menu where the font remains dark.

[IMG]http://uppix.net/c/8/d/5bacd2b6a6b0ceafd666a4353e713.png[/IMG]

How can i force the font to a light color on these two applets?

Also as i used the "clarlooks" theme for controls the status indicator is duplicated: there is one instance in the me-menu and another in the notification area. How can i remove either?

Thanks

Benjamin

[I]
PS Remark: i find that the gnome-panel is a real hassle since 10.04. Not only it is not logically constructed, but it is inconsistent and not customisation friendly. But enough nagging for today.[/I]

---

### Post by Krytarik on 2011-04-25
- Take a look into the theme's panel specification, like I described here, for a different matter:
[http://ubuntuforums.org/showthread.php?p=10622129#post10622129](http://ubuntuforums.org/showthread.php?p=10622129#post10622129)

- I really don't know why those item sometimes appear twice, although it seems to be a common issue, I, too, experienced it a while ago.

- Is this Docky that you are using parallely? You may try AWN instead, it offers multiple panels, and can put all items you are using in your current panel into one of them, please see my earlier post regarding it:
[http://ubuntuforums.org/showthread.php?p=10674484#post10674484](http://ubuntuforums.org/showthread.php?p=10674484#post10674484)
I guess that would also fix the duplicate-issue.

Greetings.

---

### Post by jesuisbenjamin on 2011-04-25
Thanks for your reply :)

I am using Cairo-Dock. I'll stick to it for now, hoping better panel modes will come out soon. The other docks haven't convinced me really.

Now i looked into the other thread you meantioned but i can't find a [FONT="Courier New"]/usr/share/themes/Clearlooks/gtk-2.0/apps/gnome-panel.rc[/FONT]

In the [FONT="Courier New"]gtk-2.0[/FONT] folder i can find a [FONT="Courier New"]gtkrc[/FONT] file only. Clearlooks is the theme i use for controls in my customized theme.

Any where to look into?

Thanks.
Benjamin

---

### Post by Krytarik on 2011-04-25
Cairo Dock is much too resource hungry for my old machine, and unnecessary overly effectful for my taste, at least with the default settings. I tried to trigger it down a bit, but it didn't really help too much.

In the Clearlooks theme, there is no special config for the panels. Because of that the default "fg[..]" colors are getting applied to the panel text. So, you need to set up a special config for them.

- Place this at the lower end of "gtkrc" (taken from Ambiance's "gnome-panel.rc"):
```
#widget_class "*Panel*"            style "panel"
widget "*PanelWidget*"            style "panel"
widget "*PanelApplet*"            style "panel"
widget "*fast-user-switch*"       style "panel" # workaround for Fast User Switch applet
widget "*CPUFreqApplet*"          style "panel" # workaround for CpuFreq Applet
class "PanelApp*"                 style "panel"
class "PanelToplevel*"            style "panel"
#widget_class "*Mail*"             style "panel"
widget_class "*notif*"            style "panel"

#widget_class "*?anel*utton"       style "panel_task_button" # causing problems to monodevelop
widget "*task*"                   style "panel"
widget "*.tasklist-button"        style "panel"
widget "*PanelApplet*TaskTitle*"  style "panel"
```- and place this somewhere into the upper part, but below the "default" style section:
```
style "panel" = "default"
{
    fg[NORMAL]        = "#ffffff"
    fg[PRELIGHT]      = "#ffffff"
    fg[SELECTED]      = "#ffffff"
    fg[INSENSITIVE]   = "#ffffff"
    fg[ACTIVE]        = "#ffffff"
}
```[INDENT]You may want to fine-tune these colors.[/INDENT]

---

### Post by jesuisbenjamin on 2011-04-25
You did it! Thanks :)

---

