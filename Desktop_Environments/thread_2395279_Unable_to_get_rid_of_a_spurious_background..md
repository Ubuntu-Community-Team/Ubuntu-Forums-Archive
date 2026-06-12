---
title: "Unable to get rid of a spurious background."
date: 2018-06-29
forum: Desktop Environments
---

### Post by makem2 on 2018-06-29
I am using Xfce desktop on 16.04.

SSD - xubuntu and home partitions

HD - windows and data NTFS partition.

I copied some pictures from the data partition to my desktop, emailed them and then deleted them from the desktop.

When I next started up the system i now have a much enlarged copy of one of the pictures as my sign-on background.

I always have my desktop background set to solid colour with a style of 'None'. When I check the settings via Desktop Settings/Backgound I now find that the 'Folder' is set to the path from where I copied the pictures, the 'Colour is still set to 'Solid colour' and the Style is still 'None'. However, now I see the pictures folder contents as background choices and the 'spurious' picture is highlighted but the desktop is the solid colour I always have.

It is just the background which appears when signing on that is now incorrect. It used to be the default background.

The greeter settings are:

```

# LightDM GTK+ Configuration
# Available configuration options listed below.
#
# Appearance:
#  theme-name = GTK+ theme to use
#  icon-theme-name = Icon theme to use
#  background = Background file to use, either an image path or a color (e.g. #772953)
#  user-background = false|true ("true" by default)  Display user background (if available)
#  transition-duration = Length of time (in milliseconds) to transition between background images ("500" by default)
#  transition-type = ease-in-out|linear|none  ("ease-in-out" by default)
#
# Fonts:
#  font-name = Font to use
#  xft-antialias = false|true  Whether to antialias Xft fonts
#  xft-dpi = Resolution for Xft in dots per inch (e.g. 96)
#  xft-hintstyle = none|slight|medium|hintfull  What degree of hinting to use
#  xft-rgba = none|rgb|bgr|vrgb|vbgr  Type of subpixel antialiasing
#
# Login window:
#  active-monitor = Monitor to display greeter window (name or number). Use #cursor value to display greeter at monitor with cursor. Can be a semicolon separated list
#  position = x y ("50% 50%" by default)  Login window position
#  default-user-image = Image used as default user icon, path or #icon-name
#  hide-user-image = false|true ("false" by default)
#
# Panel:
#  panel-position = top|bottom ("top" by default)
#  clock-format = strftime-format string, e.g. %H:%M
#  indicators = semi-colon ";" separated list of allowed indicator modules. Built-in indicators include "~a11y", "~language", "~session", "~power", "~clock", "~host", "~spacer". Unity indicators can be represented by short name (e.g. "sound", "power"), service file name, or absolute path
#
# Accessibility:
#  a11y-states = states of accessibility features: "name" - save state on exit, "-name" - disabled at start (default value for unlisted), "+name" - enabled at start. Allowed names: contrast, font, keyboard, reader.
#  keyboard = command to launch on-screen keyboard (e.g. "onboard")
#  keyboard-position = x y[;width height] ("50%,center -0;50% 25%" by default)  Works only for "onboard"
#  reader = command to launch screen reader (e.g. "orca")
#
# Security:
#  allow-debugging = false|true ("false" by default)
#  screensaver-timeout = Timeout (in seconds) until the screen blanks when the greeter is called as lockscreen
#
# Template for per-monitor configuration:
#  [monitor: name]
#  background = overrides default value
#  user-background = overrides default value
#  laptop = false|true ("false" by default) Marks monitor as laptop display
#  transition-duration = overrides default value
#
[greeter]
#background=
#user-background=
#theme-name=
#icon-theme-name=
#font-name=
#xft-antialias=
#xft-dpi=
#xft-hintstyle=
#xft-rgba=
#indicators=
#clock-format=
#keyboard=
#reader=
#position=
#screensaver-timeout=

```

Changing the background and user-background to "" had no effect.

I would appreciate guidance on how to return things to default.

---

