---
title: "Can't Warm Reboot"
date: 2008-07-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by End3r on 2008-07-20
I have been trying to update my BIOS on my m1330, and this requires a warm reboot.  So, I go to System->Quit->Reboot.  

I'm greeted with the following (In order):[LIST]
[*]A bunch of "Network-Manager" errors
[*]The Ubuntu Splash (with the progress bar)
[*]A blank screen for a few moments (at which point the fan stops and the hard drive spins down)
[*]A bunch of colorful vertical lines that gradually fill the screen)
[/LIST]
The system freezes there and won't continue.

If I hit ESC I can get the computer to finish rebooting, but it doesn't install the BIOS update.  (Seems like the equivalent of a hard reset.)

I've tried a few solutions to this problem (including one detailed [here]("http://blog.avirtualhome.com/2008/03/10/ubuntu-shutdown-problem-cifs-related/")) involving altering the order in which samba shares/the network are shut down. And nothing has worked yet.

Any help would be greatly appreciated.

---

### Post by Potatoj316 on 2008-07-21
I think its the same thing as a hard reboot but this might work.  Next time it has that problem try pushing these keys one at a time while holding left alt+SysRq, r s e i u b  (put a small pause between each) ex. alt+sysrq+r, alt+sysrq+s...

when you push alt+sysrq+b it should turn the computer off, but again it is probably not what you want, but worth a try

---

### Post by End3r on 2008-07-21
Yes, I think that forces a hard reboot. (And has the same effect as hitting ESC when I get stuck.)

Also, I should add that this problem happens *whenever* I try to warm reboot.

---

### Post by atlas95 on 2008-07-23
Do you have the "dkms" package installed? If yes remove it and retry !
I had the same problem, and after a motherboard change on my m1330, same problem again, and after some search removing dkms resolve the problem.
Say me if it is good for you.
;)

---

### Post by End3r on 2008-07-23
good news: removing dkms fixed the rebooting problem
bad news: dkms is required by the envy nvidia graphics card driver packages (nvidia-glx-new-envy etc.)

Basically, removing dkms nukes my graphics setup...

Thanks for the prompt response(s)

---

### Post by atlas95 on 2008-07-23
Heyhey, install handly the last nvidia driver (.run) on the official website.

:D
It is what I do, and I have a new motherboard just due to dkms :p
Thanks to dell and my bad tweaks :D

ps: Uninstall nvidia-glx-new-* first :) see the doc for do this installation correctly.

---

### Post by End3r on 2008-07-23
Well, unfortunately it seems as though removing dkms/using the non-envy nvidia packages didn't solve the issue.  It seems that the problem is caused by the nvidia package (which I'm not too keen on removing.)  Do you have any other ideas?

---

### Post by atlas95 on 2008-07-23
Yes, here my custom xorg.conf, compare with me, I have disable #    Option         "OnDemandVBlankInterrupts" "True"
for remove the problem too, i don't know what is the really problem, but with those some tweak, i have more less the problem.
```


Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G80 [GeForce 8400M GS]"
    Monitor        "Écran générique"
    DefaultDepth    24
#    Option "ConnectedMonitor" "DFP"
    Option         "AllowGLXWithComposite" "true"
    Option         "BackingStore" "True"
#    Option         "OnDemandVBlankInterrupts" "True"
    Option         "Coolbits" "1"
    Option         "TripleBuffer" "true"
    Option         "NoLogo" "True"
    Option         "RandRRotation"
    Option         "NvAGP" "1"
#    Option         "DynamicTwinView" "false"
    Option         "TwinView" "True"
    Option         "MetaModes" "nvidia-auto-select, nvidia-auto-select"
#force Powermizer to a certain level at all times
# level 0x1 = highest
# level 0x2 = med
# level 0x3 = lowest
# Option	"RegistryDwords"	"PowerMizerLevel=0x3"
    SubSection     "Display"
        Depth       24
        Modes      "1280x800"
    EndSubSection
EndSection



```

---

### Post by End3r on 2008-07-24
I have a much simpler xorg.conf that does not include that option.
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection
```

---

