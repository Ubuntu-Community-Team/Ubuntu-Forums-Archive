---
title: "configuring gnome-screenshot under Unity"
date: 2018-11-02
forum: Desktop Environments
---

### Post by Skaperen on 2018-11-02
under Unity my _PrSc key_ triggers _gnome-screenshot_ to snap a picture of the screen which then gives me the option to save it.  but it also makes a classic old SLR camera snap noise.  today DSLR cameras are much quieter and the new mirrorless cameras are even quieter than that. and i often have my audio set way high because of things like low audio on many YouTube videos.  what i want to do is just turn *off* that click sound.  **how can i configure that thing?**  also, how can i add a button in the display to trigger it with a mouse click?

---

### Post by again? on 2018-11-03
I believe gnome-screenshot uses /usr/share/sounds/freedesktop/stereo/screen-capture.oga

Check if the file exists (it's actually a symlink to camera-shutter.oga)
```
ls /usr/share/sounds/freedesktop/stereo/screen-capture.oga
```

Try renaming that file
```
sudo mv /usr/share/sounds/freedesktop/stereo/screen-capture.oga /usr/share/sounds/freedesktop/stereo/screen-capture.oga.bak
```
You may have to reboot to lose the sound. I tested in unity 18.04 and that was the case.

For a launcher, press your screenshot key and pin the icon to the launcher which will give you right click options.

To revert the change 
```
sudo mv /usr/share/sounds/freedesktop/stereo/screen-capture.oga.bak /usr/share/sounds/freedesktop/stereo/screen-capture.oga
```

---

### Post by Skaperen on 2018-11-04
in 16.04.5 LTS the sound was lost *without* a reboot.  maybe a signal to a lingering process will reload it in your 18.

i do find that when i use this on Firefox (mine is maximized size) it causes it to scroll down or up to the input area for quick reply

---

