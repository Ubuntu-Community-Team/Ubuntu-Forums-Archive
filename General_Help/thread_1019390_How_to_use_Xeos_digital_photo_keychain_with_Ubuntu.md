---
title: "How to use Xeos digital photo keychain with Ubuntu?"
date: 2008-12-23
forum: General Help
---

### Post by stephanecharette on 2008-12-23
I purchased a Xeos digital photo keychain, thinking since it came with a USB cable, it likely will show up as a drive under Ubuntu, and I can copy my images to it.

Unfortunately not.  When I connect the USB cable, the little LCD screen shows "Connecting..." and nothing else.  No drive icon automagically shows up on my desktop.  Doing a search on the Ubuntu forums and Google has yielded nothing.

Hoping someone knows how to get this to work under Ubuntu.

Thanks in advance,

Stéphane Charette

---

### Post by jespdj on 2008-12-23
Is it this one: [Xeos digital photo keychain](http://www.xeos-labs.com/product.php?c=1&p=4)?

That page leads to [the manual](http://www.pocketphotoframe.com/dpk/index.htm), which says:
> Step 3: Turn on your PC [Note: the Digital Photo Keychain is only compatible with Windows 2000/ ME/ XP/ Vista. The Digital Photo Keychain is not compatible with Windows 98, earlier versions of Windows, Linux or Apple (MAC) computers.]
It's not even compatible with a Mac. :(

Why do manufacturers keep on making useless junk that doesn't use a standard interface so that it works with any kind of computer?

---

### Post by stephanecharette on 2008-12-23
> **jespdj said:**
> Is it this one: [Xeos digital photo keychain](http://www.xeos-labs.com/product.php?c=1&p=4)?

Yes, that would be the one.

> **jespdj said:**
> It's not even compatible with a Mac. :(

It apparently comes with MAC and Windows software on the device, not that I can see it.

Some of the screenshots show the software on a MAC.  Note that Xeos seems to buy the chips and resells them as consumer devices.  The manufacturer seems to be "tenx".  When I look at my connected USB devices, I see one called "tenx technology, inc. TMU 3112 USB General Purpose", vendor id 1130, product id 6806.

Following up on their web site, I came across:

[http://www.tenx.com.tw/front/News.aspx?NewsID=16](http://www.tenx.com.tw/front/News.aspx?NewsID=16)
(scroll down on that page to see the MAC software)

Their product page ([http://www.tenx.com.tw/front/product_home.aspx](http://www.tenx.com.tw/front/product_home.aspx)) has a link for "Portable Digital Photo Frame", with lots of technical information, including which pin of which chip is connected to where...but nothing a "desktop user" like myself could ever hope to use.  :(

Stéphane Charette

---

### Post by jespdj on 2008-12-23
The problem is that it does not use a standard protocol over its USB connection, so it doesn't work as a standard mass storage device (like an USB memory key). It uses some proprietary protocol, so that it only works with the software that you get with it.

Those documents from tenx describe exactly what the hardware looks like, but they don't specify the protocol that the device uses to communicate with the computer. The company probably does not publish that information, which makes it very hard, even for an experienced Linux programmer, to write a driver to support this device.

I'm afraid you're out of luck with this photo keychain on Linux...

---

### Post by HansdeGoede on 2011-06-13
> **stephanecharette said:**
> Yes, that would be the one.



It apparently comes with MAC and Windows software on the device, not that I can see it.

Some of the screenshots show the software on a MAC.  Note that Xeos seems to buy the chips and resells them as consumer devices.  The manufacturer seems to be "tenx".  When I look at my connected USB devices, I see one called "tenx technology, inc. TMU 3112 USB General Purpose", vendor id 1130, product id 6806.

Following up on their web site, I came across:

[http://www.tenx.com.tw/front/News.aspx?NewsID=16](http://www.tenx.com.tw/front/News.aspx?NewsID=16)
(scroll down on that page to see the MAC software)

Their product page ([http://www.tenx.com.tw/front/product_home.aspx](http://www.tenx.com.tw/front/product_home.aspx)) has a link for "Portable Digital Photo Frame", with lots of technical information, including which pin of which chip is connected to where...but nothing a "desktop user" like myself could ever hope to use.  :(

Stéphane Charette

Hi,

Do you still have this photo frame? I'm currently working on a libgphoto2 driver for tenx tp6801 based photo frames. I'm developing and testing with this frame:
[http://www.insigniaproducts.com/products/cameras-camcorders-photo-frames/NS-DKEYBK10.html](http://www.insigniaproducts.com/products/cameras-camcorders-photo-frames/NS-DKEYBK10.html)

Chances are good this driver will work for your frame too, so I was wondering if:
1) You still have this frame
2) If you would be willing to test my driver with this frame

Thanks & Regards,

Hans

---

