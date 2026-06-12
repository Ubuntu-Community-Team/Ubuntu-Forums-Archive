---
title: "Use Nautilus file manager on Desktop (Lubuntu)"
date: 2017-06-18
forum: Desktop Environments
---

### Post by Paddy Landau on 2017-06-18
I've been hunting all over and cannot find what I'm after. I have:

[LIST]
[*]A fresh installation of Lubuntu 16.04 64-bit.
[*]Installed Nautilus.
[*]Set Nautilus as the file manager in menu > Preferences > Default applications for LXSession…
[LIST]
[*]> Launching applications > File manager > Files (Nautilus)
[*]> Core applications > Desktop Manager > nautilus
[/LIST]
[/LIST]
This works apart from one problem — the Desktop.
[LIST=1]
[*]The desktop doesn't show any of my files from ~/Desktop.
[*]When I right-click the Desktop, I get a mini-menu rather than what I'd normally expect from Nautilus — see the attached screenshot.
[*]I don't know how to change the wallpaper. Instructions say to right-click and choose Desktop Preferences, but as you can see I don't have that option.
[/LIST]
How can I restore the icons to the Desktop, let Nautilus handle it, and change the wallpaper?

---

### Post by deadflowr on 2017-06-18
See what gsettings tells you:
```
 gsettings get org.gnome.desktop.background show-desktop-icons
```
then if set to false, try changing it to true with
```
 gsettings set org.gnome.desktop.background show-desktop-icons true
```

---

### Post by Paddy Landau on 2017-06-18
Thank you — it restored the icons and has given me a much more useful right-click menu!

I used the GUI dconf-editor, which allowed me to see that I could change my background there as well.

With a bit of searching, I also found how to remove icons that I didn't want in org.gnome.nautilus.desktop.

Thanks again for your help!

---

