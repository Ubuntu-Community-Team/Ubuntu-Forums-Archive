---
title: "Mouse hover actions - can't see tooltip ??"
date: 2018-01-07
forum: Desktop Environments
---

### Post by oygle on 2018-01-07
In Claws mail, I can't see what the tooltip is, because the background and foreground are the same colour (or almost the same).

Some information at [http://www.claws-mail.org/faq/index.php/Interface#Why_doesn.27t_colour_labelling_work_under_KDE.3F](http://www.claws-mail.org/faq/index.php/Interface#Why_doesn.27t_colour_labelling_work_under_KDE.3F) , but I'm not sure if the problem is KDE/GTK + 2 or something else.

The problem is not limited to Claws, as it also happens in other applications that use GTK+ 2 , like GIMP.

When I check the system settings for colours and then view tooltips, the foreground is white and the background is black, so the tips can be seen. But when I try a tooltip in Claws or GIMP, I can't see it.

Some screenshots at [https://photos.google.com/share/AF1QipMljNig9oCqkjAMMn2cHMpBF-6KJuzBEAaY8RjXp1w5_rD36KrZfUvSo_2dksejUg?key=ZG40cFNFX0MtTkpOaWZ0S1FPZ3hpSld6anJabHJn](https://photos.google.com/share/AF1QipMljNig9oCqkjAMMn2cHMpBF-6KJuzBEAaY8RjXp1w5_rD36KrZfUvSo_2dksejUg?key=ZG40cFNFX0MtTkpOaWZ0S1FPZ3hpSld6anJabHJn)

---

### Post by vasa1 on 2018-01-07
What does your theme's *gtkrc* show? Maybe run something like```
grep -i tooltip /path/to/your/gtk2/gtkrc-file
```

On my system, I see```
$ grep -i tooltip /home/vasa1/.themes/g2bird/gtk-2.0/gtkrc
gtk_color_scheme        = "tooltip_bg_color:#333333\ntooltip_fg_color:#000010" # Tooltips. fg was #888888
style "tooltips" = "wider"
        bg[NORMAL]      = @tooltip_bg_color
        fg[NORMAL]      = @tooltip_fg_color
        XfdesktopIconView::tooltip-size = 32
# The window of the tooltip is called "gtk-tooltip"
# This will not work if one embeds eg. a button into the tooltip.
widget "gtk-tooltip*"   style "tooltips"
$ 
```

The relevant line is```

gtk_color_scheme        = "tooltip_bg_color:#333333\ntooltip_fg_color:#000010" # Tooltips. fg was #888888
```

---

### Post by oygle on 2018-01-07
> **vasa1 said:**
> What does your theme's *gtkrc* show? Maybe run something like```
grep -i tooltip /path/to/your/gtk2/gtkrc-file
```

Thanks for your reply. As my system files seem quite different, in format, I will post 3 files that contained 'gtkrc' in them.

*/usr/share/kubuntu-default-settings/dot-gtkrc-2.0-kde4*

> include "/usr/share/themes/oxygen-gtk/gtk-2.0/gtkrc"

gtk-theme-name="oxygen-gtk"

*/home/username/.gtkrc-2.0*

> include "/usr/share/themes/Breeze/gtk-2.0/gtkrc"
style "user-font"
{
    font_name="Noto Sans Regular"
}
widget_class "*" style "user-font"
gtk-font-name="Noto Sans Regular 10"
gtk-theme-name="Breeze"
gtk-icon-theme-name="breeze"
gtk-fallback-icon-theme="gnome"
gtk-toolbar-style=GTK_TOOLBAR_ICONS
gtk-menu-images=1
gtk-button-images=1

*/home/username/gtkrc-2.0*

> # created by KDE, Mon Jan 8 07:57:56 2018
#
# If you do not want KDE to override your GTK settings, select
# Appearance -> Colors in the System Settings and disable the checkbox
# "Apply colors to non-KDE4 applications"
#
#

gtk-alternative-button-order = 1

style "default"
{
  bg[NORMAL] = { 0.937, 0.941, 0.945 }
  bg[SELECTED] = { 0.239, 0.682, 0.914 }
  bg[INSENSITIVE] = { 0.937, 0.941, 0.945 }
  bg[ACTIVE] = { 0.769, 0.788, 0.804 }
  bg[PRELIGHT] = { 0.937, 0.941, 0.945 }

  base[NORMAL] = { 0.988, 0.988, 0.988 }
  base[SELECTED] = { 0.239, 0.682, 0.914 }
  base[INSENSITIVE] = { 0.937, 0.941, 0.945 }
  base[ACTIVE] = { 0.239, 0.682, 0.914 }
  base[PRELIGHT] = { 0.239, 0.682, 0.914 }

  text[NORMAL] = { 0.192, 0.212, 0.231 }
  text[SELECTED] = { 0.937, 0.941, 0.945 }
  text[INSENSITIVE] = { 0.769, 0.788, 0.804 }
  text[ACTIVE] = { 0.937, 0.941, 0.945 }
  text[PRELIGHT] = { 0.937, 0.941, 0.945 }

  fg[NORMAL] = { 0.192, 0.212, 0.231 }
  fg[SELECTED] = { 0.937, 0.941, 0.945 }
  fg[INSENSITIVE] = { 0.769, 0.788, 0.804 }
  fg[ACTIVE] = { 0.192, 0.212, 0.231 }
  fg[PRELIGHT] = { 0.192, 0.212, 0.231 }
}

class "*" style "default"

style "ToolTip"
{
  bg[NORMAL] = { 0.937, 0.941, 0.945 }
  base[NORMAL] = { 0.988, 0.988, 0.988 }
  text[NORMAL] = { 0.192, 0.212, 0.231 }
  fg[NORMAL] = { 0.192, 0.212, 0.231 }
}

widget "gtk-tooltip" style "ToolTip"
widget "gtk-tooltips" style "ToolTip"

style "MenuItem"
{
  bg[PRELIGHT] = { 0.239, 0.682, 0.914 }
  fg[PRELIGHT] = { 0.937, 0.941, 0.945 }
}

class "*MenuItem" style "MenuItem"


One of those files says 'Breeze' is the theme, another specifies 'oxygen-gtk' as the theme, yet I know that 'Aya' is the current desktop theme ?? Although that was added today, so maybe it needs a reboot to change the settings in those files.

After having noticed the comment in one of those files, have now unchecked the 'apply colors to non-QT applications, so will see what that does.

Thanks for your help. :)

---

### Post by oygle on 2018-01-07
> **oygle said:**
> After having noticed the comment in one of those files, have now unchecked the 'apply colors to non-QT applications, so will see what that does.


Exited Claws, then opened it again, ...wow, now it works and I can see the tooltip. Quickly checked GIMP and it now seems okay.  :)

Thanks **vasa1**

---

