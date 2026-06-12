---
title: "Laptop and external monitor visual effects don't work"
date: 2008-12-11
forum: General Help
---

### Post by mjschmidt on 2008-12-11
I've seen this topic "sort of" covered elsewhere, but I am a newb to Linux, so the explanations didn't really help me. I'm hoping someone can help by offering a solution, and explaining how exactly I go about implementing it.

I have a Toshiba Satellite P200 laptop hooked up to an external Samsung T220 LCD monitor. This set up works fine in Vista.

In Ubuntu, I have set it up to work like Vista, where the desktop is split across both screens (as opposed to mirrored).

Most of the time it works, but sometimes whether it is a reboot or a hard-boot, the external monitor stays blank, and I have to shut down and hard boot again.

When it does work, and I have both monitors working, visual effects will NOT work. When I am using only the laptop (no external LCD attached) the visual effects DO work.

I have looked at my xorg.conf, but I'm not sure what, if anything, I should change or add. Solutions I have seen so far aren't clear about what I should do.

I have also seen suggestions to disable "xinerama" but no explanation of how to do that (and I googled "disable xinerama").

I've also seen people talking about using TwinView, but no explanation about how to do that either.

Can anyone help? When it comes to Windows, I'd consider my self a power user, but I'm still learning the ropes of Linux. I am comfortable editing text files in gedit, and yes, I have read the article about the linux commands you should never type in to terminal. ;-)

Thanks!

---

### Post by gettinoriginal on 2008-12-15
I do not use dual monitors, but this is a guess that it is a conflict of video drivers between the two different monitors.  I do know that I have read many threads that when someone connects an external monitor they loose special effects and have to reset their Hardware Driver.  Good luck  :p

---

### Post by earthpigg on 2008-12-15
what video card are you using?

i had a similar problem with my nvidia card and 2nd display (in addition to laptop display)... switching from 173 to 177 driver fixed it.

---

