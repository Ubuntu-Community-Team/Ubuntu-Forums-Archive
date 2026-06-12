---
title: "Budget gaming video card recommendation"
date: 2011-09-17
forum: Gaming &amp; Leisure
---

### Post by jtirrell1 on 2011-09-17
Hey all, this is my first post here (I'm pretty new to posting on forums in general too) so apologies if I am confusing or anything.

I'm looking for a budget video card that would play nicely with Ubuntu that I could use for some gaming.

My specs:
2.2Ghz AMD dual core proc
2 gbs ddr2 ram (planning to upgrade to 4 soon)
Onboard Geforce 6150LE video card

The onboard video hasn't been a problem before, since I mostly play older games. (Maybe if my new card can handle it, I'll play some newer games) Recently, I bought a 24" monitor to play on, not realizing that my onboard card/driver has rendering issues (even outside of games) when I try to change my resolution to the recommended 1920x1080.

So, I'd like to get a new graphics card, but I'm nervous that I'll get one that won't work well with the open source drivers, or won't go up to the recommended resolution, and I'm on a poor college student's budget.

Any recommendations?

Thanks in advance,
jtirr

---

### Post by jtirrell1 on 2011-09-17
I forgot to say, I'm using Ubuntu 11.04. I could go back to an earlier version, but I'd rather not.

---

### Post by kaldor on 2011-09-17
For a low-end card, maybe an [_AMD Radeon HD 6570_]("http://www.newegg.ca/Product/Product.aspx?Item=N82E16814102934") would be fine. AMD works quite a lot better these days for Linux. Since you say you usually only play older games, I can't be sure of what you mean. Give some of the titles you play :)

_[Here]("http://www.phoronix.com/scan.php?page=article&item=amd_radeon_hd6450&num=4")_ is a comparison of some GPUs on Linux.

If you can afford it, though, the AMD Radeon HD 6770 is a really good card.

Edit: If you're going to do this, I'd wait for Ubuntu 11.10 because there are some newer drivers by default in the 11.10 release. You can download and install drivers yourself for 11.04, but it's quite often more painful than neccessary.

The main reason I am saying to go with AMD instead of NVIDIA is because of AMD's Linux plan. They sync their driver releases with Ubuntu releases, develop open source drivers, and support all of their newest stuff on Linux.

---

### Post by thatguruguy on 2011-09-17
> **kaldor said:**
> For a low-end card, maybe an [_AMD Radeon HD 6570_]("http://www.newegg.ca/Product/Product.aspx?Item=N82E16814102934") would be fine. AMD works quite a lot better these days for Linux. Since you say you usually only play older games, I can't be sure of what you mean. Give some of the titles you play :)

_[Here]("http://www.phoronix.com/scan.php?page=article&item=amd_radeon_hd6450&num=4")_ is a comparison of some GPUs on Linux.

If you can afford it, though, the AMD Radeon HD 6770 is a really good card.

Edit: If you're going to do this, I'd wait for Ubuntu 11.10 because there are some newer drivers by default in the 11.10 release. You can download and install drivers yourself for 11.04, but it's quite often more painful than neccessary.

The main reason I am saying to go with AMD instead of NVIDIA is because of AMD's Linux plan. They sync their driver releases with Ubuntu releases, develop open source drivers, and support all of their newest stuff on Linux.

According to the comparison you posted, the NVIDIA GT 240 is a better buy.  In the tests where the 6770 won, it won by ~10%.  In the tests where the GT 240 won, it was sometimes 50%-100% faster.  Plus, the GT 240 can be bought on new egg for $10 less than the HD 6770.

---

### Post by kaldor on 2011-09-17
> **thatguruguy said:**
> According to the comparison you posted, the NVIDIA GT 240 is a better buy.  In the tests where the 6770 won, it won by ~10%.  In the tests where the GT 240 won, it was sometimes 50%-100% faster.  Plus, the GT 240 can be bought on new egg for $10 less than the HD 6770.

Well then the GT 240 may be able to fit into his budget and be better for him. I'm just somewhat biased due to NVIDIA's lack of attention to Linux (see Optimus) and statements saying they won't support Wayland. Personally, I feel better buying a product from a company that I am sure will support my OS in the future.

