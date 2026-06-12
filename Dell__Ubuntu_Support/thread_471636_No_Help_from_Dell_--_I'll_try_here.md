---
title: "No Help from Dell -- I'll try here"
date: 2007-06-12
forum: Dell  Ubuntu Support
---

### Post by HotShotDJ on 2007-06-12
According to [Dell's Linux Wiki]("http://linux.dell.com/wiki/index.php/Wiki_Main_Page"), the drivers for the [Conexant modem]("http://linux.dell.com/wiki/index.php/Clients/Products/Inspiron_1505n") that is shipped with the E1505n is available at [ the support page]("http://support.dell.com").  It is not there.  Live chat assistance tells me that Dell sells NO systems pre-installed with Linux.  I ask about the Ubuntu systems that they are currently shipping, they tell me that no such systems are sold by Dell.

I am looking for the file [ hsfmodem_7.60.00.06oem_i386.deb]("http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Add-on_Packages").  It is not where the Wiki says it is supposed to be, and as I've said, tech support will not even acknowledge that Dell sells Ubuntu systems.

---

### Post by carcioni on 2007-06-12
There is a bit of info on the Dell site, but the package you are looking for doesn't seem to exist.
Gotta love Dell support. Someone needs to update their support scripts so the CSR's have a bit of a clue.

[http://linux.dell.com](http://linux.dell.com)


Haven't tried this site, but they say they have Linux drivers for Conexant.

[http://www.linuxant.com/drivers/hsf/downloads-installer.php](http://www.linuxant.com/drivers/hsf/downloads-installer.php)

Cheers
C

---

### Post by Lord Illidan on 2007-06-12
> **HotShotDJ said:**
> According to [Dell's Linux Wiki]("http://linux.dell.com/wiki/index.php/Wiki_Main_Page"), the drivers for the [Conexant modem]("http://linux.dell.com/wiki/index.php/Clients/Products/Inspiron_1505n") that is shipped with the E1505n is available at [ the support page]("http://support.dell.com").  It is not there.  Live chat assistance tells me that Dell sells NO systems pre-installed with Linux.  I ask about the Ubuntu systems that they are currently shipping, they tell me that no such systems are sold by Dell.

I am looking for the file [ hsfmodem_7.60.00.06oem_i386.deb]("http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Add-on_Packages").  It is not where the Wiki says it is supposed to be, and as I've said, tech support will not even acknowledge that Dell sells Ubuntu systems.
This is fishy..how can the tech support not possibly know what their own company is doing?

---

### Post by timcredible on 2007-06-12
just as something to think about, internal modems + linux = difficult.  i know it sounds like a pain with a notebook, but if you can live with it, use an external modem, because they all work with zero effort.  fwiw, if you have wireless broadband available, that works really easy too (except that you have to activate the stupid card in windows 1 time before using it with linux).

---

### Post by HotShotDJ on 2007-06-12
> **carcioni said:**
> Haven't tried this site, but they say they have Linux drivers for Conexant.
[http://www.linuxant.com/drivers/hsf/downloads-installer.php](http://www.linuxant.com/drivers/hsf/downloads-installer.php)
Yes... that is the site for the drivers.  The download only works at 14.4 Kbps and no fax.  My backup dial-up carrier laughs and hangs up (not literally, of course).  I can connect perfectly with my desktop system with an external serial modem.  One has to pay a $20 licensing fee to get full functionality.  Of course, Conexant (and Dell) provide the Windows drivers as a free download -- for anybody, no matter WHAT OS came pre-installed.  Dell is shipping this driver with the E1505n -- I presume the fully functioning version of the driver.  What will happen if somebody who purchased an E1505n needs to do a complete reinstall?  Will tech support tell them that their computer doesn't exist?

---

### Post by camarojones on 2007-06-12
> **Lord Illidan said:**
> This is fishy..how can the tech support not possibly know what their own company is doing?

For one...the Linux part of Dell is supported by Canonical. the regular...ie normal...Dell associates are not trained to support Ubuntu.

However, the Wiki site: [http://linux.dell.com/wiki/index.php/Ubuntu_7.04](http://linux.dell.com/wiki/index.php/Ubuntu_7.04) does supportthem, and the Dell/Linux support number for hardware is 866.622.1947. Otherwise they tell you to go here.

---

### Post by HotShotDJ on 2007-06-12
> **timcredible said:**
> just as something to think about, internal modems + linux = difficult. Not really.  Internal modems with no Linux drivers are difficult (impossible!) under Linux.  That is not the case here.  I've already tested my internal modem with the free crippled driver from Linuxant, and it works perfectly (although missing functionality that is available with the full driver).  What I want (and what Dell said they would provide -- see the wiki I linked to in my OP) is the fully functional driver.

---

### Post by HotShotDJ on 2007-06-12
> **camarojones said:**
>  and the Dell/Linux support number for hardware is 866.622.1947
Just got off the phone with the Linux people at Dell  using that number.  What a breath of fresh air to be talking to somebody that didn't keep saying "we don't support Linux" -- As per that call, the drivers are packaged and ready but there is some "paperwork" (regarding the third-party license, no doubt, although he didn't say specifically) that needs to be done before it can be publicly released.  He said 1 - 2 weeks.  Lets hope! :)

---

### Post by phr0ze on 2007-06-12
> **Lord Illidan said:**
> This is fishy..how can the tech support not possibly know what their own company is doing?

It's a help desk. Helpdesks can barely a take a message let alone know something about a new development. If you don't ask your question the exact way the question is listed in their database, they can't give you the answer. I find this is true of most helpdesks. The true techs are a couple of layers deep.

---

### Post by srt4play on 2007-06-12
> **HotShotDJ said:**
> What will happen if somebody who purchased an E1505n needs to do a complete reinstall?  Will tech support tell them that their computer doesn't exist?

If you use the Dell system recovery tool then you don't need to hunt down drivers because it restores the machine to factory.

---

### Post by rivasdiaz on 2007-06-28
The package you are looking for is inside the "OS" partition in the default install. Assuming you have mounted the OS partition in /media/OS, the file is in "/media/OS/debs/x9014".

---

### Post by TRGarner on 2008-02-06
I downloaded the drivers, still having issues with the internal modem.  Have seen where some people are able to get it working, I haven't got there yet but it has been a while since i used linux.  Just getting back to using a real OS after a LONG ugly fight with windows.   
Any helpful hints on getting this thing working right would great.  Currently running 7.04 on a Optiplex 270.

---

### Post by faulkes on 2008-02-06
> **TRGarner said:**
>  
Any helpful hints on getting this thing working right would great.  Currently running 7.04 on a Optiplex 270.

It has been quite some time since I actually installed the winmodem on my dell laptop.  What I do remember was that it kept wanting to grab an irq that was already assigned (iirc sound) - so that is the first thing I would check, especially if it's a desktop model, that the driver itself selects or has a free irq (despite all the pnp, etc..).  You can usually do something like that via the bios of the system.

I had quite a time getting it to work (and the sound issues really bothered me) but afterwards, I was able to use dialup at proper speeds.

As you set it up and encounter issues, post them back to the thread.  We'll help as best we can.

Faulkes

---

### Post by sr20ve on 2008-02-06
> **camarojones said:**
> For one...the Linux part of Dell is supported by Canonical. the regular...ie normal...Dell associates are not trained to support Ubuntu.

However, the Wiki site: [http://linux.dell.com/wiki/index.php/Ubuntu_7.04](http://linux.dell.com/wiki/index.php/Ubuntu_7.04) does supportthem, and the Dell/Linux support number for hardware is 866.622.1947. Otherwise they tell you to go here.

I work on the enterprise side of Dell tech support and I support all kinds of linux and vmware.

---

