---
title: "Beryl window problems"
date: 2007-07-28
forum: Desktop Effects &amp; Customization
---

### Post by G_force on 2007-07-28
When ever i open firefox or banshee with the beryl window manager i get this glitch

[IMG]http://img528.imageshack.us/img528/3235/screenshotfb3.png[/IMG]

Anyone have any ideas?

It may occur with other programs i am not sure


Thanks in advance

---

### Post by hyperair on 2007-07-28
Good grief. I've never seen such a thing before. You could try deleting your .beryl folder from your home folder, then reconfiguring it from scratch again.
```

rm -r ~/.beryl

```

---

### Post by G_force on 2007-07-28
Yeah i have tried that.....

I do have a bit of history on it

I Installed it via the Ubuntu feisty Guide

changed the rendering platform to AIGLX (ATI)

But then one of my friends changed the rendering platform to XGL

it then would crash, it would lock up but the i removed beryl-manager from the start up by logging in, in gnome failsafe terminal

```
 
cd ~/.config/autostart
rm beryl-manager.desktop beryl-xgl.desktop

```

I then restarted the computer, change the render platform to automatic
and then had that dodgy window effect.

Any ideas?

---

### Post by G_force on 2007-07-28
i created a .beryl folder + the config file then reloaded the manager
all good

---

### Post by G_force on 2007-07-28
The problem has reared its ugly head again

ANy ideas are welcome

---

