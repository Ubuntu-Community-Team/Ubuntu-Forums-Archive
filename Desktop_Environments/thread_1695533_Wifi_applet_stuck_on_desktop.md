---
title: "Wifi applet stuck on desktop"
date: 2011-02-26
forum: Desktop Environments
---

### Post by Navyblue on 2011-02-26
This might seem dumb, but I have a wifi applet stuck on the upper left corner of the desktop (on the desktop, not on any panel) that I can't get rid. I've never seen this before.

When on panel there is kind of a "handle" that I can right click which then I can "remove from panel. There is no such handle on the desktop, if I right click on the applet it would just display the wifi menu.

---

### Post by pressko on 2011-02-26
try with shift + del  ?

---

### Post by Navyblue on 2011-02-26
How do I do that? I can't select the applet.

---

### Post by Navyblue on 2011-02-26
I removed the network-manager-gnome package, it removed the applet, but it still remains on the desktop when I reinstall the package.

---

### Post by Frogs Hair on 2011-02-26
The network notification is part the notification area , wired/eth0  . To remove it , right click just to left of the applet and select remove . On some themes a vertical row of dots or line appears in this area , on others  it  hard to see at all .

---

### Post by Navyblue on 2011-02-26
The network manager applet doesn't seem to be part of the notification applet like the volume control. I could remove the notification and still have the network manager.

That said...

There is no such "handle" for the network manager applet like the notification applet. Plus, this thing is on the desktop, and unmovable.

On an unrelated note, my volume setting is missing from the notification applet. I removed and added the applet repeatedly, rebooted many times, and no luck.

It's really sad to see GNOME being so buggy.

---

### Post by Frogs Hair on 2011-02-26
The volume and mail icons are part of the indicator applet. The wireless icon is part of the notification area.

---

### Post by Frogs Hair on 2011-02-26
To restore the panel to default run this command.```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

### Post by Copper Bezel on 2011-02-26
Is it a notification area from an alternate panel application? Have you ever used Cairo Dock, for instance?

---

### Post by Navyblue on 2011-03-02
> **Frogs Hair said:**
> The volume and mail icons are part of the indicator applet. The wireless icon is part of the notification area.

Thanks, that really helped. :)

> **Frogs Hair said:**
> To restore the panel to default run this command.```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

I did that and that doesn't work.

> **Copper Bezel said:**
> Is it a notification area from an alternate panel application? Have you ever used Cairo Dock, for instance?

I had Cairo Dock, however if it was from Cairo Dock, shouldn't the wireless manager applet still remain on the GNOME bar?

---

### Post by Copper Bezel on 2011-03-02
As Frogs Hair said, it's not the applet that's moved, it's your entire notification area, which usually only contains the wireless applet. Since you reset the panel to defaults, it *should* be appearing at the upper right as usual, but it's not.

Since the Notification Area can only appear in one place at a time, that means that *something* is aping your notification area, and Cairo-Dock is a likely suspect. Go into your Cairo-Dock preferences and make certain that the Notification Area widget is disabled.

---

