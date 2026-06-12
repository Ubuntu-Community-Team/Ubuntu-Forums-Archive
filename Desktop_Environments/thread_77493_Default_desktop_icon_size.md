---
title: "Default desktop icon size?"
date: 2005-10-16
forum: Desktop Environments
---

### Post by naked on 2005-10-16
Is there a way to have them be scaled all the way down by default?  I *hate* the massive icons.  For images it is sometimes ok for them to be that big, but i'd still rather them be tiny so I can have more room to work with.  I don't like icons on my desktop anyways, but the few that I do want, I want them to be small.

Anything I can change?

L

---

### Post by jasay on 2005-10-16
I know you can right click and "stretch" the icons.  I'm still looking for a better method so that all icons are, by default, the same dictatable size.

---

### Post by naked on 2005-10-16
Right, stretching the icons small works fine for me.  But doing that with 10 icons evertime gnome decides to reset my icon prefs sucks!

Thanks though.

Anyone else?

L

---

### Post by professor_chaos on 2005-10-16
nautilus -> Edit -> Preferences -> Icon View Defaults -> Default Zoom Level

---

### Post by naked on 2005-10-16
That works for Nautilus, but not for the desktop.

L

---

### Post by lonetree on 2005-10-17
Go to 
Applications | System Tools | Configuration Editor
Expand 'apps', then expand 'nautilus', then goto 'icon_view' and change 'default_zoom_level' from "standard" to "small"

hope this helps


regards,

---

### Post by dtfinch on 2005-10-17
Thank you. I've been wondering how to do this for years.

---

### Post by naked on 2005-10-17
[QUOTE=lonetree]Go to 
Applications | System Tools | Configuration Editor
Expand 'apps', then expand 'nautilus', then goto 'icon_view' and change 'default_zoom_level' from "standard" to "small"

hope this helps


regards,[/QUOTE]

Anyone know if there is something between 'small' and 'tiny'?  Small is a LOT better, but I would still like them a little smaller.  I tried 'tiny' to see what would happen, well, they are TINY!

Thanks though!

Luke

---

### Post by lonetree on 2005-10-17
try smaller then

---

### Post by bvc on 2005-10-17
[QUOTE=naked]Anyone know if there is something between 'small' and 'tiny'?  Small is a LOT better, but I would still like them a little smaller.  I tried 'tiny' to see what would happen, well, they are TINY!

Thanks though!

Luke[/QUOTE]Edit the index.theme file of the theme. This was> [scalable/filesystems]
MinSize=1
Size=128
MaxSize=128
Context=FileSystems
Type=scalable
but it can be whatever you want it to be
> [scalable/filesystems]
MinSize=1
Size=256
MaxSize=256
Context=FileSystems
Type=scalablewhich believe it or not actually makes them smaller. Of course the down side is that you have to do this for all the diff sections of the file ....devices, apps, mimetypes etc, etc....

---

