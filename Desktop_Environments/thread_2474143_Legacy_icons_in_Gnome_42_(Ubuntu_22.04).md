---
title: "Legacy icons in Gnome 42 (Ubuntu 22.04)"
date: 2022-04-22
forum: Desktop Environments
---

### Post by Paddy Landau on 2022-04-22
Canonical has seemed to have a problem with legacy icons for a long time. First, Canonical deliberately prevented Unity from displaying legacy icons (a workaround was provided that merely undid the prevention); then Gnome had to use an extension to add the icons; and now, with Ubuntu 22.04, I can't find a way to add legacy icons at all.

As a specific example, this code displays a legacy icon.
```
yad --notification --image=info
```
I use the yad icon extensively, and so I need to be able to see it!

On Ubuntu 20.04, there was a good workaround: The Gnome extension [Topicons Plus]("https://extensions.gnome.org/extension/1031/topicons/"). It is supposed to be replaced by the official [AppIndicator and KStatusNotifierItem Support]("https://extensions.gnome.org/extension/615/appindicator-support/") on Ubuntu 22.04, but it doesn't work. Trying to install it the standard way results in "ERROR"; installing it manually succeeds, but the legacy icons still are not shown.

There's also [Tray Icons: Reloaded]("https://extensions.gnome.org/extension/2890/tray-icons-reloaded/"), which again doesn't work; the legacy icons aren't shown.

I have tried to find another replacement, but I've been singularly unsuccessful.

So…

What can you suggest for me, please?

---

