---
title: "Dell Mini 10 with Ubuntu update."
date: 2009-05-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by albinootje on 2009-05-11
Just found this here : [http://www.linux-magazine.com/online/news/dell_freshens_up_its_mini_10_netbook_with_ubuntu](http://www.linux-magazine.com/online/news/dell_freshens_up_its_mini_10_netbook_with_ubuntu)
See the video :
[http://en.community.dell.com/blogs/direct2dell/archive/2009/05/07/Ubuntu-Now-Available-for-Mini-10-Customers-in-the-United-States-and-Canada.aspx](http://en.community.dell.com/blogs/direct2dell/archive/2009/05/07/Ubuntu-Now-Available-for-Mini-10-Customers-in-the-United-States-and-Canada.aspx)

I'm happy to see Dell and Canonical working together on this, and the video also thanks the community, nice to hear that.

Any thoughts about this specific netbook ? Would you recommend it ? How's the keyboard size ?

---

### Post by floborg on 2009-05-12
I thought the Ubuntu Mini 10v was supposed to sell for $300 US.  The video links to a Mini 10 w/Ubuntu selling for $400 US.

---

### Post by stephanvaningen on 2009-05-12
There's an issue with the graphics chipset (GMA 500), which does not have correct (open source) driver available; some say it is in development at Tungsten/Intel, but this pain is going on for months...

---

### Post by mikewhatever on 2009-05-13
> **floborg said:**
> I thought the Ubuntu Mini 10v was supposed to sell for $300 US.  The video links to a Mini 10 w/Ubuntu selling for $400 US.

You are so spoiled. Dell Mini 9 is about 600-700$ over here, Dell Mini 10 costs about 725$, and Dell Mini 12 is 840$.:confused: For 400$, I'd probably get two.:P

---

### Post by skunkbad on 2009-05-13
I saw the mini 10 at Best Buy this weekend, and it was nicer than my mini 9, because the keyboard layout is normal. I don't think it is worth the money over the $249 mini 9.

---

### Post by floborg on 2009-05-13
> **mikewhatever said:**
> You are so spoiled. Dell Mini 9 is about 600-700$ over here, Dell Mini 10 costs about 725$, and Dell Mini 12 is 840$.:confused: For 400$, I'd probably get two.:P

Ouch.  At any rate, YES, Dell has put the $299 US Mini10v up on the website.  It is the same price w/Windows XP or Ubuntu 8.04 - with the same specs?:confused:

---

### Post by tyroeternal on 2009-05-14
As stephanvaningen mentioned, the Mini 10 is a bad choice because of the graphics situation right now.  Overall I like my Mini 12, and the Mini 10 is equally nice.

There are 2D drivers available through a PPA that work for Ubuntu Jaunty and the Intel GMA 500, so there is some work being done to make these systems usable.

Personally I would grab the Starling netbook from [System 76]("http://system76.com").

---

### Post by stephanvaningen on 2009-05-15
> **tyroeternal said:**
> As stephanvaningen mentioned, the Mini 10 is a bad choice because of the graphics situation right now.  Overall I like my Mini 12, and the Mini 10 is equally nice.

There are 2D drivers available through a PPA that work for Ubuntu Jaunty and the Intel GMA 500, so there is some work being done to make these systems usable.

Personally I would grab the Starling netbook from [System 76]("http://system76.com").

Yes, but system76 only delivers USA&Canada, which is only to about 5% of the world, i.e: we live in Europe ;-)

---

### Post by floborg on 2009-05-15
> **tyroeternal said:**
> As stephanvaningen mentioned, the Mini 10 is a bad choice because of the graphics situation right now.  Overall I like my Mini 12, and the Mini 10 is equally nice.

There are 2D drivers available through a PPA that work for Ubuntu Jaunty and the Intel GMA 500, so there is some work being done to make these systems usable.

Personally I would grab the Starling netbook from [System 76]("http://system76.com").

Dell ships this thing, though, with Ubuntu 8.04.  So, it would be using the Intel drivers from then, which shouldn't have the issues in Jaunty.  I wouldn't expect Dell to be so careless to ship Jaunty w/o customizing it with a better driver - whenever they do start shipping Jaunty.

---

### Post by sirebral on 2009-05-15
> **tyroeternal said:**
> As stephanvaningen mentioned, the Mini 10 is a bad choice because of the graphics situation right now.  Overall I like my Mini 12, and the Mini 10 is equally nice.

There are 2D drivers available through a PPA that work for Ubuntu Jaunty and the Intel GMA 500, so there is some work being done to make these systems usable.

Personally I would grab the Starling netbook from [System 76]("http://system76.com").

Wow. The Starling look pretty good.  It does look like a redesigned Mini 9 though.  Looks like they took the Mini 9 and smoothed out all the complaints I had though. :(  I still like my Mini 9.  I spend so much time on it.

---

### Post by tyroeternal on 2009-05-16
> **floborg said:**
> Dell ships this thing, though, with Ubuntu 8.04.  So, it would be using the Intel drivers from then, which shouldn't have the issues in Jaunty.  I wouldn't expect Dell to be so careless to ship Jaunty w/o customizing it with a better driver - whenever they do start shipping Jaunty.

There was a driver that made it into the ubuntu-mobile ppa which provides a basic 2d driver for Poulsbo.  There is certainly work being done, but it is much slower than most (all?) of us would like.

If you are determined to go with a Dell get the mini 9.  It has a well supported video card, but it has regressions in Jaunty's kernel right now.  In a few months when Karmic is set to come out it will have kernel 2.6.30 which should improve things dramatically (or compile a custom kernel with 2.6.30 now).

@stephanvaningen, you should move to the US so you can have a System76 laptop shipped to your house! :P

---

### Post by R_U_Q_R_U on 2009-05-25
Great news! The Dell Mini 10 now runs on Ubuntu 9.04 at full nominal resolution of 1024  x  576!
 

What has happened is that the [Ubuntu Mobile Team]("https://edge.launchpad.net/%7Eubuntu-mobile") has compiled and packaged kernel modules, X.org drivers, libraries to interface to kernel DRM services, etc. etc. for the Poulsbo chipset and made them available on their PPA.


[http://mok0.wordpress.com/2009/05/25/ubuntu-on-the-dell-mini-10-2/](http://mok0.wordpress.com/2009/05/25/ubuntu-on-the-dell-mini-10-2/)

---

### Post by Daveski on 2009-05-31
Well I have just ordered a Mini 10v with Ubuntu - can't wait for it to arrive.

[edit] - Huh, the estimated delivery date has slipped to nearly 7 weeks!
[edit2] - Arrived this morning, a mere 3 weeks after ordering.

---

### Post by stephanvaningen on 2010-01-24
> **tyroeternal said:**
> There was a driver that made it into the ubuntu-mobile ppa which provides a basic 2d driver for Poulsbo.  There is certainly work being done, but it is much slower than most (all?) of us would like.

If you are determined to go with a Dell get the mini 9.  It has a well supported video card, but it has regressions in Jaunty's kernel right now.  In a few months when Karmic is set to come out it will have kernel 2.6.30 which should improve things dramatically (or compile a custom kernel with 2.6.30 now).

@stephanvaningen, you should move to the US so you can have a System76 laptop shipped to your house! :P
@tyroeternal  I understand your advice ;-). To tell the truth I contacted them already more than 6 months ago asking them when they plan to expand there sales-area to Europe or even EMEA

---

### Post by mikewhatever on 2010-01-24
> **stephanvaningen said:**
> @tyroeternal  I understand your advice ;-). To tell the truth I contacted them already more than 6 months ago asking them when they plan to expand there sales-area to Europe or even EMEA

Err, the thread is 9 months old.

---

