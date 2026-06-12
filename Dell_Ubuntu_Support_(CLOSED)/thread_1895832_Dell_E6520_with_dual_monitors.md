---
title: "Dell E6520 with dual monitors"
date: 2011-12-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gopo on 2011-12-15
Hello, similar to "[Dual Monitors on a Dell Latitude E6520]("http://ubuntuforums.org/showthread.php?t=1891283")," I have a Dell E6520 with an E-port dock. 

This dock has two DVI connectors, and I have two monitors with one DVI and VGA port each.

The problem is, under Ubuntu 11.10 I can't get either of the monitors (E2211Hb and E2210c LCDs) recognized if I use the DVI ports. Only the VGA connector works. 

So since there is only one VGA connector on the back of the dock, I can only use one monitor.

Any ideas?

Thanks.

---

### Post by gopo on 2011-12-16
Here's my best clue so far.

When the DVI cable is **disconnected**, the screen says, "No DVI-D cable," and the monitor's power button glows blue.

As soon as the DVI cable is **connected**, that message instantly disappears, the screen changes to a different shade of black, and the power button glows orange. It remains in this state for probably two seconds. Then, a new message appears: "Entering Power Save mode." That message, in turn, disappears, and the screen goes black again.

If a monitor button is pressed, here's what appears:

```

Dell E2211H
There is no signal coming from your computer.
Press any key on the keyboard or mouse to wake it up.
To change to another input source press the monitor button again.
```

It's almost as if, under Ubuntu, this laptop can't properly utilize the DVI ports provided by the e-port dock. Perhaps it's missing a driver? 

What is necessary for it to make use of these extra ports? It has no problem utilizing the e-port dock's USB, Ethernet, power or VGA connectors. No idea about the serial or parallel ports; I have no use for those.

FYI, under Windows, this exact same hardware worked to drive both monitors, using DVI cables, without an issue.

---

### Post by gopo on 2011-12-20
Here's an image of the "Displays" settings, when one monitor is connected with a VGA cable (click for larger image):

