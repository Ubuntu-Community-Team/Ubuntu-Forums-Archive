---
title: "problem with graphic dell poweredge R710"
date: 2012-04-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by adiloo on 2012-04-26
i have a probleme with video ..im looking a driver vga for Dell poweredge R710 and how to install it im using ubuntu 11.10 64 bit .....Matrox Graphics, Inc. MGA G200eW WPCM450

thnk you

---

### Post by gordintoronto on 2012-04-26
Run System settings, select Additional Drivers, see if it offers a driver.

What problem are you having with video? It's entirely possible that what you see is what you get. 

Some years ago I used a Matrox video card, but never with Linux.

---

### Post by adiloo on 2012-04-27
> **gordintoronto said:**
> Run System settings, select Additional Drivers, see if it offers a driver.

What problem are you having with video? It's entirely possible that what you see is what you get. 

Some years ago I used a Matrox video card, but never with Linux.
 

the quality of video is low and I try to install the drivers that I have found but its not working .... when I Run System settings, select Additional Drivers  ..it gives me nothing:(

---

### Post by gordintoronto on 2012-04-27
I'm not sure what you mean by, "the quality of video is low." Could you expand on that, please?

As expected, there is no Linux driver for your video card. If you are comfortable changing hardware, you could probably get an Nvidia card on eBay for under $20, which would produce better results. Just make sure it will work with your motherboard. A few years ago I got a card for $10 which was a major improvement.

---

### Post by adiloo on 2012-04-28
> **gordintoronto said:**
> I'm not sure what you mean by, "the quality of video is low." Could you expand on that, please?

As expected, there is no Linux driver for your video card. If you are comfortable changing hardware, you could probably get an Nvidia card on eBay for under $20, which would produce better results. Just make sure it will work with your motherboard. A few years ago I got a card for $10 which was a major improvement.
i mean la resolution is bad when i watch a film or video recording 
thank you for your answer

---

### Post by SeijiSensei on 2012-04-28
An [R710]("http://www.dell.com/us/enterprise/p/poweredge-r710/pd") is a rack-mounted server; it's not intended for things like video.  Most people running rack servers don't even have a monitor connected once the machine is installed.

As adiloo says you could buy an NVIDIA card; it looks from the specs like the R710 has PCIe slots which gives you some options like [these](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100006519%2050001669%2040000048%20600007855&IsNodeId=1&name=PCI%20Express%202.0%20x16).

---

### Post by adiloo on 2012-04-29
> **SeijiSensei said:**
> An [R710]("http://www.dell.com/us/enterprise/p/poweredge-r710/pd") is a rack-mounted server; it's not intended for things like video.  Most people running rack servers don't even have a monitor connected once the machine is installed.

As adiloo says you could buy an NVIDIA card; it looks from the specs like the R710 has PCIe slots which gives you some options like [these](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100006519%2050001669%2040000048%20600007855&IsNodeId=1&name=PCI%20Express%202.0%20x16).

I bought R710 to install a powerful program that requires a high resolution vidéo  why I want the driver for my matrox graphics card

---

### Post by SeijiSensei on 2012-04-29
According to [http://www.matrox.com/graphics/en/support/drivers/latest/](http://www.matrox.com/graphics/en/support/drivers/latest/) the 4.4 driver on the Matrox site is the most recent one for G200 cards; it's from 2006.  Did you try installing that?

---

### Post by adiloo on 2012-04-30
> **SeijiSensei said:**
> According to [http://www.matrox.com/graphics/en/support/drivers/latest/](http://www.matrox.com/graphics/en/support/drivers/latest/) the 4.4 driver on the Matrox site is the most recent one for G200 cards; it's from 2006.  Did you try installing that?
Yes I tried several times but he gives me this errors if you can help me its  very nice of you :)

sh install.sh 
[: 43: x86_64: unexpected operator
install.sh: 57: function: not found
install.sh: 69: function: not found
install.sh: 78: function: not found
install.sh: 95: function: not found

Please enter the full path to your current X11R6 directory: 
Example: /usr/X11R6

-e \E[31mERROR: The X11R6 path could not be found. Please make
-e        sure that an X server is installed.

---

