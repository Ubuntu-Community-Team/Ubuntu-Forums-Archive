---
title: "stuck at &quot;starting hotplug subsystem&quot;"
date: 2005-11-15
forum: Desktop Environments
---

### Post by JasonSwett on 2005-11-15
I know that other people have had this problem and posted about it here, but all the replies seemed to have been different and not helpful to me at all.

When I'm booting up, it gets stuck at "starting hotplug subsystem". I have no idea what this means or what caused it. I lost patience after waiting about 10 minutes and figured it would never boot up.

Does anybody know the answer? I'm a Linux beginner, so please go easy on me with the technical terms and stuff.

Thanks,
Jason

---

### Post by codejunkie on 2005-11-15
[quote=JasonSwett]I know that other people have had this problem and posted about it here, but all the replies seemed to have been different and not helpful to me at all.

When I'm booting up, it gets stuck at "starting hotplug subsystem". I have no idea what this means or what caused it. I lost patience after waiting about 10 minutes and figured it would never boot up.

Does anybody know the answer? I'm a Linux beginner, so please go easy on me with the technical terms and stuff.

Thanks,
Jason[/quote] it's kind of hard to give you an exact answer with so many hardware configurations out there so i'll try my best to help. i don't know for 100% certainty what all hotplug does, but i think hotplug automaticly set's up hardware like usb network sound card etc, and in my case i've noticed that i get that error when i have hardware conflict's like the two devices using the same resource. so you could try and trouble shoot this by removing undeeded devices like usb scanners web cams usb printers. also if you have more than on video card, sound card, installed in the system it can cause this. for example if your motherboard has onboard devices like video and sound and you installed an addon card in the system make sure you have disabled the onboard devices in the bios because they can conflict with the addon cards .

---

