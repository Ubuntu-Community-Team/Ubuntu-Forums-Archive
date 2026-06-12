---
title: "eject CDROM w/ eject button - I know, the novelty..."
date: 2005-12-30
forum: Desktop Environments
---

### Post by endtransmission on 2005-12-30
can someone tell me how to (or where to look to) configure it so when I hit the eject button on my cdrom drive, the disk freaking ejects?

I've just setup a MythTV box for the home livingroom and this is the last lingering thing.

Using a standard ubuntu-gnome desktop - pretty stock.

---

### Post by Bou on 2005-12-30
AFAIK there's currently no way to do that: you have to go to computer:///, right-click the device and select eject device.

I would love it if somebody proved me wrong, though.

---

### Post by Perfect Storm on 2005-12-30
I can recommend using **disk mounter applet** for easy mount and eject.
Right click your panel, and pick **add to panel** and find disk mounter applet.

---

### Post by agheba on 2005-12-30
under keyboard shortcuts (system -> preferences) you will find "eject". I don't know if you can use the eject button on the drive, but you can use another key...

---

### Post by az on 2005-12-30
Here at work, I can still crash this up-to-date windows box by ejecting the cdrom when it is reading.

There are kernel patches (supermount) which allow you to eject a cd upon pressing the button, but they all can make your kernel crash.  There seems to be no solution to this hardware issue other than integrating every application which can use a cdrom drive to unmount it after a few seconds of inactivity.

---

### Post by MetalMusicAddict on 2005-12-30
This is very weird. Ive seen this mentioned alot but have never run into it. Unless the disk is being read Ive always been able to eject the disk from the button on the drive.

---

### Post by jeffreyvergara.NET on 2006-01-03
there's a lot of thread like this... anyways try:

sudo sh -c 'echo "dev.cdrom.lock=0" >> /etc/sysctl.conf'

---

### Post by Rinzwind on 2006-01-03
[QUOTE=MetalMusicAddict]This is very weird. Ive seen this mentioned alot but have never run into it. Unless the disk is being read Ive always been able to eject the disk from the button on the drive.[/QUOTE]

2 possible ways:

- Mount as root in CLI. Unmount as user should not be possible.

- Mount from CLI and cd to the mountpoint. Hitting the eject button should result in drivebay not opening (busy error). 

(2 wild guesses).

---

### Post by neighborlee on 2006-01-04
[QUOTE=jeffreyvergara.NET]there's a lot of thread like this... anyways try:

sudo sh -c 'echo "dev.cdrom.lock=0" >> /etc/sysctl.conf'[/QUOTE]

that is correct, and afaik it is to be made stock in next release of ubuntu.

cheers
nl

---

