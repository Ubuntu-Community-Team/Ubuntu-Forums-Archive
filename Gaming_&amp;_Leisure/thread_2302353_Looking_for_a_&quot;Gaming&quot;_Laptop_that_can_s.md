---
title: "Looking for a &quot;Gaming&quot; Laptop that can support Ubuntu and Virtualization"
date: 2015-11-09
forum: Gaming &amp; Leisure
---

### Post by names_are_useless on 2015-11-09
Hello Ubuntu Community,

I've been working for a few years in Linux (specifically Red Hat), but I'm interested in getting into Ubuntu ... and in getting a laptop that can support it.

What I'm looking for in a laptop will look like a very odd mix: a laptop that I can use both for ...
[LIST=1]
[*]**Virtualization & Penetration Testing:** I need a Laptop that could easily support Virtualization of several OSs, such as KaliLinux (Which I'd use for penetration testing), CentOS, Windows 10, as well as others.
[*]**Game Development:** A laptop that can support Unreal Engine (So a Laptop that can at least fit these minimum requirements, if not better: [https://wiki.unrealengine.com/Building_On_Linux#Prerequisites](https://wiki.unrealengine.com/Building_On_Linux#Prerequisites)) and most modern PC game titles on Steam.
[/LIST]

Other requirements: preferably 15" laptop, 64-bit processor, at least 128GB SSD, at least 500GB HDD, and at least 8GB RAM (although I'd much prefer 16GB).

My price range is fairly high for such a laptop ($2k at most). I imagine I'll need to get a laptop mostly focused on Gaming hardware ... but I definitely want to avoid laptops with graphic cards that don't support Ubuntu.

And why a Laptop as opposed to a PC? Just not enough room in my apartment for another PC, and I need something I can take with me since I'm on-the-go a lot.

---

### Post by oldrocker99 on 2015-11-11
First off, I have a ten year old Lenovo that "supports" Ubuntu. I run Ubuntu MATE on it for a nice, lightweight desktop which uses few resources but is powerful enough for me. Linux in general is a lean, mean OS. If dual-booting, install Windoes **first**. If using VM, go for it.

I'd stay away from AMD/ATI graphics; nVidia GPUs just work better with Linux, since nVidia's Linux drivers are far superior to AMD/ATI's. Given that, here's a link:
[http://www.bestreviews.guide/gaming_laptops?&network=ADWORDS_SEARCH&type=SEARCH&subtype=TEXT&origin=google&ad_id=1175387&google_params[matchtype]=e&google_params[network]=g&google_params[device]=c&google_params[creative]=58611601219&google_params[keyword]=gaming%20laptop&google_params[placement]=&google_params[adposition]=1s4&gclid=CjwKEAiA64uyBRCVmKyT2vuAjzgSJADfINB6Vl-MSJfcHPl444U3jG80ugExJhsqdAnAFVuCTzfK3xoCyU_w_wcB](http://www.bestreviews.guide/gaming_laptops?&network=ADWORDS_SEARCH&type=SEARCH&subtype=TEXT&origin=google&ad_id=1175387&google_params[matchtype]=e&google_params[network]=g&google_params[device]=c&google_params[creative]=58611601219&google_params[keyword]=gaming%20laptop&google_params[placement]=&google_params[adposition]=1s4&gclid=CjwKEAiA64uyBRCVmKyT2vuAjzgSJADfINB6Vl-MSJfcHPl444U3jG80ugExJhsqdAnAFVuCTzfK3xoCyU_w_wcB).

---

### Post by names_are_useless on 2015-11-11
Yeah I'm aware of Linux's lightweight, my bigger issue is running VMs, since this is the first personal laptop I'll be getting for myself, and I definitely want to use VMs with it.

Thankfully pretty much *every* gaming laptop comes with nVidia. However, I've read about issues with [nVidia Optimus]("https://en.wikipedia.org/wiki/Nvidia_Optimus") and Linux. But then there's [Project Bumblebee]("http://Bumblebee aims to provide support for NVIDIA Optimus laptops for GNU/Linux distributions. Using Bumblebee, you can use your NVIDIA card for rendering graphics which will be displayed using the Intel card. Bumblebee is officially supported by Ubuntu in 14.04 newer. However, all releases are supported by the Bumblebee Project community from Ubuntu version 12.04 up to 14.04.") I've read about recently, so hopefully I'll be ok.

I think I'd prefer to avoid the dual-boot route, as I'd hope to rely on Windows as little as possible. Will largely depend on whether I can get Unreal Engine working in Ubuntu without errors, if not, I'll probably need to dual-boot with Windows :/ (I don't think it'd be wise to run a dev tool over VM).

---

### Post by mastablasta on 2015-11-12
though they have AMD, the HP business class laptops might fit.

the truth is not all AMD chips are supported equal. the good part is that AMD often supports dual GPU in Linux. worth exploring...

Virtualisation as well as pentesting - needs CPU power and cores and RAM, 
gaming needs strong GPU/RAM and CPU. :)
HP Ssupport Ubuntu I mean has some certified machines:
[http://www8.hp.com/us/en/campaigns/ubuntu/index.html](http://www8.hp.com/us/en/campaigns/ubuntu/index.html)

but you can also try System76 since they have gaming laptop with Ubuntu preinstalled.

mmm... someday.... :-\"

---

### Post by MikeCyber on 2015-11-13
I use virtualbox but if you want to run 3D apps look into that:
[http://www.tomshardware.co.uk/answers/id-1776772/virtual-run-games.html](http://www.tomshardware.co.uk/answers/id-1776772/virtual-run-games.html)

---

### Post by names_are_useless on 2015-11-13
Thanks mastablasta, but considering the fact that I'm currently looking at Gaming Laptops ... ALL of them have nVidia Cards, and they ALL use Optimus. So joy, I'm definitely going to have to hope that I can get it working.

I was aware of System76 Laptops, but considering the price for the specs you're getting, they seem more expensive then they really should (and also no Windows 10, which I will want, just need to make sure I get the recovery disk for whatever laptop I buy). I've also read a review stating the hardware is not the best quality when compared to leading manufacturers like Dell, Acer or MSI (but then I should probably read some more reviews before ruling them out entirely).

Thanks for that link MikeCyber. Basically tells me that if I can't get Unreal Engine or certain other games working in Ubuntu, then I'll need to setup a dual-boot to both Ubuntu and Windows 10. All the more reason why I should probably get a machine that comes with Windows 10.

Right now the MSI GE72 Apache Pro-242 is my top pick (good value for the  specs): [http://www.xoticpc.com/msi-ge72-apache-pro242-p-8574.html](http://www.xoticpc.com/msi-ge72-apache-pro242-p-8574.html)
If anyone has an MSI Laptop and wishes to say anything about it, I'd appreciate it. I have read that mid-range Laptops like this one can have a big problem with overheating, but that might be the case with any modern gaming laptops nowadays.

---

### Post by oldfred on 2015-11-13
My notes on MSI, I try to keep notes on various systems.

 MSI-Z97/Intel's Core i7 5775C Broadwell Is Running Well On Ubuntu 15.10 Iris Pro 6200
[http://www.phoronix.com/scan.php?page=article&item=ubuntu-1510-bdw&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu-1510-bdw&num=1)
 MSI PX60 2qd 034us Haswell & Optimus libata.force=noncq for SSD hangup
[http://ubuntuforums.org/showthread.php?t=2296878](http://ubuntuforums.org/showthread.php?t=2296878)
MSI Z170A GAMING PRO motherboard
[http://www.phoronix.com/scan.php?page=article&item=msi-z170a-gaming&num=1](http://www.phoronix.com/scan.php?page=article&item=msi-z170a-gaming&num=1)
MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)
[http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387](http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387)
[http://ubuntuforums.org/showthread.php?t=2298912](http://ubuntuforums.org/showthread.php?t=2298912)

---

### Post by names_are_useless on 2015-11-24
Thanks for the links oldfred :)

I've got it down between these 2 laptops:
**[MSI GE72 Apache Pro-242]("http://www.xoticpc.com/msi-ge72-apache-pro242-p-8574.html")** or [B][Sager NP8657 (Clevo P650-RE3)]("http://www.xoticpc.com/sager-np8657-clevo-p650re3-p-8677.html")

[/B]If anyone has notes on Sager and Ubuntu compatibility, I would love to know about it.

Both have a GTX 970M... which does come with Optimus.

---

### Post by Sorawit_Kongnurat on 2015-11-26
I got a P170SM-A myself which I bought last year. I went with the GTX980m option and have never regret it one bit. Vm should work flawlessly on both of them. (Most cpu support virtualization nowaday) For gpu you should use bumblebee &#128522; I got trouble setting it up in the beginning, but now that it is working I am getting full performance on my nvidia card with constant powersaving when it is not being use. 

So down to the point of this thread. Personally I would recommend the sager model just because you can upgrade it later, and I just prefer the generic looks of Sager.

---

