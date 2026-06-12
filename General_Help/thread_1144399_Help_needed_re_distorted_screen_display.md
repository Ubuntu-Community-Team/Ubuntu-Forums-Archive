---
title: "Help needed re distorted screen display"
date: 2009-04-30
forum: General Help
---

### Post by hatrack on 2009-04-30
Hi all !

Over the past few months, I have been developing my work-practices to go over to using Ubuntu completely. I am running Ubuntu Ver 8.04 (Hardy) on a Dell GX-520 with 1 Gb of RAM and the monitor is a 19" TFL model. This machine has an Intel 82945 (rev 02) graphics chip on the motherboard. (This has been confirmed, using the command "lspci | grep VGA")

Now that I have recently started to use Gimp (Ver 2.6.x) for my photo-processing, I have noticed a problem with the screen display. A circle is distorted into an ellipse with the major axis orientated vertically. This suggests to me that the screen resolution is incorrectly set so that the pixels are no longer square but instead, are elongated in the vertical direction. 

Checking in "Preferences" > "Screen Resolution", I find that only five options are offered --
1280 x 800, 1280 x 768, 1024 x 768, 800 x 600 and 640 x 480, all at 60 Hz only. (This has been confirmed using the command "xrandr")

Now ... the viewable area of my 19" screen is measured to be 336 x 270 mm so ... if I set a horizontal resolution of (say) 1280 pixels then the corresponding vertical resolution should be 1028 pixels (probably 1024, a change of only 1 mm in my measurement will produce this result). As can be seen, the option to choose a resolution of 1280 x 1024 is not available. This leads me to suspect that I am using the wrong video driver but now, I am completely lost !

I have checked in the xorg.conf file and find that the 82945 graphics chip is being recognised and a BUS ID is allocated. With a display setting of 1280 x 768, superficially, the screen display looks reasonable ... it is only when attempting graphics processing that the distortion becomes obvious (and irritating) ... and now that I have moved my photo-processing from Windows to Linux ! 

[Please note --- I have a separate Windows machine with a Radeon graphics card which I formerly used for this work]

I have searched on this forum for information but find that I do not have sufficient knowledge yet to decide what is and what is not relevant. I shall therefore be most grateful if anyone can offer advice and guidance as to how I should now proceed.

Best regards to all ...

---

### Post by hatrack on 2009-05-01
Hi all !

I posted this yesterday in the "Absolute Beginners" forum but as I have not received any replies at all, I am posting it here. If this causes any confusion to other readers then I offer my sincere apologies.

Original Post --
Over the past few months, I have been developing my work-practices to go over to using Ubuntu completely. I am running Ubuntu Ver 8.04 (Hardy) on a Dell GX-520 with 1 Gb of RAM and the monitor is a 19" TFL model. This machine has an Intel 82945 (rev 02) graphics chip on the motherboard. (This has been confirmed, using the command "lspci | grep VGA")

Now that I have recently started to use Gimp (Ver 2.6.x) for my photo-processing, I have noticed a problem with the screen display. A circle is distorted into an ellipse with the major axis orientated vertically. This suggests to me that the screen resolution is incorrectly set so that the pixels are no longer square but instead, are elongated in the vertical direction. 

Checking in "Preferences" > "Screen Resolution", I find that only five options are offered --
1280 x 800, 1280 x 768, 1024 x 768, 800 x 600 and 640 x 480, all at 60 Hz only. (This has been confirmed using the command "xrandr")

Now ... the viewable area of my 19" screen is measured to be 336 x 270 mm so ... if I set a horizontal resolution of (say) 1280 pixels then the corresponding vertical resolution should be 1028 pixels (probably 1024, a change of only 1 mm in my measurement will produce this result). As can be seen, the option to choose a resolution of 1280 x 1024 is not available. This leads me to suspect that I am using the wrong video driver but now, I am completely lost !

I have checked in the xorg.conf file and find that the 82945 graphics chip is being recognised and a BUS ID is allocated. With a display setting of 1280 x 768, superficially, the screen display looks reasonable ... it is only when attempting graphics processing that the distortion becomes obvious (and irritating) ... and now that I have moved my photo-processing from Windows to Linux ! 

[Please note --- I have a separate Windows machine with a Radeon graphics card which I formerly used for this work]

I have searched on this forum for information but find that I do not have sufficient knowledge yet to decide what is and what is not relevant. I have searched for xserver-org on my machine but am informed that this is not installed. Unfortunately, I can't find any way to install this and ... I am not even sure that I should attempt to do this, anyway !

