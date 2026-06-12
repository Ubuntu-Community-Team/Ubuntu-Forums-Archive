---
title: "Brother MFC3820CN Printer"
date: 2005-11-24
forum: Desktop Environments
---

### Post by bigken on 2005-11-24
Hi can anyone help new to Ubuntu I'm unable to install my printer (brother mfc3820cn) any help would be greatly appreciated :confused:

---

### Post by bonzodog on 2005-11-24
can you take us through what you have done so far to install the printer?
Is it usb?
go to system > administration> printing, and add a new printer. It will ask you it's model and make from drop down menus.

---

### Post by bigken on 2005-11-24
Hi I'm trying to set printer up on a network it works fine with winxp 
its not listed in the borther printers I have also downloaded deb and rpm 
files from brother linux site but dont have a clue what to do with them 
I will try usb

---

### Post by bigken on 2005-11-24
ok tried usb and it and show as detected printer mfc3820cn I have tried every brother driver in the drop down menu no joy what I want to do is set it up as network printer attached to a wireless router it works great on on 1 tower and 3 laptops wireless runing xp the machine im trying to set up is a dell inspiron 9200 every thing else runs great even alps touchpad

Got printer to print on usb at last but still need to know how to setup as a network printer it has a static ip of 192.168.001.007:confused:

---

### Post by bigken on 2006-01-20
Hi all got printer to work on network using this guide 
[http://www.ubuntuforums.org/showthread.php?t=105703&highlight=network+printer]("http://www.ubuntuforums.org/showthread.php?t=105703&highlight=network+printer")

with drivers from Brother 

**[cupswrappermfc3820cn_1.0.0-2_i386.deb]("http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html")**
**[mfc3820cnlpr-1.0.4-1.i386.deb]("http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html")** 

set up as UNIX printer (lpd)
Description: MFC3820CN
host 192.168.1.9
queue BRN_463041
one very happy ubuntu user :D 

thx to  BobSongs

---

### Post by murderface on 2006-11-27
BigKen,

It looks like you might have solved your problem, but I'm posting this for others with the same problem. 

Brother now has a page specifically for setting up their printers in Ubuntu.

[http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#60]("http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#60")

Follow their directions. One place I got stuck is where they say "for networked printers, go to the cups web interface and change the device url to lpd://xx.xx.xx.xx/binary_p1"

The only problem with that is that they make you go through a bunch of other steps before you can change the device URL. 

Once you get to the Cups web interface:

1st, pick "printers" and you should see the printer you just installed from the command line, then click on "continue"

2nd, pick "modify printer", then click on "continue"

3rd, click on "continue"

4th, pick "lpd/lpr host or printer" as the device and click "continue"

5th, substitute your device URL, it should be something like "lpd://xx.xx.xx.xx/binary_p1" where xx.xx.xx.xx is the IP address of your printer and click "continue"

6th (this is where i got stuck, the mfc3820cn will not show up in the list), click on "browse" where it says "provide a .ppd file" and locate the ppd file you used while installing the printer. It should be in  "/usr/share/cups/model". For the mfc3820cn, the filename is "brmfc3820cn_cups.ppd". Then hit "modify printer" and you're done.

---

