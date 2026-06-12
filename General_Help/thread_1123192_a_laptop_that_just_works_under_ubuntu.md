---
title: "a laptop that just works under ubuntu"
date: 2009-04-11
forum: General Help
---

### Post by mr_gourami on 2009-04-11
I have an hp dv6000 and i just left ubuntu for the only reason that for the past 4 days i have been trying to get wireless to work. after 8 tutorials and 4 really pita days i give up. ill come back to ubuntu when it just freakin works. i love ubuntu dont get me wrong and i hate i have to leave it but if the wireless doesnt work... thats just not acceptable

but i am going to need a new computer soon. this is starting to not even turn on when i push the power button. my question is, what laptops models/brands/companies whatever will just work under ubuntu? No hours of configuring to get the simple things like wireless or sound to work?

i really do hate windows, no multi desktops, slower, less options, not as pretty, etc etc but it does just work when i plug it in...

---

### Post by tommcd on 2009-04-11
There are laptops and desktops that come with Ubuntu already installed and configured:
[http://www.system76.com/](http://www.system76.com/)
[http://www.zareason.com/shop/home.php](http://www.zareason.com/shop/home.php)
Then there is Linux Certified:
[http://www.linuxcertified.com/linux_laptops.html](http://www.linuxcertified.com/linux_laptops.html)

---

### Post by spcwingo on 2009-04-12
I just installed Ubuntu in my wife's dv6000 (6707us).  Wireless works after using ndiswraper to install the (windows) driver and using WICD to manage the network connections.

---

### Post by defaultusername on 2009-04-12
mr_gourami,

I recommend IBM/Lenovo's Thinkpad series. IBM/Lenovo products in general have a good reputation among Linux users. I am typing this on a Thinkpad T60 running Ubuntu 9.04. The install took only 15-20 minutes and no additional hardware configuration appeared necessary. I've always been very happy with my Lenovo laptop.

---

### Post by jflaker on 2009-04-12
> **defaultusername said:**
> mr_gourami,

I recommend IBM/Lenovo's Thinkpad series. IBM/Lenovo products in general have a good reputation among Linux users. I am typing this on a Thinkpad T60 running Ubuntu 9.04. The install took only 15-20 minutes and no additional hardware configuration appeared necessary. I've always been very happy with my Lenovo laptop.

I have a Dell Latitude D series system which "Just Works" under 7.10 (with some wrapper help) and 8.10 without any extra energy.

Get a LiveCD and visit a computer store and ask for assistance in testing a few systems (tell them they lost a sale if they will not allow your CD testing)....You should try before you buy, so try a couple of different ones with the LiveCD...if it works with the LiveCD, it will work when installed.

---

### Post by defaultusername on 2009-04-12
> **jflaker said:**
> I have a Dell Latitude D series system which "Just Works" under 7.10 (with some wrapper help) and 8.10 without any extra energy.

Get a LiveCD and visit a computer store and ask for assistance in testing a few systems (tell them they lost a sale if they will not allow your CD testing)....You should try before you buy, so try a couple of different ones with the LiveCD...if it works with the LiveCD, it will work when installed.

When I was in high school, I had a Dell Latitude C840 that played very nicely with Linux. Thanks for mentioning the Dell Latitude series! :-)

---

### Post by mb_webguy on 2009-04-12
The main things to be concerned about with laptops and Linux are the video card and wireless card.  

nVidia video cards tend to work fairly well.  ATI cards generally work, but occasionally only after a minor bit of effort on your part.  The integrated cards can be a bit of a crapshoot, depending on the chipset.

With wireless cards, as long as you stay away from the latest and greatest cards, you should be okay.  Cards with Broadcom chipsets have been a problem in the past, but the new STA driver seems to work with most of the cards that had previously not been supported.  Intel chipsets are generally well-supported, so if it's a choice between Intel and Broadcom, Intel might be the way to go.  But again, it's not a matter of will it / won't it work, but rather if you'll need to use the Windows driver.

---

### Post by hw-tph on 2009-04-12
My HP 6510b, a regular mid range laptop, works 100% straight out of the box. Hardware accelerated graphics, wireless, suspend and hibernate works. I'm very satisfied. Too bad you can't buy it with Ubuntu preinstalled.

Also, don't blame Ubuntu or the Linux community for lack of drivers. Avoid hardware from manufacturers that do not publish documentation since lack of docs means worse support.

---

### Post by NWAdawg on 2009-04-12
8.10 works on my HP zv6000. Once the restricted drivers (bcm43xx) were installed wireless worked.

---

