---
title: "Dell E6510 with 10.04 LTS (OEM)"
date: 2010-09-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by oxeb on 2010-09-30
Hello,

I bought a Dell Latitude E6510 with Windows 7 x64 Ultimate.  I have tried dual booting with Ubuntu 10.04.  The first problem I had was nouveau making the screen go black during any boot, including install.  I fixed this with the modeset.nouveau=0 line at boot.

Anyway, like a lot of Ubuntu users I get frequent hangs where I lose mouse and keyboard interactivity and the screen freezes.  My laptop is certified to work with 10.04 LTS (OEM) from Dell according to [http://webapps.ubuntu.com/certification/hardware/201009-6534/](http://webapps.ubuntu.com/certification/hardware/201009-6534/)

So my question is:

Is 10.04 LTS (OEM) from Dell something different from using the Dell-Recovery package in Synaptic with the 10.04 A00 ISO from [http://linux.dell.com/files/ubuntu/lucid/iso-images/](http://linux.dell.com/files/ubuntu/lucid/iso-images/) ?

Or is there some special image somewhere? I want to try this OEM image that my machine is certified with to see if it removes the freezes.  Also when I use the Dell-Recovery package with the ISO from linux.dell.com I have the nouveau problem again and I am not quite sure how to preload the proprietary nvidia drivers.  I am under the impression that a "FISH driver package" is a tar.gz of the deb, but I have never really seen that term before and google is giving me precious little information.

Thank you for any help you can provide.  I will check this thread often.

---

### Post by bri5569 on 2010-10-01
This is the netbook edition. It includes the broadcom wireless drivers, flash etc and the Dell Recovery Tool.

---

### Post by oxeb on 2010-10-01
You can't be serious?  They can't possibly intend for me to run the netbook edition on an i7 laptop with discrete graphics...

---

### Post by bri5569 on 2010-10-02
It definitely is. Your best best is to install the standard Ubuntu 10.04 LTS, Then install all your drivers, flash etc. Download the Dell Recovery Tool (it's in the Ubuntu software centre) and create a Dell recovery disk. I did this for my main computer and does save time if you ever have to re-install. I previously had the Dell remix version 8.04 and kept the Fluendo codecs and installed these as well in to the latest 10.04.

---

### Post by oxeb on 2010-10-02
Well, thank you for clearing that up for me.  I guess I will mull my options, but it seems like I will be waiting on Win7 for a while and then returning to try future releases.

---

### Post by oxeb on 2010-10-06
So I found an ISO image specifically for my laptop model with my video card, while I was reading a bug report.

[http://people.canonical.com/~jerone/special/ottawa-latitude-6510-Nvidia/](http://people.canonical.com/~jerone/special/ottawa-latitude-6510-Nvidia/)

This ISO also causes my system to hang every so often, although other than that it works perfectly, solving many problems the standard ISO caused.

I just want to say thank you, even though the image did not work, because it is really generous of you put out such a specific ISO.

---

### Post by Aitaix on 2010-10-21
have the same laptop. just wanna say thanks for the link!

---

### Post by artyom108 on 2010-10-24
It seems like the link at canonical has been taken down just in the last couple of days.  If anyone needs the ISO, I can find a way to get it to you.  

I'd also like to chime in with a "thank you", both for posting the link, and the folks at canonical for making the ISO in the first place. It made the install seamless for me .

Networking:
The only (tiny) issue was having to manually activate the hardware driver for the networking card after install (assuming you have this Broadcom card):

From the readme:
=========
Go to System->Administration->Hardware Drivers
Choose the Broadcom STA wireless driver
Activate

restart and you're off and running.


btw, so far at least, I'm really delighted with the e6510... I have 7i processor w 4G and 64 bit ubuntu screams on it.  Can wait to start doing software dev on this box : -)

---

### Post by hightowe on 2010-11-12
I would like to get a copy of this ISO, if possible... can anyone make it available?

Thanks.

---

### Post by albertzk on 2011-03-31
Dell is absolutely ate up on this one. The link at [http://www.ubuntu.com/certification/hardware/201009-6534](http://www.ubuntu.com/certification/hardware/201009-6534) QUOTES "The Dell Latiude E5510 laptop has been awarded the status of Certified on Ubuntu 64-bit PC." Then it goes on to say go to Dell to get a preconfigured ISO to load it with. After 3 hours first on chat then on the phone with someone who knew some English we were told that our laptop did not come with Ubuntu but Windowz so we were not eligible for the Ubuntu ISO image. I guess if you want a good laptop with Ubuntu or a good one period don't buy Dell next time. 
Thanks for all the good posts on this but I believe with the random hangs I am sticking with Windowz for now. :(

---

### Post by ajmctaggart on 2011-04-21
Can someone get me a copy of an ISO that utilizes all the required drivers for a Dell Lat E6510 - I will forever be grateful.

I begged and pleaded with Dell - they said the only way is to buy the machine w/ Ubuntu pre-installed.  

I then asked for their Ubuntu dept. to see if someone would lead me in the right direction to get my machine fully working on Ubuntu - they gave me the phone numbers to Alienware division and I believe a Server support hotline - wth!

So PLEASE if anyone figures out how to get the touchpad, sd card, suspend, hibernate, and decent battery life CONSISTENTLY please report back or PM me.

System 76 or back to Apple for me after this one...

---

### Post by MSBF on 2011-05-03
Hey, I am keen to get a copy of this as well. Please email me on myspot at mail-me.com or pm me.

---

