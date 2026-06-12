---
title: "Icons and Controls won't Theme???? O_O"
date: 2011-05-04
forum: Desktop Environments
---

### Post by The_Autonomist on 2011-05-04
Let me just say first, that i'm running Natty Narwhal. 64-bit, HP dv6 notebook.

But, a little while ago, I had done this trick:

> gksu gnome-appearance-properties

in order to get rid of the pre-installed and a couple of bisigi themes. It worked fine, or so I thought. 

Then, about an hour or so later, I restarted my computer. And when i logged on, my icons, panel, and controls won't them at all. They're this bland, gray, chunky, Windows 2000 look. 

I went to Appearance, and tried to choose different full themes, control themes, and different icons but the only thing that would change were my Window Borders. 

How do I fix this? Better yet, what's wrong???? 

I attached some pics to show what i'm talking about. 

[IMG]http://i48.photobucket.com/albums/f245/chica2k8/Screenshot-3.png[/IMG]
[IMG]http://i48.photobucket.com/albums/f245/chica2k8/Screenshot-2.png[/IMG]
[IMG]http://i48.photobucket.com/albums/f245/chica2k8/Screenshot-1.png[/IMG]
[IMG]http://i48.photobucket.com/albums/f245/chica2k8/Screenshot.png[/IMG]

---

### Post by The_Autonomist on 2011-05-04
*bump*

anyone???? help???

---

### Post by Copper Bezel on 2011-05-04
Two possibilities: you might be experiencing an ongoing bug in recent Ubuntu versions in which Gnome Settings Daemon is crashing unpredictably, or your [font="Courier New"]gksu gnome-appearance-properties[/font] might have changed permissions on some files in an unfavorable way. Theme settings are saved in gconf. Check that this file

```
~/.gconf/desktop/gnome/interface/%gconf.xml
```

isn't owned by Root.

---

