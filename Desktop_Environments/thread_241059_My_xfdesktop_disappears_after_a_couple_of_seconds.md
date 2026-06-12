---
title: "My xfdesktop disappears after a couple of seconds"
date: 2006-08-21
forum: Desktop Environments
---

### Post by jdk_ on 2006-08-21
Hi everyone,

I have been happily using xfce for some time, I had ubuntu and installed xubuntu-desktop.

Since a couple of hours ago when I log in everything seems fine but after a couple of seconds or the first window openning my (xf)desktop dies, the wallpaper is still there but no icons and no menu if I right-click on the wallpaper. Also, the background of my terminals is black rather than showing the wallpaper as it was before --this morning!

The .xsession-errors file says:

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "jdkycdoc"
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/startxfce4: X server already running on display :0

** (xfwm4:5276): WARNING **: The display does not support the XComposite extension.

** (xfwm4:5276): WARNING **: Compositing manager disabled.

** (update-notifier:5308): WARNING **: already running?
```

What happened? No idea, the only thing I can think of are:

-- A couple of days ago I followed this [guide]("http://www.ubuntuforums.org/showthread.php?t=205865") --but in the end I didn't think it was worthy to regularly use conky--, and today for the first time I untick the "Save session" checkbox at logout.

-- my laptop run out of battery and didn't shutdown properly --as power management doesn't work fine here and I forgot to plug it at some point.

I already tried to run xfdesktop and log out saving the session, it didn't help.

Thanks a lot for any help.

---

