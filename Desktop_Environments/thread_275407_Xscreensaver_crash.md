---
title: "Xscreensaver crash"
date: 2006-10-11
forum: Desktop Environments
---

### Post by kop316 on 2006-10-11
Hello all

I recently installed XGL/Compix on my computer, and quickly figured out thet Gnome-screensaver does not work nicely with it. Doe to that, I switched to using Xscreensaver, and for some reason whenever I lock the screen with Xscreensaver the gdm resets on me after a certain period of time. 

I am using an Nvidia 6800 GS and I am using the closed source Nvidia drivers.

I checked the logs to see what is going on and I got this:

Messages
Oct 11 08:36:46 localhost gconfd (chris-5085): Resolved address +ACI-xml:readwrite:/home/chris/.gconf+ACI- to a writable configuration source at position 0
Oct 11 08:42:27 localhost exiting on signal 15
Oct 11 08:42:28 localhost syslogd 1.4.1+ACM-17ubuntu7: restart.

syslog
Oct 11 09:27:33 localhost dhclient: bound to 129.2.227.181 -- renewal in 3578 seconds.
Oct 11 08:42:28 localhost syslogd 1.4.1+ACM-17ubuntu7: restart.
Oct 11 08:42:28 localhost anacron+AFs-4859+AF0-: Job +AGA-cron.daily' terminated
Oct 11 08:42:28 localhost anacron+AFs-4859+AF0-: Normal exit (1 job run)
Oct 11 09:02:29 localhost -- MARK --

To me it looks like some program is telling it to shut down, but I have no idea what would cause that. Does anyone have an idea?

Thanks

---

### Post by geep on 2006-12-20
glxinfo |grep render

direct rendering: No

XGL doesn't like GL because it runs as a layer over you X11.

check if the xscreensaver you want to use uses GL


and for games run it in another screen

example

DISPLAY=:0 cedega ( for example )


Bottom line don't use GL screensavers with XGL. maybe in the new xorg there will be support for GL in XGL

---

