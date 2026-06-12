---
title: "Can Unity be installed alongside LXDE?"
date: 2012-12-15
forum: Desktop Environments
---

### Post by JamesTheAwesomeDude on 2012-12-15
I'm wondering if it is possible to install Unity alongdise LXDE.
Is Unity itself a Desktop Environment?

I'm wondering this because I was given an old computer. It was missing a hard drive, and it had a few other issues, but I got those fixed, and put a hard drive in. I then installed Lubuntu.

I've not been using it for very long, but one thing that I miss greatly is the Unity panel.
I'd like to install Unity, if possible. I've heard that sudo apt-get install ubuntu-desktop will do it, but I don't want to install the full ubuntu desktop. I just want to add Unity to my Lubuntu desktop.

Another thing that is a concern is whether my computer is powerful enough to run Unity smoothly.

Here are the processor's stats (copied from the System Information):
```
-Processor-
Name        : AMD Athlon(tm) 64 Processor 2800+
Family, model, stepping        : 15, 4, 8 (AMD Opteron/Athlon64/FX)
Vendor        : AuthenticAMD
-Configuration-
Cache Size        : 512kb
Frequency        : 800.00MHz
BogoMIPS        : 1599.58
Byte Order        : Little Endian
-Features-
FDIV Bug        : no
HLT Bug        : no
F00F Bug        : no
Coma Bug        : no
Has FPU        : yes
-Cache-
Level 1 (Data)        : 2-way set-associative, 512 sets, 64KB size
Level 1 (Instruction)        : 2-way set-associative, 512 sets, 64KB size
Level 2 (Unified)        : 16-way set-associative, 512 sets, 512KB size
-Capabilities-
fpu        : Floating Point Unit
vme        : Virtual 86 Mode Extension
de        : Debug Extensions - I/O breakpoints
pse        : Page Size Extensions (4MB pages)
tsc        : Time Stamp Counter and RDTSC instruction
msr        : Model Specific Registers
pae        : Physical Address Extensions
mce        : Machine Check Architeture
cx8        : CMPXCHG8 instruction
apic        : Advanced Programmable Interrupt Controller
sep        : Fast System Call (SYSENTER/SYSEXIT)
mtrr        : Memory Type Range Registers
pge        : Page Global Enable
mca        : Machine Check Architecture
cmov        : Conditional Move instruction
pat        : Page Attribute Table
pse36        : 36bit Page Size Extensions
clflush        : Cache Line Flush instruction
mmx        : MMX technology
fxsr        : FXSAVE and FXRSTOR instructions
sse        : SSE instructions
sse2        : SSE2 (WNI) instructions
syscall        : SYSCALL and SYSEXIT instructions
nx        : No-execute Page Protection
mmxext        : Extended MMX Technology
lm        : LAHF/SAHF in long mode
3dnowext        : Extended 3DNow! Technology
3dnow        : 3DNow! Technology
up        : smp kernel running on up
rep_good        : rep microcode works well on this CPU
nopl

```

Anyway, the things I'd like to know are:

- Does Unity replace LXDE? (where you have to choose at login) Or can the Unity panel be run alongside LXDE?
- Is the computer even powerful enough to run Unity? (Currently, I have 503MB of RAM, but I'm going to get at least 500 more very soon.)
- Anything else I should know (e.g., Unity makes comptuters older than 2010 explode, etc.)

---

### Post by JRV on 2012-12-15
> - Does Unity replace LXDE? (where you have to choose at login) Or can the Unity panel be run alongside LXDE?

I don't know, I have not tried it. My guess would be no, you can't run LXDE and Unity simultaneously.
> 
- Is the computer even powerful enough to run Unity? (Currently, I have 503MB of RAM, but I'm going to get at least 500 more very soon.)

Ubuntu 12.10 uses the CPU to run unity if the graphics card is not up to the task.  
If your system has a good graphics card it will be a little slow.  
If the graphics card is not up to the task it will be painfully slow.

> 
- Anything else I should know (e.g., Unity makes comptuters older than 2010 explode, etc.)


Ubuntu 12.04 will run Unity 2d if the graphics do not support Unity. This is a much better choice for older hardware.

However on my 2 GHz Pentium 4 LDXE is noticably faster than Unity 2D.

I hope this helps.

---

### Post by Frogs Hair on 2012-12-15
Unity is a Compiz plug-in and I tried to enable Unity in XFCE from the CCSM and It did not start. I don't have LXDE installed though.

---

### Post by amjjawad on 2013-03-13
Hi,

Thank you for asking and thank you for choosing and using Lubuntu :)

I'm one of Lubuntu Team Family and I have read your post. Actually I was doing some search on google and found your thread :)

Anyway, from my experience with Lubuntu and Ubuntu, I would recommend NOT to go for that for some reasons:

1- Users need to understand that LXDE is a Desktop Environment that is using OpenBox as a Window Manager. Any other Window Manager that a user likes to use, he/she needs to replace Openbox with the other desired Window Manager - that is another story :)

