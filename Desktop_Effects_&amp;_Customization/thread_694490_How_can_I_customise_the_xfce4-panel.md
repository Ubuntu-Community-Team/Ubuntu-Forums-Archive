---
title: "How can I customise the xfce4-panel?"
date: 2008-02-12
forum: Desktop Effects &amp; Customization
---

### Post by geokker on 2008-02-12
I'm very happy with the performance I get from Xubuntu and generally, I keep the eye-candy to a minimum e.g. no Beryl, special effects etc. However, I would like to make the panel a little friendlier. I've figured out how to change the background but am at a loss on the various button states on the task list xfce applet.

Here's what I have so far in the .gtkrc-2.0 file:

```
style "panel"
{
bg_pixmap[NORMAL] = "custom_icons/blackpanel.png"
fg[NORMAL] = "white"
}

widget_class "*Panel*" style "panel"
widget "*Panel*" style "panel"
class "*Panel*" style "panel"
```

This gives me a shiny black background but normal depressed buttons. i don't want 'active' states for currently selected applications - I know what's active because I'm using it!

What are all the gtkrc directives and what do they mean?

Can the task list applet buttons be styled in this way?

---

