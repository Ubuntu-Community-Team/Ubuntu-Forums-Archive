---
title: "Nvidia driver does not detect resolutions on FX 5200 AGP"
date: 2008-10-12
forum: Desktop Environments
---

### Post by shinji257 on 2008-10-12
Before I start I should state the following:
This is most likely a nVidia bug rather than a Ubuntu one.  The open-source driver detects resolutions correctly but you need the proprietary driver for any visual effects.

I do not know if this has already been reported or not.  I do know that this has been a reoccuring issue.  I first discovered this with an unofficial variant called CrunchBang.  Needless to say that I have reproduced this on Ubuntu as well as Linux Mint.  This is also reproducable on both 8.04 and 8.10 builds.  For those that find that after installing the nvidia driver you are stuck at 640x480 then here is a small workaround.  These instructions are geared toward the stock Ubuntu setup however they can be adjusted as needed.  You will need a SSE compatible CPU to complete the instructions due to it's reliance on nvidia-settings.

The workaround involves inserting the frequency range for your monitor.  The driver will automatically determine all possible resolutions for your monitor.  There will be some that exceed your monitor specs so please do not choose them.

NOTE // MONITOR DAMAGE WARNING: It is your responsibility to get the correct frequency ranges for your monitor.  I will not be responsible for damages to your display due to incorrect frequency settings.

If after installing the driver you do not have the item labeled "NVIDIA X Server Settings" under the Administration section or if nvidia-settings is missing then stop here.  Remove the driver and reinstall it using EnvyNG.  This should only be required on 8.04.  EnvyNG can be installed using the envy-core and envy-gtk packages which installs the Gnome interface.  There is another envy package for KDE users although I don't remember the exact package name.

Open terminal and type:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
Enter your password when prompted.  Once done also type this and also enter your password here.
```
gksudo gedit /etc/X11/xorg.conf
```

Scroll down until you find "Section Monitor".  Here is how it looked on my end.
```

Section "Monitor"
     Identifier     "Monitor"
EndSection

```
That is an example and may look different for you.

Now then the change here is to insert the lines HorizSync and VertRefresh into this.  They define the low and high end for the frequency ranges on Horizontal and Vertical respectively.

Here is what mine looks like now

```

Section "Monitor"
     Identifier     "Monitor"
     HorizSync      56.0 - 75.0
     VertRefresh    30.0 - 83.0
EndSection

```
Note that these may (and probably will be) different from the above.  **_Do not copy them verbatim from my example._**

Now reboot.  In my case when my GDM came up it was now at 1024x768 instead of the 640x480 that I started with.  This tells me that it is working now.  Not sure why it picked that one (my screen is 1280x1024 native) however it is a safe one.  It may not be the same for you however if there is _any_ change in resolution then it is probably good for the remainder.  

**If you get any out of frequency errors or any errors from xorg.conf then address them.  There may be a typo at this point.**  Hope you remembered to backup your xorg.conf file.

Now then here is the last step.  If the resolution automatically chosen is not acceptable and you want a higher one then you will need to force it via nvidia-settings then save it to xorg.conf.

Open a terminal window and type
```
gksudo nvidia-settings
```
When prompted enter your password.

Choose X Server Display Configuration.

Pick the resolution that you want.  It will likely give you more than actually acceptable by your screen.

Now then click on Save to X Configuration File.

NOTE: I actually got a parse error here.  It was due to a line that nvidia-settings thought was invalid.  It is likely perfectly valid however there does not appear to be any harm in allowing its removal. 

I've gone ahead due to weird flickering but it doesn't seem to have affected anything.

On this screen click on Show Preview then insert a # sign changing this:
```

Section "Files"
     RgbPath     "/usr/X11R6/lib/X11/rgb"
EndSection

```
to this:
```

Section "Files"
     #RgbPath     "/usr/X11R6/lib/X11/rgb"
EndSection

```

Note that this may not be necessary on 8.04 but this line prevented me from loading the X.org server on 8.10.  I honestly didn't remember doing this on 8.04.  It is flagged as being invalid by the X.org server however online documentation indicated that it is perfectly valid.

Now then remember the line that we removed?  Or actually that the Nvidia X Server Settings application when it remade the X.org config file?  Well if you want to add it back now is the time.  Go ahead and insert following line back into the xorg.conf file in the Files section.  It should be the last one...
```

Disable     "dri2"

```

Now then has the syntax for the x.org config file changed???





For the rest of us here are my system specs.

AMD Duron 1300+ (1.3Ghz) Processor (SSE supported at 1000+)
Nvidia FX 5200 256MB AGP 4x
640MB PC133 SDRAM
240GB total capacity (200GB main installation + 40GB swap)

Ok those are the key specs.  The 40GB swap was because I was too lazy to think about what should be placed on that 40GB space.  I just ended up making it all swap for now.  I couldn't test to see if the driver would of seen my display correctly with DVI because my card does not have a DVI output.  It only has a VGA one.

---

