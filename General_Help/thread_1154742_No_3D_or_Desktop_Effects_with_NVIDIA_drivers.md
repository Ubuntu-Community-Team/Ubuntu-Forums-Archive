---
title: "No 3D or Desktop Effects with NVIDIA drivers"
date: 2009-05-10
forum: General Help
---

### Post by bbritt66 on 2009-05-10
Hello,

I have an HP Pavilion 752n and have a PCI GeForce FX 5500 graphics card installed. All the effects worked just fine in 8.04 with the driver from NVIDIA's site. However, after switching to 9.04, the card is supposedly recognized and offers the 173.14.16 driver. I accepted and activated it, but no compiz effects, can't even get any Desktop effects at all in Appearance. So I tried installing the same driver from NVIDIA's site, still no success. Then I tried 173.14.18 from NVIDIA, still no success. So I uninstalled everything (one at a time install, uninstall of course) and went back to the driver Ubuntu suggests. That is what is running now, but there are no effects.

When I try to do anything at all with the tool NVIDIA X Server Settings, it says that it is unable to parse the existing X file, even if done with sudo.

My xorg.conf file consists of simply the following:

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
	Driver	"nvidia"
EndSection

and that's it. Any suggestions? I can not afford to go out and by another card and I prefer not to have to go back to 8.04.

Thanks in advance

---

### Post by Legace on 2009-05-10
> **glennric said:**
> Anyway, I figured it out.  I had compiled and installed the nvidia 173.14.18 drivers in Intrepid, and when I upgraded it installed the nvidia 173.14.16 drivers that are the default in Jaunty.  This caused a conflict the set the default desktop window manager to metacity in gconf.  I changed that (and of course uninstalled the 173.14.18 drivers and reinstalled the 173.14.16 drivers) and now it works.  

Now I have rebuilt the 173.14.18 drivers for Jaunty and those are running fine.  I will put these in my ppa soon.  Hopefully these get included in Jaunty soon as the 173.14.16 drivers have some bugs that are rather annoying.

