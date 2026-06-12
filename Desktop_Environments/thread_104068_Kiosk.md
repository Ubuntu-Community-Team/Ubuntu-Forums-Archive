---
title: "Kiosk"
date: 2005-12-15
forum: Desktop Environments
---

### Post by lukeprog on 2005-12-15
I'd like to deploy Ubuntu across my library system, first just for patron catalog access; so all I need is a web browser. I would just use a live CD but unfortunately we don't use DHCP (not my decision).

I've read the following:
[GNOME lockdown]("http://idea.zanestate.edu/archives/2005/05/kiosk-ish-ubuntu/")
[Kisok mode Ubuntu]("http://ubuntuforums.org/showthread.php?t=93397&highlight=kiosk")
[Kiosk-ish Ubuntu]("http://idea.zanestate.edu/archives/2005/05/kiosk-ish-ubuntu/")

The first requires an extraordinary number of steps and is incomplete. The second and third are different types of kiosk lockdown than what I'm looking for, mostly.

Here's how I'd like to setup an installed copy of Breezy Badger for my patron access machines:

1. Disable CTRL+ALT+Fx keys [help!, see below]
2. Auto-login to non-sudo "all" user account [figured it out, [here]("http://ubuntuguide.org/#automaticlogingnome")
3. Auto-load locked-down Firefox [figured it out, [here]("https://addons.mozilla.org/extensions/moreinfo.php?application=firefox&category=Kiosk%20Browsing&numpg=10&id=954") - except, home page won't load until you hit the Home button]
4. Disable command line [figured it out: Configuration Editor -> desktop -> gnome -> lockdown -> disable_command_line]
5. Disable panels and file browser for "all" user account [help!]
6. Disable the "Language", "Session", and "Actions" menus from the login screen. [help!]
7. Write startup script to copy default "all" user account home directory from skeleton. [help!]

This should be sufficient, right? What would be really great is a [DeepFreeze]("http://www.faronics.com/html/deepfreeze.asp")-type solution on top of this, but I don't anything like that exists for Linux. D'oh!

I read somewhere that #1 can be done by adding the following to /etc/X11/xorg.conf:

```
Section ServerFlags
    Option "DontVTSwitch" "true"
EndSection
```

But when I did that, X failed to load upon logout or reboot. I deleted those lines and rebooted and everything worked fine again. So, this is apparently not a working solution for Breezy Badger. Any other ideas?

Anyway, MUCH thanks to anyone who can help!

---

### Post by lukeprog on 2005-12-20
Anybody?

---

### Post by kosmic on 2005-12-20
Hum HAve a look at this guide -> [http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/desktop-guide/index.html]("http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/desktop-guide/index.html") is from Read Hat but is a good guide in looking down your kiosk

---

