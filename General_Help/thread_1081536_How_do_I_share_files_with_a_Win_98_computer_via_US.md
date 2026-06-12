---
title: "How do I share files with a Win 98 computer via USB cable?"
date: 2009-02-26
forum: General Help
---

### Post by princerameses on 2009-02-26
Please don't just direct me to another page, I don't understand them. I need step by step instructions. Thanks.

---

### Post by smani on 2009-02-26
I assume what you are trying to do is to create a sort of LAN connection via USB cable. This is not that easy as USB does not natively support the TCP/IP protocol used for networking (while on the other hand firewire does). Essentially from what I know it is not that simple, unless you find drivers for both linux and win98 that emulate network interfaces for the usb connection... A simple LAN cable would be much easier.

---

### Post by princerameses on 2009-02-26
You mean an ethernet cable? The win 98 computer doesn't have ethernet ports.. But it is possible? What about XP and 98. And yes, I am trying to get internet for the older computer.

---

### Post by smani on 2009-02-26
Well, yeah, it is possible, but with quite some work... I have never done anything similar myself, but you can find additional information by googling for tcp/ip over usb, there you will find some step-by-step instructions - sorry, I cannot provide you with a simple way here, you have to do some research on the subject as it is not really something common... (btw winxp - win98 is the same matter)

---

### Post by mb_webguy on 2009-02-26
> **princerameses said:**
> You mean an ethernet cable? The win 98 computer doesn't have ethernet ports.. But it is possible? What about XP and 98. And yes, I am trying to get internet for the older computer.

The Windows machine doesn't have an Ethernet port?

Well, my suggestion would be to buy a network card.  You can get one at [Walmart]("http://www.walmart.com/catalog/product.do?product_id=2067722"), [Amazon]("http://www.amazon.com/s/qid=1235685050/ref=sr_nr_p_n_feature_two_brow_0?ie=UTF8&rs=13983711&bbn=13983711&rnid=486675011&rh=n%3A541966%2Cn%3A172455%2Cn%3A172504%2Cn%3A490499011%2Cn%3A13983711%2Cp_n_feature_two_browse-bin%3A486676011"), or anywhere else electronics are sold for less than $15 (USD).  It would take about 5 minutes to install it (which should be read "plug it in"), and that includes opening up your computer and closing it back up again.

And if you don't have a router (which you can get [for about $40]("http://www.amazon.com/s/qid=1235685600/ref=sr_nr_n_0?ie=UTF8&rs=172504&keywords=router&bbn=300189&rnid=172504&rh=i%3Aaps%2Ck%3Arouter%2Ci%3Aelectronics%2Cn%3A172282%2Cn%3A541966%2Cn%3A172455%2Cn%3A172504%2Cn%3A300189")), you can just get an [Ethernet crossover cable]("http://www.amazon.com/s/ref=nb_ss_e?url=node%3D281407%2C172456%2C172463%2C464398&field-keywords=crossover&x=0&y=0") to connect the two computers.

---

### Post by princerameses on 2009-02-26
I would rather not invest in this old computer if I don't have to.. If Damn small linux would boot, I'd be using that with a wireless adapter. Anyhow, when I got the USB cable (at the dollar store) it said "connects AM - AM This USB Cable connects one computer to another Computer for data and file sharing".

---

### Post by mb_webguy on 2009-02-26
Is it a normal-looking cable, or does it have a lumpish device in the middle?

---

### Post by princerameses on 2009-02-26
Just a normal looking USB cable. 

I'm remembering a few years back my cousin's husband hooked up two computers. And I just check one of the computers that was used, and it doesn't have an ethernet port either. So he must have used USB..

---

### Post by Slim Odds on 2009-02-26
> **princerameses said:**
> I'm remembering a few years back my cousin's husband hooked up two computers. And I just check one of the computers that was used, and it doesn't have an ethernet port either. So he must have used USB..

I wouldn't assume that he used USB. 

I agree with mb_webguy, a cheap network card is the simple fast solution.

---

### Post by mb_webguy on 2009-02-26
What you have is called an A-to-A cable (which is what I figured from your description, but wanted to make sure.  The "M" part just means it has a "Male" connector, as opposed to a "Female" connector.)

A-to-A cables are cheap because they're a bit of a hack.  They're not recommended for networking two computers because they tend to do things like shorting out the USB hub in your computer.  It's a bit like wanting two lights to be on the same circut, and wiring them together while each is plugged into the wall -- you're bound to get sparks.

They do make USB cables for what you're trying to do (like [this one]("http://www.amazon.com/Belkin-Transfer-Cable-Windows-Vista/dp/B000JJPZW0/ref=pd_cp_e_1?pf_rd_p=413863501&pf_rd_s=center-41&pf_rd_t=201&pf_rd_i=B000UTL5DC&pf_rd_m=ATVPDKIKX0DER&pf_rd_r=0WFTMX6B2KV8RT9N4Q6J")), but they have a module in between the connectors that acts as a mini networking device.  When you plug in one of these cables, Linux should automatically detect it as a networking device, and you shouldn't have to do much in terms of special setup.

---

### Post by princerameses on 2009-02-26
*sigh* I have been stressing for days trying to think of ways to connect this computer to the internet. I am too poor to invest in things. =(

Certainly SOMEONE knows how to do this using a USB cord?

---

### Post by mb_webguy on 2009-02-26
I'm afraid you're missing the point.  You *can* connect two computers using a USB cable, but if you try it using the one you bought, you're going to fry your computers, in which case you're going to be down the cost of an entire computer, if not two.  And even trying is going to involve a lot of work and some ugly hacks to your system.

The correct USB cable is going to cost about $20 or more, and will require a minimum of effort to get working.  A networking card, on the other hand, can cost as little as $8.  That's only slightly more than you'd pay for a combo meal at a fast food restaurant, and would mean you would have to do *nothing* to get the computer connected to the network assuming you have a router.

---

### Post by Aearenda on 2009-02-26
How do you value your time, and that of the people trying to advise you here? What you want to do is electrically dangerous for the computers without the right box in the middle, and you could end up destroying both. Take the advice you have been offered - borrow a network card from a friend. Scavenge one from a dead computer left for trash.

---

### Post by princerameses on 2009-02-26
Ok, if I wanted to do the network card suggestion, how would I hook it up?

---

### Post by mb_webguy on 2009-02-26
PCI cards are fairly simple to install.

1) Make sure your computer is off and unplugged.  This is pretty important, unless you actually want to risk getting electrocuted and/or frying your computer.

2) Open up the case.  Usually, especially on older computers, there are a couple of screws on the back, which once removed or loosened allow a side panel to slide off.

3) You'll see some slots on the motherboard the size of the tab on the card you purchased.  On the back panel of the computer, near these slots, there should be some covers or punched-out places.  Remove one of these, so you can access the card from the back of the computer.  Hopefully, your computer case is one that has the easily removable slot covers, because otherwise you'll have to use a screwdriver to pry off one of the punched-out spots.

4) Plug the card into the slot so that the Ethernet port is flush with the back of the computer.  It should fit snugly, but you shouldn't force it in.  It may have a screw or two to secure the card against the back panel of the case.

5) Close the computer back up, plug it back in, and you're good to go.

---

### Post by Aearenda on 2009-02-26
You may need to install the right driver on Windows 98. It's too old to have them all built in.

---

### Post by princerameses on 2009-02-27
I really want to get a linux distro on it.:evil:

It would be so nice if damn small linux would just work...

---

