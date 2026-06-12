---
title: "Plasma installation has broken Gnome Settings for extensions."
date: 2019-04-11
forum: Desktop Environments
---

### Post by JoelParke on 2019-04-11
I have been struggling for about a year under Ubuntu 18.04/18.10 with the error condition under plasma:
'[COLOR=#555555][FONT=Cantarell]Unable to locate GNOME Shell settings or version. Make sure it is installed and running.'

[/FONT][/COLOR]I have tried:
sudo apt install --reinstall chrome-gnome-shell
- no help
Next I upgrade to Ubuntu 19.04 in the hope that something might have changed.
- no help
THEN in desperation, I completely removed kde:
sudo apt remove kdelibs-bin kdelibs5-data
sudo apt remove kdm kde*
sudo apt remove kdm*
- rebooted.
And plasma was gone.
I then installed plasma again:
sudo apt install kde-plasma-desktop

BUT I still saw the dreaded failure:
'Unable to locate GNOME Shell settings or version. Make sure it is installed and running.'

SO is there anything else that I can try.  I do not want to reinstall a clean system and loose all of my package settings, etc.
Any help would be greatly appreciated.  THANKS!

---

