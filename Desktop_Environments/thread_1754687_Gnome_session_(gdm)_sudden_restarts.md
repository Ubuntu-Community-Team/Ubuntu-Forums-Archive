---
title: "Gnome session (gdm?) sudden restarts"
date: 2011-05-10
forum: Desktop Environments
---

### Post by pedrosanta on 2011-05-10
Greetings.

About a week ago my Ubuntu 10.10 Maverick Merkaat started to restart my Gnome session at random, with no apparent reason. I'm working, sometimes even doing nothing, and suddently it restarts, from nowhere, (shows up tty7 in beetwen) and sends me to the session login screen - looks similar when I do "sudo /etc/init.d/gdm restart" from the console.

I didn't do anything in special before this behavior appeared (besides the usual updates, of course).

Which logs can I check out (and where are them) to know more about this strange behavior?

Thank you in advance for pointing me out in the right direction.

---

### Post by fballem on 2011-05-10
is there any possibility that your screensaver kicked in? By default, I believe the setting is 5 minutes and black screen. I've run into it myself where I am asked for my login after a very few minutes.

---

### Post by pedrosanta on 2011-05-10
> **fballem said:**
> is there any possibility that your screensaver kicked in? By default, I believe the setting is 5 minutes and black screen. I've run into it myself where I am asked for my login after a very few minutes.

I do not think it's the screensaver. I mean, it could be the starting of screensaver the source of some kind of error that restarts my session. When I say login it's really the session login screen, not the screensaver protection one.

But since that already happened when I was typing on a empathy chat I guess it's safe to rule out the screensaver. :/

Cheers.

---

### Post by Krytarik on 2011-05-10
Check the logs "~/.xsession-errors.old" and "/var/log/Xorg.0.log.old" after that happened the next time.

Greetings.

---

### Post by pedrosanta on 2011-05-11
> **Krytarik said:**
> Check the logs "~/.xsession-errors.old" and "/var/log/Xorg.0.old" after that happened the next time.

Cool bro. Thanks. Will do that and post info here afterwards.

---

### Post by psycho5 on 2011-05-11
> **Krytarik said:**
> Check the logs "~/.xsession-errors.old" and "/var/log/Xorg.0.old" after that happened the next time.

Greetings.

Greetings, I have the same problem and here is the logs, this JUST happened and I googled this post. I was just chatting on skype, and had firefox minimized.

~/.xsession-errors.old
```

(nautilus:1879): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1879): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1879): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

** (<unknown>:1870): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



** (<unknown>:1870): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



** (<unknown>:1870): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1870): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1870): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1870): WARNING **: Attempted to register a quicklist that was previously registered
NOTE: child process received `Goodbye', closing down
** (<unknown>:1870): DEBUG: MaximizeIfBigEnough: Empathy window size doesn't fit
** (process:1897): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events

(firefox-bin:2863): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed
** (<unknown>:1870): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate

** (<unknown>:1870): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



** (<unknown>:1870): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



** (<unknown>:1870): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
** (<unknown>:1870): DEBUG: MaximizeIfBigEnough: awn-applet window size doesn't fit

** (<unknown>:1870): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
Window 0x4a00018 created on ReparentNotify, map state isViewable? 0

** (<unknown>:1870): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
Window 0x4a00070 created on ReparentNotify, map state isViewable? 0
** (<unknown>:1870): DEBUG: MaximizeIfBigEnough: awn-applet window size doesn't fit

** (<unknown>:1870): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1870): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1870): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1870): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1870): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1870): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



** (<unknown>:1870): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
** (<unknown>:1870): DEBUG: TrayChild Accepted: (null) skype Skype
** (<unknown>:1870): DEBUG: MaximizeIfBigEnough: Skype window size doesn't fit
** (<unknown>:1870): DEBUG: MaximizeIfBigEnough: Skype window size doesn't fit

** (<unknown>:1870): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1870): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1870): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1870): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1870): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1870): WARNING **: Attempted to register a quicklist that was previously registered

** (<unknown>:1870): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1870): WARNING **: Attempted to register a quicklist that was previously registered

** (<unknown>:1870): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1870): WARNING **: Attempted to register a quicklist that was previously registered

** (<unknown>:1870): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1870): WARNING **: Attempted to register a quicklist that was previously registered

** (<unknown>:1870): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1870): WARNING **: Attempted to register a quicklist that was previously registered

** (<unknown>:1870): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1870): WARNING **: Attempted to register a quicklist that was previously registered

** (<unknown>:1870): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1870): WARNING **: Attempted to register a quicklist that was previously registered

