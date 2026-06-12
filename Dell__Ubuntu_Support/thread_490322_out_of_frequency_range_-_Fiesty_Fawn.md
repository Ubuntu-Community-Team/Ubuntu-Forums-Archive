---
title: "out of frequency range - Fiesty Fawn"
date: 2007-07-02
forum: Dell  Ubuntu Support
---

### Post by kc2keo on 2007-07-02
Trying to setup Ubuntu GNU/Linux 7.04 on my step brothers computer.

Relevant specs:

Dell Dimension 4550, 1.5GB of RAM, AGP 8x Nvidia GeForce 6600GT, about 2ghz Intel P4 processor. He does not have an onboard video card either.

**[SIZE="4"]Here is the issue. Tried to truncate the story to not bore you:[/SIZE]**

When I was attempting to boot the livecd everything worked until I got into the GUI. Then at that point I would get a Out of Frequency Range h:115.4khz v:01.2hz. I considered that maybe his Dell E772c CRT monitor did not support the refresh rate or resolution. So I tried another CRT monitor and a LCD monitor with the same results. Before I booted the system I also tried to change the resolution. Any resolution attempted failed. I could not see a option to change the refresh rate. Only for the resolution. I wanted to see the text output instead of seeing the Ubuntu logo with the load bar so I edited the boot options not boot with "quiet splash". Once the X server started it immediately went out of frequency range.

So... I resorted to downloading the alternate installation livecd from the ubuntu site. I successfully installed the OS via text-based installer. Once I booted into the system I got the same issue.

At this point I decided to research my step-brother's monitor specs. So I got the specs and went to modify his "/etc/X11/xorg.conf" file to add the correct refresh rates and such. After adding the correct values and tried booting same stuff.

I have not tried installing the nvidia driver yet. I also will try using my xorg.conf file and modifying it to suite his system. Took me a few tries to get mine the way I want.

What I suspect is that Ubuntu is not reading only the "/etc/X11/xorg.conf" file but is taking monitor values from another location? Just like it does not need the ~/.xinitrc file to boot the appropriate WM.

I believe I'm on the right track to resolving this issue but am not sure. Thought I'd share it with the Ubuntu community.

---

### Post by sj3fk3 on 2007-07-05
> **kc2keo said:**
> Trying to setup Ubuntu GNU/Linux 7.04 on my step brothers computer.

Relevant specs:

Dell Dimension 4550, 1.5GB of RAM, AGP 8x Nvidia GeForce 6600GT, about 2ghz Intel P4 processor. He does not have an onboard video card either.

At this point I decided to research my step-brother's monitor specs. So I got the specs and went to modify his "/etc/X11/xorg.conf" file to add the correct refresh rates and such. After adding the correct values and tried booting same stuff.


It might help if you post the contents of xorg.conf, most (modern) monitors just need 
Section "Monitor"
    Identifier     "Monitor"
    Option         "DPMS"
EndSection

---

### Post by kc2keo on 2007-07-16
I also went as far as renaming the xorg.conf file to xorg.conf.old. I expected the X server to not boot at all. That was not the case as it gave me the same issue as before.

I forgot the mention that the monitor is a Dell 15" CRT Monitor. I do not have model with me nor do I remember as its not really important.

I also retrieved the monitors specifications and used the vertical and horizontal refresh rates for the xorg.conf file. I successfully configured my monitor that way. I will post the xorg.conf file later on if I get a chance. Hopefully my stepbrother did not rush ahead and try to wipe the OS like he did last time. He is very impatient.

Also used my xorg.conf file. I modified it so it should work with his system. The difference between my system and his is that mine is Ubuntu GNU/Linux 6.10 Edgy Eft and his is Ubuntu 7.04 Feisty Fawn and that his is a Dell Dimension 4550 Desktop Tower.

Other than that I never had such a hard time installing the system let alone use it normally. I had to use the Alternate text-based installer vs the normal installer.



Thanks for helping out,

--kc2keo/George

---

### Post by kc2keo on 2007-07-17
Good news is that I got it up and running.

Here was my approach:

-Boot in recovery mode
-At runlevel 1 I logged into my machine that I have X configured on through SFTP and downloaded my xorg.conf file again
-Looked up the monitor specs again from dells support section->printed->used specs to add them in xorg.conf
-downloaded the NVIDIA drivers from nvidia's homepage.
-upon installing I was prompted to install lib6-dev. When I went to apt-get install it I could not because it wanted the ubuntu install cd for the package. I could not mount the drive so I resorted to using another machine to pull the packages off and getting them to this machine.
-After that I decided to uninstall gdm because I feel much more comfortable if my brother got used to using the CUI.

--kc2keo

---

### Post by gulmer on 2007-07-18
> **kc2keo said:**
> I also went as far as renaming the xorg.conf file to xorg.conf.old. I expected the X server to not boot at all. That was not the case as it gave me the same issue as before.

I forgot the mention that the monitor is a Dell 15" CRT Monitor. I do not have model with me nor do I remember as its not really important.

I also retrieved the monitors specifications and used the vertical and horizontal refresh rates for the xorg.conf file. I successfully configured my monitor that way. I will post the xorg.conf file later on if I get a chance. Hopefully my stepbrother did not rush ahead and try to wipe the OS like he did last time. He is very impatient.

Also used my xorg.conf file. I modified it so it should work with his system. The difference between my system and his is that mine is Ubuntu GNU/Linux 6.10 Edgy Eft and his is Ubuntu 7.04 Feisty Fawn and that his is a Dell Dimension 4550 Desktop Tower.

Other than that I never had such a hard time installing the system let alone use it normally. I had to use the Alternate text-based installer vs the normal installer.



Thanks for helping out,

--kc2keo/George

  I have a Dell Dimension 4550 with a Dell 15" crt monitor and a nvidia video card, gforce 4000. I install Ubuntu 6.06LT last year without any problems, then, last month upgraded to Feisty, no problems with monitor frequency, refresh rate.

---

### Post by Rohen on 2007-08-14
I have the same issue but for me it's at boot time.  

After I get to login I can see everything fine, but while Ubuntu is booting I can't see a single thing.  No idea what to do here any help would be greatly appreciated!

](*,)

---

### Post by kc2keo on 2007-08-14
in your /boot/grub/grub.conf file get rid of splash quiet text. That should allow you to see the text scrolling as you boot instead of the Ubuntu load bar. I prefer the text because I can see where things go wrong easier. Like if one of my filesystems did not mount I can see if it failed and why.

---

### Post by Rohen on 2007-08-14
Ok, sounds interesting.  How do you go about doing that?

Total noob I know :)

---

