---
title: "Resolution reverts to 640x480 when started with monitor not present"
date: 2005-11-06
forum: Desktop Environments
---

### Post by brucew on 2005-11-06
This problem was present in Hoary and continues in Breezy.

I have multiple PCs, a KVM (keyboard/video/mouse) switch and my LCD monitors are dual-input, digital and analog.  The Ubuntu box is connected through the KVM switch to an analog input on one of the monitors.  (My primary workstation uses both monitors on their digital inputs.)

When I start my Ubuntu box and don't immediately switch a monitor to it during the character-mode part of the boot process, when the graphic-mode login comes up, it's in 640x480 resolution, rather than 1024x768.  After logging-in, the System | Preferences | Screen Resolution dialog displays only 640x480 at 60Hz for choices.

The only fix I've discovered is to reboot, making sure the monitor doesn't auto-switch back to the digital input.  Then when the graphic-mode login comes up, it's in 1024x768 at my preferred refresh rate and the Screen Resolution dialog will display all resolutions and refresh rates.

I've verified this [http://www.ubuntuforums.org/showpost.php?p=248755&postcount=5](http://www.ubuntuforums.org/showpost.php?p=248755&postcount=5) and it always shows 1024x768 at 75Hz, even when Ubuntu has started at 640x480@60Hz.

What can be done to make Ubuntu honor my preferred resolution and refresh rates even when it cannot see a monitor when it boots?

---

### Post by mbailey on 2005-11-07
I see the same behaviour, which is worrying because I'm planning to run one of my boxen perpetually without monitor & connect to it via ssh or FreeNX from another. Is the machine's percieved resolution going to carry over into remote sessions too?

---

### Post by dto on 2005-11-07
Thanks for starting this thread. I have something like this going on as well, but it didn't dawn on me that it maybe related to the monitor being unaccessible during boot. I've got Breezy on three machines, two of which share a monitor via a KVM switch. I had only noticed this behavior on one of them, and now that you mention it, it is always when the monitor is not currently active when booting.

After boot, it shows me the GDM login screen in a non-default resolution. Hitting ctrl-alt-backspace resets it to the correct resolution. 

It will be interesting to see if there is a useful fix for this.

---

### Post by soulglo83 on 2005-11-07
i get the same problem but its present even if the moniter is active at the time x launches, starting x  with the kvm intermediatary to the moniter and pc, will force 640x480. if restarting or starting x with the moniter plugged in directly to the vga card it will correctly recognize the moniter and allow me to change resolution within the moniter and vga card's acceptable ranges.  notice this problem is present as described above by other posters in kubuntu as well, however with the kvm plugged in i can start kubuntu and it will not force 640x480 whereas standard ubuntu does.  its ashamed that this error was present in warty and seems so simple as it is not present in any other distro's (for me anyway) thats including debian sarge. i wish i had some useful information for u, but with how many people have had and continue to have this problem, and so few people with valuable advice or bugfixes, its probably something us ubuntu fans will have to live with (unless we switch our hardware or to another distro). well im glad it works for u guys, but simply having my moniter active throughout booting isn't enough :(

---

### Post by MrFahrenheit on 2005-11-09
Hey, I'm not the only one that has this problem apparently!

---

### Post by brucew on 2005-11-09
[QUOTE=MrFahrenheit]Hey, I'm not the only one that has this problem apparently![/QUOTE]
Nope.  And I'm not sure whether that's good or bad. :)

[quote=dto]Hitting ctrl-alt-backspace resets it to the correct resolution.[/quote]

Thanks, I didn't know that one.  Much easier than rebooting.

I've messed around with settings in xorg.conf to no avail.  Digging through the logs, near as I can tell, every time Ubuntu starts it tests to see if you've replaced the monitor, then uses settings appropriate to that monitor.  Not a bad approach, except for when it fails to detect any monitor at all and reverts to lowest-common denominator settings.  IMHO, it should revert to last-known-good if it's not going to honor user-preferred.

---

### Post by metasyntax on 2005-11-09
The "desktop" resolution will not affect a freenx connection, it is a seperate thing.

brucew: under the "screen" section in /etc/X11/xorg.conf, you could edit the "Modes" lines and only put in the resolutions you want to run in.  CAVEAT:  it is possible that X may not start after you do this so make a backup copy of your xorg.conf berfore editing.  If you play games or run programs that want to run in full screen, x will not be able to switch to an unlisted resolution (i.e. quake3 may not run at 640x480 because you do not have the mode listed).

---

### Post by brucew on 2005-11-09
[quote=metasyntax]under the "screen" section in /etc/X11/xorg.conf, you could edit the "Modes" lines and only put in the resolutions you want to run in.[/quote]

Already tried that--one of several things I messed around with in xorg.conf.  No joy.

---

### Post by ceejay13 on 2005-11-25
Any further ideas on this? 

I have the same problem and I have 3 systems that I am running as servers with the high probability of no monitor connected on boot.

Any assistance gratefully received :D

---

### Post by brucew on 2005-11-25
Sorry, I've neither heard nor found anything else.

But, as suggested by dto (above), the Ctrl-Alt-Backspace to restart X-Server works well and consistently.

---

### Post by KermitJr on 2005-12-01
Here's the answer!!!! (I hope)

I was having trouble with several older video cards and a particular monitor and kept getting 640x480 no matter what I did for modes, etc.  

HOWEVER, when I went back one time and ran
```
sudo dpkg-reconfigure xserver-xorg
```

I entered the actually amount of RAM on the video card (one was 4096 and another 2048) and PRESTO! My Modes line worked as normal with or without monitor on boot.

So try entering in the actual video RAM you have and that should hopefully fix your error.

If not, troubleshoot by looking for the actual error messages in the /var/log/X11/xorg[tab].log file.

Hope this helps!
KermitJr

---

### Post by ebarreda on 2005-12-16
I have the same problem too.

I was even considering using a VGA terminator to fool the system to believe that there is a monitor connected.  I've seen some people suggesting that one can be made using three 75 ohms resistors between pins 1-6, 2-7 and 3-8.

Just came up with something on another thread and it works!

Need to modify the /etc/X11/xorg.conf to add three lines:

- Monitor section
    HorizSync      48-50
    VertRefresh   59-61
- Device section
    Option          "NoDDCValue"

---

### Post by Mad_Max_1412 on 2008-01-10
Guys,

Has anything further been developed to fix this issue as I have it with 7.10.  I use a KVM to switch my monitor/keyboard/mouse between my Ubuntu box and Windows box and if I don't have the Ubuntu box selected on boot-up then I get the low resolution.

If nothing else has appeared since, then I will try the options ebarreda wrote which were:
> 
Need to modify the /etc/X11/xorg.conf to add three lines:

- Monitor section
HorizSync 48-50
VertRefresh 59-61
- Device section
Option "NoDDCValue"

---

