---
title: "installing from USB and changing an ext3 to ext4"
date: 2009-04-23
forum: General Help
---

### Post by Castlef on 2009-04-23
hey I have 2 questions

First I Just downloaded the new jaunty ISO. I want to install from USB... but I don't want to install it "inside" windows. I want the USB to be basically like a disc and boot from the USB and then install normally. Will I be able to do that with the regular default desktop ISO?

Secondly.. i hae a separate home partition... it was so that I could reinstall ubuntu if I wanted without overwriting my home partition. My question is how hard would it be to have home become ext4? I am assuming I would have to copy all the files over somewhere.. make an ext4 partition.. then copy them to it?

---

### Post by HankB on 2009-04-23
> **Castlef said:**
> hey I have 2 questions

First I Just downloaded the new jaunty ISO. I want to install from USB... but I don't want to install it "inside" windows. I want the USB to be basically like a disc and boot from the USB and then install normally. Will I be able to do that with the regular default desktop ISO?
If you mean boot from USB and install to a partition on the hard drive, answer is yes (for Jaunty.)
> 
Secondly.. i hae a separate home partition... it was so that I could reinstall ubuntu if I wanted without overwriting my home partition. My question is how hard would it be to have home become ext4? I am assuming I would have to copy all the files over somewhere.. make an ext4 partition.. then copy them to it?
I understand you can convert ext3 to ext4 with tune2fs. By some accounts the benefit is not that great so you may consider it wiser to leave your home partition as is.

-hank

---

### Post by Paqman on 2009-04-23
> **Castlef said:**
> hey I have 2 questions

First I Just downloaded the new jaunty ISO. I want to install from USB... but I don't want to install it "inside" windows. I want the USB to be basically like a disc and boot from the USB and then install normally. Will I be able to do that with the regular default desktop ISO?


Yep, you can use the USB Startup Disk Creator, or unetbootin to create your LiveUSB. Just point them at your .iso you've downloaded.


> 
Secondly.. i hae a separate home partition... it was so that I could reinstall ubuntu if I wanted without overwriting my home partition. My question is how hard would it be to have home become ext4? I am assuming I would have to copy all the files over somewhere.. make an ext4 partition.. then copy them to it?

You could do that, or you could [convert it in place]("http://www.cyberciti.biz/tips/linux-convert-ext3-to-ext4-file-system.html"). I'd take a backup before doing that though, so the two methods are probably about equivalent in terms of time/hassle.

---

