---
title: "Ubuntu without a monitor"
date: 2007-01-26
forum: Desktop Environments
---

### Post by thuleni on 2007-01-26
Here's a trick!  My monitor blew up and I have to get some important files off my Ubuntu server...

So I have managed to log on, remembering the screens and sequence of required key-strokes, however, I am now stuck on trying to get a terminal window started to restart SAMBA.

I have spent hours searching the web for hotkeys, etc. but haven't been able to find anything that tells me how to start a terminal window, apart from those helpful one's which say: Applications>Terminal>...etc.

I was hoping that someone could (a) tell me how to start a terminal session (some people have said: Ctl-Alt-F2/6, and
(b) if I could just do a "windows run command" type function.

HELP, PLEASE :confused:

---

### Post by dannyboy79 on 2007-01-26
Pressing CTRL-ALT-F1 to CTRL-ALT-F6 gives you the console command shell windows, while CTRL-ALT-F7 gives you XFree86 (the graphical interface).

i thought I also remember alt+f1 will get you a little quick command box where you can enter commands.

if you're trying to salvage stuff off the disk, why don't you take the hdd out of the computer and put it in the one that you have a monitor for. you obviously have a monitor somewhere if you're trying to get samba working. if it's a windows box, you can just run a live cd, knoppix or ubuntu, then copy important stuff from hdd from broken monitor comp to good monitor computer hdd. not sure what your goal is?

---

### Post by Sqwishy on 2007-01-26
yes pressing ctrl alt f2 - f6 will switch you to a terminal where you can log in with a username and password. then you have you're terminal!

---

### Post by thuleni on 2007-01-26
Thanks for the info.  I am on a Windows laptop now, which is connected to my network.  So I wanted Samba to restart (I must put it into the startup sequence again...).  Then i can get to the file from this laptop.

Getting the HD out of the server and connecting it to the laptop is a bit of a mission :)

---

### Post by dannyboy79 on 2007-01-26
if your server is running a ssh server, than you can download winscp for free from somewhere, I did. here, [http://winscp.net/eng/download.php](http://winscp.net/eng/download.php). it's basically a ftp program which runs thru ssh, i think. your server doesn't have a tv out on your graphics card? they make usb to ide-connections. in fact, here is the link from buy.com. [http://www.buy.com/prod/Sabrent_USB_2_0_to_IDE_SATA_Cable_for_2_5_3_5_5_25_Drive_with_Power/q/loc/101/203070728.html](http://www.buy.com/prod/Sabrent_USB_2_0_to_IDE_SATA_Cable_for_2_5_3_5_5_25_Drive_with_Power/q/loc/101/203070728.html)

actually that link is to a ide/sata to usb adapter for 2.5 & 3.5 inch ide hard drives. for 21.99 this is an invaluable product to own. I have one that a friend brought back from china, it was only $4.99 but it only had the 2.5 & 3.5 inch ide hard drives to usb adpater. anyway, good luck

---

### Post by thuleni on 2007-01-26
hohoho - I am in.  I was forgetting the extra password after "sudo ...." to do the re-start command.

a big thanks guys!!

ciao

:KS

---

