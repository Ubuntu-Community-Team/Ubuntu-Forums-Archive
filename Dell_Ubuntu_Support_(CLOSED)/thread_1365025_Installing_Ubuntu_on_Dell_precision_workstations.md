---
title: "Installing Ubuntu on Dell precision workstations"
date: 2009-12-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ecomod on 2009-12-26
hi all!

I would like to buy a Dell precision workstation (most likely one of the M6400 series) and was wondering whether you could tell me if it is possible to install Ubuntu on any of these.
I have found very little information when I made a search on the web. I cannot give any specific details about a particular workstation I am interested in, buying one will depend whether it is possible to install Ubuntu or not ;) I would be very grateful if you could let me know if anyone has been succesfull at installing ubuntu on any of the precition workstations.

many thanks in advance for your help!

cheers

Marco

---

### Post by lukeiamyourfather on 2009-12-26
It should work just fine with a few exceptions. The wireless controller on the advertised models is a "Dell" branded controller which might not have drivers in Linux. Cheers!

EDIT: Looks like there is an option for an Intel wireless controller too. Also you might want to consider one of these in the same price range (ThinkPad W700).

[http://shop.lenovo.com/SEUILibrary/controller/e/web/LenovoPortal/en_US/catalog.workflow:category.details?current-catalog-id=12F0696583E04D86B9B79B0FEC01C087&current-category-id=95F811B4EF37447BAA6A66969FB312CF](http://shop.lenovo.com/SEUILibrary/controller/e/web/LenovoPortal/en_US/catalog.workflow:category.details?current-catalog-id=12F0696583E04D86B9B79B0FEC01C087&current-category-id=95F811B4EF37447BAA6A66969FB312CF)

---

### Post by recluce on 2009-12-27
I cannot speak specifically for that model of Dell, but from my experience with other Dell notebooks:

Many times you have a choice between an Intel Wifi card and a Dell branded one, which usually is a Broadcom card. In my experience, the Intel Wifi causes less trouble than the Broadcom: Intel is supported by Ubuntu out of the box, while Broadcom needs a proprietary driver, which did not always work for me in x64 Ubuntu.

In other words: get the Intel Wifi if you can.

---

