---
title: "Ubuntu doesn't let me change vissual effects"
date: 2009-04-06
forum: Desktop Environments
---

### Post by ssno117 on 2009-04-06
hello

i am having problems with my ubuntu 8.10 desktop

whenever i try to change the visual effects from none to extra or normal  - - it doesn't let me do it and says unable to change visual effects.

I dont know what graphics card i have ( can u give me the command to find out ?)

i also added compiz config system manager and selected desktop cube and 3d windows feature.

although it doesn't work





PLZ help me

i am a noob at linux so please keep it simple

thanks guys and gals

---

### Post by EXCiD3 on 2009-04-06
Open up Terminal (Applications->Terminal) and run
```
lspci -nn | grep VGA
```

And this will display your video card information. With that in mind we can help you get the proper drivers for it so that you can use desktop effects (hopefully).

---

### Post by linuxuser21 on 2009-04-06
I am running Ubuntu Studio in Virtualbox.  I know my card can handle it and I know it can because it can do it and then some on my host machine.  Is there a way to force it to?

---

### Post by ajmctaggart on 2009-04-07
[http://forums.virtualbox.org/viewtopic.php?t=5533&sid=b8600f35a2ec92df0ac04bddaeec9897]("http://forums.virtualbox.org/viewtopic.php?t=5533&sid=b8600f35a2ec92df0ac04bddaeec9897")

May have your answer...

Up to this point, I thought it was a "no," for 3D in a VM, but it looks like it's possible, but I think it's really gonna burden the system...You would need ridiculous CPU because it can't take advantage of the graphics card your system has directly.  If it did, what would your host system use to show you the guest system? Get it?

Good Luck, but I think if you want it, you're gonna need to take the plunge! :)

---

### Post by Adavur on 2009-04-07
Hi. My problem is a bit like this but more 'unusual' I think.

I have my Ubuntu running at a 4gb USB-stick. First I enabled Extra Effects at a totally new Lenovo (IBM) ThinkPad x61. It worked fine.
Then I plucket the USB into an older IBM ThinkPad R50, which worked fine too.
At last I put it into my stationary computer, a Medion with NVIDIA graphic card. I changed the visual effects to none and came it up with this error message:

[INDENT][I][SIZE="4"]NVIDIA accelerated graphics driver (version 173)
[/SIZE]
3D-accelerated proprietary graphics driver for NVIDIA cards.

This driver is required to fully utilise the 3D potential of NVIDIA graphics cards, as well as provide 2D acceleration of newer cards.

If you wish to enable desktop effects, this driver i required.

If this driver is not enabled you will not be able to enable desktop effects and will not be able to run software that requires 3D acceleration, such as some games.[/I][/INDENT]

I pushed the ENABLE-button, it loaded and at last it said that the "*Desktop effects could not be enabled."*

Then I tried the two ThinkPads again, but THIS TIME THEY DIDN'T WORK!!??
And now Desktop Effects won't work at any computer!?

Then I went into 'Applications -> Add/Remove -> System Tools' and uninstalled the driver 'NVidia binary X.Org driver ('version 173' driver)'
and 'NVIDIA X Server Settings' but it still didn't work.

My thought is that it may have installed the driver half but I find it a bit strange anyway.

Anyone who knows a reason or have the same problem? - Or both? ;-)

/Mathias

---

### Post by Therion on 2009-04-07
To use Compiz (the desktop effects) you need the restricted driver installed for your video card. You were prompted to install them.  Did you reboot after?  
The driver install *requires* a reboot.

> **Adavur said:**
> Then I went into 'Applications -> Add/Remove -> System Tools' and **uninstalled the driver** 'NVidia binary X.Org driver ('version 173' driver)'
and 'NVIDIA X Server Settings' but it still didn't work.
Because you've uninstalled the required driver.

Go to System/Administration/Hardware drivers and see if you can reinstall the proprietary nVidia driver for your computer.  Reboot after it's installed and try to enable the desktop effects again.

---

### Post by Adavur on 2009-04-07
*#Therion ->>*
Yes I did reboot.
But the tricky thing is that I use the same Linux-system at 3 different machines/computers because of my USB stick, and it's only my stationary Medion that have a NVIDIA graphic card, so there shouldn't really be a problem with the ThinkPads. And there wasn't in the beginning but after I installed the driver for the Medion, they don't work either :S
- Therefore I tried to uninstall the NVIDIA-driver ;)

But if anyone know a way I would really like to hear from you.....?

---

### Post by ajmctaggart on 2009-04-07
I am sure there are many ways to get this accomplished Adavur, but you have to remember that two Thinkpads are going to be a lot easier to switch a usb stick between than throwing a desktop into the equation...

Really if you want to use a usb stick between all three of these, options like compiz are going to slow down boots and cause problems w/ updates, etc.  

Not at all trying to dissuade you from trying, but it certainly isn't the norm to get compiz and all the eye-candy goodies going on a usb-stick that will be used on multiple systems...it's usually used for a fast, lean, portable system...

Have you setup your usb-stick to hold onto read/write changes?  Otherwise, every time you boot, it's like using a live-cd, it will go back to the default...

Good Luck!

---

### Post by Adavur on 2009-04-08
Well, thank you for the answers :)

You're right, but I'm new at Ubuntu, so I bought my stick to try it. Soon I will properly get the full installation on my computer.

But thanks anyway. And yes, it is set to save every time I close. Actually it works very good.

---

### Post by Naz_Farooq on 2009-04-08
> **ssno117 said:**
> hello

i am having problems with my ubuntu 8.10 desktop

whenever i try to change the visual effects from none to extra or normal  - - it doesn't let me do it and says unable to change visual effects.

I dont know what graphics card i have ( can u give me the command to find out ?)

i also added compiz config system manager and selected desktop cube and 3d windows feature.

although it doesn't work





PLZ help me

i am a noob at linux so please keep it simple

thanks guys and gals

Go to
System >> Administrator >> Hardware
and activate your Display card hardware which would be not activated. When you activate it, it would install its driver and start working.
Go to background setting and change visual effects from none to extra. It will work hopefully.
I had the same problem before and I did this.

---

