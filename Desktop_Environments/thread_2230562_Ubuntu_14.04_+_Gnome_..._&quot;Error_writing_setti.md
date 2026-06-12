---
title: "Ubuntu 14.04 + Gnome ... &quot;Error writing setting&quot; when apply dark theme"
date: 2014-06-19
forum: Desktop Environments
---

### Post by vuarnet on 2014-06-19
Good evening / morning / afternoon,

I installed ubuntu server 64 bit to my laptop to get an encrypted lvm the way I wanted it. And I subsequently installed gnome-core and a few other applications as I build my way up to the necessary programs. I prefer things to be as minimal as possible without being obsessive.

My problem is this -- I downloaded the gnome tweak tool, and I really prefer the dark theme, so I clicked "Global dark theme" under the "Appearance" tab and I get the error message popping up "Error writing setting". I get this same message if I try to change any of the settings on the "Appearance" tab. I feel like I'm just missing some backend package, but I have searched and can't find it, so it's no longer obvious to me.

Any help would be greatly appreciated. I checked dmesg and there are no errors. When launching gnome-tweak-tool in terminal, I get:

```

$ gnome-tweak-toolINFO    : GSettings missing key org.gnome.nautilus.desktop (key computer-icon-visible)
INFO    : e.g.o no updates for alternate-tab@gnome-shell-extensions.gcampax.github.com (shell version 3.10.4 extension version 21.0)
INFO    : e.g.o no updates for impatience@gfxmonk.net (shell version 3.10.4 extension version 9.0)
INFO    : e.g.o no updates for launch-new-instance@gnome-shell-extensions.gcampax.github.com (shell version 3.10.4 extension version 8.0)
INFO    : e.g.o no updates for caffeine@patapon.info (shell version 3.10.4 extension version 19.0)

```

Has anyone else come across this? The dark theme is really my favorite since it's so basic and I don't need to install any PPAs or other external nonsense to get it to work. I would really appreciate any feedback you guys might have.

Thanks!

---

### Post by vuarnet on 2014-06-19
Ah. I've figured it out. Finally.

I realized I was missing a settings.ini in a gtk 3 folder. On a hunch, I ran (from ~/.config):
mkdir gtk-3.0
cd gtk-3.0/
touch settings.ini

And tried to apply the settings again, they worked! Figured I'd post my solution here in case anyone had a similar issue.

---

### Post by Carl_Witthoft on 2014-11-26
thanks for posting this.   I was having zero success with the "unity-tweak-tool" or the default settings/appearance tool;  gnome-tweak-tool allowed me to switch to all valid installed themes.

---