I shall  be very grateful if anyone can offer advice and guidance as to how I should now proceed.

Best regards to all ...

---

### Post by jbrown96 on 2009-05-01
You should just need to add the resolution to your xorg.conf file.

1) Backup!
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.back
``` If something bad happens, and you can't get into a graphical environment, run this same command with the two files reversed. This will at least get you back to the distorted display.

2) Edit your xorg.conf
```
gksu gedit /etc/X11/xorg.conf
```

look for a section like this
> Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
[COLOR="Red"]Modes "1024x768"
Virtual 1024 768[/COLOR]
EndSection

You will need to add the red sections and change the resolution to your desired setting. Logout/Login then you should have your new resolution.

---

### Post by CatKiller on 2009-05-01
The other option is to put in refresh rates for the monitor, if you have them:

Often, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
``````
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```You'll need to replace aa-dd with the values for **your** monitor.

---

### Post by hatrack on 2009-05-01
My thanks to you both for your quick reply. Rather than write two separate messages, I'll combine my answer into one.

First of all, to "CatKiller" --- Unfortunately this computer is second-hand and so I don't have any documentation for it. 

Now to "jbrown96" --- I'm afraid your suggestion didn't solve the problem, the system defaulting into LoRes 800x600 mode.

However, I've had problems trying to edit xorg.conf in the recent past, so this result may be due to my inadequacies !

The relevant section of this file that gives the distorted display reads --
```

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```I have edited this so that it now reads ---
```

Section "Device"
    Identifier    Device0
EndSection

Section "Monitor"
    Identifier    "Monitor0"
EndSection

Section "Screen"
    Identifier    "Screen0"
    Monitor        "Monitor0"
    Device        "Device0"
    DefaultDepth    24
    Modes    "1280x1024"
    Virtual    "1280x1024"
EndSection

```I'm afraid that I can't see my error but ... there's got to be one in there ... somewhere !

Can you please advise ?

Many thanks and Best regards ...

---

### Post by CatKiller on 2009-05-01
> **hatrack said:**
> First of all, to "CatKiller" --- Unfortunately this computer is second-hand and so I don't have any documentation for it. 

If it's got a model number, you can often find the information you need from a search of the Internet.

> **hatrack said:**
> However, I've had problems trying to edit xorg.conf in the recent past, so this result may be due to my inadequacies !

You only need to add the two lines in; you don't need to change any of the others.

---

### Post by jbrown96 on 2009-05-01
Sorry that didn't work for you. I've never had much trouble with resolutions, but I did find a couple of guides that may help you.

[This one]("https://wiki.ubuntu.com/X/Config/Resolution") looks good and you should be able to see what happens immediately rather than getting the low resolution mode.


For [this one]("http://ubuntuforums.org/showthread.php?t=83973") you will need information about the monitor. Google the model number? It will produce better modes, so maybe that will work better.

---

### Post by hatrack on 2009-05-01
Hi !

My thanks to you both for your tips.

It's late here now (0115 hrs ! ) so I'm off to bed now. I'll try your ideas tomorrow when I'm a bit more "switched-on" and report in due course.

Best regards ...

---

### Post by hatrack on 2009-05-02
Hi all !

I have spent today experimenting with the ideas and information kindly supplied by jbrown96 and CatKiller and have generated seven versions of xorg.conf. Unfortunately, in every case, the System defaults to a screen resolution of 800x600 with the option to set 600x400.

I have further experimented with the settings available to me from the actual monitor controls. When these are invoked, a splash screen is presented showing the presently-set resolution (1280x768 ) and the optimum (1280x1024) ... which is what I am trying to achieve. As I mentioned previously, when I look in "System" > "Preferences" > "Screen Resolution" the maximum that I can set is shown to be 1280x800. However, if I set this maximum it is then not possible to fit the Ubuntu Desktop onto the screen ... the controls do not have sufficient adjustment range to allow this.

Clearly, something very fundamental is wrong but I am afraid that today's experiments have not brought me any nearer to a solution to this problem. I hope that someone can kindly offer some further suggestions and I have attached a complete listing of the relevant section of the xorg.conf files that I have so far generated, together with infomation on the basic file currently in use.

I look forward to comments/suggestions in due course and thank all who spend time looking at this matter on my behalf.

Best regards to all ...


Appendix -- xorg.conf files ---

