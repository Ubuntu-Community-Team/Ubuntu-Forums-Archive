---
title: "Can't change screen resolution."
date: 2011-03-13
forum: Desktop Environments
---

### Post by Kin2InuYasha on 2011-03-13
I've recently installed Ubuntu 10.10 on an old Dell computer I have.  Everything seems to work fine, but I can't seem to change the screen  resolution. In the monitor Preferences it says Monitor:Unknown. It's  stuck on 1600x1200 and I'd like it to be closer to 1024x768

I've tried changing the xorg.conf file to no avail. I've been browsing for 3 days now looking for a solution.

Any help is appreciated.

[http://hamsterhutt.host56.com/WHATACOM-4ACEC222.xml](http://hamsterhutt.host56.com/WHATACOM-4ACEC222.xml)
These are my specs if it helps any, please ignore the windows installation info because I have it installed alongside ubuntu.

---

### Post by Krytarik on 2011-03-13
Try following this guide:
[https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions)

Greetings.

---

### Post by Kin2InuYasha on 2011-03-13
> **Krytarik said:**
> Try following this guide:
[https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions)

Greetings.

This method doesn't seem to work for me. I follow the instructions, and I get a new resolution in the monitor preferences, but when I try to load it I get a an error "configure crtc 0 failed" and "The selected configuration could not be applied"

I heard that the crtc 0 failed error was because the refreshrate was too high, but I've set it as low as 30 and it still doesn't work.

---

### Post by Krytarik on 2011-03-13
Are you able to add/apply the mode with the xrandr commands?

---

### Post by Kin2InuYasha on 2011-03-13
> **Krytarik said:**
> Are you able to add/apply the mode with the xrandr commands?

I can add, but cannot apply. It gives me the option of another resolution in the monitor preferences immediately after I complete the commands, but when I try to apply that resolution It gives me an error "The selected configuration could not be applied"

---

### Post by Krytarik on 2011-03-14
You should apply the added mode with the the respective xrandr command, not through the GUI, since I am not sure if that would work also.

Could you please post the output of "xrandr" and which commands you use, and the output of them. Please use the code-tags therefore (the #-button in the editor).

---

### Post by Kin2InuYasha on 2011-03-14
```
robbie@Whatacomputer:~$ gtf 1024 768 59

  # 1024x768 @ 59.00 Hz (GTF) hsync: 46.90 kHz; pclk: 63.04 MHz
  Modeline "1024x768_59.00"  63.04  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync

robbie@Whatacomputer:~$ xrandr --newmode potatoes 63.04  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync
xrandr: Failed to get size of gamma for output default
robbie@Whatacomputer:~$ xrandr --addmode default potatoes
xrandr: Failed to get size of gamma for output default
robbie@Whatacomputer:~$ xrandr --output default --mode potatoes
xrandr: Failed to get size of gamma for output default
xrandr: Configure crtc 0 failed
robbie@Whatacomputer:~$ 

```This is how I've understood it to the best of my abilities. Like I said, doing this will show the 1024x768 resolution in the monitor preferences, but will not allow me to apply it. It also doesn't save the settings after a reboot.

---

### Post by Krytarik on 2011-03-14
First, you should use "cvt" instead of "gtf" to get the modeline, as I understood that "cvt" is more appropriate.

And I did websearch about the error messages you are getting.

I would like to make sure that you are running the correct driver. Please post the output of:
```
lshw -c video
```Also check if a "/etc/X11/xorg.conf" is present, it shouldn't. But if it is, post its content as well.

Then, why are you trying to set the mode to specifically 59 Hz? If you just leave that away (default is 60 Hz), does it work then?

---

### Post by Kin2InuYasha on 2011-03-14
```
root@Whatacomputer:/home/robbie# lshw -c video
  *-display               
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:e8000000-efffffff memory:feb80000-febfffff

```It's not an LCD monitor, it's an old crt I had lying around. I know it's capable of a 1024x768 resolution because my Windows installation on it worked, right?

I do have a xorg.conf file, I don't remember whether it was already there, or whether I created it when I was trying to fix this issue a few days ago. It isn't original though.

```
Section "Monitor"
    Identifier    "Configured Monitor"
      Option      "DPMS"  "true"
      HorizSync    30.0-60.0
      VertRefresh  50.0-70.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
      DefaultDepth      24
      SubSection "Display"
                  Depth         24
                  Modes         "1024x768" "800x600"
      EndSubSection
      
EndSection
```And as far as the Refreshrate, I thought that maybe 60 was too high and causing problems, so I set it to 59. I will use 60 from now on.

Thank you for responding so quickly.


::UPDATE::
Using cvt with this same method changed nothing.

---

### Post by Krytarik on 2011-03-14
Oh, I somewhat assumed (out of my experience here in the forums), that I'm almost the only one who is still using a CRT. ;-)

And correction: It seems like "cvt" is *always* the better choice, so take it instead.

Please at least rename your "xorg.conf".

And yes, you are running the intel driver. I would like to upgrade it to the most recent version:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```Then reboot/relogin.

Also, you should always try to run a CRT at least at 75 Hz. Please check if it runs with that mode in Windows7.

---

### Post by Kin2InuYasha on 2011-03-14
Still rockin CRT's and XP's here buddy. lol But yes, I will try that and respond again shortly.

Rename, or delete xorg.conf completely? If that's what you mean, how do I go about doing this?

---

### Post by Krytarik on 2011-03-14
> **Kin2InuYasha said:**
> Still rockin CRT's and XP's here buddy. lol But yes, I will try that and respond again shortly.

Rename, or delete xorg.conf completely? If that's what you mean, how do I go about doing this?
LOL How did the "7" slip through?! :P

Ah, since it looks like you copied the xorg.conf from somewhere, simply delete it:
```
sudo rm /etc/X11/xorg.conf
```It may be that the monitor specs included in it are not correct, and therefore cause those errors.

---

### Post by Kin2InuYasha on 2011-03-14
Well, the update didn't change anything, on windows it lists that the monitor has 60, 70, 75, 85, and 100 MHz capability. I've deleted the xorg.conf file. Rebooted, nothing has changed.

I also tried using the xrandr technique using 75 MHz, rebooted, nothing. Things are looking grim.

---

### Post by Krytarik on 2011-03-14
The changes you make with the xrandr commands *don't preserve* after shutdown/reboot. If we get them working, you will have to add them to GDM's startup script, see the guide therefore.

When you run the commands now, do you still get the error "xrandr: Configure crtc 0 failed"?

---

### Post by Kin2InuYasha on 2011-03-14
> **Krytarik said:**
> When you run the commands now, do you still get the error "xrandr: Configure crtc 0 failed"?
Yes.

Again, I don't know if this helps or not.. I've downloaded a program from the software center called "Monitor Settings" and when it loads all it says in the window is "The current monitor is in the database but does not support DDC/CI

It then says that I should try plugging the chord into another slot on the monitor..... it's a CRT, the chord is built into it.

---

### Post by Krytarik on 2011-03-14
> **Kin2InuYasha said:**
> 
Again, I don't know if this helps or not.. I've downloaded a program from the software center called "Monitor Settings" and when it loads all it says in the window is "The current monitor is in the database but does not support DDC/CI

It then says that I should try plugging the chord into another slot on the monitor..... it's a CRT, the chord is built into it.
No, that doesn't help.

Thanks for updating your profile, funny pic, and I even see where you live now, really late there now, and quite early again here.

I noticed, that I failed to derive "crtc" to CRT. ;-)

Although it is a bit more complex, I would like to try to set up a correct "xorg.conf", basically in order to pass the monitor specs, HorizSync and VertRefresh, maybe it helps.

To get those values, try both
```
xvidtune
```press "Cancel"!

and
```
sudo apt-get install hwinfo
hwinfo --monitor
```Then set up the xorg.conf by following the guide, you may use its included example as template. Then post it here, so that I can take a look.

I need to take a sleep now, maybe you too.

---

### Post by Kin2InuYasha on 2011-03-14
Yeah, I'm used to working at night, so I'm not phased, I will probably stay awake until around noon. 

Yes, I will give this a try and report back shortly. I appreciate you sticking with me and not getting frustrated with me. Have a good sleep.

---

### Post by Krytarik on 2011-03-14
> **Kin2InuYasha said:**
> Yeah, I'm used to working at night, so I'm not phased, I will probably stay awake until around noon. 

I'm also living the other way around currently.
> **Kin2InuYasha said:**
> 
Yes, I will give this a try and report back shortly. I appreciate you sticking with me and not getting frustrated with me. Have a good sleep.
Take your time! Frustrated?...No, I like technical challenges! :)

---

### Post by Kin2InuYasha on 2011-03-14
Well, this is embarrassing. I seem to have broken Ubuntu. I replaced the xorg.conf with one I edited and now Ubuntu won't let me log in, just a black screen. 

I'll see if I can find a work around for this.

---

### Post by Grenage on 2011-03-14
> **Kin2InuYasha said:**
> Well, this is embarrassing. I seem to have broken Ubuntu. I replaced the xorg.conf with one I edited and now Ubuntu won't let me log in, just a black screen. 

Help??!?!

Just delete your xorg.conf (did you back up the old one?) and it should boot up normally.  Is the screen just black, or is there a prompt?  If it just looks black, the prompt may just be 'off the screen', so try the auto-adjust option on the monitor.

Failing that, you could boot off a Live CD and delete the config file there.  Out of curiosity, what monitor make/model do you have?

---

### Post by Kin2InuYasha on 2011-03-14
> **Grenage said:**
> Out of curiosity, what monitor make/model do you have? It is a KDS Visual Sensations vs190i
It's an old monitor, but it's always worked well and I've never had any problems with it, never flickered or changed color so I'm still rolling with it. I don't have a need to buy an LCD yet...

Also, I'm back up to par, I deleted the xorg.conf with the terminal in safe mode.

---

### Post by Kin2InuYasha on 2011-03-14
That is was hwinfo gives me,
```
root@Whatacomputer:/home/robbie# hwinfo --monitor
22: None 00.0: 10000 Monitor                                    
  [Created at monitor.95]
  Unique ID: rdCR.I3KwnjtzyG2
  Hardware Class: monitor
  Model: "KOREA Monitor"
  Vendor: KDS "KOREA"
  Device: eisa 0x1985 
  Resolution: 720x400@70Hz
  Resolution: 720x400@88Hz
  Resolution: 640x480@60Hz
  Resolution: 640x480@67Hz
  Resolution: 640x480@72Hz
  Resolution: 640x480@75Hz
  Resolution: 800x600@56Hz
  Resolution: 800x600@60Hz
  Resolution: 800x600@72Hz
  Resolution: 800x600@75Hz
  Resolution: 832x624@75Hz
  Resolution: 1024x768@87Hz (interlaced)
  Resolution: 1024x768@60Hz
  Resolution: 1024x768@70Hz
  Resolution: 1024x768@75Hz
  Resolution: 1280x1024@75Hz
  Resolution: 1600x1200@75Hz
  Resolution: 1280x1024@85Hz
  Resolution: 1024x768@85Hz
  Resolution: 800x600@85Hz
  Config Status: cfg=new, avail=yes, need=no, active=unknown

23: None 00.1: 10000 Monitor
  [Created at monitor.95]
  Unique ID: jyhG.I3KwnjtzyG2
  Hardware Class: monitor
  Model: "KOREA Monitor"
  Vendor: KDS "KOREA"
  Device: eisa 0x1985 
  Resolution: 720x400@70Hz
  Resolution: 720x400@88Hz
  Resolution: 640x480@60Hz
  Resolution: 640x480@67Hz
  Resolution: 640x480@72Hz
  Resolution: 640x480@75Hz
  Resolution: 800x600@56Hz
  Resolution: 800x600@60Hz
  Resolution: 800x600@72Hz
  Resolution: 800x600@75Hz
  Resolution: 832x624@75Hz
  Resolution: 1024x768@87Hz (interlaced)
  Resolution: 1024x768@60Hz
  Resolution: 1024x768@70Hz
  Resolution: 1024x768@75Hz
  Resolution: 1280x1024@75Hz
  Resolution: 1600x1200@75Hz
  Resolution: 1280x1024@85Hz
  Resolution: 1024x768@85Hz
  Resolution: 800x600@85Hz
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

And this is my fresh xorg.conf

```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "glx"
    Load  "dbe"
    Load  "record"
    Load  "extmod"
    Load  "dri2"
    Load  "dri"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "AccelMethod"            # [<str>]
        #Option     "DRI"                    # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "VideoKey"               # <i>
        #Option     "FallbackDebug"          # [<bool>]
        #Option     "Tiling"                 # [<bool>]
        #Option     "Shadow"                 # [<bool>]
        #Option     "SwapbuffersWait"        # [<bool>]
        #Option     "XvMC"                   # [<bool>]
        #Option     "XvPreferOverlay"        # [<bool>]
        #Option     "DebugFlushBatches"      # [<bool>]
        #Option     "DebugFlushCaches"       # [<bool>]
        #Option     "DebugWait"              # [<bool>]
        #Option     "HotPlug"                # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

I'm kind of confused as of what to do next, I'm new to all of this and Ubuntu.

---

### Post by Grenage on 2011-03-14
Give this a whirl:

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "KDS"
	ModelName "VS190I"
	HorizSync 30 - 95
	VertRefresh 50 - 120
Modeline "1024x768_75.00"   82.00  1024 1088 1192 1360  768 771 775 805 -hsync +vsync
EndSection

Section "Device"
	Identifier "Device0"
	Driver "intel"
	VendorName "82845G"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1024x768"
	EndSubSection
EndSection
```

---

### Post by Kin2InuYasha on 2011-03-14
Oh my GOD both of you are so sexy right now. IT WORKED;)

I added your code to the xorg file.

I've rebooted a couple of times just to make sure it sticks, and it does. Everything seems to be working fine, I even have a few more resolutions to choose from. This is wonderful, I've been fighting this for like a week.

I really appreciate you building the xorg file for me Grenage, it works beautifully. And Krytarik I couldn't have accomplished this without you man. You're awesome. I would have given up a while back without you helping me. I'd buy you a bottle if I could.

Well, I'm determined to learn how this OS works, so I'm going to start on the linux "How to" courses. I appreciate both of you.:D Thank you.

---

### Post by Grenage on 2011-03-14
> **Kin2InuYasha said:**
> Oh my GOD both of you are so sexy right now. IT WORKED;)

