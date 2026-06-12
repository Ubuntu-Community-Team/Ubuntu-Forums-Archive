---
title: "DWM not paying attention to .xinitrc"
date: 2010-11-06
forum: Desktop Environments
---

### Post by HpZ on 2010-11-06
Nothing in my .xinitc file is having any effect on DWM.

Yes, I've linked it to .Xsessions. And it works with AwesomeWM. When I installed arch, and used the same .xinitrc file everything worked fine, so I'm assuming it's a problem with Ubuntu.

Anyone had any luck with .xinitrc?

here is mine:

```
#!/usr/bin/env bash
eval `cat ~/.fehbg` & 

while true; do
   xsetroot -name "$( date +"%F %R" )"
   sleep 1m    # Update time every minute
done &

while true
do
   if acpi -a | grep off-line > /dev/null; then
       xsetroot -name "Bat. $( acpi -b | awk '{ print $4 " " $5 }' | tr -d ',' ) | Vol. $(amixer get Master | tail -1 | awk '{ print $5}' | tr -d '[]') | $(date +"%a, %b %d %R")"
   else
       xsetroot -name "Vol. $(amixer get Master | tail -1 | awk '{ print $5}' | tr -d '[]') | $(date +"%a, %b %d %R")"
   fi
   sleep 1s &

mpd /home/fin/.mpd/mpd.conf
gnome-settings-daemon &

#Dzen & Conky
(sleep 15s && conky | dzen2 -x '500' -e '' -fg '#dcdcdc' -bg '#3f3f3f' -w '650' -ta r -fn '-*-terminus-*-r-normal-*-*-120-*-*-*-*-iso8859-*' -p ) &
wicd &
wicd-curses &
nm-applet &
gnome-power-manager &
#exec `awesome --config ~/.config/awesome/rc.lua`
exec /usr/local/bin/dwm

```

---

### Post by HpZ on 2010-11-06
So I just used the exact same .xinitrc and config.h with my Debian install and it worked...

Problem with Ubuntu, DWM or me?

---

