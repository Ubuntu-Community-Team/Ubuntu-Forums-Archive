---
title: "Can't go into X or Gnome or KDE"
date: 2007-03-06
forum: Desktop Environments
---

### Post by kuriharu on 2007-03-06
I can't get my system to run X. When it starts to open X, I get an error that says "X failed to start. Do you want to view the log?". I say Yes, then I get a blank log (it's at 100% with no text). 

When I try to run fglrxinfo, I get "Can't open display 0". When I try kdeinit, I get "Can't open, $DISPLAY isn't set.".

I've set the /etc/X11/xorg.conf to use vesa or ati as a driver, but still no dice. Anybody have any clues.

---

### Post by ComplexNumber on 2007-03-06
during the last time that you logged into gnome or kde successfully, did you do any of the following:
-updated your video drivers?
-changed the xorg.conf manually? is so, what exactly did you change?

---

### Post by kuriharu on 2007-03-06
Thanks for the reply.

Long story short, I tried upgrading from Dapper to Edgy. Naturally, it didn't work, and then XGL wouldn't work. Gnome and kDE were fine, but Xgl/Beryl were messed up. Rather than leave good enough alone, I decided to fix fglrx.

When I ran fglrxinfo, it was using Mesa, not the ATI drivers. I tried to reinstall fglrx, but there were tons of dependencies that apt-get wouldn't install. In the process of trying to reinstall fglrx, there were tons of files that had to be uninstalled. I saw fglrx among them but it wasn't until it was running.

I've tried reinstalling fglrx but no luck. And I've tried the ati and vesa drivers in xorg, but no dice. No matter what, I can't get X to run.

Any ideas of where I should start? My data's intact, but if I don't have to reinstall from scratch that would be nice.

---

### Post by kuriharu on 2007-03-07
I still can't go into x, though I've made some progress.

I managed to install the ati driver. I did this by doing an apt-get dist-upgrade, then manually uninstalling each package that errored out. This took a LONG time, but it seemed to work.

I typed Xorg at the prompt, and I saw the X screen with the cursor, but that's as far as it went. I rebooted and typed gdm and my screen went blank.

Any hints?

---

### Post by kuriharu on 2007-03-07
Okay, no suggestions. Typical of the forums. One reply if you're lucky, and that's about it.

I'll probably reinstall. I gotta say, Linux on the desktop sucks. Windows is definitely more repairable and doesn't break when you try to do an upgrade like this. 

Linux on the desktop is ridiculous.

---

### Post by freebird54 on 2007-03-07
You must have amazing luck with Windoze - there have been multiple times I had to multiple consecutive re-installs of Windoze to get something to not work very well.  Since 3.11 it has been harder and harder to fix things when they screw up - it can take hours of registry pruning, and re-installing apps to get things back to normal - and sometimes you have to go to bare metal even after everything else.

As to your problem - I think your best bet is to get the system running, THEN fglrx, THEN xgl - THEN Beryl.

For the mesa driver thing you could try this

```
mkdir -p /usr/X11R6/lib/modules/dri
ln -s /usr/lib/dri/fglrx_dri.so /usr/X11R6/lib/modules/dri 

```

or search the Beginners forum for reference to stopping a built-in AGP driver that is not needed with fglrx running..

good luck!

---

### Post by kuriharu on 2007-03-08
Thanks for the tip, I'll try that.

Thanks for putting up with my rant. I'm pretty exhausted. It's been a long 5 days since my install went south. And I've had bad luck with Windows, too, but most versions of Windows will let you reinstall without reformatting, which I've done on numerous occasions to remedy this kind of situation.

I'll post results here in a few minutes.

---

### Post by kuriharu on 2007-03-08
No dice.

Any attempt at running fglrxinfo gets "Could not open display :0" and that's it. GDM, kdeinit, startx, nothing works.

I'll just reinstall. Most of the data is backed up. Is there any way to get a list of all installed programs? It's gonna be tough to have to go through EVERYTHING again.

---

