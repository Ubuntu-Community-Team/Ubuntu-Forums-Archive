---
title: "Title Bar/Min Max Close Buttons All Missing Full Screen"
date: 2014-11-26
forum: Desktop Environments
---

### Post by garyzw on 2014-11-26
Strange now i'm getting the problem but only when windows are in full screen. 

I tried rm -rf sessions  

and

xfwm4 --replace

and rebooted but no luck

---

### Post by Toz on 2014-11-26
> **garyzw said:**
> Strange now i'm getting the problem but only when windows are in full screen. 

I tried rm -rf sessions  

and

xfwm4 --replace

and rebooted but no luck

Which version of Xfce are you using?
You wouldn't happen to have something like maximus installed or a wmctrl script that removes the titlebars on maximize, do you?
Or, are they maybe hiding under your panel?

Can you post a screenshot?

---

### Post by garyzw on 2014-11-26
Thanks Toz for the reply I have xfce 4.10
No I don't have maximus installed or a wmctrl script.
Here is a screenshot of gedit windowed and one of it maximized. The problem exist with any window I maximize

---

### Post by lisati on 2014-11-26
How are you maximising your windows? By clicking on the icon or by using F11? On my box (*not* xfce) using F11 makes the icons disappear, and pressing it agin makes them reappear.

---

### Post by garyzw on 2014-11-26
> **lisati said:**
> How are you maximising your windows? By clicking on the icon or by using F11? On my box (*not* xfce) using F11 makes the icons disappear, and pressing it agin makes them reappear.

No I did not use F11 if a press F11 then my bottom panel also disappears

---

### Post by lisati on 2014-11-26
> **garyzw said:**
> No I did not use F11 if a press F11 then my bottom panel also disappears

