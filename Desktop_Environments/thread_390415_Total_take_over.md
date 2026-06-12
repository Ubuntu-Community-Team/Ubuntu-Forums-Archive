---
title: "Total take over"
date: 2007-03-21
forum: Desktop Environments
---

### Post by jerryroy on 2007-03-21
i want to stretch my capabilities an knowledge of this great operating system by fully pimping out the way it looks, an doing it by myself creating everything from scratch using gimp

---

### Post by kostkon on 2007-03-22
It's not easy the thing you want to do. Assuming you use Ubuntu, you'll have, at least, to create your own metacity theme, gtk theme, or if you use Compiz/Beryl your own theme for these 3D desktops. Furthermore, you'll have to have your own wallpaper, GDM and icon theme and last your own splash screens.

It's all lot of hard work. OK, you can easily create your own wallpaper and splash screens but a desktop and icon themes are a little more complex things to make.

Most people don't make all-in-one packages in the theming world. They usually make a desktop theme with maybe a wallpaper, or only icon themes and stuff like that. But if you want to create a fully integrated desktop that everything will be created from you, go for it. Why not?

And, if you feel like sharing it, gnome-look.org would be a good place to upload your themes.

---

### Post by jerryroy on 2007-03-22
so how can i change the splash screen?

---

### Post by kostkon on 2007-03-22
Hi,

if you mean the **uSplash**, the spash screen you see during the boot process, then you can start from here:

[https://help.ubuntu.com/community/USplash]("https://help.ubuntu.com/community/USplash")

If you mean the Gnome splash image that you see after you login, create a reasonably sized image and then use the *gnome-splashscreen-manager* application to replace the current splash screen image with your own image.

To install *gnome-splashscreen-manager*, just search for it in *Synaptic* or just type this on a terminal:
```
sudo apt-get install gnome-splashscreen-manager
```

---