2- Installing a desktop Package, for example "ubuntu-desktop" is NOT like installing Ubuntu. Same goes for Lubuntu. If you have Ubuntu, installing "lubuntu-desktop" is not like installing Lubuntu.

3- Installing Unity on Lubuntu does not make sense to me at all. In fact, it kills the whole idea of Lubuntu which is designed to be light, fast and simple.
I have no idea if you can install JUST Unity without all the other stuff or you can't but that doesn't matter; I suggest not to do that.

Unity will not run smoothly even with 1GB RAM. Unity is being heavily developed and day after day, it is getting more features. Last time I was on Unity (2 years) and 2GB RAM, it was giving me hard time.

If you want to give it a try for your own reason, Dual-Boot with Ubuntu and you will feel the difference OR just intall "ubuntu-desktop" which I personally never recommend.

By the way, YOU CAN actually customize your Lubuntu Desktop to be similar (not 100% like) to Unity ;)

If you are still interested and if anyone else interested, please let me know.
Well, it is not a secret so here you go:

1- Create a new Panel OR just move the default panel 
2- Keep that panel on the left side
3- Change the height of the panel, etc
4- Enlarge the size of the icons
5- Add more icons

You will get something similar to Unity without changing major stuff or installing anything :)

Thanks!

---

### Post by quequotion on 2013-03-13
> **JamesTheAwesomeDude said:**
> I'm wondering if it is possible to install Unity alongdise LXDE. It is.
> Is Unity itself a Desktop Environment?It's a compiz plugin masquerading as a DE. I prefer to call Ubuntu's DE "Ayatana", after Canonical's UI subproject, and refer to only the launcher and panel as "Unity", but there is no consistent usage of either anywhere.

> I'd like to install Unity, if possible. I've heard that sudo apt-get install ubuntu-desktop will do it, but I don't want to install the full ubuntu desktop. I just want to add Unity to my Lubuntu desktop. You can install Unity separately from ubuntu-desktop. To get the basic Unity desktop, you could install just the "unity" package, but it will be somewhat difficult to get set up (no access from the login screen, etc).

To make things easier on yourself, you could install "gnome-session" as well. (Unlike other DEs, Unity does not have a distinct "unity-session" package to make it available at the login screen: Canonical has rolled this into the "gnome-session" package.)```
sudo apt-get install unity gnome-session
```This should be much smaller than installing all of ubuntu-desktop, but the dependency tree is still extensive. As far as I can tell, there's no longer any way to run Unity without Compiz.

> Another thing that is a concern is whether my computer is powerful enough to run Unity smoothly.What kind of video card do you have? Your CPU specs look fine, but GPU is more important for Unity.

