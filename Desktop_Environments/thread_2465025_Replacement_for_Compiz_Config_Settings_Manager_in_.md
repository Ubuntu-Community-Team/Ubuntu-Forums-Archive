---
title: "Replacement for Compiz Config Settings Manager in Ubuntu 20.04?"
date: 2021-07-19
forum: Desktop Environments
---

### Post by swaranga on 2021-07-19
I recently migrated from Ubuntu 16.04 to Ubuntu 20.04 and one of the things I am missing is the Compiz Config Settings Manager. I used the "window grid" functionality of this application very much. It would allow me to quickly move a window to a quadrant (top-left, top-right, bottom-left, bottom-right) or a half (top-half, bottom-half, right-half, left-half) using a keyboard shortcut like Ctrl+NumPad (1-9). This application seems to no longer be supported in 20.04 and right now I can only use the mouse to move a window to the left or right half which is very limited.

Are there any replacements for this application that works in 20.04?

---

### Post by deadflowr on 2021-07-19
A replacement would be to install and use unity.
The new desktop, gnome-shell, does not use compiz,
but the older, still installable, unity desktop still does.

Alternatively if you want to keep on using gnome-shell, there may be some shell extensions which do some or all of what you want.
Though you would need to dig for them here: [https://extensions.gnome.org/]("https://extensions.gnome.org/")

Caveat for extensions would as they are community built entities they can either end up breaking whenever a new gnome-shell version is released.
Or the creator can simply abandon them at anytime.
So it's sort of a buyer beware situation. If that make sense.

---

### Post by monkeybrain20122 on 2021-07-19
```
sudo apt install ubuntu-unity-desktop compizconfig-settings-manager
```

choose lightdm when the popup asks, reboot then you are back in unity. I am using Unity in 20.04, no problem whatsoever and a lot more responsive than gnome shell. I keep the gnome session so I can login to add some extension and try it out once in a while. Even with extensions it is still awkward to use IMO and it is sluggish.

 Gnome shell doesn't use compiz and gnome has its own way of doing  things. I don't know of any extension that can duplicate the function  you want, though you may look into the built in function called  activities. I don't know what it does in gnome shell except exposing  desktops and apps (kind of like scale + expose in compiz) but "activities" is  very configuable and complex in KDE.

---

### Post by CatKiller on 2021-07-19
Another option to consider is [Pop OS' Cosmic](https://blog.system76.com/post/655369428109869056/popos-2104-a-release-of-cosmic-proportions) or Kubuntu.

---

### Post by swaranga on 2021-07-20
I ended up using WinTile: [https://extensions.gnome.org/extension/1723/wintile-windows-10-window-tiling-for-gnome/](https://extensions.gnome.org/extension/1723/wintile-windows-10-window-tiling-for-gnome/) which seems to work more or less (the keyboards shortcuts are a little weird although I can get used to them). The other option was to go back to Unity but I am not much of a fiddler and Gnome otherwise seems to work well and I like the dark mode.

---

### Post by ActionParsnip on 2021-07-21
Gnome Tweak, maybe?

---

### Post by Frogs Hair on 2021-07-28
Not an official Ubuntu release, but maybe of interest. 
[Ubuntu Unity – Unity is power.]("https://ubuntuunity.org/")

---

### Post by Guy_Rouillier on 2022-01-16
I just installed CCSM on 21.10 Ubuntu Mate from the Synaptic Package Manager.  So on that spin at least, CCSM is still available in the regular repos.

---

### Post by BlueAZ on 2022-01-18
Wow, thank you, MonkeyBrain20122!  Works like a charm!!  I've missed Unity so much.

---

