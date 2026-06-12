---
title: "More Hardware that works &quot;Out of the Box&quot;"
date: 2007-06-05
forum: Dell  Ubuntu Support
---

### Post by HotShotDJ on 2007-06-05
I guess its time I post the good stuff about my Dell E1505 notebook.  I bought it at the end of March -- before the Ubuntu deal was announced.  As soon as it arrived, I wiped out all the partitions that it shipped with (it came with Windows ME II (Vista) installed -- I never even looked at it... first boot up was with a Kubuntu Feisty Beta DVD!).  Pretty much everything worked out of the box -- even the WiFi on my WPA2 network.  Quick install of 915resolution and a reboot, and my Wide Screen was perfect.  Surprisingly, most of the Fn+* keys worked as labeled and all the multimedia buttons worked for system volume and for music playback in Amarok.

Configuring and using my HP Deskjet 950C (local USB printer) and my Brother HL-5170 (network printer) was straight-forward and they both worked perfectly -- not surprising as I had bought them both after first checking for Linux compatibility.  My scanner (Epson Perfection 1650) was detected and worked with absolutely no manual configuration.

Today, my new LG External (USB) Super Multi DVD Rewriter with LightScribe arrived.  Again, everything worked when I plugged it in.  Created a Kubuntu DVD and labeled it as well as a music CD.

Other stuff that "Just Worked"

-- an external USB hard drive (80 Gig)
-- several USB Keychain Drives
-- USB Keyboard
-- USB Logitech TrackBall

I'm still having some trouble with Suspend/Standby -- usually it works as it should, but occasionally, the touchpad and keyboard stop working after restoring from suspend.  The only way to correct is to plug in a USB keyboard and mouse so I can get back to my desktop and restart my computer.  Otherwise, a hard reboot is needed (best to avoid doing THAT!). There was also a tweak [here]("https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/34821/comments/27") that was needed so that I could power down from KDE smoothly.  Also, I cannot get an external monitor to work properly.  I didn't really try very hard, though.  I can wait for the next version of xorg which is rumored will fix that.

---

### Post by jnusa on 2007-06-06
Dell CERC SATA 6 2610SA raid controller works out of the box on Feisty - Just need some management tools for Ubuntu!

---

### Post by magicfab on 2007-06-07
> **HotShotDJ said:**
> Today, my new LG External (USB) Super Multi DVD Rewriter with LightScribe arrived.  Again, everything worked when I plugged it in.  Created a Kubuntu DVD and labeled it as well as a music CD.


You mention of lightscribe got me curious... I found Fiesty packages for [LaCie's 4L software]("http://www.lacie.com/support/drivers/driver.htm?id=10094") (which is non-free BTW):
[http://techystuff.info/?p=29](http://techystuff.info/?p=29)

I'll post that separately in case other Dell users would want to look into it.

Cheers,

---

### Post by fjgaude on 2007-06-07
Thanks for supporting on your free time the Ubuntu-Dell community. Such efforts are self-rewarding. <smile>

frank

---

### Post by taxi16 on 2007-06-10
> **fjgaude said:**
> Thanks for supporting on your free time the Ubuntu-Dell community. Such efforts are self-rewarding. <smile>

frankhi i have been try to get my laptop to worrk on wifi ? it iis a dell inspiron 6000 with built in wifi  can any body help??

---

### Post by HotShotDJ on 2007-06-10
> **magicfab said:**
>  I found Fiesty packages for [LaCie's 4L software]("http://www.lacie.com/support/drivers/driver.htm?id=10094") (which is non-free BTW):
[http://techystuff.info/?p=29](http://techystuff.info/?p=29)I ran into those packages as well, but since I wasn't familiar with the source, I decided to download LaCie's software directly from LaCie and use alien to convert them into debs.  If those debs are safe, then that would be the better option.  (The LaCie software works as advertised!  I use the templates it provides using Gimp, and then print using 4L-gui)

---

