---
title: "Recommended PCI Video Cards (Dimension 3000)"
date: 2007-06-04
forum: Dell  Ubuntu Support
---

### Post by kidwizdumb on 2007-06-04
Hi,

I'm looking for a recommendation in the slim line of available PCI video cards for my Dell Dimension 3000 workstation, and one that will work well with Ubuntu (Feisty Fawn). The IT guy upgraded my computer to a dual monitor set up by installing an ATI RV280 [Radeon 9200 Pro] PCI card. This was satisfactory when I had WinXP installed, but not with linux. The card's 2D speed seems really slow in Ubuntu 7.04 and I don't like that the screen goes blank and refreshes itself periodically (this was an issue in windows too). When I drag windows I'm noticing below average redraw.

The RV280 will not work with the accelerated fglrx driver and I've tried many approaches in terms of configuration, although I could not install directly from the ATI provided packages.

This is a standard PCI slot AFAIK and not the PCI Express type. There is no AGP slot in my system.

Thanks!

-M

---

### Post by angryfirelord on 2007-06-20
I have an X1600 in a laptop and that works fine under Feisty using fglrx. Are you sure you changed your xorg Driver to say "fglrx"?

Anyway, if you still want another card, any nvidia chipset-based card will do. ATI's support for Linux  downright sucks. Here's a list of them: [http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048+1069609642+1305520548&Configurator=&Subcategory=48&description=&Ntk=&srchInDesc=]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048+1069609642+1305520548&Configurator=&Subcategory=48&description=&Ntk=&srchInDesc=")

---

