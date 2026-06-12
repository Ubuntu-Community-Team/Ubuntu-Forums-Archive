---
title: "xserver very low resolution and xorg.conf limited"
date: 2008-11-08
forum: Desktop Environments
---

### Post by recklessray on 2008-11-08
hi, my xserver is very simple. or i am, probably the latter.

```

here is xorg.conf:

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

..and here is the output from lspci | grep -i vga

```

root@xen:~# lspci | grep -i vga
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)

```

so, there we have it. my screen resolution is 600 x 800 on a nice new big monitor. i'd settle for 1280 x 720. but no matter what i try dpkg-reconfigure-xserver for instance make a blind bit of difference. ive swapped cards as with this current nvidia 5500 from a similar nvidia just in case anything odd was happening with the old one. still no use. 

i would be eternally grateful if any of my learned friends in the ubuntu forums could shed even a dim glimmer of light on my dilemma here. any commands i might try, or size of lump hammer to hit the darn thing with...

i have googled this, but i do now write in veritable desperation! 

i love linux - doesnt it keep you on your toes?! 

many thanks in advance for any help offered.

ray o/

---

### Post by roberto.eiberle on 2008-11-08
If you paste this in Xorg.conf just after device and before Endsection you should be able to select any of these resolutions



SubSection "Display"
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection

worked for me, I copied it over from my 8.04 install as I had the same problem in intrepid

---