** (<unknown>:1870): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
** (<unknown>:1870): DEBUG: MaximizeIfBigEnough: Empathy window size doesn't fit

** (<unknown>:1870): WARNING **: Attempted to register a quicklist that was previously registered
** (<unknown>:1870): DEBUG: MaximizeIfBigEnough: awn-applet window size doesn't fit

** (<unknown>:1870): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1870): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1870): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1870): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1870): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1870): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist



(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:1870): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:1870): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
Window 0x4a09d94 created on ReparentNotify, map state isViewable? 0
Window 0x4a09e47 created on ReparentNotify, map state isViewable? 0
** (<unknown>:1870): DEBUG: MaximizeIfBigEnough: Empathy window size doesn't fit
** (<unknown>:1870): DEBUG: MaximizeIfBigEnough: Empathy window size doesn't fit
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :2.
gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :2.
nautilus: Fatal IO error 11 (Resource temporarily unavailable) on X server :2.
ejecter: Fatal IO error 11 (Resource temporarily unavailable) on X server :2.
polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :2.
nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :2.
unity-window-decorator: Fatal IO error 11 (Resource temporarily unavailable) on X server :2.0.
gnome-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :2.
<unknown>: Fatal IO error 11 (Resource temporarily unavailable) on X server :2.
awn-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :2.0.
gnome-power-manager: Fatal IO error 11 (Resource temporarily unavailable) on X server :2.
evolution-alarm-notify: Fatal IO error 11 (Resource temporarily unavailable) on X server :2.
avant-window-navigator: Fatal IO error 104 (Connection reset by peer) on X server :2.
gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :2.
applet.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :2.
gwibber-service: Fatal IO error 11 (Resource temporarily unavailable) on X server :2.
alarmclock: Fatal IO error 11 (Resource temporarily unavailable) on X server :2.
update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :2.
bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :2.
firefox-bin: Fatal IO error 11 (Resource temporarily unavailable) on X server :2.
<unknown>: Fatal IO error 11 (Resource temporarily unavailable) on X server :2.
** (process:1897): DEBUG: zeitgeist-datahub.vala:58: Zeitgeist-daemon disappeared from the bus, exitting...

** (process:1897): WARNING **: zeitgeist-datahub.vala:218: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.


```

and 

for Xorg.O.old
```

oj@oj-desktop:~$ cat /var/log/Xorg.0.old
cat: /var/log/Xorg.0.old: No such file or directory
oj@oj-desktop:~$ cat /var/log/Xorg.O.old
cat: /var/log/Xorg.O.old: No such file or directory

