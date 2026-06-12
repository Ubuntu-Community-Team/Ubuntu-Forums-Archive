---
title: "Conky hide from single desktop in Gnome Shell?"
date: 2012-08-15
forum: Desktop Environments
---

### Post by khughitt on 2012-08-15
Does anyone know if it is possible to either hide conky from a single desktop, or to display it on one or more desktops in Gnome 3?

---

### Post by Sector11 on 2012-08-24
> **pwnedd said:**
> Does anyone know if it is possible to either hide conky from a single desktop, or to display it on one or more desktops in Gnome 3?

I do not use GNOME 3 but running a conky on a single desktop is easy with OpenBox.
**WARNING:**  Compiz considers all desktops as one huge desktop.  Other composite managers may or may not.  xcompmgr and compton does not.

> Wmctrl is a command line tool to interact with an
EWMH/NetWM compatible X Window Manager (examples include
Enlightenment, icewm, kwin, metacity, and sawfish).

Wmctrl provides command line access to almost all the features
defined in the EWMH specification. For example it can maximize
windows, make them sticky, set them to be always on top. It can
switch and resize desktops and perform many other useful
operations.

```
sudo apt-get install wmctrl
```

In conky remove 'sticky' from *own_window_hints*:
```
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar,skip_pager
```
on conkys that will only run on the desktop that you start them on.

To continue:
```
Desktop count: 1, 2, 3, 4 ...
wmctrl counts: 0, 1, 2, 3 ...
```

so from my autostart.sh:
```
# Daily
wmctrl -s 1 &
 conky -c ~/Conky/S11_email.conky &
 conky -c ~/Conky/S11_v9_R.conky &
 conky -c ~/Conky/S11_Dates.conky &
 conky -c ~/Conky/S11_v9_SM.conky &
 conky -c ~/Conky/S11_VNS.conky &
 conky -c ~/Conky/S11_CB.conky &
 conky -c ~/Conky/S11_Rem_Cal.conky &
 conky -c ~/Conky/S11_v9_H.conky &
	(sleep 10s && wmctrl -s 0 && conky -c ~/Conky/S11_Chronograph.conky) &
	(sleep 10s && wmctrl -s 0 && conky -c ~/Conky/VO_Radiotray.conky) &
	(sleep 10s && wmctrl -s 0 && conky -c ~/Conky/S11_coin.conky) &
```

Explanation:
[LIST=1]
[*]*wmctrl -s 1*  puts the booting system on Desktop 2
[*]the next 8 lines start 8 conkys, the first two have the 'sticky' the next six do not - six conkys only on Desktop 2 and two on 'all' desktops.
[*]the last three lines; sleep for 10 seconds - wmctrl switches to desktop 1 - and three conkys added - they have NO 'sticky' so they only show on Desktop 1
[/LIST]

Hope that helps.
Thanks to mobilediesel.

---

