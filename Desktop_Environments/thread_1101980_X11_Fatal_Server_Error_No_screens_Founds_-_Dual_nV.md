---
title: "X11 Fatal Server Error: No screens Founds - Dual nVidia Graphics Cards/Three Screens"
date: 2009-03-20
forum: Desktop Environments
---

### Post by Sootah on 2009-03-20
I just installed Ubuntu on my desktop system after having it up and running on my laptop for a little while. My desktop has two nVidia graphics cards in it, an 8800 GTS running dual Samsung 22" widescreens, and an older 7800 GTX running my Samsung 46" LCD TV via an DVI->HDMI connection.

The first reboot after I installed the nVidia drivers worked fine, my primary display came up but nothing else. I gksued into the nvidia-settings manager and had it detect the displays, but in the display configurations it only showed the screens from my 8800 even though it did show the other graphics card in there.

Anyway, I didn't save any settings or have it apply anything and I rebooted. After this, it booted to a good old fashioned command prompt; and while this was nostalgic for me and took me back to my DOS days with my 386, I'd obviously prefer to have a GUI on my desktop.

I tried replacing my xorg.conf with the xorg.conf.failsafe file that I found, but that didn't work either. I still get the X11 fatal server error: No screens found.

So, how can I get back into X, and furthermore, get my displays all working in harmony?

Thanks in advance for your help.

-Sootah

---

### Post by Sootah on 2009-03-21
Anybody?

---

### Post by Sootah on 2009-03-22
You, my friends, were not much help. Fortunately, I am quite stubborn and have figured out the issue myself.

I ended up doing a reinstall, which initially worked again as it did the first time. This time around, I grabbed the latest v180.29 drivers from nVidia's website and did a manual install of them. This resulted in the same **Fatal server error: No screens found** issue as before.

Anyway, I poked around in the /var/log/Xorg.0.log and found that while the X server correctly detects both of the cards, it for some reason will not just load one of them unless one is specifically specified by the BusId; which in my opinion is retarded. Perhaps this is an issue with the nVidia driver, but I don't know because I don't know how X interacts with the driver or how it determines its displays.

After viewing the log I was able to discern both cards BusIds from it, and so I added the bolded line below to the "Device" section.

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
**    BusID          "PCI:1:0:0"**
EndSection

After specifying which card was to be used X started fine. I've now also got a dual head setup working beautifully with full compiz effects and all that, and have *kind of* got the third monitor working properly; although I cannot get it to work with TwinView yet - it'll only display as a seperate X screen, and this behaves screwely as well as the fact that it dicks up the taskbar on the two main monitors by extending them across both displays.

I'll poke around more and see if there's a way to get the third monitor to act correctly.

This has been quite the frustrating experience because I am a complete newbie to Linux. I've had a hint of experience with it here and there, but were it not for the fact that I also have a laptop I was able to use to even figure out how to work vi I'd not have been able to do this.

So much for the whole "Just Works" slogan, eh? :)

Once I get the third monitor working the way I want it to I'll do a writeup on it and include my xorg.conf file as well, but I do think that the multi-monitor setup really needs to be something that's looked at. I have to use the nvidia-settings package to configure anything correctly as the default display configuration tool doesn't work with the dual displays at all. I'm sure I could get it working with it if I were to mess with the xorg.conf file more; but the fact that I have to hand-code a config to make something as simple as this work is frustrating.
Later on I added another device section (Device1) and specified the other card's BusId

---

