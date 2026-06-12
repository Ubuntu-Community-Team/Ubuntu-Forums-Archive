---
title: "GTK3 windows can no longer be moved in the background w/ RMB"
date: 2018-10-28
forum: Desktop Environments
---

### Post by marginallosses on 2018-10-28
Running Xubuntu 18.04. It seems the GNOME devs, in their infinite wisdom, have decided that being able to move windows without raising them is not compatible with their dream of building the best touch-driven interface for phones and tablets (since they clearly are no longer targeting desktop computing).

With all other graphical applications, I can drag a background window by using the right mouse button on its title bar.

With GTK3 applications, attempting to drag the window with the right mouse button instead results in the window menu popping up. It's not possible to drag it.

I'm guessing that this is due to GTK3 apps no longer having a dedicated title bar and no dedicated place to bring up the window menu via a left-click, so their decision was to make right-clicks anywhere on the title bar bring up the window menu. I use the window menu extremely rarely and when I do it's always with the alt+space keyboard shortcut.

Is there anyway to change GTK3's behavior under xfce?

If GTK3 adoption actually starts spreading beyond GNOME's in house applications this will become a big problem for me... :confused:
Besides this behavior is the fact that the appearance of the GTK3 windows aren't influenced by my theme selection and so they're all just flat gray and you can't tell which one is in the foreground. Absolute garbage UI/UX, like the greybird theme.

---

### Post by again? on 2018-10-28
Install gtk3-nocsd
> Description: Disable Gtk+ 3 client side decorations (CSD)
 gtk3-nocsd LD_PRELOADs a small library to disable the client side
 decorations (CSD) of Gtk+ 3.
 .
 Since Gtk+ 3.10, its developers added a so-called header bar or custom
 title bar. With this and the client-side decoration, the original
 title bar and window border provided by the window manager are
 disabled by Gtk+. This makes all Gtk+ 3 programs look like alike, but
 have different handling from other windows on non-GNOME desktops. Even
 worse, this may break some window manager or compositors.
 .
 Unfortunately, there is no reliable way of turning off CSDs in Gtk+
 directly. This library makes this possible.
```
sudo apt install gtk3-nocsd
```
Log out.

Effectively it adds a title bar to [**GNOME Core Applications**]("https://en.wikipedia.org/wiki/GNOME_Core_Applications").
I hide the title bar in maximised windows and close with a mouse gesture so as not lose too much vertical space.

---

### Post by marginallosses on 2018-10-29
Brilliant, worked like a charm, many thanks!

---

