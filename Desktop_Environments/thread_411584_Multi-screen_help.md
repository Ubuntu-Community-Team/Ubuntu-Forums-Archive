---
title: "Multi-screen help"
date: 2007-04-17
forum: Desktop Environments
---

### Post by elchato on 2007-04-17
Hi guys

Im completly new to Ubuntu and to Linux (just migrated today!) and I'm trying to make my laptop (toshiba, single Nvidia video card with 2 outs) work with 2 monitors, and I'd like to be able to switch from the 2 monitors to 1 monitor (can't carry an screen with the laptop!).

I was messing around with xorg.conf... and ended up unable to go back to the graphic interphase and having to reformat and reinstall since I didn't know what else to do...

also, Im not able to get 1280x800 resolution on my laptop since I installed ubuntu... (?)

any help for the n00b?
THANKS A LOT

---

### Post by mojoman on 2007-04-17
First of all, always keep a back-up of your xorg.conf when you're editing it. I suspect that you've already learned that lesson so I might be stating the obvious but a nice and simple way is to copy your xorg.conf to another name, e.g.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.backup.file
```

Then go about freely and edit your xorg.conf. If the computer doesn't boot up properly after your meddling, start it in terminal mode and do
```

sudo cp /etc/X11/xorg.backup.file /etc/X11/xorg.conf
```

and the restart the computer
```

sudo shutdown -r now
```

And you're back on your feet, ready to try once more! (you could, of course, save the changes in the xorg.conf that didn't work in yet another file so that you can view the changes that didn't work).

Now, about your question, are you interested in just having the same output on two monitors (which, I think, is fairly easy) or are you interested in having two monitors sharing the desktop, i.e. a split screen (in which case you probably should be using twinview)?

In the first case, I think you just have two monitor and/or screen sections in your xorg.conf (though I'm not 100% since I've never tried this setup myself). Post your xorg.conf and the specs for your monitors and we'll see what we can come up with.

In the other case, you could have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=301946&highlight=twinview](http://ubuntuforums.org/showthread.php?t=301946&highlight=twinview)

I've had more than my share of woe before I managed to set up my projector as a second monitor using twinview so I might be able to help you out with this setup as well, though I'm not sure it's suitable for a laptop where you only occasionally plug in an extra monitor.

/mojoman

---

### Post by veugelenw on 2007-04-17
I got my multi monitor config working ony after installing this driver (I have a Geforce 4 4200):

```
sudo apt-get install nvidia-glx
```

The driver from the nvidia website did't work for me. (card not supported)

---

### Post by elchato on 2007-04-17
AHHH!!

I had it working, only that it would start on the wrong screen and while trying to change that... went down again, Im writing from the livcd right now.

[PHP]sudo cp /etc/X11/xorg.backup.file /etc/X11/xorg.conf[/PHP]

Are you sure about this command line? Its not working, Says the file doesn't exist.. yes I did verify and both files are very well there.

I don't want to reformat again!!!

---

### Post by mojoman on 2007-04-17
> **elchato said:**
> AHHH!!

I had it working, only that it would start on the wrong screen and while trying to change that... went down again, Im writing from the livcd right now.

[PHP]sudo cp /etc/X11/xorg.backup.file /etc/X11/xorg.conf[/PHP]

Are you sure about this command line? Its not working, Says the file doesn't exist.. yes I did verify and both files are very well there.

I don't want to reformat again!!!

If your backup-file is named "xorg.backup.file" and it is located in the "/etc/X11" then that command is correct and should work. Are you really sure about the name and location of the backup-file?

/mojoman

---

### Post by elchato on 2007-04-17
GOT THEM WORKING!
now I only have to get the startup window in my laptop screen instead of the extra screen... any ideas how to do that? When I try to change "LeftOf" to "RightOf" it doesnt do it... instead it changes the virtual placements of the screens.

Other thing, I'd like to change the screen resolution on my laptop's screen for 1280x800... here's my xorg.conf

```
Section "Device"
    Identifier     "nVidia Corporation G70 [GeForce Go 7600]"
    Driver         "nvidia"
Option "TwinView" "True"
Option "TwinViewOrientation" "RightOf"
Option "UseEdidFreqs" "True"
Option "MetaModes" "1280x800, 1280x800"
Option "UseDisplayDevice" "DFP, CRT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G70 [GeForce Go 7600]"
    Monitor        "KM-718"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

---

### Post by elchato on 2007-04-17
I got the screen resolution down... i just added "1280x800" on every screen subsection...

...now, how can I get the log on window on my lappie instead of the extra screen?

---

### Post by mojoman on 2007-04-17
Under ```
Section "screen"
``` you have  ```
Subsection       "display"
``` where you have ```
Modes      "1024x768" "800x600" "640x480"
```. Try editing the modes-lines (all of them) to

```
modes      "1280x800" "1024x768" "800x600"
```. 

I think that should do it but just in case I'm wrong ... keep a backup ;) 

/mojoman

---

### Post by elchato on 2007-04-17
I have that working already... thanks anyway, really appreciate it!

Any ideas to move my log window?

---

### Post by mojoman on 2007-04-17
I'm sorry if I seem a bit slow but what do you mean with log window?

/mojoman

---

### Post by elchato on 2007-04-17
you know, the startup window...

hmm... like what you normally see when you use only one screen

---

### Post by mojoman on 2007-04-17
Do you mean the login window? I get the startup script and the xubuntu icon on both screens (and when I used ubuntu it was the same) but the login screen only appears on my monitor, which is right where I want it. Are you getting the login window on the wrong monitor?

---

### Post by elchato on 2007-04-17
yes

---

### Post by mojoman on 2007-04-17
Ok. I've always got the login screen on the monitor, except when it didn't start at all, at which point I got it on the projector screen instead. You want the login to appear on the laptops ordinary screen, right?

This is just a long shot but you have a couple of options that I don't have, "UseEdidFreq" and "UseDisplayDevice". Now, you could try to just comment these out. Or (you might want to try out this first) you could shift the "DFP, CRT" to "CRT, DFT".

BTW, you know that you don't have to reboot after each try, right? Just log out, hit ctrl+alt+backspace (to restart x-server) and hopefully log in once it starts up again. Also, if you add # in front of a line in a configuration file that line is not read by the system. This is very handy if you later decide to add that option again or for keeping memory notes in your configuration files.

/mojoman

---

### Post by mojoman on 2007-04-17
One more idea. There is an option to state the refresh rate for the second monitor
```

Option "SecondMonitorHorizSync"   "<hsync range(s)>"
Option "SecondMonitorVertRefresh" "<vrefresh range(s)>"
```

That might be enough to get the system to understand that the other monitor is the first monitor, i.e. where the login screen should appear.

---

### Post by elchato on 2007-04-17
Tried all of them... still the same

---

### Post by elchato on 2007-04-17
bump

---

### Post by Jhongy on 2007-04-18
I toiled with multiple monitors for a while, until I stumbled upont he following nVidia page. It looks a bit daunting, but read it through, particularly the "metamodes" part, and the link to the appendix so you can figure out the device names of your connected monitors (CRT-0, DFP-0, DFP-1, etc). The line TwinViewOrientation "Clone" is also important I think.


It's a bit dated (for XFree86), but --- I followed a number of tutorials on this site regarding TwinView, Xinerama, etc, and none seemed to work. Following this one through and understanding the bits I needed in the xorg.conf file helped immensely.

[http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-g.html](http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-g.html)


j

---

