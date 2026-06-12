---
title: "Customizing the colors &amp; looks of the mainstream Ubuntu"
date: 2017-11-12
forum: Desktop Environments
---

### Post by vesa33 on 2017-11-12
Hi,
 I usually use some other variant of Ubuntu because the orange theme colors seem so flagrant/disharmonious to me, but this time it is about my preconfigured work computer so it is better if I continue with the mainline Ubuntu installed on it. When you do a search about color customization in Ubuntu, you typically find hints about different tweak tools that do not work any more or change a color in one place, leaving everything else to the same old orange. It seems that there is no continuity in tweak tools because the power people of Ubuntu are unwilling to support color  customization within the mainline Ubuntu.

Anyway, I managed to adjust the theme colors by manual adjustment -- more about that below. However, I would appreciate hints on how to find and install some nice non-orange icon set. The version of Ubuntu is 16.04 LTS. Thanks in advance for help with that!

For changing theme colors I offer following recommendations / ideas:
  - Find the directory of your theme inside /usr/share/themes and take a backup of it
  - Find the colors codes inside the configuration files and replace them. Since there are quite a few places to change and more than one shade of orange to replace, some systematic approach is recommended.
  - There are application-specific subdirectories that increase the number of configuration files a lot. Perhaps they could be deleted or otherwise disabled, allowing them to use defaults, so as to keep the number of configuration values reasonably low?

I did the color replacement by swapping the green and blue component of each color code. That changed each hue of orange to a hue of violet with similar brightness and saturation (or if not exactly violet, something between violet and flamingo pink.)

---

### Post by Frogs Hair on 2017-11-13
You may want to look at some other themes and icons. There are plenty of installation instructions available with a search.

[https://www.gnome-look.org](https://www.gnome-look.org)

---

### Post by vesa33 on 2017-11-13
Thank you. That address should actually also be updated to page [https://help.ubuntu.com/community/UbuntuEyeCandy](https://help.ubuntu.com/community/UbuntuEyeCandy) . So if any of our readers have privileges to modify that page, please fix.

I'll try installing an icon set with Unity-Tweak-Tool, and probably report back in about 12 hours.

---

### Post by vesa33 on 2017-11-14
OK, I managed to install some icons from there, manual copying was required. unity-tweak-tool did its job well for icons. At first changes didn't seem to take effect but that happened because I started it with sudo, probably only modifying the settings for the root user!

At some point of the process, gnome-terminal "lost connection" to its icon so that whichever icon theme I choose it just shows a an icon with a question mark. However, unlocking it from Launcher and bringing it in again fixed the problem. All is well that ends well O:)

---

