---
title: "Artifacts in GNOME"
date: 2007-05-02
forum: Desktop Environments
---

### Post by emax on 2007-05-02
Hi there,

I have recently upgraded from Edgy to Feisty.

Prior to the upgrade, everything was fine.

On upgrade, compiz ceased to work so I have removed all packages and purged the configuration files.  Will re-visit this one another day!

My user account wouldn't launch GNOME properly after that, I couldn't get metacity to start without manually starting it.

I removed all my .gconf* and .gnome* directories and restarted GNOME and all is well.

However, I notice strange artifacts, particularly in Firefox on screen.

This strangeness also extends into GNOME's generic dialog boxes.

Buttons appear corrupted and this often changes when the mouse is run over the boxes.

[IMG]http://www.emdevelopment.com/gnome_artefacts.png[/IMG]

KDE's buttons seem unaffected by this, however, subtle artifacts are visible in applications, particularly around icons (ie. the favicon logo on firefox tabs etc).

I have another user account for my mum (our babysitter) which is unmolested and has always used metacity.  The same artifacts are present with that account too so that rules out any user-specific configuration problems.

I haven't changed my Xorg.conf for a long time either (using an ATI 9200 on the Open source driver).

Any pointers would be much appreciated.

---

### Post by Ferrat on 2007-05-03
My best guess would be tryinging to reconfigure the xorg-server and reinstalling all grafic drivers

---

