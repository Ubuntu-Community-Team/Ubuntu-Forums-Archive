---
title: "Figuring out what Ubuntu does under the hood"
date: 2009-06-18
forum: General Help
---

### Post by wacky_keyboards on 2009-06-18
In a related thread,

[http://ubuntuforums.org/showthread.php?t=1190316](http://ubuntuforums.org/showthread.php?t=1190316)

I asked about turning off the Ubuntu graphical login screen so that I could run my preferred window manager (CTWM).  (And a big THANK YOU to the helpful people out there who pointed me towards how to do this!!)  So this brings up the next step:  mimicking some of the stuff that Ubuntu does, without needing to invoke the GDM to get it.

In general, is there a way to poke around and see what applications are actually being invoked when a given menu option (e.g. System -> Preferences -> Keyboard) is chosen, or when a given icon (say the Network Manager applet) is left- or right-clicked?

I picked these 2 examples in particular because I've noticed 2 issues when NOT logged in under the GDM:

1.  I don't get my preferred key delay time or repeat rate, which I set when I'm logged in using GDM (or even at the text console prompt).  I tried using "kbdrate" but that doesn't go fast enough for my preference.  I've also tried "setq r rate" but that just issues an error message about an XFree86 extension not being available.  So what is it that's used by Ubuntu when the GDM is running?

2.  I have verified that NetworkManager is started, even when I have GDM disabled, so it seems like I just need to know how to interface with it from the command line in order to use its services.  (Or, I could launch a GUI if one exists that doesn't require GNOME.)  Does anyone know what this might be?

Thanks!
2.

---

### Post by t4thfavor on 2009-06-18
launch the WM from the commandline using ctrl+alt+F1 ann screen, then reconnect to it from a terminal window after its loaded. There may also be commandline options that will give you more/less info about the process. 

Please not I have never tried it, but it does sound very plausable.

---

### Post by aysiu on 2009-06-18
GDM and window managers are completely independent. GDM is the login screen thing.

Are you perhap confusing GDM with Gnome (the desktop environment)?

Network manager starts with ```
sudo /etc/init.d/NetworkManager start
``` and the little applet starts with ```
nm-applet --sm-disable
```

---

### Post by wacky_keyboards on 2009-06-18
t4thfavor:  I'm not sure what you mean with your suggestion.  If I have GDM running, then I know that I can use ctrl-alt-f1 to obtain a text window.  (Actually, it'll give me a text-console login prompt.)  Are you suggesting I log in, and then invoke my window manager (CTWM)?

Thanks!

---

### Post by wacky_keyboards on 2009-06-18
aysiu:  my apologies for misusing nomenclature, as it is a little confused in my head.  B-)  You are correct:  I am confusing GDM with Gnome.  Let me clarify my first posting.

Previously, I used the default provided by the Ubuntu installation.  That meant being presented with a GDM-based (X) login screen.  When I log in, Gnome is fired up, along with lots of applets and other things.  This gives me certain functionality, like changing the keyboard repeat rate or interfacing easily with the NetworkManager.

I have since disabled GDM, so now I log in through a text login screen, like they used to do on those old terminals.  B-)  I start up my favorite vintage-1990s window manager, CTWM.  It's at that point that I want to recreate some of the functionality, but I don't know how to do that.

With the specific command that you gave, namely

nm-applet --sm-disable

what should I expect to see?  I do not see any icons or windows appearing when I invoke it.

Thanks!

---

### Post by aysiu on 2009-06-18
I see. So you've disabled both GDM *and* Gnome.

If your new window manager has a system tray or notification area, you should see the network manager applet that allows you to click on it and select a wireless network.

Oh, and the command for the keyboard preferences is ```
gnome-keyboard-properties
```

---

### Post by wacky_keyboards on 2009-06-18
aysiu:  you are correct.  I disabled BOTH GDM and Gnome.

The keyboard preference command (gnome-keyboard-properties) worked perfectly!  (I wonder what mechanism it uses?)  The only glitch is that it brings up an options window each time.  It does have an "--apply" option, which is supposed to apply the settings and quit, but this still brings up the options window.  It would be nice not to need to deal with that.

My new window manager (CTWM) does not have either a system tray or notification area, so I don't see the applet.  However, your keyboard suggestion helped me find an alternative:  the Gnome panel itself (using "gnome-panel")!  This provided a place for the NetworkManager applet to attach (it attaches to the "top" panel).  In addition, because the panel is seen by CTWM as just another X application with a couple of windows, I can place them wherever I want, in whichever desktop I want (so that they don't clutter up all my desktops)!  As long as the Gnome panel ONLY provides a place to attach applets (and doesn't, for example, launch a bunch of other "support" applications), then this sounds like a good compromise!

Thanks!

---

### Post by coffeecat on 2009-06-19
I don't know whether you need this now, but I'll answer this one.

> **wacky_keyboards said:**
> In general, is there a way to poke around and see 
what applications are actually being invoked when a given menu option (e.g. System -> Preferences -> Keyboard) is chosen, or when a given icon (say the Network Manager applet) is left- or right-clicked?

Yes, so long as you can still log in to Gnome to get the particular command that you want to use in CTWM.

For most apps, right-click on the Applications menu in the gnome desktop and select 'edit menus'. Right-click on the app you want to check and select 'properties'. Under 'command' you'll find the terminal command you need in order to invoke it.

For apps that are started when gnome is started (such as Network Manager), go to System > Preferences > Startup Applications. Highlight the one you want to check, click on 'edit' and again the command is in the command field.

---

### Post by wacky_keyboards on 2009-06-19
coffeecat:  Actually, I *did* still need to know this.  Thank you very much!!

By the way, here's an example of menu option names changing between Ubuntu versions:  to obtain the startup applications under Intrepid Ibex (8.10), it's System > Preferences > Sessions, and then the Startup Programs tab (which is selected by default).

---

