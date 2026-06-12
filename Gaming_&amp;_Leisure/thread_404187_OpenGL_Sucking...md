---
title: "OpenGL Sucking.."
date: 2007-04-08
forum: Gaming &amp; Leisure
---

### Post by GSF1200S on 2007-04-08
On any game requiring OpenGL 3d rendering, one core of my processor will immediately jump to 100%, while the other cores usage stays at 0%. Occasionally the processors will switch.

It was rediculous enough where it even managed to be pulling 100% from one core playing pinball (!).

I can play Battlefield 2 all day on Windows without ever breaking 60% usage, but a pinball game causes my fans to come on all the time. Same with billiards, same with racing.. doesnt matter...

**edit** even typing glxgears in the terminal causes one cpu to shoot up to a hundred. For a while, the cores cycle. Then, it stops cycling and one just gets really hot. This crap has to be bad for a processor.

---

### Post by FoolsGold on 2007-04-08
This may be a stupid question, but are you certain that you've got hardware OpenGL running, and not the software renderer that's used when you haven't installed the drivers for your video card?

---

### Post by Feba on 2007-04-08
With GLX gears, this is normal, it's looking for all the performance it can. I don't think this should be happening during normal gameplay however.

---

### Post by r00tintheb0x on 2007-04-08
Do you come back with something like this?

michael@malakai:~$ glxinfo |grep rend
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 915G 20061017 x86/MMX/SSE2

---

### Post by GSF1200S on 2007-04-08
> **r00tintheb0x said:**
> Do you come back with something like this?

michael@malakai:~$ glxinfo |grep rend
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 915G 20061017 x86/MMX/SSE2


poeticrpm@poeticrpm-laptop:~$ glxinfo |grep rend
direct rendering: Yes
OpenGL renderer string: GeForce Go 7600/PCI/SSE2
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod,

---

### Post by GSF1200S on 2007-04-08
> **FoolsGold said:**
> This may be a stupid question, but are you certain that you've got hardware OpenGL running, and not the software renderer that's used when you haven't installed the drivers for your video card?

Yeah.. im pretty sure. The post above this one makes it seem like its working..

It works fine, but when my fan goes crazy over some pinball game, something just isnt right.

Also, if I use beryl, whenever the Diamond is in my system tray, my cpu goes right up to 100% as well. If I close the gem out, beryl still works but my system resources drop right back down into normal usages..

---

### Post by GSF1200S on 2007-04-08
Heres some screenshots of what im talking about... I cant really run any OpenGL stuff- this cant possibly be good for the processor...

---

### Post by GSF1200S on 2007-04-09
bump

---

### Post by hikaricore on 2007-04-09
I can't help but notice you have a page open about beryl.  Are you running beryl at the same
time as the games?  Because this WILL cause issues and you should use beryl-manager to
temporarily disable it.  Aside from that, which driver are you using?  Is it "nvidia" or "nv"?

---

### Post by kvonb on 2007-04-09
I wouldn't worry about it damaging your CPU.  Intel CPUs are designed to be able to run at 100% which will take them to their maximum rated heat output.

If it gets too hot, there is a thermal shutdown device built into the CPU, so it will temporarily shut itself down long before any damage occurs.

Which video driver did you install?  The official Feisty driver, or the binary from Nvidia?

Try switching them to see if it makes a difference.

I'm using the binary driver from the Nvidia web-site, and mine also runs the CPU at close to 100% when running Enemy Territory, however it switches between the CPU's every few seconds (I have a P4 Prescott, hyperthread) and it works fine.

Maybe you just never noticed it before!

Have you done ALL the Feisty updates?

I know that under Edgy I had to turn hyperthreading on with a kernel parameter, maybe that is the key!  I can't remember what it was now though, maybe search the forum for it.

Also I just noticed from my screenshot that gkrellm gives an average CPU usage, maybe try installing that (search in synaptic for gkrellm) and set it to show combined CPU usage.

I would think that is what any Windows CPU usage meter would show, hence the lower reported usage.  Just a thought!

---

