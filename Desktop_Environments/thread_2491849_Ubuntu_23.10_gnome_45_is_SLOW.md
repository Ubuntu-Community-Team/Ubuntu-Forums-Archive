---
title: "Ubuntu 23.10 gnome 45 is SLOW"
date: 2023-10-23
forum: Desktop Environments
---

### Post by bert.ram.aerts on 2023-10-23
I run Ubuntu 23.10 Mantic on a Lenovo laptop with nVIDIA GeForce RTX-2060, but I use only nVIDIA graphics, not the built-in Intel, by selecting "Discrete Graphics" in the BIOS.
As I am not happy with Wayland, I still use X11.
I login using Gnome, so version  45, and not Ubuntu.

I have 2 issues:

1. slowness
At startup, just after logging in, I need to wait almost a minute after clicking to e.g. open a terminal or Thunderbird before it really opens.

2. external monitor issues
When I run VLC on an external monitor via HDMI, the frame rate of 29.7 fps is not reached, a movie looks very bad and delayed.

I also installed XFCE4 and can login in XFCE, there both issues do not exist.

---

### Post by TheFu on 2023-10-25
Thunderbird is a snap package by default, which is part of the reason for it being slow. There are likely other reasons, since Mozilla uses their own toolkit, not GTK+.  I run Thunderbird over an X11 network connection and startup of Thunderbird over the network takes ... give me a second ... 30 seconds.  Both systems involved are Ryzen 5600G and GigE connected.  I use X11 over ssh for the connection.  I'm not using Gnome or any DE on either system, FWIW.  That removes at least 500MB-2GB of RAM bloat right there.

None of my systems runs non-LTS releases, so it isn't 23.10.  In theory, because the GUI and GPU are split between 2 fairly powerful systems, it should be faster overall.

I don't use VLC. It is far too bloated.  mpv or a mpv front-end + mpv are very popular.  However, the exact container, video codec, and resolution matter. Not enough information provided to say anything except that VLC is bloated.  VLC has lots of features, but 95% of the time we don't use them.  mpv has all the playback features of vlc and more. Use a front-end if you need a GUI - something like **celluloid** or **smplayer**. There are others.

Mixing gnome-based DEs is dangerous.  They can have unintended interactions.  If you need multiple DEs, please, please, use different userids for each.  Linux is multi-user. Take advantage of that.  It is also a great way to see if issues are specific to 1 userid's settings or system-wide.  Create a new user and test under that account.

---

### Post by tea for one on 2023-10-25
> **TheFu said:**
> Thunderbird is a snap package by default, which is part of the reason for it being slow. 
Thunderbird (thunderbird	1:115.3.1+build1-0ubuntu1) is not listed as a snap package in the manifest for 23.10
[https://cdimage.ubuntu.com/daily-live/20231016.1/mantic-desktop-amd64.manifest](https://cdimage.ubuntu.com/daily-live/20231016.1/mantic-desktop-amd64.manifest)
Firefox is a snap (firefox	1:1snap1-0ubuntu3)

---

### Post by TheFu on 2023-10-25
```
$ snap search thunderbird
Name             Version      Publisher    Notes  Summary
thunderbird      115.3.2-2    canonical&#10003;   -      Mozilla Thunderbird email application

```
May not be default, but it could be installed by accident, easily.

---

### Post by bert.ram.aerts on 2023-10-26
(I installed Thunderbird as snap, at the moment it went from version 102 to 115 as .deb was not available.)

But now I created 2 new users on my laptop, one for Gnome Desktop Environment, one for Ubuntu DE and kept the existing user for XFCE.
Now indeed in Gnome everything is normal with VLC and after startup.

So I learned thanks to this forum that the same user for different DE's is asking for problems...

---

### Post by TheFu on 2023-10-26
> **bert.ram.aerts said:**
> So I learned thanks to this forum that the same user for different DE's is asking for problems...

There are many other things to be learned in this thread.

---

### Post by apg6xswhjc on 2023-11-11
I have had the same issue. What I have noticed is that many apps are very slow to open when you first log in; Thunderbird (.deb), Terminal (.deb), Settings. If you wait a minute or two, the apps open quickly, as you'd expect them to. 

I haven't got around to fixing this yet, but I recall having a similar problem previously, and think it required removing and then reinstalling gnome shell extensions, as they were incompatible after an upgrade. Investigations to continue.

---

### Post by apg6xswhjc on 2024-01-12
I've done some more investigating on this, and it appears to be related to xdg-desktop-portal-gnome.service failing on initial startup. Log shows:

 ```
Jan 13 11:36:47 user Dependency failed for xdg-desktop-portal-gnome.service - Portal service (GNOME implementation).
Jan 13 11:36:47 user systemd[2066]: xdg-desktop-portal-gnome.service: Job xdg-desktop-portal-gnome.service/start failed with result 'dependency'.
```

Sadly, I haven't found what the dependency causing the trouble is...

The service then starts successfully exactly 2 minutes later, and things seem to mainly be OK from there.

If you manually start the service with `systemctl start --user xdg-desktop-portal-gnome.service` once you've logged in, that seems to work too. Of course even to open a terminal seems to take some time as well (sigh).

There's some information around about removing the package, but that seems to be for situations where the users are not using gnome anymore.

My workaround is to add a new Startup Application with the above systemctl Command. This runs it at login, and accessing any gnome related apps is normal, ie you don't need to wait 2 minutes. You could alternatively add the systemctl command to the ~/.profile file.

If anyone comes across the real cause behind the problem and how it can be fixed, please add below.

---

### Post by honzap00 on 2024-02-05
> **TheFu said:**
> Thunderbird is a snap package by default, 

I apologize for entering the discussion, but I understand correctly that it's better to avoid a snap?

---

