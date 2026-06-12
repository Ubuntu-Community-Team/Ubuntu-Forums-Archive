---
title: "wrong script causes delay in the autostartup of all apps."
date: 2009-02-25
forum: General Help
---

### Post by deformation on 2009-02-25
Hello

I am getting this really annoying problem, I get a 60 seconds delay in the startup process. that means all my startup apps "network manager, conky etc etc" will fireup after 60 seconds of my login.

the problem happened while configuring my system to use dropbox uploader, i got this script from some forums :

> # Just in case some random app calls on Nautilus, lets set some safeguards to minimise the impact:
# Disable Nautilus desktop, because we really really do not want it!
gconftool-2 -s -t bool /apps/nautilus/preferences/show_desktop false &
# Do not let Nautilus set the background, because we really really do not want this either.
gconftool-2 -s -t bool /desktop/gnome/background/draw_background false &
# Make Nautilus use spatial mode, should start-up quicker.
gconftool-2 -s -t bool /apps/nautilus/preferences/always_use_browser false &
# Make Nautilus show the advanced permissions dialog -- if it has to start, lets at least make it usable :) 
gconftool-2 -s -t bool /apps/nautilus/preferences/show_advanced_permissions true &
# And finally...
# ...start dropbox daemon, but give it a minute so we can establish a net connection.
(sleep 60s && ~/.dropbox-dist/dropboxd) &

obviously the last line is responsible about the delay i am getting.

I deleted dropbox folder, and all the scripts associated with it. but the problem still here, i got a 60 sec delay in the startup of all the startup apps.

any help is much appreciated.

---

### Post by deformation on 2009-02-27
bump

---

### Post by deformation on 2009-03-27
bump 

come on people :/ i am desperate here.

---

### Post by deformation on 2009-05-30
come on people, help please :(

---

### Post by ontwowheels on 2009-06-01
Have you tried going into the start applications and selecting the option to "remember running applications".  Or however it is stated, I am not on my Ubuntu machine at the moment.

Anyway, I would close all apps down and check that setting and do a shutdown.  Start back up and see if that changes anything.

---

### Post by Brandon Williams on 2009-06-01
Are you saying that you deleted the quoted script but the 60 second delay is still there? Or did you just delete the ~/.dropbox-dist directory? If you are still running the script, why? And more importantly, how is it being launched?

Delay in one app that is configured as a 'Startup Application' (or whatever it's called in gnome) will not cause other apps to be delayed. You would only see a delay in startup of other things if you're running the script in some other way, perhaps from .xsession or .xsessionrc.

---

### Post by deformation on 2009-06-01
> **ontwowheels said:**
> Have you tried going into the start applications and selecting the option to "remember running applications".  Or however it is stated, I am not on my Ubuntu machine at the moment.

Anyway, I would close all apps down and check that setting and do a shutdown.  Start back up and see if that changes anything.

why would i try to remember running apps? hows that going to help?

i did remove all the autostart apps from my list, and shutdown to do a clean fresh startup, still same, i got a delay in the start up of network manager, if i choose a new app to autostart, for example : pidgin, it will still take 60 seconds delay.

---

### Post by deformation on 2009-06-01
> **Brandon Williams said:**
> Are you saying that you deleted the quoted script but the 60 second delay is still there? Or did you just delete the ~/.dropbox-dist directory? If you are still running the script, why? And more importantly, how is it being launched?

Delay in one app that is configured as a 'Startup Application' (or whatever it's called in gnome) will not cause other apps to be delayed. You would only see a delay in startup of other things if you're running the script in some other way, perhaps from .xsession or .xsessionrc.

i deleted the whole .dropbox folder, and deleted the script, the script name was autostart.sh, i deleted it then did a search for anything named autostart.sh or dropbox, nothing found.

here is my list of autostart apps :
> 
xd4@xd4-laptop:~$ ls -la /home/xd4/.config/autostart
total 44
drwx------  2 xd4 xd4 4096 2009-03-12 12:39 .
drwxr-xr-x 24 xd4 xd4 4096 2009-04-17 22:49 ..
-rw-r--r--  1 xd4 xd4  134 2008-11-09 15:59 conky.desktop
-rw-r--r--  1 xd4 xd4  443 2008-11-09 15:58 jockey-gtk.desktop
lrwxrwxrwx  1 xd4 xd4   44 2009-03-12 12:39 qstart.desktop -> /usr/lib/openoffice/share/xdg/qstart.desktop
-rw-r--r--  1 xd4 xd4 5121 2008-11-09 15:58 redhat-print-applet.desktop
-rw-r--r--  1 xd4 xd4  147 2008-12-29 08:07 tilda.desktop
-rw-r--r--  1 xd4 xd4 2308 2008-12-09 09:46 tracker-applet.desktop
-rw-r--r--  1 xd4 xd4 1864 2008-12-09 09:46 trackerd.desktop
-rw-r--r--  1 xd4 xd4  339 2008-11-09 15:58 update-notifier.desktop
-rw-r--r--  1 xd4 xd4  166 2008-12-28 18:10 xpad.desktop

---

