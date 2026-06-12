---
title: "just bought a keyboard which only goes up to F6 ; need to reassign hotkeys...."
date: 2011-12-28
forum: Desktop Environments
---

### Post by shantiq on 2011-12-28
just bought a keyboard which only goes up to F6 [microsoft arc]; need to reassign hotkeys.... for Opera 



i wish to change F11 for Fullscreen to F6


read around a bit and tried a few things but still no joy


is there anywhere in the files i can modify that?

---

### Post by shantiq on 2011-12-29
ok worked it out    [ might be of use to others too]

files are there   i did the same for both altho not sure second one needs doing


```
sudo gedit /usr/share/opera/ui/standard_keyboard.ini
```
```
sudo gedit /usr/share/opera/ui/standard_keyboard_compat.ini
```


scan documents with Search     in the end i replaced F11 with F3   as I had F6 already allocated


F3 in opera if for find which i never used so removed that line


then SCROLL DOWN TO Browser Window



and replace   ```
Platform Windows-Unix-MCE, F11			= Enter fullscreen | Leave fullscreen
```


with   ```
Platform Windows-Unix-MCE, F3			= Enter fullscreen | Leave fullscreen
```



and reload Opera

it still reads F11 in the view dropdown box but now works with F3:KS

---

