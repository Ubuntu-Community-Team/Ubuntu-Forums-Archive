---
title: "parts of my openbox autostart.sh don't work"
date: 2009-01-09
forum: Desktop Environments
---

### Post by Stefanie on 2009-01-09
i've been using openbox for a few days but i can't get some parts of my autostart.sh-file to work properly.
this is the file:

```
#!/bin/bash

# Run the system-wide support stuff
. $GLOBALAUTOSTART

xset b off &
xmodmap /etc/SwapCapsEsc.kmap &

# Programs that will run after Openbox has started
(sleep 2 && gnome-panel) &
(sleep 2 && nm-applet) &
(sleep 2 && combiconky) &
(sleep 2 && gnome-do) &
(sleep 2 && checkgmail) &
(sleep 2 && genesis) &


```

everything seems to work fine except "xset b off" (to turn that stupid system bell off) and the xmodmap-line (script to swap caps lock and escape). both work fine in gnome, why doesn't it work in openbox?

---

### Post by der_joachim on 2009-01-11
Are you sure that xset and xmodmap need to be backgrounded? AFAIK they are not meant to be run as daemons. What happens if you remove the ampersands at the end of the xset and xmodmap lines?

---

### Post by lmno386 on 2009-01-11
Q: Why do cats like to hear other cats make noise? A: It's meow-sic to their ears! .............................................................................................................................................[**warhammer gold**](http://www.warhammergold119.com/) [**buy warhammer gold**](http://www.warhammergold119.com/) [**cheap warhammer gold**](http://www.warhammergold119.com/) [**warhammer gold**](http://www.warhammergold119.com/warhammer-gold-us) [**warhammer gold**](http://www.warhammergold119.com/Warhammer-Gold-eu) [http://www.warhammergold119.com](http://www.warhammergold119.com)

---

### Post by Stefanie on 2009-01-12
thanks for your reply, but that didn't help. i also tried enclosing the commands in brackets, quotes or backticks but still no result.

---

### Post by urukrama on 2009-01-12
Both those commands rely on X. Perhaps they are run before X is fully loaded, and therefore have no effect. Have you tried them with some sleep (like you do with the other commands)?

---

### Post by Stefanie on 2009-01-14
the first time i tried them i put them at the end of the file with sleep 2, like my other applications, but that didn't work either. do you think increasing the sleep-time might help?

---

### Post by urukrama on 2009-01-14
I just tried it myself, and it works fine in my Openbox session (I checked the xset settings with *xset q* and it made the changes I requested). 

My guess is that gnome-settings-daemon (or xfce-mcs-manager), which is started by the default autostart.sh script with the *. $GLOBALAUTOSTART* command, overrides those settings. A brief internet search seems to confirm this. 

You'd either have to use something else to set your Gtk themes, change the settings in Gnome (using gconf-editor, look under desktop/gnome/peripherals/keyboard for both keyboard and system bell settings), or possibly load xset after gnome-settings-daemon is fully loaded.

---

### Post by Stefanie on 2009-01-15
thanks, i didn't know about gnome-settings-daemon overriding those options. i will try to find a work around. 

(where's the thanks button gone?)

---

### Post by Stefanie on 2009-01-16
i increased the sleep time and it seemed to work after logging in again, but after restarting it doesn't work anymore :confused:

---

### Post by urukrama on 2009-01-16
If you do use gnome-settings-daemon, why don't you just adjust the settings in gconf-editor? You will then have no need to launch xset and xmodmap. If you start gconf-editor, have a look under desktop/gnome/peripherals/keyboard and you should see all the options you want.

---

### Post by Stefanie on 2009-01-19
ok thanks.

---

