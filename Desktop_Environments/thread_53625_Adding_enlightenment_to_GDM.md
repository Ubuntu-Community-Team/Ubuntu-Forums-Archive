---
title: "Adding enlightenment to GDM?"
date: 2005-08-01
forum: Desktop Environments
---

### Post by erik-the-red on 2005-08-01
I installed enlightenment through synaptic, but it does not appear in the GDM Sessions Menu, unlike openbox and fluxbox, which both showed up when installed through synaptic.

How do I add enlightenment to GDM?

---

### Post by vaskark on 2005-08-01
[QUOTE=erik-the-red]I installed enlightenment through synaptic, but it does not appear in the GDM Sessions Menu, unlike openbox and fluxbox, which both showed up when installed through synaptic.

How do I add enlightenment to GDM?[/QUOTE]
Go to /usr/share/xsessions and create an Enlightenment.desktop file. Here's what mine looks like (your install path may be different, tho):

[Desktop Entry]
Encoding=UTF-8
Name=E17
Comment=This session logs you into E17
Exec=/usr/local/bin/enlightenment
# no icon yet, only the top three are currently used
Icon=
Type=Application

It should appear in GDM right away, or you may have to restart gdm. Can't recall right now ;)

---

