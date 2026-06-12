---
title: "printer device"
date: 2009-06-17
forum: General Help
---

### Post by aleblanc on 2009-06-17
I am using Ubuntu 8.10.
I have a printer connected to a USB port.
I can print documents fine through the menus of various applications such firefox by selecting the ML-2010 printer (I have a Samsung ML-2010p).
I can also print via the command-line with lpr if I specify the printer:

lpr -P ML-2010 file

However, I can find no /dev/lp device, and this bothers me. 
What is the printer device called in Ubuntu?

---

### Post by Tamlynmac on 2009-06-17
You may wish to read this page and download/install the driver. The install instructions for Ubuntu are on the page.

[http://www.samsung.com/us/support/download/supportDownDetail.do?group=&type=printersmultifunction&subtype=monochromelaserprinters&model_nm=ML-2010P&language=&cate_type=all&mType=DR&dType=D&vType=&cttID=2072073&prd_ia_cd=06010400&disp_nm=ML-2010P&model_cd=&menu=download&menu2=detail](http://www.samsung.com/us/support/download/supportDownDetail.do?group=&type=printersmultifunction&subtype=monochromelaserprinters&model_nm=ML-2010P&language=&cate_type=all&mType=DR&dType=D&vType=&cttID=2072073&prd_ia_cd=06010400&disp_nm=ML-2010P&model_cd=&menu=download&menu2=detail)

Hope this help and gets you going.

---

### Post by aleblanc on 2009-06-17
I have no problems working the printer. I just want to know where the printer device is. Normally in linux it should be linked to /dev/lp right? But maybe it's different for Ubuntu?

---

### Post by Tamlynmac on 2009-06-18
I must apologize for misinterpreting your post and have no idea where the that's located. I searched for a while and even checked for "cups" & "usb".

Sorry I can't help and again for my error.

Good Luck and hopefully someone else will pick this up and have an answer. At least it getting bumped.

---

### Post by plucky on 2009-06-18
On my system the printer is /dev/usblp0 --> /dev/usb/lp0 for a usb connected printer./dev/lp0 is for a parallel port connected printer.

I think.I may be wrong.;)

---

### Post by arnoldjames on 2009-06-18
> **Tamlynmac said:**
> You may wish to read this page and download/install the driver. The install instructions for Ubuntu are on the page.

[http://www.samsung.com/us/support/download/supportDownDetail.do?group=&type=printersmultifunction&subtype=monochromelaserprinters&model_nm=ML-2010P&language=&cate_type=all&mType=DR&dType=D&vType=&cttID=2072073&prd_ia_cd=06010400&disp_nm=ML-2010P&model_cd=&menu=download&menu2=detail](http://www.samsung.com/us/support/download/supportDownDetail.do?group=&type=printersmultifunction&subtype=monochromelaserprinters&model_nm=ML-2010P&language=&cate_type=all&mType=DR&dType=D&vType=&cttID=2072073&prd_ia_cd=06010400&disp_nm=ML-2010P&model_cd=&menu=download&menu2=detail)

Hope this help and gets you going.
There are dangers with this.  The samsung installation requires you give root access to their installer and it changes permissions on many files, such that when I did it, it broke wireless internet such that I had to reinstall.  Be careful with third party packages!

---

