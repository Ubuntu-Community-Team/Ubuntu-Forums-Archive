---
title: "Screen &quot;too big&quot; and K Menu gone!"
date: 2006-11-18
forum: Desktop Environments
---

### Post by wilberfan on 2006-11-18
I just did an

```
 sudo aptitude install kde-core 
```

and when I started the session, the K Menu (is that what it's called?) was gone and the desktop is "bigger" than the monitor!  There are icons n' things off the screen that I can only get to if I move the pointer over to an edge of the screen--at which point things scroll over...

I've just spent 10 minutes in KControl looking for a screen rez setting--to no avail!

My Gnome sessions still look great...

What's going on?!

---

### Post by aysiu on 2006-11-18
Go to Konsole, and try these commands: ```
kicker &
sudo aptitude update
sudo aptitude install kde-guidance
kcontrol
``` The first command gets the panel back up, you can then add the KMenu from there (frankly, I'm surprised it wasn't there to begin with). The next two commands install the screen resolution config, and the last command launches the Control Center, so you can adjust the screen resolution.

---

### Post by wilberfan on 2006-11-18
Okay... I got the K menu (applet?) restored to the task bar...

Why do I get this when I start KControl?


> X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

Why can't I find the screen res setting once I open KControl??!

Why do minimized windows just disappear (ie, not show up on the task bar at the bottom of the screen?!

---

### Post by aysiu on 2006-11-18
Sounds as if you're missing quite a few applets on your panel (including the task list). You can add that (taskbar) the same way you added the KMenu.

As for the message you get when you start KControl, that's normal.

You sohuld be able to find screen resolution in KControl if you installed *kde-guidance*. It's under Peripherals > Display

---

### Post by wilberfan on 2006-11-18
Dude, I really thought we had it licked!

I got the applets restored to the task bar (thanks!)  I NEVER would have found screen res in Peripherals > Display (thanks!) It was set to 1792 x 1344 (when I needed 1280x1024).   

Things started sucking when I changed the res and it told me to "press the 'restart x server button' in the menu".

OK.  Where the #%$& is that?!   I tried a Ctrl-Alt-Delete...and I just got a blank screen--a BLACK, blank screen...

Something's wrong somewhere...    (Could any of this be due to installing a new video card?!  The old card was an nVidia--so's the new one...)

---

### Post by aysiu on 2006-11-18
Control-Alt-Backspace restarts the X server. It's not a button, though--it's three--so I don't know what the message means.

Try it out.

And, yes, it could have something to do with a new video card.

---

### Post by wilberfan on 2006-11-18
> **aysiu said:**
> And, yes, it could have something to do with a new video card.

Words to chill my heart!

Look out world--time to reinstall Edgy!!  :evil:

---

### Post by aysiu on 2006-11-18
> **wilberfan said:**
> Words to chill my heart!

Look out world--time to reinstall Edgy!!  :evil:
Before you reinstall, can we try something else?

Log out of KDE
Then press Control-Alt-F1
Log in
Type: ```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/kdm stop
sudo dpkg-reconfigure xserver-xorg
``` Answer the questions as best you can. If you don't know the answer to a question, just go with the default. Finally: ```
sudo /etc/init.d kdm restart
``` (or *gdm restart* if you're using GDM) and then press Control-Alt-Backspace

---

### Post by wilberfan on 2006-11-18
I appreciate your enthusiasm (I really do!)--but now I'm getting file system check errors...

Something is seriously snarked.

I'm gonna try the re-install!   "Just try 'n' stop me, world!"

---

### Post by wilberfan on 2006-11-18
Okay....  I'm reinstalled enough to have reloaded kde-core.  First thing I notice?   There is no monitor entry in the peripheral section of the Control panel!

WTF?

[edit] None of the screen savers work, either...

---

### Post by aysiu on 2006-11-18
I thought we went over this.

To get the monitor section, you need to install *kde-guidance*.

---

### Post by wilberfan on 2006-11-19
That's been filed away for future reference.  I've decided I'm new enough at this that I want to see EVERYTHING (well, a lot of) what KDE can do.   So I pussed-out and installed the Kubuntu Desktop.  

Does kde-guidance include the screensavers?  (Gawd, where would you ever LEARN that you had to install something separate to be able to adjust your monitor unless you stumbled down this road and ended up asking?!)

I went back and looked, and yes, oh wise one, you DID say that that critter had to be installed to adjust those settings.  The first time through, I read it as more of a workaround...

My bad.

Your psychocats page is awesome, btw.  Thanks for your patience, kind sir.

---

### Post by aysiu on 2006-11-19
> **wilberfan said:**
> 
Does kde-guidance include the screensavers?  (Gawd, where would you ever LEARN that you had to install something separate to be able to adjust your monitor unless you stumbled down this road and ended up asking?!) I did ask, as a matter of fact. Check out this thread:
[What package has the display in KDE peripherals?](http://ubuntuforums.org/showthread.php?t=232259&highlight=kde-guidance)

For screensavers, try installing *kscreensaver*.

---

### Post by wilberfan on 2006-11-19
So the Sensei was a Grasshopper once?    I feel a leeeeeetle less stupid, right now.   Thanks.   8-[ 

The part of that thread where you said Firefox took 12 seconds to load?   I've noticed that, too!  {Sigh...}   I may have to 'speriment with KDE-Core on the Pentium 4 here...and play with Kubuntu on the AMD Dual-Core.

Thanks again for your help.  Sometimes I work at this stuff for much too long at a stretch and get a little punchy!  :redface:

---

### Post by wilberfan on 2006-11-19
Interesting...  I just removed the kubuntu-desktop and installed the kde-core (as I had yesterday).   The same three applets failed to load on the taskbar at initial startup of the kde-core...

I got the kde-guidance loaded this time, without any problems.

The next thing I notice is that there is no volume-adjustment icon/applet on the taskbar, and it doesn't seem to be among the choices  in the right-click menu...

Is that another module that must be installed?

---

### Post by wilberfan on 2006-11-19
I just reinstalled 'superkaramba' and the widget I started up has an ugly black non-see-through background (see attachment).   It looked great under the full kubuntu.

Is there something I need to install--or is there just a system setting I'm not seeing?

---

### Post by wilberfan on 2006-11-19
Crap.  Here's the screen capture.

---

### Post by aysiu on 2006-11-19
Honestly, I don't know. I'm not a sensei, and I never was. I'm still very much a grasshopper.

For the volume, you can try *kmix*. That may do it. Or maybe it's *kmixer*--I forget.

*kde-core* is definitely slimmer and faster, but the downside is you have to actually get to know the packages a bit and figure out which ones you need to reinstall afterwards.

---

### Post by wilberfan on 2006-11-19
> **aysiu said:**
> For the volume, you can try *kmix*. That may do it. Or maybe it's *kmixer*--I forget.

*kmix* would appear to be the correct answer here.

I've (temporarily?) gone back to the full kubuntu-desktop (!).   The fonts in Thunderbird looked TERRIBLE.  Wanted to see if the full install would fix it--it did.

---

