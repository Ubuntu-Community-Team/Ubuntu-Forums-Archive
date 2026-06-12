---
title: "ATI Underscan"
date: 2012-07-12
forum: Desktop Environments
---

### Post by ThePol1 on 2012-07-12
Over the last couple days I have been struggling with underscan on my HTPC (by default a couple inches of my screen would be cut off). Adjusting underscan in the Catalyst Control Center solved the problem, but it wouldn't save changes after a reboot. I've tried multiple solutions (running sudo amdcccle, rebuilding xorg.conf, etc) all of which didn't save after a reboot.

 Here are my specs:
- Motherboard: ASUS AMD Zacate E-350 E35M1-M PRO
- Samsung 46" TV
- HDMI connection from HTPC to TV
- AMD ATI Catalyst 12.6 driver (built via instructions here: [http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers](http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers))

I resolved this with the following command:
sudo aticonfig --set-pcs-val=MCIL,DigitalHDTVDefaultUnderscan,4

Simple. Hopefully this will help someone else in the future. :)

---

### Post by ThePol1 on 2012-08-28
As an update, the above is one way to fix the underscan problem. 

Alternatively, my Samsung TV allows you to change the picture type to "Just Fit" and this resolves the problem. :)

---