It was worth a shot. :( I'll step aside now to make room for someone more familiar with XFCE than myself.

---

### Post by garyzw on 2014-11-26
> **lisati said:**
> It was worth a shot. :( I'll step aside now to make room for someone more familiar with XFCE than myself.

Thanks lisati. I appreciate the help though.

---

### Post by Toz on 2014-11-26
Some more questions:

- do you have installed and are running compiz?
- does this also happen with xfce apps like mousepad, xfburn, thunar?
- not knowing about your monitor and the screenshot not showing it, is it possible that your screen is shifted so the top part is off-screen?
- are any of the appmenu packages installed?

If you're willing to share your process list:
```
ps -u $USER
```
...to have a look to see if something is running there that would be doing this.

And finally, can you try logging in with another account (or guest account) to see if the problem persists? It would be good to know if this is a profile issue or a system issue.

---

### Post by garyzw on 2014-11-26
I tried the guest session and the problem is there also.

No compiz installed


Don't have mousepad, I installed gedit but it does it in all apps


it is possible that my screen shifted so the top part is off-screen-- if do how to fix?


No appmenu packages installed



The output of the ps -u $USER is

```
  PID TTY          TIME CMD
 1287 ?        00:00:00 init
 1402 ?        00:00:01 dbus-daemon
 1410 ?        00:00:00 upstart-event-b
 1418 ?        00:00:39 gnome-keyring-d
 1433 ?        00:00:00 upstart-dbus-br
 1435 ?        00:00:00 upstart-file-br
 1441 ?        00:00:00 upstart-dbus-br
 1502 ?        00:00:00 sh
 1516 ?        00:00:00 xfce4-session
 1519 ?        00:00:00 xfconfd
 1528 ?        00:00:06 xfce4-panel
 1536 ?        00:00:00 pidgin
 1538 ?        00:00:02 radiotray
 1540 ?        00:00:00 xfce4-clipman
 1552 ?        00:00:00 gvfsd
 1555 ?        00:00:00 update-notifier
 1557 ?        00:00:00 indicator-power
 1559 ?        00:00:00 zeitgeist-datah
 1561 ?        00:00:00 polkit-gnome-au
 1563 ?        00:00:00 indicator-appli
 1567 ?        00:00:00 nm-applet
 1570 ?        00:00:00 xfce4-power-man
 1574 ?        00:00:00 xfce4-volumed
 1579 ?        00:00:00 xfsettingsd
 1581 ?        00:00:00 gvfsd-fuse
 1604 ?        00:01:25 pulseaudio
 1781 ?        00:00:00 zeitgeist-daemo
 1789 ?        00:00:00 zeitgeist-fts
 1801 ?        00:00:00 at-spi-bus-laun
 1805 ?        00:00:00 dbus-daemon
 1808 ?        00:00:00 at-spi2-registr
 1823 ?        00:00:00 cat
 1829 ?        00:00:03 panel-1-whisker
 1834 ?        00:00:02 panel-11-weathe
 1835 ?        00:00:06 panel-12-mailwa
 1836 ?        00:00:00 panel-4-systray
 1837 ?        00:00:00 panel-5-indicat
 1841 ?        00:00:00 init
 1843 ?        00:00:00 indicator-messa
 1846 ?        00:00:00 indicator-sound
 2094 ?        00:00:00 gvfs-udisks2-vo
 2104 ?        00:00:00 gconfd-2
 2112 ?        00:00:00 pidgin <defunct>
 2114 ?        00:00:00 pidgin <defunct>
 2122 ?        00:00:00 gvfs-mtp-volume
 2126 ?        00:00:00 gvfs-gphoto2-vo
 2134 ?        00:00:00 gvfs-afc-volume
 2144 ?        00:00:00 gvfsd-trash
 2281 ?        00:00:00 gvfsd-metadata
 3278 ?        00:00:00 gvfsd-network
 3284 ?        00:00:00 gvfsd-smb-brows
 3303 ?        00:00:00 gvfsd-dnssd
 3321 ?        00:00:00 gvfsd-smb
 3548 ?        00:00:00 gvfsd-http
 4178 ?        00:00:00 dconf-service
 6105 ?        00:00:06 xfdesktop
 9775 ?        00:00:00 Thunar
10692 ?        00:00:07 xfwm4
14651 ?        00:00:00 exo-helper-1
14652 ?        00:00:00 xfce4-terminal
14656 ?        00:00:00 gnome-pty-helpe
14657 pts/6    00:00:00 bash
14689 pts/6    00:00:00 ps
```

---

### Post by garyzw on 2014-11-26
This is my nvidia settings

---

### Post by Toz on 2014-11-27
> **garyzw said:**
> I tried the guest session and the problem is there also.
So its a systemic problem.

> Don't have mousepad, I installed gedit but it does it in all apps
I'd like to see if this is a GTK3 issue. Can you confirm whether the same happens with Thunar (a gtk2 app)?


> it is possible that my screen shifted so the top part is off-screen-- if do how to fix?
If yours is a desktop with a monitor, the monitor should have controls on it to adjust the screen location. If you have a laptop, then this probably won't make a difference. Its a bit of a long shot.

It really looks like something (a program?) is removing the window decorations on maximize, but I can't seem to identify which one. Is this a new, recent problem? Did it happen after a recent upgrade or program installation?

Edit: One other suggestion: does changing the Appearance and/or Window Manager theme make a difference?

---

### Post by garyzw on 2014-11-27
Yes it happens with Thunar also.
It is a desktop with a monitor and I tried adjusting the screen location settings but that didn't help either
Changing the Appearance and/or Window Manager theme makes no difference.

I have had Xubuntu 14.04 LTS installed since its release in April and it has been working fine until about a week ago when this problem started.

---

### Post by Elfy on 2014-11-27
thread hijack posts moved to new thread and prefixed

---

### Post by Toz on 2014-11-27
Can you post back some more info?

1. Your current xfwm4 settings:
```
xfconf-query -c xfwm4 -lv
```

2. A listing of your xfce4-panel settings:
```
xfconf-query -c xfce4-panel -lv
```

3. The version of xfwm4 that you are running:
```
xfwm4 -V
```

---

### Post by garyzw on 2014-11-27
Toz I reinstalled and now it all works. I thank you for your help.

---

