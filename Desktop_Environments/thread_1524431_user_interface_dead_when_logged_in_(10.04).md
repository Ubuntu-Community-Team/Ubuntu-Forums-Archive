---
title: "user interface dead when logged in (10.04)"
date: 2010-07-05
forum: Desktop Environments
---

### Post by sterob on 2010-07-05
Hi,
when I log in, I can move the mouse, but nothing else. The whole user interface is unresponsive and  absolutely no keystroke works. It is probably not because of my hardware (hp 2710p) because logging in as root (with only slightly different Gnome configuration) does work well.

I assume it is because of some error inside the Gconf. There is always an error when starting Gnome that an entry could not be read, including some bunches of ~30 question marks. If it is useful, I can give you the whole message literally.

I haven't changed data inside Gconf, but I did have it open when I was installing a program, and then the console did show the message with the question marks for the first time (while processing some "trigger" post-install). I think the program I was installing was drapes (for changing desktop wallpapers in Gnome). Strangely Gnome did startup correctly afterwards for a couple of times (always showing the above-mentioned error). I have no idea what change made it suddenly stop working yesterday.

The differences in Gnome configuration between the working root and the unresponsive user account are, as far as I can tell from memory:

changed theme (elegant-brit), wallpaper, fonts, globalmenu in the panel, installed - added to panel - uninstalled drapes. 

The rest is the same for the root account.

I can still log in to the shell as the normal user, but "startx" leads to the disabled graphical interface. As I said, the graphical interface works well when I use the root shell (that's where I am now). I can't access the internet from the user shell unfortunately (if I need to, I will figure out how to set up wlan in the shell).

Thank you in advance, and sorry for the long introduction!

---

### Post by lkjoel on 2010-07-05
Download LinuxEssentials from my sig.
Extract it, then log out and **log back into xterm**.
Then run:
```
cd /path/to/extracted/folder
chmod +x FASTGNOME.sh
./FASTGNOME.sh
```
or if you installed Terminal Enhancements 0.1b from my sig, you only need to type:
```
cd /path/to/extracted/folder
chmod +x FASTGNOME.sh
FASTGNOME.sh
```

---

