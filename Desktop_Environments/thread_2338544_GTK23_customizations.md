---
title: "GTK2/3 customizations"
date: 2016-09-29
forum: Desktop Environments
---

### Post by loceka2 on 2016-09-29
Hello,

I have two issues that can be resolved by customizing the GTK settings (I think), but I'm not skilled enough with GTK and my researches didn't help.

The first issue concerns the XFCE4 "pager" (workspace switcher) in the taskbar, which is way too wide when using multiple screens (there are several posts related to this issue over the net but with no solution).
I've seen in [this post]("https://ubuntuforums.org/showthread.php?t=1945518&p=11787469#post11787469") that the colors could be changed (and it works for me too) so I wondered if the size could also be tweaked, and how? I couldn't find the matching instructions.

The second issue concerns the XFCE4 Vertex Maia theme which is almost perfect expect for the button selection : there is no hint a button is selected which is very disturbing when using TAB navigation.

Here is a screenshot of buttons using the Vertex Maia Dark theme:
[ATTACH=CONFIG]271422[/ATTACH]

And here is a screenshot of the same screen using the XFCE Dusk theme:
[ATTACH=CONFIG]271421[/ATTACH]

As you can see, the latter hints which button is currently selected, as anyone would expect.

Is there a way to change the settings in order to add such a hint in that theme ?
I guess it uses xfwm4 but I have no clue what it implies regarding the customization...

Thanks in advance,
Loceka.

---

### Post by kc1di on 2016-09-29
Hello loceka2 and welcome to XFCE and Ubuntu,
you can change the size of the switcher or I should say the style by following this post. 
hope it may be of help to you. 
[http://askubuntu.com/questions/744046/can-the-size-of-the-workspace-switcher-applet-be-changed]("http://askubuntu.com/questions/744046/can-the-size-of-the-workspace-switcher-applet-be-changed")

---

### Post by vasa1 on 2016-09-29
> **loceka2 said:**
> ... As you can see, the latter hints which button is currently selected, as anyone would expect.

Is there a way to change the settings in order to add such a hint in that theme ?
I guess it uses xfwm4 but I have no clue what it implies regarding the customization...

Thanks in advance,
Loceka.
If the gtkrc file of your theme has a line like```
	GtkWidget		::focus-line-width			= 0
```
you could change it to 1 or 2 from 0 and hope for the best.

xfwm4 is the window manager and I don't think it influences how selected buttons appear in your example.

---

### Post by loceka2 on 2016-09-29
> **kc1di said:**
> Hello loceka2 and welcome to XFCE and Ubuntu,
you can change the size of the switcher or I should say the style by following this post. 
hope it may be of help to you. 
[http://askubuntu.com/questions/744046/can-the-size-of-the-workspace-switcher-applet-be-changed](http://askubuntu.com/questions/744046/can-the-size-of-the-workspace-switcher-applet-be-changed)

Hello and thank you !
It's not quite what I was asking for, since it changes the behaviour of the tool (the workspace contents are no longer displayed) but it will do if I can find no way to tune it.

> **vasa1 said:**
> If the gtkrc file of your theme has a line like```
    GtkWidget        ::focus-line-width            = 0
```
you could change it to 1 or 2 from 0 and hope for the best.

Hoping wasn't enough I fear.
I've declared it in both [FONT=courier new]~/.gtkrc-2.0[/FONT] and [FONT=courier new]~/.config/gtk-3.0/settings.ini[/FONT] with no result.

I've also added [-GtkWidget-focus-line-width:1]("https://developer.gnome.org/gtk3/stable/gtk-migrating-GtkStyleContext-parser-extensions.html") to [FONT=courier new]/usr/share/themes/Vertex-Maia/gtk-3.0/gtk-dark.css[/FONT] but without any visible improvement.
The file [FONT=courier new]/usr/share/themes/Vertex-Maia/gtk-2.0/gtkrc[/FONT] already declared [FONT=courier new]GtkWidget::focus-line-width = 1[/FONT].

Of course I restarted X (and even rebooted) between each operation.

---

### Post by vasa1 on 2016-09-29
[https://github.com/horst3180/vertex-theme/issues/197](https://github.com/horst3180/vertex-theme/issues/197)

BTW, the Vertex themes aren't readily amenable to customization just by editing the css files.

---

### Post by loceka2 on 2016-09-30
Thank you for pointing out that it was a GTK2-only issue.
Indeed in GTK3 applications (in paman at least), the focused button is highlighted.

I still can't see how to fix it for the GTK2 apps though.

---

