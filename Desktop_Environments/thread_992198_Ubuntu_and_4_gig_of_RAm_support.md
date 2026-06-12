---
title: "Ubuntu and 4 gig of RAm support"
date: 2008-11-24
forum: Desktop Environments
---

### Post by mabooali on 2008-11-24
Hi,

I have installed Ubuntu 8.2.4 and I beleive that I have installed a 32 bit version. I upgraded my PC RAM to a total of 4 gig but Ubuntu only sees 3 gig!? the bios shows 4 gig and I was wondering if this is an OS issue or I need to change some settings in Ubuntu to support /read the 4 gig of RAM?

Also, MY PC is a P4, Dell Optiplex GX280 and I was wondring if I can install Ubuntu 64-bit on this PC? I couldn't find an answer to this question from the Dell website!?

Please advise,

Regards,

Masood

---

### Post by taurus on 2008-11-24
32bit version (even windows) can only read/detect up to 3.2GB even if you have more than that.  If you want to use all 4GB of RAM, install the 64bit version if your harddrive supports 64bit.

p.s.  P4 is only 32bit processor.

---

### Post by mabooali on 2008-11-24
> **taurus said:**
> 32bit version (even windows) can only read/detect up to 3.2GB even if you have more than that.  If you want to use all 4GB of RAM, install the 64bit version if your harddrive supports 64bit.

p.s.  P4 is only 32bit processor.
So, P4 is 32-bit and I cannot install Ubuntu 64-bit, correct?

I couldn't find out from Dell to see if Dell Optilex GX280 will support 64-bit OS or not. is there any test that I can perform to see if it suppoets?

Please advise,

Masood

---

### Post by wildbillkelso on 2008-11-24
Hi Masood.

I have an Optiplex GX620 with a pentium D 64 bit processor. I tried the 64 bit version of Ubuntu and it worked well but I found a lack of drivers for the peripherals I use made it not so practical at the moment as most of my equipment has no 64 bit drivers. I particularly found a distinct lack of 64 bit drivers for wireless USB for Ndiswrapper and I have to use wireless in my rented flat. I can not run cables in. I am no expert mind you but this is just my limited experience wich may help you.

Hope this may help a bit.

Best regards.

Tim

---

### Post by WhichNameShouldIUse on 2008-11-25
> **wildbillkelso said:**
> Hi Masood.

I have an Optiplex GX620 with a pentium D 64 bit processor. I tried the 64 bit version of Ubuntu and it worked well but I found a lack of drivers for the peripherals I use made it not so practical at the moment as most of my equipment has no 64 bit drivers. I particularly found a distinct lack of 64 bit drivers for wireless USB for Ndiswrapper and I have to use wireless in my rented flat. I can not run cables in. I am no expert mind you but this is just my limited experience wich may help you.

Hope this may help a bit.

Best regards.

Tim

Tim,

I'm wondering if you've had issues getting the installation you're describing to recognize the full RAM that should be available.  Mine is only seeing 3.4 GiB.  I am attempting 64bit Desktop install of 8.10 on a GX620 with 6GB of RAM.  I've searched other posts here extensively but so far have come up with nothing that solved this.

Thanks in Advance,

Michael

---

### Post by WhichNameShouldIUse on 2008-11-25
Nevermind.  Looking stupid is the price of leaping before you look.  I finally found this, unearthed by a search of Dell's support site, saying that the board will only allow addressing 4GB (though it can physically handle 8GB).  [http://support.dell.com/support/edocs/systems/opgx620/en/ug/A02/sffspecs.htm#wp1133451](http://support.dell.com/support/edocs/systems/opgx620/en/ug/A02/sffspecs.htm#wp1133451)


> **WhichNameShouldIUse said:**
> Tim,

I'm wondering if you've had issues getting the installation you're describing to recognize the full RAM that should be available.  Mine is only seeing 3.4 GiB.  I am attempting 64bit Desktop install of 8.10 on a GX620 with 6GB of RAM.  I've searched other posts here extensively but so far have come up with nothing that solved this.

Thanks in Advance,

Michael

---

### Post by wildbillkelso on 2008-11-27
Sorry for the delay in replying whichnameshouldiuse.

I had so many problems in obtaining 64 bit drivers for my peripherals, I reverted back to the 32 bit version without checking out the memory situation. I must add though everything in Ubuntu worked very well. It booted up very quickly and everything I had drivers for performed very well. I think there must be loads of 64 bit pc's out there using 32 bit because there are so many comapanies not developing 64 bit drivers for theie gear. I will buy more carefully in future.

Cheers.

Tim

---

