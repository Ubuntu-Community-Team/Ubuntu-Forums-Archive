---
title: "Dwl-520+ Wireless Mega Problemo"
date: 2005-12-21
forum: General Help
---

### Post by gd505 on 2005-12-21
Well, I am new to ubuntu and I have seen it before in action and I thought it was pretty cool. Know I have it and am having a mega problemo with my dwl-520+. It is not the dwl-g520 or the dwl-520. 

It does get detected by ubuntu but I put in all my info and wep key and all and it still doesn't work. I tried ndiswrapper and putting the inf. drives and doing the modprobe ndiswrapper and still nothing. Am I just doomed?

Is their any simple way to fix it up and going. Please help me. Oh and by the way I have heard that for many people this card just worked in a jiffy. I wish it were my case. I think it may be because I am using a european version?

ThankYou

---

### Post by futz on 2005-12-21
Here's a thread that may help - it depends on where you live which chipset is in the card: [http://www.linuxcompatible.org/Dwl-520_D-link_wireless_card_need_help_t33009.html](http://www.linuxcompatible.org/Dwl-520_D-link_wireless_card_need_help_t33009.html)

I've not had much luck with the Gnome GUI wireless setup. I usually end up manually editing the config file for the wireless card myself to get em working. (The Gigabyte freebie card in this Ubuntu box I'm using has been the exception - it worked right off the bat.)

Oh ya, if you can, disable WEP while testing. It's just one more variable that you can do without at this stage. Once the card is working, be sure to secure your network again.

---

### Post by psoleko on 2005-12-21
FYI when doing the ndiswrapper deal, you have to blacklist the driver for the card that the kernel would load. I've had this problem before with the same card.

---

