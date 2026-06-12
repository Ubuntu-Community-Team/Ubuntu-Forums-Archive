---
title: "xfce4 background / wallpaper - .jpg not allowed"
date: 2007-01-22
forum: Desktop Environments
---

### Post by vodsonic on 2007-01-22
Tried to change the wallpaper on my Xfce4 desktop (under Xubuntu 6.10). I used sudo thunar to put several .jpgs in /usr/share/xfce4/backgrounds, which is where the default background images - all in .png format - are found. If I open the Desktop Properties window and select any of the .jpg files as my background, I only get a solid color on my desktop.

Xfce4 doesn't seem to want to display .jpgs as wallpaper. I don't know if this is due to the compressed nature of .jpgs, and/or if it was just a decision based on conserving storage space and system resources.

I had to use GIMP to open the .jpgs and save them as .png.

Unless I ran into a subtle permissions problem. I did move the .jpgs into /usr/share/xfce4/backgrounds as the superuser, but I don't know if the permissions are set right for a user to open one of the images for use as a background.

Does anyone have a definitive answer regarding whether Xfce 4 will allow the use of .jpgs as a background?

---

### Post by -Phi- on 2007-01-22
I think your issue is a permissions one. Xfce4 certainly displays .jpg wallpapers.

Try setting an image that's in your home directory as a desktop image. Just navigate from the file manager interface. Alternatively, try changing the permissions on the wallpapers you moved as root. 

Good luck!

- Phi

---

### Post by Pobega on 2007-01-22
Yeah, I'm using a .jpg as my desktop wallpaper right now.

It's probably just what -Phi- said, you could put it in your /home directory or you could always chmod the files in /usr/share/xfce4/backgrounds.

---

### Post by kerry_s on 2007-01-22
I'm also using a jpg out my home directory.

---

### Post by sachsash on 2008-05-24
Thanks mate.
I sill can't add .jpg wallpapers to the Appearances Preferences app.

---

