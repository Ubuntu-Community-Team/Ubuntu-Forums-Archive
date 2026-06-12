---
title: "Better Broadcom Wireless support?"
date: 2005-10-13
forum: Desktop Environments
---

### Post by Chris361 on 2005-10-13
I installed Hoary about a month ago, fought with it to get my wireless card to work. I finally got it to recognize the card, however, it would not enable itself - therefore it wouldn't work.

So quick question, I have heard that Breezy clears up some hardware problems, including wireless support. Has there been improvements in the Broadcom area? Broadcom, if you aren't aware, do not have Linux drivers for their wireless chipsets. I am using a Compaq R3000CA (Canadian edition) Laptop and it has a Broadcom 802.11g chipset. As well, is there support for WPA encrypted networks?

Thanks guys.

---

### Post by drogoh on 2005-10-13
Ndiswrapper has fairly good Broadcom support, might look into that.

Look [here]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B") to see if your chipset is supported.

---

### Post by Chris361 on 2005-10-13
Thanks I will check it out.

---

### Post by revellion on 2005-10-13
You're out of luck since this is not an Ubuntu related issue. it's about Broadcom's lack of giving out the specs so that a driver is possible to make.

I've gotten it to work using NDIS-Wrapper on a Dell Latitude D610 without too much problems :|

Still... a Native driver would be a lot better :D

---

### Post by Chris361 on 2005-10-13
So basically the support has not changed in the new release?

What about WPA encryption?

Oh and I have the Broadcom 4306 (or 94306) 802.11g Wireless chipset.

---

### Post by Chris361 on 2005-10-13
I sent an email to Broadcom using there contact form on the Broadcom website.

It looked something like this:

> Subject: Linux drivers

Where are they? Please release the the specs of your drivers to the Linux community. Oh and, welcome to the Open Source revolution. Please support it (I won't tell Microsoft I promise).

I am using the Broadcom 802.11g 4306 (Or 94306 not sure) Wireless chipset in my Compaq R3000 Laptop (Canadian edition).

I hope you decide to support ALL of your customers soon.

You can send an email to them too at: [http://broadcom.com/contact/feedback.php](http://broadcom.com/contact/feedback.php)

hehe

---

### Post by Chris361 on 2005-10-13
Ohhh a reply! :D

Broadcom writes:

> Broadcom is currently evaluating our support strategy for Linux users. As the chipset supplier, Broadcom provides Linux support to our customers - the manufacturers of wireless devices - that ultimately provide products to end customers, such as wireless LAN vendors, cable modem vendors, and notebook providers. It is up to these manufacturers to provide Linux client support to their end customers. Broadcom does not make a Linux client version available for end users at this time, however this may change in the future. In the meantime, please contact the manufacturer of your wireless device for Linux drivers. Linux support for certain products may also be available from Linuxant, and third party provider at [http://www.linuxant.com/driverloader/](http://www.linuxant.com/driverloader/)



Regards,

Broadcom Support Team

I was a jerk, but hey, I now have a response! ;)

---

### Post by GeneralZod on 2005-10-13
> I was a jerk, but hey, I now have a response! 

Heh - nice work! :) It would be cool in future if people would adopt a more professional tone, though, as antagonism solves nothing.

This sounds like a stock response, so I'm guessing they've been asked this question tons of times.  Personally, I'm surprised they don't just open up the specs - wireless cards are a mature technology now and so heavily commoditised that I can't believe there are any worthwhile "trade secrets" remaining!  And this goes double for WinModems! :)

---

### Post by Chris361 on 2005-10-13
I agree. And yes I could have been nicer hehe.

---

### Post by dto on 2005-10-13
> As the chipset supplier, Broadcom provides Linux support to our customers - the manufacturers of wireless devices - that ultimately provide products to end customers, such as wireless LAN vendors, cable modem vendors, and notebook providers. It is up to these manufacturers to provide Linux client support to their end customers.
As far as I know, none of us are direct Intel customers, yet they have made an effort to the community to ensure native Linux driver support for their wireless cards, haven't they? Isn't [this](http://ipw2200.sourceforge.net/) an Intel-initiated project, or am I incorrect?

---

### Post by Antman on 2005-10-15
There are two distros I have used that support my broadcom pCMCIA card right out of the box: Linspire 5 and Mepis 3.3.1. I think Suse 10 does too but don't quote me on that. I'm not sure how they can get their distros to work with the cards and other linux distros can't?!? 

Oh well... that is why you need to pick a distro that works with YOUR hardware. ;) 

Ant

---

### Post by idarwin on 2005-12-07
[QUOTE=Chris361]Ohhh a reply! :D

...


I was a jerk, but hey, I now have a response! ;)[/QUOTE]

Do you really? Do you realize that that response was generated automatically by a PHP script, that nobody at Broadcom looked at your input or has even heard of you? I got  the same form letter, and within about 60 seconds of submitting my (slightly more polite) request to that script.  I doubt that they're even counting them. I'd bet the logic in the script is something like:
[LIST]
[*]If subject == 'Linux Drivers'; then sendEmail(notListening.txt); return; end;
[*]Save email, comment in database table 'toBeLookedat'
[/LIST]

---

### Post by idarwin on 2005-12-07
BTW, there is an active Linux driver support project for the 4306, in several phases, and without any intentional help from BroadCom:[LIST=1]
[*]Reverse-engineering the specifications from the binary Linux drivers that were released; see both [http://linux-bcom4301.sourceforge.net/]("http://linux-bcom4301.sourceforge.net/") and  [http://bcm-specs.sipsolutions.net/]("http://bcm-specs.sipsolutions.net/")
[*]Trying to write a Linux driver from this spec; see [http://bcm43xx.berlios.de/]("http://bcm43xx.berlios.de/")
[*]Presumably this information will also be useful to open source OS projects that don't use Linux drivers (yes, these do exist :-)), like the BSD projects such as [OpenBSD]("http://www.openbsd.org/") which was a leader in getting some other wireless drivers supported. Apple's Darwin, FreeBSD, NetBSD, etc.
[/LIST]
If you have any doubts about the legality of this approach, please do not bother this list with them as it is a technical list. Do, however, look up the term "Chinese Wall" on Wikipedia (there's a link to this on one of the pages cited above).

I don't believe the driver is ready for prime time yet but, if you like to live on the edge and enjoy compiling your very own Linux kernel, this might be just what you need. The more people that test it and provide useful feedback, of course, the better.

So: things are looking up (slowly) for people who bought things with 4306's in them. :)

---

