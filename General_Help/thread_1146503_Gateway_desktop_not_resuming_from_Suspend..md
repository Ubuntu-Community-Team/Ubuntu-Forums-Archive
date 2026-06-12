---
title: "Gateway desktop not resuming from Suspend."
date: 2009-05-02
forum: General Help
---

### Post by nbtrap on 2009-05-02
I'm running 9.04 on a Gateway FX and the machine won't resume from suspend in Ubuntu (but will in Windows). It wouldn't work in 8.10 either, but it DID work in 8.04. When I try to resume, it hangs at a blank screen with a blinking cursor in the top left corner and doesn't move from there. Here is my xorg.conf:

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

I'm using nVidia's 180 drivers, but it still didn't work when I was using the 173. Any ideas?

Also, I'm not very computer savvy. Please be specific.

---

### Post by nbtrap on 2009-05-02
Bump.

---

### Post by nbtrap on 2009-05-03
Bump.

---

### Post by asdel on 2009-05-11
> **nbtrap said:**
> I'm running 9.04 on a Gateway FX and the machine won't resume from suspend in Ubuntu (but will in Windows). It wouldn't work in 8.10 either, but it DID work in 8.04. When I try to resume, it hangs at a blank screen with a blinking cursor in the top left corner and doesn't move from there. Here is my xorg.conf:




I've encountered a similar problem, but with a twist.

I have a Gateway FX. It would suspend properly, but when resuming, it would not turn on the power to the monitor. It would power on and be fully functional, exception no monitor. Completely dark.

See [http://en.opensuse.org/NVidia_Suspend_HOWTO](http://en.opensuse.org/NVidia_Suspend_HOWTO)

---

### Post by asdel on 2009-05-12
> **asdel said:**
> *** EDIT THE NEXT DAY. PLEASE DISREGARD ***



I've encountered a similar problem, but with a twist.

I have a Gateway FX. It would suspend properly, but when resuming, it would not turn on the power to the monitor. It would power on and be fully functional, exception no monitor. Completely dark.

See [http://en.opensuse.org/NVidia_Suspend_HOWTO](http://en.opensuse.org/NVidia_Suspend_HOWTO)



I am sorry to have lead anyone astray. This does work, but it renders the wireless highly unreliable.

I've removed the blacklist line i've added, and my wireless is now working. (But my resume is failing again. :( ).

Sorry once again for leading anyway astray.

---

### Post by asdel on 2009-06-04
> **asdel said:**
> I am sorry to have lead anyone astray. 

Second apology in one post:(. The solution to the suspend problem is to blacklist intel_apg kernel module and use the NVagp module in xorg.conf instead.

I have a gateway fx running ubuntu 9.04 with no problems, although I worked through a few issues. See this thread for details:

[http://ubuntuforums.org/showthread.php?t=1167791](http://ubuntuforums.org/showthread.php?t=1167791)

---

