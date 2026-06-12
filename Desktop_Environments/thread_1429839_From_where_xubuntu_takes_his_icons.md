---
title: "From where xubuntu takes his icons?"
date: 2010-03-14
forum: Desktop Environments
---

### Post by vickoxy on 2010-03-14
Hi,
i use Xubuntu 9.10, and installed some icon themes. Of course, xfce does not implement all icons in that theme, but it takes some default/system icons. So, i have idea to replace those system icons with other-but have no idea from where does it takes them. Is it /usr/share/pixmaps/ or maybe /usr/share/icons/hicolor...?

So, before i mess something up-maybe someone here knows where to find those icons.

Thanks

---

### Post by denham2010 on 2010-03-15
Xfce will take icons from the installed theme first, and, should the icon needed not be in that theme, it then goes to /usr/share/icons/hicolor.

To add your own icon to the theme, you need to find out the name of the required icon (scan the /usr/share/icons/hicolor directory for the icon you wish to replace).

Now just place a copy of the icon you want the theme to use in ~/.icons/<themename> and re-name it so it is the same as the icon in /usr/share/icons/hicolor.

The theme will now use your icon instead of the default (you may need to log out and back in for the change to take effect).

Just ensure you place your icon in your theme folder under the same path as it was in /usr/share/icons/hicolor. eg. if the icon you want to replace is in /usr/share/icons/hicolor/128x128/devices, you will place your icon in ~/.icons/<themename>/128x128/devices

Cheers.

---

### Post by vickoxy on 2010-03-15
> **denham2010 said:**
> Xfce will take icons from the installed theme first, and, should the icon needed not be in that theme, it then goes to /usr/share/icons/hicolor.

To add your own icon to the theme, you need to find out the name of the required icon (scan the /usr/share/icons/hicolor directory for the icon you wish to replace).

Now just place a copy of the icon you want the theme to use in ~/.icons/<themename> and re-name it so it is the same as the icon in /usr/share/icons/hicolor.

The theme will now use your icon instead of the default (you may need to log out and back in for the change to take effect).

Just ensure you place your icon in your theme folder under the same path as it was in /usr/share/icons/hicolor. eg. if the icon you want to replace is in /usr/share/icons/hicolor/128x128/devices, you will place your icon in ~/.icons/<themename>/128x128/devices

Cheers.

Well, i tried that, but still couldn´t find the bluetooth icon-e.g. Icon that i have is not in hicolor...

---

### Post by denham2010 on 2010-03-15
> **vickoxy said:**
> Well, i tried that, but still couldn´t find the bluetooth icon-e.g. Icon that i have is not in hicolor...

Which app are you trying to change the icon for?

---

### Post by vickoxy on 2010-03-15
> **denham2010 said:**
> Which app are you trying to change the icon for?

E.g panel icons for Bluetooth and Battery status. I replaced all bluetooth icons in /hicolor/ with desired one but no change was visable after logout. Network icon belong to elementary icon theme. Although it should be blue stripes there not the white ones. So, i really don´t know why are those icons acting like this...

---

### Post by denham2010 on 2010-03-16
> **vickoxy said:**
> E.g panel icons for Bluetooth and Battery status. I replaced all bluetooth icons in /hicolor/ with desired one but no change was visable after logout. Network icon belong to elementary icon theme. Although it should be blue stripes there not the white ones. So, i really don´t know why are those icons acting like this...

Battery applet:

```
/usr/share/icons/hicolor/scalable/status/xfpm-primary....svg
```

I don't have bluetooth applet or network manager installed, so am unable to locate those directly, but they should also be in the status folder.

---

### Post by vickoxy on 2010-03-16
> **denham2010 said:**
> Battery applet:

```
/usr/share/icons/hicolor/scalable/status/xfpm-primary....svg
```

I don't have bluetooth applet or network manager installed, so am unable to locate those directly, but they should also be in the status folder.

I looked there-found battery status, but there is no bluetooth icon....

---

### Post by denham2010 on 2010-03-16
Bluetooth:

```
/usr/share/icons/hicolor/......./apps
```

You will find a bluetooth icon of each size....you will need to change all of them so no matter what size the tray is, it will select your icon.

---

### Post by vickoxy on 2010-03-16
> **vickoxy said:**
> E.g panel icons for Bluetooth and Battery status. I replaced all bluetooth icons in /hicolor/ with desired one but no change was visable after logout. Network icon belong to elementary icon theme. Although it should be blue stripes there not the white ones. So, i really don´t know why are those icons acting like this...

I said there that i done this-and that is the issue-i found all these bluetooth icons in hicolor, and few days ago i replaced them - but nothing changed. Other than that-those hicolor icons do not look the same as the bt icon that i have in my panel. So it doesn´t  take them from hicolor.

---

