---
title: "Unable to run script from Desktop"
date: 2014-10-07
forum: Desktop Environments
---

### Post by Jorge_Calderon on 2014-10-07
I created this Desktop icon:

[Desktop Entry]
Encoding=UTF-8
Name=Robomongo
Comment=Launch Robomongo
Exec=/usr/local/robomongo-0.8.4-i386/bin/robomongo.sh
Icon=utilities-terminal
Type=Application
Terminal=true

When i double click on it, it opens a Terminal window in my home directory and no other output gets printed.  In the shell, when I type "/usr/local/robomongo-0.8.4-i386/bin/robomongo.sh", I get the Robomongo GUi come up.

---

### Post by vasa1 on 2014-10-07
Take a look at [https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)

[s]Maybe you need a **Version** line?[/s]

Also see [http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s05.html](http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s05.html)

---

