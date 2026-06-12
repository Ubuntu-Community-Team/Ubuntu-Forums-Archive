---
title: "nVidia cards supported?"
date: 2008-01-08
forum: Desktop Effects &amp; Customization
---

### Post by phmcguin on 2008-01-08
I have an nVidia GeForce2 DDR Generic. I've been having huge problems getting desktop effects enabled and have a thread running on this. In this thread [Desktop effects can not be enabled] people have suggested more then once "you're card is not supported". I've also seen this in a number of other posts in this forum.

So I've googled for a list of un/supported cards for Ubuntu Gutsy. But I'm not getting anywhere. Is it actually written anywhere that Ubuntu doesn't support my card?

Thanks,
-a very frustrated new Ubuntu user.:confused:

---

### Post by phmcguin on 2008-01-08
Also, 

Can someone tell me how Compiz and XGl hang together? Are they different packages for the same thing?  Do you need both?

---

### Post by Forlong on 2008-01-08
Who claims GeForce2 is not supported by Ubuntu?
If you have a GeForce2 MX, you can use **nvidia-glx** otherwise **nvidia-glx-legacy** will work.

All you need to do is installing the proper driver via *System &#8594; Administration &#8594; Restricted Drivers Manager*


Xgl is for graphics cards (drivers) that don't support AIGLX (like the proprietary ATI fglrx driver from the Ubuntu repositories).
Nvidia cards do not need it, although I'm not sure Compiz will work with the legacy driver.

---

### Post by phmcguin on 2008-01-08
Thank you very much!!! That's the most exact and trusted answer I've been able to get on this whole confusion!

Greatly appreciated!

PS If you look at some of the "Desktop effects can not be enabled" posts you'll see plenty of posts from others stating 'your nVidia card isn't supported by Ubuntu- you won't be able to run Compiz'

---

### Post by FuturePilot on 2008-01-08
If your Nvidia card has less than 64MB of RAM you won't be able to use Compiz. One reason being the black window bug. Your card should be supported by the nvidia-glx driver. I have a GeForce 2 also and use that driver. However Compiz does not work due to the lack of Video RAM.

---