### Post by #&amp;thj^% on 2018-06-29
I have never had to use this but>>>**"xubuntu-default-settings" **installs all the default settings, artwork, fonts, themes, greeter configuration, and so on for xfce.

---

### Post by makem2 on 2018-06-29
> **1fallen said:**
> I have never had to use this but>>>**"xubuntu-default-settings" **installs all the default settings, artwork, fonts, themes, greeter configuration, and so on for xfce.

```

makem@ssdTOSH:~$ xubuntu-default-settings
xubuntu-default-settings: command not found
makem@ssdTOSH:~$

```

I would appreciate your opinion on this:

[https://ubuntuforums.org/showthread.php?t=1871890](https://ubuntuforums.org/showthread.php?t=1871890)

Post #4

So many times I have made changes and upon rebooting I have been locked out for various reasons and spend much time sorting things. I prefer now to ask before taking google's advice.

---

### Post by #&amp;thj^% on 2018-06-29
Is it installed?
```
apt policy xubuntu-default-settings
```

---

### Post by makem2 on 2018-06-29
> **1fallen said:**
> Is it installed?
```
apt policy xubuntu-default-settings
```

```

makem@ssdTOSH:~$ apt policy xubuntu-default-settings
xubuntu-default-settings:
  Installed: 16.04.6
  Candidate: 16.04.6
  Version table:
 *** 16.04.6 500
        500 http://gb.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        500 http://gb.archive.ubuntu.com/ubuntu xenial/universe i386 Packages
        100 /var/lib/dpkg/status
makem@ssdTOSH:~$

```

---

### Post by #&amp;thj^% on 2018-06-29
Welp I guess that's why I have never used it then. :D
I can see no way here with that to help, but I usually just use the terminal for this anyway via:
```
sudoedit  /etc/lightdm/lightdm-gtk-greeter.conf
```
And this just an example to go by as far as the selected image to use:
Change this to:
```
[greeter]
background = /usr/share/backgrounds/greybird.svg
user-background = false
```
Save the file and now dose it change?

---

### Post by makem2 on 2018-06-29
grrrr just had another system lockup, can't wait to upgrade.

Well, I didn't care what background at this stage so used the settings you gave.

It did change, but it was just a black screen (false?) so I guess the login is set to user. No, matter, black is fine with me.

I did consider making such changes myself but as I said, I am now wary!

Many thanks for you help. Marking as solved.

---

### Post by #&amp;thj^% on 2018-06-29
I just wanted to add to you can see what is available to use in the terminal with:
```
cd  /usr/share/backgrounds/ && ls
greybird.svg  xfce

```
Also the xfce is another folder to browse with:
```
cd  /usr/share/backgrounds/xfce && ls
xfce-blue.jpg  xfce-teal.jpg

```
And you are not limited to just a .svg format you can use "most" formats just as long as they are placed in "/usr/share/backgrounds/" for one location.

---

### Post by makem2 on 2018-06-29
> **1fallen said:**
> I just wanted to add to you can see what is available to use in the terminal with:
```
cd  /usr/share/backgrounds/ && ls
greybird.svg  xfce

```
Also the xfce is another folder to browse with:
```
cd  /usr/share/backgrounds/xfce && ls
xfce-blue.jpg  xfce-teal.jpg

```
And you are not limited to just a .svg format you can use "most" formats just as long as they are placed in "/usr/share/backgrounds/" for one location.

```

makem@ssdTOSH:~$ cd  /usr/share/backgrounds/ && ls
xfce
makem@ssdTOSH:/usr/share/backgrounds$ 
makem@ssdTOSH:~$ cd  /usr/share/backgrounds/xfce && ls
xfce-blue.jpg  xfce-teal.jpg
makem@ssdTOSH:/usr/share/backgrounds/xfce$

```

Notice, no mention of greybird.svg? Maybe that explains the black screen. Later I will try one of the others to confirm.

EDIT: Yes, the black background was because greybird.svg was missing. I am using xfce-teal.jpg

---

