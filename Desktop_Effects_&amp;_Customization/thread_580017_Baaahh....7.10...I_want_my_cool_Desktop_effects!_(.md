---
title: "Baaahh....7.10...I want my cool Desktop effects! :("
date: 2007-10-18
forum: Desktop Effects &amp; Customization
---

### Post by maxxym on 2007-10-18
Well.. I upgraded by laptop to Gutsy. I have to say.. I like it MUCh better than KDE. It runs very fast too.

I would like to enable those cool desktop effects, but it tells me that it can't :(

I installed Restricted Driver by using Restricted Driver Manager. That went fine. When I open it up, it tells me that my ATI accelerated driver is in use...so far so good.

So then I went to enable those effects and it still telling me that it can't enable effects :(

What gives??

---

### Post by JawsThemeSwimming428 on 2007-10-18
What graphics card are you using?

---

### Post by stijngysemans on 2007-10-18
Maybe you can give us some more information about the specific card used and the exact error message you're getting.

---

### Post by maxxym on 2007-10-18
How do I check which card I am using? I know it's ATI, but I am not sure what command to run to give you guys some info :( Sorry, I am on my 5th day with Linux....

---

### Post by lazyart on 2007-10-18
run compiz from the command line and post the output.  I had this same problem and I just had to comment out a few lines in the compiz script to get it rolling for me.

---

### Post by luisromangz on 2007-10-18
If you are using an ATI card, besides the ATI fglrx drivers you need to use XGl, as fglrx doesn't (yet) support AIGLX, which is the default option for Desktop Effects.

You have to install XGL, then launch it instead you normal XServer. There are many how-tos regarding this issue.

---

### Post by maxxym on 2007-10-18
ok in Device Manager (DUHH!!) it shows:

Radeon Mobility X1400

Then on the right it says:

Vendor: AIT Technologies
Device: Radeon Mobility X1400
Status: Status
Bus Type: PCI
Device Type: Unknown
Capabilities: Unknown

---

### Post by maxxym on 2007-10-18
Wooohooo got it working!!

THIS IS SWWWWEEETTT!!!!!

---

### Post by tooleh on 2007-10-18
> **maxxym said:**
> Wooohooo got it working!!

THIS IS SWWWWEEETTT!!!!!



What exactly did you do?

---

### Post by depele on 2007-10-18
yes please tell me.

because when I install xgl I get a very slow X server.

Please help me...

---

### Post by maxxym on 2007-10-18
ok I will try to explain as best I can since I am new and don't know all the terminology.


First, I installed Proprietary drivers for my card. System>Administration>Restricted drivers....I installed them...

Still didn't work. I was getting some error saying that Composite could not be loaded....


So then, I edited my xorg.config file:

sudo gedit /etc/X11/xorg.config

Last section you want to change from 0 to 1 so it says:

Section "Extensions"
	Option		"Composite"	"1"

Still didn't work..


So then I did sudo apt-get install xserver-xgl

It took a while for it to install, but once it did, it told me to reboot. I restarted my laptop and turned on effects and they all work.

---

### Post by Amaranth on 2007-10-18
Careful, if you enable Composite it disables OpenGL acceleration so then Xgl will run _really_ slow.

---

### Post by SCGreg on 2007-10-18
Thought I'd reply to this post rather than start yet another compiz thread..

I'm having a small problem with my compiz-fusion - it was working fine until I tried installing  the settings manager, now some of the effects seem to have disabled themselves. The settings manager won't load for some reason so I can't customise it that way, and even when changing from 'none' to 'extra' and vice versa in appearance preferences, nothing happens. The minimise/maximise animations work, but the jelly-like drag animations have stopped, and I can't seem to get the cube working

Any ideas? :)

Oh yeah - running on an nVidia Geforce 8800 GTX if that helps anyone. ;)

---

### Post by fmacher on 2007-10-18
another one over here who cant enable compiz fusion with ati x1650xt

---

### Post by buntunub on 2007-10-18
The Desktop Cube is not enabled by default on Gutsy. To do that youll have to go to Synaptic and install the Compiz Settings Manager.

---

### Post by SCGreg on 2007-10-18
> **buntunub said:**
> The Desktop Cube is not enabled by default on Gutsy. To do that youll have to go to Synaptic and install the Compiz Settings Manager.

I did - and it won't run for some reason :(

---

### Post by Vaderdarth211 on 2007-10-18
I'm getting a composite extension not found on an ati radeon express 200m

---

### Post by tasomaniac on 2007-10-19
You can enable composite extension in xorg.conf file

```
sudo gedit /etc/X11/xorg.conf
```

At the end of this file. You see
```

Section "Extensions"
	Option "Composite" "Enable"
EndSection
```

I hope it solves your problem

---

### Post by eric87m on 2007-10-19
I'm running 7.10 on old Dell laptop with a... Radeon Mobility 7500. It doesn't show up in restricted drivers though. Only my Linksys wireless card. How do I install the drivers for it?

(I looked around on this forum and even it though the card is old and sucks it runs Compiz fine some people said)

---

### Post by Vaderdarth211 on 2007-10-21
> **tasomaniac said:**
> You can enable composite extension in xorg.conf file

```
sudo gedit /etc/X11/xorg.conf
```

At the end of this file. You see
```

Section "Extensions"
	Option "Composite" "Enable"
EndSection
```

I hope it solves your problem

THanks it works. you're the best.

---

