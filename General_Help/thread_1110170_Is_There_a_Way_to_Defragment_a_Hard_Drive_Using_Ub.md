---
title: "Is There a Way to Defragment a Hard Drive Using Ubuntu?"
date: 2009-03-29
forum: General Help
---

### Post by 2048Megabytes on 2009-03-29
[SIZE="3"]Is there a way to defragment a hard drive using the Linux Ubuntu operating system?[/SIZE]

---

### Post by UbuntuNerd on 2009-03-29
you mean you want to defragment the linux computer or you want to defragment a windows computer from the linux one?

---

### Post by fballem on 2009-03-29
The following article might help:

[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

If you're running a dual boot system, then the Windows files will need to be defragmented, but not the linux files.

Hope this helps,

---

### Post by 2048Megabytes on 2009-03-30
[SIZE="3"]That is very interesting information.  Fragmented files won't be all over your hard drive if you are using a Linux Operating System.  

Linux really does have advantages over Windows (the biggest being security).  I really wish I could install Linux Ubuntu and dual boot on my system, but my motherboard hates it.  The chipset with the Gigabyte GA-M78SM-S2H motherboard doesn't agree with the Ubuntu Operating System.  

Anyone know of a Linux Operating System that will install easily and work with no issues using my current motherboard?[/SIZE]

---

### Post by KCG102282 on 2009-03-30
> **2048Megabytes said:**
> [SIZE="3"]That is very interesting information.  Fragmented files won't be all over your hard drive if you are using a Linux Operating System.  

Linux really does have advantages over Windows (the biggest being security).  I really wish I could install Linux Ubuntu and dual boot on my system, but my motherboard hates it.  The chipset with the Gigabyte GA-M78SM-S2H motherboard doesn't agree with the Ubuntu Operating System.  

Anyone know of a Linux Operating System that will install easily and work with no issues using my current motherboard?[/SIZE]
What issues are you having with your motherboard?

---

### Post by coffeecat on 2009-03-30
> **2048Megabytes said:**
> [SIZE=3]The chipset with the Gigabyte GA-M78SM-S2H motherboard doesn't agree with the Ubuntu Operating System.[/SIZE]

Two questions: which versions of Ubuntu have you tried, and what exactly went wrong when you did try.

If you've only tried Hardy 8.04, you might have more luck with Intrepid 8.10, or even 9.04 Jaunty Beta.

According to the Gigabyte website, that board has the NVIDIA GeForce 8200 chipset which I would have thought would work just fine.

---

### Post by Cybie257 on 2009-03-30
> **2048Megabytes said:**
> [SIZE="3"]The chipset with the Gigabyte GA-M78SM-S2H motherboard doesn't agree with the Ubuntu Operating System.  

Anyone know of a Linux Operating System that will install easily and work with no issues using my current motherboard?[/SIZE]

It would be interesting to hear what sort of problems you are having. I use a Gigabyte board and have had nothing but success with it, even installing a native (via the dd image found on the net) MAC OSX Op. I took a quick look at the specs of your board and the only real (big) difference is that you have integrated nVidia VGA (which is great for Linux) and and AMD Processor. Personally I have always had and preferred Intel vs AMD, but would be far from accusing the AMD from being an issue. 

In the past, when I used to prefer the KDE Desktop, I tried installing Kubuntu (V 6.04) on a laptop. That freaked it out and it would never work. Ubuntu installed flawlessly. Maybe try Kubuntu and see if that has the opposite effect that I encountered. 

Other than that, please post your issue(s) and maybe there is something someone can do to help. :)

-Cybie

---

### Post by 2048Megabytes on 2009-03-30
[SIZE="3"]I am pretty sure it is the motherboard I am having issues with. My specifications are as follows:

Power Supply: OCZ StealthXStream OCZ600SXS 600 Watt 
Video Card: MSI Radeon HD 3650
Memory: 2 gigabytes of Super Talent PC2-6400 
Motherboard: Gigabyte GA-M78SM-S2H
Processor: AMD Athlon 4600+ Dual-Core Windsor (2.4 gigahertz)

I have tried to install the following Linux Operating Systems and they will not install.  I can't remember what error codes come up, but they will not work.

OpenSuse 10.3
Ubuntu 7.10
Ubuntu 8.04

I am currently using Windows Vista 32-bit Service Pack 1 for my operating system.
[/SIZE]

---

### Post by sailthesea on 2009-03-30
To answer your original question:
 Is There a Way to Defragment a Hard Drive Using Ubuntu?
Not if your trying to install Ubuntu, use the windows utility to pack everything down to the "front" of the HDD (do it at least twice) then you shouldn't have any problem installing Ubuntu of most distros on your cleaned drive
Good Luck

---

### Post by Slim Odds on 2009-03-30
> **KCG102282 said:**
> What issues are you having with your motherboard?

Well.... for one thing.... the FONTS ARE HUGE!!   :)

---

### Post by freonchill on 2009-03-30
theme/txt size?

---

### Post by fballem on 2009-03-31
I noticed a large text size on my display as well. I have an Nvidia 8600 and my monitor is an LG W2242TQ (22-inch lcd).

The first problem may be that your resolution is not set correctly. The following post provides some solutions for your Video Card: [http://ubuntuforums.org/showthread.php?t=1076047&highlight=ati+screen+resolution](http://ubuntuforums.org/showthread.php?t=1076047&highlight=ati+screen+resolution).

You may want to download the Jaunty beta from here: [http://www.ubuntu.com/testing/jaunty/beta](http://www.ubuntu.com/testing/jaunty/beta) I have been using Jaunty since alpha-5 and it appears remarkably stable. Also your video card is supported in this release. Jaunty is due for release on, or about, April 23. It should work like the past, where if you installed the Beta and keep current with updates, then your installation will move seamlessly from Beta to Release with no problem.

Given that you have a dual-core processor, I suggest that the 64-bit version would be suitable.

Assuming that your resolution is correctly set (mine is 1680 x 1050), then I right-click on the display, which gives me the menu shown in screenshot.png.

I select change desktop background, which gives me the menu shown in Screenshot-Appearance Preferences. I select the Fonts tab and then select the Details button, which gives me the screen shown in screenshot-font rendering details.png. I can then adjust the size of the fonts.

Hope that these suggestions help.

---

### Post by KCG102282 on 2009-03-31
> **2048Megabytes said:**
> [SIZE="3"]I am pretty sure it is the motherboard I am having issues with. My specifications are as follows:

Power Supply: OCZ StealthXStream OCZ600SXS 600 Watt 
Video Card: MSI Radeon HD 3650
Memory: 2 gigabytes of Super Talent PC2-6400 
Motherboard: Gigabyte GA-M78SM-S2H
Processor: AMD Athlon 4600+ Dual-Core Windsor (2.4 gigahertz)

I have tried to install the following Linux Operating Systems and they will not install.  I can't remember what error codes come up, but they will not work.

OpenSuse 10.3
Ubuntu 7.10
Ubuntu 8.04

I am currently using Windows Vista 32-bit Service Pack 1 for my operating system.
[/SIZE]
Without error codes we cant help you!

---

