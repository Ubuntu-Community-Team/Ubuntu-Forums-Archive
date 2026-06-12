---
title: "Kubuntu 8.10 with Wubi: Can't increase resolution"
date: 2009-01-25
forum: General Help
---

### Post by Annorax on 2009-01-25
Hi all,

I have Windows XP and installed Wubi with Kubuntu 8.10. I am unable to increase my resolution past 800x600. 

I added the resolutions to my xorg.conf and restarted via CTRL+ALT+BACKSPACE but under Display in Settings I cannot set it past 800x600.

Can someone please tell me how to increase this? :)

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1200x800" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

---

