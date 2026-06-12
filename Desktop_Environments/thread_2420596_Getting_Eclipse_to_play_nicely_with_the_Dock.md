---
title: "Getting Eclipse to play nicely with the Dock"
date: 2019-06-07
forum: Desktop Environments
---

### Post by charlieg on 2019-06-07
Most applications group. I have downloaded Eclipse from eclipse.org (as opposed to installing the Snap; historically I've always encountered issues with the prebuilt versions outside of eclipse.org) and added an appropriate .desktop file:

```
charles@charles-H310M:~$ cat .local/share/applications/eclipse-photon.desktop 
#!/usr/bin/env xdg-open
[Desktop Entry]
Comment=Java IDE
Terminal=false
StartupNotify=true
Name=Eclipse Photon
Categories=Development;IDE;
Exec=env UBUNTU_MENUPROXY=0 /home/charles/Applications/eclipse/eclipse
Type=Application
Icon=/home/charles/Applications/eclipse/icon.xpm
```

However Eclipse is not playing nicely with the dock, leading to situations like this:

[img]https://ubuntuforums.org/attachment.php?attachmentid=283397&d=1559905065[/img]

On the left is the icon as added by 'Add to favourites' and on the right are the instances.

Note: I am using Dash 2 Panel but the problem occurs in the standard dock too.

I can't seem to find any tutorials on how to solve this in Linux. I managed to [make it work fine in Windows](https://stackoverflow.com/a/44847146) but I would dearly love to solve this in Gnome too.

---

