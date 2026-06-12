---
title: "HELP DAMSEL IN DISTRESS... DESPERATELY looking for usb host controller info"
date: 2009-01-30
forum: General Help
---

### Post by oliviagreyling on 2009-01-30
okay.... so I believe I may not be in the right place for my question,:oops:, yes I am blonde, and no, I am so definitly not familiar with Ubuntu, Kubuntu, Edbuntu, etc, and yes I see a pattern (explanation if someone pleases).

I was looking to find a usb host contoller for an old dell latitude ls PP01S that has a low speed usb on the motherboard. I need a host controller so I can use a 2.0 usb connector. I was searching on the internet, came across this link and thought this was a place I could find an answer.\\:D/

I have tried a few sites that claim they search and find the correct controller, but when they do, it won't install. Dell tech claims that there is no host controller available..](*,).

yeah well I am giving you a challenge.:-k 
I think you guys (and gals) can do anything.=D>

Judging from the posts on here you guys/gals ARE comic-con and  rocking genuises.:guitar: 

I am absolutley mystified by a whole world lurking beyond my reach. Is there the remote chance one of you will clue me in about the host controller?[-o< 

...and here I felt so proud that I figured THAT out...sigh.:cry:

---

### Post by fragos on 2009-01-31
You neglected to say what system you have or what device you wish to connect. If new hardware is required the repsonse would be different for a desktop than a laptop. A USB 1.0 controller will work with a USB 2.0 device a the 1.0 speed -- no new controller hardware required. The connectors for 1.0 and 2.0 are the same. You may not need to do anything but plug and go.

---

### Post by HermanAB on 2009-01-31
Hmm, there are no shortage of these things:
[http://www.usbgear.com/USB-PCI-PCMCIA.html](http://www.usbgear.com/USB-PCI-PCMCIA.html)

Cheers,

Herman

---

### Post by cmnorton on 2009-01-31
I am not swift with computer model numbers, so knowing how old this computer is and what kind of slots it has would be helpful. I am assuming it has USB and Cardbus. If your host controller -- built onto the motherboard -- is not USB V2.0, you will have a difficult time dealing with an external USB hard-drive, but may not have a hard time with a flash drive.

Years ago like a lunkhead, I purchased several PCI and Cardbus USB 2.0 adapters from big-time manufacturers, Adaptec, D-Link, hoping to get external USB hard drives to work when the motherboards had the USB 1.0/1.1 chipset. I tried this on desktop and laptop hardware. Please be advised that I could never get USB external hard drives to work with the older USB chipsets, despite putting in a new 2.0 controller. 

My advice is to get a new PC or live without the USB device. Maybe Linux drivers have gotten better, but I tried this on Linux and Windows. Back then, it was Windows 2K and early versions of XP.

---

### Post by HermanAB on 2009-01-31
Nowadays USB works pretty good and a USB adaptor is a lot cheaper than a new PC.  Just go your local electronics shop and buy one - any one - and plug it in.

Cheers,

Herman

---

### Post by cmnorton on 2009-02-01
> **HermanAB said:**
> Nowadays USB works pretty good and a USB adaptor is a lot cheaper than a new PC.  Just go your local electronics shop and buy one - any one - and plug it in.

Cheers,

Herman 

... and depending on the USB version on the motherboard, you may see a lot of delayed write errors trying to write to the USB hard-drive. When you say "these days", the USB controller on the motherboard is probably 2.0 and has been since at least 2004.

---

### Post by HermanAB on 2009-02-01
The IO devices are connected to the PCI bus.  Therefore each device is independent of the other.  You can have USB 1.0 and USB 2.0 devices in the same machine.  Whatever is on the motherboard already has no effect on the new adaptor.

So, just buy a new card and plug it in.

---

### Post by oliviagreyling on 2009-02-01
Hello ubuntu gurus, much thanks to you all for helping me out :P. To answer a few questions and clarify, I believe this is a 2000 dell (latitude LS) laptop and is running on (2003)windows XP. My computer crashed and my financial situations rivals the economy, so I am stuck with this for the moment.#-o 

When I plug the 2.O into the computer it says I need a host controller.  I was actually trying to DL itunes and transfer data from my iphone.(Now, for some strange reason I can't even complete the on line itunes DL ](*,) The DL bar is all green, but the "next" is grayed out.) I called Dell regarding the host controller, and they said I had only a 1.0 built in on the motherboard, (I don't believe it has both 1.0 and 2.0),and was also told no host controller by dell was available. 

I noticed HermanAD entered a link, which I will check out, but I am confused 8-[ ( go figure) as to if there is no download for a host controller and my only option is a "usb card"/adaptor.. and are they one and the same? I have a wifi card in, so I assume that is where it would go? There is also a smaller, about approx 1.5 inch x .25 inch narrow ""slot" next to the printer connection that I am quite unsure what its purpose is???   

I don't understand the flash drive application, I thought that was for memory?? This is a real problem if I can not get itunes on as it is the only da** way to update my da** phone. I really hate to admit my ignorance :oops: on computers, but I am probably the computer anitchrist.:frown: Still I am very interested in learning.

Which brings me to; what is all the different ubuntus stuff? Is this specifically a site for you high tech genuis types? ...oh yes, very important ;), how do I change the "old_grey_wolf" that appears to have been randomly selected to be attached to my name? I am definitely a girlie girl when it comes to girlie girl things, and take great offense to that [-(...

---

### Post by Yashiro on 2009-02-01
System Menu (top bar), Preferences, About Me.
Click the picture.

---

### Post by ieee488 on 2009-02-01
something like eBay item #360128529152 will work very well for your laptop and it is only $13

---

### Post by HermanAB on 2009-02-01
Howdy,

You need a 'PCMCIA USB 2.0 Adaptor'.  Your local high street electronics shop should have one for you.  People commonly buy those when the built-in adaptor is slow (like yours) or broken.

Here is a common one:
[http://www.bestbuy.ca/catalog/proddetail.asp?logon=&langid=EN&sku_id=0926INGFS10049745&catid=20388](http://www.bestbuy.ca/catalog/proddetail.asp?logon=&langid=EN&sku_id=0926INGFS10049745&catid=20388)
Prices vary from $15 on up.

Just get one, plug it in and power up.  Linux should detect it and make it work.  Thereafter, you will need some iPod software, which is also available, eg. GtkPod.

Cheers,

Herman

---

### Post by fragos on 2009-02-01
Just to be clear your problem is when connecting your iPhone via USB cable to your PC? You refer to download, do you mean PC to iPhone? USB 2.0 devices are supposed to be compatible with a USB 1.0 interface.

---

### Post by HermanAB on 2009-02-01
The problem is that the old USB 1.0 devices are very buggy and frequently do not work as advertised.  Hence I recommend the use of a new adaptor.

---

### Post by fragos on 2009-02-01
> **HermanAB said:**
> The problem is that the old USB 1.0 devices are very buggy and frequently do not work as advertised.  Hence I recommend the use of a new adaptor.

Some vendors like Compaq built USB before the standards were finalized and their USB only worked well with devices Compaq designed. I bought one of these Compaq PCs because USB was the future. A lesson well learned.

---

