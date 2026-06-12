---
title: "Dell Vostro 1500 and Ubuntu 7.10 - No sound and Video on VESA mode ¿?"
date: 2007-10-18
forum: Dell  Ubuntu Support
---

### Post by sh4ka on 2007-10-18
I recently purchased a Dell Vostro 1500.

I installed the new Ubuntu 7.10, and when i boot the system i can see that there is no sound enabled :S and also my video card ( Intel® Integrated Graphics Media Accelerator X3100 ) is in VESA mode... 

Any ideas how can I enable sound in this laptop, and have my graphics working properly with acceleration enabled ?

Thanks!

---

### Post by kamaboko on 2007-10-18
at least you got it installed. my 1400 vostro and gutsy do not like each other.

---

### Post by sh4ka on 2007-10-19
Well..

Sound is fixed :), i just followed this guide: [http://ubuntuforums.org/showpost.php?p=3494809&postcount=10](http://ubuntuforums.org/showpost.php?p=3494809&postcount=10)

Now, anyone know how to setup my video card drivers, because i wanna use all the feature my card have, i dont wanna run all the time in vesa mode.

My card is Intel® Integrated Graphics Media Accelerator X3100

Thanks.

---

### Post by sh4ka on 2007-10-19
Any ideas about the VESA graphics problem?

---

### Post by kamaboko on 2007-10-19
> **sh4ka said:**
> Well..

Sound is fixed :), i just followed this guide: [http://ubuntuforums.org/showpost.php?p=3494809&postcount=10](http://ubuntuforums.org/showpost.php?p=3494809&postcount=10)

Now, anyone know how to setup my video card drivers, because i wanna use all the feature my card have, i dont wanna run all the time in vesa mode.

My card is Intel® Integrated Graphics Media Accelerator X3100

Thanks.

I tried that link for the sound and it failed on the last command
 sudo m-a a-i alsa

did you have this problem?  i'm using a vostro 1400.  i suspect we have the same sound card.

---

### Post by OneTime4YourMind on 2007-10-20
Ok i was able to get the wifi and video drivers to work.

For the wifi i (broadcom bcm43xx):

Downloaded this file: 
*[http://blakecmartin.googlepages.com/bcm43xx-0.3.2-internet.tar.gz](http://blakecmartin.googlepages.com/bcm43xx-0.3.2-internet.tar.gz)
*then in terminal i typed: 
```

sudo aptitude update
(type password)
sudo aptitude upgrade

```
*Then i extracted the tar.gz file, ran "setup.py", and chose the recommended installation (note you MUST be online! Use wired lan or dialup)
-----------------------------------
For video i (nvidia 8400m GS):

*went to: system>administration>synaptic package manager>repositories 

*and enabled all repositories (check everything under 'downloadable from internet', then click close, then click reload)

*then i clicked 'search' and searched for "nvidia"

*finally, from the search results, i installed "nvidia-glx-new" and restarted the computer

video acceleration is **simply beautiful** you gotta try it!
-----------------------------------
For sound i (intel HDA):

*went to: system>administration>synaptic package manager (make sure all repositories are enabled like in the previous step)

*Then i searched "linux-backports-modules"

*and installed it (mark it for installation and click apply)

*finally, i restarted the computer.

Now the sound is completely fixed! Though, audio capture still dont work.

---

### Post by sh4ka on 2007-10-20
> **kamaboko said:**
> I tried that link for the sound and it failed on the last command
 sudo m-a a-i alsa

did you have this problem?  i'm using a vostro 1400.  i suspect we have the same sound card.

Hello,

No, i had no problems at all, but after the process i had to reboot the computer, try rebooting, maybe you have luck in that way.

bye.

---

### Post by fear_nothing on 2007-10-23
Had the same problem. but fixed it... 'twas real easy

ibm x40 laptop
ubuntu 7.10

issue no sound, fix here

[http://www.ubuntux.org/no-sound-on-ubuntu-dapper](http://www.ubuntux.org/no-sound-on-ubuntu-dapper)

---

### Post by JonnyBlazexx on 2007-10-28
> **OneTime4YourMind said:**
> Ok i was able to get the wifi and video drivers to work.

For the wifi i (broadcom bcm43xx):

Downloaded this file: 
*[http://blakecmartin.googlepages.com/bcm43xx-0.3.2-internet.tar.gz](http://blakecmartin.googlepages.com/bcm43xx-0.3.2-internet.tar.gz)
*then in terminal i typed: 
```

sudo aptitude update
(type password)
sudo aptitude upgrade

```
*Then i extracted the tar.gz file, ran "setup.py", and chose the recommended installation (note you MUST be online! Use wired lan or dialup)
-----------------------------------
For video i (nvidia 8400m GS):
[SIZE="5"]*went to: system>administration>synaptic package manager>repositories

*and enabled all repositories (check everything under 'downloadable from internet', then click close, then click reload) [/SIZE]

*then i clicked 'search' and searched for "nvidia"

*finally, from the search results, i installed "nvidia-glx-new" and restarted the computer

video acceleration is **simply beautiful** you gotta try it!
-----------------------------------
For sound i (intel HDA):

*went to: system>administration>synaptic package manager (make sure all repositories are enabled like in the previous step)

*Then i searched "linux-backports-modules"

*and installed it (mark it for installation and click apply)

*finally, i restarted the computer.

Now the sound is completely fixed! Though, audio capture still dont work.

I searched and searched allover the last few days, trying to figure out how to get my network card and video card to work.  Many posts pointed to the restricted drivers section or other workarounds.  My restricted drivers would not work, I could not do any apt-get commands to download the required dependencies.  It just wasn't working!  Then wah-la! I made sure that all the repositories were enabled in synaptic package manager were enabled, and all worked flawlessly!  I really wish that people would stress this more, like OneTime4YourMind did.  Probably save a lot of people a lot of trouble.  As I'm sure I'm not the only one who had this problem arise.  

Thanks! have a great day everyone. :)

---

