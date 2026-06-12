---
title: "Hey, does this fix the Vsync problem?"
date: 2011-02-09
forum: Desktop Environments
---

### Post by Oranges10e on 2011-02-09
Hello,

**_before I explain:_**

we all know what a pain in the *** Compiz with Nvidia hardware can be,  when trying to do a simple Vsync for the desktop and videos, which  somewhat works - sometimes - most of the time it doesn't.

I do NOT care WHY, WHEN, HOW, and HOW long the reason may be for this issue.

Now, ATI has released new drivers, with experimental support for it and  Compiz *?* (sure, it's somehow a bit buggy here and there, but it seems  to work okay for now). On Intel GMA, with the supported Open Source  drivers, everything works out of the box (with Compiz and Vsync).

Now, I have just HAD it with Compiz and all the trying around (for MONTHS now) [IMG]http://www.nvnews.net/vbulletin/images/smilies/thumbdown.gif[/IMG]

Then it just hit me "why not try out something else". Everytime I follow  that what geeks tell me "shheheh yehehh know it'Z so muCh awesomer than  the effect$ on M$ OS" I fail to see the reason.

So I tried out "Mutter". 

I uninstalled EVERYTHING from Compiz via the Ubuntu Software-Center and  then I installed Mutter. Vsync ist activated via the Nvidia Control  Panel for both Videos and OpenGL.

It works right out of the box. My desktop is Vsync'ed. My videos are,  too. With the help of VDPAU it's even better, offloading the CPU. So, my  question is, what is the downside of this? This can't be it, right?  What is the downside of using Mutter like this? There has to be  something to kill my good mood right now.

I am happy as hell right now, so be please gentle and try not to spoil  it TOO much for me (and don't give me the long story, keep it short).  THIS is what I wanted all this time. An easy way to setup, not too many  crazy effects and stuff going on BUT a smooth and fast desktop.

Oh, and I do not feel any reduction in speed. Most ppl tell me "bleh,  vsync slows stuff down, then the reaction time is slowed down, too.  Compiz rock0rs". 

I DON'T care, I never have and never will. I love it like it is now -  Simple, very, very easy to set-up and up until now - reliable.

Thank you for your time.

**Now for what I did:**

**Howto **(Ubuntu 10.04 LTS - I will only use **LTS** from now on, everything else is just too unstable):

A) Install the Nvidia prop. drivers recommended for your system and go  in to nvidia-settings (system -> Nvidia X Server Settings) and enable  Vsync for Videos and OpenGL.

B) Disable Compiz (system -> settings -> appearance) and use  Metacity. After that, uninstall Compiz, that will get activated when you  install those Nvidia drivers (and thus the tearing begins). Do this via  the Ubuntu Software-Center. Just uninstall everything you find related  with "compiz" - especially "compiz core" and the stuff it needs.

C) Reboot, just to be sure. Go to the Software-Center and install  "Mutter" from there. Go to system -> settings -> startprograms (I  don't know the actual name, because I am using the German Ubuntu - you  get the point). Add a new startup called "Mutter" and use this command:  "mutter --replace". Save, reboot,...

D) Done.

Edit: To test things I have tried 720/1080p videos on my HDD and even HD stuff from Youtube. No prob at ALL. Please, if someone could test this and tell me how it went. I tried this under load, too (where Compiz usually breaks Vsync and all). I opened up 4 HD videos and a bunch of other apps on 8 desktops - no problem at all.

---

### Post by P4man on 2011-02-09
Simple fix for me was just adding 

```
option "composite" "disable"
```
in my xorg.conf. All tearing and stuttering gone on my xbmc home theatre pc.

---

### Post by Krytarik on 2011-02-09
> **P4man said:**
> Simple fix for me was just adding 

```
option "composite" "disable"
```in my xorg.conf. All tearing and stuttering gone on my xbmc home theatre pc.
And no effects at all, right!?

---

### Post by P4man on 2011-02-09
> **Krytarik said:**
> And no effects at all, right!?

Right. THis is for a HTPC that only runs XBMC and mythbackend, so I dont care. I never completely got rid of video tearing with either nvidia or ATI cards with compositing and compiz enabled. But the above howto also removes compiz so, my solution is faster ;)

---

### Post by sydbat on 2011-02-09
> **P4man said:**
> Simple fix for me was just adding 

```
option "composite" "disable"
```
in my xorg.conf. All tearing and stuttering gone on my xbmc home theatre pc.Dumb question - where in xorg.conf would I put this? As in under what section / subsection?

---

### Post by P4man on 2011-02-09
Not a stupid question at all. I needs to be in its own section "Extensions". 

Below my xorg.conf which also solves a problem for anyone connecting an nvidia 8xxx to a tv using DVI->HDMI adapter.  For reasons I dont quite understand, the TV thinks audio is coming over HDMI, even though the videocard doesnt support it. As a result, you get no audio on the tv at all, and my case, constant flickering of the tv as it cant sync the signal (audio clock?)

Disabling EDID and manually specing the resolutions and frequencies instead fixed that for me.

