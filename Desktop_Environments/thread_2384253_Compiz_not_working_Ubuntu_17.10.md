---
title: "Compiz not working Ubuntu 17.10"
date: 2018-02-04
forum: Desktop Environments
---

### Post by Donnut on 2018-02-04
In Ubuntu 17.04, I installed compiz and it just worked. I just installed a fresh copy of 17.10, and it's not working. What am I doing wrong? I used the following commands:
```
sudo apt-get install compiz
sudo apt-get install compizconfig-settings-manager compiz-plugins

```

---

### Post by deadflowr on 2018-02-04
17.10 doesn't use compiz as it does not use the unity desktop or any of the other desktops that can reliably use compiz (gnome-flashback, xfce4 or mate to name a few that can reliably use compiz).
You can try running compiz with the new desktop: gnome-shell.
But it can get rather broken looking, or seems broken from the last time I tried to replace gnome-shell's compositing window manager with compiz.

What you could do and what should work, is install the unity desktop
```
sudo apt install unity-session
```
then logout , then toggle the session, and log back into the unity session.

---

### Post by Donnut on 2018-02-04
Ah, OK, I like using Gnome-shell though, so maybe I'll just forget about making my windows wobbly again... :-(

---

### Post by deadflowr on 2018-02-04
Maybe this:
[https://extensions.gnome.org/extension/669/wobbly-windows/]("https://extensions.gnome.org/extension/669/wobbly-windows/")
might work or might not work

---

