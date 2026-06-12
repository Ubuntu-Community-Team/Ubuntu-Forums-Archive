---
title: "what is it about the desktop files that specifies x.org vs wayland?"
date: 2023-11-09
forum: Desktop Environments
---

### Post by britton-kerin on 2023-11-09
I noticed that /usr/share/xsessions/ununtu.desktop and /usr/share/xsessions/ubuntu-xorg.desktop vary only in Name:


```
$ 'diff' -u ubuntu.desktop ubuntu-xorg.desktop                            
--- ubuntu.desktop      2022-04-07 11:07:53.000000000 -0800
+++ ubuntu-xorg.desktop    2022-04-07 11:07:53.000000000 -0800
@@ -1,5 +1,5 @@
 [Desktop Entry]
-Name=Ubuntu
+Name=Ubuntu on Xorg
 Comment=This session logs you into Ubuntu
 Exec=env GNOME_SHELL_SESSION_MODE=ubuntu /usr/bin/gnome-session --session=ubuntu
 TryExec=/usr/bin/gnome-shell
```


the XDG_SESSION_TYPE does indeed show wayland or x.org for the different session so it's working, but it seems weird that the two session files only differ by the Name.  Is it really the case that this is being used both to the display the session name in the desktop manager and also to trigger something else somewhere that changes what is actually started?  And if so where is that something else?

---

### Post by matt-rw on 2023-11-11
somehow controlled by gdm I think. This did not help much:
```
$ systemctl status gdm3.service
```

---

