---
title: "ubuntu 8.10 resolution help"
date: 2009-01-29
forum: General Help
---

### Post by scrilla on 2009-01-29
well im completley new to linux as of yesterday. i installed ubuntu on my secondary hard drive to see what linux was all about. it went smooth no problems. now that its installed i have a problem where i cant get a higher resolution then 800x600 and its driving me nuts. ive googled out the ying yang and tried editing the /etc/X11/xorg.conf file as per suggested by some people... that didnt work. i learned all about the repository and got myself Envy and that didnt work. so now im stuck as to what i really need to do to fix this problem. i have a dell 15" lcd monitor model e152fp, my computer is a hp pavilion a705w and im using the integrated video. all i know about the video is the hp site says its "intel extreme graphics" doesnt say anything else. the chipset is 845gv. if someone can please help me with a solution to this id greatly appreciate it. im loving the new experience of another os but im not liking this resolution one bit. here is my xorg.conf... right now its using "vesa" which would explain the low resolution. hopefully someone knows exactly what .rpm i need to download to get this functioning correctly or what i need to do to fix it. thanks for taking a look and i appreciate any help.

Section "Device"
Identifier "Configured Video Device"
Driver "vesa"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection

---

### Post by gee-jay on 2009-01-29
I have almost exactly the same problem (new to Linux, installed it on a second harddrive yesterday). I've also played around with the xconf file, but with no success. I've got an NVIDIA graphics card though.

So, sorry not able to help, but just thought I'd share my frustration!

Gareth.

---

### Post by mixmaster on 2009-01-29
For what it is worth I could never get the Intel integrated graphics on my desktop machine to work properly under Intrepid, although some people seem to have managed it on some chipsets.  It did work on Hardy using an Edgy generated xorg.conf, although Hardy could never create a workable x setup during an install.  I currently have a bug-report open on this issue.

I eventually bought an el-cheapo ATI card in a clearance sale.

---

### Post by russu52 on 2009-01-29
have you tried adding this subsection at the very end of section "screen", just before "EndSection"?

Subsection "Display"
Mode "1024 x 768"
EndSubsection

---

### Post by scrilla on 2009-01-29
i tried adding just that to xorg.conf but after i save then refresh and all i get is a black screen then when i reboot it follows with config errors it says and puts me back in low resolution mode

---

