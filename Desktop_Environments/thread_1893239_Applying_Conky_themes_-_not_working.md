---
title: "Applying Conky themes - not working?"
date: 2011-12-09
forum: Desktop Environments
---

### Post by MattPerovich on 2011-12-09
I apologize if I'm doing something incredibly obvious - this is my first Linux system I've ever worked on (made the switch from Windows), and this computer's a project for a High School class...

Moving on, I seem to be having trouble with applying themes to Conky. Namely, I want it to look something like this:
[http://vindsl.com/images/vindsl-desktop-28-may-2011.png](http://vindsl.com/images/vindsl-desktop-28-may-2011.png)

However, when I run Conky through terminal it looks like the picture I've included. I can't figure out how to apply themes, or even how to move it (about 1/4th of it is being hidden by my taskbar).

Any tips/tricks/advice for a beginner?
Thanks!

PS - I've tried following the instructions included with the installation of different themes. Conky, however, doesn't seem to have a .conky file in my Home folder, even after installing Conky.

OS: Ubuntu 11.10 64-bit

---

### Post by stinkeye on 2011-12-10
Firstly, your diving in at the deep end with this conky config.

When you run conky it looks for a config @ **~/.conkyrc**. ( ~ is a shortcut for /home/*[COLOR="DimGray"]username[/COLOR]*)
If there is no such file it will load with the default config from /etc/conky/conky.conf, which is what you see.

All the output you see on screen is determined by your config.

To run VinDSL Conky you will need all scripts and fonts with scripts in the correct path as determined by the **.conkyrc**.

Then you must edit things in the conkyrc to suit your computer.
eg HDD CPU GFX etc.

You can also test any conky configs you download using...
```
conky -c /path/to/config 
```
I keep numerous configs in a conky folder in my home directory.
You can name them anything you want and use the **conky -c** option to load them.
eg I have one conky config which checks and displays unread gmails.
I saved the config as **conkygmail** and to run conky using this config I use...
```
conky -c ~/conky/conkygmail
```

[**_[COLOR="DarkRed"]HOWTO: VinDSL Conky Script[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1771033")
[**_[COLOR="darkred"]HOW TO: A Beginners Guide to Setting up Conky[/COLOR]_**]("http://ubuntuforums.org/showthread.php?p=5436679#post5437628")

---

