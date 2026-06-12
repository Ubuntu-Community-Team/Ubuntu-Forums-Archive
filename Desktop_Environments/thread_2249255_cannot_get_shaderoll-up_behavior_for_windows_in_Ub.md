---
title: "cannot get shade/roll-up behavior for windows in Ubuntu 12.04"
date: 2014-10-20
forum: Desktop Environments
---

### Post by Ka_Chun_Yu on 2014-10-20
I'm re-posting from the General forum, after not seeing any response for a couple of weeks ...

After creating a brand new installation of 12.04 and running Gnome Classic Desktop, I've discovered that I  cannot get my old preferred behavior of roll-up/shade for windows.   That is, when I double-click on the title bar, I would like the window  to roll-up until only the title bar is showing, instead of the default behavior of maximizing the window.

I've changed the window settings in every place that I could find, but to no effect.  This includes:


[LIST]
[*]In Ubuntu Tweak, where the Window Manager settings show "Titlebar double-click action" as "Roll-up". 
[*]In Ubuntu Advanced Settings, where "Windows->Action on title bar double-click" is "Toggle Shade". 
[*]And finally also in gconf-editor, where /apps/metacity/general/action_double_click_titlebar is set to "toggle-shade". 
[/LIST]

I've logged out and in after these changes, but all to no effect.  I suspect that these are all affecting the same metacity parameter. Is there another setting that may be overriding this?

---

### Post by Retro_Garage on 2014-10-21
It depends on if the theme you are using supports that. In 13.10 I've found you cannot move buttons, I have a similar issue with progress bars. Just try another theme and try it.

---

### Post by mcduck on 2014-10-22
Nipe, it has nothing to do with the* theme* you are using. However it depends on the *window manager* in use. Can't rember wich window manager Gnoe Classic used in 12.04, but if it's not COmpiz then any config tool made for Unity desktop won't have any effect on the window behaviour.

...and if it is Compiz, you should try using CompizConfig Settings Manager, Metacity settings won't make any difference (even though Compiz uses Metacity's themes)

---

### Post by Ka_Chun_Yu on 2014-10-23
I am using Compiz.  But where in CompizConfigSettings Manager is the control for roll-up/shade?  An Advanced Search for "shade" shows:

Animations->Shade Animation
General Options->Key bindings
Group and Tab Windows->General
Ring Switcher->Misc. Options
Shift Switcher->Misc. Options

It doesn't seem that any of these are controlling the click-on-window behavior.

---

### Post by CantankRus on 2014-10-23
In 14.04 when not running the unity plugin I can use...
```
gsettings set org.gnome.desktop.wm.preferences action-double-click-titlebar toggle-shade
```

Failing that try using mouse scroll...
```
gsettings set org.compiz.gwd mouse-wheel-action shade
```

In 14.04 the unity plugin now draws the decorations and when using unity, rollup/shade doesn't work.

---

### Post by deadflowr on 2014-10-23
From the above, the general idea is sound, but the places in 12.04 are slightly different, since 12.04 uses gconf.
So instead of them being in org, they are in /apps.

The best tool to use would be gconf-editor, which will show as Configuration Editor when installed.
The paths to look for would be
/apps >> gwd >> mouse wheel action --double click where the value would be and enter you own value(shade)
and
/apps >> metacity >> general >> action double click titlebar -- same as above(toggle_shade)

A simple command line for them would be
```
 gconftool --set --type string /apps/gwd/mouse_wheel_action shade
```
and
```
 gconftool --set --type string /apps/metacity/general/action_double_click_titlebar toggle_shade
```

But I personally think using the editor is easier in the long run, fwiw.
Anyway hope it helps...

---

### Post by Ka_Chun_Yu on 2014-10-24
> **deadflowr said:**
> From the above, the general idea is sound, but the places in 12.04 are slightly different, since 12.04 uses gconf.
So instead of them being in org, they are in /apps.

The best tool to use would be gconf-editor, which will show as Configuration Editor when installed.
The paths to look for would be
/apps >> gwd >> mouse wheel action --double click where the value would be and enter you own value(shade)
and
/apps >> metacity >> general >> action double click titlebar -- same as above(toggle_shade)

A simple command line for them would be
```
 gconftool --set --type string /apps/gwd/mouse_wheel_action shade
```
and
```
 gconftool --set --type string /apps/metacity/general/action_double_click_titlebar toggle_shade
```

But I personally think using the editor is easier in the long run, fwiw.
Anyway hope it helps...

You're right -- the gsettings command for 14.04 doesn't work in 12.04.  But your second gconftool command did it.  Thanks!

---

### Post by Ka_Chun_Yu on 2014-10-24
Thanks to everyone who replied.  This gconftool call worked ...

```
gconftool --set --type string /apps/metacity/general/action_double_click_titlebar toggle_shade
```

---

