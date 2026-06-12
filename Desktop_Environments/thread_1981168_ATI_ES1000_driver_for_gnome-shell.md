---
title: "ATI ES1000 driver for gnome-shell"
date: 2012-05-16
forum: Desktop Environments
---

### Post by snotplop on 2012-05-16
Hey mods! This is a copy of a thread I just started over in "Server Platforms". I figure that since this is dealing specifically with getting a GUI working that it fits here in "Desktop Environments" as well. Please feel free to punish as needed ^.^
Original thread: [http://ubuntuforums.org/showthread.php?p=11941002](http://ubuntuforums.org/showthread.php?p=11941002)
------------------------------------------------------------------------------------------------------------------

Hey all,

Building up an Ubuntu 12.04 LTS server for my job;
our needs require that we have a gui, so I decided to go with gnome-shell since it's just so darn pretty. :smile: Problem is that support for ATI cards seems to be moving more towards a wasteland with each successive release of ubuntu... :sad:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) - is really not helpful in any way, although it at least attempts to document the situation...

Our server is an HP Proliant DL380 G7, and lspci reports:
```

 $ lspci -vv | grep -E "VGA.*controller" 01:03.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI ES1000 (rev 02) (prog-if 00 [VGA controller]) 
```Using the "preferred" method of self, automagic configuration, I'm  just getting dropped into the proverbial "There is a problem with your  display" message with several not-very-helpful options, just after  lightdm comes up, but all before I'm granted a greeter.


Here's what I've done so far to metamorphosize ubuntu server-minimal into one with a gui:
```
$ sudo apt-get install ubuntu-desktop gnome-shell
$ sudo update-rc.d lightdm defaults
$ sudo apt-get remove ubuntu-desktop network-manager
$ sudo telinit 6
    <broked>
$ grep -E "\(EE\)" < /var/log/Xorg.0.log
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    17.328] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    17.433] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    17.947] (EE) AIGLX error: Calling driver entry point failed
[    17.947] (EE) AIGLX: reverting to software rendering
```Funny that... By reading the Ubuntu documentation above I thought  that 12.04 prefers the open source radeon driver and *not* fglrx..?
Let's force it to use "radeon" by crafting a quick n' dirty /etc/X11/xorg.conf:
 ```
$ cat xorg.conf
Section "ServerLayout"
    Identifier     "single head configuration"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
       Option    "XkbLayout" "us"
EndSection

Section "Device"
    Identifier  "Videocard0"
    Driver      "radeon"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Videocard0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth    24
    EndSubSection
EndSection
$ sudo telinit 6
$ grep -E "\(EE\)" < /var/log/Xorg.0.log
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    15.292] (EE) AIGLX error: Calling driver entry point failed
[    15.292] (EE) AIGLX: reverting to software rendering
```No beans.
Hmm... maybe fglrx is actually the way to go...?

 ```
$ sudo apt-get install fglrx
$ cat /etc/X11/xorg.conf
Section "ServerLayout"
    Identifier     "single head configuration"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
       Option    "XkbLayout" "us"
EndSection

Section "Device"
    Identifier  "Videocard0"
    Driver      "fglrx"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Videocard0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth    24
    EndSubSection
EndSection
$ grep -E "\(EE\)" < /var/log/Xorg.0.log
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   217.205] (EE) No supported AMD display adapters were found
[   217.205] (EE) No devices detected.
[   217.211] (EE) No supported AMD display adapters were found
[   217.380] (EE) GLX error: Can not get required symbols.
```Mreow... :sad: Anybody have any ideas?

---

### Post by QIII on 2012-05-16
Not sure what ATI wasteland you think Ubuntu is moving to, but you must be unfamiliar with the blatant and public display of affection between Canonical and AMD/ATI every fourth and tenth month.

The ES1000 is no longer supported by ATI in Linux.

---

### Post by snotplop on 2012-05-16
> **QIII said:**
> Not sure what ATI wasteland you think Ubuntu is moving to, but you must be unfamiliar with the blatant and public display of affection between Canonical and AMD/ATI every fourth and tenth month.

What is the model of your GPU?

Indeed I am unfamiliar with the development; ATI's website is devoid of any mention of linux in their "drivers" section and the haphazard official ubuntu post from above doesn't lend much confidence... NVIDIA ftw  for more than a decade ^.^

Anyway, from lspci, it appears to be an ATI ES1000 (aka: RV100,                       Radeon 7000(VE), M6, RN50/ES1000). This card is nothing special; it's onboard and on a server, but it would be wonderful if we could get some proper direct rendering :)

Tx!

---

### Post by snotplop on 2012-05-16
> **QIII said:**
> The ES1000 is no longer supported by ATI in Linux. ==> Wasteland. This server is a current product :( gg ATI

---

### Post by QIII on 2012-05-16
NVIDIA has legacy cards, too.

As far as NVIDIA for the win, there is a lot of FUD about ATI out there.  It lingers from a time when ATI was ATI and before it was bought by AMD.

The fglrx driver works very well for the more recent, and still supported, cards.  I dispel the FUD daily on this forum and show posters how very easy it is to get the ATI cards to work -- with full hardware acceleration and H.264.  NVIDIA has no corner on the hardware acceleration market.

Your card is no longer supported by its manufacturer and has no official Linux driver.  Many NVIDIA owners face the same difficulty.

The open source driver developers can only do so much looking into a black box.  They have done, and continue to do, an astounding job given their task.  You'll have to use that, blemishes and all.

---

### Post by QIII on 2012-05-16
> **snotplop said:**
> ==> Wasteland. This server is a current product :( gg ATI

The lack of support is from ATI, not Ubuntu.  Again, the card is not supported in Linux by its OEM.

---

### Post by QIII on 2012-05-16
> **snotplop said:**
> ATI's website is devoid of any mention of linux in their "drivers" section...

Oh?  Is it?

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

I do not wish to sound contrary, but I really dislike FUD.  Both about NVIDIA and ATI.  Both make fine products and provide fine drivers.

It is a simple business decision on the part of both ATI and NVIDIA to choose which cards they will continue to spend time on.  They make conscious decisions about cost/revenue and find that some expenditures simply make no business sense.

AMD has long been a member of the Linux Foundation and NVIDIA recently became one.  Neither ignores Linux.  They make business decisions.  BOTH of them.

---

