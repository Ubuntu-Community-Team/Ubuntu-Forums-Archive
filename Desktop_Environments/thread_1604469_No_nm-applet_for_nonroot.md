---
title: "No nm-applet for nonroot?"
date: 2010-10-24
forum: Desktop Environments
---

### Post by doriansmith on 2010-10-24
Hello,

I have the following problem that network manager applet only shows up and I can connect to Internet, if run as root.

How'd I get there:

- installed 10.04 LTS initially in server mode (no desktop environment) with wired ethernet attached, everything seemed to work fine as far as i remember;
- then added gnome desktop (actually by just apt-getting some gnome-requiring program) and everything seemed to work fine still;
- set up auto-login, too, still fine;
- then i moved the box to where it only had wireless ethernet.

Now what happens is, that network manager nm-applet does not show up in notification area at all, although it runs (and even briefly shows a sort of semi-transparent pop-up).
When I kill it from console and run it via sudo, THEN it works
But it always asks me for wireless password, doesn't allow to save it, and always drops the wifi and re-asks for wireless password after some period of inactvity 

As I browsed the forums I understood that there might be some issues with Gnome keyring manager, but I have no idea where do I go from here to make it work, so that  WiFi is connected automatically for nonroot, allows to save password and doesn't drop connection.

As far as I understand, the Gnome keyring manager should've asked me for some default keyring or some such thing upon first run of nm-applet or upon entering passwords somewhere. I can't recall exactly, but I suspect that never happened.

When I run "Passwords and encryption keys" I only have 1 key under "Passwords" tab -- "Passwords: login" and that's it.

Any ideas?

---

### Post by eslo on 2010-11-08
This is what I did:
sudo nano -w /etc/NetworkManager/nm-system-settings.conf

Change the string
"managed=false" to "managed=true"

Restart network manager.
sudo service network-manager restart

---

