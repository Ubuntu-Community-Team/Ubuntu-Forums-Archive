---
title: "Is ordering a Dell a mistake?"
date: 2007-08-08
forum: Dell  Ubuntu Support
---

### Post by vcallaway on 2007-08-08
It initially took me a week to place the order for my laptop.  I wanted a 17" screen and Ubuntu.  They don't offer one pre-loaded so I ordered the Inspiron 1720.

The order date was 7.28 with a ship date of today 8.8.  Today I get an automated phone call telling me the computer is back ordered and estimated ship day is 8.28!

I went with dell in the first place because I know that everything is compatible.  I hate to just cancel the order and go somewhere else.

It should not take a month to get a laptop.  I'm afraid if I cancel the order it will take a month to get my money back.

---

### Post by syssyphus on 2007-08-08
I am going through the same thing here.... 

basically, everyone I have heard of that has received their Ubuntu dell has been happy with it.

and the consensus is that the dell deals are better than system76, etc.

dell is a huge bureaucratic monster, and it takes forever to get your gear.

I will probably end up sticking it out and getting my dell, but I am going to be cussing a lot in the mean time.

---

### Post by rfruth on 2007-08-08
The 1720 is a Vista box (gonna dual boot ?) wi-fi use planned ?  I want / need a notebook also want to support Ubuntu not sure what to do :confused:

---

### Post by Syke on 2007-08-09
The 1720 is a Santa Rosa chipset. You're going to have a lot of troubles getting Ubuntu to run on that. Even the 1420N with Ubuntu pre-installed has a lot of troubles. I was at LinuxWorld today playing with the 1420N. I tried to turn on Desktop Effects - oops, crashed the machine hard. How can they ship an Ubuntu certified machine that can't even run 3D?!

---

### Post by deserthowler on 2007-08-09
> **rfruth said:**
> The 1720 is a Vista box (gonna dual boot ?) wi-fi use planned ?  I want / need a notebook also want to support Ubuntu not sure what to do :confused:

Well, my 1420 has Ubuntu installed and things work great so far.
Earl

---

### Post by AndyQ on 2007-08-09
I have a 1720 running Ubunto and had similar order issues. Ordered around the 3 July, initial shipping was the 20th. On the 19th it was then delayed until the 14th August however it arrived the following week, so I think the estimated dates are to be taken a little lightly.

Regarding Ubuntu, I initially had a few issues and has been mentioned, at first site it appears that the live cd won't work - however it does (and I think that this applies to the 1420 also.

To get it working is a three step process. At the boot options, press F6 and add break=top to the beginning of the option (it does need to be at the beginning, for some reasonit didn't work at the end).

That will break out into a console very early on in the boot sequence. Ignore the tty message and type:
modprobe piix
exit

This loads the piix driver which is needed to mount the DVD image (I think) and continues the boot sequence.

X will fail to load at this point however as the NVidia drivers don't support the internal card. However just edit the /etc/X11/xorg.conf file, change "nv" to "vesa" and then run startx.

That will load X up and you can do your install.

There is a more detailed guide to the other minor issues in this forum (search for 1710).

---

### Post by vcallaway on 2007-08-09
I read through all of the issues before placing my order.

While the system may not be boot and go it is all supported.  I don't have any problems dealing with that.  I suppose I will just wait.  I'm just annoyed.

I will NOT be dual booting.  I have zero need for windows.

---

### Post by notwen on 2007-08-09
I have had pretty good luck w/ my first order from Dell.  I placed the order for my Inspiron 1420n on July 17th and received it Aug 1st.  The Dell Community Linux forums are no where near the likes of Ubuntu Forums but atleast it's a start for Linux & a major OEM relationship.  I hope you get what you want, regardless of who you end up purchasing your PC from. =]

---

### Post by kuja on 2007-08-09
I guess I got lucky. I ordered mine around jul 10 and recieved around aug 6.

---

### Post by mpospisil on 2007-08-09
I ordered my Dell Ubuntu desktop on July 6th and it said its estimated shipping date was August 10th.  However I received my computer on July 17th.

---

### Post by jmnormand on 2007-08-09
Just an update:  the 3d on the 1420/1520/1720 with the intel x3100 (xserver-xorg-video-intel) was patched recently and is now working fine.

it did take 3 weeks for the 1420 to show up about a month ago.

---

### Post by timcredible on 2007-08-09
seems like all my friends and co-workers buy dell desktops and laptops (i'm not sure why, maybe their tv ads are best).  anyway, linux doesn't work well on most of them - the most recent issue was someone bought a xps and wanted to dual boot but gparted couldn't re-partition the hard drive - don't know why.  the issue before that was person had to send their desktop back because it kept blue-screening (did it from the start, before we got a chance to install linux).  dell was easy to work with to get a replacement, however.  anyway, imho, dell is overpriced.  i've had 4 HPs and have had zero problems with them, and everything worked perfectly with linux.  also, since they support linux very well on their printers, i always look at them first for desktops.  just my 2 cents worth.

---

### Post by jrusso2 on 2007-08-09
Dell laptops are built in various places in Asia.  When you place an order there is someone who gathers all the parts for your particular laptop with all its features into a bin.

If a part is not available they have to order it.  They only keep a minimal stock of parts on hand.

I am willing to bet something they need to build yours is out of stock

---

### Post by sacherjj on 2007-08-09
I think the desktops have more common components and are easier to predict.  I've received two E520Ns and they shipped in a reasonable time.  Most serious delays are Laptops.

---

### Post by jacob01 on 2007-08-09
when i orderd my dell with ubuntu it was befor ther switched from dimension to insparon and i orderd mine and the estimated time of delivery was like 3 weeks then i checked back 2 days later and it said it had been shipped and then a 2 days later i had my dell and i was so supprised it was great:guitar:

---

### Post by Tulsapoke on 2007-08-09
I have had my E1505 for almost 2yrs and I have been running Ubuntu for the last year.  I have had no problems and I have had no problems with Ubuntu.  On my recommendation my father and brother also have Dell laptops with Ubuntu and they have had no problems either.

---