I added your code to the xorg file.

I've rebooted a couple of times just to make sure it sticks, and it does. Everything seems to be working fine, I even have a few more resolutions to choose from. This is wonderful, I've been fighting this for like a week.

I really appreciate you building the xorg file for me Grenage, it works beautifully. And Krytarik I couldn't have accomplished this without you man. You're awesome. I would have given up a while back without you helping me. I'd buy you a bottle if I could.

Well, I'm determined to learn how this OS works, so I'm going to start on the linux "How to" courses. I appreciate both of you.:D Thank you.

Glad to hear that it helped.  The config only took about 2 minutes to write; they are very simply really, I have a basic guide [here]("http://www.grenage.com/xorg.html") if you're interested.

Kudos to Krytarik for doing far more legwork than I.

---

### Post by Kin2InuYasha on 2011-03-14
> **Grenage said:**
> Glad to hear that it helped.  The config only took about 2 minutes to write; they are very simply really, I have a basic guide [here]("http://www.grenage.com/xorg.html") if you're interested.

Kudos to Krytarik for doing far more legwork than I.
I will definitely bookmark that. I will probably need to reference it if I install it on another computer with a monitor similar to this one. Thank you.

---

### Post by Kin2InuYasha on 2011-03-14
Actually there is one more issue, It's not relevant to this thread, but when I go to youtube, the flash player doesn't play it properly, It's grey/black, grainy, and has lines through the video's. It didn't start doing this until the resolution changed. I've tried reinstalling the flash player, and changing the Refresh rate.

 It's not big deal, just a last second Question/Comment.

