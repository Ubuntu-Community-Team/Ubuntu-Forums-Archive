---
title: "3DDesktop Problem"
date: 2005-04-14
forum: Desktop Environments
---

### Post by laissezfaire on 2005-04-14
Hi everyone:
After setting up the ATI dirivers for my laptop computer I installed 3dDesktop (along with the required libimlib2 package) I had to install these files manually since I donot have internet access through linux.

Anyway, what happens now is first of all when I launch 3ddesktop all I get are gray rectangles except for the rectangle for the current desktop.

What is worse, after running 3ddesktop, my computer starts hanging for small durations (programs and games start freezing for about one second every 5 seconds) and everything goes to normal if I restart the computer (provided that I donot run 3ddesktop again).

I donot know if this is a bug or a compatibility problem or if I installed things incorrectly. Any help is appreciated.

---

### Post by accuser on 2005-04-15
You shoud read the friendly manual...

However:

1) When 3ddesktop needs to capture an image for each desktop before it can display that desktop in the changer. If you read the on-line manual:
```

$ man 3ddesktop

```
it will explain about this.

2) 3ddesktop will refresh the desktop images it has to keep them fresh. This is done periodically - every 5 seconds or so.

Neither of these are bugs, as such.

Personally, 3ddesktop is fun, but only for a while. I uninstalled it after wowing my firends and family. ;-)

---

### Post by paul cooke on 2005-04-15
[QUOTE=accuser]You shoud read the friendly manual...

However:

1) When 3ddesktop needs to capture an image for each desktop before it can display that desktop in the changer. If you read the on-line manual:
```

$ man 3ddesktop

```
it will explain about this.

2) 3ddesktop will refresh the desktop images it has to keep them fresh. This is done periodically - every 5 seconds or so.

Neither of these are bugs, as such.

Personally, 3ddesktop is fun, but only for a while. I uninstalled it after wowing my firends and family. ;-)[/QUOTE]

I do believe there is a howto for this item which explains how to set it up so that it gets called via a hotkey, and also doesn't refresh all the time, but only when you call it up.

[http://www.ubuntulinux.org/wiki/3ddesktopHowto](http://www.ubuntulinux.org/wiki/3ddesktopHowto)

---