```

[1]  Relevant section of basic xorg.conf file which allows screen resolutions of 1280x768 and 1280x800 to be set. 1280x768 is the maximum usable -- adjustments do not allow 1280x800 to be fitted onto display screen.
 
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
--------------------------------------------------------------------------------------------
[2]  Experimental files

Version_01
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection


Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    Modes    "1280x1024"
    Virtual    1280x1024
EndSection

# The above section has been edited to add "DefaultDepth", "Modes" & "Virtual" which
 # were not in previous version of this file 
----------------------------------------------------------------------------------------------------

Version_02
Section "Device"
    Identifier    Device0
EndSection

Section "Monitor"
    Identifier    "Monitor0"
EndSection

Section "Screen"
    Identifier    "Screen0"
    Monitor        "Monitor0"
    Device        "Device0"
    DefaultDepth    24
    Modes    "1280x1024"
    Virtual    "1280x1024"
EndSection

# The above section has been edited to add "DefaultDepth", "Modes" & "Virtual" which
 # were not in previous version of this file  and to change the Identifiers to Zero
 ---------------------------------------------------------------------------------------------------
Version_03
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    HorizSync    30kHz - 83kHz                                <--- Errors here noticed & rectified -- See Version_04
    VertRefresh    56kHz - 75kHz                             <--- Errors here noticed & rectified -- See Version_04
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
-----------------------------------------------------------------------------------------------

Version_04
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    HorizSync        30 - 83
    VertRefresh    56 - 75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    Modes    "1280x1024"
    Virtual    1280x1024
EndSection
----------------------------------------------------------------------------------------------------

Version_05 ----- NB ModeLine generated on line and pasted into file
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    HorizSync        30 - 83
    VertRefresh    56 - 75
    Modeline "1280x1024" 109.62  1280 1336 1472 1720  1024 1024 1026 1062
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    Modes    "1280x1024"
    Virtual    1280x1024
EndSection
------------------------------------------------------------------------------------------------

Version_06 ----- NB ModeLine edited
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    HorizSync        30-83
    VertRefresh    56-75
    Modeline "1280x1024" 108  
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    Modes    "1280x1024"
    Virtual    1280x1024
EndSection
-------------------------------------------------------------------------------------------------

Version_07 ----- NB "Monitor" section edited to incorporate detailed info obtained using ModeLine calculator
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    HorizSync        60.00Hz
    VertRefresh    63.73
    Modeline "1280x1024" 109.62  1280 1336   1024 1024 
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    Modes    "1280x1024"
    Virtual    1280x1024
EndSection
----------------------------------------------------------------------------------------------

```

---

### Post by jbrown96 on 2009-05-02
I'm not sure how you feel about this, but you may try 9.04 or at least from a liveCD. It has much newer Intel drivers and a newer X-server as well.

---

### Post by CatKiller on 2009-05-03
If you want to see what's actually causing that mode to be rejected, /var/log/Xorg.0.log is the log file for X. You can view it with ```
less /var/log/Xorg.0.log
``` (PageUp & PageDown do the obvious, q to quit less) You should be able to find the reason in there for why a particular mode isn't being chosen. If this still doesn't give you enough information, you can use ```
     Option     "ModeDebug"     "True"
