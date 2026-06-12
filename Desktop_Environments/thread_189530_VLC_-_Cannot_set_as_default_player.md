---
title: "VLC - Cannot set as default player"
date: 2006-06-05
forum: Desktop Environments
---

### Post by eeclark on 2006-06-05
When I right click on a video file, I cannot set VLC as the default player.
I get a message that it cannot add it to the database.

I have to go into VLC and open the video.

Tried "Open with..." in the properties of the file itself...tried to add VLC (also tried to add it as a custom command "wxvlc")  no luck

Exact message:
Could not add application to the application database

Does anyone know how to get this done?

I also tried changing the permissions on my .local folder from root to my login, but that did not help either.

---

### Post by dmorel on 2006-06-05
never mind... you already tried what I was suggesting! Ignore this post. sorry.

hth,
-morel

---

### Post by eeclark on 2006-06-05
Thanks anyway.

I was able to install mplayer and noticed that it shows in the list as alternate apps to open videos.

Any one know why I cannot set VLC as default?

---

### Post by eeclark on 2006-06-05
I also wanted to say that I installed the xine-ui package and get the same result.

No one else has tried a to set a default video player to view a file (mp4 or avi) with anything other than mplayer and totem?

---

### Post by cshake on 2006-06-05
[QUOTE=eeclark]No one else has tried a to set a default video player to view a file (mp4 or avi) with anything other than mplayer and totem?[/QUOTE]

My .avi context menu has Xfmedia, VLC, and Xine as my media players, I didn't have any problems adding them (had to manually locate the vlc bin, but once I did it worked).
Before I switched from gnome to xfce4 VLC was already working, so I don't think the window manager would be the problem. I also had .avi and .mp4 working in totem with gstreamer-ugly multiverse codecs, though that also shouldn't affect VLC.

Did you install VLC from the package manager or build it yourself? I don't know if that would make a difference, but it's possible.

[edit] I looked at your original post again - 'wxvlc'? I just pointed it to 'vlc' and it worked for me.

---

### Post by eeclark on 2006-06-06
tried pointing to both vlc and wxvlc - no luck.
These debs are fresh from the repo.

---

### Post by mlind on 2006-06-06
I'm using VLC as default player for all video formats, except .wmv.
I just used nautilus to assign default player for each format and it works.

Also using VLC from the official repos.

---

### Post by eeclark on 2006-06-06
can you wlak thru the steps you used?
Are you doing the right click on the file to set it or a diff method?

---

### Post by mlind on 2006-06-06
[QUOTE=eeclark]can you wlak thru the steps you used?
Are you doing the right click on the file to set it or a diff method?[/QUOTE]

yup. right-click file > Properties > Open With > VLC

does ~/.xsession-errors file contain any verbose output about the problem?

---

### Post by eeclark on 2006-06-06
This is weird.
The only thing I did was:
Reintall VLC and other req debs.
Stopped the TrailFocus plugin (Compiz/XGL)
Reboot

Now it shows.

In the past I have tried rebooting and logout/login so I do not think that was the resolution.

I had also tested it after reinstalling. 

I guess the magic combo was reinstall and reboot?? (I sure hope not)

I did have an xsession failure upon logout and login...that is why I had to reboot. It said that it did not have a screen to attach to.

---

### Post by mlind on 2006-06-06
[QUOTE=eeclark]It said that it did not have a screen to attach to.[/QUOTE]

Could you post the whole error message?

I had similar problem and resolution was to delete .Xauthority file and relogin.
I accidently started another X server using 'sudo', and root gain ownership of my
local .Xauthority.

---

### Post by eeclark on 2006-06-06
I can but I don't think it is in there.
Doesn't it get regenerated upon a successful reboot/relogin?

```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "edward"
/etc/gdm/Xsession: Beginning session setup...
Could not init font path element /usr/lib/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/lib/X11/fonts/OTF, removing from list!
Could not init font path element /usr/lib/X11/fonts/CID/, removing from list!
SESSION_MANAGER=local/smallville:/tmp/.ICE-unix/5110
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

** (update-notifier:5140): WARNING **: no cdrom: disk

evolution-alarm-notify-Message: Setting timeout for 52357 1149652800 1149600443
evolution-alarm-notify-Message:  Wed Jun  7 00:00:00 2006

evolution-alarm-notify-Message:  Tue Jun  6 09:27:23 2006

evolution-alarm-notify-Message: Loading file:///home/edward/.evolution/calendar/local/system

(gnome-panel:5130): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed
evolution-alarm-notify-Message: Loading
evolution-alarm-notify-Message: Loading contacts:///
evolution-alarm-notify-Message: Loading file:///home/edward/.evolution/tasks/local/system

(gnome-panel:5130): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -15 and height 24
evolution-alarm-notify-Message: Loading file:///home/edward/.evolution/memos/local/system
evolution-alarm-notify-Message: Loading alarms for today
evolution-alarm-notify-Message: Loading alarms for today
evolution-alarm-notify-Message: Loading alarms for today
evolution-alarm-notify-Message: Loading alarms for today
evolution-alarm-notify-Message: Loading alarms for today
pas-id-447747D60000000A-birthday has recurrences
pas-id-447747D600000017-anniversary has recurrences
pas-id-447747D600000017-birthday has recurrences
VLC media player 0.8.4 Janus
[00000261] main playlist: nothing to play


```

Also I own my .Xauthority.
```

-rw-------  1 edward edward      121 2006-06-06 09:27 .Xauthority


```

---

### Post by mlind on 2006-06-06
yeah, it's not on log anymore. You got it sorted nevertheless, that's what matters.

---

