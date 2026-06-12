---
title: "restricted drivers disappearred"
date: 2009-02-22
forum: General Help
---

### Post by Bucky Ball on 2009-02-22
Hi.

Okay, anyone help me here? Been having heaps of trouble with nvidia drivers. Ran this command:

sudo apt-get remove nvidia*

... and that got me to where I want to be. Trouble is, it has removed all my restricted Atheros wireless drivers from System/Hardware Drivers and thus I have no wireless! What is happening here and how do I re-install them easily. Wondering if I should just take the PCI wireless card out and reinsert it. Might be easiest.

Bemused.

---

### Post by Bucky Ball on 2009-02-22
Okay, loaded ubuntu-restricted-modules and that got the wireless going again. But it also got me back to low resolution graphics, even though the nvidia restricted driver is not in use in System->Hardware Drivers.

The problem is arising from the fact I am using the nvidia 180.29 which I installed with the nvidia installer. Obviously anything nvidia other than this driver is causing a conflict. Any ideas?

---

### Post by hansdown on 2009-02-22
Glad you got your wireless working Bucky Ball.

I'm not sure if the nvidia 180.29 drivers are working for you, or causing a problem though.

---

### Post by Bucky Ball on 2009-02-23
Thanks for the reply, hansdown. Here's what's happening. I load the 180.29. Says it's already installed. I go ahead anyway and it uninstalls the old one and puts a fresh one in. All's well. Reboot and back to low graphics. The driver seems to go away but obviously it is still installed because I just installed it, just being ignored. Right, how the hell do you uninstall 180.29? I haven't had any success with that either using this command:

sh NVIDIA-Linux-x86_64-180.29-pkg2.run -uninstall

... which seems to be the way to do it.

---

### Post by hansdown on 2009-02-23
If you click on system> administration> hardware drivers, do you get a screen that looks like this?

Note that the "in use" is marked.

You may need to reinstall some nvidia stuff.

If you go to synaptic, search for nvidia.

Right now, I have nvidia kernel common installed.

Also, I have nvidia-glx-new installed. That is what works on my box, and may not work on your's.

---

### Post by Bucky Ball on 2009-02-23
Er, yea. Well past that unfortunately. I am getting nothing to work, glx-new, 180.29, nothing. If I install the 180.29, it works beautifully ... until I reboot. Then it's back to the low res configuration window and my monitor is not listed in there anyhow.

I say this but the way it all started was a quest for the correct resolution for the screen of 1360x768. I decided to be happy with 1280x768, but things have broken in the process. If I could get the 180.29 driver to stick it would be another story. It is installed but ignored when I reboot. That is my problem at this point I'm pretty sure.

---

### Post by hansdown on 2009-02-23
Um, how did you install the drivers?

---

### Post by Bucky Ball on 2009-02-23
sh NVIDIA-Linux-x86_64-180.29-pkg2.run

... and to uninstall

sh NVIDIA-Linux-x86_64-180.29-pkg2.run --uninstall

... all with x off.

And also, when I try to run nvidia-setting, I get the message that I'm not using NVIDIA X driver. So stop X, run nvidia-xconfig, as advised, startx and ... nothing. No different and I get the same result from running nvidia-settings.

---

### Post by hansdown on 2009-02-23
This version is still in beta.

Are you testing it?

---

### Post by Bucky Ball on 2009-02-23
> **hansdown said:**
> This version is still in beta.

Are you testing it?

Well, I think I can consider I have. 

What I effectively ended up doing was uninstalling everything nvidia, getting the wireless drivers back by installing ubuntu-restricted-modules then installing envyng. I then manually installed the 173.14.12 driver and after a little tweaking, all is sweet. The problem with 180.29 (for me, at least) was it seemed to be ignored on reboot. Seemed to work fine when I installed it, but as soon as I stopped and started X, gone.

bodhi.zazen is of course correct on this thread:

[http://ubuntuforums.org/showthread.php?t=1074568](http://ubuntuforums.org/showthread.php?t=1074568)

Doesn't make any difference what resolution is defined in the xorg.conf. After I installed the 173 driver, it defaulted to 1024x768 (from memory). I opened nvidia-settings and changed the resolution to 1280x768, wrote that to xorg.conf with the nvidia-setting 'write to config' tool, rebooted and, you guessed it, defaulted to 1024x768. 

So, I opened System->Preferences->Screen Resolution and changed the resolution in there to 1280x768, rebooted and presto, 1280x768. I have no idea whats going on.

I am pretty much where I was 3 or 4 days ago before I started the quest for the native screen resolution of 1360x768: system is stable at 1280x768 and running with nvidia driver. Still have no idea of how I might achieve 1360x768 resolution though. Any ideas?

Thanks for your comments ... :)

---

