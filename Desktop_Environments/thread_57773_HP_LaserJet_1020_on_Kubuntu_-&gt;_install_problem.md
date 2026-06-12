---
title: "HP LaserJet 1020 on Kubuntu -&gt; install problem"
date: 2005-08-17
forum: Desktop Environments
---

### Post by vedro on 2005-08-17
ellow

I have purchased a HP LaserJet 1020 (mum needs for her small business :P) and now I want it to install on my laptop Thinkpad R40 on which I run Kubuntu 5.04.
Now the thing is that I`m well known with some issues with some printers and Linux. However I have found out here: [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1020](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1020) , that this printer will work with Linux with those drivers: [http://support.ideainformatica.com/hplj1020/](http://support.ideainformatica.com/hplj1020/). Now, the instructions are very clear. But I have a problem. Everything is going fine untill this command in the installation procedure: make install-hotplug --> I get this message in the terminal:

root@zeko:/home/vedro/Downloads/foo2zjs # make install-hotplug
[ -d /etc/hotplug/usb ] || install -d -m 755 /etc/hotplug/usb/
install -c -m 755 hplj1000 /etc/hotplug/usb/
ln -sf /etc/hotplug/usb/hplj1000 /etc/hotplug/usb/hplj1005
ln -sf /etc/hotplug/usb/hplj1000 /etc/hotplug/usb/hplj1020
/etc/hotplug/usb/hplj1000 install-usermap
/etc/hotplug/usb.usermap: No such file or directory
make: *** [install-hotplug] Error 2
root@zeko:/home/vedro/Downloads/foo2zjs #             

Now I can read I know what the problem is: I seem to be missing the usb.usermap file. But in the /etc/hotplug/ directory are some other usb related files: usb.agent usb.handmap usb.rc 

So, how can I get the usb.usermap file? 

Here: [http://www.wlug.org.nz/HotPlugNotes](http://www.wlug.org.nz/HotPlugNotes) is a related topic and I saw in the usb.usermap are hardware signatures. Something like this can be found also at this page: [http://support.ideainformatica.com/hplj1020/](http://support.ideainformatica.com/hplj1020/) under that link: [http://support.ideainformatica.com/hplj1020/hplj.usermap](http://support.ideainformatica.com/hplj1020/hplj.usermap)
There are some similarities but I`m not sure if this is the same thing...?  :???: 

So, the usb.usermap can be created manualy or it has to be done by the system?
Or is there somethnig that I have forgotten on? I have read the instructions on those pages carefully and I`m at a dead end  :???:  ](*,)  

Please help me, becasue is very important for my mum that the printer will work by sometime tomorow... She is opening her firm (pediatric ambulant) and she needs to print allot of documents.. and she wont be happy if the printer wont work. So I am almoust begging for your help...  ](*,) 

have a nice day, 
vedro

---

### Post by jobli on 2005-08-20
Hi!

Try this. It worked for me:

ln -s /usr/share/doc/hotplug/examples/usb.usermap /etc/hotplug/usb.usermap

---

### Post by Pointwood on 2005-08-20
I would like to hear if you got it working?

I have the same printer but I borked my installation by trying to get it to work :(

I would like to get my printer working though :)

---

### Post by Pointwood on 2005-08-22
Okay, I couldn't resist, I tried again and I didn't totally destroy my system which I consider a vast improvement over last time :D

Anyway, the printer seems to be okay:

> ~/downloads/foo2zjs# usb_printerid /dev/usb/lp0
GET_DEVICE_ID string:
MFG:Hewlett-Packard;MDL:HP LaserJet 1020;CMD:ACL;CLS:PRINTER;DES:HP LaserJet 1020;FWVER:20041129;

Furthermore I got this 
> [http://milliways:631/printers/LaserJet_1020](http://milliways:631/printers/LaserJet_1020)
   Description: HP LaserJet 1020 foo2zjs
 Location: Local
 Printer State: processing, accepting jobs. 
"Sending print file, 14542 bytes..." 
Device URI: usb://HP/LaserJet%201020

So, it seems to accept the printer jobs I send, but it never seems to arrive at the printer - I haven't gotten it to print a single page :(

Any suggestions?

---

### Post by vedro on 2005-08-23
Ellow

Hmmm.. it seems that all of my procedures were correct but the LaserJet 1020 and ThinkPad R40 (and maybe other Centrino I based platforms Laptop) are not compatible. I have Installed the same printer on my desktop machine (P4) on Kubuntu and Win 2003 (dual boot) and the printer worked without any problems. Printer worked fine even when I have installed it on my girlfriends desktop PC, 2 of fiend PC`s. But on the laptop I could die trying. I have Win XP on the R40 an the printer wont work even there. Drivers install sucessfuly but you are not able to print anything.. It seems that there are some issues with the data transfer over USB controler, main chipset on the Centrino platform and this printer...

