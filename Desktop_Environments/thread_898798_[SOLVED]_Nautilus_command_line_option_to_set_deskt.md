---
title: "[SOLVED] Nautilus command line option to set desktop wallpaper?"
date: 2008-08-23
forum: Desktop Environments
---

### Post by ladr0n on 2008-08-23
Hey guys

Is there a way to set the nautilus wallpaper from the command line?  I have a script to set a random wallpaper at each login in openbox (using feh) and I'd like to do something similar on my gnome desktop.

---

### Post by Diabolis on 2008-08-23
That is similar to what was done in this thread: [http://ubuntuforums.org/showthread.php?t=888071&highlight=wallpaper+perl](http://ubuntuforums.org/showthread.php?t=888071&highlight=wallpaper+perl)

What solved it was this post: [http://ubuntuforums.org/showpost.php?p=5577700&postcount=3](http://ubuntuforums.org/showpost.php?p=5577700&postcount=3)

The command that you actually want to use is a gnome key:
```
gconftool-2 -t str --set /desktop/gnome/background/picture_filename *"Path to the image file"*
```

---

### Post by ladr0n on 2008-08-24
Okay, thanks.  That's exactly what I was looking for.

---

### Post by Twexcom on 2010-05-12
gconftool-2 -t str --set /desktop/gnome/background/picture_filename "/home/beetle/Desktop/yourfilename"

That is one way which you can do it.

It was even put in a script to make things easier, so you can just right click an image and click "set as wallpaper", and it does it automatically: [http://www.kompulsa.com/it/itdownloads.html#nautilus_scripts](http://www.kompulsa.com/it/itdownloads.html#nautilus_scripts)

---