Here is his PPA, btw:
[https://launchpad.net/~glennric/+archive/ppa/+sourcepub/601558/+listing-archive-extra](https://launchpad.net/~glennric/+archive/ppa/+sourcepub/601558/+listing-archive-extra)

---

### Post by bbritt66 on 2009-05-11
> **Legace said:**
> Here is his PPA, btw:
[https://launchpad.net/~glennric/+archive/ppa/+sourcepub/601558/+listing-archive-extra](https://launchpad.net/~glennric/+archive/ppa/+sourcepub/601558/+listing-archive-extra)

Ok, I tried this, with those packages. Twice. Still no success. I know the card works. It was working fine in 8.04. Any other advice/suggestions would be greatly appreciated.

Thanks!

---

### Post by CatKiller on 2009-05-11
> **bbritt66 said:**
> I accepted and activated it, but no compiz effects, can't even get any Desktop effects at all in Appearance.

Do you get any relevant error messages if you run gnome-appearance-properties from a Terminal and try to enable the effects?

---

### Post by bbritt66 on 2009-05-11
> **CatKiller said:**
> Do you get any relevant error messages if you run gnome-appearance-properties from a Terminal and try to enable the effects?

Yes, interesting too. I noticed GLX wasn't working... seems my card has been "blacklisted". Following is the message:


There is no available graphics driver for your system which supports the composite extension, or the current one already supports it.
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2562' found 
aborting and using fallback: /usr/bin/metacity

And that's it. Does that mean I'm just out of luck with any Ubuntu release beyond 8.04?

---

### Post by zolistir87 on 2009-05-11
I don't know about you, but it seems to me that your xorg.conf is kinda short.

Try doing the following:(assuming you have nvidia driver and nvidia x server settings installed)

Open up: System->Administration->NVIDIA X Server Settings.

Do the desired setup and then press "Save to X Configuration File". Now for some reason this didn't work out so well for me so I did the following. In the dialog that appeared when you press save there is a button "Show preview". I copied the code displayed by it, and edited, then saved xorg.conf manually.

Try this and see what happens.

---

### Post by bbritt66 on 2009-05-11
> **zolistir87 said:**
> I don't know about you, but it seems to me that your xorg.conf is kinda short.

Try doing the following:(assuming you have nvidia driver and nvidia x server settings installed)

Open up: System->Administration->NVIDIA X Server Settings.

Do the desired setup and then press "Save to X Configuration File". Now for some reason this didn't work out so well for me so I did the following. In the dialog that appeared when you press save there is a button "Show preview". I copied the code displayed by it, and edited, then saved xorg.conf manually.

Try this and see what happens.

I did this, and now my xorg file looks more like a real xorg.conf file should, but still no success. Still the same error as above when trying to enable Desktop effects, not to mention Compiz. I also noticed in the tool NVIDIA X Server Settings tool under the OpenGL/GLX info that Direct Rendering is ="NO"... isn't that odd? Shouldn't that be YES if the driver is working? I've noticed it with any of the drivers I've been told to use, it's always no and I always get the message that no drivers were found to handle effects. So even though it sees the card, even in the error message, the drivers don't work. I know this has to have something to do with the newer version of X and also the newer kernel, as I stated before, it worked perfectly in 8.04 with NVIDIA's driver, but I really don't want to downgrade, and I also can't afford another card.

Not to seem grumpy or anything, honestly, but I shouldn't have to buy another card anyway, I know if I downgraded it would work (though not with the drivers provided by Ubuntu, it never has, even when I tried 8.10) but with 8.04 and NVIDIA's own drivers it worked. Now it won't work with any driver. I hate Windows, and only bring it up to point out a fact of the card being operational, but it will work in Windows as well. I use Ubuntu and FreeBSD for everything, the only reason a window's box is in the house is for my kids to play games on, but the card will work in it. Basically all I'm saying is that the card is fine. Something else is going on with it, like the new X server and/or kernels.

By the way, here is what my xorg.conf file looks like now:

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder63)  Mon Mar  2 12:46:46 PST 2009

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Mon Mar  2 12:45:55 PST 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 85.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5500"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by Ceiling Fan Man on 2009-05-11
I JUST got finished battling this problem with nvidia-settings... Here's what I did:

**1)** open a terminal
**2) sudo mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup**
**3) sudo nvidia-settings**
*[Attempt to save, clicked Preview, copied the contents to a temporary TXT file for safe keeping during the procedure, close nvidia-settings]*
**4) sudo gedit /etc/X11/xorg.conf**
*[Paste all contents from the preview and save]*

As for your drivers, I've always had good luck with Envy. Using Terminal, type:
**sudo apt-get install envyng-core**
then
**envyng -t**

At this point a series of easy-to-follow instructions will appear. It will give you a list of available drivers, and there will be columns for "Compatible" and "Recommended" with either a **-** or a **+** in them for each driver. Ideally, you want to pick the driver with both columns being **+**.

From my experience, this seems to work better than "System > Administration > Hardware Drivers."

---

### Post by bbritt66 on 2009-05-11
> **Ceiling Fan Man said:**
> I JUST got finished battling this problem with nvidia-settings... Here's what I did:

**1)** open a terminal
**2) sudo mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup**
**3) sudo nvidia-settings**
*[Attempt to save, clicked Preview, copied the contents to a temporary TXT file for safe keeping during the procedure, close nvidia-settings]*
**4) sudo gedit /etc/X11/xorg.conf**
*[Paste all contents from the preview and save]*

As for your drivers, I've always had good luck with Envy. Using Terminal, type:
**sudo apt-get install envyng-core**
then
**envyng -t**

At this point a series of easy-to-follow instructions will appear. It will give you a list of available drivers, and there will be columns for "Compatible" and "Recommended" with either a **-** or a **+** in them for each driver. Ideally, you want to pick the driver with both columns being **+**.

From my experience, this seems to work better than "System > Administration > Hardware Drivers."

