---
title: "xorg resolution dosent stick when using a KVM"
date: 2009-01-14
forum: Desktop Environments
---

### Post by oaqster on 2009-01-14
hi everyone!
i've been searching through the forms and have tried a number of things with some success but am still not getting the results that i should be getting.  basically i have an LCD panel (BENQ E2400HD) and have an nvidia card (GeForce4 MX 4000) and they work fine together giving me the max resolution on my LCD (1920x1080) - the issue is when i introduce a KVM into the mix as i want to have the ability to use the bigger screen with my work laptop running **eViL** vista (which by the way is able to apply the full resolution & remember it)

i had setup the nvidia drivers using EnvyNG and everything works great with all the compiz eye candy i want enabled.

i had read on a number of posts that keeping the KVM pointed to the ubuntu box while it boots will fix the problem, but it really makes no difference in my case. going throught the kvm during startup X would complain about display configuration and land me into a painful 640x480 or an equally painful 800x600 resolution, looking at my xorg.conf it seemed like it was relying alot on auto-detecting everything at startup as it didnt have much to it, so i started probing my hardware and updated the xorg.conf to have more infomraiton about the monitor and the vga card.

attached: xorg.conf_orig and xorg.conf_curr

i believe that i should be able to provide enough information in the xorg.conf to be able to tell ubuntu not to try and detect it but seems like i've not quite given it enough, because according to the Xorg.0.log its still trying to detect my stuff and is assuming a standard CRT, after the changes i did to my xorg.conf X boots up with 1024x768 which is better than the 640x480 but still not ideal, i vud b able to live with this if it gave me the option to switch to the resolution i want and it doesnt System -> Preferences -> Screen Resolution has 1024x768 as the max, System -> Administration -> Nvidia X Server Setting however has the option to switch to 1920x1200 which is close but not perfect and as the LCD doesnt have any presets for that i get bad fonts and even the screen becomes a little jittery.

ive run a few tests to proble the hardware & settings with & without the kvm attached, outputs of which i've attached here, with the Xorg.0.log files for both situations

attached: xorg_tests, Xorg.0.log_direct and Xorg.0.log_kvm

one of the intresting things is the output of ddcprobe, which fails to probe the monitor while connected through the kvm

[B]edid: 
edidfail[/B]

while it detects the LCD and all its modes fine while connected directly

[B]edid: 
edid: 1 3
id: 790d
eisa: BNQ790d
serial: 00005445
manufacture: 44 2008[/B]

etc. etc.

also in the Xorg.0.log while having the kvm connected its still probing the hardware and removing the display mode i added

(II) NVIDIA(0): NVIDIA GPU GeForce4 MX 4000 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.18.20.38.00
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce4 MX 4000 at PCI:1:0:0:
[B][COLOR="Red"](--) NVIDIA(0):     CRT-0
(--) NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "1920x1080_50+0+0"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
[/COLOR][/B](WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp

so the basic question is how can i make the settings for my monitor that i know works to STICK and skip the detection and auto-select part while X starts. am i missing some stuff that needes to be added to the xorg or what?

sorry for the looong post, just wanted to provide as much information as i had.  ooh almost forgot im running Hardy 8.04 & uname -r = 2.6.24-23-generic
thanx!
oaqster

---

### Post by oaqster on 2009-01-14
bump

---

### Post by oaqster on 2009-01-15
bump *again*
someonez gotta have some idea whats going on??
still trying other stuff but no real progress - will report back....

---

### Post by oaqster on 2009-01-16
okay - managed to force my display into the xorg even though the system is unable to proble the hardware. :guitar: reading the documentation for the nvidia driver 

[http://http.download.nvidia.com/XFree86/Linux-x86/1.0-9629/README/appendix-d.html](http://http.download.nvidia.com/XFree86/Linux-x86/1.0-9629/README/appendix-d.html)

i found an option called CustomEDID, using which you can provide details of your display stored on your filesystem as opposed to having it probed at startup.  to create the file simply go to the System -> Administration -> NVIDIA X Server Settings, and under your GPU the diplay CRT or DFP will be listed clicking on it will give a tab with a button called Acquire EDID.  with the display connected directly use that button to generate a edid.bin file (you can name it what ever), this will contain all the information about your display that the xorg needs. now just add the CustomEDID option to the Device section.

Option		"CustomEDID" "CRT-0:/somelocation/somewhere/edid.bin"

just replace CRT-0 with what ever device its recognized as, CRT, DFP or TV, and provide the path to your edid.bin file.  now when i connect through the KVM i get booted up in the correct resolution, and the system knows what the monitor is.

the hardware still cant probe the display (ddcprobe fails in edid) - but xrandr reports everything correctly and i have what i need.

reading up on my KVM i found out that good KVMs will provide the probe information back to the PCs regardless of which one is in focus, most good ones will only provide it back to the one in focus, but unfortunately in my case if you have a really cheap one it will not provide any information back to the any of the PCs - so ppl i would recommend to stay away from this KVM - model number: MT401UK

[http://www.pacificgeek.com/product.asp?id=85089](http://www.pacificgeek.com/product.asp?id=85089)

lesson learnt: spend a little more upfront to reduce headaches later on

---

### Post by information_entropy on 2009-01-16
Thanks for the information.

I was having a similar problem with a system that I use for testing that
normally does not have a monitor attached.

When I upgraded it  8.10 from 8.04, as soon as I disconnected the monitor
the resolution went to 800x600 or 640x480 (depending on installed video card).

If I accessed it with remote desktop viewer or any vnc viewer the
resolution was fine as long as the system was started with a monitor
attached.

I got it to work by editing xorg.conf,  but your solution is probably better.

Thanks for reading the manual for me. :)
I will try that as soon as I have time.

---

