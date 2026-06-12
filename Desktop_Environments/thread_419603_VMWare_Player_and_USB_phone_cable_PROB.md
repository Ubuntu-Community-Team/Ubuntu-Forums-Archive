---
title: "VMWare Player and USB phone cable PROB"
date: 2007-04-23
forum: Desktop Environments
---

### Post by peabee on 2007-04-23
Good morning, 
Please bear with me whilst I try to give all the required information :)

I have Feisty Fawn on my laptop - hooray, 
I have VMWare Player (the version installed by the FF Synaptic Package manager) - hooray
The guest OS is XP Home with SP2 - sort of hooray

I have a K750 unlock cable connected to a Sony Ericsson W810i. 

Now, if I plug my printer (HP) into the laptop and then fire up the VMWare Player, it's detected in 'XP' and I can click the button at the top of the player to install the software - all is well. 

However, if I plug in the USB cable...no button appears at the top of the Player and I am unable to install the XP drivers....can't unlock phone....pants...help. 

I don't want to have to start all over again and dual boot.  

Is this because, perhaps, Ubuntu can't detect the cable?  How would I check whether it's found something plugged into the USB.  I know it's an issue with the cable as the USB mouse and printer seem to work pretty well :)

Any help would be appreciated as I have a few phoes to unlock and don't fancy sitting in the loft for ages with the slooooooooow XP laptop :)

Thanks
P

---

### Post by beerorkid on 2007-04-23
looks like player only allows 2 USB connections.  Not sure if you could get more by using a hub?

from [here]("http://www.vmware.com/community/thread.jspa?messageID=585184&#585184")
> 1. Only TWO usb 1.1 ports are available in the VM. So, once you have two usb devices hooked up, you can't connect any more.

2. Your .vmx file should contain these lines:
usb.present = "TRUE"
usb.generic.autoconnect = "TRUE"

3. You must eject (don't know the equivalent Vista command) the usb device from the Host prior to launching the guest OS. Once inside the guest, and no more than 1 other usb device is hooked up, clicking on the connect button should connect it. 

lots of USB info [here]("http://www.vmware.com/support/ws45/doc/devices_usb_ws.html")

---

