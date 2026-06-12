---
title: "USB TV Tuner"
date: 2006-03-30
forum: Desktop Environments
---

### Post by AusIV4 on 2006-03-30
Hi, I'm hoping to set up my laptop to work as a television in the near future (probably not until dapper is out). I'd like to be able to watch TV and if possible record with MythTV. I've been doing research on the subject for a large part of the day, and I keep coming up with conflicting reports as to whether or not certain cards work with Linux. So I figured I'd ask people using the distro I intend to use. (I did a search of the forums earlier, but didn't find anything more recent than Hoary).

Is there anyone out there who has any personal experience with any USB TV tuners on Ubuntu? As I've stated, I'm working with a Laptop, so PCI is not an option. I know [linuxtv.org](http://linuxtv.org/v4lwiki/index.php/USBVideo#Working_Devices) has a list of tuners that are reported to work, but I'd rather hear from somebody who has experienced it first hand. Tell me whatever you can, what card, how many hoops you had to jump through to get it to work, etc.

---

### Post by RikoW on 2006-03-31
Hi,

I have a terratec cinergy T2 which works perfectly under Ubuntu. Just plug it in, set up the channels and watch what you like. it's a DVB-T card, though. The box even has a little tux printed on it ("Yes, we support Linux"). And I support Linux supporters :)

I didn't set up mythtv, though. Looked to complicated for my purpose. I'm using xine or kaffeine (for recording especially). Search the forum for the card, there are more posts around which also will help you to set it up.

Cheers,

           Riko

---

### Post by zegnus on 2006-04-12
Hi RikoW !! , I have a Cinergy Hybrid T USB XS card and I have ubuntu 5.10, I put it and Device Manager says that it is detected, but when I use xawtv says that /dev/video0 not exist.

We have the same card ??, if not, your card is USB ??

If your card works perfect, can you say exactly what you do for this card works, for example:

Plug-in
go to terminal ant put: ls -lf /dev/video ... 
go to xine, menu, edit, ... etc etc etc..
to see any channel ??

If you can reply this, you help me a lot !

Regardss!

---

### Post by l3lackEyedAngels on 2006-04-25
RikoW,

I cannot find anything on the Terratec web site to back up your statement that you can just plug in the t2 to a computer running Ubuntu and then everything just works. What you are telling me really seems too good to be true.

I will throw down the cash and buy this mutha, and a USB 2.0 pcmcia card too, of the t2 is as good as you say! Is there anyway to convince me?

---

### Post by RikoW on 2006-04-26
Well, it worked for me as I said. Search this forum for "Terratec T2" or "Cinergy T2" for other people how had it working out of the box. 
I plugged the T2 in, which is a USB card, but most likely different than the Hybrid you mentioned above. It is however a DVB-T card not an analog card, so you can only receive digital, terrestial TV broadcasting.

What you then need to do is to scan the correct channels. I did that from the command line. See for example this thread:

[http://ubuntuforums.org/showthread.php?t=116685]("http://ubuntuforums.org/showthread.php?t=116685")

But more easily, you can install kaffeine player from the repos. Kaffeine lets you scan for channels corresponding to the region you are living in. Again, this is for digital TV only.

As I mentioned before, the T2 has a Tux printed on the cardboard box it came in.

Good luck,

              Riko

---

### Post by robinj128n on 2006-07-16
> **AusIV said:**
> Hi, I'm hoping to set up my laptop to work as a television in the near future (probably not until dapper is out). I'd like to be able to watch TV and if possible record with MythTV. I've been doing research on the subject for a large part of the day, and I keep coming up with conflicting reports as to whether or not certain cards work with Linux. So I figured I'd ask people using the distro I intend to use. (I did a search of the forums earlier, but didn't find anything more recent than Hoary).

Is there anyone out there who has any personal experience with any USB TV tuners on Ubuntu? As I've stated, I'm working with a Laptop, so PCI is not an option. I know [linuxtv.org](http://linuxtv.org/v4lwiki/index.php/USBVideo#Working_Devices) has a list of tuners that are reported to work, but I'd rather hear from somebody who has experienced it first hand. Tell me whatever you can, what card, how many hoops you had to jump through to get it to work, etc.

Purchased a Terratec Hybrid T xs USB receiver from savastore.com.  Tunes in analogue and digital terrestrial signals superbly. However, Terratec advised there is no analogue radio tuner included in the 'Cinergy Hybrid T USB XS', so it is not possible to use the FM radio function of 'Cyberlink PowerCinema software supplied'. If you want to receive radio over the dvb-t signal, use the alternative software for dvb-t receiption 'Cinergy Digital 3' which you can download free from the following link:
[http://supporten.terratec.net/modules.php?op=modload&name=Downloads&file=index&req=viewsdownload&sid=368](http://supporten.terratec.net/modules.php?op=modload&name=Downloads&file=index&req=viewsdownload&sid=368).

In addition, the feature to delete recorded files directly in the PowerCinema software is not available. However, they can be deleted using Windows explorer.

Furthermore, don't forget to plug in the break out cable which incorporates the remote’s pick up.  Remote's software is on inst disc and download the drivers etc from terratec site to ensure you have latest.

Furthermore, if you choose to link to satellite boxes for viewing/recording etc using uhf aerial coax (channels 21-69), tune them in on TV settings, signal settings, capture device - set to analog. Be sure of course that such boxes are turned on and daisy-chained before tuning (although there is no loop through on the Hybrid T).  Sterio sound and picture is great.
 
Savastore is an EXCELLANT supplier; I've spent £ks there.  Supplied this kit next day.

[http://www.savastore.com/productinfo/product.aspx?catalog_name=Savastore&product_id=10284945&pid=44&rstrat=0](http://www.savastore.com/productinfo/product.aspx?catalog_name=Savastore&product_id=10284945&pid=44&rstrat=0)

---

### Post by MungoH on 2007-07-28
I had the same situation using Feisty. I have a usb cinergy card which didn't get picked up automatically, but installing the module described here works a treat:

[http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices](http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices)

after that it gets picked up automatically and I have DVB in kaffeine etc

---

