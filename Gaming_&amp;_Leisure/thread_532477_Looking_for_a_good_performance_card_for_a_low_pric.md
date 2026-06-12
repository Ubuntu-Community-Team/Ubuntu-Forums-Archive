---
title: "Looking for a good performance card for a low price"
date: 2007-08-22
forum: Gaming &amp; Leisure
---

### Post by jacob01 on 2007-08-22
any ideas im hoping to be able to spend less than $90 U.S but i wont a card with a high clock speed (450+ preferably 500mhz+) high memory speed (800+) and a pci express.
nvidia

somthing that will be able to play  quake wars thats coming out with playable frames or something to get 50+ in cs source 

any ideas
sorry about this i am not good at making decisions and i want a good card that will perform well and play new games pretty good i have some ideas on page 3 what one will perform the best

looking at this card would it be what im looking performance wise

---

### Post by cogadh on 2007-08-22
I just got a MSI NX7600GS for $80 that fits most of those specs, it was AGP however. I'm sure you could find a PCIx version of that model or better for about the same price. In fact, I just did a quick search and found this:
[http://www.ewiz.com/detail.php?name=MSI-85GT51](http://www.ewiz.com/detail.php?name=MSI-85GT51)

---

### Post by jacob01 on 2007-08-22
hows msi for you, some one told me to stay away from msi. i don"t know why?

---

### Post by cogadh on 2007-08-22
So far it has been great (only had the card for a week now). I had heard the opposite, MSI is very solid, but stay away from EVGA.

---

### Post by blueamcat on 2007-08-23
I found a few great cards if you're still looking.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814122023](http://www.newegg.com/Product/Product.aspx?Item=N82E16814122023)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814127295](http://www.newegg.com/Product/Product.aspx?Item=N82E16814127295)

That website will have one for you. I'm sure of it.

---

### Post by jacob01 on 2007-08-23
blue i was actually looking at the same msi card you pointed out but i was reading the reviews and it said that it didn't perform well but i looked at the specs and it looks good. so i don't know

also has any one else heard any thing about evga or had a good or bad experience?

---

### Post by jacob01 on 2007-08-23
> **cogadh said:**
> So far it has been great (only had the card for a week now). I had heard the opposite, MSI is very solid, but stay away from EVGA.

i have heard that on the evga fans are likely to go after 6 months to a year but thats it

---

### Post by jacob01 on 2007-08-23
if i do get this will it play games that come out a year from now

and if some one can hook me up with an installation guide for the nvidia drivers and recommend what ones to use it wold be great 

thanks in advance

---

### Post by jacob01 on 2007-08-24
bump

---

### Post by jacob01 on 2007-08-24
bump

---

### Post by cogadh on 2007-08-25
I usually use this how-to with the nvidia-glx-new package:
[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html)

---

### Post by Moustacha on 2007-08-25
get the GT version if it's not too much more for you

---

### Post by jacob01 on 2007-08-26
> **Moustacha said:**
> get the GT version if it's not too much more for you

what gt card

and i guess iam going to get the msi card that was recommended earlier

also the link you gave me helps alot but it has a link to a how to, for people with an intel integrated graphic and that doesn't work 

is it a known problem were if you have an intel gma graphics and you install the nvidia card your computer freezes?

---

### Post by cogadh on 2007-08-26
You will need to disable the Intel IGP in your BIOS after you physically install the new card, otherwise it will cause problems.

---

### Post by jacob01 on 2007-08-26
ok so plug the new card into the pcie then plug the monitor into the new card and start up my computer and disable the igp

---

### Post by cogadh on 2007-08-26
Almost forgot, you also have to make sure you set the display driver in your xorg.conf to either the default vesa driver or the basic "nv" driver, otherwise you won't get the GUI when you reboot into Ubuntu.

---

### Post by jacob01 on 2007-08-26
how about would i do that

would i type

sudo gedit /etc/X11/xorg.conf
then go down to display and were it says driver type vesa or nv

---

### Post by cogadh on 2007-08-26
Almost right, you need to go to the "Device" section, not the "Display" section. I recommend using the "nv" driver, it has never failed me in the past.

---

### Post by Moustacha on 2007-08-26
7600GT, it was in reference to on of cogadh's post about getting a 7600GS. According to Tom's hardware guid vga charts, the 7600GT is better than the 8500GT, ~ 82% better...
[http://www23.tomshardware.com/graphics_2007.html?modelx=33&model1=716&model2=856&chart=318](http://www23.tomshardware.com/graphics_2007.html?modelx=33&model1=716&model2=856&chart=318)

---

### Post by blueamcat on 2007-08-27
I've got the EVGA Nvidia 7800 GTX card. Still love it after 16 + months... So it seems to be a good card.

---

### Post by jacob01 on 2007-08-27
> **Moustacha said:**
> 7600GT, it was in reference to on of cogadh's post about getting a 7600GS. According to Tom's hardware guid vga charts, the 7600GT is better than the 8500GT, ~ 82% better...
[http://www23.tomshardware.com/graphics_2007.html?modelx=33&model1=716&model2=856&chart=318](http://www23.tomshardware.com/graphics_2007.html?modelx=33&model1=716&model2=856&chart=318)

im not sure now what would be the best card that will get the best performance

 [http://www.newegg.com/Product/Product.aspx?Item=N82E16814130075](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130075)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814127295](http://www.newegg.com/Product/Product.aspx?Item=N82E16814127295)
 [http://www.newegg.com/Product/Product.aspx?Item=N82E16814130062](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130062)
 [http://www.newegg.com/Product/Product.aspx?Item=N82E16814130017](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130017)
 [http://www.newegg.com/Product/Product.aspx?Item=N82E16814127293](http://www.newegg.com/Product/Product.aspx?Item=N82E16814127293)
out of those what one would perform the best

i think the msi 8600gt oc will be the best out of those

sorry about his i just want to get the best card for the money and that will be able to play new games pretty good

---

### Post by Moustacha on 2007-08-27
8 series cards under linux *currently* don't perform as well as they do under windows, and i believe there's no plans for xvmc on 8 series cards aswell. phoronix has a comparison of the 8 series linux v windows.
8600gt does perform better under windows at least, not so sure about linux because of the driver issues. it is more expensive, and currently only the dx10 stuff is on vista, which dx10 games run like a dog on middle-end hardware, AMD and nvidia.

Go for either 7600GT or 8600GT (which **currently** is a glorified 7600GT)

---

### Post by tracker1 on 2007-08-30
To be honest, I usually have my price point already, and will look at newegg for whatever the best card is that fits my budget, as previously mentioned many 7x00 cards will out-perform the 8x00 counterparts (exception to 8600+ ... GTX > GT > GS  the Gx moniker is usually equivalent to 3-400 in model increases... I find the 7600GT to be a great value, I'm running two of them currently.  Though that's on my windows pc (work/gaming) ... for my linux machines, I've honestly stuck with onboard intel based graphics, simply because they are fairly well supported on install. ...I didn't have any issues with my old desktop with a single 7600GT under Ubuntu 5.06-5.10 (last year)...  I'm partial to XFX, eVGA and ASUS myself as far as mfg's go.  As mentioned eVGA fans on lower end cards tend to break down faster... really wish they'd all switch to ball bearing fans for vidcards.

---

### Post by derekr44 on 2007-08-30
> **tracker1 said:**
> eVGA fans on lower end cards tend to break down faster... really wish they'd all switch to ball bearing fans for vidcards.

I bought [this fan](http://www.newegg.com/Product/Product.aspx?Item=N82E16835118006) right from the get-go for my 7600GT and it's slick. :popcorn:

---

### Post by aaronc222 on 2007-08-30
I'm running a PNY 7600GS.  At the time it was the cheapest 7600 on newegg.  I ran Ubuntu 7.04, XP, and Vista on it with no problems and great frame rates in Nexuiz(90+) and Warsow(90+), other than Vista which would give 40-50 fps.

The only problem I've had is the stock fan.  It was extremely loud.  I replaced it with the [ZeroTherm GX710]("http://www.newegg.com/Product/Product.aspx?Item=N82E16835887007") and all is fine now.

---

### Post by benhagerty on 2007-08-30
I would go with a regular 7900gs. Great card for the price

---

### Post by Tuna-Fish on 2007-08-30
Just one little point for the first post in here: The frequencies alone don't tell jack **** about the card.

If you actually want to buy a good card, you also have to look at the number of shaders and the width of the memory bus.

A card with 800MHz memory and a 128bit bus has just as much memory bandwidth than a card with 256 bit bus and 400MHz memory. Same goes with shaders: more shaders is just as good as having faster shaders.

Thus just looking at the clocks is pretty damned misleading: 7900GS has significantly lower clocks than a 7600GT, but because it has both more shader units and a wider memory bus, it is actually the faster card by a wide margin.

These days, you cannot just look at card stats and say this card is better than that, because it is all so complicated. The only good way really is to go find a benchmark chart, and screw what it says on the box, just look at real benchmark numbers.

tom's hardware's VGA charts are quite good, just remember to look at a benchmark that actually represents your situation, that is look at a same resolution that you will be playing in. For example, I got 1680x1050 monitor, so I look at this page:

[http://www23.tomshardware.com/graphics_2007.html?modelx=33&model1=716&model2=712&chart=288](http://www23.tomshardware.com/graphics_2007.html?modelx=33&model1=716&model2=712&chart=288)

---

### Post by glupee on 2007-08-30
> **Tuna-Fish said:**
> Just one little point for the first post in here: The frequencies alone don't tell jack **** about the card.

If you actually want to buy a good card, you also have to look at the number of shaders and the width of the memory bus.

A card with 800MHz memory and a 128bit bus has just as much memory bandwidth than a card with 256 bit bus and 400MHz memory. Same goes with shaders: more shaders is just as good as having faster shaders.

Thus just looking at the clocks is pretty damned misleading: 7900GS has significantly lower clocks than a 7600GT, but because it has both more shader units and a wider memory bus, it is actually the faster card by a wide margin.

These days, you cannot just look at card stats and say this card is better than that, because it is all so complicated. The only good way really is to go find a benchmark chart, and screw what it says on the box, just look at real benchmark numbers.

tom's hardware's VGA charts are quite good, just remember to look at a benchmark that actually represents your situation, that is look at a same resolution that you will be playing in. For example, I got 1680x1050 monitor, so I look at this page:

[http://www23.tomshardware.com/graphics_2007.html?modelx=33&model1=716&model2=712&chart=288](http://www23.tomshardware.com/graphics_2007.html?modelx=33&model1=716&model2=712&chart=288)
+1
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814133186](http://www.newegg.com/Product/Product.aspx?Item=N82E16814133186)

---

