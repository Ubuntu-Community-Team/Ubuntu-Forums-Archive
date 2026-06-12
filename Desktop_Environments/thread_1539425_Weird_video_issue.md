---
title: "Weird video issue"
date: 2010-07-26
forum: Desktop Environments
---

### Post by Carlo1973 on 2010-07-26
I have no idea what I did. Either I was drunk without drinking alcohol or was suffering from heat stroke this weekend, but I must have either configured something weird, or I have installed something that my video display doesn't like.

I started up my laptop this morning and noticed at the login screen and on the desktop this weird band.

At the log in screen, the band is there but its sort of overlaying the image that is there. The image is visible behind the band at the bottom, just that specific area that the band is covering is muted a bit.

When I log into the desktop, the whole desktop displays while its loading everything up in the background. However, once it's done loading, the band re-appears. This time it is blacking everything out, except my docky bar shows up fine.

Attached are two screen shots of my desktop showing the black bar/band that is covering things up.

I thought maybe I installed some incompatible ATI drivers and that may have caused the initial issue. I've since un-inistalled everything I thought I have installed this weekend.

The video card on my laptop isn't that fancy. Its an ATI radeon on an old Compaq Presario V2000.

---

### Post by ajgreeny on 2010-07-26
Did you install the new kernel update 2.6.32-24, that came this weekend just gone?  I certainly did as I always do and have a very slightly strange video glitch at login.   I have an old ati 9200SE card which does not display plymouth properly, (the ubuntu logo with five dots beneath on purple background), so I have removed the **plymouth-theme-ubuntu-text** theme and use the straight **plymouth-theme-text** for plymouth.  With kernel 23 this gave a narrow changing colour blue band across the bottom of the screen as the login screen was about to show.  It still does this but with the band now about one third down from the top of the screen.

It's no big deal as it goes straight away when the login screen appears, but I wonder if the two problems are related.  Try the previous kernel from the grub menu, and maybe you will get back your previous screen behaviour.

---

### Post by Carlo1973 on 2010-07-26
Thanks AJGreeny. I'll try that. Ubuntu is the only OS on my system so I don't have a grub bootup menu. I'll have to try to enable it, and give your suggestion a try.


<Edit>

Tried but failed. Still the same issue.

---

### Post by ajgreeny on 2010-07-26
Press shift when you switch on and you should get the menu, I think, even on a ubuntu only machine.

---

### Post by Carlo1973 on 2010-07-26
Strange enough that didn't help. I got the menu, but it appears that the other kernel images got auto-cleaned.

 
Turned out to be Docky itself. On a wim I disabled docky and what do you know I can see my full screen again.

Further investigation showed that compositing has failed.

Not sure what exactly caused it to fail but I'm thinking its from me blindly updating ATI drivers without researching enough prior to installation. I remember trying to see if I could get a certain game to work properly and failed.

I'm currently going through Synaptic Package Manager, attempting to reinstall Compiz components. Hopefully after the reboot it will work.

<edit>

Unfortunatly reinstalling Compiz components failed.

Here is my current screen shot of me trying to load fusion-icon from terminal.

I'd hate to have to blast and reinstall everything in order to get compiz working again. I think this is the entire issue right now that I'm having. Is there a way to force compiz to reconfigure? What about forcing gdm (or X?)to re-identify my graphics card?

Compiz was working prior to me messing things around so I know my gfx card is compatible.

---

### Post by rebootme on 2010-07-30
FWIW - I'm having the same problem with the black band at the bottom of the screen.

---

### Post by rebootme on 2010-07-30
Looks like this thread on launchpad explains it.

[https://answers.launchpad.net/docky/+question/91206](https://answers.launchpad.net/docky/+question/91206)

---

### Post by Carlo1973 on 2010-07-30
> **rebootme said:**
> Looks like this thread on launchpad explains it.

[https://answers.launchpad.net/docky/+question/91206](https://answers.launchpad.net/docky/+question/91206)

I'm just curious as to the cause. I'm not convinced that its the Kernel as I'm using Ubuntu on another system and it has the same kernel version. As for compositing being the problem, I don't that is it either. Sure my compositing got messed up, but that was caused by me trying to find ways to fix the black bar at the bottom to begin with. 

Not sure if this is caused by a chance in Gnome, Kernel, or weird driver issue.

The system that was having the problem is using an ATI radeon mobility chipset (laptop is about 5 or 6 years old). The video driver is part of the kernel. No 3rd party software is required.

My desktop system is using Nvidia as its graphics chipset.  It's an 8600GTS series card, and does have 3rd party drivers. Not from the repositories, but from Nvidia. It too has been having an interesting graphics issue but its different. When I boot up I get an error stating that its running in low graphics mode. I click on restart X and voila it works fine with compositing and everything. No black bars. Nothing.  Not sure what caused that issue either. Just started happening one day. It is not affecting performance or preventing me from doing my work so I'll leave it for now until I have the time to address it. I primarily turn my desktop in my study on in the morning, and remote into it from work through my laptop when I need to do testing from outside the company network. Most of my work is done on my laptop.

Since starting this post, I've reinstalled Ubuntu, well more like I've installed KUBUNTU onto my laptop, thinking it was something I messed up in GNOME when trying to force Gnome to change the login screen or something or when I installed ATI drivers for what I think are newer video cards than what I have on my system. So far after all updates I'm not getting any issues that I can see. I know this doesn't tell me anything in the way as to what the cause is, but I was getting pissy at the direction Gnome was heading. I was even thinking of possibly installing E17.

---

### Post by linux18 on 2010-07-30
grab xcompmgr and type " xcompmgr -n " if it goes away then its a transparency issue and this workaround fixed it.

---

### Post by rebootme on 2010-07-30
I fixed it!

I had to use the nvidia settings to:

1 - Turn off xinerama
2 - Enable TwinView
3 - Turn on visual effects

---

### Post by Carlo1973 on 2010-07-30
I guess this issue is tentatively fixed! LOL

I'll just mark this threat as solved. Not sure what more can be done with it. I'll switch back to Gnome after Gnome 3 is released probably. I just hope that they re-do their theme engine.

Carlo

---

