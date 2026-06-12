---
title: "right choice for toshiba portege r100?"
date: 2009-05-12
forum: General Help
---

### Post by simonpollo on 2009-05-12
Hi to everybody out there!

I recently bought an used toshiba portege r100 notebook (1GHz Centrino, 512 RAM, 40GB HDD, WLAN, Cardreader but NO CD or DVD drive) and want to install a Linux distribution (Ubuntu) for the first time ever because I had terrible experiences with both Vista and Mac OS.

Since the notebook lacks an optical drive and basically has the same technical "qualifications" as a normal netbook I thought Ubuntu Netbook Remix might be the best choice. 

I basically want you experts out there to tell me that I can install UNR on my notebook and that I will live a happy life as an Ubuntu user.

A couple of simple YESes will do!

Thanks a lot guys!

Cheers 

Simon

---

### Post by shel-hall on 2009-07-11
> **simonpollo said:**
> Hi to everybody out there!

I recently bought an used toshiba portege r100 notebook (1GHz Centrino, 512 RAM, 40GB HDD, WLAN, Cardreader but NO CD or DVD drive) and want to install a Linux distribution (Ubuntu) for the first time ever because I had terrible experiences with both Vista and Mac OS.

Since the notebook lacks an optical drive and basically has the same technical "qualifications" as a normal netbook I thought Ubuntu Netbook Remix might be the best choice. 

I basically want you experts out there to tell me that I can install UNR on my notebook and that I will live a happy life as an Ubuntu user.

A couple of simple YESes will do!
How about a "maybe" and a "sorta?"

Booting Ubuntu on the Portege R100 is interesting.  It doesn't boot from a USB key, though it will from a special USB floppy drive.  It won't boot Ubuntu from the PCMCIA slot using the same CD drive that one can use to install Windows.  Ubuntu seems to loose interest in the PCMCIA slot after it begins to boot, so the boot process just dies.  I've managed to get around that, but when Ubuntu 9.04 desktop finally boots by this method, the display is scrambled.

I've PXE-booted mine, as well.  The video isn't scrambled, but uses only part of the screen.

I haven't gotten far enough along to tell you if Ubuntu supports the rest of the hardware.

UNR may be different; so far I've only tried Desktop.

FWIW, WinXP runs pretty well on the R100.  Once you install the drivers from Toshiba's website, that is.

-Shel

---

### Post by shel-hall on 2009-09-16
Just for completeness ...

To boot Ubuntu on the Toshiba Portege R100, make a boot image on both a CF card in a CF-to-PCMCIA adapter and a USB key.  Put them both into the machine in the normal way, and boot from the PCMCIA slot.  The boot process will start from the CF card, then continue from the USB key.

Once installed, you won't have very good video, so use the solution found at [http://electronicrandomness.blogspot.com/2008/02/toshiba-portege-r100-upgrade-and.html](http://electronicrandomness.blogspot.com/2008/02/toshiba-portege-r100-upgrade-and.html).

-Shel

---

### Post by knave on 2009-09-26
You saved my life shel.  I actually ended up selling my first r100 because I wiped the XP installation and couldn't figure out a way to install an OS.  Floppy + CD ROM didn't work.

Fast forward a year and I spied a cheap R100 with a busted keyboard.  Replaced it and went down the wubi route.  2 days ago I used your method to ditch Windows for good and it worked perfectly (Xubuntu here).  It didn't use the USB drive though, just the CF.  Beautiful. I am sooooo stoked with this!  

Now I know that it's possible I'm going to research a reasonably priced SSD (unlikely) or get an adapter to install onto a CF.  

Oh yes.

THANKS!

---

### Post by shel-hall on 2009-11-03
> **knave said:**
> You saved my life shel.
Well, maybe I spared you a little trouble, and maybe you saved a few bucks ...

> Now I know that it's possible I'm going to research a reasonably priced SSD (unlikely) or get an adapter to install onto a CF.
There are some very inexpensive CF+adaptor combinations available on eBay (US), sourced from Hong Kong, that will fit the R100 and effectively become an SSHD.  I have one, but I have only used it for a brief test, so I can't testify to its speed, longevity, or reliability.

-Shel

---

### Post by knave on 2009-11-12
Thanks Shel, I have since done this, sorta.  I successfully installed Ubuntu using an adapter, but know whe I try to boot from the CF card, I just get a blinking cursor after the Toshiba splash screen...[here's my post in another thread]("http://ubuntuforums.org/showthread.php?t=1300186")

Are you able to point to a model on ebay that worked for you?  I don't mind trial and error, but I'm New Zealand so shipping can be tortuous.  Alternatively I can try the NZ equivalent of ebay - trademe.co.nz.  I have tried with [this]("http://http://www.trademe.co.nz/Electronics-photography/iPod-MP3-accessories/Other/auction-252749197.htm") adapter.

Would [this one]("http://www.trademe.co.nz/Browse/Listing.aspx?id=252812052") be any better?  The price is higher, so maybe it's better hehe.  The pic is nearly the same though...

---

### Post by shel-hall on 2010-06-02
Did you ever get this sorted, and the R100 running?

I'm sorry I missed your posting back in November!

-Shel

---

