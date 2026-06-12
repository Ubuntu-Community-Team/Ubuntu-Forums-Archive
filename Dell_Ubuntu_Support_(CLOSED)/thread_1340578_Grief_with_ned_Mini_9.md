---
title: "Grief with ned Mini 9"
date: 2009-11-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Ragtop on 2009-11-28
My mini-9 came from the Dell outlet store refurb operation today with no operating system installed. The disks with the 'putr said "already installed", but when I booted the li'l critter the first time I got the Dell splash screen, instructions for setup and boot options and "No loader" with a blinking cursor.

I copied the CD files to a pen drive, but it wouldn't boot. I got the msg: "Pen drive Without Operating System. Remove pen drive and reboot.". This, of course just takes me in circles.:confused:

After reading some posts here, I have doubts about the Dell version of Ubuntu. However, the disk I got with the Mini9 is not Dell branded. It's labeled "Ubuntu 8.04 + LTS recovery media" and the copyright is to Canonical Ltd.

My plans are to get the 9.10 netbook remix, but I'd really like to have an OS up and working soon.  

Any help or suggestions greatly appreciated.):P

Thanks in advance!

BC
                                                                                                   [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]                            [[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=8403479")                                                                       [IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG]             [[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=8403479")

---

### Post by anjilslaire on 2009-11-28
Use this guide, substituting the netbook remix iso for the regular ubuntu image:
[http://www.ubuntumini.com/2009/11/user-guides-for-ubuntu-910-karmic-koala.html](http://www.ubuntumini.com/2009/11/user-guides-for-ubuntu-910-karmic-koala.html) 

You can create the bootable flash (pen) drive using unetbootin or the "Create a USB Startup Disk" included in Ubuntu. Simply copying the cd onto the drive doesn't make it bootable.

---

### Post by Ragtop on 2009-11-29
OK, I'm a wimp!  My Mini 9 arrived today with no operating system installed.  I'd been wrestling with Ubuntu 9.10, but couldn't get any joy from rejiggering the boot order in system setup.  I called and baffled the Dell support "chat" person til they referred me to phone support for Ubuntu.  That was an experience, to say the least, but as you might guess, the tech I got in India just wanted to get the computer running.   The only solution he had was to boot the mini from the 8.04 disk that came with.  So, I went and bought a new Toshiba CDRW etc, etc and called the number the last tech had given me, DELL main!!!  Well, about 40 minutes later I was talking to the same tech in India and he talked me thru booting and installing the software.  I could have done it myself, but I wanted documentation.

So, as I go thru the various setups to make the mini "Mine!" I cannot get the network card to recognize my home Linksys network.  (I have the same problem with a mini 10 running winXP!)  ](*,)

Does anyone have the "magic dust":rolleyes: to sprinkle on this thing to get it to talk to a Linksys network?  Is there a setup trick for the Dell net card to get it to hook up?

Thanks in advance!

BC

---

### Post by ugm6hr on 2009-11-29
The Mini 9 has a RealTek RTL8101E/RTL8102E PCI Express Fast Ethernet controller, which should just work.  No magic dust required.

You can check what's going on by plugging the ethernet cable in, and giving the output from:
```
ifconfig
route -n
```

PS: Since you were reinstalling anyway, I'd have gone for 9.04 or 9.10...  And asking here will often point you to useful info. e.g. [http://www.ubuntumini.com/2009/11/user-guides-for-ubuntu-910-karmic-koala.html](http://www.ubuntumini.com/2009/11/user-guides-for-ubuntu-910-karmic-koala.html)

---

### Post by superm1 on 2009-11-29
> **Ragtop said:**
> OK, I'm a wimp!  My Mini 9 arrived today with no operating system installed.  I'd been wrestling with Ubuntu 9.10, but couldn't get any joy from rejiggering the boot order in system setup.  I called and baffled the Dell support "chat" person til they referred me to phone support for Ubuntu.  That was an experience, to say the least, but as you might guess, the tech I got in India just wanted to get the computer running.   The only solution he had was to boot the mini from the 8.04 disk that came with.  So, I went and bought a new Toshiba CDRW etc, etc and called the number the last tech had given me, DELL main!!!  Well, about 40 minutes later I was talking to the same tech in India and he talked me thru booting and installing the software.  I could have done it myself, but I wanted documentation.

So, as I go thru the various setups to make the mini "Mine!" I cannot get the network card to recognize my home Linksys network.  (I have the same problem with a mini 10 running winXP!)  ](*,)

Does anyone have the "magic dust":rolleyes: to sprinkle on this thing to get it to talk to a Linksys network?  Is there a setup trick for the Dell net card to get it to hook up?

Thanks in advance!

BC

If you are using WPA2, try changing authentication modes from TKIP->AES or Vice/Versa.

---

### Post by Ragtop on 2009-11-30
Thanks for the replies, folks, and as we used to say in the radio business - "Keep those cards and letters coming!"  In this case, because the problem still persists.  The mini-9 (RealTek RTL8101E/RTL8102E PCI Express Fast Ethernet controller) connects fine on non-secured networks, of which I can often find one or two in my daily travels.  However, I have no intention of unsecuring my home network.  Until I bought this cute li'l feller, my network just consisted of a Dell XPS desktop that's about four years old, a one year old Dell Inspiron laptop, and the Linksys wireless router to connect to the cable modem.  That configuration worked fine, allowing me to work wherever I wanted around the house, or even next door and across the street.

Do I need a null modem, or a standard network cable to check that ipconfig, ugm6hr??

I was already wrestling with those later releases, but couldn't get USBcreator of unetbootin to make me a thumb drive, and since i had to go buy a CD drive anyway, I just thought I would stick with the disks that came with the mini while using Dell's (so called) :lolflag:Ubuntu support!  ( A story for another time - or not if others have had the same delightful:frown: experience I had with them over the weekend)

What is (and _*where*_ is) WPA2, please, superm1.?  If I knew if I was using it or even had it, perhaps I could "try changing authentication modes from TKIP->AES or Vice/Versa.     "  It sounds like a great idea!

Thanks again folks, and I'll continue this battle tomorrow.

---

### Post by ugm6hr on 2009-11-30
My mistake - I thought you were talking about wired ethernet.

I presume you are using WPA2 then; I have some recollections of there being problems with Broadcom wifi + 8.04 + WPA2.

There are posts scattered around about this which back up superm's advice:
[http://www.mydellmini.com/forum/dell-mini-9-hardware-issues-problems/14488-cant-connect-mini-9-ubuntu-linksys-wireless-router.html#post122334](http://www.mydellmini.com/forum/dell-mini-9-hardware-issues-problems/14488-cant-connect-mini-9-ubuntu-linksys-wireless-router.html#post122334)

Also: [https://bugs.launchpad.net/dell-mini/+bug/300784](https://bugs.launchpad.net/dell-mini/+bug/300784)
This says there is a fix in the updates - so make sure you have updated.  Use a wired ethernet to get the updates if necessary.

---

