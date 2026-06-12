---
title: "Video display problems after install"
date: 2005-12-10
forum: General Help
---

### Post by baskin on 2005-12-10
I just finished the install of breezy.  Display works fine through the startup screen with all of the system checks reading OK.  But as soon as the checks are through, the monitor flashes off.  It looks like there is no communication between the CPU and monitor.

I'm using a biostar P4M800-M4 motherboard with onboard video.  The onboard video is S3 UniChrome Pro.  The monitor is an old HP Pavillion D5258A.

I am very much a newbie to Linux and Ubuntu.  Would apprecaite any help in "idiot" terms  ;)

---

### Post by infoseeker on 2005-12-10
I had a blank screen when my shared graphics memory was too low. Setting it to 16MB sorted out that problem ;)

If you have an old monitor then you might have to edit the '/etc/X11/xorg.conf' file to reduce the resolution.
The best way to do this is probably to boot up the pc and select 'recovery mode' and when you get to the prompt type

nano /etc/X11/xorg.conf

Edit the xorg.conf file, removing anything above '800x600'

This is an example (mine) :
> Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Device"
	Monitor		"710S"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
and at other depths as well if you have them  ;)

---

### Post by baskin on 2005-12-11
Thanks, got it to work!  Chose 800x600 in xorg dialogue, then when the GUI started it went to 1024x768. 

But turns out the sound isn't working now.  The correct on-board sound is being recognized, but no output.  Did get some mic sound to show on the montior, but can't hear anything coming out.

---

