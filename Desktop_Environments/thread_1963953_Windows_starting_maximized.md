---
title: "Windows starting maximized"
date: 2012-04-23
forum: Desktop Environments
---

### Post by unimatrix on 2012-04-23
When using Ubuntu Classic and every window opens fully maximized.
I've been googling a lot to find a solution.

Here are the following suggestions I've found across various sources:

[LIST]
[*][$ *sudo apt-get remove --purge maximus*]("http://gusantov.blogspot.com/2011/07/all-windows-opened-maximized-on-ubuntu.html")
[*][$ *gconftool -s /apps/metacity/general/auto_maximize_windows -t bool false*]("http://askubuntu.com/a/43987")
[*][use dconf-editor and switch the setting Desktop > Unity > 'Form Factor' to Desktop]("http://askubuntu.com/a/45392")
[*][use CCSM (compizconfig-settings-manager) and change the 'Place Windows > General > Placement Mode' to Smart]("http://askubuntu.com/a/45392")
[*][Disable "Window Snapping" and "Grid" plugins in CCSM]("http://askubuntu.com/a/41924")
[*][Set "Automaximize value" to 100% in Ubuntu Unity Plugin in CCSM]("http://askubuntu.com/a/70973")
[/LIST]

One of them finally worked for me. I don't know which one, but I decided to collect all of them in one place.

---

### Post by DesertF0x on 2012-05-15
Does anybody know how to to this for gnome shell?

---

### Post by markbl on 2012-05-15
> **DesertF0x said:**
> Does anybody know how to to this for gnome shell?
This auto maximise "feature" was included in 11.10 (and probably 11.04) Unity and is one of the reasons I tried gnome-shell which I have used ever since. I have never seen gnome-shell auto maximise a window. Are you asking how to turn it on? If so, then I don't  think you can unless you find/write an extension.

---

### Post by DesertF0x on 2012-05-15
I have the problem that applications start maximised even if the were not maximised before they were closed. I am using gnome shell. The problem exists since I updated to precise(12.04).

---

### Post by epabst on 2012-06-01
I use Ubuntu with GNOME Shell.  When I upgraded to Ubuntu 12.04 the title bars were gone and I couldn't resize windows.  I installed and started "Compiz Fusion Icon" and used it (in the system tray) to switch to the Metacity window manager.  That fixed it.

---

