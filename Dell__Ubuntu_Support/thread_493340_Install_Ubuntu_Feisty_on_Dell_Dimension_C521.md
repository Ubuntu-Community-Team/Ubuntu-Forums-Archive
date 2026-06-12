---
title: "Install Ubuntu Feisty on Dell Dimension C521"
date: 2007-07-05
forum: Dell  Ubuntu Support
---

### Post by EcliptuX on 2007-07-05
Hi,

I want to buy several Dimension C521 to install Ubuntu Feisty on them.
I read on several place on the internet there was a bug with the USB port (mouse) with Ubuntu : freeze etc...

This bug appears on november 2006.

Do you now if the lastests Dimension C521 are working without a bug with Ubuntu Feisty ?


Thanks for your answer :)

---

### Post by kill4killin on 2007-07-06
I'm not sure if this is a problem specific to the C521 model or with all installations of 7.04, however, I have a USB mouse on the computer I'm using right now as well as my desktop that are both running 7.04 and I can say that I have never had any problems with my USB mouse on these machines.

---

### Post by cacycleworks on 2007-07-06
> **EcliptuX said:**
> Hi,
I want to buy several Dimension C521 to install Ubuntu Feisty on them.
I read on several place on the internet there was a bug with the USB port (mouse) with Ubuntu : freeze etc...

This bug appears on november 2006.
Do you now if the lastests Dimension C521 are working without a bug with Ubuntu Feisty ?
Thanks for your answer :)


Hi EcliptuX,

My company bought 4 of the C521 with AMD processors. Buy an inexpensive USB hub and you will have no freezing issues. We have tested and installed the following Linux OSs without any of the freezing problems:
Edubuntu 
Kubuntu (live CD then install to HD)
Knoppix (live CD)
SLAX (installed and booted via 1M USB drive, no less)

A couple of options to always use if there is problem on initial boot: acpi=off and noapic

Kubuntu was the easiest to install.

From what I have read, recompiling the kernel and then also adjusting the USB port to the slow speed driver for the mouse and kybd may cure the problem.

These are hubs we used successfully:
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2948137&CatId=392](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2948137&CatId=392)
(is my top pick - gets the job done without lights and seems of quality)

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1363068&CatId=392](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1363068&CatId=392)
(the LEDs which light up are quite obnoxious in the dark - employees like the pretty lights - otherwise a great hub - is among my top pick)

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1440536&CatId=392](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1440536&CatId=392)
(gets very warm - otherwise a great hub)

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1530625&CatId=392](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1530625&CatId=392)
(the sony media stick reader slot is a bit pathetic - otherwise a great hub)

Basically, we go for the cheapest powered hubs available. All seem to have worked perfectly fine with Dell's USB mouse and keyboard)

With the incredible deals Dell is having, I do not hesitate to recommend the C521. Its upgradeability is a touch weak, with only 1 or 2 slots (low profile) and the less than full size opening in the front panel for the CD drive. 

Here is a webpage I started but need to finish:
[http://mbfreight.googlepages.com/dellamddimensionandlinux](http://mbfreight.googlepages.com/dellamddimensionandlinux)

:mrgreen:

---

### Post by EcliptuX on 2007-07-07
OK thanks for yours answers.
I read than the lastest Bios for the C521 (dated from january 2007) fix the USB bug.
So I suppose than the new C521 are running with the latest Bios version and the bug is now fixed.

Someone to confirm this information ?

---

### Post by cacycleworks on 2007-07-07
Actually, the latest BIOS is dated [6/27/2007, v 1.1.0]("http://support.dell.com/support/downloads/download.aspx?c=us&cs=04&l=en&s=bsd&releaseid=R158731&SystemID=DIM_P4_C521&servicetag=&os=WW1&osl=en&deviceid=308&devlib=0&typecnt=0&vercnt=5&catid=1&impid=-1&formatcnt=1&libid=1&fileid=212144"). Dell has an [amazing support section with downloads]("https://support.dell.com/support/downloads/index.aspx?c=us&cs=04&l=en&s=bsd") for all the latest drivers as well as the most comprehensive manuals I have ever seen from a computer maker. They completely and clearly outline the process to disassemble the case, etc, in the "service" manual for the C521. (as well as a diagram detailing all of the motherboard headers!)

I know my C521s are all flashed to 1.0.8 dated from May and the "usb problem" was still there. Buy a cheap hub and the C521 is 100% reliable. I promise. If not, I buy the C521 from you.

:)

