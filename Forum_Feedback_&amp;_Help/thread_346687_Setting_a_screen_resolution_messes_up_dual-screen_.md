---
title: "Setting a screen resolution messes up dual-screen setup"
date: 2007-01-26
forum: Forum Feedback &amp; Help
---

### Post by christoph_steinbeck on 2007-01-26
This is a documentation posting - I did not know where else to put it.

I have set-up a dual-screen xorg.conf with an ATI firegl on an IBM T41p which suddenly stopped working. With dual screen, I mean that the gnome desktop spans my two LCD monitors (laptop-built-in and additional one standing right of it).

With "stopped working" I mean that the systems boots until the GDM login screen where the dual screen setup is still ok, but during the login process, the system reverts to a mirrored mode where both screens show the same content.

The reason was that I once used System->Preferences>Screen Resolution to switch between two resolutions for testing. That created a respective Key in the Gnome Preferences which, at login, somehow messes up the x-server configuration.

The fix was to use gconf-editor and delete two key under desktop->gnome->screen->0 related to resolution and refresh rate.

Cheers, Chris

---

