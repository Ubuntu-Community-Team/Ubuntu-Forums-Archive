---
title: "XFCE themes look ugly after restart"
date: 2017-03-14
forum: Desktop Environments
---

### Post by wiler2 on 2017-03-14
Hello,

when I delete the folder ~/.config/xfce4/, and login again, the theme is ok, as you can see on this screenshoot:

[ATTACH=CONFIG]274137[/ATTACH]


But when I do another login, the window panes, panel, buttons etc. look ugly, and I am unable to change the theme by going to Settings Manager -> Appearance -> Style (I mean the style is on Greybird, as it should be, but it doesn't change when I click on different styles). I've also tryed to use the unity-tweak-tool, but it didn't work.

Screenshot of the ugly appearance:


[ATTACH=CONFIG]274138[/ATTACH]


[ATTACH=CONFIG]274139[/ATTACH]


If I open xfsettingsd on terminal, it doesn't work as a workaround, but this message is shown: " WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-cHagy63RaP: Conexão recusada".
I've noticed that the theme changes to the correct, but almost instantly the ugly theme takes place.

I've already reinstalled xubuntu-desktop and xfce4 packages. Tryed xfce-theme-manager also.

When I remove the dir ~/.cache and restart lightd, it doen't work neither.


Anyone coud help me?

Thanks in advance

---

### Post by wiler2 on 2017-03-15
If change the window manager theme in Settings/Window Manager/style, it only changes the icons of the windows. The appearance of xubuntu remais the same as the screenshots.

---

### Post by wiler2 on 2017-03-15
I've uploaded the trace of the crash of xsettings: [https://www.dropbox.com/s/zx6wk9rig4jmhkj/_usr_bin_xfsettingsd.1000.crash?dl=0](https://www.dropbox.com/s/zx6wk9rig4jmhkj/_usr_bin_xfsettingsd.1000.crash?dl=0).

---

### Post by flocculant on 2017-03-15
Settings/Window Manager/style changes only the windows. Greybird is default

Appearance - Style Greybird
Appearance - Icons elementary Xfce darker

Make sure that when you login, you are logging in to Xubuntu Session, not Xfce Session

---

### Post by wiler2 on 2017-03-16
> **flocculant said:**
> Settings/Window Manager/style changes only the windows. Greybird is default

Appearance - Style Greybird
Appearance - Icons elementary Xfce darker

Make sure that when you login, you are logging in to Xubuntu Session, not Xfce Session

flocculant,

I'm loggin in Xubuntu Session and changing the appearance doesn't change the theme. 

[IMG]http://i.imgur.com/3jxzcdP.png[/IMG]

[IMG]http://i.imgur.com/DAD2N4i.png[/IMG]

---

### Post by wiler2 on 2017-03-16
Hello,

Xorg sometimes crashes too right after login: [crash of Xorg]("https://www.dropbox.com/s/f5jr5jr2ma51mj1/_usr_lib_xorg_Xorg.0.crash?dl=0").

xfsettingsd on debug mode:

```
trt@l45225:~$ export XFSETTINGSD_DEBUG=1
trt@l45225:~$ xfsettingsd --replace --no-daemon
xfce4-settings(xsettings): _XSETTINGS_S0 registered on screen 0
xfce4-settings(xsettings): 29 settings changed (serial=0, len=1164)
xfce4-settings(xsettings): resource manager (xft) changed (len=193)
xfce4-settings(displays): Detected CRTC 63.
xfce4-settings(displays): Detected CRTC 151.
xfce4-settings(displays): Detected CRTC 152.
xfce4-settings(displays): Detected CRTC 64.
xfce4-settings(displays): Detected CRTC 65.
floating point exception core dump
```


Also, when I log as a guest user, the theme is OK, as is when I delete ~/.config/xfce4/, and login again.


I forgot to told that I have 3 monitors connected in 2 graphical cards: 
```
00:02.0 Display controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 8400 GS Rev. 3] (rev a2)
```

In software updates => additional drivers, I'm using X.Org X server -- Nouvau display driver. 
[[IMG]http://imgur.com/plCz8NVl.png[/IMG]]("http://i.imgur.com/plCz8NV.png")

My default graphical card selected in BIOS is the onboard (Intel)

---

### Post by flocculant on 2017-03-17
Log out.

Go to vt1 - ctrl+alt+f1 

Login 

Remove ~/.config/xfce4/

Logout

Should be back at the normal login screen again.

check Xubuntu session on the top panel is set

Login

---

### Post by wiler2 on 2017-03-20
> **flocculant said:**
> Log out.

Go to vt1 - ctrl+alt+f1 

Login 

Remove ~/.config/xfce4/

Logout

Should be back at the normal login screen again.

check Xubuntu session on the top panel is set

Login

When I did this the theme became ok, but the two monitors connected to my onboard GPU become disabled (I have two monitors connected to the onboard GPU and 1 to geforce). If I leave them like this, the theme doesn't change if I logout and login again, but if I configure them, in the next login the Xorg crashes right before the login and the theme becomes ugly like I described: [log of Xorg]("https://www.dropbox.com/s/3t751tpwqwq8cpa/_usr_lib_xorg_Xorg.0.crash?dl=0").

---

