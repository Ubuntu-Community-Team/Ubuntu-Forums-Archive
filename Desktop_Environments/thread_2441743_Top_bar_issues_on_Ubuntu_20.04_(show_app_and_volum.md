---
title: "Top bar issues on Ubuntu 20.04 (show app and volume)"
date: 2020-04-26
forum: Desktop Environments
---

### Post by MaximB on 2020-04-26
Hi,
Everything used to work fine on Ubuntu 18.04.
Then I made a clean OS install, preserving my home directory.
Now I have 2 major (for me) issues.

1. When I open several applications, they only shown at the top bar as icons without description.
Like if I open several VLC videos, I only see several icons, but not their "clickable app with description", and firefox for some reason I only see at the left side panel, but not on top.
There was supposed to be a gnome3 extension for this...
It used to work on Ubuntu 18.04

2. when I hover over the volume icon and spin the mouse wheel I see that the sound icon goes up. however I no longer see the indication bar/slider (to see how much it goes up/down).
However when I click the volume icon and spin the mouse wheel, I do see it, along with the whole panel.
Can I make it work so I will see the volume bar/slider even when I only hoover over the volume and spin the mouse wheel?
it used to work on Ubuntu 18.04.

---

### Post by linux4me on 2020-04-27
I'm using a clean install of 20.04, and both #1 and #2 work as you desire on my machine, not as you are reporting. I wonder if that when you transferred your old home directory, you included something from .config or .local that's interfering with how things are supposed to work?

---

### Post by mörgæs on 2020-04-27
Yes, that's a likely explanation. If /home is kept then the installation is not so clean after all.

---

### Post by Claus7 on 2020-04-27
Hello,

I think that this might be in the right direction:
[https://linuxconfig.org/reset-gnome-desktop-settings-to-factory-default-ubuntu-20-04-focal-fossa](https://linuxconfig.org/reset-gnome-desktop-settings-to-factory-default-ubuntu-20-04-focal-fossa)

yet, just backup first your original settings:
[https://www.ostechnix.com/backup-and-restore-linux-desktop-system-settings-with-dconf/](https://www.ostechnix.com/backup-and-restore-linux-desktop-system-settings-with-dconf/)

Regards!

---

