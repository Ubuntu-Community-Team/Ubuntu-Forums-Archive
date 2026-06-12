---
title: "Screensaver turning on every 10 minutes"
date: 2014-03-28
forum: Desktop Environments
---

### Post by evan8 on 2014-03-28
Having an issue with screen saver turning on after every 10 minutes even if watching video. Disabled screen saver and even turned it off. Found this solution

"
The problem is that screen blanking is not turned off by xfpm. The  output of the command 'xset q' showed me that my screensaver blanking  was activated (despite NOT having xscreensaver installed). The best  solution I found was to turn it off entirely using a configuration file  in /etc/X11/xorg.conf.d/ with this in it:
Section "ServerFlags"
	Option "BlankTime" "0"
EndSection"

But I do not have that folder/file. Any suggestions?

---

### Post by Toz on 2014-03-28
In Ubuntu, the xorg.conf.d folder is located at /usr/share/X11/xorg.conf.d.

---

### Post by evan8 on 2014-03-28
I can find the conf.d folder. but which file or do i have to create one?

---

### Post by vasa1 on 2014-03-29
I took another route which is a bit of a workaround but I use a script to monitor %CPU usage: if %CPU usage exceeds a specified value (as it would if a typical video is playing), a "mousemove" is triggered every 8 min and that prevents screen blanking:

```
#!/usr/bin/env bash

sleep_period=8m

while true; do
  high="$(ps -eo %C --sort -%cpu | awk 'NR==2')"
  if ps -eo %C --sort -%cpu | awk 'NR==2 { exit !($1>5); }'; then
      notify-send 'ALERT' "$high"
      xdotool key shift
  fi
  sleep ${sleep_period}
done

``` I had to install *xdotool* which doesn't come as default in any Ubuntu flavor, AFAICT. The notify-send is just for fun. (I think I needed to install *libnotify-bin* as well to get my home-made notifications to appear.)

---

### Post by evan8 on 2014-03-29
> **vasa1 said:**
> I took another route which is a bit of a workaround but I use a script to monitor %CPU usage: if %CPU usage exceeds a specified value (as it would if a typical video is playing), a "mousemove" is triggered every 8 min and that prevents screen blanking:

```
#!/usr/bin/env bash

sleep_period=8m

while true; do
  high="$(ps -eo %C --sort -%cpu | awk 'NR==2')"
  if ps -eo %C --sort -%cpu | awk 'NR==2 { exit !($1>5); }'; then
      notify-send 'ALERT' "$high"
      xdotool key shift
  fi
  sleep ${sleep_period}
done

``` I had to install *xdotool* which doesn't come as default in any Ubuntu flavor, AFAICT. The notify-send is just for fun. (I think I needed to install *libnotify-bin* as well to get my home-made notifications to appear.)
interesting. i'll try that out if all else fails. thanks

---

### Post by evan8 on 2014-03-29
Well. I seemed to have fixed it on xubuntu . Not sure if the command did it or the actual power settings. I was using xfce on my main machine and haven't fixed. But I'll probably just install xubuntu instead tomorrow. thanks. problem half way solved :)

---

### Post by buzzingrobot on 2014-03-30
Are you sure it isn't the screen lock that's activated at the 10-minute mark?

---

### Post by evan8 on 2014-03-31
Upgrading to 14.04 seems to be the fix. Now It has " light locker" settings and works fine on both my computers.  Solved

---

