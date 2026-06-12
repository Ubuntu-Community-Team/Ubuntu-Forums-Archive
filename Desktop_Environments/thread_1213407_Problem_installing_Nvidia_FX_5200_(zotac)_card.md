---
title: "Problem installing Nvidia FX 5200 (zotac) card"
date: 2009-07-14
forum: Desktop Environments
---

### Post by terry@softreq.com on 2009-07-14
Hello! 

I took out an ATI card and installed a Zotac Nvidia 5200 FX card.

I restarted the computer, got past the login screen and met the "white screen" that people talk about.

This is probably a driver problem, but I'm unsure how to resolve it. 

I went to the Zotac site that directed me to the NVIDIA site, but little help for Unbuntu users. 

I'm using release 9.04 (Jaunty) 

Any help appreciated - Thanks, Terry

---

### Post by Mia1990 on 2009-07-15
if your driver is installed you should be able to see it in hardware drivers look there then in synaptic if you have the 5200 card then driver 173 should work.you can install [envNG]("http://albertomilone.com/nvidia_scripts1.html") to install the right driver for your card it should be in synaptic if your running 9.02 i here it works good.I have never had to use it myself.

---

### Post by terry@softreq.com on 2009-07-15
Thanks for your help Mia.

I looked under "hardware drivers" and there were no special drivers listed. 

Do I need to go out to the site and download the driver first, then install using Synaptic?  I looked under Synaptic and didn't find "envng".

I noticed when I go out to "add/remove applications", under "System Tools" it lists the "Nvidia binary x.org driver (version 177 driver".  Can I use this method to add the driver?

---

### Post by terry@softreq.com on 2009-07-24
IT WORKED!

First I installed the NVIDIA 173 drivers using Synaptic, but I found I could only use the video 
card in the lowest appearance setting.

Then I installed envNG and ran that, and it seemed to do a better job of installing drivers.  After running envNG, I was able to run the card at the highest appearance setting :)

---

