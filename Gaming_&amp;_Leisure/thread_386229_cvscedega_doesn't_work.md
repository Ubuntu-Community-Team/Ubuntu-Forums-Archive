---
title: "cvscedega doesn't work"
date: 2007-03-16
forum: Gaming &amp; Leisure
---

### Post by thelinuxer on 2007-03-16
Hi all,

I managed to download and build cvscedega from source code. Now I have an executable but it returns an error that I can't handle. Here is what happens:

```

cvscedega /media/sda5/Games/Hardwood\ Solitaire/Hardwood\ Solitaire.exe 
err:font:ReadFontDir Can't open directory "/usr/X11R6/lib/X11/fonts/truetype/"
Could not load graphics driver 'x11drv'
err:win:GetDesktopWindow Wine init error: either you're trying to use an invalid native USER.EXE config, or some graphics/GUI libraries or DLLs didn't initialize properly. Aborting.

```

I have an NVidia 7300 LE graphics card

Are there needed packages that I need to install? 

Thanx

---

### Post by hikaricore on 2007-03-17
First of all if you're just trying to run windows programs, you may want to try wine: [http://www.winehq.org](http://www.winehq.org)

For easily installable packages you'll find them here for ubuntu:  [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

I'm not sure if your game is working in wine but it can't hurt to try.  You should only use cvscedega if you have software that's known only to run /w cvscedega, otherwise you're likely wasting your time and giving yourself a headache.

I was unable to find any linux related mention of Hollywood Solitare with search engines or in the [Wine Application DataBase]("http://appdb.winehq.org") so if you have luck with your title, please consider adding it to the database to help the community.  :)

Good Luck,

--Aaron

---

### Post by hikaricore on 2007-03-17
One more thing, have you installed the proprietary drivers for your Nvidia card?  Or are you using the open source drivers that come stock with ubuntu?  If you're using the stock drivers you may have issues with games and other video intense application, you may want to install the drivers Nvidia offers for linux instead.  These are not directly supported by the linux community, but you can usually find people willing to offer assistance and solutions.  :)

---

### Post by thelinuxer on 2007-03-17
Hi hikaricore,

Thanx for replying. I managed to install the drivers using this way 

```

sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-xconfig

```

There was some linux games that needed 3D acceleration they were slow before I install this and now they are fine.

I am just experementing with cvscedega. I want to know how to make it work. Let's take Silent Hill2 as an example

[http://cedegawiki.sweetleafstudios.com/wiki/Silent_Hill_2](http://cedegawiki.sweetleafstudios.com/wiki/Silent_Hill_2)

This wiki says it's unplayable, I actually don't care because the installer never starts.Here is what I do:

```

:~$ cvscedega Silent\ Hill.exe
err:font:ReadFontDir Can't open directory "/usr/X11R6/lib/X11/fonts/truetype/"
Could not load graphics driver 'x11drv'
Could not load graphics driver 'x11drv'
wine: Unhandled exception, starting debugger...
err:win:GetDesktopWindow Wine init error: either you're trying to use an invalid native USER.EXE config, or some graphics/GUI libraries or DLLs didn't initialize properly. Aborting.

```

I tried wine and the installer completed successfully without any problems. But I just don't know how to start the game! I tried KMenu->Wine->Programs->Silent Hill and all I can find is "Uninstall Silent Hill"

I am completely clueless

---

### Post by hikaricore on 2007-03-17
First of all, glad you were able to get your drivers installed. :)

With wine, just like cvscedega you will need to goto the directory the game is located in to start it.

```
cd ~/.wine/drive_c/Program\ Files/Silent\ Hill
wine Silent\ Hill.exe
```

The location of your install and the name of the exe application may vary.  :)

You can always make a launcher for software later but it's best to start it from a terminal so you can see what is going on.

Tho looking at this: [http://appdb.winehq.org/appview.php?iVersionId=4525](http://appdb.winehq.org/appview.php?iVersionId=4525)

You probably won't get much further than the title screen, even with cvscedega.

---

