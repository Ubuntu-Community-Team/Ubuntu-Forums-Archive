---
title: "How Can I Enable Desktop Effects?"
date: 2007-07-23
forum: Desktop Effects &amp; Customization
---

### Post by BETOCORELLA on 2007-07-23
I Clicked On Enable Destop Effects But All I Get Is A White Screen. How Can I Enable Them

---

### Post by mckryptyk on 2007-07-23
Take a look at the stickies at the top of the forum section here:
[http://ubuntuforums.org/forumdisplay.php?f=223](http://ubuntuforums.org/forumdisplay.php?f=223)

Also try to use the forums search before posting someone might have already asked the same question.

Cheers

---

### Post by doomster on 2007-07-23
when Asking such things, it would be better to post a small description of 
your current hardware build , in order to be easier to locate the problem:D

---

### Post by BETOCORELLA on 2007-07-23
Sorry Lol Its A Compaq Presario F558us Amdturion 64, With Nvidia Card

---

### Post by doomster on 2007-07-23
most of nvidia build pc's shouldnt have a problem. 
to begin with make sure you have enabled Restricted drivers support for your nvidia card from system>Administration>restricted drivers Manager.

---

### Post by doomster on 2007-07-23
i would probably get around compiz documentation for starters at 
[Compiz documentation site]("http://compiz.org/Documentation/Documentation")

---

### Post by BETOCORELLA on 2007-07-23
Ok It Says Your Hardware Does Not Need Any Restricted Drivers. What Now

---

### Post by RomeReactor on 2007-07-23
Hi. Do you know what video card is installed in your Compaq? If not, try this from the terminal:
```
sudo lshw -class display
```
and post the output here.

---

### Post by BETOCORELLA on 2007-07-23
Ok Im Using My Phone 2 Put This But It Say Its.......vga Compatible Controller, C51 Pci Express Bridge,  Nvidia Corp, Physical Id Is 5, Bus Info Is Pci@00:05.0, Version Is A2 Size 256mb, With 64 Bitz, Clock Is 66mhz, Capabilities Vga Bus_master Cap_list, Configuration Is Latency=0

---

### Post by RomeReactor on 2007-07-23
Does it say **driver=nvidia**? Do you have direct rendering enabled?
```
glxinfo | grep rendering
```

---

### Post by G_J on 2007-08-05
> **RomeReactor said:**
> Hi. Do you know what video card is installed in your Compaq? If not, try this from the terminal:
```
sudo lshw -class display
```
and post the output here.

i did dat and this is what came up for me


 *-display               
       description: VGA compatible controller
       product: 82810 DC-100 CGC [Chipset Graphics Controller]
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@00:01.0
       version: 02
       size: 64MB
       width: 32 bits
       clock: 66MHz
       capabilities: vga bus_master cap_list
       configuration: driver=i810_smbus latency=0
       resources: iomemory:f8000000-fbffffff iomemory:ffa80000-ffafffff irq:11

its dat good enough to install Beryl or Compiz...i tried da same thing as da thread maker...enable desktop effect and just a white screen came up and went back to my original desktop....

o idk if this makes a diffrents but im running Ubuntu Studio

---

### Post by G_J on 2007-08-05
can some1 help me out on this plz

---

### Post by G_J on 2007-08-05
some1...any1....i put my info up there ^^^^

---

### Post by G_J on 2007-08-05
some1????

info/help plz

---

### Post by RomeReactor on 2007-08-06
Hi. The problem *might* have to do with Ubuntu Studio, due to the low latency kernel it uses, though I can't assure you that. You might want to search the [Desktop Effects & Customization]("http://ubuntuforums.org/forumdisplay.php?f=223") section of these forums and the [Compiz forums]("http://forum.compiz.org/") for an appropriate answer. If no answer comes up, try posting there, and give your thread a name suggestive of your particular problem, like "Enablng Desktop Effects in UbuntuStudio + intel 82810 DC-100 card = white screen" or something along those lines.

---

### Post by Chudilo on 2007-08-06
Get ENVY it'll install everything for you.
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

