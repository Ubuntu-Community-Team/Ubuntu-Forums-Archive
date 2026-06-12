---
title: "Switching Xscreen"
date: 2008-12-16
forum: General Help
---

### Post by MarcusAntonius on 2008-12-16
I have a TV in another room which I want to use for watching movies. I set it up as a second xscreen via the nvidia-settings manager, and the picture is fine.

Now the problem: If I would want to start a video I would need to see the  television, which is impossible (since it is in another room). Is there a way to view this second xscreen via my computer monitor?

I thought ctrl+alt+f8 would do the job, but I only get a black screen (also with the other fs).

Does someone have a suggestion/solution?

---

### Post by MarcusAntonius on 2008-12-17
Or let me rephrase my question:

When pressing Ctrl+Alt+F8 am I supposed to switch to the second xscreen?

---

### Post by MarcusAntonius on 2008-12-18
Here my xorg.conf
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen1"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "FUS P19-2"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GT"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"

# Removed Option "TwinView" "1"
# Removed Option "metamodes" "TV: nvidia-auto-select +0+0, DFP: 1280x1024 +0+0; TV: nvidia-auto-select +0+0, DFP: nvidia-auto-select +0+0"
    Identifier     "Screen1
    Device         "Device1"
    Monitor        "Monitor1
    DefaultDepth    24
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "TwinView" "0"
    Option         "metamodes" "TV: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0
    Device         "Device0"
    Monitor        "Monitor0
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP: 1280x1024 +0+0; DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by MarcusAntonius on 2008-12-20
Does nobody have an idea? I'm sure there are more people facing the same problem... If my question doesn't make sense, please tell me.

In the meantime I found one way, to play video files on the second xscreen:
"DISPLAY=:0.1 mplayer -fs filename"

This works perfect, but unfortunatly only for local files. For streaming videos I still don't know how to do it...

---

### Post by SteveDee on 2008-12-29
> **MarcusAntonius said:**
> Does nobody have an idea? I'm sure there are more people facing the same problem... If my question doesn't make sense, please tell me.

In the meantime I found one way, to play video files on the second xscreen:
"DISPLAY=:0.1 mplayer -fs filename"

This works perfect, but unfortunatly only for local files. For streaming videos I still don't know how to do it...

I have a similar problem, but I can at least see the right hand side of the TV screen if I stretch across the chimney breast!

Having the computer in the same room as the tv is useful when we need to hit <space> to pause the video.

But I too would like to be able to launch SMPlayer on the monitor, then drag, click or otherwise move it over to the TV.

---

### Post by SteveDee on 2008-12-29
I thought it might be possible to use VNC to view the TV screen on the monitor.

However, if I run Vinagre from the monitor using a :0.1 suffix I only see the monitor (on the monitor).

If I run Vinagre on the TV screen, I can then see the monitor on the TV screen, but this is the opposite of what I need.

In other words Vinagre always seems to default to the main display. There must be  a solution to this.

---

### Post by SteveDee on 2008-12-30
OK, I've now got this working on my twinview system so that I can run and control SMPlayer (on the TV screen) from the computer monitor screen via Vinagre. The answer is not to enter a "display.screen" value, but simply the screen number.

Configure remote access via System > Preferences > Remote Desktop > General 
 - Allow other users to view & control your desktop.
 - You can also create a password.

On the monitor, start Vinagre (Applications > Internet > Remote Desktop Viewer).
Select "Connect" and enter "{computer name}.local:1"
Enter password (if you've set one up in Remote Desktop Preferences above).

You can now start your preferred video application on the TV screen via the Remote Desktop Viewer, select a video and control the player.

---

### Post by MarcusAntonius on 2009-01-02
That's great, I didn't think of using Vinagre. Thank you very much.

Just because I am curious: Do you think it should work in theory switching the screens with CTRL+ALT+F8 or is this something different?

---

### Post by SteveDee on 2009-01-02
> **MarcusAntonius said:**
> That's great, I didn't think of using Vinagre. Thank you very much.

Just because I am curious: Do you think it should work in theory switching the screens with CTRL+ALT+F8 or is this something different?

I find the whole issue of screens, displays & virtual screens rather confusing. Well you can tell I'm confused, I said I had a TwinView setup, but clearly I don't.

I have 2 separate X servers driving 2 physical display devices, where each screen is unique and the mouse pointer is able to traverse from one screen to the other.

As I understand it, on Linux the <ctrl><alt><F8/7> sequence normally switches between virtual screens (rather than physical screens). But see: [http://brainstorm.ubuntu.com/idea/9522/](http://brainstorm.ubuntu.com/idea/9522/) as this may not be the case with Ubuntu.

On my single screen system, this <ctrl> sequence gives me a black & white screen I can't do much with. On my dual screen system the display blanks for a second or so then recovers.

So in summary, I don't think this <ctrl> sequence will help when you have 2 physical displays.

---

### Post by SteveDee on 2009-02-18
> **SteveDee said:**
> OK, I've now got this working on my twinview system so that I can run and control SMPlayer (on the TV screen) from the computer monitor screen via Vinagre. ......

Here is a much better way of doing this: [http://ubuntuforums.org/showthread.php?t=1073242](http://ubuntuforums.org/showthread.php?t=1073242)

---

### Post by nidelius on 2009-03-25
you could put the mouse over to the second X screen and then hit alt + F2 to launch the run dialog. Then run the command to start the application directly in the second X-screen without any DISPLAY parameters.
Just a little something that might be useful.

---

