---
title: "VGA port not working under 11.10 on Latitude E6520"
date: 2011-10-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jeffzap on 2011-10-21
I performed a fresh install of Ubuntu 11.10 (64 bit) on my Latitude E6520 last weekend.  I discovered a few days afterward that I cannot get a VGA signal out of the VGA display port on the side of the laptop.  

I tried connecting a projector (which was just shown to work via a colleague's laptop) and could not get it to detect using the Displays panel in System Settings.  Clicking "Detect Displays" would cause my built-in LCD to blink, and would also result in a short period of a few seconds where my system was semi-responsive (sputtering mouse movement), after which it would return to normal, but nothing would appear on the external display.

I had never used the port prior to this, so I cannot report on whether it worked with versions prior to 11.10.

I'd appreciate any suggestions on how to troubleshoot this.  Is there a log file where I can look while trying again in order to determine what might be the problem?  BIOS settings to check?  Possible kernel parameters and such to pass?  I haven't found much searching for vga port problems with Ubuntu and this model.

Thanks,
Jeff

---

### Post by w15p on 2011-10-22
Do you have optimus enabled in the bios?  I found display auto-detection didn't work with optimus disabled.

Of course, I have the opposite problem as you - my VGA works fine but my hdmi out does not (locks up boot)

BTW: I have the quadcore with the Nvidia graphics, not (just) the integrated intel.

---

### Post by masgeeks on 2011-10-22
Had same problem with Dell Precision laptop M6300 - never could figure out why I could not get external monitor to work, so gave up.  I just assumed it had never worked in the first place...  :-\

---

### Post by jeffzap on 2011-10-23
> **w15p said:**
> Do you have optimus enabled in the bios?  I found display auto-detection didn't work with optimus disabled.

Of course, I have the opposite problem as you - my VGA works fine but my hdmi out does not (locks up boot)

BTW: I have the quadcore with the Nvidia graphics, not (just) the integrated intel.

Oh, I didn't think to try with Optimus enabled since I'd read it caused other issues.  So you're right - with Optimus enabled the display detection works and I can use the VGA port.  Interestingly enough I also finally saw the Ubuntu boot splash screen display at an appealing resolution for the first time on this laptop!

Unfortunately it causes a new problem - I don't get window decorations and none of the window management key combinations work - so I can effectively just run one application at a time, whose window gets drawn somewhere on the screen and can't be repositioned.  I tried Unity and GNOME in all available modes, same result.  GNOME also refuses to try and render using its 3D accelerated mode with Optimus enabled.

Maybe that's a new topic, but is there a way to get a usable desktop with Optimus enabled?

Thanks,
Jeff

---

### Post by DGTL_Magician on 2011-10-23
You have to install Ironhide for that. Ironhide enables the Optimus stuff to work and give you back your 3D acceleration.

Been running it for three weeks now without issues.

---

### Post by jeffzap on 2011-10-25
> **DGTL_Magician said:**
> You have to install Ironhide for that. Ironhide enables the Optimus stuff to work and give you back your 3D acceleration.

Been running it for three weeks now without issues.

Awesome - the combination of re-enabling Optimus and installing Ironhide solved all my problems.  Thanks a lot!

Jeff

---

### Post by ktmini on 2011-11-02
I'm glad to see you folks managed to get ironhide working on 11.10! :)

Each time I tried to install it (optimus or not), best case scenario was glxgears showin up but then I got a message saying I needed to write myself the enabling and disabling scripts.. with no success.

Would you have any advice?
Thanks in advance!

.T.

---

