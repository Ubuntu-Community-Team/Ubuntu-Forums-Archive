---
title: "Stuck in low res after Nvidia driver install (Ubuntu 10.10)"
date: 2011-01-04
forum: Desktop Environments
---

### Post by anthonyvo on 2011-01-04
Running Ubuntu 10.10
Card is an Nvidia Quadro FX 1500
Monitor is a Dell E172FP

Well, after installing the drivers for my Nvidia Quadro FX 1500, I am stuck in 800x600. The options in the Nvidia X-server Settings (under System > Administration) show only "Auto / 640x480 / 320x240"

I've edited the xorg.conf (backed up before every attempt, of course,) to add modes, etc. but to no avail.

I just installed read-edid via Synaptic and in Terminal ran this:
```
$ sudo get-edid | sudo parse-edid
```I received this back (apparently, no EDID is being read - I have my monitor connected with an DVI adaptor)
```

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
    Function supported
    Call successful

    VBE version 300
    VBE string at 0x2110 "NVIDIA"

VBE/DDC service about to be called
    Report DDC capabilities

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
    Function supported
    Call successful

    Monitor and video card combination does not support DDC1 transfers
    Monitor and video card combination does not support DDC2 transfers
    0 seconds per 128 byte EDID block transfer
    Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
    Read EDID

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
    Function supported
    Call failed

The EDID data should not be trusted as the VBE call failed
Error: output block unchanged

```Any ideas on how to force or fake the EDID info? (I only need 1024x768 on this living room PC.)

-Anthony

---

### Post by anthonyvo on 2011-01-04
Just bumping this up.

I've since uninstalled the manual .run driver/package from Nvidia and have reinstalled the nvidia drivers via ubuntu. Still only gives me the 640x480 resolution as the max option (but looks like it's in "auto" w/ 800x600.)

-Anthony

---

### Post by anthonyvo on 2011-01-04
Celebration! I'm posting what worked for me in case anyone else can benefit from it:

I edited my xorg.conf (after backing it up, of course) and changed this:
```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

```

to this:
```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 72.0
    VertRefresh     43.0 - 60.0
EndSection

```

Now I have my Nvidia Quadro FX 1500 in 1024x768 "glory." :guitar:

-Anthony

---

### Post by Krytarik on 2011-01-04
Congratulations! Did disabling the "DPMS"-option make it work or is just setting the correct specs enough, in your case?

For anyone else who wants to set the correct specs of the used monitor:
```
sudo apt-get install hwinfo
sudo hwinfo --monitor
```

---

### Post by Shlomir on 2011-01-04
I'm getting the same problem. I got the latest NVIDIA driver through Synaptic and still have the LowRes issue.

I have an NVIDIA FX5700 card, could someone please suggest what setting in xorg.conf I need?

---

### Post by BicyclerBoy on 2011-01-04
Any clues in the /var/log/Xorg.0.log   file ?

Any EDID warnings errors..

What is the native res of the monitor ?
And connected how ?

Below xorg.conf snippet could be useful. You need to replace the "CRT-0" with something appropriate.

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "ModeValidation" "AllowInterlacedModes"
    Option         "UseEDID" "FALSE"
    Option         "UseDisplayDevice" "CRT-0"
    SubSection     "Display"
        Depth       24
#        Modes      "1920x1080i60" "1280x720p60" "1024x576p50" "848x480p60"
    EndSubSection
EndSection


The "AllowInterlaceModes" is most likely not necessary for you..


Does that read-EDID package actually work for anyone ?
I think it is i386 or powerPC only...

---

### Post by Krytarik on 2011-01-04
> **Shlomir said:**
> I'm getting the same problem. I got the latest NVIDIA driver through Synaptic and still have the LowRes issue.

I have an NVIDIA FX5700 card, could someone please suggest what setting in xorg.conf I need?
Did you try anthonyvo's solution, with your own monitor specs of course?

---

### Post by anthonyvo on 2011-01-05
> **Krytarik said:**
> Congratulations! Did disabling the "DPMS"-option make it work or is just setting the correct specs enough, in your case?

I think it had to do with the sync. I can't see how enabling Energy Star functions would have helped (isn't that what DPMS is?) The monitor seems to go to sleep after some time anyway.

Later today, I'll experiment with it and find out.

-Anthony

---

### Post by Krytarik on 2011-01-05
> **anthonyvo said:**
> I think it had to do with the sync. I can't see how enabling Energy Star functions would have helped (isn't that what DPMS is?) The monitor seems to go to sleep after some time anyway.

Later today, I'll experiment with it and find out.

-Anthony
Exactly, it's about power management. But apparently it is able to interfere sometimes however. Looking forward to get your test result, thanks.

