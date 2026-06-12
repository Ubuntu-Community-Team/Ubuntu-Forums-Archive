---
title: "Restore lubuntu desktop (black screen after login)"
date: 2016-02-22
forum: Desktop Environments
---

### Post by Maldus on 2016-02-22
Hello everyone,
I just installed lubuntu and I was trying out some terminal emulators. After trying gnome-terminal I decided to uninstall it, but instead I just ended up messing my desktop environment. I assumed everything that had gnome in it was to be removed and I uninstalled the following packages:
blueman* evince* gdebi* gnome-desktop3-data* gnome-disk-utility* gnome-icon-theme* gnome-icon-theme-full* gnome-icon-theme-symbolic* gnome-keyring* gnome-mplayer* gnome-system-tools* gnome-time-admin* gnome-user-guide libgnome-desktop-3-10* lubuntu-core* lubuntu-default-session lubuntu-default-settings lubuntu-desktop* lubuntu-icon-theme*
even after reinstalling them, after the login screen I get a black screen with the cursor, but nothing else. Since I reinstalled everything I'm guessing I'm just missing some settings or links to start everything correctly; I've tried some generic solution to this problem ( like removing .Xauthority ), but nothing worked. Can anyone help me?
Since it's a fairly new installation, the best think would be a "restore everything" option, like reinstalling lubuntu without having to format the partition.

---

### Post by T.J. on 2016-02-24
Hi!



I'm sorry, but since the Lubuntu (LXDE) uses gnome files, by removing them you rendered it unable to start up completely.  This can be fixed without reinstalling, hopefully. 

1. Press Ctrl+alt+F1 to get a command prompt.
2. login using your id.
3. enter 

sudo apt-get install lubuntu-desktop lightdm default-settings xorg lubuntu-core

Follow any prompts. Hopefully, that will be enough.  Then 

sudo shutdown now -r (or press ctrl+alt+delete).

If all goes well, the machine should restart in GUI mode.  Good luck, and please let me know if I can do anything more to help.  (If you get an error about a package name, I might have a package name wrong, such as xorg. Just remove that one and retry with the rest.)

Take care!

t.j.

---

### Post by Maldus on 2016-03-01
Thank you for your help;
Unfortunately installing those packages (only default-settings was not found; I guess you meant lubuntu-default-settings?). However before reading your answer I settled with booting in text mode and starting lxde gui with startx (that was my intention since the beginning), so its not really a problem anymore.

---

