---
title: "gnome 3 changing applets impossible, also with &lt;Alt&gt;"
date: 2011-10-29
forum: Desktop Environments
---

### Post by 21m0n on 2011-10-29
Hi,
I have Ubuntu 11.10 with gnome 3 and can't change, move or remove any applets. I know, that the Alt-key must me pressed, while clicking with the right mouse button on it, but this doesn't help.
I've also tried to change the keyboard modifier key for metacity in gconf-editor. That also didn't change anything.
Any ideas?

---

### Post by twtduck.ii on 2011-10-29
Try this:
1. If you don't already have dconf-tools, install it with ```
sudo apt-get install dconf-tools
``` or from the Soft ware Center by searching dconf-editor
2. Open your dash and search dconf and open it.
3. Go to desktop -> unity -> panel and edit the systray-whitelist to your liking.
Hope it helps!
Twtduck.II

---

### Post by 21m0n on 2011-10-29
I've set the systray whitelist to "all", using

```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
```but it didn't help. I've logged out and in again. The value "all" also appears right in dconf-editor now.

---

### Post by ubu_dynamite on 2011-10-29
With Gnome3 you mean "Unity, Gnome-shell or Gnome-fallback"?

With Gnome-fallback you can use alt+right click

---

### Post by 21m0n on 2011-10-29
ok, I wasn't specific: of course gnome-shell. I thought Alt+rightmouse also works for gnome-shell, top panel. So does that mean, you can't add, move or change anything in the gnome-shell top panel? :(

edit: in fallback mode it works, but I didn't want to use that, because I couldn't get compiz as the default window manager there.

---

### Post by ubu_dynamite on 2011-10-29
You can't add, move or change anything in the gnome-shell easily no.

There are some ppa's with extensions

[http://www.ubuntugeek.com/install-gnome-shell-extensions-on-ubuntu-11-10-using-ppa.html](http://www.ubuntugeek.com/install-gnome-shell-extensions-on-ubuntu-11-10-using-ppa.html)
[http://www.webupd8.org/2011/04/gnome-shell-extensions-additional.html](http://www.webupd8.org/2011/04/gnome-shell-extensions-additional.html)
[https://live.gnome.org/GnomeShell/Extensions](https://live.gnome.org/GnomeShell/Extensions)

Haven,t tried them myself yet.

---

