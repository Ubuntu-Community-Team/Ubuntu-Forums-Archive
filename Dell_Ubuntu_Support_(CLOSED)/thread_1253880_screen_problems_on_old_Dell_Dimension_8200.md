---
title: "screen problems on old Dell Dimension 8200"
date: 2009-08-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Yveen on 2009-08-30
Hi

I'm newbee and non-english speaker, but here's the clearest explanation I can do:

I installed Ubuntu few days ago on an old Dell Dimension 8200 and thought my graphic card was HS 'cause troubles went quickly.
With a new GeForce FX 5500, installation ran perfectly.
But the days after, my system crashed every 2 start-ups. eg: 1st start-up of the day, freezed black screen after Ubuntu logo, just strange colorized lines & parasites. But when I force the shut-down and re-start immediately, it works fine...

any idea?

---

### Post by RedRat on 2009-08-30
> **Yveen said:**
> Hi

I'm newbee and non-english speaker, but here's the clearest explanation I can do:

I installed Ubuntu few days ago on an old Dell Dimension 8200 and thought my graphic card was HS 'cause troubles went quickly.
With a new GeForce FX 5500, installation ran perfectly.
But the days after, my system crashed every 2 start-ups. eg: 1st start-up of the day, freezed black screen after Ubuntu logo, just strange colorized lines & parasites. But when I force the shut-down and re-start immediately, it works fine...

any idea?

How much RAM memory do you have and how much Video RAM on the FX-5500 (My old one had 128Mb but perhaps the newer ones have 256Mb). I believe the Dell Dimension 8200 came with either 512Mb or 1Gb of memory. it could be lack of RAM memory in the computer.

What version of the nVidia drivers are you using? Do you have the correct nVidia drivers installed.

A bit more information about your system would be helpful to those of us in the Forum.

---

### Post by Yveen on 2009-08-31
768 Mb  (PC800 RDRAM) for my Dell
256 Mb for graphic card.
Is it a problem ?

I didn't installed nVidia propriatary (how can I say that in english?) drivers because I read they were sometimes making problems. I think xserver-xorg-video-nv is the one I installed for the job. Is it an error ?

Thanks for your help...

---

### Post by RedRat on 2009-08-31
> **Yveen said:**
> 768 Mb  (PC800 RDRAM) for my Dell
256 Mb for graphic card.
Is it a problem ?

I didn't installed nVidia propriatary (how can I say that in english?) drivers because I read they were sometimes making problems. I think xserver-xorg-video-nv is the one I installed for the job. Is it an error ?

Thanks for your help...

It may be that your video card might be using some of that RAM, perhaps others here can help with that. But let us say that it takes 256Mb, that leaves you with 512Mb on board which should be enough to run Linux. It has been a long time since I used the linux nv driver, so that could be part of the problem. I think the intent of that driver is to get you started. But if my memory serves me, I think you should be able to get greater than 800x600 resolution, providing that your monitor is correctly identified by Linux. I have not used the native apps to set resolution and monitor for quite some time. Perhaps others may help.

I would suggest that you download and try EnvyNG for installing the appropriate Nvidia driver. You should also then install nvidia-settings. Again when you run either of these programs you must use the sudo command or the changes will not take after you reboot. EnvyNG will give you some options on which driver to install. I am still using one of the "older" drivers from Nvidia and it works fine with my 8600 series card. 

You might want to try the older driver and see if it works well with your machine. If it does everything you want in terms of graphics, keep it. I am not a great believer in upgrading merely for the sake of upgrading. The upgrade must offer some new capability.

I would suggest that you might want to acquire new memory modules, perhaps scale up to 2 Gb since memory is relatively inexpensive.

---

### Post by cos85 on 2009-08-31
Does the OS work even if you can't see it, or is the computer completely crashed?

The display driver may be detecting your monitor incorrectly and trying a refresh rate/resolution combo that is not supported. If you have another monitor, you could try connecting that instead. 

Alternatively, you can try your luck with the *nouveau* driver that's still experimental in jaunty (it's in the repos). The proprietary driver is also always an option. These could do a better job at detecting your monitor.

If nothing works, you'll have to dig into */etc/X11/xorg.conf*. As a start, try running:
*sudo dpkg-reconfigure xserver-xorg*
which could fix it for you. To get a terminal, after booting into the OS press Ctrl+Alt+F1.

---

### Post by Yveen on 2009-09-01
> **cos85 said:**
> Does the OS work even if you can't see it, or is the computer completely crashed?

It seems something is working 'cause I got a mouse arrow moving on my black screen. So I'll try to get a terminal with your Ctrl+Alt+F1 tip.

I'll try the Envy soft too. And thanks both Redrat & cos85 for your advise


Do you think I could get some infos from the "system diary" (I don't know exact english name, it's the last line of my system/administration menu). For the moment it seems written in Arabic for me...

---

### Post by RedRat on 2009-09-02
> **Yveen said:**
> It seems something is working 'cause I got a mouse arrow moving on my black screen. So I'll try to get a terminal with your Ctrl+Alt+F1 tip.

I'll try the Envy soft too. And thanks both Redrat & cos85 for your advise


Do you think I could get some infos from the "system diary" (I don't know exact english name, it's the last line of my system/administration menu). For the moment it seems written in Arabic for me...

Is the mouse cursor you mention in the shape of "X" or is it the expected "arrow"? If it is the "X" then you may have very definitely a mismatch of video driver and you might be "text mode".

---

### Post by Yveen on 2009-09-07
The mouse is arrow shapped.
I tried Al+Impr+K, magic keys as they say in my documentation, and I needed to do it twice. After that, my screen became nice, loggin screen came (usually its automatic) and everything worked fine.

Do you think it could be a motherboard-battery pb, to explain that a restart in the day causes no errors, it's only the 1st start in the morning wich is troublemaking?:confused:

---

### Post by RedRat on 2009-09-07
> **Yveen said:**
> The mouse is arrow shapped.
I tried Al+Impr+K, magic keys as they say in my documentation, and I needed to do it twice. After that, my screen became nice, loggin screen came (usually its automatic) and everything worked fine.

Do you think it could be a motherboard-battery pb, to explain that a restart in the day causes no errors, it's only the 1st start in the morning wich is troublemaking?:confused:
Actually what I should have wrote is it in the shape of a very large "X" or a large arrow. This may indicate that it is in crude vga mode (I believe that would be something like 480x320 or something like that. But if you can log in and it comes up in normal resolution (i.e., what you have set) than you are in graphic mode. 

As to the battery, I had a 8200 where I worked and that was many years ago, maybe 5 or 7 years. I don't know if they are still making them. Yes, your battery could be faulty. This may be difficult to tell because in Linux, if you have a network connection, it goes out and sets your clock during the login process. To see if your battery is losing time, during startup, get into the bios before linux can load. Check the time on the system clock off the bios. If that time is way off, you may be having a weakening battery. Also, if the battery does go, you may lose some of your bios settings. I can't remember how to replace the battery on the 8200, I think it just pops out of holder on the motherboard. Usually that battery is charged during computer operation, so the battery could be up to charge during the day.

---

