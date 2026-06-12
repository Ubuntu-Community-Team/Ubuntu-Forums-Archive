---
title: "gnome-shell graphics are badly broken"
date: 2012-01-25
forum: Desktop Environments
---

### Post by Arancaytar on 2012-01-25
On an Ubuntu 11.10 installation that worked fine, I installed gnome-shell, restarted and started a session. I now notice that every animation is accompanied by blocks of random pixels moving across the screen, on some menus every other letter of text is missing, graphical elements are randomly displaced or missing, and other stuff.

I have no idea what's causing this, but I suspect the graphics driver or something in that area. What should I check or do to troubleshoot this?

---

### Post by UltimateCat on 2012-01-25
You can try:

System> Preferences> Catalyst Control Center (administrative)
and it will tell you the current status of the graphic driver and if it is functioning properly.

I am going through a similar graphics problem myself and I ( think ) it's a driver issue.
I won't know till I learn more. 

What I have learned so far is that working with and or fixing graphics problems are very complex.  Also, it ( might ) be a broken dependency.  Have to learn more about that as well. 

Hope this helps.

---

### Post by Arancaytar on 2012-01-25
There is no such thing as a System menu in any panel.

However, in Applications -> Other, I did find the "Catalyst Control Center". Unfortunately, beyond telling me that the graphics card appears to be working, there doesn't seem to be anything there.

At this point, I'd be happy if I could just throw it all out and get back to Unity, but that's broken as well.

---

### Post by MiThRaZoR on 2012-01-25
Do you have an ATI card?

If so you're going to have to uninstall and reinstall the drivers.

That's what worked for me.

Edit: Here's the link.
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:__Need_to_fully_remove_-fglrx_and_reinstall_-ati_from_scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:__Need_to_fully_remove_-fglrx_and_reinstall_-ati_from_scratch)

---

### Post by Arancaytar on 2012-01-26
Thanks; following the linked instructions has cleared up the graphics driver problems.

Unfortunately, it is apparently impossible to configure the Gtk and icon theme (the latter appears to be stuck on Mono, even though it is set to Humanity-Dark in gconf-editor). (see [screenshot](http://ermarian.net/images/icon-theme.png))

I'm also having some trouble setting keyboard shortcuts. At least I've figured out that the reason desktop effects aren't working is that gnome-shell doesn't include compiz, so that's working as intended.

---