Pointwood, maybe you have the same issue... So maybe the USB 2.0 chipsets are the problem. What is your configuration

tenx for all the help,
vedro

---

### Post by Pointwood on 2005-08-23
Hmm...this is an older desktop PC with a Via chipset, this one specifically: 
[http://usa.asus.com/products/mb/socketa/a7v333/overview.htm](http://usa.asus.com/products/mb/socketa/a7v333/overview.htm)

It uses the VIA KT333 chipset.

You are right though, that might be the reason.

The printer sometimes seem to loose the firmware. By that I mean that when I run the command 'usb_printerid /dev/usb/lp0' the reply doesn't contain 'FWVER' as it should. I can then upload it again, run the command and get an answer that looks fine..

---

### Post by vedro on 2005-08-23
Yes, that was the problem to - you have to power off/on the printer then you have printer info back. 

Your MBO has VIA VT6202 USB2.0 controller, my laptop has an Intel USB 2.0 controler (Intel 855 chipset )... It`s puzzling  :???:  
But on my USB controler in the workstatin is a NEC chip (I havent checked at other computers where I have pluged in the printer)  Further testing will be needed to come to a reasonable conclusion. So by now we can asume that the main chipset of the PC is not the problem, but the USB 2.0 controler chip. Hmm, as I remember, NEC was the first who made the certified USB 2.0 controler chip... :???: 

have a nice day,
vedro

---

### Post by Pointwood on 2005-08-23
[QUOTE=vedro]Yes, that was the problem to - you have to power off/on the printer then you have printer info back.[/QUOTE] Well, I mean, when you have once gotten it to accept it and get the right text, it shouldn't be loosing it again, or?

[QUOTE=vedro]Your MBO has VIA VT6202 USB2.0 controller, my laptop has an Intel USB 2.0 controler (Intel 855 chipset )... It`s puzzling  :???:  
But on my USB controler in the workstatin is a NEC chip (I havent checked at other computers where I have pluged in the printer)  Further testing will be needed to come to a reasonable conclusion. So by now we can asume that the main chipset of the PC is not the problem, but the USB 2.0 controler chip. Hmm, as I remember, NEC was the first who made the certified USB 2.0 controler chip... :???: 

have a nice day,
vedro[/QUOTE] I don't know enough about this stuff to make any conclusions at all :)

---

### Post by vedro on 2005-08-23
ellow...

* Well, I mean, when you have once gotten it to accept it and get the right text, it shouldn't be loosing it again, or?* 

Actualy the printer info can get lost.. the drivers "ask" this printer for his "identity" everytime you power the printer on.

* I don't know enough about this stuff to make any conclusions at all* 

Well I had in my computer history some incopatibilty issues.. but not with such periferial as a printer is.  :-P

---

### Post by jobli on 2005-08-23
Hello again!

My printer works ok, but if I turn it off, then I have to upload the firmware manually
to make it work. At first I just could print once and then had to turn it off/on and upload the firmware to be able to print again. I then edited the hotplug script according to a (SUSE) tip at linuxprinting.org ,rebooted with the printer on, and now it works  O:) except for the on/off issue.

Tip:
Added "sleep 10" at the top.
Specified printer to "/dev/lp0"

---

### Post by Pointwood on 2005-08-23
Where exactly did you add that?

/n00b :(

EDIT: I think I added it at the right place, but I don't think it made any difference.

If I try to print something I can see it in KJobViewer where it seems to be processed, but nothing ever reaches the printer :(

---

### Post by vedro on 2005-08-24
ellow

The same by me... 

I`m still sticking to that my USB controler and the printer does not work --> because I cannot get the printer running even under Win XP...

have a nice day,
vedro

---

### Post by Pointwood on 2005-08-24
My printer works fine in Windows XP...

---

### Post by Johnp_g on 2005-11-11
Hi,

I've been looking around for help on the HP1020

I recently installed Ubuntu Breezy 5.10 (after Debian Sarge got me away from RedHat6.2.....!)

"Breezy" uses "udev" to manage hotplugging, previously with Debian Sarge I had the same problems uploading the firmware as mentioned here.

I found this thread in the wiki page relating to printer compatability, but I've just put an explanation this morning of how I got my HP1020 working in this thread :-
[http://ubuntuforums.org/showthread.php?p=483600]("http://ubuntuforums.org/showthread.php?p=483600")
so I thought I'd link it in from here.

I don't know if Hoary uses udev, so it might be necessary to upgrade to Breezy to get it to work?  As I mention in the other thread, there's a typo in the udev rule that needs to be corrected for automatic firmware upload to work.

Cheers,

John

---

### Post by JunCTionS on 2008-03-29
vedro, thanks for telling me (in your question) where to find the drivers for this printer.
it worked flawlessly with Kubuntu 7.10 (Gutsy) for a SMB shared printer.

---

