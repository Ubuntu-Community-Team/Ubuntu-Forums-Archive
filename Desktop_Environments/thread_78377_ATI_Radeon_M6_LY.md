---
title: "ATI Radeon M6 LY"
date: 2005-10-18
forum: Desktop Environments
---

### Post by ahillerin on 2005-10-18
I ve got the this card ATI Radoen M6 LY...(it s on a DELL C510 with Ubuntu Breezy). I just  want to know if someone already succeed to make it working with a resolution of 1280*1024 ... Actually I tried several configuration (in xorg.conf), and by looking on the net (that why I didnt put the fglrx driver) but I don t have any solution yet... 

NB: I have astrange message in the Xorg.0.log  saying that "Panel Size from BIOS: 1024x768" but I dont know if it is link!!! 

so I set the xorg.conf as this:

....
Section "Extensions"
Option "RENDER" "Enable"
EndSection
....

Section "Device"
Identifier "ATI Technologies, Inc. Radeon Mobility 9000 (M6 LY)"
Driver "ati"
Option "AGPMode" "4"
Option "AGPSize" "64" # default: 8
Option "RingSize" "8"
Option "BufferSize" "2"
Option "EnablePageFlip" "True"
Option "EnableDepthMoves" "True"
Option "RenderAccel" "true"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "Screen 1"
Option "DPMS"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Radeon Mobility 9000 (M6 LY)"
Monitor "Screen 1"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1200x1024" "1024x768"
EndSubSection
..
up to Depth 24

...


but all the time i have an error messages in the Xorg.0.log

(II) RADEON(0): PLL parameters: rf=2700 rd=60 min=12000 max=35000; xclk=16600
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEON(0): Validating modes on Primary head ---------
(II) RADEON(0): Panel ID string: 1024x768
(II) RADEON(0): Panel Size from BIOS: 1024x768
(II) RADEON(0): BIOS provided dividers will be used.
(II) RADEON(0): Total number of valid DDC mode(s) found: 0
(WW) RADEON(0): Mode 1200x1024 is out of range.
(WW) RADEON(0): Valid modes must be between 320x200-1024x768
(II) RADEON(0): Valid mode using on-chip RMX: 1024x768
(II) RADEON(0): Total number of valid FP mode(s) found: 1
(--) RADEON(0): Virtual size is 1024x768 (pitch 1024)
(**) RADEON(0): *Mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1024x768" 65.00 1024 1040 1176 1344 768 770 776 806

I tried also with different parameter for vsync in the Monitor section but without success...


Anybody already successed to have this resolution on such kind of card?

---

### Post by nobby_trussin on 2005-10-18
looks like you've put 1200x1024 in your conf file which is why you're getting an out of range error shouldn't it be 1280x1024 :)

also, if you still can't get it to work, perhaps try getting the proper ati drivers off the ati site as i expect the ones that come with breezy are very much generic

regards

nobby

---

### Post by ahillerin on 2005-10-18
Oups sorry I was also done with 1280*1024

That s my problem this card normaly can support 1280x1024 but i cannot set it (max is 1024*768)... So that i wanted to know if someone already succeed to to this with such kind of card...

I tried with the ati driver and also with radeon one but each time with no success.

---

### Post by nobby_trussin on 2005-10-18
that's what i mean though. you need to put 1280x1024 in your xorg.conf instead of 1200x1024

---

### Post by nobby_trussin on 2005-10-18
ah sorry i see what you mean. could it be the monitor type that needs changing and can't handle the higher res.

oh the joys of linux :)

---

### Post by ahillerin on 2005-10-18
Maybe.. the only thing that I can tell is that on M$$$ XP  it s working fine !! I tried also to uptdate the monitor with synch parameters but it didnt help to pass the 1024*768 boundary!!! :???:

---

