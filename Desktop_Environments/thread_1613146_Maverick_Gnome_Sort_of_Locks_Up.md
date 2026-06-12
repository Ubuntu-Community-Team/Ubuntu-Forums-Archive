---
title: "Maverick Gnome Sort of Locks Up"
date: 2010-11-04
forum: Desktop Environments
---

### Post by Pater Phil on 2010-11-04
I've been a Linux Desktop user since 2002, using almost every major distribution at some point until settling on Ubuntu 7.04. I really liked Ubuntu at first. I have it running on my desktop, laptop, MythTV boxes, wife's netbook, dad's machine, mother's machine, servers at work and home. After my experience with Maverick on my laptop, I will probably be switching to something else. It seems that every release is more problematic. To me, it seems there is such a rush to dumb things down, that releases are actually betas, and I am tired of the frustration.

OK, I have a Dell Latitude D510. Single-boot machine, with the entire hard drive devoted to Ubuntu. The graphics chip is an ATI RS690M (x1200 series), and I have 2GB of RAM. Lucid (AMD64) was installed and working fine with Compiz enabled.

For kicks, I did an in place upgrade to the unperfect 10.10. I never managed to successfully login to Gnome (my preference). After credentials were entered, the gnome-session would start, and then halt even before the panels were drawn.

I did a fresh install. When I tried to login, same problem. I did a fresh install of the 32-bit version, and same problem. Switched to a text console, discovered aptitude was no longer installed by default (this frosted me to no end), installed aptitude, and updated the system. Still unable to login. 

I then tried a safe-mode session. Successfully logged in. However, as soon as the screensaver started, I started having issues. When I entered my password, the screensaver kept the screen occupied. The mouse would register, but nothing happened. I could still switch consoles, but never could get X moving again.

I did a fresh install of AMD64 again, and could not login. Went to safe-mode session, logged out, and tried logging into a regular session. Success until the screensaver activated. Same problems as before. Tried going to a different screensaver, did a preview, and bam, unable to close the preview. Mouse works, can partially view the desktop, cannot access any other programs, but can access other consoles. Killed X.

Disabled screensaver. Next, I tried opening Synaptic for the hell of it, and gksudo hangs. At the same time, mouse is moving, but no clicks register, I can't switch between windows. I can access other consoles. top shows nothing out of the ordinary. Kill X. 

Back in Gnome, everything seems to work for a bit, and then the desktop sort of hangs. Try switching to Metacity. Log out. Log in. Can't get to a desktop. Kill X. Log out. Log in to safe mode. It works. Log out. Log in to regular session, can't finish logging in. From console, I switch back to Compiz. Kill X. Voila, I login in again. I open Firefox. I can open Synaptic no problem using sudo from a bash Window. No error output. A few minutes later, the desktop locks up again. 

Switch to console, kill X, and install kubuntu-desktop. Try logging into KDE session. Splash screen gets to the first icon, and then nothing changes for ten minutes. No hard disk activity, nothing. Kill X. Try logging into KDE session. Success. KDE is has been working fine. Still can't get into Gnome. 

I have spent about 6 hours searching for something relevant. I can't find anything for Maverick. I have reached my absolute tolerance limit. I don't even have any idea how to begin tracking the problem down, because I have never encountered anything like this (partial lock-up). Honestly, I have never had difficulty with X or Gnome, and so I am not really sure where to look for debugging information. dmesg output seems normal. 

Any help is appreciated, but I am thinking hard about going to another distro that is not connected to Ubuntu. Again, I am really becoming disappointed with what appears to me to be diminishing quality control. The sad thing is, I still really prefer the Ubuntu community to any other.

-Pater Phil

---

### Post by P4man on 2010-11-04
press control alt+f1, log in, type

dmesg

and see if that sheds  some light on the issue. Alternatively, check out the logs in /var/log/

---

### Post by Pater Phil on 2010-11-04
I checked dmesg again. I don't note anything indicating an error. Per your suggestion, I looked through all of the logs and did not note anything throwing an error other than a mysql-apparmor conflict (I believe from installing mysql). 

I spent 14 hours up in KDE without any issues. Logged out and then back into a Gnome session. The music plays, and then progress halts. Kill X, then tried logging into Gnome again. Success. I opened screensaver and did a preview for blank screen. The screen doesn't blank, and the preview buttons are inaccessible but viewable after the cursor crosses them. Still cannot focus anywhere on the desktop. 

