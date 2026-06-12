---
title: "Ubuntu 16.04 - Disable the user list in gdm greeter"
date: 2016-05-12
forum: Desktop Environments
---

### Post by i2dave on 2016-05-12
This is probably one of those common queries, but the solution I tried in 14.04 LTS now doesn't work in 16.04 !!

I have a netboot install of ubuntu, which adds ubuntu-gnome-desktop as the desktop environment.  I want to prevent the user list from showing up on the login greeter, which was achieved in 14.04 by setting "greeter-hide-users=true" in an /etc/lightdm/lightdm.conf.d config file, and also setting "disable-user-list=true" in an /etc/dconf/db/gdm.d config file.

I guess one of those settings worked, because what I want is purely a prompt for the username, with no indication of other users showing.

We're running NIS.

In 16.04, the same netboot config files have been migrated, and I can't use the same settings to disable the user list.  I've tried all sorts of options, but none seem to work :(

My desktop is "ubuntu-gnome-desktop", running gdm3 with unity-greeter - fairly bog-standard.....

Can anyone help?  Configuration settings would be useful, as I want to be able to configure the system during the network install, either via kickstart / preseed or during postinstall scripts.

Thanks in advance

---

### Post by Markus_Lankeit on 2016-05-23
Combining thoughts from [http://askubuntu.com/questions/62564/how-do-i-disable-the-guest-session](http://askubuntu.com/questions/62564/how-do-i-disable-the-guest-session) and [http://ubuntuforums.org/showthread.php?t=2192126](http://ubuntuforums.org/showthread.php?t=2192126)

This is what worked for me:

sudo sh -c 'printf "[SeatDefaults]\nallow-guest=false\ngreeter-hide-users=true\ngreeter-show-manual-login=true\n" > /usr/share/lightdm/lightdm.conf.d/50-no-guest.conf'


This disallows guest sessions and forces manual logins (no pick-list for login names).

To activate without reboot:

sudo service lightdm restart

Note: this closes out your existing GUI session... save anything valuable before running this!

---

### Post by deadflowr on 2016-05-24
^^^Lightdm is the wrong display manager.
for gdm3 look for the file */etc/gdm3/greeter.dconf-defaults*.
You should be able to simply uncomment the line:
```
# disable-user-list=true
```
then a simple restart of gdm should show you if it worked or not.

---

### Post by i2dave on 2016-07-22
After some searching, I found the answer....

Apparently, gdm3 (now the default in Gnome desktop) doesn't work in the same way as before, and displays users based on their UID!  It's all controlled via teh AccountsService, and you can't easily disable the user list, to show just a username/password prompt!

So, I'm ditching gdm3 and switching to a different login manager that DOES allow manual logins!

---

### Post by blachniom on 2017-02-17
Sorry to warm up an old thread, but someone could use the answer.
The option to hide the user list from GDM3 login screen is inside /etc/gdm3/greeter.dconf-defaults under [org/gnome/login-screen] section.
Like this:

> 
[org/gnome/login-screen]
# - Disable user list
disable-user-list=true


I mean it's specified there by default just to be uncommented.
Cheers

---

### Post by gregster on 2017-04-10
I'm working my way through this problem right now, and this does not work for me. Have you actually made this work?
Mine is a 16.04 netboot build which installs ubuntu-gnome-desktop. I've done clean builds at each point to ensure I haven't poisoned anything with previous edits.
I've worked my way through editing the file as below, fiddling with  /usr/share/gdm/* stuff, dconf-editor, etc. and find that although all seem to offer hope, none actually have any impact.
Does anyone have a real-life solution that demonstrably works?

> **blachniom said:**
> Sorry to warm up an old thread, but someone could use the answer.
The option to hide the user list from GDM3 login screen is inside /etc/gdm3/greeter.dconf-defaults under [org/gnome/login-screen] section.
Like this:



I mean it's specified there by default just to be uncommented.
Cheers

---