Ok, I followed those instructions, still no success so what I did was uninstall ***everything*** having to nvidia with purge, rebooted, then reinstalled everything, rebooted again and followed the instructions above again. Still nothing. Same errors as posted previously. It sees the card, but then when trying to enable Desktop Effects it says no drivers available or simply "could not enable effects". The resolution changes when the driver is installed, but that's it, no 3D, no Direct Rendering, no effects, no nothing. I'm stumped. Thanks for all the replies and if anyone has any more advice it would be greatly appreciated!

Thanks in advance.

---

### Post by bbritt66 on 2009-05-11
I've been searching around for answers and came across this from hawkhock on the Ubuntu threads, that user has the same card I do, although he/she is referring to Ubuntu8.10 but I think it applies to 9.04 as well unfortunately. Here is what was in the post:

[COLOR="Blue"]I concur with piratebill. After three days of reading posts and searching the forum, I learned that support for Nvidia GeForce FX5500 (which I have) has been discontinued. This may be the same case for you.

The best driver available for FX5500 is 173 and it is not compatible with 8.10. Advice given to me was to downgrade to 8.04 which I did in order to run 3D packages.

If you find solution for your problem, would be interested to hear about it as it may also work for me.[/COLOR]

[COLOR="Black"]So I was wondering, if this is the case and it's hopeless in any Ubuntu distro after 8.04, (and I don't want to make anyone mad here, it's just a question) does anyone know of a distro that WILL support my card? I'm searching around now. Thanks![/COLOR]

---

### Post by zolistir87 on 2009-05-12
Even if your card it discontinued should work. That only means that no more updates or support will be given for this card, not that stuff that worked will not work anymore. Compiz is not Vista, you don't need pixel shaders or anything to run those effects. I got compiz(and/or beryl) running once on a Geforce 4 MX. Checked compiz-fusion wiki, and your card is not on their blacklist. I'm out of ideas right now, but you should keep trying.

---

### Post by bbritt66 on 2009-05-12
Well good news and bad news. Good news is Fedora 10 will work, you just have to configure grub with nopat, otherwise it won't boot, but nonetheless it works. So it's not just the newer kernels and X servers, it's something with Ubuntu. 

Bad news is, I don't like Fedora so I'll be taking it off. I've used Ubuntu for a years. I only joined these forums when 8.10 came out because it had problems with older cards as well. For now, until I find a distro that I like (or Ubuntu makes older cards work without the user having to do back-flips) I guess I'll go back to Ubuntu 8.04. I really like Ubuntu, I even have it installed in some of my clients' offices, as servers. There are many, many people out there who don't have bleeding edge hardware (like me, and my clients). So my reasoning is this... if Fedora can make it work, so can Ubuntu if they wanted to. So I'll hang back with 8.10 until I find another distro that will work like it should without costing so many man hours. On my personal computers, it's not that big of a deal, but with the new releases, I can't recommend it anymore to anyone with older hardware (and it's not even THAT old, really).

Not trying to trash Ubuntu, I loved it. I guess I'm just upset that I have realized that beyond 8.04, there is no upgrading for me with Ubuntu unless I buy a new card or computer. It just made me wonder why if Fedora can do it, why can't Ubuntu?

Thanks for all the replies. And if anyone comes up with a fix for this, let me know please. I would LOVE to still be able to use Ubuntu!

---

### Post by zolistir87 on 2009-05-13
Well if you find a distro which works better with your hardware, just use that one. Use whatever works for you. Have you tried the other big distros out there? openSUSE maybe? Maybe it will work out for you(If your worried about the whole KDE thing, yes it has GNOME too).

---

### Post by bbritt66 on 2009-05-14
> **zolistir87 said:**
> Well if you find a distro which works better with your hardware, just use that one. Use whatever works for you. Have you tried the other big distros out there? openSUSE maybe? Maybe it will work out for you(If your worried about the whole KDE thing, yes it has GNOME too).

Well, I didn't want to have to go with a RPM oriented distro, but Fedora has the edge here. Maybe if the Ubuntu developers decide to support hardware like that again then I can switch back because I really liked Ubuntu.

By the way, thanks everyone for the replies and help!

---

