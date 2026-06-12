---
title: "New computer for christmas"
date: 2008-12-14
forum: General Help
---

### Post by saxin on 2008-12-14
I want to buy a new PC for christmas. Will be dualbooting WinXP (for gaming) and Ubuntu 8.10. Would like to be able to run Compiz Fusion etc, without problems.  I have been looking around and found this:

[LIST]
[*]Antec Three Hundred (without PSU)
[/LIST]
[LIST]
[*]Asus P5QL-E, P43, Socket-775, DDR2, ATX, GbLAN, ICH10R, PCI-Ex(2.0)x16
[/LIST]
[LIST]
[*]Corsair Powersupply 550W Black, ATX/EPS, 120mm Fan, 4xSATA, SLI, WxHxL
[/LIST]
[LIST]
[*]Intel Core™ 2 Duo E8500 3.16GHz, Socket LGA775, 6MB, 1333Mhz, BOXED w/fan
[/LIST]
[LIST]
[*]Kingston DDR2 HyperX PC8500 4096MB CL7, Kit 2x matched HyperX 2GB DDR2
[/LIST]
[LIST]
[*]Samsung SpinPoint F1 500GB SATA2, 16MB 7200RPM
[/LIST]
[LIST]
[*]XFX GeForce 9800GTX+ 765M 512MB PhysX PCI-Express 2.0, "OC" 2xDVI, HDCP, Graphics Plus, 3D Stereo
[/LIST]

I got a DVDrom, so I don't need that. 

What do you think about the hardware? Anything I should be aware of? Maybe I can get some better hardware? Have I forgotten anything? :)

---

### Post by saxin on 2008-12-15
I hope that some of you can help me :)

---

### Post by djbushido on 2008-12-15
this doesn't look to be a problem, linux runs on practically everything. My only gripe is that you didn't list the system as x86 or x64. Other than that, nothing strikes me as out of the ordinary.

---

### Post by linux_tech on 2008-12-15
In terminal type in-
```
lspci -n
```
then go to
[http://kmuto.jp/debian/hcl/](http://kmuto.jp/debian/hcl/)
and paste results

---

### Post by khelben1979 on 2008-12-15
I can't see any major problems with your new setup, although I would recommend that you get an [anti-static armlink]("http://www.komplett.se/k/ki.asp?sku=303162") before you mount it.

Here's a couple of tips:

Make sure the components are compatible with the motherboard. Some graphics cards and ram memory modules doesn't work with certain types of motherboards.

To be on the safe side, a more powerful PSU at 650W is a better choice, especially if you're going to use it as an heavy gaming computer which probably would involve future upgrades of that machine later on.

Some powerful graphic cards which is released nowadays are very hot and having a couple of 80mm chassi fans are also a good idea to keep the temperature down.

[DriverHeaven]("http://www.driverheaven.net/") is a good place to be if you need more support on this.

---

### Post by saxin on 2008-12-15
> **djbushido said:**
> this doesn't look to be a problem, linux runs on practically everything. My only gripe is that you didn't list the system as x86 or x64. Other than that, nothing strikes me as out of the ordinary.

Ahhh, good good. I guess I will try x64 first. If there is alot of problems with programs, then I go back to x32 :D

> **linux_tech said:**
> In terminal type in-
```
lspci -n
```
then go to
[http://kmuto.jp/debian/hcl/](http://kmuto.jp/debian/hcl/)
and paste results

This is a bit hard, when I don't have bought the PC yet. :)

---

### Post by saxin on 2008-12-15
> I can't see any major problems with your new setup, although I would recommend that you get an [anti-static armlink]("http://www.komplett.se/k/ki.asp?sku=303162") before you mount it.


I got anti-static armlink at work, so that is no problem.

> 
Make sure the components are compatible with the motherboard. Some graphics cards and ram memory modules doesn't work with certain types of motherboards.


OK. As far as I know, the memory is working with this MB. I'm not sure about the graphic card, but I guess it will work? Can anyone confirm this?

> 
Some powerful graphic cards which is released nowadays are very hot and having a couple of 80mm chassi fans are also a good idea to keep the temperature down.


This is what I'm afraid of. I want a nice setup, but I don't want it to be noisy. I forgot to write that down. So if you take this in consideration, is it still a good setup?

---

### Post by 3rdalbum on 2008-12-15
I'd recommend an aftermarket CPU cooler if you can afford it; a good one will help keep the noise down.

The E8500 is pretty popular for overclocking too, so the aftermarket cooler will come in handy there! Just be aware that overclocking will void the warranty of your CPU, motherboard, and possibly your RAM too.

I have two 80cm fans in my computer to keep the temps down in summer (and allow overclocking during the winter), and it's not really too noisy. If you plug the fans into your motherboard rather than just into the PSU, then they will go faster or slower depending on the temperature of your motherboard.

I don't see any reason why the graphics card won't work. This is the first time I've heard about PCIE x16 graphics cards not working with PCIE x16 motherboards.

---

### Post by saxin on 2008-12-15
I was reading a bit more now. And it seems like there is problems with onboard soundchip (Realtek ALC1200). :confused:

---

### Post by BlackS3th on 2008-12-15
Quick replie plz.... Random question ... How do i create a thread ... I would thank youu if yo told me

---

### Post by khelben1979 on 2008-12-15
> **BlackS3th said:**
> Quick replie plz.... Random question ... How do i create a thread ... I would thank youu if yo told me

Just start [from the main page]("http://ubuntuforums.org/index.php") and choose a category, then press the brown button which is located in the upper left corner: New Thread. ):P

---

