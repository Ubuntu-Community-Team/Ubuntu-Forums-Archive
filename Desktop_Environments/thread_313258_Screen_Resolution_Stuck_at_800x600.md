---
title: "Screen Resolution Stuck at 800x600"
date: 2006-12-05
forum: Desktop Environments
---

### Post by tux-curious on 2006-12-05
Hey.

So I'm running Edgy, but I had the same problem with Dapper too.

Today I logged off my desktop when I went to school. When I logged back on the screen resolution went down to 800x600.

I went to the Screen Resolution tool, but it would only give me the options of 800x600 and 640x480.

I reset my computer, and it let me change it back, so all's good.

I was wondering if anybody knows what causes this, or if anybody else has the same problem.

---

### Post by vierdreieins on 2006-12-10
I'm having the same problem, only mine gets stuck in 640x480 and won't let me choose anything else. I logged out and tried it again, and it went back. I'm having trouble with it booting from the CD, though. Yours is installed and you're having the same problem?

---

### Post by vierdreieins on 2007-01-13
Now I'm having the problem after a month of running it from the hard drive with no issues whatsoever--it's stuck at 640x480, and it's really bugging me. 

I'm just a tad discouraged that no one has responded to this and that I haven't seen any other similar posts about the issue.

---

### Post by studiesrule on 2007-01-13
just open up a terminal and type:
sudo dpkg-reconfigure xserver-xorg
Follow the wizard (cause thats what it is), and when it comes to screen resolutions, check all those that you want.
Then restart.

---

### Post by vierdreieins on 2007-01-13
> **studiesrule said:**
> just open up a terminal and type:
sudo dpkg-reconfigure xserver-xorg
Follow the wizard (cause thats what it is), and when it comes to screen resolutions, check all those that you want.
Then restart.

The problem though isn't that the resolution simply doesn't exist, it's just that it seems to ignore it upon booting every once in a while, and re-starting it a couple of times seems to reset it. I'm mostly curious why it would ignore it for a few restarts and then revert back to normal.

---

### Post by Hub-1 on 2007-01-13
You can cycle trough your Display Modes by pressing:  **CTRL**+**ALT**+ '**+**'  or **CTRL**+ **ALT**+ '**-**'
An other solution is using xrandr to set your displaymode. Open a terminal and type:
```
xrandr
```
This shows your available display modes. You can then use the option -s to choose your display mode according to the numbers displayed on front of the resolution.
This sets the highest possible resolution:
```
xrandr -s 0
```
Also, could you please paste the output of this command?
```
cat /etc/X11/xorg.conf | grep Modes
```

---

