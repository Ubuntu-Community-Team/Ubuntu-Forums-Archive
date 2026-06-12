---
title: "Problem installing kwin on xubuntu 14.04"
date: 2014-06-02
forum: Desktop Environments
---

### Post by danbuz on 2014-06-02
I triend installing kwin with this method [https://www.youtube.com/watch?v=A0xTiTUiIng](https://www.youtube.com/watch?v=A0xTiTUiIng)
but I got message that the KWM have broken packages when I check install kde-style-skulture in synaptic.

I 'm not able to run windows manager settings at all, tried everthyng but no success. The errors are similar to this topic [http://discuss.howtogeek.com/t/unable-to-install-kwin-and-kwin-window-manager/14573/8](http://discuss.howtogeek.com/t/unable-to-install-kwin-and-kwin-window-manager/14573/8) but nothing works for me..

Is it possible to run kwin in 14.04 at all? The *-gles packages described in the video are also missing in synaptic.

---

### Post by danbuz on 2014-06-04
Any Ideas? Someone tried to install kwin already?

---

### Post by luctor on 2014-07-07
I installed it and didn't need many packages
look at this video [https://www.youtube.com/watch?v=z5kiYjg3Rog](https://www.youtube.com/watch?v=z5kiYjg3Rog)
I don't even know what language the guy is speaking but the description and video explains enough for me

> ```
sudo apt-get install kwin-style-qtcurve kde-window-manager-common kde-window-manager kdeartwork-theme-window qtcurve kde-window-manager-active

```
```
cp /etc/xdg/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml

```
```
gedit ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml
```

- inlocuiti xfwm4 cu kwin apoi restart
(replace xfwm4 with kwin ??? probably)

Aplicatie Kwin:
```
[Desktop Entry]
Version=1.0
Name=Kwin
Comment=Window Manager
Exec=kcmshell4 kwincompositing kwindecoration kwinoptions kwinscreenedges kwintabbox desktop
Icon=xfwm4
Terminal=false
Type=Application
Categories=XFCE;GTK;Settings;DesktopSettings;X-XFCE-SettingsDialog;X-XFCE-PersonalSettings;
StartupNotify=true
OnlyShowIn=XFCE;
```

- Save as: Kwin.desktop

i didn't bother with the autostart :-)

Still figuring out how to get the numix style window decorations to work ...

---

