---
title: "terminal/gnome-console fonts"
date: 2005-02-06
forum: Desktop Environments
---

### Post by buldir on 2005-02-06
I would like to install the console 8x8 and 8x16 fonts for use in the Gnome terminal.  I installed "xfonts-konsole" and "xfonts-terminus" via Synaptic, but they don't show up in the list of available fonts.  Any thoughts?  Thanks.

---

### Post by Tomek on 2005-05-02
Hi, 

I've got the same problem/question, so I'm bumping this thread. :)

---

### Post by buldir on 2005-05-03
Tomek,

I figured it out.  Just for the record, I'm using Kubuntu Hoary.  Using apt-get or synaptic, install the following fonts:

xfonts-konsole
xfonts-terminus
console-terminus

The first one may not be available to you, since it is related to the KDE console and not Gnome.  Anywho, then type in the command line:

```
sudo dpkg-reconfigure -plow fontconfig
```

It will bring up a window asking you to reconfigure your font rendering settings.  I chose the CRT option (#1).  There's also "Autohinting" (#2) and "Subpixel" (#3) for LCDs.  I have an LCD and think option #1 looks best, but that's my opinion.  Hit enter.  The next screen is the important one.  It asks if you want to enable bitmapped fonts by default.  Select "Yes" and hit enter.  It then makes the changes to your font.config file.  Close the CLI, log out, and log back in.  You should now be able to see and select bitmapped fonts in the Gnome CLI font settings.  You may have to reboot, but I think restarting X by logging out and back in should do the trick.  I hope this helps.

---

