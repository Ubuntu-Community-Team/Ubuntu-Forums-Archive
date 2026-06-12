---
title: "(Howto) Getting around the Black Screen Issue (Ubuntu 12.04 LTS)"
date: 2012-05-07
forum: Desktop Environments
---

### Post by startgame412 on 2012-05-07
Hello, This howto provides a tutorial for getting around the black screen issue which may present itself when one tries to run Ubuntu from live CD or after a fresh installation. What happenes is that the screen goes black after you have made your selection to either run Ubuntu from live CD or install from hard disk. After this selection is made, you may see a blinking cursor briefly and then your screen may display a message such as no signal and go black or it may go black without displaying anything. To get around this issue, you will want to install with the alternate installation CD and after you install the system, make sure that the first boot option is selected in grub 2 and press the e key on your keyboard. Here you want to add the option "nomodeset" without the quotes and the end of the kernel line. This line begins with linux and usually ends with quiet splash. Once you do this you should see the ubuntu splash screen but then you may be presented with a new problem about your monitor being out of range. Here is what you may need to do.

```
sudo service lightdm stop
``` ```
sudo nano /etc/X11/xorg.conf
``` You will now edit the Xorg conf file with the following information.

```
Section "Screen"
    Identifier      "Primary Screen"
    Device          "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
    DefaultDepth    24
    SubSection "Display"
        Depth           24
        Modes   "1280x1024" "1024x768" "640x480"
    EndSubSection
EndSection

```

The above is an example Xorg config file. Replace the values accordingly especially the Modes parameter with the correct screen resolution. Enter the resolution that you know your monitor supports. After you are working with the xorg.conf file, save it and then ```
sudo service lightdm start
``` The desktop environment should load and you should no longer have the problem with the black screen. The problem with the black screen could be because of several reasons one of which I think could be that my computer does not directly support VGA but my monitor supports VGA so I am forced to use a DVI to VGA adapter. This could be the issue but I really do not know. Anyway, I hope this helps someone.

---

### Post by Amndeep7 on 2012-07-05
What happened to me was that some how or other, my xorg.conf file deleted itself, so when it first booted up, it was a black screen.  When I do CTRL+ALT+F7 (after logging in after doing CTRL+ALT+F1, (I'm assuming) the default settings are too big for the screen, so the bottom half turns black and the top half worked for both halves of the screen.  By this I mean that it displayed one half of the screen, and when you moved the mouse to go to where the other half of the screen ought to be, the screen did not fully change and it only updated the view beneath the mouse.  However, by following the instructions you had above, the screen turned back on.  However, I just made the xorg.conf file the same as that of a different computer I have which fixed the problem.  This is my xorg.conf file:

```


Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection

```

Edit:
Actually, it turns out that whenever I reboot, I get the black screen.  However, now the xorg.conf file exists, all I have to do is restart lightdm every single time - which I'm not going to do.  I'll post another edit when I figure out how to solve that problem.

Edit 2:
Turns out that I had to mess with another file (grub default settings) that came about because of the type of netbook that I'm running this on (to help anyone out its an Acer Aspire One AO751h).  Go here for help: [URL="https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo"]https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo
[/URL]

---

