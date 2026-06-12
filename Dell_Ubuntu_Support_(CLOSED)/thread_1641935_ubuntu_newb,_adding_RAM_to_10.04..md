---
title: "ubuntu newb, adding RAM to 10.04."
date: 2010-12-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by reefis on 2010-12-09
i'm pretty dumb about computers. have had this dell dimension 3000, 2.8 ghz, 512 ram for years not realizing adding RAM would make it suck less. so i doubled the ram to 1 gb (cheaped out on adding the system max 2GB). Just started using ubuntu because Windows was so damn slow. Ubuntu ran smooth before, and the change is barely noticable other than compiz working better. I mostly upgraded to get flash video to not be so choppy and it's still very very choppy with the RAM increase, especially fullscreen.  I've noticed the computer never uses more than 300 mb of RAM when pushing the computer to the max. is there something I need to do to get ubuntu to recognize the new RAM. System Monitor tells me have 993.9 Mb of memory.

---

### Post by snowpine on 2010-12-09
Welcome to the forums!

You do not need to do anything to get Ubuntu to recognize your RAM (as you can see from the system monitor saying 993mb). If you never use more than 300mb of RAM, then unfortunately there is no benefit to increasing your RAM from 512mb to 1gb.

You can read more about the system requirements for Adobe Flash here: [http://www.adobe.com/products/flashplayer/systemreqs/](http://www.adobe.com/products/flashplayer/systemreqs/)

Flash performance is a combination of 3 factors: RAM (512mb is the minimum), CPU (2.8ghz should allow you to watch up to 480p video), and graphics card. You do not mention what kind of graphics card you have? If you have integrated graphics, you might get a performance boost from upgrading to a graphics card with 64mb+.

---

### Post by Xial on 2010-12-11
> **reefis said:**
> i'm pretty dumb about computers. have had this dell dimension 3000, 2.8 ghz, 512 ram for years not realizing adding RAM would make it suck less. so i doubled the ram to 1 gb (cheaped out on adding the system max 2GB). Just started using ubuntu because Windows was so damn slow. Ubuntu ran smooth before, and the change is barely noticable other than compiz working better. I mostly upgraded to get flash video to not be so choppy and it's still very very choppy with the RAM increase, especially fullscreen.  I've noticed the computer never uses more than 300 mb of RAM when pushing the computer to the max. is there something I need to do to get ubuntu to recognize the new RAM. System Monitor tells me have 993.9 Mb of memory.

As snowpine mentioned, your RAM is already recognized.

Having supported a few Dimension systems in the past, I too would suggest a video card, since many of them only have the integrated Intel graphics chipset by default. 
The amount of RAM you have showing is consistent with integrated video: That number should've been 1023 or 1024 MB if you had a dedicated card.

The Dimension 3000 machines usually have just a PCI (not PCI-Express -- this becomes important, please make note!) rail for add-in cards. This limits your selection of cards a little, but you should still see a performance increase with a dedicated card handling your graphical needs.

If you made note of my comment earlier, here's where it becomes important:
If you go into a local shop and ask for a video card, you MUST make a point of requesting PCI-and-NOT-PCI-Express to the sales person. I don't want you to go in, and be sold something that won't fit that machine. :)

Here's a selection of video cards on Newegg, in case you decide to purchase online: [PCI Video Cards on Newegg](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709%20600007853&IsNodeId=1&bop=And&Order=PRICE&PageSize=20).
You may have other shopping sources available to you; please feel free to use them as well.

---

