---
title: "Dell Vostro A90, Ubuntu Jaunty - Cannot Enable Visual Effects"
date: 2009-06-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jonkoay on 2009-06-05
Lately, I've received my Vostro A90. Got a new 64GB SSD and decided to install Jaunty into the machine.

But I'm not sure what went wrong. I cannot enable desktop visual effects. Now it's stuck in "None". The moment I select "Normal", I 'll get "Desktop Effects cannot be enabled". 

I also noticed that HD videos are slightly slower compared to Dell's default Ubuntu (8.04?).

I greatly appreciate any help.

---

### Post by Vaun on 2009-06-05
Are you running UNR (Ubuntu Netbook Remix)?  The two do not play well together at all.  You'll need to select either one or the other.

I have the same machine and it runs really good.  You just need to make a few changes to /etc/X11/xorg.conf.

Jaunty is much faster than the Dell Ubuntu Remix 8.04 with the clutter dell-launcher.

---

### Post by jonkoay on 2009-06-09
> **Vaun said:**
> Are you running UNR (Ubuntu Netbook Remix)?  The two do not play well together at all.  You'll need to select either one or the other.

I have the same machine and it runs really good.  You just need to make a few changes to /etc/X11/xorg.conf.

Jaunty is much faster than the Dell Ubuntu Remix 8.04 with the clutter dell-launcher.
I'm using the desktop version of Ubuntu 9.04, not the UNR version or the Dell version. I'm not sure what went wrong, but I still cannot enable my desktop visual effect.

---

### Post by lswartz on 2009-06-09
> **Vaun said:**
> You just need to make a few changes to /etc/X11/xorg.conf.

What changes did you make in there? 

Thanks.

---

### Post by vinu76jsr on 2009-06-09
I got the same problem

my spec are
Dell Inspiron 1525(Integrated intel graphics) with freshly installed Jaunty

---

### Post by vinu76jsr on 2009-06-09
hey got it working , refer here

[https://bugs.edge.laaunchpad.net/ubuntu/+ACsource/compiz/+bug/155653]("https://bugs.edge.laaunchpad.net/ubuntu/+ACsource/compiz/+bug/155653")

---

### Post by jonkoay on 2009-06-10
I've manage to fix the problem, I have to go to gconf-editor and uncheck compositing_manager. I've enabled it previously because I needed it to get my gnome do to work on external monitor.

After I disabled it, I've manage to get my desktop Visual Effects working again.

---

### Post by bladams on 2009-07-04
Just got my Dell Vostro A90 a few days ago and didn't see your post until today.  My A90 came with a 16G SSD and 1GHz of RAM; would like to upgrade both. As you have a 64G SSD, did it come with that or have you upgraded? Same question about RAM, would appreciate your experience or thoughts. Thanks, Bob

---

### Post by jaqrah on 2009-07-04
> Just got my Dell Vostro A90 a few days ago and didn't see your post until today. My A90 came with a 16G SSD and 1GHz of RAM; would like to upgrade both. As you have a 64G SSD, did it come with that or have you upgraded? Same question about RAM, would appreciate your experience or thoughts. Thanks, Bob

First place I would start is here:

[http://www.ubuntumini.com/2008/11/upgrading-your-mini-9s-ram-guide.html](http://www.ubuntumini.com/2008/11/upgrading-your-mini-9s-ram-guide.html)

Great site...and this provides explicit direction for moving up to 2gb ram.

As of now, you can upgrade your SSD(MLC) to 64gb or 128gb with these new ssds from SuperTalent.  Or you can switch to a SSD(SLC)for increased read/write speeds.

[http://www.supertalent.com/products/ssd_detail.php?type=Half%20mini%202%20PCIe](http://www.supertalent.com/products/ssd_detail.php?type=Half%20mini%202%20PCIe)

The SSD (MLC) is now available retail, but moving up to 64gb or 128gb is a pricey endeavor.

---

### Post by jonkoay on 2009-07-06
> **bladams said:**
> Just got my Dell Vostro A90 a few days ago and didn't see your post until today.  My A90 came with a 16G SSD and 1GHz of RAM; would like to upgrade both. As you have a 64G SSD, did it come with that or have you upgraded? Same question about RAM, would appreciate your experience or thoughts. Thanks, Bob

Congrats on getting your Dell Vostro A90. Hope you got an excellent deal when buying it. I got mine with USD75 discount.

My default A90 came with the exact same configuration as yours. I upgraded mine, based on recommendation given in [http://www.mydellmini.com/forum/](http://www.mydellmini.com/forum/).

The following are the parts I have used for my upgrade.

1) Kingston Hyper-X 2GB DDR2-533 CAS 3
- [http://www.newegg.com/Product/Product.aspx?Item=N82E16820104100&Tpk=KHX4200S2LL%2f2G](http://www.newegg.com/Product/Product.aspx?Item=N82E16820104100&Tpk=KHX4200S2LL%2f2G)

2) RunCore Pro 64GB Mini PCIe PCI-e SSD Solid State Drive for Dell Inspiron Mini 9 and Vostro A90
- [http://www.mydigitaldiscount.com/ProductDetail.jsp?LISTID=800008DE-1224564428](http://www.mydigitaldiscount.com/ProductDetail.jsp?LISTID=800008DE-1224564428)

---

