---
title: "No desktop, top and bottom panels appear but a black screen"
date: 2010-03-28
forum: Desktop Environments
---

### Post by swedski on 2010-03-28
Hello,
I recently tried to install ubuntu 9.10 on a Compaq Presario 8000 with 512gb and a 40gb hd.
After installation the computer booted but I had a black screen with my bottom and top panels intact so in effect no real desktop.  I tried to change to a different background but to no avail.
When I shut down, the background picture appeared  for two seconds and the machine shut down.

I have tried the kill nautilus idea someone suggested but that did nothing.

I am fairly new to ubuntu and linux.

One weird thing which leads me to believe it is hardware related, I tried to install Mint from a magazine CD and ran it from the CD and sure enough I got the same problem with Mint, and the desktop pic came up just before shutdown

Anyone have a similar problem

---

### Post by ajgreeny on 2010-03-28
I imagine you have an ati graphics card, and that you are:-

1.  running with the open source driver that came on install.
2.  you have a resolution above 1024x768.
3.  you are running the normal desktop effects that ubuntu gives you by default.
4.  you are also running at 24 bit colour, which ubuntu gives as default.

You have one or two options, but first to get a desktop background, use Alt+F2 and type ```
metacity --replace
``` in the box, hit return, and there it should be!

Now look in **System-Administration-Hardware Drivers** to see if any graphics card drivers are available;  I suspect not with a card which gives these symptoms, but you may be luckier than me with the card installed.

Now either
1.  set the system to run without compiz, by going to **System-Preferences-Appearance** and on the Visual Effects tab choose "none".  I like compiz, so I choose other ways of getting the desktop.
2.  reduce the resolution to 1024x768 or below;  I know, that's silly with a big screen, so ignore that!
3.  Reduce the colour depth of the display by making an /etc/X11/xorg.conf file manually and putting in the 16 bit colour depth required.

Here's a copy of the bones of my xorg.conf file for you to use as a template.  Just use your own resolution figures and refresh rates, and give it a try.

```
Section "Device"
    Identifier     "Configured Video Device"
    Driver         "ati"
EndSection 

Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-80
            VertRefresh    50-75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    16
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```

---

### Post by swedski on 2010-03-28
Wow thanks!

I got to the step just before re-writing the xorg and now my desktop works.
Thanks for the help
Swedski

---

