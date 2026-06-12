---
title: "startup services control in XFCE"
date: 2011-01-06
forum: Desktop Environments
---

### Post by elmosim2 on 2011-01-06
I'm running antiX, I know it isn't ubuntu but it's technically ubuntu based right?  Anyway, I'm trying to run just gnome-panel under the xfce environment.  I have gnome-panel installed (I can open it from a terminal).  But, I can't seem to figure out how to get it to open at startup.  There's a nifty "Choose Startup Services" option in the antiX Control Center but it only lets me manage services that it already has in a list.  

I would just flat out run gnome but I'm trying to keep things light.  Any ideas?

---

### Post by Simian Man on 2011-01-06
Why would you run gnome-panel over the Xfce panel?  Xfce can use gnome-panel applets with xfapplet and gnome-panel is much buggier than the Xfce panel.

---

### Post by elmosim2 on 2011-01-06
I need to lock it down to users can't edit anything at all.  The XFCE kiosk mode documentation is really old and doesn't seem to apply anymore.  The gnome-panel is easily locked down with pessulus.

---

### Post by sisco311 on 2011-01-06
It works for me. I'm using Xfce 4.6.2.

You have to create and edit the file /etc/xdg/xfce4/kiosk/kioskrc or if you are using Xubuntu /etc/xdg/xubuntu/kiosk/kioskrc and add something like:
```
[xfce4-panel]
CustomizePanel=%**panelgroup,user1,user2**
```

This will allow only the group **panelgroup** and the users **user1** and **user2** to customize their panels.

EDIT:
See [http://wiki.xfce.org/howto/kiosk_mode](http://wiki.xfce.org/howto/kiosk_mode)

---

### Post by elmosim2 on 2011-01-11
My mistake, I must have been looking at the wrong documentation or something.    Thank you for pointing me in the right direction.

---