``` in the "Device" Section to give you even more information.

It's possible that your monitor is actually passing along EDID information, but that information is incorrect. That's what my monitor does. You can use ```
Option     "UseEDID"     "False"
``` in the "Device" Section to tell X to ignore the information that it receives and just use what you give it.

---

### Post by hatrack on 2009-05-03
Hi CatKiller !

Thank you very much for these tips.

I'm out for most of today but I'll try your suggestions later when I get home and report the results.

In meantime, I've had another thought ... As an experiment, late last night I plugged this monitor in to my old Windows machine, which has a Radeon 7000 card and runs under Win 2000. I can set a resolution of 1280x1024 in a few minutes ... absolutely no sweat ! It is just one of the many options offered. I'm now thinking to move this card over to my Linux machine and if this works, to buy another Radeon card for use full-time. Can you recommend a good choice of card and possibly an xorg.conf to use with it for ordinary photo-processing ... _not_ gaming ? 

Thank you again for your efforts on this ... as a pensioner of 75, I most certainly appreciate your advice !

best regards as always ...

---

### Post by CatKiller on 2009-05-03
You could try the Win2K machine with that monitor running from a live cd to see if the card would be likely to help.

> **hatrack said:**
> Can you recommend a good choice of card and possibly an xorg.conf to use with it for ordinary photo-processing ... _not_ gaming ?

Not really. I've been out of the hardware game for quite some time. Matrox cards used to be considered good for colours and rubbish for gaming, but I don't know what they're like now, and I've got no idea what their Linux support is like. AMD/Ati have been more forthcoming with their specifications lately, so the free drivers for Ati cards should improve considerably over time. NVidia have released reasonable closed-source drivers for quite a long time, but nothing else. So if their driver works for a particular NVidia card then it's great, but if it doesn't there's nothing you can do. NVidia won't support older cards because they want you to keep buying new cards. The free drivers have been stunted in functionality for ages because they can't get any information from NVidia. Intel release open source drivers for their graphics chipsets, but I don't think they're in the add-on card market.

X is in a state of flux at the moment because it has some fairly severe limitations (as a framework it is *really* old, and was devised when all the graphical things that people want these days weren't even imagined). It's being gradually replaced with something better that should do more stuff automatically. Free drivers are more likely to keep up with these changes than non-free ones. Each of the last few releases of Ubuntu have come out with caveats that the non-free drivers don't work straightaway because the vendor hasn't released a driver that works with that version of X.

---

### Post by jbrown96 on 2009-05-03
Nvidia has significantly better drivers, but that probably won't matter too much for photo editing. ATI drivers are particularly bad at playing video because they "tear" a lot. Furthermore, the drivers are changing rapidly, and they have dropped support for a lot of older cards (<HD3000 I believe). 

Both proprietary drivers should be able to set up your xorg.conf with no problems... unless it's the EDID data that is wrong.

---

### Post by hatrack on 2009-05-04
Hi All !

First of all, my thanks to jbrown96 and CatKiller for their latest advice.

Further to our protracted correspondence on this matter, I am pleased to report that the problem is well on the way to finally being solved. I simply transferred the Radeon 7000 card from my old Windows machine and now I am able to set a resolution of 1280x1024 @ 60Hz, with no trouble at all.

However ! ... this leaves me with a Windows machine without a graphics card. So ... I have today bought an Nvidia Geforce FX-5200 card with 256Mb RAM on the basis that this will certainly be Windows-compatible and probably Ubuntu-compatible. It would indeed be nice to use this new card with Ubuntu because it has four times the RAM of the old Radeon 7000 card. 

Unfortunately, with the Nvidia card fitted, the system reports "Unable to set Video" and then refuses to boot. Naturally, I do not yet have any Nvidia drivers installed but ... I can only do this when I'm running an ATI card and I'm not at all sure that I should try to do this. I have also looked in Synaptics but again, I'm not sure what (if anything) I should try to install from there.

I am sorry to trouble this Forum further with my problems but I just don't know how to get an Nvidia driver installed whilst running with my ATI card so that I can begin proper testing with the new card.

Can anyone kindly advise me further on this matter ?

Best regards to all

---

### Post by jbrown96 on 2009-05-04
How far does it get into the boot process before it fails? I haven't seen that message before. At the grub menu, could you try a recovery kernel and then choose the option to fix your display (I don't remember the exact text).

If you get sufficiently far into the boot process, then the problem is likely due to Ubuntu trying to use a specific video driver for your card that won't work with Nvidia. The recovery option before should make your xorg.conf as generic as possible, and hopefully that works. 


Otherwise, put the ATI card back in, so you can boot. Then run ```
sudo dpkg-reconfigure --xserver-xorg
``` This will generalize your xorg.conf to use the vesa driver, which works with basically any card. Then try the Nvidia one, and you should be able to install the proprietary one from there. If you still have problems with resolution, use nvidia-settings (Apps--->System tools) to set it. The general display manager doesn't work very well. You may need to install it (I can't remember if it comes standard with the driver). ```
sudo apt-get install nvidia-settings
```

---

### Post by CatKiller on 2009-05-04
> **hatrack said:**
> Unfortunately, with the Nvidia card fitted, the system reports "Unable to set Video" and then refuses to boot. Naturally, I do not yet have any Nvidia drivers installed but ... I can only do this when I'm running an ATI card and I'm not at all sure that I should try to do this. I have also looked in Synaptics but again, I'm not sure what (if anything) I should try to install from there.

So if I've got this straight; putting the Radeon 7000 card in your Ubuntu machine worked fine, but you'd like to get your new NVidia card working in your Ubuntu machine too? If you aren't gaming, the NVidia card probably won't be any better for what you'll use it for than the Radeon, so it might be most sensible to keep the Radeon in the Ubuntu machine and put the NVidia card in the Windows machine as you'd originally planned. 

However, everyone likes a challenge :)

You say that you get a message that Ubuntu is "unable to set video." Whereabouts in the boot process does this error occur? Before the drives are detected? Before the progress bar? After the progress bar, but before the login window?

> 
I am sorry to trouble this Forum further with my problems but I just don't know how to get an Nvidia driver installed whilst running with my ATI card so that I can begin proper testing with the new card.

Depending on where the error occurs, you may still be able to get to a virtual console and do things from the command line, which would cut out some of the hardware swapping steps. I'm going to assume that you can't though, for a skeleton method.

Boot the machine with the Radeon card in, so that you can see what you're doing. If you're using the proprietary Ati driver (I've lost track) remove it. You may be able to just untick the entry in System -> Administration -> Hardware Drivers, or you may have to remove the fglrx package in Synaptic.

In principle, if you aren't using the proprietary Ati driver, Ubuntu will probe the hardware when you boot with the NVidia card in and load the nv driver. If it doesn't, you'll need to specify the most generic driver available in your xorg.conf that will work with both cards. This is the VESA driver and doesn't do anything exciting at all. You can do this by putting a line in the Device section of your xorg.conf that says ```
        Driver          "vesa"
