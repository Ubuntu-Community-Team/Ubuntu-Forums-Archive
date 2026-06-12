---
title: "Failed to load module &quot;fglrx&quot;"
date: 2009-07-10
forum: Desktop Environments
---

### Post by Jeenyus on 2009-07-10
Hi,
I've been using Jaunty since it came out and I also have an older ATI that isn't supported under the new X.  The other day I installed the suggested updates from the Update Manager and now whenever I try and boot up ubuntu I receive this message in a text box:

(EE) Failed to load module "fglrx" (module does not exist, 0)
(EE) No drivers available

There was a button to review the log so I took a look and saw that I'm running X.Org X Server 1.6.1.902 and that was about all I made of that. If anyone has any advice on how to get my machine working again I'd greatly appreciate it.

Thanks,
Jeenyus

---

### Post by RobertHamilton on 2009-10-11
I know this is an old thread, but why make a new one if there's already one here with the problem unsolved. :) 

I also have this problem after installing the latest ATI Catalyst Driver for my ATI HD 4850 from AMD's website and then removing it, following these instructions:

1. Launch the Terminal Application/Window and navigate to the /usr/share/ati folder.

2. With superuser permissions, enter the command "sh ./fglrx-uninstall.sh".

3. Reboot your system.


 to activate the fglrx one from System->Administration->Hardware Drivers... because i thought this might solve my problem i was having with Runescape (a java-based game) that I can't get into High Detail.

Some other details you might want to know.. I'm using 64bit Jaunty Jackelope and 64bit Google Chrome (not the chromium-browser); the actual google-chrome created for Linux users.

If you can help me solve both my problems that'd be fantastic!:KS

---

