---
title: "[SOLVED] gnome-compiz-manager broke Compiz setup"
date: 2008-04-12
forum: Desktop Effects &amp; Customization
---

### Post by kutjara on 2008-04-12
I've been running Compiz-Fusion (most recently version 0.7.4)  pretty successfully for the past few weeks on my Acer Aspire 4315 laptop with Intel 960 chipset and X3100 graphics. Then tonight, I was browsing through Synaptic and discovered a little package called Gnome Compiz Manager, which promised to give me a gnome-panel icon with which to turn Compiz on and off, as well as a small configuration utility. Being the kind of guy who likes to play with new gizmos, I duly installed the package (which brought with it a gnome-compiz-manager library).

When I rebooted my machine, however, I found that my CPU was running at 100% utilization, even when it was doing nothing. I ran top and found that compiz.real was using 90%+ of my CPU. The only way to fix things was to kill compiz.real. This situation persisted through numerous reboots and an attempt to fix things via the GUI for gnome-compiz-manager (called GLDesktop).

When these efforts failed, I decided to uninstall gnome-compiz-manager (and the library dependency). Unfortunately, this didn't fix the problem. Compiz.real was still using up nearly all of my CPU. The only problem was that now, I couldn't kill compiz.real, because (according to the error message) my display was already using a window manager, which I should probably change using the --replace command. While ordinarily good advice, what I wanted was compiz.real killed, not a lecture in WM switching.

I finally gave in, replaced Compiz with metacity, and then completely uninstalled Compiz-Fusion. Now my system is running normally again (albeit without the lovely desktop effects).

Has anyone else encountered this problem? I'm prepared to reinstall and reconfigure Compiz, but I'm concerned that gnome-compiz-manager has hidden some config file somewhere that'll reach out and bite Compiz again the second I reinstall it. I'd be grateful for any advice, because I love what Compiz can do and would very much like to have it back, but not if all it does is burn up my CPU.

---

### Post by Zorael on 2008-04-12
Curious.

You could try Synaptic's "completely remove" or Adept Manager's "purge" option on the gnome-compiz-manager and compiz packages. Also delete your Compiz settings. The directory with your compiz settings is called .compiz and resides in your home directory. The prefixed dot makes it hidden, so you need to make sure your file manager displays them (or ls -a).

The terminal way would be:
```
$ sudo apt-get autoremove --purge compiz* libcompiz* emerald* libemerald* libdeco* gnome-compiz-manager* libgnome-compiz-manager*
$ rm -r ~/.compiz
```

Then reinstall, either through a GUI package manager of choice or through the terminal.

Lastly, doesn't starting metacity automatically kill compiz.real?

---

### Post by russo.mic on 2008-04-12
I would examine your driver installation.  are you using XGL or AIGLX?  if your using XGL did you turn off direct composite in xorg.conf?

Let me know and I'll try and steer you in the correct direction if I can!

Russo

---

### Post by kutjara on 2008-04-12
> **Zorael said:**
> Curious.

You could try Synaptic's "completely remove" or Adept Manager's "purge" option on the gnome-compiz-manager and compiz packages. Also delete your Compiz settings. The directory with your compiz settings is called .compiz and resides in your home directory. The prefixed dot makes it hidden, so you need to make sure your file manager displays them (or ls -a).

The terminal way would be:
```
$ sudo apt-get autoremove --purge compiz* libcompiz* emerald* libemerald* libdeco* gnome-compiz-manager* libgnome-compiz-manager*
$ rm -r ~/.compiz
```

Then reinstall, either through a GUI package manager of choice or through the terminal.

Lastly, doesn't starting metacity automatically kill compiz.real?

Even though I previously used Synaptic to remove Compiz, it didn't completely remove everything. When I used the purge command, another dozen or so files were zapped.

After purging everything with compiz in the name, I rebooted, made sure everything was working correctly and that there were no untoward entries in any log files, and then reinstalled the latest version of Compiz using Synaptic. The second I typed compiz --replace, however, CPU usage shot up to 100% and I was back where I started. Only reverting to metacity gave me back control of my PC.

At this point it looks like the only option I have is a full reinstall of Ubuntu. It's either that or hunt through every graphics-related file on my system, trying to figure out what gnome-compiz-manager did. I'm going to be doing a fresh install of the release version of Hardy on the 24th, so I guess I'll stick with a standard desktop till then.

Thanks for the suggestion, though. I hadn't used the purge command before, so it's very nice to have that in my small but growing Linux toolbox.

Edit: To answer your question, yes switching to Metacity did kill compiz.real, but it was back the next time I booted, sucking up every resource it could find. Indeed, switching to Metacity was the only way I could find of killing compiz.real long enough to uninstall the Compiz packages.

---

### Post by kutjara on 2008-04-12
> **russo.mic said:**
> I would examine your driver installation.  are you using XGL or AIGLX?  if your using XGL did you turn off direct composite in xorg.conf?

Let me know and I'll try and steer you in the correct direction if I can!

Russo

Thanks russo.mic. I haven't really investigated my driver setup because, up to now, I haven't had any problems with graphics. I'll definitely look into it now, though; this little problem has piqued my curiosity, and I'd like to get to the bottom of the negative interaction between compiz.real and gnome-compiz-manager.

When I type compiz --replace, I get a line telling me that XGL isn't present. I experimented by installing the xgl version of X-server, but that slowed my glxgears framerate from 750fps to around 200. It also didn't fix the compiz.real problem.

---

### Post by kutjara on 2008-04-12
Update:

I finally figured out how to fix this (actually, a kind soul on the Compiz-Fusion forums knew and told me - thanks crdlb!). It was a simple matter of running the ccsm (compizconfig-settings-manager) application, going to the Preferences tab, and selecting "reset to default" under the Profiles heading. This immediately fixed whatever it was that gnome-configuration-manager broke.

CPU utilization is now down to sensible levels (2% at idle), and compiz.real doesn't even appear in top anymore. I'm a happy Compiz-using camper again.

---

