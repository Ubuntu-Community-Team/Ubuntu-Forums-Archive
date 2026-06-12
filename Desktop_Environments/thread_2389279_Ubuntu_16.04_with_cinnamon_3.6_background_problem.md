---
title: "Ubuntu 16.04 with cinnamon 3.6 background problem"
date: 2018-04-14
forum: Desktop Environments
---

### Post by ripedar2 on 2018-04-14
I have installed Ubuntu 16.04 and then cinnamon 3.6.7. But it seems like double layered with Default desktop/window manager. I don't understand why. I had problem when I locked screen with keyboard shortcut i had to type password twice. Once in Cinnamon and then in Default (not cool security feature for me). I removed shotcut from Default to lock screen and it fixed it. 
But here is problem: Everytime i change something in wallpaper/background stuff it resets to wallpaper that is set in Default profile and I can't change it until logout and login. Can someone help me with this? How to disable this weird overlaying of two window managers?

---

### Post by logix2 on 2018-04-16
You might have both Nautilus and Nemo file managers drawing your desktop. You can either make sure Nemo (the default Cinnamon file manager) is set as default or remove Nautilus altogether.

For option 1 (make Nemo default) you can use these two commands:

```
gsettings set org.gnome.desktop.background show-desktop-icons false
xdg-mime default nemo.desktop inode/directory application/x-gnome-saved-search
```

Or, if you want to remove Nautilus, use this command:
```
sudo apt remove nautilus
```

In both cases, Logout or restart after running these commands.

---

### Post by ripedar2 on 2018-04-18
that didn't helped. Its like Unity is still running under Cinnamon and doing what it want.

---

### Post by logix2 on 2018-04-19
Make sure you select the Cinnamon session from the login screen, instead of Unity.

---

