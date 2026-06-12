---
title: "XDMCP in second display session"
date: 2007-03-22
forum: Desktop Environments
---

### Post by suRoot on 2007-03-22
Hi...

Is it possible to get a remote XDMCP to start in a second X session?

For instance, I want the ability to have my local desktop on display :0 (ctrl+alt+f7)

I would like to press ctrl+alt+f8 & be able to see the desktop of my remote XDMCP host... yet still have the ability to switch back to my local desktop.

It seems that the default behavior when I login remotely via XDMCP is that it takes away my local session & I no longer have access to my local desktop.

I guess the underlying question would be how do I start a second X server?  I think if I can do that then I can accomplish my goal.

Thanks.

---

### Post by Rui Pais on 2007-03-22
Hi,
yes, of course.
Just edit /etc/X11/gdm/gdm.conf-custom and add on section:
> [servers]
the following:
```
1=Terminal -query <other_machiner_ip_or_name>

```

replacing *<other_machiner_ip_or_name>* with the ip or the network name of the machine you want to use.

hth

---

