---
title: "Composite extension for Gusty?"
date: 2007-09-30
forum: Desktop Effects &amp; Customization
---

### Post by michael37 on 2007-09-30
Does Gutsy default to```

Section "Extensions"
        Option          "Composite"     "1"
EndSection

```config?

I am getting a rush of long-suffering ATI users who can't get GLX working due to fglrx driver not supporting GLX and Composite at the same time.  Same for Xinerama.

---

### Post by tbroderick on 2007-09-30
I would guess '0'.

---

### Post by michael37 on 2007-10-01
I've heard that Gutsy enables composite Windows manager by default.  I don't really have a computer where I feel like doing a fresh install of Gutsy, so I am asking for public help here.

For Nvidia and Intel video users, composite should be set to yes since it uses AIGLX.

For ATI users who want a decent 3D performance using the restricted driver, this change is a major hassle.

---

### Post by FuturePilot on 2007-10-01
> **tbroderick said:**
> I would guess '0'.

That would turn it off. Basically 1=Enable 0=Disable

---

### Post by tbroderick on 2007-10-01
> **FuturePilot said:**
> That would turn it off. Basically 1=Enable 0=Disable

Yes, but unless something has changed, using '1' broke your system when not using xgl. Composite works fine when listed as '0' in xorg.conf. I'm using xserver-xgl, compiz-fusion, Gutsy, fglrx, '0' and everything works fine for me.

---

### Post by jimminy_kriket on 2007-10-01
I just installed the beta, it comes set to 0. Atleast after installing fglrx from the restricted drivers manager.

---

### Post by joshuachad on 2007-10-01
I use nvidia's glx new driver in the repos and mine is set to 0 also.

---

### Post by jskasia on 2007-10-01
Hello I'm install Gusty_beta, my vga card is ATIXpress 200M

First time install my visual effect is not work but this solution work fine for me
```
$sudo apt-get install xserver-xgl
```

Then reboot.

Now I can enable basic visual effect, but i still can not enable more effect.

Waiting for full release 7.10, coming soon.

---

### Post by michael37 on 2007-10-01
OK thanks for clarifications.  Btw, is 'nv' driver still present is Gutsy?

To avoid further confusion and add clarity:

[LIST]
[*]Nvidia -- use AIGLX,  Xorg and Composite=1.  'nvidia' driver is preferred.  
[*]Intel -- use AIGLX,  Xorg and Composite=1.  'intel' driver is preferred, although 'i810' driver works too.
[*]ATI -- use Xgl, turn AIGLX off, Composite=0, Xgl provides composite functionality.  'fglrx' driver is preferred.
[/LIST]

---

### Post by michael37 on 2007-10-01
> **jskasia said:**
> Hello I'm install Gusty_beta, my vga card is ATIXpress 200M

First time install my visual effect is not work but this solution work fine for me
$sudo apt-get install xserver-xgl

Then reboot.

Now I can enable basic visual effect, but i still can not enable more effect.

Waiting for full release 7.10, coming soon.

Xgl requires extensive configuration per [this FAQ](https://help.ubuntu.com/community/CompositeManager/Xgl).  Simply installing the software is not enough.

---

### Post by progressnerd on 2007-10-02
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/148221](https://bugs.launchpad.net/ubuntu/+bug/148221) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				You can nominate this bug for the Gutsy release.

---

### Post by rofthorax on 2007-10-03
> **jskasia said:**
> Hello I'm install Gusty_beta, my vga card is ATIXpress 200M

First time install my visual effect is not work but this solution work fine for me
```
$sudo apt-get install xserver-xgl
```

Then reboot.

Now I can enable basic visual effect, but i still can not enable more effect.

Waiting for full release 7.10, coming soon.



I have something similar on a Toshiba A135-2276, I tried this, and it didn't work and worse yet it screwed up the graphics, looked like it was running without double-buffering. I deinstalled it, and rebooted, and everything returned to normal. 

I think this is something to save for the final release of Ubuntu..

---

### Post by mrgnash on 2007-10-04
> **michael37 said:**
> Xgl requires extensive configuration per [this FAQ](https://help.ubuntu.com/community/CompositeManager/Xgl).  Simply installing the software is not enough.

With Feisty and all previous releases that was the case. However, activation of XGL in Gutsy is automatic, and in fact, if you make a separate session as per the instructions outlined in that FAQ, the results will be less than favourable.

In any case, compose="1" or "0" using fglrx and xgl produce the same effect for me at this point: a sluggish desktop with weird artifacts and compiz does not work.

---

### Post by michael37 on 2007-10-04
> **mrgnash said:**
> With Feisty and all previous releases that was the case. However, activation of XGL in Gutsy is automatic, and in fact, if you make a separate session as per the instructions outlined in that FAQ, the results will be less than favourable.

Very interesting, thank you for the info.  What method does Gutsy use to auto-configure XGL?  Method B of aforementioned FAQ?

---

### Post by progressnerd on 2007-10-04
> However, activation of XGL in Gutsy is automatic

How was it automatic? I'm using the Gutsy beta and had to install xgl-xserver with apt to get Compiz up and running. Then it was excruciatingly slow until I installed fglrx, and now it's just buggy.

---

### Post by kaka0502 on 2007-10-17
Thanks jkasia. I am using ubuntu gutsy RC and still had the composite exxension problem on my ATI Radeon 200M. Which after installing xorg-xgl worked as a charm.:guitar:

---

### Post by misfitpierce on 2007-10-17
ATI users must use XGL for effects until 8.42 drivers are out this month sometime. :)

---

### Post by michael37 on 2007-10-17
> **misfitpierce said:**
> ATI users must use XGL for effects until 8.42 drivers are out this month sometime. :)

I would trust Xgl over Xorg/AIGLX promised/supposed/future implementation by ATI closed sourced driver.  Novell guys did a great job with Xgl.  

Just updated my guide for Gutsy, ATI, fglrx, Xgl and Compiz [thread=569654]in this thread[/thread]

---