---

### Post by Grenage on 2011-03-14
> **Kin2InuYasha said:**
> Actually there is one more issue, It's not relevant to this thread, but when I go to youtube, the flash player doesn't play it properly, It's grey/black, grainy, and has lines through the video's. It didn't start doing this until the resolution changed. I've tried reinstalling the flash player, and changing the Refresh rate.

 It's not big deal, just a last second Question/Comment.

It might be worth making a separate thread for the Flash problem, as you'll get much more appropriate viewings.  Could you screenshot what it looks like?  Are you using the default flash?

---

### Post by Kin2InuYasha on 2011-03-14
> **Grenage said:**
> It might be worth making a separate thread for the Flash problem, as you'll get much more appropriate viewings.  Could you screenshot what it looks like?  Are you using the default flash?

[This]("http://hamsterhutt.host56.com/ohman.png") is what it looks like. But you're right, I'm just going to start a new thread with this specific question. Thanks again!

---

### Post by Krytarik on 2011-03-14
Great, you both worked it out already! Also, respect for your guide/website, Grenage. I suppose you did a websearch for the monitor's specs?

---

### Post by Grenage on 2011-03-14
> **Krytarik said:**
> Great, you both worked it out already! Also, respect for your guide/website, Grenage. I suppose you did a websearch for the monitor's specs?

I did! But I believe that the modeline effectively negates the need for the monitor's capabilities.  While I couldn't find the specs for the monitor directly, a search turned up another xorg.conf where EDID had picked up the correct values.

---

### Post by Krytarik on 2011-03-14
> **Grenage said:**
> I did! But I believe that the modeline effectively negates the need for the monitor's capabilities.
Since it didn't work with the modeline alone, at least with xrandr, I guess the passing of the correct specs is indeed needed.

---

### Post by Grenage on 2011-03-14
> **Krytarik said:**
> Since it didn't work with the modeline alone, at least with xrandr, I guess the passing of the correct specs is indeed needed.

A valid point indeed! :)

---

