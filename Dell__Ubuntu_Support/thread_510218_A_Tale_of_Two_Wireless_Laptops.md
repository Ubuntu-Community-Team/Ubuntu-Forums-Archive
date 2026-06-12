---
title: "A Tale of Two Wireless Laptops"
date: 2007-07-26
forum: Dell  Ubuntu Support
---

### Post by WrathofthePenguin on 2007-07-26
So I've been working on setting up wireless in the house because of the wife's new Dell 1505N. I have a 700m that I installed Ubuntu on long ago and decided that I'd get it up and running first so that any problems I encountered would be on my laptop instead of hers.

My fun began with getting ndiswrapper working on my 700m. I spent hours trying to get it up and running to no avail. I finally discovered the problem. Me. I was using the wrong driver. Feel free to laugh in replies...

Now that it was up and running, I installed WPA supplicant. After a little playing there I got it to connect to my wireless network successfully. I had no problem whatsoever setting it up to stop asking me for the password for the keyring - life is good.

So now that I've got everything up and running on my laptop, I turn to the new laptop. I turn on the wireless radio and it immediately finds my network. That's a good start. I figure I'll probably have to install WPA Supplicant, but to my surprise, it just pops up a window asking for the PSK for my network. I enter it and it connects flawlessly. It even connects in about a fifth of the time it takes my laptop to connect (sometimes my laptop takes 30 seconds to a minute to connect).

Nice work Dell.

Now if only there was an easier way to use profiles with WPA...

---

### Post by deserthowler on 2007-07-27
HA HA:lolflag:  If this is the laugh-at-me section:

I got a new 1420n.  Had a lot of trouble getting wireless going until I did a further search of the manual and found the on-off toggle switch for wireless.  

Earl

---

### Post by WrathofthePenguin on 2007-07-27
Heh heh - One nice thing about finding out the problem was yourself - nothing's wrong with the equipment!

---

