---
title: "A question about Network Manager"
date: 2005-12-06
forum: Desktop Environments
---

### Post by mrmcctt on 2005-12-06
I have installed Network Manager for my WiFi connection.  

I have gDesklets installed and one of the side candy applets I have checks my gmail account.  This fails on initial start up because the WiFi connection is not up yet.

I have set the 'nm-applet' to run at start with an order of 10 and gDesklets to run at start with an order of 150.  Network Manager keeps prompting me for a 'keyring password' on every boot.

I guess an answer to one of these two questions would help:

     1.  Is there a way to 'automate' the keyring password window so I don't have to type it in every session?
     2.  How can I get gDesklets to start later (what is the max number I can use in the 'order' field) so that I may have wireless connected before gDesklets starts?

On a lighter side, I wish I had heard of Network Manager sooner.  This beats wifi radar hands down, in my opinion.  Hopefully the rumors(?) I've seen on the boards are true and Network Manager make it into Dapper.

---

### Post by mrmcctt on 2005-12-06
> 1. Is there a way to 'automate' the keyring password window so I don't have to type it in every session?

I have attached a screenshot of the "Request for Keyring Password" message that I get at boot.  I don't want to create a security problem so if getting rid of this message means unlocking something that shouldn't be, then I'll live with it.

Thanks

---

### Post by vtec on 2005-12-06
Does your system also pasue at bootup while trying to bring up the network and conect to a time server?

---

### Post by mrmcctt on 2005-12-06
Yes it does.  I still 'Ctrl-c' through that.

I thought that was normal until I built my daughter a system and dual booted Win2K and Breezy.  She has a Linksys Wireless PCI card (can't remember model offhand) that will automatically connect to the router on boot.  Also, her machine does not pause for the 'Configuring network devices' and she has no wired connection.  My wireless device in my laptop is of the Atheros chipset.

I have no idea of a fix for this.  Not really broken in my opinion, just an annoyance.

As an update, I tried gnome-keyring-manager to see if I could automate the keyring password requirement.  I'm still working on it but it doesn't look hopeful.

---

### Post by vtec on 2005-12-06
I tired to turn off the boot process of connecting to the ntp server. I used BUM, which i seemingly don't fully understand becuase sometimes its tries to connect and other times it got right though. Not sure what is causing the differances. I would like to disable that gnome keyring thing though. Just let network manager do its thing as soon as it comes up.

---