```

So what do we do from here?

---

### Post by Krytarik on 2011-05-11
psycho5, I had a typo in the name of the log file, check again with "/var/log/Xorg.0.log.old", and it's a zero in the middle.

---

### Post by pedrosanta on 2011-05-15
Ok. Happened again. Was playing around with LibreOffice and BAM!, tty7, session restart, login screen.

My logs (on paste.ubuntu.com):

[**~/.xsession-errors.old**]("http://paste.ubuntu.com/607774/")

[**/var/log/Xorg.0.log.old**]("http://paste.ubuntu.com/607776/")

I'm gonna run through these and see if I can make some sense out of it.

Cheers.

---

### Post by pedrosanta on 2011-05-15
It looks like it has something to do with the Hardware Sensors plugin from Awn Dock ([~/.xsession-errors.old]("http://paste.ubuntu.com/607774/"), line 820).

I already disabled it. I'm gonna look if it keeps occurring, look a little further on this and maybe submit a bug to Awn.

Cheers.

---

### Post by Krytarik on 2011-05-15
I don't think that the cause is AWN's Hardware Sensors applet. Instead it seems like the xserver crashed for another reason, logged at the end of "Xorg.0.log.old", but there is no obvious hint to what might be the cause.

However, most often it's caused by the video driver. Currently, you are running the "nvidia-current" driver, you may try the "nvidia-173" instead. To do so, install/activate it through "System -> Administration -> Additional Drivers".

---

### Post by pedrosanta on 2011-05-15
> **Krytarik said:**
> However, most often it's caused by the video driver. Currently, you are running the "nvidia-current" driver, you may try the "nvidia-173" instead. To do so, install/activate it through "System -> Administration -> Additional Drivers".

Ok, I'll try that. Thx. Cheers.

---

### Post by xrat on 2011-05-20
I was recently dealing with the same symptoms, though on different hardware ([the discussion of it was in German]("http://www.luga.at/mailing-lists/luga/2011/05/msg00087.html")).

I recommend you first check your xorg.conf (a FontPath entry was caused my X to crash).

Besides, try to find a pattern that allows you to reproduce the crash. If this does not already indicate where the problem lies get a full backtrace, see [http://wiki.debian.org/HowToGetABacktrace](http://wiki.debian.org/HowToGetABacktrace) and [https://wiki.ubuntu.com/X/Backtracing](https://wiki.ubuntu.com/X/Backtracing)

---

### Post by pedrosanta on 2011-06-13
> **Krytarik said:**
> I don't think that the cause is AWN's Hardware Sensors applet. Instead it seems like the xserver crashed for another reason, logged at the end of "Xorg.0.log.old", but there is no obvious hint to what might be the cause.

However, most often it's caused by the video driver. Currently, you are running the "nvidia-current" driver, you may try the "nvidia-173" instead. To do so, install/activate it through "System -> Administration -> Additional Drivers".

With that version Wine applications run excruciatingly slow, and I need a couple for my daily work. I had to revert to "nvidia-current" before I could test the problem with that version. :/

---

### Post by pedrosanta on 2011-06-13
Hi. I began noticing a pattern in the last couple of times this happened - it keeps occurring.

In the last times this restart occurred when I close the last remaining open Chrome window. My version of Chrome is the stable 11.0.696.57.

I will try to update this version and check if it keeps occurring.

Cheers.

---

### Post by atul_dapper on 2011-08-29
> **xrat said:**
> I was recently dealing with the same symptoms, though on different hardware ([the discussion of it was in German]("http://www.luga.at/mailing-lists/luga/2011/05/msg00087.html")).

I recommend you first check your xorg.conf (a FontPath entry was caused my X to crash).

Besides, try to find a pattern that allows you to reproduce the crash. If this does not already indicate where the problem lies get a full backtrace, see [http://wiki.debian.org/HowToGetABacktrace](http://wiki.debian.org/HowToGetABacktrace) and [https://wiki.ubuntu.com/X/Backtracing](https://wiki.ubuntu.com/X/Backtracing)


Fantastic reply, thank you very much!!  

The xorg.conf-FontPath was the culprit in my case.

I had struggled to get at the cause and had completely given up.  Thanks to all your links, especially the Debian one since I am on Debian.

Please keep up the good work.

Regards.

---

### Post by marco1123 on 2011-10-10
> **atul_dapper said:**
> Fantastic reply, thank you very much!!  

The xorg.conf-FontPath was the culprit in my case.

I had struggled to get at the cause and had completely given up.  Thanks to all your links, especially the Debian one since I am on Debian.

Please keep up the good work.

Regards.

Hi atul_dapper! I have the same problem as you, but instead, I don't have a FontPath to blame. I'm suspecting this can be a module related issue.

I would appreciate if you could tell me which kernel version are you using. My video chipset is Intel based, so I doubt it can be a module related issue.

Thanks in Advance!

---

### Post by pedrosanta on 2011-10-11
FYI, I don't longer have this issue since I've updated to Ubuntu 11.04. Thanks everyone for the help.

Cheers.

---

### Post by OnSite511 on 2012-01-18
Both my wife and I have a similar issue. I was able to open Xorg.0.log.old and these seem to be the relevant lines:


```

[  1546.978] 
Backtrace:
[  1547.305] 0: /usr/bin/X (xorg_backtrace+0x37) [0x80a66f7]
[  1547.305] 1: /usr/bin/X (0x8048000+0x62b3a) [0x80aab3a]
[  1547.305] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xecf40c]
[  1547.305] 3: (vdso) (__kernel_vsyscall+0x2) [0xecf416]
[  1547.305] 4: /lib/i386-linux-gnu/libc.so.6 (__select+0x2d) [0x33ae9d]
[  1547.305] 5: /usr/bin/X (WaitForSomething+0x18c) [0x80a3f8c]
[  1547.306] 6: /usr/bin/X (0x8048000+0x29ed2) [0x8071ed2]
[  1547.306] 7: /usr/bin/X (0x8048000+0x1c70c) [0x806470c]
[  1547.306] 8: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xf3) [0x289113]
[  1547.306] 9: /usr/bin/X (0x8048000+0x1ca21) [0x8064a21]
[  1547.308] 
Caught signal 3 (Quit). Server aborting
[  1547.308]

```

It seems to be fairly reproducable with a rapid double enter in Firefox. I'll see about reproducing again after I post this. Edit: posted and edited w/double enter. no error. can't be that....

Any ideas as to what/where I should start looking?

---

