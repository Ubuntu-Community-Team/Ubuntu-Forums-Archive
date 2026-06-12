---
title: "[64bit] Having trouble configuring for multiple monitors"
date: 2010-05-12
forum: Desktop Environments
---

### Post by mothergoose729 on 2010-05-12
I have two monitors of different resolutions. Under settings->display the settings for my monitor look like this:


[IMG]http://i303.photobucket.com/albums/nn153/mothergoose729/current.png[/IMG]

Ultimately what I want is to set up this kind of configuration:

[IMG]http://i303.photobucket.com/albums/nn153/mothergoose729/whatIwant.png[/IMG]

But whenever I do, it doesn't work out. When I up after setting the above settings, my configuration ends up like this:

[IMG]http://i303.photobucket.com/albums/nn153/mothergoose729/twonotgood.png[/IMG]

Any attempt to change the resolution or to change the display type to anything other then clone is simply ignored. If I disable the second monitor I can set my first to the proper resolution. If I try to set the settings to what I want they will stick but the second monitor doesn't actually turn on, and if i try to drag windows that direction it acts like a single display.

I have tried using the ATI control panel to adjust my display, but there seems to be a problem entering it as an administrator.I can load the CCC just fine as a regular user, but when I try as an admin a terminal pops up, I type in my password, and nothing happens. 

I want to avoid trying to reinstall my display drivers or do anything drastic. In previous versions of linux I would just nano the Xorg.conf file and be done with it, but it seems ubuntu 10.04 LTS doesn't use Xorg, or at least not a Xorg.conf I am used to. I want to set the monitors at their native res and as independent displays, similar to what twin view did for me not to long ago. Can anybody help me?

---

### Post by mothergoose729 on 2010-05-12
bump

---

### Post by mothergoose729 on 2010-05-13
bump :(

---

### Post by Zorael on 2010-05-14
You may want to try **arandr** from the repositories. I never had much luck with the included monitor configuration tool either.

If memory serves, I read on the mailing lists that a new plasmoid is in the works. So while the current tool may get minor bugfixes, I imagine that developer effort is placed in the new plasmoid instead.

If you're familiar with the terminal, the **xrandr** tool is also pretty straight-forward. But **arandr** is plenty powerful.
```
$ xrandr --output CRT1 --mode 1280x1024 --rate *CRTREFRESHRATEHERE* --right-of DFP1
```

---

### Post by mister_playboy on 2010-05-14
I had the exact same issues as the first poster, but it later fixed itself. :confused:

I'll give arandr a look.

---