``` This should let you boot with either card in and still have graphics.

Once you've got the computer successfully booted to a graphical environment with the NVidia card in, you can then proceed to install the proprietary driver for that card if you wish, or to either remove the vesa line or replace it with an equivalent nv line in your xorg.conf.

---

### Post by hatrack on 2009-05-04
Once again, my thanks to you both. I'll write a combined reply to both your messages to save a lot of repetition.

The "Failure to install graphics" message occurs very early on in the boot process. I'm back with the Radeon card for now so I can't immediately reproduce the exact circumstances but (so far as I recall) it happens before I get to the Grub. What I could do is fit the Nvidia card again and note exactly when the failure does happen.

I'm going to try some more experiments with your suggestions and I will report again tomorrow. In the meantime, it's really nice to have 1280x1024 resolution and first experiments in photo-processing indicate that the Radeon with only 64Mb memory is a whole lot faster than was the integrated Intel graphics chip on the motherboard.

So ... even if I find that I can't resolve the Nvidia versus Radeon problem, I'm a whole lot better off than I was  :).

Thank you both very much indeed ...

---

### Post by CatKiller on 2009-05-04
If it's before the GRUB menu then it's a hardware problem; the Linux kernel hasn't loaded yet.

There may be a setting in your BIOS that can help. There's normally a message very early on in the boot process that says "press such-and-such-key to enter Setup" or "press such-and-such-key to enter BIOS." Sometimes it's the Del key, and sometimes it's one of the F-keys.

---

### Post by hatrack on 2009-05-05
Once again, thank you very much for your continuing interest in my problem.

I'm not at all sure what caused the failure at boot but it seems to have cured itself. I'm back running the Radeon card for the minute and everything is working fine with that so ... my thought is that the problem described was caused by my clumsiness when installing the nVidia card ... perhaps it didn't quite seat it all the way into the slot ?

For later runs, the card worked but I had driver problems so that the highest Res  I could set was 1260x768 ... which is where we came in with this particular problem !

I'm working my way through the possibilities to set up the nVidia card now today (between other jobs that must be done) and I'll report later ASAP.

Regards ...

---

### Post by CatKiller on 2009-05-05
> **hatrack said:**
> perhaps it didn't quite seat it all the way into the slot ?

Sounds like it.

Good luck!

---

### Post by hatrack on 2009-05-15
Hi All !

I apologise for being off-line for a while ... a little matter of some minor eye-surgery has kept me away for my computer.

However, I'm back now and would firstly like to thank all who looked at my post and particularly those who kindly offered advice.

After a long, long struggle, the problem of monitor resolution/square pixels is finally solved. All that was needed was for me to write the correct vertical and horizontal ranges into xorg.conf !

I feel thoroughly stupid and apologise for wasting people's time ... my only excuse is that I'm very much a newbie to Linux generally so ... I haven't got the hang of it yet. But ... thanks to you all ... I'm learning !

Best regards ...

---

### Post by CatKiller on 2009-05-16
> **hatrack said:**
> I feel thoroughly stupid and apologise for wasting people's time ... my only excuse is that I'm very much a newbie to Linux generally so ... I haven't got the hang of it yet. But ... thanks to you all ... I'm learning !

Not at all. We all needed to learn once. Glad you're up and running now.

---

