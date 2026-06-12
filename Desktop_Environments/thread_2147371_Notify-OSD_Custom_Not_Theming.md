---
title: "Notify-OSD Custom Not Theming"
date: 2013-05-21
forum: Desktop Environments
---

### Post by cipherboy_loc on 2013-05-21
On my laptop (running Ubuntu 10.04 as it has outdated hardware) I was able to theme my Notify-OSD using the repository [here]("https://launchpad.net/~leolik/+archive/leolik"). When I went to replicate the steps on my desktop running Ubuntu 13.04, the theming did not change. 

Information:
- Both computers are running Fluxbox as the default window manager
- Desktop notify-osd package version: Installed: 0.9.35daily12.11.28-0ubuntu1-leolik~ppa1
- File exists:
```

cipherboy@ubuntu-basement:~$ cat ~/.notify-osd 
slot-allocation = dynamic
bubble-expire-timeout = 5sec
bubble-vertical-gap = 5px
bubble-horizontal-gap = 5px
bubble-corner-radius = 0,5%
bubble-icon-size = 20px
bubble-gauge-size = 5px
bubble-width = 240px
bubble-background-color = 3c3b37
bubble-background-opacity = 100%
text-margin-size = 10px
text-title-size = 100%
text-title-weight = bold
text-title-color = ffffff
text-title-opacity = 100%
text-body-size = 90%
text-body-weight = normal
text-body-color = ffffff
text-body-opacity = 100%
text-shadow-opacity = 100%
bubble-close-on-click = 0
bubble-prevent-fade = 1
bubble-as-desktop-bg = 1

```

The main differences between these systems are in what is installed: on the desktop Gnome3 and Unity are also installed, whereas the laptop has only Gnome2. 

Running Notify-osd from the terminal does not enlighten me:
```

cipherboy@ubuntu-basement:/usr/lib/i386-linux-gnu$ killall notify-osd 
cipherboy@ubuntu-basement:/usr/lib/i386-linux-gnu$ ./notify-osd 
reading settings from '/home/cipherboy/.notify-osd'
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.
---separate window---
cipherboy@ubuntu-basement:/usr/lib/i386-linux-gnu$ notify-send "hi"
cipherboy@ubuntu-basement:/usr/lib/i386-linux-gnu$ 

```

What it should look like:
[http://imgur.com/5HhYn8z](http://imgur.com/5HhYn8z)

What it looks like:
[http://i.imgur.com/3taWDgG.png](http://i.imgur.com/3taWDgG.png)


Note: Upon playing around, it looks like it obeys some of the config file (size, image size, etc), but not the colors nor border radius.

Ideas?


Thanks,
Cipherboy LOC

---

### Post by Frogs Hair on 2013-05-21
10.04 is/was using gnome 2 and 13.04 is using gnome 3.6.. I am am only seeing 12.04 (gnome 3.4) listed in the ppa. but  I don't speak the language. You may want to check out the application at the link.  [http://www.webupd8.org/2013/04/configurable-notifyosd-updated-for.html](http://www.webupd8.org/2013/04/configurable-notifyosd-updated-for.html)

---

### Post by cipherboy_loc on 2013-05-22
Yes, that was the application I was using; the version string confirms it. Despite this however, it appears as if it is ignoring part of my theming file, but not all of it, which is odd. 


Thanks,
Cipherboy

---

### Post by Frogs Hair on 2013-05-22
You can ask a question at the link. [https://answers.launchpad.net/~leolik](https://answers.launchpad.net/~leolik)

---

### Post by cipherboy_loc on 2013-05-24
Could you double check your link? For me at least, it takes me to the page detailing all his posts/bug reports, 3 of which he created, one of which was submitted by somebody else but confirmed by him. What am I supposed to do with this? 


Thanks,
Cipherboy

---

### Post by Frogs Hair on 2013-05-24
You can login to launchpad and file a bug report on that PPA . When filing out the report the option to ask a question instead will be offered. If you use Launchpad answers the question may be addressed by a random volunteer and not by the PPA maintainer. The developer offers an email address on the PPA main page/ overview, but again you have login or create a Launchpad account.

---

