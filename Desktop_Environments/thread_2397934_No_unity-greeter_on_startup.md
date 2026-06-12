---
title: "No unity-greeter on startup"
date: 2018-08-05
forum: Desktop Environments
---

### Post by dukedirt on 2018-08-05
So recently I've been messing around with different desktops. (I'm on ubuntu 18.04)

I tried out xfce (xubuntu) and decided to switch to unity rather.

I now have Unity working as it should except for one thing: [B]the start-up login page still uses the xfce style.
[/B]When I lock my pc, it still uses the unity style as it should.

I've tried purging all xubuntu related files, but no luck.

I'm pretty new to this sort of thing, so any help is appreciated.

---

### Post by #&amp;thj^% on 2018-08-05
First you will need to clean up and disable the old settings via:
```

sudo mv /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf.disabled
```

Reinstall unity-greeter to remove any changes in /usr/share/glib-2.0/schemas/com.canonical.unity-greeter.gschema.xml
```

sudo apt install --reinstall unity-greeter
```



NOTE:To enable it back>> **"only if needed"**.(This will restore what it was like before)
```

sudo mv /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf.disabled /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
```

Restarting the lightdm is needed
```

sudo systemctl restart lightdm
```
Check to see if there any other dconf overrides file that take priority
```

grep -rn -e "com.canonical.unity-greeter" -e "background=" -e "draw-user-backgrounds=" /usr/share/glib-2.0/schemas/
```

---

### Post by again? on 2018-08-05
You can also switch to the unity greeter by creating your own overriding conf file.
Firstly make sure unity-greeter is installed...
```
sudo apt install unity-greeter
```

Create your custom config...
```
echo -e "[Seat:*]\nuser-session=unity\ngreeter-session=unity-greeter" | sudo tee /etc/lightdm/lightdm.conf.d/99-my-settings.conf
```
Creates this config. [ATTACH=CONFIG]280657[/ATTACH]
Reboot.


If you want to revert changes simply remove the custom config...
```
sudo rm /etc/lightdm/lightdm.conf.d/99-my-settings.conf
```

---

