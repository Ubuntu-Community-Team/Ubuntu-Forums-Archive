---
title: "Dial-up on Dell e1505"
date: 2007-07-05
forum: Dell  Ubuntu Support
---

### Post by kcamerud on 2007-07-05
I'm losing my eyesight poking through forums on how to get dial-up to work on Dell laptops!  I have the new Dell e1505 laptop but because I'm temporarily at a dial-up connection, I cannot connect to the internet.  I'm writing this using my old dell 5150/windows connection.  Can anyone help me get dial-up to work on my "new" laptop?

Kurt

---

### Post by Uber Schwarz on 2007-07-05
Best thing to do is to get a serial port modem and if your laptop doesn't have a serial port then get a USB to serial port convertor. Serial Port Modems work straight out of the box on Linux.

---

### Post by neptho on 2007-07-05
Who is your provider?  If you are AOL, you may be out of luck.  Otherwise, you may need to call your ISP and ask them for your username and password.

Using [GNOME PPP](http://www.eskimo.com/support/Gnome-PPP.html) will likely be the easiest way; just change the settings in the above screenshots to the ones that your ISP gives you.

You may need to run:
 ```
%sudo apt-get install gnome-ppp
``` if it is not already installed.

---

### Post by Bartender on 2007-07-06
Does the 1505 have a serial port??

---

### Post by neptho on 2007-07-06
> **Bartender said:**
> Does the 1505 have a serial port??

Nothing seems to, anymore, and if it is the Ubuntu release offered by Dell, it has a modem internal - as well as the LinuxAnt drivers.

---

### Post by Uber Schwarz on 2007-07-06
So it has a dialup modem? Does it work right away or must download some drivers?

---

### Post by neptho on 2007-07-06
> **Uber Schwarz said:**
> So it has a dialup modem? Does it work right away or must download some drivers?

As noted above, the Dell E1505N with Ubuntu preinstalled does have working drivers; the machine needs to be properly setup to use PPP, though.

---

### Post by kcamerud on 2007-07-06
sudo apt-get install gnome-ppp gets me a "couldn't find package gnome-ppp".  However, when I drop-down the network icon along the top of the page, and click on Dial Up Connection, I have two choices:  1.  Connect to ppp0 via modem 2. Disconnect from ppp0 via Modem.  When I click #1 or #2, nothing seems to happen.  It seems something needs to be set up somewhere, I just don't know where.

---

### Post by David Ostrom on 2007-07-06
You need an internet connection to download the package. you can download the dialer onto your windows computer [http://packages.debian.org/unstable/net/gnome-ppp](http://packages.debian.org/unstable/net/gnome-ppp) save it to a disk or thumb drive and install, enter isp phone number, your user name and your password. Hope this helps.

---

### Post by Bartender on 2007-07-06
Hi, David -
I've been talking to myself on this thread 
[http://ubuntuforums.org/showthread.php?t=480717&highlight=dial-up](http://ubuntuforums.org/showthread.php?t=480717&highlight=dial-up)

Shouldn't the OP download the Ubuntu Feisty package (post #2) instead of a generic debian package?

EDIT:  Also, to the OP - you might want to sign up at the Dell Forums.  They have a Linux section now and I think you're likely to get a direct answer as to whether you need more downloads.  I'd asked on the Dell Forum about dial-up and was told that drivers for the laptop modem would be available soon.  That was a couple of weeks ago.

---

### Post by Uber Schwarz on 2007-07-06
I see their laptop also comes with a wireless card so I assume it works right out of the box too?

---

### Post by David Ostrom on 2007-07-07
Hi Bartender,
I had a problem with my dial-up connection after an update manager. Had to boot into win/XP:( and download the package and all has been fine. Like your avatar suggest, stick a screwdriver in it and see if it works, that's Linux.:D

---

### Post by Bartender on 2007-07-07
> **Uber Schwarz said:**
> I see their laptop also comes with a wireless card so I assume it works right out of the box too?

I'm not sure.  The OP didn't say if he bought one of the new Dellbuntu's or not.  The Dellbuntu wireless should definitely "just work".  They put an Intel wireless card in it.  I'm not sure whether a Windows 1505 has an Intel card or some cheaper alternative like Broadcom.  Broadcom being synonymous with "trouble".

---

### Post by kcamerud on 2007-07-07
Thanks for your time and efforts.  I've used windows too long and the CLI is difficult for me to readjust to.  I installed gnome-ppp (both varieties) and neither seems to be able to detect my modem.  I installed wvdial and it could not find my modem.  Gnome PPP shows on my applications list but I get the message "can not open modem" when I click "connect".  I'm running Feisty 7.04.  To answer another question, the E1505 does not have a serial port and in my current location, I have no way to check to see if the wireless is working.  I am, by the way, not in Korea as my id indicates, but rather in Idaho visiting family who have dial-ups.  Any more suggestions on getting my Feisty to recognize the built-in modem?

---

### Post by Bartender on 2007-07-08
k -
You've got one of the new Dells with Ubuntu pre-installed?
[http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&thread.id=10735](http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&thread.id=10735)
Looks like Dell has not been entirely cooperative with supplying drivers for what is apparently a Conexant modem.  Maybe you oughta call Dell tech support and ask them what's the holdup?
EDIT: Found a post regarding serial-to-USB adapters if you're thinking about going thru the expense and hassle of buying an external serial full-hardware modem..
[http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&thread.id=10470](http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&thread.id=10470)

---

### Post by kcamerud on 2007-07-08
Thanks for the two links.  I looked for the hsfmodem_7.60.00.06oem_i386.deb driver on google and found rather disappointing replies.  Seems no one else can find it either.  Hmm.  I thought Microsoft invented vaporware but it sounds like Dell is doing it too.  For the time that I use a dialup, I'm not interested in buying a converter cable and a serial modem.  Dell unsupport is truly a disappointment for me.

---

### Post by Mr_bleu on 2007-07-08
He doesn't state that he has the E1505N, which comes with linux.

---

### Post by Bartender on 2007-07-08
> **kcamerud said:**
> Thanks for the two links.  I looked for the hsfmodem_7.60.00.06oem_i386.deb driver on google and found rather disappointing replies.  Seems no one else can find it either.  Hmm.  I thought Microsoft invented vaporware but it sounds like Dell is doing it too.  For the time that I use a dialup, I'm not interested in buying a converter cable and a serial modem.  Dell unsupport is truly a disappointment for me.
Amen to that.  I've found there's always someone at Dell to talk to you when you want to spend money, but help/support/complaint numbers are a whole different thing.

---

