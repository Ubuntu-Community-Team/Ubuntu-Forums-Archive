---
title: "Three Questions"
date: 2009-03-25
forum: General Help
---

### Post by GForsythe on 2009-03-25
Hello. I have just installed Ubuntu on my laptop and have three general questions:

1.) I tried to download the linux drivers for my printer, an HP Deskject 930c.  However, the file will not open/run, and I can not get Linux to read my printer.  How can I resolve this issue so that I can print from Linux?

2.)  Because I am blind, I am heavily reliant upon DOS and do a lot of work on my other computers in Word Perfect 5.1.  I would like to know if there is a way to save Open Office files as WP5.1 files, so that I can access them once edited in Linux on my DOS machines.

3.)  I would like some recommendations for free and simple scanning software for Linux.  As I mentioned above, my blindness makes a lot of software unfit for my use.  Does anybody know any scanning software that works well with Orca?  And more specifically, because I scan a lot of articles, is there scanning software out there that is good at recognizing columns?

Thank you very much

---

### Post by boof1988 on 2009-03-25
> **GForsythe said:**
> 1.) I tried to download the linux drivers for my printer, an HP Deskject 930c.  However, the file will not open/run, and I can not get Linux to read my printer.  How can I resolve this issue so that I can print from Linux?

If the printer is not suported by the default-installed drivers (hplip).  Then one option is to download and install the latest hplip drivers, as outlined below, if the latest drivers will support you printer.

I think I can help a little with the printer drivers...

I recommend downloading the hplip drivers at the link below since I don't know which drivers you are trying to use.  Also I have used these drivers and installation method and they seems to work pretty well.

[LIST=1]
[*]Download the drivers by using the "Download HPLIP" button on the [hplip installation page](http://hplipopensource.com/hplip-web/install/install/index.html).  Or click [here](http://prdownloads.sourceforge.net/hplip/hplip-3.9.2.run) for direct download.

[*]Use the instructions on the [hplip installation page](http://hplipopensource.com/hplip-web/install/install/index.html) to install the drivers automatically.  Or (to start the installer) just "change directory" into the directory which the hplip-3.9.2.run has been downloaded and run, in terminal:
```
sh hplip-3.9.2.run
```
[/LIST]

The previous is an automatic installer method that I find pretty useful.  It walk you through the installation process.  If it wont work for you, please post back and we can try to figure out any other options.

---

### Post by rjl6591 on 2009-03-25
It's nearly always better to install from the Ubuntu package when one is available. 

sudo apt-get install hplip

---

### Post by kanikilu on 2009-03-25
Both OpenOffice Writer and Abiword say they can import WordPerfect files, but I'm not sure what version and I can't really test it since I don't have it.

Also, neither of them seem to be able to "save as" or export to WordPerfect, at least not by default. There may be available filters out there that I'm not aware of, though.

---

