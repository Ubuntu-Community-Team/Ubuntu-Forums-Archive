---
title: "Unity 8 and Mir in Ubuntu 14.04 LTS"
date: 2014-04-22
forum: Desktop Environments
---

### Post by ccmiller12 on 2014-04-22
So once when they are released, will users be able to install Unity8 with Mir on top of Ubuntu 14.04 LTS? If so, do you think it would it be safe to do so? I'd like to have Unity 8 and Mir installed, but also want to keep my LTS version of Ubuntu too.

Cheers,

Cmiller

---

### Post by grahammechanical on 2014-04-22
There is something we must be clear about. Ubuntu 14.04 runs on the Xserver and Unity 7 and will do so for the length of its 5 year support period. 

It should be possible to install a Unity 8 preview session in 14.04. We get a login option. The package is in the software centre and is called unity8-desktop-session-mir. It is described as a desktop session running Unity 8 on a Mir backend. It is for evaluation and demonstration purposes only. And it does not work at all on my system. We need to wait a bit longer for this.

The software centre also has unity-desktop-mir which brings in Xmir. I have not found any problems with that. We do need to use the open source video drivers. There is also in the software centre Unity 8 but it is months since I experimented with it. I cannot remember how well it works. This was back in the days when it was thought that Xmir would be default in 14.04 but since the developers gave up on that idea all effort for Unity 8 was directed at Unity 8 on phones and tablets. And on those devices both Mir and Unity 8 are working well, so I hear.

I do know that Mir and Unity 8 go together. So, I am guessing that we will not be seeing Mir/Unity 8 in desktop Ubuntu until Ubuntu 14.10. It may be that in time we may be able to convert Ubuntu 14.04 from Xserver/Unity 7 to MIr/Unity 8 but it will only be by user choice.

Regards.

---

### Post by olliemonster on 2014-05-14
Yes i think so if you install the package unity8 it should run in qemu and unity8-desktop-session-mir and unity8-desktop-session-x11 would only add themselves to the desktop switcher and if it fails you could you ctrl alt and a fn key from 1 to 6 to get to a tty console.

---

