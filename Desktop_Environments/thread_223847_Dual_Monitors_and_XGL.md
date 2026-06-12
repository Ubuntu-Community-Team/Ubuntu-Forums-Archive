---
title: "Dual Monitors and XGL?"
date: 2006-07-27
forum: Desktop Environments
---

### Post by ModusOperandi on 2006-07-27
Is it possible to have Xgl work on a dual-head (big desktop) setup? I know that XGL does something to the display in order to have it's composition (reroute the output of X to display 1 instead of display 0?), but I have no idea if XGL can handle the "1"display being used.

TIA

Edit: I had installed Xgl before I enabled Big Desktop. I have been running off of Failsafe Gnome, which I why I could post. I logged out and tried to log in using the Gnome Session, but it only loaded the first of the icons in that Ubuntu splash. It stopped there and the only thing I could do was move the mouse. I had to hard-reboot and load up Failsafe Gnome to edit this post.

I have a Radeon X850 Pro (AGP) with the latest fglrx drivers and Xgl packages available via Synaptic.

---

### Post by RAOF on 2006-07-27
Current XGL should work with dual-head setups.  If you've got your XGL packages from xgl.compiz.info (or any of the repositories mentioned on [compiz.net](compiz.net)), then you should be right.

If you're using the XGL from the Ubuntu Universe repository, then it 'aint gonna work.  That XGL is ancient, and one of the many updates between then and now has been dual-head support.

---

### Post by ModusOperandi on 2006-07-27
I added "deb [http://xgl.compiz.info](http://xgl.compiz.info) dapper main" to sources.list and then clicked reload and upgrade in Synaptic. It found the upgrades to the xgl and compiz packages, but when I logged back in under gnome, it did the same thing (pause after "Window Manager")

---

### Post by RAOF on 2006-07-27
1) It might be useful to have more info about precisely **how** you've set up XGL - there have been so many different howtos posted :)

2) It's probably a good idea to continue asking on the [compiz.net](compiz.net) forums.  I haven't had any dual-head experience, but there are **definitely** people there who have.

---

### Post by leohart on 2006-07-27
I don't think I will be of much help to you but a word for your courage, rest assure my friend since I am running my Ubuntu box with Compiz and Dual Monitor (Twinview via nVidia binary driver).

Just keep looking on compiz.net forum.;)

---

### Post by ModusOperandi on 2006-07-31
I uninstalled and reinstalled the Xgl and Compiz packages (they had been installed when I had enabled big desktop mode.) This time, I can load the normal Gnome session fine, but Xgl doesn't start, and in my Home folder there is a a file called .xsession-errors (contents below.) I set up Xgl with the .Xsession script in my home folder, and that worked until I tried to do the dual-head setup.

The .Xsession-errors file:
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "modusoperandi"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/modus-desktop:/tmp/.ICE-unix/5179
esd: Esound sound daemon already running or stale UNIX socket
/tmp/.esd-1000/socket
This socket already exists indicating esd is already running.
Exiting...
esd: Esound sound daemon already running or stale UNIX socket
/tmp/.esd-1000/socket
This socket already exists indicating esd is already running.
Exiting...

** (gnome-session:5179): WARNING **: Esound failed to start.

Gnome-Message: gnome_execute_async_with_env_fds: returning -1

(gnome-panel:5709): GConf-WARNING **: Directory `/apps/panel/toplevels/bottom_panel_screen1/screen' was not being monitored by GConfClient 0x81226b8

(gnome-panel:5709): GConf-WARNING **: Directory `/apps/panel/toplevels/top_panel_screen1/screen' was not being monitored by GConfClient 0x81226b8

(gnome-panel:5709): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed
evolution-alarm-notify-Message: Setting timeout for 85857 1154415600 1154329743
evolution-alarm-notify-Message:  Tue Aug  1 00:00:00 2006

evolution-alarm-notify-Message:  Mon Jul 31 00:09:03 2006

evolution-alarm-notify-Message: Loading file:///home/modusoperandi/.evolution/calendar/local/system
CalDAV Eplugin starting up ...
evolution-alarm-notify-Message: Loading contacts:///
evolution-alarm-notify-Message: Loading file:///home/modusoperandi/.evolution/tasks/local/system
evolution-alarm-notify-Message: Loading file:///home/modusoperandi/.evolution/memos/local/system
evolution-alarm-notify-Message: Loading alarms for today
evolution-alarm-notify-Message: Loading alarms for today
evolution-alarm-notify-Message: Loading alarms for today
evolution-alarm-notify-Message: Loading alarms for today

(gnome-panel:5709): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -21 and height 24

(evolution-2.6:5742): evolution-mail-WARNING **: ignored this junk plugin: not enabled or we have already loaded one

(evolution-2.6:5742): e-utils-WARNING **: Plugin 'Bogofilter junk plugin' failed to load hook 'org.gnome.evolution.mail.junk:1.0'

(evolution-2.6:5742): camel-WARNING **: camel_exception_get_id called with NULL parameter.

```

---

### Post by DarkNemesis618 on 2006-07-31
I have dual monitors and XGL works fine for me.  I used the following link for setting it up.

[http://www.ubuntuforums.org/showthread.php?t=131267]("http://www.ubuntuforums.org/showthread.php?t=131267")

Here are some screens.
[Screenshot 1]("http://photos1.blogger.com/blogger/2346/822/1600/screen3.jpg")

[Screenshot 2]("http://photos1.blogger.com/blogger/2346/822/1600/screen2.jpg")

[Screenshot 3]("http://photos1.blogger.com/blogger/2346/822/1600/screen1.jpg")

---

