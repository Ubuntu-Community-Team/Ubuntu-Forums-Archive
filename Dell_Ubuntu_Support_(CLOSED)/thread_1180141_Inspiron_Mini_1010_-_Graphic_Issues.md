---
title: "Inspiron Mini 1010 - Graphic Issues"
date: 2009-06-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by afonja on 2009-06-06
Hello everyone,

On thursday I bought a new Dell Inspiron Mini 10(1010), I've installed Ubuntu Netbook Remix straight away. And it seems that Ubuntu does not have support of Dell's video chipset as my desktop is lagging as a hell... I can surf the web and etc.

Does any1 know how to solve this problem or any ideas?!

Regards

---

### Post by coffeeaddict22 on 2009-06-06
Hi,
Did you use the Dell .iso, or the vanilla UNR .iso?
Can you open a terminal, type in ```
lshw -C display
``` and post back; that will tell us what chipset you're using.

---

### Post by sirebral on 2009-06-07
It is Intel's Chipset.  
> 
Intel Graphics Media Accelerator (GMA) 950

And unfortunately it has been getting lackluster reviews.  I would think the Mini 10 would have a better video card then the Mini 9, but it doesn't.

---

### Post by afonja on 2009-06-07
*-display UNCLAIMED     
       description: VGA compatible controller
       product: System Controller Hub (SCH Poulsbo) Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=0

---

### Post by afonja on 2009-06-07
> **sirebral said:**
> It is Intel's Chipset.  

And unfortunately it has been getting lackluster reviews.  I would think the Mini 10 would have a better video card then the Mini 9, but it doesn't.

Is that mean that I'm unable to use Ubuntu on my dell mini 10?

P.S. Non-dell version of Ubuntu Netbook Remix

---

### Post by sirebral on 2009-06-07
> **afonja said:**
> Is that mean that I'm unable to use Ubuntu on my dell mini 10?

P.S. Non-dell version of Ubuntu Netbook Remix

Not sure if you can or cannot.  If I where you I would take the unit back to tell for a refund.  Get the Latitude 2100 if you can.  It has the same video card as the Mini 9, a touch screen, a rubberized cover, and .. it is 10 inches.

The video card you have is really lackluster and a lot of people have been posting problems with it.  You said you bought it Thursday?  I hope you can return it for an exchange.  

If you can not ... I am not sure how to help you.  It is just a very poor card.

---

### Post by afonja on 2009-06-07
> **sirebral said:**
> Not sure if you can or cannot.  If I where you I would take the unit back to tell for a refund.  Get the Latitude 2100 if you can.  It has the same video card as the Mini 9, a touch screen, a rubberized cover, and .. it is 10 inches.

The video card you have is really lackluster and a lot of people have been posting problems with it.  You said you bought it Thursday?  I hope you can return it for an exchange.  

If you can not ... I am not sure how to help you.  It is just a very poor card.

Just been in the shop, tried to exchange for Samsung N110 - they said that they wouldn't take it back unless I will set-up Windows back on it... haven't got an external CD-rom.... ((((

---

### Post by snowpine on 2009-06-07
Dell sells the Mini 10 with a special "remix" of Ubuntu that has good support for your video card. If you can get ahold of the "Dellbuntu" installer online, that would be the path of least resistance to get Ubuntu running on your Mini 10.

---

### Post by Talon2 on 2009-06-07
See [this]("http://mok0.wordpress.com/2009/05/25/ubuntu-on-the-dell-mini-10-2/").

---

### Post by afonja on 2009-06-07
> **Talon2 said:**
> See [this]("http://mok0.wordpress.com/2009/05/25/ubuntu-on-the-dell-mini-10-2/").
I have tried this - this only makes quality of display better, but doesn't solve lagging problems...

---

### Post by sirebral on 2009-06-07
> **afonja said:**
> Just been in the shop, tried to exchange for Samsung N110 - they said that they wouldn't take it back unless I will set-up Windows back on it... haven't got an external CD-rom.... ((((

You don't want that one either.  It has the same video card.  The 945 GSE.

Well good luck!!  I don't any experience with the video card, but I hope your issue resolves.

---

### Post by boxman108 on 2009-07-10
Does the Netbook Remix work well on the Dell Latitude 2100. I really enjoy 9.04 on my 2100 but what would the benefit be of having the Remix?

---

### Post by mikewhatever on 2009-07-10
> **boxman108 said:**
> Does the Netbook Remix work well on the Dell Latitude 2100. I really enjoy 9.04 on my 2100 but what would the benefit be of having the Remix?

If the Dell Latitude 2100 doesn't have a gma500 adapter, there shouldn't be any problems. From what I saw on the web, it seems to have gma950, which is worth while verifying. The Remix has no benefits other then a modified interface, better suited for small screen machines. I really don't think there is any reason to switch if you are happy with the regular interface.

---

### Post by dudafmendes on 2009-07-12
Hi, 
I installed Xubuntu and cleaned a bit the system. It runs much faster than Ubuntu and it is really easy to setup a really functional and clean interface, but the issue with the GPU remains.

I ended up reinstalling window$ xp. 

For some more information about the problem with the GPU:
[http://www.phoronix.com/scan.php?page=news_item&px=NzAyOQ](http://www.phoronix.com/scan.php?page=news_item&px=NzAyOQ)

D.

---

### Post by mikewhatever on 2009-07-12
The Phoronix article is half a year old. There has been, for some time, a 2d driver for Jaunty in the mobile repository. Installing it fixes the resolution, and the only issue that remains is 3d acceleration. A 3d driver has been uploaded recently and provides very decent multimedia experience, however, it freezes the system after a while, and therefore, is not usable for now.

In short, after installing the 2d driver, Dell mini 10 is a perfectly usable Internet and text editing machine. What's lacking badly is multimedia support.

---

### Post by dudafmendes on 2009-07-13
Hi Mike, 

You are right about the 2d, I did everything a while ago. I'll reinstall with the new drivers and test.

D.

---

