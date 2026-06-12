---
title: "Xresources overwritten on login"
date: 2015-10-19
forum: Desktop Environments
---

### Post by qstrahl on 2015-10-19
Some of my Xresources settings are being overwritten on every login; specifically, this setting (among others):

```
Xft.rgba: rgb
```

A bunch of other "Xft" settings get set as well, and so I did a quick search in dconf-editor for "xft", which turned up what looked like the probable source of this behaviour: "com.canonical.unity-greeter.xft-rgba", which was set to "rgb". All the other offending "Xft.*" could be found there as well, so I changed them in dconf-editor, confident that this would solve the problem -- but it does not. Even after a reboot, I still see "Xft.rgba: rgb" in the output of "xrdb -q", despite the settings being changed in dconf-editor (and despite me explicitly setting this to "none" in my .Xresources file).

This setting causes my terminal font to render with really wide kerning, very unreadable. I'm at a loss for what might be causing this. Really thought I had it when I found those settings in dconf-editor... anyone have any insight on this matter?

---

### Post by deadflowr on 2015-10-19
Changes to the unity-greeter settings in dconf-editor won't happen like other changes, because those settings are pre-user settings.
(And trying to set them as root doesn't work either)
You need to set manual overrides
See something like: [http://ubuntuforums.org/showthread.php?t=2278995&p=13289229#post13289229](http://ubuntuforums.org/showthread.php?t=2278995&p=13289229#post13289229)

---

### Post by qstrahl on 2015-10-19
Thank you very much! That was really frustrating.

Alternatively, is there a way for me to keep the subpixel rendering settings without the font being weirdly wide? It would be nice to have, if only it didn't seem to make the font unreadably wide for some reason.

---

### Post by qstrahl on 2015-10-19
Oops, it looks like I was a little too optimistic -- the suggestion at that link did not solve this issue. Still unsure what to do.

---

### Post by deadflowr on 2015-10-19
Have you looked at the settings in this part
> org.gnome.settings-daemon.plugins.xsettings
I don't think these need an override,fwiw.

---

### Post by qstrahl on 2015-10-19
Yes, I have looked at them; they are not responsible for these settings, as far as I can tell. It seems very likely to me that the offender is com.canonical.unity-greeter, because it lists all the settings that I am noticing get overwritten when I check "xrdb -q"... but creating an override file and compiling the schemas as per the link you mentioned did not seem to have any effect on this behaviour.

---

### Post by buzzingrobot on 2015-10-20
The Arch wiki has some useful guidance on font rendering: [https://wiki.archlinux.org/index.php/Font_configuration](https://wiki.archlinux.org/index.php/Font_configuration)

Look especially at the sections labeled "Font Configuration" and "Presets".

There's a similar page in the Ubuntu wiki that I can't find at the moment.

Also, if your display allows you to adjust the sharpness setting, don't forget to try it. It can make a significant difference.

Most desktop environments offer a GUI tool to adjust at least some font settings. Make sure those settings match any you set manually to prevent potential overrides.  (Unity lacks that kind of tool by default, so install "unity-tweak-tool".)

---