### Post by carml on 2009-02-23
I beg you perdon,if my question is odd: why are you trying to use 1320x768 resolutio? If you're satisfiedd of 1280x768,why to bother the change?
BTW what is the model of your Atheros?

---

### Post by Bucky Ball on 2009-02-23
Not 1320, 1360x768. It is the native resolution of the Acer X193HQ monitor I am using. If I can nut it out, I can help out some others along the way. Besides which, why shouldn't it be possible?

... And having said that, I'd like to relate the news that I have managed to get 1360x768 into the nvidia-settings resolutions list. But when I select it, I get this message:

> Failed to set MetaMode (6) 'CRT-0: 1360x768@60 @1360x768 +0+0' (Mode 1360x768, id: 55) on X screen 0and asks if I want to remove that metamode. Anyhow, I got it into the resolution list by making a two changes to my xorg.conf, oddly enough, after thinking it made no diff, maybe I got the right combination. This change:

```
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer X193HQ"
    HorizSync       31.0 - 80.0
    VertRefresh     55.0 - 76.0
   ** ModeLine       "1360x768@60" 85.50 1360 1424 1536 1792 768 771 778 795 -hsync -vsync**
    ModeLine       "1280x768@60" 80.1 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
    ModeLine       "1280x720@60" 74.5 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    Option         "DPMS"
EndSection

```

.. and:

```
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "**1360x768@60 +0+0;** 1280x768@60 +0+0; 1280x720@60$
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```That's it. I got the modeline from here:

[http://www.mythtv.org/wiki/Modeline_Database#EDID_modelines_from_HDTVs](http://www.mythtv.org/wiki/Modeline_Database#EDID_modelines_from_HDTVs)

... but maybe I have the numbers wrong somewhere in the modeline. The actual res in the manual is 1366x768. I tried changing it to that but didn't appear in the list oddly enough.

Anyhow, getting closer but learned something along the way. At least I know how to get the machine back to stable, even if it is the wrong res still. :)

---

### Post by carml on 2009-02-23
Sorry for the mistake,I meant 1360x768,yes you're right it could be useful to others.
I have also a question: what is the model of your Atheros?
I have some little issue using mine,it works but sometimes,since I installed ATI native drivers I have to reboot to use eth0 or wlan0,.
That's not a big problem,but it's tiresome :( .

---

### Post by Bucky Ball on 2009-02-23
It is a TPLink wn651G pci wireless card. 

[http://www.tp-link.com/products/product_des.asp?id=17](http://www.tp-link.com/products/product_des.asp?id=17)

These are the details of the chipset from my lspci:

 ```
Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
```The card worked 'out of the box', no problems. Was only when I removed everything nvidia the drivers died.

---

### Post by carml on 2009-02-23
Thanks all the same,but mine is AR5007EG.

---

### Post by hansdown on 2009-02-23
Bucky Ball, I found a pdf for your monitor.

It says 1366-768@ 75 Hz.

---

### Post by fragos on 2009-02-23
> **Bucky Ball said:**
> sh NVIDIA-Linux-x86_64-180.29-pkg2.run

... and to uninstall

sh NVIDIA-Linux-x86_64-180.29-pkg2.run --uninstall

... all with x off.

And also, when I try to run nvidia-setting, I get the message that I'm not using NVIDIA X driver. So stop X, run nvidia-xconfig, as advised, startx and ... nothing. No different and I get the same result from running nvidia-settings.

Installing binary drivers from the venddor web sites will work but you break the update process because these drivers won't be registered in the application data base. The next time the kernel updates you video drive will most likely not work with the new kernel. I recommend that drivers are installed from the Ubuntu repositories. That way they will be updated when the kernel is updated.

---

### Post by Bucky Ball on 2009-02-23
> **hansdown said:**
> Bucky Ball, I found a pdf for your monitor.

It says 1366-768@ 75 Hz.

Thanks hansdown, but I have a manual that came with the machine a week and a half ago and it clearly states 1366x768@60Hz so don't know what's happening there. I will give it a try though.

I am going to continue with this thread here:

[http://ubuntuforums.org/showthread.php?t=1074568&page=2](http://ubuntuforums.org/showthread.php?t=1074568&page=2)

as this one is about a problem I had along the way and is now starting to merge with the original thread. Hope to see you there. I have some interesting news ... I achieved 1360x768@60!

---

### Post by hansdown on 2009-02-23
Hope you get it working.

---

### Post by Bucky Ball on 2009-02-23
Thanks for your comments, ideas and posts people. I am continuing this thread here:

[http://ubuntuforums.org/showthread.php?t=1074568&page=2](http://ubuntuforums.org/showthread.php?t=1074568&page=2)

... which is where it all started. This thread is about one of the issues I had along the way and is starting to merge with the original issue, so hope to see you there. You will discover a very interesting development ... I did achieve 1360x768 ... but not what was expected.

---