---

### Post by PaulInBHC on 2011-09-17
I used to have problems getting an ATI card working with ubuntu. I have an onboard nvidia 730 and could not get 11.04 to install. Recently I installed an ATI HD5670 and am running 11.10 beta with no video problems. I like the card and newegg has them for a good price.

---

### Post by kaldor on 2011-09-17
> **PaulInBHC said:**
> I used to have problems getting an ATI card working with ubuntu. I have an onboard nvidia 730 and could not get 11.04 to install. Recently I installed an ATI HD5670 and am running 11.10 beta with no video problems. I like the card and newegg has them for a good price.

This is another reason why I am recommending AMD; their Linux support keeps getting stronger and better. I am in the same boat as you. 2 years ago, an AMD card I kept trying to get working would not behave. I bought a brand new PC with a brand new 6000 series AMD card and it has no issues. They support open source drivers, they constantly patch and fix their proprietary drivers, and they aren't limiting their hardware drivers to just one OS.

---

### Post by jtirrell1 on 2011-09-17
Awesome tips, thanks. I may buy the 6570. The main  idea was to get one that would run my monitor at 1920x1080 without problems.

The games I mostly play now are things like Half-Life, Warcraft 3, starcraft, Morrowind (I'll try to play ES4 if i can), maybe WoW. Big fan of rts games, which don't change too much as far as graphics go.

Thanks.

---

### Post by HolgerB on 2011-09-17
Ok, here are my two cents:
I usually refuse to buy the latest and greatest new cards from either NVidia and / or ATI. They drop to half the prices once a year has gone by.

Esp. for one being on a budget I would try to get a used NVidia card from ebay. I shot myself a 9800GT with 512 MB for around 30€. For my media PC I got another NVidia card, a passive 9500GT with 1GB of RAM for something like 15€.

From my experience a card such as the 9800GT will play older games with upper details levels at 1080p without any stress. I would stay away from ATI. They have better open source driver support now (check phoronix.com), but in general the open source radeon is no match for fglrx and sometimes installing fglrx under Linux can be more a PITA than the NVidia pendant.

---

### Post by kaldor on 2011-09-17
> **jtirrell1 said:**
> Awesome tips, thanks. I may buy the 6570. The main  idea was to get one that would run my monitor at 1920x1080 without problems.

The games I mostly play now are things like Half-Life, Warcraft 3, starcraft, Morrowind (I'll try to play ES4 if i can), maybe WoW. Big fan of rts games, which don't change too much as far as graphics go.

Thanks.

Will you be doing the gaming on WINE or Windows?

---

### Post by R33D3M33R on 2011-09-18
> **thatguruguy said:**
> According to the comparison you posted, the NVIDIA GT 240 is a better buy.  In the tests where the 6770 won, it won by ~10%.  In the tests where the GT 240 won, it was sometimes 50%-100% faster.  Plus, the GT 240 can be bought on new egg for $10 less than the HD 6770.

This might be true, but if the OP ever decides to install Windows alongside Linux or the ATI drivers improve performance, he will notice the HD 6770 being significantly better. 

You can compare HD 6570 with GT 240 price/performance. 6570 is only a few procent faster in Windows, but it might take while to catch up in Linux. Power consumption is nearly the same. If you get GT 240 much cheaper, don't hesitate to buy it. If you buy HD 6570, **be sure to buy the GDDR5 one**!

Look at the review here: [http://www.tomshardware.com/reviews/radeon-hd-6570-radeon-hd-6670-turks,2925.html](http://www.tomshardware.com/reviews/radeon-hd-6570-radeon-hd-6670-turks,2925.html)

---

### Post by jtirrell1 on 2011-09-18
Mostly Wine. I may dual boot with windows, though, for the games that don't work on wine.

---

### Post by Perfect Storm on 2011-09-18
If you also want to gaming via wine, go for Nvidia card.

---

### Post by kaldor on 2011-09-19
> **Artificial Intelligence said:**
> If you also want to gaming via wine, go for Nvidia card.

Agreed.

---

