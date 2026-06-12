---
title: "Ubuntu 20.04: Can't change arrangement of desktop icons"
date: 2020-05-03
forum: Desktop Environments
---

### Post by roots on 2020-05-03
Hi all,

I just gave Ubuntu 20.04 / Gnome-Flashback a go and it's looking pretty neat so far. However, I have an issue which currently is a deal breaker for me: With both Metacity and Compiz, there is no way to re-arrange (=move) icons on the desktop. The Right-Click menu on the desktop just gives me "auto-arrange" with both other options (grid placement and free placement) greyed out. Trying to change those settings with dconf-editor did not work either, the new settings just won't stick. It is working in Gnome-Shell though, where free icon placement is activated per default.

Anyone got an idea? Any suggestions very much appreciated!
r.

---

### Post by mc4man on 2020-05-04
The previous other methods are not implemented so they were disabled. (- even though they  are still listed in gschemas
See - [https://gitlab.gnome.org/GNOME/gnome-flashback/issues/41](https://gitlab.gnome.org/GNOME/gnome-flashback/issues/41)

You could disable it (Desktop icons) in gnome-flashback  & switch to nemo-desktop just for the Desktop.( nemo would be available as an additional file-manager & could be made the default..
```
gsettings set org.gnome.gnome-flashback desktop false
```

Edit: tested, works ok. You can place anywhere. Limited to only 'arrange by name' from r. click. 
To try install nemo.

In dconf-editor must set org.nemo.desktop use-desktop-grid  to false

Icon size set in org.nemo.icon-view default-zoom-level  (- default is "standard" which is too big for me, i use "small"

You would create a startup app  that uses nemo-desktop as command.
By default startup app are created to run immediately on log in, if any issue delay a sec. or 2

Ex. 
```
Desktop Entry]
Type=Application
Name=Nemo
Comment=Start Nemo desktop at log in
Exec=nemo-desktop
AutostartCondition=GSettings org.nemo.desktop show-desktop-icons
X-GNOME-AutoRestart=true
X-GNOME-Autostart-Delay=2
NoDisplay=false
```

---

### Post by roots on 2020-05-07
Hi, thanks for the info.

Meanwhile I tried using xfdesktop which worked well for handling the desktop via thunar. However, due to further issues with gnome-flashback I switched to MATE. Anyway, thanks again for the suggestions.

r.

---

