---
title: "Help with DWM please!"
date: 2009-02-18
forum: Desktop Environments
---

### Post by fisfia on 2009-02-18
Hi,

I installed dwm because I don't like Awesome anymore. I installed it with sudo apt-get install dwm. But I heard theres not a configfile like for awesome to change things. Instead you have to recompile dwm after changes. How does this work? How do I recompile if I installed with apt-get? I didnt use source in the first place. 

I would like dwm windows to be called not 1, 2, 3, 4 etc but www, music, im, and so on. This is my goal. Any clues for me?

---

### Post by kerry_s on 2009-02-18
[http://xmonad.org/](http://xmonad.org/)

---

### Post by ddnev45 on 2009-02-25
[http://www.suckless.org/dwm/customisation/]("http://www.suckless.org/dwm/customisation/")

[http://ubuntuforums.org/showthread.php?t=1053814&highlight=dwm]("http://ubuntuforums.org/showthread.php?t=1053814&highlight=dwm")

examples of config.h

[http://dotfiles.org/search?q=config.h]("http://dotfiles.org/search?q=config.h")

you can recompile from source and it should (worked for me) update the version from apt.

---

### Post by urukrama on 2009-02-25
Just download the source code from the dwm website, edit the config.h file to your liking and compile. Dwm is so small that building it from source doesn't take much time at all.

I've never really seen the point of installing dwm from the repos. It is generally and outdated package, and you are not able to customise the build.

But, as mentioned, just recompile and it should update your installed version (just make sure you have specified the right path in config.mk).

---

### Post by ddnev45 on 2009-02-25
> **urukrama said:**
> Just download the source code from the dwm website, edit the config.h file to your liking and compile. Dwm is so small that building it from source doesn't take much time at all.

I've never really seen the point of installing dwm from the repos. It is generally and outdated package, and you are not able to customise the build.

But, as mentioned, just recompile and it should update your installed version (just make sure you have specified the right path in config.mk).

Sort of off topic, and don't mean to hijack the thread, but do you have an entry or fix for the config.h that will eliminate the small areas of screen around terminal windows? I can't get the terminal windows to tile completely to the right or bottom.

*Edit: Never mind, found what I needed in the Arch Linux wiki.*

[http://wiki.archlinux.org/index.php/Dwm]("http://wiki.archlinux.org/index.php/Dwm")

---

