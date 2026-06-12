---
title: "Problems with Acer 23&quot; H233H Monitor"
date: 2009-02-24
forum: General Help
---

### Post by davidss on 2009-02-24
First of all you must know my computer knowledge is absolutely next to zero...I've run into a bit of a problem. I'm using a Dell Pentium 4, 2.80Ghz with 512MB of RAM (quite an oldie i know) running windows with a NVIDIA GeForce FX 5200 video card. I just bought a H233H Acer 23" LCD Monitor and I attempted to install the driver which I was linked to by the ACER install cd. When I did this my computer decided not to work anymore. The driver I had installed was (obviously) too complex for my computer as I could no longer start up in normal mode and got the dreaded blue screen telling me "no.more.irp.stack.locations" and the dumping of physical memory started etc. I decided to boot back in safe mode got rid of the driver acer had told me to install and now everything seems back to normal. My question is; I want to up the resolution of my screen otherwise i wouldn't have bought this one, I'm running a resolution of 1280 x 768 which is far below the monitor's performance of 1920 x 1080. Changing the settings via dsiplay properties doesn't help. Do you think i need a new video card or do you have a suggestion for a driver i should use or a possible other sollution? I would be most thankful for your help!
David

---

### Post by bubbawv on 2009-03-27
I just posted a response to a similar question at this location:

[http://ubuntuforums.org/showthread.php?p=6964583#post6964583]("http://ubuntuforums.org/showthread.php?p=6964583#post6964583")

I also have a GeForce FX5200 card.  I let Ubuntu install the propritary driver then I changes the xorg.config file manually.  My details are on the other post.  Hope this helps.

---

### Post by blackened on 2009-03-27
My favorite reference for things screen resolution is [https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")

I've always found xrandr alot more useful than mucking around in xorg.conf (though sometimes that is necessary).

---

