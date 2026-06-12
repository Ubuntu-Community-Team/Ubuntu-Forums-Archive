---
title: "Battlefield 1942 - twinview"
date: 2007-02-15
forum: Gaming &amp; Leisure
---

### Post by feest on 2007-02-15
Hi, I got a copy of Bf 1942 installed on cedega and I know from my previous install it works fine with cedega, it does. But the problem is i have 2 screens running twinview, I figured out that when i use only 1 screen (other screen disconneted at boot) it runs fine. But when i have 2 screens active it fails to start saying "Invalid videomode specified" and stops. doe sombody know a solution for this?

---

### Post by Jovec on 2007-02-15
If you can run BF1942 in a window you shouldn't have this problem, but IIRC that game doesn't have a windowed mode natively.  I don't know enough about cedega/wine yet to know if it can force a windowed mode.


Instead of unplugging your monitor, if you want you can edit your xorg.conf to add a new metamode for twinview that will temporarily disable your second monitor:

```
$sudo vim /etc/X11/xorg.conf
```

(replace vim with your editor of choice, i.e. nano).

Look for the line that reads (similar to):

```
 Option         "MetaModes" "1280x1024,1280x1024"
```

and make it say:

```

 Option         "MetaModes" "1280x1024,1280x1024; 1280x1024,NULL"
```

Important:  Don't use 1280x1024 if that is not the resolution you want to run in!  Use the resolution appropriate for your video card and monitors.

Now you'll need to restart your xserver - either restart the computer, ctrl+alt+backspace, sudo /etc/init.d/gdm[xdm,kdm] restart, etc.... for the new mode(s) to take effect.

Here is what is going on:  With twinview, in the above example, your resolution is 2560x1024, which is not a valid resolution for BF1942 IIRC, and you don't have a metamode entry for the resolution the game wants to run at.  The second metamode entry above will disable the second monitor, so your resolution will just be 1280x1024 on one screen, which the game can run at.

If the game doesn't automatically switch to the proper metamode with the second screen disabled, you can do it manually. To switch modes, you can just run:

```
xvidtune -next
```

before running your game.  When you are done, run it again to switch back to both monitors.  You could incorporate this into a script if you like to do it automatically.

---

### Post by feest on 2007-02-18
well because of some problems i removed it so thx for the help but currently i can not use it...

---

### Post by feest on 2007-10-06
I've tried it again (after a very  long time) but this video mode does not seem to help. It still says.... Invalid videomode specified?

---

