---
title: "how can I change the background colour of workstpace switcher?"
date: 2006-04-30
forum: Desktop Environments
---

### Post by Stefan_hb on 2006-04-30
Hello,
I´d like to change the background colour of the workspace-switcher (or "pager") in the gnome panel, and also the colour that shows that a workspace is selected. is there a possibility to do so?
Thanks,
 Stefan

---

### Post by Ramses de Norre on 2006-04-30
It depends on your theme.

---

### Post by Stefan_hb on 2006-04-30
[QUOTE=Ramses de Norre]It depends on your theme.[/QUOTE]
Good answer, so minimalistic, so true.
I found out how to modify the active theme, so I could choose the colour of the pager myself, to  give it a kind of "pseudo-transparency"-effect, screenshot:
[IMG]http://img263.imageshack.us/img263/2812/bildschirmfoto2ni.th.jpg[/IMG]
Large: [http://img263.imageshack.us/my.php?image=bildschirmfoto2ni.jpg]("http://img263.imageshack.us/my.php?image=bildschirmfoto2ni.jpg")
Click on the picture to see it without scale.

Just add theese lines to the gtkrc of your active theme:
```
style "clearlooks-pager"
{
  bg[NORMAL]        = "#xxxxxx"
  bg[SELECTED]      = "#xxxxxx"
}
class "WnckPager" style "clearlooks-pager"
```
Replace xxxxxx with colours of your choice (Hex-value).

---

### Post by Ramses de Norre on 2006-04-30
I'm getting this with your code:> An error occurred while loading or saving configuration information for wnck-applet. Some of your configuration settings may not work properly.```
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/display_all_workspaces' specified for `/apps/panel/applets/applet_10/prefs/display_all_workspaces' stores a non-schema value

```
I added this lines to the gtkrc file: ```
style "clearlooks-pager"
{
  #bg[NORMAL]        = "#808080"
  bg[SELECTED]      = "#000000"
}
class "WnckPager" style "clearlooks-pager"
```

---

### Post by Stefan_hb on 2006-04-30
hmm, I added these lines to 
/usr/share/themes/Industrial/gtk-2.0/gtkrc
and everything works fine:
```
style "clearlooks-pager"
{
  bg[NORMAL]        = "#667465"
  bg[SELECTED]      = "#85A36E"
}
class "WnckPager" style "clearlooks-pager"
```

---

