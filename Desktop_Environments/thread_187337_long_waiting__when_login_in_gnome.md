---
title: "long waiting  when login in gnome"
date: 2006-06-02
forum: Desktop Environments
---

### Post by lsh on 2006-06-02
:( I update my box to 6.06, after the login with GDM, i have to wait about 3-4 minutes before  gnome desktop is completely loaded.  the hd doesn't work. The console works (using ctrl+f1). 

this is my .xsession-errors,what can I do?:-(


-------------------------------------------------------------------------
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "root"
/etc/gdm/Xsession: Beginning session setup...
stdin: is not a tty
Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
Creating backend ...
SESSION_MANAGER=local/lostfly:/tmp/.ICE-unix/3615
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
Launching a SCIM process with x11...
Loading socket Config module ...
Creating backend ...
Loading x11 FrontEnd module ...
GTK Panel of SCIM 1.4.4

Starting SCIM as daemon ...
SCIM has been successfully launched.
Smart Common Input Method 1.4.4

Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

(gnome-panel:3752): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(gnome-panel:3752): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed
&#36733;&#20837; gnome-fs-desktop &#22833;&#36133;&#65306;&#26410;&#25214;&#21040;&#22270;&#26631;

//the line mean:load gnome-fs-desktop fail,can not find icons.

(gnome-panel:3752): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -9 and height 24
The application 'nautilus' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
gnome-panel: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
The application 'gnome-terminal' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
The application 'gksu' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
--------------------------------------------------------------------------

---

### Post by NewWithoutClue on 2006-06-02
/var/log/Xorg.0.log will probably give you an even better idea of what is wrong.

---

### Post by lsh on 2006-06-02
[QUOTE=NewWithoutClue]/var/log/Xorg.0.log will probably give you an even better idea of what is wrong.[/QUOTE]


this is xorg.0.log,thanks

---

### Post by el_baby on 2006-06-03
Hi NewWithoutClue :-)

I guess I'm newer and more clueless :-D

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

Does the ***defunct*** **xrdb** process rings any bells?

lsh... could you verify if you have a defunct xrdb process while your desktop is delaying its startup?

(do you know how to do this from a text console? I can explain this if you need it).


PS: FWIW, last thing I remember doing **before** this started happening is installing additional languages (Spanish and Hebrew).

---

### Post by lsh on 2006-06-04
yes ,I have more than one  defunct xrdb process ,and my card is   Nvidia's,
I should check compiz .:-)

---

### Post by kattydude on 2006-06-05
Did you try what's described in this thread ?
[http://ubuntuforums.org/showthread.php?t=158964&highlight=xrdb](http://ubuntuforums.org/showthread.php?t=158964&highlight=xrdb)

I had the same problem and the fix described (relating to the loopback interface) worked for me..

---

### Post by el_baby on 2006-06-05
Well... it **definitively** had to do with a non-existent localhost... that is, the interface existed but had no IP address assigned to it.

However, I still couldn't find the cause of these (though I think it is related to [thread=188959]my LVM setup[/thread]).

I ended up adding a line like this:
```
ifconfig lo 127.0.0.1
```
to my [FONT="fixed"]/etc/rc.local[/FONT] file... anyway, I'd like to really know why the loopback interface doesn't get its IP address...

---

