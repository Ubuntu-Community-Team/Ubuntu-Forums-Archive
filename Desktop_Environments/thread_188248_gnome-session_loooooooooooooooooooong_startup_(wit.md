---
title: "gnome-session loooooooooooooooooooong startup (with xrdb process defunct)"
date: 2006-06-03
forum: Desktop Environments
---

### Post by el_baby on 2006-06-03
Hi, [I posted this]("http://www.ubuntuforums.org/showthread.php?p=1087373#post1087373") as a follow-up of [a previous post]("http://www.ubuntuforums.org/showthread.php?p=1084611"), and got no response... maybe posting it as a new thread will get me somewhere...

I just installed my first ubuntu (dapper-desktop from release cd).

It went somehow fine but after a while, I got the same delays that lsh says he has.

What I notice is that during this delay at the x session startup, I see a ***defunct*** **xrdb** process (which I can't kill).

When this process finally dies (whether I try to kill it or not), apparently the xsession completes its startup with these errors in .xsession-errors:

```
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

(gnome-panel:6465): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(gnome-panel:6465): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -5 and height 24

``` 
Most of my searches about this send me to [this large thread]("http://www.ubuntuforums.org/showthread.php?t=131267"), but this seems to be more related to installing compiz with an Nvidia card...

I don't use compiz and my card is an Intel i810 (on board), so I don't think this is quite related.

The desktop eventually starts up and then everything is normal. Does the ***defunct*** **xrdb** process rings any bells?

FWIW, last thing I remember doing **before** this started happening is installing additional languages (Spanish and Hebrew).

Other than that, the system runs fine... well... the graphical "Users and Groups" interface also takes quite long to start... but that's a minor annoyance.

I think I'm sticking with Ubuntu...

---

### Post by el_baby on 2006-06-05
Well... noone answered, but I finally nailed it down to the loopback interface (localhost) not having an IP address (should be 127.0.0.1).

I still don't know why that happened, but it probably had something to do, in my case, with migrating the [FONT=Courier New]root[/FONT] and [FONT=Courier New]/var[/FONT] filesystems to **LVM** as I explain [thread=188959]in this thread[/thread].

For now, I simply added:
```
ifconfig lo 127.0.0.1
``` to my [FONT=Courier New]/etc/rc.local[/FONT] startup script and it works fine.

---