---

### Post by anthonyvo on 2011-01-06
Well, you were right. After adding the DPMS option, it would hang at the splash screen on boot. I was under the impression that the sync range was the solution. Perhaps it's a combo of the two. I might be tempted to play with the sync range to see if it too caused it... Or just leave well enough alone.

---

### Post by anthonyvo on 2011-05-04
Just an update: Well, my love affair with Ubuntu is now on the rocks. After today's update to 11.04, I'm back to stuck on splash (i.e., xserver doesn't run.) 

That was fun. Tomorrow in going to reinstall (all my important files are backed up) and if this xorg/invidious thing can't be overcome, I'm going back to Windows.

Been at this for 12 hours...

---

### Post by Krytarik on 2011-05-04
Well, you didn't say what you tried to fix it.

Try:
- setting "nomodeset" as a kernel boot option:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
- booting into "recovery mode"
- removing "/etc/X11/xorg.conf" with a liveCD

Greetings.

---

### Post by anthonyvo on 2011-05-05
I think my problem was that in 10.10 I had to manually install my Nvidia driver and then remove the DPMS option in the Xorg.conf file (no EDID since it was analog connection for my monitor.) Now, xserver won't start because it says the version of the kernel the driver was compiled with is older than the one it has now.

In any case, nomodeset didn't work so I'm going to do burn a live CD now and test that. If it works, then I'll do a fresh install.

Since this topic/thread had originally been solved in 10.10, I'll be over at the installation/upgrade section with anything further.

-Anthony

---

### Post by teknotuck on 2011-08-28
Well nothing worked for me BUT I still fixed it! This is not something I saw posted anywhere else either so I am posting it here to help others who might have tried everything and still be having issues as I was.

Modify your xorg.conf file to list the correct range, by default nvidia creates something like this.
```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
#    Option         "DPMS"
# Commented the above out, trying to get anything higher than 640x480 STILL NO GO BUT LEAVING THIS TILL 
# I CAN GET SOMETHING WORKING.
EndSection            

```

The problem is that the  HorizSync and the VertRefresh range is way to narrow. Find what your monitor-system really supports. Get the highest and lowest frequencies your monitor can handle, dont worry about the resolution part. The server should be able to figure that out if it knows the real range that your monitor can be driven. Mine worked out to be this.

# HorizSync    28.0 - 33.0 Modifying with actual numbers from the manual
HorizSync       31.469 - 79.976
#    VertRefresh     43.0 - 72.0        
VertRefresh     59.810 - 75.062

I did have two other edits I made, I don't think they helped but in case they did here is that section too.

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
# Adding the 2 lines below as my modification to this part of the file
    Option         "IgnoreEDID" "1"
    Option "NoDDC"
EndSection

After a reboot I now have 27 different resolutions to chose from instead of 2.

I spent over 12 hours easily on this problem but its fixed now. I probably can remove some of what I added into the file as I was testing. All of the get-edid stuff failed as did everything else but just finding the real range values and putting those into the file did the trick, which makes total sense when you think about it.

Ill attach my config file, mind you I KNOW there is stuff I will be cleaning up but I know it might be helpful to someone and hey, that is what its all about.

Also this was done on a Shuttle system with a PNY Geforce 7600GS PCI-E cart and with a Samsung LN40B500 40" LCD HDTV monitor and only using a VGA cord since video card has vga and dvi out but monitor has vga and hdmi. 

Crap it won't let me attach the file, here it is via copy and paste, already having to type this a second time cause the first time the system timed out and I was logged out by the time I hit submit.
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 280.13  (buildmeister@swio-display-x86-rhel47-05.nvidia.com)  Wed Jul 27 17:18:55 PDT 2011

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
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
    VendorName     "Samsung"
    ModelName      "LN40B500"
#    HorizSync       28.0 - 33.0 Modifying with actual numbers from the Samsung manual
    HorizSync       31.469 - 79.976
#    VertRefresh     43.0 - 72.0
    VertRefresh     59.810 - 75.062
#    Option         "DPMS"
# Commented the above out, trying to get anything higher than 640x480 STILL NO GO BUT LEAVING THIS TILL 
# I CAN GET SOMETHING WORKING.
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
# Adding the 2 lines below as my second modification to this file, the NoDDC technically is the 4th mod
    Option         "IgnoreEDID" "1"
    Option "NoDDC"
EndSection

#Section "Screen"
#    Identifier     "Screen0"
#    Device         "Device0"
#    Monitor        "Monitor0"
#    DefaultDepth    24
#    SubSection     "Display"
#        Depth       24
#    EndSubSection
#EndSection
# Test Number 3 Below, have not rebooted to test the second mod I did yet.
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
#        Modes      "1920x1080" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    Option         "TwinView" "0"
    Option         "metamodes" "1920x1080_60 +0+0; 1600x1024 +0+0; 1920x1080 +0+0; 640x480 @1600x1024 +0+0"
# Modified the line above plus removed the nvidia-auto-select +0+0; part which was the first declaration of metamodes
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```
Hope this helps someone
:KS

---

### Post by jayarsantos on 2011-10-12
Thanks for this one,teknotuck, your a life saver(: got mine working now ubuntu 10.10. here is my modification based on yours.

Section "Monitor"
    # HorizSync source: builtin, VertRefresh source: builtin
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-1"
    HorizSync       28.000 - 60.000
    VertRefresh     43.000 - 60.000
    #Option         "DPMS"
EndSection

---

### Post by Revlin John on 2012-01-28
Hey Guys and Gals,

THANK YOU!

I spent quite a bit of time figuring this out and this thread was HUGE help. Here's my info:

My card is GeForce FX 5700 Ultra

$ sudo apt-get install nvidia-settings-updates

[In Additional Drivers I activated:] NVIDIA accelerated graphics driver (version 96)

And I created this very minimal /etc/X11/xorg.conf:
```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.00 - 60.00
    VertRefresh     50.00 - 76.00
    #Modlines DO NOT WORK FOR MY CARD+MONITOR!
    #Option         "DPMS"
EndSection

Section "Screen"
        Identifier     "Screen0"
        Device         "Device0"
        Monitor        "Monitor0" 
        Option  "AddARGBGLXVisuals"     "True"
EndSection

Section "Device"
        Identifier           "Device0"
        Driver               "nvidia"
        VendorName    "NVIDIA Corporation"
        Option               "NvAGP" "3"
        Option               "IgnoreEDID" "1"
        Option               "NoDDC"
        #Option        "NoLogo" "True"
EndSection


```As you can see I concluded through trial/error that Modelines do not work for my monitor or I was getting them terribly wrong, so I just gave up. I think the Horizontal and Vertical sync settings were big because I finally went and looked up the specs for my monitor, but the biggest factor was using version 96 (not the post-release updates) of the nVidia drivers because I tried every single driver. 96 was the last one I tried  and the only one that worked.

Thanks a bunch!

Revlin

---

### Post by atkane on 2012-05-29
hey Ya'll, just got done fixing this with this, still pretty new with ubuntu. Just wanted to say thanks guys!

---

### Post by DiogoAbdalla on 2012-07-11
> **anthonyvo said:**
> Running Ubuntu 10.10
Card is an Nvidia Quadro FX 1500
Monitor is a Dell E172FP

Well, after installing the drivers for my Nvidia Quadro FX 1500, I am stuck in 800x600. The options in the Nvidia X-server Settings (under System > Administration) show only "Auto / 640x480 / 320x240"

I've edited the xorg.conf (backed up before every attempt, of course,) to add modes, etc. but to no avail.

I just installed read-edid via Synaptic and in Terminal ran this:
```
$ sudo get-edid | sudo parse-edid
```I received this back (apparently, no EDID is being read - I have my monitor connected with an DVI adaptor)
```

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
    Function supported
    Call successful

    VBE version 300
    VBE string at 0x2110 "NVIDIA"

VBE/DDC service about to be called
    Report DDC capabilities

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
    Function supported
    Call successful

    Monitor and video card combination does not support DDC1 transfers
    Monitor and video card combination does not support DDC2 transfers
    0 seconds per 128 byte EDID block transfer
    Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
    Read EDID

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
    Function supported
    Call failed

The EDID data should not be trusted as the VBE call failed
Error: output block unchanged

```Any ideas on how to force or fake the EDID info? (I only need 1024x768 on this living room PC.)

-Anthony

Just registered to say that this worked perfectly for me (in Mint 13, witha Geforce GT540). Thank you a million.

---

### Post by t3chn0k on 2013-04-30
Hello! This is my first post on this Forum and I came here to THANK YOU!

After updating my nvidia driver, my second monitor (a 32" Buster TV) was stucked @640x480.

After reading your topic, I edited my *xorg.conf* file like you did, doing exatly the same changes, and... Voilà!!! It worked like a charm!!!!

And there is more: after doing the change I have unlocked even more resolution options than I had before updating the driver! Haha! Even my full HD (1900x1080p) is working now!!!

Thank you, thank you, thank you!!!

I wish you the very best! ;)

---

### Post by leonid870721 on 2013-11-11
Thanks a million, chief! My 9800GT 512MB failed and I had to replace it with a 7200 / 7300 gs 128MB! Nouveau worked fine with the previous one, but it did not at all with the 7000 series.

---

