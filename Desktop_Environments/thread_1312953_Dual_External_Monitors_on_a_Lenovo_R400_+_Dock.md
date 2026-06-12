---
title: "Dual External Monitors on a Lenovo R400 + Dock"
date: 2009-11-03
forum: Desktop Environments
---

### Post by Scabby_al on 2009-11-03
I recently installed Ubuntu 9.10 and have been very happy with it. I've gotten dual monitors to work in Gnome but I want to convert to XFCE. I like that it's lighter, you can right click to access the menu and minimize to the desktop so I don't need any panels. I attempted to use xrandr and gnome-display-properties in XFCE with no success and the display applet only shows one monitor. 

tl;dr

Hardware:
* Lenovo R400 with integrated Intel video card docked in a full size Lenovo dock.
* Two external monitors connected. One via DVI and one VGA.

What I want to do:
* Span my XFCE desktop across both monitors and turn off the laptop display.


Thanks in advance for any help. I've been looking all over these boards and Google and couldn't find an answer unique to my set up.

---

### Post by Untitled_No4 on 2009-11-03
Hi,

Although I don't use XFCE and don't have an R400, the process to get those two screens working is similar. Since ThinkWiki.org have already explained most of what you have to do I think it's best if you have a look on their page:
[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2")

The only thing missing from this page is that the current Ubuntu versions don't have a default xorg.conf file and you need to create one which is done by running
```
sudo X -configure
``` while X is not working. This will create a xorg.conf.new file in the home folder of the user running the command. You need to edit this file (you can delete everything that is not necessary for the dual screens and add the sections outlined in ThinkWiki) and save it as xorg.conf

For reference, here is the xorg.conf file I ended up with:
```

Section "Device"
  Identifier    "ATI 1"
    Option "Monitor-DVI-0" "Monitor 1"
    Option "Monitor-DVI-1" "Monitor 2"
  EndSection

  Section "Monitor"
    Identifier    "Monitor 1"
  EndSection

  Section "Monitor"
    Identifier    "Monitor 2"
  EndSection

  Section "Screen"
    Identifier    "Screen 1"
    Monitor       "Monitor 1"
    Device        "ATI 1"
    SubSection "Display"
      Depth           24
      # big virtual screen to place
      Virtual         2560 1024 
    EndSubSection
  EndSection

```

My setup has an ATI card, two DVI screens of 1280 x 1024 each. The Virtual bit should be your screen width in pixels X 2 and the height.

Just in case, if once you have your new xorg.conf in place X doesn't start it means something is wrong with the file and you should remove/rename it and check what is wrong and try again.

Since I'm not currently using the computer I did that for I am working from memory, so if something is not clear let me know and I'll write a more detailed reply with all the steps I've taken.

P.S.

---

### Post by Scabby_al on 2009-11-04
Thanks for the quick response! I'll try it today and let you guys know if it works!

---

### Post by Scabby_al on 2009-11-04
I was able to use xrandr to turn off the laptop display (which didn't stick but I believe I need to write a script on boot to have that happen) and configured my xorg.conf with no success. Do I need to use the same identifiers in xorg.conf as are used in the xrandr output? (example: VGA1, HDMI2, etc.)

---

### Post by Untitled_No4 on 2009-11-04
Yes, your screen identifiers in xorg.conf should respond to the ones in xrandr, so if your screens are VGA1 and DVI1 your xorg.conf should look something like that:
```

Section "Device"
  Identifier    "ATI 1" ## Your graphic card identifier here
    Option "Monitor-VGA1" "Monitor 1"
    Option "Monitor-DVI1" "Monitor 2"
  EndSection

  Section "Monitor"
    Identifier    "Monitor 1"
  EndSection

  Section "Monitor"
    Identifier    "Monitor 2"
  EndSection

  Section "Screen"
    Identifier    "Screen 1"
    Monitor       "Monitor 1"
    Device        "ATI 1" ## Again, your identifier here
    SubSection "Display"
      Depth           24
      # big virtual screen to place
      Virtual         2560 1024  ## Change this to reflect the size of the combined screens
    EndSubSection
  EndSection

```

Log out and back in and run xrandr and the screen identified as Monitor 1 (VGA1 in the above case) should have a maximum size of the combined screens. 
Once you get the screens as you like them you can automate the process. Check out the section titled "Now automate it on login" which has an example of a script which identifies which monitors are connected and sets the output accordingly.

---

