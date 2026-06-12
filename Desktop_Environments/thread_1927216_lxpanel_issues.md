---
title: "lxpanel issues"
date: 2012-02-17
forum: Desktop Environments
---

### Post by Gordon D on 2012-02-17
Hi,

My initial impression of the lubuntu desktop was good. It was just what I was after for my older netbook pc that was struggling will the latest Ubuntu 11.10 release.

I am having ongoing issues with lxpanel running and 100% and requiring a "lxpanelctl restart" and also, when the machine comes out of standby, the icons are strangely spaced.

The only software I have added to the default is Thunderbird/Lightning and Ubuntu One.

These issues seem to have been around for a while given the google hits I get on them and although fairly minor are enough of an issue to have me consider alternate desktops or distros.

Anyway, I am more than happy to help to provide more technical information (with a little hand holding) as I would prefer not to dump the whole desktop because of this.

Cheers

Gordon

---

### Post by ajgreeny on 2012-02-17
Unfortunately this is a well known problem that seems to be associated with the presence of the power-manager icon in the system tray of lxpanel; remove the icon with the power-manager preferences and the empty spaces that appear, particularly after coming out of suspend, or when plugging in or unplugging a mains electricity supply, seem to go away.

I have a simple script in my home which I run with an alias in terminal
```
#!/bin/bash

killall lxpanel
find ~/.cache/menus -name '*' -type f -print0 | xargs -0 rm
lxpanel -p Lubuntu &
```which works very easily and quickly, and the glitch is not big or troublesome enough to stop me using Lubuntu on my netbook.

The problem is being looked at, I think, by developers of LXDE as it is an LXDE problem, not specifically Lubuntu, and the speed of LXDE development is very fast at the moment, so try to hang in there and you may find it is dealt with quicker than you think.

---

### Post by Rodney9 on 2012-02-17
Unfortunately it seems to be a bug that effects some laptops, luckily not mine.

Here is the bug report with some workarounds - 

[https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/846878](https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/846878)

Here is some other workarounds - 

[http://ubuntuforums.org/showthread.php?t=1869357](http://ubuntuforums.org/showthread.php?t=1869357)



For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by Gordon D on 2012-02-17
> **ajgreeny said:**
> 
I have a simple script in my home which I run with an alias in terminal
```
#!/bin/bash

killall lxpanel
find ~/.cache/menus -name '*' -type f -print0 | xargs -0 rm
lxpanel -p Lubuntu &
```

Many thanks for this ... combined with switching off the power management icon, I think I can live with this until the cavalry arrives :p

Gordon

---

### Post by ajgreeny on 2012-02-18
> **Gordon D said:**
> Many thanks for this ... combined with switching off the power management icon, I think I can live with this until the cavalry arrives :p

Gordon
If you really need a battery icon in your panel there is a battery-monitor applet available in the list.

Also if the xfce4-power-manager was only available from the panel icon, you can make it show in the Lubuntu menu with ```
gksu leafpad /usr/share/applications/power-manager.desktop
```and delete or comment out the line which says something like "Only show in XFCE"  I deleted it from mine, so can't remember the exact line, but it will be obvious.

---

### Post by nomnex on 2013-02-02
> **Gordon D said:**
> I think I can live with this until the cavalry arrives

Henry Gebhardt is the new maintainer of the LX Panel since January 2013.
 The panel did not have maintainer for some time. The latest version is 0.5.12.
There's a bug report upstream.
[http://sourceforge.net/tracker/?func=detail&aid=3030538&group_id=180858&atid=894869](http://sourceforge.net/tracker/?func=detail&aid=3030538&group_id=180858&atid=894869)
I would not be too optimistic about a stable panel, on all type of hardware, anytime soon.

---

