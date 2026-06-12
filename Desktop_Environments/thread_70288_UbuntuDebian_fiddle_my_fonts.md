---
title: "Ubuntu/Debian fiddle my fonts"
date: 2005-09-29
forum: Desktop Environments
---

### Post by Raeth on 2005-09-29
> Greets,
On all distros I try, I am able to change the anti-aliasing type with the handy GNOME Font Preferences. There is "Monochrome", "Best shapes", "contrast" and "Subpixel smoothing".
I can change these with real-time effect on any distro, apart from Ubuntu (and Debian).
Ubuntu is eternally stuck on Subpixel mode, making fonts look scratchy and thin, rather than smoothly AA'd.
Does anyone know how to disable this lock and apply another AA type?
Ta,
RaethAlrighty, I solved it by sticking this into my .fonts.conf directory in home:
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <match target="font">
    <edit name="autohint" mode="assign">
      <bool>true</bool>
    </edit>
  </match>
</fontconfig>
```
This must have removed the disabling data that was in there to begin with.

---

### Post by Alexander Kirillov on 2005-09-30
[QUOTE=Raeth]Greets,
On all distros I try, I am able to change the anti-aliasing type with the handy GNOME Font Preferences. There is "Monochrome", "Best shapes", "contrast" and "Subpixel smoothing".
I can change these with real-time effect on any distro, apart from Ubuntu (and Debian).
Ubuntu is eternally stuck on Subpixel mode, making fonts look scratchy and thin, rather than smoothly AA'd.
Does anyone know how to disable this lock and apply another AA type?
Ta,
Raeth[/QUOTE]
Works fine here. Did you try clicking on "details" button?

---

