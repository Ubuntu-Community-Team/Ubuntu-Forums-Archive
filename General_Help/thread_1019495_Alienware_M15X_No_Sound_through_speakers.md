---
title: "Alienware M15X No Sound through speakers"
date: 2008-12-23
forum: General Help
---

### Post by kdaemon on 2008-12-23
I have had this issue of sound through headphone jack but not the system speakers with Ubuntu, Kubuntu, Fedora, Mandriva etc and have read all the stuff I could find through google and on these forums but is there a better fix than changing the model options in /etc/modprobe.d/alsa-base?

Adding: options snd-hda-intel model=mbp3 to the alsa-base file switches the sound from the headphone jack to the speakers but this is hardly a fix, having to edit this file and re-load ALSA everytime you want to change from jack to speakers and back is a pain. I played with various other options and found the following to work:

options snd-hda-intel model=lenovo-101e

Adding the above options line to /etc/modprobe.d/alsa-base works in that the sound switches from speakers to headphone jack when the jack is inserted and switches back again when removed. I suppose then that it works as intended in that the headphone jack is auto sensing but ALSA is still using the wrong drivers and stuff so this is more of a bodge than a fix.

Does anyone know if the Realtec ALC889A is supported by ALSA or is this something I just have to wait to be fixed?

---

### Post by kdaemon on 2008-12-26
OK, I've abandoned all hope in getting Ubuntu/Linux to work on the Alinenware M15X, too much doesent work and it runs like a dog when running Linux, it even runs slower than it does when running Vista which is some going!

Decided to go back to my old laptop a Toshiba Satelite Pro U200 and guess what, also uses Intel HDA sound and im right back to square 1 looking for options for the alsa-base file, this is starting to suck, when your spending more time trying to get your system to work than you are productivly using your computer then it is time to dump it and move on.

Does Ubuntu/Linux/Sound work PROPERLY with any laptop currently in circulation (and worth owning so no 486 spec'd machine)? Is there a machine out there that I can install Ububntu (or other distro) on and everything work as it should? Or do the ppl (whoever) @ Ubuntu/Alsa intend to fix this?

Any help/advice will be much appreciated!

---

### Post by jguillory on 2009-05-02
Good news on the m15x front...

I've just recently installed Ubuntu 9.04 - the Jaunty Jackalope (64bit) on my m15x.

Noticeable things that don't work:
a.  Light pipes (all of them).  As in another posting, I set them to the colors I wanted while
     Vista was installed and then removed that system.

Intermittent things:
a.  Shutdown/Reboot.  Every once in a while the m15x seems to hang, with the screen
    blank and the light pipes on.  I've had to hold the power switch down for 4 seconds and
    the system will shutdown.  Boots back up fine with no problems (so far)
b.  Has only happened once (unlike in windows).  Upon booting into the system, no net
     card was found.  Wireless worked ok though.  Had to reboot to see card again.  I
     believe that this is definitely a hardware issue.

Things I haven't tested (will get back to it)
a.   Hibernation.
b.   Sleep.
c.   Stealth.

Things that work:
a.  Sound:  after reading the above post kdaemon and applying his addition to the alsa
     conf file, my sound card seems to work great!  With headphones and without.  Nice!
     Thanks kdaemon. 
b.  Video:  blazing fast after I have downloaded an applied the nVidia update version
     180, and rebooted the machine.  Patch is easily applied using the Synaptic Package
     Manager.
c.   Bluetooth, wireless, net adapter, touchpad, usb ports, etc...


Performance issues that people have spoken about are not seen in this version of Ubuntu and I can say that I am totally impressed with my sweetheart of a laptop again!
Goodbye Vista.  Catcha in the nether!

If you guys are wondering...all this was done by a total noob!  I haven't been within the linux realm since I installed Red Hat on my IBM1412 laptop in 1997.  I'm glad I chose Ubuntu.  It's great to be here.

---

### Post by smite_of_bloodstone on 2013-01-04
Adding
options snd-hda-intel model=lenovo-101e
to /etc/modprobe.d/alsa-base.conf

had been working great for me using my M15x

After installing Ubuntu 12.10, this no longer seems to do it.
Does anyone know the foo required to get this working again?

---

### Post by lisati on 2013-01-05
A lot can change in 3 years; it might be a good idea to start a new thread, with a link back to this one if required.

Old thread closed.

---

