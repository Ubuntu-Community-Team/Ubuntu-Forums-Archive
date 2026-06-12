---
title: "OS X Icon theme causes crash during log in"
date: 2007-06-02
forum: Desktop Effects &amp; Customization
---

### Post by Death_Sargent on 2007-06-02
I have been trying to use the OSX icon theme from 

[http://nekohayo.googlepages.com/icons](http://nekohayo.googlepages.com/icons)

however everytime i try to log in with said theme i get a message about my sesion only lasting ten seconds although while on nonxgl sessions everything renders as it should. though I still get this error code in the box

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "pete"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/pete-laptop:/tmp/.ICE-unix/8217
Initializing nautilus-main-menu extension
Initializing gnome-mount extension
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

** (gsynaptics-init:8311): WARNING **: Using synclient
Xlib: connection to ":0.0" refused by server

Xlib: No protocol specified



(firestarter:8314): Gtk-WARNING **: cannot open display:  
/usr/local/bin/start_beryl.sh: Error: beryl-manager not launched. Xgl not running?
Unknown parameter CoastingSpeedThreshold

(search:8303): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(evolution-alarm-notify:8315): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-power-manager:8316): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
```

please note i have posted this else where i just though a change of location and name might better my chances of getting support

---

### Post by Death_Sargent on 2007-06-02
anyone have any clue

---

### Post by Death_Sargent on 2007-06-02
tried a similar theme called osx-mod and got the same error?

---

### Post by kiddo on 2007-06-02
are you sure that if you change your icon theme to, say, Tango, and logout+login you won't get the same problem?

What I see in your session log is a beryl error somewhere. Are you sure that's not the problem? I'm pretty darn sure my icon theme is innocent in that regard. I have a friend using it 100% of time and he never had a problem. Other users don't seem to have any problem either.

edit: by the way, it is not very good etiquette to post multiple times on your own thread repeatedly, especially at close intervals

---

### Post by Death_Sargent on 2007-06-02
im sure its not beryl as the problem occurs in normal xorg sessions though i have yet to test tango but will now for sake of arguement

---

### Post by Death_Sargent on 2007-06-02
with no surprise from me tango log in works properly

---

### Post by Death_Sargent on 2007-06-02
perhaps i need to install something

---

### Post by kiddo on 2007-06-02
then, I don't really know, sorry. Tried with a different test user account?

and stop piling up posts, use the **edit button**!

---

### Post by Death_Sargent on 2007-06-02
ok im gona use your icons and manually rebuild the theme. my thinking is you might wan't to look into your files on the server because im willing to bet something has become corrupted

---

### Post by kiddo on 2007-06-02
Well, this is the reason why the website has MD5Sum hashes to allow you to compare your downloaded file to them and make sure it's not corrupted:

MD5sum: fa4eda9c112acc51de2ee34e6174f2c3

---

### Post by Death_Sargent on 2007-06-02
still causes crashing after a new download so i had the idea to try and find the oldest theme i could which was 3.0 as that was the last one to supposedly be tested on older version of gnome than 2.14 so I am assuming it was tested on the version of gnome that feisty comes with.

I will edit this post after i test it

--edit--

ok now i know i must be missing a dependency or something because even that did not work.

---

### Post by Death_Sargent on 2007-06-03
i ave now tried two other themes that are also mac osx clones and they both causethe same problem ARG

---

### Post by Death_Sargent on 2007-06-04
fixed here 

[http://ubuntuforums.org/showthread.php?p=2780856#6](http://ubuntuforums.org/showthread.php?p=2780856#6)

---

