---
title: "Icons changing on their own after installing Compiz"
date: 2011-01-03
forum: Desktop Environments
---

### Post by sosukeinu on 2011-01-03
Hello,
I'm using an Acer Aspire One with ubuntu 10.10 Desktop/Netbook and Kubuntu 10.10 installed. I'm using Compiz for the window manager and Emerald for the decorator. I know my problem has something to do with compiz because after uninstalling it, the problem went away, so I'm hoping I'm just missing a setting somewhere.
After installing compiz, my icons/system theme (not my window decorations) will change on their own,(Please see attached screenshots) and even when I choose, let's say, 'ambiance' in the appearance menu, the panels for gnome will change, but the icons will not. the only way i can get the ubuntu mono-dark icons to reappear is to logout/restart, etc. However, it will still switch to unity icons on a seemingly random basis. It is a little thing, but it is driving me crazy. Any help would really be appreciated. Thank you.

---

### Post by ChrisEiffel on 2011-01-03
I have a similar issue. When my computer starts up it will sometime launch the same grey default theme. If I open System -> Preferences -> Appearance then the theme corrects to the desired theme except the icons and the nautilus GUI still looks weird.

---

### Post by sosukeinu on 2011-01-03
Just found this [http://www.uluga.ubuntuforums.org/showthread.php?t=1575703](http://www.uluga.ubuntuforums.org/showthread.php?t=1575703) seems to be a widespread problem :(

---

### Post by Bernabé on 2011-03-09
to fix the appearance of nautilus you just have to kill it and open it again:
nautilus -q

---

### Post by Copper Bezel on 2011-03-09
For most folks, adding gnome-settings-daemon to Startup Applications seems to be working. If that doesn't fix anything, it might need to be delayed and Nautilus restarted afterward, as

```
sleep 10 && gnome-settings-daemon && killall nautilus
```

---

