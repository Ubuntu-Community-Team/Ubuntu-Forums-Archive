---
title: "nvidia restricted driver issue and effects"
date: 2008-03-04
forum: Desktop Effects &amp; Customization
---

### Post by ram130 on 2008-03-04
I have nvidia geforce 5200fx and ubuntu installed....i was using ubuntu with a dell which had onboard graphics by INTEL....the effects and everyting was great, especially on the same hardware vista told me couldnt do aero....anyway i put the hard drive into another machince. It booted fine after i did the xconfig ting. But now i dnt have any effects and to use them ubuntu says i need to enable the nvidia restricted driver. So i downloaded the latest driver frm nvida.com and try to enable effects and it said to restart...when i did ubuntu would not start...I had to renable back the other driver through xconfig. i tried multiple time and tried lookin up the problem online to no avail.  Anyone can help me out?:

---

### Post by jeffus_il on 2008-03-04
It it correct to say that the grphics X Server is not starting , but Ubuntu does boot and you have a text console?

---

### Post by ram130 on 2008-03-04
Well no... I see normal ubuntu boot screen then a black screen after that. No login screen or terminal. This happens every time i boot with the nvidia driver enable. To get it bac i hav to boot ubuntu into recovery mode to switch to the other driver.

---

### Post by PmDematagoda on 2008-03-04
Enable the nv or vesa driver and lets recapitulate, how did you install the Nvidia driver?

---

### Post by jeffus_il on 2008-03-04
I think that you may be better off using the driver supplied in the Ubuntu repository.
Install it using```
 sudo aptitude install linux-restricted-modules
```
And tell us what happens.

---

### Post by ram130 on 2008-03-04
> **PmDematagoda said:**
> Enable the nv or vesa driver and lets recapitulate, how did you install the Nvidia driver?

downloaded it first then i installed it via terminal as directed by the read me from nvidia.

---

### Post by ram130 on 2008-03-04
> **jeffus_il said:**
> I think that you may be better off using the driver supplied in the Ubuntu repository.
Install it using```
 sudo aptitude install linux-restricted-modules
```
And tell us what happens.

ok ill try it and post you my results later as im at work

---

### Post by PmDematagoda on 2008-03-04
+1 on jeffus_il's post, downloading the driver directly and installing it needs some fiddling around. Use the repositories, that will simplify matters.

---

### Post by ram130 on 2008-03-04
will enable the effects and accelerations of my card?

---

### Post by PmDematagoda on 2008-03-04
> **ram130 said:**
> will enable the effects and accelerations of my card?
Yes it will.

---

### Post by ram130 on 2008-03-05
what is the latest version? i dnt have internet at home to use the command...

---

### Post by PmDematagoda on 2008-03-06
You can download the latest Nvidia driver for Linux from [here]("http://www.nvidia.com/object/linux_display_ia32_169.12.html").

---

### Post by ram130 on 2008-03-06
i thought u said i need to install the linux-restricted-modules and use dat as the graphics driver, or what?:confused:

---

### Post by jeffus_il on 2008-03-06
Initially that was the plan, the easiest and the safest way to get you working, then you asked for the graphics effects and accelerations i.e. compiz , and I think PmDematagoda then rightly so recommended that you install the latest driver from the manufacturer since the effects need this. Make sure you are stable and running first before you do this. Once the driver is installed you may need to install xserver-xgl, but first get the Nvidia latest driver working as it should.

---

### Post by ram130 on 2008-03-06
> **jeffus_il said:**
> Initially that was the plan, the easiest and the safest way to get you working, then you asked for the graphics effects and accelerations i.e. compiz , and I think PmDematagoda then rightly so recommended that you install the latest driver from the manufacturer since the effects need this. Make sure you are stable and running first before you do this. Once the driver is installed you may need to install xserver-xgl, but first get the Nvidia latest driver working as it should.

well downloaded both...so when i reach home, im gonna install the latest nvidia driver. Then reboot, hopefully it wont freeze again.....

---