### Post by GSF1200S on 2007-04-09
> **hikaricore said:**
> I can't help but notice you have a page open about beryl.  Are you running beryl at the same
time as the games?  Because this WILL cause issues and you should use beryl-manager to
temporarily disable it.  Aside from that, which driver are you using?  Is it "nvidia" or "nv"?

No.. I installed beyrl, but I rarely use it. I need to figure out how to get the emerald theme, because I cant stand not having min/max/ close in the right corner.

Im using the NVIDIA driver from the website. I could never get the GLX driver from the package manager to prevent the computer from crashing. Its impossible to have the GLX driver without having the restricted modules, which has the common kernel listed as a dependency... If I remove either the common kernel or the restricted modules, it removes the GLX driver. If I dont remove anything, I get an API mismatch and the Xwindow wont load. Installing the driver from the website, I can remove the the common kernel and restricted modules, and then I just compile the madwifi drivers from source off there website (for my wireless). 

I dont know.. Ive minimized BF2 (XP) and looked at the dual meters and both cores were running about 55%. God guys, I just hate seeing 100%. Ive had two Athlon processors crap themselves in the past. Ive been really defensive of this intel dual core.

Mine switches too.. for like a minute... then it just stops switching, and one stays 100% while the other one stays at 0-7%.

Am I just being paranoid? Any other ideas?

**Edit** The reason I had a page open about beyrl wasnt because of beyrl. I was looking for any threads dealing with high cpu usage.. I do try and figure this stuff out with search before I post a new thread...

**Edit2** Yes, I have all the upgrades. Seems like their is a lot in Beta releases..

---

### Post by Topper_H on 2007-06-09
I'm so glad I found someone who shares the same problem I have !
I'm getting mad with my openGL games that shoot my CPU to 100% for no reason. It seems indeed that the CPU load switches from one core to another randomly.

Interestingly, we share some common specs :
Athlon X2 3800+
Nvidia graphic card (FX5200) with proprietary drivers (from feisty repos in my case)

I encountered this problem with many openGL games so far :
- NWN
- Defcon
- Boson
-falconseye
- Pinball (come on this can't need 100% cpu !)

I've been tracking this bug for weeks and I also found another topic that could match : [http://ubuntuforums.org/showthread.php?t=452266](http://ubuntuforums.org/showthread.php?t=452266)

We sould share our experience and consider filing a bug report on launchpad

---

### Post by Topper_H on 2007-06-09
Ok I think I got it !

After reading some of your other threads concerning the nvidia panel, I started tweaking around and I found that the faulty parameter is "Sync to Vblank"
Switching this to ON solved all my OpenGL/CPU problems !!!

Hope it helps

---

### Post by Cappy on 2007-06-09
Could you please specify which "Sync to VBlank" you checked? 
In nvidia-settings it appears on the "X Server XVideo Settings" tab under "Video Texture Adaptor" and "Video Blitter Adaptor". It also appears on the "OpenGL Settings" tab.

---

### Post by Topper_H on 2007-06-09
Ok, in my config it's all unchecked in Xserver Xvideo settings, but checked in Opengl Settings.

Hope it'll help you guys.

---

### Post by GSF1200S on 2007-06-10
> **Topper_H said:**
> Ok, in my config it's all unchecked in Xserver Xvideo settings, but checked in Opengl Settings.

Hope it'll help you guys.

Ive come a ways since I first posted this topic. Just opening and closing the NVIDIA panel will make the CPU usage rest at usual levels. Still, I dont think a pinball game should demand 40% cpu usage. Ill see what happens when I reinstall Ubuntu... Kubuntu is nice and all, but Ive had too many dumb issues that really annoy me. Its too bad: I think KDE has more potential- haha, this is a different thread. Plus, GNOME seems to have come a long way since when I used it a few months ago..

Anyways.. just load the nvidia server settings and close it, and games will play at reasonable levels. You think checking the sync to vblank option is whats doing it, but ill almost gaurentee that a reboot will leave you with the same problem... until you reload the nvidia settings..

---

### Post by rax_m on 2007-08-19
Thanks for this thread.. Changing the Sync to Vblank setting under OpenGL Settings (nvidia-settings) stopped my one cpu from hogging 100% cpu as well :) 
I can now play soulfu without the temp of my laptop getting to 75 C ;)

---