I then read through all the logs and dmesg. Nothing indicated.

I'm not saying Gnome is the problem, but whatever is causing this, Gnome seems to be a prerequisite. I don't know if is a compositing problem or what.

Thanks for the assistance so far.

-Pater Phil

---

### Post by P4man on 2010-11-04
actually, yeah that does make sense. It could be a compositing issue. after restarting X, if you run

```
compiz --replace
```

Does compositing (desktop effects) work then? If it doesnt, then you probably just have to turn off desktop effects in system>preferences>appearance or solve the videodriver issue you are having. What videocard and drivers do you have?

---

### Post by Pater Phil on 2010-11-04
I am using the radeon driver. I've already done the compiz --replace, metacity --replace, etc. I had not thought about changing the effects settings. I will do so next.

Turned the machine off for a while. Came back and logged into Gnome. Tried to open Synaptic from the menu. As soon as gksudo starts, everything sort of locks-up. I immediately checked all of the logs, and there is nothing.

Do you know of a way to check compiz output?

-Pater Phil

---

### Post by Pater Phil on 2010-11-04
Okay, I disabled all effects. I now cannot seem to lock it up. So now I am wondering if it is driver or compiz related. Either way, it is frustrating that what was working no longer is. 

Okay, the hardware is cheap. I have a personal preference for AMD CPUs, and nVidia or Intel was not an option with an AMD processor when I bought this laptop. Still, the machine is Aero capable and only about 2.5 years-old. So I sort of don't expect the problem.

I use animation on the desktops, but keep Compiz limited to aesthetic uses only on the laptop. Still, I want it to work. 

I know I'm not going to buy another laptop unless the graphics are nVidia. For my tastes, there are too many different families of AMD/ATI GPUs, and support for mine was dropped less than a year after I bought it. Worse, motherboards with the same chip were still being manufactured even after driver support ended. So that is an AMD issue.

Now I also have a Mac Mini. I bought it for the aesthetic and the form factor. Lucid will remain on there, or I'll switch to another distro. I've already read that you cannot boot an EFI platform from the CD. Perhaps I'll consider installing from USB.

Enough ranting. Thanks for the help so far. Next up is filing (a) bug report(s).

-Pater Phil

---

### Post by P4man on 2010-11-04
You could also try the opensource drivers. They arent that bad these days.

---

### Post by waynefoutz on 2010-11-04
I have a Dell Latitude D531, pretty much the same all AMD/ATI hardware. Mine has the Radeon Mobility x1270.  I had pretty much the same issue with Maverick. The live CD booted up fine, but once I installed it I couldn't get past the purple splash screen. I got the startup sound, the mouse pointer, on a splash screen...no desktop. I was upgrading it from Hardy (8.04.) I finally gave up and put Lucid on it, which is probably for the best, since I prefer LTS versions anyway. But I never did figure out why it wouldn't start the desktop.

---

### Post by Pater Phil on 2010-11-05
I'm already using the radeon driver. The proprietary driver doesn't support the chip, and I have not had a positive experience with it on other AMD/ATI cards. I don't really think the radeonhd driver provides much of an option. 

Seems to me the issue is between the driver and compiz. I'm looking at options now.

---

### Post by Pater Phil on 2010-11-05
There was already a Launchpad bug report filed. 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/665991]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/665991")

---

### Post by Pater Phil on 2010-11-06
I have been playing around a bit. It seems that kernel mode-setting (KMS) may be the culprit, or a conflict between KMS/radeon driver/Compiz. I disabled KMS, turned Compiz back on with effects, and have been unable to produce a freeze.

To disable KMS, edit [FONT="Courier New"]/etc/default/grub[/FONT].
```
[FONT="Courier New"]sudo nano /etc/default/grub[/FONT]
```

Then add [FONT="Courier New"]nomodeset[/FONT] to [FONT="Courier New"]GRUB_CMDLINE_LINUX[/FONT].

```
[FONT="Courier New"]GRUB_CMDLINE_LINUX_DEFAULT="nomodeset quiet splash"[/FONT]
```

Then update GRUB and reboot.
```
[FONT="Courier New"]sudo update-grub
sudo reboot[/FONT]
```

---

### Post by infroger on 2011-01-25
Have a D531 and had the very same problem after installing Maverick. 

Disabling KMS as suggested by Pater resolved it!

Thank you very much!

Regards,
Roger

---

