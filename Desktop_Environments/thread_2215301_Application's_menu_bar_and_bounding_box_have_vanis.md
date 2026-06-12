---
title: "Application's menu bar and bounding box have vanished"
date: 2014-04-06
forum: Desktop Environments
---

### Post by rowan2 on 2014-04-06
Today I noticed that a lot of applications are missing the box that normally surrounds the application window to allows moving and resizing the window. Also, their top menu bars are missing. Hopefully that is an easy to understand description.
The only way to maximise and move the window around is to use the "super key" shortcuts. If I maximise a window, I can see the Close, Minimise and Maximise buttons at the top, of the screen, but I don't see the "File" or "Help" or any other menu options.

So far I've seen it affecting Terminal, Skype, Calculator and the File manager windows. It doesn't affect Google Chrome as much, but that program seems to have its own, slightly different window setup. Chrome still has the thin bounding box that allows resizing and movement, but the menu at the top of the screen is still missing.

Checking the** /var/log/apt/history.log** update log, I see the previous two updates were:

```
Start-Date: 2014-04-03  19:04:54Commandline: aptdaemon role='role-commit-packages' sender=':1.84'
Install: linux-image-extra-3.11.0-19-generic:amd64 (3.11.0-19.33), linux-image-3.11.0-19-generic:amd64 (3.11.0-19.33), linux-headers-3.11.0-19-generic:amd64 (3.11.0-19.33), linux-signed-image-3.11.0-19-generic:amd64 (3.11.0-19.33), linux-headers-3.11.0-19:amd64 (3.11.0-19.33)
Upgrade: libsystemd-login0:amd64 (204-0ubuntu19.1, 204-0ubuntu19.2), linux-headers-generic:amd64 (3.11.0.18.19, 3.11.0.19.20), systemd-services:amd64 (204-0ubuntu19.1, 204-0ubuntu19.2), libsystemd-daemon0:amd64 (204-0ubuntu19.1, 204-0ubuntu19.2), libgudev-1.0-0:amd64 (204-0ubuntu19.1, 204-0ubuntu19.2), libpam-systemd:amd64 (204-0ubuntu19.1, 204-0ubuntu19.2), libnss3-1d:amd64 (3.15.4-0ubuntu0.13.10.1, 3.15.4-0ubuntu0.13.10.2), udev:amd64 (204-0ubuntu19.1, 204-0ubuntu19.2), gir1.2-gudev-1.0:amd64 (204-0ubuntu19.1, 204-0ubuntu19.2), libudev1:amd64 (204-0ubuntu19.1, 204-0ubuntu19.2), linux-signed-generic:amd64 (3.11.0.18.19, 3.11.0.19.20), libsystemd-journal0:amd64 (204-0ubuntu19.1, 204-0ubuntu19.2), libnss3:amd64 (3.15.4-0ubuntu0.13.10.1, 3.15.4-0ubuntu0.13.10.2), linux-signed-image-generic:amd64 (3.11.0.18.19, 3.11.0.19.20), linux-libc-dev:amd64 (3.11.0-18.32, 3.11.0-19.33), linux-image-generic:amd64 (3.11.0.18.19, 3.11.0.19.20), linux-generic:amd64 (3.11.0.18.19, 3.11.0.19.20)
End-Date: 2014-04-03  19:05:53


Start-Date: 2014-04-04  18:53:18
Commandline: aptdaemon role='role-commit-packages' sender=':1.83'
Upgrade: libyaml-0-2:amd64 (0.1.4-2ubuntu0.13.10.2, 0.1.4-2ubuntu0.13.10.3)
End-Date: 2014-04-04  18:53:20
```

Any idea where I should start looking? Is there an option or a shortcut key that I could have accidentally toggled that disables these features for program windows?

---

### Post by grumblebum2 on 2014-04-06
You don't say what release you are using.
Try running ...
```
/usr/bin/gtk-window-decorator --replace & disown
```

If using unity/compiz look in **compizconfig-settings-manager**(ccsm) and check the windows decoration plugin is enabled.
May have to install ccsm...
```
sudo apt-get install compizconfig-settings-manager
```

Then to run use "ccsm" in terminal or search in dash.

---

### Post by rowan2 on 2014-04-06
Sorry... I typed it in the tag box but it hasn't shown.
Ubuntu 13.10 64-bit with nVidia 319.60 (if that matters).

Here's a screenshot of the problem. Notice there's no bounding box around the Terminal and Skype and Files and Calculator windows?

[IMG]http://i.imgur.com/sOrNfvG.jpg[/IMG]

And bingo! You had it in one. Problem solved!
It was the "Window Decoration" setting in CCSM.
What could cause that to disable? Is there a shortcut somewhere?

---

### Post by grumblebum2 on 2014-04-06
> **rowan2 said:**
> Sorry... I typed it in the tag box but it hasn't shown.
Ubuntu 13.10 64-bit with nVidia 319.60 (if that matters).

Here's a screenshot of the problem. Notice there's no bounding box around the Terminal and Skype and Files and Calculator windows?



And bingo! You had it in one. Problem solved!
It was the "Window Decoration" setting in CCSM.
What could cause that to disable? Is there a shortcut somewhere?
Nah, it's just compiz ...likes to do as it pleases sometimes. ;)

---

### Post by rowan2 on 2014-04-06
> **grumblebum2 said:**
> Nah, it's just compiz ...likes to do as it pleases sometimes. ;)
I see.
Thanks a lot for the help!
I'll add the problem and solution to my "My Beefs with Ubuntu" blog. :p

---

### Post by grumblebum2 on 2014-04-06
> **rowan2 said:**
> I see.
Thanks a lot for the help!
I'll add the problem and solution to my "My Beefs with Ubuntu" blog. :p
No problem.
FYI
In 14.04 the window decorations plugin is no longer used and decorations are provided by the unity plugin and
lets you show application menus in the titlebar when hovered with mouse.
This and the fact that you can now minimize an application by clicking on it's launcher icon 
makes unity a lot more user friendly.

---

