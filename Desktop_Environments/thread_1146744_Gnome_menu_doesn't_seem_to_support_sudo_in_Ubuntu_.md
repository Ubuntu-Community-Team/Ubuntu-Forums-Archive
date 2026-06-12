---
title: "Gnome menu doesn't seem to support sudo in Ubuntu 9"
date: 2009-05-02
forum: Desktop Environments
---

### Post by tulchan on 2009-05-02
Can anyone help - I have installed UPS monitoring software from Belkin in Ubuntu 9

The software consists of 
    a daemon to watch the UPS (via USB) - called upsd
    a gui to configure and monitor the UPS - called monitor

I installed the software through a root terminal sessions and have added /usr/local/bulldog/upsd to the startup programs.

To launch the monitor app, I have to open a root terminal and type '/usr/local/bulldog/monitor' or using an ordinary terminal type 'sudo /usr/local/bulldog/monitor'.
Both options work fine, my problem comes when I try to add monitor to the Gnome 'Applications' menu.
If I set the entry as 'sudo /usr/local/bulldog/monitor', I get the following error in the authlog.

May  3 02:00:15 wt sudo:      bob : TTY=pts/0 ; PWD=/home/bob ; USER=root ; COMMAND=/usr/local/bulldog/monitor
May  3 02:00:17 wt CRON[4613]: pam_unix(cron:session): session closed for user root
May  3 02:04:29 wt sudo: pam_unix(sudo:auth): authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=  user=bob

Can anyone suggest a way that I can run the monitor program from the gui as root without having to open a gnome-terminal?

---

