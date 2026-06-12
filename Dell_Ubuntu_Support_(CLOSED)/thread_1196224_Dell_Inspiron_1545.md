---
title: "Dell Inspiron 1545"
date: 2009-06-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by W.Sorting on 2009-06-24
Hi everybody, 

I have a choice between processors and wireless cards on the New Dell Inspiron 1545. 

1. Intel® Celeron® 585 (1MB cache/2.16GHz/667Mhz FSB) (Will this work?  I'm planning on selecting this option).  
2. Intel® Pentium® Dual Core T3400 (2.16GHz/667Mhz FSB/1MB cache) 
3. Intel® Pentium® Dual Core T4200 (2.0GHz/800Mhz FSB/1MB cache) 

1. Dell Wireless 1397 802.11g Half Mini-Card
2. Dell Wireless 1510 802.11 n half mini-card
3. Dell Wireless 1515 802.11 Wireless-N Mini-card 
4. Intel WiFi Link 5100 802.11 Wireless-N Mini Card

Which Card(s)/Processor(s) have the best hardware support in Ubuntu Jaunty?  Preferably will work without configuration, or too much tweaking.  Must work fully after tweaking/config/fixes. 

Thank you.
-W.Sorting

---

### Post by HoTMetaL on 2009-06-24
Why not just get an Inspiron 1545 (15n) with Ubuntu already pre-installed from Dell? Mine just arrived and it is great. Don't pay for a Windows license if you don't need one. This notebook is already certified to run Ubuntu, and is at least $50 less than one with Vista and same specs:

[www.dell.com/ubuntu](www.dell.com/ubuntu)

---

### Post by W.Sorting on 2009-06-25
Thanks for your reply.

Unfortunately I live in Canada and Dell's Inspiron 15n only sells in the USA.  Dell sells no 15 inch ubuntu-driven laptops in Canada.    

Do you think, if I choose the exact same hardware as the 15n but on the Canadian Inspiron 1545, will it serve the same purpose?  

Thank you.  

-W.Sorting

---

### Post by HoTMetaL on 2009-06-25
Almost any combination of hardware on the Canadian 1545 should work well with Ubuntu. I would avoid the ATI graphics option if you don't need higher-end graphics, as Ubuntu works quite well with the default Intel X4500 chipset right out of the box. You should DEFINITELY choose the Intel WiFi Link 5100 wireless option if wireless connectivity is going to be important to you. The default option of Dell's 1397 (which is an inferior Broadcom chip) is supported in Ubuntu but by a separate, downloadable driver. The Intel will work without lifting a finger, and tends to work better with most all Linux distributions (as the Intel driver is built into the Linux kernel).

---

### Post by W.Sorting on 2009-06-25
Awesome, Thanks!

---

### Post by jclifton on 2009-09-08
I just got a 1545 with the 1397 wifi card because it was a cheap option for working from home.  Where can I download the drivers for this card to function in Ubuntu?

---

### Post by Knowle on 2009-09-10
I assume that's the same card in the 15n? It should be labeled as "Dell Wireless 1397 802.11g Half Mini-Card". 

Try going to System > Administration > Hardware Drivers
It was automatically loaded/installed for me and listed as "Broadcom STA wireless card"

---

