---
title: "Printer installed but not according to HP-Toolbox"
date: 2009-05-05
forum: General Help
---

### Post by Bucky Ball on 2009-05-05
Hi all.

Bit of a nightmare really. I built a computer for my mother-in-law after christmas and was running sweet. She took it home and still running sweet but the HP CP1215 laserjet colour printer has for some reason started to malfunction. Why not just go over and fix it up? My mother-in-law lives about 750kms away!

So, we've been trying to fix it online and over the phone. She has been doing great. We've managed to uninstall and reinstall HPLip, run hp-setup and eventually installed the printer. According to hp-setup, it's good to go; correct device and bus # and fine.

Open System->HP-Toolbox and the printer shows up in the left column, but in the right pane is the message:

ERROR: No device found or unsupported device.

Try and print: nothing. In other words, we have hit a bit of a brick wall. Setup says the printer is installed, Toolbox says it is and isn't. No printing. Tried deleting the printer and in Toolbox going 'Device->Setup New Device' but that takes up back to the HP-Setup window (on her machine - oddly it takes me to a GUI Wizard on mine) and sets it up again to the same result and error message. Wondered if this was a permission problem but when you type:

sudo hp-toolbox

... in a terminal, same result. Doesn't matter if you launch as root or normal user.

Anyways, we are desperate for any help with this as this printer has been offline for 3 months and my M-I-L needs to use it pretty urgently by now and as you can imagine, is sick of trying to fix it. Good on her for the patience and persistence. She decided to try Linux after years of MS and loves it ... apart from this little hiccough! She has even been digging around in the console (with my instruction)!

Tnx in advance ...

:)

Just to add to the confusion, this site says to use foo2jz:

[http://openprinting.org/show_printer.cgi?recnum=HP-Color_Laserjet_CP1215](http://openprinting.org/show_printer.cgi?recnum=HP-Color_Laserjet_CP1215)

But this site from HP seems to give definite proof that it works with HPLip, and that is how I had it working when it left here:

[http://hplipopensource.com/hplip-web/models/color_laserjet/hp_color_laserjet_cp1215.html](http://hplipopensource.com/hplip-web/models/color_laserjet/hp_color_laserjet_cp1215.html)

---

### Post by Bucky Ball on 2009-05-08
Help!! (if you have a HP printer or any clue). :)

bump

---

### Post by Bucky Ball on 2009-05-18
Oh, well. Obviously no ideas from the world. I'll finish this up with ... I can't get my hands on to fix this from 750kms away, my mother-in-law is not exactly a coding guru (yet) and consequently is about to go back to windows. Oh well.

---

### Post by bumanie on 2009-05-18
Go [here]("http://hplipopensource.com/hplip-web/gethplip.html") and download the self extracting installer and try that. It has worked for me every time if there has been a problem with the 'native' installation.

---

### Post by Bucky Ball on 2009-05-20
Thanks but done it. My only suggestion to her is that she uninstall everything (re HP and printer, not Ubuntu!) and try again. This involves me trying to explain the ins and outs over the phone.

I think the problem is this is one of about 50 HP devices that need not just HPLip, but a HP plug-in needs to be installed as part of the process. Sounded over the phone like she did it right but thinking back, maybe we screwed that bit.

[http://hplipopensource.com/hplip-web/models/color_laserjet/hp_color_laserjet_cp1215.html](http://hplipopensource.com/hplip-web/models/color_laserjet/hp_color_laserjet_cp1215.html)

This page stresses that plug-in is required and is not part of the HPLip tarball, but doesn´t tell you where the hell you get it from or what it&#347; name is to search for it! Hmmm ...


Thanks again.

ps: you´re not in Geelong by any chance, bumanie!? :)

---

### Post by Bucky Ball on 2009-05-21
I did a little more searching last night and fluked on a site that tells me to open a terminal and input:

```
sudo hp-plugin
```

Apparently that works for this printer as long as you have hp-toolbox installed already (in other words, if you have the printer installed already I guess, which we have).  I find it hard to believe but you never know. I have passed that on to my mother in law and she's gonna get back to me. Let you know.

---

### Post by Bucky Ball on 2009-07-25
Tying this up: If you are having problems with the HP colourlaserjet cp1215 printer with Ubuntu Hardy 8.04 you need to install the latest HPLip as Hardy has the older version. See [this thread]("http://ubuntuforums.org/showthread.php?t=1204163") for simple instructions and links.

---

