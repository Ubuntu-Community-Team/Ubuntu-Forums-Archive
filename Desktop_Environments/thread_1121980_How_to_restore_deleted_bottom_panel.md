---
title: "How to restore deleted bottom panel?"
date: 2009-04-10
forum: Desktop Environments
---

### Post by klopus on 2009-04-10
I'm using Gnome 2.26 in a latest build of Ubuntu 9.04 Beta. I'm new to Gnome, was more of a KDE guy until 4.x which I'm finding isn't my cup of tea :)

Anyway. I by mistake removed (via panle right-click menu) the bottom panel and now want it back. I was hoping to replace it with Cairo dock. Latter didn't work as I hoped since Cairo gets obscured by open windows. This makes is useless as an always available place to restore minimized windows, switch to other window, run a new app, etc.

So to recap here are the questions:

[LIST=1]
[*]How to restore removed bottom panel?
[*]Is there an OSX type dock that can auto-hide or bleed through windows?
[/LIST]

Thanks!

---

### Post by howefield on 2009-04-10
> **klopus said:**
> How to restore removed bottom panel?
Right click your top panel and select New Panel, then right click the new panel to add the widgets required, eg trash, window selector ect.

> Is there an OSX type dock that can auto-hide or bleed through windows?

Yes, Cairo !!

---

### Post by UbuntuNerd on 2009-04-10
you can also type this command in a terminal to restore your panels to default like they were before:
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```

---

### Post by Jimgary on 2009-05-03
Thanks for your solution but it's to another problem I'm having! When using virtual desktops in jaunty 9.04, the panel's aren't visible on the other desktops and, even worse, if I navigate to those desktops, I can't do anything. Compiz cube won't even work. The only thing I can do is to restart the X-server. If I reset the panels by:

gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

I don't have any problem but I'd rather not have to do this every time at start up. Any suggestions?

---

### Post by Sisyphus48 on 2009-05-18
Thank you UbuntuNerd for the info on restoring the panels; You save my bacon!!

---

### Post by Deerfoot on 2009-10-12
A big thank you to UbuntuNerd from me also!
I was freaking out when I deleted the bottom panel by mistake.

---

### Post by urbanop on 2009-12-21
This one worked very well for 8.04:

[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

---

### Post by semperfi83 on 2010-05-10
Props for UbuntuNerd, what a great tip.

Using Ubuntu 10.04:popcorn:

---

### Post by Alabaster on 2010-05-11
I reiterate the props. You da man.

---

