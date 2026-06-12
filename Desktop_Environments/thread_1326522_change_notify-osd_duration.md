---
title: "change notify-osd duration"
date: 2009-11-14
forum: Desktop Environments
---

### Post by winchendonsprings on 2009-11-14
Id like to change the duration tim eof the system pop ups. is there a file i can change? and where is its location? maybe in gconf editor? ive explored the web and both those options but im not exactly sure what im looking for

---

### Post by winchendonsprings on 2009-11-16
bump up

---

### Post by sieken on 2009-11-19
i bump aswell.

---

### Post by Aearenda on 2009-11-19
You can't do it in 9.10, AFAIK, without changing the code.

---

### Post by winchendonsprings on 2009-11-28
is there a way to do it with compiz? in animations?

---

### Post by Aearenda on 2009-11-28
Not AFAIK. But if you don't like it, why not install gnome-stracciatella-session to revert to the normal Gnome notifications? See [https://wiki.ubuntu.com/DesktopTeam/Specs/Jaunty/StracciatellaSession](https://wiki.ubuntu.com/DesktopTeam/Specs/Jaunty/StracciatellaSession).

---

### Post by winchendonsprings on 2009-11-28
no, i really like notify-osd. i'd actually like to make the notifications appear for longer

---

### Post by lswb on 2009-11-28
The developers apparently are of the philosophy that this type of user-level configuration is undesirable, thereby frustrating those who believe the notification time is too short as well as those believing it is too long.

---

### Post by MetroPietro on 2010-05-06
This is still a problem in Lucid. "Genaroneto" has done fine work showing us [how to add a patch and recompile notify-osd so that it accepts configuration parameters]("http://ubuntuforums.org/showthread.php?t=1378676").
But that thread does not explain how to add any parameter to change the duration of the notification-bubbles. So I am bumping this post.

---

### Post by ArielEnter on 2010-05-12
In the following post [http://ubuntuforums.org/showthread.php?t=1345040&highlight=Notify+OSD](http://ubuntuforums.org/showthread.php?t=1345040&highlight=Notify+OSD) [clhodapp]("http://ubuntuforums.org/member.php?u=918776") explains:

> Run:
     ```
sudo apt-get install devscripts build-essential
apt-get source notify-osd 
```Make your changes. I personally just made the notifications shorter by changing the definition of DEFAULT_ON_SCREEN_TIMEOUT in defaults.c then run:

     ```
sudo apt-get build-dep notify-osd
debuild 
```Install deb in directory above root of source, then run

```
      sudo echo -e "Package: notify-osd\nPin: version 0.0.24-0ubuntu1\nPin-Priority: 1001" > /etc/apt/preferences 
```
 to stop the package from being updated and your changes from being overwritten. Obviously, you need to correct the version to be whatever the current version is when you make your changes. Also, this is pretty hackish, since you should really *not* be just changing the code for an exisiting debian source package, but should rather be making your own version of the package.Thanks [clhodapp]("http://ubuntuforums.org/member.php?u=918776")

---