> - Does Unity replace LXDE? (where you have to choose at login) Or can the Unity panel be run alongside LXDE?If you installed unity and gnome-session, you should have "LXDE" and "Ubuntu" to choose from.
> - Is the computer even powerful enough to run Unity? (Currently, I have 503MB of RAM, but I'm going to get at least 500 more very soon.) Unity takes about 200MB of VRAM for me, but that varies by setup.
> - Anything else I should know (e.g., Unity makes comptuters older than 2010 explode, etc.)Unity is neither your only option, nor your best option (in my opinion). [Take a look at my thread on custom Pantheon DE]("http://ubuntuforums.org/showthread.php?t=2124220")s. Pantheon is a relatively lightweight and highly modular DE from the [elementary project]("http://elementaryos.org/"). ```
sudo add-apt-repository ppa:elementary-os/daily
sudo apt-get update
sudo apt-get install pantheon-shell
```

I put together a feature-rich desktop with winpanel, plank, and openbox that runs on less than 40MB of VRAM.
Furthermore, the dependencies for Pantheon are delightfully few.
Plank supports libunity, and has just about all the features you'd want from Unity's launcher.
Wingpanel also supports most of what you'd want from the Unity panel, except global menus (at the moment)...

I don't know if the elementary developers plan to add support for indicator-appmenu in the future or not, but for now the plugin is blacklisted in wingpanel's configuration and wingpanel will crash on start if it is not.

I have Openbox, Pantheon, Unity, and some hybrids of them installed and working on the same machine.

---

### Post by JLeon85 on 2013-03-13
I don't get how this is different than just running the Ubuntu DE. With Unity, you'll have the same windows management as Ubuntu, your taskbar menu will be there and locked in place, etc., so what is there left that's different? 

You can also easily install an icon dock on the left side of the screen in Lubuntu, in fact Cairo Dock even has Unity themes for that. 

On my system, I installed Lubuntu then installed the Ubuntu DE. My loading screen still says Lubuntu even if I set Ubuntu to be default. So it seems to me that would be the exact same thing as running Unity on Lubuntu.

---

### Post by JOHNNYG713 on 2013-03-13
It can be done, (with some work) if you can run compiz, but if you can run compiz, why not just run Ubuntu?, you can still run ubuntu in 2D mode if unable to run unity (compiz), If you want to keep LXDE, add docky, simdock, or cairo dock ect. to simulate unity !

---

### Post by quequotion on 2013-03-13
> **JLeon85 said:**
> I don't get how this is different than just running the Ubuntu DE. With Unity, you'll have the same windows management as Ubuntu, your taskbar menu will be there and locked in place, etc., so what is there left that's different? "Just running the Ubuntu DE" is precisely what JamesTheAwesomeDude wanted advice on doing, so I recommended "apt-get install unity gnome-session" for a minimal installation and to avoid "ubuntu-desktop"--a huge metapackage that installs the entire Ubuntu software suite.

Although Pantheon/Openbox is much better, considering that it's a Lubuntu installation.

---

### Post by JLeon85 on 2013-03-14
> **JamesTheAwesomeDude said:**
>  I've heard that sudo apt-get install ubuntu-desktop will do it, but I don't want to install the full ubuntu desktop. I just want to add Unity to my Lubuntu desktop.

quequotion, I don't want to split hairs here, but he _didn't_ want the full desktop.

---

### Post by quequotion on 2013-03-15
> **JLeon85 said:**
> quequotion, I don't want to split hairs here, but he _didn't_ want the full desktop.
[s]That's what I said, or what I meant to say at least.

Perhaps we have different interpretations of the term "desktop environment"?

When I say *DE* I refer to the *interface components only* (window manager, panels, launchers, desktop, icons, etc), not a *software suite* (file browser, text editor, video player, etc).

More precisely I should say "desktop interface", but I suspect the less familiar term would also be misunderstood.

Unfortunately *DE* seems to be commonly used to mean "desktop interface *with or without* an additional software suite".[/s]

Another possibility is that he wants to run Openbox with the Unity panels, which cannot be done with the Unity compiz plugin.
Now that I read it over again, I suppose that is what he asked, to which I replied:> [Installing only unity and gnome-session] should be much smaller than installing all of ubuntu-desktop, but  the dependency tree is still extensive. As far as I can tell, **there's no  longer any way to run Unity without Compiz**.

Actually, an *approximation* of that interface could be made out of Unity 2D and Openbox.
Unfortunately, Unity 2D is no longer developed, not up to par with Unity's features, and will be deprecated.

---

