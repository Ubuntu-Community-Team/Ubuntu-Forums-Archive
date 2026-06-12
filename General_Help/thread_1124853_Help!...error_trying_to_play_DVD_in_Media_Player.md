---
title: "Help!...error trying to play DVD in Media Player"
date: 2009-04-13
forum: General Help
---

### Post by gabriella on 2009-04-13
I'm trying to play a DVD in Media Player. But it wont! When I insert the DVD (or click on it in the pull down menue below Movie I get the following
"An error ocured" "could not read from resource"

I know this isn't much info but any ideas on how I should start tracking down this problem? Any help appreciated

---

### Post by RedSingularity on 2009-04-13
First in terminal run: 

sudo apt-get install ubuntu-restricted-extras

Then: 

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update && sudo apt-get install libdvdcss2 w32codecs

---

### Post by RedSingularity on 2009-04-13
The above is if you are using a 32 bit version of ubuntu.  Change the last part "w32codecs" to 64 if you have a 64 bit.

---

### Post by gabriella on 2009-04-13
> **Shadow121 said:**
> The above is if you are using a 32 bit version of ubuntu.  Change the last part "w32codecs" to 64 if you have a 64 bit.

Thanks! yes I do have a 64 bit. That seems to have fixed the problem. The DVD plays fine with amazing definition. Maybe its just the DVD production but I'm convinced this is sharper than Window Media Player?

The only thing, and this is probably unrelated to my above question, is that the audio level seems a bit low. I have it on full volume right now. Is there anyway of increasing the audio?

Gabriela

---

### Post by fooman on 2009-04-13
> **gabriella said:**
> 

The only thing, and this is probably unrelated to my above question, is that the audio level seems a bit low. I have it on full volume right now. Is there anyway of increasing the audio?

Gabriela

what player? ...there should be a volume control on the player itself,  is that turned up?

also,  look in the top panel and *double*-click on the speaker/volume icon.  that will bring up the aslamixer....check that all of the volume sliders are maxed out (master, pcm, etc...).

---

### Post by gabriella on 2009-04-13
> **fooman said:**
> what player? ...there should be a volume control on the player itself,  is that turned up?

also,  look in the top panel and *double*-click on the speaker/volume icon.  that will bring up the aslamixer....check that all of the volume sliders are maxed out (master, pcm, etc...).

I'm using the default Media Player that comes with Ubuntu. Clicking on the speaker icon just brings up the volume slider "Master" which is at max. This is the case also with the volume up/down buttons of my lap top

---

### Post by RedSingularity on 2009-04-13
Try double clicking the Ubuntu master button on the panel.  (Not the one in the player the one on your desktop)

---

### Post by fooman on 2009-04-13
try this, open a terminal (applications > accessories > terminal) and type or copy/paste the following command to install the "gnome-alsamixer":

```
sudo apt-get install gnome-alsamixer
```

after it installs,  open it in applications > sound & video > gnome alsamixer

you should see a few more sliders in there....check that they are all turned up to max.

hope that helps.

---

### Post by gabriella on 2009-04-13
> **Shadow121 said:**
> Try double clicking the Ubuntu master button on the panel.  (Not the one in the player the one on your desktop)

you mean the one on the bar at the top next to the Date etc? Thats what am clicking. Just brings up Master!

---

### Post by mb_webguy on 2009-04-14
Right-click on the volume icon in the notification area (top right of the desktop by default) and select Open Volume Control.  Check each output device (i.e. the ones that don't start with "Capture") and see if any of the volume controls are turned down.

---

### Post by gabriella on 2009-04-14
> **mb_webguy said:**
> Right-click on the volume icon in the notification area (top right of the desktop by default) and select Open Volume Control.  Check each output device (i.e. the ones that don't start with "Capture") and see if any of the volume controls are turned down.

OK it seems I already have ALSA without having to install it. So when I right click I get the panel of sliders. Some are maxed out like Master. The only one that increases volume a bit is PCM. What does it mean when there is a red "X" under one such as PC Speaker? I can adjust this one.

And what does the Switches>Video tab do?

Thanks

---

