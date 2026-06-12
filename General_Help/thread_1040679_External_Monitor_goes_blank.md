---
title: "External Monitor goes blank"
date: 2009-01-15
forum: General Help
---

### Post by Toribor on 2009-01-15
Specs first:
Dell XPS M1210
2.4ghz dual core (32 bit)
2gb RAM
Intel Integrated 945G Graphics Controller
Linux Ubuntu 8.04
(Native Resolution 1280x800)

Monitor:
Dell 1703FP
(Native Resolution 1280x1024)


Essentially I am only experiencing this problem when plugged into an external monitor. (I use my laptop with a monitor, keyboard, mouse, ect. when I'm home) After a while of using my external monitor the screen will suddenly go blank. If I hit Ctrl+Alt+Backspace I can see text on the screen, but once I get back to the logon screen it goes blank again.

If I open up my laptop often times the screen will show up on there, but no form of configuration (Re-enabling the external monitor, disabling my laptop monitor, enabling both, ect) will get the picture to show up on the external monitor. The monitors power LED will flicker green for a moment, as if it were picking up a signal, then immediately go amber and power down. This happens after about 45 minutes of use.

This happens regardless of anything I do or install. I used my computer without installing compiz fusion for a while, thinking to blame it had the same problem, so I installed it anyway.

To me this seems like an issue with my graphics card drivers. (Intel 945GM) That specific graphics card has caused so many problems so far I can't imagine it isn't responsible for this. Again, I don't think it's neccessarily a hardware issue, but I am looking for advice on installing alternate drivers (I'm indifferent to proprietary or open source drivers) or reconfiguring the current setup. I'm open to any and all help though.


---

I've posted on this problem 3 times previously with no results, and then I recently reformatted attempting to fix the problem but nevertheless I am having the same issue. This doesn't seem to be a hardware problem as Windows works flawlessly and more of an issue with the initial settings for ubuntu causing severe hardware failure.

Previous posts, more information and things I have tried can be seen here:

[http://ubuntuforums.org/showthread.php?t=997469](http://ubuntuforums.org/showthread.php?t=997469)

[http://ubuntuforums.org/showthread.php?t=944732](http://ubuntuforums.org/showthread.php?t=944732)

[http://ubuntuforums.org/showthread.php?t=1005262](http://ubuntuforums.org/showthread.php?t=1005262)




Thank you in advance for any help! I really do appreciate the help and support of the community and I try my best to give back to those even less experienced than I. You guys rock! :)

---

### Post by Toribor on 2009-01-20
Bump. Really looking for some advice on this, it's a pretty frustrating problem that is preventing me from using Ubuntu at all when I am hooked up to my external monitor.

---

### Post by Toribor on 2009-01-27
Double bump. Am I posting in the wrong forum? Really looking for some advice here.

---

### Post by Toribor on 2009-02-10
Triple bump, three weeks and no response. I cannot even use Ubuntu with my monitor. Help please, I've spent a lot of time trying to make it easy for others to give me some helpful advice with no headway. Does anyone know of a more appropriate place to ask if there is one?

---

### Post by Toribor on 2009-02-13
Bump #4 can anyone help me? I'm getting tired of reposting this...

---

### Post by densou on 2009-02-14
first, paste here your xorg.conf { /etc/X11/xorg.conf } and /etc/modules

you MUST use the randr utility for set a working dual-head workstation:
[http://www.intellinuxgraphics.org/dualhead.html](http://www.intellinuxgraphics.org/dualhead.html)
[http://www.x.org/wiki/Projects/XRandR](http://www.x.org/wiki/Projects/XRandR)

---

### Post by adam2007 on 2009-03-01
&#1468;no help but at least you're not alone.

same problem xubuntu 8.10 on inspiron e1405

---

### Post by raymr on 2009-05-30
Try adding this line in /etc/X11/xorg.conf:

Section "Monitor"
    Identifier    "Configured Monitor"
    [COLOR=Red]Option "FramebufferCompression" "off"[/COLOR]
EndSection


Works for me.

---

### Post by bacardiandwatermelon on 2009-05-31
What happens if you change the power management settings from 40 minutes to never? Does it stop going to sleep?

---

### Post by mannheim_68161 on 2010-01-15
cannot hook up external monitor (: tv-set), system crashes and strange display-malfunctions appear (both on the integrated laptop-screen as well as on the tv).

system: FujitsuSiemens laptop (AMILO PRO), using intel's 945GM-chip, ubuntu karmic koala 9.10 

can anybody help? or tell me, where to find help?

---

