---
title: "desktop effects compiz can not be enabled"
date: 2009-12-11
forum: Desktop Environments
---

### Post by brettybaby on 2009-12-11
I have ubuntu 9.04

I installed compiz and compizConfig manager

When try to enable desktop effects in the appearance menu; I get a message saying desktop effects could not be enabled.

why?

---

### Post by willro on 2009-12-11
welcome to the club. be prepared for a wait, i've had a thread about this for upwards of 2 weeks now. without any helpful responses.

---

### Post by metalf8801 on 2009-12-11
It could be your graphics card not supporting 3D graphics on Linux 
do you know which graphics card your using? 

take a look at this link 
[https://help.ubuntu.com/9.04/desktop-effects/C/compiz-problems.html](https://help.ubuntu.com/9.04/desktop-effects/C/compiz-problems.html)



I hope this helped 
Dan

---

### Post by brettybaby on 2009-12-11
> **metalf8801 said:**
> It could be your graphics card not supporting 3D graphics on Linux 
do you know which graphics card your using? 

take a look at this link 
[https://help.ubuntu.com/9.04/desktop-effects/C/compiz-problems.html](https://help.ubuntu.com/9.04/desktop-effects/C/compiz-problems.html)



I hope this helped 
Dan


I have already tried to use a different driver with that admin Hardware Driver form

I do not see any dropdown list selection and it just says NO PROPRIETARY DRIVERS ON THIS SYSTEM

I guess Im stuck.  I have a  p4 gigabtye motherboard with onboard 32mb video
8VM533M-RZ motherboard

*8VM533M*-*RZ* is a highly value-oriented P4 platform with good performance and complete **...** core provides class leading 2D,3D *video* quality and performance. [B].
[http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=1766](http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=1766)
[/B]

---

### Post by akashiraffee on 2009-12-11
> **brettybaby said:**
> 
I do not see any dropdown list selection and it just says NO PROPRIETARY DRIVERS ON THIS SYSTEM

I guess Im stuck.  I have a  p4 gigabtye motherboard with onboard 32mb video
8VM533M-RZ motherboard

Well, they are sort of overselling the product by saying that chip (the S3 ProSavage) has 3D acceleration -- actually what they say is "2D/3D" acceleration.  If this means it is a video chip which provides some generic acceleration (which that would include anything, eg, watching a movie could be considered 3D) then that's true, but it is also by definition true of ANY and ALL video chips.  It is like putting a "no cholesterol" label on vegetable oil -- true, but vegetable oil never has cholesterol in it.  So this is some marketing semantics.  They might as well have said "1D/2D/3D/4D" acceleration, since moving images have time as a forth dimension ;)

3D acceleration in a more meaningful sense, with regard to video chipsets, refers to cards than provide acceleration for the DirectX or openGL libraries, which are the libraries used to write what most people would consider legitimate 3D applications.   You do not have to have such a card to run such an application, but then you will not have hardware acceleration.  

**Your S3 does not provide 3D support in this sense.**   Compiz is openGL based, and, unfortunately, *does* require hardware acceleration (which is unusual) because without it, the desktop would be ridiculously slow.  Adding a true 3D card can improve the realtime performance of openGL applications by a factor of 10 (ie, 1000%).  

Compiz needs that in order to be useful, because it runs along with other things.  With a 3D application like a game, you can always try it without a card -- it will just hog 100% of the processor constantly, and probably be very slow.   But running your processor at 100% just for the desktop is obviously pointless.

[http://www.via.com.tw/en/products/chipsets/legacy/kn266/](http://www.via.com.tw/en/products/chipsets/legacy/kn266/)

When you are considering buying a 3D card, make sure the specifications refer to **DirectX** and **openGL** hardware implementation.  That is a major feature, so it will be mentioned.  Notice it is not in the specs for the S3.

The majority of such cards are made by ATI or nvidia, altho there are some others.  For linux, you probably want one of those 2 since they do supply proprietary drivers.

Another thing to watch for I have gotten burned by is that if your board has a **PCIe 1.0** slot, it may not support most actual PCIe video cards, which require a **2.0** slot (altho they *usually *work).  Most mobo's have 1.0 slots still, and in fact do not even say that -- they just say "PCIe slot".    You may have to email the manufacturere to find out!  So make sure you can return the card easily if it does not work well with the mobo.

---

### Post by brettybaby on 2009-12-11
well I have an ATI RADEON 256mb ddr 9600se card here.

I will install that and try again

---

### Post by brettybaby on 2009-12-11
works perfect with the ATI radeon card I have

I wonder if Dual display works good on this card with Ubuntu

Is there a list of commands for COMPIZ; I dont know all the key shortcuts

I enabled cube but the cube only has 2 windows that flip and not a 3d cube?

---

### Post by akashiraffee on 2009-12-11
> **brettybaby said:**
> well I have an ATI RADEON 256mb ddr 9600se card here.

I will install that and try again

That one should work:

[http://ati.amd.com/products/radeon9600/radeon9600pro/specs.html](http://ati.amd.com/products/radeon9600/radeon9600pro/specs.html)

[I]"Supports DirectX® 9.0 and the latest version of OpenGL®"

[/I]Of course, dirextX is only used on MS, but I have never heard of a card that had one without the other.

---

### Post by brettybaby on 2009-12-18
I turned off desktop EXTRA effects and then I tried to enable it again

Now it poped up the error it said last time

Effects can not be loaded

I think it is because my video card driver.

I tried to load the driver in the SYSTEM > Administration > HARDWARE DRIVERS

but it will not allow me to do anything there.

---

