---
title: "No DVI output"
date: 2009-02-01
forum: General Help
---

### Post by Derspankster on 2009-02-01
For the past couple of releases I cannot use my DVI on my system. It results in a black screen after usplash.  I'm currently running Hardy although I believe this started with Gutsy.  I have tried adding options to my xorg.conf with no success.  I've also scoured these forums and the net for a solution.  Apparently, many others are having this problem but the solutions being offered don't fix my problem.  

I am running the restricted nvidia driver and Compiz. I suspect that the nv driver will work so apparently it's a driver issue. There is no DVI option available to me in nvidia-settings. 

Since I purchased a new monitor recently I thought I'd revisit the issue. Help, anyone?

---

### Post by KuriKai on 2009-02-01
Hey I just dvi working on a new monitor I bought
To get it working 
I had to reconfigure xorg
so backup your xorg first

---

### Post by Derspankster on 2009-02-01
> **KuriKai said:**
> Hey I just dvi working on a new monitor I bought
To get it working 
I had to reconfigure xorg
so backup your xorg first

Thanks. Could you be a little more specific?  Perhaps you could post your xorg.conf?  I've tried a couple of changes to my xorg.conf but they haven't worked.

---

### Post by Derspankster on 2009-02-04
More information. I am able to boot on DVI with the Nvidia driver disabled. I don't get anywhere near the proper screen resolution but at least I know my Nvidia 6600 card actually can output using DVI.  

I booted with the Nvidia driver and after I heard that I was logged in (no output after X started, black screen) I rebooted from a live CD and and browsed to my xorg0.log file written during the previous boot so I could see what happened.   

I see two warnings in my xorg.log file.

(WW) NV(0): Bad V_BIOS checksum
(WW) NV(0): Unable to estimate virtual size

and this error

(EE) AIGLX: Screen 0 is not DRI capable.

It appears to be driver related in the end. I am unsure what the warnings mean but I think the error is telling me that direct rendering cannot be enabled. My card is a Nvidia 6600 and I'm sure that it's capable of DRI.

I run Compiz so I am using glx-new (I enabled it) Not sure where to go with this now. Should I turn AIGLX to off in my xorg.conf?

---

### Post by Derspankster on 2009-02-05
*bump*  Anybody have and ideas?

---

### Post by xidahs on 2009-05-04
I thought it'd be a simple case of just plugging two monitors into my 6600 card and enabling twinview in nvidia-settings and away we go little did I know how many problems I was gonna have with the dvi port of this card. I live in hope that this problem will be fixed assuming by nvidia but until then I have to use the onboard graphics of my motherboard + the vga port of my Geforce 6600 using xinerama which is not perfect and means compiz is out of the window for the time being if and when a fix does become available could someone please post here. I would also be interested if anyone knows of a link to a howto on installing the latest nvidia driver on jaunty as all my attempts have failed and this situation is getting old .

---

