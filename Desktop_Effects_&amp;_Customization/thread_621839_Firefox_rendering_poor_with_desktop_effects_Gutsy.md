---
title: "Firefox rendering poor with desktop effects Gutsy"
date: 2007-11-24
forum: Desktop Effects &amp; Customization
---

### Post by satbunny on 2007-11-24
Ok, 7.10, with Nvidia 8300GS on a Dell 530n and the restricted proprietary driver.

I switch "Normal" desktop effects and Firefox (and Smartweasel) start to have rendering problems when you scroll a page. It looks like the page has been roughly fed through a fax machine and folded over onto itself in a corrugating pattern.

Turn off all desktop effects and the problem goes away, so I guess it is a problem between Firefox/gecko and compiz.

If I take a screenshot the screen redraws itself, so I can't evidence it.

It may be this bug, but maybe not:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/110384](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/110384)

---

### Post by irisevelyn on 2008-01-17
Do you always have this problem?
I have it  too, but I found out recently that it is not always there. I was running CompizFusion for about two weeks without the problem and then it appeared again. I also sometimes get rendering problems with other programs, even the file browser, but firefox usually starts first. 
I suspect that another program somehow causes Compiz to have problems. 
It usually appears after a while when I have several programs running. (It is not the temperature, I checked) 
Do you run Mathematica by any chance? It seemed to appear when I had it running, but I'm not sure about that yet, I'll do some tests when I have the time.

I just wanted to find some more information before filing a bug report.

I have a nvidia 8400 on a HP Pavilion, 2500, with the proprietary drivers.

---

### Post by chewylove on 2008-01-29
I have the same notebook.  I realized firefox does this when I have a wine application open.
Hope that helps.

---

### Post by BuntuFreak on 2008-01-29
I second that. I'm a recent convert to Ubuntu. I couldn't let go of Internet Explorer. So installed it and run it using Wine, of course. My computer has just 512MB RAM. I think that might be the problem. Slows down the box once you run wine.

Best.

---

### Post by tgrimley on 2008-06-02
Is there a solution for this?

---

### Post by satbunny on 2008-06-03
Oddly it comes and goes. I had to do a full reinstall a few weeks back and it started again. I shall now reinstall the latest NVIDIA drivers with ENVY and test it.

I am still on Gutsy BTW.

---

