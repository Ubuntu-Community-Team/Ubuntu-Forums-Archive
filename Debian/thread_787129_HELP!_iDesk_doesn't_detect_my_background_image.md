---
title: "HELP! iDesk doesn't detect my background image"
date: 2008-05-08
forum: Debian
---

### Post by Cifra on 2008-05-08
Well I installed a Debian base system with Openbox and I'd like to use idesk with it. The problem is, i've got a wallpaper called 'image.jpg' in my .idesktop/icons/ directory nad the settings in the ideskrc file are (copied them from [http://idesk.sourceforge.net/wiki/index.php/Idesk-usage](http://idesk.sourceforge.net/wiki/index.php/Idesk-usage))

```
 Background.File: image.jpg
 Background.Delay: 1
 Background.Source: ~/.idesktop/icons
```

But the program still says it 'can't detect background image' when I try to run it with xterm.

Anyone had similar problems and found a solution?

---

### Post by urukrama on 2008-05-08
I've never really used idesk, but have you tried specifying the full path to the image file you want to use? Try the following:

> Background.File: /path/to/image.jpg
 Background.Delay: 1
 Background.Source: /home/USERNAME/.idesktop/icons

---

