---
title: "2 network manager icons in the applet panel"
date: 2018-03-19
forum: Desktop Environments
---

### Post by tides on 2018-03-19
Hi there,
I see two network icons in the applet panel as shown here:
[IMG]https://i.imgur.com/GY2ezBR.png?1[/IMG]

I've looked for the issue all over the forums and tryed many solutions:
- editing ~/.config/lxsession/Lubuntu/desktop.conf in order to remove the nm-applet string
- removing the nm-applet.desktop from /etc/xdg/autostart (which at the moment I move to autostart-disabled)
- playing with the applet indicator options
 but noone worked!

Here is the process:
[IMG]https://i.imgur.com/Tf2bUTK.png?1[/IMG]

Is anyone experiencing the same bug?
Thanks for the help.

Edit:
sometimes it boots just fine, with no duplicates.
sometimes it randomly duplicates other icons (redshift here)
[IMG]https://i.imgur.com/sILresB.jpg?1[/IMG]
in this case the first 3 icons from the left are part of "Pannello di sistema" (system panel), the remaining are part of "Applet indicatore" (indicator applet).

[IMG]https://i.imgur.com/i4yMUky.png?1[/IMG]

A possible fix would be to edit the system panel and remove every icon except the energy manager (which is only shown by it) but there's no option and I have no clue how to do it via terminal.

---

### Post by nlee2 on 2018-03-20
I do this when I see 2 nm-applet icons

pkill nm-applet && nm-applet &

---

### Post by tides on 2018-03-22
> **nlee2 said:**
> I do this when I see 2 nm-applet icons

pkill nm-applet && nm-applet &

It works, thanks. Even if it isn't a permament fix.

---

