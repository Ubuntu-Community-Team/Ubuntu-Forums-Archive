---
title: "Need to clear CMOS for working video"
date: 2009-02-11
forum: General Help
---

### Post by sniperbob on 2009-02-11
Hi, I have the weirdest issue.

I have Ubuntu 8.04 installed on a media box I setup, it has an ASUS A8V-VM motherboard and a Geforce 6200 video card.

Where it's at right now, if I clear the CMOS, then boot up - my video (generally) works fine (the S-Video out on the video card doesnt seem to work 100% of the time...)

But, once I shutdown - all bets are off. The video often times doesnt work. I've reproduced the issue. Reset CMOS, boot.. looks OK (aside from that **** S-Video out that doesnt put any signal out). Reboot, no video through the POST, it only comes up once GNOME loads, at the login screen. Reboot again, no video period.

I'm in the process of downloading a new BIOS version - I doubt it will fix it but im hoping it will.

I have swapped the 6200 video card with an identical card (I had a couple laying around) so I seriously doubt it is an issue with the video card.


Any thoughts?

---

### Post by dcstar on 2009-02-12
> **sniperbob said:**
> Hi, I have the weirdest issue.

I have Ubuntu 8.04 installed on a media box I setup, it has an ASUS A8V-VM motherboard and a Geforce 6200 video card.

Where it's at right now, if I clear the CMOS, then boot up - my video (generally) works fine (the S-Video out on the video card doesnt seem to work 100% of the time...)

But, once I shutdown - all bets are off. The video often times doesnt work. I've reproduced the issue. Reset CMOS, boot.. looks OK (aside from that **** S-Video out that doesnt put any signal out). Reboot, no video through the POST, it only comes up once GNOME loads, at the login screen. Reboot again, no video period.

I'm in the process of downloading a new BIOS version - I doubt it will fix it but im hoping it will.

I have swapped the 6200 video card with an identical card (I had a couple laying around) so I seriously doubt it is an issue with the video card.


Any thoughts?

And of course you disable the internal Video card in the BIOS, don't you?

---

### Post by sniperbob on 2009-02-13
Yes, it has been disabled, and the PCIE video set as primary.

The BIOS flash doesnt seem to have fixed it at all.

Edit:

Yep.. hasn't done a thing for it. After one cold-start, the svideo died again. After another few reboots, there isnt any video on the VGA out either.

Is it possible its a BIOS/Chipset conflict? Some nasty bad mojo between the VIA chipset, the Nvidia card, and the Hauppauge card? If thats the case.. what on earth can I do?

---

