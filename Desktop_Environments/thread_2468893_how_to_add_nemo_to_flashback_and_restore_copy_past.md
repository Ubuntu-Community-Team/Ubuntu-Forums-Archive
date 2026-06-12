---
title: "how to: add nemo to flashback and restore copy paste Desktop functionality"
date: 2021-11-13
forum: Desktop Environments
---

### Post by Claus7 on 2021-11-13
Hello,

these are the steps followed in order to restore the missing functionality of copy-paste between Desktop (not the folder under nautilus known as Files, yet the Desktop itself with its icons) and other folders in ubuntu flashback 21.10.

1) open synaptic package manager and install nemo (type nemo and install it along with all its dependencies)

2) open dconf editor and change org.gnome.gnome-flashback desktop from true to false: now desktop icons and background are no longer handled from flashback

3) type in terminal: gsettings set org.nemo.desktop show-desktop-icons true
make nemo show desktop icons

4) open startup applications and add: nemo-desktop 
command in order for nemo to handle the desktop

5) type in terminal: gsettings set org.gnome.gnome-flashback root-background true
restore the background image of your choice and change it under System Settings->Background only; right clicking on desktop and changing background is not working any more

6) reboot
if not, some changes won't take effect: e.g. background loss is not seen if reboot does not take place if step 5 is omitted

7) do not use 
gsettings set org.gnome.desktop.background show-desktop-icons false
as found elsewhere, because, if changed, it will not show Desktop folder under nautilus (Files) tree

One nice thing that was long missed is that by right clicking on Desktop and choosing Open in Terminal you will see that now the prompt is on Desktop and not in your home folder. 

The option send to bluetooth device is not enabled by default. In order to do so follow this link:
[https://forums.linuxmint.com/viewtopic.php?p=2020031&sid=80d43a8d3e1c521e3acc4b8912dfdb58#p2020031](https://forums.linuxmint.com/viewtopic.php?p=2020031&sid=80d43a8d3e1c521e3acc4b8912dfdb58#p2020031)
log out and back in for change to take effect.
edit: in case the above does not work then do the following:
i) go do /home/user_name/.local/share/nemo/actions (substitute user_name with that one of your computer)
and add the file named sendtobluetooth.nemo_action 
ii) the contents of the file should be:
[Nemo Action]
Active=true
Name=Send to Bluetooth 
Comment=Send file to bluetooth device
Exec=bluetooth-sendto %F
Icon-Name=bluetooth
Selection=Any
Extensions=any
Quote=double
iii) and make it executable

edit2: if the desktop fonts are too small then open dconf editor and go to org/nemo/desktop and change the font value

Regards!

---

### Post by Claus7 on 2022-03-20
Hello,

in order to recup the commands in order to add nemo:
```
gsettings set org.gnome.gnome-flashback desktop false
gsettings set org.nemo.desktop show-desktop-icons true
gsettings set org.gnome.gnome-flashback root-background true
```
and add nemo-desktop command in startup applications.

In order to revert back and remove nemo from handling the desktop:
remove nemo-desktop from startup and

```
gsettings set org.gnome.gnome-flashback desktop true
gsettings set org.nemo.desktop show-desktop-icons false
gsettings set org.gnome.gnome-flashback root-background false
```

In order to make nemo desktop icons labels look like flashback in such a way so as to be discernible either using a dark or light background do the following:
go to ~./config/gtk-3.0
and at the end of the file gtk.css add

> /*some shadow effects on text label*/
.nemo-desktop.nemo-canvas-item {
    text-shadow: 1px 1px 2px black;
}

/*retain the same text shadow when on hover and do not affect slight highlight, without showing any color as a background*/
.nemo-desktop.nemo-canvas-item:hover {
    background-color: alpha(@theme_selected_bg_color, 0.00);
    text-shadow: 1px 1px 2px black;
    /*background-image: none;*/
}

/*when icon selected add a blue hue background*/
.nemo-desktop.nemo-canvas-item:selected {
    background-color: alpha(0, 178, 246, 0.2);
    text-shadow: 1px 1px 2px black;
    /*background-image: none;*/
}

this works using any theme.

It was not possible to remove the expanding of the icon label upon mouse hovering or even add bold text.

> white-space: nowrap;
overflow: hidden;
text-overflow: ellipsis;
font-weight: bold; 
did not work.

Regards!

---