[[IMG]http://i.imgur.com/xyrSk.png[/IMG]](http://imgur.com/shCY8)

And a screenshot of the settings dialog, when any monitor is connected with a DVI cable (click for larger image):

[[IMG]http://i.imgur.com/skIRS.png[/IMG]](http://i.imgur.com/uhrnB.png)

Note that the displays aren't even recognized by the OS when the DVI cable connectors are used. And remember, Windows has no problem with this! :)

---

### Post by gopo on 2011-12-20
Hmm... What part of the OS controls whether the DVI ports are recognized or not? Maybe I could start troubleshooting there, or perhaps there's a bug to report?

---

### Post by gmurray13 on 2012-01-01
I also am experiencing this same problem using Kubuntu 11.10, KDE 4.7.3, kernel 3.0.0-14-generic with a similar hardware config (E6420 and an E Port Plus docking station)

I am also currently just able to use the VGA port out of the docking station, while Windows 7 on the same machine seems to work without issue.  I've tried using both DVI ports, and neither one seems to be recognized by the OS.

Just thought I'd add my .02 to let others know it's not an isolated problem.

---

### Post by gmurray13 on 2012-01-01
So, booting into windows and looking at the hardware config, it looks like there are 2 video cards in my machine:

Intel (R) HD Graphics Family
NVIDIA NVS 4200M

I'm guessing that it's using the Intel card, which possibly doesn't support DVI or something?

I had tried installing the NVIDIA drivers previously (a month ago or so) by hand (i.e., downloading the package from the nvidia site and installing it), but didn't have much luck with that.  Then, I just noticed that there was a menu item in the KDE main menu for "System -> Additional Drivers".  It seems to provide the capability to install the NVIDIA drivers through a more "controlled" process.  I tried that (which downloaded and installed drivers), but they didn't seem to be recognized.  Then, I ran nvidia-xconfig, which replaced my /etc/X11/xorg.conf file with an updated one.  But, unfortunately, when I restarted, X didn't start, and the only way I could get back to KDE was to restore the backed up xorg.conf.

So, back to square one again.

---

### Post by gopo on 2012-01-02
> **gmurray13 said:**
> So, booting into windows and looking at the hardware config, it looks like there are 2 video cards in my machine:

Intel (R) HD Graphics Family
NVIDIA NVS 4200M


Hmm, looks like I have pretty much the same setup (which can be viewed using 'lspci -v' at the command line):
[LIST]
[*]Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
[*]nVidia Corporation GF108 [Quadro NVS 4200M]
[/LIST]
> 
I'm guessing that it's using the Intel card, which possibly doesn't support DVI or something?


You may be on to something there. But more below...

> I had tried installing the NVIDIA drivers previously... by hand... but didn't have much luck with that.

So I read at [http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660) that I should definitely NOT install the drivers provided by the Ubuntu repositories. That's because for those laptops that use nVidia's "Optimus" processor-switching technology, those drivers won't help. Optimus apparently works at the BIOS level, allowing the OS to call on either the nVidia card or the onboard Intel chip as the situation demands.

I did get [Bumblebee]("https://launchpad.net/~bumblebee") installed, and it works great!

However... this still doesn't allow the nVidia card to control the main X server, apparently.

---

### Post by gmurray13 on 2012-01-02
As they say in Boston...bummah!

I'll give that thread you posted above a thorough read, and maybe also try installing the nvidia proprietary drivers by hand again and see if I can get that to work.  I wish I had a monitor that had a DP, because this thread ([http://ubuntuforums.org/showthread.php?t=1242327](http://ubuntuforums.org/showthread.php?t=1242327)) seems to indicate that this person didn't have luck with DVI, but *did* have luck with DP.

---

### Post by gmurray13 on 2012-01-02
> **gopo said:**
> I did get [Bumblebee]("https://launchpad.net/~bumblebee") installed, and it works great!

However... this still doesn't allow the nVidia card to control the main X server, apparently.

Does this mean that with Bumblebee, you have 2 external monitors running over the 2 DVI connectors?  Are you finding any drawbacks?

---

### Post by gopo on 2012-01-03
> **gmurray13 said:**
> Does this mean that with Bumblebee, you have 2 external monitors running over the 2 DVI connectors?

Nope, sorry gmurray! It allows me to run individual applications specifically using the nVidia chip, if I prefix the command with "optirun ". Like:

```
optirun firefox
```

So I can get the improved graphics performance *for individual applications*. But not for X.

I know -- dang! :)

---

### Post by gmurray13 on 2012-01-03
Well, I found that I could turn off Optimus in the BIOS, so I did that, and now I have multiple monitors in Linux using the Nvidia driver in Kubuntu.  I'll see how much it affects my battery life in Windows and maybe I'll leave it off all the time, or maybe I'll just turn it off when I run Linux on the laptop.

Thanks for the clues about Optimus - that's what helped me get to a point where I at least now have an external DVI monitor working!

Good luck!

---

### Post by gopo on 2012-01-04
> **gmurray13 said:**
> Thanks for the clues about Optimus - that's what helped me get to a point where I at least now have an external DVI monitor working!

Oho! Fantastic! That's why these forums can be so helpful! 

In my case perhaps I just need to cross my fingers and try installing the nVidia driver. I'll consider it.

---

### Post by gopo on 2012-01-09
> **gopo said:**
> In my case perhaps I just need to cross my fingers and try installing the nVidia driver. I'll consider it.

I installed the nvidia driver today ("nvidia-current, version 280.13-0ubuntu6"). I had a number of problems attempting to get it to work and have spent most of the day trying to get my Xorg back into a usable state. So... I wouldn't recommend that for others with this specific hardware configuration.

Some of the highlights:

[LIST]
[*]Installed the driver with 'apt-get install nvidia-current'.
[*]Used nvidia-xconfig to generate a config file.
[*]Ran startx as a user (doesn't work, error messages indicate that user isn't allowed to run the X server).
[*]Ran startx as root (worked, nvidia logo appeared, could get a desktop by inserting an ".xstartup" file in my home directory with "exec gnome-session").
[/LIST]

---

### Post by gopo on 2012-01-10
> **gmurray13 said:**
> Well, I found that I could turn off Optimus in the BIOS, so I did that...

I discovered something interesting. With Optimus enabled, the graphics cards listed on my laptop are:

```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation GF108 [Quadro NVS 4200M] (rev a1)
```

And with Optimus disabled, the Intel integrated controller seems to disappear:

```
01:00.0 VGA compatible controller: nVidia Corporation GF108 [Quadro NVS 4200M] (rev a1)
```

But apparently, confusingly, this doesn't actually disable the integrated graphics, if I read this right: "[Note that you cannot disable the Intel GPU even with Bumblebee installed]("https://github.com/Bumblebee-Project/Bumblebee/blob/master/README")."

I **was** able to get X running, as root, with the nVidia drivers installed (though I don't remember checking if it was *actually* the nVidia drivers being used).

gmurray13, would you please post the contents of your X configuration (your [FONT="Courier New"]/etc/X11/xorg.conf[/FONT] file), if you have one? Perhaps it will help me. Thanks!

---

### Post by gmurray13 on 2012-01-11
Not much there...but here it is:

Section "InputClass"
        Identifier "middle button emulation class"
        MatchIsPointer "on"
        Option "Emulate3Buttons" "on"
EndSection

Section "InputDevice"
        Identifier     "Mouse0"
        Driver         "mouse"
        Option         "Protocol" "auto"
        Option         "Device" "/dev/psaux"
        Option         "Emulate3Buttons" "yes"
        Option         "ZAxisMapping" "4 5"
        Option         "AutoAddDevices" "off"
        Option         "AllowEmptyInput" "false"
        # generated from default
        #    Option         "Emulate3Buttons" "no"
EndSection

Section "Device"
        Identifier      "Default Device"
        Option  "NoLogo"        "True"
EndSection

---

### Post by gopo on 2012-01-12
> **gmurray13 said:**
> Not much there...but here it is...

Very much appreciated, thanks! I'll give it a try.

---

