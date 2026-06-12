---
title: "Transparent mc in 9.10"
date: 2010-02-09
forum: Desktop Environments
---

### Post by BentFX on 2010-02-09
Okay, this image is what I was trying to get when I started. If it looks good to you, read on.

[IMG]http://bentfx.elementfx.com/images/mc_screenshot.png[/IMG]

First thing you need is Eterm... all other terminals seem to lack something, right-clicks are lost, menubars that won't go away, general wonkiness, it was always something.

Get Eterm...
```
sudo apt-get install eterm
```

If you load mc in an Eterm now the fonts are messed up. The fix is to change the default locale from UTF-8 to ISO-8859. we gotta modify some files...

in the file /var/lib/locales/supported.d/en add the line...

```
en_US.ISO-8859-1 ISO-8859-1
```

in the file /var/lib/locales/supported.d/local delete the UTF-8 line and replace it with...

```
en_US.ISO-8859-1 ISO-8859-1
```

Then run the command...

```
sudo dpkg-reconfigure locales
```

That should print out a lot of UTF-8 lines and our new ISO-8859 line.

Reboot!

mc should now display properly in an Eterm.

The next step is to modify the colors in mc, and add transparency to the main mc items.

Go to [Zagura's blog]("http://www.zagura.ro/index.php/2008/01/09/midnight-commander-color-themes/") and download the color changing script. (bookmark that site :))

I unpacked it as a sub-folder of ~/.mc so I would always have it where it is used.

Read Zagura's blog post and learn to load the different themes. It is really the easiest way to deal with colors in mc.

Open the theme files in a text editor to see how they are formatted. The default.theme is commented to show the different color options.

The general format is easy... It goes something like this...

```
ITEM_NAME=Foreground,Background
```

Once you've got a handle on all this, choose your favorite theme, make a copy of it, and start changing background colors to "default". When used in the background spot, default is transparent. I called my theme [BentFX.theme]("http://bentfx.elementfx.com/files/BFX_theme.tar.gz").

While editing/testing I used these commands to reload my theme and launch Eterm/mc to test my changes...
```
./mc_change_theme.sh BentFX.theme
Eterm -O --viewport-mode --shade 75 --buttonbar 0 -e mc
```

I realize this tutorial isn't real good but it explains all the things that I fought over in getting what I wanted... Your mileage may vary!

---

