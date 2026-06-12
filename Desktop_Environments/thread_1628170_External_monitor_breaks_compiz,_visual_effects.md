---
title: "External monitor breaks compiz, visual effects"
date: 2010-11-22
forum: Desktop Environments
---

### Post by gogolink on 2010-11-22
Hi all,

A few days ago, I did a clean install of Ubuntu 10.10 onto a Mac.  I dual-installed with Mac OS, and everything appeared to be going very smoothly...  until I connected to an external monitor (a video beamer I use in my classroom).  This led to:

a) the external monitor apparently being considered the primary monitor, and
b) compiz effects being disabled.  

I addressed (a) by modifying the file **monitors.xml** in [me]/.config.  (Before that. I had created a startup entry **xrandr --output LVDS1 --primary**. That also seemed to work; after changing monitors.xml, however, I disabled that startup entry, as it now appeared redundant to me.)  Generally and for all I can tell, my actual computer screen is now correctly identified as the primary monitor -- from the moment I log in, at least.  The log-in screen itself, though, appears on the external monitor, or not at all when that monitor is turned off.

This is the content of my monitors.xml file: 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=176262&stc=1&d=1290439172[/IMG]

I have not found any solution for (b): when I physically unplug the external monitor and reboot, compiz will run again; but once I plug in the external monitor, it won't.

Any ideas?

---

### Post by gogolink on 2010-11-23
OK, so would it be reasonable to assume that the external monitor uses a driver that is blacklisted?  Would that be the reason that visual effects are disabled when the monitor is plugged in?

What do you think?  How could I find out?
If the problem is one of a blacklisted driver: would there be any way around it?  Or is there likely to be an update that will allow the driver to be un-blacklisted?

Any suggestions would be much appreciated.  Thank you!

---

### Post by gogolink on 2010-11-23
Here's a bit more information:

Running **compiz-check** (from this website: [http://forlong.blogage.de/entries/pages/Compiz-Check]("http://forlong.blogage.de/entries/pages/Compiz-Check")) with the external monitor *off* (and visual effects on), I get this information:

```
Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]


```

As I said, as soon as I plug in the video beamer, visual effects turn off (there's a short flickering and rebuilding of the screen) and compiz fusion stops working.  Running compiz-check again gives me this result:

```
Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Your current resolution is too high to run Compiz. 

Would you like to know more? (Y/n) y

 Your resolution is 2464x900 but the maximum 3D texture size that your
 graphics card is capable of is 2048x2048. Thus Compiz will not be able to run
 on this setup. You have to decrease the resolution first (in case you are
 using a dual-head setup, try disabling one monitor and run the script again). 

```

The 2464 width must be the result of the 1440 width of my primary monitor, and the added 1024 of the secondary monitor, which I placed to the right of the first.  So let's see if desktop effects work again if I decrease the resolution of the secondary monitor...

Hm.  No, that didn't fly.  This time, the screen became messed up -- somewhat on the primary monitor, and entirely on the secondary one.

What else can I try?

---

### Post by gogolink on 2010-11-23
So this time I placed the second monitor on top of the primary one -- which worked!

Well, the only bummer is that when I maximize a window, part of it is now hidden under the top panel.  When I place my secondary monitor below the primary one, it's the bottom part of a maximized window that's hidden under the bottom panel -- which is not too bad, but still slightly annoying.  Does anyone have a solution to this problem?

---

### Post by gogolink on 2010-11-29
Can't declare this lonesome thread "solved" yet.  For one, there's the issue with the bottom panel.  I can live with that, fine.  But the other remaining problem is this:

When I turn on the computer and choose the Ubuntu drive (this is a dual install with Mac OS), Grub loads, and I get the splash / log-in window -- but on the wrong screen: If the video beamer is plugged in, the log-in window appears on the external monitor -- even if that one's not turned on yet.  Which means that I'm usually logging in blindly, on a screen that shows nothing but the Ubuntu background.

Now, I could live with that, as well.  But what's annoying me is that Ubuntu will start with desktop effects disabled (System > Preferences > Appearance > Visual Effects: None).  I can now enable those effects, and use Compiz Fusion -- but I have to do that each time I log in.  It always starts with visual effects disabled.

My guess is that this happens because the log-in screen breaks Compiz Fusion: I believe it still works on a former display setting, one in which I have both monitors arranged next to (and not on top of) one another, so that the combined width exceeds the maximum 3D texture width this graphics card can handle.

If that guess is correct, all I would have to do is set my current display setting, in which the two monitors are arranged on top of one another, as the default one also for the splash / welcome screen.  But how would I do that?

Again, I'd much appreciate any suggestions...  :)

---

### Post by gogolink on 2010-11-30
It appears all I had to do was to click "set as default" in the display settings.  And I could have sworn I had done that before...

Be it as it may -- now pretty much everything seems fine.  The login-window still appears on the wrong screen, but that's not a problem.  The main screen -- my computer's screen -- appears above that display, as I have set it in display settings.  Ubuntu loads with compiz running and visual effects enabled.  

Everything's fine.

---

### Post by thevan on 2011-03-20
Placing the external monitor on top appears to work for me. This should really be fixed though... also there's no non-terminal way to set one as the primary monitor AFAIK. Silly silly.

---

