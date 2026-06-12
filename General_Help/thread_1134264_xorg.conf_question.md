---
title: "xorg.conf question"
date: 2009-04-23
forum: General Help
---

### Post by anv on 2009-04-23
where is the new configuration information which earlier were inside xorg.conf. referring these lines which mention that something is configured in some other place than in xorg.conf: 

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
EndSection

"Configured Video Device"

so where is the configuration data and how I can put my hands into it. can I have somehow the old way back to my installation?

---

### Post by ubu-for on 2009-04-23
I had the same problem and could solve it by backing up my xorg.conf, starting "NVIDIA X Server Settings" as root, saved some changes to my xorg.conf within "NVIDIA X Server Settings" and Ubuntu didn't ignore my new xorg.conf settings any longer.

[http://ubuntuforums.org/showpost.php?p=7000752&postcount=14](http://ubuntuforums.org/showpost.php?p=7000752&postcount=14)

---

