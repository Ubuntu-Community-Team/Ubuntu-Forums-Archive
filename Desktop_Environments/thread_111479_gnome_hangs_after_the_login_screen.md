---
title: "gnome hangs after the login screen"
date: 2006-01-02
forum: Desktop Environments
---

### Post by almostlinux on 2006-01-02
Till yesterday i didn't have any problem ...and today it won't go past the login screen !

after  i login ... it's a blank red screen (with my mouse pointer) 


i tried failsafe gnome: no luck

i went into command line mode and typed 'startx' and it said something like:

```


no user profile 

creating a new /home/pradeep/.servercofig.7349

user not authorized to startX 
Exiting

```


what could be the problem? :confused:  

HELP !

---

### Post by shin on 2006-01-02
Dont start by startx.
Use sudo "/etc/init.d/gdm stop" then "start" or "sudo killall gdm", "sudo gdm".
Check dmesg and /var/log/Xorg.0.log. Probably some app is the problem. There should be some informations about it.

You can always try:
sudo mkdir /home/temp
sudo mv ~/* /home/temp/

And check if now gdm will start. If yes - find out which settings are the problem and fix them.

---

### Post by almostlinux on 2006-01-03
[QUOTE=shin]Dont start by startx.
Use sudo "/etc/init.d/gdm stop" then "start" or "sudo killall gdm", "sudo gdm".
Check dmesg and /var/log/Xorg.0.log. Probably some app is the problem. There should be some informations about it.

You can always try:
sudo mkdir /home/temp
sudo mv ~/* /home/temp/

And check if now gdm will start. If yes - find out which settings are the problem and fix them.[/QUOTE]

when i start gdm it takes me back to the login screen ! and it hangs after the login

I didn't see any error messages in Xorg.0.log

These were the last few lines of 'dmesg':

```

[4295242.438000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[4295242.441000] [drm] Initialized i915 1.2.0 20040405 on minor 0: Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller
[4295242.441000] mtrr: base(0xd0020000) is not aligned on a size(0x300000) boundary

```

---

### Post by almostlinux on 2006-01-03
here's something i found again from the dmesg:

```

[4294793.963000] mtrr: base(0xd0020000) is not aligned on a size(0x300000) boundary
[4294816.488000] NET: Registered protocol family 10
[4294816.488000] Disabled Privacy Extensions on device c02eb280(lo)
[4294816.488000] IPv6 over IPv4 tunneling driver
[4294826.997000] eth0: no IPv6 routers present

```

could this be a problem coz of the networking...?

---

### Post by art on 2006-01-03
I don't know what /home/pradeep/.servercofig file is suposed to do, but I would think it might be the cause of the problem. Are you running a server?

---

### Post by almostlinux on 2006-01-04
no i'm not running any server...

is there a way i can re-install just the gnome desktop again (without losing out any settings?)

---

### Post by steve.horsley on 2006-01-04
Gnome is a bit of a mess - it scatters config files all over the place. The easiest thing is to rename your home directory and make a new empty one. Use alt-ctl-F1 to get a console, log in and do this:
```
cd /home
sudo mv pradeep pradeep-old
sudo mkdir pradeep
sudo chown pradeep:pradeep pradeep
```
Now you should be able to log in with the gui (hopefully) and drag all your stuff (but not the gnome rubbish) back into your new folder.

---

### Post by axrj on 2006-01-04
I don't know if this could help you...

This happened to me several times, each time after a kernel update. I had nothing to do to fix it, the desktop has been loaded as usual after two or three minutes of wait.

But this happened after a fresh install of Breezy as there is a post-install notification, then an update... which does not seem to be your case.

---

### Post by almostlinux on 2006-01-04
@steve.horsley

i did exactly what you said... still won't work ... i guess it's some program failing to load after the login ? 

@ axrj 
there were no updates or anything and i've waited for over 5 minutes :)

---

### Post by almostlinux on 2006-01-05
bump! i'm still stuck ... it's been 3 days since i  logged into my ubuntu :(

---

### Post by Mustard on 2006-02-09
It sounds like your .Xauthority file has changed ownership to 'root' from the sounds of the symptoms.  It's a file in your $HOME directory, that sometimes gets corrupted when users run graphical apps from terminal without using gksudo instead of sudo.

---

### Post by nanotube on 2006-02-09
and have you by any chance played with your firewall recently?
i once accidentally disabled all loopback traffic, and that caused gnome to hang on login...

---

### Post by nascent16 on 2006-02-13
I am having the same issue. It appears in the Xorg.0.log that the DRIScreenInit function of the fglrx driver for ATI is the culprit. I'll keep you updated on what it takes to fix it.

---

