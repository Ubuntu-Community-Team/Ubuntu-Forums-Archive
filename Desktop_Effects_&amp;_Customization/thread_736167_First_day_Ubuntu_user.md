---
title: "First day Ubuntu user"
date: 2008-03-26
forum: Desktop Effects &amp; Customization
---

### Post by homerm06 on 2008-03-26
I need to know how to install Beryl to install emerald themes... I don't know how to do that. I'm a complete noob! i can follow instructions just informative ones. If you said you need to open something without saying how to get there I'll be lost.

---

### Post by Sam Lars on 2008-03-26
Well, first of all, are you using the graphic effects already?

---

### Post by Joeb454 on 2008-03-26
Beryl is discontinued now :) Try looking for Compiz-Fusion instead, its installed by default after Ubuntu 7.10 :)

---

### Post by Cerny on 2008-03-26
look under the community documentation for the compiz-fusion install and troubleshooting.

---

### Post by unoodles on 2008-03-26
You dont need beryl. beryl has merged with another project called compiz.
You can enable extra desktop effects by click System->Preferences->Appearences, then click on the visual effects tab.

---

### Post by uthturn on 2008-03-26
also the control panel for compiz is not installed you have to do it yourself just open terminal and type ccsm the terminal will tell you the correct command to enter
you will then see it under system/preferences/advanced desktop effects settings

---

### Post by Takido on 2008-03-26
Im a second day ubuntu user. I just installed compliz by using sudo apt-get install compizconfig-settings-manager

and afterwords i typed ccsm, i changed the settings around a bit. Then i closed and went to the appearence and i went to click on desktop effects {custom} my screen flashed a few times and told me that they could not be enabled. Am i missing somthing? Compliz is the only thing that i've installed in terms of graphics and stuff.

---

### Post by Sephoroth on 2008-03-26
CCSM can also be installed in Add/Remove under the name "Advanced Desktop Effects Manager (CCSM)"

@Takido:  Are you sure your graphics card is compatible (or has decent drivers enabled)?

---

### Post by northern lights on 2008-03-26
In order to customize compiz to your liking you got to have its settings manager installed. From a terminal run ```
sudo apt-get install compizconfig-settings-manager
```

You can open it via the "ccsm" command or navigate to "System>Preferences>Appearance" and under the "Visual Effects" tab you'll now find a "custom" radio button.

To install emerald run```
sudo apt-get install emerald
```

Obviously installations can also be done via Synaptic (Check in "System>Administration").

---

### Post by roccity1 on 2008-03-26
what kind of graphics card do you have?if it's not 3d you will get that.

---

### Post by Takido on 2008-03-26
i have an integrated SiS laptop graphics card. It's a Piece of crap but i can run WoW at 5 FPS lol

---

### Post by northern lights on 2008-03-26
Run ```
lspci | grep VGA
``` to find out your card model.

Paste the output here.

---

### Post by Takido on 2008-03-27
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

Also.. I just bought a SVGA cable.. how do i get it to send from my laptop to my HDTV?

---

### Post by Takido on 2008-03-27
Anyone know?
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

---

### Post by northern lights on 2008-03-28
Can you install the following two packages and report back on progress: xserver-xorg-core and xserver-xorg-core-dbg

```
sudo apt-get install xserver-xorg-core-dbg
sudo apt-get install xserver-xorg-core
```

also, see this [bug report]("https://bugs.launchpad.net/ubuntu/+bug/115609")

---

### Post by homerm06 on 2008-03-31
I'M SUPER SORRY I'M LATE ON THE REPLY!!!!

I didn't know that beryl was discontinued...... how about installing a theme with the "emerald" extension???

Thanks for the help guys, I just uninstalled Ubuntu because of the default theme :( I"m going to dual boot in a few minutes :)

---

### Post by Sam Lars on 2008-03-31
Emerald is great.
```
sudo apt-get install emerald
```
To then use Emerald as your window manager
```
emerald --replace
```
You can manage themes in System > Preferences > Emerald Theme Manager.  Click on Import to add themes, and then you can do a total makeover of them through the Edit Themes tab.

---

### Post by homerm06 on 2008-04-03
> **Sam Lars said:**
> Emerald is great.
```
sudo apt-get install emerald
```
To then use Emerald as your window manager
```
emerald --replace
```
You can manage themes in System > Preferences > Emerald Theme Manager.  Click on Import to add themes, and then you can do a total makeover of them through the Edit Themes tab.

Oy I just got out of work I'll try it and report tomorrow to see if that works ^_^

---

### Post by homerm06 on 2008-04-03
Ok I found Emerald Theme Manager and I found out how to get around it. I just had to reboot to see the new themes ^_^ Thanks everyone for helping me out. I'm beginning to get used to Ubuntu, I gave Vista several chances so I'm going to do the same with Gutsy :)

---

