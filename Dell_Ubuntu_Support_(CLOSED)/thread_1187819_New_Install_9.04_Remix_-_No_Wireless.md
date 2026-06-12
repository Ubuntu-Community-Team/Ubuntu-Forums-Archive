---
title: "New Install 9.04 Remix - No Wireless"
date: 2009-06-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rokeven on 2009-06-15
I just installed 9.04 Remix on a Dell Mini 9.  Immediately after the install, the hardware driver dialog popped up and wanted to install and activate the Broadcom driver.  I agreed, and it installed successfully once I connected the computer to a wired internet connected.  My problem is the wireless does not show anywhere still.  If I click on the network icon on the taskbar, it shows the wired connection, but nothing about wireless.  If I open "Network Tools", the wireless device does not show on the drop down menu.

I have scoured the forum, and everyone seems to say the Mini 9 works perfectly except for a minor microphone bug.  There seem to be a select few with major wireless problems, but no solutions that I can find.  

Please help!  I installed 9.04 because everything was supposed to work, but that is not the case and I am now stuck!

---

### Post by Vostrocity on 2009-06-15
Right click on the network icon and see if Wireless is checkboxed. If that doesn't work, connect your Ethernet then go to hardware drivers. See if there's another driver for your WiFi card and install that.

---

### Post by rokeven on 2009-06-15
> **Vostrocity said:**
> Right click on the network icon and see if Wireless is checkboxed. If that doesn't work, connect your Ethernet then go to hardware drivers. See if there's another driver for your WiFi card and install that.

There is no "wireless" option under the network icon.  I have tried connecting the ethernet and installing the driver under "hardware drivers".  It would not even install unless the ethernet was connected since it needed to download the driver over the net.  I have tried uninstalling it and reinstalling it over and over.  I never get a wireless option under the network though.

---

### Post by ugm6hr on 2009-06-15
Bizarre... Could this be a hardware problem?

If the hardware is the same Mini 9, there should be no problem.

Does lshw find your wifi?

```
lshw -class network
```

---

### Post by rokeven on 2009-06-15
> **ugm6hr said:**
> Bizarre... Could this be a hardware problem?

If the hardware is the same Mini 9, there should be no problem.

Does lshw find your wifi?

```
lshw -class network
```

It does not.  It only shows the ethernet connection.  Ubuntu knows the wireless card is there, since it had me install the driver.  I have two Mini 9's, and tried swapping the SSD over to the other one last night.  Same result there.  No wireless.  Both systems came with Ubuntu 8.04, which had the wireless working perfectly.

---

### Post by ugm6hr on 2009-06-15
Only thing I can think is that you have a corrupt NBR download.

Did the wifi work on the Live USB?  I'm pretty sure mine did (I can double-check if yours doesn't - I think I still have the LiveUSB somewhere).

---

### Post by rokeven on 2009-06-15
> **ugm6hr said:**
> Only thing I can think is that you have a corrupt NBR download.

Did the wifi work on the Live USB?  I'm pretty sure mine did (I can double-check if yours doesn't - I think I still have the LiveUSB somewhere).

It did work on the Live CD once the driver was installed.  Out of the box, it did not though.  I have reinstalled three times now, and the Live CD has worked every time, but never once installed.

---

### Post by ugm6hr on 2009-06-15
Hmmm...

Clearly not a hardware issue then.

I have no idea why it would work in Live mode, but not after installation.

Can't be a BIOS setting either, if it works in Live mode.

I'm stumped.

---

