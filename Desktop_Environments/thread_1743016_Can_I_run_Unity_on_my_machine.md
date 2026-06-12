---
title: "Can I run Unity on my machine?"
date: 2011-04-29
forum: Desktop Environments
---

### Post by timwryan on 2011-04-29
I have a Dell 700m. It has:
[LIST]
[*]1.60Ghz Intel Pentium M with 2048kB cache
[*]490740kB RAM
[*]Intel 855GME chipset
[*]OpenGL 1.4
[*] 1280x800 display
[/LIST]

The RAM is user-upgradable to 1GB (or even 2GB if I take apart the keyboard). The processor and chipset I can't do much about. Do I have any options besides purchasing anew computer/using Ubuntu classic?

Thanks,

Tim

---

### Post by 3Miro on 2011-04-29
If you can run OpenGL 1.4, then you should be fine.

Can you run desktop effects on 10.10? If you can run Normal desktop effects, then Unity should work fine.

You can always get a liveCD with Unity and boot form it to test.

---

### Post by timwryan on 2011-05-02
I did have screen effects in 10.4, but lost them in 10.10. This was annoying, but not so horrible. Not getting Unity is a little upsetting...

Some digging shows that here is some issue with drivers for the chipset I have. I looked at xorg yesterday and it seems like drivers are out there, but I do not understand how to install them. They do seem to exist, however. I think this is over my head to repair. I have trouble translating what I see on xorg into what I see in my package manager. If anyone feels like walking me through this, I would be much obliged.

Thanks for your help,

Tim

---

### Post by Rubi1200 on 2011-05-02
This:
> Intel 855GME chipset
could be a problem.

It's an older chipset which already had issues with 10.04 and 10.10. At the time, there were workarounds for that, but whether something like it exists for Natty I don't know.

For Unity hardware requirements, see here:
[https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements](https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements)
[https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements)

---

