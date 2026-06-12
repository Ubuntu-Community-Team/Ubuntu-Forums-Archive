---
title: "Is there a driver for WF748-UI gigafast wireless usb driver"
date: 2009-04-30
forum: General Help
---

### Post by Johnny19734 on 2009-04-30
Guys - 

Is there a driver for WF748-UI gigafast wireless USB driver? I have a buddy who just installed 9.04 and he says it doesn&#8217;t recognize the device. Does any one know if UBBY supports these cheapo devices? Does UBBY have a driver or does he have to use NDIS Wrapper?

Here is the link for the windows driver:

[http://www.gigafast.com/products/product_drivers/WF748-UI_drivers.htm](http://www.gigafast.com/products/product_drivers/WF748-UI_drivers.htm)

[IMG]http://www.gigafast.com/images/product_detail/WF748-CUI_medium.jpg[/IMG]

---

### Post by Polygon on 2009-04-30
Hi,

according to this page:

[http://linux-wless.passys.nl/query_hostif.php?hostif=USB](http://linux-wless.passys.nl/query_hostif.php?hostif=USB)

it says that the WF748-CUI  (you forgot the C =P ) is listed as 'green' which means good/very good/perfect support, and it uses the zd1211 driver

if it does not work out of the box in ubuntu, i guess you can compile the drivers from the site

this is the comment that was left in the entry on that website i posted above:

> 
[http://zd1211.ath.cx/](http://zd1211.ath.cx/) ZD1211B; edit Makefile according to the pointers on the site 

good luck =) post back or pm me if you need help

---

### Post by Johnny19734 on 2009-04-30
> **Polygon said:**
> Hi,

according to this page:

[http://linux-wless.passys.nl/query_hostif.php?hostif=USB](http://linux-wless.passys.nl/query_hostif.php?hostif=USB)

it says that the WF748-CUI  (you forgot the C =P ) is listed as 'green' which means good/very good/perfect support, and it uses the zd1211 driver

if it does not work out of the box in ubuntu, i guess you can compile the drivers from the site

this is the comment that was left in the entry on that website i posted above:



good luck =) post back or pm me if you need help

Dude that list is gold, I will try later and let you know. Thanks alot.

---

