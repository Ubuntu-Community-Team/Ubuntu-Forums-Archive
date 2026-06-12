---
title: "gdm/nautilus broke after update..."
date: 2007-04-16
forum: Desktop Environments
---

### Post by pirothezero on 2007-04-16
Not really sure what happened.

I had to install 170 updates so I did. Asked for a restart when I do I get xserver screaming at me that glx module could not be loaded so I was like hmm wth so figured it was just the same thing as when you recompile a kernel you have to reinstall video drivers so I reinstall my nvidia drivers and when I go to startx it jumps right into the desktop instead of hitting a login manager. and I get this:

[http://obzftw.com/Screenshot-1.png](http://obzftw.com/Screenshot-1.png)

Before updating I had this:

[http://obzftw.com/Screenshot.png](http://obzftw.com/Screenshot.png)

Off the bat apparently this is whats wrong with nautilus/gdm doesnt want to work properly. T
Taskbars design on each window is like old gnome or something. 
Font looks different i think bigger mostly. 
No icons in any of the options in applications places or system.
Programs do not show up at the bottom on the taskbar no idea whats up with that.
ALT-TAB does not alt-tab which is always great.
In terminal I can't hold down left or right arrows to move the cursor I have to press it for each move over which is annoying.
Mouse sensitivity was reset to might as well have been zero. When I adjusted it it was down to zero and been like that since.

And the best part: My root password doesn't work in any of the Administration options in System yet it works in console for sudo...wtf....=/

Here is my .xsessions-errors:
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "piro"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/anubis:/tmp/.ICE-unix/4860
Window manager warning: 0 stored in GConf key /desktop/gnome/peripherals/mouse/cursor_size is not a reasonable cursor_size; must be in the range 1..128
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

(gnome-panel:4932): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -5 and height 24
evolution-alarm-notify-Message: Setting timeout for 27478 1176768000 1176740522
evolution-alarm-notify-Message:  Mon Apr 16 19:00:00 2007

evolution-alarm-notify-Message:  Mon Apr 16 11:22:02 2007

Conky: unknown variable temp
Conky: unknown variable temp
Conky: unknown variable fan
Conky: desktop window (1000061) is subwindow of root window (1a5)
Conky: window type - override
Conky: drawing to created window (2400002)
Conky: drawing to double buffer

(gnome-panel:4932): GConf-CRITICAL **: gconf_client_set_string: assertion `val != NULL' failed
Window manager warning: Error on terminal command "(null)": No terminal command has been defined.


(eog:5325): GLib-CRITICAL **: g_strcasecmp: assertion `s1 != NULL' failed

(eog:5325): Pango-CRITICAL **: pango_color_parse: assertion `spec != NULL' failed

(eog:5325): GLib-CRITICAL **: g_strcasecmp: assertion `s1 != NULL' failed

```

dont know what else to include.

thanks in advance.

---

