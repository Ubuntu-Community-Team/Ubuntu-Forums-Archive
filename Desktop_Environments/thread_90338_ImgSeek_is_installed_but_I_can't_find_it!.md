---
title: "ImgSeek is installed but I can't find it!"
date: 2005-11-14
forum: Desktop Environments
---

### Post by snowjunkie on 2005-11-14
Hi,
I installed imgseek just a while ago, but now I can't find it anywhere to start it.  Anyone have any ideas?

:confused:

---

### Post by arnieboy on 2005-11-14
[QUOTE=snowjunkie]Hi,
I installed imgseek just a while ago, but now I can't find it anywhere to start it.  Anyone have any ideas?

:confused:[/QUOTE]
if u installed it as a deb package, open synaptic and search for "imgseek" or whatever the package name was by **name**. when u find it, right click it and hit properties. there u will see a tab called "installed files" look in that and u will find what u are looking for. if u see something like **/usr/bin/imgseek**, u can run it from terminal as simply ```
imgseek
```. if u need a desktop entry, try using gnome menu editor to create a menu entry for imgseek.

---

### Post by Ampersand on 2005-11-14
Hi
Running 'imgseek' from a terminal should work, if not then open Synaptic, find imgseek in the package list, right click on it and go to properties, then look under the installed files tab. The files in /usr/bin are the executables (for example, /usr/bin/imgseek). Typing that in at a terminal will run it.

---

### Post by etc on 2005-11-14
imgSeek has the most annoying executable name
try this exactly, down to the capitalization
```
imgSeek
```

---

### Post by snowjunkie on 2005-11-15
[QUOTE=etc]imgSeek has the most annoying executable name
try this exactly, down to the capitalization
```
imgSeek
```[/QUOTE]

That's it!  Got it.  However, when I use "Search for Files..." with "File System" selected it doesn't show up in the results.  Why is that?

---

