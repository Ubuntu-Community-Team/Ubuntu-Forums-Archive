---
title: "System broken after 11.04 update"
date: 2011-04-30
forum: Desktop Environments
---

### Post by Gheter on 2011-04-30
Hi all.

I updated my 10.10 to 11.04 about 4 hours back. The first reboot I could login but the files and desktop would keep on flashing on and off. Only the walpaper was constant. I rebooted it again and now it doesn't even reach the login screen. I just get a long line of white. Same thing with recovery mode. I have a quad booted system with ubuntu, puppy linux, windows xp and windows 7. I should be able to edit the ubuntu files through puppy. I would prefer not to forma the system. Any help?

Thanks

---

### Post by Ron Jones on 2011-04-30
> **Gheter said:**
> Hi all.

I updated my 10.10 to 11.04 about 4 hours back. The first reboot I could login but the files and desktop would keep on flashing on and off. Only the walpaper was constant. I rebooted it again and now it doesn't even reach the login screen. I just get a long line of white. Same thing with recovery mode. I have a quad booted system with ubuntu, puppy linux, windows xp and windows 7. I should be able to edit the ubuntu files through puppy. I would prefer not to forma the system. Any help?

Thanks

I experienced something similar during my upgrade. When you started up in recovery mode, did you choose the option that has 'limited video functionality?' (I think it's the 4th or 5th option from the top... in the list of choices).

If you can log in using that option, try going to the "System > Administration > Additional Drivers" utility. Check and see if the system has automatically discovered and downloaded the appropriate proprietary video driver. IF that is the case, you should be able to activate it and reboot.

If there is nothing listed in the Additional Drivers utility, open a terminal window and issue the following command:

```
/usr/lib/nux/unity_support_test -p
```

Within the output should be your video card manufacturer (Usually either NVIDIA or ATI), and the type of card. 

Use this information to find, download and install the proper driver for your card.

It may be as easy as going to "System > Administration > Synaptic Package Manager" and searching for the proper driver.

Then again, it may turn out to be.... a "quest" (in which case you should have some advil handy) ](*,)

---

### Post by Gheter on 2011-05-01
Thanks for the reply but even when I boot into recovery mode all I see is a long line of white. No options, characters or any recognisable language.

If you can tell me how to fix this by editing files through my puppy installation or a live cd please do.

Thanks

---

### Post by Krytarik on 2011-05-01
If you have the proprietary driver of either Nvidia or ATI/AMD installed, removing "/etc/X11/xorg.conf" should be sufficient to get you back to your desktop.

You may then try reinstalling those, installing the "experimental" Nvidia driver if that applies, or stick with the default open source drivers.

Please tell us some details about your video card/chip and the driver you were running if you can't figured it on your own.

Greetings.

---

### Post by Gheter on 2011-05-01
Thanks

I removed the xorg.conf file and now I can use the Ubuntu classic mode. I still cannot use the Ubuntu mode as the screen keeps blinking. My graphics card is an Nvidia 256mb XFX. I was running the Nvidia driver on 10.10. Any help, on making the Ubuntu mode work?

Thanks

Mode here refers to the options on the login screen.

---

### Post by Gheter on 2011-05-01
And this is the output from Ron's suggestion:

raghav@raghav-ubuntu:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce FX 5200/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 173.14.30

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes

---

### Post by Krytarik on 2011-05-01
I checked what driver version is appropriate for your card, through Nvidia's website. It is the 173. Also, the subversion is even more recent than of those driver offered on their website. So, nothing we can do about the proprietary driver, other than somehow downgrade, but I don't recommend that.

But in fact, I wondering why the posted output states the proprietary is running, when you removed the xorg.conf.

We will try now:
- create a fresh xorg.conf: that may land you in the same broken state as before, or doesn't change anything
```
sudo nvidia-xconfig --add-argb-glx-visuals --no-logo --force-generate
```
- replace "nvidia" by "nouveau" in the xorg.conf: that may work better, or worse, but should at least work stable in "Ubuntu Classic (No effects)"

---

### Post by Gheter on 2011-05-01
Thanks.

The system is already stable in Ubuntu Classic and Ubuntu Classic (No effects) modes. I want to run the *Ubuntu *mode. (Italics is how it is written on the system).

Do you think the xorg.conf regeneration would help with that? Because if it only stabilises the Classic modes there would be no need to do thatas they are already stable

Thanks

---

### Post by Krytarik on 2011-05-01
> **Gheter said:**
> 
Do you think the xorg.conf regeneration would help with that? Because if it only stabilises the Classic modes there would be no need to do thatas they are already stable

There is a chance, yeah. Otherwise I wouldn't have suggested that.

---

### Post by Gheter on 2011-05-05
I did the regenerate xorg.conf. Now when I boot into Ubuntu mode a dialogue popups saying that the hardware is insufficient to run unity when the previous test confirmed that it could. Then it automatically redirects to Ubuntu Classic.

Any help?

Thanks

---

### Post by efflux on 2011-05-05
Exactly the same problem here. I have a Quadro FX 3000. Nvidia driver is completely non functioning. Same flashing around of desktop and unity problem. I didn't even know what unity was until now. Never used that before.

Sadly the last two versions of Ubuntu have been backwards steps. I had to move several systems to Debian.

---

### Post by Krytarik on 2011-05-05
You both try the "experimental" driver you find in "Additional Drivers", that is in fact the "nouveau" driver I was referring to earlier. Many users seem to have success with those.

---

### Post by efflux on 2011-05-05
OK. Tried that nouveau driver. It works mostly. At least I'm at the desktop. It just doesn't contain icons that I should see.

Why this Unity desktop? Unity is this fancy desktop, right? I upgraded from 10.10 with no Unity. I do use a Wacom Cintiq but do not want this Unity. I've not got a tablet PC but a Wacom Cintiq.

---

### Post by Krytarik on 2011-05-05
Then just log out and choose "Ubuntu Classic" as the "Session" option at the bottom of the login screen after clicking at your username.

---

### Post by efflux on 2011-05-05
Nouveau driver doesn't work with my Cintiq. Ubuntu 11.04 does not work at all with my Cintiq and it is set up correctly exactly as it was with 10.10. It only works with my standard monitor. I can't use 11.04.

I also can't believe Ubuntu now defaults to the Unity desktop. It is horrible.

---

### Post by efflux on 2011-05-05
Wow! Goodbye Ubuntu. This is the worst release ever.

---

### Post by efflux on 2011-05-05
OK. Got it working in the end so still on Ubuntu here. It's Unity. I have to have the Nvidia drivers working or it's no go with my Cintiq. You have to first set up for classic before even attempting to boot in with Nvidia then get rid of all effects which are another disaster. Then my graphics card and Cintiq work but the Cintiq strips are screwed up and cause a total crash back to login when setting them up with xsetwacom. This has all worked out the box up until now.

---

### Post by akademy on 2011-05-09
I got the same flashing desktop problem after upgrading. The screenlets and desktop icons appear then quickly disappear over and over again, but I can see the background image fine.

I'm also using the nVidia. 

I can get to the login screen no problem, but I don't see any option to select a "Classic Desktop". The login screen looks exactly the same as 10.10 for me.

Any suggestions?

---

