---
title: "Contents of /etc/gtk-3.0/settings.ini wanted"
date: 2014-02-04
forum: Desktop Environments
---

### Post by vasa1 on 2014-02-04
Will a Xubuntu user kindly post the contents of */etc/gtk-3.0/settings.ini* if you haven't modified it?

Thanks!

---

### Post by Dennis N on 2014-02-04
Here you go:
```

dn@Roxanne:/etc/gtk-3.0$ cat settings.ini
[Settings]
gtk-theme-name = Ambiance
gtk-icon-theme-name = ubuntu-mono-dark
gtk-fallback-icon-theme = gnome
gtk-sound-theme-name = ubuntu
gtk-icon-sizes = panel-menu-bar=24,24
```

---

### Post by vasa1 on 2014-02-04
> **Dennis N said:**
> Here you go:
```

dn@Roxanne:/etc/gtk-3.0$ cat settings.ini
[Settings]
gtk-theme-name = Ambiance
gtk-icon-theme-name = ubuntu-mono-dark
gtk-fallback-icon-theme = gnome
gtk-sound-theme-name = ubuntu
gtk-icon-sizes = panel-menu-bar=24,24
```
Thank you!

So now my question is this: how do gtk3 apps such as *Synaptic* or *software-properties-gtk* look assuming that Ambiance and ubuntu-mon-dark aren't installed by default in Xubuntu? Or have you taken some steps to ensure that your gtk and icon themes (whatever they are) are used?

Did you run something like:
```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
sudo ln -s /home/vasa1/.gtkrc-2.0 /root/.gtkrc-2.0 

```?

---

### Post by Dennis N on 2014-02-04
> **vasa1 said:**
> Thank you!

So now my question is this: how do gtk3 apps such as *Synaptic* or *software-properties-gtk* look assuming that Ambiance and ubuntu-mon-dark aren't installed by default in Xubuntu? Or have you taken some steps to ensure that your gtk and icon themes (whatever they are) are used?

Did you run something like:
```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
sudo ln -s /home/vasa1/.gtkrc-2.0 /root/.gtkrc-2.0 

```?


Synaptic and other "root-applications" (is that the proper term?) that require authentication look the same to me as other applications when the theme you use is in **/usr/share/themes**. If your theme in use only exists in **~/.themes** then the root applications don't use it - I believe then they use a root theme. 

So I put all new theme folders in /usr/share/themes. If copies of a theme exist in both places, the one in ~/.themes has priority for "non-root" applications. Icon themes I always put in /usr/share/icons. I haven't seen the need to do any linking like you have. How does that work out?

As to the settings in /etc/gtk-3.0/settings.ini I would guess this themes the Unity Panel. Where else are there ubuntu-mono-dark icons but on the panel? I wonder if you change these settings in Ubuntu Unity, what the effect would be? I also don't think those settings are used by Xubuntu at all. 

What is a gtk-sound-theme? Do you know?

---

### Post by vasa1 on 2014-02-04
> **Dennis N said:**
> Synaptic and other "root-applications" (is that the proper term?) that require authentication look the same to me as other applications when the theme you use is in **/usr/share/themes**. If your theme in use only exists in **~/.themes** then the root applications don't use it - I believe then they use a root theme. Yes, that is my situation: I have both my gtk theme and icon themes at home and not in */usr/share*.

> **Dennis N said:**
> So I put all new theme folders in /usr/share/themes. If copies of a theme exist in both places, the one in ~/.themes has priority for "non-root" applications. Icon themes I always put in /usr/share/icons. I haven't seen the need to do any linking like you have. How does that work out?The reason I have them at home is because I fiddle with them quite often. Re. the linking ... that was suggested here: [http://ubuntuforums.org/showthread.php?t=2044806](http://ubuntuforums.org/showthread.php?t=2044806) by mcduck.

> **Dennis N said:**
> As to the settings in /etc/gtk-3.0/settings.ini I would guess this themes the Unity Panel. Where else are there ubuntu-mono-dark icons but on the panel? I wonder if you change these settings in Ubuntu Unity, what the effect would be? I also don't think those settings are used by Xubuntu at all.Okay, I don't follow the Unity story but I just thought it odd that Xubuntu (and Lubuntu) should have something that refers to an absent theme. 

> **Dennis N said:**
> What is a gtk-sound-theme? Do you know?I think it was related to the days when Ubuntu played "event sounds".
I found these on getting sounds back on:
[https://wiki.archlinux.org/index.php/Libcanberra#Configuration](https://wiki.archlinux.org/index.php/Libcanberra#Configuration)
and
[http://forum.xfce.org/viewtopic.php?pid=26597#p26597](http://forum.xfce.org/viewtopic.php?pid=26597#p26597) (which links to two other links).

---

### Post by Dennis N on 2014-02-04
Thanks for the links. I want to look into enabling sounds again just to see how and what can be done.

---

