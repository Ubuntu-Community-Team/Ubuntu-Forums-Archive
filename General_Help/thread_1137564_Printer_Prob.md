---
title: "Printer Prob"
date: 2009-04-25
forum: General Help
---

### Post by MNGS on 2009-04-25
Hi folks,

Just installed 9.04 yesterday morning and *I love it*...but it's not finding a driver for my printer.

Brother MFC-3240C.

I find [http://solutions.brother.com/linux/en_us/download_prn.html#MFC-3240C](http://solutions.brother.com/linux/en_us/download_prn.html#MFC-3240C)
but they are .rpm files and the printer setup function seems to want a PPD file. ???

Please understand that I don't know command line or understand the peculiarities of all that's going on here. You'll have to use small words and explain exactly what I need to do. And I'll be so grateful.

Thank you so much!

---

### Post by HermanAB on 2009-04-25
Honestly, the easiest way to get that printer to work is to hook it to a Windows machine as a print server.  Otherwise, sell it on Ebay and buy a HP printer.

---

### Post by sstakes1 on 2009-04-25
I do not have personal experience with that model. I use another model of Brother.  But I did notice that Brother provides .deb files. Have you tried using those to install the printer drivers and get it to work? The install instructions are also available on the site.

---

### Post by skippymo on 2009-04-25
i use the cups driver on my mfc-3360c and works awesome, search synapic package manager for brother and use the cups, if it is a IP printer than use (inside printer properties) the ldp settings and put the IP in there example:    lpd://172.16.0.3/IP   make sure the /IP is there, took me a while and pulled most of my hair out for that part, should work for you

hope this helps.

---

### Post by Noel96 on 2009-04-25
> **MNGS said:**
> 
Brother MFC-3240C.

I find [http://solutions.brother.com/linux/en_us/download_prn.html#MFC-3240C](http://solutions.brother.com/linux/en_us/download_prn.html#MFC-3240C)
but they are .rpm files and the printer setup function seems to want a PPD file. ???

At the above URL, there are also DEB files. These should be compatible with Ubuntu since Ubuntu is a Debian-based system. I'd download them. Then double click on them and see what happens. It's likely that the PPD file you want is part of the DEB installation. I'm not sure what the LPR file is about but the CUPS wrapper is probably the one you want.

---

### Post by plucky on 2009-04-26
> **MNGS said:**
> Hi folks,

Just installed 9.04 yesterday morning and *I love it*...but it's not finding a driver for my printer.

Brother MFC-3240C.

I find [http://solutions.brother.com/linux/en_us/download_prn.html#MFC-3240C](http://solutions.brother.com/linux/en_us/download_prn.html#MFC-3240C)
but they are .rpm files and the printer setup function seems to want a PPD file. ???

Please understand that I don't know command line or understand the peculiarities of all that's going on here. You'll have to use small words and explain exactly what I need to do. And I'll be so grateful.

Thank you so much!

Open Synaptic Package manager and search for MFC-3240C and you should find ```
brother-cups-wrapper-extra
brother-lpr-drivers-extra
```

Mark both for installation and Apply.

Connect and turn on printer,then open **System > Administration > Printing** and add new printer.

Thats all there is to it

Good Luck

---

