---
title: "help with the dell precision 410 (no sound with on board sound card)"
date: 2007-06-12
forum: Dell  Ubuntu Support
---

### Post by tommy2k7_uk on 2007-06-12
hello i wonderd if anyone can help me with getting the sound to work on the dell precision 410 i installed it ubuntu linux 7.04 last night and after i installed it i had no sound when i click on the speaker where the date and time is it says no volume control gstreamer plugins and/or devices. any one no how to fix this

---

### Post by LiquidIQ on 2007-06-13
Do you have the latest BIOS installed for the Precision 410? That might help with the sound issues since Ubuntu gets a lot of it's onboard soundcard information from the BIOS.

---

### Post by p24t on 2007-06-13
I'm not exactly sure which system you have.  I've never had luck with dell's site, but I found 2 computers, neither of which have an audio driver for linux.

If this is an old system, with like a PII or a PIII in it, then this is the audio card it has:
[http://search.dell.com/results.aspx?c=us&l=en&s=dhs&cat=sup&cs=19&k=Dell+Precision+410&qmp=12&p=1&subcat=dyd%2f3&rf=all&nk=f&sort=K&snpsd=A&ira=False&~srd=False&ipsys=False&advsrch=False&~ck=anav](http://search.dell.com/results.aspx?c=us&l=en&s=dhs&cat=sup&cs=19&k=Dell+Precision+410&qmp=12&p=1&subcat=dyd%2f3&rf=all&nk=f&sort=K&snpsd=A&ira=False&~srd=False&ipsys=False&advsrch=False&~ck=anav)

I don't think there's a linux driver for the Crystal audio 4237.  

There's a newer system that came up when I searched:
[http://www.dell.com/content/products/productdetails.aspx/xpsdt_410?c=us&l=en&s=dhs&cs=19](http://www.dell.com/content/products/productdetails.aspx/xpsdt_410?c=us&l=en&s=dhs&cs=19)

This has an X-Fi card.  I'm guessing this isn't it since you said onboard, but there's still no driver for the X-Fi that I've seen.

---

### Post by tgomas on 2007-07-19
If your system is the old one like mine you should have a CS4236B soundcard.
You can verify it with the command:

dmesg | grep isapnp

which returns following line for me:

isapnp: Card 'CS4236B'

in that case (and perhaps for any CS423x card) you should use the snd_cs4236 module for the kernel.

try to load the module

sudo modprobe snd_cs4236

and if it works you can add the module in /etc/modules by adding its name at the end of the file in order to load the module at the boot of the system.

---

