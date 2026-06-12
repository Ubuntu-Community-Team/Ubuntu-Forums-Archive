---
title: "Display no longer goes to standby in Karmic"
date: 2009-11-13
forum: Desktop Environments
---

### Post by ScottMinster on 2009-11-13
I recently upgraded to Karmic, and one of the bigger annoyances I've found is that the display stays on all the time -- it no longer goes into DPMS standby (or whatever it's called).  I can force it to go into that mode if I manually run `xset dpms force standby', but I'd like it to be automatic.

My current power management settings have the "Put display to sleep when inactive for" set to 10 minutes.  It was an hour, but I changed it in case the setting was lost for some reason in the upgrade.  But that didn't work -- it will still have the screen saver running even after sitting all night.

Besides wasting power, it's annoying because some screen savers take a lot of CPU, which force the CPU into a higher frequency, produce more heat, and cause the laptop's fans to kick on (the ability to choose which screen savers to run like we had in xscreensaver would be nice, but that's another topic).

So, any ideas what might be stopping the DMPS standby mode?

---

### Post by Kushkah on 2009-11-13
Bump, same problem, haven't found a fix yet :(

---

### Post by OrangeCrate on 2009-11-16
Le bump...

My preferred setting, is a blank screensaver at 30 minutes, and the display goes to sleep at one hour.

When set-up,  it works for the current session only, but, though the screensaver still works, it loses the sleep setting after the computer has been shut down.

I've spent some time searching for a workaround, but haven't found anything. Unless someone can point us to fix, here's hoping for a solution to show up in the updates soon...

---

### Post by OrangeCrate on 2009-11-16
Adding to my post ^

-----

After reading through the fairly lengthy list of bugs associated with the Gnome screensaver, I decided to just get rid of it, and replace it with the Xscreensaver package. If anyone is interested, here's the quick way to do this:

1. Open Synaptic, and install the xscreensaver package.

2. While there, uninstall the gnome-screensaver package.

3. Go to Preferences > Startup Applications, and add the following instruction to your startup list:

Type in a title of your choice. I just used Xscreensaver.

The command is, "xscreensaver -no-splash" (without the quotes).

Add a description, if you like, and you're done.

Reboot, then go to System > Preferences > Screensaver, and you'll see the xscreensaver dialog.

On the first page, you choose your screensaver. Personally, as I said, I prefer a blank one at 30 minutes, so I left the Mode at "Blank Screen Only", and I set "blank after" to 30, and change the "Cycle After" to 0 (it's a number, not a letter).

On the advanced tab, I set "Standby After" to 60 minutes, and I changed the other options, "Suspend After", and "Off After" to 0.

(If you want more screensavers, look through the xscreensaver packages in Synaptic.)

And that's that, it works just fine.

:)

-----

Everything a person would ever want to know about Xscreensaver is located here:

> For many years, GNOME shipped xscreensaver as-is, and everything just worked out of the box. Recently, however, they've been re-inventing the wheel again in the form of "gnome-screensaver"...

[http://www.jwz.org/xscreensaver/man1.html](http://www.jwz.org/xscreensaver/man1.html)

---

### Post by ScottMinster on 2009-11-18
I figured out why my screen wasn't blanking in Karmic.  Way back (I think it was Intrepid), I found that gnome-power-manager wasn't remembering past battery discharge and charge rates (it thought it was a different battery each I (un)plugged the laptop).  So, I downloaded the source, hacked it a bit (not a real fix, just good enough for my use) and installed my own binary.  I guess enough had changed in g-p-m since Intrepid that my old hacked version no longer worked right :)

After disabling my hacked version, the screen blanks as expected.  I also have access to the newer power history dialog.  I just hope that it remembers my battery stats correctly in this version.

@OrangeCrate: interesting info on replacing gnome-screensaver with xscreensaver.  I don't know why Gnome had to go and ruin a perfectly good screensaver system.  I wouldn't be quite as annoyed with it if they at least implemented all the same options.  As it stands, there's no way to configure 90% of the screensaver options, including which screensavers are run.  I don't know why the Gnome leaders sanction things like that, but it's a clear pattern -- screensaver, broken session management, and recently the neutered login manager.  Of course, I'm still disappointed I cannot set different backgrounds on different workspaces, and I haven't been able to do that since Gnome 1.4!  Maybe I just need to switch to XFCE.

---

### Post by OrangeCrate on 2009-11-18
> **ScottMinster said:**
> I figured out why my screen wasn't blanking in Karmic.  Way back (I think it was Intrepid), I found that gnome-power-manager wasn't remembering past battery discharge and charge rates (it thought it was a different battery each I (un)plugged the laptop).  So, I downloaded the source, hacked it a bit (not a real fix, just good enough for my use) and installed my own binary.  I guess enough had changed in g-p-m since Intrepid that my old hacked version no longer worked right :)

After disabling my hacked version, the screen blanks as expected.  I also have access to the newer power history dialog.  I just hope that it remembers my battery stats correctly in this version.

@OrangeCrate: interesting info on replacing gnome-screensaver with xscreensaver.  I don't know why Gnome had to go and ruin a perfectly good screensaver system.  I wouldn't be quite as annoyed with it if they at least implemented all the same options.  As it stands, there's no way to configure 90% of the screensaver options, including which screensavers are run.  I don't know why the Gnome leaders sanction things like that, but it's a clear pattern -- screensaver, broken session management, and recently the neutered login manager.  Of course, I'm still disappointed I cannot set different backgrounds on different workspaces, and I haven't been able to do that since Gnome 1.4!  **Maybe I just need to switch to XFCE**.

That would be a nice choice. Over the years I've used both XFCE (Xubuntu), and E17 (OzOS) with xscreensaver, and if the truth be known, I've always preferred it to the Gnome option.

---

### Post by fostytou on 2009-11-20
My screen saver and monitor shutdown *were* working "fine" after initial install of 9.10 x64 with the nvidia drivers.  The only problem was that when I wanted to wake the screen up I would move the mouse and the monitor would come on, then have to move the mouse for another 2-3 seconds or click repeatedly for the screen saver to turn off.  My problem arose when I tried to just disable the screen saver (by de-selecting the check box in the screen saver window) and just have the monitor go to low power mode.  After this, nothing happened.

To start analysis I set the timing for the monitor power down to 1 minute and waited... nothing.  After a few tries, I noticed an error icon (that looked like a window-maximize option) in the top launcher near my pidgin notifier.  When I hovered on the area where it popped up and let the timer run through again I got a popup to this link:

[http://blogs.gnome.org/hughsie/2009/08/17/](http://blogs.gnome.org/hughsie/2009/08/17/)

It seems the 2 required fixed have been implemented at a top level, but need to be carried down to our distribution.  I'm not sure who can initiate these fixes.  I'm also not yet experienced enough to apply these patches, but would love to learn.  Who can get me/us on the right track?

Thanks!

P.S.  Note, I also tried re-enabling the screen saver and would simply get the screen starting to fade, then coming back up.

---

### Post by OrangeCrate on 2009-11-22
<deleted>

---

### Post by fostytou on 2009-11-23
Interesting....  It seems in my case that the power down on the monitor works as long as the screen saver is activated before it.  No screen saver when the timed event happens, no monitor turn-off.  If I set the screen saver to anything greater than the monitor power off time I get the screen saver, but no power off.

---

### Post by blueridgedog on 2009-12-03
> **OrangeCrate said:**
> 

Reboot, then go to System > Preferences > Screensaver, and you'll see the xscreensaver dialog.



No need to reboot:

```
$ killall gnome-screensaver
$ xscreensaver -no-splash &
```

---

### Post by sideburns on 2009-12-07
Personally, I use Fedora, but come here for help on my sister's Ubuntu box.  I've found from experience that if gnome-screensaver is installed, Gnome will start it at login, even if you've told it not to.  What works for me is to install xscreensaver, with all its extras, uninstall gnome-screensaver, change the settings in Sessions, log out, log back in and Bob's your uncle.  I'm sure killall will work, but I know that log out/log in does the job if you prefer not to use a terminal.

---