```

bob@HTPC:~$ cat /etc/X11/xorg.conf
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
        Identifier      "Configured Video Device"
        Driver         "nvidia"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        DisplaySize     640    360
        ModeLine "1920x1080p50" 148.50 1920 2448 2492 2640 1080 1084 1089 1125 +HSync +VSync
        ModeLine "1920x1080p60" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +HSync +VSync
        ModeLine "1920x1080p24"  74.16 1920 2558 2602 2750 1080 1084 1089 1125 +HSync +VSync
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
        Option         "ExactModeTimingsDVI" "True"
       ** Option         "UseEdid" "FALSE"**
        Option "ModeValidation" "AllowNon60HzDFPModes, NoEdidModes, NoEdidDFPMaxSizeCheck, NoVertRefreshCheck, NoHorizSyncCheck, NoMaxSizeCheck, NoDFPNativeResolutionCheck"
        Option         "UseEvents" "True"
        SubSection     "Display"
          Depth  24
          Modes "1920x1080p50" "1920x1080p60" "1920x1080p24"
        EndSubSection
EndSection
[B]
Section "Extensions"
        Option "Composite" "disable"
EndSection[/B]

```

---

### Post by sydbat on 2011-02-09
> **P4man said:**
> Not a stupid question at all. I needs to be in its own section "Extensions". 

Below my xorg.conf which also solves a problem for anyone connecting an nvidia 8xxx to a tv using DVI->HDMI adapter.  For reasons I dont quite understand, the TV thinks audio is coming over HDMI, even though the videocard doesnt support it. As a result, you get no audio on the tv at all, and my case, constant flickering of the tv as it cant sync the signal (audio clock?)

Disabling EDID and manually specing the resolutions and frequencies instead fixed that for me.

```

bob@HTPC:~$ cat /etc/X11/xorg.conf
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
        Identifier      "Configured Video Device"
        Driver         "nvidia"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        DisplaySize     640    360
        ModeLine "1920x1080p50" 148.50 1920 2448 2492 2640 1080 1084 1089 1125 +HSync +VSync
        ModeLine "1920x1080p60" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +HSync +VSync
        ModeLine "1920x1080p24"  74.16 1920 2558 2602 2750 1080 1084 1089 1125 +HSync +VSync
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
        Option         "ExactModeTimingsDVI" "True"
       ** Option         "UseEdid" "FALSE"**
        Option "ModeValidation" "AllowNon60HzDFPModes, NoEdidModes, NoEdidDFPMaxSizeCheck, NoVertRefreshCheck, NoHorizSyncCheck, NoMaxSizeCheck, NoDFPNativeResolutionCheck"
        Option         "UseEvents" "True"
        SubSection     "Display"
          Depth  24
          Modes "1920x1080p50" "1920x1080p60" "1920x1080p24"
        EndSubSection
EndSection
[B]
Section "Extensions"
        Option "Composite" "disable"
EndSection[/B]

```Thanks brother!!

---

### Post by Oranges10e on 2011-02-10
> **P4man said:**
> Right. THis is for a HTPC that only runs XBMC and mythbackend, so I dont care. I never completely got rid of video tearing with either nvidia or ATI cards with compositing and compiz enabled. But the above howto also removes compiz so, my solution is faster ;)

It's faster but, like someone else said, it takes away ALL effects, leaving the 2D desktop to tear (like in Windows XP), but at least videos work fine that way. With Mutter you at least have a few effects and the 2D desktop ist vsync'ed plus all videos.

I have been testing it since yesterday the whole time in different situations. Now, there ARE issues, but they seem minimal and I hope they get fixed in the NEAR future, maybe it's something else in the end:

Sometimes windows "hang" or get "stuck" and the only way to close them is with F4. Or, like this morning, having to reboot because I couldn't click on any of the maximize or minimize buttons or even close for that matter.

When using something like Crossover Games (I test a bunch of games with that from time to time):

Sometimes, if you switch to a different (virtual)space, the window you had, for example while installing something, would just disappear and stay gone. You can see it in the lower taskbar, but you can't get it to show again. F4 or trying to hit the X of the window, that you can't see, is the way to end that misery. 

Other than that, everything else works normal, fast, smooth and with vsync.

So, this just shows me, that it IS possible to do and it just has to do with Compiz (in combination with Nvidia)...AGAIN. Ever since I switched to Linux (UBuntu) I have ALWAYS had some kind of problem, and most of the time it is related with Compiz. But ONLY on Nvidia hardware. On Intel GMA onboard cards, since they use good Open Source drivers, that is NO prob at ALL.

Since ATI is coming down fine (I have had several other issues with ATI cards and Compiz in the past, but I don't know how they are doing now), but isn't there yet, I might consider buying a cheap laptop OR using my old Macbook Pro with Intel GMA with Compiz and in future, if ATI gets this right, then an ATI card. On this machine, the most powerful laptop that has ever existed, I will have to use Mutter and report on those minimal bugs, since it's the most easiest thing I have ever used on Linux (besides the /no composite thingy).

:KS:KS:KS:KS:KS:KS:KS

---