---

### Post by EcliptuX on 2007-07-07
> **cacycleworks said:**
> Actually, the latest BIOS is dated [6/27/2007, v 1.1.0]("http://support.dell.com/support/downloads/download.aspx?c=us&cs=04&l=en&s=bsd&releaseid=R158731&SystemID=DIM_P4_C521&servicetag=&os=WW1&osl=en&deviceid=308&devlib=0&typecnt=0&vercnt=5&catid=1&impid=-1&formatcnt=1&libid=1&fileid=212144"). Dell has an [amazing support section with downloads]("https://support.dell.com/support/downloads/index.aspx?c=us&cs=04&l=en&s=bsd") for all the latest drivers as well as the most comprehensive manuals I have ever seen from a computer maker. They completely and clearly outline the process to disassemble the case, etc, in the "service" manual for the C521. (as well as a diagram detailing all of the motherboard headers!)

I know my C521s are all flashed to 1.0.8 dated from May and the "usb problem" was still there. Buy a cheap hub and the C521 is 100% reliable. I promise. If not, I buy the C521 from you.

:)

Ok ok cacycleworks ;)
The little problem of your solution is when I have to buy and install 10 C521.
In the worse case, to buy 10 usb hubs it's not very "nice" but if it's a valid issue, it's ok for me :)

---

### Post by cacycleworks on 2007-07-07
> **EcliptuX said:**
> Ok ok cacycleworks ;)
The little problem of your solution is when I have to buy and install 10 C521.
In the worse case, to buy 10 usb hubs it's not very "nice" but if it's a valid issue, it's ok for me :)

Cheers EcliptuX,

Yes, thankfully, the hubs are very inexpensive. I operate a mail order company, so if you are not in the US, I can act as middleman for you to get any of the hubs I list above. Further, I have found that when the original manufacturer (in China, Taiwan, etc) can be discovered, they will often ship products bypassing the dealer network for about 50% of MSRP and have very cheap postage charge.*

We've been working on bigger issues than the keyboard, so once we have something stable for our new internal network, I'll look into potential fixes like compiling the kernel, USB settings, etc. This might happen within 3 months. ;)

:) Chris


*- a quick Google on the part number (CYC-2027) shown on the printed circuit board of the LED hub resulted in this Google translated page: 
Shenzhen creators Yuchen Technology Limited, the company's headquarters is located in Bao'an District of Shenzhen.Factories mainly engaged in computer peripheral products HUB USB serial, and USB peripherals such as small manufacturers, USBHUB professional production. Most of the products through CE / UL / ROHS and other international quality certification.

A little more search leads to this page, which really has good info:
[ http://www.made-in-china.com/ .....]("http://www.made-in-china.com/productdirectory.do?subaction=hunt&mode=and&style=b&word=7+port+USB+HUB&comProvince=nolimit&code=0&x=0&y=0")

---

### Post by EcliptuX on 2007-08-02
Thanks for your proposition but it's ok for the hubs :)

The problem now, is to buy a C521 model in France !
This model is suddently not available on the french website :(

---

### Post by cacycleworks on 2007-08-02
> **EcliptuX said:**
> 
This model is suddently not available on the french website :(


Ooooooo, yes, it would seem Dell is ending that product and now pushing the Vostro. On the US small business site, they have the E521 for $359 and the C521 for $409. And the new vostro small and smaller for $369 and $399.

Dell has a small selection of chipsets, so installing ubuntu should fit a similar recipe for any of them.

:)
Chris

---

