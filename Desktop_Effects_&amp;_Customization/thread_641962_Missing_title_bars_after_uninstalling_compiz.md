---
title: "Missing title bars after uninstalling compiz"
date: 2007-12-16
forum: Desktop Effects &amp; Customization
---

### Post by cjdaweasel on 2007-12-16
I recently installed Compiz on Dapper Drake using this guide here:

[http://www.tectonic.co.za/view.php?id=916]("http://www.tectonic.co.za/view.php?id=916")

It worked like a charm. Compiz installed, ran beautifully, but ultimately didn't do anything that I really needed. So I did the apt-get remove to remove the packages and deleted what I had added into my ./Xsession file (I didn't have one so I had to create it to install Compiz, I removed the file as part of my uninstall process), and logged out and back in.

Now my multiple desktops don't work and my title bars are missing. Everything defaults to the upper left corner of the screen. If I select Windows from my preferences menu I get an unknown error (the most useful of them all).

However, if I log into the Failsafe gnome Session, everything loads like it should, title bars,  and all. 

My Power management doesn't load in failsafe, I assume because some of the startup scripts have been disabled.

I think I'm having the same issue as this guy, but there wasn't a resolution that I could see:

[http://ubuntuforums.org/showthread.php?t=597940]("http://ubuntuforums.org/showthread.php?t=597940")

How do I get my title bars back?

---

### Post by cjdaweasel on 2007-12-16
Bump

Anyone?

---

### Post by njparton on 2007-12-16
I've just done precisely the same so I'm registering my interest in a solution. Sorry I can't help directly :)

I'm wondering if there's a way of reinstalling (-compiz) or refreshing gnome without messing up the whole installation?

---

### Post by potatu on 2007-12-16
Well, I'm no expert, but it seems to me that metacity doesn't kick in. Try this in the terminal.

```
metacity --replace
```

---

### Post by njparton on 2007-12-16
What's metacity for?

---

### Post by njparton on 2007-12-16
Well that worked for me until I rebooted.  How do I make it permanent?

Run it as root?

---

### Post by njparton on 2007-12-16
Running it as sudo doesn't help.

Neither does re-installing all the metacity packages via synaptic.

Does anyone have any other ideas?

---

### Post by potatu on 2007-12-16
Metacity is the standard window manager in Ubuntu. When you installed Compiz it uses the Compiz equivalent, Emerald, instead. However, after uninstalling, the system is still trying to fire up Emerald even though it doesn't exist.

I found this solution in another thread, should help you out. Fire up your terminal and type
```
gconf-editor
```

The configuration editor dialog should pop up. Navigate your way into desktop>gnome>applications>window_manager and change the value of default from (I presume) /usr/bin/compiz to /usr/bin/metacity . Exit and reboot.

That should take care of things.

---

### Post by cjdaweasel on 2007-12-16
> **potatu said:**
> Metacity is the standard window manager in Ubuntu. When you installed Compiz it uses the Compiz equivalent, Emerald, instead. However, after uninstalling, the system is still trying to fire up Emerald even though it doesn't exist.

I found this solution in another thread, should help you out. Fire up your terminal and type
```
gconf-editor
```

The configuration editor dialog should pop up. Navigate your way into desktop>gnome>applications>window_manager and change the value of default from (I presume) /usr/bin/compiz to /usr/bin/metacity . Exit and reboot.

That should take care of things.

I did that and /usr/bin/metacity is listed as both current and default. Just be sure I wiped them, put it back in, and rebooted. Still no titlebars. Still have them in failsafe mode though.

Edit: Do want to point out that I jumped in as the "offending" user  and did all this from that Terminal.

---

### Post by njparton on 2007-12-17
Excellent, that worked for me but you have to do it for both current and default.

---

### Post by cjdaweasel on 2007-12-17
Okay, so here's what has to be done apparently.

Run Terminal and put in:
```
gconf-editor
```

Go to** desktop>gnome>applications>window_manager** and make sure that /usr/bin/metacity is listed as both current and default.

Close that window.

In the terminal then type:

```
metacity --replace
```

Exit Terminal and Reboot.

I had to do both of those things in that order to get it to stick. Thanks for the help guys! Nice to have my titlebars back!

---

### Post by potatu on 2007-12-17
> **cjdaweasel said:**
> I did that and /usr/bin/metacity is listed as both current and default. Just be sure I wiped them, put it back in, and rebooted. Still no titlebars. Still have them in failsafe mode though.

Edit: Do want to point out that I jumped in as the "offending" user  and did all this from that Terminal.

Well, in that case I'm not your man, I'm afraid. You did try the "metacity --replace" as well?

EDIT: Didn't see your post there, glad to see it worked!

---

### Post by petermck on 2007-12-17
I had the same problems as other users have reported in this thread. No window borders etc. I tried metacity --replace with the same results reported above. Just running metacity without the --replace flag gave the same results, which indicated that metacity is not running at login.
I should point out that I have been using compiz and emerald for several weeks with no major problems, but uninstalled it to free up some resources. That's when my problems with windows management started. 
When uninstalling emerald and all the compiz stuff I chose to 'remove completely', which should have removed all configuration files. However two directories (.compiz and .emerald) where left in my home directory and appeared to stop metacity from starting. I deleted these directories completely and got my windows borders etc back. Metacity is now shown in System Monitor.
I should also add that I tried the suggested changes with gconf-editor with no success until I removed these directories.

---

### Post by petermck on 2007-12-17
Here's a couple of other tweaks I made to get metacity running really well.
[LIST=1]
[*]Uninstalled xserver-xgl. This was using a lot (40%+) of CPU power.
[*]In gconf-editor apps>metacity>general, I selected 'Use metacity as composite manager'. This is in addition to the changes described above (gconf-editor desktop>gnome>applications>window_manager, and set current and default to /usr/bin/metacity). I also applied these changes running gconf-editor as a normal user and as root. There are two seperate .gconf config directories, one under /root and one in your home directory. I'm not sure if this is really necessary but it seems to work well and cause no problems.
Iin /etc/X11/xorg.conf I set
```

Section "Extensions"
        Option          "Composite"     "1"
EndSection

```
[/LIST]
I'm using the fglrx driver with an ATI xpress 200M graphics card so some of this composite stuff may only be applicable to this hardware, but metacity now works properly using minimal resources (System Monitor shows it as sleeping usually).
Here's the performance of  fgl_glxgears and glxgears, which for a cheap integrated graphics card is pretty good.
```

user@xyz:~$ fgl_glxgears 
Using GLX_SGIX_pbuffer
1314 frames in 5.0 seconds = 262.800 FPS
2054 frames in 5.0 seconds = 410.800 FPS
2241 frames in 6.0 seconds = 373.500 FPS
1901 frames in 5.0 seconds = 380.200 FPS
2270 frames in 5.0 seconds = 454.000 FPS
2154 frames in 5.0 seconds = 430.800 FPS
2316 frames in 5.0 seconds = 463.200 FPS
1634 frames in 5.0 seconds = 326.800 FPS
user@xyz:~$ glx
glxdemo   glxgears  glxheads  glxinfo   
user@xyz:~$ glxgears 
4806 frames in 5.0 seconds = 961.111 FPS
5911 frames in 5.0 seconds = 1182.195 FPS
9047 frames in 5.0 seconds = 1809.367 FPS
8583 frames in 5.0 seconds = 1716.441 FPS
5743 frames in 5.0 seconds = 1148.570 FPS
9193 frames in 5.0 seconds = 1838.555 FPS
8724 frames in 5.0 seconds = 1743.714 FPS

user@xyz:~$ 

```

---

### Post by njparton on 2007-12-18
Excellent, I'm using onboard nvidia graphics but I'll give that a try too.

---

### Post by njparton on 2007-12-18
Hmmm, there are quite a few xserver packages listed in synaptic, I assume you left the xserver-xorg* packages alone?

My system's running faster than ever now, I don't know whether to just be happy or push on further :evil:

---

### Post by FokkerCharlie on 2007-12-19
Oh, dear!

I thought I'd give these instructions a try (metacity --replace, change the gconf settings to metacity) to get my desktop working a bit faster, but it's had unpleasant results!

Now my system won't boot correctly- after GRUB, the sreen reads 'Starting' and 'Loading, please wait', and then goes dark.  There's a fair bit of HDD activity, but nothing else.  I have to hold the power button to turn the system off.

Interestingly, there is no problem booting in recovery mode, where everything works absolutely fine.  I've also tried reversing the above steps (compiz --replace, gconf ->compiz), with identical results.  I even re-installed compiz, to no good effect.

This seems very strange to me, as I thought that these changes would only have an effect on starting the graphical (X Session, sorry, I'm new!) part of the OS.

And another thing- during the same session that I started trying to revert to metacity, the update manager downloaded some things (kernel headers, I think.  Whatever they are).

Any ideas?

Thanks in advance.

Charlie

---

### Post by aselya1 on 2007-12-19
Installing new headers always breaks GRUB for me, as I can't have splash at boot. Are you in a similar situation? If nothing else, try editing GRUB boot options at boot (as in press e on the line you would want to boot from, then highlight the line that starts with 'kernel' and press e again) and changing 'splash' to 'nosplash' (then press enter and then b to boot). 
I don't think that it is related to the changes you made with compiz though, just happened to coincide.

---

### Post by FokkerCharlie on 2007-12-19
aselya1

Thanks, that fixed it!

I had no inkling that headers would change grub. Or indeed what headers are.

It's nice to know that it's not just me who can't splash, too!

Cheers
Charlie

---

### Post by bharadwaj on 2008-01-29
yeah the same worked for me but was wondering if i could get any bug fix for exrald itself

---

### Post by ScottKidder on 2008-01-29
If all else fails just make an Sessions entry pointing to Metacity, I'm not really sure other than that...I would've kept compiz :D

---

