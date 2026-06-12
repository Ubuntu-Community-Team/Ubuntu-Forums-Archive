---
title: "Nvidia in breezy"
date: 2006-01-12
forum: General Help
---

### Post by yib on 2006-01-12
Hi everyone,

I recently got rid of ubuntu 5.04 and installed breezy; now I can't get nvidia going.

My hardware:
 P3 800
 riva tnt2 video card

I've installed nvidia-glx from the repository, and enabled with nvidia-glx-config enable. Whenever I start the xserver I get an error. 

Strangely this worked fine under 5.04. 

Thanks for any help.

yib

---

### Post by Sepht on 2006-01-12
nvidia actually forked their own drivers, older cards need to install nvidia-glx-legacy

---

### Post by johna11en on 2006-01-12
Just use automatix. 


[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

---

### Post by Sepht on 2006-01-12
[QUOTE=johna11en]Just use automatix. 


[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)[/QUOTE]
don't bother, it'll do nothing but clutter your system.
apt-get install nvidia-glx-legacy
is all you need to do to install working nvidia drivers

---

### Post by sabredog on 2006-01-12
You can install Automatix and select only the Nvidia Drivers for installation.

Worked perfectly with my older Nividia Gforce2 Mx220 32mb card.

---

### Post by yib on 2006-01-12
Hi,

Thanks for the quick replies. 

I have tried both nvidia-glx and nvidia-glx-legacy. Both returned screen not found. I have also tried automatix, again same error. In fact, under 5.04 I used nvidia-glx and it worked find the first time. I don't really understand why it won't work under 5.10.

Any other ideas will be more than welcome.

Thanks again.

yib

---

### Post by trigg on 2006-01-12
Could you post your Xorg.0.log?  That might help diagnose the problem.

---

### Post by yib on 2006-01-13
From Xorg.0.log:

(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.

This is from using nvidia-glx-legacy. 
nvidia tnt2 not supported by default in the 2.6.12 kernel?

yib

---

### Post by phidippus on 2006-01-13
If the screen looks fine, does that mean Ndivia is working fine?

---

### Post by trigg on 2006-01-13
[QUOTE=yib]From Xorg.0.log:

(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.

This is from using nvidia-glx-legacy. 
nvidia tnt2 not supported by default in the 2.6.12 kernel?

yib[/QUOTE]

nvidia should be supported as long as you have 
linux-restricted-modules-2.6.12-10-i386 (or i686 or k7 depending on your kernel)

I think it installs the i386 variant by default, so if you have and use one of the other kernels you might have to install it manually, for example, if you are using the k7 kernel do this:

```

sudo apt-get install linux-restricted-modules-2.6.12-10-k7

```

---

### Post by yib on 2006-01-14
Yup, I tried that too before I posted, same result. 

I guess last resort could always just be going back to 5.04 since that worked, but I would like to try to get this fixed, since I see no reason why nvidia shouldn't work in breezy.

yib

---

### Post by cjazz on 2006-01-14
Yib, what kernel are you using. I apologize if you've already explored this, but I wonder if this thread might help: [http://www.ubuntuforums.org/showthread.php?t=79224](http://www.ubuntuforums.org/showthread.php?t=79224)

---

### Post by trigg on 2006-01-15
[QUOTE=yib]Yup, I tried that too before I posted, same result. 

I guess last resort could always just be going back to 5.04 since that worked, but I would like to try to get this fixed, since I see no reason why nvidia shouldn't work in breezy.

yib[/QUOTE]

I think I gave you bum advice -  it should be the nvidia-legacy package of restricted modules - not the regular restricted modules:

```

sudo apt-get remove --purge linux-restricted-modules-2.6.12-10-386 \
&& sudo apt-get install linux-restricted-modules-2.6.12-10-386-nvidia-legacy

```

---

