---
title: "What wifi card to get for Dell desktop? (Inspiron 530N)"
date: 2007-08-13
forum: Dell  Ubuntu Support
---

### Post by chriscorbell on 2007-08-13
I'm planning to order a new Ubuntu-running Dell desktop this week (Inspiron 530N).  I'd like it to have an 802.11g card (internal or USB) for my home wireless network, but this isn't an option for factory configuration.

Can anyone recommend a card with linux drivers - maybe even with support from Dell or the card manufacturer?

Back-story: I called Dell sales support to ask and they were pretty confused - even though it's sitting in my shopping cart the rep couldn't find Inspiron 530N in their product list. When I reiterated that this was the model running Linux, not Windows, there was a long eerie silence and then a quick change of topic.  Their final recommendation was that I go ahead and just buy the desktop - it was claimed that a purchase code would make it much easier for them (sales support!) to track down the model and its supported accessories.

Should I even be doing this?  Is there a better place to get a $400 Ubuntu box where sales support doesn't think you're speaking Klingon?

---

### Post by technikalKP on 2007-08-13
I don't know about specific wifi cards, but you may want to check out wireless bridges - something like:

[http://www.compusa.com/products/product_info.asp?product_code=50556000](http://www.compusa.com/products/product_info.asp?product_code=50556000)

You can also set up some regular wireless routers to act as bridges, too.

With this setup, you connect your PC to the bridge using the internal NIC and a normal ethernet cable, then configure the bridge to connect to your wireless network.  As far as your PC is concerned, it's hardwired to the network so you want have to deal with any driver or configuration issues.  Performance is as good as any other wireless device.

I've used these for quite a while on linux-based Tivo boxes and other PC's at my house and have been pleased.   Not as elegant as an internal wifi card, but it will work.

---

### Post by chriscorbell on 2007-08-13
Thanks, I want to avoid using the NIC card if possible because I want to use it to run a local wired hub with the UBUNTU box as the DHCP server.  (This is a dev box for some webservice apps among other things).

Anyway - I did some more searching and it looks like the Edimax EW-7128G PCI card might be the way to go - uses Ralink chipset and thus appears to have a native Linux driver.

Thanks, & I will post again if I go this route and get it all working.

Chris

---

